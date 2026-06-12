---
title: "[SOLVED] soundblaster audigy"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by Homunculi on 2007-04-28
i am looking to get the sound blaster audigy working in feisty fawn 7.04 

i tried the upgrade .. that froze and well thank god for backups ... 

so before installing egdy again i thought i would look at F.F.  
to see the new stuff ... (i like ) 

but as all good things there is one problem 

i check out 2 howto's but to no avail the sound carde is seen and loaded ... 
it is not muted .. volume is 100% ... checked the jacks on all (just to make sure even tho i was listening to music before doing the failed upgrade ) 

if some one has a way to get the sound working ... tell me and i will be on feisty fawn :lolflag: 


:guitar: 
rock on

---

### Post by deadgobby on 2007-04-28
If it is not the USB verion. There is several ways to get going. One if you have installed Ubie on the HD. One is disable the on board sound in the BIOS. Next is to double click on the speaker icon. Go to Edit>Prefs and click on the boxes unchecked to mark. Then go to the switches and see if the IEC958 is not check marked. The other is to install ALSA mixer. Play with the volume levels and go. You can install ALSA mixer several ways. One is through the terminal.
 sudo aptitude install alsamixer. Once installed. Open up the Terminal and type in alsamixer and use the tab key and adjust sound levels.
Gobby

---

### Post by sradhakrishna on 2007-04-28
Am almost sure you've done this already, but if you haven't, can you try this and see if it works for you??

Go to System->Preferences->Sound and on the Devices tab, set all the options to ALSA (some of them have Autodetect or Intel ICH5). You will need to reboot once you've set these options...

In the volume control (System->Preferences->Volume), File->Change Device set to Audigy.

This worked for me!

Regards,
Radha.

---

### Post by Homunculi on 2007-04-28
sorry i am kinda out of wit on meds ... 

here is what i have .. custom system 

amd x2 3800+
1gb ddr2 800mhz
2 250gb sata drives 
2 plextor ide dvd 
nvidia 7600gt 
soundblaster audigy

...$alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

...$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy [Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM
Playback]
  Subdevices: 32/32


i have gone into sys setting and played with controls ... 
and aslamixer ..

went to one web page and emu 10k2 driver is to be on there and that file or driver is not listed in Feisty fawn

---

### Post by Homunculi on 2007-04-28
and i forgot to mantion it was a clean install

---

### Post by phansiizwe on 2007-04-28
If you are running Gnome, double click on the speaker icon next to the clock to get to the Gnome mixer screen.
Select the tab labeled "switches" and deselect the "Digital Output Jack" checkbox.
This should get your sound working.

---

### Post by Homunculi on 2007-04-28
nope i am using kde ... 
is this a problem ?

---

### Post by Homunculi on 2007-04-28
i wish not to say i/o error 
but it was me more than likely .. coming out of a codeine  comma (being treated for pneumonia )

after poking and prodding on the feisty fawn install i just reinstalled ... went strait to the volume control  and turned of the digital output and all the drivers work for the soundblaster audigy ... 

thank you every one for the help and the how to's .. i have feisty fawn up and running 
 
with all mp3, dvd, wav, and system sounds running

---

### Post by Ardentfrost on 2007-04-29
I have tried everything in this thread and am still having problems with my Audigy 2 ZS :(

I've changed just about every setting possible in both alsamixer and in the System -> Preferences -> Sound thing... Earlier I had 2 sound cards (one on-board) so after failing to get my Audigy to work for a bit, I just disabled the other via BIOS so my Audigy is now card 0... and it still doesn't work.  I've done the "turn the A/D off" thing (and when I toggle it, I hear a little pop in my sub, so that makes me think it's close to working :mad: ).  I did the IEC958 thing suggested in this thread to no avail.  I've dodecaquintruple checked mutes in every mixer available to me.

I've also tried a plethora of suggestions from other threads too. :cry: 

Is it just futile at this point?  What am I doing wrong?  :(

---

### Post by Homunculi on 2007-04-29
i hope you have luck with you sound card ... i was looking everywhere and i started loading drivers and all that stuff .

 but like i said ... i was in a drug induced comma for pneumonia .. 

did you try a reinstall go straight to the panel  turn off the a/d and try ? 

all mine worked no problem... 

do not give up on it ... you will get it  (i did lol) :) 

:guitar:  

rock on

---

### Post by mpgarate on 2007-04-29
I had this problem. It was extremely annoying. Thanks to this thread, I Won!!! I have sound, after unselecting audogy analog/digital output jack. Community Support Rocks!

---

### Post by Ardentfrost on 2007-04-29
> **mpgarate said:**
> I had this problem. It was extremely annoying. Thanks to this thread, I Won!!! I have sound, after unselecting audogy analog/digital output jack. Community Support Rocks!

I wish that would have worked for me :(  I still have major issues

---

### Post by ivesjd on 2007-05-28
worked for me with a fresh install of Fiesty. No drivers or anything. But Im kinda wondering what it would be like with the drivers. Must be something good about having them :)

---

### Post by Drake2k on 2008-02-05
Fiesty

For PONY

Ok I'm having a similar issue.  I can't use gnome alsa mixer because i get errors from it (bug that's been reported).  The stuff works, I just don't have 5.1
I made sure 5.1 was enabled in Amorok and what not.  I don't HAVE a Digital Output Jack option.

I did a aplay -l and get this.

```
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


Any suggestions?

---

### Post by Kopachris on 2008-03-07
> **phansiizwe said:**
> If you are running Gnome, double click on the speaker icon next to the clock to get to the Gnome mixer screen.
Select the tab labeled "switches" and deselect the "Digital Output Jack" checkbox.
This should get your sound working.

Thank you!  That worked for me.

---

