---
title: "Can't listen to MIDI files"
date: 2005-10-25
forum: Multimedia &amp; Video
---

### Post by albertoramirez on 2005-10-25
Hello my friends

Well, I have a Sound Blaster Audigy card, and got no problem to listen MP3s and WAV files, but I can't listen to MIDI files or tracks in Rosegarden, so...

HEEEEEELP!!!

please

:confused:

---

### Post by zombie_st on 2005-10-26
You'll need to download and install the MIDI package. The easiest way to do this is to install [Automatix]("http://ubuntuforums.org/showthread.php?t=66563"), as it will input the proper repositories and install all the necessary packages for you with just a click.

(Note: You don't even have to type in the terminal to install Automatix; if you download it/open it in the archive manager and then export it to home, you can just double click the install file, and it'll do everything for you. Hope this helps!)

---

### Post by albertoramirez on 2005-10-28
Well, I tried it, but got no sound on MIDI files

so sad :(

---

### Post by nastya on 2005-10-28
Did you restart after using Automatix to install the package? Also, are you recieving any errors when trying to play a midi after installing the package?

---

### Post by albertoramirez on 2005-10-28
Well, re started the session, but today I tried and got no sound.  It is just the output, got no error messages, and the software runs, but got no sound

:(

---

### Post by Clemens Tolboom on 2005-12-27
Do you have midi now?

I tried automatix with the same (silent) result.
- timidity plays midi ... but that's a midi to wav convertor.
- pmidi is silent
- rosegarden is silent

Hope to find any solution soon :(

---

### Post by barfos on 2005-12-27
I am also in MIDI hell.  I can 'make it work' by typing timidity, but I can't get midi to play in any normal program.  So I'm interested in any solutions that show up.

barfos

---

### Post by FarEast on 2006-01-07
Hi,

If you can play MIDI files by typing 'timidity foo.mid' in a shell
window, it is easy to get timidity to work in 'ALSA server mode'.

Alter /etc/ init.d/timidity as follows:

```
#!/bin/sh
#
# TiMidity      /etc/init.d/ initscript for TiMidity++
...
[COLOR="SeaGreen"]TIM_ALSASEQ=true[/COLOR]
TIM_ALSASEQPARAMS="-B2,8"
[ -r /etc/default/timidity ] && . /etc/default/timidity
[ "${TIM_ALSASEQ}" != "true" ] && exit 0
PARAMS="${TIM_ALSASEQPARAMS} -iAD"
...

```

Then...

```
$ sudo /etc/init.d/timidity start
$ aconnect -o
client 62: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
client 72: 'Serial MIDI' [type=kernel]
    0 'Serial MIDI 1   '
client 128: 'TiMidity' [type=user]
    0 'TiMidity port 0 '
    1 'TiMidity port 1 '
    2 'TiMidity port 2 '
    3 'TiMidity port 3 '

```

The output shows available port numbers to which
you can send MIDI messages.  For example, you can
play a MIDI file with pmidi in the following way:

```

$ pmidi -p 128:0 foo.mid
```

I hope this will help you;) 

Kind Regards,
FarEast

---

### Post by stratotak on 2006-01-07
just a thought..seeing as you have a soundblaster..soundblaster cards have midi hardware built in there card...if you wanted you could use the midi hardware om card to play midi...i dont have a soundblaster on my laptop so i have no expierence on setting it up and loading the sf2 font..and youed have to get it so that the sounfont loaded on boot or manually load the sf2 font  every time you wanted to use midi..which im not sure of the commandline for it..but found a post that is more indepth about soundblaster and sf2 and getting to load at boot

[http://ubuntuforums.org/showthread.php?t=47409&highlight=soundblaster+midi](http://ubuntuforums.org/showthread.php?t=47409&highlight=soundblaster+midi)

---

### Post by FarEast on 2006-01-07
What stratotak wrote is a good solution for the topic starter:p .

Those who have sound blaster have only to load soundfonts with
'sfxload' command which the package 'awesfx' provides.

```
$ sudo asfxload xxxxx.sf2
$ aconnect -o
client 64: 'EMU10K1 MPU-401 (UART) - Rawmidi 0' [type=kernel]
    0 'EMU10K1 MPU-401 (UART)'
client 65: 'Emu10k1 WaveTable' [type=kernel]
    0 'Emu10k1 Port 0  '
    1 'Emu10k1 Port 1  '
    2 'Emu10k1 Port 2  '
    3 'Emu10k1 Port 3  '
client 72: 'uart16550 MIDI #0 - Rawmidi 1' [type=kernel]
    0 'uart16550 MIDI #0'
```

Then MIDI file handlers (such as pmidi, kmid, etc.) can use built-in
synthesizer of sound blaster.  For example,

```
$ pmidi -p 65:0 foo.mid
```

---

### Post by vector on 2006-01-07
yes this should be automagicly working in ubuntu!!! ??
I dont like apt-getting or fiddling with config files cause A) i dont know much  and b) im running the flag of linux works outa the box.
I just came across this midi nogo myself.
heres how I fixed it, well i just did what a mate told me...I understand nothing

sudo apt-get install timidity
sudo modprobe snd_seq_midi
lspci -v (find the sound card, mines a mother board device)
modprobe snd_intel8x0
sudo apt-get install freepats
 it works in timidity anyway

please Mr Ubuntu put this on your todo list to be fixed ;)

---

