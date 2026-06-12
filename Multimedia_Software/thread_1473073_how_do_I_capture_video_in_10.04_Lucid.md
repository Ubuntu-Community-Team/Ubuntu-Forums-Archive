---
title: "how do I capture video in 10.04 Lucid"
date: 2010-05-04
forum: Multimedia Software
---

### Post by charonred on 2010-05-04
How do I capture video from my JVC GR-DF470 MiniDV camera into 10.04 Lucid. 

PiViTi looks good for an editing app, and I've installed OpenShot as well, but neither have a way of capturing the video from a camera. 

I used Kino previously in 8.04 Hardy, but it was buggy at best in 9.10 Karmic; I've just installed it in 10.04, but capture keeps stopping after 2 or 3 seconds. 

I also tried kdenlive, but the audio capture has a lot of 'noise' that is louder than the voices on the tape, and once it finishes capturing video, it doesn't display a 'Save' dialogue as it is supposed to - so that wasn't very successful either.

So what can I use to capture video from a MiniDV Camera via Firewire.

---

### Post by no2498 on 2010-05-05
open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

look in applications sound & video
cheese webcam booth

try the cam in it first

hope this helps

---

### Post by charonred on 2010-05-10
Thanks, tried that - the Logitech webcam works ok in v4l2, but not in v4l1 (no device options);the problem is capturing video from a video camera, not a webcam, anyhow I tried playing back video in JVC camera, but not even detected or listed in devices.

---

### Post by Linuxforall on 2010-05-10
If your cam is not being detected, then you have no luck, however if your cam uses hdd or sd card to store movies, you can then connect it in PTP mode to see if it gets detected.

---

### Post by lisati on 2010-05-10
I'm not sure if the situation has changed in recent releases of Ubuntu, but there was a time where you had to tinker with firewire modules to get it to work properly with camcorders.

---

### Post by charonred on 2010-05-10
Camera is a MiniDV, though it has a card for photo storage, video is strictly tape. 

Same camera worked fine with Kino in Hardy 8.04; just connected the camera, captured the video, edited it, then exported file ready for DVD or Youtube ... easy

After Hardy things seemed to deteriorate with Firewire Camera support, despite there being millions of video cameras that use it.

I've managed to go totally Ubuntu on my PCs running only Dreamweaver in WINE because there is no Linux equivalent. I really like Lucid, but if I can't capture from a perfectly good MiniDV camera, then I may have to install Windows on another drive just to capture video from camera -  it's a shame Virtualbox doesn't support firewire ports, then I could avoid booting from one OS to another ... what a pain (grumble, grumble)

---

### Post by no2498 on 2010-05-10
? does fire wire vid come up as raw file type

---

### Post by no2498 on 2010-05-10
ubuntu put the, v4l and v4l2 together 

see if you can find this in synaptic
libv4l/v4l1compat.so
or may be
libv4l/v4l2compat.so

hope it helps

---

### Post by charonred on 2010-05-10
When I connect the camera, Firewire capture is Raw DV from memory - I'll double check in a while.
neither *libv4l/v4l1compat.so* or *libv4l/v4l2compat.so* show up in Synaptic, but they must be there for the Logitech webcam to work under them as per [previous post]("http://ubuntuforums.org/showpost.php?p=9271322&postcount=3")

I'll post back to confirm Raw DV in a while, I'm just doing my morning emails etc; and also setting up Win XP-SP3 on my previous PC; a Skt A board, Athlon 2600+ XP CPU, with 1Gb RAM - not super powerful, but should be adequate for DV capture. I'll also be able to use my Compro USB Digital TV tuner, and KWorld VHS to DVD adapter (tried for 18 months to get Compro & KWorld to work in Ubuntu without success) - that's all that the Win XP install will have to do, and with no updates etc, it might actually remain stable for a while ...

---

### Post by no2498 on 2010-05-10
type raw in synaptic look at what all comes up

---

### Post by no2498 on 2010-05-10
btw i use a pocket 3100 aiptek dv cam as my webcam but i use usb had to take the card out so it did not see it as a card reader

---

### Post by charonred on 2010-05-10
search Synaptic for 'raw' shows

libraw 1394-11 is installed

as are the following

alsa-utils
dcraw
libiec61883-0
libnl1
pulseaudio-utils
liaudiofile0
python-dbus
liblzma1
dbus-x11
libdbus-glib-1-2
libndesk-dbus1.0-cil
dvgrablibsndfile1
python-debian
libndesk-dbus-glib1.0-cil
libterm-readkey-perl
libxcb-event1
libxcb-atom1
libxcb-keysyms1
libxcb-aux0
libxcb-render-util0
libxvmc1
libdbus-1-3
exiv2
dbus
libparted0debian1
parted

---

### Post by no2498 on 2010-05-10
may be time you start trying things
you need raw as per what i do not know
the raw i do know you do need

im only pointing

---

### Post by no2498 on 2010-05-10
btw i can only get 1 cam that is plugged in at a time i need to unplug 1 of them

---

### Post by charonred on 2010-05-10
The Logitech webcam is USB, the JVC MiniDV is Firewire, so they shouldn't interfere with each other should they.

The problem seems to Kdenlive capturing, but not displaying a 'Save' dialogue when capture is finished, hence the capture is lost.

As for Kino it apparently hasn't been updated for a few years, so not much use.

---

### Post by ukripper on 2010-05-11
Try openshot. i have JVC minidv(also firewire) camera. It works fine with KDENLIVE and openshot. You got to play with the settings in kdelive to get the right settings

---

### Post by charonred on 2010-05-11
I already installed Open Shot hoping it could capture (apparently in will in a future release, but not yet), but it looks like a good editor.

Kdenlive does capture the video, it just doesn't provide me with a 'Save' dialogue - tried it several times with no luck - if it works with your JVC MiniDV, then I'll keep persevering with it.

In the meantime I've setup the older PC with a clean install of XP-SP3, so I'll just capture with Movie Maker and save in a shared folder, then go back into Lucid and grab the video from the network shared folder - lot of stuffing around, but I'll be able to get the videos, edit them and upload to Youtube etc.

---

### Post by ukripper on 2010-05-11
When i get home i'll give you the full settings for my JVC minidv and KDENLIVE, hope it works for you as well. I use 9.04 not 10.04 on the laptop I connect it on. I haven't tried it with 10.04 so far.

---

### Post by charonred on 2010-05-11
thanks, I'd appreciate that.

---

### Post by ukripper on 2010-05-11
ok just installed kdenlive on my lucid laptop. And it works just fine with my JVC minidv cam. Manage to capture raw dv video and then rendered it with progressive mode lossless mpeg4 without any problem. I am attaching screenshot of my capture settings as promised.

My cam model is GR-D820EK

---

### Post by charonred on 2010-05-11
Thanks, same settings as I have, but will try a little later this morning; I just have to catchup on some website work for a client first.

---

### Post by charonred on 2010-05-11
Ok, now here's something strange; I can't connect in kdenlive until I run the following script in Terminal, only then is the camera now recognised.
```
sudo chmod 666 /dev/raw1394
```

It used to be like this with Kino, but not kdenlive, so something has gone awry :confused: Any idea how I can change this permission to permanent?

Anyhow, once I had the camera connected, I tried a different tape (shorter clip) this time, but I still had the same problem; I stop recording (capture) but no dialogue box comes up, however when I 'disconnect' from capture source, a dialogue box comes up offering the choice of 'discard' or 'import' - so after importing I can now save the file and 'render' it. Now I can work on it in Open Shot :) I'll try PiTiVi later.

---

### Post by no2498 on 2010-05-11
you need to make a new ? for this it will be faster
sudo chmod 666 /dev/raw1394
It used to be like this with Kino, but not kdenlive, so something has gone awry  Any idea how I can change this permission to permanent?

glad to see your getting some place

---

### Post by ukripper on 2010-05-12
better solution would be to add udev rule for video group. 

follow below solution taken from this wiki - [https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire)

**_[COLOR="Black"]Method1[/COLOR]_**
Ubuntu 10.04 terminal:
```
echo 'KERNEL=="raw1394", GROUP="video", MODE="0664"' |
sudo tee /etc/udev/rules.d/50-raw1394.rules
&& sudo restart udev
```

Then unload and reload raw1394,

```
 modprobe -r raw1394 && modprobe raw1394
```

and type in a terminal:

```
sudo /etc/init.d/udev restart
```

Next time when you restart you won't have to keep changing permissions.


**_Method2:_**
Alternatively, you can add the the command ```
chmod 666 /dev/raw1394
``` just before "exit" in file /etc/rc.local. It will execute this command everytime you reboot your machine.  

Alternate solution(method2) will only work if your cam is plugged in during boot up but udev solution (method 1 above) doesn't need cam to be plugged in at boot. Therefore, I'd prefer to go with udev method.

---

### Post by ukripper on 2010-05-12
> **charonred said:**
>  I stop recording (capture) but no dialogue box comes up, however when I 'disconnect' from capture source, a dialogue box comes up offering the choice of 'discard' or 'import' - so after importing I can now save the file and 'render' it. 

That is how new kdenlive works. You capture the stream/video from dv and then import it in the timeline to render it. It is professional way of doing things. I like the new kdenlive, have to admit. Much faster rendering.Pitivi is just useless, no idea why it was even included in default lucid install.

---

### Post by charonred on 2010-05-12
thanks for script, first part was ok, but when I did second part I got a fatal error
```
~$ modprobe -r raw1394 && modprobe raw1394
FATAL: Error removing raw1394 (/lib/modules/2.6.32-22-generic-pae/kernel/drivers/ieee1394/raw1394.ko): Operation not permitted

```

---

### Post by ukripper on 2010-05-12
> **charonred said:**
> thanks for script, first part was ok, but when I did second part I got a fatal error
```
~$ modprobe -r raw1394 && modprobe raw1394
FATAL: Error removing raw1394 (/lib/modules/2.6.32-22-generic-pae/kernel/drivers/ieee1394/raw1394.ko): Operation not permitted

```
sorry my mistake use sudo:

```
sudo modprobe -r raw1394 && sudo modprobe raw1394
```

---

### Post by charonred on 2010-05-12
thanks heaps, rebooted  and it works a treat, camera is detected straight away :) 

now to see if I can capture and save this video - it's about half an hour long; the one I saved before was only 4 minutes

---

### Post by ukripper on 2010-05-12
> **charonred said:**
> thanks heaps, rebooted  and it works a treat, camera is detected straight away :) 

now to see if I can capture and save this video - it's about half an hour long; the one I saved before was only 4 minutes

Nice one. You will need to render it in a different format and make sure when you rendering for PC use or online web use "force progressive", this will de-interlace minidv capture. you won't see those jarred horizontal lines after de-interlacing

---

### Post by charonred on 2010-05-12
hmmm, well went through the whole process of capturing, but after disconnecting, no discard or import dialogue box came up, so not able to save - I'm thinking there's something 'wrong' with that tape. 

This particular video was recorded on a friends Panasonic, but when I play it back on mine, sometimes there is sound, sometimes there isn't ... maybe the heads are aligned a little different, and that might be causing the capture/save problem ?? I captured it ok in Windows Movie Maker, but again no sound. The 4 minute video I captured earlier was same brand of tape, but was recorded in my camera and has good sound.

I think I'll go over friends and play it back on theirs, and if there is good sound, then I'll dubb it across to a new tape in my camera (sound records fine on each camera) :confused:

---

### Post by ukripper on 2010-05-12
> **charonred said:**
> 
I think I'll go over friends and play it back on theirs, and if there is good sound, then I'll dubb it across to a new tape in my camera (sound records fine on each camera) :confused:

Seems like Tape is playing up. Copy from one tape to another would do the trick

---

### Post by charonred on 2010-05-12
thanks all for your input, I'll post back when I've figured this tape/capture problem out.

---

### Post by mrbabinga on 2010-06-12
dvgrab will do it. Haven't used it in awhile but it worked fine. Kino will access firewire. I believe it uses dvgrab.  You may have to set permissions to access the firewire port.

Good luck with it.

---

### Post by foxy123 on 2010-08-14
I can capture video using this advice from [http://www.kinodv.org/](http://www.kinodv.org/) 
```
How to fix FireWire capture in Ubuntu 10.04 (Lucid)
( 26.05.2010 22:36 )
In a Terminal, enter 'gksu gedit /etc/modprobe.d/blacklist-firewire.conf'.
Uncomment (remove the #-character at the beginning of the line) ohci1394, sbp2, dv1394, raw1394, and video1394. Then, comment (add a #-character to the beginning of the line) out the firewire-ohci and firewire-sbp2 lines. Save and Quit gedit.
Next, run 'sudo update-initramfs -k all -u' and finally reboot.

Now, when you plugin your camcorder, it should have permission by default (unlike in the past). Vote for this to become the default by indicating that this bug affects you. 
```

I can start capturing after reboot but as soon as I stop the camera or pause it stops working as Kino cannot find my camera. I have to reboot to be able to capture video again.

---

### Post by Dai777 on 2010-09-18
> **foxy123 said:**
> I can capture video using this advice from [http://www.kinodv.org/](http://www.kinodv.org/) 
```
How to fix FireWire capture in Ubuntu 10.04 (Lucid)
( 26.05.2010 22:36 )
In a Terminal, enter 'gksu gedit /etc/modprobe.d/blacklist-firewire.conf'.
Uncomment (remove the #-character at the beginning of the line) ohci1394, sbp2, dv1394, raw1394, and video1394. Then, comment (add a #-character to the beginning of the line) out the firewire-ohci and firewire-sbp2 lines. Save and Quit gedit.
Next, run 'sudo update-initramfs -k all -u' and finally reboot.

Now, when you plugin your camcorder, it should have permission by default (unlike in the past). Vote for this to become the default by indicating that this bug affects you. 
```

I can start capturing after reboot but as soon as I stop the camera or pause it stops working as Kino cannot find my camera. I have to reboot to be able to capture video again.

done this but still not picking up my camcorder. WTF doesn't Ubuntu pick up fire wire as standard. Surely this is an oversight by the Ubuntu people.

---

