---
title: "MTP device: folder management"
date: 2010-04-20
forum: Multimedia Software
---

### Post by ericmo on 2010-04-20
I own a Creative Zen, and have already successfully used both Rhythmbox and Gnomad to transfer files to it. But the problem is that I can't manage my "files" (not my "songs"). Banshee didn't work, and Exaile is not recognising my Zen (probably I'm missing some libraries or plugins). I've heard Exaile let's me manage the files in my MTP device, is that so?

Whenever I transfer any song to my Zen, it is transfered to my /music folder instead of being transfered into an /artist-album or an artist/album folder. It is kind of messy, I want to keep my files organized.

And if I try to move my files manually (from my HD to my device, or within my device) by letting Nautilus automatically mount my Zen as an external device, then it doesn't recognizes the files I've moved.

So, is there any workaround for me to manage my files in Zen without making them unrecognizable to it, say, using Rhythmbox? Or is there any other software that allows me to manage my files in such manner?

(From what I've googled, it seems that this is a general problem for most of MTP devices, hence the title of the thread.)

Cheers.

---

### Post by ericmo on 2010-04-20
Rhythmbox can show the location of a file.
When looking at a song in your HD, it shows something like file:///home/music/..., but when looking at a MTP device, the location is something like xrbmtp://"a five digit number"/mp3file. That is for any mp3 file, including those files that are in folders named in the format "/artist-album".

So, am I right to suppose that there is no workaround around that? Because that is the impression I'm getting, if by mounting the MTP Device the "actual" folders that are there aren't visible...

Also, I've found this thread in which the user used this command

```
mtp-connect --sendfile /video/directory/film.avi Video
```

to send a video to his MTP device (iriver Clix). I'm not sure that would work with mp3 files for Creative Zen, would that work? I'm afraid that I'll mess up what is already in my device by running "random" commands like that.

---

### Post by ericmo on 2010-04-20
I'm glad to be asking something that it's not trivial. I thought I'd be asking something so silly, but guess this is a real problem for people with mp3 players, because no one was able to give a solution yet (that's how trivial I thought that was, because it was so trivial in Windows).

Currently, I'm trying to workaround this by trying to sync Banshee with a folder or playlist, and hoping it will sort things out in folders. Banshee doesn't read the files in my Zen, but I've made copies of them and now I'm cleaning it up, so I hope it won't matter, otherwise I'll have to use a PC with Windows to transfer my stuff back.

---

### Post by ericmo on 2010-04-20
Well, that didn't work at all. I'm out of ideas.
Maybe I'll try something with Wine, I don't know...

---

### Post by ericmo on 2010-04-20
[http://tiagoboldt.net/blog/creative-zen-linux/](http://tiagoboldt.net/blog/creative-zen-linux/)

I've found that link above.
I used the commands there to mount my Creative Zen manually, through mtpfs:

```
sudo -s
mtpfs -o allow_other zen/

```And this to unmount:
```

fusermount -u /media/zen

```Then I can navigate in my Zen with Nautilus, and simply copy and paste files into it, and all files will be recognized. But I think there was some conflict with my USB Wireless Adapter (3com Office Connect), because my internet broke after I've run those commands. Rebooting solved this.

This should be the standard procedure, how come Ubuntu/Nautilus doesn't automatically mounts Creative Zen this way? The way it is automounted is misleading, because even though you can navigate through the files in it, none of the files you put in it aren't recognized.

---

### Post by ericmo on 2010-04-20
[B]That post above hasn't worked either.

[/B]I'm sorry. I thought things were going well, because the folders were being copied ok and the files were recognized. But when I re-checked the files in Nautilus, it had simply created empty folders (same names as the ones I tried to copy and paste) and thrown all mp3 files into /music folder, instead of sorting them in the empty folders that were created.

---

### Post by ericmo on 2010-04-20
And the mtpfs really does make my wireless adapter stop functioning...

---

### Post by ericmo on 2010-04-20
I'm trying Gnomad2 again.

Why does it allow me to create folders in my device if all files are transfered to /music folder? This is driving me mad!

---

### Post by ericmo on 2010-04-20
On Gnomad2 it is possible to create a folder, and then "data transfer" some mp3 files.

But then it doesn't transfer the tags with it. So you can manually create folders and manually re-tag all of the mp3 files you transferred to your MTP device. Isn't there an easier way to do that?

C'mon, am I the only minimally organized person in the world, who keep his music organized in folders? I don't get why not letting me choose where to put my files is considered to be a "feature" in Gnomad.

If I could at least rename the transfered files to "artist-songtitle", then it would at least organized in a minimal sense. But the way it is now is so messy. And ironically, Gnomad let's you rename files you transfer from device to HD like that. There is something wrong, or something that I'm really not getting...

---

### Post by Chronon on 2010-04-21
I am quite organized with my files, but I only use MSC devices.

I will note that many MTP devices do not permit any access to the files themselves (i.e. there's no file browser on the device).  I think that it's often considered that file names and paths are unimportant when using MTP.  I like having access to my file tree so I have always steered toward MSC devices.

---

### Post by ericmo on 2010-04-21
I'm not sure Creative Zen is compatible with MSC/UMS too, but I don't think it is. I guess they forced MTP to make DRM work in it.

About Gnomad2 and data transfer, if I data transfer music to my Zen, it will also lose length information, besides the tags. So I can't fast forward any song.

I'm guessing I'll have to settle with the mess, I'm almost giving up.
I'll try to use Zen with Virtualbox later, it's kind of annoying that my device is made to work properly in Windows only, but I'm guessing this might be the only way to make it work as I want. I have already found some posts saying that that works:

[http://www.linuxquestions.org/questions/linux-hardware-18/creative-zen-vision-m-and-vmware-404202/](http://www.linuxquestions.org/questions/linux-hardware-18/creative-zen-vision-m-and-vmware-404202/)

Anyway, I think there is no solution for this. Hope that at least will help someone else to see what won't work and try something else.

Cheers.

---

