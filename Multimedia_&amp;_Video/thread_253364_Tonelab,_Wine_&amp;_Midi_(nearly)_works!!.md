---
title: "Tonelab, Wine &amp; Midi (nearly) works!!"
date: 2006-09-08
forum: Multimedia &amp; Video
---

### Post by gosh on 2006-09-08
Hi,

I'm using a Vox Tonelab SE, a multi-effect modelling board for my guitar.
It has a piece of software (Tonelab SE SoundEditor) so you connect it to your computer through midi and then alter the different sounds and effects.

I managed to install my USB MidiSport 1x1 using this howto: [http://www.ubuntuforums.org/showthread.php?t=96506](http://www.ubuntuforums.org/showthread.php?t=96506)

I installed wine and then launched Tonelab SE SoundEditor using wine.
Perfect!

Then I tried to set-up the right midi-connection. For both MIDI IN port and MIDI OUT port I selected Midisport 1x1.
The program then starts receiving information from my Tonelab board.
It even shows the right information of the currently selected preset on the board, but then stops with an error message:

```
Receive Error:  Can't receive a dump message.
Please check your Tonelab
All other requests are cancelled
```I click OK and it says:

```
Receive Error: Data size is not correct
```When I try change any of the parameters and write them to the board, it works!

So it looks like only receiving gives trouble, not sending.](*,)

I am nearly there.....
Can anyone help me solve the last bit?


EDIT: In Windows XP everything works fine.
The MidiSport ports are called somewhat differently thought:
In USB Midi 1x1
Out USB Midi 1x1
Does that make a difference?

---

### Post by IdoMcFly on 2006-09-08
Oh my god! I'm not alone! :D

I'll try to help when I got some time :)

---

### Post by gosh on 2006-10-30
grrr:(

I'm thrown a step back.
Since Edgy I get this message when running ToneLab through wine

[SIZE=2] ```
[/SIZE][SIZE=2]fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.

``` [/SIZE]
The program starts but the midi-interfaces do not work.

---

### Post by gosh on 2007-01-07
Well, after a disasterous switch to Feisty, I had to do a fresh install of Edgy.
Tonelab works again as in the first post of this thread: able to send but not to receive MIDI-information.

Anyone more luck?

---

### Post by gosh on 2007-01-14
Again, a small succes.
The thing that stops it from completely working probably is a bug in Wine: [http://bugs.winehq.org/show_bug.cgi?id=6788](http://bugs.winehq.org/show_bug.cgi?id=6788)

My pc can receive some information from the floorboard. 
When I start the Soundeditor it gives two errors:
```
Receive Error: Can't receive a dump message
```
```
Receive Error: Data size is not correct
```
In the terminal it reads:
```
err:midi:MIDI_AlsaToWindowsDeviceType Cannot determine the type (alsa type is 100000) of this midi device. Assuming FM Synth
```

When I select Global -> Dump Cur -> Write it send the current patch to the SoundEditor, except for the name of the patch in the small window. In the large blue window everythings seems OK. Also change controls on the floorboard is correctly send to the SoundEditor.

When I select Global -> Dump All -> Write it gives:
```

Receive Error: Data size is not correct

```I use kmidimon to see what messages are sent to and from the floorboard.
To use kmidimon I patch my MidiSport in to kmidimon in the pathcbay of Jack. Global Dump All gives this message in the terminal:

```
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
fixme:midi:midRecThread Sysex received but no buffer to store it!
```This is the exact message as described in the Wine-bug.

To complete, attached is the ouput of Kmidimon.

Anyone any idea how to get on from here?

---

### Post by majoridiot on 2007-01-14
> **gosh said:**
> Anyone any idea how to get on from here?

as this is a bug/implementation problem with wine, your options are pretty limited to being 
patient, keeping on top of the bug report and trying to work around the problem.  or, you can
learn to code, jump in and fix the wine code! ;)

---

### Post by gosh on 2007-01-15
> **majoridiot said:**
> as this is a bug/implementation problem with wine, your options are pretty limited to being 
patient, keeping on top of the bug report and trying to work around the problem.  or, you can
learn to code, jump in and fix the wine code! ;)

Well, I'll just be patient then..:-|

---

### Post by gosh on 2007-04-30
Midi is much improved under wine 0.9.36.
It now works!
:guitar:

---

