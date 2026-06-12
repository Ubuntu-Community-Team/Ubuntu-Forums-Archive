---
title: "[SOLVED] Very weird video issue"
date: 2008-04-10
forum: Multimedia &amp; Video
---

### Post by Thrasonic on 2008-04-10
Hello Ubuntu Community!  I'm using Ubuntu 8 beta and it's been very good.  I’m also a newbie so please keep that in mind.  Anyway, last night something strange happened.  I installed Virtual Box from the DEB download of their web site.  The installation told me that my account had to be a member of the VirtualBox group in order for me to use the program.  I added myself to the group and logged off, expecting to be able to log back in.  The screen went blank and nothing happened.  This has been going on with shutting down or rebooting since I started using beta 8, so after a minute of waiting I did what I always do and shut off the PC.

I turned it back on and the OS appeared to load as usual.  I logged in without a problem but than my screen went blank, sort of.  the background was black and I could see some windows open up (like Pidgin and Amarok) but those windows were solid white.  I couldn't make out anything.  So I figured that somehow my xorg.conf was jacked up.  I shut it off again in my usual manner and booted into recovery mode.  I went to a console and repaired the xorg.conf file, going with the defaults.  

I rebooted and something different happened this time.  Once the OS loaded I had a blank screen that occasionally flickered so I could actually see the desktop, but this was only for a brief second.  Something was totally jacked up.  I couldn't do anything and this was after fixing the xorg.conf file, setting it back to defaults.

I decided to do a wipe/reinstall.  This was a test drive so I’d lose nothing important.  I started the 8 beta reinstall with the alternate installation CD and it went as smooth as silk.  No hiccups at all.  However, upon reboot (once installation finished and prompted me to remove the CD) the same problem happened.  I thought that was very strange.  I turned off my PC and figured I’d try something else in the morning.

So this morning I removed the IDE hard drive and put another in its place and ran through the installation steps again.  I didn’t think this would work and sure enough it didn’t.  The same problem happened.  The one thing I haven’t tried and didn’t think of until on my way to work was to try and boot into safe mode or VGA mode or whatever it’s called in Linux speak.  If anyone thinks this might be a way to get back into the GUI let me know.  If anyone has seen this problem before let me know.  If the safe mode idea doesn’t pan out I’m going to install Kubuntu 7.10 and see what I get.  This is all just very strange.  Any ideas will be appreciated.

---

### Post by Thrasonic on 2008-04-10
So I figured it out.  I swapped the video cables and that did the trick.  Weird.  I was using a DVI cable and I swapped it with a VGA cable.  That's all it took.  Very, very strange.

---

