---
title: "[SOLVED] Webcam only works with Cheese"
date: 2008-09-05
forum: Multimedia Software
---

### Post by R3N3G4D3 on 2008-09-05
I installed gspca driver for my webcam (Logitech QuickCam Communicate Deluxe), and then installed the gspcagui to test the webcam. The gui appeared and wasn't throwing any errors but also didn't seem to recognize the webcam, so I figured the driver wasn't working. Today I installed Cheese and launched it just to see if I get the same result. To my surprise the webcam light went on and a second later I saw myself on the screen in Cheese. I tried a few other webcam apps and they froze while trying to detect the camera (even though they detected that it was connected and that it was a camera). I also tried woome.com since they have camera detection flash plugin, and had no success with that either (it detected the camera but froze trying to use it). Additionally Cheese does not seem to be able to detect the camera when any of the other apps are attempting to use it (blocked resource I'm guessing?), yet detects it just fine otherwise. Now I'm confused, either my driver doesn't work and Cheese has its own integrated driver, or Cheese is the only program that knows how to use the driver correctly. Can someone help me out here?

---

### Post by Crafty Kisses on 2008-09-05
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---

### Post by R3N3G4D3 on 2008-09-05
Ekiga does detect both the microphone (it actually replayed the recording) and the video (can see myself on the screen) on my webcam. The video, however, only works with V4L2, and shows the following error when used with V4L:
> Error while opening video device UVC Camera (046d:0992)

A moving logo will be transmitted during calls. Notice that you can always transmit a given image or the moving logo by choosing "Picture" as video plugin and "MovingLogo" or "StaticPicture" as device.

Your video driver doesn't support the requested video format.
Does that mean that the tools that freeze trying to use the webcam are relying on V4L? Can I tell them to use V4L2 somehow? Can I set V4L2 as default?

Also, just in case, here is my lsusb output:
```
Bus 005 Device 003: ID 046d:0992 Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 046d:c227 Logitech, Inc. 
Bus 001 Device 005: ID 046d:c226 Logitech, Inc. 
Bus 001 Device 004: ID 046d:c223 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

```
No, I'm not affiliated with Logitech :P, just that most input devices are sold either by them or Microsoft, and being a Linux convert kinda obliges me to stay way from M$.

---

### Post by R3N3G4D3 on 2008-09-10
I've resolved the issue, thought I'd post my solution for others with the same problem in the future.

After more digging around I found out that there is no OS-wide V4L settings and each app has its own. So I found out that flash 10 (currently pre-release) does in fact support V4L2. After upgrading my flash plugin, I can now use the camera in web apps. As for regular apps, I just stick to the ones that support V4L2.

---

