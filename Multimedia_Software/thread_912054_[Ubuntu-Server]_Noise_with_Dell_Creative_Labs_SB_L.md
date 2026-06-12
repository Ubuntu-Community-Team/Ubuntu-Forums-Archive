---
title: "[Ubuntu-Server] Noise with Dell Creative Labs SB Live! 5.1"
date: 2008-09-06
forum: Multimedia Software
---

### Post by adcwoef on 2008-09-06
Hello

I have a Dell Creative Labs SB Live! 5.1 sound card I i though it would be nice to make some use of it so yesterday I plugged in the whole speaker system to my computer but I did not get any sound. I know it should work because it has before with exactly the same hardware but with other software tough (Windows XP and Ubuntu with GNOME).The problem is that now I don't have a easy GUI to configure the sound with.

I have been Googling around the web for several hours on topics about how to get the sound to work properly, asked in several IRC-channels and I have also tried a lot self but all with no desired results. I Will post some information about the relevant parts of my system below:

```

erikw@compton:~/tmp$ lspci -v
[....]
02:00.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
        Subsystem: Creative Labs Unknown device 1003
        Flags: bus master, medium devsel, latency 64, IRQ 21
        I/O ports at cf20 [size=32]
        Capabilities: [color=#FF0000]<access denied>[/color] (what?)

02:00.1 Input device controller: Creative Labs [SB Live! Value] Input device controller
        Subsystem: Creative Labs Unknown device 1003
        Flags: bus master, medium devsel, latency 64
        I/O ports at cf18 [size=8]
        Capabilities: [color=#FF0000]<access denied> [/color](what?)
[....]

```


```

erikw@compton:~/tmp$ groups erikw
erikw adm dialout cdrom floppy [color=#FF0000]audio[/color] dip www-data video plugdev fuse lpadmin admin

```

```

erikw@compton:~/tmp$ cat /proc/asound/cards
 [COLOR="Red"]0 [Live [/COLOR]          ]: EMU10K1X - Dell Sound Blaster Live!
                      Dell Sound Blaster Live! at 0xcf20 irq 21
 1 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with AD1980 at irq 22

```
0 Live is the correct sound card that I want to use and I assume it's the standard sound card in the system since it has the number 0 and it's the default sound card in *ALSAMIXER*

Here is a picture of my current *ALSAMIXER* settings on the right sound card:

**[PICTURE](http://img.skitch.com/20080905-jb8ah12fmkh9gn922ruqh61b42.jpg)**

The text in Swedish says the following:

*"When this is on Mute I hear noise when I try to play any music or other sound"*


```

erikw@compton:~/tmp$ sudo speaker-test -t wav

speaker-test 1.0.15

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 2048 to 8192
Period size range from 1024 to 1024
Using max buffer size 8192
Periods = 4
was set period_size = 1024
was set buffer_size = 8192
 0 - Front Left
Time per period = 1.318552
 0 - Front Left
[....]

```

When I run this test all I hear is noise or no sound at all depending on if I have Mute or Unmute on the Analog/digital regulator in *ALSAMIXER*.

```

erikw@compton:~/tmp$ mplayer the_latin_kings_-_valkommen_till_fororten_-_halva_inne.mp3
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing the_latin_kings_-_valkommen_till_fororten_-_halva_inne.mp3.
Audio file file format detected.
Clip info:
 Title: Halva Inne
 Artist: The Latin Kings
 Album: V&#65533;lkommen Till F&#65533;rorten
 Year: 1994
 Comment: 
 Track: 10
 Genre: Hip-Hop
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  10.9 (10.9) of 405.0 (06:45.0)  1.9% 

```
When I play music files in *mplayer* all I hear is noise or noting at all depending on the Analog/digital settings in *ALSAMIXER*.

So. What can the problem be? I know it should work.

I really appreciate all help I can get on this because I have tried long on my own no but with the result of fail :(

/Erik Westrup

---

### Post by adcwoef on 2008-09-08
No one knows?

---

