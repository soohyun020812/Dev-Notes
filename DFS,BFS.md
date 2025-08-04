### DFS / BFS 탐색 알고리즘 정리
그래프 탐색 알고리즘은 복잡한 구조(네트워크)에서 특정 개체를 찾거나, 연결성을 파악하거나, 가능한 모든 조합을 확인할 때 사용됩니다. 대표적인 탐색 방식으로 DFS(깊이 우선 탐색)와 BFS(너비 우선 탐색)가 있습니다.

---

**📌 DFS vs BFS 비유**
> **드라마 시청 비유**
  - **DFS** : 드라마 한 편 끝까지 몰아보고 다음 드라마 보기  
  - **BFS** : 여러 드라마를 동시에 한 회차씩 보는 방식  

---

**💡 문제 유형**

DFS/BFS는 다음과 같은 유형에서 주로 활용됩니다:

| 유형       | 설명                                   |
|------------|----------------------------------------|
| 경로 탐색  | 최단거리, 특정 목적지까지 도달 여부 등 |
| 네트워크   | 연결 여부 확인 (컴퓨터, 사회관계망 등) |
| 조합 만들기 | 가능한 모든 경우의 수 탐색             |

---

### 🔨 DFS (Depth-First Search)

**✅ 개요**
  - 한 갈래를 **끝까지** 탐색한 뒤, **다른 갈래**로 이동
  - **재귀 함수** 기반 구현이 일반적

**✅ 구현 예시 (프로그래머스 타겟 넘버 문제)**
```java
void dfs(int n, int sum, int[] numbers, int target) {
    if (n == numbers.length) {
        if (sum == target)
            answer++;
        return;
    }

    dfs(n + 1, sum + numbers[n], numbers, target);
    dfs(n + 1, sum - numbers[n], numbers, target);
}
```

**✅ 설명**
  - 인덱스를 하나씩 늘려가며 재귀 호출
  - 각 숫자를 더하거나 빼는 두 경우의 수 모두 탐색
  - 모든 경우의 수를 확인

--- 

### 🔄 BFS (Breadth-First Search)

**✅ 개요**
  - 모든 인접 노드를 한 번에 방문한 후, 그 다음 레벨로 이동
  - Queue (FIFO) 기반 구현이 일반적

**✅ 구현 예시 (프로그래머스 여행경로 문제)**
```python
from collections import deque

queue = deque()
queue.append("ICN")

while queue:
    current = queue.popleft()
    for next in flights_from[current]:
        queue.append(next)
```

**✅ 설명**
  - 시작점에서 출발 가능한 노드를 Queue에 넣음
  - Queue에서 하나씩 꺼내면서 그 다음 연결 노드를 탐색
  - 연결된 순서대로 탐색하여 경로의 순서 보장

--- 

**⚖️ DFS vs BFS 비교**
| 항목    | DFS                       | BFS                      |
| ----- | ------------------------- | ------------------------ |
| 탐색 방식 | 한 갈래 끝까지 → 백트래킹           | 같은 레벨을 순서대로 모두 탐색        |
| 구현 방법 | 재귀 함수 (stack 기반)          | Queue 또는 LinkedList 사용   |
| 특징    | 조합 완성 후 검증 → 명확한 정답 판별 가능 | 비교적 시간 효율적 (최단 거리 등에 유리) |
| 단점    | 깊이 탐색 시 시간 오래 걸릴 수 있음     | 메모리 사용량 증가 가능            |

