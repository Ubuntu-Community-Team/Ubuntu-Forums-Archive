---
title: "Ubuntu 10.10 - Wired and Wireless not working in Lenevo G580"
date: 2012-08-10
forum: Networking &amp; Wireless
---

### Post by itsjvivek on 2012-08-10
All:

I am not a Ubuntu expert. I just bought Lenovo G580 yesterday and installed Ubuntu 10.10.

Both wired and wireless is not working. The driver seems to be Atheros. I did try searching the forums and tried installing compact driver.But no success.

Can anyone please help me out.

---

### Post by seshdroid on 2012-08-10
Go To Lenovo's website and download the drivers for Linux. You should be sorted out by that.

Else, remaining in the same website identify the wireless card  manufacturer and product code. Then go to the vendors website and download the drivers for Linux from there.

---

### Post by mörgæs on 2012-08-10
Downloading drivers from some web site is a bad Windows habit. There is (almost) always a better solution.

First: 10.10 is unsupported. Best is to begin with a fresh install of 12.04. Please post again if you still have the problem.

---

### Post by itsjvivek on 2012-08-10
Sure.Let my install 12.04 and try.

Will keep posted on this thread

---

### Post by itsjvivek on 2012-08-10
Just finished installing Ubuntu 12.04.Still no luck with wired and wireless

---

### Post by mörgæs on 2012-08-12
Please run the command 

```
sudo lshw > lshw.txt
```

and post the lshw.txt file.

---

