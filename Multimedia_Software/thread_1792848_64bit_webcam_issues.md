---
title: "64bit webcam issues"
date: 2011-06-28
forum: Multimedia Software
---

### Post by brent0n on 2011-06-28
i was using a Rosewill RCM-8163 webcam in 10.10 and it worked perfectly. i upgraded to 11.04 and now the cam is extremely dark whenever i use an application. when i use the webcam through flash on webpages, it works fine, no issues at all. i'm thinking there is probably an easy solution to this, but i've googled lots and not been able to find it. any ideas?

---

### Post by brent0n on 2011-06-29
anyone?

---

### Post by no2498 on 2011-06-29
install v4l2ucp
it comes up in system , preferences as video4linux control panel
it should help
it has a preview you can use

---

### Post by brent0n on 2011-06-30
thanks, that did help. i found out that specifically checking Exposure, Auto Priority in that panel did the trick. unfortunately, it stays fixed very briefly and reverts and i have to recheck it. HMM!

---

### Post by no2498 on 2011-06-30
you got me on needing to reset it
mine stays just wish i could set some colors with it
you may ask a deferent ? for it

---

### Post by brent0n on 2011-07-02
ask a different question? i'm unsure of what you mean good sir! does anyone have ideas for me? i'd really prefer to use my external cam and can't because of this issue! thanks in advance. :)

---

### Post by no2498 on 2011-07-02
if you have 2 cams try setting it in gstreamer-properties

in a terminal type gstreamer-properties click enter
click video
set it to the cam you wish to use

i think it will stay

---

### Post by brent0n on 2011-07-13
i tried that, but no luck either, it just reverted everytime i closed it. fortunately though, i did find a fix. if you have the same issues you can just do this:


sudo uvcdynctrl -d 'video1' -s 'Exposure, Auto' 1

---

### Post by brent0n on 2011-07-14
alas, after the computer was restarted the webcam was back to it's old tricks. i've tried using v4l2ucp to set it, tried guvcview, it reverts with the box still checked, i've used that command to set it, just doesn't work after the restart. i'm going insane! anyone have ideas?

---

### Post by no2498 on 2011-07-15
this is some thing old that worked at 1 time for me hope it helps you


OK, this worked great for me, but let me neatly sum this all up.

I have a Sunplus Technology Co., Ltd Flexcam 100 (shabby little cam I got as a free gift when ordering contact lenses), so for other cameras, you'll want to adjust to different values.

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

---

### Post by brent0n on 2011-07-19
that directory doesn't even exist for me :S

---

### Post by no2498 on 2011-07-20
you need to make it

you can see a difference if you just run it 
that way you can see if it helps first 

sudo /etc/modprobe.d/options

---

