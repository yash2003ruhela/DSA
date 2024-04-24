# DSA
import java.util.Scanner;
public class GraphCreate {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("Enter no of vertices");
        int n = sc.nextInt();

        while(n<0){
            System.out.println("enter valid vertex");
            n = sc.nextInt();
        }

        int[][]arr = new int[n][n];
        for ( int row=0;row<n;row++){
            for(int col=0;col<n;col++){
                System.out.println("Enter 1 if there is node between " +row+ "and" +col+ "else,Enter 0");
                int edge = sc.nextInt();
                if(edge!=0 && edge!=1){
                    edge = sc.nextInt();
                }
                arr[row][col] = edge;
                arr[col][row] = edge;


            }
        }
        System.out.println("Printing 2d matrix");

        for(int row=0;row<n;row++){
            for(int col=0;col<n;col++){
                System.out.print(arr[row][col]);
            }
        }
    }
}











// 2nd BFS
import java.util.LinkedList;
import java.util.Queue;

class Graph {
    int vertices;
    LinkedList<Integer>[] adjList;

    Graph(int vertices) {
        this.vertices = vertices;
        adjList = new LinkedList[vertices];
        for (int i = 0; i < vertices; ++i)
            adjList[i] = new LinkedList<>();
    }
    
    void addEdge(int u, int v) {
        adjList[u].add(v);
    }

    void bfs(int startNode) {
        Queue<Integer> queue = new LinkedList<>();
        boolean[] visited = new boolean[vertices];

        visited[startNode] = true;
        queue.add(startNode);

        while (!queue.isEmpty()) {
            int currentNode = queue.poll();
            System.out.print(currentNode + " ");

            for (int neighbor : adjList[currentNode]) {
                if (!visited[neighbor]) {
                    visited[neighbor] = true;
                    queue.add(neighbor);
                }
            }
        }
    }
}

public class Main {
    public static void main(String[] args) {
        int vertices = 5;

        Graph graph = new Graph(vertices);

        graph.addEdge(0, 1);
        graph.addEdge(0, 2);
        graph.addEdge(1, 3);
        graph.addEdge(1, 4);
        graph.addEdge(2, 4);

        System.out.print(
            "Breadth First Traversal starting from vertex 0: ");
        graph.bfs(0);
    }
}

