---
title: "Use Webcam Studio to livestream?"
date: 2013-02-15
forum: Multimedia Software
---

### Post by Gato303co on 2013-02-15
> **MaindotC said:**
> I use [WebCamStudio]("http://www.ws4gl.org/") and it works well.  I have a really good video card so I dunno if that has anything to do with it, but as an example I can run Starcraft in an xp vm, change the resolution to make it 640x480 (Starcraft's unchangeable resolution), fire up ws4gl and broadcast on ustream/livestream.  I've not yet run into an application I couldn't screencast.  The big problem I have is most streaming providers only allow 320x280 output.  If I play counterstrike - well yeah ws4gl can handle that, even full screen, but squeeze that into uStream or Livestream sucks :(

How do you use Webcam Studio for GNU/Linux (WS4GL) to stream to livestream/Ustream?  I have been trying the 0.57 beta 4 (191) the most recent verion, and it only has an option to stream to a service called "GISS.tv" only, I don't see an option to stream to a different server and the ws4gl manual doesn't explain deep how to stream a screencast to those or similar services.

Plus, services like Livestream accepts formats MP4, codec H.264 or flv, and ws4gl streams in .ogg format, so how can it be possible to stream to LIvestream or UStream? Thanks for attention

---

### Post by oldos2er on 2013-02-15
Post moved to its own thread.

---

### Post by pablodavid on 2013-05-08
In my case I do the following to broadcast live to livestream with Ubuntu 12.04:

1. Open webcam studio (I use version 0.57 beta 4 all deb) before opening your web browser
2. Select your video input (in my case I use the EasyCap usb capture device with the upgraded STK1160 driver from Ezequiel Garcia, and the ADVC firewire video capture device)
3. In the output tab in webcam studio make sure the “activate output stream” is selected 
4. Open your browser and go to livestream, ustream or justin TV (your preference)
5. Specifically in livestream when entering your virtual studio activate your local camera and select WebcamStudio video device V4L2
6. You will be seeing your video input from webcamstudio
7. Select your audio input
8. Hit cue, and transition to live stream
9. Done
10. Follow similar procedure in ustream or justin TV
V/r Pablo

---

### Post by Gato303co on 2013-05-09
Thanks for you help :)

---

### Post by Gato303co on 2013-05-14
I have a problem, after  following these steps it works and I can stream to livestream...
But the output in livestream is only 320x240, I have tried with different options on Webcam Studio to get the output to 640x480 and 720x480 without success, anyone knows how this can be solve? I am using Webcam Studio 0.57 beta4 (191) on Xubuntu Linux 12.04 64bits, thanks for any help you can give

---

