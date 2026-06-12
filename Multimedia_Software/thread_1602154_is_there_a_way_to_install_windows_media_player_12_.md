---
title: "is there a way to install windows media player 12 through wine ?"
date: 2010-10-21
forum: Multimedia Software
---

### Post by Wanas on 2010-10-21
I am really fedup from playing .mpg (1080i) videos on linux. I tried to use smplayer or vlc but the video plays so poor, I got like scales (lines) on the video like on the screenshot embedded below (the screenshot I found on the net). 

When I play the same video on windows 7 its so great with windows media player 12, when I play it with smplayer or vlc on windows 7 I got the same performance like in linux, its like windows media player has its own mpg hardware accelerator !!

---

### Post by Lazaruss on 2010-10-21
It's not on [WineHQ]("http://www.winehq.org"), so i guess not

---

### Post by cascade9 on 2010-10-21
If you've got an nVidia card (8XXX or higher) you could try VDPAU (nVidia hardware video decoding). If you've got an ATI card, XvBA (ATI hardware video decoding) might work as well, but its a lot more buggy than VDPAU.

---

### Post by Wanas on 2010-10-21
> **cascade9 said:**
> If you've got an nVidia card (8XXX or higher) you could try VDPAU (nVidia hardware video decoding). If you've got an ATI card, XvBA (ATI hardware video decoding) might work as well, but its a lot more buggy than VDPAU.

yeah I have a nVdia 330m in my laptop and I have enabled VDPAU in smplayer but its the same with the .mpg @ .ts (1080i) Videos only

---

### Post by soldier1st on 2010-10-21
no u cannot install it through wine but you could skin VLC to look like Windows Media Player. also is there any reason you want Windows Media Player? does it offer something that a linux equivilent doesen't?

---

### Post by cgroza on 2010-10-21
^^Some video of him does not work ok, and he thinks installing WMP in wine will work.

---

### Post by Wanas on 2010-10-21
> **soldier1st said:**
> no u cannot install it through wine but you could skin VLC to look like Windows Media Player. also is there any reason you want Windows Media Player? does it offer something that a linux equivilent doesen't?

yeah as I mentioned above .mpg or .ts in the resolution of 1920×1080 (1080i) works so poor on vlc and smplayer compared to playing it with windows media player

---

