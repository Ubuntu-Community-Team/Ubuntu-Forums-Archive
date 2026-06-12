---
title: "Video Editing in Linux"
date: 2006-02-14
forum: Multimedia &amp; Video
---

### Post by Ben Stamper on 2006-02-14
I've had a pretty decent switch over to Ubuntu, but I still have one question-- what is the best answer for video editing? I'd rather not dual-boot, so I could use a native program or just prot it over with Wine or Cedega. Thank you!

---

### Post by gingermark on 2006-02-14
[Kino](http://www.kinodv.org/) is an open source video editor. It is still in development, but you could give it a go, and see whether it meets your needs. I don't know of any other editors for Linux.

I guess if Kino doesn't cut it (ahem), then you could then look into Wine or Cedega. What editing suite do you own / are you thinking of buying?

---

### Post by ahlich on 2006-02-15
How serious are you?

[http://heroinewarrior.com/cinelerra.php3](http://heroinewarrior.com/cinelerra.php3)

there are debian apt sources, info here:

[http://cvs.cinelerra.org/getting_cinelerra.html](http://cvs.cinelerra.org/getting_cinelerra.html)

---

### Post by mips on 2006-02-16
cinelerra is very powerfull and will probably do more than you need but then again I don't know what you need ;)

---

### Post by bored2k on 2006-02-16
Since I only do simple editing to my -usually- avi files, I use avidemux. For mkv files there's mkvtoolnix, but I don't really do that.

---

### Post by fsman on 2006-02-16
a good way is to use kino for DV capture and general home movie editing. For more complex (similar to adobe premiere) use cinelerra.

Personally, I would'nt use the cvs as that build doesn't import/export in dv quicktime (which you will need if you capture with kino)

I found that using alien to convert the cinelerra rpm into a deb works best (do a search in the forum).

TIP - Install Cinelerra 1.2 version first and run once. Then remove and install version 2.x. I don't know why but it seems to setup the config files to be compatible with kino. (it worked for me after many hours of trial and error)

---

### Post by fsman on 2006-02-16
oh - here are the rpm's of the offical version. PS side effect is you don't have to add lots on debian sources too.:) 

[http://prdownloads.sourceforge.net/heroines/](http://prdownloads.sourceforge.net/heroines/)

---

### Post by Rev. Nathan on 2006-02-17
Hi, the thing I think keeping me back from completely ridding Windows is Adobe Premiere (and Premiere Elements when I feel lazy). I've lurked Google, and indeed found Cinerella was the best. I've been using the .deb, and as fsman said, I have not tried the RPM (I have alien, converted RPMs before, though).

My problem with Cinerella was stability... the counter would still go after I stopped! It almost always did it, and changes would not get applied and so on... is Cinerella stable enough to work with?

---

### Post by relevantrhino on 2006-05-11
Anyone using Cinelerra?  How is the current stability and how does it compare with Adobe Premiere?

---

