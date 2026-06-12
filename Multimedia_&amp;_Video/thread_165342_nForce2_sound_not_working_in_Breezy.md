---
title: "nForce2 sound not working in Breezy"
date: 2006-04-24
forum: Multimedia &amp; Video
---

### Post by jonqrandom on 2006-04-24
After a couple of months of my old PC being very very dead, i got given (amongst other things) an asus A7N8X nForce2 mobo with onboard sound, which shows up like so in lspci:

0000:00:05.0 Multimedia audio controller: nVidia Corporation nForce MultiMedia audio [Via VT82C686B] (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)

Sadly, i've had no luck with the sound - it didn't work at install, the fix at [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly) didn't work (presumably because it's for 5.04 and i'm running 5.10), and installing the nForce audio drivers didn't work either (i installed them, following the instructions at [http://ubuntuforums.org/showthread.php?t=96370&highlight=nvidia+sound](http://ubuntuforums.org/showthread.php?t=96370&highlight=nvidia+sound), but again no joy, so i uninstalled them)

I don't know whether this would affect anything, but i have a Bt878 vidcap card in too;

0000:01:08.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
0000:01:08.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)

it was in my last ubuntu box and worked fine alongside the onboard sound on that mobo and another sound card to boot :/

Now i *could* stick a cheapo old soundcard in, if all else fails, but i'd rather not, so any help would be greatly appreciated :)

[SIZE="1"](apologies for the repost, i don't know how in the *hell* i managed to post this in "Ubuntu Forums > Support & Resources  > Previous Release Archive  > Warty Warthog 4.10  > Warty 4.10 Application Support  > Ubuntu Live CD", but anyway...:confused: )[/SIZE]

---

### Post by jonqrandom on 2006-04-25
bump :/

---

### Post by rickc on 2006-05-14
I have the same problem....
Hmmmm I'll keep looking & post back if I have any luck finding a workthrough and or another driver/patch

---

### Post by rickc on 2006-09-25
I got my sound to work on 2 speakers, but I don't think linux has a driver that allows for 2 outputs for sound like windows does

---

### Post by jocko on 2006-09-25
Have you tried this [howto]("http://www.ubuntuforums.org/showthread.php?t=253725")? 
I wrote it to explain how I get my sound working on an nforce 2 motherboard with integrated soundstorm (which I believe asus A7N8X also have).

Good luck

---

### Post by rickc on 2006-09-26
> Have you tried this howto?
I wrote it to explain how I get my sound working on an nforce 2 motherboard with integrated soundstorm (which I believe asus A7N8X also have).

Good luck
Reply With Quote

No I haven't, but I  am now. It looks just like what the DR. ordered. Thanks again. Now I can get my DFI LANPARTY NFII ULTRA motherboard to work 100%. :D

---

### Post by GabbaGandalf on 2006-10-26
> **jocko said:**
> Have you tried this [howto]("http://www.ubuntuforums.org/showthread.php?t=253725")? 
I wrote it to explain how I get my sound working on an nforce 2 motherboard with integrated soundstorm (which I believe asus A7N8X also have).

Good luck

is there no other way to get 5.1 and/or my subwoofer work?

got a a7n8x deluxe rev2 with soundstorm and i want to use 5.1 sound.

---

