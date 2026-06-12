---
title: "dell inspiron 1501 ubuntu 9.10 wireless not working"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by nnymous12 on 2010-01-24
Dear Ubuntu Experts,

On my _Dell Inspiron 1501_ (I think I run it as i386, I have upgraded to _ubuntu 9.10_) the **wireless card refuses to work**.  
I believe that the card is OK, since it used to work with an older version of Fedora (lost the wireless function when upgrading to Fedora 8 ).  Since then, I fried the had drive and after that I decided to go with Ubuntu on the new hard disk.  Since installing the new hard drive, I was never able to get the wireless card to work, and upgrading to Ubuntu 9.10 did not help.
I installed  the i386 b43-fwcutter (from 
[http://packages.ubuntu.com/intrepid/utils/b43-fwcutter](http://packages.ubuntu.com/intrepid/utils/b43-fwcutter) ).
I found this link here:
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72) (note, since I have an active internet connection, I did not follow these instructions, I used the gui that came up when I clicked the download link and let the installer find/download the firmware)

I installed _wifi radar_, and re-started the computer: none of the local wireless nets show up (other computers find many networks) and wifi radar says it has no hardware.

Please help!

One more request: As you see from my rumblings above, I AM COMPLETELY CLUELESS when it comes to my computer.  _PLEASE_ HELP ME WITH _FOOLPROOF INSTRUCTIONS_.

[U][B]THANKS!
[/B][/U]

---

### Post by drpjkurian on 2010-01-24
Hi 
I think you have lost the driver for your card while upgrading.
Please type the following command in terminal to know the make of your card
```
sudo lshw -C network
```
&
```
iwconfig
```

---

### Post by cjjoy1980 on 2010-01-24
Even I am having problem connecting to wifi with my E1505. But I belive mine is not a driver installation problem but some configuration problem. 
I am able to see the wifi network but cannot connect to it.  

I installed my wireless driver using ndswrapper you can give it a shot and see if it works for you. 


1. Install ndswrapper:

sudo aptitude update
sudo aptitude install ndisgtk

2. Install network driver

wget [http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE)
unzip -a R151517.EXE

cd DRIVER
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l

3. Test wireless

sudo iwlist scanning

4. Install wireless Manager like wicd or wifi-radar to connect to wifi. 
I have installed wifi-radar and am facing some problem, let me know if it works for you.

For detailed steps refer to link below:

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

---

### Post by pertti on 2010-01-24
I was having problems with the wireless card in my Dell 6400/E1505 in Karmic. I just found the solution, and it was pretty silly... Maybe this can work for you too.

I had two driver choices on System > Administration > Hardware Drivers. I selected STA and activated it, and then rebooted. After logging in, I used the combination in my keyboard to turn the wireless on and off (it's Fn + F2 in my laptop) and it worked! I always thought that the wifi card was already on, because the wifi LED was on.

The inspiration came from this thread: [http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699). A similar problem also reported on this thread: [http://ubuntuforums.org/showthread.php?p=8718187#post8718187](http://ubuntuforums.org/showthread.php?p=8718187#post8718187)

---

