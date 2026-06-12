---
title: "S/PDIF Sound card"
date: 2010-09-01
forum: Multimedia Software
---

### Post by Vegar on 2010-09-01
Hello, I've recently been trying to figure out how to use SPDIF with my current on-board sound card with Ubuntu, no luck (it was working flawlessly in Win7).

Now, I've been trying to achieve this several times before but every time i try, i give up because of the lack of support for my specific sound card, or only partial fixes.

_What i need you for_ is picking out a GOOD sound card (preferably USB) that works with Ubuntu without too much hassle (preferably none).
I want confirmation that the card works with Ubuntu 10.4 from some source.

P.S. I know the motivation for helping out a random like me on the Internet is not that strong, but lets say I give $10 (via paypal) to whoever leads me to a purchase

---

### Post by Vegar on 2010-09-03
bump

---

### Post by lykeion on 2010-09-03
I can't recommend you any sound card - for this I'd need to know what you would use it for - but I can try to help you with the issues you have with your current sound card.

Follow these instructions to setup your internal sound card (should include s/pdif support as well)

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

This will involve launching commands in a terminal and editing configuration files. If you need any help with this feel free to post your problems. I would avoid upgrading ALSA though, because this can screw up your sound settings if you don't know what you're doing.

---

### Post by cchhrriiss121212 on 2010-09-03
[This]("http://ubuntuforums.org/showthread.php?t=1559817") seemed to work well for someone. It depends how much you want to spend though and what you mean by good, Cambridge stuff is quality but not cheap.

---

### Post by Vegar on 2010-09-04
Thanks for the replies guys. lykeion, i have some experience so it won't be a problem i hope, I'll give it a try. 

Some information: I'm watching a lot of movies (blu-ray and .mkv files) and i want to be able to play the audio that comes with these files (DTS/DD)
Afaik my only option is to use s/pdif. 
I still have to boot windows to get my awesome 5.1 to play real surround.

Edit: To clarify i want to use Digital (Optical) output

Edit2: Allright, I just realised that the problem may not be my sound card, but the codec I'm using to play files... The link you posted, lykeion, made all sound work for me, before only VLC worked. But still, it does not pass the audio directly (which makes it stereo, I have Logitech Z-5500 and it can take "raw" DTS/DD i think.

---

### Post by lykeion on 2010-09-04
Good to hear you have some progress with your issue.

Ubuntu Lucid uses PulseAudio set to 2 channels by default, but you can change that to 6 channels (5.1 surround sound):

System > Preferences > Sound > Hardware tab > Select surround sound profile from the dropdown box

Test your surround sound
```
speaker-test -c 6
```(6 channels for a 5.1 setup)

Helpful links:
[https://help.ubuntu.com/community/SurroundSound](https://help.ubuntu.com/community/SurroundSound)
[http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)

---

### Post by Vegar on 2010-09-04
Okay, that "works" but not like intended. What I'm trying to say is that the speaker system can make "fake" surround from 2 channel audio, and because it does not recognize the sound as RAW dd/dts, it uses a mode called "PLII - Movie/Music" Instead, which ****s up. Front L/R and Center works but not rear L/R (it plays on front L/R.

I've tried to play a raw dts file, and the speaker system doesnt even recognize that as DTS so. I think the problem is with PA. (when i tested the .dts file i used ("aplay test.dts")

Thanks for the assistance so far, lykeion

---

