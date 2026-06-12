---
title: "Mysterious Loss Of Sound in 9.04"
date: 2009-06-26
forum: Multimedia Software
---

### Post by misteralexander on 2009-06-26
12-hours ago, the sound in my 9.04 install was doing great.  Music over Amarok, phone calls on Skype, Audio of Firefox . . . all was well in my life.

I wake up this morning & there isn't any sound on a movie. Hmm.  I figure ALSA hiccuped.  No sound in Amarok. No sound in VLC.  I force restart ALSA, nothing.  I reboot.  Nothing.  I didn't just update my computer, so I know it isn't some mysterious patch doing this. I'm just all out stumped.

Here is the output of LSPCI:
```

misteralexander@linux-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
02:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)
misteralexander@linux-laptop:~$

```

Here is the output of APLAY -L:
```

misteralexander@linux-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
misteralexander@linux-laptop:~$ 

```

Seemingly for no reason, just nothing. No entry sound(s), nothing . . . just bunk.

Any help is help!  Thanks!
-Alex.

---

### Post by tixetsal on 2009-06-26
Same problem here after recent updates.  Stried several solutions, no luck.  Reinstalled.  Audio worked great until i updated, then I lost audio again.
I feel your pain, brother.  I just want to watch blade runner in 1080p, for pete's sake!

---

### Post by tolotos on 2009-06-27
Have you checked whether the alsa volumes are muted in alsamixer (Search for something like "Analog F" or Master")? Have you tried to configure your audio-program in a way so that it sends the output directly to alsa, instead of pulseaudio? Provides the console output of vlc or your favourite music player any clues?

---

### Post by tixetsal on 2009-06-27
I discovered that by booting 2.6.28-11-generic, instead of 2.6.28-13, my audio was restored, as long as I booted that kernel. I have another box with Asus P5N7A-VM MOBO, and this bug did not effect that machine. My AMD geforce 8200 will not play nice with 28-13 though. My sound card shows up in lspci, but aplay -l tells that I have no sound card.

---

### Post by tolotos on 2009-06-27
Seems like some modules not being loaded in your 28-13. What is lsmod saying? Are there modules related to alsa (they start with snd, or require snd modules) loaded in your kernel?
And what do you mean by AMD geforce 8200? Do jou hava a amd or a nvidia graphic card?

---

### Post by tixetsal on 2009-06-27
> **tolotos said:**
> Seems like some modules not being loaded in your 28-13. What is lsmod saying? Are there modules related to alsa (they start with snd, or require snd modules) loaded in your kernel?
And what do you mean by AMD geforce 8200? Do jou hava a amd or a nvidia graphic card?

I think that you are correct.  The sound seems to work about 25% of the time now in 28-13, for some reason.  
I don't see any alsa modules.  
I have 2 machines, the one that we are tinkering with is an AMD geforce 8200 chipset MOBO.  My intel ASUS P5N7A-VM MOBO has the o/s setup identically, and it has had no sound issues.  

aplay -l tells me that my sound card is not detected, although i can see it with lspci

lsmod from 28-13 yields:

snd_hda_intel         557492  0 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    78792  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm


lsmod from 28-11 yields:

snd_hda_intel         557364  5 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    78792  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm

the diff is:

1c1
< snd_hda_intel         557492  0 
---
> snd_hda_intel         557364  5 
4c4
< snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
---
> snd_pcm                99336  3 snd_hda_intel,snd_pcm_oss
13c13
< snd                    78792  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
---
> snd                    78792  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

---

### Post by EduardoAB on 2009-06-27
i have just installed Skype and it works only for chating. No sound or phone call is possible. Please help !!!

---

### Post by tolotos on 2009-06-28
@tixetsal

Strange. I would have expected more differences. At least one module which is loaded, in 11, which isn`t loaded in 13. Hmm.
Was there any audio-programm running while you made an lsmod on your 11? I don`t believe that it should make a difference in this case, but pls do this just to be shure, that all necessary modlues are loaded. And plaese post the entire output of lsmod (as attachment), eventually there is a strange named, alsa related module, which doesn`t start with snd. The output of dmesg(only of your 13) might also be of some interest (plaese add this as attachment too).
Thats the last thing I would try, If this doesn`t gives any clues, I am out of ideas :confused:. 

@EduardoAB

You can select quite many options in skype, for audio output. I would proceed in this order:
1) Make sure sound works on your system (hearing music, etc....)
2) In skype try the different options for audio-output until you hear the voice of the testcall.
3) Make sure you enabled your micro in alsamixer.
4) In skype try the different options for audio-input.
Step 3 is most likly to cause the biggest problem. There are damn many options in alsamixer. And its pivotal to set them correctly. You should espacially take a close look at the switches (for example "Analog S" or "Shared M"). 
A quicker test programm to check for step 3, is the gnome Sound Recorder, which is installed by default.

Hope that helps

---

### Post by misteralexander on 2009-06-29
> **tolotos said:**
> Have you checked whether the alsa volumes are muted in alsamixer (Search for something like "Analog F" or Master")? Have you tried to configure your audio-program in a way so that it sends the output directly to alsa, instead of pulseaudio? Provides the console output of vlc or your favourite music player any clues?

I am the original thread starter. I learned, that in the new kernel update, ALSA Mixer WAS muted.  All Channels.  I just opened up sound control & un-muted the channels & all was fine.

---

### Post by tixetsal on 2009-06-29
> **tolotos said:**
> @tixetsal

Strange. I would have expected more differences. At least one module which is loaded, in 11, which isn`t loaded in 13. Hmm.
Was there any audio-programm running while you made an lsmod on your 11? I don`t believe that it should make a difference in this case, but pls do this just to be shure, that all necessary modlues are loaded. And plaese post the entire output of lsmod (as attachment), eventually there is a strange named, alsa related module, which doesn`t start with snd. The output of dmesg(only of your 13) might also be of some interest (plaese add this as attachment too).
Thats the last thing I would try, If this doesn`t gives any clues, I am out of ideas :confused:.

tolotos, thanks for the suggestions.  As annoying as these types of bugs can be, they have helped me learn more about the o/s than I would if everything was seamless.  

-interesting blurb:
[http://drowninginbugs.blogspot.com/2009/02/pulseaudio.html](http://drowninginbugs.blogspot.com/2009/02/pulseaudio.html)

OK, with music playing, here I have lsmod from 11 working, 13 failing, and 13 when it WAS working (it seems to work every 3-4 boots).  I had to compress the dmesg to meet the forum guidelines.  I included a copy from -13 with audio and -13 without audio.  
You may want to grep or diff those jokers, because they are enormous.  Thanks.

---

### Post by EduardoAB on 2009-06-29
Thank for tour help but still w.o. sound. What is ALSAMIXER? Where is it in UBUNTU?

---

### Post by Andrew U.K. on 2009-06-30
Alsamixer is the volume control for the advanced linux sound something... Basically it controls the sound levels.

Open a terminal and type alsamixer to open up its control panel.

---

### Post by Andrew U.K. on 2009-06-30
I'm looking at alsamixer and the very first box IEC958 shows off.
Should this be on? If so how do I turn it on?

I lost sound after upgrading to 9.04 from Hardy.

Thanks.

Andrew

---

### Post by tolotos on 2009-07-03
@Andrew U.K.

IEC958 is a switch for digital output. This being off is correct. If you would turn it on, your sound would vanish, because normal speakers can`t handle digital output. Select the option in alsamixer  and type "M" to see the consequences yourself (It does no harm). Type "M" again it will be off.

Have you tried to configure your audio-program in a way so that it sends the output directly to alsa, instead of pulseaudio? If this works, we would know your problem being pulseaudio. If this doesnt work its alsa.

@EduardoAB

Are you getting along? 

@tixetsal

Your lsmod and dmesg seems fine. With your sound working sporadically I have really now idea what could be wrong. As you might have noticed in your working lsmod, snd_hda_intel is used by more processes than in the failing lsmod. My gues would have been, that some old config files have remaind during your upgrade and that they would cause the problem. However with your sound working sometimes, this seems unlikly.
A schot in the blue wchich might solve the prob would be to do a 

apt-get --purge remove alsa pulseaudio
apt-get install alsa pulseaudio

The option --purge removes the config files, when deinstalling. Aside from that I am unfortunatly out of ideas. 
I hope that you will solve your problem

---

### Post by tixetsal on 2009-07-05
> **tolotos said:**
> 
@tixetsal

Your lsmod and dmesg seems fine. With your sound working sporadically I have really now idea what could be wrong. As you might have noticed in your working lsmod, snd_hda_intel is used by more processes than in the failing lsmod. My gues would have been, that some old config files have remaind during your upgrade and that they would cause the problem. However with your sound working sometimes, this seems unlikly.

The thing is, this is a fresh install of 9.04, not an upgrade.  Sound works fine on the fresh install, with all defaults, until the new kernel is installed.

> **tolotos said:**
> 
A schot in the blue wchich might solve the prob would be to do a 

apt-get --purge remove alsa pulseaudio
apt-get install alsa pulseaudio

The option --purge removes the config files, when deinstalling. Aside from that I am unfortunatly out of ideas. 
I hope that you will solve your problem

I had tried this before, but I gave it another shot for good measure, with no success.  Thanks for all of the help, man.  It seems that i will just have to boot the older kernel on this chipset.

---

### Post by fagiani on 2009-07-27
I have a T42 from Lenovo with the Intel 82801DB0-ICH4 sound card and ubuntu always worked fine until I upgraded to 9.04 and now my audio acts weird mainly on Skype (where it will at every 2 very minutes hang both in and out audio for exact 10 seconds). Other sound breakage happens on audio players when moving windows, alternating workspaces, etc.

Did anyone have this kind of issue so far? How can I provide more information in order to fix it?

Thanks a lot!

---

### Post by martinbaselier on 2009-07-27
You could give OSSv4 a try.

---

### Post by fagiani on 2009-07-28
I've followed that and the audio still works on ubuntu but skype will not work with audio at all... Any hints?

---

### Post by martinbaselier on 2009-07-28
If you followed my guide and have medibuntu added to your repositories,
just type:
sudo apt-get install skype-static-oss

If you haven't got medibuntu added, follow the multimedia guide in my signature.

---

### Post by igorzwx on 2009-07-28
QUOTE:
just type:
sudo apt-get install skype-static-oss

end of QUOTE

you need skype-static-oss  only if you have OSS4 installed.
If you have ALSA it does not make sense.

---

### Post by fagiani on 2009-07-28
Hey Martin,

Thanks once more! I have Skype working with OSS4 now but the very same pattern of every 2 minutes a 10 second pause, how can I investigate what is going on?

Thanks,

Paulo

---

### Post by igorzwx on 2009-07-28
Hi Paolo!

As far as I know Martin has OSS4, but he does not use Skype.
I have both. Skype works well.
I am really intrigued what is the problem

---

### Post by igorzwx on 2009-07-28
"every 2 minutes a 10 second pause"

Do you have the same with Ekiga?

---

