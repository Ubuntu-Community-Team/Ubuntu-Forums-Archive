---
title: "Slow download internet speed on ubuntu"
date: 2011-11-30
forum: Networking &amp; Wireless
---

### Post by Master_T on 2011-11-30
Hi guys

I'm rather new to ubuntu and linux in general, but I recently assembled an HTPC to use with my projector, and I've chose ubuntu 11.10 to put on it.

Now, the first week, everything went well. But since two day ago a very annoying problem appeared: the internet connection (that the pc gets from an ethernet connection directly to the router) suddenly slowed down to a trickle of its usual speed, and gives no signs of getting back to normal.

Now, this is not a router problem I think, because my windows7 laptop uses the same router, but where the laptop downloads at 750-800 k/s, ubuntu won't go faster than 25-30 k/s, no matter the download source or program used (tested chromium, wget and jdownloader, all the same)

This is really weird, but I don't recall doing anything that involved the internet/lan connection and can't find any similar problem with a google search.

Hope you can help me, any info you might need just ask and I'll provide.

EDIT: some info:

PC is based on an Asus AT5IONT-I with integrated intel atom and Nvidia ION
Router is a TP-Link TD-W8950ND

EDIT 2: The problem seems to be the same one as described here:

[http://ubuntuforums.org/showthread.php?t=1800215](http://ubuntuforums.org/showthread.php?t=1800215)

but although I followed the instructions there and I was able to build and run the r8168 driver, the problem still persists :(

---

### Post by BC59 on 2011-11-30
The only coming to my mind is that the cable is failing.

---

### Post by Lisiano on 2011-11-30
First of, let's check that the ethernet connection hasn't dropped for some magic reason to a lower speed
```
lshw -c network
```
We are looking for these 2 lines
       size: 100Mbit/s
       capacity: 1Gbit/s
Size is the current speed and capacity is the maximum possible speed. As you see, I'm connected to a 100Mbit network when my PC can connect to a 1Gbit network. I blame my ISP for my router. Anyway. If this shows your normal speed, try doing some speed tests on [speedtest.net]("speedtest.net") . Usually a local server is best, one from your ISP is even better, both is best. If this fails to give normal readings then something is very wrong. But as another test, try to download a Ubuntu ISO (Or anything with a direct link) using a program called [Axel]("apt://axel"), just click it to download it or type this into a terminal ```
sudo apt-get install axel
```
Now try to download a Ubuntu ISO using axel, say you want to try with 8 connections
```
axel -a -n8 http://releases.ubuntu.com/11.10/ubuntu-11.10-alternate-i386.iso
```
The -a is so that axel gives us pretier output, and -n8 means 8 connections, you can type it as -n8 or -n 8 it doesn't matter. You can use more or less, but try with 8 first.

EDIT: @BC59 Possible.

@OP - Try running this
```
sudo ping -A 192.168.1.1
```
Substitute 192.168.1.1 with your routers IP.
What this will do is start flooding your router, after a few seconds press Ctrl+C and copy-paste whatever appears after this line
```
--- 192.168.1.1 ping statistics ---
```
For me it was this
```
--- 192.168.1.254 ping statistics ---
4821 packets transmitted, 4821 received, 0% packet loss, time 2642ms
rtt min/avg/max/mdev = 0.260/0.377/10.076/0.192 ms, ipg/ewma 0.548/0.362 ms
```
If it says that the packet loss is bigger than 0%. You have a physical problem.

---

### Post by bluexrider on 2011-11-30
swap the ports on the router, might have a bad port
swap out the cables if the problem moves then it moved with the bad cable.
hook the box directly to the INTERNET ie: remove the router from the picture

always use reliable ping - trace for feedback as in [http://speedtest.net/](http://speedtest.net/) and use the same host for each test.

Good luck

---

### Post by Master_T on 2011-11-30
Thanks for the replies, but all seems normal on the tests I made.

I thought I had found the solution here:

[http://ubuntuforums.org/showthread.php?t=1800215](http://ubuntuforums.org/showthread.php?t=1800215)

The problem seems to be the same, but I followed the various procedures indicated there and it didn't solve my problem, and the thread is closed so I cannot reply :(

---

### Post by bluexrider on 2011-11-30
Master_T,

you are referring to the R8168 driver then try this:

1. Download script here
[http://www.jamesonwilliams.com/bin/r...cripts.tar.bz2]("http://www.jamesonwilliams.com/bin/r8168_scripts.tar.bz2")
( [http://www.jamesonwilliams.com/hardy-r8168](http://www.jamesonwilliams.com/hardy-r8168) )

2. Download r8168-8.025.00.tar.bz2 here 
[http://code.google.com/p/r8168/downloads/list](http://code.google.com/p/r8168/downloads/list)

3. Extract r8168_scripts.tar.bz2 and go to the extracted dir
cd r8168_scripts

4. Copy new r8168-8.025.00.tar.bz2 drivers to this directory

5. Edit "switchmods" end set VERSION to
VERSION=r8168-8.025.00

6. run switchmods
sudo ./switchmods


[http://ubuntuforums.org/showthread.php?t=1861865](http://ubuntuforums.org/showthread.php?t=1861865)

---

### Post by Master_T on 2011-12-01
> **bluexrider said:**
> Master_T,

you are referring to the R8168 driver then try this:

1. Download script here
[http://www.jamesonwilliams.com/bin/r...cripts.tar.bz2]("http://www.jamesonwilliams.com/bin/r8168_scripts.tar.bz2")
( [http://www.jamesonwilliams.com/hardy-r8168](http://www.jamesonwilliams.com/hardy-r8168) )

2. Download r8168-8.025.00.tar.bz2 here 
[http://code.google.com/p/r8168/downloads/list](http://code.google.com/p/r8168/downloads/list)

3. Extract r8168_scripts.tar.bz2 and go to the extracted dir
cd r8168_scripts

4. Copy new r8168-8.025.00.tar.bz2 drivers to this directory

5. Edit "switchmods" end set VERSION to
VERSION=r8168-8.025.00

6. run switchmods
sudo ./switchmods


[http://ubuntuforums.org/showthread.php?t=1861865](http://ubuntuforums.org/showthread.php?t=1861865)

Thanks, but those links do not seem to work...

---

### Post by bluexrider on 2011-12-01
> **Master_T said:**
> Thanks, but those links do not seem to work...

I checked the links before posting. I will admit it was a little slow connecting but it took me to the list of tar-balls stated.

Try it again 

                            [  [IMG]http://www.gstatic.com/codesite/ph/images/dl_arrow.gif[/IMG]  ]("http://r8168.googlecode.com/files/r8168-8.026.00.tar.bz2")           [    r8168-8.026.00.tar.bz2    ]("http://code.google.com/p/r8168/downloads/detail?name=r8168-8.026.00.tar.bz2&can=2&q=")                  [    r8168-8.026.00.tar.bz2 ]("http://code.google.com/p/r8168/downloads/detail?name=r8168-8.026.00.tar.bz2&can=2&q=")

     [[IMG]http://www.gstatic.com/codesite/ph/images/dl_arrow.gif[/IMG]  ]("http://r8168.googlecode.com/files/r8168-8.025.00.tar.bz2")           [    r8168-8.025.00.tar.bz2    ]("http://code.google.com/p/r8168/downloads/detail?name=r8168-8.025.00.tar.bz2&can=2&q=")                  [    r8168-8.025.00.tar.bz2 ]("http://code.google.com/p/r8168/downloads/detail?name=r8168-8.025.00.tar.bz2&can=2&q=")

                               [  [IMG]http://www.gstatic.com/codesite/ph/images/dl_arrow.gif[/IMG]  ]("http://r8168.googlecode.com/files/r8168-8.024.00.tar.bz2")           [    r8168-8.024.00.tar.bz2    ]("http://code.google.com/p/r8168/downloads/detail?name=r8168-8.024.00.tar.bz2&can=2&q=")                  [    r8168-8.024.00.tar.bz2 ]("http://code.google.com/p/r8168/downloads/detail?name=r8168-8.024.00.tar.bz2&can=2&q=")

---

### Post by Master_T on 2011-12-01
> **bluexrider said:**
> I checked the links before posting. I will admit it was a little slow connecting but it took me to the list of tar-balls stated.

Try it again 

                            [  [IMG]http://www.gstatic.com/codesite/ph/images/dl_arrow.gif[/IMG]  ]("http://r8168.googlecode.com/files/r8168-8.026.00.tar.bz2")           [    r8168-8.026.00.tar.bz2    ]("http://code.google.com/p/r8168/downloads/detail?name=r8168-8.026.00.tar.bz2&can=2&q=")                  [    r8168-8.026.00.tar.bz2 ]("http://code.google.com/p/r8168/downloads/detail?name=r8168-8.026.00.tar.bz2&can=2&q=")

     [[IMG]http://www.gstatic.com/codesite/ph/images/dl_arrow.gif[/IMG]  ]("http://r8168.googlecode.com/files/r8168-8.025.00.tar.bz2")           [    r8168-8.025.00.tar.bz2    ]("http://code.google.com/p/r8168/downloads/detail?name=r8168-8.025.00.tar.bz2&can=2&q=")                  [    r8168-8.025.00.tar.bz2 ]("http://code.google.com/p/r8168/downloads/detail?name=r8168-8.025.00.tar.bz2&can=2&q=")

                               [  [IMG]http://www.gstatic.com/codesite/ph/images/dl_arrow.gif[/IMG]  ]("http://r8168.googlecode.com/files/r8168-8.024.00.tar.bz2")           [    r8168-8.024.00.tar.bz2    ]("http://code.google.com/p/r8168/downloads/detail?name=r8168-8.024.00.tar.bz2&can=2&q=")                  [    r8168-8.024.00.tar.bz2 ]("http://code.google.com/p/r8168/downloads/detail?name=r8168-8.024.00.tar.bz2&can=2&q=")

Thanks for your help, but in the end I just reinstalled the whole system, less trouble...

---

### Post by bluexrider on 2011-12-01
Sweet...got it going again.

Please mark this (SOLVED)

---

