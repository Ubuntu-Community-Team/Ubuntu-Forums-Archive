---
title: "Dell XPS m1530 Microphone"
date: 2008-05-10
forum: Multimedia Software
---

### Post by Zigara on 2008-05-10
Hello,

I recently switched to Ubuntu (8.04) and it seems the internal microphone on my Dell XPS M1530 is acting odd..

I have the volume set to max but I can barely hear myself, I know its working but its SUPER SUPER quiet, the odd part is.. It worked fine before..

I didn't change anything that I know of so I'm not sure what todo..

Any help would be wonderful!

Thanks.

(PS: I already set the Digital Input Source to Digital Mic 1)

---

### Post by scapermoya on 2008-08-02
yeah I have the same problem. enabling micboost doesn't help much, if at all.


is there a way to increase mic volume (sensitivity?) in the inner-workings of ubuntu?

---

### Post by polyvios on 2008-08-20
open the mixer (right click, open volume control)
edit->preferences.
add everything.
go to mixer, select the recording tab.
make sure the "digital" and "capture" slides are unmuted (both mic and speaker icons).  I also unmuted "capture 1" but i don't think that made a difference.  
slide the "digital" volume up to maximum.
open sound recorder.
select "record from input: digital".
make sure it works.
enjoy.

---

### Post by colonelqubit on 2009-05-11
My Dell m1530n also has a very quiet microphone.

I don't have a "digital" slider and in soundrecorder the only option I have for capture is the device named "Capture".

I wonder if there's a difference in sound cards between the m1530 and the m1530n. lspci reports that I have a 82801H:

Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

---

### Post by rbfthomas on 2009-05-29
> **polyvios said:**
> open the mixer (right click, open volume control)
edit->preferences.
add everything.
go to mixer, select the recording tab.
make sure the "digital" and "capture" slides are unmuted (both mic and speaker icons).  I also unmuted "capture 1" but i don't think that made a difference.  
slide the "digital" volume up to maximum.
open sound recorder.
select "record from input: digital".
make sure it works.
enjoy.

I tried this, but the unmutings don't "take".  I see the little red 'x' on the microphones, and I click it to go away, but when I close the dialog box, or even go to another tab, when I come back they're back where they were.  What gives?

---

### Post by hornbake on 2009-06-04
This is a known bug:
[https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/275998](https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/275998)

See also this thread:
[http://ubuntuforums.org/showthread.php?t=956565](http://ubuntuforums.org/showthread.php?t=956565)

I've not found any working solution.  My XPS 1330 has the same problem.

---

### Post by jacksenechal on 2009-09-19
After some searching around, I found this post which totally fixed it for me:

[http://justscript.blogspot.com/2009/06/ubuntu-dell-m1530all-microphone-boost.html](http://justscript.blogspot.com/2009/06/ubuntu-dell-m1530all-microphone-boost.html)

> First install the pulse audio stuff!

    ```
sudo apt-get install pavucontrol
```

after installation you will get 2 new options in "Applications/Sound" namely "Pulse Device Cooser" and "Pulse Volume Control",

Run "pulse device chooser", it will appear as a small icon in the tray area. left click this icon and click "manager".

goto the devices tab and highlight the capture device and click properties drag the volume meter to about 130-140% and click close.

---

### Post by hamdori on 2009-10-26
Thanks Jacksenechal for the great information.
I've been looking for the solution for long time, and here I found it. :-)

---

