# Table of Contents

**Dynamic programming**
  - 1 [Ways to handle DP](https://github.com/opalInwza007x/Dynamic_Programming-101#1-ways-to-handle-dp)
  - 2 [Top-down DP](https://github.com/opalInwza007x/Dynamic_Programming-101/blob/main/README.md#2-top-down-dp)
      - 2.1 Coin Change
      - 2.2 Paths in a grid
      - 2.3 Grid Paths
      - 2.4 DP Tasks
  - 3 [Partitioning Problem](https://github.com/opalInwza007x/Dynamic_Programming-101/blob/main/README.md#3-partitioning-problem)
      - 3.1 ตัวอย่างโจทย์ Partitioning
      - 3.2 Partitioning Tasks
  - 4 [Bitmask with Dynamic Programming](https://github.com/opalInwza007x/Dynamic_Programming-101/blob/main/README.md#4-bitmask-with-dynamic-programming)
      - 4.1 ตัวอย่างโจทย์ Bitmask with DP
      - 4.2 Bitmask with DP Tasks

2. Billboard
3. ก้านกล้วย
4. ICPC_K_Magic_Staff
6. หยิบหิน
7. cheese
8. secret
9. สู้เขา Courage

# Dynamic programming 101

ปล. นี่เป็นภาษา opal_Inwza007x ถ้าไม่เข้าใจ ก็ไปถาม [opal_Inwza007x](https://www.facebook.com/profile.php?id=100002974790342) 

ปล2. ผมชอบยกตัวอย่างจากโจทย์ วิธีที่ดีที่สุดสำหรับการเรียนแบบนี้คือ __ต้องเข้าใจว่าผมทำไรไปบ้าง__ แล้วก็เดี๋ยวแปะ similar question ไว้ให้ลอง :D

__ปล3. ผมชอบเขียนเป็น Top-Down นะครับ เน้น Recursive 555__

Dynamic programming หรือ DP หรือ กำหนดการพลวัต คือเทคนิคที่ทำให้เราได้คำตอบที่มีประสิทธิภาพมากที่สุด โดยการลองแยกสถานการณ์ใหญ่เป็นสถานการณ์เล็กๆ เพื่อรวมคำตอบที่ดีที่สุดจากสถานการณ์เล็กๆไปตอบสถานการณ์ใหญ่

## 1. Ways to handle DP

วิธืรับมือโจทย์ DP ฉบับ Top-Down Enjoyer

0. (สำคัญ) พยายามดูโจทย์ให้เป็น DP

1. อ่านโจทย์ให้เรียบร้อย เช็คว่าควรเก็บ state ไหนบ้าง

2. คิด Base case เพื่อหยุดการ recursive

3. คิดว่าการ recursive แต่ละครั้ง เป็นแบบไหนได้บ้าง

4. ใส่ memorization เพื่อลดการคิดซ้ำ

5. Implement! มันส์ๆ

## 2. Top-down DP

### 2.1 ตัวอย่างที่ 1 Coin Change

> กำหนดให้คุณต้องทอนเงินทั้งหมด m บาท โดนคุณมีเหรียญทั้งหมด n ชนิด ต้องทอนเงินน้อยที่สุดจำนวนกี่เหรียญ

__Test Case#1__

ต้องทอนเงิน 19 บาท โดยคุณมีเหรียญ 3 ชนิด คือ 1 บาท, 4 บาท, 5 บาท ต้องทอนน้อยที่สุดกี่เหรียญ

- ในกรณีนี้ถ้าเราใช้ Greedy โดยการทอนเหรียญที่มีมูลค่ามากที่สุดไปตลอดก็ได้ครับ โดยเราจะทอน 5 บาท 3 รอบ แล้วก็ 4 บาท 1 รอบ ซึ่งก็คือเราจะทอนไป 4 เหรียญนั่นเอง

__Test Case#2__

ต้องทอนเงิน 6 บาท โดยคุณมีเหรียญ 3 ชนิด คือ 1 บาท, 3 บาท, 4 บาท ต้องทอนน้อยที่สุดกี่เหรียญ

- ในกรณีนี้ถ้าเรา Greedy โดยการทอนเหรียญที่มีมากสุดไปตลอด จะได้เป็น 4 บาท 1 รอบและ 1 บาท 2 รอบ นั่นก็คือเราทอนไป 3 เหรียญ แต่ช้าก่อน!!! ถ้าเราทอน 3 บาทไป 2 รอบ เราจะทอนไปแค่ 2 เหรียญเอง ซึ่งน้อยกว่าอย่างเห็นได้ชัด
  
__ขั้นที่ 1 อ่านโจทย์ให้เรียบร้อย เช็คว่าควรเก็บ state ไหนบ้าง__

> A state can be defined as the set of parameters that can uniquely identify a certain position or standing in the given problem.

ก็ประมาณว่าเอาไว้ระบุสถานะพิเศษของที่เรากำลังคิดอยู่ เช่น ตอนนี้เราเหลือ 3 บาทที่ต้องทอน หรือว่าเหลือ m บาทที่ต้องทอน

```c++
ll solve(ll m) {
    // process
}
```

__ขั้นที่ 2 คิด Base case เพื่อหยุดการ recursive__

ในโจทย์นี้ก็มีเคสหยุดคือ 

- เหลือ 0 บาทที่ต้องทอน นั่นก็คือเราทอนครบแล้วนั่นเอง

- เหลือน้อยกว่า 0 บาทที่ต้องทอน นั่นคือเราทอนเงินเกินแล้วอย่าเอาเคสนี้มาคิดเด็ดขาด!!!

```c++
ll solve(ll m) {
    if (m == 0) {
        return 0; 
    }
    if (m < 0) {
        return inf; // เราต้องการทอนน้อยๆ เพราะฉะนั้นเราจึงคืนค่ามากๆ เพื่อไม่ให้ได้เอาไปคิด
    }
    // process
}
```

__ขั้นที่ 3 คิดว่าการ recursive แต่ละครั้ง เป็นแบบไหนได้บ้าง__

ก็คือเรามีเหรียญทั้งหมด n ชนิด ในตอนที่เราต้องทอน m บาท เราก็ลองทอนไปทุก n ชนิดเลยครับ โดยเราต้องการเคสที่ทอนด้วยจำนวนน้อยที่สุด

```c++
ll solve(ll m) {
    if (m == 0) {
        return 0; 
    }
    if (m < 0) {
        return inf;
    }
    ll min_change = inf; // เวลาหาค่าน้อยๆ ตั้งค่ามากๆ ไว้ก่อน
    for (auto e : coins) {
        min_change = min(min_change, solve(m - e) + 1); // การทอนแต่ละครั้งใช้ 1 เหรียญเท่ากันหมด
    }
    return min_change;
}
```

__ขั้นที่ 4 ใส่ memorization เพื่อลดการคิดซ้ำ__

```c++
ll solve(ll m) {
    if (m == 0) {
        return 0; 
    }
    if (m < 0) {
        return inf;
    }
    if (visited[m]) {
        return memo[m]; // เคยมาแล้ว
    }
    visited[m] = 1; // ถ้ายังไม่เคยมา ตอนนี้ก็มาแล้ว
    ll min_change = inf;
    for (auto e : coins) {
        min_change = min(min_change, solve(m - e) + 1);
    }
    memo[m] = min_change // จำค่าไว้
    return memo[m];
}
```

คำตอบของเราจะเกิดจากการเรียก `solve(m);`

ถ้าสรุปเป็นสมการ recursive ก็ได้ตามภาพเลยครับ

<img src="https://github.com/opalInwza007x/TEST/assets/114739286/de6e3ed5-bf3c-4642-8419-ca4a1986a5d9" width="750px" align="center">

__การทำงานของ Test case#2__

<img src="https://github.com/opalInwza007x/TEST/assets/114739286/5ce64bf5-c8c7-41bd-8030-db378799a407" width="385px" align="center">

อันนี้ถนัดอธิบายตัวต่อตัวมากกว่า รอว่างๆเดี๋ยวมาเขียนให้ดูครับ ลายมือผมเละเกิน555

### 2.2 ตัวอย่างที่ 2 Paths in a grid

[source : OTOG - Fruit Fruit Fruit (ภาคโหด)](https://api.otog.in.th/problem/doc/290)

> กำหนดตารางมาให้ขนาด `n × m` โดยแต่ละช่องจะมีจำนวนเต็มใดๆ ให้หาผลรวมที่มากที่สุดเริ่มจากซ้ายบน `(0, 0)` ไปยังขวาล่าง `(n - 1, m - 1)` โดยที่สามารถเดินไปได้แค่ทิศขวากับล่างเท่านั้น

__Test Case#1__

กำหนดตารางขนาด 2 × 3

<img src="https://github.com/opalInwza007x/TEST/assets/114739286/93377df7-49bf-416c-a550-045a186dc036" width="385px" align="center">

- ในกรณีนี้ถ้าเราใช้ Greedy โดยการ BFS เลือกไปทางที่มี value มากที่สุดตลอด ก็ผ่านได้ครับ โดยจะเดินตามทางนี้เลย

<img src="https://github.com/opalInwza007x/TEST/assets/114739286/de654431-55d7-4c90-bc1f-60b67fe0fe49" width="385px" align="center">

- โดยผลรวมที่มากที่สุดคือ 5 + 7 + 4 + 9 = 25 นั่นเอง

__Test Case#2__

กำหนดตารางขนาด 3 × 3

<img src="https://github.com/opalInwza007x/TEST/assets/114739286/237b22c2-cac3-47e9-a72f-67710b1f6ec6" width="385px" align="center">

- ในกรณีนี้ถ้าเรา Greedy หรือ dijkstra เลือกตามทางมากสุดไปตลอด จะเดินตามทางนี้ครับ

<img src="https://github.com/opalInwza007x/TEST/assets/114739286/c8368d66-99c4-4194-8cb6-a45d1d2a8627" width="385px" align="center">

- ซึ่งผลรวมที่เราได้คือ 2 + 4 + 1 + 3 + 7 = 17 แต่ว่าในอีกเส้นทางนึง

<img src="https://github.com/opalInwza007x/TEST/assets/114739286/88a1a9f5-4bf0-4e3a-9025-2e17760c53fb" width="385px" align="center">

- ผลรวมเป็น 2 + -20 + 69 + -20 + 7 = 38 ซึ่งมากกว่าอย่างเห็นได้ชัด

__ขั้นที่ 1 อ่านโจทย์ให้เรียบร้อย เช็คว่าควรเก็บ state ไหนบ้าง__

ถ้าเราจะเก็บ state แค่ว่าอยู่ row หรือ col ไหนก็คงไม่ใช่ เพราะฉะนั้นเก็บทั้งคู่เลย

```c++
ll solve(ll x, ll y) {
    // process
}
```

__ขั้นที่ 2 คิด Base case เพื่อหยุดการ recursive__

ในโจทย์นี้ก็มีเคสหยุดคือ 

- เรา noclip หรือทะลุจุดที่สามารถเดินไปได้ อย่าเอามาคิดเด็ดขาด

- ถึงเป้าหมายแล้ว หรือก็คือมุมขวาล่างนั่นเอง

```c++
ll solve(ll x, ll y) {
    if (x > n - 1 || y > n - 1) {
        return -inf; // เนื่องจากเราหาค่ามาก จึงคืนค่าน้อยๆ เพื่อไม่ให้นำมาคิด
    }
    if (x == n - 1 && y == m - 1) {
        return arr[x][y]; // เดี๋ยวอธิบายด้านล่าง
    }
    // process
}
```

__ขั้นที่ 3 คิดว่าการ recursive แต่ละครั้ง เป็นแบบไหนได้บ้าง__

ในเคสนี้เราก็ต้องการทางที่เก็บ val ได้มากที่สุดจากการเดินทิศ __ขวา__ และ __ลง__

```c++
ll solve(ll x, ll y) {
    if (x > n - 1 || y > n - 1) {
        return -inf;
    }
    if (x == n - 1 && y == m - 1) {
        return arr[x][y]; // เดี๋ยวอธิบายด้านล่าง
    }
    ll path1 = solve(x + 1, y) + arr[x][y]; // เดินลงล่าง
    ll path2 = solve(x, y + 1) + arr[x][y]; // เดินทางขวา
    reuturn max(path1, path2); // เอาทางที่มีผลรวมมากที่สุด
}
```

ถามว่าทำไมพอถึงจุดขวาล่างแล้วไม่ได้ `return 0;` เพราะว่าถ้าดูตรง `path1` กับ `path2` ค่าที่บวกไปเรื่อยๆ จะไปถึงแค่ (n - 2, m - 1) หรือ (n - 1, m - 2) พอถึงจุด (n - 1, m - 1) ก็จะคืนค่าไปเลย เพราะฉะนั้นเราควรจะคืนค่า value ที่ (n - 1, m - 1) เพื่อให้ได้ผลบวกครบตั้งแต่ซ้ายบนถึงขวาล่าง

__ขั้นที่ 4 ใส่ memorization เพื่อลดการคิดซ้ำ__

```c++
ll solve(ll x, ll y) {
    if (x > n - 1 || y > m - 1) {
        return -inf;
    }
    if (x == n - 1 && y == m - 1) {
        return arr[x][y];
    }
    if (visited[x][y]) {
        return memo[x][y]; // เคยมาแล้ว
    }
    visited[x][y] = 1; // ถ้ายังไม่เคยมาก็มาแล้ว
    ll path1 = solve(x + 1, y) + arr[x][y];
    ll path2 = solve(x, y + 1) + arr[x][y];
    memo[x][y] = max(path1, path2); // จำค่าไว้
    reuturn memo[x][y];
}
```

คำตอบของเราจะเกิดจากการเรียก `solve(0, 0);`

__ขั้นเท่าไหร่ไม่รู้แต่ optimize แบบ coolๆ__

ถามว่าถ้าเกิดเราเดินจากจุดขวาล่างไปซ้ายบนแทน จะได้คำตอบเหมือนกันรึเปล่า ซึ่งจากการพิสูจน์โดยไม่ต้องใช้ binomial theorem ผสมกับ Persistent Segment Trees เราก็จะได้ว่า คำตอบเหมือนกันครับ โดยเราจะเรื่มที่จุดขวาล่างแล้วเดินได้แค่ทาง __ซ้าย__ และ __ขึ้น__ แทน

```c++
ll solve(ll x, ll y) {
    if (x < 0 || y < 0) {
        return -inf; // ทะลุขอบ
    }
    if (x == 0 && y == 0) {
        return arr[x][y];
    }
    if (visited[x][y]) {
        return memo[x][y];
    }
    visited[x][y] = 1;
    ll path1 = solve(x - 1, y) + arr[x][y]; // เดินขึ้นข้างบน
    ll path2 = solve(x, y - 1) + arr[x][y]; // เดินไปทางซ้าย
    reuturn memo[x][y] = max(path1, path2);
}
```

คำตอบของเราจะเกิดจากการเรียก `solve(n - 1, m - 1)` ซึ่งมันดีกว่าตรงที่เราไม่ต้องประกาศ `n` และ `m` เป็น global เพื่อที่จะเช็คว่าจุดที่อยู่ตอนนี้เลยขอบหรือถึงจุดหมายรึยัง โดยแบบนี้เราสามารถเช็คได้จากค่า index หรือก็คือ 0 ได้เลยนั่นเอง

ถ้าสรุปเป็นสมการ recursive ก็ได้ตามภาพเลยครับ

<img src="https://github.com/opalInwza007x/TEST/assets/114739286/e387ca62-5777-4bc5-bf70-93683349b868" width="750px" align="center">

### 2.3 ตัวอย่างที่ 3 Grid Paths

[source : CSES - Grid Paths](https://cses.fi/problemset/task/1638)

> กำหนดตารางมาให้ขนาด `n × m` โดยแต่ละช่องจะมีทางเดิน `.` และกำแพง `*` ต้องการหาจำนวนวิธีเดินทั้งหมดที่เริ่มจากซ้ายบน `(0, 0)` ไปยังขวาล่าง `(n - 1, m - 1)` โดยคำตอบอาจมีขนาดใหญ่ ให้ mod ด้วย `1e9 + 7`

__Test Case#1__

กำหนดตารางขนาด 4 × 3

<img src="https://github.com/opalInwza007x/TEST/assets/114739286/364591ad-fc83-452f-bf21-86a2c3933f64" width="385px" align="center">

- เราสามารถเดินได้ทั้งหมด 2 รูปแบบ ตามภาพด้านล่าง

<img src="https://github.com/opalInwza007x/TEST/assets/114739286/f80286b5-2fd7-4964-a83a-48499a5dc07c" width="385px" align="center">

<img src="https://github.com/opalInwza007x/TEST/assets/114739286/5768e97f-7ba7-4565-a245-91a61b1dfbbc" width="385px" align="center">

__ขั้นที่ 1 อ่านโจทย์ให้เรียบร้อย เช็คว่าควรเก็บ state ไหนบ้าง__

ถ้าเราจะเก็บ state แค่ว่าอยู่ row หรือ col ไหนก็คงไม่ใช่ เพราะฉะนั้นเก็บทั้งคู่เลย

```c++
ll solve(ll x, ll y) {
    // process
}
```

__ขั้นที่ 2 คิด Base case เพื่อหยุดการ recursive__

ในโจทย์นี้ก็มีเคสหยุดคือ 

- เรา noclip เข้ากำแพง หรือทะลุจุดที่สามารถเดินไปได้ ก็ถือว่าเป็นการเดินที่ผิดพลาด

- ถึงเป้าหมายแล้ว หรือก็คือมุมขวาล่างนั่นเอง

```c++
ll solve(ll x, ll y) {
    if (x > n - 1 || y > n - 1) {
        return 0; // เดินผิด วิธีนี้ไม่ถูกคิด
    }
    if (x == n - 1 && y == m - 1) {
        return 1; // เดินมาถูก ได้วิธีเดินอีก 1 วิธี
    }
    // process
}
```

__ขั้นที่ 3 คิดว่าการ recursive แต่ละครั้ง เป็นแบบไหนได้บ้าง__

ในเคสนี้เราก็ต้องการหาวฺิธีเดินทั้งหมดจากการเดินทิศ __ขวา__ และ __ลง__

```c++
ll solve(ll x, ll y) {
    if (x > n - 1 || y > n - 1) {
        return 0;
    }
    if (x == n - 1 && y == m - 1) {
        return 1;
    }
    ll path1 = solve(x + 1, y); // เดินลงล่าง
    ll path2 = solve(x, y + 1); // เดินทางขวา
    reuturn path1 + path2; // หาวิธีทั้ง 2 ทาง
}
```

__ขั้นที่ 4 ใส่ memorization เพื่อลดการคิดซ้ำ__

```c++
ll solve(ll x, ll y) {
    if (x > n - 1 || y > m - 1) {
        return 0;
    }
    if (x == n - 1 && y == m - 1) {
        return 1;
    }
    if (visited[x][y]) {
        return memo[x][y]; // เคยมาแล้ว
    }
    visited[x][y] = 1; // ถ้ายังไม่เคยมาก็มาแล้ว
    ll path1 = solve(x + 1, y);
    ll path2 = solve(x, y + 1);
    reuturn memo[x][y] = ((path1 % mod) + (path2 % mod)) % mod; // mod และจำค่าเอาไว้
}
```

คำตอบของเราจะเกิดจากการเรียก `solve(0, 0)`

__ขั้นเท่าไหร่ไม่รู้แต่ optimize แบบ coolๆ__

เราจะเรื่มที่จุดขวาล่างแล้วเดินได้แค่ทาง __ซ้าย__ และ __ขึ้น__ แทน

```c++
ll solve(ll x, ll y) {
    if (x < 0 || y < 0) {
        return 0;
    }
    if (x == 0 && y == 0) {
        return 1;
    }
    if (visited[x][y]) {
        return memo[x][y];
    }
    visited[x][y] = 1;
    ll path1 = solve(x - 1, y); // เดินขึ้นข้างบน
    ll path2 = solve(x, y - 1); // เดินไปทางซ้าย
    reuturn memo[x][y] = ((path1 % mod) + (path2 % mod)) % mod;
}
```

คำตอบของเราจะเกิดจากการเรียก `solve(n - 1, m - 1);` ซึ่งดีกว่าตรงที่เราไม่ต้องประกาศ `n` และ `m` เป็น global เพื่อที่จะเช็คว่าเลยขอบหรือถึงจุดหมายรึยัง โดยแบบนี้เราสามารถเช็คได้จากค่า index หรือก็คือ 0 ได้เลย

ถ้าสรุปเป็นสมการ recursive ก็ได้ตามภาพเลยครับ

<img src="https://github.com/opalInwza007x/TEST/assets/114739286/46d147ee-8cb6-40ea-8544-dacd0ee8ea94" width="750px" align="center">

### 3. Partitioning Problem

เป็นแนว DP ที่พบได้บ่อยใน TOI จะเป็นการเน้นไปที่การแบ่งช่วงให้ได้คำตอบที่ดีที่สุด

### 3.1 ตัวอย่างโจทย์ Partitioning TOI18_sausage

[source : programming.in.th - TOI18_Sausage](https://programming.in.th/tasks/toi18_sausage)

> มีไส้อั่วที่เป็นรูปทรงกลมเรียงต่อกันเป็นสายยาวทั้งหมด `n` ลูก แต่ละลูกมีค่าความอร่อยเป็นของตัวเอง เราสามารถเลือกกินไส้อั่วได้แค่ลำดับแรกของสาย และลำดับสุดท้ายของสายเท่านั้น แต่ละครั้งในการกินไส้อั่วทิพย์ ความอร่อยของไส้อั่วชิ้นที่เลือก $`D_x`$ กับความอร่อยของชิ้นปลายสายอีกด้านที่ไม่ได้กิน $`D_y`$ จะผสมผสานกันเกิดเป็นความอร่อยทิพย์ซึ่งมีค่าเท่ากับ $`|D_x - D_y|`$ โดยเราสามารถตัดสายไส้อั่วออกเป็นเส้นเล็ก ๆ ได้หลายเส้นก่อนจะลงมือกิน ให้หาผลรวมของความอร่อยในการกินไส้อั่วที่มีค่ามากที่สุด

ข้อนี้เหมือนเป็นโจทย์ 2 อันมารวมกัน

1. เราได้ไส้อั่วมาเส้นนึง หาวิธีกินให้ได้ผลรวมความอร่อยมากที่สุด
2. ลองแบ่งไส้อั่วหลาย ๆ แบบ แล้วเอาไส้อั่วที่แบ่งไปคิดใน `1.` หาวิธีแบ่งให้ได้ผลรวมความอร่อยมากที่สุด

เนื้องจาก `1.` ก็เป็นได้แค่โจทย์ DP ธรรมดา จึงขออธิบายแค่ `2.` ก็พอ

ครั้งแรกที่ได้อ่านคงจะสับสนว่าจะต้องแบ่งยังไงให้ได้ทุกแบบ เพราะฉะนั้นเรามาลองคิดดูว่าเราจะแบ่ง และกินทุกแบบได้ยังไง

<img src="https://github.com/opalInwza007x/TEST/assets/114739286/69fe51dc-c46d-4ff0-b706-0de2f102b62c" width="750px" align="center">

ในภาพมีไส้อั่ว 4 ลูก แต่ละลูกแทนด้วยสี เขียว เหลือง แดง และน้ำเงิน ตามลำดับ โดยไส้อั่วเส้นที่มีเส้นใต้สีแดงคือถูกกินแล้วจาก state ก่อนหน้า โดยเห็นได้ว้าแม้บางครั้งจะเหลือไส้อั่วแบบเดียวกัน แต่ลำดับการกินก็จะต่างกัน เราก็จะเก็บแบบที่กินแล้วได้คะแนนเยอะสุดไว้

ถ้าเราจะ implement ลงโค้ด ก็สามารถเขียนได้ตามด้านล่างเลย

```c++
ll solve(ll l, ll r) {
    if (l > r) {
        return 0;
    }
    ll most = -inf;
    for (int i = l; i <= r; i++) {
        most = max(most, eat(l, i) + solve(i + 1, r));
    }
    return most;
}
```

กำหนดให้ `eat()` คือ `1.` ไปเขียนเอาเอง โดยสามารถได้คำตอบจากการเรียก `solve(0, n - 1)` แต่เราเห็นว่าค่า `r` ไม่ได้ถูกเปลี่ยนแปลงเลย เราเลยสามารถลด state ได้อีกเหลือแค่

```c++
ll solve(ll l) {
    if (l == n) {
        return 0;
    }
    if (visited[x]) {
        return memo[x];
    }
    visited[x] = 1;
    ll most = -inf;
    for (int i = l; i < n; i++) {
        most = max(most, eat(l, i) + solve(i + 1, n));
    }
    return memo[x] = most;
}
```

โดยสามารถได้คำตอบจากการเรียก `solve(0);`

### 4. Bitmask with Dynamic Programming

### 4.1 ตัวอย่างโจทย์ Bitmask with DP

[source : OTOG - ไม่เลือกงาน ไม่ยากจน](https://api.otog.in.th/problem/doc/812)

__ปล. เราจะโฟกัสที่กรณี `n` <= 20 ถ้ามากกว่านั้นต้องใช้ Heuristic search เข้ามาช่วยละ__

> มีทั้งหมด `n` บริษัท แต่ละบริษัทมี `n` ตำแหน่ง แต่ละตำแหน่งในแต่ละบริษัทจะมีค่า pain เป็นของตัวเอง ให้หาผลรวมค่า pain ที่น้อยที่สุดถ้าเราต้องเข้าทำงานทุกบริษัท โดยห้ามอยู่ตำแหน่งเดียวกันกับบริษัทอื่น

__Test Case#1__

มีทั้งหมด 4 บริษัท โดยมีค่า pain ดังตาราง

<img src="https://github.com/opalInwza007x/TEST/assets/114739286/7a52a270-a1ea-4d68-b1eb-28e3effc0dcd" width="750px" align="center">

หนึ่งในการเลือกเข้าทำงานที่ผลรวมค่า pain น้อยที่สุด คือ 

<img src="https://github.com/opalInwza007x/TEST/assets/114739286/c3444d72-77ef-4025-ac52-863387ab1d29" width="750px" align="center">

__ขั้นที่ 1 อ่านโจทย์ให้เรียบร้อย เช็คว่าควรเก็บ state ไหนบ้าง__

หลายคนอาจจะคิดไม่ออกว่าเราจะเก็บว่าทำงานตำแหน่งนี้ไปแล้วยังไง ซึ่งผมเคยใช้ map เข้ามาช่วยก่อนครับ...

```c++
ll solve(ll pos, bool visited[]) {
    if (memo[pos][mp[visited]]) {
        return [pos][mp[visited]];
    }
    // โค้ดกากๆ
}
```

ซึ่งแน่นอนว่า memory ระเบิดแน่นอน แล้วเราจะทำยังไงล่ะครับ?

เราลองมองเลขเป็นฐาน 2 ที่จะมีแค่ 0 และ 1 ดูครับ เช่น

| เลขฐาน 10 | เลขฐาน 2 |
| :---: | :---: |
| 0 | ...00000 |
| 1 | ...00001 |
| 2 | ...00010 |
| 3 | ...00011 |
| 4 | ...00100 |
| 5 | ...00101 |
| 6 | ...00110 |
| 7 | ...00111 |

นี่มันสามารใช้แทน visited ได้เลยนี่นา!!!! ใช้แค่ variable type int ไม่ก็ ll ประหยัดเม็ม แถมยังใช้ง่ายอีกต่างหาก โดยความหมายตามนี้เลย

| เลขฐาน 10 | เลขฐาน 2 | ความหมาย |
| :---: | :---: | :---: |
| 0 | ...00000 | ยังไม่เคยทำงานตำแหน่งไหนเลย |
| 1 | ...00001 | เคยทำงานตำแหน่งที่ 1 แล้ว |
| 2 | ...00010 | เคยทำงานตำแหน่งที่ 2 แล้ว |
| 3 | ...00011 | เคยทำงานตำแหน่งที่ 1 และ 2 แล้ว |
| 4 | ...00100 | เคยทำงานตำแหน่งที่ 3 แล้ว |
| 5 | ...00101 | เคยทำงานตำแหน่งที่ 1 และ 3 แล้ว |
| 6 | ...00110 | เคยทำงานตำแหน่งที่ 2 และ 3 แล้ว |
| 7 | ...00111 | เคยทำงานตำแหน่งที่ 1, 2 และ 3 แล้ว |

```c++
ll solve(ll state) {
    // process
}
```

__ขั้นที่ 2 คิด Base case เพื่อหยุดการ recursive__

```c++
ll solve(ll state) {
    ll cnt = __builtin_popcount(state); // คำสั่งนับ bit ที่เป็น 1
    if (cnt == n) {
        return 0;
    }
    // process
}
```

ก็คือ ถ้ามี bit 1 ทั้งหมมด `n` อัน ก็คือทำงานครบทุกบริษัทแล้ว จบการทำงานได้ 

__ขั้นที่ 3 คิดว่าการ recursive แต่ละครั้ง เป็นแบบไหนได้บ้าง__

__ถ้ายังไม่รู้จัก bitwise Operators ลองไปอ่านก่อนครับ [Programiz - C++ Bitwise Operators](https://www.programiz.com/cpp-programming/bitwise-operators)__

```c++
ll solve(ll state) {
    ll cnt = __builtin_popcount(state);
    if (cnt == n) {
        return 0;
    }
    ll min_cost = inf;
    for (int i = 0; i < n; i++) { // วนทั้ง n ตำแหน่ง
        ll new_state = state | (1 << i);
        if (new_state == state) { // ถ้าเคยทำตำแหน่งนี้แล้ว ค่า new_state จะไม่เปลี่ยน
            continue;
        }
        min_cost = min(min_cost, pain[i][cnt] + solve(new_state));
    }
    return min_cost;
}
```

__ขั้นที่ 4 ใส่ memorization เพื่อลดการคิดซ้ำ__

```c++
ll solve(ll state) {
    ll cnt = __builtin_popcount(state);
    if (cnt == n) {
        return 0;
    }
    if (visited[state]) {
        return memo[state];
    }
    visited[state] = 1;
    ll min_cost = inf;
    for (int i = 0; i < n; i++) {
        ll new_state = state | (1 << i);
        if (new_state == state) {
            continue;
        }
        min_cost = min(min_cost, pain[i][cnt] + solve(new_state));
    }
    return memo[state] = min_cost;
}
```

โดยคำตอบได้จากการเรียก `solve(0);`
