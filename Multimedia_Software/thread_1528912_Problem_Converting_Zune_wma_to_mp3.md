---
title: "Problem Converting Zune wma to mp3"
date: 2010-07-11
forum: Multimedia Software
---

### Post by maxzorin73 on 2010-07-11
I am new to Ubuntu after switching from Windows Vista. So far I really like it. I am trying to convert music in wma format that I purchased on Zune to mp3 format so that I can play it in Rhythm Box and use it on a SanDisk Fuze that I recently purchased. I installed Sound Convert. Sound Convert works fine when converting wma files that were created from ripping CD's. However, it freezes when trying to convert wma files that were purchased from Zune. Also if I try to double click on one of the wma files to play it with movie player, I get an error message saying that the file is encrypted and decryption is not supported.

I did find a converter on Windows that works. However, it was a trial version that only converts 90 secs. The full version costs $25. I do not feel that I should have to pay for music that I have already paid for. The music was purchased a la carte from Zune (not with the monthly pass).

Does anyone know of a workaround to free my Zune music so I can access it on Ubuntu?

Thanks in advance for any input.

---

### Post by Naitsirhc Hsem on 2010-07-11
I would try Audacity with the Lame mp3 plugin, both available in the software center

---

### Post by gandaran on 2010-07-11
> **maxzorin73 said:**
> I am new to Ubuntu after switching from Windows Vista. So far I really like it. I am trying to convert music in wma format that I purchased on Zune to mp3 format so that I can play it in Rhythm Box and use it on a SanDisk Fuze that I recently purchased. I installed Sound Convert. Sound Convert works fine when converting wma files that were created from ripping CD's. However, it freezes when trying to convert wma files that were purchased from Zune. Also if I try to double click on one of the wma files to play it with movie player, I get an error message saying that the file is encrypted and decryption is not supported.

I did find a converter on Windows that works. However, it was a trial version that only converts 90 secs. The full version costs $25. I do not feel that I should have to pay for music that I have already paid for. The music was purchased a la carte from Zune (not with the monthly pass).

Does anyone know of a workaround to free my Zune music so I can access it on Ubuntu?

Thanks in advance for any input.
if they are DRM protected wma audio files then probably the only way you can convert them is to first burn them to a cd then rip the cd with sound juicer or any other ripper.

---

### Post by mc4man on 2010-07-11
If they are not protected, (don't know zune at all), they possibly could be wmap (wma3pro, WMA version 9

Can you play them in rhythmbox or totem?

(try r. clicking on one -> properties -> audio, WMA version 9 usually means wmap, WMA version 8 usually means wma2

If they're wmap then support can be added to gstreamer in karmic and lucid by adding this ppa and updating your gstreamer plugins, in this case gstreamer0.10-ffmpeg (though all that can be updated should be..

[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

Otherwise you could install w32codecs (on a 32 bit install only), and try soundkonverter instead or use mplayer to convert to .wav, then do as you please

Your best bet is to figure out what they are first

---

### Post by maxzorin73 on 2010-07-14
Thank you to everyone for your ideas and suggestions. The files were regular wma files but must have been locked somehow by Zune. I burned them onto CD's and ripped them using Sound Juicer. This method worked. The problem seemed to be limited to my older Zune music files. My more recent Zune music files were actually mp3's. Thanks again! :)

---

