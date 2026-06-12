---
title: "video crashes player"
date: 2009-07-11
forum: Multimedia Software
---

### Post by iprolonged on 2009-07-11
Running 9.04 on a Dell desktop.

Trying to play a ripped AVI file, it crashes VLC, MPlayer and Movie Player - this is very frustrating, as I can't even see error messages!

Is there some wizardry I can run from the terminal to see what's going wrong?

Thanks in advance.

Dave

---

### Post by khelben1979 on 2009-07-11
What happens if you are trying to play other avi files or movies in other formats?

There might be that the players are experiencing trouble with it's video codecs. Adding [Medibuntu]("http://en.wikipedia.org/wiki/Medibuntu") to your /etc/apt/sources.list file would be to recommend.

---

### Post by iprolonged on 2009-07-11
Thanks khelben1979 - unfortunately it's with every .avi I've tried :( I'll try with some .mpeg and see if there's any difference...

I followed the instructions at [https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories) so I think I have Medibuntu added - do I need to run apt-get update for it to take effect?

Dave

---

### Post by HappyFeet on 2009-07-11
> **iprolonged said:**
> 
do I need to run apt-get update for it to take effect?

Dave

It can't hurt.

---

### Post by andrew.46 on 2009-07-12
Hi iprolonged,

> **iprolonged said:**
> 

Trying to play a ripped AVI file, it crashes VLC, MPlayer and Movie Player - this is very frustrating, as I can't even see error messages!

Is there some wizardry I can run from the terminal to see what's going wrong?


Well, you could run the file with MPlayer from the commandline with the following syntax:

```
mplayer -v *myfile.avi*
```

With the substitution of the real name and path to your file instead of *myfile.avi*. Then post the complete terminal command and output here, there should be a few hints in there.

All the best,

Andrew

---

### Post by iprolonged on 2009-07-12
Thanks Andrew, gave that a whirl. Interestingly, I now have audio, but no video?!

Output attached, thanks guys.

Dave

---

### Post by olae on 2009-07-12
Hi. 
I ve the exactly the same problem. For a fraction of a second a error msg pops up and says "skipped frame 8" or similar. Any video player, any kind of file, except youtube streams. I have a Compaq nc6320. I did install the medibuntu. I get audio and numerous lines of such msgs, after starting mplayer from the command line:

"X11 error: BadAlloc (insufficient resources for operation)1.2% 2 0 
Type: 0, display: 0xa935690, resourceid: 4600006, serial: d4"

Thanks for your help, the message lead me to that page. Will see if it helps me.

[http://forums.fedoraforum.org/showthread.php?t=104445](http://forums.fedoraforum.org/showthread.php?t=104445)

---

### Post by andrew.46 on 2009-07-13
Hi iprolonged,

> **iprolonged said:**
> Thanks Andrew, gave that a whirl. Interestingly, I now have audio, but no video?!

Perhaps you could also try:

```
mplayer *-vo x11* dvd.avi 
```

And if this works it should also work as a video output for vlc.

Andrew

---

### Post by iprolonged on 2009-07-14
Andrew, that almost worked: I now have video, but no audio, using mplayer! :)

Also gave VLC a go, got the following error:

libdvdread: Can't stat x11
No such file or directory
libdvdnav: vm: failed to open/read the DVD
[00000413] access_directory access error: x11: No such file or directory
[00000413] access_file access error: cannot open file x11 (No such file or directory)
[00000407] main input error: open of `x11' failed: could not create access: no suitable access module
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82

I think I might just cut my losses at this stage and just do a clean re-install, I've nothing on the machine anyway - advantage of working from the Cloud :)

Thanks for your help.

Dave

---

