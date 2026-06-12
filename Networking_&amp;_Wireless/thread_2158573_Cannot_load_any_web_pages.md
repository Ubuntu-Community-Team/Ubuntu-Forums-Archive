---
title: "Cannot load any web pages"
date: 2013-06-29
forum: Networking &amp; Wireless
---

### Post by ubowm on 2013-06-29
Hello everyone,
I'm a newbie when it comes to troubleshooting network problems in Ubuntu.
My current issue is not connecting and loading web pages. I have only been able to use the ping command successfully with google.com and other sites.
I have searched these forums and elsewhere, but haven't had any luck with solving the issue.

Also, this issue started immediately after Ubuntu updated itself. I'm unsure what all was updated, but it was ~150Mb update recently.
If someone could help me out with this, I would greatly appreciate it.

---

### Post by sanderj on 2013-06-29
What's the output of:

```
host www.google.com
wget www.google.com
mtr -nrc2 8.8.8.8
```

Post the output here

---

### Post by ubowm on 2013-06-29
Had to copy/paste this from a text file. Sorry for any formatting issues.

```
@ub01:~$ host [www.google.comwww.google.com]("http://www.google.comwww.google.com") has address 74.125.239.116
[www.google.com]("http://www.google.com") has address 74.125.239.112
[www.google.com]("http://www.google.com") has address 74.125.239.113
[www.google.com]("http://www.google.com") has address 74.125.239.114
[www.google.com]("http://www.google.com") has address 74.125.239.115
[www.google.com]("http://www.google.com") has IPv6 address 2607:f8b0:4005:800::1010
```

```
@ub01:~$ wget [www.google.com--2013-06-29]("http://www.google.com--2013-06-29") 15:59:17--  [http://www.google.com/](http://www.google.com/)
Resolving [www.google.com]("http://www.google.com") ([www.google.com]("http://www.google.com"))... 74.125.239.113, 74.125.239.114, 74.125.239.115, ...
Connecting to [www.google.com]("http://www.google.com") ([www.google.com)|74.125.239.113|:80]("http://www.google.com)|74.125.239.113|:80")... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: &#8216;index.html&#8217;
```

```
@ub01:~$ mtr -nrc2 8.8.8.8HOST: ub01                        Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 192.168.1.1                0.0%     2    2.7   3.1   2.7   3.6   0.6
  2.|-- 66.122.73.254              0.0%     2   10.7  11.2  10.7  11.7   0.8
  3.|-- 216.102.182.131            0.0%     2   11.5 182.0  11.5 352.5 241.1
  4.|-- 12.83.49.170               0.0%     2   10.9 132.3  10.9 253.8 171.7
  5.|-- 12.122.136.181             0.0%     2   17.7  89.5  17.7 161.3 101.5
  6.|-- ???                       100.0     2    0.0   0.0   0.0   0.0   0.0
  7.|-- 216.239.49.170             0.0%     2   97.2  57.5  17.7  97.2  56.2
  8.|-- 209.85.250.63              0.0%     2   34.8  28.0  21.2  34.8   9.7
    |  `|-- 209.85.250.66
  9.|-- 216.239.49.198             0.0%     2   42.7 193.1  42.7 343.4 212.6
    |  `|-- 72.14.232.63
 10.|-- 72.14.233.200              0.0%     2  115.6 178.3 115.6 240.9  88.6
 11.|-- 216.239.48.167             0.0%     2   35.8  90.4  35.8 145.1  77.3
    |  `|-- 216.239.48.165
 12.|-- ???                       100.0     2    0.0   0.0   0.0   0.0   0.0
 13.|-- 8.8.8.8                   50.0%     2   38.6  38.6  38.6  38.6   0.0
```

---

### Post by sanderj on 2013-06-30
That looks good. 

Can you explain what doesn't work in your webbrowser? Which webbrowser? What if yo use another webbrowser?

---

### Post by ubowm on 2013-06-30
Thank you for your help. I have managed to resolve the issue by setting the MTU to 1492 from Automatic.
I'm unsure why this worked, but everything seems to be working properly now.

---

