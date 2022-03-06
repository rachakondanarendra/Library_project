# Library_project

/*Library project*/

#include<stdio.h>
#include<string.h>

struct book
{
    int no;
	char title[20];
	char author[20];
	float price;
};


int main()
{
	int i,n,range,choice,num=1;
    struct book b[20];
    
    while(num!=0)
    {
    printf("\n1.Reading books details\n2.Display books details\n3.Available books\n4.To print Book numberwise\n5.Search with title");
    printf("\n6.No.of available copies\n7.Delete book\n8.Update a book\n9.Insert specific position\n10.exit");
    
    printf("\n\nEnter your choice:");
    scanf("%d",&choice);
    
    
	if(choice==1)
	{
	printf("How many books details do you want to enter:");
    scanf("%d",&n);
    read(b,n);        //reading function 
	}

    else if(choice==2)
        print(b,n);       //printing funtoin 

    else if(choice==3)
	    available(b,n);   //available books
	    
	else if(choice==4)
		numberwise(b,n);          //books details-book numberwise

    else if(choice==5)
    	based_on_title(b,n); //searching a book based on title
	
    else if(choice==6)
        copies(b,n);  //available no.of copies for a book
        
    else if(choice==7)
    	n=delete_book(b,n);        //deleting a book

	
    else if(choice==8)
    	update_book(b,n);   //update a book
    	
    else if(choice==9)
		n=insert_by_pos(b,n);    //insert a book at specified postion
	
    else if(choice==10)
    {
	}
    else
    {
    	printf("\n\nError:invalid choice");
    	break;
    }
	
	printf("\n\nTo continue enter -> 1\nTo exit enter -> 0\n\nEnter your choice:");
    scanf("%d",&num);
    
    if(num<0 || num>1)
    {
    	printf("Error:Invalid choice");
    	break;
	}
	
	
}
}

int read(struct book b[ ],int n)     //reading function
{
	printf("\n------Reading books details------\n");
	int i;
	
    for(i=0;i<n;i++)
    {
    	
	    printf("\nEnter Book %d details\n\n",i+1);
	    printf("Enter book no:");
		scanf("%d",&b[i].no);
	    printf("Enter title:");
	    scanf("%s",b[i].title);
	    printf("Enter Author name:");
	    scanf("%s",b[i].author);
	    printf("Enter price:");
	    scanf("%f",&b[i].price);
	    
	    
	}

	
}

int print(struct book b[ ],int n)          //printing function
{
	int i;
	printf("\n------Books Details------\n");
	for(i=0;i<n;i++)
	{
		printf("\nBook %d details:\n",i+1);
	    printf("\nBook no :%d",b[i].no);
	    printf("\nTitle   :%s",b[i].title);
	    printf("\nAuthor  :%s",b[i].author);
        printf("\nPrice   :%f\n",b[i].price);
        
        if(b[i].no==b[i+1].no)
	    	break;
	    
			
	}
	
	
}

int available(struct book b[ ],int n)          //available books
{
	int i,j,count=0,size;
	printf("\nEnter no.of available books:");
	scanf("%d",&size);
	int available[size];
	printf("\nEnter available books numbers:");
	for (i=0;i<size;i++)
	{
	scanf("%d",&available[i]);
	}

	printf("\n------Available Books Details------\n");
	for(i=0;i<n;i++)
	{
		for(j=0;j<n;j++)
		{
		
		if(b[i].no==available[j])
		{
		    printf("\nBook %d details:\n",i+1);
	        printf("\nBook no :%d",b[i].no);
	        printf("\nTitle   :%s",b[i].title);
	        printf("\nAuthor  :%s",b[i].author);
            printf("\nPrice   :%f\n",b[i].price);
            count++;
            
        }
    }
        
	}
	printf("\nNo.of available books :%d\n ",count);
}

int based_on_title(struct book b[ ],int n)          //searching a book based on title
{
	char title[20];
	int i,j;
	printf("\n---Searching a book by its title---\n");
	printf("\nEnter book title:");
	scanf("%s",title);
	printf("\n------Your searched book Details------\n");
	for(i=0;i<n;i++)
	{
	    if(strcmp(b[i].title,title)==0)
	    {
		    printf("\nBook %d details:\n",i+1);
	        printf("\nBook no :%d",b[i].no);
	        printf("\nTitle   :%s",b[i].title);
	        printf("\nAuthor  :%s",b[i].author);
            printf("\nPrice   :%f\n",b[i].price);
		}
    }
}

int update_book(struct book b[ ],int n)          //update a book
{
	int i,u; 
	printf("\n------Book updation------\n");
	printf("\nEnter a book number to update:");
	scanf("%d",&u);  //u=updating book number
	
    printf("\n-------Enter new book details------\n");
   
	printf("\nEnter book no:");
	scanf("%d",&b[u-1].no);
	printf("Enter title:");
	scanf("%s",&b[u-1].title);
	printf("Enter Author name:");
	scanf("%s",&b[u-1].author);
    printf("Enter price:");
    scanf("%f",&b[u-1].price);
    
	printf("\n------Books Details after updation------\n");
	print(b,n);
}

int copies(struct book b[ ],int n)          //available no.of copies for a book
{
	int i,j,c[20],size;
	
	for(i=0;i<n;i++)
	{
		printf("\nEnter available copies for this book:'%s':",b[i].title);
		scanf("%d",&c[i]);
    }
	

	printf("\n------No.of copies available for a book title------\n");
	for(i=0;i<n;i++)
	{
		printf("\nAvailable copies for this book:'%s'' is %d",b[i].title,c[i]);
    }
}

int delete_book(struct book b[ ],int n)          //deleting a book
{
	int i,j,pos;
	printf("\n------Deleting a book------\n");
	
	printf("\nEnter book position to delete:");
	scanf("%d",&pos);   //d=deleting position
	if(pos>=n+1)
	{
		printf("\nInvalid position:deletion not possible\n");
	}
	else
	{
	
	for(i=pos-1;i<n-1;i++)
	{	
	
		b[i].no   =  b[i+1].no;
		strcpy(b[i].title,b[i+1].title);
		strcpy(b[i].author,b[i+1].author);
		b[i].price = b[i+1].price;
	}
	}
	printf("\n-------Books details after deletion-------\n");	
	for(i=0;i<n-1;i++)
	{
		printf("\nBook %d details:\n",i+1);
	    printf("\nBook no :%d",b[i].no);
	    printf("\nTitle   :%s",b[i].title);
	    printf("\nAuthor  :%s",b[i].author);
        printf("\nPrice   :%f\n",b[i].price);
	}
	return n-1;
}



int insert_by_pos(struct book b[ ],int n)          //inserting at specified position
{
	int i,j,pos;
	printf("\nEnter position to insert a book details:");
	scanf("%d",&pos);
	
	
	    
	for(i=n;i>=pos-1;i--)
	{
		b[i+1].no=b[i].no;
		strcpy(b[i+1].title,b[i].title);
		strcpy(b[i+1].author,b[i].author);
		b[i+1].price=b[i].price;
		
	}
	printf("Enter book no:");
	scanf("%d",&b[pos-1].no);
	printf("Enter title:");
	    scanf("%s",b[pos-1].title);
	    printf("Enter Author name:");
	    scanf("%s",b[pos-1].author);
	    printf("Enter price:");
	    scanf("%f",&b[pos-1].price);	
	    
	printf("\n------Books Details after inserting at specified position------\n");
	for(i=0;i<=n;i++)
	{
		printf("\nBook %d details:\n",i+1);
	    printf("\nBook no :%d",b[i].no);
	    printf("\nTitle   :%s",b[i].title);
	    printf("\nAuthor  :%s",b[i].author);
        printf("\nPrice   :%f\n",b[i].price);
	}
	return n+1;
}

int numberwise(struct book b[ ],int n)  //books details-book numberwise
{
	int i,j,temp;
	char tem[20];
	for(j=0;j<n-1;j++)
	{
		for(i=0;i<n-1;i++)
		{
			if(b[i].no>b[i+1].no)
			{
				temp=b[i].no;
				b[i].no=b[i+1].no;
				b[i+1].no=temp;
				
				strcpy(tem,b[i].title);
				strcpy(b[i].title,b[i+1].title);
				strcpy(b[i+1].title,tem);
				
				strcpy(tem,b[i].author);
				strcpy(b[i].author,b[i+1].author);
				strcpy(b[i+1].author,tem);
				
				temp=b[i].price;
				b[i].price=b[i+1].price;
				b[i+1].price=temp;
			}
		}
	}
	
	printf("-------Books details-books numberwise-------");
	for(i=0;i<n;i++)
	{
		printf("\nBook %d details:\n",i+1);
	    printf("\nBook no :%d",b[i].no);
	    printf("\nTitle   :%s",b[i].title);
	    printf("\nAuthor  :%s",b[i].author);
        printf("\nPrice   :%f\n",b[i].price);
	}
	
}





