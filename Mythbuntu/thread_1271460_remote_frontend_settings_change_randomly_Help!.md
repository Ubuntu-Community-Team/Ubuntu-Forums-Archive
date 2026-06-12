---
title: "remote frontend settings change randomly? Help!"
date: 2009-09-20
forum: Mythbuntu
---

### Post by epi 1:10,000 on 2009-09-20
Every time I exit and restart myth frontend or reboot my front end GUI changes.  Sometimes when I reboot and then got to watch recordings it will lock up.  Sometimes the remote frontend will lock up when I after I get to my recordings list and try to select a recording.  All my other settings are stable but some times it goes back to the configuration screen on start up.   Any one else ever encounter this?  Is it a hardware problem?

Gigabyte EP45-UD3L P45 mobo   with a Hot north bridge
Intel e7300 C2D
Galaxy 9800 GT
2 gig pny pc6400
Raidmax 600W PSU
Sony SATA DVD burner
Seagate 7200.11 500gb HD
WD green 1tb hd

---

### Post by epi 1:10,000 on 2009-09-21
update:

all memory passes memtest 86+ v1..70
memory modules tested individually

I tested the rails
11..96V,   5.06V,   3.42V
measures w/ fluke multimeter

Mobo keeps crashing and bios MB Intelligent Tweaker(M.I.T.) menu states that it keeps crashing because of overclocking or voltage fluctuations.  The 3.3V rail is running @ 3.42 witch is with in the +/- 5% range but still high.  This board has seen some abuse (board bending when installing cpu fan and when mounting on standoffs.  In addition I accidentally separated the northbridge heatsink when picking it up.  I cleaned off the old thermal pad/glue and aplied arctic silver 5 and remounted the heatsink.  The north bridge was running noticeably hooter than my other gigabyte p43 mobo so I added a northbridge fan and extra case fan which was effective in brining down the temps. The computer still has 3 or four crashes before it gets to my video card bios post screen.

I tried installing mythbuntu on the other HD and the settings stay stable but sometimes it freezes on mythfrontend program start or when I try to watch a recorded program.

Question:  If I am having hardware problems what do to narrow down to which component/s it is?

---

### Post by Boppy3125 on 2009-09-21
Is it possible you have DHCP and something odd happening with server name.  Usually, frontend settings are stored on the database related to the server name.  If this is a remote frontend, you may want to setup your frontend, look in the database to see if the settings saved, then look again after the reboot.  I use the MythWeb web site to look at those settings myself.  Just a thought.  Good luck.

---

### Post by klc5555 on 2009-09-21
This kind of heavy-duty hardware instability often ends up being a power supply problem. Dirty or unstable power produces lockups and spontaneous reboots that usually resemble memory module glitches.

Power supplies that come bundled with cases are generally complete lightweight worthless junk. Even from reputable case manufacturers. Almost guaranteed to die in a year or so -- sometimes slowly, sometimes with a bang and sparks. If you have a spare supply to swap in, you might want to run a test. If you decide the supply is the problem, go with a high quality replacement from a specialist like PC Power & Cooling. I've never had one of theirs fail in 15 years of using them.

---

### Post by epi 1:10,000 on 2009-09-21
I tried a different psu and still had the same problem but every thing worked fine when I switched out the mobo. THX for your help

---

