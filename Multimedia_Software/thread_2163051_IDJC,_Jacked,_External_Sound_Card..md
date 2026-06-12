---
title: "IDJC, Jacked, External Sound Card."
date: 2013-07-16
forum: Multimedia Software
---

### Post by DCRR on 2013-07-16
Hi,
I have a question setting up IDJC with and external sound card.

I'm running:
 Ubuntu 12.04.2
IDJC 0.8.9
Jacked (Installed with IDJC)
and using an EDIROL UA-EX1 USB external sound card.

I have followed the directions on [http://idjc.sourceforge.net/index.html](http://idjc.sourceforge.net/index.html) and IDJC is broadcasting my playlist great.

I have gone in the ALSA mixer control in terminal and turned the Edirol sound card on.

My issue is I also use CDJS/Turntables/Ableton/Reason/EFX box etc. When I do my radio show live, I need to be able to connect my external mixer via sound card.

In the UBUNTU sound settings my Edirol UA-1EX sound card is recognized and I am getting a signal. Tried recording with Audacity and works great.

In Jack Audio Connection Kit>Setup>Interface the Edirol sound card is recognized as hw:1. I set the settings to ALSA/capture only. Which is what I assume the Jacked server would need be set too. Thought I would just press play on the Jacked server and IDJC would sum the playlist and Edirol Sound card signals together. Then would just turn off the playlist and would here my e.g CDJs signal. No avail.

I looked in Jacked>connect and would assume I would need to connect Jacked to IDJC similar to an analog signal via cables to mixer, sound source, etc. When I go in Jacked>Connection>ALSA there is only a 14:MIDI through connection. Which if it were just a signal thru, I would assume would be able to connect to an IDJC input audio and be unaffected signal then just turn off the playlist, However this is not the case.

In IDJC I have looked in the Jacked Ports, and do not see anything resembling and input from my sound card.

I thought maybe the AUX in on IDJC would bring in an Auxilary Sound card. But that does not work either.

Bit stumped on how to get the EDIROL sound card signal into IDJC for Live broadcast. I've looked at the forum, but do not see anything resembling this issue.

Any help would be appreciated.

Thanks in advance!

---

