---
title: "Broadcom Corporation BCM4312 802.11a/b/g, not detected"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by mrefan on 2009-10-31
hello
i have a HP Pavilion dv 6000 series. my wireless card is BCM4312!
recently i`ve had installed the latest ubuntu version ( 9.1  64 bit edition)
and now it does not detect my wireless lan! 
when i click on  * system> administration > hardware drivers* it wont find my wireless card!
please help me... if i can not do this,unfotunately; i will recover my windows vista! 
please help me

---

### Post by salabanzi on 2009-10-31
i have this problem too. please help! :(

---

### Post by mrefan on 2009-10-31
yohooo... what a beautiful feeling when you can connect to the net without any wire!
i found
finally i found it
open your terminal and do this:


mohsen@mohsen-ubuntu9:~$ sudo apt-get install bcmwl-kernel-source

then restart your computer... it will happen :D

please report me if it works
thanks god

---

### Post by salabanzi on 2009-10-31
> **mrefan said:**
> yohooo... what a beautiful feeling when you can connect to the net without any wire!
i found
finally i found it
open your terminal and do this:


mohsen@mohsen-ubuntu9:~$ sudo apt-get install bcmwl-kernel-source

then restart your computer... it will happen :D

please report me if it works
thanks god


thank god indeed :D! this solution does work. thank you so much!!

---

### Post by Tekmoor on 2009-10-31
This worked for me!

Dell 1535 laptop
I have a Dell 1397 Wireless card that is really a bcm4312

Thanks mrefan! :D

---

### Post by alloutnow on 2009-10-31
I had the same problem (I just installed **Ubuntu 9.10, 64 bit**) on my **HP Pavilion dv 6000** laptop.

I got my **Broadcom Corporation BCM4312 802.11a/b/g** card to work after following **mrefan's** suggestions but there is still something very wrong here!  My wireless connection is disconnection again and again and asking me to re-inserting the wireless security key every time!?  **WTF is going on, anyone?** :confused:

---

### Post by gubbi.fisk on 2009-11-01
I have the same problem. The driver is installed. But it won't connect, it just disconnects other times it just states that it couldn't get IP-address. 

Installed Ubuntu 9.10 just after the release!

Please help!

---

### Post by doixanh on 2009-11-01
Same BCM4312 here. I got it installed with ndiswrapper, but no luck to connect to my Access Point.

Any ideas?

---

### Post by mrefan on 2009-11-01
install this package and dependencies:

[http://packages.ubuntu.com/da/karmic/admin/bcmwl-kernel-source](http://packages.ubuntu.com/da/karmic/admin/bcmwl-kernel-source)

then try again

---

### Post by gubbi.fisk on 2009-11-01
> **mrefan said:**
> install this package and dependencies:

[http://packages.ubuntu.com/da/karmic/admin/bcmwl-kernel-source](http://packages.ubuntu.com/da/karmic/admin/bcmwl-kernel-source)

then try again

I've already got that package. So I reinstalleded, but changes.

I'm running Ubuntu 9.10 32bit.

Gubbi.fisk

---

### Post by mrefan on 2009-11-01
aw.... finally i did`nt find out, does it works?
thats OK now?! or not? 
there are both of them, i386 and x64 :)

i wish it works

---

### Post by gubbi.fisk on 2009-11-01
No, it doesn't work for me. I must have reinstalled that package like 10 times... But still no luck! I only used the 32-bit version, obviously.

---

### Post by mrefan on 2009-11-03
this is the last way that i knew it!

go to * system>administration > synaptic package manager * and then un install these packages:
1.bcmwl-kernel-source
2.b43xx-fcuter

then type this command in your terminal:

#sudo apt-get install linux-backports-modules-karmic

sorry for my delay!

please report :)

---

### Post by milan.skocic on 2009-11-07
there is also a solution here :

[http://www.uluga.ubuntuforums.org/showthread.php?p=8263853#post8263853](http://www.uluga.ubuntuforums.org/showthread.php?p=8263853#post8263853)

---

### Post by rjbull on 2009-11-20
This worked for me too. 


mohsen@mohsen-ubuntu9:~$ sudo apt-get install bcmwl-kernel-source

I also say thanks God!

Lenovo G550
T4300

---

