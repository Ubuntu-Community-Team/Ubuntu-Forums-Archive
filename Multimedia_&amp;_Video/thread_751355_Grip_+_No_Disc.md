---
title: "Grip + No Disc"
date: 2008-04-10
forum: Multimedia &amp; Video
---

### Post by _godbout_ on 2008-04-10
Hi there,

I had to fight for one hour with grip to make it find my cdrom drive, and I'm wondering why, By default, the cdrom device taken is /dev/cdrom. I assume that it was not correct, so I changed it to /dev/cdrom0, /dev/cdrom1, /mnt/cdrom, /media/cdrom0, etc. etc... No one worked.
Then, I had a look in the fstab file, where I could find that my cdrom was actually /dev/hda. So I changed it, but without success. I had to use another program (vlc) to get the correct line, which was in fact /dev/scd0. Where is this /dev/scd0 coming from? How can I find it from the linux conf files? All other program for music works correctly, only grip had troubles to find it.

Thanks for the answers!

---

### Post by _godbout_ on 2008-04-10
Some different things I tried. At the beginning, I wanted to use Audio Cd Extractor, but I found it impossible to encode in mp3. I downloaded the gstreamer, lame, etc... I still can't extract in mp3...

Then I tried grip, so, and before extracting, it's ripping the cd into wav, which takes quite a while...

I definitely miss my CDEx from Windows that I loved so much!!!

---

### Post by logos34 on 2008-04-10
> **_godbout_ said:**
> Some different things I tried. At the beginning, I wanted to use Audio Cd Extractor, but I found it impossible to encode in mp3. I downloaded the gstreamer, lame, etc... I still can't extract in mp3...

Then I tried grip, so, and before extracting, it's ripping the cd into wav, which takes quite a while...

I definitely miss my CDEx from Windows that I loved so much!!!

Since Feisty ubuntu uses the libata scsi driver for sata AND ide devices, so drive designations will often change from /dev/hd* to /dev/sd* and /dev/scd0 for hard disk and cd/dvd, respectively.

The command

sudo lshw -C disk

should list scd0 as one of the possible logical names for the cdrom drive.

Check Grip>config>rip>options.  Maybe "Delay encoding until disc is ripped" is checked.  

You can run CDex on Wine in linux.

---

### Post by _godbout_ on 2008-04-11
Thanks a lot for your answer!

I'll have a look on that at home and let you know the results.

Thanks again,

---

### Post by _godbout_ on 2008-04-11
Ok, so I tried the sudo lshw command, the result is:

> 
PCI (sysfs)


and nothing more. It doesn't go back to the prompt, but just waiting...

Then, my "Delay encoding until disc is ripped" is unchecked.

I'm gonna check around if I can find something.

---

### Post by adam_kimber on 2008-05-04
> **logos34 said:**
> 

sudo lshw -C disk

should list scd0 as one of the possible logical names for the cdrom drive.



You are a star. The path /dev/scd0 worked perfectly for me in GRIP! I have just upgraded to Hardy and before it was using /dev/cdrom. Cheers!:KS

---

