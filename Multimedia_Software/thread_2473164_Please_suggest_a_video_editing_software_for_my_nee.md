---
title: "Please suggest a video editing software for my need(s)"
date: 2022-03-25
forum: Multimedia Software
---

### Post by jmichaels29 on 2022-03-25
I need a GUI piece of video editing software that basically allows me to, say, take an hour video and select a small segment (let's say 2 minutes), to take (edit) that segment out and save it as its own individual little video (file)... 
 
Something simple to use would be great....  Preferably, something in the Ubuntu Software center...
 
Regards,

MJ

---

### Post by kc1di on 2022-03-26
Hi MJ,
I believe that kdenlive would do what you want and it will run well in any desktop. 
[https://kdenlive.org/en/]("https://kdenlive.org/en/")
Sould be in the repository.
Good luck.

---

### Post by Kanehekili on 2022-05-01
I've written [VideoCut]("https://github.com/kanehekili/VideoCut") for fast cutting (similar to VidCutter) supporting Kubuntu (QT). A [private ppa]("https://launchpad.net/~jentiger-moratai/+archive/ubuntu/mediatools")  for "focal" and "jammy" can be installed . It supports many codecs, is  based on mpv and ffmpeg and has its own fast muxer (which makes smoother  cuts than ffmepg)

A direct install can be used for "bionic" with the "opencv" backend.

---

### Post by TheFu on 2022-05-01
I've looked for programs like this for years. There are all sorts of tools for this.  Heck, you can use handbrake to clip the beginning and end off any video if you like.

Most popular video editors like OpenShot and KDenLive will re-encode the video, losing quality in the effort. Both are very heavy programs and have a huge list of features that take multiple tutorials to learn, IME. If you need transitions, titles, credits, then those are probably what you want.  I've not been able to try **VideoCut**. It is on my list.

I have been using **LosslessCut** (which is available as an AppImage) for a few months. It is replace some commercial MS-Windows software I'd been using and upgrading for over a decade. It isn't perfect, but it does meet your stated needs. It supports mplayer EDL files. I have comskip create the EDLs to premark where commercials are located in recorded TV, then pull the video and EDL into LosslessCut for quick validation before having it export the cuts and merge them into a single file. For the types of cutting I do, I'm 100% positive that mkvmerge would do a faster, more efficient job than ffmpeg. I used a script to create an mkvmerge command for a few years. I still use this today for very quick edits. It is at least 2x faster than ffmpeg. At least.

**VidCutter** might work too. It supports a number of EDL formats, which can be useful, but it stopped working for me due to missing dependences in the snap package.

You could also use **mkvtoolgui** or any of the ffmpeg GUI tools. They are GUIs, but would require entering start/end times manually, so they aren't really GUIs  - more like command option entry panels.

LosslessCut is very simple. Takes just a few minutes to be productive. There are caveats, like it doesn't support frame-accurate cuts. If that is important to you, it is still worth checking out, since usually, the allowed cut location will be at a scene change position.

To find more options, if you search with "VidCutter vs" in any search engine, I bet some comparison articles will be found.

---

