---
title: "AC97 codec problems."
date: 2007-06-12
forum: Multimedia &amp; Video
---

### Post by Fredinthebox on 2007-06-12
Hi all,

Im new to linux and the forums in general, but am learning quickly as I fix the problems I run into.

My newest endeavor is getting my integrated soundcard working. I run a MSI K9NU Neo motherboard which uses a Realtek integrated soundcard which runs the infamous (to me, as I scan the forums for a solution) AC97 drivers.

The soundcard seems undected since my alsamixer give me this error:
> alsamixer: function snd_ctl_open failed for default: No such device

I installed the AC97 drivers found [[COLOR="RoyalBlue"]here[/COLOR]]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false") but after theyre done installing I still have no sound and when I reboot i get a 
> Your session only lasted less than 10 seconds. Error while loading shared libraries: libasound.so.2 cannot open....etc etc
on reboot which i can only solve by reinstalling libasound and alsa by using the command:
> sudo apt-get install --reinstall libasound2 alsa 

So Im stuck, and I havent found anything on these forums that works yet, although if an answer does exist I apologize and would be forever grateful to be pointed in the right direction.

Thanks!
-T

---

