---
title: "Another wireless card not working thread"
date: 2011-12-15
forum: Networking &amp; Wireless
---

### Post by etphoto on 2011-12-15
I'm pretty new to ubuntu (using 10.04) and did a clean install on my Dell Inspiron 14.20. Everything works (hard wire Internet) except the wireless card.  I've read these forum extensively and tried numerous instructions to no avail.  I'm pretty sure I have the correct drivers install but for some reason the wireless card just does not work (it works when I change hard drives that has windows 7 installed).  The little pie shaped wireless icon has a read exclamation point over it and just won't search for available wireless connections.

When I do a Hardware Drivers search it revels the installed driver but has the message 
"This driver is activated but not currently in use."  When I remove and re activate the driver the messages reads "This driver is activated and in use".  Yet, the wireless card still does not work and after a reboot the message returns to the not currently in use.Pl

Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)  is the card i have installed and according to post in the threads i've read is very common card and should work.

Please, someone point me in the right direction.

ET

---

### Post by bluexrider on 2011-12-15
here is the Ubuntu WIFI docs 


[LIST]
[*][WifiDocs]("https://help.ubuntu.com/community/WifiDocs")
[*][Driver]("https://help.ubuntu.com/community/WifiDocs/Driver")
[*][bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx?action=fullsearch&context=180&value=linkto%3A%22WifiDocs%2FDriver%2Fbcm43xx%22")
[/LIST]

---

### Post by pastalavista on 2011-12-15
Have you tried installing the 'b43-fwcutter' package? It works for several Broadcom cards when the recommended one won't.

---

### Post by irv on 2011-12-15
Go to this thread: [http://ubuntuforums.org/showthread.php?t=1742147&page=3]("http://ubuntuforums.org/showthread.php?t=1742147&page=3")

and follow the instructions I have in post #25. I have a broadcom card too and this is what worked for me. By the way if you go to 12.04 when it is released in April 2012, you will need to do the same again to get it to work. I am testing 12.04 now and the new kernel is still not working with broadcom cards.

---

### Post by etphoto on 2011-12-15
b43-fwcutter' package is installed.

iry

using the command  
sudo apt-get install firmware-b43-installerI get the following response. 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package firmware-b43-installer

I went to Synaptic Package Manager and couldn't find firmware-b43-installer.  What do I do now?

ET

btw; thanks for the quick response. I'm getting pumped I might be wireless by tonight.

---

### Post by irv on 2011-12-15
> **etphoto said:**
> b43-fwcutter' package is installed.

iry

using the command  
sudo apt-get install firmware-b43-installerI get the following response. 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package firmware-b43-installer

I went to Synaptic Package Manager and couldn't find firmware-b43-installer.  What do I do now?

ET

btw; thanks for the quick response. I'm getting pumped I might be wireless by tonight.

Do the following commands one at a time and in the order you see them.
Make sure you are plugged in on the wire and on the Internet.
After you do the following you must reboot and then unplug the wire and you should have wireless working.
```
sudo apt-get remove bcmwl-kernel-source
```
```
sudo apt-get install firmware-b43-installer
```
```
sudo apt-get install b43-fwcutter
```
```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl| lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3 |rt6|rt7|witch|wl'
```
This is the output from the last command:
> # which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt 

---

### Post by etphoto on 2011-12-15
Thanks Irv,

Feeling like files and packages were missing from my computer, I decided to reformat my drive and do another install but with ubuntu 11.10.  I then followed your instructions but my card still isn't working. This is really frustrating.  From searches on this forum and google it would seems wireless cards with ubuntu not working to be common.   

I've recently retired and have the time to play with and learn ubuntu but its hard when you can't even get passed connecting to the internet. lol

et

---

### Post by gordintoronto on 2011-12-15
Do you know how to connect if the card were working?

---

### Post by irv on 2011-12-15
> **etphoto said:**
> Thanks Irv,

Feeling like files and packages were missing from my computer, I decided to reformat my drive and do another install but with ubuntu 11.10.  I then followed your instructions but my card still isn't working. This is really frustrating.  From searches on this forum and google it would seems wireless cards with ubuntu not working to be common.   

I've recently retired and have the time to play with and learn ubuntu but its hard when you can't even get passed connecting to the internet. lol

et

My card is a Broadcom 4311 and it is in a Dell Inspiron 1521 laptop. I can say that this procedure worked with my card.

---

### Post by etphoto on 2011-12-16
> **gordintoronto said:**
> Do you know how to connect if the card were working?

hmmm, I assume so. No different than Windows I'd assume. click on the wireless icon and choose a wireless network.

After right clicking on the icon the "enable wireless" is grayed out and I'm unable to click it.

ET

---

### Post by pastalavista on 2011-12-16
> **etphoto said:**
> b43-fwcutter' package is installed.

iry

using the command  
sudo apt-get install firmware-b43-installerI get the following response. 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package firmware-b43-installer

I went to Synaptic Package Manager and couldn't find firmware-b43-installer.  What do I do now?

ET

btw; thanks for the quick response. I'm getting pumped I might be wireless by tonight.

I just had a thought...

Check your software sources (Settings>>Repositories in Synaptic Package Manager)and be sure you have restricted and third party repositories checked. If you don't have 'firmware-b43-installer' showing, that may be why. There is also a 'firmware-b43legacy-installer' to be had but you need the restricted (proprietary) sources enabled to use them.

---

### Post by etphoto on 2011-12-16
> **pastalavista said:**
> I just had a thought...

Check your software sources (Settings>>Repositories in Synaptic Package Manager)and be sure you have restricted and third party repositories checked. If you don't have 'firmware-b43-installer' showing, that may be why. There is also a 'firmware-b43legacy-installer' to be had but you need the restricted (proprietary) sources enabled to use them.

Thanks. I did check that. But, I went ahead and did another install and upgraded to 11.10 and followed iry's instructions. still didn't work. Since i've upgraded the enable wireless is grayed out and I'm trying to figure out why, maybe that is the issue.

---

### Post by etphoto on 2011-12-16
Solved. I don't know what I did but got everything working. I rebooted 3 times and for some reason the wireless kicked on. Thanks SO MUCH to the people who tried helping me. These forums are great.

ET

---

