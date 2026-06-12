---
title: "Creative web cam not working with 9.10"
date: 2009-12-29
forum: Multimedia Software
---

### Post by rhjs on 2009-12-29
I am new to Ubuntu I have installed 9.10 on a PC running XP.

I  have installed a Creative Live! Cam Skype edition web cam which worked with XP.
I have tested the webcam on Ubuntu with Cheese and it works. Too much red colour, but it works.

The web cam does not work with Skype. 
I emailed Skype and they replied :-

Make sure to install the following software packages.

Qt 4.2.1+
D-Bus 1.0.0
Libasound2 1.0.12
PulseAudio 0.9.10+ (optional)
PulseAudio 0.9.15+(optional recommended)

Also that driver info could be found at [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)


It seems a lot of software. I have no idea what this software does,or how to use it.
I have searched the Synaptic Package Manager and the Ubuntu Software Centre 
and it has not been recognised.

Can anybody help please.

---

### Post by premamotion on 2009-12-29
Here is the answer:

[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

You need to have installed theese modules: 

ov51x-jpeg-source_1.5.9-1
libv4l1 
gstreamer0.10-ffmpeg

after that, start skype with the command

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

Cheers!

---

### Post by rhjs on 2009-12-30
Thanks for the info.

I now have video in the Skype video test page.The colour seems ok but dark.

I see that the video will not start up with the Skype program.
I have to run the terminal command line and keep the terminal running while Skype is running.
If I stop the terminal I stop the video.

Is this as you would expect.

Thanks again.

---

### Post by premamotion on 2009-12-30
No need to keep opened the terminal window... just make a laucher pointing to a script, like skype.sh and open it.

The script should be

[B]#!/bin/sh
sudo artsdsp -m skype
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype[/B]

and make sure that the script property is executable!

---

### Post by rhjs on 2010-01-01
Ok so far.It seems to work.

This is a re-learning curve.I hav'nt used shell commands since the days of msdos.

Which text editor do you prefer?
I wrote the script file in nano but notice that ubuntu later found it via gedit.

I'll have to search the web for editor manuals.

Thanks again and best regards.

---

### Post by arugge on 2010-01-08
I'm having trouble writing the script. I follow what you say and save it as a skype.sh file, then when i launch the cam dosn't work? Any suggestions?

---

### Post by premamotion on 2010-01-08
> **arugge said:**
> I'm having trouble writing the script. I follow what you say and save it as a skype.sh file, then when i launch the cam dosn't work? Any suggestions?

Did you made the script executable?

After that, you can point to this script with a laucher.

---

### Post by arugge on 2010-01-08
I think i did. I right clicked on it and then in permission enabled it to allow it to execute as a program. I probably did something wrong though so tell me what else i need to do and how exactly the sript should look.

---

### Post by fishtoprecords on 2010-01-09
> **premamotion said:**
> [B]#!/bin/sh
sudo artsdsp -m skype
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype[/B]


What does the "artsdsp" do?
I can't find man pages for it.

Thanks

---

