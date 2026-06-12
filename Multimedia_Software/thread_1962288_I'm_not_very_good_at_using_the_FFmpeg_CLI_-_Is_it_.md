---
title: "I'm not very good at using the FFmpeg CLI - Is it frowned upon to use the WinFF GUI?"
date: 2012-04-20
forum: Multimedia Software
---

### Post by AlexOnVinyl on 2012-04-20
I've been struggling to learnt he FFMpeg CLI - as well as MEncoder CLI - theres a lot of things in the CLI that overwhelm me - but I feel guilty for using the GUI frontends rather than using the CLI because I'm on Linux.

I guess my question is, is it so bad to use the GUI of a program like FFMpeg for converting my multimedia rather than using the CLI (or atleast using it at this point in time)? Because I've had people tell me that if I don't understand it I shouldn't be using Linux.. :(

Is is possible to learn the CLI from the output that the GUI frontend puts out?

---

### Post by dniMretsaM on 2012-04-20
There is absolutely nothing wrong with using a graphical tool! GUIs exist for a reason. If you *want* to use the CLI, by all means. But GUIs are perfectly fine.

---

### Post by AlexOnVinyl on 2012-04-21
> **dniMretsaM said:**
> There is absolutely nothing wrong with using a graphical tool! GUIs exist for a reason. If you *want* to use the CLI, by all means. But GUIs are perfectly fine.

Thanks man. Made me feel better :)

---

### Post by Yellow Pasque on 2012-04-21
> Because I've had people tell me that if I don't understand it I shouldn't be using Linux..
I'm betting that these are the same people that find using Gentoo to build everything from source to be fun.

> Is is possible to learn the CLI from the output that the GUI frontend puts out?
Yes. That's probably easier than reading the huge ffmpeg manpage.

---

### Post by zombifier25 on 2012-04-21
I can't see why you should be flamed to death for using the GUI.
**Use what works.**

---

### Post by SeijiSensei on 2012-04-21
> **AlexOnVinyl said:**
> Is is possible to learn the CLI from the output that the GUI frontend puts out?

Yes.  If you can see the generated commands you can then look up the options that you don't recognize.

Running tools like ffmpeg or mencoder from the command line can be very helpful if you want to run batch conversions.  Say you have a directory of H.264 files in the MKV container that you want to convert to XviD in AVI.  You can write a quick script like this:

```
#!/bin/bash

for f in *.mkv
do
   NEWNAME=$(echo $f |  sed 's/\.mkv$/.avi/g')
   mencoder "$f" -o "$NEWNAME" -ovc xvid -oac mp3lame
done

```

(I omitted the options for simplicity.)  The script creates a new filename replacing ".mkv" with ".avi" and runs mencoder to create the file.  It iterates over all files in the current directory matching *.mkv. I enclosed the filenames in quotes in case they have embedded spaces.

One other GUI tool you might look at is [Handbrake]("https://launchpad.net/~stebbins/+archive/handbrake-releases").

---

### Post by FakeOutdoorsman on 2012-04-22
If you decide to use WinFF then you should stick with ffmpeg from the repository. I haven't checked WinFF in any recent Ubuntu release, but in the past its presets used syntax that is often incompatible with a compiled or more recent ffmpeg.

SeijiSensei's suggestion of Handbrake is a good one.

---

### Post by AlexOnVinyl on 2012-04-23
> **SeijiSensei said:**
> Yes.  If you can see the generated commands you can then look up the options that you don't recognize.

Running tools like ffmpeg or mencoder from the command line can be very helpful if you want to run batch conversions.  Say you have a directory of H.264 files in the MKV container that you want to convert to XviD in AVI.  You can write a quick script like this:

```
#!/bin/bash

for f in *.mkv
do
   NEWNAME=$(echo $f |  sed 's/\.mkv$/.avi/g')
   mencoder "$f" -o "$NEWNAME" -ovc xvid -oac mp3lame
done

```

(I omitted the options for simplicity.)  The script creates a new filename replacing ".mkv" with ".avi" and runs mencoder to create the file.  It iterates over all files in the current directory matching *.mkv. I enclosed the filenames in quotes in case they have embedded spaces.

One other GUI tool you might look at is [Handbrake]("https://launchpad.net/~stebbins/+archive/handbrake-releases").

I actually have Handbrake but it only outputs to .m4v or .mkv - which is disappointing, but Im willing to learn the CLI for FFMpeg - Thank you sensei for your help!

> **FakeOutdoorsman said:**
> If you decide to use WinFF then you should stick with ffmpeg from the repository. I haven't checked WinFF in any recent Ubuntu release, but in the past its presets used syntax that is often incompatible with a compiled or more recent ffmpeg.

SeijiSensei's suggestion of Handbrake is a good one.

FakeOutDoorsman - I got the FFMpeg from the **Medibuntu** repository and just recently got the **WinFF** from this repository:

> ppa:paul-climbing/ppa

---

