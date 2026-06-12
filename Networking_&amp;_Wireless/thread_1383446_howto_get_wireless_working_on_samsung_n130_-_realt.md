---
title: "howto: get wireless working on samsung n130 - realtek 8192"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by ssam on 2010-01-17
this should work on any machine with a realtek 8192 or 8192e card

karmic does not contain a driver for the realtek 8192 wireless card. there are already several posts that show how to download the driver source, compile and install it.

however the kernel in lucid (ubuntu 10.04) has the driver built in. it is possible to run the lucid kernel in karmic. this safer because it saves you from having to download packages of unknown origin, and run untrusted scripts (all the other howtos require this).

first you need to install the lucid kernel. the latest version can be found at [https://launchpad.net/ubuntu/lucid/+source/linux](https://launchpad.net/ubuntu/lucid/+source/linux) you want the linux-image-2.6.32-10-generic binary package for either i386 (32bit) or amd64

i got mine from a mirror [http://fr.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-10-generic_2.6.32-10.14_i386.deb](http://fr.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-10-generic_2.6.32-10.14_i386.deb)

2.6.32 has been out for a few months, so you should find it just as stable as the karmic kernel. if lucid switches to 2.6.33 by the time you read this, then you may want to hunt out the older 2.6.32 version.

now download that deb, double click it, and install.

now one more step,
currently the ubuntu lucid kernel does not contain the firmware for the card. this will hopefully be fixed soon, see
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/508746](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/508746)
if the bug is not marked as fixed, then you will need to grab the firmware from kernel.org

```
sudo apt-get install git-core
cd /tmp
git clone git://git.kernel.org/pub/scm/linux/kernel/git/gregkh/firmware.git
sudo cp -av firmware/RTL8192E /lib/firmware/
```

now reboot and enjoy your wireless

---

### Post by anipet on 2010-01-19
greatly thank you for the heads up on this situation :)

---

### Post by liamgh on 2010-01-31
Thanks for this! Am running Ubuntu Lucid on a Sumsung R580 which has one of these WiFi cards. Obtained and copied the firmware as described and now I can connect to WiFi networks (including WPA2 encrypted ones).

---

### Post by bit mad on 2010-01-31
Thanks, I'm almost there now!

N130 with a persistant USB (made from Windows with LiLi) of the live netbook version -
lucid-netbook-i386.iso - with MD5 correct. We did that git jiggerypokery and all went well.

Now I get a wlan0 section from *ifconfig* (didn't before) and clicking on the networks icon shows a load of Wifi networks it can see. I probably haven't got the hang of it yet - it seems to be connected, but the update manager says it hasn't got a connection and web browsing doesn't work. The connections then disconnect within a minute or two.

What do we try next?

**EDIT - UPDATE:**
Might have been just bad luck - I tried with another distro using the NDISWRAPPER method *(and Wireless_LAN_Realtek_1678.0.1019.2009.zip unzipped into a wifi folder in the home folder)* and that didn't work either - despite being near what I believed to be an open hotspot. But I did have luck later on in a different location with that method...... and didn't have the Ubuntu 10.04 USB key with me at that point.

---

### Post by knakworst on 2010-02-02
Before I try, does this also work on a RTL 8192SE?

---

### Post by northd_tech on 2010-02-06
> **knakworst said:**
> Before I try, does this also work on a RTL 8192SE?

The 8192**SE** looks to be much easier to work with than the 81**92E**- do a forum search here for "Realtek 8192SE" and you should find several threads (I have posted some info on a few of them).  Forum member "Chili555" had a method that worked pretty well for a few people.

You could also try downloading the 8192SE UNIX/LINUX driver directly from Realtek's website:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

The 3rd section is labeled "8192SE" and the filename that I saw was "rtl8192se_linux_2.6.0013.1204.2009.tar.gz"

Hope this helps.

Edit:  For the 8192E, it is worth reading this thread too:

[http://ubuntuforums.org/showthread.php?t=1239342&page=7&highlight=Realtek+8192E](http://ubuntuforums.org/showthread.php?t=1239342&page=7&highlight=Realtek+8192E)

Edit2:  Here is a link that should get you on the right path for that 8192SE, knakworst:

[http://ubuntuforums.org/showthread.php?t=1328209](http://ubuntuforums.org/showthread.php?t=1328209)

---

### Post by knakworst on 2010-02-09
Thanks for the reply. It was easy indeed, just make / make install the driver. Ik hope the card works out of the box in 10.04 LTS though.

---

### Post by pro1ove on 2010-03-03
I am so glad to hear that the 8192se realtek chipset is supported in Lucid Lynx!

---

### Post by Nuskrad on 2010-10-07
I've just installed Ubuntu 10.10 and can't get my wireless to work now. Under 10.04 all that was required was installing the firmware from git as described in the OP, however it no longer seems to exist, when I run it I get the error "fatal: The remote end hung up unexpectedly".

So, how do I get it working now? :confused:

---

### Post by pinheads.place on 2010-11-17
> **Nuskrad said:**
> I've just installed Ubuntu 10.10 and can't get my wireless to work now. Under 10.04 all that was required was installing the firmware from git as described in the OP, however it no longer seems to exist, when I run it I get the error "fatal: The remote end hung up unexpectedly".

So, how do I get it working now? :confused:

hi, i av the same error on my samsung N150 :confused:

---

### Post by Antster on 2010-11-28
I'm a newcomer to Linux & am using a Samsung N130, Realtek RTL8192e card, Ubuntu 10.10.

I have been having a nightmare with this, but after a week of digging around I have finally found a solution that works for me - it's on this thread: [http://ubuntuforums.org/showthread.php?p=10014569](http://ubuntuforums.org/showthread.php?p=10014569)

I managed to get online using my USB mobile broadband, then:
1) Downloaded the file included in commandergc's post of 18 October.
2) Unpacked it into my Home/Downloads folder
3) followed the scripts in commandergc's post.

Hope this helps, it's completely fixed the problem for me.

---

### Post by cjbrooker on 2011-01-03
This post worked for me on my Samsung N130:

[http://ubuntuforums.org/showpost.php?p=10104853&postcount=20](http://ubuntuforums.org/showpost.php?p=10104853&postcount=20)

---

