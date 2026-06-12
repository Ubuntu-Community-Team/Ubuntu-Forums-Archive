---
title: "How do I install network manager after removing it?"
date: 2010-04-08
forum: Networking &amp; Wireless
---

### Post by Kygoski on 2010-04-08
I made the mistake of downloading "kwlan", and now I want my original Network Manager back. Uninstalling kwlan left me with no Internet connection of any sort, but I downloaded networkmanager 0.8.tar.bz2 using the NetworkManager from the disk. How do I get my network manager back? Also, please be as detailed as possible? I'm a newbie at ubuntu. My ubuntu version is 9.10 if if helps, (that koala version).Help please? :(


You cAn personally email mr if needed at [email]Kygoskiskyblue@hotmail.com[/email]

---

### Post by garvinrick4 on 2010-04-08
> **Kygoski said:**
> I made the mistake of downloading "kwlan", and now I want my original Network Manager back. Uninstalling kwlan left me with no Internet connection of any sort, but I downloaded networkmanager 0.8.tar.bz2 using the NetworkManager from the disk. How do I get my network manager back? Also, please be as detailed as possible? I'm a newbie at ubuntu. My ubuntu version is 9.10 if if helps, (that koala version).Help please? :(


You cAn personally email mr if needed at [email]Kygoskiskyblue@hotmail.com[/email]
sudo apt-get install network-manager-gnome

---

### Post by Kygoski on 2010-04-09
Thanks for your timely reply :) it almost worked, except for it says that it was unable to fetch some archives, maybe run apt-get update or try with. Is this because my laptop is not connected to the Internet?

---

### Post by _BugsBunny_ on 2010-04-09
Yes, it's because you're not connected to the Internet. You can try to get an internet connection going manually. Easiest would be to setup (temporarily) a wired connection, but you can get a wireless connection going as well by using iwconfig. You'll probably need to edit /etc/network/interfaces and temporarily add interfaces that are normally configured by network manager.

You'll also need wpa-supplicant installed. You may already have this since it's used by other network managers. If not then then you'll need to sneakernet files in any case.

Sneakernet may be the easiest solution of all though. Try this first:
Download the deb for network manager. Scroll to the bottom of this page and choose your architecture: 
[http://packages.ubuntu.com/karmic/network-manager](http://packages.ubuntu.com/karmic/network-manager)

Download it then try to install it:
```
sudo dpkg -i <name of downloaded deb file>
```
It will install, if you already have all the needed dependencies still installed.

If that doesn't work check if you have wpasupplicant installed. If so see this page: [WiFi/HowToUse - Debian Wiki](http://wiki.debian.org/WiFi/HowToUse#wpasupplicant) Run iwconfig first to get the name of the interface (see *man iwconfig* for details)

---

### Post by Kygoski on 2010-04-09
Before I try this, will it give me any possible boot error of any kind?

---

### Post by _BugsBunny_ on 2010-04-09
Booting shouldn't be effected in any way. You may get network related errors, depending on some settings, but it shouldn't prevent a successful boot (unless something else is wrong).

---

### Post by Kygoski on 2010-04-09
Disregard this last post, I found out I have i386.

I have an AMD Athlon 64 X2 processor. There's two options available, (AMD and i386) I think I have the i386 Ubuntu Koala, but I have an AMD processor. When I go down to click on the "i386" architechture, it says "For Intel x64" or something like that. The AMD one says AMD64, (I think it's the one I should download.), but I don't want to download the wrong one :c Which one is it?

---

### Post by garvinrick4 on 2010-04-09
> **Kygoski said:**
> Disregard this last post, I found out I have i386.

I have an AMD Athlon 64 X2 processor. There's two options available, (AMD and i386) I think I have the i386 Ubuntu Koala, but I have an AMD processor. When I go down to click on the "i386" architechture, it says "For Intel x64" or something like that. The AMD one says AMD64, (I think it's the one I should download.), but I don't want to download the wrong one :c Which one is it?
Code: uname -a

---

### Post by Kygoski on 2010-04-09
> **garvinrick4 said:**
> Code: uname -a

 [SOLVED] I finally got this thing up and running. What I did was:  Downloaded &quot;Network-Manager-Gnome&quot; (i386 architecture) [http://ns2.canonical.com/karmic/i386/network-manager/download](http://ns2.canonical.com/karmic/i386/network-manager/download) . After downloading that from my LiveCD's connection, (You can also use another computer and save it to a flash drive or something.), I then booted into my normal Ubuntu 9.10 OS, and started the &quot;.deb&quot; file. (The Applet icon wasn't in the top Panel/Notification Area.) After a successful install, I plugged into an Ethernet connection (Wired). I started Ubuntu Software Center and searched &quot;Network Manager.&quot; Since I was connected to the Internet at this point, I downloaded it again (From Software Center) and waited for it to be done. Afterwards, it prompted me to restart. After rebooting, I saw the icon for Network Manager in the Notification Area/Panel. Simply connected to my router to type this report :3  Hope I helped someone!!~   [P.S.] How do I set this Thread as &quot;[Solved]&quot; as I've seen others?

---

### Post by mark bower on 2010-04-09
see my link, same question as yours.

[http://ubuntuforums.org/showthread.php?t=1450683](http://ubuntuforums.org/showthread.php?t=1450683)

---

