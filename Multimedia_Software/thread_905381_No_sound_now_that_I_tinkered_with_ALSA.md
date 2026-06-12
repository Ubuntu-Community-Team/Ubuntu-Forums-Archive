---
title: "No sound now that I tinkered with ALSA"
date: 2008-08-30
forum: Multimedia Software
---

### Post by rapattack1 on 2008-08-30
Hi I was trying to record with a Microphone and now I have no sound at all. I looked at the Sound sticky and tried a few things but didn't want to reinstall ALSA as I have stuffed up with those type of commands before and ended up stuffing everything. Not being able to boot into the system at all and then having to reinstall Ubuntu again. Then the updates and it kills my small internet monthly usage. I just reinstalled a week or so ago:( ! Please help! I have a Sound blaster Live card and the onboard sound is disabled in the bios. Alsa only recognises the sb card but lists it 3 times when I do the command to find out what card I have. I am still very much a newbie to the sound stuff and linux generally.

---

### Post by minky311 on 2008-08-30
Are you talking about this command
```
cat /proc/asound/cards
```

---

### Post by rapattack1 on 2008-08-30
It wasn't that one but here is what i got from that command.
carla@carla-desktop:~$ cat /proc/asound/cards
 0 [Live           ]: EMU10K1X - Dell Sound Blaster Live!
                      Dell Sound Blaster Live! at 0xe800 irq 19

I think I made a really silly mistake.....will get back to you but I think I know why I don't have sound.

---

### Post by rapattack1 on 2008-08-31
Gee I was wrong. I thought I was not getting sound because the power cable to the speakers wasn't plugged in. Don't know when it dropped out but anyway it is hooked up now and still no sound.

---

### Post by minky311 on 2008-08-31
could you also post what you get when you type this into terminal
```
cat /proc/asound/modules
```

Also to make things clear have you gone into system->preferences->sound and if so is your sound card listed?

---

### Post by rapattack1 on 2008-08-31
$ cat /proc/asound/modules
 0 snd_emu10k1x

Yep it is listed there-under default mixer tracks.

---

### Post by minky311 on 2008-08-31
First could you go back to sound and make sure that your sound card is set as the device used for playback in all fields. After that go to the little speaker icon in the upper right hand corner, right click it, go to volume control. Once there make sure there is nothing muted. Also while you're in volume control click file->change device and see if there are any other devices listed if so make sure they are not muted.

---

### Post by rapattack1 on 2008-08-31
OK in sound preferences it says Autodetect for most of the playback things but in Sound Capture it says ALSA. In the drop down boxes it doesn't say Sound Blaster.......... as a selection but it say EMU..... which is the soundcard. But! There is EMU...... rear, EMU...... front..... etc. This has been the problem all along. This front, rear etc thing is all throughout when I try in wether it be Ubuntustudio(this is on my secondary drive) or Ubuntu(plain).
Ok the first device which is the sound blaster I unmuted and enabled everything before so they are fine. The next thing is Sigmatel.....(Oss mixer) and in playback there is only Speaker and that is enabled/up volume wise. In recording volume/line-in/microphone/cd...one is enabled and the others muted. If i unmute one it mutes another of the things automatically.
Next device Playback ALSA PCM...................... there is only playback and the sound is up. Next is Capture Monitor source......................... recording is up and enabled. Next is Capture ALSA PCM on front............... recording Master is up and enabled.
Phew....if you prefer images of whatever let me know.

---

### Post by minky311 on 2008-08-31
Press alt F2 and type in gstreamer-properties under default output try setting plugin as alsa and trying each device one at a time then testing it.
Also try any other configuration to see which one works if any.

---

### Post by rapattack1 on 2008-09-01
Ok well I got some type of sound out of this:
Default output
Plugin: Alsa............
Device:EMU10K1X rear

Default input
Plugin: ALSA
Device: Default

the other device I got either nothing or very low sound. Is that right?

Yes I can play music!!! Geez I still can't record with a microphone.

---

