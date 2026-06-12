---
title: "no wireless found in 9.10 after install"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by rastro123 on 2009-10-29
Hi I just install 9.10 and now the laptop does not see the broadcom wireless card. I'm on line now with wireless using the live cd, and it sees it without problem, but twice now I've installed it on the hhd and it is just not there. Nothing. I did iwconfig and eth1 is not there. Can anyone please help, this is so frustrating after spending many hours at it?

---

### Post by chrisplymouth on 2009-10-29
Broadcom wireless support is broken in the fresh install. Plug your computer into a trusty LAN and update your repositories. Go to synaptic and search for bcmwl-kernel-source. Install the package and reboot your PC. Your broadcom wireless should now be working.

---

### Post by reylafo on 2009-10-29
Fixed on the final release!
Release Candidate was a No-go for Broadcom on a Dell-Inspiron-1545.
But re-installed final version and everything worked OK.

Ubuntu is awesome!

---

### Post by Kevin Kent on 2009-10-29
Tried the fix but still not got wirless on a Dell mini with 9.10 remix.  Anything else worth looking at??

---

### Post by MerlinsLair on 2009-10-29
> **chrisplymouth said:**
> Broadcom wireless support is broken in the fresh install. Plug your computer into a trusty LAN and update your repositories. Go to synaptic and search for bcmwl-kernel-source. Install the package and reboot your PC. Your broadcom wireless should now be working.

Thanks for the info! My wireless is now working albeit very, very slow. Wired is also working and also very slow. Other than that, I've not yet seen any other issues.

---

### Post by lloydlloyd on 2009-10-29
> **chrisplymouth said:**
> Broadcom wireless support is broken in the fresh install. Plug your computer into a trusty LAN and update your repositories. Go to synaptic and search for bcmwl-kernel-source. Install the package and reboot your PC. Your broadcom wireless should now be working.

Awesome. This worked for me on a Compaq Presario V6000.
Wireless up and running!!

Loving the Koala!

---

### Post by commonplace on 2009-10-29
Wow, this is the kind of showstopper that should have never made it into a final release. I've just finished the install on my wife's laptop and so far, the installer looked great until the graphics went crazy and I had to finish up blindly. And the first thing I encounter is no wireless connection. In 2009, I thought we were passed that. Ugh.

Hoping this fix works, at least, and hopefully this is the worst of it!

/Kevin

---

### Post by peakpc on 2009-10-29
Hi, I finally figured out the secret to making it work.
You have to install (enable) the hardware drivers running from the Live CD then (of course you can't reboot to make it stick, but if you install to the HD now it will be available after install and you can enable and reboot it get it working. At least this worked for me. (after one bad install and trying all the options in other posts.) :)

---

### Post by jtmedin on 2009-10-29
BTW is there some way to see the rate of down/up load on the ip connection? TIA

---

### Post by cptnazeroth on 2009-10-30
I was having the same problem and at first, the bcmwl-kernel-source thing didn't work. I have no clue what I did to get it to work. I did a bunch of things. Would it make a difference if I had "source code" checked? Because on my last attempt, I unchecked that before restarting and things worked upon restarting.

Otherwise, I did a bunch of other stuff involving fwcutters, ndiswrappers and firmware - But on my last attempt, when I tried to set up the ndiswrapper it said that my broadcom adapter was already installed - Out of confusion, I unchecked "source code" in the repository settings and restarted and it worked. That probably won't help anyone, but that's what I did. Pretty sure I did more then I had to as it seems the problems I had in Hardy are actually fixed. lol.

---

### Post by Stewtheking on 2009-10-30
**[SIZE="4"]Thankyou[/SIZE]** peakpc, I can confirm that method worked for me (hp 6735s, broadcom wlan drivers)

---

### Post by silver1973 on 2009-10-30
Thanks for your help, everyone. Everything works now!

---

### Post by ctt1wbw on 2009-10-30
Same here.  Thanks for the tip.  Any idea why it wasn't loaded at initial install?

---

### Post by vikas.sriv14 on 2009-10-30
I am a newbie and still can't work it out. Can somebody help me.

---

### Post by Kevin Kent on 2009-11-01
I have ended up following sequence in :
[http://ubuntuforums.org/showthread.php?t=1229614]("http://ubuntuforums.org/showthread.php?t=1229614")

Works fine now.:D

---

### Post by MerlinsLair on 2009-11-01
> **vikas.sriv14 said:**
> I am a newbie and still can't work it out. Can somebody help me.

Follow the thread linked above and you should be able to find an answer to your problem. I've copied the thread and link here for you...just in case.

> Kevin Kent 	 		**Re: no wireless found in 9.10 after install**
 		I have ended up following sequence in :
[http://ubuntuforums.org/showthread.php?t=1229614](http://ubuntuforums.org/showthread.php?t=1229614)

Works fine now.:grin:

---

### Post by jcolsen on 2009-11-02
I have tried a lot of things and still haven't fixed the wireless on my dell inspiron e1505
the network manager doesn't even let me enable wireless
the wifi light is on
is ubuntu gonna release a fix or will I have to keep fishing the web?

---

### Post by busman on 2009-11-17
> **jtmedin said:**
> BTW is there some way to see the rate of down/up load on the ip connection? TIA

Yes, click on your network connection, and it should open a new window, and click the "GENERAL" tab, and it shows the connection rate at the bottom of the window that opens.

---

### Post by kouakou on 2009-12-13
> **chrisplymouth said:**
> Broadcom wireless support is broken in the fresh install. Plug your computer into a trusty LAN and update your repositories. Go to synaptic and search for bcmwl-kernel-source. Install the package and reboot your PC. Your broadcom wireless should now be working.

Worked like a charm....I am loving the mini even more....!!!
Mille fois Merci !!!

---

### Post by jesuit99 on 2009-12-24
I installed ndiswrapper-utils along with this to help he bcm thing. also install b43-fwcutter. My wifi seems to be fixed even though i completely removed the softwares?

---

### Post by Jason ON on 2009-12-30
New to Ubuntu here and have installed 9.10, however my wireless doesn't seem to be working just like others have claimed.  I am dual-booting on a HP Pavilion zv6000 and the regular LAN works fine, but wireless isn't.

Let me share with you what I've done so far.  

When first loading U9.10 in the System > Administration > Network Tools, I had the wireless listed, but was labeled as inactive.

I tried the steps in this forum (System > Administration > Synaptics > looking for the Broadcom file and activating it.

Reboot and still no wifi and suddenly Network Tools does not list a wireless card at all.  I then tried this ([http://ubuntuforums.org/showthread.php?t=1229614](http://ubuntuforums.org/showthread.php?t=1229614)) as suggested in this topic, to no success.  Network Tools is still not seeing the card itself.  Did I miss something?

Please give me a hand, here.  I am not incommunicado since I have eth0 access, but I want to be a live boy, no strings attached.

Thank you, 

Jason

---

### Post by bkratz on 2009-12-30
> **Jason ON said:**
> New to Ubuntu here and have installed 9.10, however my wireless doesn't seem to be working just like others have claimed.  I am dual-booting on a HP Pavilion zv6000 and the regular LAN works fine, but wireless isn't.

Let me share with you what I've done so far.  

When first loading U9.10 in the System > Administration > Network Tools, I had the wireless listed, but was labeled as inactive.

I tried the steps in this forum (System > Administration > Synaptics > looking for the Broadcom file and activating it.

Reboot and still no wifi and suddenly Network Tools does not list a wireless card at all.  I then tried this ([http://ubuntuforums.org/showthread.php?t=1229614](http://ubuntuforums.org/showthread.php?t=1229614)) as suggested in this topic, to no success.  Network Tools is still not seeing the card itself.  Did I miss something?

Please give me a hand, here.  I am not incommunicado since I have eth0 access, but I want to be a live boy, no strings attached.

Thank you, 

Jason




You might try this one, it seems to work for most people

[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

---

### Post by ywh842005 on 2009-12-30
have u try System->Administration->Hardware Driver
I have the same problem with my Acer 5100 laptop Broadcom wireless. I went to hardware driver, it detect the wireless driver automatically, after i restart, the wireless works smoothly.

---

### Post by ywh842005 on 2009-12-30
Jason ON

have u try System->Administration->Hardware Driver
I have the same problem with my Acer 5100 laptop Broadcom wireless. I went to hardware driver, it detect the wireless driver automatically, after i restart, the wireless works smoothly.

---

### Post by Jason ON on 2009-12-30
I tried and even tried the steps here: [http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865) which were the same as the ones I tried above, but with the CD in the drive.

When I rebooted (I forgot to take the CD out) and booted off the disk I saw the wireless card listed again, but when I took the CD out and rebooted it is gone again.  When I go here:  System->Administration->Hardware Driver there is only a "software driver" listed, which is active.  There is no Broadcom 43xx listed.

Thanks for the suggestions, guys.  Keep 'em coming!

Jason

---

### Post by Jason ON on 2009-12-30
Okay, so I formatted the HDD and reloaded Ubuntu all together.  Once up I ran the System > Admin > Hardware Drivers and saw the BC43 driver which I loaded and activated.  Went to Network tools and the wireless card is "active" but I still can't get onto a wireless network (whose modem is 7 feet from where I'm sitting).  So I go back to Hardware Drivers and see another one listed for "Software Modem" which I activate as well since the description tells me I need it or my modem won't work.  Suddenly, the BC43 driver disappears and the wireless connection in Network Tools is no longer even listed.

If anyone has some step-by-step dummy poof directions for me, that'd be fantastic.

Thanks,

---

