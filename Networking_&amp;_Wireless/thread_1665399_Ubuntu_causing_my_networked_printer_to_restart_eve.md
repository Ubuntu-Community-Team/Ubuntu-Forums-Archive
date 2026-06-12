---
title: "Ubuntu causing my networked printer to restart every 5 minutes"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by fogNL on 2011-01-12
This is a bit of a long one, so please bare with me.

I recently received a new HP Laserjet 1536dnf printer from a company I just started with.  When I hooked it up to my network, and ran the installer, the printer was doing this odd thing that every 5 minutes (almost exactly), it would display "Error 49 turn off turn back on" on its screen, then restart and go through the initialization phase and back to the regular screen.  Other than when it was doing this, it could still print/scan/etc without issue.  Being a home office, the noise the printer would make would be very loud and annoying (every 5 minutes!).  So, I called HP, they did the regular checks, checked to see if it was firmware, etc.  Finally they replaced it with a new one.

I receive the second one, hook it up, low and behold, same issue.  Now I'm thinking its something with my environment.  I call HP tech support again, and they guy is 100% sure its being caused by my toner cartridge that I got with the printer, and that the problem will be resolved when I get a new cartridge (they weren't going to replace it obviously).  While he seemed quite sure about this, something just didn't seem right with that solution with me.  Rather than going out and wasting money on a cartridge i don't need just yet, I decided not to move on that.

Then, one day I was re-arranging some stuff, and I unplugged the LAN cable from the back of the printer and forgot about it.  I realized after a while, that the printer was no longer restarting every 5 minutes, so, it must be a network issue somehow.  I tried using different cables, etc, nothing seemed to do it.

The next day, I had my little home theatre PC turned off because I was cleaning up cables behind my tv, and I noticed that hte printer wasn't restarting anymore.  When I turned on the HTPC, a few minutes later, the printer would start restarting every 5 minutes again.

The HTPC I have is a Zotac MAG with a copy of Ubuntu 10.04 32bit installed on it.  Its currently the only Ubuntu system on my network, I have 4 other computers running with a mix of Win7 and WinXP.

So, now i'm trying to figure out what in god's name can be running on this little Ubuntu box that's causing my printer to restart every 5 minutes (on the dot).  I've checked cron, I don't see anything going.  Thinking it may be related to avahi, I stopped that service, but it continues to happen.

I decided to run wireshark to see if anything is being sent to the printer from the HTPC at the exact moment the "49 error" pops up, and this is all I see:

> 34	09:53:54.904796	HewlettP_3e:d7:40	Broadcast	ARP	Who has 192.168.1.6?  Tell 192.168.1.27

(192.168.1.27 is the printer, 192.168.1.6 is the HTPC)

Does anyone have any suggestions on what else to look for?  I've gone through a few log files on the HTPC, but I can't seem to find anything.

Any suggestions, no matter how small is greatly appreciated.  Thank you.

---

### Post by fogNL on 2011-01-12
A little bit of additional info.  I was looking at my syslog on the HTPC, and came across this that seems to coincide with a reset of the printer:

> 
Jan 12 10:24:11 tauron kernel: [ 1862.198099] rtl819xU:SetHwReg8190pci(): [HW_VAR_ACM_CTRL] Write 0x1
Jan 12 10:24:11 tauron kernel: [ 1862.198105]
Jan 12 10:24:17 tauron kernel: [ 1868.194472] rtl819xU:SetHwReg8190pci(): [HW_VAR_ACM_CTRL] Write 0x1
Jan 12 10:24:17 tauron kernel: [ 1868.194478]
Jan 12 10:24:17 tauron kernel: [ 1868.235601] rtl819xU:Error TX URB for zero byte -2, error -2
Jan 12 10:24:23 tauron kernel: [ 1874.195467] rtl819xU:SetHwReg8190pci(): [HW_VAR_ACM_CTRL] Write 0x1
Jan 12 10:24:23 tauron kernel: [ 1874.195472]
Jan 12 10:24:27 tauron kernel: [ 1878.194475] rtl819xU:SetHwReg8190pci(): [HW_VAR_ACM_CTRL] Write 0x1
Jan 12 10:24:27 tauron kernel: [ 1878.194480]


In this machine i'm using a USB wireless device because the built in wireless didn't have much range.  Googling hasn't really given me much info on these, what I presume are, errors.

---

### Post by fogNL on 2011-01-12
I spent some time going through the printer's web control panel, and found an Advanced section that displays different features.  Going through these one by one, I found that disabling the "WS-Discovery" feature seems to have solved my issue.  Question is now, what does this do?  Do I need it?

With WS-Discovery turned off, I am still seeing in Wireshark that the line:

> 67	12:48:54.691955	HewlettP_3e:d7:40	Broadcast	ARP	Who has 192.168.1.6?  Tell 192.168.1.27

still appears.  As well, on the HTPC, I still get the:

> Jan 12 13:04:17 tauron kernel: [11468.218480] rtl819xU:SetHwReg8190pci(): [HW_VAR_ACM_CTRL] Write 0x1

At the very least every 5 minutes.  However, at least its no longer causing the printer to reset.

So, to summarize:

- Printer restarts every 5 minutes when connected to home network
- Appears this only happens when HTPC computer is connected
- Disabling WS-Discovery in Network->Advanced options on printer page resolves the issue.

Question remains, why does WS-Discovery being enabled along with this HTPC on the network cause the printer to restart every 5 minutes.  What on the ubuntu box talks with WS-Discovery?

---

### Post by fogNL on 2011-01-12
removed duplicate post.

---

