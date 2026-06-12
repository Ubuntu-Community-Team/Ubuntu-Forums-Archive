---
title: "Wireless connectivity for Ubuntu 10.04"
date: 2013-03-13
forum: Networking &amp; Wireless
---

### Post by rohit3051 on 2013-03-13
Hi experts,


I am having trouble connecting to internet using wifi from ubuntu 10.04(I need this version to install a software that runs only on this version). I have browsed through a lot of forums to solve my internet issue and each one has shown a different procedure. So I decided to post it here to get a step by step procedure to get wifi connectivity.  I installed Ubuntu 10.04 using wubi, and from my research I could guess that all my drivers are not installed properly. I used ndiswrapper to install windows driver and still it does not work.

I am stuck with this problem for the past 3 days and it worries me as I am delaying my project.

I would be glad if someone could point me to a step by step guide explaining what is being done at each step so that I can have a clear idea.



Wireless card: Intel centrino wireless N 2200

Below are some outputs to the commands asked in a previous forum I thought would be helpful.

tiger@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:9e:01:04:60:cc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0x8000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB)
-------------------------------------------------------------------------
tiger@ubuntu:~$ mtr -nrc2 8.8.8.8
HOST: ubuntu                      Loss%   Snt   Last   Avg  Best  Wrst StDev
tiger@ubuntu:~$ 
--------------------------------------------------------------------------
tiger@ubuntu:~$ host [www.google.com]("http://www.google.com")
;; connection timed out; no servers could be reached
---------------------------------------------------------------------------
tiger@ubuntu:~$ mtr -nrc2 8.8.8.8
HOST: ubuntu                      Loss%   Snt   Last   Avg  Best  Wrst StDev
tiger@ubuntu:~$ host [www.google.com]("http://www.google.com")
;; connection timed out; no servers could be reached
tiger@ubuntu:~$ host [www.google.com]("http://www.google.com") 8.8.8.8
;; connection timed out; no servers could be reached
----------------------------------------------------------------------------

TIA



Questions:

1.Does installing Ubuntu through wubi have any drawbacks?
2. What is the procedure to setup wifi after installing windows driver?
3. there is no wlan0 in my ifconfig. What is wlan0 ?

---

### Post by chait on 2013-03-13
Hi [**[COLOR=#000000]rohit3051[/COLOR]**]("http://ubuntuforums.org/member.php?u=1798946"),
    wlan refers to wireless device on your system.
   can u post the output of the following command on ur system?
   ifconfig wlan0

cheers

---

### Post by rohit3051 on 2013-03-13
Hi chait,

As I said I do not have wlan0.

**#ifconfig wlan0**
wlan0: error fetching interfaces information: Device not found.

Can you suggest what steps do I need to follow from here.
TIA

---

### Post by mörgæs on 2013-03-13
Windows, Wubi, old Ubuntu, Ndiswrapper: My advice is to avoid all of them if possible. 

Which applications work only in 10.04?

Have you considered a dual boot with Buntu 12.10? Your time might be better spent by focusing on getting the applications to run in a recent Buntu.

---

### Post by rohit3051 on 2013-03-13
I only have the problem with connecting wifi in Ubuntu 10.04. 
No, I have not tried other versions of Buntu
 I will try the latest version if all others fail. Now my priority is to get 10.04 working as it is a must for my project.

Thanks.

---

