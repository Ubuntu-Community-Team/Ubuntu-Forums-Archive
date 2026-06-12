---
title: "Sound card problem, detected but not working."
date: 2005-11-19
forum: Multimedia &amp; Video
---

### Post by RubberChipmunk on 2005-11-19
Okay, this issue is really confusing and/or frustrating me.

I've used Ubuntu (well, linux in general) before, but had to switch back to windoze because I couldn't get sound working. Now, I'm back on linux with Ubuntu, and I'm still having problems setting up sound. Oh, the irony.

Actually, I am a bit excited because I'm further than I was before. After I gave up trying to figure out what my onboard sound chip was, I threw in a CompUSA 4 Channel sound card that I had been using in my last computer. The card itself uses the CMedia CMI8738 Chipset. When I put in the card, Ubuntu autodected it, and I can adjust volumes and everything. I made sure to attach every cable I needed to attach to get this to work, but l am not hearing any sound through my speakers.

I am very confused about this. Anyone have any ideas?

---

### Post by Joeb on 2005-11-19
I just responded in the other section, but the same two questions apply.  Did you disable your on-board sound in your BIOS?  And, the second was which sound system are you using, ALSA or OSS?

Joeb

---

### Post by RubberChipmunk on 2005-11-19
As far as I can tell, onboard sound is disabled. I disconnected every wire from it that I know of, but this computer isn't very well planned out (note to self, never get another compaq). If there's something I need to do other than disconnecting it, then I don't know about it.

Using the ALSA sound system.

---

### Post by Joeb on 2005-11-19
[QUOTE=RubberChipmunk]As far as I can tell, onboard sound is disabled. I disconnected every wire from it that I know of, but this computer isn't very well planned out (note to self, never get another compaq). If there's something I need to do other than disconnecting it, then I don't know about it.

Using the ALSA sound system.[/QUOTE]

The wires aren't the part that needs disconnected, but the System BIOS needs to have it turned off.  I'm not sure how you get into the BIOS settings on your computer but usually it is some keypress combination while the computer is booting (like holding down the "delete" key).

You might try changing from ALSA to OSS to see if that works (however, I've had better luck with ALSA).

Now here are a couple of  "stupid" questions, so I hope you aren't offended (as most of us have stumbled from them).  First, are you sure your speakers work?  Second, are you sure in the ALSA mixer control, you don't have some volume "muted" (little red x over the speaker)?

Joeb


[EDIT] you might also check out [http://linux.iuplog.com/default.asp?item=94639](http://linux.iuplog.com/default.asp?item=94639)

---

### Post by RubberChipmunk on 2005-11-19
Of course I'm not offended.

Yes, the speakers work. I just used them with a Mac last night when I installed Ubuntu (to get the disk image) and they work fine.

And yes, I checked to make sure ALSA wasn't muted using *alsamixer* in the console.

I'll try adjusting the BIOS and get back to you.

---

### Post by RubberChipmunk on 2005-11-19
Okay, I adjusted the BIOS so that the onboard audio device is disabled. The only one enabled right now is the card.

Still no sound.

---

### Post by Joeb on 2005-11-19
[QUOTE=RubberChipmunk]Okay, I adjusted the BIOS so that the onboard audio device is disabled. The only one enabled right now is the card.

Still no sound.[/QUOTE]


Did you check out the link for sound troubleshooting?  Also, in the mixer controls is the master volume up AND the PCM volume?  What are you using to see if the sound works (startup sound, CD, .wav file, etc.)

---

### Post by RubberChipmunk on 2005-11-19
Actually, I didn't even see the link you posted until now. haha

Yes, all volumes are up and unmuted, including Master and PCM. I had been using a CD to test sound, but I switched to .wav files recently.

[EDIT]: I checked out the link and tried it. Still nothing. I've even switched speakers and that didn't work.

---

### Post by Madstone on 2006-01-20
In the BIOS have you tried changing the Plug and Play OS option to "No"?

---

### Post by Mtnear on 2006-06-12
Hi.  Was this ever solved?  I'm having the same problem only CMedia 8738 is the onboard chip for my motherboard.  I'm not getting any sound out of my system either.

---

### Post by CarbonPlexus on 2006-07-30
Yeah I have this problem too. I have an Audigy card. Is there anything else I can try? I know my sound worked fine in Breezy, I don't know why it would stop in Dapper... although I noticed originally when I wasn't getting sound it was because it was registering my onboard sound as the sound card (and I was getting sound out of that) so I changed the defaults and it now shows the Audigy card as default but now I'm not getting sound out of either one.

---

