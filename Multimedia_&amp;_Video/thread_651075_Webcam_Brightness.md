---
title: "Webcam Brightness"
date: 2007-12-27
forum: Multimedia &amp; Video
---

### Post by Hark3n on 2007-12-27
Okay, I've seen quite a few threads asking for help on this issue, but most of them go unanswered.

Yesterday I bought myself a Logitech Quickcam Express Plus, for use with Skype.  When I plugged it in, it immediately showed up in Skype.  The test returned a stunning looking picture.

I then tested it further by contacting my brother.  About 30 seconds into our conversation my picture went very dark.  So dark that only the very light areas where visible.

Since then I've been all over the forums looking for a solution, but nothing helps.  I have tried camE, camorama, camera monitor, and even Kopete.  I have yet to find a config file that can be edited.

If anyone has any idea as how to remedy this, please help.  I'm sure I won't be the only one thanking you.

Regards,
E

---

### Post by nikkkko on 2008-01-22
Did you find an answer to this? 

My related question : There are picture quality controls in Kopete but not in Skype.  Is there a way of adjusting webcam parameters at system level for all applications, in the same way that the Alsa mixer works over sound?

---

### Post by nikkkko on 2008-01-22
Here's a useful post culled off the Skype linux forum :

> I have a Sunplus Technology Co., Ltd Flexcam 100 (shabby little cam I got as a free gift when ordering contact lenses), so for other cameras, you'll want to adjust to different values.

My optimal settings were:
Gamma: 4
Red: 290
Green: 310
Blue: 315

Go to the the Linux Video settings directory:
CODE
cd /sys/module/gspca/parameters/


EVERY FOLLOWING COMMAND MUST BE RUN AS ROOT! (sudo doesn't handle the ">" redirection stuff elegantly without weird escaping, which I haven't mastered yet)

CODE
sudo su


And echo new values to the gamma and color files:
CODE
echo 4 > /sys/module/gspca/parameters/gamma
OR
echo 290 > /sys/module/gspca/parameters/GRed
OR
echo 310 > /sys/module/gspca/parameters/GGreen
OR
echo 315 > /sys/module/gspca/parameters/GBlue

After tweaking with these, right click the skype systray icon, and chose "Options", then "Video Devices", then click the video "Test" button to check it out. You'll need to close and reopen the options window after each change.

Once you've tweaked to the best config possible, save the module settings permanently to /etc/modprobe.d/options:

Add these lines (with your values) to the "/etc/modprobe.d/options" file:
CODE
options gspca gamma=4
options gspca GRed=290
options gspca GGreen=310
options gspca GBlue=315

The forum thread can be found [here.]("http://forum.skype.com/index.php?showtopic=106357&st=0&gopid=488987&#entry488987")

---

