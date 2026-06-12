---
title: "Problems installing TEW-424UB in Jaunty."
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by NinjaNumberNine on 2009-09-08
Hi, could someone explain how to set up the TEW-424UB in Ubuntu 9.04 Jaunty Jackalope?
I heard it was built-in, but I don't know where to start. All the ndiswrapper stuff seems to be for Edgy Eft.
Thanks!

---

### Post by VastOne on 2009-09-08
It appears (from the google's I did) that the ndiswrapper solution is still relevant no matter what version of Ubuntu you are using.

this thread 

[http://ubuntuforums.org/showthread.php?t=1187250&highlight=tew-424ub](http://ubuntuforums.org/showthread.php?t=1187250&highlight=tew-424ub)

seems to have the most information.

---

### Post by t0mppa on 2009-09-08
Ah well, VastOne beat me to it.

---

### Post by NinjaNumberNine on 2009-09-08
All that is kind of confusing but thanks for the reply. My problem seems to be installing the drivers through ndiswrapper. After installing it I just get a message, doesn't even seem to be an error just a question. (I'll post that here in a minute, typing this from another computer right now) Also, I used[ these instructions]("https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-424UB_%28ndiswrapper%29?highlight=%28%5CbCategoryWireless%5Cb%29"). On the first step, installing ndiswrapper, there is a complication. I will post full terminal in next post.
Thanks again, everyone!

---

### Post by NinjaNumberNine on 2009-09-08
Step One: I installed ndiswrapper and a utility I noticed (see the "Synaptic" screenshot) 
Step 2: I loaded the utility, selected "New Driver" and when it asked for the .INF file I found it on the CD, then pressed enter but it gave me a "Cannot tell if hardware is present" notification. See the "Windows Wireless Drivers" screenshot.
That is the way I did it just now; the terminal way is as follows, (I did this originally)
```
halstan33@ubuntu:~$ sudo apt-get install ndiswrapper-common
[sudo] password for halstan33: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11-generic linux-headers-2.6.28-11
Use 'apt-get autoremove' to remove them.
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/21.4kB of archives.
After this operation, 98.3kB of additional disk space will be used.
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 136529 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.53-2ubuntu1_all.deb) ...
Processing triggers for man-db ...
Setting up ndiswrapper-common (1.53-2ubuntu1) ...
halstan33@ubuntu:~$ sudo apt-get install ndiswrapper-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndiswrapper-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ndiswrapper-common
E: Package ndiswrapper-utils has no installation candidate
halstan33@ubuntu:~$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11-generic linux-headers-2.6.28-11
Use 'apt-get autoremove' to remove them.
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-utils-1.9
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/36.6kB of archives.
After this operation, 127kB of additional disk space will be used.
Selecting previously deselected package ndiswrapper-utils-1.9.
(Reading database ... 136540 files and directories currently installed.)
Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.53-2ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up ndiswrapper-utils-1.9 (1.53-2ubuntu1) ...
halstan33@ubuntu:~$ sudo ndiswrapper -l /media/TEW-424UB/Drivers/Windows XP/Sis163u.INF
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
halstan33@ubuntu:~$ 
``` This is where I stop. I can't mount the directory /media/TEW-424UB/Drivers/Windows XP/ because of the space in between Windows and XP (I always knew they had a reason for the weird name) because this happens:
```
halstan33@ubuntu:~$ cd /media/cdrom/Drivers/Windows XP/
bash: cd: /media/cdrom/Drivers/Windows: No such file or directory
halstan33@ubuntu:~$ 

``` How can I get past this? also when I type the long ndiswrapper command why does it just show me a list of options instead of just "doing it?"
anyway that's where I am now...

---

### Post by NinjaNumberNine on 2009-09-08
Sorry, posted last message twice.

---

### Post by NinjaNumberNine on 2009-09-09
bump

---

### Post by NinjaNumberNine on 2009-09-09
I just have until tonight to get it working and that's just 4 hours. Somebody please?  :sad:

---

### Post by NinjaNumberNine on 2009-09-09
Sighs in desperation.... **(NO)**thanks for all the help... :roll:
It's all over...
The doom is sealed...
Dad goes back entirely to microsoft...

---

### Post by NinjaNumberNine on 2009-09-09
He gave me ten more minutes, but I doubt that I will get another reply by then.. Why do the manuals NEVER work for me? :cry:

---

### Post by uylug on 2009-09-09
Seems like you're attempting to install the drivers using the -l option? you should use the i option instead.
 
Also, I've got the same network adapter so if you run into problems, contact me via PM or email.

---

### Post by sorak on 2009-09-10
to get past the "space" issue, use a backslash... like this... /mnt/drive/Windows\ XP/fileyouneed.ext ... this is called "escaping" the character, if you just type part of it and hit Tab to autocomplete it, then it should mark up the name properly for you. if there is more than one match then tab will not autocomplete. hit tab twice to get a list of matches and add characters to narrow down what youre referring to.

---

### Post by NinjaNumberNine on 2009-09-10
Thanks for the help, that was encouraging. Last night, I tried reinstalling ubuntu, (pretty easy with wubi) and when I loaded the drivers it accepted them and said Hardware Present. I was excited, and Dad said I could work on it some more. Thing is, how do I get it to use this connection? I will post any outputs you want.

---

### Post by NinjaNumberNine on 2009-09-10
Right now I'm recompiling the linux kernel with "linux-2-6-28-10" and it is going fine. Someone said that was the problem. BTW, Uylug, do you mean you run this and it works? Also we are talking about the usb device, right? I heard later that there is a TEW-424UB card and TEW-424UB USB Wireless Adapter. I have the second one. See this link: [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Trendnet_TEW-424UB]("http://http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Trendnet_TEW-424UB")

Again, Thanks to both for the answers (finally :) ) and please post again!

---

### Post by NinjaNumberNine on 2009-09-10
That did not work, ran out of hard disk space. HOWEVER i install Kubuntu 9.04 and the device is recognized as soon as i install the windows wireless drivers. Only one problem; I have to retype the 48 letters/numbers WEP/WPA code every time I log on...  That kind of lowers the user satisfaction. Anyway I am glad I got this working, thanks for the replies and ALSO I HAVE NO SOUND IN KUBUNTU 9.04!! _:)__:)_  
-So if you have any ideas on how to get the _***autotypecodeinatloginandconnecttonetwork***_ working or ideas for the sound problem, send 'em over. :lolflag:
Thanks!

---

### Post by NinjaNumberNine on 2009-09-10
Bingo, I fixed both problems by installing updates! :)

---

