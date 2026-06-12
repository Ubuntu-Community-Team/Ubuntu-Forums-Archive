---
title: "Will This Work?"
date: 2012-06-03
forum: Mythbuntu
---

### Post by jharadie on 2012-06-03
Wondering if this will work or does it need something different?

Computer: HP, Intel P4 3.0G CPU
RAM: 1G, upgrading to 3G
HD: 200G for MB, on an NTFS partition
Tuner: WinTV PVR 150 MCE PCI
Will do clean install of MB, adding Mate desktop
Comcast provides channels 2-29 without digital box, need digital box above that.

Will MB easily recognize/work with the WinTV card?  Or should I look for additional drivers?
Any comments about the WinTV card?

In many ways I'm still very much a noob, want to be as prepared as possible before taking the plunge. :)

Many thanks in advance.

---

### Post by tgm4883 on 2012-06-03
> **jharadie said:**
> Wondering if this will work or does it need something different?

Computer: HP, Intel P4 3.0G CPU
RAM: 1G, upgrading to 3G
HD: 200G for MB, on an NTFS partition
Tuner: WinTV PVR 150 MCE PCI
Will do clean install of MB, adding Mate desktop
Comcast provides channels 2-29 without digital box, need digital box above that.

Will MB easily recognize/work with the WinTV card?  Or should I look for additional drivers?
Any comments about the WinTV card?

In many ways I'm still very much a noob, want to be as prepared as possible before taking the plunge. :)

Many thanks in advance.

PVR150 is supported out of the box. It's an old card, but they were so popular that they are very well supported.

You mention an NTFS partition for Mythbuntu. I'm assuming you mean you are going to use WUBI, which I don't know much about. If you mean you are just using the NTFS partition for storage, I doubt that will work well, if at all.

:EDIT:

The rest of the hardware looks fine.

Why are you adding mate desktop? Is this a media centre or a desktop PC?

---

### Post by nickrout on 2012-06-03
> **jharadie said:**
> Wondering if this will work or does it need something different?

Computer: HP, Intel P4 3.0G CPU
RAM: 1G, upgrading to 3G
HD: 200G for MB, on an NTFS partitionyou need a lot more hard drive space if you want to do any serious recording.> 
Tuner: WinTV PVR 150 MCE PCIold card but a goodie in it's day. Are you sure cocast still does analogue? I thought analogue in the US was dead?> 
Will do clean install of MB, adding Mate desktop whay add another desktop? It is unneeded - mythtv runs full screen, you never touch the desktop> 
Comcast provides channels 2-29 without digital box, need digital box above that.

Will MB easily recognize/work with the WinTV card?  Or should I look for additional drivers?
Any comments about the WinTV card?

In many ways I'm still very much a noob, want to be as prepared as possible before taking the plunge. :)

Many thanks in advance.

mythbuntu will easily handle the card. It's a question of whether the card will handle your comcast TV.

---

### Post by tgm4883 on 2012-06-03
> **nickrout said:**
> you need a lot more hard drive space if you want to do any serious recording.old card but a goodie in it's day. Are you sure cocast still does analogue? I thought analogue in the US was dead? whay add another desktop? It is unneeded - mythtv runs full screen, you never touch the desktop

mythbuntu will easily handle the card. It's a question of whether the card will handle your comcast TV.

OTA analog is dead, but there was no mandate for cable companies to kill it off as well. Some have and I believe that Comcast has in some areas.

---

### Post by jharadie on 2012-06-04
Thanks for the info, much appreciated.

My bad:  This will only be a backend, but I need to put Virtualbox on, to run a small server.  That's why the Mate desktop.  Currently the machine is running Ubuntu 12.04 LTS, with an old IDE drive that's partitioned 80G for 12.04, 50G for stuff, and I set aside a 200G NTFS in anticipation of going to MB (wiping the 80G Ubuntu for the clean install).

200G won't be enough for MB?  What's the recommendation?  I don't need to record in HD, SD will work for my needs.

Our building has some sort of arrangement with Comcast about the analog channels (2-29).  While I'd like the WinTV card to handle the digital ones, as long as it can handle the analog ones, I'm good.

Thanks.  :)

---

### Post by nickrout on 2012-06-04
What is wrong with xfce? That's the desktop mythbuntu uses.

Why virtualbox? Are you wanting to run another OS? There's no reason (other than resources) that MB cannot act as a server too. I had a backend that ran as a mail and web server too, it worked. My current BE also runs squeezeserver and a torrent client.

200G is more than enough for the OS, but you will find the space limiting unless you want to record very little. Plan on getting a 1TB or 2TB drive before very long.

The PVR150 is analogue only. I haven't used mine for ages, and I cannot tell you how much disk space recordings take. However SD mpeg2 recordings from satellite are about 2G/hour, so I expect it would be similar.

---

### Post by jharadie on 2012-06-04
> **nickrout said:**
> What is wrong with xfce? That's the desktop mythbuntu uses.

Why virtualbox? Are you wanting to run another OS? There's no reason (other than resources) that MB cannot act as a server too. I had a backend that ran as a mail and web server too, it worked. My current BE also runs squeezeserver and a torrent client.

200G is more than enough for the OS, but you will find the space limiting unless you want to record very little. Plan on getting a 1TB or 2TB drive before very long.

The PVR150 is analogue only. I haven't used mine for ages, and I cannot tell you how much disk space recordings take. However SD mpeg2 recordings from satellite are about 2G/hour, so I expect it would be similar.

Thanks!  I thought I had to install a desktop, and that MB wouldn't allow anything else.  If it will let me run a mail & web server, that solves a lot of issues, really makes things easier.

I can limp by with the 200G for now (main thing is to get Jeopardy for my family).  I understand there's a way to convert MB files to avi (h264)?

The PVR 150 is just a starter.  My goal is a PCHDTV HD-5500 PCI, though I guess I should get the TB drive first.  :)

---

### Post by Lester_Burnham on 2012-06-04
Hi,

I would create the recording location on it's own partition, just to be sure you don't fill the system drive. As it will grind to a halt if full.

Not sure if mythbuntu has the smarts on its own to stop this happening if recordings are on the system drive. I'm unsure how good auto expire is this situation.

Lester

---

### Post by nickrout on 2012-06-04
> **Lester_Burnham said:**
> Hi,

I would create the recording location on it's own partition, just to be sure you don't fill the system drive. As it will grind to a halt if full.

Not sure if mythbuntu has the smarts on its own to stop this happening if recordings are on the system drive. I'm unsure how good auto expire is this situation.

Lester

Myth is smart enough to handle this, but it is certainly a good idea to use another partition for recordings.

---

### Post by Lester_Burnham on 2012-06-04
Thanks Nick

---

### Post by jharadie on 2012-06-04
Thanks to all!

:P

How do I mark this as [Solved]?

---

