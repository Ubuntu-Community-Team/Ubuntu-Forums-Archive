---
title: "kworld video input for digital video conversion"
date: 2013-01-19
forum: Mythbuntu
---

### Post by bah1976 on 2013-01-19
Hi folks - this isn't strictly a mythbuntu or maybe not even a mythtv question, but I'm hoping for the voice of experience here.

Has anybody used the input on a tuner card to capture auxillary A/V?  I've got a kworld 115 card that has a yellow rca video and 3.5mm audio input.  I'd love to be able to "tune" to that "channel" and record whatever's coming in to a mp4 or something.  I'd like to be able to do this to leverage my existing hardware to convert some old home movies & vhs tapes to the digital age, and use Plex to easily view them.  I think this should be similar to using them to record from a cable box, but without a specific program ID, but mine are strictly ATSC tuners and I've never configured anything besides the direct coax inputs.  Any thoughts or pointers on this forum?  

Thanks...

---

### Post by klc5555 on 2013-01-19
You should be able do this inside or outside of Mythtv.

Inside of mythtv, in the backend setup, set up a Video Source with no grabber. Call it "conversion" or whatever. In Input Connections, bind this Video Source to the unused Composite input of your card. 

In Channel Editor, go to this "Conversion" video source and add a channel to it. Give the a number, say "3" or "4" Mark the channel as "invisible" (because you don't need it to appear in your schedules listings) Go back into Input Connections and set this channel as the startup channel in preference to "Please add" for this composite input. Exit.

Now you should be able to Manual Schedule recording through this input, as though it were an odd sort of VCR, or you can run it in LiveTV and watch what it's cranking in by changing LiveTV to the "conversion" Video Source by means of the on-screen "m" key menu when you've entered LiveTV. After your LiveTV "show" is complete, you go into the AutoExpire list and move this livetv recording into the Default group, where it becomes permanent and can be trimmed, edited, and transcoded like any other Mythtv recording.

Outside Mythtv, I suppose you'd use v4l-utils to control the Composite input of your card directly (if this card has been set up in Mythtv with "open dvb on demand", so Mythtv releases it when not in use, and the card is not otherwise engaged in a recording).

```
v4l2-ctl -n
``` would likely list all the card's inputs.```
v4l2-ctl -i 2
``` (or the number listed for the composite input) would likely change this to the Composite input. Then,
```
cat /dev/video0 > video.mpg
```...or whatever /dev/videoX number the device is on, should produce playable recording "video.mpg" from whatever's coming in through the card's analog tuner.

---

### Post by bah1976 on 2013-01-21
Appreciate the input..  I'd like to use the mythtv method, but I don't have an unused composite input in Input Connections.  My kworld 115 cards are setup as dvb cards, and it sees them as Air2PC V2.  There's nowhere there to set them up with the composite input that I see.  Do I need to add another card somehow?  Maybe an "Analog V4L capture card"  I cycled through my choices, and don't see any options that aren't "failed to open".

---

### Post by bah1976 on 2013-01-21
Ok, I added a v4l card, and associated the input with it, but I can't find it in the front end.  If I try to "C" to switch cards, it's not there.  Or Menu/switch input.  Or channel up/down to the new channel "1".  Other thoughts?

---

### Post by klc5555 on 2013-01-21
> **bah1976 said:**
> Appreciate the input..  I'd like to use the mythtv method, but I don't have an unused composite input in Input Connections.  My kworld 115 cards are setup as dvb cards, and it sees them as Air2PC V2.  There's nowhere there to set them up with the composite input that I see.  Do I need to add another card somehow?  Maybe an "Analog V4L capture card"  I cycled through my choices, and don't see any options that aren't "failed to open".

You need to add the analog portion of the card as a separate tuner, which will set itself up (probably) on /dev/video0 In fact examining the output of dmesg after a boot may show that it's already present /dev/video0. The s-video and composite inputs in Mythtv setup's Input Connections will be subsets of the analog tuner. 

How to set up the K115 analog tuner in Linux/Mythtv? Darned if I know precisely, since I don't have one of these cards. All I know is that it's supposedly easily doable, that there is a lot of internet traffic out there where this card has been used for analog in Mythtv for years, and that the relevant V4l guide is [http://linuxtv.org/wiki/index.php/KWorld_ATSC_115](http://linuxtv.org/wiki/index.php/KWorld_ATSC_115)

Good luck!

---

### Post by bah1976 on 2013-01-21
I'm making progress.  I've got video coming in.  I have to wait until I get home to see if audio works.

Thanks for the help so far!

---

