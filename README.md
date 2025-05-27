TERMWORK 1A  DATE : 13/02/2025

#include <stdio.h>
#include <stdlib.h>
//Function to compute gcd
int gcd(int m, int n)
{
    int r;
    while(n!=0)
    {
        r=m%n;
        m=n;
        n=r;
    }
    return m;
}
int main()
{
    int m,n;
    //Input two non negative and non zero numbers.
    printf("Enter two non negative and non zero numbers.\n");
    scanf("%d%d",&m,&n);
    if(m<=0||n<=0)
    {
        printf("Invalid input.\nTry again.\n");
    }
    else
    {
        int result=gcd(m,n);
        printf("GCD of %d and %d is %d.\n",m,n,result);
    }
    return 0;
}

=> OUTPUT
Enter two non negative and non zero numbers.
50 5
GCD of 50 and 5 is 5.
=================================================================================================================================

TERMWORK 1B  DATE : 13/02/2025

#include <stdio.h>
#include <stdlib.h>

int main()
{
    int m,n,t;
    //Input two non negative and non zero numbers.
    printf("Enter two non negative and non zero numbers.\n");
    scanf("%d%d",&m,&n);
    if(m<=0||n<=0)
    {
        printf("Invalid input.\nTry again.\n");
    }
    else
    {
       if(m<n)
       {
           t=m;
       }
       else
       {
           t=n;
       }
       /*while(t)
       {
           if(m%t==0)
           {
               if(n%t==0)
               {
                   printf("GCD(%d,%d)=%d\n",m,n,t);
                   exit(0);
               }
               else
               {
                   t--;
               }
           }
           else
           {
                t--;
           }
       }*/
       while(t>0)
       {
           if(m%t==0 & n%t==0)
           {
               printf("GCD(%d,%d)=%d\n",m,n,t);
               exit(0);
           }
           else
           {
               t--;
           }
       }
    }
    return 0;
}

=>OUTPUT
Enter two non negative nad non zero numbers.
10 5
GCD(10,5)=5
=================================================================================================================================

TERMWORK 2A    DATE : 19/02/2025

#include <stdio.h>
#include <stdlib.h>

int main()
{
    int item,pos,flag=0,i,a[5];
    printf("Enter array elements : ");
    for(i=0;i<5;i++)
    {
        scanf("%d",&a[i]);
    }
    printf("Enter item to search : ");
    scanf("%d",&item);
    for(i=0;i<5;i++)
    {
        if(a[i]==item)
        {
            flag=1;
            pos=i;
            break;
        }
    }
    if(flag==1)
    {
        printf("%d is present in the array at position %d.\n",item,pos+1);
    }
    else
    {
        printf("%d is not found in the array.\n");
    }
    return 0;
}

=> OUTPUT
Enter array elements : 4 6 2 8 7
Enter item to search : 2
2 is present in the array at position 3.

=================================================================================================================================

TERMWORK 2B   DATE 19/02/2025

#include <stdio.h>
#include <stdlib.h>
#include<time.h>
#define MAX 200

void getdata(int arr[])
{
    int i;
    for(i=0;i<MAX;i++)
    {
        arr[i]=rand();
        printf("%d ",arr[i]);
    }
}
int main()
{
    int item,pos,flag=0,i,a[MAX];
    clock_t start1=0,end1=0;
    getdata(a);
    start1=start1+clock();
    printf("\n\nEnter item to search : ");
    scanf("%d",&item);
    for(i=0;i<MAX;i++)
    {
        if(a[i]==item)
        {
            flag=1;
            pos=i;
            break;
        }
    }
    if(flag==1)
    {
        printf("\n%d is present in the array at position %d.\n",item,pos+1);
    }
    else
    {
        printf("\n%d is not found in the array.\n",item);
    }
    end1=end1+clock();
    printf("\nTime taken is = %f\n",((float)(end1-start1))/CLOCKS_PER_SEC);
    return 0;
}

=>OUTPUT
41 18467 6334 26500 19169 15724 11478 29358 26962 24464 5705 28145 23281 16827 9961 491 2995 11942 
4827 5436 32391 14604 3902 153 292 12382 17421 18716 19718 19895 5447 21726 14771 11538 1869 19912 
25667 26299 17035 9894 28703 23811 31322 30333 17673 4664 15141 7711 28253 6868 25547 27644 32662 
32757 20037 12859 8723 9741 27529 778 12316 3035 22190 1842 288 30106 9040 8942 19264 22648 27446 
23805 15890 6729 24370 15350 15006 31101 24393 3548 19629 12623 24084 19954 18756 11840 4966 7376 
13931 26308 16944 32439 24626 11323 5537 21538 16118 2082 22929 16541 4833 31115 4639 29658 22704 
9930 13977 2306 31673 22386 5021 28745 26924 19072 6270 5829 26777 15573 5097 16512 23986 13290 
9161 18636 22355 24767 23655 15574 4031 12052 27350 1150 16941 21724 13966 3430 31107 30191 18007 
11337 15457 12287 27753 10383 14945 8909 32209 9758 24221 18588 6422 24946 27506 13030 16413 29168 
900 32591 18762 1655 17410 6359 27624 20537 21548 6483 27595 4041 3602 24350 10291 30836 9374 11020 
4596 24021 27348 23199 19668 24484 8281 4734 53 1999 26418 27938 6900 3788 18127 467 3728 14893 24648 
22483 17807 2421 14310 6617 22813 9514

Enter item to search : 3430

3430 is present in the array at position 136.

Time taken is = 5.499000

=================================================================================================================================

TERMWORK 3        DATE : 05/03/2025

#include <stdio.h>
#include<time.h>
#include <stdlib.h>
#define MAX 48000

void mergesort(int arr[], int low, int high){
    int mid;
    if(low<high){
        mid=(low+high)/2;
        mergesort(arr,low,mid);
        mergesort(arr,mid+1,high);
        merge(arr,low,mid,high);
    }
}

void merge(int arr[], int low, int mid, int high){
    int i,j,k,l,b[MAX];
    l=low;
    i=low;
    j=mid+1;
    while((l<=mid)&&(j<=high)){
        if(arr[l]<=arr[j]){
            b[i]=arr[l];
            l++;
        }
        else{
            b[i]=arr[j];
            j++;
        }
        i++;
    }
    if(l>mid){
        for(k=j;k<=high;k++){
            b[i]=arr[k];
            i++;
        }
    }
    else{
        for(k=l;k<=mid;k++){
            b[i]=arr[k];
            i++;
        }
    }
    for(k=low;k<=high;k++){
        arr[k]=b[k];
    }
}

void getdata(int arr[]){
    int i;
    printf("Randomly generated array.\n");
    for(i=0;i<MAX;i++){
        arr[i]=rand();
        printf("%d ",arr[i]);
    }
}

int main()
{
    int arr[MAX];
    clock_t start1=0,end1=0;
    getdata(arr);
    start1=start1+clock();
    mergesort(arr,0,MAX-1);

    printf("\n\nSorted array.\n");

    for(int i=0;i<MAX;i++){
        printf("%d ",arr[i]);
    }
    printf("\n");
    end1=end1+clock();
    printf("TIme taken is = %f\n",((float)(end1-start1))/CLOCKS_PER_SEC);
    return 0;
}

OUTPUT ==>

Randomly generated array.
41 18467 6334 26500 19169 15724 11478 29358 26962 24464 5705 28145 23281 16827 9961 491 2995 11942 4827 5436 32391 14604 3902 153 292 12382 17421 18716 19718 19895 5447 21726 14771 11538 1869 19912 25667 26299 17035 9894 28703 23811 31322 30333 17673 4664 15141 7711 28253 6868

Sorted array.
41 153 292 491 1869 2995 3902 4664 4827 5436 5447 5705 6334 6868 7711 9894 9961 11478 11538 11942 12382 14604 14771 15141 15724 16827 17035 17421 17673 18467 18716 19169 19718 19895 19912 21726 23281 23811 24464 25667 26299 26500 26962 28145 28253 28703 29358 30333 31322 32391
TIme taken is = 0.000000

=================================================================================================================================

TERMWORK 4           DATE : 05/03/2025

#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#define MAX 200

void getdata(int arr[]) {
    int i;
    for (i = 0; i < MAX; i++) {
        arr[i] = rand();  // Generate random numbers
        printf("%d ", arr[i]);
    }
}

void insertionSort(int arr[], int n) {
    int i, j, v;
    for (i = 1; i < n; i++) {
        v = arr[i];  // Store the current element
        j = i - 1;

        // Shift elements of the sorted part to the right
        while (j >= 0 && arr[j] > v) {
            arr[j + 1] = arr[j];
            j = j - 1;
        }

        // Insert the current element at the correct position
        arr[j + 1] = v;
    }
}

int main() {
    int arr[MAX];
    clock_t start, end;

    printf("Randomly generated array is : \n\n");
    getdata(arr);  // Generate random array

    start = clock();

    insertionSort(arr, MAX);  // Sorting using Insertion Sort

    printf("\n\nAfter sorting, Array becomes : \n\n");
    for(int i=0;i<MAX;i++){
        printf("%d ",arr[i]);
    }
    end = clock();

    printf("\n\nTime Taken is = %f seconds\n", ((double)(end - start)) / CLOCKS_PER_SEC);

    return 0;
}

OUTPUT ==>

Randomly generated array is :

41 18467 6334 26500 19169 15724 11478 29358 26962 24464 5705 28145 23281 16827 9961 491 2995 11942 4827 5436

After sorting, Array becomes :

41 491 2995 4827 5436 5705 6334 9961 11478 11942 15724 16827 18467 19169 23281 24464 26500 26962 28145 29358

Time Taken is = 0.000000 seconds

=================================================================================================================================

TERMWORK 5       DATE : 12/03/2025

#include <stdio.h>
#include <stdlib.h>
#define MAX 20
#define INFINITY 999

int cost[MAX][MAX], visited[MAX];

void prims(int cost[][MAX], int n) {
    int i, j, ne = 1;
    int a, b, u, v, min, mincost = 0;
    for (i = 2; i <= n; i++)
        visited[i] = 0;

    printf("\nEdges of the spanning tree - \n");
    visited[1] = 1;  // Start with vertex 1

    while (ne < n) {
        min = INFINITY;

        // Find the edge with the minimum weight
        for (i = 1; i <= n; i++) {
            if (visited[i] == 1) {
                for (j = 1; j <= n; j++) {
                    if (visited[j] == 0 && cost[i][j] < min) {
                        min = cost[i][j];
                        a = i;
                        b = j;
                    }
                }
            }
        }

        if (visited[b] == 0) {
            printf("%d. EDGE (%d,%d) = %d\n", ne++, a, b, min);
            mincost += min;
            visited[b] = 1;  // Mark the vertex as visited
        }
        cost[a][b] = cost[b][a] = INFINITY;  // Remove the edge from consideration
    }

    printf("\nMINIMUM COST = %d\n", mincost);
}

int main() {
    int i, j, n;
    printf("Enter the number of vertices: ");
    scanf("%d", &n);

    printf("Enter the cost matrix (Enter 999 for INFINITY):\n");
    for (i = 1; i <= n; i++) {
        for (j = 1; j <= n; j++) {
            scanf("%d", &cost[i][j]);
            if (cost[i][j] == 0 && i != j) {
                cost[i][j] = INFINITY;  // No edge between different nodes
            }
        }
    }

    prims(cost, n);

    return 0;
}

OUTPUT =>

Enter the number of vertices: 4
Enter the cost matrix (Enter 999 for INFINITY):
999 1 4 2
1 999 999 999
4 999 999 3
2 999 3 999

Edges of the spanning tree -
1. EDGE (1,2) = 1
2. EDGE (1,4) = 2
3. EDGE (4,3) = 3

MINIMUM COST = 6

=================================================================================================================================

TERMWORK 6                 DATE : 26/03/2025

#include <stdio.h>
#include <stdlib.h>
#define MAX 20

int main(int argc, char *argv[]) {
    int x[MAX] = {0}, weights[MAX], values[MAX], v[MAX][MAX], n, i, j, m, val1, val2;

    // Input number of items
    printf("Enter the number of items: ");
    scanf("%d", &n);

    // Input item weights
    printf("Enter weights: \n");
    for(i = 0; i < n; i++)  // Start from 0 to work with 0-based index
        scanf("%d", &weights[i]);

    // Input item values
    printf("Enter values: \n");
    for(i = 0; i < n; i++)  // Start from 0 to work with 0-based index
        scanf("%d", &values[i]);

    // Input knapsack capacity
    printf("Enter the KNAPSACK capacity: ");
    scanf("%d", &m);

    // Initialize DP table
    for(i = 0; i <= n; i++) {
        for(j = 0; j <= m; j++) {
            if(i == 0 || j == 0)
                v[i][j] = 0;
            else
                v[i][j] = -1;
        }
    }

    // Dynamic programming process to fill the table
    for(i = 1; i <= n; i++) {
        for(j = 1; j <= m; j++) {
            if(j < weights[i-1])  // Adjusted for 0-based index
                v[i][j] = v[i-1][j];
            else {
                val1 = values[i-1] + v[i-1][j-weights[i-1]];  // Adjusted for 0-based index
                val2 = v[i-1][j];
                if(val1 > val2)
                    v[i][j] = val1;
                else
                    v[i][j] = val2;
            }
        }
    }

    // Print the DP table
    printf("The matrix is:\n");
    for(i = 0; i <= n; i++) {
        for(j = 0; j <= m; j++) {
            printf("%d\t", v[i][j]);
        }
        printf("\n");
    }

    // Output the maximum profit
    printf("Maximum profit obtained is: %d\n", v[n][m]);

    // Track the selected items
    i = n;
    j = m;
    while(i != 0 && j != 0) {
        if(v[i][j] != v[i-1][j]) {
            x[i-1] = 1;  // Mark item as selected (0-based index for x)
            j = j - weights[i-1];  // Adjust index for weights (0-based)
        }
        i = i - 1;
    }

    // Output selected item weights
    printf("Weights of selected items are: {");
    for(i = 0; i < n; i++) {
        if(x[i] == 1)
            printf(" %d ", weights[i]);  // Print weights instead of values
    }
    printf("}\n");

    system("PAUSE");
    return 0;
}

OUTPUT ==>

Enter the number of items: 4
Enter weights:
3 4 5 6
Enter values:
2 3 4 1
Enter the KNAPSACK capacity: 8
The matrix is:
0       0       0       0       0       0       0       0       0
0       0       0       2       2       2       2       2       2
0       0       0       2       3       3       3       5       5
0       0       0       2       3       4       4       5       6
0       0       0       2       3       4       4       5       6
Maximum profit obtained is: 6
Weights of selected items are: { 3  5 }

=================================================================================================================================

TERMWORK 7                   DATE : 02/04/2025

#include <stdio.h>
#include <stdlib.h>


void floyds(int p[10][10], int n) {
    int i, j, k;
    for(k = 1; k <= n; k++) {
        for(i = 1; i <= n; i++) {
            for(j = 1; j <= n; j++) {
                if(p[i][j] > p[i][k] + p[k][j]) {
                    p[i][j] = p[i][k] + p[k][j];
                }
            }
        }
    }
}

int main() {
    int p[10][10], w, n, e, u, v, i, j;

    printf("Enter the number of vertices: ");
    scanf("%d", &n);
    printf("Enter the number of edges: ");
    scanf("%d", &e);

    // Initialize the matrix with infinity (999) for all non-diagonal elements
    // Diagonal elements are initialized to 0 (distance from a vertex to itself is 0)
    for(i = 1; i <= n; i++) {
        for(j = 1; j <= n; j++) {
            if(i == j)
                p[i][j] = 0;  // Distance to itself is 0
            else
                p[i][j] = 999;  // Set to infinity
        }
    }

    // Input the edges and their weights
    for(i = 1; i <= e; i++) {
        printf("Enter the end vertices of edge %d with its weight: ", i);
        scanf("%d%d%d", &u, &v, &w);
        if(u <= n && v <= n) {
            p[u][v] = w;
        } else {
            printf("Invalid vertex number. Please enter valid vertex numbers.\n");
            i--;  // Decrement i to repeat the input for this edge
        }
    }

    // Print the input matrix (Adjacency Matrix)
    printf("\nMatrix of input data:\n");
    for(i = 1; i <= n; i++) {
        for(j = 1; j <= n; j++) {
            printf("%d\t", p[i][j]);
        }
        printf("\n");
    }

    // Run Floyd-Warshall algorithm to compute shortest paths
    floyds(p, n);

    // Print the result (Shortest paths)
    printf("\nThe shortest paths are:\n");
    for(i = 1; i <= n; i++) {
        for(j = 1; j <= n; j++) {
            if(p[i][j] == 999)
                printf("999\t");  // If there's no path, print "INF"
            else
                printf("%d\t", p[i][j]);
        }
        printf("\n");
    }

    return 0;
}

OUTPUT ==>

Enter the number of vertices: 3
Enter the number of edges: 9
Enter the end vertices of edge 1 with its weight: 1 1 0
Enter the end vertices of edge 2 with its weight: 1 2 4
Enter the end vertices of edge 3 with its weight: 1 3 5
Enter the end vertices of edge 4 with its weight: 2 1 2
Enter the end vertices of edge 5 with its weight: 2 2 0
Enter the end vertices of edge 6 with its weight: 2 3 999
Enter the end vertices of edge 7 with its weight: 3 1 999
Enter the end vertices of edge 8 with its weight: 3 2 2
Enter the end vertices of edge 9 with its weight: 3 3 0

Matrix of input data:
0       4       5
2       0       999
999     2       0

The shortest paths are:
0       4       5
2       0       7
4       2       0

=================================================================================================================================

TERMWORK -08                   DATE : 16/04/2025

#include <stdio.h>
#include <stdlib.h>
#include<math.h>
#define MAX 20

char arr[MAX][MAX];

void print_grid(int n, int x[]){
    for(int i=1;i<=n;i++){
        for(int j=1;j<=n;j++){
            arr[i][j]='-';
        }
    }

    for(int i=1;i<=n;i++){
        arr[i][x[i]]='Q';
    }

    for(int i=1;i<=n;i++){
        for(int j=1;j<=n;j++){
            printf("\t%c",arr[i][j]);
        }
        printf("\n");
    }
}

int safetoplace(int x[], int k){
    for(int i=1;i<k;i++){
        if(x[i]==x[k]||i-x[i]==k-x[k]||i+x[i]==k+x[k])
            return 0;//false
    }
    return 1;//true
}

void nqueens(int n){
    int x[20],count=0,k=1;
    x[k]=0;
    while(k!=0){
        x[k]=x[k]+1;
        while((x[k]<=n)&&(!safetoplace(x,k))){
            x[k]=x[k]+1;
        }
        if(x[k]<=n){
            if(k==n){
                count++;
                printf("\n\tPlacement %d is : \n\n\n",count);
                print_grid(n,x);
                getch();
            }
            else{
                k++;
                x[k]=0;
            }
        }
        else{
            k--;
        }
    }
    return;
}

int main()
{
    int n;
    printf("\t CPROGRAM OF N-QUEEN PROBLEM\n\n");
    printf("\nEnter the number of Queens : ");
    scanf("%d",&n);
    printf("\n\n\tUSING %d QUEEN'S STRATEGY\n\n",n);
    nqueens(n);
    return 0;
}

OUTPUT =>

         CPROGRAM OF N-QUEEN PROBLEM


Enter the number of Queens : 4


        USING 4 QUEEN'S STRATEGY


        Placement 1 is :


        -       Q       -       -
        -       -       -       Q
        Q       -       -       -
        -       -       Q       -

        Placement 2 is :


        -       -       Q       -
        Q       -       -       -
        -       -       -       Q
        -       Q       -       -

Process returned 0 (0x0)   execution time : 4.062 s
Press any key to continue.

=================================================================================================================================

TERMWORK -09                   DATE : 09/04/2025

#include <stdio.h>
#include <stdlib.h>
#define INF 999

int a[10][10], visited[10], n, e, cost = 0;

void get() {
    int i, j;

    printf("Enter the number of cities (nodes): ");
    scanf("%d", &n);

    printf("Enter weight matrix (enter %d for no direct connection):\n", INF);

    for (i = 1; i <= n; i++) {
        for (j = 1; j <= n; j++) {
            scanf("%d", &a[i][j]);
            if (a[i][j] == 0 && i != j) {
                a[i][j] = INF;
            }
        }
        visited[i] = 0;
    }
}

void mincost(int city) {
    int i, ncity;
    visited[city] = 1;
    printf("%d -> ", city);
    ncity = least(city);
    if (ncity == -1) {
        for (i = 1; i <= n; i++) {
            if (a[city][i] != INF && visited[i] == 0) {
                ncity = i;
                printf("%d", ncity);
                cost += a[city][ncity]; // Increment cost here
                visited[ncity] = 1;
                return;
            }
        }
        return;
    }
    cost += a[city][ncity]; // Increment cost when moving to the least neighbor
    mincost(ncity);
}

int least(int c) {
    int i, nc = -1;
    int min = INF;

    for (i = 1; i <= n; i++) {
        if ((a[c][i] != INF) && (visited[i] == 0)) {
            if (a[c][i] < min) {
                min = a[c][i];
                nc = i;
            }
        }
    }
    return nc;
}

void put() {
    printf("\nMinimum cost : %d\n", cost);
}

int main() {
    get();
    printf("\nThe Path is : ");
    mincost(1);
    printf("1\n");
    put();
    return 0;
}

OUTPUT =>

Enter the number of cities (nodes): 5
Enter weight matrix (enter 999 for no direct connection):
0 2 999 5 1
2 0 4 999 999
999 4 0 3 999
5 999 3 0 2
1 999 999 2 0

The Path is : 1 -> 5 -> 4 -> 3 -> 2 -> 1

Minimum cost : 10

=================================================================================================================================

TERMWORK 10     DATE : 23/04/2025

#include <stdio.h>
#include <stdlib.h>

struct Node{
    int data;
    struct Node *left;
    struct Node *right;
};

struct Node* createNode(int data){
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data=data;
    newNode->left=NULL;
    newNode->right=NULL;
    return newNode;
};

void insert(struct Node **root, int data){
    struct Node *newNode = createNode(data);
    if(*root == NULL){
        *root = newNode;
        return;
    }
    struct Node *current = *root;
    while(1){
        if(data<current->data){
            if(current->left==NULL){
                current->left=newNode;				 // if lesft child is NULL -> insert there 
                break;
            }
            else{
                current=current->left; 				// or move to left child
            }
        }
        else{
            if(current->right==NULL){
                current->right=newNode;
                break;
            }
            else{
                current=current->right;
            }
        }
    }
}

void inOrder(struct Node *root){
    if(root!=NULL){
        inOrder(root->left);
        printf("%d ",root->data);
        inOrder(root->right);
    }
}

void freeTree(struct Node *root){
    if(root!=NULL){
       freeTree(root->left);
       freeTree(root->right);
       free(root);
    }
}

int main()
{
    int arr[]={5,3,7,1,4,6,8};
    int n=sizeof(arr)/sizeof(arr[0]);
    struct Node *root = NULL;
    for(int i=0;i<n;i++)
        insert(&root,arr[i]);
    printf("Sorted Array : ");
    inOrder(root);
    printf("\n");
    freeTree(&root);
    return 0;
}

OUTPUT =>

Sorted Array : 1 3 4 5 6 7 8
