---
title: "Trying for 5.1, but I have problems and questions"
date: 2006-08-30
forum: Multimedia &amp; Video
---

### Post by zeno86 on 2006-08-30
Hi,

I am trying to run 5.1 surround sound on my system ( Ubuntu 6.06 64 bit edition). I have onboard audio (Nvidia Corp. MCP51 AC97 Audio Rev. 2).
So far I did speaker-test -c5 -Dplug:surround51 and got sound to play out of each speaker correctly, but when I play mp3s it is not surround. I have a couple of questions I would like to have answered if possible:



1)My onboard sound required me to plug my speakers into the  line-in (I think thats what it's called) and microphone as well as the sound port. (They are color coded blue-pink-green). When in XP I had to use a program (think it was called soundman.exe) to set the mic and line in port to be recognized as line outs to the speakers (I think the particular section to do this was called phonejack switch). Is there such a program in linux/ubuntu to do this? or can it perhaps be done in alsamixer?



2)Although the speaker test played the sound right out of each speaker right is it truly in surround sound mode? Is there a download that I can try to test it that someone with working surround has tried and verified can play 5.1? (I don't have dvd player to try dvd T.T)



3)In Amarok, when you go to the sound engine option, when xine is chosen it says under ALSA device configuration, the 6 channel row reads plug:surround51:0. That looks ver similar to the speaker-test text (Dplug:surround51 -c5). Is the c5 part of the speaker-test text suppose to be incorporated into part after the surround51's colon)? If so how?



Here is some more info about my system:
Biostar Tforce 6100-939 mobo
AMD64 3200+
1 gig corsair ram 
onboard video: Geforce 6100
onboard audio: Nvidia Corp MCP51 AC97 Rev. 2 (Realtek ALC655)
Alsa version (one included in the Ubuntu 6.06 release)

---

### Post by zeno86 on 2006-08-30
Well I got 5.1 sound to work during mp3s but I've encountered a new problem. When trying to play video in vlc it was stuttering like crazy. So I went in and set the alsa setting in vlc from default to my sound card which set it back to 2 speaker sound (although it does still have 5.1 in amarok). Does anyone know why it stutters?

Oh yeah I used this: [http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml](http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml) to fix the 5.1 sound problem.

---

### Post by Hatch151990 on 2006-08-30
The reason your music isnt playing in surrond is because mp3's dont support more than 2 channels (stereo). If you want your music to play out of the rear speakers as well i think there is an option in alsa mixer to play the left and right channels through the rear channels.

---

