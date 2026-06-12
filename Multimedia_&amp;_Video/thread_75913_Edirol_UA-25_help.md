---
title: "Edirol UA-25 help"
date: 2005-10-14
forum: Multimedia &amp; Video
---

### Post by joanverde on 2005-10-14
I got an Edirol UA-25 external USB 2.0 sound card.

Where can I find my Edirol UA-25 and use it as prime sound card?

How can I configure to use it for recording in i.e. Audacity?

Thx for any help,
John

---

### Post by joanverde on 2005-10-15
No one knows anything?

Please help me if you can; a good answer could become a good HOW-TO 
for other users.

Thx

---

### Post by rvdbogrd on 2005-11-27
Hi John,

Yesterday I bought the same device. I was actually a bit stunned by Ubuntu, detecting it neatly by name and popping up a dialog about a new soundcard, which told me to look in System - Preferences - Audio.

There the UA-25 was selectable as default sound device. It worked (system sounds and Rhythmbox playing mp3); tonight I tested Rosegarden MIDI output and even that was working.

However, for some applications I'm hearing continuously occurring glitches in the digital sound output, sounding like a severely scratched cd... Probably buffering problems. I couldn't get Audacity to work with the UA-25; maybe because it's using an other sound system (pardon my newbieness ;-)).

I hope my notes are of relevance for you - maybe you should upgrade Ubuntu to Breezy Badger. I suspect that makes some difference. I'll post updates to this thread when I'm getting any further.

ED: I'm seeing in other posts that you propably already upgraded to Breezy. Did you get the pop-up notification?

Regards,
Rob van den Bogaard

---

### Post by johngrinham on 2005-12-29
Hi all, first, I have Ubuntu on one machine, but I'm using 'Studio to go' and Agnula Demudi with my Edirol UA-25. (both Debian as is Ubuntu)

I can't use the ua-25 with Audacity(audacity seems very picky about what cards it will talk to, it won't talk to my Sound Blaster Platinum 5.1 either, but it will talk to the onboard AC97) (ps Audacity doesn't interface with Jack, so it must be turned off when using Audacity)

I also get these scratching noises, but they are only in the playback, they are not recorded. If you make the 'frames/period' in Jack bigger, you can replay previously recorded samples without noise, but the latency goes way too high.

I experimented with the 'AC97' (with the edirol still attached) and got scratches with it also, but then I removed the edirol and the scratches disappeared.

I have seen a couple of entries in windows forums with similar symptoms, so we could have a bug in the edirol, or maybe the driver (in ALSA) is not good enough. (but I don't think it  is just an Ubuntu problem).

What do you think.?

---

### Post by rvdbogrd on 2005-12-29
Thanks for the update, John. I would like to confirm that the scratching noises are present when using the internal (AC97) sound card of my laptop while the UA-25 is connected. They are absent while the UA-25 is disconnected.

Recently I got Jack and some soft synths running, along with Seq24 as a sequencer, although for the moment they are only usable with the AC97. Increasing frames/period for the UA-25 in Jack does indeed reduce xruns and restarts, but you have to set the thing to really insensible values... (as you said, too much latency)

I completely agree that this is probably not an Ubuntu problem.

---

### Post by bambinou on 2006-01-25
hi guys i will have to apollogise with my numerous grammar mistakes but english isnt my first language...but i still give a try :
i found this forum by mistake ,so i have red your questions about the ua 25 and might have the correct answers for you(i hope).
the strange noises that appears to come out of this little external sound card normally come from the phantom switch at the back that is turned on.put your headphones on and the volume at the maximum,turn the phantom on and off,you will hear a big sound output difference,having the phantom on can also affect the recording timing and other timing issues.
i have a sony laptop with an ac97 (like you guys)i had this crakling sound for ages and had enough,so i have done my own research and tryed different things.i have disabled the ac97 from the bios(or you can do it just via device manager),but i advise to disable it in the bios,this way even if you unplug your external sound card the comp wont look for another sound card(and of course install the drivers automaticly).
i have the sofware project 5 from cakewalk and do not suffer of anymore from timing problems or scratching noises from my ua-25,it took me a while to get my head around it but finally everything works fine now.other scratching noises could come from your onboard lan card too,if the first option doesnt work,try to unplug your lan cable and listen if anything happen.
the ua-25 is a very good sound card for home edition music.
i will check this forum sometimes to see if your sound works ok now


good luck guys




                              ben

---

