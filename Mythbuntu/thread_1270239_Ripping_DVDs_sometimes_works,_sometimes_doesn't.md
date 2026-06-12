---
title: "Ripping DVDs sometimes works, sometimes doesn't"
date: 2009-09-19
forum: Mythbuntu
---

### Post by NautiusMaximus on 2009-09-19
Sometimes, if I put a DVD in my DVD drive, and choose "Import DVD" from the Optical disks menu, my Mythbuntu box rips the DVD, and a file turns up in the videos folder, where I can play it via Media Library/Videos.

So far, so good. That's what's supposed to happen.

Sometimes, however, I do the same thing, with the same options selected (I choose "perfect" for the image quality) and it whirs away for a while saying it's ripping it, and eventually says it's finished ripping it, but there's no trace of the file on my hard disk. It's not in the videos folder and the video manager can't see it.

Any ideas?

Thanks
NM

---

### Post by williammanda on 2009-09-19
You will have this problem due to the encrytion and it can not do every dvd. I too have the same problem when recording commercial dvd's. 1 or 2 out of 10 will not record.

---

### Post by NautiusMaximus on 2009-09-19
I suspect that's not the whole answer, because I successfully ripped a DVD today that failed to rip yesterday.

---

### Post by uncle hammy on 2009-09-19
FWIW, I have found the Myth rip feature to be EXTREMELY finicky.  I have found that almost any minor defect on the DVD will cause major issues with the DVD import process.

In fact, out of sheer frustration, I finally stopped using Myth's DVD Import altogether, and have had to resort to ripping my DVDs with DVDFab on a Windows machine, and moving the result over to my Myth box when it completes.

---

### Post by movieman on 2009-09-19
Note that K3B will rip DVDs in Ubuntu, so there's no need to mess around with Windows.

---

### Post by klc5555 on 2009-09-20
> **uncle hammy said:**
> FWIW, I have found the Myth rip feature to be EXTREMELY finicky.  I have found that almost any minor defect on the DVD will cause major issues with the DVD import process.

In fact, out of sheer frustration, I finally stopped using Myth's DVD Import altogether, and have had to resort to ripping my DVDs with DVDFab on a Windows machine, and moving the result over to my Myth box when it completes.

There are several ripping tools for Linux that have their various strong points and that you can use to supplement the touchy ripping tool in Mythtv. The standard one is dvdrip. For dvds that it can't handle (it has a lot of trouble with multi-language-track DVDs, as does the Myth ripper) Thoggen is a good choice (though there is a bit of quality degradation and the utility is really, really slow --frequently ca. 12 hrs to do a dvd). Finally, for some DVDs that none of the other tools seem able to rip successfully, like Disney, Sony, or some HBO ones, VLC can frequently do very smoothly, once you set it up properly.

All of these tools produce videos that the Myth internal player can play. Thoggen produces Ogg-vorbis files, so the .ogv file extension has to be added to the filter for viewable video files in Myth. Once files from these rippers have been added to myth via Video Manager, then mythtranscode can be used to build indexes for them, so that jumping forward and backward in the videos will work.

---

### Post by williammanda on 2009-09-20
> **klc5555 said:**
> Finally, for some DVDs that none of the other tools seem able to rip successfully, like Disney, Sony, or some HBO ones, VLC can frequently do very smoothly, once you set it up properly.


Please direct me to how vlc does recordings.
Thanks

---

### Post by klc5555 on 2009-09-20
> **williammanda said:**
> Please direct me to how vlc does recordings.
Thanks

Wow. I hadn't realized until now how truly awful the VLC documentation is. The VLC ripping guides easily findable on Google all seem to refer only to the Windows versions.

At any rate, VLC can rip essentially anything it can play. In the "Media" drop down, use the "Convert/Save" Option. Choose "disc", choose the correct title on the disc, click "convert/save". Then on the second menu check "file" (with or without "play locally"), choose a file name, choose the "encapsulation", video format and options, audio format and options, click "save", and away it chugs.

---

