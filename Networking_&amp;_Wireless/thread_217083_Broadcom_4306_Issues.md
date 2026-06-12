---
title: "Broadcom 4306 Issues"
date: 2006-07-16
forum: Networking &amp; Wireless
---

### Post by UberIcarus on 2006-07-16
I'm trying to use the guide here:

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

But when I click on the link:  

[http://drinus.net/airport/wl_apsta.o](http://drinus.net/airport/wl_apsta.o)

I get a prompt to download wl_apsta.htm and wl_apsta.o So I removed the last part from the link and I found a link to 4 different files marked bcm43xx-fcutter-00(1,2,3,4,).tar.bz2

I extracted all 4 to my desktop in separate folders, but using the command: sudo apt-get install bcm43xx-fcutter 
nets me the following error:
Reading package lists... Done
Building dependancy tree... Done
E: Couldn't Find Package bcmx43xx-fwcutter

So I really can't continue with the guide if it can't find the package =(

Edit: Oh, and this is my first time ever using linux, so don't assume I know how to do anything the right way, lol. =)

---

### Post by Jagot on 2006-07-16
bcm43xx-fwcutter is in the universe repo, so the reason you may not be able to obtain it is that you have not enabled that repository yet.  See here:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by S.nazari on 2006-07-16
If someone has no internet connection what good would truning on the repo. do?

---

### Post by UberIcarus on 2006-07-16
Okay, thought I had added the repositories, but I hadn't. So I figured out how to do that...and it told me to reload synaptic package manager, which I did...and it tries to download 9 files, which since I have no internet connection it can't do.

Still does not find bcm43xx

---

### Post by UberIcarus on 2006-07-17
bump....anyone?

---

### Post by UberIcarus on 2006-07-17
Bump again. Can anyone tell me what I'm doing wrong?

---

### Post by flashblue on 2006-07-17
you need to have an internet connection to get the bcm43xx-fwcutter
plug in an ethernet cable to your router to your computer then run
"sudo apt-get install bcm43xx-fwcutter" in a terminal Applications > Accessories > Terminal
Then after installing fwcutter run
"bcm43xx-fwcutter -w /lib/firmware /path/to/wl_apsta.o"
then run iwconfig, see which devce supports wireless, probably eth0 then run "iwconfig eth0 essid NAME_OF_NETWORK"
this should work, it worked for me...
EDIT: you can configure it with System > Administration > Networking after you installed the firmware...
then reboot, it should start automatically

---

### Post by UberIcarus on 2006-07-17
thanks flashblue.

However I'm still having difficulties. I followed the instructions of the guide mentioned above, and when I go to put the drivers in the kernal folder I get this:

sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-25-386 /home/jackfrost/Desktop/wl_apsta.o
fwcutter can cut the firmware out of /home/jackfrost/Desktop/wl_apsta.o
  filename :  wl_apsta.o
  version  :  3.130.20.0
  MD5      :  e08665c5c5b66beb9c3b2dd54aa80cb3

extracting bcm43xx_microcode2.fw ...
/lib/firmware/2.6.15-25-386/bcm43xx_microcode2.fw: No such file or directory

Is it because the firmware has allready been cut out of wl_apsta.o?

In any event, the light on my laptop will still not come on. Should I try using ndiswrapper instead? If so, would I go about removing everything?

---

### Post by UberIcarus on 2006-07-17
okay, I think I may have got it working. When I open the default network manager with Ubuntu the light comes on. I still can't figure out how to configure it. I installed network-manager-gnome...but I can't seem to find out how to open that program, It's on here somewhere but I have no GUI interface for it. Any suggestions? The light coming on is pretty good I guess. I want a way to search for available wireless networks, etc.

---

### Post by UberIcarus on 2006-07-17
trying to use the guide presented here: [http://www.ubuntuforums.org/showthread.php?t=201902](http://www.ubuntuforums.org/showthread.php?t=201902)

This is what I get


jackfrost@jackfrost-laptop:~$ sudo ndiswrapper -i ~/home/jackfrost/Desktop/bcmwl 5.inf
Installing bcmwl5
couldn't copy /home/jackfrost/home/jackfrost/Desktop/bcmwl5.inf at /usr/sbin/ndi swrapper line 135.
jackfrost@jackfrost-laptop:~$ sudo ndiswrapper -i ~/home/jackfrost/Desktop/bcmstuff/bcmwl5.inf
bcmwl5 is already installed. Use -e to remove it
jackfrost@jackfrost-laptop:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  invalid driver!
jackfrost@jackfrost-laptop:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-26-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
jackfrost@jackfrost-laptop:~$

---

### Post by flashblue on 2006-07-17
what brand of computer do you have?
also
run
"```
sudo bcm43xx-fwcutter -w /lib/firmware /path/to/wl_apsta.o
```"
just /lib/firmware not 2.6.15 folder
then run "```
sudo modprobe bcm43xx
```"
If you have an apple computer ndiswrapper will not work
after this run ```
iwconfig eth0 rate 11M
```
```
iwconfig eth0 essid WIRLESS_NETWORK_NAME
```and configure the rest with network manager
you dont need network-manger-gnome but to run it type nm-applet in a terminal
to scan for wireless networks run
```
iwlist eth0 scan
``` add sudo if necessary

---

### Post by flashblue on 2006-07-17
if you need further help, pm me

---

### Post by UberIcarus on 2006-07-18
Okay, the light on my wireless card in my laptop comes on now. The laptop is a compaq 2210US. I abandoned the ndiswrapper method, and am now using fwcutter. Only problem is when I open the network manager, my wireless card shows up as a wired connection. When I use eth1 scan (my wifi card is eth1, the actual working wired network is eth0), it shows up nothing. I'm sitting right next to my wireless router.

---

### Post by UberIcarus on 2006-07-18
Any suggestions anyone? This is really frustrating. Further info, when I hit activate for eth1 (the wifi card) under networking GUI, I get no lights coming on from my wifi. Only when I hit "Ok" Does the light come on. Still no fuctionality. using nm-applet I seem to be bringing up a duplicate of my eth0 connection. THe light seems to come on mostly when I start up Networking (GUI), And then goes off.

---

### Post by UberIcarus on 2006-07-19
Problem solved: (I think). I can now scan, find other connections, etc.

The only small problem I had was nm-applet made my computer lockup when I tried connecting to "Cell 1" instead of the ESSID "tmobile" (There are about 10 different signals for tmobile where I'm at, and they all have the essid of tmobile" so I think that nm-applet was getting confused)

Is there any more well, user friendly network manager gui? One where I can scan, see all active wireless connections and then just click on the damn thing?

Nevermind, on reboot network manager sees the other available networks, still has trouble connecting to TMobile, but I know it's up and running and can scan on its own.

Something some of the people who write guides for getting ndiswrapper to work might want to note: bcmwl5.inf did not work for me, that was the only problem. I had to use bcmwl5**a**.inf

---

