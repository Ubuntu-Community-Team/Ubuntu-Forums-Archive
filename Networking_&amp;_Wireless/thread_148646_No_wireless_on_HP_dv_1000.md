---
title: "No wireless on HP dv 1000"
date: 2006-03-22
forum: Networking &amp; Wireless
---

### Post by adelinh on 2006-03-22
Hi, I can't seem to get my wireless to work on my laptop. I can connect throught the ethernet, but my wireless light does not turn on. Why can't I connect? I am extremely new to this, but it interests me and want to learn more about it. Thanks

---

### Post by jasondean on 2006-03-22
Hello, this link should get u started in the right direction. :) 

[http://www.ubuntuforums.org/showthread.php?t=25683]("http://www.ubuntuforums.org/showthread.php?t=25683")

---

### Post by adelinh on 2006-03-22
How do I run the commands?

---

### Post by arnieboy on 2006-03-22
applications --> accessories --> Terminal

---

### Post by adelinh on 2006-03-22
Still lost, I downloaded the automatix wi-fi GUI but the wireless light is still off, and I cant really follow what the link that jason sent me says.

---

### Post by adelinh on 2006-03-22
Actually, I noticed the network does not even show it on the options. It only shows the eth0 and the dial up, which I won't use. I have been trying for hours, please help. Thanks.

---

### Post by jasondean on 2006-03-22
for the link i posted you can pretty much cut and paste what the author wrote, I also have a dv1000 laptop and thats what i used my wifi up and running

---

### Post by adelinh on 2006-03-22
How do I find those files on an HP. These files: bcmwl5.inf or bcmwl5a.inf

---

### Post by jml on 2006-03-22
The files you are looking for can be found in one of two places.  If you still have Windows installed on your laptop, you can use windows search feature to look for them.  If you have already removed Windows from your laptop, you should be able to find the files on the CD that comes with your laptop.  I have an hp nx6110 and it comes with an Application and Recovery DVD.  Your laptop should have a similar CD or DVD.  Just search the disc for the file.  If you don't have the disc either, as a last resort, go to the HP website and look for the download link.  There should be an area on the site to download various drivers for the laptop.  The advantage of going to the web site is that the drivers available for download may be more current than the ones you have available on the computer or on the supplied disc.  Hope this helps.

Joe

---

### Post by adelinh on 2006-03-22
How am I supposed to get these files if I can't access anything from the C drive?

---

### Post by jasondean on 2006-03-23
I installed the files the from cd that came with the laptop, if u dont have the cds and arent sure how to mount a drive in linux, easiest thing would be to log back into windows and copy the files to a disk or thumbdrive from there. Also they are on HP website under support

---

### Post by adelinh on 2006-03-23
Do I need to have the ubuntu installed, or can I do this from the live CD, not that it matters, I aready had to put a fresh copy of Windows from erasing it earlier. I want to give up because it is taking DAYS now to get this working. Why does everything else work except the darn wireless?

---

### Post by jasondean on 2006-03-23
It should also work from live cd granted you would have to reset up the computer everytime you boot.  The first link i gave you is the best i'v seen for setting up wireless.  Since you are new at Linux/Ubuntu it may be better to learn about filestructure, basic commands first, that way the instructions wont  seem like greek.

---

### Post by jml on 2006-03-24
I may have missed something when I read your earlier posts.  Why can you not acces your C drive?  Do you no longer have Windows installed on the laptop? Or is it that you can't read the C drive from within Linux?  

If Windows is still on the drive you can either find the file from within Windows and copy the file to a CD.  Then boot into linux, mount the CD and then you will have access to the driver from within Linux.

If You no longer have Windows on the laptop, you can get it off the recovery CD.

Joe

---

### Post by adelinh on 2006-03-24
So I don't have the live CD in the drive? I thaught it always had to be in the drive for it to run. I also looked on search in windows for those files but couldn't find them. I have the restore CD, but how do I get those specific files?

---

### Post by adelinh on 2006-03-24
How do you read the C drive from Linux?

---

### Post by bluestorm on 2006-03-26
Hi.
I came to this forum looking for some issues with a dv1000, and i just saw that you may need some help.

First of all, please be tolerant to my awful english. Then you should know i am very new to ubuntu too, so some of my answers may not be The-Simpliest-Way-To-Do-It.

Then, i may answer to you two questions :
   - how to access to the windows drive ?
   - how to connect over the wifi ?

In order to access to the windows drive, you should first look into the /windows (it might not exist) and /media directories : during installation, ubuntu may have automatically detected you windows partition, and set a mount point (a directory where you can access another drive or partition or usb key, and so on...) in these directories.

If no directory related to windows exist, then you have to mount it yourself. It's a little bit more difficult, and it's not the main purpose of my post (at the beginning i just wanted to help you about the wifi) so i will just give you a link to the ubuntu wiki :
[MountingWindowsPartitions]("https://wiki.ubuntu.com/MountingWindowsPartitions")
I think this article could be better. But hey, it's a wiki, so it surely will become a great article one day : just read it and keep the URL.


About the wifi, i installed it yesterday. I didn't used any GUI tool, and what i have done is kind of a little trick, maybe not the conventional way to do it.

It was based upon the scripts i use on my debian to connect to the wifi, so the structure is a little weird (and i am a really bad scripter) :
 - i putted a script named */etc/network/inet_wireless_home.sh* :```
#!/bin/bash
IFACE=$1
iwconfig $IFACE nick bluestorm mode Managed
iwconfig $IFACE rate Auto
iwconfig $IFACE essid "my_network"
#iwconfig $IFACE key on
iwconfig $IFACE key 013456789 [1]
#iwspy $IFACE mac-address

```

(this script was first designed to be in a pre-up of /etc/network/interface, that's why i choose this directory).

You may change the nick (bluestorm), the essid, and the key. If you don't use a key, just use it (WEP sucks, but it's still better than nothing) or comment the 'key ...' line.

Then i putted a script in my ~ (dirty place), named *network.sh* containing :
```
#!/bin/sh
sh /etc/network/inet_wireless_home.sh eth1
dhclient eth1
```

(if you don't use dhcp, just erase the last line).

After booting, the important point is that you have to push the "wifi" button :
**even if the led is inactive, the network get enabled/disabled when you press the button**

After have pressed this button, just do "sudo sh network.sh", and the network will (should) be on.

Of course, this must not be the best way to do it (finding a way to have it started automatically at boot would be nice), but, well, it works.

(i was initially looking for a way to activate the led. In the laptop page, the one reporting the dv1000 issue say that "sudo modprobe ipw2200 led=1" should be ok, but here it doesn't work).



EDIT : i just had it working much better.

First, i loaded the ipw2200 at boot time, by adding "ipw2200 led=1" in the */etc/modules* file.
Then, i wrote the */etc/network/interfaces* file :
```
auto eth1
iface eth1 inet dhcp
   pre-up /etc/network/inet_wireless_home.sh eth1

```

Then, i used the "System Services" application in the Administration panel to have "networking" launched at boot time (you need to go in "administrator mode" fot that).

Now, i have the led working, and the wifi setting up automatically at boot time.

---

