---
title: "Not able to make an audio discs in Brasero"
date: 2020-03-31
forum: Multimedia Software
---

### Post by Joe_Linux on 2020-03-31
Not able to make an audio discs in Brasero. I add an mp3 file to start I tell it to burn it starts and freezes. Any help would be appreciated.

---

### Post by Autodave on 2020-03-31
Try *xfburn.*  It is in the repositories.  Works very well and works when Brasero won't.

Keep in mind that if you are using MP3s, you do not want to create an audio disk: that is for WAV files.

---

### Post by Joe_Linux on 2020-03-31
Saw youtube video did chmod for 
sudo chmod 4711 /usr/bin/cdrdao 
sudo chmod 4711 /usr/bin/wodim 
sudo chmod 0755 /usr/bin/growisofs
Thanks

---

### Post by Autodave on 2020-03-31
MP3s cannot and do not need to be burned as an audio disk!  If your player is capable of playing MP3s, then use New Data Composition.

---

### Post by DuckHook on 2020-03-31
@ Joe_Linux

Autodave is entirely correct. You appear to be confusing the concept of an audio-disk with a data-disk. They are completely different animals. You cannot burn an audio-disk by simply transferring mp3 files. Repeat: mp3 files are not audio-disk files. They are data files. If you simply copy them to a CD/DVD disk using Brasero, they will not play in a primitive CD player.

New CD players can play mp3, but they must read the CD/DVD as a data disk, **not** an audio disk.

If your player can only read audio disks, then to create an audio disk, you must first transcode your mp3 files back into WAV files. Only then can you burn your audio-disk using WAV files. To transcode mp3 to WAV, use the command-line utility mpg321:```
sudo apt install mpg321
```Read the man page after installing.

---

### Post by scdbackup on 2020-04-01
Hi,  normally Brasero should be able to convert MP3 automatically to the uncompressed CD-DA format. The web says that it uses program gstreamer for that.  Whatever, a wrong audio input format is not supposed to cause a freeze of the burn program. The effect is rather that the resulting CD would play random noise.  If Brasero's messages don't give a clue, then you will have to convert the MP3 files manually and use a backend burn program like cdrdao, wodim, cdrecord, or cdrskin. E.g. ```
 cdrskin dev=/dev/sr0 -audio -sao -eject trackfile1.wav trackfile2.wav trackfile3.wav 
``` The same arguments work with wodim and cdrecord, too.  If the freeze of Brasero is with the conversion stage, then above run might yield a playable CD. If the problem is between Brasero's burn backend and the drive, there is at least hope to see some program messages which explain what's wrong.  Have a nice day :)  Thomas

---

