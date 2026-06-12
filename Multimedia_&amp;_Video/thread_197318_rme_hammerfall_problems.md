---
title: "rme hammerfall problems"
date: 2006-06-15
forum: Multimedia &amp; Video
---

### Post by jaskah on 2006-06-15
hello
i`m running ubuntu dapper and want to use my rme hammerfall interface and pci card.
i have everything isntalled: alsa-tools and alsa-firmware.
when i load the drivers  the card works but no sound levels are shown in the hdspmixer. i can, for example, use audacity with the hammerfall as my default soundcard.
also: when unplugging the card and re-starting the computer the card isn´t recognized and i have to load the drivers again with hdsploader.
how can i correct these problems?
any help greatly appreciated.
jason

---

### Post by damu on 2006-06-15
I don't have the answer to your specific problem.
But if you want to do music/sound production on linux (like you I have a Hammerfall and I guess you didn't buy RME's product just to edit few things with Audacity! ;) ), I would suggest to try: [Studio to go]("http://www.studio-to-go.com") . You can donwload a demo for free, and buy a licence if u like it.(very cheap compare to its windows equivalent). It comes with VST support(not every VST works, but a decent amount of them do) and all the main linux softwares for audio : ardour , rosegarden, all the alsa plug ins, etc. 
 or you can try [musix]("http://musix.org.ar/en/index.html"), a free audio distribution put together by a spanish team which rocks!

---

### Post by jaskah on 2006-06-15
hi
thanks for your suggestions...i'd rather stick with ubuntu for now.
i only need a sound editor (audacity) a mix program (ardour) and pure data / super collider.
therefore, if i can get the hammerfall and these other applications running i will be satisfied.
i don't want to buy into another distribution (studio to go) as i already have mac's with logic, peak, etc. but i want to switch over to linux, because in the long run this will definitely be the way to go.

---

### Post by RFScheer on 2006-06-20
I have dapper working with RME pci card + Multiface II.  The hdspmixer was showing levels and peaks but quit doing that the other day.  Haven't a clue why that changed.  Since I never unplug the MFII, I haven't seen the problem of not recognizing the card on plug in.  

My use is strictly for playback using JACK and BruteFIR.  This is working well for music and many video formats but not yet for Mplayer dvd playback.

---

### Post by damu on 2006-06-25
The main issue with audio production in linux is that you need a low latency kernel. You might not need it for some easy editing work in Audacity, but it will definitely be the case if you want to have some serious work done with Ardour.

That's why I suggested Musix (live cd) which comes with all softwares and a low latency kernel, ready to use. 

Ubuntu is simply not ready for that. It might be in the future For now, the only way to get it running is to tweak the kernel yourself. [Ubuntustudio]("http://ubuntustudio.com") is the right place to get the informations on how to do that these quite tecky tasks!

Good luck! ;)

---

### Post by wavesound on 2008-01-28
Hi 
Have you tried 64studio?
This works well with RME + Ardour and has an RT Kernel.

I can't get my RME to work in gutsy at all. I have to use the realtek now.
It's a real shame

Bob

---

### Post by jaskah on 2008-02-02
hi
can you post some information about what machine you are using? maybe there is a hardware problem somewhere.

---

### Post by wavesound on 2008-02-02
Hi
I can play music on my other system ( 64studio)
so I cant see it being hardware.

I could  also use the RME on 6L6 Ubuntu.

Seems something is changing on the newer Ubuntu re sound.

Cheers
Bob

---

