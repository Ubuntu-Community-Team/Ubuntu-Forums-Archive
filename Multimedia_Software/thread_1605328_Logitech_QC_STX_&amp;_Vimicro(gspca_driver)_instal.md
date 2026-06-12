---
title: "Logitech QC STX &amp; Vimicro(gspca driver) installation help? (need webcam &amp; mic) :("
date: 2010-10-25
forum: Multimedia Software
---

### Post by Ukarion on 2010-10-25
Hello! I just installed the new ubuntu (10.10) and I still haven't seen an "easy" way to install the driver for the Logitech Quickcam STX.. I found out that installing gspca driver will make the cam work fully.. but I have 0 clue how to install it! Yes Ubuntu does detect my web cam (Saw through Camorama.) 

I don't know how to install .tz.bz2 files and have  1% of knowledge on how ubuntu runs.

Thank you.

---

### Post by no2498 on 2010-10-25
type gspca in the package manager this is what come up for me 


source for the gspca v4l kernel module
The gpsca video for linux (v4l) driver, provides support for
webcams and digital cameras based on the spca5xx range of chips
manufactured by SunPlus, Sonix, Z-star, Vimicro, Conexant, Etoms,
Mars-semi, Pixart and Transvision.

The gspca driver is a rewrite of the well known spca5xx v4l kernel
module from the same author, Michel Xhaard.

This package provides the source code for the gspca kernel modules.
Kernel source or headers are required to compile these modules. For
basic install steps see /usr/share/doc/gspca-source/README.Debian.gz


hope that helps some


most webcams just work now days

look in sound&video for 
cheese webcam booth

try the cam in cheese first

---

### Post by Ukarion on 2010-10-26
> **no2498 said:**
> type gspca in the package manager this is what come up for me 


source for the gspca v4l kernel module
The gpsca video for linux (v4l) driver, provides support for
webcams and digital cameras based on the spca5xx range of chips
manufactured by SunPlus, Sonix, Z-star, Vimicro, Conexant, Etoms,
Mars-semi, Pixart and Transvision.

The gspca driver is a rewrite of the well known spca5xx v4l kernel
module from the same author, Michel Xhaard.

This package provides the source code for the gspca kernel modules.
Kernel source or headers are required to compile these modules. For
basic install steps see /usr/share/doc/gspca-source/README.Debian.gz


hope that helps some


most webcams just work now days

look in sound&video for 
cheese webcam booth

try the cam in cheese first

Hmm... my webcam shows up.. but i have no mic. When i go on skype and configure the webcam and audi.. I see my webcam as "USB camera (046d:08d7)(/dev/video0)"  but when i look under microphone.. i see nothing but PulseAudio Server (local). It says the same thing for Microphone, Speakers, and Ringing.

---

### Post by Ukarion on 2010-10-27
My mic is being detected :) so is my webcam :)

---

### Post by no2498 on 2010-10-27
glad you got it working

---

### Post by cmdematos on 2010-10-27
NOT SOLVED - I have a fresh install of 10.10, and there is no gspca driver in the distro under Synaptic Package Manager.

What PPA are you using to locate this?

Many thanks -

---

### Post by Ukarion on 2010-10-28
> **cmdematos said:**
> NOT SOLVED - I have a fresh install of 10.10, and there is no gspca driver in the distro under Synaptic Package Manager.

What PPA are you using to locate this?

Many thanks -

For the mic.. I found out ubuntu was detecting it with PulseAudio Volume control (Look for "PulseAudio Volume control" in Ubuntu Software Ceneter for download). I had to change the Input to the Logitech Mic and the output just keep it as the "Internal Audio" one.

As for the webcam.. Ubuntu just detected it (It's labled as USB Camera)




I still cant get my mic to work in skype, although i do have it correctly configured in PilseAudio Volume Control. 

(Output = Internal Audio, Input = Quickcam Communicate STX)


What can i do to get skype to detect my mic? It's still labeled as "PulseAudio (Local)" when i try to change the settings for the Microphone and I cant seem to change it to the Communicate STX mic..

Thank you.

---

### Post by no2498 on 2010-10-28
sorry i only help with the webcams
skype is a new ball game

---

### Post by Kyentei on 2010-11-09
@[Ukarion]("http://ubuntuforums.org/member.php?u=384402")
Installing pavucontrol (PulseAudio Volume Control) helped a lot. I also got my mic working in skype with it. You need to go to the Recording tab in pavucontrol while you are running a skype test call (or a normal phone call for that matter) and select which input device skype should be choosing from. ^.^

---

### Post by linuxisgoed on 2012-02-12
I have been using the Logitech QuickCam Communicate STX for a long time but only just discovered how to get the video working.

I am running ubuntu 11.04 64 bit with the classic view 

I have previously installed pulse audio to get the audio working and just discovered that by going to : system->preferences->main menu and then selected skype under internet ,click the properties button on the right and enter the following 

env LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

next to the browse button.
Then restart skype and test it by going options->video devices->test 
Let us know if it works :)

---

