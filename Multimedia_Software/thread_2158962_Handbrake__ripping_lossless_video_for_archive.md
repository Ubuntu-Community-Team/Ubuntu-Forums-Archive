---
title: "Handbrake / ripping lossless video for archive"
date: 2013-07-01
forum: Multimedia Software
---

### Post by maxxjr on 2013-07-01
I am thinking about ripping my DVD collection.

My strategy generally is:

Rip to lossless first, so that I can archive the DVD's.  I understand the size impact, but my "library" is relatively small.  These canbe streamed to my TV's, etc. or directly played, and I should have the best quality compared to the DVD sources.  This lossless collection can also later be used to create a compressed collection for mobile devices, as needed.

Having almost zero experience using the tools, am I missing anything with taking this approach?

---

### Post by SeijiSensei on 2013-07-01
There really isn't a "lossless" version of the content of a DVD.  It, too, is compressed using the old MPEG2 standard.  

I doubt you would discern much difference between the DVD original and an H.264-encoded version like Handbrake provides.  Remember that (NTSC) DVDs have a maximum resolution of 720x480.  Modern HDTVs have much more resolution than that (1920x1080).

Even people who capture "transport streams" or rip Blu-ray discs choose H.264 as the codec.

I'd just fire up Handrake, rip a single DVD, and see what you get.

If you want to archive DVDs, you might consider simply creating .iso images of the disks themselves.  K3b will do this if you have libdvdcss2 installed (which you'll need for any commercial DVD).

---

### Post by shantiq on 2013-07-02
i suppose here an understanding of lossless might be to keep absolutely everything as is on the DVD disc
So the best way to do this is to put disc in the drive open the folder and drag both video.ts and audio.ts  into a folder bearing the name of the disc

also can use```
     vobcopy -m
``` to mirror entire DVD to home folder
Then drag folder in vlc or Videos [Totem]where it will play a "lossless" version of the dvd; all is exactly as if playing the plastic disc minus whirring of the disc drive

That would be my understanding of lossless here
Failing that to do what Sensei advises   a 2Gb mkv is as good as original DVD on a normal-sized computer screen

**PS    **i would advise this route over the iso route since it leaves your VOBs visible by simply opening the folder; if say you wanted to extract the audio of a specific section or turn to a different format for say a portable player at a later stage   ;     but of course an iso IS a single file and does open in vlc and can easily be unpaacked if needed     so really a question of knowing what one wants from one's files

---

### Post by SeijiSensei on 2013-07-02
I suggested copying the DVD to an .iso image because it keeps the structure intact and creates just a single file.  Mplayer-based players like SMPlayer can play ISO images just as easily as they can play the actual DVD.  You double-click the .iso image and it starts.

---

### Post by maxxjr on 2013-07-02
I like the ISO idea.  Only problem, copy protection seems to get in the way.  

dd if=/dev/sr1 of=dvd.iso

...results in 10's of MB written to dvd.iso, before an I/O error is reported.

I have been researching this a bit this morning, and still have not found a clean solution.

---

### Post by maxxjr on 2013-07-02
Found the solution for the ISO.  It basically has to do with region codes.  Some application has to access the DVD player and register the region code.  Afterwards, dd works.

---

### Post by SeijiSensei on 2013-07-02
Commercial DVDs with CSS often cannot be copied simply with dd.  K3b, for instance, decodes the content using libdvdcss2 before writing the ISO image.

---

### Post by evilsoup on 2013-07-02
If you have libdvdcss installed, Shantiq's vobcopy line should work.

---

