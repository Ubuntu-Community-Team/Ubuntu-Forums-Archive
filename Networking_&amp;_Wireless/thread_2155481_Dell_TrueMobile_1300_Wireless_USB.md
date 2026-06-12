---
title: "Dell TrueMobile 1300 Wireless USB"
date: 2013-06-18
forum: Networking &amp; Wireless
---

### Post by undrline on 2013-06-18
Every version/flavor of ubuntu that I install, I have to figure out all over again, and for this installation, how to get this wireless adapter working again.
With Lucid, adding firmware-addons-dell and, possibly, linux-firmware-nonfree packages seemed to work.  I stuck with Lucid for years; I could only sporadically get it to work on Mavrick, Natty, and Oneric.  I just upgraded to Precise, and want to post what I did.

I found this closed thread that helped me, but it didn't have everything, because I ran into problems:
[http://ubuntuforums.org/showthread.php?t=986342&p=6729214#post6729214](http://ubuntuforums.org/showthread.php?t=986342&p=6729214#post6729214)

I installed the package ndisgtk via Synaptic
I had to download and decompress the file I've reattached here
[COLOR=#000000]I installed the driver within: [/COLOR]```
[COLOR=#000000]DellTruemobile1300WirelessUSB-Linux$[/COLOR][COLOR=#000000] sudo ndiswrapper -i oem15.inf[/COLOR]
```[COLOR=#000000]
I got "fatal" error whenever I tried to modprobe ndiswrapper or anything of the sort, but following some other instructions, [/COLOR]I ran these magic spells:

```
sudo depmod -a
sudo ndiswrapper -m
```
I should've done a man depmod to figure out what it would do before I went along with it, but I didn't.  It's possible that it's not even a necessary step.
The ndiswrapper -m, according to the documentation and the terminal response, edits a conf file that should allow it to be found again on startup.
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Troubleshooting](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Troubleshooting) said that getting that fatal error I should follow some other documentation.  But, after unplugging the card and plugging it back in, then removing the ethernet cable, the network manager recognized it.


[COLOR=#333333][FONT=Ubuntu]

[/FONT][/COLOR]

---

