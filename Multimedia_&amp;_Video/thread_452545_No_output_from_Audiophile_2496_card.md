---
title: "No output from Audiophile 2496 card"
date: 2007-05-23
forum: Multimedia &amp; Video
---

### Post by Sabru on 2007-05-23
Okay, after re-enabling the integratd audio in the BIOS, the sound card is definitely detected. 

However, There is still no output whatsoever from the card. When I disable integrated audio, things get worse. I login, and then the screen goes blank, with no desktop. I enable integrated audio AGAIN, and tried specifying the sound card as the output in the sound menu, but then all audio applications crash. I checked the alsamixer to see if anything was muted. Turned everything up, still nothing.

If anyone else has a working audiophile 24/96 card in their box, I'd love to hear how you got it working. Or if anyone might have a suggestion, I'd appreciate it. Thanks in advance!

---

### Post by Sabru on 2007-05-23
Okay, no response yet, so I will try to be more specific:

I have re-installed ubuntu studio with onboard audio disabled to see if that will fix the problem. Now, not only am I not getting any audio, but I'm not getting any desktop either. When I login, nothing. just the mouse cursor and a black screen. So now, I try re-enabling onboard audio, but It's only getting worse, I get the same blank screen, with no audio from either the sound card, or the integrated port. I can't see anything to configure anything. This didn't happen before I installed the card.

This is getting very frustrating... Ubuntu Studio... M-Audio Audophile 2496... Biostar 1945-G M7 motherboard... please someone help!

---

### Post by Sabru on 2007-05-24
Alright, I had no other choice but to install ubuntu studio for the third time. Now, the OS itself works fine, but I'm not getting ANY audio from either the sound card or the onboard audio. Nothing. I've even followed the "comprehensive sound problem solutions guide." Still nothing. Everything suggests that the driver is installed; I can edit the sound card settings in envy24control; although this is pretty much futile, since I can't hear anything to adjust. 

It seems that everything is working, except for the part where I'm actually supposed to hear stuff. And yes,  I checked the connection to my speakers.

Help please!

---

### Post by Sabru on 2007-05-24
The M-audio site recommends the Open Sound system, so I enabled that in the sound menu. Still doesn't work.

Audio programs still crashing. Still no sound from either output.

User angry!

---

### Post by snoop on 2007-05-24
Very strange that the desktop is not working. The sound should not be able to do anything to the desktop. Have your tried feisty rather than ubuntustudio? 

Sorry, the only things i can think of is to try and tweak alsa mixer and also try the aoss package. I hear it allows audacity to finally work.

---

### Post by Sabru on 2007-05-24
Thank you for the input. I actually did try regular feisty, but oddly enough, the same thing happened.  It's definitely related to the audio settings in the BIOS too. 

Here's a strange thing: I just plopped in an old Turtle Beach sound card to see if that would work. Sure enough, it worked immediately. I didn't even login before it made the familiar "ping" noise.

I'm beginning to think that either M-Audio is garbage when it comes to linux,  or this Audiophile 2496 sound card was DOA. Either way, I've decided to send it back. Maybe I can sue them for the 10+ hours of my life that I spent trying to get this 100$ paperweight working.

---

### Post by Dinkers on 2007-09-17
I have the same problem. The audiophile card worked perfectly out of the box with edgy eft. But now in feisty there is no sound at all. 

I don't seam to find my imother board ntegrated sound card in my bios, so I don't know how that would change things.

---

