---
title: "Cinelerra - can't stop timeline running"
date: 2008-11-28
forum: Multimedia Software
---

### Post by potatoehead64 on 2008-11-28
Hi
I'm new to Cinelerra. It looks pretty good although somewhat complicated (I'd been used to using MS moviemaker!).
I've checked out a few tutorials on this and I'm getting there. 
The trouble I'm having is when I preview a clip in the viewer, the timeline continues to run forever. I;m unable to stop it or close down the program normally. The only way of getting out of this is to kill the program in terminal. 

Does anyone know why this happens?
Is there a setting I missed or does it sound like a bug in the installation?

(running 8.04 studio)

Cheers

Martin

---

### Post by solder4Christ on 2009-05-19
I'm having the same problem.
I'm running a new 8.04.2 install (I reinstalled yesterday). 

I've been using Ubuntu for about 6 months now, and I've been wanting to get Cinelerra working properly (to get out of the horrible lack of stability in WMM, and to get more professional looking results than WMM). 

The only problem is that there has been some problems getting the software working . At first, I was having a problem where the video and the audio wouldn't play in sync (the audio would play at normal speed, while the video would lag behind VERY VERY noticeably). I remedied that problem by un-selecting "Play Every Frame". Now I'm having the problem listed above.

If anybody could help us, that would be great :D

Thanks!

---

### Post by solder4Christ on 2009-05-21
Hey

Ok, I did a little research, and I found [_this page_]("https://init.linpro.no/pipermail/skolelinux.no/cinelerra/2009-April/015650.html").

Found on the given page:
> Try:
Preferances > Playback > Audio Driver = ALSA check tab Stop playback locks
up

After doing what was suggested, the time line problem has ceased to be an issue for me. 

I'm now having a bit of trouble with the audio codecs that my camera uses, but it appears that other than that, Cinelerra is functioning as it is supposed to.

---

