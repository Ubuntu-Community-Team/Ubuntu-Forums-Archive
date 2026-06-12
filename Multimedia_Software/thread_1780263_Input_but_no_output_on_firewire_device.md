---
title: "Input but no output on firewire device"
date: 2011-06-11
forum: Multimedia Software
---

### Post by cameronsteele on 2011-06-11
Hello,

I'm using FFADO on JACK in order to use my firewire device (M-Audio Profire 610) and I seem to have the opposite issue as others who have similar problems. Everything starts up fine, and I can record audio into Ardour using my inputs, but I can't get any output from any of my 8 line outs.

I've checked the connections using QjackCtl, and I tried to route audio from another program (Audacious) but I can't seem to pull audio out of the device (or the computer won't send my device audio?).

I'm sort of new to linux, I'm wondering if anyone has any ideas as to what I could try? It would be greatly appreciated.

---

### Post by shortent on 2011-09-13
I'm having a similar issue with a Presonus Firestudio Project. JACK can see my device perfectly, all 8 inputs and 10 outputs are visible in the patchbay, but I cannot get any audio to the speakers even though qjackctl shows that audio is being routed to the appropriate outputs (I have tried them all). However, I can patch audio in from the mic preamps and record to ardour with no drama and I can play audio through JACK into my SB-XFI audio card. 

Any hints? FFADO.org says this product is unsupported but I am confused as to why my Inputs work fine  when my outputs do not.

---

### Post by clakes on 2012-01-09
Came across this thread while googling for this very issue I'm also experiencing with my MOTU UltraLite card.
It's really driving me MAD: excellent input and FFADO/Jack response, but not a hiss routed to my output, although everything seems to be in place.
:wall-headbang:

---

### Post by ivey on 2012-01-23
Hi,

Im having same problem... 
I havent try recording but I can monitor input...
but no output...
I havent been able to find answers...

System
Ubuntu Oneiric Ocelot (3.0.0-15-generic)
MOTU_Ultralite 

cheers

I

---

