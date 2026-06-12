---
title: "Sound Blaster Live! difficulties"
date: 2006-12-03
forum: Multimedia &amp; Video
---

### Post by nim278 on 2006-12-03
I can't get my Sound Blaster Live! card working. I tried two different cards from the same series: the CT4760 and the SB0060, both based on the EMU10k1 chip. I am running a clean install of Edgy (and tried Dapper live cd as well).

I'm quite sure I followed all the steps of the Comprehensive Sound Problems Solutions guide correctly: [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

The volume control displays the message: ```
No volume control GStreamer plugins and/or devices found.
```

aplay gives the following output: 
```
maciek@maciek-desktop:~$ aplay -l
aplay: device_list:222: no soundcards found...
maciek@maciek-desktop:~$ sudo aplay -l
aplay: device_list:222: no soundcards found...

```

However, the sound card is detected by lspci:
```
maciek@maciek-desktop:~$ lspci |grep Live
02:0d.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:0d.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)

```

Not all the drivers are loaded:
```
$ lsmod |grep snd
snd_timer              27529  1 
snd_page_alloc         12040  0 
snd_util_mem            6528  0 
snd_hwdep              11268  0 
snd                    66924  3 snd_timer,snd_util_mem,snd_hwdep
soundcore              11232  1 snd

```
```
$ lsmod |grep emu
emu10k1_gp              4992  0 
gameport               17160  2 emu10k1_gp

```

So it appears that the driver for the gameport on the card gets loaded, but  the sound driver does not. I would exoect to see either emu10k1 or snd_emu10k1 loaded.

If i do "modprobe snd_emu10k1", it just hangs there until i hit CTRL+C, if I do "modprobe emu10k1" the system freezes and I have to hard reset.

Any ideas?


Maciek

---

### Post by nim278 on 2006-12-03
Partial fix:
I added "snd-emu10k1" to my /etc/modules file and rebooted. This enabled my LiveDrive, but not the soundcard it is connected to. I can hook up my speakers through the headphone jack on the front, but the outputs at the back on the card itself do not work nor are they recognized by Ubuntu. The main control in the volume control is "Headphone", not "Volume". There are no controls available for inputs and outputs on the back, just the front.

This is especially strange because the LiveDrive connects to the computer THROUGH the SoundBlaster card....

Anyone?

M

---

### Post by nim278 on 2006-12-05
I've always been a development version junkie.. so I decided to plunge to Feisty for the heck of it and to see if maybe newer alsa drivers would help something. They don't. Though nothing is broken (yet) :)

M

---

### Post by nim278 on 2006-12-05
Starting to feel pretty lonely here talking to myself, but one more thing to add -- this all worked in Breezy!! It first broke when I upgraded to Dapper and hasn't been fixed since.

---

### Post by suyixiang on 2006-12-11
I am having the same problems with my Sound Blaster Live card.  It looks like you have not had any help.  ](*,)  Have you come up with any solutions?

---

### Post by nim278 on 2006-12-11
Nope.. I'm completely clueless.. seems like I've tried everything :(

---

### Post by janascii on 2006-12-12
I've been having troubles with my soundblaster cutting out as well.  Each time it cuts out I run.

sudo /etc/init.d/alsa-utils reset

and it makes sound again.  One problem I have with this is that it turns my mic on in some random card that Ubuntu detected and I get horrible feedback until I mute that channel.  This fix hasn't been permanent for me yet though.

---

### Post by solitary on 2006-12-12
My Soundblaster Live Value is working fine. Only thing I have done from default install is raising volume in alsamixer for 'Wave Sur' since I use the black connector at the back of my soundcard.

---

### Post by scizmeli on 2006-12-15
I have exactly the same problem with ubuntu 6.10 and have no required knowledge or skills whatsoever to fix it.

please somebody help!

---

### Post by inerlogic on 2007-01-28
same problem here as the first post, same message from the volume control, same results, no sound...

the one thing i haven't tried is moving the card to another pci slot....

going to try that now....

(the next move is to look for a sound card that HAS linux support, if not the drivers included with it....)

---

### Post by inerlogic on 2007-01-28
ok, that actually worked, my mobo has 3 PCI slots (and one PCI-x)
the SB Live was in the bottom slot, there was a factory modem in the next slot up, and the third slot up was empty, i threw out the modem, move the SB Live up two slots, POOF
on reboot i have sound...

try playing musical slots, that may work

---

### Post by nim278 on 2007-03-16
I've tried removing everything but the video card, and the Sound Blaster in every possible slot. Same problem. Likewise, I tried a different Live! card that also uses the emu10k1 driver, and I tried an SB Ensoniq card (uses the ens1371 driver). Same scenario in each case. The hardware seems to be loaded OK, but ALSA doesn't seem to be able to communicate with it. I know these cards work in Ubuntu for other people, and I know they worked for me in Hoary/Warty/Breezy, but Dapper broke them.

It would seem to me like inerlogic is on the right trail though.. it may have something to do with the way the the kernel handles the motherboard / PCI / IRQ settings? I'm kindof stabbing in the dark, but it seems to be specific to certain computers, not certain sound cards....

M

---

### Post by Bernie_K on 2007-07-26
The following easy 3-step fix for my SoundBlaster Live! (model CT4760) worked:

1. Insert the speaker's analog cable plug into the SoundBlaster Live! card's second line-out jack (the jack second-closest to the game port).

2. Under the System->Preferences->Sound menu, Devices tab, change all "Sound playback" selections to "Multichannel Playback", and change the "Device" selection to "SBLive! Platinum [CT4760P] (Alsa mixer)".

Pressing the "Test" button after completing the above steps should result in an audible test tone. (The test tone can also be heard without doing Step 1 above, but no other analog audio signals are directed to the SoundBlaster Live! card's line-out jack closest to the game port- so subsequent tests using other audio sources failed.)

3. Test with an audio data file. For example, from a shell:

aplay /usr/share/sounds/startup.wav

If the test in Step 3 fails, then use the Alsa mixer (litttle speaker icon near the date/time display on the top menu bar) to ensure your "Master" and "PCM" volume controls (on the "Playback" tab) are not muted, and re-test.

If the re-test in Step 3 fails after ensuring the Alsa mixer's Master and PCM volumes are not muted, then toggle (uncheck/check) the "SB Live Analog/Digital Output Jack" under the Alsa mixer's "Switches" tab. This will give the Alsa drivers a little poke, and the test in Step 3 should work.

Good luck!

---

### Post by juniorsonny on 2007-08-27
That worked for me too.  Thanks!!!!!!

---

### Post by lotusel98 on 2007-09-15
This worked for me too!

Thanks!!!

(Note: If the last step still doesn't work, Restart, and it should)

---

### Post by Bif Powell on 2008-02-02
> **Bernie_K said:**
> The following easy 3-step fix for my SoundBlaster Live! (model CT4760) worked:

1. Insert the speaker's analog cable plug into the SoundBlaster Live! card's second line-out jack (the jack second-closest to the game port).

2. Under the System->Preferences->Sound menu, Devices tab, change all "Sound playback" selections to "Multichannel Playback", and change the "Device" selection to "SBLive! Platinum [CT4760P] (Alsa mixer)".

Pressing the "Test" button after completing the above steps should result in an audible test tone. (The test tone can also be heard without doing Step 1 above, but no other analog audio signals are directed to the SoundBlaster Live! card's line-out jack closest to the game port- so subsequent tests using other audio sources failed.)

3. Test with an audio data file. For example, from a shell:

aplay /usr/share/sounds/startup.wav

If the test in Step 3 fails, then use the Alsa mixer (litttle speaker icon near the date/time display on the top menu bar) to ensure your "Master" and "PCM" volume controls (on the "Playback" tab) are not muted, and re-test.

If the re-test in Step 3 fails after ensuring the Alsa mixer's Master and PCM volumes are not muted, then toggle (uncheck/check) the "SB Live Analog/Digital Output Jack" under the Alsa mixer's "Switches" tab. This will give the Alsa drivers a little poke, and the test in Step 3 should work.

Good luck!

I did all of this and everything worked just as you describe however step 3 never works for me.  When I toggle Analog/Digital Output Jack I even here it kind of pulse once in the speakers when I do it so I think it's getting the poke you describe.

(Obvious?) Music and other sounds don't play either.

Many thanks for those steps - helpful troubleshooting information.

Bif

---

