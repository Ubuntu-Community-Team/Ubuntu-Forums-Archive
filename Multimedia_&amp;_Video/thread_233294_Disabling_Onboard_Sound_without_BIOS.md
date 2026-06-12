---
title: "Disabling Onboard Sound without BIOS"
date: 2006-08-09
forum: Multimedia &amp; Video
---

### Post by PCalitrack on 2006-08-09
My BIOS suck balls, and I need a way to disable my onboard sound card through Ubuntu? Anybody know the files/procedures I need to modify to remove the check for that sound card? Thanks.

Maybe remove the modules to my onboard sound card?? I am pretty new so I am kind of hesistant about what to remove and how..

---

### Post by simonn on 2006-08-09
If you know the name of the module for you soundcard, you can try blacklisting the module.

add a line to /etc/modprobe.d/blacklist like:

```

blacklist [module]

```

EDIT: Can I ask what you are trying to do, because there may actually be a better way of achieveing this than not loading the driver.

For instance, I wanted to force my Audigy to be card 0, so it was used by default by java. This was done by adding the following to /etc/modprobe.d: 

```

options snd-emu10k1x index=0
options snd-intel8x0 index=1

```

snd-emu10k1x (Audigy) is card 0
snd-intel8x0 (onboard) is card 1

---

### Post by PCalitrack on 2006-08-10
I think I may actually be trying to do the same thing as you are suggesting. See I am running a Dell Laptop (with crap BIOS), and I have an external SB Live 24 Bit plugged into my USB hub. I get sound out of the card when I play music or watch movies, but I still have a few complaints. When I am listening to music and I run a flash program or play a movie at the same time, my sound comes out of my laptop speakers instead of my speakers plugged into my SB Live External. Likewise with Java, for some reason java is sending its sound through my onboard sound card (actually it sometimes sounds like it is coming from the same place as system beeps). I figured if I could get my system to stop looking for the onboard sound card then sound would have to go through my SB Live external. 

My SB live external sound card is set as the default currently in the System->Preferences->Sound... I also has problems mixing. I'll be listening to music then get on GAIM and chat for a while. Then I turn off my music player and I get beep after beep after beep after beep. Also, this doesn't relate to those problems, but I don't have any options in alsamixer for my sound card other than the volume controls.

---

### Post by simonn on 2006-08-10
What does the following return:

```

lsmod | grep snd-

```

---

### Post by PCalitrack on 2006-08-10
patrick@patrick-laptop:/$ sudo lsmod | grep snd-*
snd_intel8x0           33692  0
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_usb_audio          79296  2
snd_usb_lib            16640  1 snd_usb_audio
snd_rawmidi            25504  1 snd_usb_lib
snd_seq_device          8716  1 snd_rawmidi
snd_hwdep               9376  1 snd_usb_audio
snd_pcm                89864  5 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_usb_audio
snd_timer              25220  1 snd_pcm
snd                    55268  13 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_usb_audio,snd_rawmidi,snd_seq_device,snd_hwdep,snd_pcm,snd_timer
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
soundcore              10208  1 snd
usbcore               130692  8 usblp,usbhid,snd_usb_audio,snd_usb_lib,usb_storage,ehci_hcd,uhci_hcd

---

### Post by simonn on 2006-08-10
Adding the following to the bottom of /etc/modprobe.d/alsa-base and then rebooting should do the trick: 

```

# My Mods - Force soundcard number
options snd_usb_audio index=0
options snd-intel8x0 index=1

```

You may have to reassign the gnome sounds to the usb soundcard, but probably not.

---

### Post by PCalitrack on 2006-08-10
I'm confused. I guess i am the type of person who likes to know what is going on and how you came to that conclusion. Now as far as I can tell, the index thing is assigning the card # to each card. Maybe, I am wrong on this, though. Currently, I have the SB Live as default so it is card 0 already.

patrick@patrick-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: External [SB Live! 24-bit External], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Or maybe is that the device #?

Thanks for the help. I really appreciate it.

---

### Post by PCalitrack on 2006-08-12
Ok, I figured out how to disable my onboard sound card using just linux. Here's what I did:

I have a Sound Blaster Live 24 Bit External and an onboard Intel AC97 card.

1) Issue the command "lsmod" and find the mods for your internal sound card
2) sudo gedit /etc/modprobe.d/blacklist
3) For each module, append "blacklist <module>" to /etc/modprobe.d/blacklist where <module> is the name of your module.
Here is what I added to mine:
# turn off internal soundcard
blacklist snd_intel8x0
blacklist snd_ac97_codec
blacklist snd_ac97_bus
4) Reboot and enjoy.

This fixed my problems in flash whereby sound would come out my onboard card. Now sound is directed to my external card. However, there are a few minor issues: (1) Sound only comes out 2-2.1 for the Firefox flash players (2) You cannot play music and listen to the flash player audio at the same time (i.e. no mixing with flash)

Hope this helps someone.

---

### Post by rafaelcapanema on 2006-11-29
Thank you very much, PCalitrack! I've got practically the two same sound cards as yours. Worked perfectly for me.

---

### Post by blaqmarket on 2007-03-09
omg PCalitrack thank you soooooooooooo much, ive had the same problem with my turtle beach santa cruz card and was frustrated by the lack of audio and would sign onto my windows partition just so i could listen to some music, but now that is no longer the case. thank you again

---

### Post by ManOnOneWheel on 2007-07-31
All right! You got it buddy. I finally got my stupid Intel ICH6 SigmaTel whatever nothing chip to disappear. All my sound now comes through my Audigy 2 ZS Notebook. Took me forever to find this thread, and boy am I glad I did.

---

### Post by arsnova on 2007-11-14
I've followed *every* thread I can find on getting my Audigy 2ZS working consistently--prior to Edgy and Gutsy, all was okay (notebook: Dell Inspiron 9300)...

Maybe none of us are fans of blacklisting devices, but this absolutely did the trick!:D Before now, I've had a *nightmare* of a time getting ALSA to commit to my external card.

Thanks! :guitar:

---

### Post by Acuos on 2007-12-07
Wanted to say thanks for the file edit.  Been struggling to get the sound card working, Audigy 2 ZS Notebook.. Finally have all hardware working. 

:KS

---

### Post by doctorwho? on 2008-04-15
alright follow up on the thread , i've tried the blacklisting script but i'm not getting aloud any permissions.. what do i need to change and what am i doing wrong ? nice forum by the way

*Edit 
Nevermind fixed it :) Thanks

---

### Post by simonn on 2008-04-15
Do you mean that you do not have permissions to edit /etc/modprobe.d/blacklist?

Tru using:
```

sudo nano /etc/modprobe.d/blacklist

```

---

### Post by RoughriderUT on 2008-06-14
Been racking my brains for a fix on this, thanks a lot for the info PCaltrack

---

