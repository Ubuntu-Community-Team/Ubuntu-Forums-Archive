---
title: "ubuntu 11.04 beta wireless problem"
date: 2011-04-16
forum: Networking &amp; Wireless
---

### Post by eng.zizo on 2011-04-16
hi all ,
 
im using dell 1545 laptop , and i've already installed ubuntu 11.04 beta version (64 bit) on it , after i've activated my broadcom wirless ; i wasn't able to detect my home wireless network !!! , could anybody please help me with that ? :)

---

### Post by KegHead on 2011-04-16
Hi!

Have you clicked on the wifi icon on the tip bar and selected your's?

KegHead

---

### Post by eng.zizo on 2011-04-16
> **KegHead said:**
> Hi!

Have you clicked on the wifi icon on the tip bar and selected your's?

KegHead


i can't find it

---

### Post by treasonvoice on 2011-04-16
> **eng.zizo said:**
> i can't find it

You can't find the wifi icon? Are you running in safe mode?

---

### Post by exile on 2011-04-19
I have exactly the same problem. Once you activate the broadcom driver the wifi part of the network windicator vanishes. Deactivate it and it's there again. I deactivated STA drivers and installed the B43 installer and cutter in synaptic, rebooted, now wireless. Seems that there are issues with 64bit broadcom STA drivers - my machine is a Dell (AMD) 1501.

---

### Post by domex on 2011-04-25
> **exile said:**
> I have exactly the same problem. Once you activate the broadcom driver the wifi part of the network windicator vanishes. Deactivate it and it's there again. I deactivated STA drivers and installed the B43 installer and cutter in synaptic, rebooted, now wireless. Seems that there are issues with 64bit broadcom STA drivers - my machine is a Dell (AMD) 1501.

Thank you very much kind sir, this worked perfectly and i have a Dell 1400 vostro:KS

---

### Post by violinbach on 2011-04-28
I am running a *32-bit* dell inspiron 1501 and had the same problem.

The solution here worked for me as well.  Had to do a couple reboots however.

Thanks!

---

### Post by Edvora on 2011-04-30
Hi, I've been having the same problem, I have a Dell Inspiron 15 as well. That process seems to work, but I don't know how to deactivate my STA drivers (I don't even know what STA drivers are...) and I don't know how or where to install a B43 installer and cutter (I don't know what that is either). Can anyone tell me how to do those things?

---

### Post by mpranav007 on 2011-04-30
this solved my problem too!!

---

### Post by domex on 2011-05-01
> **Edvora said:**
> Hi, I've been having the same problem, I have a Dell Inspiron 15 as well. That process seems to work, but I don't know how to deactivate my STA drivers (I don't even know what STA drivers are...) and I don't know how or where to install a B43 installer and cutter (I don't know what that is either). Can anyone tell me how to do those things?

To deactivate goto ***System / Additional drivers ***then it will search and open a small window, click on deactivate, after that reboot.  Then go to** System / Synaptic Package Manager** type in the clear box **b43**
and hit search, once the list comes up, check the first box, and then mark for installation, after click on Apply on the top which will be highlighted in green. after it applies it should be all good,if not reboot.

---

### Post by dkc.com on 2011-05-08
Hi friends,

Using Dell Inspiron 1520 and facing the same problem with the fresh install of Ubuntu 11.04. I tried the method but it doesn't help.

I have put my trouble here: [http://ubuntuforums.org/showthread.php?p=10787009#post10787009]("http://ubuntuforums.org/showthread.php?p=10787009#post10787009")

Can anybody please advise?

Thanks.

---

### Post by meconio on 2011-05-15
I had the same issue with 11.04 in my Inspiron 1720 with a 1390 WLAN, and deactivating the STA broadcom driver, and installing the b43-firmware package did work.

Make sure you restart after deactivating the STA and prior to install the b43.

---

### Post by arindamlala on 2011-06-19
Thanks a lot... I was also facing the same problem. Now it is solved.

---

### Post by Mebuntux on 2011-07-04
I had the same problem. Now solved. Thanks!

---

### Post by rockinronnie on 2011-07-28
Worked a treat on my old Dell Inspiron 1501 ... thank you!

---

### Post by sentinelace on 2011-08-02
not working for me on Dell Precision m4300.  1390 Wireless.  I install the b43 and disabled the other and still no go.  It worked during the first boot and then hasn't connected since.

---

### Post by sentinelace on 2011-08-02
I got mine to work but I have to have the broadcom driver enabled / activated.  Any idea why?

---

### Post by trooperchix on 2011-08-03
[http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/]("http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/")

Use it, it works.  You absolutely have to do a complete shutdown and restart for this to work.  I didn't even have to go to the alternate fixes.  I couldn't find anything, nothing worked, I did all kinds of research.  Give it a shot.  It saved my behind...

Be sure to disable the proprietary drivers option under software sources or update manager will update your driver right back to the one that doesn't work.  Go to Update Manger.  At the bottom left hit the settings button.  It's under the Ubuntu Software tab, right in the middle of the page.

---

### Post by javapadowan on 2011-09-09
WOW!!!!

Getting rid of the STA driver then getting the b43 cutter DID WORK! When you select the cutter, it selects a related b43 driver and installs quickly. I was so excited. It only took 1 and 1/2 minutes. 

I rebooted then dropped my CAT 5 network cable and my network started to snap, crackle and pop!

All my networks appeared and so did my neighbors network :)

You guys rock for working this thing out for me.

---

### Post by serz152 on 2011-11-27
I am using a dell latitude D630 and have aquired the same scenario but do I too use the b43 method or something different the internet is mine but it is wpa2 encrypted will that make a difference

---

### Post by serz152 on 2011-11-27
This is a complete waste of time it doesnt connect to the internet it shows a connection established yet firefox shows no server and no technical support to help ***[SIZE=3]JUNKJUNKJUNK[/SIZE]***

---

### Post by SidMoore on 2011-11-27
Hot Dog!!! Domex's fix worked just fine with my Dell Vostro 1400. Didn't even have to reboot. Many thanx for a fine solution to a vexing problem.

---

### Post by serz152 on 2011-11-28
:o:o:confused:Garbage servers are super slow and the interface is hard to understand after getting it to work with the internet I would give it a big thumbs down if you are having trouble you need to get the b43 firmware installed then it will connect but extremely slow if you got that kinda time. I tried it and I certainly hope not all of linux products perform this poorly I try it again after its been perfected and out of the early stages leave it too the developers to tweak this OS not for any computer novice. Needs a lot of work.:(:(

---

### Post by skylarks on 2011-12-11
for wifi activation in DELL latitude 630 and DELL precision M65 simply go to :
Dash home 
search terminal
now open terminal icon in search window
type following command
"sudo apt-get install firmware-b43-install"
press enter and give administrator password and accept installation after finish enjoy ur wifi

---

### Post by bogan on 2011-12-11
Hi! , **Skylark**,
You Posted:> **Re: ubuntu 11.04 beta & 11.1 wireless problem**
         for wifi activation in DELL latitude 630 and DELL precision M65 simply go to :
Dash home 
search terminal
now open terminal icon in search window
type following command
"sudo apt-get install firmware-b43-install"
press enter and give administrator password and accept installation after finish enjoy ur wifi     Will your tip work on other Ubuntu versions ?

When I tried in 10.10 I got prompted to install  sphinxsearch, and when I entered your code I got: ```
 root@alan-MS-7616:/home# search terminal
Sphinx 0.9.9-release (r2117)
Copyright (c) 2001-2009, Andrew Aksyonoff

using config file '/etc/sphinxsearch/sphinx.conf'...
FATAL: failed to connect to MySQL (error=Can't connect to local MySQL server
 through socket '/var/run/mysqld/mysqld.sock' (2))
root@alan-MS-7616:/home#
``` Folder and file '/var/run/mysqld/mysqld.sock' do not exist.

Any suggestions?

Chao! , **bogan**.

---

### Post by jamesbon on 2011-12-16
I too faced the same problem in my case the STA driver was working since many weeks but recently after an update
```
sudo apt-get dist-upgrade
``` I lost wireless connectivity.
 What worked for me is described here
[http://ubuntuforums.org/archive/index.php/t-1732258.html](http://ubuntuforums.org/archive/index.php/t-1732258.html)


I've removed all firmware related to b43 driver by issuing > sudo apt-get purge firmware-b43*.
I've reinstalled firmware ```
sudo apt-get install firmware-b43-lpphy-installer
```. Worked like a charm.
Of course, I was connected to the Internet through a wired connection.
Can also check this link [http://www.computerandyou.net/2011/05/how-to-solve-no-wireless-networks-in-ubuntu-11-04/](http://www.computerandyou.net/2011/05/how-to-solve-no-wireless-networks-in-ubuntu-11-04/)

---

