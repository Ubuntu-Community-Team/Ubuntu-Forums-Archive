---
title: "saa7134 card not detected with # cat /proc/asound/cards"
date: 2007-11-22
forum: Mythbuntu
---

### Post by devrieshh on 2007-11-22
The saa7134 card isnt detected with # cat /proc/asound/cards  
and also not in kmix,witch i used in the previus mythbuntu(in ubuntu 7.10),where i got sound,but with recordings  metallic and to fast.
in this version of mythbuntu, tv time is normally working,togetter with mythbuntu tv tv time has no video but only sound and mythbuntu only video just as only in mythbuntu...
with kmix i could get sound in the mythbuntu version in ubuntu by switching on and of the video switch in saa7134...

---

### Post by devrieshh on 2007-11-23
fixed the problem with reinstalling alsa source etc see` Comprehensive Sound Problem   Solutions Guide`

---

### Post by devrieshh on 2007-11-24
> **devrieshh said:**
> The saa7134 card isnt detected with # cat /proc/asound/cards  
and also not in kmix,witch i used in the previus mythbuntu(in ubuntu 7.10),where i got sound,but with recordings  metallic and to fast.
in this version of mythbuntu, tv time is normally working,togetter with mythbuntu tv tv time has no video but only sound and mythbuntu only video just as only in mythbuntu...
with kmix i could get sound in the mythbuntu version in ubuntu by switching on and of the video switch in saa7134...

problem is I have to do that again after rebooting...

---

### Post by devrieshh on 2007-11-24
> **devrieshh said:**
>  fixed the problem with reinstalling alsa utils etc.(see Comprehensive Sound Problem Solutions Guide v0.5e)  problem is I have to do that again after rebooting...also I am not sertain iI have sound recording films...(recordet movie,no sound just nois...  
.

---

### Post by devrieshh on 2007-11-26
Sound cards are detected after reinstalling alsa...
:~$  cat /proc/asound/cards
 0 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with AD1888 at 0xe400, irq 20
 1 [SAA7134        ]: SAA7134 - SAA7134
                      saa7133[0] at 0xfe900000 irq 19

But,after starting mythtv frontend....,` watching tv`   I have no sound until I startup kmix,moving to saa7134 and swiching video swich off and on again...when i go to the next station I have to do that again...  This is probably also the reason I only can record without sound...

thanks for some advice

---

### Post by KillerKiwi on 2007-12-04
I've got a pinnacle 150 with the same chip

It sounds like you need to use alsa digitally
[http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound#Setting_up_ALSA.27s_.asoundrc.2C_Properly](http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound#Setting_up_ALSA.27s_.asoundrc.2C_Properly)

It looks complicated but just cut and paste the ~/.asoundrc  text

Then make sure the capture volume is up and turn the input level off (else you will be able to hear when its recording!)

It works for me.. although the tv tuner still had a bug I had to work around so I dont get white noise on random channel changes

---

