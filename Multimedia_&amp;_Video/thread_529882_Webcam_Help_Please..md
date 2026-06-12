---
title: "Webcam Help Please."
date: 2007-08-19
forum: Multimedia &amp; Video
---

### Post by BnetTheAwesome on 2007-08-19
I'm using a Logitech Quickcam for Notebooks Pro. I'm using Feisty. It is being detected but won't display in any programs (XawTV, Camorama etc.). Any suggestions? I'm trying to start a Youtube show soon, but I need this webcam working.

---

### Post by gatman3 on 2007-08-19
I just went through this last week.  I was not able to get the QuickCam for Notebooks Pro to work at all.  If you search, it seems that there are perhaps some experts who have figured it out, but not me.  I took mine back and got a QuickCam for Notebooks Deluxe, and it worked great with Feisty right out of the box.

---

### Post by BnetTheAwesome on 2007-08-19
> **gatman3 said:**
> I just went through this last week.  I was not able to get the QuickCam for Notebooks Pro to work at all.  If you search, it seems that there are perhaps some experts who have figured it out, but not me.  I took mine back and got a QuickCam for Notebooks Deluxe, and it worked great with Feisty right out of the box.
I want it to work and not have to take it back in. Does anyone here know how to make it work?

---

### Post by gatman3 on 2007-08-19
What's the usb id?  (type "lsusb" in a terminal window, look for something like 046d:08cb).

It seems that there might be multiple models of the QC for Notebooks Pro.  Some earlier posts show that some folks were able to get it working with Ekiga using the UVC driver with the 08c3 model.  I had the 08cb model, and I tried the UVC driver and never got it working.

You might just try reinstalling the UVC driver, which is how the others got it to work.  Here is the link to the linux-uvc driver:

[https://linux-uvc.berlios.de/](https://linux-uvc.berlios.de/)

According to that page, your webcam might be supported (check the usb id and compare it to their list of supported devices).

Didn't work for me, but maybe you'll be more lucky.

---

### Post by BnetTheAwesome on 2007-08-19
> **gatman3 said:**
> What's the usb id?  (type "lsusb" in a terminal window, look for something like 046d:08cb).

It seems that there might be multiple models of the QC for Notebooks Pro.  Some earlier posts show that some folks were able to get it working with Ekiga using the UVC driver with the 08c3 model.  I had the 08cb model, and I tried the UVC driver and never got it working.

You might just try reinstalling the UVC driver, which is how the others got it to work.  Here is the link to the linux-uvc driver:

[https://linux-uvc.berlios.de/](https://linux-uvc.berlios.de/)

According to that page, your webcam might be supported (check the usb id and compare it to their list of supported devices).

Didn't work for me, but maybe you'll be more lucky.

Mine's a 046d:08c3 webcam. I'll try installing the UVC and seeing if it works.

---

### Post by BnetTheAwesome on 2007-08-19
Not working. X( Ekiga said my driver did not support their color pallete. Please help anyone. I need serious help here. No one seems to respond here. (Except for gatman3)

---

### Post by gatman3 on 2007-08-19
Yes, I got the same error from Ekiga with the 08cb model.

I noticed in this recent thread:

[http://ubuntuforums.org/showthread.php?t=241681](http://ubuntuforums.org/showthread.php?t=241681)

that someone got your 08c3 model working just by reinstalling the drivers... again.  You might try just repeating the process a few times before you give up on UVC.

I also double checked the abandoned PWC (Philips Web Cam) driver page, and it clearly states that it does not support the 08c3 model, so don't waste your time there.

Not to be too much of a wet blanket, but the other problem I foresaw is that the UVC drivers only support Video4Linux 2, and I don't think there are too many applications supported yet (Ekiga is one of the only ones, and I haven't used it much but I don't think it captures video; it's just a telephony client).  I just checked Cinelerra, and it appears to only support V4L1.  Point is, I'm not sure what app you can use to capture video with the UVC drivers even if you get them to work with your camera (you mentioned YouTube as your ultimate goal).  Anyone else know of a video capture application that works with Video4Linux 2?

---

### Post by gatman3 on 2007-08-19
On reading that thread I pointed you too a little more carefully, it looks like there are a few files that Fingolfin supplied as a patch or something (read his first post).  Try following his directions in the first post of that thread.

---

### Post by BnetTheAwesome on 2007-08-19
> **gatman3 said:**
> Yes, I got the same error from Ekiga with the 08cb model.

I noticed in this recent thread:

[http://ubuntuforums.org/showthread.php?t=241681](http://ubuntuforums.org/showthread.php?t=241681)

that someone got your 08c3 model working just by reinstalling the drivers... again.  You might try just repeating the process a few times before you give up on UVC.

I also double checked the abandoned PWC (Philips Web Cam) driver page, and it clearly states that it does not support the 08c3 model, so don't waste your time there.

Not to be too much of a wet blanket, but the other problem I foresaw is that the UVC drivers only support Video4Linux 2, and I don't think there are too many applications supported yet (Ekiga is one of the only ones, and I haven't used it much but I don't think it captures video; it's just a telephony client).  I just checked Cinelerra, and it appears to only support V4L1.  Point is, I'm not sure what app you can use to capture video with the UVC drivers even if you get them to work with your camera (you mentioned YouTube as your ultimate goal).  Anyone else know of a video capture application that works with Video4Linux 2?
Didn't work. Any other drivers compatible with my webcam?

---

### Post by gatman3 on 2007-08-19
Make sure you have the driver loaded (not sure of if it's "modprobe uvc" or what the exact driver name is, or you could try rebooting).  If you do this:

lsmod | grep usb

you should see some reference to the uvc driver if it's loaded.

I am not an authority on the subject (although apparently the only one around to help you right now), but from my survey, there are 3 current webcam drivers:

gspca
uvc
pwc

uvc isn't working for you.  pwc says it doesn't support your camera.  Not sure about gspca, but I don't think it supports any of the newest logitech cams (works great with my older QC for Notebooks Deluxe camera).  gspca also seems to work out-of-the-box with Feisty with the cameras that it likes, and it didn't like my QC for Notebooks Pro (different usb id, though).  So... my guess is that you are SOL unless you can get the uvc driver working.  And then figure out an application to capture video using V4L2.

---

### Post by gatman3 on 2007-08-19
Sorry... to be more clear, if you do 

lsmod | grep usbcore

you should get a list like this:

usbcore               135048  11 snd_usb_audio,snd_usb_lib,gspca,usb_storage,libusual,usbhid,xpad,usblp,ehci_hcd,ohci_hcd

This shows that usbcore is presently using my gspca driver for my webcam.  You should see some reference to uvc in the usbcore line (I think).

---

### Post by BnetTheAwesome on 2007-08-19
> **gatman3 said:**
> Make sure you have the driver loaded (not sure of if it's "modprobe uvc" or what the exact driver name is, or you could try rebooting).  If you do this:

lsmod | grep usb

you should see some reference to the uvc driver if it's loaded.

I am not an authority on the subject (although apparently the only one around to help you right now), but from my survey, there are 3 current webcam drivers:

gspca
uvc
pwc

uvc isn't working for you.  pwc says it doesn't support your camera.  Not sure about gspca, but I don't think it supports any of the newest logitech cams (works great with my older QC for Notebooks Deluxe camera).  gspca also seems to work out-of-the-box with Feisty with the cameras that it likes, and it didn't like my QC for Notebooks Pro (different usb id, though).  So... my guess is that you are SOL unless you can get the uvc driver working.  And then figure out an application to capture video using V4L2.
*Sigh* I guess I'll get the camera you mentioned. Logitech Quickcam for Notebooks Deluxe, right?

---

### Post by gatman3 on 2007-08-19
This is the one that I traded down to and works well with the gspca driver (actually it worked out-of-the-box for me with no modifications to Feisty, just plugged it in):

[http://www.compusa.com/products/product_info.asp?pfp=cat3&product_code=328756](http://www.compusa.com/products/product_info.asp?pfp=cat3&product_code=328756)

The keywords are "RightLight Technology" and "RightSound Technology", which seem to be associated with a particular chip that is supported by gspca.

(ominously, I couldn't find it listed on the Logitech web site as a current product, so perhaps it is reaching end of life?)

Also, the Logitech QuickCam Communicate STX appears to use the same chip and behaves identically (I have one of those now on my desktop).

The only caveat:  I haven't tried sound, so I can't tell you if it works or not.  I'll look into it and see if I can figure it out (I use it with Kopete, which doesn't support sound anyway).  Worst case, you should be able to plug a microphone into your soundcard's mic input and use that.

---

### Post by gatman3 on 2007-08-19
I tried YouTube quick capture.  Video works, but can't get audio to work from my webcam.  I tried VLC and video works also, but no audio.  In VLC you can specify the audio device, and I think with some fiddling you could use a microphone plugged into your sound card.  Might be able to do that with YouTube too, don't know (it looks like Flash is looking for a "linux microphone"... not your webcam, so an additional mic might work).

I wouldn't rule out getting webcam audio to work, but it didn't appear to work "out-of-the-box" with that quick check I did.  Oh well.

Good luck.

---

### Post by gatman3 on 2007-08-20
OK, I got audio working with my 046d:08d8 Logitech QuickCam for Notebooks Deluxe.

For me, the audio device is /dev/dsp2.  It may show up as a different number depending on the sound card(s) installed before it.

In VLC, I was able to capture video WITH sound as follows:

File->Open Capture Device->Video4Linux tab
Video device name = /dev/video0
Audio device name = /dev/dsp2

(If it's working you should see the live video stream and hear your voice played back through the speakers when you talk, with a short lag).

I looked for ALSA mixer controls for the webcam audio:

alsamixer -c 2

(in my system it shows up as card #2, yours may be different, again, depending on your specific sound card interfaces).

Unfortunately, the only control available is the automatic gain control (press M to toggle AGC on or off), no input level control or anything like that.  But... it works just the same (you can experiment with the AGC to see what it does).

I was also successful using YouTube quick capture with a discrete microphone plugged into my sound card, but I haven't figured out yet how to configure Flash to use /dev/dsp2 instead of the default.  Might be able to do that with the .asoundrc, or maybe there's a cleaner way to configure; I'll experiment.

---

### Post by BnetTheAwesome on 2007-08-20
I'm successful. I got a new webcam. Well, traded for one that works. It is a creative. I can't get audio however and can someone help me with that? Also, I'd like to edit my youtube videos, so what is a good video editing software? And what is a good format converter so I can eventually put these videos on Youtube? Help would be appreciated.

---

### Post by gatman3 on 2007-08-20
For everyone's reference, which Creative webcam model did you get that works?

For audio, I have found that the audio devices for my webcams show up as /dev/dsp2 (my soundcards are at /dev/dsp and/or /dev/dsp1).

For starters, do:

ls /dev/dsp*

and see which audio devices are available.  An educated guess would be to use the highest numbered one.

Then load VLC using your favorite package manager.  VLC can be used to capture audio/video streams from webcams.  In VLC, go to:

File->Open Capture Device->Video4Linux (tab)

In video device name try "/dev/video0".  (this is the most likely, but may be different on your system)

In audio device name try "/dev/dsp2" or whatever the highest listest /dev/dsp* device is in your system.

That should pop up a video window, and if audio is working you will hear it come through your speakers with a short lag (you may need to adjust your mixer settings using alsamixer or some other mixer program).  If you get that far, your hardware is working.  Then you just need to learn to use VLC to capture streams.

For basic video editing, try Kino or Avidemux.  Cinelerra is by far the best, but it has a steep learning curve; I also couldn't get it working from the repository; I needed to compile the source to get it working and it was a little bit of a pain, but worth it in the end.  But if you go with Cinelerra, plan on spending several weeks learning how to use it fully.

---

### Post by BnetTheAwesome on 2007-08-20
Audios is working fine (Got a microphone). My main problem now is I'm going to do my show on blip.tv (A Linux user's friend), but I don't know any good video capture software for Linux. Does anyone know a good one? I have video editing software now, but no capture software.

---

### Post by gatman3 on 2007-08-20
I have used VLC to successfully capture video and audio (read the posts above this one).  VLC works really well, except that I haven't figured out how to control the frame rate (or even to figure out what the captured frame rate is... although it seems to be around 12.5 fps with my Logitech webcam).

Kino only seems to want to capture from 1394 devices, not webcams.

I have not been able to get Cinelerra to successfully capture from my webcam, although it appears capable from the configuration settings.  Problem is it keeps crashing when I try to capture.

Most other programs like Camorama or gqcam only seem to be able to capture stills.

Anyone else have a suggestion of a good program to use to capture webcam video?

(you might want to start a new thread to ask the question)

---

### Post by tashmooclam on 2007-08-22
I downloaded EasyCam2 but my camera is not recognized.

---

### Post by gatman3 on 2007-08-22
> **tashmooclam said:**
> I downloaded EasyCam2 but my camera is not recognized.

Sorry, I'm not familiar with EasyCam2.  I guess it's some kind of installer to try to automatically set up the right driver?  Haven't used it.  I didn't see it in the Feisty repositories.  I think that in most cases it shouldn't be necessary to use something like EasyCam2 to load new drivers with Feisty unless you have a really oddball camera, because Feisty has the spca5xx/gspca and uvc drivers available as modules.

I have recently learned that the golden site for info about web cam drivers is:

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

You should start by going there and looking up your camera to see if it is supported and which driver it should use (look it up by USB ID, don't rely just on name, because some vendors like Logitech actually have multiple cameras with the same name but different hardware).

---

### Post by tashmooclam on 2007-09-05
Looking at the link you provided, I see that my gigaware webcam uses the "gspcav1" driver.
Where do I go to get that?
I used synaptic package manager and did this as a search and found nothing.
The easycam idea was from an ubuntu wiki if I recall correctly.

---

### Post by gatman3 on 2007-09-05
I'm not exactly sure about gspca vs. gspcav1, but some web searching suggests that one is the transitory name for the gspca driver.  I think this should be compiled as a loadable module if you are using Feisty (probably earlier ubuntu versions as well), and if all goes well it should be loaded automatically when you plug in your camera.  Of course, if it was then I'm guessing that you wouldn't be looking for help (duh...)

Try checking to see if the gspca driver is loaded, for starters.  Try this (these are my results as well with one of my logitech cameras):

> lsmod | grep gspca
gspca                 607824  0 
videodev               28160  1 gspca
usbcore               134280  8 gspca,snd_usb_audio,snd_usb_lib,ndiswrapper,usbhid,ehci_hcd,uhci_hcd

If it isn't loaded, try doing a:

> sudo modprobe gspca

and see if it loads the module after this.

If that doesn't work, go get the driver source and try compiling and loading it from scratch:

[http://mxhaard.free.fr/spca50x/Download/gspcav1-20070508.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20070508.tar.gz)

(You will probably need the kernel headers and a variety of other basic necessity packages for compiling, if not already installed on your system).

---

