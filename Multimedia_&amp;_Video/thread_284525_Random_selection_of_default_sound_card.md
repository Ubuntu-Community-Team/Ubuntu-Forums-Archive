---
title: "Random selection of default sound card"
date: 2006-10-25
forum: Multimedia &amp; Video
---

### Post by richardw1983 on 2006-10-25
I have a VIA on board sound chip and a SAA7134 TV tuner card. 50% of the time the VIA is detected as card0 on bootup and eveything works fine. The other 50% of the time the VIA is detected as card1 on bootup and I have problems with missing system sounds, also sound on some web sites is missing but sound on other web sites is still OK. Both the VIA and SAA appear in KMix.

I have looked through these forums and found the following solution has been been put forward:

At the end of the /etc/modprobe.d/alsa-base file add these two lines

options snd-via82xx index=0
options saa7134 index=1


I have tried this and it does result in the VIA always being detected as card0 and the sound working OK. However in my case at least, I can no longer use my TV tuner card. The SAA is no longer present in KMix and the kdetv program does not detect any devices.

I have also tried the following variations:

Adding ONLY the "options saa7134" line results in the same situation as described above (i.e. only VIA listed in KMix)


Adding ONLY the "options snd-via82xx" line results in only SAA being listed in KMIx. There is no sound at all. The kdetv program works as far as video is concerned but there is no sound

So I am still looking for a way of getting the VIA chip to always be detected as card0 on bootup but also being able to use the TV tuner card at the same time.

Thanks in advance

---

