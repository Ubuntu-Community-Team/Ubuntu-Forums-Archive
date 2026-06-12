---
title: "Playing DVD issues..."
date: 2008-08-09
forum: Multimedia Software
---

### Post by Auxilio on 2008-08-09
i've got a few issues with attempting to play DVDs on my MSI laptop. At first I tried the built-in player, but that didn't work. So I tried a differnt one, thinking that it didn't have the proper decoding software. I've tried the VLC media player, I've tried gxine, and I've tried MPlayer Movie Player. None of these have worked. Every time I stick a DVD in the drive, the built-in movie player keeps on opening and saying that the resource cannot be read. Then, when I try VLC Player, it will show the FBI warning, and then stop. When I try the other players, my laptop freezes for a few seconds, then I am able to exit the program. My laptop's model number is VR601X-412CA. I've looked in the software package manager, and I can't find any generic DVD drivers. My friend said I would need DVD decoders, but I can't find any of those either. Could anyone help me? Thanks.

---

### Post by wolfen69 on 2008-08-09
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
then
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
then
```
sudo apt-get install libdvdcss2
```
enjoy your movies

---

### Post by Auxilio on 2008-08-09
Thank you very much, that allowed the movie player to work, but now i get a whole bunch of graphic errors while the movie is playing. The video has green squares and graphic errors all over the place, with a window that continously appearing that only says, "Error!" on the taskbar at the bottom. It doesn't appear long enough for me to see what it says, I can only tell that there's a window there, because it appears on the taskbar. Then, when i exited the media player, it says, "Too many video packets in buffer [9096 in 8259791 bytes]". What does this mean and how do I fix it? Thanks for being patient with me. Also, if I might ask, what did that last fix/code do for me?

---

### Post by LoneDoppelGanger on 2008-08-14
Many humble thanks to you Wolfen69. Enjoying I am.

---

### Post by Auxilio on 2008-08-14
It actually started playing fine now, so I don't actually need any additional help. It must've been in an update I installed. Thanks for your help again.

---

