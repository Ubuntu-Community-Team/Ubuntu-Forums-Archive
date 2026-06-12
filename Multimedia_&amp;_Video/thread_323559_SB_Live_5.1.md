---
title: "SB Live 5.1"
date: 2006-12-22
forum: Multimedia &amp; Video
---

### Post by fracktor on 2006-12-22
I am running Ubuntu Edgy and having some trouble with my Creative SB Live 5.1 card. It is playing the system sounds, (logon sound, logout, when clicking test I hear the test tone) but it is not playing any other media (website sounds, mp3's, music cd's, etc..) 
I went into the alsa mixer and made sure nothing was muted and turned up everything to around 80. Any ideas would be greatly apreciated...

---

### Post by budgie9 on 2006-12-22
You don't give us details on what you are running to listen to mp3's etc. Perhaps a good place to start would be the Sticky above. There is also other help in the support sections.

If you have problems after that then do come back and I am sure there will be someone to help you with a specific problem.

---

### Post by fracktor on 2006-12-22
I am using xmms to play the mp3's. It shows as playing, but their is no sound. I am using firefox web browser, and on sites that would have sound, its not playing. I followed the sticky  guide of "comprehensive sound prolem solutions" but still cant't seem to find out what is going on. It plays the system sounds, but nothing else.

 I do have onboard sound card as well, so I don't know if that may be interfareing? Is their a way to disable it? Sorry, I am new to linux as I am coming from windows.

---

### Post by budgie9 on 2006-12-22
There is a very good chance the other On-board card is causing the problem. Many don't seem to realise that two cards can cause a conflict of IRQ's on the computer. It has to be set up carefully to take multiple cards.
In some computers you can disable the internal card in the BIOS. BUT I would strongly suggest you also disable it with the jumper on the m/board see your manual, as this will free the IRQ for your SB live.
Also have you downloaded the mp3 drivers?  These need to be added. I am not sure what they are at this moment as I am using XP yuk, but I think it is mad files. Do a search for these in the downloader I think you will find them.

---

### Post by fracktor on 2006-12-22
Thanks for those tips. I will disable the sound card and look for the mp3 drivers. I wish their was a easy way to disable the onboard sound in device manager like XP.

---

### Post by budgie9 on 2006-12-22
You can but that may not resolve your problem it is better to zactually do in the hardware, thus preventing future problems.

---

