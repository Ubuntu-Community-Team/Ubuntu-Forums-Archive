---
title: "BluRay to mpg"
date: 2015-02-08
forum: Multimedia Software
---

### Post by michael-piziak on 2015-02-08
Can a BluRay file be converted to mpg?

I tried WinFF but it doesn't support such a conversion.

What I know about the file is that it is:  Matroska video (video/x-matroska)

It's also:  codec H264  video   and codec DTS audio with surround 5.1

Finally, the file name ends with "bluray.x264.amiable.mkv


The file will play on the Ubuntu computer; however, I want to move the file to a USB thumbdrive and plug it into an HD tv and play it.


Also, I tried to dump the file to a usb several times without converting, result was:  error splicing file, file to large.    The file is about 5.9 gigs.   ?

---

### Post by Rob Sayer on 2015-02-09
It's not actually a "blu ray" file.  It's been re encoded from a blu ray source.  6G is a rather large file but BR video is much bigger.

What I don't quite get is why you want to convert to mpg.  I think avidemux would do that, but why mpg?

Have you looked at the docs for your TV to see what video formats it works with when you use the USB port for input?  Note that's not the file extension ... that's just the container ... but the actual format.  The format you'd usually find in a .mpg file isn't what I'd expect most TVs to require.

If you want to get into this kind of stuff the first thing you need to do is install mediainfo-gui so you can actually see what format/codec was used for your video files.  It's an essential program IMO for media.

Your TV may actually accept the format as is.  If you don't have any big enough USB sticks you can split mkv files with mkvtoolnix.

If you have to re encode to be able to use the USB port, avidemux is actually the converter I'd use.  SOmetimes it chokes on the audio format and then I convert that with audacity and import that file into avidemux.

One thing you have to realize about encoding video though ... unless you have a pretty powerful computer you can easily end up spending more time encoding a video than watching it.  The fast encoding settings don't give you very good quality.

---

### Post by michael-piziak on 2015-02-09
Thanks for your detailed reply.

The tv I'm using is a Sony Bravia.  I have been converting youtube clips to mpg1 or mpg2 and putting them on the usb stick and watching them - using WinFF.

The file I have now may work in the tv; however, each time I attempted to copy it onto 2 different usb thumb drives I would get an error mid way through the copy - both usb thumb drives are more than large enough.

Thanks again for your reply.

---

### Post by dustin19 on 2015-02-09
> **michael-piziak said:**
> Thanks for your detailed reply.

The tv I'm using is a Sony Bravia.  I have been converting youtube clips to mpg1 or mpg2 and putting them on the usb stick and watching them - using WinFF.

The file I have now may work in the tv; however, each time I attempted to copy it onto 2 different usb thumb drives I would get an error mid way through the copy - both usb thumb drives are more than large enough.

Thanks again for your reply.

sorry to butt in, how are your flash drives formatted? if it is fat32 that's the problem. that drive format has a max filesize of i think 2 gb

---

### Post by michael-piziak on 2015-02-09
I have formatted the 8gb and even the 128 gb thumb drives with FAT (compatible with all systems).

What format would you suggest I try - ?

The TV must be able to read it - I dunno if the tv could read a linux format.

---

### Post by dustin19 on 2015-02-09
exfat or ntfs.
i have used ntfs on tvs, it has worked so far. (cant say it works on all makes/models since i haven't used all.)
exfat... never used but i hear it works.

---

### Post by michael-piziak on 2015-02-09
> **dustin19 said:**
> exfat or ntfs.
i have used ntfs on tvs, it has worked so far. (cant say it works on all makes/models since i haven't used all.)
exfat... never used but i hear it works.

What utility could I use to format in ntfs or tvs ?

Currently, I can only format in Fat  or:
linux ext2
or linux ext4
or encrypted (compatible with linux fat)

Also, is there a program to split the files up?   I tried U Splitter but it didn't work right for me.

---

### Post by Yellow Pasque on 2015-02-09
What are you using to format? Gparted?
You do have ntfs-3g package installed, correct?

---

### Post by dustin19 on 2015-02-10
hey mike
sorry for the late response, the easiest way to format the flashdrive in ntfs is with a windows machine. i happen to use windows and linux both.
also file splitters, in my experience, can make the split video unplayable. the original will be fine but the output files may have issues unless recombined. again just me experience, ymmv
i am not sure (since i have never needed to look) but there may be linux packages that allow formatting in ntfs. sorry i could not be more helpful

---

### Post by mc4man on 2015-02-10
Any current Ubuntu release can format to ntfs  & it should be available in the Disks app (ntfs-3g is inc. in the default install

---

### Post by michael-piziak on 2015-02-10
> **mc4man said:**
> Any current Ubuntu release can format to ntfs  & it should be available in the Disks app (ntfs-3g is inc. in the default install


I downloaded gparted and can do it in ntfs.

Just curious though, what is already on Ubuntu 12.04 lts that can format a flash drive in ntfs - Disk Utility ???

---

### Post by Yellow Pasque on 2015-02-10
Forget the ntfs. Sony doesn't list it as supported:
[http://esupport.sony.com/US/perl/support-info.pl?info_id=799&mdl=KDL46EX723](http://esupport.sony.com/US/perl/support-info.pl?info_id=799&mdl=KDL46EX723)

```
sudo apt-get install exfat-utils mediainfo libav-tools
```
Make sure exfat-utils package is installed and format the drive to that.

It doesn't look like the TV will play a .mkv file, so you will have to dump your video into an mp4 container. Something like this could work:
```
avconv -i bluray.x264.amiable.mkv -c:a copy -c:v copy outputfile.mp4
```

---

