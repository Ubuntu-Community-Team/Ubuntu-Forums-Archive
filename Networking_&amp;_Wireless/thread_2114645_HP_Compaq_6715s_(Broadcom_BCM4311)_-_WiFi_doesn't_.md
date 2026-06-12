---
title: "HP Compaq 6715s (Broadcom BCM4311) - WiFi doesn't work"
date: 2013-02-10
forum: Networking &amp; Wireless
---

### Post by dziadzia fritz on 2013-02-10
[B]Hello,
[/B]
first i have to say sorry that i didn't used FAQ before.

I'm compleatly newbie Ubuntu-user and i need help with wireless in my **HP Compaq 6715s **laptop.

I've tried this method with ndiswrapper, but it doesn't work at all.

I have normally DHCP connection, but WiFi doesn't work.

What do?

**Version of ubuntu: 12.10 32 bit**

---

### Post by kc1di on 2013-02-10
Hello dziadzia fritz and welcome Ubuntu,

please go to a terminal and type or copy the following command and post the results here. 

```
lspci -nn | grep 0280
```

---

### Post by dziadzia fritz on 2013-02-10
Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 02)

---

### Post by kc1di on 2013-02-10
ok go to [this page]("http://askubuntu.com/questions/38327/how-can-i-get-broadcom-bcm4311-wireless-working") and follow the instructions in the answer there.

---

### Post by dziadzia fritz on 2013-02-10
> I fixed my problem with the Broadcom bcm4311 drivers on 11.04 (Natty Narwhal)

Steps I took for fixing this problem (I stole this method from nm_geo on ubuntu forums): ( You may need to install synaptic or your favorite package manager)

open your package manager and search for 'bcm'

uninstall the bcmwl-kernel-source package

make sure that the firmware-b43-installer and the b43-fwcutter packages are installed

type into terminal:

cat /etc/modprobe.d/* | egrep 'bcm'
(you may want to copy this) and see if the term 'blacklist bcm43xx' is there

if it is, type cd /etc/modprobe.d/ and then sudo gedit blacklist.conf

put a # in front of the line: blacklist bcm43xx

then save the file (I was getting error messages in the terminal about not being able to save, but it actually did save properly).

reboot

hopefully this works for you all!

Yeah! It works great! :) Thanks for help! :)

---

### Post by kc1di on 2013-02-10
your welcome ;)

---

### Post by mörgæs on 2013-02-11
> **dziadzia fritz said:**
> Yeah! It works great! :) Thanks for help! :)

Good, then please mark the thread 'solved'.

---

### Post by ssreddy555 on 2013-02-11
Mine is BCM 4312; I'm using Ubuntu 11.04. For me, bcmwl-kernel-source worked.

However, on another machine, I used Mint KDE 12, but here,I had to apt-get install update first & then install the STA driver available in the Additional Divers. But, errors kept appearing & each time I reboot, it was gong into "checking errors" mode.

---

### Post by irma2 on 2013-10-11
Thank you veery much!!!!

---

### Post by customj79 on 2013-10-11
do this it should work open terminal type one in order then hit enter type the next one and so on then wait
sudo lsmod    	 	 	 	   	 	 	 	   
sudo apt-get install lshw 

          
sudo lshw -C network

---

