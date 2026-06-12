---
title: "Logitech Quickcam Ultra Vision Help Needed"
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by toddbmobile on 2008-02-02
I just purchased a**[COLOR="Red"] Logitech Quickcam Ultra Vision[/COLOR]** off Ebay, and as Emeril says **_"BAM_**" it is the bomb under windows, I love it, and my kids love the cool effects. I however am a Ubuntu Gusty 7.10 user, and want it to work under Linux. I have followed everyone's how tos and none seem to work. I of course have the uvc driver loaded. The cam and its mike shows up under lsusb as well. I get to this point/ERROR when I try to launch luvcview:

 luvcview -s 640x480
luvcview version 0.2.1 
 size width: 640 height: 480 
Video driver: x11
A window manager is available
video /dev/video0 
[B][COLOR="Red"]ERROR opening V4L interface 
: No such file or directory[/COLOR][/B]

I know others have said they got theirs working under 7.10, but after following their how to I still am not any closer to the solution. The light on the webcam does not light either. I have an HP Pavilion dv5000 series laptop, and an ATI Radeon XPRESS 200M video card runnig compiz fusion fine.

At one time when I first tried to get it working in the beginning I got the following message:

 luvcview -s 640x480 
luvcview version 0.2.1 
 size width: 640 height: 480 
Video driver: x11 
A window manager is available 
video /dev/video0  luvcview
[B][COLOR="Red"]Unable to set format: 5. 
 Init v4L2 failed !! exit fatal [/COLOR][/B]

Help, anyone with a sure fire solution................................Help :)

---

### Post by linuxwizard on 2008-02-02
Try using a different USB port.

---

### Post by toddbmobile on 2008-02-02
Tried it and got the same below:

 luvcview -s 640x480
luvcview version 0.2.1 
 size width: 640 height: 480 
Video driver: x11
A window manager is available
video /dev/video0 
Unable to set format: 5.
 Init v4L2 failed !! exit fatal

---

### Post by linuxwizard on 2008-02-02
Your cam is listed here > [http://www.quickcamteam.net/hcl/linux/logitech-webcams](http://www.quickcamteam.net/hcl/linux/logitech-webcams) > in the notes > Incompatibilities with some USB controllers reported on Linux. > Than here > [http://www.quickcamteam.net/documentation/faq/logitech-webcam-linux-usb-incompatibilities](http://www.quickcamteam.net/documentation/faq/logitech-webcam-linux-usb-incompatibilities)
> You stated the light did not come on so it is not getting power from port. This is why I suggested trying another port.

---

### Post by wjston on 2008-02-04
> **toddbmobile said:**
> I just purchased a**[COLOR="Red"] Logitech Quickcam Ultra Vision[/COLOR]** off Ebay, and as Emeril says **_"BAM_**" it is the bomb under windows, I love it, and my kids love the cool effects. I however am a Ubuntu Gusty 7.10 user, and want it to work under Linux. I have followed everyone's how tos and none seem to work. I of course have the uvc driver loaded. The cam and its mike shows up under lsusb as well. I get to this point/ERROR when I try to launch luvcview:

 luvcview -s 640x480
luvcview version 0.2.1 
 size width: 640 height: 480 
Video driver: x11
A window manager is available
video /dev/video0 
[B][COLOR="Red"]ERROR opening V4L interface 
: No such file or directory[/COLOR][/B]

I know others have said they got theirs working under 7.10, but after following their how to I still am not any closer to the solution. The light on the webcam does not light either. I have an HP Pavilion dv5000 series laptop, and an ATI Radeon XPRESS 200M video card runnig compiz fusion fine.

At one time when I first tried to get it working in the beginning I got the following message:

 luvcview -s 640x480 
luvcview version 0.2.1 
 size width: 640 height: 480 
Video driver: x11 
A window manager is available 
video /dev/video0  luvcview
[B][COLOR="Red"]Unable to set format: 5. 
 Init v4L2 failed !! exit fatal [/COLOR][/B]

Help, anyone with a sure fire solution................................Help :)

Your camera won't turn on if you haven't got a driver showing up in "Options>Video."
If the driver is enabled, try going to your home folder>hit Ctrl H on your keyboard and you should see a number of hidden folders appear. Look for the one marked ".Skype" and double click it. You should now see a folder with your username. Open that and right click on the config.xml file. Open that with Bluefish Editor. Scroll down until you come to a section beginning with "Video." Add the section I highlighted in red and save the file before closing it. 
<Video>
      <AutoSend>1</AutoSend>
      [COLOR="DarkRed"]<CaptureHeight>480</CaptureHeight>
      <CaptureWidth>640</CaptureWidth>
      <Device>/dev/video0</Device>
      <Fps>30</Fps>[/COLOR]
    </Video>
Now try and test your camera in the options>video section of skype again. Hopefully this will work for you. I have and nVidia Geforce fx5200 card and that solved this for me with both a Pro 9000 and Ultra Vision camera.

---

### Post by toddbmobile on 2008-02-15
Tried what you stated. It works, and I also can now get the webcam to work when I run luvcview -s 640x480 or skype. However it works up until I close the program. If I open skype or run luvcview -s 640x480 the webcam won't come back on. To get it to work again, I have to play musical usb ports. In other words if I move my usb devices around thru a series of lsusb in terminal the device will work again. I have got to be close to the answer. By the way my webcam worked grest under skype 30 FPS like you said.

---

