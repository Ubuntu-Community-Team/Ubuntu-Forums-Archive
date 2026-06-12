---
title: "Franklin CDU-680 Wireless Broadband"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by nesplayer777 on 2010-01-08
So I got a Franklin CDU-680 Wireless Broadband Modem and this manual included instructions on installing the modem on Linux, specifically Ubuntu. So I tried to follow the simple instructions and I am troubleshooting. Here are the instructions: 

Copy the Linux Folder from your device to your Desktop  Open terminal 
  cd to Desktop/Linux  
Run "sudo ./connect"  
Enter root password 
 Device will switch to modem mode and attempt to connect.   

Ok, so here's the problem. I changed my directory to Desktop/Linux under the Terminal, and then typed in sudo ./connect as the instructions said, and the outcome of that input is this:    
j@ubuntu:~$ cd Desktop/Linux 
j@ubuntu:~/Desktop/Linux$ sudo ./connect 
[sudo] password for j:  
sudo: unable to execute ./connect: No such file or directory
j@ubuntu:~/Desktop/Linux$   

So I browsed the directory on my Desktop GUI, and sure enough the "connect" application exists in the directory. The terminal somehow just couldn't recognize the file. Or maybe I am doing something wrong. Please help me correcting this issue. Thanks!  P.S. My ISP for this mobile broadband is a local company; not Verizon, AT&T, Sprint, etc.

---

### Post by pdc on 2010-01-09
if we start from near the beginning

if you open a terminal and type two letters in it

> ls

that is asking the computer to list the various directories that are there: eg Documents, or Downloads or Pictures ??

maybe it says Desktop amongst the list

if so, now type in the command

> cd Desktop  .. *if that is how Desktop is spelt* ..

that should get you "inside" Desktop

now type

> ls

that should tell you what is in/on the Desktop

now in your terminal type this command (you can copy it from here)

> sudo ./connect

.. *it should ask you for your sudo password* .........

what has happened when you do this?

---

### Post by nesplayer777 on 2010-01-09
The only item on my desktop is the Linux folder, which contains the programs to connect to the Internet, thus I think it's irrelevant to do a ls on the Desktop directory. But if you still recommend me doing it then I will do it. :)

j@ubuntu:~$ cd Desktop/Linux 
j@ubuntu:~/Desktop/Linux$ ls 
[COLOR=Red]connect[/COLOR]  execute.sh  itfchg  Linux connect steps_CDU680.txt 
j@ubuntu:~/Desktop/Linux$ sudo ./connect 
[sudo] password for j: 
sudo: unable to execute ./connect: No such file or directory 

So I tried again:

j@ubuntu:~/Desktop/Linux$ ls 
[COLOR=Red]connect[/COLOR]  execute.sh  itfchg  Linux connect steps_CDU680.txt 
j@ubuntu:~/Desktop/Linux$ sudo ./connect 
sudo: unable to execute ./connect: No such file or directory 

The one highlighted in in red is the program I am attempting to execute but the terminal just doesn't. Strange enough it does prompt me for my root password, and so I type in the correct password, and then the output is [COLOR=Lime]No such file or directory[/COLOR].

Is it just me or this just doesn't make any sense?

In case it matters, I am running Ubuntu under the Wubi installer for Windows. I assume it shouldn't matter, but does it?

---

### Post by pdc on 2010-01-09
so it looks like this is what you want to use

[http://www.fklt.com/product-usb.php](http://www.fklt.com/product-usb.php)

the CDU-680 is bottom right?

1) Well, are you using Ubuntu 9.10?

2) open a terminal; type in

> uname -r

tell us the results

3) When you plug the modem in, does an icon appear on your desktop?

4) right-click on this icon: select "Eject" from the menu

in a terminal type

> lsusb

copy and paste the results back here

___________________________

Let's see what a standard configure gives: what about right-click on network manager; on the top line at the right?

5) Try to configure the network you want to connect to:by:

Select EDIT CONNECTIONS from network manager; on the top line to the right: RIGHT-CLICK

Select MOBILE BROADBAND (third along on the menu line)

Select ADD

Select COUNTRY;

Select NETWORK;

Click to close if you got it all done;

now LEFT-CLICK on network manager:

any joy?

The reason I ask is the Franklin looks like it has been hard work in the past

[http://ubuntuforums.org/showthread.php?t=691687](http://ubuntuforums.org/showthread.php?t=691687)

maybe it is less hard now !!

---

### Post by pdc on 2010-01-09
in post #3 what I was wanting you to do was help us understand what files were where:

so if I open a terminal I get

> pdc@pdc-desktop ~ $ 

if I now type in 

> ls

I get this answer 

> Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos

those are all Directories (or Folders) in my system

if I now want to get inside the directory called Desktop 

I type ( in a terminal)

> cd Desktop   (and hit enter)

and I get 

> pdc@pdc-desktop ~/Desktop $

and there is nothing listed there as I have no files stored there ...... but you might

does that make it clearer, what was asked?

---

### Post by pdc on 2010-01-10
well, nesplayer777;

this device intrigued me and I did some more reading;

seems like ........ with many devices ........

it comes loaded with windows software, so linux sees it as a CD-ROM device; you need to "flip" the device so linux now sees it as a modem;

the twist to the Franklin device is it comes with software that should run Ubuntu; so folks report it working up till 7.04 or so;

so the software for Ubuntu they provide seems to do two things:

1) flip the device so it is seen as a modem
2) runs wvdial to connect


HOWEVER: there seems much DOUBT now that the linux software works ............


so can one do without it?

when one looks around for howto "flip" the device, the programme usb_modeswitch has been advocated;

your device gains mention there; (so confirming it is seen as a CD-ROM device first, and needs flipping)

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=69](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=69)

and there was some debate about what exact data to enter to get it to work;

however the person posting there said the linux software DID NOT WORK for them; it is buggy; yes, that is only one person's view but I have seen it a couple of times now; eg this VERY, VERY long post

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=4316123](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=4316123)

the good news should be also you don't need to use usb_modeswitch;

if you see an icon on the desktop, do as 3) and 4) and 5) in post #4 above

---

### Post by nesplayer777 on 2010-01-11
Forgive me if I am not responding too soon. :) 

I had a big day yesterday and had no time on the computer. I am typing this up on Windows, and I have Wubi installed with Ubuntu. So later today I'll boot my Ubuntu virtual drive (Wubi) and give these a whirl and tell you the results. I really appreciate all the support I am getting. Thanks! :)

---

### Post by nesplayer777 on 2010-01-16
So I decided to ditch this program that allows me to connect my mobile broadband Internet, so I want to try out the built-in mobile broadband setup that's included in network connections. I did as you instructed, but when I LEFT-CLICK, I am not seeing my mobile broadband connection on the list...

---

### Post by pdc on 2010-01-16
I believe you need to "flip" your device before it is recognised as a modem;

I mentioned looking to see if it created an icon on your desktop; 

with the modem plugged in, does an icon for it appear?

with some modems, if you select the "eject" option from the menu for that icon, you "change" the device, and linux will see it as a different device

If the above does not work, you need to install usb_modeswitch (as in post #6 above)

come back to us

...... by the way ......... in post #4 we asked for 

> uname -r

and 

> lsusb

could you help us by supplying those?

---

