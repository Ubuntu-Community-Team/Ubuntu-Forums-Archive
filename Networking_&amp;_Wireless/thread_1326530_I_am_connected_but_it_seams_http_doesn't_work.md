---
title: "I am connected but it seams http doesn't work"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by alisdair on 2009-11-14
Hi i've just upgraded to Karmic but the internet doesn't work. I am connected, i can ping servers and even my skype works as well but i cannot connect to any page. Please do you have some ideas? Which lists should i post to help you help me? Sry for eng but i hurried :) Thanks for ideas

---

### Post by driftertx on 2009-11-14
do the following from a command line:

[email]mike@hellfire:~/.ssh[/email]$ wget **[www.yahoo.com](www.yahoo.com)**
[I]--2009-11-14 13:24:04--  [http://www.yahoo.com/](http://www.yahoo.com/)
Resolving [www.yahoo.com](www.yahoo.com)... 69.147.76.15
Connecting to [www.yahoo.com|69.147.76.15|:80](www.yahoo.com|69.147.76.15|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://m.www.yahoo.com/](http://m.www.yahoo.com/) [following]
--2009-11-14 13:24:05--  [http://m.www.yahoo.com/](http://m.www.yahoo.com/)
Resolving m.[www.yahoo.com](www.yahoo.com)... 67.195.160.76, 69.147.125.65
Connecting to m.[www.yahoo.com|67.195.160.76|:80](www.yahoo.com|67.195.160.76|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html'

    [  <=>                                            ] 119,311      324K/s   in 0.4s    

2009-11-14 13:24:05 (324 KB/s) - `index.html' saved [119311][/I]


this is what you should see if it's working okay, if it works then it means something is misconfigured with your proxy settings within firefox (making the assumption by 'sites don't work' you mean web browsing). Remove any proxy settings from **Edit/Preferences/Network Button/Settings**

---

### Post by alisdair on 2009-11-14
I should add this problem have all connection (ethernet, usb, wifi) in common. There is no problem in proxy, i tried to use opera too. :) I try to do [driftertx]("http://ubuntuforums.org/member.php?u=485484") wrote :)

---

### Post by alisdair on 2009-11-14
> **driftertx said:**
> do the following from a command line:

[EMAIL="mike@hellfire:%7E/.ssh"]mike@hellfire:~/.ssh[/EMAIL]$ wget **[www.yahoo.com]("http://www.yahoo.com")**
[I]--2009-11-14 13:24:04--  [http://www.yahoo.com/](http://www.yahoo.com/)
Resolving [www.yahoo.com]("http://www.yahoo.com")... 69.147.76.15
Connecting to [www.yahoo.com|69.147.76.15|:80]("http://www.yahoo.com%7C69.147.76.15%7C:80")... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://m.www.yahoo.com/](http://m.www.yahoo.com/) [following]
--2009-11-14 13:24:05--  [http://m.www.yahoo.com/](http://m.www.yahoo.com/)
Resolving m.[www.yahoo.com]("http://www.yahoo.com")... 67.195.160.76, 69.147.125.65
Connecting to m.[www.yahoo.com|67.195.160.76|:80]("http://www.yahoo.com%7C67.195.160.76%7C:80")... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html'

    [  <=>                                            ] 119,311      324K/s   in 0.4s    

2009-11-14 13:24:05 (324 KB/s) - `index.html' saved [119311][/I]


this is what you should see if it's working okay, if it works then it means something is misconfigured with your proxy settings within firefox (making the assumption by 'sites don't work' you mean web browsing). Remove any proxy settings from **Edit/Preferences/Network Button/Settings**

It worked. It was connected in the same way, only some other ip.

---

### Post by driftertx on 2009-11-14
Copy and paste what response you get from wget and paste it here, also run install and run this:

also do from terminal: **'sudo apt-get install traceroute'**

then do you: **'traceroute [www.yahoo.com](www.yahoo.com)'**


From the looks of it, if DNS works and traceroute works you either have something intercepting your port 80/HTTP traffic upstream or firewall issue.

---

### Post by alisdair on 2009-11-14
So i tried to install traceroute, but it couldn't connect to the server (i tried more servers) so i download it at sisters computer, installed and here is the list. In addition i found out that [www.ubuntu.com](www.ubuntu.com) and subpages works for me, but for one while it didn't and worked only ubuntu.cz So i am bit confused. :( 

```
    traceroute to www.yahoo.com (1.0.0.0), 30 hops max, 60 byte packets
     1  * * *
     2  lo0-bras1-ost1-plus.ctc.prg.vol.cz (88.146.111.22)  17.162 ms  21.814 ms  26.866 ms
     3  pe1-ost1-plus.ctc.prg.vol.cz (88.146.109.97)  32.444 ms  36.830 ms  41.866 ms
     4  ge1-2.bb1.prg.vol.cz (195.122.209.37)  52.914 ms  57.693 ms  62.995 ms
     5  ge1 (195.122.209.37)  67.559 ms  72.867 ms  77.386 ms
     6  * ge4-2.tr3.prg.vol.cz (212.20.123.36)  70.762 ms *
     7  * * *
     8  * * *
     9  * * *
    10  * * *
    11  * * *
    12  * * *
    13  * * *
    14  * * *
    15  * * *
    16  * * *
    17  * * *
    18  * * *
    19  * * *
    20  * * *
    21  * * *
    22  * * *
    23  * * *
    24  * * *
    25  * * *
    26  * * *
    27  * * *
    28  * * *
    29  * * *
    30  * * *
    
```

---

### Post by driftertx on 2009-11-14
sounds like your provider is having problems with DNS. I can tell you that 1.0.0.0 is not the IP address for Yahoo.com! Try using opendns servers, 208.67.222.222 and 208.67.220.220

---

### Post by alisdair on 2009-11-14
> **driftertx said:**
> sounds like your provider is having problems with DNS. I can tell you that 1.0.0.0 is not the IP address for Yahoo.com! Try using opendns servers, 208.67.222.222 and 208.67.220.220

sorry i dont understand, what are these servers for?

ED: or how should i use it?

---

### Post by alisdair on 2009-11-14
I tried more servers, but i found only one which shows real ip. 

```
    traceroute to www.seznam.cz (77.75.72.3), 30 hops max, 60 byte packets
     1  * * *
     2  lo0 (88.146.111.22)  14.059 ms  18.800 ms  23.861 ms
     3  pe1 (88.146.109.97)  28.756 ms  33.735 ms  38.994 ms
     4  ge1 (195.122.209.37)  49.645 ms  54.818 ms  59.597 ms
     5  ge1 (195.122.209.37)  64.583 ms  69.584 ms  74.671 ms
     6  te2-1.tr1.prg2.vol.cz (212.20.124.60)  79.810 ms  70.814 ms  67.564 ms
     7  * * *
     8  * * *
     9  * * *
    10  * * *
    11  * * *
    12  * * *
    13  * * *
    14  * * *
    15  * * *
    16  * * *
    17  * * *
    18  * * *
    19  * * *
    20  * * *
    21  * * *
    22  nix.seznam.cz (194.50.100.195)  65.027 ms !X * *
    ondra@laptop-1:~$ traceroute [www.fnx.cz]("http://www.fnx.cz/")
     
   
  
```

---

### Post by alisdair on 2009-11-14
I changed DNS servers and it works.

---

