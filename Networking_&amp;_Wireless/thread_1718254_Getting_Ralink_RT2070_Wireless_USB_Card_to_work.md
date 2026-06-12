---
title: "Getting Ralink RT2070 Wireless USB Card to work"
date: 2011-03-31
forum: Networking &amp; Wireless
---

### Post by kawohi on 2011-03-31
I am very new to Ubuntu & I been having trouble getting my rt2070 wireless usb card to work on my desktop.  I am using Ubuntu 10.10.


I made a thread at AskUbuntu, with some help but it didn't get me far.

[http://askubuntu.com/questions/31029/how-do-i-get-a-ralink-rt2070-wireless-usb-stick-to-work/32702#32702](http://askubuntu.com/questions/31029/how-do-i-get-a-ralink-rt2070-wireless-usb-stick-to-work/32702#32702)

Pastebin of dmesg: [http://pastebin.com/UrFY3NSR](http://pastebin.com/UrFY3NSR)

```
Representative portion in case pastebin wipes this entry:

    [  234.984025] hub 1-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
    [  234.984041] hub 1-0:1.0: unable to enumerate USB device on port 8
    [  235.184037] hub 5-0:1.0: unable to enumerate USB device on port 2
    [  235.744031] usb 5-2: new full speed USB device using uhci_hcd and address 8
    [  235.864020] usb 5-2: device descriptor read/64, error -71
```

Ralink also has a page for support...
[http://eng.ralinktech.com.tw/support.php?s=2](http://eng.ralinktech.com.tw/support.php?s=2)

This is what the readme file

[http://pastebin.com/hTFrhY2w](http://pastebin.com/hTFrhY2w)

Here are all folders/file names that is in the folder for the wireless USB driver

[http://pastebin.com/1y8uvyqY](http://pastebin.com/1y8uvyqY)

I also tried 

```
cd RT3070_LinuxSTA_V2.3.0.1_20100208
sudo make
sudo make install
sudo mkdir /etc/Wireless/RT2870STA
sudo cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
cd os/linux
sudo /sbin/ifconfig ra0 down
sudo /sbin/rmmod rt2870sta
sudo /sbin/insmod rt2870sta.ko
sudo modprobe rt2870sta
```

It worked up too [HTML]sudo /sbin/ifconfig ra0 down[/HTML] with a message of no device detected.

I also read this thread

[http://ubuntuforums.org/showthread.php?t=1670201&](http://ubuntuforums.org/showthread.php?t=1670201&)

& followed the steps & it didn't work for me. I hope someone can help!

---

### Post by MooPi on 2011-03-31
Sorry to see your having trouble. Can you give us some info ?
In terminal ```
lsusb
``````
lsmod
``` Post back the results so we can view

---

### Post by chili555 on 2011-03-31
I don't want to step on the toes of the very capable MooPi, but if you have tried several USB slots and get the same error, It seems likely to me that the device is electrically defective.

Does it work without complaint on other computers? Do other USB devices work well on this computer, USB drives, cameras, etc.?

rt2870sta is built in to the kernel in 10.10; a different driver compiled from a tarball is not going to fix an electrical defect, in my humble opinion.

I have subscribed to the thread and let's see what happens.

---

### Post by MooPi on 2011-03-31
My thoughts as well but don't know what happened so far per thread description, so just poking around to see if there is an obvious or glaring problem. Thanks but I don't see how you could step on my toes as I truly respect your opinion and skill set with regard to wireless devices.

---

### Post by TBABill on 2011-03-31
To the OP, the key to your problem lies not in downloading, compiling, etc. The problem most likely exists in /etc/modules for that device. I'm just guessing, but probably more than one driver trying to claim the device. Very common for the 2860/2870/3090 and others.

---

### Post by chili555 on 2011-03-31
I don't think this is a driver conflict, although we may find a driver conflict is a secondary issue.> #
[  186.184048] hub 1-0:1.0: unable to enumerate USB device on port 8
#
[  186.384039] hub 5-0:1.0: unable to enumerate USB device on port 2
#
[  189.480034] hub 1-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
#
[  192.448025] hub 1-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
#
[  195.416030] hub 1-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
#
[  198.384033] hub 1-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
#
[  198.384050] hub 1-0:1.0: unable to enumerate USB device on port 8
#
[  198.584094] hub 5-0:1.0: unable to enumerate USB device on port 2
#
[  201.680055] hub 1-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
#
[  204.648036] hub 1-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
#
[  207.616031] hub 1-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
#
[  210.584034] hub 1-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?

---

### Post by kawohi on 2011-03-31
Hey guys! Thanks for replying!

> **chili555 said:**
> I don't want to step on the toes of the very capable MooPi, but if you have tried several USB slots and get the same error, It seems likely to me that the device is electrically defective.

Does it work without complaint on other computers? Do other USB devices work well on this computer, USB drives, cameras, etc.?

rt2870sta is built in to the kernel in 10.10; a different driver compiled from a tarball is not going to fix an electrical defect, in my humble opinion.

I have subscribed to the thread and let's see what happens.

Yes, it worked on my Windows 7 64-bit laptop. The card is brand new, bought from Amazon too so I don't think its broken.
I have a USB 2GB flash drive and it worked on Ubuntu

---

### Post by chili555 on 2011-03-31
I suspect MooPi will want you to reboot with the device unplugged, open a terminal and do:```
sudo tail -f /var/log/messages
```Leave the terminal open and plug in the device. Are there any interesting messages thrown up?

---

### Post by kawohi on 2011-03-31
lsusb & lsmod

[http://pastebin.com/TDaYK2DY](http://pastebin.com/TDaYK2DY)

when I enter ```
sudo tail -f /var/log/messages
```

Then put in the card [thats what you wanted right?] I get this -

```
Mar 31 13:03:13 lj-Ubuntu kernel: [  221.580015] usb 1-7: new high speed USB device using ehci_hcd and address 5
```

[http://pastebin.com/X9LVSpHt](http://pastebin.com/X9LVSpHt)

---

### Post by MooPi on 2011-04-01
That was close to what I would have suggested but instead I would have suggested a reboot without the device. Open a terminal and type ```
dmesg>01RTtest.txt
``` 
Then plug the device in and type in terminal ```
dmesg>02RTtest.txt
``` Post back here the text files.
But I don't know if that would give anymore useful info to this mystery.
The command lsmod shows no module being loaded for the device listed in lsusb. This device should have a module in the kernel and doesn't need an external module loaded to work.
Here is my suggestion. 
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Hopefully your in need of a kernel upgrade . Reboot and see if your device works. If this doesn't work or your not in need of a kernel upgrade try to reboot and enter the grub menu by hitting the shift key just after the bois splash disappears. Scroll down to a previous kernel and boot to that. With any luck your device will work.

---

### Post by kawohi on 2011-04-01
> **MooPi said:**
> That was close to what I would have suggested but instead I would have suggested a reboot without the device. Open a terminal and type ```
dmesg>01RTtest.txt
``` 
Then plug the device in and type in terminal ```
dmesg>02RTtest.txt
``` Post back here the text files.
But I don't know if that would give anymore useful info to this mystery.
The command lsmod shows no module being loaded for the device listed in lsusb. This device should have a module in the kernel and doesn't need an external module loaded to work.
Here is my suggestion. 
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Hopefully your in need of a kernel upgrade . Reboot and see if your device works. If this doesn't work or your not in need of a kernel upgrade try to reboot and enter the grub menu by hitting the shift key just after the bois splash disappears. Scroll down to a previous kernel and boot to that. With any luck your device will work.

But it does detect it when I enter lsusb?

```
Bus 001 Device 003: ID 148f:2070 Ralink Technology, Corp. RT2070 Wireless Adapter
```

Also I do not have internet access with that desktop, how can I upgrade it from my windows desktop?

---

### Post by MooPi on 2011-04-01
> **kawohi said:**
> But it does detect it when I enter lsusb?

```
Bus 001 Device 003: ID 148f:2070 Ralink Technology, Corp. RT2070 Wireless Adapter
```

Also I do not have internet access with that desktop, how can I upgrade it from my windows desktop?
Yes but the command "lsmod" does not show a module loading to enable the device. So you have a connected device that works with Windows as confirmation that it works and confirmation that it is connected to your Ubuntu install but no driver is loading. The kernel in 10.10 has a module for your chip but it isn't showing in lsmod. I can only guess that you disabled it with a prior step or action. My solution is to upgrade to the newest kernel to get that standard module back. I don't know how you'll get  an internet connection for this computer other than lan cable I guess. 
Have you ever blacklisted for this module. Can you show us the /ect/modprobe.d/blacklist.conf file contents ?

---

### Post by kawohi on 2011-04-02
> **MooPi said:**
> Yes but the command "lsmod" does not show a module loading to enable the device. So you have a connected device that works with Windows as confirmation that it works and confirmation that it is connected to your Ubuntu install but no driver is loading. The kernel in 10.10 has a module for your chip but it isn't showing in lsmod. I can only guess that you disabled it with a prior step or action. My solution is to upgrade to the newest kernel to get that standard module back. I don't know how you'll get  an internet connection for this computer other than lan cable I guess. 
Have you ever blacklisted for this module. Can you show us the /ect/modprobe.d/blacklist.conf file contents ?

Alright, heres everything.

dmesg, before & after.
[http://pastebin.com/e9QvDWpc](http://pastebin.com/e9QvDWpc)

blacklist
[http://pastebin.com/HRG84jXp](http://pastebin.com/HRG84jXp)

I haven't had Ubuntu installed on my desktop for very long, I changed some files, moved stuff around but thats it. Ialso [today] reformatted Ubuntu and used the 10.10 edition CD I got from the mail from Ubuntu. 

I have no way to get internet on the desktop. There is no possible way to upgrade the kernel from another desktop??

---

### Post by MooPi on 2011-04-02
Okay I see something to edit. Open terminal
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
At the very end of that file add this text
```
#Ralink 2870
blacklist_rt2800pci
blacklist_rt2800lib
blacklist_rt2800usb
blacklist_rt2x00pci
blacklist_rt2x00lib
blacklist_rt2x00usb
```
Save and reboot. Hopefully your wireless will be seen and work with your network encryption.

---

### Post by flash63 on 2011-04-02
Hello,
try this > [http://ubuntuforums.org/showthread.php?p=10610378&posted=1#post10610378](http://ubuntuforums.org/showthread.php?p=10610378&posted=1#post10610378)

Identical to TP-Link TL-WN321Gv3  > [http://forum.ubuntuusers.de/topic/inbetriebnahme-tp-link-tl-wn321g-wlan-stick/#post-2804142](http://forum.ubuntuusers.de/topic/inbetriebnahme-tp-link-tl-wn321g-wlan-stick/#post-2804142)

---

### Post by kawohi on 2011-04-02
> **MooPi said:**
> Okay I see something to edit. Open terminal
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
At the very end of that file add this text
```
#Ralink 2870
blacklist_rt2800pci
blacklist_rt2800lib
blacklist_rt2800usb
blacklist_rt2x00pci
blacklist_rt2x00lib
blacklist_rt2x00usb
```
Save and reboot. Hopefully your wireless will be seen and work with your network encryption.

Sorry it didn't work.

> **flash63 said:**
> Hello,
try this > [http://ubuntuforums.org/showthread.php?p=10610378&posted=1#post10610378](http://ubuntuforums.org/showthread.php?p=10610378&posted=1#post10610378)

Identical to TP-Link TL-WN321Gv3  > [http://forum.ubuntuusers.de/topic/inbetriebnahme-tp-link-tl-wn321g-wlan-stick/#post-2804142](http://forum.ubuntuusers.de/topic/inbetriebnahme-tp-link-tl-wn321g-wlan-stick/#post-2804142)

I followed, and nothing happen.

---

### Post by MooPi on 2011-04-02
I'm going to have to side with chill555 on this instance. The device is either defective or totally incompatible with Linux. I got no more wrenches to throw at this problem.

---

### Post by flash63 on 2011-04-03
> **kawohi said:**
> Sorry it didn't work.
I followed, and nothing happen.

Block rt3070sta
```
echo 'blacklist rt3070sta' | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Check the configuration file:
```
cat /etc/modprobe.d/rt2870sta.conf
```
Content must be
```
install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "148f 2070" > /sys/bus/usb/drivers/rt2870/new_id
```
Remove rt3070sta and load rt2870sta
```
sudo modprobe -rf rt3070sta
sudo modprobe rt2870sta
iwconfig
```

---

### Post by kawohi on 2011-04-03
> **flash63 said:**
> Block rt3070sta
```
echo 'blacklist rt3070sta' | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Check the configuration file:
```
cat /etc/modprobe.d/rt2870sta.conf
```
Content must be
```
install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "148f 2070" > /sys/bus/usb/drivers/rt2870/new_id
```
Remove rt3070sta and load rt2870sta
```
sudo modprobe -rf rt3070sta
sudo modprobe rt2870sta
iwconfig
```

Where does the tar file have to be???

---

### Post by flash63 on 2011-04-03
> **kawohi said:**
> Where does the tar file have to be???
There is no tar file.

---

### Post by kawohi on 2011-04-03
> **flash63 said:**
> There is no tar file.

No such file or directory when checking config.

So the files that is on the disc doesnt need to be used? So far nothing has worked :(

---

### Post by flash63 on 2011-04-04
No useful response so far to this post [http://ubuntuforums.org/showpost.php?p=10631659&postcount=18](http://ubuntuforums.org/showpost.php?p=10631659&postcount=18)

Create the configuration as already linked
[http://ubuntuforums.org/showthread.php?p=10610378&posted=1#post10610378](http://ubuntuforums.org/showthread.php?p=10610378&posted=1#post10610378)

Blacklist rt3070sta:
```
echo 'blacklist rt3070sta' | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Restart. The Stick schould now work.

---

### Post by matt-fender on 2011-04-04
> **flash63 said:**
> No useful response so far to this post [http://ubuntuforums.org/showpost.php?p=10631659&postcount=18](http://ubuntuforums.org/showpost.php?p=10631659&postcount=18)

Create the configuration as already linked
[http://ubuntuforums.org/showthread.php?p=10610378&posted=1#post10610378](http://ubuntuforums.org/showthread.php?p=10610378&posted=1#post10610378)

Blacklist rt3070sta:
```
echo 'blacklist rt3070sta' | sudo tee -a /etc/modprobe.d/blacklist.conf
```Restart. The Stick schould now work.


You sir are a winner!, I purchased like 10 of these little blighters on eBay purely because they are meant to work OOTB on Ubuntu 10.04. Finally I have them working! Thankyou! :)

---

### Post by kawohi on 2011-04-05
[http://ubuntuforums.org/showpost.php?p=10610378&postcount=5](http://ubuntuforums.org/showpost.php?p=10610378&postcount=5) 
OMG.
OMG.
OMG

this worked~

[http://ubuntuforums.org/showpost.php?p=10610378&postcount=5](http://ubuntuforums.org/showpost.php?p=10610378&postcount=5)

Before I was on my iPhone and I looked at the answer here. I went on my laptop and saw that there was only half of the line that was showing on the iPhone. So I entered it again and IT WORKED!

Thank you everyBODY.

---

