---
title: "Network detected, no internet"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by GribbleMR2 on 2008-12-20
First off, I am very new to linux based systems.  I finally got sick and tired of windows and decided to try Ubuntu (8.10).  I am still figuring out how to do everything, so it would be greatly appreciated if any advice could be given in as much detail as possible.

On to the problem.

I just installed Ubuntu 8.10 yesterday w/ dual boot with my original Windows XP (which is what I am posting from).  

Ubuntu recognized my network immediately, but when I tried to hop online, I got nothing.  I am using a wired connection through a Motorola DSL modem.  I am able to ping the loopback and the modem, but am unable to get a successful ping from anywhere else.

I have a couple screenshots that may help identify my problem:
[http://www.freeimagehosting.net/image.php?14853b933b.jpg](http://www.freeimagehosting.net/image.php?14853b933b.jpg)
[http://www.freeimagehosting.net/image.php?e9ff3d263f.jpg](http://www.freeimagehosting.net/image.php?e9ff3d263f.jpg)

If more info is needed to help me, let me know and I will post it.


I read here that this has been a common problem lately, and that using wicd may help, but when I try to install wicd I get this:  [http://www.freeimagehosting.net/image.php?deb8ae896d.jpg](http://www.freeimagehosting.net/image.php?deb8ae896d.jpg)
I also downloaded Damn Small Linux and ran if off of a USB drive to see if my problem was exclusive to Ubuntu, and had the same problem.

Any and all help is greatly appreciated.  Thanks in advance for helping a noob get away from windows!

FIXED!!!!!!!!!!!!! I WAS STUPID! THANKS TO ALL WHO HELPED!

---

### Post by Jameshardy88 on 2008-12-20
just double check that you have got work offline unticked in the file menu. I had that problem yesterday with a fresh install of intrepid. I now however have exactly the same problem except it is not ticked lol. Anyway i hope this works for you

---

### Post by GribbleMR2 on 2008-12-20
Already checked that, thanks.  Let me know when you fix your problem.

---

### Post by GribbleMR2 on 2008-12-21
Bump

---

### Post by IQRules on 2008-12-21
Try this, if the router is 192.168.1.1

Run this from laptop,

$ sudo route add default gw 192.168.1.1 eth1

Eth1 is the wireless IP port, your surfing should be fine.

WICD is way to go.

---

### Post by GribbleMR2 on 2008-12-21
> **IQRules said:**
> Try this, if the router is 192.168.1.1

Run this from laptop,

$ sudo route add default gw 192.168.1.1 eth1

Eth1 is the wireless IP port, your surfing should be fine.

WICD is way to go.

Desktop, not laptop.  Also, I do not have a wireless router or wireless card.

---

### Post by antmenj on 2008-12-21
What happens if you go to [http://209.85.171.99/]("http://209.85.171.99/") (google)?

If you go to the update manager will it download package information?

---

### Post by GribbleMR2 on 2008-12-22
> **antmenj said:**
> What happens if you go to [http://209.85.171.99/]("http://209.85.171.99/") (google)?

If you go to the update manager will it download package information?
Nothing and no.  Also, I called my ISP and they refuse to offer ANY assistance to non-windows users (seriously considering switching).

Thanks for all the recommendations.  I really hope I can find a fix.

---

### Post by cabbiinc on 2008-12-22
I can't see any of the images that you've linked too so forgive me if you've already covered this.

Can you ping your modem's address? Does it return anything?

---

### Post by Windows Refugee on 2008-12-22
I'll second what CABBIIBC said.... Your screenshots are not showing at the two links you posted.

Are you using DHCP or configuring IP manually ?  If manually, did you specify gateway and DNS server addresses (I put my router's IP address into both fields when doing a manual (non-DHCP) configuration)?  Is your DSL modem possibly configured to allow only certain host IP addresses on your LAN ?  Can you get out to the Internet if you log in as the root user ? 

I just posted an issue with Wi-Fi connectivity on my new Ubuntu v8.10 install.  I can get out to the Internet when logged in as root, but not as any another user.  See [http://ubuntuforums.org/showthread.php?t=1018319](http://ubuntuforums.org/showthread.php?t=1018319)

The fact that you can successfully ping your modem tells me that if this is a configuration issue on your desktop, it is probably a DNS configuration issue... But experience has taught me that anything is possible. 

Try placing a known website's IP address into Firefox, instead of a URL. (for instance, entering 209.85.135.147 then pressing ENTER should take you to [www.google.com](www.google.com)) If you can get to a website using it's IP address, but not when entering it's URL, that's a good indication that it's a DNS issue!

---

### Post by GribbleMR2 on 2008-12-22
I cannot access the internet as the root user.  It "successfully" connects to the "network" (which only contains this computer) on startup, but will not let me past the modem.  Firefox will not connect to an IP address either.  Everything works fine when I boot the same box in windows.  Light on the modem indicating internet connection stays green while in Ubuntu.

screenshots:

[[IMG]http://img228.imageshack.us/img228/3729/ifconfigoi5.th.jpg[/IMG]](http://img228.imageshack.us/my.php?image=ifconfigoi5.jpg)

[[IMG]http://img392.imageshack.us/img392/750/ifupdr0.th.jpg[/IMG]](http://img392.imageshack.us/my.php?image=ifupdr0.jpg)

[[IMG]http://img392.imageshack.us/img392/3221/networkinterfacesyt2.th.jpg[/IMG]](http://img392.imageshack.us/my.php?image=networkinterfacesyt2.jpg)

[[IMG]http://img228.imageshack.us/img228/9061/wicdpm0.th.jpg[/IMG]](http://img228.imageshack.us/my.php?image=wicdpm0.jpg)

Edited to add:  I have tried both DHCP and manual settings (including dns server and gateway info) with no success.

---

### Post by Windows Refugee on 2008-12-22
Another thought...

Is this computer using (or being assigned) the same IP address when you boot Windows, as it is when you boot Ubuntu ?

---

### Post by Windows Refugee on 2008-12-22
Oops... 

I thought your first screenshot showed TX & RX errors on eth0, but I was reading it wrong.
There doesn't appear to be any obvious problems with the output.

Sorry for the confusion !

---

### Post by GribbleMR2 on 2008-12-22
PROBLEM FIXED!!!!!!!!!!!!!!!

I am now posting from Ubuntu to triumphantly announce that I am a dumbass, and simply needed to put it back in DHCP (address only) and this time type in the CORRECT DHCP IP!  Thanks again to everyone that tried to help!  Sorry for wasting your time.

---

### Post by Iowan on 2008-12-22
Glad it's fixed - it's not a waste of time if a problem gets solved.  Triumphantly mark this one [SOLVED] (Under Thread Tools).

---

