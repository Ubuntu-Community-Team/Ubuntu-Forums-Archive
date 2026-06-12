---
title: "Multitrack recording problem"
date: 2006-08-26
forum: Multimedia &amp; Video
---

### Post by alamet on 2006-08-26
Hi, I am trying to record a multitrack song with Dapper.
I need to be able to listen to the previously recorded tracks while I record a new one (really common task!) for example I generate a click track and, listening to it by phones I play and record the guitar.
I tried with Rosegarden 4 and Audacity but in both the new recorded track is somehow influenced by the other tracks I listened in the phones - it records into itself the new recorded stuff with a distorted and shifted version of the other tracks.
Which is my problem? I have an integrated AC '97 soundcard (very bad) is this the matter?
Thanks

---

### Post by zettberlin on 2006-08-26
> **alamet said:**
> 
I tried with Rosegarden 4 and Audacity 

I suggest you give it a try with ardour, it is generally the application best suited to your task. At the other hand it could indeed be a flaw of your soundchip or better: its DA-converter. I do not actually know, if such effects can occur with cheap hardware but i would not be suprised...

So i would suggest as follows:

1) try ardour
2.) get a better soundcard (around 100 EUR/USD M-Audio Delta 44 is very good...)

---

### Post by dolson on 2006-08-26
This happens with my Audigy2ZS card as well...

What I have to do is after launching Audacity, I have to go into alsamixer (terminal version), and change the PCM Capture level to 0.

I don't know if that will help you.

---

### Post by repins on 2006-08-26
How do you configure QTDIR?

---

### Post by zettberlin on 2006-08-27
> **repins said:**
> How do you configure QTDIR?

:~$ export QTDIR=/usr/share/qt3

for muse and others you need pkgconfig properly set up too:

:~$ export PKG_CONFIG=/usr/bin/pkg-config


Works for me quite well, if you want to have these set permanently you need to place those lines into ~/.bashrc or better in /etc/bashrc

---

### Post by alamet on 2006-08-28
I tried to change the PCM Capture level to 0, but it didn't work... 
I will try with Ardour tomorrow

---

### Post by alamet on 2006-09-04
Ok! With Ardour it works perfectly! :biggrin:  I'll use it for my recordings.
However, it's really strange either Audacity and Rosegardern can't do it...
Their interface is more user-friendly I chose them for this.
Thanks

---

### Post by Prelude Jive on 2006-09-17
I'm having this problem with Audacity right now. I was going to get Ardour as well and I was wondering, do you have to be connected to the internet to use JACK (run Ardour)?

---

### Post by dolson on 2006-09-17
No, you don't need to be on the net to use JACK. Not sure why you would think that. :)

---

