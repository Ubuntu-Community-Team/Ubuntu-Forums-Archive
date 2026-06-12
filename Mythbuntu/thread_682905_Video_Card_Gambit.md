---
title: "Video Card Gambit"
date: 2008-01-30
forum: Mythbuntu
---

### Post by RFinn on 2008-01-30
I've been playing around unsuccessfully with getting the S-Video tv-out on my Radeon 9600 Pro (128 mb) to work. At this point, it displays on the TV but is garbled and kind of grey. It could have something to do with Xorg Config (from within the Ubuntu Config manager, not the terminal) thinking it's a digital display (in fact it's a 27" JVC CRT TV). I might try and play a bit more, but if anyone has any ideas i'm all for it. I have an extra NVidia GEForce NV15 card with 4 pin S-Video laying around that I might give a shot, but I'd prefer not to downgrade to an inferior card. The DVI on the video card works fine and the other option I'm considering is picking up a DVI to S-video converter and giving it a shot. 

Anyways, input is always appreciated.

---

### Post by stdPikachu on 2008-01-30
Do you know which ATI video driver you're using? It should say in the ubuntu video manager screen. TV-out with ATI cards has always been a bit dodgy, unfortunately.

As an aside, I always got better results out of a VGA > SCART convertor (also came with s-video and composite output) than I ever did with using the TV-out on my old nVidia 5200.

---

### Post by RFinn on 2008-01-30
It's the FGLRX driver, the Catalyst control center sees the second display but only gives me options for screen resolution and refresh rate. Curiously, whenever i try to change something on display 2 (which should eb the TV) in either Xorg Config or Catalyst it also changes the output on my default monitor (a 19" samsung LCD).

---

### Post by RFinn on 2008-01-31
Resolved... After trying every setting known to man and nearly going out of my mind I came across a small post out there in Cyberland mentioning a jumper on the bottom of this particular card that switched the output from Pal to NTSC... So now it works great, although I have to wonder at the logic behind setting a video card that probably does the bulk of its sales in North America to Pal OTB.

Now I get to have some fun with LIRC

---

### Post by stdPikachu on 2008-01-31
I'm still staggered that there's been a graphics card within the last five years that still needs a jumper to switch between PAL and NTSC, but glad you got it working at any rate.

---

