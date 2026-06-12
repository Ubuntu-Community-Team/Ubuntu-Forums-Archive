---
title: "Default Sound card"
date: 2007-04-15
forum: Multimedia &amp; Video
---

### Post by sanderjd on 2007-04-15
I have two sound cards. One is the built in audio on my motherboard, the other is a sound blaster audigy (more specific details about both cards available if anyone asks). Both cards work fine right out of the install ever since...I think Edgy. The problem is that Ubuntu can't seem to make up it's mind which card to use. Sometimes when I startup it is sending sound through the built-in card, and sometimes through the soundblaster. I would prefer to be able to tell it to use the Soundblaster all the time, but really I just want it to *pick one* so that I don't have to go under my desk and fiddle with the speaker cord all the time just to get sound. Does anyone know how to set the default sound card? I know that in System->Preferences->Sound there is something that says "Default Mixer Tracks", where I can choose the card I want, but this doesn't seem to actually work. I'm using Feisty Beta right now, but I had the same problem with Edgy, and in fact, it was one of the reasons I upgraded to Feisty, because I thought it might fix the problem. No such luck.

Any ideas?

---

### Post by simonn on 2007-04-15
Do you know the module names of the drivers that the sound cards use? A simple way of determining this is to do the following:

```

$ lsmod | grep snd

```

This will list most/all of the modules/drivers involved with sound - post here if you have trouble. Also post what sound cards you have.

Then, create a file in /etc/modprobe.d (e.g. sudo nano /etc/modprobe.d/mysoundcards) called whatever you want to call it similar to:

```

options snd-emu10k1x index=0
options snd-intel8x0 index=1
options snd-usb-audio index=2

```

This forces my Audgy 2 ZS (emu10k1x driver) to be sound card 1 (index=0), my motherboard's built in sound (intel8x0) to be sound card 2 (index=1) and my usb headset (usb-audio) to soundcard 3 (index=2).

Reboot.

---

### Post by sanderjd on 2007-04-16
Ok, that's great. That fixes it. Now my only question is - why does this not work to begin with? Why does the default sound card setting in System->Preferences->Sound not work? Is this a bug? Is there something strange about my hardware that makes it so it doesn't work for me but it works for everyone else? It seems like this is probably a pretty common problem, and fairly simple to fix. Is it already being looked at or should I report it?

---

### Post by simonn on 2007-04-16
> **sanderjd said:**
> Why does the default sound card setting in System->Preferences->Sound not work? Is this a bug?

It does work. However, it only works for applications that use it, i.e. gnome applications, because it is a gnome setting (IIRC - I use Xubuntu and I tend to fix things at the lowest level possible, GUI's are for girls! :)).

I came across this problem using a Java application. Java is unaware of gnome (unless specifically programmed to be aware of it which the app in question was definitely not) and seems to always use the sound card @ index 0.

With choice comes complication.

> It seems like this is probably a pretty common problem, and fairly simple to fix.

Says the one who had to ask how to fix it - not having a go, just pointing out that you are jumping to conclusions. Your situation sounds quite specific to the hardware you are using.

---

### Post by sanderjd on 2007-04-20
Really? Why is it specific to my hardware? I have two sound cards and would like to be able to choose which one the sound comes out of. That doesn't seem specific to my hardware at all, you even told me how to fix it without knowing anything about my hardware besides that I have two sound cards.

Simple to fix does not mean "everyone immediately knows how to fix it" - simple to fix means "it only takes about 20 seconds to fix once someone tells you what the problem is", which this is definitely a case of.

But I do see that maybe what you told me to do is a pretty low level hack that perhaps wouldn't generalize very well (although I don't think I know enough about how multimedia in Ubuntu works to say that for certain).

---

### Post by simonn on 2007-04-20
> 
Sometimes when I startup it is sending sound through the built-in card, and sometimes through the soundblaster.


The apparent random nature of your original problem appears to be unique(ish) and most probably hardware related. Your hardware seems to be causing the kernel to load the sound cards modules in an order that is inconsistent. This does not normally happen.

The solution I gave is not a hack and is documented in the alsa documentation. It also is more generic than setting the sound card used by gnome, KDE, XFCE etc.

---

### Post by Hintshigen on 2007-04-21
Hi Simonn, 

I've been trying pretty much every example and tutorial I can find on these forums to fix my sound card issue. And once I had read your comment on how the Sound Preferences in Gnome is only used by applications that look for it and use it might help explain my problem. I get sound in movies and mp3's but nothing else, no 'click' when clicking on a link and no login/logoff sound. I also don't get any sound in WoW which is useing OSS as per the howto on this site.

After doing that grep here is what I got.

(I have a Sound Blaster Audigy 2 ZS & AC '97 on-board sound)

```

snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         7936  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_emu10k1           121248  2 snd_emu10k1_synth
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_via82xx            29208  0 
snd_via82xx_modem      16008  0 
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_usb_audio          79744  0 
snd_usb_lib            17280  1 snd_usb_audio
snd_hwdep               9988  3 snd_emux_synth,snd_emu10k1,snd_usb_audio
snd_ac97_codec         98336  3 snd_emu10k1,snd_via82xx,snd_via82xx_modem
ac97_bus                3200  1 snd_ac97_codec
snd_mpu401_uart         9472  1 snd_via82xx
snd_rawmidi            25472  5 snd_seq_virmidi,snd_emu10k1,snd_seq_midi,snd_usb_lib,snd_mpu401_uart
snd_pcm                79876  6 snd_emu10k1,snd_via82xx,snd_via82xx_modem,snd_pcm_oss,snd_usb_audio,snd_ac97_codec
snd_seq                52592  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9100  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_page_alloc         10888  4 snd_emu10k1,snd_via82xx,snd_via82xx_modem,snd_pcm
snd                    54020  19 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_seq_oss,snd_via82xx,snd_via82xx_modem,snd_pcm_oss,snd_mixer_oss,snd_usb_audio,snd_hwdep,snd_ac97_codec,snd_mpu401_uart,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
gameport               16520  3 snd_via82xx,emu10k1_gp
soundcore               8672  1 snd
usbcore               134280  7 xpad,usbhid,snd_usb_audio,snd_usb_lib,ehci_hcd,uhci_hcd

```

How do I know what to load first, second, third, etc., etc., also how does the machine know to look in the newly created file in modprobe.d?

Thank you for any help you can offer in this, and sorry to semi-hi-jack this thread.

Hintshigen

---

### Post by simonn on 2007-04-21
These are your three cards:

snd_usb_audio
snd_emu10k1
snd_via82xx

You probably want to do as my first post with:

```

options snd-emu10k1 index=0
options snd_via82xx index=1
options snd-usb-audio index=2

```

> 
also how does the machine know to look in the newly created file in modprobe.d?


Because... it does :). It looks at every file in there when it loads a module.

---

### Post by Hintshigen on 2007-04-21
Thank you very much Simonn, that worked perfectly. I still don't understand how it works fully, but I'm just glad it does. :)

Thanks again, hopefully I can return the favor to you or the community as I learn more about this stuff.

Hintshigen

---

### Post by simonn on 2007-04-21
> **Hintshigen said:**
> I still don't understand how it works fully

In Ubuntu, When the kernel installs a module (a module is the equivalent to a driver in windows), the loader (modprobe) looks through all the files in /etc/modprobe.d to see if there are any options that it should add when loading the module, if the module is blacklisted, if the module name used is actually an alias to another module etc etc.

With the line:

> 
options snd-emu10k1 index=0


What we are saying is:

When you load the module snd-emu10K1 use the optional parameter index=0.

The parameter index=0 tells alsa (the kernel's sound subsystem) that this sound card should be treated as the first sound card. Think of the indexes as virtual sound card slots.

---

### Post by bagg on 2007-05-15
This is the output of mine, can you help me out too : ) 

```
snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         7936  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_emu10k1           121248  3 snd_emu10k1_synth
snd_ac97_codec         98336  1 snd_emu10k1
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10888  2 snd_emu10k1,snd_pcm
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
snd_hwdep               9988  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                52592  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9100  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  17 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
```

---

### Post by nioakeim on 2007-05-23
This is the same as mine situation. You have 2 cards but i think the onboard one is disabled from bios

---

### Post by stchman on 2007-05-23
> **sanderjd said:**
> I have two sound cards. One is the built in audio on my motherboard, the other is a sound blaster audigy (more specific details about both cards available if anyone asks). Both cards work fine right out of the install ever since...I think Edgy. The problem is that Ubuntu can't seem to make up it's mind which card to use. Sometimes when I startup it is sending sound through the built-in card, and sometimes through the soundblaster. I would prefer to be able to tell it to use the Soundblaster all the time, but really I just want it to *pick one* so that I don't have to go under my desk and fiddle with the speaker cord all the time just to get sound. Does anyone know how to set the default sound card? I know that in System->Preferences->Sound there is something that says "Default Mixer Tracks", where I can choose the card I want, but this doesn't seem to actually work. I'm using Feisty Beta right now, but I had the same problem with Edgy, and in fact, it was one of the reasons I upgraded to Feisty, because I thought it might fix the problem. No such luck.

Any ideas?

Here is the way to make one soundcard the default:

[http://www.stchman.com/mult_sound.html](http://www.stchman.com/mult_sound.html)

It worked for me.

---

