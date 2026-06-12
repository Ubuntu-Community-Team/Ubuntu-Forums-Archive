---
title: "[SOLVED] Cannot get 5.1 Surround to work"
date: 2007-08-06
forum: Multimedia &amp; Video
---

### Post by shadowen2 on 2007-08-06
Wow....lots of us having problems with our surround sound!  I am yet another in the masses who aren't able to get the surround working.  

Here's what I've done

1) Edited ~/.asoundrc  so it looks like

     pcm.!default {
          type plug
          slave.pcm "surround51"
          slave.channels 6
          route_policy duplicate
     }

2) Checked alsamixer and turned the volume all the way up on all devices.
3) Checked the permissions on ~/.asoundrc and set them to 777 so I know it's readable.
4)  Ran the speaker test utility and only got sound through the front left and the front right.
5)  Rebooted the machine and ran speakertest again...just to make sure....still not working

I'm running a Soundblaster Live 5.1 Platinum (yes, I know it's old) on an Athlon X2 4200 with a Biostar Mobo.  Everything works on this up until this point.  The system is connected to a Sony amplifier (for my home theatre) via the SPDIF Coaxial Out on the front of the LiveDrive!.  I've also tried this via the TosLink out.  Both options I'm able to get stereo sound from the front left and right only.  

I'm stumped....

My questions are two:

1)  Is it that the drivers don't support the digital outputs?  I've noticed that a lot of people are referring to a set of speakers from say...Logitech...for example.  My guess is that these speakers plug directly into the sound card (back panel) and utlize multiple stereo headphone jacks.  Maybe the SPDIF/TosLink doesn't have the necessary information to drive 5.1 surround through it?

2)  What else can I try?  I'm stumped!  I've read every how-to, and manual I can find and nothing seems to work.

Thanks for your help!

:guitar:

---

### Post by shadowen2 on 2007-08-06
Another interesting side note...I've been doing some more testing...

I do have 5.1 surround for a movie off a DVD if I choose "AC3 Passthrough" with Totem.  If I choose 5.1 surround sound I still only get front left and front right but the sound that should come from the center and rear channels is missing (no voices or background noise).

---

### Post by MrHippocampus on 2007-08-06
I have an audigy 2 and the behavior you describe is the same. No creative card that I know of has a 5.1 AC3/DTS encoder on board so it cant generate a digital 5.1 stream on the fly, it can only send a 2 channel PCM digital signal on its own (or a 5.1 stream from a DVD or another source with a pre-made digital stream). The same thing happens on windows.

On the point of the rear/center speakers not working with a proper 5.1 stream, check that the relevant channels are on and up to full (run "alsamixer" in a terminal to do this) and also try another media player e.g. xine or mplayer.

---

### Post by shadowen2 on 2007-08-06
Wow!  Thanks...I can't believe I didn't think about it like that!  It makes sense to me now why it doesn't work!  

My next question then is does anyone know of an audio card that's compatible with Linux and whose drivers have been written to support, and that actually has AC3/DTS encoding?  I will go look myself but if anyone out there has one or has experience with one their feedback would be great!

---

### Post by shadowen2 on 2007-08-23
As a side note since I just marked this thread as solved, I thought I'd add a bit of documentation in case this will help someone else out there.  

I found a chip that will encode DTS, AC3 and Dolby Pro Logic II.  It's made by C-Media and their main website is [http://www.cmedia.com.tw/](http://www.cmedia.com.tw/)  This link is only for the chip, you will need to search for cards and/or motherboards that will have this chip.  I've also not seen any information on how well this works for Linux.  I saw one made by a company called Auzentech.  Good luck guys!

---

