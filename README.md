# assignment2-Madhur
# i am interested in coding.
# Pulugurtha Vinay Madhur
###### Venice

I like the food especially pasta and its also known as city of canals. That's what i like about the city.
It's a city build on water also know as **The floating city** and the city rests on **118 islands** separated by 150 canals.

---
# Direction from Maryville to Las Vegas
1.First book a cab from your location to Kansas International Airport.
  1. After reaching airport collect the boarding pass to from your respective flight desk.
  2. Then go through the airport checking and then board your respective fligh. 

# Items to carry for the trip
* Clothes
    * Trousers(if summer)
    * T-Shirts
    * Shades   
* Skincare
    * Sun Cream
    * Body lotion
* DSLR camera
* Snacks
* Shoes

[link](https://github.com/pvinaymadhur/assignment2-Madhur/blob/main/AboutMe.md)

---

# Table Creation

The below table recommends the food and drinks i like the most.Changes and flavours may vary from country to country.

| Food/Drinks  |     location  |   Price    |
| ----         |     -----     |   ---:     |
| Choco fudge  |   Starbucks   |   $4.90    |
| Cheese Cake  |   Starbucks   |   $10.45   |
| Butter Bites |   Starbucks   |   $12.33   |
| latte mocha  |   Starbucks   |   $15.98   |

---

# Best life changing quotes by great people

> "When something is important enough, you do it even if the odds are not in your favor."
>       -by *Elon Musk*.
>
> "When you do not know what to choose, show total involvement in everything."
>       -by *SadhGuru*.

---

# Dynamic Programming,Linear Algebra and Numerical Methods

> Dynamic Programming -  A DP is an algorithmic technique which is usually based on a recurrent formula and one (or some) starting states. A sub-solution of the problem is constructed from previously found ones. DP solutions have a polynomial complexity which assures a much faster running time than other techniques like backtracking, brute-force etc.


```
int m, n;
vector<long long> dp_before(n), dp_cur(n);

long long C(int i, int j);

// compute dp_cur[l], ... dp_cur[r] (inclusive)
void compute(int l, int r, int optl, int optr) {
    if (l > r)
        return;

    int mid = (l + r) >> 1;
    pair<long long, int> best = {LLONG_MAX, -1};

    for (int k = optl; k <= min(mid, optr); k++) {
        best = min(best, {(k ? dp_before[k - 1] : 0) + C(k, mid), k});
    }

    dp_cur[mid] = best.first;
    int opt = best.second;

    compute(l, mid - 1, optl, opt);
    compute(mid + 1, r, opt, optr);
}

int solve() {
    for (int i = 0; i < n; i++)
        dp_before[i] = C(0, i);

    for (int i = 1; i < m; i++) {
        compute(0, n - 1, 0, n - 1);
        dp_before = dp_cur;
    }

    return dp_before[n - 1];
}
```
Source Link For Dynamic Programming - <http://www.topcoder.com/thrive/articles/Dynamic%20Programming:%20From%20Novice%20to%20Advanced>

> Linear Algebra - Linear algebra, mathematical discipline that deals with vectors and matrices and, more generally, with vector spaces and linear transformations. Unlike other parts of mathematics that are frequently invigorated by new ideas and unsolved problems, linear algebra is very well understood. Its value lies in its many applications, from mathematical physics to modern algebra and coding theory.
```
const double EPS = 1e-9;
const int INF = 2; // it doesn't actually have to be infinity or a big number

int gauss (vector < vector<double> > a, vector<double> & ans) {
    int n = (int) a.size();
    int m = (int) a[0].size() - 1;

    vector<int> where (m, -1);
    for (int col=0, row=0; col<m && row<n; ++col) {
        int sel = row;
        for (int i=row; i<n; ++i)
            if (abs (a[i][col]) > abs (a[sel][col]))
                sel = i;
        if (abs (a[sel][col]) < EPS)
            continue;
        for (int i=col; i<=m; ++i)
            swap (a[sel][i], a[row][i]);
        where[col] = row;

        for (int i=0; i<n; ++i)
            if (i != row) {
                double c = a[i][col] / a[row][col];
                for (int j=col; j<=m; ++j)
                    a[i][j] -= a[row][j] * c;
            }
        ++row;
    }

    ans.assign (m, 0);
    for (int i=0; i<m; ++i)
        if (where[i] != -1)
            ans[i] = a[where[i]][m] / a[where[i]][i];
    for (int i=0; i<n; ++i) {
        double sum = 0;
        for (int j=0; j<m; ++j)
            sum += ans[j] * a[i][j];
        if (abs (sum - a[i][m]) > EPS)
            return 0;
    }

    for (int i=0; i<m; ++i)
        if (where[i] == -1)
            return INF;
    return 1;
}
```
Source Link For Linear Algebra - <https://www.britannica.com/science/linear-algebra>

> Numerical Methods - In numerical analysis, a numerical method is a mathematical tool designed to solve numerical problems. The implementation of a numerical method with an appropriate convergence check in a programming language is called a numerical algorithm.
```
double ternary_search(double l, double r) {
    double eps = 1e-9;              //set the error limit here
    while (r - l > eps) {
        double m1 = l + (r - l) / 3;
        double m2 = r - (r - l) / 3;
        double f1 = f(m1);      //evaluates the function at m1
        double f2 = f(m2);      //evaluates the function at m2
        if (f1 < f2)
            l = m1;
        else
            r = m2;
    }
    return f(l);                    //return the maximum of f(x) in [l, r]
}
```
Source Link For Numerical Method - <https://en.wikipedia.org/wiki/Numerical_method>

