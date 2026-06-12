---
title: "The server is taking too long to respond"
date: 2011-01-26
forum: Networking &amp; Wireless
---

### Post by amsterdamharu on 2011-01-26
My friend here in China needs to use the following site a lot:
[http://www.internaxx.lu/](http://www.internaxx.lu/)
But sometimes for hours on end he will get a message "The server at ... is taking too long to respond".

I've checked the site from my account (also in China) and see that the page loads very slowly, it's not blocked or I'll get a "connection reset by host".

I wonder what can be done about it since it's really important to him that it works immediately and not be unavailable for hours. Family in Europe say they have no problem reaching the site so it must be something geograpical.

I ran the following trace but can't make heads or tails of it:
```
me@desk:~$ sudo traceroute internaxx.lu -q 10 -n
traceroute to internaxx.lu (195.46.238.195), 30 hops max, 60 byte packets
 1  my.ip.I.guess  25.015 ms  25.575 ms  25.563 ms  35.112 ms  35.108 ms  35.657 ms  42.978 ms  43.392 ms  43.776 ms  53.513 ms
 2  218.77.143.41  36.545 ms  39.437 ms  42.370 ms  45.125 ms  47.982 ms  50.887 ms  28.960 ms  30.892 ms  33.805 ms  57.710 ms
 3  218.77.143.57  69.723 ms  72.343 ms  74.301 ms  74.621 ms  73.720 ms  76.512 ms  78.220 ms  81.181 ms  82.611 ms  82.494 ms
 4  202.97.33.126  200.116 ms  199.034 ms  201.515 ms  201.811 ms  202.378 ms  172.322 ms  163.486 ms  163.501 ms  163.387 ms  162.168 ms
 5  202.97.60.158  210.870 ms  213.378 ms  214.444 ms  213.424 ms  213.964 ms  213.531 ms  120.276 ms  120.922 ms  120.906 ms  120.930 ms
 6  202.97.49.106  278.857 ms  278.779 ms  278.774 ms  277.958 ms  279.225 ms  279.117 ms  282.544 ms  280.396 ms  278.838 ms  279.180 ms
 7  202.97.50.54  278.719 ms  279.061 ms  279.209 ms  278.840 ms  279.268 ms  278.480 ms  277.041 ms  287.090 ms  286.876 ms  285.499 ms
 8  218.30.54.114  315.194 ms  313.159 ms  336.051 ms  336.020 ms  334.720 ms  332.404 ms  329.927 ms  327.376 ms  300.021 ms  298.343 ms
 9  64.215.80.102  667.982 ms  664.814 ms  662.957 ms *  662.052 ms  662.427 ms  662.923 ms  665.797 ms  671.532 ms  671.722 ms
10  213.166.61.197  471.037 ms  471.181 ms  471.154 ms  471.460 ms  472.206 ms  471.198 ms  458.431 ms  460.259 ms  448.526 ms  450.464 ms
11  213.166.61.66  658.277 ms * *  666.519 ms *  649.877 ms  650.429 ms  657.384 ms  659.051 ms  650.931 ms
12  194.154.192.141  658.008 ms  648.778 ms  649.434 ms  649.742 ms  649.489 ms  653.110 ms  653.796 ms  653.430 ms  652.988 ms  651.888 ms
13  195.46.232.134  667.812 ms !X  661.071 ms !X * * * * * * * *
```Could the 600+ time it takes in some hubs cause the timeout? The *** at the end means it takes to long or does the server not like to be pinged?

A ping to there doesn't really work here either:
```
me@desk:~$ ping internaxx.lu
PING internaxx.lu (195.46.238.195) 56(84) bytes of data.
From 195.46.232.134 icmp_seq=1 Packet filtered
From 195.46.232.134 icmp_seq=2 Packet filtered
From 195.46.232.134 icmp_seq=3 Packet filtered
```Thanks for reading my post, if you have time could you run the traceroute command and see if it's any quicker in your location. I am in China.

---

### Post by Antarctica32 on 2011-01-26
No faster here in eastern U.S.
sorry
While reading your post I noticed that you openly displayed your IP address. I advise you take this off, as a black hat could trace your IP and find your location very easily.

---

### Post by amsterdamharu on 2011-01-26
Antarctica, thank you for telling me. I guess that was a bit careless of me.

Changed it now.

Too bad I can't pinpoint the problem here, if it's the provider at least my friend has reasonable complaints but I am not technical enough to say it is or isn't.

He will try a proxy later and see if it's some Chinese dns/firewall that messes it up but at the moment it's working for him.

---

### Post by amsterdamharu on 2011-01-27
bump:

Last try to see if anyone has a briliant idea to get the page loaded and if all fails to see what causes it.

I will have him using a proxy this friday to see if/when the connection fails it will work through proxy. That would indicate the problem lies with the great (fire)Wall or badly configured DNS.

---

