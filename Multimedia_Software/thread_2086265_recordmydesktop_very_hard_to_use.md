---
title: "recordmydesktop very hard to use"
date: 2012-11-20
forum: Multimedia Software
---

### Post by sdowney717 on 2012-11-20
My experience history
I ran this on cinnamon desktop and got a usable red button on the panel to stop and control the program.

then something happened and when started, the menu panel disappears and just white bars at top of screen with the current window displayed. No way to shut it down, no control of the PC menus. I eventually pulled the plug on the PC.

Subsequent tries same, so log into gnome3

same white panel and no controls when running record my desktop
so reboot.

Then I discovered you can hit alt-F2 key to open a command input box
then type gnome-terminal to load terminal window
then run htop to see processes
then find record desktop pid number
open a tab on the terminal 
type 'kill pidnumer'
then it stops the recording and does the save which takes a very long time. And I get my menus back

When I run this I lose all menu ability, and it only displays the current window.

So how do you stop and start this app?

here is a screen shot of the recorded desktop when played back showing the white bar at top.

---

### Post by sdowney717 on 2012-11-20
ok, tried a select a window to record. I get a box that gets recorded and no way to control the stop and start. Although I do retain my menu controls.

here are more screen shots

How do you control the program, again this time I used htop to kill the pid process

---

### Post by sdowney717 on 2012-11-20
A bug exists, so I am not alone on this 
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=650353](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=650353)

I should try unity and see if it does same as gnome3 and cinnamon.
How come there are not a lot of people posting this as a problem?
Anyone use it fullscreen?
What do you use?

---

### Post by dannyboy79 on 2012-11-20
i use a bash script which uses ffmpeg to record. I am not at home so I can't post the script but it's very flexible allowing you to control the resolution, frame rate etc etc. it even captures audio from a microphone.

although I jusdt came across this one and it looks pretty darn good.

[https://wiki.jasig.org/display/JSG/Screencasting+In+Ubuntu](https://wiki.jasig.org/display/JSG/Screencasting+In+Ubuntu)

---

### Post by cybrsaylr on 2012-11-20
Try Kazam which I found runs much better.

---

### Post by sdowney717 on 2012-11-20
I found out by intense web clicking how to make it work with gnome3

picture shows the settings.
set sound to pulse

The sound however is horrible. I can select either the mic or line in. Line in the volume is very low.
Mic is noisy and low. there is no bass in the sounds. very tinny sound.

Do you have to have some kind of cable to link sound out to the sound input on the motherboard?

MB is a P5QC Asus with core 2 duo intel chip running Nvidia 8400gs. So It should not be too weak to work ok?

---

### Post by sdowney717 on 2012-11-20
> **cybrsaylr said:**
> Try Kazam which I found runs much better.

your amazing!
kazam records very well and the sound is great, loud and has bass.
It also is linked up sound with the video.

I had tried on gnome screencaster, but you dont get sound and the webm files it creates are not controllable as far as seeking.
kazam webm files you can seek.

What is going on with the recordmydesktop, compared to kazam it has got issues. although mostly with sound.

I noticed kazam uses Monitor of builtin audio analog stereo. There was some posts about forcing RMD to use this by running a pulse audio volume control, it had to be selected, but I could not, it would not allow me. Then it had issues with having to do it each time.

---

### Post by cybrsaylr on 2012-11-20
Tried a few of these Screencaster programs and Kazam seems to work the best so far.

---

### Post by sdowney717 on 2012-11-20
On my PC, the webm works best. The other one H264 mp4 causes a hesitation or jerkiness to the recording.

I also notice on both an occasional blue flashing at the top mostly, sometimes over the entire screen, in recording full screen

Is my core 2 duo 3 ghz  computer too slow or is the 8400gs Nvidia card too slow.

8gb memory should be plenty.

---

### Post by monkeybrain2012 on 2012-11-20
+ 1 to Kazam. recordmydesktop is kind of garbage in my experience, it has multiple issues and doesn't work with Compiz. It was ok in old Ubuntu releases when compiz was optional, but not since Unity.

---

