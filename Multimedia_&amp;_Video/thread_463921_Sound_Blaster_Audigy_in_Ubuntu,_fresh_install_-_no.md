---
title: "Sound Blaster Audigy in Ubuntu, fresh install - no sound"
date: 2007-06-04
forum: Multimedia &amp; Video
---

### Post by cyrylski on 2007-06-04
Hello, 

If you have no sound in a fresh Feisty Fawn install and you're using Creative Labs Sound Blaster **Audigy**, perhaps this may help:

First, type to make sure that your card is detected properly, type this
```
cat /proc/asound/cards
``` into the terminal.

You should get something like that:

```
 0 [Audigy         ]: Audigy - Audigy 1 ES [SB0160]
                      Audigy 1 ES [SB0160] (rev.3, serial:0x521102) at 0xd000, irq 19

```

This means that the card IS working and IS present in the system.

If any audio player you use seems to playback the audio but you can't hear anything in the speakers, try this:

type this into terminal:

```
alsamixer
```

In the ALSA mixer GUI use arrows to go right to the Audigy Analog/Digital Output Jack

In my case I had to TURN OFF the **Audigy Analog/Digital Output Jack** switch.

And... there is the sound: taadaaaaa :)

I hope it helps anyone.

---

### Post by thedannyk on 2007-06-05
Excellent tip.  My exact problem.

---

### Post by Cappy on 2007-06-05
```
sudo apt-get install gnome-alsamixer
gnome-alsamixer
```

gnome-alsamixer is a little more beginner friendly.

I'm using an Audigy 4 (non-pro) and it only works with the "Audigy Analog/Digital Output Jack" control on. Seems to be a common problem for some cards.

---

### Post by cyrylski on 2007-06-05
> **thedannyk said:**
> Excellent tip.  My exact problem.

Whoa! :) I'm glad it helps :)

---

### Post by euchrid on 2007-06-07
If you get the sound up and running, but can't record, try updating the Alsa driver.

Information and instructions at: [http://ubuntuforums.org/showthread.php?p=2798055#post2798055]("http://ubuntuforums.org/showthread.php?p=2798055#post2798055")

Hope this comes in useful for all the people having sound problems relating to Alsa in Feisty.

---

### Post by Kuraboy on 2007-06-08
hi, thank you.... 

I was very sad that Kubuntu 7 couldn't play any sound, tried many tutorials, but yours was the solution :D

Should this be reported as a bug?


It seems like version 7 isn't quite good like version 6, with 6 I could take my laptop to suspend and hibernate, but now I cant :(

---

### Post by Jolt on 2007-06-09
I Have been having sound problems and when I type in alsamixer I get
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xefffc000 irq 16
My card is a Soundblaster X-fi xtrememusic. I am not sure what is wrong

---

### Post by pittimunga on 2007-06-10
I'm having a similar issue as Jolt.  I'm on a laptop so I'm using an Audigy 2 NX via usb.  Ubuntu recognizes it as existing because it is listed in my sound preferences.  When I select it in sound preferences and run "test," I do get a tone through my Audigy.  But all sound from the system besides the test tone still goes through my laptops onboard sound.  

When I run cat /proc/asound/cards through terminal, I get this: 

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xb0000000 irq 21
 1 [NX             ]: USB-Audio - SB Audigy 2 NX
                      Creative Technology Ltd SB Audigy 2 NX at usb-0000:00:1d.0-1, full speed


Anyone have any suggestions as to how to solve this?

---

### Post by mrwasabi on 2007-06-14
My question is, has anyone gotten the full benefit out of their audigy card in linux, I mean eax, eq, and all the other bells and whistles you paid for? I've only managed to get the basic functions for sound, and used the eq in amarok to make it sound a little better, but nothing compared to windows.

---

### Post by Cappy on 2007-06-14
I didn't until I just googled my sound card and "bass treble linux" and found this for my Audigy 4:
```

Tone Controls:
To enable bass and treble tone controls, the 'Tone' switch must be turned on.
This can be achieved with the following command:
           'amixer sset Tone on'

or "unmute" (m key) the "Tone channel" in alsamixer.
Use alsactl to save and restore this and any other settings automatically.

```

So yes, I can do anything my card does on Windows.

---

### Post by whayong on 2007-06-16
I need further help with this.  I still can't get it working.  Here's what I got.

cat /proc/asound/cards
 ```
0 [SI7012         ]: ICH - SiS SI7012
                      SiS SI7012 with ALC655 at 0xe000, irq 3
 1 [Audigy         ]: Audigy - Audigy 1 [SB0090]
                      Audigy 1 [SB0090] (rev.3, serial:0x511102) at 0xea00, irq 11
```

When I do alsamixer, the sis card is what comes up.  So I guess the right question is, how do I tell Ubuntu to use the audigy card?

---

### Post by Cappy on 2007-06-16
Goto (System-->Preferences-->Sound) and make sure your sound card is set on the "device".

Tried that already? Not working? Use this:

[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Configuring_default_soundcards_.2F_stopping_soundcards_from_switching](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Configuring_default_soundcards_.2F_stopping_soundcards_from_switching)

---

### Post by whayong on 2007-06-16
> **Cappy said:**
> Goto (System-->Preferences-->Sound) and make sure your sound card is set on the "device".

Tried that already? Not working? Use this:

[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Configuring_default_soundcards_.2F_stopping_soundcards_from_switching](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Configuring_default_soundcards_.2F_stopping_soundcards_from_switching)

using the GUI doesn't work.

I tried the link, it's not helping either which leads me to believe that I'm doing something wrong.  

 lsmod | grep snd
```
snd_emu10k1_synth       7296  0 
snd_emux_synth         34688  1 snd_emu10k1_synth
snd_seq_virmidi         6784  1 snd_emux_synth
snd_seq_midi_emul       6784  1 snd_emux_synth
snd_emu10k1           120352  3 snd_emu10k1_synth
snd_util_mem            4864  2 snd_emux_synth,snd_emu10k1
snd_hwdep               9092  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           3844  0 
snd_seq_oss            31616  0 
snd_intel8x0           32796  0 
snd_ac97_codec         97312  2 snd_emu10k1,snd_intel8x0
ac97_bus                2304  1 snd_ac97_codec
snd_pcm_oss            43264  0 
snd_mixer_oss          16512  1 snd_pcm_oss
snd_seq_midi            8576  0 
snd_rawmidi            24448  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      7424  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_pcm                76680  5 snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq                49648  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          8204  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    51716  17 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_hwdep,snd_seq_oss,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
snd_page_alloc          9992  3 snd_emu10k1,snd_intel8x0,snd_pcm
soundcore               7520  1 snd

```

From this, is my Audigy card the "snd_emu10k1?"  That's what I used when making the file.  Did I get it wrong?

---

### Post by Cappy on 2007-06-16
I'm going to help with the alternate method, it is much easier.

What is the output from:
```
sudo asoundconf list
```

I'll assume that echoes back just "Audigy" for your Audigy soundcard and then something else for your other. So what you need to run is
```
sudo asoundconf set-default-card Audigy
```

---

### Post by nealj751 on 2007-06-16
> **pittimunga said:**
> I'm having a similar issue as Jolt.  I'm on a laptop so I'm using an Audigy 2 NX via usb.  Ubuntu recognizes it as existing because it is listed in my sound preferences.  When I select it in sound preferences and run "test," I do get a tone through my Audigy.  But all sound from the system besides the test tone still goes through my laptops onboard sound.  

When I run cat /proc/asound/cards through terminal, I get this: 

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xb0000000 irq 21
 1 [NX             ]: USB-Audio - SB Audigy 2 NX
                      Creative Technology Ltd SB Audigy 2 NX at usb-0000:00:1d.0-1, full speed


Anyone have any suggestions as to how to solve this?


I had a similar problem w/ my onboard sound and audigy, to fix it i had to disable the onboard sound in bios, then alsamixer used my audigy instead of it.  Good fix if you don't need the onboard sound.

---

### Post by Cappy on 2007-06-16
I ended up doing that too! =P That was before I knew about the "sudo asoundconf set-default-card" command. I never have needed my onboard sound so I just turned it off.

---

### Post by hifiguy36 on 2007-06-20
Thanks! I was having the same issue. 
> sudo asoundconf set-default-card Audigy
worked for me as well.

---

### Post by Ken Milburn on 2007-08-24
I have a similar problem; no sound from my Creative Labs Sound Blaster X-fi Xtreme Audio.
I do get sound from my USB headset if I select usb audio

cat /proc/asound/cards
 0 [CA0106         ]: CA0106 - CA0106
                      AudigyLS [Unknown] at 0xa000 irq 19
 1 [Headset        ]: USB-Audio - Logitech USB Headset
                      Logitech Logitech USB Headset at usb-0000:00:1d.2-2, full 

Since this is a fairly recent new model, is it possible it needs a different driver? 
Creative Labs lists X-fi Xtreme separate from the Audigy models.  Creative also reports no Linux driver available from themselves.

I tried the suggests posted above with no positive results.

What direction do you suggest?

---

### Post by jimcho on 2007-11-24
Another thanks!

I already had my on-board sound disabled in the bios, but it still shows up in /proc/asound/cards.  I previously had *some* sounds working (divx movies, etc.), but no system sounds or sounds from Internet sites like youtube.

After issuing the ```
sudo asoundconf set-default-card Audigy
``` command, I was able to set all of my sound preferences back to Autodetect and all system sounds and Internet video sounds now work.

Thanks again.

---

### Post by jimcho on 2007-11-24
Actually, it's not all roses.

It's working fine for me once I'm logged in, but apparently the **sudo asoundconf set-default-card Audigy** command is *per user*.  When I log out, I don't get the logout sound or the drum roll in the sign in screen.

When I log into another account, I have to set the defaults all over again.

Is there some way to make the Audigy the system default? So that it works starting from the sign in screen and applies to all users?

Thanks.

---

### Post by sober2007 on 2007-11-26
this is my first time using ubuntu ... this is my first time using linux

i have Sound Blaster Audigy 2 Value

i'm not sure how to do anything ... i want to make it work. where do i get the driver? ... i figured out how to install VLC already and i've run lots of updates for Ubuntu already.

i'm not sure how or where to do command-lines yet ... is there something i can type into synaptic package monitor to get it working?

---

### Post by RozenFrozen on 2008-02-08
K so i know the problem, just not how to fix it, 

It goes >  0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd7cf4000 irq 16
 1 [Audigy2        ]: Audigy2 - Audigy 2 ZS [SB0350]
                      Audigy 2 ZS [SB0350] (rev.4, serial:0x20021102) at 0xb400, irq 17


I need to get The Audigy over top of the HDA

---

