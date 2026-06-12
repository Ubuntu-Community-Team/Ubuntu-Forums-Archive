---
title: "Ustream broadcasting with 9.04"
date: 2009-04-28
forum: Multimedia Software
---

### Post by Ninesvnsicks on 2009-04-28
I just updated to Ubuntu 9.04 jaunty jackalope and my webcam works fine locally but when I go to use it with ustream I get no video.  Their flash interface does detect it I just don't get any video and when I click start broadcasting it just highlights the button and doesn't do anything.  I have tried other things like webcamstudio and flashcam with the same result.

---

### Post by Ninesvnsicks on 2009-04-29
Any ideas?

---

### Post by MaindotC on 2009-04-30
I can't broadcast audio.  It was working fine in 8.04 but I decided to upgrade to 8.10 and it seems to be related to 8.10 and above.  I'm going to try different sound driver settings.

---

### Post by Ninesvnsicks on 2009-05-01
Here is what I get just a blank grey square instead of video and when I hit broadcast it just highlights a brighter green color and doesn't broadcast.  As you can see tho it does detect my camera.

[IMG]http://img147.imageshack.us/img147/6646/screenshotustreamtvbroa.png[/IMG]

---

### Post by MaindotC on 2009-05-01
I confirm this same issue w/ the broadcast button for audio as well :(

---

### Post by Ninesvnsicks on 2009-05-02
I got it to work my flash wasen't set to allow it usually asks in windows but in ubuntu I had to go to youtube then right click and go to flash settings for some reason ustream wouldn't let me into flash settings not sure why but if you set it to allow and then load ustream it works.

---

### Post by MaindotC on 2009-05-02
Still not working :(  What did you click in Settings?

---

### Post by Ninesvnsicks on 2009-05-04
Go to youtube or some flash site and right click on the flash area go to settings then go to the privacy tab and switch it to allow it's on deny by default.

---

### Post by MaindotC on 2009-05-04
I did click and allow that and I'm still getting a highlighted green "Start Broadcast" button but it's not changing to "Broadcast Started".  I've checked my account and it doesn't show that I'm broadcasting.  I'm just re-installing to 8.04 - the time it will take to figure this out will be way longer than it will take me to do a clean install.

---

### Post by RAD-MAN on 2009-07-22
I know this is kinda old, but I figure if I am able to help for once I might as well say something. In case someone finds this again.
You can allow Ustream through here:
[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html)

Works in 8.10 to my knowledge.

---

### Post by MaindotC on 2009-07-23
HA!  Kickass, that works!  Thanks Rad-Man!  Do you happen to know how to stream input from like cable tv to ustream?  I've gotten everything on my computer, such as desktop, dvd, or movie file, to stream using the vloopback module in WebcamStudio, but I'm not sure how to capture input to my video card and redirect it to ustream or livestream. Thanks!

---

### Post by handyguy on 2009-07-24
> **RAD-MAN said:**
> I know this is kinda old, but I figure if I am able to help for once I might as well say something. In case someone finds this again.
You can allow Ustream through here:
[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html)

Works in 8.10 to my knowledge.

Thank you very much that post was super helpful and i have been trying to use ustream in ubuntu 9.04 for a long time and finally I am able to. Thank You very much

---

### Post by afrodeity on 2010-06-24
I am streaming, but no audio showing in the vu metre. I've tried setting to simultaneous output via pulseaudio applet, but still nothing. Needs a proper tutorial for this. Please help.

---

