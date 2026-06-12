---
title: "Diagnosing stuttering video"
date: 2011-11-21
forum: Multimedia Software
---

### Post by Jethro_uk on 2011-11-21
Running a 10.04 box, with 2x1TB USB2 drives in a RAID (duplicated) array.

Have a powerline (network over mains) network between ubuntu box and mediaplayer.

Plays SD video fine, and HDTV shows fine, but went to play a bluray-rip yesterday, and got a little bit of stuttering.

Media player reports network speed at between 7-10Mbs.

Can anyone suggest a way to diagnose whether I am experiencing slow network, or slow disk speeds ?

e2a: Running palimpsest benchmarks gives me an average speed of 39Mb/s and a minimum of 32Mb/s

---

### Post by BHEJU on 2011-11-21
It could also be related to the mediaplayer and/or the codecs it uses. 
If your mediaplayer has USB port.. try running a B-ray from USB. that would eliminate network from equation and you will know if it's network or mediaplayer.
Hope this helps.
I run my mediaplayer via Wi-Fi and I don't have problem running Hi-Def media files.

Cheers,

---

### Post by SeijiSensei on 2011-11-21
What video card do you have?  (If you don't know, run the command lspci.)  1080p content is very demanding.  If you don't have a relatively modern machine, the CPU may not be able to keep up with the content.  Some video cards like recent NVIDIA models have the ability to off-load the video decoding to specialized firmware in the graphics adapter.  If you have an NVIDIA adapter, I recommend installing smplayer and choosing the VDPAU driver from Options > Preferences > General > Video.

---

### Post by Jethro_uk on 2011-11-21
> **SeijiSensei said:**
> What video card do you have?  (If you don't know, run the command lspci.)  1080p content is very demanding.  If you don't have a relatively modern machine, the CPU may not be able to keep up with the content.  Some video cards like recent NVIDIA models have the ability to off-load the video decoding to specialized firmware in the graphics adapter.  If you have an NVIDIA adapter, I recommend installing smplayer and choosing the VDPAU driver from Options > Preferences > General > Video.

I am not playing the video on the Ubuntu machine, but through a dedicated media player.

---

### Post by Jethro_uk on 2011-11-21
> **BHEJU said:**
> It could also be related to the mediaplayer and/or the codecs it uses. 
If your mediaplayer has USB port.. try running a B-ray from USB. that would eliminate network from equation and you will know if it's network or mediaplayer.
Hope this helps.
I run my mediaplayer via Wi-Fi and I don't have problem running Hi-Def media files.

Cheers,

Mediaplayer does have a USB port, but I don't have a blu-ray player. I can't see that it would get 30 minutes into a file and then play up, if it were a codec issue ... on the basis that it looks like the network is the slowest part of the chain, I need to do some more digging there ...

---

### Post by BHEJU on 2011-11-21
I meant to say that save the file in a usb drive and put it in mediaplayer.
If the file runs for 30 mins, that does not eliminate codec issue. Actually, from my exp, its more likely that you have codecs / source file (B-ray) issue with. Again its my exp, and you might be correct in thinking that its a network issue. But I wouldn't count out the codecs / source file either.

Hope you get this working soon

Cheers,

---

### Post by Jethro_uk on 2011-11-21
> **BHEJU said:**
> I meant to say that save the file in a usb drive and put it in mediaplayer.
If the file runs for 30 mins, that does not eliminate codec issue. Actually, from my exp, its more likely that you have codecs / source file (B-ray) issue with. Again its my exp, and you might be correct in thinking that its a network issue. But I wouldn't count out the codecs / source file either.

Hope you get this working soon

Cheers,

Ah ! I see. Hmmm I need a >8Gb stick ... I shall have to go shopping.

---

### Post by Jethro_uk on 2011-12-21
Right, having purchased a 16Gb USB stick, I can definitely point at the network. Same file stutters on n/w playback, but is crystal clear all the way through played from a USB stick.

Unfortunately. because the server is in a remote location, it's impractical to plug the USB stick in every time to copy a file. Which means it needs to be done over the network. Which is where things get interesting ... despite the servers n/w card being set to 100MB/s, and my Windows machine the same, I am only achieving 1Mbyte/s point to point. So a 6GB file can take nearly 2 hours to copy.

Diagnostic tool with the powerline adapter says they are running at 80%, which is >100Mb/s ... so where's the delay ?

---

### Post by BHEJU on 2011-12-23
Well, If you want to eliminate the disk from the equation..
You might want to make one more trip to the server and put the usb drive in it and read the movie from the usb drive over network .. and if that works fine.. you have isolated the issue to your HD.

Cheers,

---

