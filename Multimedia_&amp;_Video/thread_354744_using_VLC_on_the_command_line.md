---
title: "using VLC on the command line"
date: 2007-02-06
forum: Multimedia &amp; Video
---

### Post by ac251404 on 2007-02-06
Hi. I am trying to start using VLC to encode my .avi files to .wmv files. I need them in wmv format because I need to stream them to my xbox360 (via a virtual machine running xp-mce). I figured out how to do this in VLC using the Wizard but now I want to write a ruby script to do it all for me (monitoring a folder for new files) and I am not sure how to form the command line arguments.

In the wizard I select the following:

Transcode/Save to File

Select my source file (source.avi)

Transcode video with options: codec = WMV 2, Bitrate = 1024
Transcode audio with options: codec = MPEG Audio, Bitrate = 192

Encapsulation format = ASF

File to save to: newvideo.wmv


So could someone help me out in figuring how to do this conversion from the terminal?

Thanks

---

### Post by ac251404 on 2007-02-06
Well I got as far as this:

```

vlc -vvv source.avi --sout '#transcode{vcodec=wmv2,vb=1024,acodec=mpga,ab=192}:standard{access=file,dst=testout.wmv,mux=asf}'

```

Which appears to run okay but is only encoding the audio. Any ideas?


EDIT: Okay in case anyone else comes across this - the above was absolutely fine except the vcodec is case sensitive and had to be WMV2. So now everything is working.

---

