---
title: "A very unique internet connectivity issue"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by udey on 2009-05-26
Hello all,

I am using Ubuntu 9.04 64-bit on Acer Aspire Notebook running Intel Core 2 duo with all the fancy hardware. No other OS on the Notebook.

There are many features of the Notebook I am unable to use in Ubuntu.
But firstly I need to get started with the internet.

So I am using my Dektop PC running WindowsXP to find out what I can do to be happy with my Notebook running Ubuntu 9.04


**OK, I have tried:**
**1. PPPCONFIG :** This gives a TUI menu to enter data - but it does not recognise "eth0". It says "/dev/eth0" was not found. I had selected automatically detect connections but it does not find eth0. But the Network Manager shows "eth0" existing and installed.
Also the TUI menu of pppconfig suggests only COM ports of "ttyS1" / "ttyS2" / "ttyS3". It doesn't find "eth0".
**the results of my "pppconfig".**
>>> 1. What happens is it takes all the data input and saves it in a connection I named "lastmile".
>>> 2. Then I run the "sudo pon lastmile" command and it gives the error of not finding any "/dev/eth0"
>>> 3. So of course the PPPCONFIG supposedly doesn't need any manual entries in 9.04 but it seems its TUI offers limited finctionality to customise settings.
>>> 4. In the TUI I had selected the option to automatically detect the network devices but it only lists the "ttyS0" / "ttyS1" / "ttyS2" / "ttyS3". It doesn't find "eth0".

Yet my **Network Manager** knows there is a "eth0".


**2. Roaring Penguin :**  Downloaded from WinXP this utility and extracted it on my Notebook by copying it from USB drive. 
**So here is the command and the setup finalised info:**
$ sudo pppoe-setup

<then I entered all the data>

** Summary of what you entered ** 
 
Ethernet Interface: eth0 
User name:          udey 
Activate-on-demand: No 
DNS addresses:      Supplied by ISP's server 
Firewalling:        STANDALONE 

Type 'pppoe-start' to bring up your PPPoE link and 'pppoe-stop' to bring 
it down.  Type 'pppoe-status' to see the link status. 
$ sudo pppoe-start 
................TIMED OUT 
$
[B]
NOTE THAT[/B] this setup never asked me for **dial number.**


**3. Of course the Network Manager** has been of no help in connecting to my Cable Internet.


* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *

](*,)

OK, so now I figured my ISP is different from the regular connections people use world over.

**So I found these 2 threads:**

BOTH threads have the creator **who never posted if they managed to solve **this issue or not.

:(

OK, refer to the forum user **"navir" of Bombay**, India who posted **back in 2006** the below problem which best **describes my ISP and** my internet connectivity problems.

The "navir" dude also mentions my ISP "lastmile" in the first post on second page of the below thread.

[http://ubuntuforums.org/showthread.php?t=129610](http://ubuntuforums.org/showthread.php?t=129610)

1. See, I too have a **raspppoe** client in my WinXP to dial.
2. I too have a simple cable line coming from my ISP and the cable goes into my computer's LAN point
3. There is no router nor anything else - a simple cable internet which my **Windows XP calls "LAN".** WinXP **calls this PPP over Ethernet**.

4. The last post there by a **Russian **user says he got it working.
5. Sadly the Indian users including "navir" whose problem is same as mine - have not posted whether they gave up or tried and resolved it.


So there - now that is what I am facing - raspppoe  ?!? What do I do for it in Ubuntu ?


See the dates on the forum topic - it reveals a lot too. [IMG]http://forums.highiqsociety.org/fusionbb/images/smilies/tongue.gif[/IMG]

That thread is in **Archives and is locked**. 


**A similar problem thread here:** Another dead-end - no one says they solved it.
[http://ubuntuforums.org/showthread.php?t=622848](http://ubuntuforums.org/showthread.php?t=622848)




Any tips or links or help would be most appreciated.    :confused: :cry:

Best Wishes,
UD

---

### Post by udey on 2009-05-26
Hello friends,

Can anyone suggest something for this Cable Internet connection possibilities on Ubuntu 9.04

:(

---

### Post by udey on 2009-05-30
Hi,

So I am guessing no one outside India uses Cable Internet connection ?


Well, rp-pppoe also doesn't seem to work.

:(


ERRORS:
>   laptop pppd[7277]: Plugin rp-pppoe.so loaded.
    laptop pppd[7277]: RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
    laptop pppd[7277]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
    laptop pppd[7277]: pppd 2.4.5 started by root, uid 0
    laptop pppd[7277]: PPP session is 57510
    laptop pppd[7277]: Connected to 00:50:bf:51:c8:2a via interface eth0
    laptop pppd[7277]: Using interface ppp0
    laptop pppd[7277]: Connect: ppp0 <--> eth0
    laptop pppd[7277]: Terminating on signal 15
     
   
  laptop pppd[8451]: Plugin rp-pppoe.so loaded.
    laptop pppd[8451]: RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
    laptop pppd[8451]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
    laptop pppd[8451]: pppd 2.4.5 started by root, uid 0
    laptop pppd[8451]: PPP session is 57511
    laptop pppd[8451]: Connected to 00:50:bf:51:c8:2a via interface eth0
    laptop pppd[8451]: Using interface ppp0
    laptop pppd[8451]: Connect: ppp0 <--> eth0
    laptop pppd[8451]: Connection terminated.
    laptop pppd[8451]: Exit.
   
  


---

### Post by TransitMan on 2009-05-30
Are you on a Cable Internet system or DSL system?
Cable has no PPPoE, DSL does, depending.
If you provided a little more insight into you ISP and the connection, then someone might be able to help.

---

