---
title: "mobile broadband can't connect"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by nikus@rocketmail.com on 2010-01-15
Just loaded Ubuntu 9.10 on a Dell 5100, (XP finally got the bsod) I have verizon mobile broadband, all was very good until I realized I cannot connect wirelessly. The usb modem was not recognized, there is no indication of any wireless connection. There is no icon and nothing happens when the usb modem is plugged in.
I have been working on this for hrs & hrs.
Can someone help
I am a complete novice on Linux, but CompT1 A certified on PC's
Thanks

---

### Post by pdc on 2010-01-15
so you don't get any icon appearing on the desktop when you plug the modem in?

If you open a terminal: in the Accessories menu?

copy and paste these commands, and copy and paste back the results

> uname -r 

and 

> lsusb

the first should tell us the exact version number you use, and the second asks the computer to list (ls) the usb devices that are connected to it

---

### Post by nikus@rocketmail.com on 2010-01-15
ndy@wendy-laptop:~$ uname -r
2.6.31-17-generic
wendy@wendy-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 106c:3714 Curitel Communications, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
wendy@wendy-laptop:~$ 

This is what came back

---

### Post by alexfish on 2010-01-15
hi 

can you these commands from the terminal

Code:

  	 	 	 	 	 	  modprobe -r usbserial
 

 modprobe usbserial vendor=0×106c product=0×3714
 

 

 mesg|grep -i ttyUSB
 

 lsusb

---

### Post by nikus@rocketmail.com on 2010-01-15
wendy@wendy-laptop:~$ modprobe -r usbserial
wendy@wendy-laptop:~$ modprobe usbserial vendor=0×106c product=0×3714
FATAL: Error inserting usbserial (/lib/modules/2.6.31-17-generic/kernel/drivers/usb/serial/usbserial.ko): Operation not permitted
wendy@wendy-laptop:~$ mesg|grep -i ttyUSB
wendy@wendy-laptop:~$ 
wendy@wendy-laptop:~$

---

### Post by alexfish on 2010-01-15
sorry 

you should be in root

Code:

sudo su

then repeat the above

---

### Post by nikus@rocketmail.com on 2010-01-15
remind me how to get into root

---

### Post by nikus@rocketmail.com on 2010-01-15
Ok I remembered

wendy@wendy-laptop:~$ sudo -i
[sudo] password for wendy: 
root@wendy-laptop:~# modprobe -r usbserial
root@wendy-laptop:~# modprobe usbserial vendor=0×106c product=0×3714
FATAL: Error inserting usbserial (/lib/modules/2.6.31-17-generic/kernel/drivers/usb/serial/usbserial.ko): Invalid argument
root@wendy-laptop:~# mesg|grep -i ttyUSB
root@wendy-laptop:~# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 106c:3714 Curitel Communications, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@wendy-laptop:~#

---

### Post by alexfish on 2010-01-15
hi

can you these commands from the terminal

also when prompted enter your password

Code:

sudo su

modprobe -r usbserial


modprobe usbserial vendor=0×106c product=0×3714




mesg|grep -i ttyUSB


lsusb

then when finished to exit root 

Code:

exit

"your post got there before mine"

---

### Post by nikus@rocketmail.com on 2010-01-15
wendy@wendy-laptop:~$ sudo su
[sudo] password for wendy: 
root@wendy-laptop:/home/wendy# modprobe -r usbserial
root@wendy-laptop:/home/wendy# exit
exit
wendy@wendy-laptop:~$ modprobe -r usbserial
wendy@wendy-laptop:~$ modprobe usbserial vendor=0×106c product=0×3714
FATAL: Error inserting usbserial (/lib/modules/2.6.31-17-generic/kernel/drivers/usb/serial/usbserial.ko): Operation not permitted
wendy@wendy-laptop:~$ mesg|grep -i ttyUSB
wendy@wendy-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 106c:3714 Curitel Communications, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
wendy@wendy-laptop:~$ 
wendy@wendy-laptop:~$

---

### Post by pdc on 2010-01-15
I think Alex wanted you to run all these command as the sudo su

> sudo su

> modprobe -r usbserial

> modprobe usbserial vendor=0×106c product=0×3714 

> dmesg|grep -i ttyUSB 

> lsusb

and then to exit as substitute user, (su) you type exit;

I think

---

### Post by nikus@rocketmail.com on 2010-01-15
From Root

root@wendy-laptop:/home/wendy# modprobe -r usbserial
root@wendy-laptop:/home/wendy# modprobe usbserial vendor=0×106c product=0×3714
FATAL: Error inserting usbserial (/lib/modules/2.6.31-17-generic/kernel/drivers/usb/serial/usbserial.ko): Invalid argument
root@wendy-laptop:/home/wendy# mesg|grep -i ttyUSB
root@wendy-laptop:/home/wendy# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 106c:3714 Curitel Communications, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@wendy-laptop:/home/wendy# exit
exit

---

### Post by nikus@rocketmail.com on 2010-01-15
All commands from the beginning in Root ?

---

### Post by alexfish on 2010-01-15
hi

can you post the model number of this device IE Verizon "XXXX"

also try to make a connection with gnome ppp . or wvdial

---

### Post by nikus@rocketmail.com on 2010-01-15
The USB device is a Pantech UM175VW, I tried to download a device driver from Verizon, but it would fail at download each time.
I'm not sure what these are or how to use them.
gnome ppp . or wvdial

---

### Post by pdc on 2010-01-15
here's a post on gnome-ppp

[http://www.jasons.org/2008/09/02/howto-verizon-um175-usb-evdo-card-under-ubuntu-hardy/](http://www.jasons.org/2008/09/02/howto-verizon-um175-usb-evdo-card-under-ubuntu-hardy/)

see if any of that works for you

---

### Post by nikus@rocketmail.com on 2010-01-15
Thank you, I'll keep working on it

---

### Post by alexfish on 2010-01-15
if you have gnome ppp installed ;ask your provider for the details that are required by the input boxes

---

### Post by Loosewheel on 2010-01-16
> **nikus@rocketmail.com said:**
> Thank you, I'll keep working on it

Hi nikus,
Did you already right click NetworkManager-> Edit Connections-> Mobile Broadband-> Add a New Connection, and set it up? If not you might want to reboot, just for drill, and give that a go. And After setting up the connection plug in the device, click on NM and select the connection.
(Oh, and cross you fingers :)

---

### Post by nikus@rocketmail.com on 2010-01-16
My options in system are only "network connections"  & "network tools"

I can see "Network Manager" in the file system, but do not get the edit option when I right click or open the file.

---

### Post by nikus@rocketmail.com on 2010-01-16
Thank you all for your assistance, I'm am just not able to get this to work,

Is there a remote assistance option or program for Linux Ubuntu?

---

### Post by Loosewheel on 2010-01-16
> **nikus@rocketmail.com said:**
> My options in system are only "network connections"  & "network tools"

I can see "Network Manager" in the file system, but do not get the edit option when I right click or open the file.

nikus, you should have a 'NM Icon' in the top right of the panel.(By the Volume Control and Clock). That is what you want to right click on to 'Edit Connections'.

And click on System-> Help and Support-> Internet and Networks. Sections 2.3 Connecting Mobile Broadband, and section 5.3 Troubleshooting may help.

---

### Post by pdc on 2010-01-16
loosewheel is guiding you to configure using network manager

click on this link

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

go halfway down the page to where it says:

> **_Create a Mobile Broadband connection_**

follow the instructions there

You should be looking at the TOP-RIGHT on the TOP BAR:

---

### Post by nikus@rocketmail.com on 2010-01-16
I have an envelope icon, the clock and name in the upper right, nothing else.

---

### Post by nikus@rocketmail.com on 2010-01-16
I found NM icon and the sound icon and put them in the panel,I had set up and tried to configure these already

---

### Post by pdc on 2010-01-16
this post would suggest you check the APN settings 

[http://www.jasons.org/2008/09/12/using-networkmanager-with-pantech-um175-under-ubuntu-hardy/](http://www.jasons.org/2008/09/12/using-networkmanager-with-pantech-um175-under-ubuntu-hardy/)

the guy said

> Go to the Mobile Broadband tab, add a new connection.

7. I only filled in a name for the connection, used the following parameters:

Phone Number: #777
Username: <phonenumber> @vzw3g.com (use your device’s phone # here)
Password: vzw
Check the “System Setting” box.

If you go back to NM, and select edit for the connection you did, does your setup look like this?

Seems like they will have give you a phone number ... eg 112233

so your system would say (for phone no 112233) .. in the Username section .......... the entry  would be ...... [email]112233@vzw3g.com[/email]

---

### Post by nikus@rocketmail.com on 2010-01-16
This is exactly how I have set it up, there is no system settings box in that window.

---

### Post by pdc on 2010-01-16
this link 

[http://forums.atomicmpc.com.au/index.php?showtopic=7990](http://forums.atomicmpc.com.au/index.php?showtopic=7990) (post #9)

got success by editing the file

/usr/share/hal/fdi/information/10freedesktop/10-modem.fdi

If we get you to issue the command 

> gedit /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi

and using the Search/Find option on the top menu of the text editor that you have opened; that is called gedit; 

look for an entry

> 0×3714

the reason I ask is that this post

[http://www.jasons.org/2008/09/12/using-networkmanager-with-pantech-um175-under-ubuntu-hardy/](http://www.jasons.org/2008/09/12/using-networkmanager-with-pantech-um175-under-ubuntu-hardy/)

talked of 

> At line 175, add a couple of USB ids, specifically 0×3711 and 0×3714, so the line looks like:

<match key=&#8221;@info.parent:usb.product_id&#8221; int_outof=&#8221;0×3701;0×3702;0×3711;0×3714&#8243;>

and that is where the top post got his success

I guess if you DO NOT HAVE the 0x3714 entry, you CLOSE gedit and issue the command

> sudo gedit /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi ...... enter your sudo password ......

and add the lines as suggested above, by carefully copying and pasting them

---

### Post by Loosewheel on 2010-01-16
> **nikus@rocketmail.com said:**
> This is exactly how I have set it up, there is no system settings box in that window.

Did you happen to notice the last post in that link pdc gave you? 
Here it is:

"One thing to note.  Before Verizon’s UM175 (I assume this is true with other CDMA devices and providers but I don’t know) will work in Linux, it MUST be used in Windows or OS X (using Verizon’s VZAccess program)  to activate the device.  I spent the better part of three days banging my head wondering why it didn’t work.  I tried it in my Mac to make sure it was good hardware, the software activated it, and now it works like a charm!"

Has the device been activated with VZAccess?

---

### Post by nikus@rocketmail.com on 2010-01-16
I've edited the files and checked them 3-4 times, they are exactly as listed. The device was being used on XP before it crashed.  Line 175 is correct, 0x3714 is there, 

I plugged the device into my desktop w/Vista, worked perfectly

---

### Post by nikus@rocketmail.com on 2010-01-16
Correction, it did not work on my desktop with Vista, it was connecting to MY wireless modem,  I turned it off and it did not connect to vzn.
back to square one

---

### Post by pdc on 2010-01-16
instead of trying network manager, if you try wvdial

> sudo apt-get install wvdial

then 

> sudo wvdialconf

that should create a file in the directory /etc called wvdial.conf

so if you want to look at it 

> gedit /etc/wvdial.conf

and if you want to edit it, to change the entries

> sudo gedit /etc/wvdial.conf

and to connect, if from a terminal you run 

> sudo wvdial

it should dial and connect 

and you should be a member of the group dialout and (I believe) dip

here

[http://www.pharscape.org/HSOconnect-Ubuntu-8.04.html](http://www.pharscape.org/HSOconnect-Ubuntu-8.04.html)

paul looks to see if he is in the group dialout

> Am I in the dialout group?

paul@r60-ubuntu:~/Desktop/hsoudev$ grep dialout /etc/group dialout:x:20:paul 
paul@r60-ubuntu:~/Desktop/hsoudev
$ 

Yes I am 


 If I was not in the dialout group then I could use the command:

usermod -a -G dialout paul


google search for yourself on how to ensure you are a member of these two groups, and how to add yourself if you are not

---

### Post by nikus@rocketmail.com on 2010-01-18
Finally figured it out.
 
It was not Verizon or Linux that caused the problem, 
what I found out was the USB modem had locked itself from months of inactivity,
I turned off my wireless modem and unhooked the network cable from my Vista system.
Then installed the vzm manager again and plugged in the usb modem, a new screen popped up asking to re-activate the usb modem,, I clicked yes, I proceded to finish the install and then could get on line with the wireless usb modem.
 
I shut down my desktop system and then plugged it into the laptop running Linux, it came up instantly and connected!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
  **[COLOR=black]_One note_[/COLOR]: All other possible internet connections MUST be diabled for the usb modem to connect to verizon**.
 
Thank you all for your help and efforts, GREATLY APPRECIATED!!

---

