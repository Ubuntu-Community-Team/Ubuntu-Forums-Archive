---
title: "to copy a music cd"
date: 2007-10-28
forum: Multimedia Production
---

### Post by stevetxt on 2007-10-28
I'm looking for the easiest way to make a backup copy of a music cd with Gutsy.  There seems to be no single program with the option "make copy of cd".  With Serpentine I can extract the songs into a file.  By default they came out "ogg" format.  Is this ok for my purpose?

Then I am stumbling trying to use Serpentine to burn the new cd.  I can click "add" and find the file with the tracks, but it's not clear how to add them all.  I can add one at a time by selecting it and opening it.  This seems like a lot of fuss, plus I don't know if the format will come out right for ordinary players.  

I've searched for simple information on how to do this but have had no success so far.  Can anyone either advise me how to do it or point to some clear description of the process?

Thanks.

---

### Post by nalmeth on 2007-10-28
When the disc mounts on your desktop, right-click it, and select "Copy Disc".

If you're copying your CD's to your PC, I recommend you not use OGG or MP3. Those are lossy codecs, and you will lose some integrity every time you convert your songs. 

If you want to copy using Sound Juicer, go into the preferences, and choose either WAV or FLAC.

FLAC is a lossless audio codec that will compress your files to half the size of WAV, with essentially the same quality. This is what I do when adding my CD's to my collection.

For future reference, when you use Serpentine, I believe it converts the files back to WAV so they can be played in CD/DVD-Players.

---

### Post by trak87 on 2007-10-28
Assuming this is for personal backup... Easiest way is the command line. I haven't tried this in a while, but I think this works. Open a terminal, insert your cd and run this:

```
cdparanoia -wB -d/dev/cdrom
```

You'll end up with a bunch of wav files, one for each track. To see the results, type **ls -l *.wav** . Next, insert a blank cd and run this:

```
wodim -sao -v -pad speed=16 -dev=/dev/cdrom -audio *.wav
```

Simple enough? You can also use k3b.

---

### Post by daengbo on 2007-10-29
If you want to copy the exact format of the CD, you need to right click on the CD icon and choose "Copy Disc" then choose "Copy Disc to File Image." This will give you an image which you can right click on and choose "Write to Disc" when you want to make a new disk.

If these are all audio CDs and space is a factor for you, you can use Sound Juicer to rip the CD to FLAC. Go into the Sound Juicer preferences and change the default fie format to FLAC. FLAC is a lossless codec, so you can transfer from CD -> FLAC -> CD without any degradation of sound. FLAC will cut off about 40% of the size of a .wav.

When you want to make a new CD with the FLAC files, simply open Serpentine Audio CD Creator and add the CDs FLAC files. Write to disc, and presto, you're done.

---

### Post by stevetxt on 2007-10-29
Thanks.  This answers my questions.

---

