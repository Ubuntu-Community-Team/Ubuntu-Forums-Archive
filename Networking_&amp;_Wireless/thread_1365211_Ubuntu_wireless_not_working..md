---
title: "Ubuntu wireless not working."
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by kkjane on 2009-12-26
So, I recently have been looking in the market for a new netbook. And the one I want says it comes with Ubuntu. So I decided to check it out. 
I downloaded it, and I am duel booting it on my Dell Ispiron E1505, with Windows Vista basic. Well, I have AT&T uverse internet at my house, and I am able to get Internet when I'm on Vista, but as soon as I boot up Ubuntu, Wireless networks enabled...Yet, it's not detecting any networks. I am just wondering if I have to manually upload the server or whatver into the Ubuntu Network connections thing. Any help would be appreciated. Thanks.

---

### Post by zey on 2009-12-26
try to use madwifi or ndiswrapper... may it can help you..
have you try it?







[http://z-computer-z.blogspot.com]("http://z-computer-z.blogspot.com/")

---

### Post by kkjane on 2009-12-28
Well, I tried like manually entering the information from my ATT Uverse. But I'm a little confused as to what I need to put in. 
What is my SSID? Is it the Name like...2Wire166 or something else?
Also, are the BSSID and Mac address the same thing? 
Because, I entered in all the information, but the Apply button does not become available, only the Cancel button is. 
I have no clue what Madwifi or Ndiswrapper is, so if you would like to elaborate on that, so I know what I'm using is before I just go into something blindly, that would be great!

---

### Post by aquarius18 on 2009-12-28
> **kkjane said:**
> Well, I tried like manually entering the information from my ATT Uverse. But I'm a little confused as to what I need to put in. 
What is my SSID? Is it the Name like...2Wire166 or something else?
Also, are the BSSID and Mac address the same thing? 
Because, I entered in all the information, but the Apply button does not become available, only the Cancel button is. 
I have no clue what Madwifi or Ndiswrapper is, so if you would like to elaborate on that, so I know what I'm using is before I just go into something blindly, that would be great!

SSID is the name of the wireless network you are connecting to. You would have given your wireless network some sort of an identifier when you first set it up. You may find the name in Vista when placing your mouse pointer over the network icon in the system tray.

Mac address stands for Media Access Control. To find your MAC address open a terminal in Ubuntu and type

> sudo ifconfig -aThe output will be something like [B]HWaddr 00:09:A7:2B:8C:03
[/B]
BTW I am having the same problem as you - pls see this thread:

[http://ubuntuforums.org/showthread.php?t=1366056](http://ubuntuforums.org/showthread.php?t=1366056)

Frank

---

### Post by kkjane on 2009-12-28
Well I am assuming that my SSID is the "2WIRE166" cause that's what it says on my icon. 
I have my Mac address...00:25:3C:84:BF:48...Is that the same thing s my BSSID? 
And why would my Apply button not be accessible even after I filled out all the information? Ugh, I'm so f-ing confused.

---

### Post by efflandt on 2009-12-28
You do not even need to be concerned about MAC address or anything.  The only 2 things you need to fill in for your wireless in Network Manager are SSID (the 2WIRE166 sounds like it), and Wireless Security (you can leave everything else blank).  If the Uverse modem is remotely similar to the 2Wire I have for DSL, the default WEP key is in square brackets [ ] on the modem label (unless you changed it).

Then it depends whether kernel modules are properly enabled for wireless on your laptop.  An older Dell laptop I have for work has BCM4311, and a new Dell 1545 that I am setting up for someone with BCM4312 both need Broadcom STA.  If you go to System > Administration > Hardware Drivers, see if it shows any drivers for your laptop and whether Broadcom STA is activated (forget about the wadcutter one).  You might need to temporarily wire your laptop to the modem to install that, unless you can figure out how to insert the Ubuntu install CD and use that as a source.

---

