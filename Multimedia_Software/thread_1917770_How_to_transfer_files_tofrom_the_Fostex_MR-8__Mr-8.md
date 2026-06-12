---
title: "How to transfer files to/from the Fostex MR-8 / Mr-8 mk 2"
date: 2012-01-30
forum: Multimedia Software
---

### Post by jinnan_tonnix on 2012-01-30
I own a rather old Fostex MR-8 solid state 8-track digital multitrack recorder. Although old, it still sounds great with a MIC200 pre-amp and condensor microphone driving the inputs.

In fact, I prefer using it to record guitar parts for songs.

Anyway, the although the audio is recorded to standard WAV files, Fostex use some tricks to preserve space. If you use overdubs, or punch-ins at certain parts, only these clips are recorded and a metadata file is created which instructs the Fostex on when to play the clips as a finished song.

The problem importing this to a PC based DAW (e.g. Rosegarden, Ardour, Audacity or my personal favourite - Qtractor) is that the clips do not line up. All the parts need to be manually aligned in the sequencer.

Fostex provide some software which will left-pad the clips with silence so that the individual tracks all line up perfectly in your DAW - but it's only for Windows or Mac.

However, the good news is that the Windows software will work with only a minor tweak to Wine.

Here's how:

First, you'll need to get the Windows version of Fostex's Wave Manager software.
[http://www.fostexinternational.com/docs/tech_support/wav_manager.shtml](http://www.fostexinternational.com/docs/tech_support/wav_manager.shtml)
If over time, the link becomes invalid, search for Fostex Wave Manager.

If you haven't already installed WINE, you'll need to do this now.


For some reason, the Wave Manager program will only look at drive D and this must be configured as a floppy drive.

Using a USB cable, either:
[LIST]
[*]Connect the Fostex and switch it to its USB mode, from the menu.
[*]Or, it's easier if you have a card reader; connect the card reader with the memory card in place.
[/LIST]


[LIST=1]
[*]Configure Wine (in Unity type 'wine' then choose Configure Wine)
[*]Under the Drives tab, remove any drive which may already configured as 'D'.
[*]Click the 'Add' button, then choose drive 'D'
[*]Click the 'Browse' button, and choose the folder into which the memory card is mounted (it will be something like /media/FOSTEX)
[*]Click 'Show Advanced' and choose 'Floppy disk' from the drop-down list under the 'Type' section. *** THIS IS CRUCIAL ***
[*]Click OK
[/LIST]

Now launch the Fostex software by right-clicking the WAVManager.exe file and choosing to launch with Wine.

With luck, you'll be able to see the song folders and their wave files.

Enjoy!

---

