---
title: "Acer Aspire One/Atheros AR9285 drops wireless connection since upgrade of v9.10"
date: 2009-12-19
forum: Networking &amp; Wireless
---

### Post by flopwich on 2009-12-19
I have an Acer Aspire One configured for double-booting with Ubuntu v9.10 and Windows XP Home.  The wireless works fine on the Windows side and used to with Ubuntu as well, even after I upgraded to v9.10.  I ran System Manager the other day, though, and after it updated Ubuntu the wireless was broken.  It connects when you first boot up and then drops the connection after about 10 seconds.  It won't reconnect without rebooting, and then the same thing happens.  Ubuntu is able to connect with a direct Ethernet connection without a problem.

I've attached a Word 97 file with all the information you say to gather.  Note that since the wireless won't work I gathered it all with the Ethernet connection only, except for the search for wireless networks.  If you need more information, please let me know, but be explicit.  I'm a noob with Linux and need precise instructions.

I posted a thread on this problem on the beginners' forum, but the discussion went cold after a couple of days with no success on my end.  The link is here: [http://ubuntuforums.org/showthread.php?t=1354252](http://ubuntuforums.org/showthread.php?t=1354252)

Thanks for your help.

---

### Post by coffeecat on 2009-12-19
I had flakey wireless with 9.10 on this Acer laptop with the Atheros AR928X wireless chipset. But it was flakey from the start, not good and then problematic after an update. Anyway, it was fixed by installing these two packages:

linux-backports-modules-karmic-generic
linux-backports-modules-wireless-karmic-generic

They'll pull in the 2.6.31-xx numbered package to correspond to your kernel. You need to reboot after you install them. Obviously, you'll need to use your ethernet connection to do the install. You'll get updated drivers including the Atheros wireless ones. No guarantee that will work with the AR9285, but it's worth a try.

---

### Post by flopwich on 2009-12-20
[quote=coffeecat;8528060]I had flakey wireless with 9.10 on this Acer laptop with the Atheros AR928X wireless chipset. But it was flakey from the start, not good and then problematic after an update. Anyway, it was fixed by installing these two packages:

linux-backports-modules-karmic-generic
linux-backports-modules-wireless-karmic-generic


Thank you, but, no joy. On the first boot-up it didn't connect at all, but reported that I was disconnected as soon as I booted up. After that it looked just as before, with a connection established at first, that it then dropped in a few seconds.

---

### Post by coffeecat on 2009-12-20
Sorry to hear that didn't work for you, but I found this:

[https://help.ubuntu.com/community/AspireOne/Ubuntu9.10](https://help.ubuntu.com/community/AspireOne/Ubuntu9.10)

Scroll down to almost the end of the page. Apparently you need the Madwifi driver. Instructions and link are there.

---

### Post by flopwich on 2009-12-21
> **coffeecat said:**
> Sorry to hear that didn't work for you, but I found this:

[https://help.ubuntu.com/community/AspireOne/Ubuntu9.10](https://help.ubuntu.com/community/AspireOne/Ubuntu9.10)

Scroll down to almost the end of the page. Apparently you need the Madwifi driver. Instructions and link are there.

I'm working on following these instructions.  Unfortunately, the files are now stored on a different site than listed there, they don't appear to be in the same format listed there, and that makes things a bit sticky for a Linux noobie to figure out.  I may be at this a while.

---

### Post by flopwich on 2010-01-10
Ah, the resolution is come!  It turns out that the Ubuntu upgrade that locked me out of wireless access set the connection profile in the connection editor so that both the IPv4 and IPv6 Method were set to DHCP.  My wireless access point is about five years old, though, and can't handle IPv6.  I set the Method for IPv6 to "Ignore" and everything started working immediately, without a re-boot.

I'm so glad to have Ubuntu back.  Without the wireless access capability this netbook left me either with a brick or being forced back to the Borg and using Windoze.  What a horrible fate!

Thanks to all you folks for trying to help.  I do appreciate your efforts.  I learned a few things about the operating system through your advice.

---

### Post by boyevil on 2010-02-13
> **coffeecat said:**
> I had flakey wireless with 9.10 on this Acer laptop with the Atheros AR928X wireless chipset. But it was flakey from the start, not good and then problematic after an update. Anyway, it was fixed by installing these two packages:

linux-backports-modules-karmic-generic
linux-backports-modules-wireless-karmic-generic

They'll pull in the 2.6.31-xx numbered package to correspond to your kernel. You need to reboot after you install them. Obviously, you'll need to use your ethernet connection to do the install. You'll get updated drivers including the Atheros wireless ones. No guarantee that will work with the AR9285, but it's worth a try.

Note this fixes low reception as well.

---

### Post by cake_or_death on 2010-02-23
> **coffeecat said:**
> I had flakey wireless with 9.10 on this Acer laptop with the Atheros AR928X wireless chipset. But it was flakey from the start, not good and then problematic after an update. Anyway, it was fixed by installing these two packages:

linux-backports-modules-karmic-generic
linux-backports-modules-wireless-karmic-generic

They'll pull in the 2.6.31-xx numbered package to correspond to your kernel. You need to reboot after you install them. Obviously, you'll need to use your ethernet connection to do the install. You'll get updated drivers including the Atheros wireless ones. No guarantee that will work with the AR9285, but it's worth a try.

This fixed my wireless immediately.  I tried it yesterday on my new AOD250-1613.  No more dropped connections, and about 20% better reception.
-- immediately after a reboot, that is.

---

### Post by patrikh20 on 2010-10-06
Just wanted to put this out there. I have an aspire one 532h and was having trouble with the wireless. I finally figured out it was the hardware sensor applet for awn. Most random thing, if it was ensiled my wireless would drop and connect every couple of seconds. Turned it off on works awesome.

---

