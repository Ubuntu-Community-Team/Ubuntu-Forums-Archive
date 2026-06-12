---
title: "Download songs from Imeem and MySpace"
date: 2008-06-07
forum: Multimedia Software
---

### Post by Jojan on 2008-06-07
Is there a good easy method on how I can download music from Imeem and MySpace that isn't meant for downloading?

I've found guides for Windows, but none for Ubuntu (or other GNU/Linux based systems). I know it is possible to record the sound that's going out from spekers directly to Audacity, but I have never gotten that to work. But don't get hung up on Audacity if you have another method to grab the tracks.

Worst case might be that I have to borrow my parent Windows XP copmuter to get it down.

---

### Post by mastermindg on 2008-06-07
Taken from:

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

Recording example using PulseAudio and Audacity

This recording is equivalent to using the 'stereo mix' source setting in Windows to record the sounds going through the computer i.e. it should be able to record anything that the computer can output to speakers/headphones. Note that recording from some sources e.g. some web-based Flash audio sources, may be illegal in some countries; it is your responsibility to ensure that you abide by all relevant laws.

This example worked on Hardy 8.04. For the initial configuration, the above steps were followed except that:

    *

      Nothing was put into /etc/asound.conf
    *

      libflash-mozplugin was installed as well as libflashsupport.
    *

      The three changes listed above under 'Applications -> Sound and Video -> click on PulseAudio Preferences' weren't made. (Note also that these options are now under Applications -> Sound and Video -> PulseAudio Device Chooser, which launches a panel icon 'PulseAudio Applet', and then they are under Configure Local Sound Server, but they weren't changed in any case).

Once Audacity, PulseAudio and a sound source e.g. Totem music player or a web-based sound source are working, take the following steps to record.

    *

      Open up 'Applications -> Sound and Video -> PulseAudio Volume Control'.
    *

      Assuming you started with no applications playing anything, the Playback tab will be blank
    *

      On the Output Devices tab, right click on the volume level for the sound output that you actually listen with e.g. USB audio headphones might be 'ALSA PCM on front:1 (USB Audio) via DMA'. Select Default in the little box that pops up.
    *

      On the Input Devices tab, on the Show options at the bottom right, choose Monitors (or All). Right click on the monitor for the sound output that you listen to i.e. the monitor of the same device that you selected on the Output tab e.g. 'Monitor Source of ALSA PCM on front:1 (USB Audio) via DMA'. Select Default in the little box that pops up.
    *

      Open up the source of the sound, e.g. Totem music player or a web page that plays audio. Once the sound starts, pause it and go back to the start if you can.
    *

      Go back to the Playback tab of the PulseAudio Volume Control. It should be showing the sound stream. If you right-click on the volume bar of the stream and hover the mouse over the 'Move Stream...' words, you can verify that the sound is pointing towards the same place you selected in Output Devices above.
    *

      Open up audacity but use the command 'padsp audacity' instead of just 'audacity'. This will make the OSS source within audacity actually come from PulseAudio. You can permanently change the command for the menu item if you wish using System -> Preferences -> Main Menu.
    *

      Under Edit, Preferences in Audacity, in the 'Audio I/O' section, de-select the two checkboxes under Playthrough, set the recording device to 'OSS :/dev/dsp' and the channels to '2 (Stereo)'. Set the playback device to 'OSS :/dev/dsp' too. Click on Ok to close the dialog.
    *

      Click on the record button in audacity and start the sound off again from the source. When you're done, stop the recording in audacity, remove any bits of the sound that you don't want e.g. leading and trailing blank sounds, and export as an mp3 file.

---

### Post by Huss on 2008-07-04
Thanks, that worked for me.

---

### Post by nickpick on 2009-06-06
There's actually a potentially better way of doing it.

1. Install Firefox and the DownloadHelper extension.
2. Find the song and download the .flv file, using the said extension. This is essentially the .mp3 you want, hidden inside a different container.
3. Extract using the terminal: ```
mplayer DOWNLOADED_FILE.flv -dumpaudio -dumpfile OUTPUT.mp3
```
4. Use the program of your choice to edit the tags, e.g. Amarok, Picard, Audacity, etc.

---

### Post by n~kf)}BW% on 2010-11-08
Here is a working Linux shell script to download MySpace music, for real geeks only! (It's not that easy for beginners but will do the job ;) I encourage you to improve it.
Tested in Ubuntu :popcorn:
[http://360percents.com/posts/linux-myspace-music-downloader/](http://360percents.com/posts/linux-myspace-music-downloader/)

---

