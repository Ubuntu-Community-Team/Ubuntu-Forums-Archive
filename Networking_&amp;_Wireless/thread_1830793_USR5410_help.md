---
title: "USR5410 help"
date: 2011-08-22
forum: Networking &amp; Wireless
---

### Post by shethc on 2011-08-22
Hello!
I am newbee to the world of ubuntu and linux and have just installed ubuntu 11.04 on an old laptop. I have US robotics 5410 card for wirelss however I am unable to get my wireless to work.
I searched the forum and found this thread - [http://ubuntuforums.org/showthread.php?t=75448&highlight=5410&page=4](http://ubuntuforums.org/showthread.php?t=75448&highlight=5410&page=4)
Unfortunately I cannot find '/acx' directory and I am unable to create it. Can anyone please help?
Thank you.

---

### Post by praseodym on 2011-08-22
Hello,

can you post the following outputs:

```
lspci -nnk
lsusb
pccardctl info
lsmod
iwconfig
rfkill list
```

---

### Post by shethc on 2011-08-22
Thanks for the reply. I am attaching a .txt file as the output was too large.

---

### Post by praseodym on 2011-08-22
The driver is no longer part of the linux-kernel, so forget about that "firmware" thing. The old module acx only supports WEP encryption. You should use ndiswrapper with the attached Windows-XP-driver instead.

```
sudo apt-get install ndisgtk ndiswrapper-common ndiswrapper-utils-1.9
```
Unpack the driver folder into your /home-directory and install:

```
sudo ndiswrapper -i ~/ti1130pci_xp/TNET1130.INF
sudo modprobe -v ndiswrapper
sudo ndiswrapper -ma
sudo depmod -a
```

Control:
```
ndiswrapper -l #a small L
dmesg | grep ndis
iwconfig
sudo iwlist scan
rfkill list
```

---

### Post by shethc on 2011-08-22
I get the following message when I run the first command. I was concerned because it says its not able to locate the package. Is this ok?

Thanks!

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.


chsheth@PCG-FRV34-UC:~$ sudo apt-get install ndisgtk ndiswrapper-common ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ndisgtk
E: Unable to locate package ndiswrapper-common
E: Unable to locate package ndiswrapper-utils-1.9
E: Couldn't find any package by regex 'ndiswrapper-utils-1.9'
chsheth@PCG-FRV34-UC:~$

---

### Post by praseodym on 2011-08-22
Do you have any internet connection? These packages are also located on the CD/DVD in **~/pool/main/n**. Just double click them

---

### Post by shethc on 2011-08-22
ok, i was able to get the drivers and followed your code and instructions. now i see a red light blinking on the card :)
 
however i dont see available wireless networks when i go to Preferences > Network Connections.
did i mess up somewhere?
 
thanks again for helping out. i greatly appreciate.

---

### Post by praseodym on 2011-08-22
Can you show the outputs of:

```
lsmod
ndiswrapper -l
cat /etc/modprobe.d/ndiswrapper.conf
iwconfig
cat /var/lib/NetworkManager/NetworkManager.state
rfkill list
dmesg | grep ndis
uname -a
sudo iwlist scan
```
The driver only supports WPA encryption imho, so you may modify the settings in your router interface.

---

### Post by shethc on 2011-08-22
actually i rebooted the machine and it's seeing the wireless now. thanks again for all the help. i am really, really grateful :)

---

### Post by praseodym on 2011-08-22
Great. You can set the "Solved"-Flag by editing the first post.

---

### Post by NotesGuy on 2011-12-11
a quick THANK YOU.  found this thread and I have same USR PCMCIA card on an old Dell laptop ... following your instructions got me going wireless.  
Only thing was it took me a minute to figure out I unpacked to wrong place so this line kept giving errors:  
sudo ndiswrapper -i ~/ti1130pci_xp/TNET1130.INF

---

### Post by samehmeh on 2012-06-30
Hi praseodym,

I followed all the instructions but wasn't able to get it working. I noticed this message when I ran this command: 
family@family-PCG-FRV25-UC:/$ sudo ndiswrapper -ma
module configuration information is stored in /etc/modules.conf
family@family-PCG-FRV25-UC:/$ 

Could you please help?

Thanks!


----

never mind it works now. Although rebooting didn't work, I just took the card out and reinserted it, and now it works....Thanks a lot for your help!

---

### Post by praseodym on 2012-07-01
You need to run this command:

```
sudo cp /etc/modules.conf /etc/modprobe.d/ndiswrapper.conf
```

---

