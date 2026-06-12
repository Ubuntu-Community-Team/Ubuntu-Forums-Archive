---
title: "How often do you patch and update your system?"
date: 2011-11-02
forum: Mythbuntu
---

### Post by GaryP2 on 2011-11-02
I’m interested in learning how others manage their Myth installations from a patching and updates perspective. 
 
When I installed my first Mythbuntu 10.04/MythTV .23-fixes systems 14 months ago, I disabled all OS and applications updates (including security updates) right after pulling down all the updates available at that time after that initial installation. My systems have been extremely stable with only a couple issues that I researched when they happened and couldn’t find evidence at the time of being fixed. I don’t have any ports exposed to the Internet (such as to MythWeb), although they always has the ability to communicate out to the Internet to download the program guide (Schedules Direct), etc..
 
I keep all of my general purpose computers up-to-date, so it’s always concerned me somewhat to not do the same due diligence with the Myth systems. But given what Myth is doing and typically not getting a second chance at capturing much of what I record, I want to avoid any situation where I may compromise the system. I buy into the “if it ‘anit broke don’t fix it” to some degree but overall believe more in preventative maintenance for IT system. Plus if I ignore what it took to set up Mythbuntu for too long, I forget too many details and will really be in trouble when it finally break! (even though I took a lot of notes when I did the initial install)
 
I’m interested in how you do updates - how frequently, what updates you do – Ubuntu, MythTV, security updates only, etc. - if you’ve had issues or changed your approach over time, etc. Are you updating each time the Mythbuntu team releases an update (which is when Unbuntu releases their updates), or focused just on LTS releases and updating MythTV in between OS releases? Do you always keep MythTV current or only when you see compelling new features that you want to use.
 
Thanks much!

---

### Post by AlecJ on 2011-11-02
My system is on 10.04 Lts with all the updates now using .24 with fixes, works very well.
There were a few issues with old recording not being deleted and a full HD so not recording new shows, but once I deleted the 900Mb manually it's been fine since.

The new video drivers (Nvidia) are very good, way better, since BBC HD channels have gone DVB-S2 and I don't have any cards, but the picture is good enough not to bother with the cost of new cards.
 
Having problems with the new DVD's encryption, Still waiting for the fix to come down, it's fixed on my Desktop 11.04.

Oh and you lose the DVD rip function, but I rip from other computers on the network now

I do all the updates downloaded in the background then installed as and when I notice then.

---

### Post by GaryP2 on 2011-11-02
> **AlecJ said:**
> The new video drivers (Nvidia) are very good, way better, since BBC HD channels have gone DVB-S2 and I don't have any cards, but the picture is good enough not to bother with the cost of new cards.
Which NVIDIA driver version are you finding that is working well, and did you manually install it or was installed through the update manager or some other mechanism? My frontends are using 195.36.24. I read somewhere where newer 256.x and 260.x drivers showed more stream error artifacts and sometimes locked up the frontend. Although my frontends never lock up, I see more undesirable QAM stream error artifacts than than through built in TV QAM tuners. I’ve tried different variations of the VDPAU setting with about the same results. It’s not horrible through Myth but just more breakup than just watching through a TV.
 
Thanks for the feedback on everything else as well!

---

### Post by nickrout on 2011-11-02
I update my system about once a week. It is mainly mythtv updates from the mythbuntu repo, but I get all the updates and the system just keeps on going.

---

### Post by newlinux on 2011-11-02
I update my laptops regularly. I rarely update  my servers holistically. I do update certain packages here and there (like myth packages), but I stay away from kernel updates unless I'm specifically looking for something or doing an whole system update. I also go LTS->LTS for OS upgrades, usually a month or two after the LCS is out.

---

### Post by JamesNorris on 2011-11-03
> **nickrout said:**
> I update my system about once a week. It is mainly mythtv updates from the mythbuntu repo, but I get all the updates and the system just keeps on going.

Same here, although I haven't upgraded to 11.10 this time, 10.04 to 10.10 was fine, 10.10 to 11.04 was a mess and I've read the things about lirc problems with the 11.10 upgrade, and lirc breaking would significantly kill the WAF here, so I'll make do as-is for now.

---

### Post by AlecJ on 2011-11-03
> **GaryP2 said:**
> Which NVIDIA driver version are you finding that is working well, and did you manually install it or was installed through the update manager or some other mechanism? My frontends are using 195.36.24. I read somewhere where newer 256.x and 260.x drivers showed more stream error artifacts and sometimes locked up the frontend. Although my frontends never lock up, I see more undesirable QAM stream error artifacts than than through built in TV QAM tuners. I’ve tried different variations of the VDPAU setting with about the same results. It’s not horrible through Myth but just more breakup than just watching through a TV.
 
Thanks for the feedback on everything else as well!

Same as you, 195.36.24, but with Myth .24 the picture is noticeably better.

---

### Post by nickrout on 2011-11-03
> **GaryP2 said:**
> Which NVIDIA driver version are you finding that is working well, and did you manually install it or was installed through the update manager or some other mechanism? My frontends are using 195.36.24. I read somewhere where newer 256.x and 260.x drivers showed more stream error artifacts and sometimes locked up the frontend. Although my frontends never lock up, I see more undesirable QAM stream error artifacts than than through built in TV QAM tuners. I’ve tried different variations of the VDPAU setting with about the same results. It’s not horrible through Myth but just more breakup than just watching through a TV.
 
Thanks for the feedback on everything else as well!

Signal problem?

---

### Post by thatguruguy on 2011-11-03
From what I've read, mythbuntu will only be released every 2 years from 12.04 onwards (in accordance with the Ubuntu LTS release schedule), which probably makes a lot of sense.

---

### Post by GaryP2 on 2011-11-03
> **nickrout said:**
> Signal problem?
My cable DTV reception is awesome overall to where I doubt it’s a local issue very often if at all. One of the worse examples was watching a cable only channel (WGN from Chicago) and getting a lot of artifacts one weekend but only when Cubs baseball games were on. I never saw artifacts during commercials or other shows on WGN that weekend. That led me to believe it was more of an issue between where the games were happening and WGN master control. But during that time, I switched back and forth between watching live TV through Myth vs. a TV tuner and I found the Myth artifacts more annoying.
 
Ever since I built my Myth system, I’m super observant and critical of even the slightest DTV reception anomalies – and always wondering if it’s an issue with my Myth setup but typically concluding that it’s an issue external to me. I’ve got the original Silicondust HDHomeRun network tuners and have had excellent results with them.

---

### Post by tgm4883 on 2011-11-04
> **thatguruguy said:**
> From what I've read, mythbuntu will only be released every 2 years from 12.04 onwards (in accordance with the Ubuntu LTS release schedule), which probably makes a lot of sense.

This is true, I just haven't made a blog post about it yet. We will release only LTS releases (although we will still provide package builds for each release in between).

---

### Post by GaryP2 on 2011-11-07
> **AlecJ said:**
> Same as you, 195.36.24, but with Myth .24 the picture is noticeably better.
[SIZE=3][FONT=Calibri]Alec (or anyone else) – does the Ubuntu Update Manager ever try and get you to update to a newer version of the NVIDIA drivers under 10.04? In other words, did you deliberately have to choose to stay on 195.36.24? I’ve had my system frozen from all updates since the initial installation but am planning on having the Update Manager do it’s thing later this week in making everything current and was just wondering if I need to look out for an specifically unselect the driver update. When I installed the system about 14 months ago, I think that 195 was the most current at that time.[/FONT][/SIZE]

---

