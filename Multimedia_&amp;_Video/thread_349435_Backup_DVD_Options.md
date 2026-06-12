---
title: "Backup DVD Options"
date: 2007-01-30
forum: Multimedia &amp; Video
---

### Post by SteveF on 2007-01-30
I'm planning on converting some home videos to DVD (concerned about the tapes degrading).  I've decided to get a standalone DVD recorder (I'm not planning on doing a lot of video work, so looking at ease of use instead).

Unfortunately, I'm not convinced of the compatibility of different DVD recorders with other machines.  So my thought was, after recording the DVD, I would bring it to my computer and back it up to the hard drive for future use.

What I want to be able to do with the backup is:
1) I want the backup itself to be as quick a process as possible
2) If the DVD gets damaged or is incompatible with a player, burn a new DVD (once I get a DVD burner)
3) Way down the line, edit the movies by cutting scenes, merging separate movies into one movie, modifying the titles and possibly chapter marks.
4) Have the potential to be able to burn the movie to a new DVD format that could be created way down the line.

I'm thinking that my editing requirements can be handled by leaving the video in mpeg2 format.  I think I should be able to the limited cut and combines without re-encoding.

I came up with 3 options for backing up and am looking to see if there are any pros/cons to them (or some other alternative):
1) Use a command like dd to create an ISO from the DVD
2) Use a ripping tool like dvd:rip to create a folder of VOB files
3) Use a ripping tool like dvd:rip to create the mpeg files

I'm thinking that if I choose item 1 or 2, I can still get to the mpeg files (when I get around to editing) by futher ripping (mount the iso loopback or ripping the vob files).

Any thoughts/suggestions?

Thanks,

Steve

---

### Post by revertex on 2007-01-30
no need steps 1 and 2, use dvdbackup to decrypt css and create a folder of VOB files in just one step.

what about k9copy and dvdshrink?

---

### Post by SteveF on 2007-01-30
> **revertex said:**
> no need steps 1 and 2, use dvdbackup to decrypt css and create a folder of VOB files in just one step.

what about k9copy and dvdshrink?

I guess I was unclear.  I wasn't talking about doing all three steps.  I was talking about choosing to do just one of them and I was wondering if there were any pros/cons to storing as a backup either:
just the iso
just the vobs
just the mpeg

My first thought was just create ISOs since I only want to reburn right now and if I ever want to modify the files, I can mount it as loopback and then rip to mpeg.  But if the time to create the iso is not that much different than ripping straight to mpeg, then I might go the mpeg route (though that would require creating an ISO when I wanted to burn).

Steve

---

### Post by revertex on 2007-01-30
hmmm, storing just the mpegs seems the worst option, you will lose dvd structure, (i mean dvd menus navigation) subtitles and audio languages.

to watch dvd from a iso you don't need to mount, vlc and mplayer can play iso images.

---

### Post by SteveF on 2007-02-16
I think I decided upon  converting to VOBs instead og ISO (lose everything if file gets damaged) and vs mpg (lose DVD structure).

Next question:
Since these are DVDs I created on a standalone DVD recorder can I just copy the VIDEO_TS folder to my hard drive or am I better off using a ripping software like dvdbackup?  There's no encryption to remove so I would think copying files should be fine.

Any thoughts?

Thanks,
Steve

---

### Post by revertex on 2007-02-16
Steve, you can copy to your HD and watch with any player, go ahead.
The only issue is the file size.

---

### Post by SteveF on 2007-02-16
I thought I should be able to, but then I thought I read somewhere that ordering of files might be important and copying might not work.  But then again that may have had to do with creating the ISO.

I did use K3B to create an ISO and when I accessed that file, it seemed to work.

Thanks,

Steve

---

