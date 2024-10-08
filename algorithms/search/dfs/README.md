# 깊이 우선 탐색(Depth First Search)

특정 정점(노드)에서 시작해서 트리나 그래프에서 한 가지 경로를 최대한 깊이 탐색하고, 해당 경로를 끝까지 탐색한 후 다른 경로로 이동

모든 정점을 방문하고자 하는 경우에 사용

#### DFS의 특징

- 일반적으로 재귀 함수를 사용하여 구현
  - 스택으로도 구현 가능
- 모든 경우의 수에 대해 탐색을 진행
- 사이클이 있는 경우, 무한 루프에 빠지지 않도록 방문 체크를 해주어야 함
  - 사이클(Cycle) : 그래프에서 한 노드에서 시작해, 여러 간선을 지나 시작 노드로 다시 도착하는 경로
- BFS보다 깊은 경로를 빠르게 찾는데 용이

```
def dfs(now):
  visited[now] = 1
  print(now, end=" ")

  for next in v[now]:
    if visited[next] == 0:
      dfs(next)
```

#### DFS의 시간복잡도

V : 정점(노드)의 수, E : 간선의 수  
인접 리스트로 표현된 그래프 : O(V + E)  
인접 행렬로 표현된 그래프 : O(V^2)  
희소 그래프(그래프 내에 적은 숫자의 간선만을 가지는 그래프)의 경우 인접 행렬보다 인접 리스트를 사용하는 것이 유리

인접 리스트(각 정점에서 이동 가능한 간선을 리스트로 표시)  
1 |-> 2 -> 3  
2 |-> 3 -> 4  
3 |  
4 |-> 3

인접 행렬((x,y) = 1 이면 x에서 y로 가는 간선이 존재한다는 의미)  
0 | 1 | 1 | 0  
0 | 0 | 1 | 1  
0 | 0 | 0 | 0  
0 | 0 | 1 | 0
