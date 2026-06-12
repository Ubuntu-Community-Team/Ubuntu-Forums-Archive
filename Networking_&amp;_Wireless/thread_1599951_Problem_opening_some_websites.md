---
title: "Problem opening some websites"
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by albincepa on 2010-10-18
I am new to ubuntu 10.10
I am now unable to retrieve some websites like [http://kvpy.org.in/](http://kvpy.org.in/) , while it can be easy retrieved from other operation system.
I have also tried firefox3.6 and chromium web browser:confused::confused::confused:

---

### Post by Lazaruss on 2010-10-18
Do you get any error messages (3 digit number codes)

---

### Post by albincepa on 2010-10-18
> **Lazaruss said:**
> Do you get any error messages (3 digit number codes)
i am not getting any error codes...
it shows the title name in the title bar but fails to display the page

---

### Post by Lazaruss on 2010-10-18
totally blank page, no loading icons, progress bars?

---

### Post by albincepa on 2010-10-18
> **Lazaruss said:**
> totally blank page, no loading icons, progress bars?
in the status bar it just says "waiting for www.kvpy.org.in" and i am having a blank page .

---

### Post by albincepa on 2010-10-18
> **albincepa said:**
> in the status bar it just says "waiting for www.kvpy.org.in" and i am having a blank page .
but i still can access the same using other proxy sites while in ubuntu itself

---

### Post by Lazaruss on 2010-10-18
can you run
```
sudo apt-get install traceroute
```
and then
```
traceroute www.kvpy.org.in
```
and post the output

---

### Post by cariboo on 2010-10-18
This isn't a Cafe question, moved to Networking and Wireless

---

### Post by albincepa on 2010-10-19
> **Lazaruss said:**
> can you run
```
sudo apt-get install traceroute
```
and then
```
traceroute www.kvpy.org.in
```
and post the output
here is the output
traceroute [www.kvpy.org.in](www.kvpy.org.in)
traceroute to [www.kvpy.org.in](www.kvpy.org.in) (184.73.179.124), 30 hops max, 60 byte packets
 1  117.204.112.1 (117.204.112.1)  25.792 ms  27.705 ms  31.681 ms
 2  218.248.173.118 (218.248.173.118)  33.647 ms  35.590 ms  39.554 ms
 3  59.163.206.157.static.chennai.vsnl.net.in (59.163.206.157)  75.574 ms  77.525 ms  79.459 ms
 4  172.31.4.93 (172.31.4.93)  89.465 ms  91.430 ms  93.369 ms
 5  172.31.4.93 (172.31.4.93)  97.368 ms  99.337 ms  101.272 ms
 6  Vlan512.icore1.SVW-Singapore.as6453.net (116.0.71.25)  173.240 ms  133.103 ms  145.812 ms
 7  if-11-0-0-1920.core2.S9R-Singapore.as6453.net (209.58.96.145)  179.810 ms  183.814 ms  185.697 ms
 8  if-14-0-0-39.core1.S9R-Singapore.as6453.net (209.58.82.189)  139.681 ms  143.686 ms if-3-1-0.mcore3.PDI-PaloAlto.as6453.net (216.6.29.125)  483.654 ms
 9  if-10-0-0.core2.S9R-Singapore.as6453.net (209.58.82.46)  179.613 ms  183.623 ms  185.535 ms
10  ix-2-0.icore1.PDI-PaloAlto.as6453.net (209.58.17.14)  347.505 ms if-3-1-0.mcore3.PDI-PaloAlto.as6453.net (216.6.29.125)  485.467 ms  487.400 ms
11  dca-edge-18.inet.qwest.net (67.14.36.6)  349.376 ms * Vlan1144.icore1.PDI-PaloAlto.as6453.net (216.6.29.102)  361.278 ms
12  * * *
13  dca-edge-18.inet.qwest.net (67.14.36.6)  317.840 ms  319.735 ms  317.805 ms
14  72.21.222.139 (72.21.222.139)  321.760 ms * *
15  72.21.199.34 (72.21.199.34)  325.707 ms  327.634 ms *
16  * * 72.21.222.139 (72.21.222.139)  341.522 ms
17  * * *
18  * * *
19  * * *
20  ec2-184-73-179-124.compute-1.amazonaws.com (184.73.179.124)  332.813 ms  334.750 ms  334.728 ms

---

### Post by Lazaruss on 2010-10-19
ok, i'm not sure whats going on - given traceroute reaches the server...

Couple of things to try

delete cookies and cache - try Ctrl + F5 simultaneously, else Tools > Clear Recent History - Expand details, only tick cookies, cache and site preferences

[www.kvpy.org.in/main](www.kvpy.org.in/main) - i get automatically redirected to this

do either of these have an effect?

---

### Post by albincepa on 2010-10-22
> **Lazaruss said:**
> ok, i'm not sure whats going on - given traceroute reaches the server...

Couple of things to try

delete cookies and cache - try Ctrl + F5 simultaneously, else Tools > Clear Recent History - Expand details, only tick cookies, cache and site preferences

[www.kvpy.org.in/main](www.kvpy.org.in/main) - i get automatically redirected to this

do either of these have an effect?
thanx for your help [Lazaruss]("http://ubuntuforums.org/member.php?u=997173") it really worked out for me
Thanx once again...............

---

### Post by Rushyang on 2010-10-24
> **albincepa said:**
> thanx for your help [Lazaruss]("http://ubuntuforums.org/member.php?u=997173") it really worked out for me
Thanx once again...............

Hey I have the same problem.. and a solution which worked for you.. Doesn't work for me.. Please help! 

I'm not able to open, YouTube, Wikipedia, Wooledge, Some github reference sites, gravatar etc!! Please Help!

So far, I have tried..
1) Disabling/Enabling IPv6 
2) Trying different browser.

Note: Those sites are opening in my other OS: Win 7 flawlessly..

---

### Post by Rushyang on 2010-10-24
Here is my traceroute of [www.youtube.com](www.youtube.com)

> rushyang@Maverick_Meerkat: ~ $ traceroute [www.youtube.com](www.youtube.com)
traceroute to [www.youtube.com](www.youtube.com) (209.85.231.91), 30 hops max, 60 byte packets
 1  117.198.192.1 (117.198.192.1)  37.575 ms  41.530 ms  43.505 ms
 2  218.248.169.230 (218.248.169.230)  47.486 ms  49.462 ms  51.438 ms
 3  115.113.128.17.static-mumbai.vsnl.net.in (115.113.128.17)  61.415 ms  63.402 ms  67.372 ms
 4  59.163.25.242.static.vsnl.net.in (59.163.25.242)  69.352 ms  69.333 ms  71.380 ms
 5  121.240.0.10.static-Mumbai.vsnl.net.in (121.240.0.10)  77.279 ms  79.262 ms  81.237 ms
 6  216.239.43.214 (216.239.43.214)  83.215 ms  43.363 ms  57.580 ms
 7  72.14.232.100 (72.14.232.100)  79.544 ms  81.615 ms  85.496 ms
 8  72.14.238.90 (72.14.238.90)  89.476 ms  89.458 ms  103.426 ms
 9  maa03s01-in-f91.1e100.net (209.85.231.91)  107.404 ms  111.389 ms  111.359 ms



Traceroute of wooledge...

> traceroute to wooledge.org (209.142.155.49), 30 hops max, 60 byte packets
 1  117.198.192.1 (117.198.192.1)  37.585 ms  41.551 ms  43.528 ms
 2  218.248.169.234 (218.248.169.234)  47.502 ms  51.489 ms  51.475 ms
 3  121.244.68.77.static-lvsb.vsnl.net.in (121.244.68.77)  61.455 ms  65.430 ms  67.418 ms
 4  59.163.16.54.static.vsnl.net.in (59.163.16.54)  273.427 ms  273.565 ms  273.556 ms
 5  59.163.16.54.static.vsnl.net.in (59.163.16.54)  273.546 ms *  275.349 ms
 6  if-1-0-0-101.core1.CFO-Chennai.as6453.net (116.0.79.9)  111.305 ms  71.566 ms  71.800 ms
 7  if-14-0-0.core2.CFO-Chennai.as6453.net (116.0.79.14)  75.851 ms  81.840 ms  83.825 ms
 8  if-4-0-0.core2.S9R-Singapore.as6453.net (116.0.84.22)  113.869 ms  117.773 ms  121.743 ms
 9  if-1-1677.tcore2.LVW-LosAngeles.as6453.net (209.58.96.162)  305.655 ms  305.626 ms  309.597 ms
10  Vlan12.icore2.LAA-LosAngeles.as6453.net (216.6.12.49)  313.575 ms  315.567 ms  317.539 ms
11  192.205.35.129 (192.205.35.129)  315.513 ms  317.502 ms  321.446 ms
12  cr2.la2ca.ip.att.net (12.122.129.34)  306.031 ms  301.813 ms  300.017 ms
13  cr1.slkut.ip.att.net (12.122.30.29)  310.002 ms  311.987 ms  315.962 ms
14  cr2.dvmco.ip.att.net (12.122.30.26)  335.955 ms  335.935 ms  337.921 ms
15  cr1.cgcil.ip.att.net (12.122.31.86)  317.900 ms  319.866 ms  319.990 ms
16  cr1.cl2oh.ip.att.net (12.122.2.206)  321.837 ms  323.827 ms  327.804 ms
17  cr83.cl2oh.ip.att.net (12.123.151.49)  339.846 ms  311.820 ms  315.777 ms
18  gar10.cl2oh.ip.att.net (12.123.150.29)  295.884 ms  301.830 ms  301.826 ms
19  12.91.184.198 (12.91.184.198)  329.874 ms  333.784 ms  337.773 ms
20  lornohcora1.lornohcoro1.centurytel.net (209.142.152.11)  313.750 ms  315.731 ms  319.705 ms
21  wooledge.org (209.142.155.49)  325.687 ms  335.677 ms  337.657 ms


---

### Post by Lazaruss on 2010-10-24
albincepa, which one of my suggestions was the one that worked?

---

### Post by darth62969 on 2010-10-24
not to change the subject but i'm having a similar but different issue. the websites that do not start with www. are coming up with a error saying " 
Server not found
Firefox can't find the server at pace.discovery-us.net.
    *   Check the address for typing errors such as
          ww.example.com instead of
          [www.example.com](www.example.com)

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.
please help me. i am trying to get info for collages and this error is not helping!

---

### Post by darth62969 on 2010-10-24
the site does not even link properly. :(

---

### Post by albincepa on 2010-10-25
i dont know how it worked.......
i just cleared the cache file and history.But that didnt get me work at that moment.
But the next day i tried to open the site and it was opened

---

### Post by Rushyang on 2010-10-25
> **albincepa said:**
> i dont know how it worked.......
i just cleared the cache file and history.But that didnt get me work at that moment.
But the next day i tried to open the site and it was opened

I tried everything that already.. First I thought that must because of flash plugin.. but then mywiki.wooledge.org stop opening too.

I am very regular into upgrading every packages in ubuntu too! and it's been almost a week. This thing is driving me crazy! I can't leave ubuntu and boot into windows cause I want to learn more bash scripts? That's crazy!

---

### Post by albincepa on 2010-10-26
Now I am having the same issue with many other websites..
I am now unable to retrieve any website in the search result of Google News.
I am getting fed up with ubuntu....:confused::confused::confused::confused:

---

### Post by Tristan Tonks on 2010-12-22
I've had this problem since Karmic - I get this error consistently from a number of sites and many (Often including this site) wont let me POST data such as this post which may or may not do ... :(

Error 101 (net::ERR_CONNECTION_RESET): Unknown error.

---

### Post by furlabs on 2010-12-24
I've seen this sort of thing before with a bad MTU size. Here is a link that explains it:
[https://blue-labs.org/howto/mtu-mss.php]("https://blue-labs.org/howto/mtu-mss.php")

Basically, to accommodate for certain websites you need to clamp your MTU to 1492 bytes. Here is how to do that from the command line:
```
ifconfig eth0 mtu 1492
```

Doing this on the workstation may be sufficient, or you might need to do the same clamp at your modem/router, I'm not sure.

Hope this helps someone!

---

