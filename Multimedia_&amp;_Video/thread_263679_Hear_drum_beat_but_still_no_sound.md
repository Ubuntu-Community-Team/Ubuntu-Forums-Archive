---
title: "Hear drum beat but still no sound???"
date: 2006-09-23
forum: Multimedia &amp; Video
---

### Post by PCSpectra.com on 2006-09-23
First off I apologize if this answer is right under my nose, but I have searched Google and these forums and I am either not using the right keywords or I blazed right by the answers.

I booted up with Knoppix and I hear sounds properly, so I know it's not a faulty hardware issue.

I plugged the speakers in correctly and I managed to get a quick drum beat at startup under Ubuntu, but once I get into the desktop area and goto Sounds menu and click any of the sounds or search and find wave files and double click on them to play them, I get an error along the lines of: 

**Totem could not start**
Could not establish connection to sound server

I have searched for TOTEM and Sound System on these forums and could not find anything relevent.

I have also browsed many of the stickies in hopes of finding something. I've played with the graphical equalizer and made sure everything was on...


I'm at a loss, I can't figure out why I can hear that drum beat at startup but no other sounds will play when double clicked wave files???

Anyone know what may be going on?

ASUS Mother board, C-Media Electronics
CM8738

Not sure if that info will help any...

Ideas, suggestions, comments???

Cheers :)

---

### Post by christhemonkey on 2006-09-23
Are you sure that the volume isnt muted?
(look at the volume icon in the top right hand tray)

I know i fell for this one, as have a few...

EDIT: Accidentally skimmed over the bit you mentioned about Totems error report.  That wouldnt be caused my the sound being turned down...
If you go into a terminal and type
```
sudo killall esd 
``` 
What happens?

---

### Post by PCSpectra.com on 2006-09-23
Hey...thanks for the quick reply

I've tried that and all I get is

esd: No process killed

I tried running esd at the terminal and got this?

> ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default


---

### Post by christhemonkey on 2006-09-23
What is the output of:
```
aplay -l 
```

and

```
cat /proc/sound 
```

---

### Post by PCSpectra.com on 2006-09-23
1) No Sound Cards Found

2) No such file or directory

I'm totally lost...why would I hear the startup drums, which Ubuntu would need the sound card/drivers for...then when I do this, nothng happens???

---

### Post by christhemonkey on 2006-09-23
Hm what about
```
cat /proc/asound/cards 
```

and:
```
lspci -v | grep -i audio 
```
The first one see if ALSA (the default sound architecture) detects your card at all.

The second sees if the kernel recognises it (presumably it does if it plays the drum sound at login!)

---

### Post by PCSpectra.com on 2006-09-23
A little more promising I guess :-P 

> 
root@PCSpectra1:~$ cat /proc/asound/cards

0 [CMI8738MC6     ]: CMI8738-MC6 - C-Media PCI CMI8738-MC6
                     C-Media PCI CMI8738-MC6 (model 55) at 0xd800, irq 177
root@PCSpectra1:~$ lspci -v | grep -i audio

0000:00:05.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)


---

### Post by christhemonkey on 2006-09-24
Can you type:
```
lsmod | grep cmipci 
```

That is listing all modules currently loaded by your kernel, and then searching through to see if the one for your soundcard is loaded. (it should be)

If it produces no output, try loading the module:
```
sudo modprobe snd-cmipci 
```

---

### Post by PCSpectra.com on 2006-09-24
Edit: Here are the results of the first command

> snd_cmipci             34336  0
gameport               15496  1 snd_cmipci
snd_pcm                89864  2 snd_cmipci,snd_pcm_oss
snd_opl3_lib           10624  1 snd_cmipci
snd_mpu401_uart         7808  1 snd_cmipci
snd                    55268  10 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device


Cool, I will try this...

In the mean time, while reading Ubuntu docs, learning about APT, etc...

I opened my sessions window to see what apps I was loading and nocited this:

***** I tried removing --sm-disable restarted and still nothing :(*****
> gnome-volume-manager --sm-disable 

From what I understand, Sessions are analogous to Windows startup menu...

So if my volume manager is loading and disablling something at startup...

Could that be the reason why I hear the drum beats at startup but once applications start initializing I hear nothing???

How would I fix this if this is indeed my problem? How would that have occured, I don't remember disabling anything at install

---

### Post by christhemonkey on 2006-09-25
gnome-volume-manager actually deals wth mounting removable medium (CDs and usb disks for example), so is unrelated to this.


Ok, the module is loaded.
This is good!


I have this sound card as well, and seem to remember it being screwed up when i installed...
I think to fix this, i just deleted the all .asound files in my home directory.

Open a file browser in your home directroy and press Ctrl+H to view hidden files, then delete all starting with ".asound". Then try playing a .wav file or the like.
If this works, then you can delete them from your trash.

If not, restore them for now and edit the file /etc/asound.conf

```
gksudo gedit /etc/asound.conf 
```

and add this to the new file:
> pcm.!default {
type hw
card 0
}

ctl.!default {
type hw
card 0
}

Then try playing a sound file.

---

### Post by ISagalaev on 2006-11-15
> Open a file browser in your home directroy and press Ctrl+H to view hidden files, then delete all starting with ".asound".

Ah! Thank you very much!

I have similar problem (drum sound on login prompt, then no sound in Gnome) after upgrading from Dapper to Edgy. Deleting .asound* helped.

Now some details to my case.

After reading the old .asoundrc.asoundconf I've created a new file with this:

```

asoundconf list                           # pick a card from the list
asoundconf set-default-card I82801DBICH4  # set it as default

```

And then I compared this new file with the old one and found that it was trying to use my AC97 modem as a default sound card:

```

-!defaults.pcm.card Modem
-defaults.ctl.card Modem
+!defaults.pcm.card I82801DBICH4
+defaults.ctl.card I82801DBICH4

```

---

