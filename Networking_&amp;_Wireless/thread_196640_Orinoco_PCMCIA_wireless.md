---
title: "Orinoco PCMCIA wireless"
date: 2006-06-14
forum: Networking &amp; Wireless
---

### Post by anderbubble on 2006-06-14
First things first:
PCMCIA Orinoco WiFi card (PC24E-H-FC) by Lucent Tech, rebranded to HP, upgraded from silver to gold, and flashed with the latest firmware. Using the card in a Toshiba Portege 3480CT.

The card works perfectly under windows, and I used it successfully with SuSE 10 and Ubuntu 5.10.

Searching for AP's (using network manager) yields no results. Same with iwconfig. If I specify an ESSID, I can connect, but signal strength is reported as 0% (even when sitting right next to the AP).

Plugging the card in yields both eth0 and wifi0 names. (In the past, it has been wlan0 and wifi0). A. lsmod shows that both orinoco and orinoco_cs modules are inserted. This, however, is getting out of my expertise. Is it possible that multiple drivers are loading for the same card, and interfering with each other?

Current tests:
personal orinoco gold card in personal dapper laptop: failure
borrowed orinoco gold card in personal dapper laptop: failure
borrowed cicso card in personal dapper laptop: success
personal orinoco gold card in borrowed winXP laptop: success

I've reinstalled dapper twice trying to fix this. Any help would be greatly apprectiated.

~jonathon

---

### Post by pedalwrench on 2006-06-14
I have sort of the same problem with Dapper, I have a orinoco silver card.

The card works in Mepis LiveCD, DSL LiveCD and Win98 and win2k.

I tried loading Dapper with no luck.  The card just doesn't do networking in Dapper.  DHCP doesn't work and neither does a static IP.  

From other threads in the forum this looks like a Dapper wide issue.

---

### Post by anderbubble on 2006-06-14
It might be useful if someone could just give a reason why there are two nodes into this device. Where do they come from? Is is supposed to do that, or is that part of the problem?

---

### Post by harishg on 2006-06-15
I have been using orinoco gold and it never gave me any problems with dapper.I use an encrypted connection and once I put in the key it worked without problem.The only problem I had was i put the key as ascii when it was a hexadecimal key.

---

### Post by anderbubble on 2006-06-15
Just to clarify, that is not my specific problem. I am using unencrypted AP's (and have tried with multiple AP's, including one of my own).

---

### Post by forkd on 2006-07-17
I'm having the same issue with my orinoco silver PC24E-H-FC, dapper doesn't see it at all.  

Just for fun I popped in my Asante AeroLan AL410-G, which never worked with Breezy, and it worked fine...even with WEP. 

After installation of Dapper I dist-upgrade and then neither of them work. :( 

now I know why there is a wait to buy a hand gun. ;)

---

### Post by mpvano on 2006-07-17
It might or might not have something to do with your problem. Wireless is currently very confusing because there are too many conflicting drivers and subsystems loading drivers and trying to adminster them being installed as part of the default installation.

It seems to more or less work, most of the time for me, but I can't believe some of the craziness that I find installed.

If you are seeing two interfaces, it's because the "hostap" series prism/orinoco drivers are the ones you are using.

On every orinoco or prism based system I have, BOTH sets of drivers seem to be loaded, but on my systems, the orinoco_xx driver suite is the one that's in use, and everything works fine.

The hostap_xxx module suite has completely different properties. In particular it loads custom firmware into prism chipsets. The second interface, called wifi0, is used for auxiliary control and is normally ignored.

You can see if BOTH drivers are loaded by the following two commands:

lsmod | grep hostap
lsmod | grep orinoco

You can tell which one "grabbed" the card and is actually running your wireless by looking for the "wifi0" device in iwconfig. If it's present, your probably using the hostap drivers.

I have two notebooks using the gnome utilities and orinoco cards to connect using DHCP to my WEP based wireless network. They were both clean installs and work just fine, as long as I don't try swapping cards around or reconfiguring them for wired ethernet or anything else complicated during a session.

I can't for the life of me figure out what is loading the unused drivers, but checks with dmesg see both sets being loaded. I suspect the WPA utilities are doing it when ifup -a is run - I think it's idiotic to let higher level drivers probe for and load drivers, but they seem to do so.

I also have a sneaking suspicion that the only reason that scanning is working with the orinoco drivers is that the hostap drivers have run and loaded new firmware into the cards - the last firmware in most prism based didn't used to be able to scan!

My primary notebook has a builtin card and I don't find the gnome applications workable since I roam between networks  a lot and need both static and dynamic addressing and a variety of security methods. I configure it with manually edited custom /etc/network/interfaces files because I have never been able to get any of the network managers to work properly for all the places I go.

Everything works fine here, for me, but I think the plain ubuntu installs I'm using only work by dumb luck, since there definitely shouldn't be TWO sets of drivers installed, as there is on every machine I own with prism chip sets installed......

Mario

P.S. I've tried reporting some of what I've found to the bug system (called Malone, but as near as I can tell, IT'S badly broken as well. I have an account, but can't use it because it seems to have a broken authentication system for people who have a different email address than their forum account name here - or so the Malone mailing list indicates). I haven't been able to log into that system at all, even though the system accepts my password as if the login completed - I'm just never logged in).

mv

---

### Post by tturrisi on 2006-07-17
The orinocos are sometimes tricky & confusing to get working because orinoco cards have been made using different chipsets over the years, and some rebranded ones use other chipsets and chipset model numbers, e.g. lucent, lucent-agere, agere, atheros, prism1, prism2, prism2.5.

As well the orinoco drivers have been sometimes a bit screwy.  The newer kernels and distros use newer orinoco drivers.  Check dmesg to see the driver version being loaded.

more info here:
[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Orinoco.html](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Orinoco.html)
[http://airsnort.shmoo.com/orinocoinfo.html](http://airsnort.shmoo.com/orinocoinfo.html)

---

### Post by az on 2006-07-17
> **anderbubble said:**
> 
Searching for AP's (using network manager) yields no results. Same with iwconfig. If I specify an ESSID, I can connect, but signal strength is reported as 0% (even when sitting right next to the AP).


But when connected, can you transfer bandwidth?  Because I think that the driver just neven got scanning functionality nor signal strength functionality.

I have an oriocco_cs card and it is one of the most reliable wireless connections I have known.  I can almost be a block away!

---

### Post by biodiesel-bri on 2006-07-24
Check this thread for the fix:
[http://www.ubuntuforums.org/showthread.php?p=1295873#post1295873](http://www.ubuntuforums.org/showthread.php?p=1295873#post1295873)

-B

---

### Post by numer on 2006-07-30
The reason for both wifi0 and wlan0 is (from [http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/FAQ?rev=HEAD&content-type=text/plain]("http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/FAQ?rev=HEAD&content-type=text/plain")):
"Host AP driver supports multiple virtual interfaces per wireless
card. wifi0 is the master radio interface and wlan0 is the first
virtual interface for this radio. Other virtual interfaces are wlan0ap
(for hostapd), and one interface per WDS link.

In most cases, one should ignore wifi0 interface and just use wlan0
interface. In other words, assign IP address to wlan0, not wifi0 and
in general, just ignore the wifi0 interface."


Unfortunately, my Dell TrueMobile 1150 which is an orinoco based card, is not being mapped to hostapp quite correctly (it is instead being mapped to orinoco), so I end up with wifi0 and eth0 - and this does not work...

I guess I should dig into the PCMCIA configs to correct this, but I am not sure how to do this. Yet.

---

### Post by xtemplarx on 2006-10-26
I'm having this same issue with my Lucent Technologies Orinoco Gold card.

My situation:  both 6.06 and 6.10 do the same thing.  When booting from the LIVE CD, the wireless card works flawlessly.  However once I install the distro to the hard disk, the card will activate, but never obtains an IP address and won't talk to the AP at all, even if I force a static IP and plug in all the network info by hand.  Pretty odd.

Works off the live CD, but not off of the installed distro.  What's up with that?  :P

---

### Post by xtemplarx on 2006-10-31
Update... tried it with a cisco aironet card...same story.  wireless works under livecd, but doesn't connect or talk to dhcp once the system's installed on the machine.

This really stinks coz I love the way ubuntu runs on my laptop... but I guess I'll have to go back to fedora or suse.  :(

---

### Post by lindenle on 2006-11-02
I would also like to report the same  problem. I have an orinoco gold PC24E-H-FC and it works just fine in my laptop under debian etch, but  does not work in Ubuntu 6.10. The module is loaded and the card appears to be working but it wil never pull an ip from my router.

One thing I noticed is the dmesg log shows information for the device as if it is eth0 but it is actually eth1. On my debian system the dmes log gives eth3 when the card is eth3. Maybe the module is screwed up?

---

### Post by escifell on 2006-11-03
I am in the same fix. Orinoco gold clone called enterasys on an IBM T20. Worked fine under 5.10 but flies like a brick under 6.06. Seen some comment that things get better under 6.10 also lots of mixed message boards saying that there is a interrupt comflict but I don't want to waste more time chasing this with deadends. All most unsatisfactory.

What I need is a simple clear message of what I need to do to get back on the air with my laptop.

Help please.

---

### Post by lindenle on 2006-11-10
> **lindenle said:**
> I would also like to report the same  problem. I have an orinoco gold PC24E-H-FC and it works just fine in my laptop under debian etch, but  does not work in Ubuntu 6.10. The module is loaded and the card appears to be working but it wil never pull an ip from my router.

One thing I noticed is the dmesg log shows information for the device as if it is eth0 but it is actually eth1. On my debian system the dmes log gives eth3 when the card is eth3. Maybe the module is screwed up?

Just an FYI I had the same probem in debian the 2.6.17-rc2 kernel. I think it may be a kernel issue ;). Of course I could not figure out how to build a newer kernel under ubuntu but under debian it was no problem so the machine is up and running. Hope this helps.

---

### Post by FrodoB on 2006-11-10
Post your output from dmesg please.

---

### Post by lindenle on 2006-11-11
> **lindenle said:**
> Just an FYI I had the same probem in debian the 2.6.17-rc2 kernel. I think it may be a kernel issue ;). Of course I could not figure out how to build a newer kernel under ubuntu but under debian it was no problem so the machine is up and running. Hope this helps.


I did find a nice how-to for building a linux kernel under ubunutu here:

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

### Post by FrodoB on 2006-11-11
I can comment that when I first read this post I decided to try my Orinoco Classic Gold PC Card 8410-WD/A also called PC24E-11-FC/R (Hermes I chipset) and it would not work on Edgy either. It started correctly in the dmesg output, but whenever I tried to use it the dmesg reported that the device had failed.

This surprised me, because the card still worked on Slackware 10.2 using Kernel 2.4 and it also had worked on Debian Sarge using kernel 2.8, no setup it was just found and easily setup.

So I then loaded the driver up on my old XP machine and replaced the firmware and put it back in Edgy and all is now well.

This is probably not relevant to this thread, but it might help someone who is looking for Orinico information and has the same card that I have. Sorry for the intrusion.

---

### Post by Nite_Hawk on 2006-11-29
I'm having the exact same problem with a Lucent Technologies Orinoco Silver card, model PC24E-H-FC.  The card works fine in the livecd, but once the system is installed, the network can not be accessed.  dmesg reports:

ADDRCONF(NETDEV_UP): eth0: link is not ready.

iwconfig reports that the card is getting a signal and grabs the correct ESSID, but it is set to 2MB/s for the rate which is odd.  ifconfig reports no traffic over the interface, and dhcp doesn't work.

This really has me scratching my head.  The card worked fine previously with an old 2.4 kernel debian sarge installation, and also with the livecd.  Very odd.

Nite_Hawk

---

### Post by escifell on 2007-09-03
Sorry to bring this thread back to life! But after total failure to get the Enterasys Roamabout PCMCIA card working (orinoco clone) I reverted to a wired network. However, I am back on the wireless track again and if there is a simple how-to to fix this problem I will do it. Otherwise I will consign the card to the bin and buy one that works out-of-the-box.

Issue is exactly as previous post. Card works OK as LiveCD but as soon as you install the connection goes bad - system knows about the network reports correct ESSID but it will not pickup the network niether using DHCP nor static IP address.

Thnaks

---

