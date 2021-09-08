# assignment2-naidu

# Sujith Reddy Naidu

### Hyderabad

**Hyderabad is situated at the Deccan Plateau, 500 meters above the sea level**.**Hyderabad is famous for dhum biryani.**
Hyderabad was found on the banks of Musi river in 1591. Today that area is known as old city where Mecca Masjid and Hussain Sagar Lake exist. The area has many official buildings and that area is very old.From the recent time, **Hyderabad has been merged with Secunderabad.**

---

# Directions From Maryville To Orlando

1. first of all  go to kansas airport from maryville.
2. Now travel to ft.lauderdale from kansas through aeroplane.
    1. ft.lauderdale is the only nearest airport from orlando.
    2. Take a car from enterprise for travelling purpose. 
3. Now navigate to motel you booked in orlando through car.

# Carryon Items List To That Place

* Camera
* Jacket
* Flip flops
* Bagpack
* Clothes
---

**[Info About Myself](AboutMe.md)**

---

# Places I Like The Most

xxxx

| Item  | Location  | Cost | 
|---|---|---|
|Burger   | Chickfill A  | $7.99  |   
|  Pizza | Dominos  | $15.99  |   
|  Dosa | Ramki Bandi  | $7.95  |  
| Towa Idli  |  Krupa | $4.55  |

***

# Pithy Quotes

>Imitation is suicide. – *Ralph Waldo Emerson*

>Flatter yourself critically. – *Willis Goth Regier*

---

# Convex Hull construction using Graham's Scan Algorithm

Graham's scan is a method of finding the convex hull of a finite set of points in the plane with time complexity O(n log n). It is named after Ronald Graham, who published the original algorithm in 1972.[1] The algorithm finds all vertices of the convex hull ordered along its boundary. It uses a stack to detect and remove concavities in the boundary efficiently.

Link: <https://en.wikipedia.org/wiki/Graham_scan>

```
struct pt {
    double x, y;
};

bool cmp(pt a, pt b) {
    return a.x < b.x || (a.x == b.x && a.y < b.y);
}

bool cw(pt a, pt b, pt c) {
    return a.x*(b.y-c.y)+b.x*(c.y-a.y)+c.x*(a.y-b.y) < 0;
}

bool ccw(pt a, pt b, pt c) {
    return a.x*(b.y-c.y)+b.x*(c.y-a.y)+c.x*(a.y-b.y) > 0;
}

void convex_hull(vector<pt>& a) {
    if (a.size() == 1)
        return;

    sort(a.begin(), a.end(), &cmp);
    pt p1 = a[0], p2 = a.back();
    vector<pt> up, down;
    up.push_back(p1);
    down.push_back(p1);
    for (int i = 1; i < (int)a.size(); i++) {
        if (i == a.size() - 1 || cw(p1, a[i], p2)) {
            while (up.size() >= 2 && !cw(up[up.size()-2], up[up.size()-1], a[i]))
                up.pop_back();
            up.push_back(a[i]);
        }
        if (i == a.size() - 1 || ccw(p1, a[i], p2)) {
            while(down.size() >= 2 && !ccw(down[down.size()-2], down[down.size()-1], a[i]))
                down.pop_back();
            down.push_back(a[i]);
        }
    }

    a.clear();
    for (int i = 0; i < (int)up.size(); i++)
        a.push_back(up[i]);
    for (int i = down.size() - 2; i > 0; i--)
        a.push_back(down[i]);
}
```
Link: <https://cp-algorithms.com/geometry/grahams-scan-convex-hull.htm>

