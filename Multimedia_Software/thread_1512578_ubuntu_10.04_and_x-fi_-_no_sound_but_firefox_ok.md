---
title: "ubuntu 10.04 and x-fi - no sound but firefox ok"
date: 2010-06-18
forum: Multimedia Software
---

### Post by Magick93 on 2010-06-18
Hi

I have an X-Fi soundcard.

I cannot get any audio from playing mp3s in apps like VLC and Movie Player. But flash works fine. Firefox sounds are fine.

What can I do to fix this? Thanks

---

### Post by mr_hide3 on 2010-06-18
well since you are getting sound then the sound card is recognized 
i'm sure you went through this [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) ?
anyway , i'm guessing maybe it's something to do with the codecs? when you try to play an mp3 file , does the app give you a message box saying "search for suitable plugin" ?

and , was it working before ,then it stopped working , or just never worked?

another thing to try out is , check the sound preferences , check the hardware tap if the correct hardware is used
and under "applications" tap check if the muted applications are actually muted there when they play
firefox has it's own plugin in alsa [firefox bin] so clearly this one is working and not muted 

anyway , i'm not an expert , just trying to help ,maybe if you provide more information more help would be possible

---

### Post by lidex on 2010-06-18
Do 'Part 1' here:
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")
Also this:
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by Magick93 on 2010-06-19
Hi

Thanks for the reply

VLC works fine. But Movie Player and Miro are unable to output any sound. Movie Player can play, for example, a .flv file, but there is no sound. 

I can play the same file in VLC and it is fine.


Both Movie Player and Mire used to be fine - before I upgraded to 10,04.

I dont get any notices about missing codecs.

---

### Post by Magick93 on 2010-06-19
I found this answer on this thread:
[http://ubuntuforums.org/showthread.php?p=9448764](http://ubuntuforums.org/showthread.php?p=9448764)

---

### Post by mr_hide3 on 2010-06-21
well did it work?

---

