---
title: "Dell WiFi not working in 12.10"
date: 2013-03-10
forum: Networking &amp; Wireless
---

### Post by ashish811 on 2013-03-10
My Dell Inspiron 3421 came pre-installed with Ubuntu 12.04 LTS.
Everything was working including WiFi and Bluetooth.
Then I made a clean install of Ubuntu 12.10 64bit version.
And to my surprise, WiFi was not working. However Bluetooth was working.

Network properties shows the device as 'UNCLAIMED'. And I can't even enable it using 'eth1 up' command.
I searched through the forums and tried few tricks which were marked as SOLVED, but they didn't work for me.

Here are details of my WiFi device from a screenshot in Windows7

Device: **Dell Wireless 1704 802.11b/g/n (2.4GHz)**
Manufacturer: [B]Broadcom

[/B]This system is of my daily use and really need the WiFi to work. Please help me with solutions.

---

### Post by chili555 on 2013-03-10
What is the exact identity of your Broadcom? Run this terminal command and pick out the Broadcom wireless. ```
lspci -nn
```Post the result here.

---

### Post by ashish811 on 2013-03-11
Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)

---

### Post by chili555 on 2013-03-11
Please see: [http://askubuntu.com/questions/259252/wireless-networks-not-working/259264#259264](http://askubuntu.com/questions/259252/wireless-networks-not-working/259264#259264)

---

### Post by ashish811 on 2013-03-11
thats why I love Ubuntu and use it since version 8.04 .....   :)
that worked flawlessly.
Thanks chili555

---

### Post by chili555 on 2013-03-11
> **ashish811 said:**
> thats why I love Ubuntu and use it since version 8.04 .....   :)
that worked flawlessly.
Thanks chili555Can I get a Solved? If so, please edit the title of your thread and add [SOLVED] at the beginning. 

Glad it's working.

For the benefit of all you over-eager searchers, my solution is for this *only*:> Broadcom Corporation BCM43142 802.11b/g/n [[COLOR="#FF0000"]14e4:4365[/COLOR]] If yours is not the same device, then keep searching.

---

### Post by ashish811 on 2013-03-11
did that :)

---

### Post by ashish811 on 2013-03-12
this fix is working but everytime I restart my system, I need to execute this command in the terminal to start  WiFi and get it working:   "  sudo modprobe wl   "
any fix for this ??

---

### Post by chili555 on 2013-03-12
> **ashish811 said:**
> this fix is working but everytime I restart my system, I need to execute this command in the terminal to start  WiFi and get it working:   "  sudo modprobe wl   "
any fix for this ??Let's get wl to load automatically on boot; from a terminal:```
sudo su
echo wl >> /etc/modules
exit
```You should be all set.

---

### Post by ashish811 on 2013-03-12
yup did that and its fine now ...
further to add, my Touchpad went laggy after very 1st restart of doing the WiFi fix install and went inactive in 2nd restart.
However I run the command to enable touchpad and its working fine since then.
Not sure what caused that conflict though

---

### Post by ashish811 on 2013-03-13
> I tried the same steps on one of my colleagues system who has the same laptop but failed
here is the terminal message:
:~/Downloads$ sudo dpkg -i wire*.deb
(Reading database ... 151446 files and directories currently installed.)
Preparing to replace wireless-bcm43142-dkms 6.20.55.19-1 (using wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb) ...

------------------------------
Deleting module version: 6.20.55.19
completely from the DKMS tree.
------------------------------
Done.
Unpacking replacement wireless-bcm43142-dkms ...
Setting up wireless-bcm43142-dkms (6.20.55.19-1) ...
Loading new wireless-bcm43142-6.20.55.19 DKMS files...
Building only for 3.5.0-17-generic
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.

sudo apt-get update
sudo apt-get upgrade
problem was fixed after executing above commands

---

### Post by nickton on 2013-03-17
Hi ashish811,

I have a query and problem of my own which requires advice!

I have the same Dell Inspiron 3421 (i5, 1GB NVIDIA graphics, 4gb RAM, etc.) which came pre-installed with Ubuntu 12.04LTS. I suppose that the version was a specially customised version of Ubuntu by Dell for this 3421 system with in-built drivers,etc. So I made a Dell Ubuntu 12.04LTS recovery disk as they prompted to me the first time I powered-ON my system. Then, I formatted the whole drive, wiped out everything and installed my unused copy of Win-7-Pro-64bit, its working successfully without problems. Now I wanted to load Ubuntu as the secondary dual boot OS to my system with Win-7 being Primary. So i tried the following ways:

1) I Used the Dell Ubuntu Recovery Disk to install ubuntu 12.04 LTS. In the setup interface I selected "LOAD AND INSTALL ONLY MY UBUNTU PARTITIONS". Created the ext4/ and swap for the installations,etc. Everything went on OK and files got copied successfully  The system restarted and the next stage of the setup began where I had to type in computer name, username, password,etc. which I did. Evrything seemed ok. but then the progress bar shows CONFIGURING and the setup stops showing an error message that "Installation has stoped/encounterd a problem/will not continue, Do you want to send error report?" ------------ [B][I]SO IN SHORT THIS OPTION I TRIED OVER AND OVER AGAIN BUT DID'NT WORK. WHY is it happening?Is'nt the recovery medium supposed to work? HOW DO I SOLVE IT?
[/I][/B]
2) Next I downloaded the fresh Ubuntu 12.04LTS 64bit from the Ubuntu website. I loaded it on a PenDrive using the UNIVERSAL USB INSTALLER and tried booting from USB. It booted successfully and shows the 1st option screen Try Ubuntu, Install, Mem Test,etc. But when I select the option Install on Hard Drive/Try Ubuntu the screen goes blank and the same list of options appear again. ------[I][B]WHY is it happening? HOW DO I SOLVE IT?
[/B][/I]
3) I suppose 12.04LTS is always more stable due to the LTS. but will installing the latest 12.10 will help in anyway? Why did'nt the Dell Ubuntu recovery disk work?

What do I do? Can anyone help me? all responses will be appreciated as I am new to Linux/Ubuntu!

---

### Post by ashish811 on 2013-03-17
> **nickton said:**
> Hi ashish811,

I have a query and problem of my own which requires advice!

I have the same Dell Inspiron 3421 (i5, 1GB NVIDIA graphics, 4gb RAM, etc.) which came pre-installed with Ubuntu 12.04LTS. I suppose that the version was a specially customised version of Ubuntu by Dell for this 3421 system with in-built drivers,etc. So I made a Dell Ubuntu 12.04LTS recovery disk as they prompted to me the first time I powered-ON my system. Then, I formatted the whole drive, wiped out everything and installed my unused copy of Win-7-Pro-64bit, its working successfully without problems. Now I wanted to load Ubuntu as the secondary dual boot OS to my system with Win-7 being Primary. So i tried the following ways:

1) I Used the Dell Ubuntu Recovery Disk to install ubuntu 12.04 LTS. In the setup interface I selected "LOAD AND INSTALL ONLY MY UBUNTU PARTITIONS". Created the ext4/ and swap for the installations,etc. Everything went on OK and files got copied successfully  The system restarted and the next stage of the setup began where I had to type in computer name, username, password,etc. which I did. Evrything seemed ok. but then the progress bar shows CONFIGURING and the setup stops showing an error message that "Installation has stoped/encounterd a problem/will not continue, Do you want to send error report?" ------------ [B][I]SO IN SHORT THIS OPTION I TRIED OVER AND OVER AGAIN BUT DID'NT WORK. WHY is it happening?Is'nt the recovery medium supposed to work? HOW DO I SOLVE IT?
[/I][/B]
2) Next I downloaded the fresh Ubuntu 12.04LTS 64bit from the Ubuntu website. I loaded it on a PenDrive using the UNIVERSAL USB INSTALLER and tried booting from USB. It booted successfully and shows the 1st option screen Try Ubuntu, Install, Mem Test,etc. But when I select the option Install on Hard Drive/Try Ubuntu the screen goes blank and the same list of options appear again. ------[I][B]WHY is it happening? HOW DO I SOLVE IT?
[/B][/I]
3) I suppose 12.04LTS is always more stable due to the LTS. but will installing the latest 12.10 will help in anyway? Why did'nt the Dell Ubuntu recovery disk work?

What do I do? Can anyone help me? all responses will be appreciated as I am new to Linux/Ubuntu!


Firstly, post your query to the correct section.

I presume that you tried to install Ubuntu on a separate partition. If not then please do so.
Create a partition from withing Windows or from the Ubuntu installation media where they ask you to select the location to install Ubuntu(Choose the Something Else option).
Try using another PenDrive if you still get the error.
Re-post in the Forums in the CORRECT section to get further help from experts. (I'm just a simple user :)  )

---

