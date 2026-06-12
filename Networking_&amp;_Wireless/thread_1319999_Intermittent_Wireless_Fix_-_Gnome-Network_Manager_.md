---
title: "Intermittent Wireless Fix - Gnome-Network Manager is Broken"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by gerowen on 2009-11-08
I thought I would post this for anybody having issues with wireless since there seems to be a lot of these popping up since 9.10.  When I installed 9.10, my wireless, which worked fine in earlier versions, was intermittent.  It would drop signal, disconnect randomly, or traffic would just stop for a few seconds, and I'm sitting literally less than 5 feet from my router.  I tried all kinds of tweaks with the network manager and couldn't figure it out.  However, my issues now are fixed thanks to a little piece of software called wicd.  Wicd is a network management program that allows you a lot of the same functionality, and in a few places a little more, than the Gnome-Network-Manager.  I've been using it for a couple of days now and have had no issues.  I have transferred GBs of data to my server at an average speed of 2 MB per second over wireless with no drop in service or any of the issues I had before.  If any of you are having issues with wireless, try out wicd, it might just fix your problem(s).  The only real problem I've seen with wicd is that it has no option to disable your wireless.  This isn't a problem because I have a wireless switch that I use anyway, so it kind of eliminates redundancy, however if you don't have one of these switches and want to disable your wireless, you may need to write your own script to turn it on and off.

---

### Post by StarryFlag on 2009-11-08
Lovely information. But how could I install that wicd?

---

### Post by GarrettFoster on 2009-11-08
Open the software center. Search for Wicd and tell it to install. It will automatically remove Network Manager.

---

### Post by bkratz on 2009-11-09
> **StarryFlag said:**
> Lovely information. But how could I install that wicd?




Be very careful though, I tried WICD (which removed network-manager) and not only did it not help, I then lost my wired connection also, forcing a system reload with 9.10.  I am waiting to see what fixes occur with NM before attempting wireless again.

---

### Post by DrawnToScale on 2009-11-09
> **bkratz said:**
> Be very careful though, I tried WICD (which removed network-manager) and not only did it not help, I then lost my wired connection also, forcing a system reload with 9.10.  I am waiting to see what fixes occur with NM before attempting wireless again.


Please report back your findings.  Is is not possible to un-install the WICD and re-install the Network Manager?  I guess you run the risk of having no connection and then you can't download any fixes, huh?

---

### Post by StarryFlag on 2009-11-09
> **GarrettFoster said:**
> Open the software center. Search for Wicd and tell it to install. It will automatically remove Network Manager.

That's helpful, sir, considering my wireless is "trouble", it can not connect to the internet, and I have no wire connection available (My modem has a built-in wireless router, and I have no Ethernet wire.)

Also, the page which we can manual download .deb package doesnt have wicd for karmic. So that's a no-go.

---

### Post by Seventh Reign on 2009-11-09
wicd was no help here.  I've had to revert back to Jaunty for the time being.  No solutions have been successful.  Under Karmic, Both Wireless and Wired connections drop constantly.  Connection strength is constant 100% with no fluctuation.  Connection strength under Jaunty jumps between 73% and 93%

---

### Post by ununpentium on 2009-11-27
A clue...

In past I installed Ubuntu 8.xx, then I upgraded to 9.04, then to 9.10, and I never got problems with the wireless connection... (just an increased slowness with 9.10, but never intermittent or disconnections...).
Now I formatted the hard disk (Due to problems...), and I installed ubuntu 9.10 directly... and I have the intermittent wireless problem...

So, how is this possible? What is the difference between an upgraded 9.10 and a directly installed 9.10?

I just installed backports etc... nothing!

Why in past I didn't get the problem? What do the 8.xx and 9.04 versions put on our hard disks that 9.10 does not?

Any idea?

I hope this can help...

---

### Post by arban on 2009-12-06
I have also been having problems with wireless connectivity since installing 9.10 and thought I would share my progress thus far.

First some basic info. I am using a Compaq Presario V2000 laptop paired with a Belkin Wireless Pre-N Router (model F5D8230-4) setup as an access point using 128-bit WEP. Prior to stalling Ubuntu 9.10 the laptop was running Gentoo Linux since purchase. I had no problems with wireless connectivity on that platform using ndiswrapper and the Windows supplied driver inf file. Also making use of this router is a Dell XPC laptop running Windows XP with no connectivity problems.

Since installing Ubuntu 9.10, the initial connection to the wireless router works fine but after a minute the connection is dropped. I have tried switching from the Ubuntu suggested driver (BCM43xx) to ndiswrapper using the Windows provided driver (bcmwl5a) but that did not appear to have any effect. I have also hand edited /etc/network/interfaces and called 'sudo ifup eth0' with the same connectivity issues. Before replacing network-manager with wicd, as suggested above, I happened to go over to my in law's place. Using their wireless router, I had no problems with making and keeping the wireless connection and there were no speed issues of note. I do not know the setup of that router. 

Earlier this week I installed wicd. While I like the user interface better I still have the same connectivity issues. Today I tried changing my route to broadcast on G only rather than on both B and G. That did not solve the problem for me either. I also check and the router has the latest firmware. So now I am without any other ideas.

---

### Post by arban on 2010-01-01
Happy New Year All

A quick update on my wireless issue ... which may no longer be an issue. I just changed my wireless router's security setting from using WEP to WPA (TKIP pre-shared key) and now my laptop remains connected and I can access the internet. At first it would not load a webpage but soon after I seem to be having no problems browsing the web. Not sure why the security setup would effect connectivity. If anyone is qualified to comment on this it would be good for my brain.

---

