---
title: "hvr-2250 problems"
date: 2011-02-21
forum: Mythbuntu
---

### Post by grunge09 on 2011-02-21
System:

AMD 965 3.4GHz Quad Core CPU
1GB DDR2 667mhz ram
1TB Samsung 7200 rpm SATA II HD
CDRW IDE Drive
Mythbuntu 10.10 64 bit release
This box is primary backend server with front end all in one.  

I followed Lowskys how to.  Could not get it to lock on channels.  So I used the DEV drivers.  Now I can lock on channels.

I can't seem to get the 2-83 analog cable channels.  I am using Bright House networks of Central Florida Cable.  I know an old CRT TV without a cable box can receive 2-83 channels.  I checked with my sisters tv.

So no 2-83 channels.

I can get the 2250 on DVB card settings to lock on channels with QAM 256 channel scan. 

I can even get it to record some channels on the front end (of the same box)

But when I want to watch LIVE TV, it starts to , it shows text of that channel briefly and then logs me out, and I have to log back into the system again.  And when I installed I set it to auto logon.

---

### Post by LowSky on 2011-02-22
You have a few differnet issues. First your using a Phenom II x4 965 with 667mhz DDR2 RAM? Is that even possible? To be faira mythtv box doesn't need to be super powerful, but that RAM and AM2motherboard are probably killing the performance of that AM3 processor. You have quite a bottleneck there. But on a more serious note: 1TB does fills up quick, so read up on auto expire, it will be a life saver. You dont want to turn on the frontend only to find those episodes you were saving for a rainy day were deleted to make room for some marathon of old kungfu movies your significant other wanted to watch.

Did you install the analog drivers? I don't really have a tutorial for that, plus they only work with lots and lots of tweeking last time I checked.

The log out issue is more than likely a problem with your video settings. What video card are you using?

check your playback settings  on the frontend under setup>TV settings>playback>playback profiles (screen 3/8)> change current video playback profile, until you find one that works.

I find the High Quality option works best for ATI graphics cards, and VDPAU for Nvidia card 84xx series or higher. Also make sure you enabled your proprietary graphic drivers

Like I said analog support is iffy, I don't use it and so I haven't contributed much to the thread that is somewhere in this same portion of the forum.

---

### Post by grunge09 on 2011-02-22
It was a system that I threw together.  I found the MB and CPU on Ebay for a steal, the rest I had in parts and extra stuff from other machines I had lying around.  I wanted a zippy backend server.  Dual tuners streaming info across a gigabit network.   The ram was from another machine that won't miss it anymore.  Anyhow,,,,

I guess I should have done more homework about the HVR-2250 before I bought it.  I saw dual tuners, analong and digital support,  and Qam support so I got it.  Didn't know it was not fully supported yet in mythbuntu.  (I tried a live cd of mythknoppix last night really same issue no analog support).

Video card is a Nvidia 210 with vga, dvi & hdmi out (hdmi out to my 37" lcd)

I have been using Ubuntu linux for 5 years, still kinda a noob at linux, but the community suppport is great.   I have been working on pcs for 20 years.  1st one was an IBM ps2 model 30 286.   Used to run a BBS on a 386fx/40 when that was the fast thing, ran dos 6's interlink via lpt port to backup systems via a jumbo 120 tape drive.  Then got 2 NIC's and lantastic via COAX, and it snowballed form there.  

I have 6 pcs at the house now.  A 4tb rack raid array, gigabit switch, most of the machines are AMD 965 quad cores but on AM3 motherboards with sata 300 drives.  Couple of AMD 6000+ systems.  All but one pc is ubuntu (sister is died in the wool XP user I gave her a ubuntu pc it has to be her choice to switch).  

Just wanted to let you know I am not dumb by any stretch, just a little fuzzy on linux yet.

---

