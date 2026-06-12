---
title: "Complete noob help me please"
date: 2012-03-18
forum: Networking &amp; Wireless
---

### Post by nashy10 on 2012-03-18
Look i  know how forums work and im sure people will be mad at me for posting this but im on a dell inspiron 6400, and windows never worked for me, i decided to put ubuntu on. So i did, only issue is wifi, ive spent a decent 3 hours looking up the drivers and things like that but its all extremely complicated and i have no idea how to even use this OS yet. could someone please give me a step by step guide on how to fix this? I feel  retarded not knowing this OS.

---

### Post by 2F4U on 2012-03-18
You first need to find out what network card is installed in your machine:

[http://ubuntuforums.org/showthread.php?t=1754291](http://ubuntuforums.org/showthread.php?t=1754291)

---

### Post by nashy10 on 2012-03-18
I entered the command in terminal to show me the wireless :
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:efdfc000-efdfffff

---

### Post by chili555 on 2012-03-18
@nashy10--

Nobody is going to get mad at you or even impatient because you are a new user and just learning Ubuntu Linux. All of them had a first day, too; even me. If someone is rude to you, a lot of people will be mad at them! Ask all the questions you need to and don't be shy about it.

This is 2F4U's thread to answer and I hate to step on toes. There is one thing you might try if you can hook up an ethernet connection. Open a terminal and do:```
sudo apt-get install b43-fwcutter firmware-b43-installer
```OK, back to you 2F4u!

---

### Post by nashy10 on 2012-03-19
tried this command, completed successfully with no effect.

---

### Post by chili555 on 2012-03-19
You may need to reboot. Please show us:```
dmesg | grep b43
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by nashy10 on 2012-03-19
rebooted, no effect. copy and pasted that command into terminal, results:

nash@ubuntu:~$ dmesg | grep b43
[   35.427523] b43-pci-bridge 0000:0b:00.0: setting latency timer to 64
nash@ubuntu:~$ lspci -nn | grep 0280
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
nash@ubuntu:~$

---

### Post by BertN45 on 2012-03-19
Before you install the drivers, you have to deactivate the driver from from the menu "additional drivers" or "hardware drivers". Else that old one will block the new drivers you just installed.

---

### Post by nashy10 on 2012-03-19
i did this then ran the command again, result:

> nash@ubuntu:~$ sudo apt-get install b43-fwcutter firmware-b43-installer
[sudo] password for nash: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
firmware-b43-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  fakeroot dkms patch
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 356 not upgraded.
nash@ubuntu:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
nash@ubuntu:~$ 




---

### Post by chili555 on 2012-03-20
> $ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?It wants you to do:```
[COLOR="Red"]sudo[/COLOR] apt-get autoremove
```You have the firmware in place correctly, otherwise *dmesg* would complain loudly; it did not. You might just confirm it with:```
ls /lib/firmware/b43
```Do you see all sorts of ucode files, etc.? No need to post here if you do.

Let's dig deeper:```
rfkill list all
```Thanks.

---

### Post by nashy10 on 2012-03-20
first command result:
nash@ubuntu:~$ ls /lib/firmware/b43
ls: cannot open directory /lib/firmware/b43: Permission denied
nash@ubuntu:~$ sudo ls lib/firmware/b43
ls: cannot access lib/firmware/b43: No such file or directory
nash@ubuntu:~$ 

i tried to add sudo to see if it would help, guess that didnt really do anything :P, and this is what i got for rfkill list all:
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by chili555 on 2012-03-20
> ls: cannot open directory /lib/firmware/b43: Permission deniedThat's a new one on me! Just when I think I've heard everything...

Please do:```
sudo su
cd /lib/firmware/b43 
```Any complaints or warnings? If not, then do:```
chmod 644 *
```Now do you see the ucode files when you do:```
ls -al
exit
```

---

### Post by nashy10 on 2012-03-20
yeah i see a bunch of ucodes

---

### Post by chili555 on 2012-03-20
Excellent! Now do you have a wireless interface?```
iwconfig
```Does it scan?```
sudo iwlist wlan0 scan
```Can you click the Network Manager icon and see your network? Can you click and connect?

---

### Post by nashy10 on 2012-03-20
nope, got more issues :(
nash@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

and then i got this 

nash@ubuntu:~$ sudo iwlist wlan0 scan
[sudo] password for nash: 
wlan0     Interface doesn't support scanning.

---

### Post by chili555 on 2012-03-20
Something is not quite right. Let's see if we can diagnose it. We are going to get some logs into a text file, zip them and please post the zip file as an attachment to your reply using the paperclip tool at the top of the reply box. Reboot so we have a clean slate.

Open a terminal and do:```
dmesg > nashy.txt
lsmod >> nashy.txt
ls -al /lib/firmware/b43 >> nashy.txt
zip nashy.zip nashy.txt
```You will find the file nashy.zip in your user directory. Please attach it to your reply.

---

### Post by nashy10 on 2012-03-27
Hey um well i rebooted because i half gave up on this whole ubuntu thing. But then i booted and it said recovery i pressed it it did something and now the wifi works ! so please mark this solved.

---

### Post by chili555 on 2012-03-27
> **nashy10 said:**
> Hey um well i rebooted because i half gave up on this whole ubuntu thing. But then i booted and it said recovery i pressed it it did something and now the wifi works ! so please mark this solved.Terrific! Glad it's working! Only you, the thread starter can use Thread Tools at the top and Mark Solved.

---

### Post by dave2001 on 2012-03-27
> **nashy10 said:**
> i half gave up on this whole ubuntu thing. 

Ubuntu (any Linux distro really) can be a bit frustrating at times when you've just switched over from Windows, but if you persevere you'll find it gets easier quickly.. especially once you get over those first system configuration hiccups. 

Glad to hear your wireless is working! It's not only working in "recovery mode" is it?

Also, don't think twice about posting more questions here.. this is not your average forum. The people here are overwhelming helpful and friendly.

---

