---
title: "Advice for better resolution pictures using the Cheese webcam application??"
date: 2018-03-22
forum: Multimedia Software
---

### Post by kansasohio on 2018-03-22
Hello,

I have been trying to get high quality still photographs using the Cheese webcam program.  

I am having limited success and wonder if anyone might be able to give me any advice which might help me get better pictures.

My pictures seem to be in focus but seem to be of a lower resolution than I would expect.  I have a logitech webcam that I bought for this purpose which sets up at the highest resolution of  1600x1200 which I "think" translates into 2mp.

I'm pretty sure that I need more resolution...a lot more.  I thought my webcam was a higher resolution but I can't seem to find any model number on it and the camera sets up as a uvc camera (046di0991) in Cheese.  Would this be the right camera setting or is it just a generic driver?

What I would really like to do is set up a 12 mp digital camera to use in cheese using the av output and a usb converter.  Would anyone know if this can be done in Cheese?

I am also trying to find out the highest resolution webcam that Cheese can handle.  Would anyone know what this might be?  

Would anyone have a suggestion for a great (under $60.00) webcam?

My Cheese version is 3.18.1

My apologies for so many sporadic questions.

Thanks in advance for any advice.  I really appreciate it.

Regards,
Tim

---

### Post by TheFu on 2018-03-24
I don't use cheese.  I've been using **guvcview**.

Resolution of any webcam will be controlled by the webcam drivers.  I have a Logitech C920 Pro which was over $100 and it does 1080p resolutions on Windows, [s]but only 720p (1280x720) on Linux[/s]. Got 1920x1080p working.  Some higher resolutions were listed, but they only flickered and showed a green image.  I doubt you have a 1200p capable webcam for $60.   Also, Logitech isn't exactly known for being Linux friendly, so ported drivers from their other models might be the only drivers available.

The first thing you need to know is the specific model of webcam.  lsusb should help with that, assuming a USB interface.
Here's mine:```

lsusb|grep Logit
Bus 001 Device 009: ID 046d:082d Logitech, Inc. HD Pro Webcam C920
```

Without that, you (we) cannot research which driver might provide the best results.  Now I'm curious. Need to see if better drivers are available for my C920 - which is a highly regarded, cheap, webcam for youtube tutorials, BTW.

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam) might also be helpful, but I found the Arch wiki more useful.

---

### Post by kansasohio on 2018-03-27
Thanks TheFu for your advice.

Using the code that you provided (Thank you for that) I get this:
mint@mint ~ $ lsusb|grep Logit
[B]Bus 002 Device 012: ID 046d:0991 Logitech, Inc. QuickCam Pro for Notebooks


[/B]
When I open the Cheese program and select my webcam (under preferences) my only device option is this:[B]
UVC Camera (046d:0991)

[/B]
The only information printed on my webcam is on the lens and it says:[B]
2MP autofocus, Carl Ziess, Tessar 2.0/3.7 


[/B]I purchased this webcam a couple of years ago when I was researching still photography and someone recommended this particular webcam.  I think that I even stumbled on the original comment the other day when I found a forum where someone said that they even take their laptop and the webcam on vacation to take pictures (keep in mind that this was back in 2012 - it probably didn't sound so ridiculous them.)

I'm starting to think that perhaps my auto focus isn't working on the webcam and that this might be part of my problem.  It doesn't seem totally blurry...it just sees to have "artifacts" around the edges of items that I try to photograph.  Would the autofocus be dependent on the driver that Linux uses?

I also use guvciew and like it a lot.  Cheese is awesome for my intended purpose right now because I am interested in stop-motion photography and also in other applications where I can take still photographs like an old fashioned photobooth.

I apologize for using MP for describing the resolution my camera.  I'm used to digital cameras and really don't do much video.  It seems like I'm using the wrong terms.

Thank you again.
Tim

EDIT:  I'm still trying to digest the information given in the link that you provided.  I wanted to reply to you quickly to thank you for your reply - I'm still working on what you provided me with.

---

### Post by TheFu on 2018-03-27
If this is the device: [https://www.amazon.com/Logitech-QuickCam-Pro-Notebooks-USB/dp/B00006LIOM](https://www.amazon.com/Logitech-QuickCam-Pro-Notebooks-USB/dp/B00006LIOM) then it is a non-HD webcam (VGA CCD sensor) with photo resolution that is a little higher at 1280 x 960.  Expecting anything better resolution will likely be fruitless.  2 MP is pretty low res.

I have no idea whether autofocus is supported through the drivers or not. Sorry.

---

### Post by kansasohio on 2018-03-27
> **TheFu said:**
> If this is the device: [https://www.amazon.com/Logitech-QuickCam-Pro-Notebooks-USB/dp/B00006LIOM](https://www.amazon.com/Logitech-QuickCam-Pro-Notebooks-USB/dp/B00006LIOM) then it is a non-HD webcam (VGA CCD sensor) with photo resolution that is a little higher at 1280 x 960.  Expecting anything better resolution will likely be fruitless.  2 MP is pretty low res.

I have no idea whether autofocus is supported through the drivers or not. Sorry.


Thank you for the reply.

The camera linked doesn't appear to be the same.  I finally found my model...it's a c905. 
Amazon has it here:
 [https://www.amazon.com/Logitech-960-000045-720p-Webcam-C905/dp/B000RZNI4S/ref=sr_1_fkmr0_3?s=electronics&ie=UTF8&qid=1522171947&sr=1-3-fkmr0&keywords=2MP+autofocus%2C+Carl+Ziess%2C+Tessar+2.0%2F3.7](https://www.amazon.com/Logitech-960-000045-720p-Webcam-C905/dp/B000RZNI4S/ref=sr_1_fkmr0_3?s=electronics&ie=UTF8&qid=1522171947&sr=1-3-fkmr0&keywords=2MP+autofocus%2C+Carl+Ziess%2C+Tessar+2.0%2F3.7)

Your camera seems very nice, but the wide screen aspect would actually hinder me as I'm looking for square picture (i.e not wide-screen) directly out of the camera.

The strange thing is that all of the cameras that I look at seem to take an actual 2mp picture (or less) even when they're advertised as 5mp or higher. The higher ratings are actually for an enhanced picture.

I'm starting to think that there are no high resolution still image web-cams that aren't wide-screen hd.

  I agree - 2mp is pretty low res these days.  I think that my price range needs raised, but I still don't see what I need.  The amazon price for my camera seems way out of line.  I bought mine for much less.

---

### Post by TheFu on 2018-03-27
It is an older camera - made for WinXP!  People looking for that model will be replacing one, probably used in a business, so the re-sellers are charging more. "Carl Zeiss ultra-wide angle lens" is in the description, BTW.

Have you considered using a $50 PnS camera instead?  The photos will be much better - much better.  Just get a cheap tripod.  Or they have wifi, you can control many of them through a smartphone app.  My canon PnS supports that, though I've never used that feature in the real world.  Only you know if the workflow you need can work with some other hardware.  Perhaps you are doing stop-motion movies and would like to have photos taken automatically every 8 seconds?  IDK.  With a nicer PnS camera, you could just shoot 1080p video and grab 1 frame every 8 seconds.  There are tools that can do that pretty easily.

---

