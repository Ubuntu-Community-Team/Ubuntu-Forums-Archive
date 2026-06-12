---
title: "ENS1371 - Ensoniq AudioPCI sound problems"
date: 2006-02-23
forum: Multimedia &amp; Video
---

### Post by csk on 2006-02-23
hi all
i am a newbi so please bear with me. i just installed the lastest unbuntu and noticed that i am getting no sound. i went through the FAQ, made sure none of my sound things are on mute but to no avail.
 
i think my sound card is installed. i typed 
"cat /proc/asound/cards"
and got
0 [I82801BAICH2   ]: ICH - Intel 82801BA-ICH2
                     Intel 82801BA-ICH2 with AD1885 at 0xe800, irq 17
1 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI
                     Ensoniq AudioPCI ENS1371 at 0xdf00, irq 21
which i think means my sound card was detected....
any suggestions as to how i can get sound would be much appriciated. 

cheers

---

### Post by mpvano on 2006-02-23
Your 1371 is CARD 1. The default card in your system is CARD 0 which appears to be Intel hardware on your motherboard.

You may be able to get some applications working by changing the "default sound card" entry in the gnome sound control panel (System->Preferences->Sound), but most interesting sound applications don't have anything to do with the method Gnome uses for sound output.

You can also change the defaults for ALSA sound applications by properly configuring a .asoundrc file in your home directory, but again, not all applications may honor this.

There's no other single place you can easily switch ALL applications to use CARD1 instead of CARD 0. You normally need to tell individual applications which card to use.

You'll probably get more joy by figuring out how to disable the intel card if you are not using it. Note however that if you are using a softmodem based on a riser card on the motherboard, this will disable the modem as well.

You may be able to disable the modem in your bios settings. That would be the easiest place to do so if it's supported properly in the bios setup dialog.

Otherwise, if you display the results of the following terminal command:

lsmod | grep snd

you can get a list of all the sound driver modules installed. Once you figure out their names this way, you can try to disable the intel drivers from loading. This would leave your ensoniq card as CARD 0.

(I believe you can disable the card's drivers by blacklisting its driver modules by listing their names in a file in /etc/discover.d, but it depends exactly how your hardware is designed)

hope this helps,

Mario

---

### Post by csk on 2006-02-23
thanks for the reply. 

btw i discover my card is a "Vibra 128" from Creative. does this change anything?

when i type in 

lsmod | grep snd

i get 

snd_ens1371            22240  0
gameport               14472  1 snd_ens1371
snd_intel8x0           30144  3
snd_ac97_codec         72188  2 snd_ens1371,snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  5 snd_ens1371,snd_intel8x0,snd_ac97_codec,snd_pcm_ oss
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_rawmidi            22816  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_m idi_event
snd_timer              21764  3 snd_pcm,snd_seq
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmi di,snd_seq
snd                    48644  16 snd_ens1371,snd_intel8x0,snd_ac97_codec,snd_pcm _oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_dev ice
soundcore               9184  1 snd

I am not sure how to deciper this.

I did go to /etc/discover.d, and fount a file called linux-sound - base_noOSS [Read Only] with 

skip ac97
skip ac97_codec
skip ac97_plugin_ad1980
skip ad1848
skip ad1889
skip adlib_card
skip aedsp16
skip ali5455
skip btaudio
skip cmpci
skip cs4232
skip cs4281
skip cs461x
skip cs46xx
skip emu10k1
skip es1370
skip es1371
skip esssolo1
skip forte
skip gus
skip i810_audio
skip kahlua
skip mad16
skip maestro
skip maestro3
skip maui
skip mpu401
skip nm256_audio
skip opl3
skip opl3sa
skip opl3sa2
skip pas2
skip pss
skip rme96xx
skip sb
skip sb_lib
skip sgalaxy
skip sonicvibes
skip sound
skip sscape
skip trident
skip trix
skip uart401
skip uart6850
skip via82cxxx_audio
skip v_midi
skip wavefront
skip ymfpci
skip ac97_plugin_wm97xx
skip ad1816
skip audio
skip awe_wave
skip dmasound_core
skip dmasound_pmac
skip harmony
skip sequencer
skip soundcard
skip usb-midi

am i supposed to modify something in this? 
thanks 
csk

---

### Post by csk on 2006-02-23
never mind figured it out

---

### Post by daboochmeister on 2006-04-28
Could you share?  I'm not getting any sound at all (but w/ a 1371 that's card 0).

---

### Post by cvmostert on 2006-05-03
[QUOTE=csk]never mind figured it out[/QUOTE]

Yes, it helps alot when you share your sucesses upon getting hardware to work, there are often other people with the same problem who would appreciate the hours you spent in getting your hardware to work.

thats what ubuntu is all about. making it easy

take care

---

### Post by multios on 2006-05-03
Please check my last post in the following discussion:
[http://www.ubuntuforums.org/showthread.php?t=167214&highlight=es1371](http://www.ubuntuforums.org/showthread.php?t=167214&highlight=es1371)

Basically, when you get to gdm, do not log in! 
First, log in at a console, and then type: 
sudo modprobe -r snd_ens1371
sudo modprobe snd_ens1371 

Then go back to your gdm scren (alt-F7) and log in. 

For whatever reason, there is a problem with the module loading correctly at bootup, but using modprobe as mentioned above works. 
I didn't need to use alsaconf, alsamixer, alsactl at all (and in fact you have to run those every time you reboot also...if you try and use them). 

I haven't had any other problems. 
My personal preference and one I really recommend is to use the OSS module (es1371) that seems to take a lot of work. I use the es1371 modules on other systems and it works wonderfully. No problems at all. 

HTH
multios

---

