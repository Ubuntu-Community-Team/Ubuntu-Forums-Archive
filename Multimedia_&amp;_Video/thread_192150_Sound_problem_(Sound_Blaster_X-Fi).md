---
title: "Sound problem (Sound Blaster X-Fi)"
date: 2006-06-08
forum: Multimedia &amp; Video
---

### Post by xBoPx on 2006-06-08
Hi

I'm fairly new to Linux and I just installed Kubuntu, everything works fine exept the sound, its not working at all. Im using a Sound Blaster X-Fi card, and it turnes out it was not supported by ALSA. Is there any other way to make the sound work? Can I convert a Windows driver into linux in some way?

---

### Post by Ptero-4 on 2006-06-08
Can you try esd/oss emulation in alsa? Sometimes that works.

---

### Post by xBoPx on 2006-06-08
Thx for answering =)

I installed a package called alsaplayer-esd. (I hope that was correct, im not very good with this.. =) ).
I couldn't here anything and I got this msg: 
"Failed to load output plugin "alsa". Trying defaults.
/bin/sh: /usr/bin/esd: Filen eller katalogen finns inte
Failed to initialize plugin!
/usr/lib/alsaplayer/output/libesound_out.so failed to load
NOTE: THIS IS THE NULL PLUGIN.      YOU WILL NOT HEAR SOUND!!"

---

### Post by puppy on 2006-06-09
Sorry xBopx but there is NO support for the Creative X-Fi in Linux - i.e. whatever you try you will not get sound in Ubuntu using this card. Use your onboard sound instead if you can

Creative are unwilling to release technical details about the new chip which means that the guys over in ALSA development can't even start on writing drivers... and there is no eta i.e. support will be sometime, maybe never (knowing Creative)  :rolleyes:

Update: Creative have said they will make *closed* source driver available in quarter two.....   2007!!

Well now I know that I'm selling my X-Fi, getting something that is supported under linux and never buying another Creative product again - they can go scr*w themselves - way to alienate potential customers Creative - a**holes!

---

### Post by xBoPx on 2006-06-10
Ugh, 2007! That wasn't very fast at all =(. Well I guess Il try the onboard card. If that doesn't work I can always try to dig out some old card from the garage =). 
Thanks alot for the info, I think Im gunna follow you lead and avoid Creative in the future.

---

### Post by desicratn on 2006-06-16
I have the same card (X-fi).I spent too much money on it to just ditch it and honestly it kicks *** on my windows games.
Im pretty new to unbuntu so I wasnt just going to ditch a 100$ card, even though that is pretty f#@^ked up of Creative...so I  tinkered and came up with a cheap work around. 
I just made a cable using a 1/8th(2 female) to 1/8th(1 male) Y adapter, two 3ft male to male 1/8th audio extension cables and a female 1/8th to 1/8th coupler( all parts cost like 10 bucks from radio shack).Just plug the two extensions into the sound out for each card,plug those into the Y splitter, put the coupler on the male end of the Y splitter and plug the speakers into that. Turned on the on board sound which now works in unbuntu (which doesnt see my X-fi anyways), and disabled the onboard sound in windows. It works pretty dang good for a 10$ fix. Just a simple idea that works for me, take it for what its worth.Hope this helps

---

### Post by theguyotc on 2006-07-08
Anyone tried running a cable from the output of a X-fi to the input of an onboard sound card?

---

