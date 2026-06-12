---
title: "devices setup flickers or changes"
date: 2014-01-29
forum: Multimedia Software
---

### Post by NrNice on 2014-01-29
Hi there,

I came accross this issue in my new Mint/Mate box (Ubuntu 13.10):
When I  open PulseAudio Volume control, "Output Devices" window and I set the  drop-list to "Headphones", the drop-list is flickering every 1 to 5  seconds. I have drops in the headphone.
If I set to "Analog Output", the next flick, the drop-list will change to "Headphones".
Same with "Input Devices", "LIne In" will change to "Front Microphone" at the next flick.
I can see that as well with alsamixer CLI.
At first I was thinking this is a compatibility issue between kernel and Nvidia driver. Now I am not sure.

I tried the 5 different drivers from "Driver Manager" without success: 
-nvidia319 (recommanded)
-nvidia319-updates
-nvidia-304
-nvidia304-updates
-xserver-xorg-video-nouveau

My kernel is 3.11.0-12-generic

This is the same issue that this thread as well
[http://forums.linuxmint.com/viewtopic.php?f=48&t=124784&hilit=kernel+nvidia+flickering+sound](http://forums.linuxmint.com/viewtopic.php?f=48&t=124784&hilit=kernel+nvidia+flickering+sound)

It's why I am not sure; when I remove my headphone the drop-list is steady, nothing change no flicker.
I have 2 headphones sets, the both have the same problem One is around 30 ohms the other 880 ohms.
When  I plug in, the drop-list change automatically from "Analog Output" to   "Headphones" and when I remove, it changes back to "Analog Output".
I tried with a jack to jack cable, so no headphone but only a jack. Issue is the same!!!!
Conclusion: Detection is not done by impedance but by the presence of the jack.
I tried to find a setup in the UEFI to stop the detection but there is nothing. Maybe there is one in the driver? Where?

I need to use my headphone to monitor audio. I don't want to buy another one and I need Line input.
Previousely  on this box I was running Ubuntu 10 then Stella6.3 (mix of Centos6.3) and same headphone  without this problem, so this is not a hardware issue.

ALSA information is located [here]("http://www.alsa-project.org/db/?f=db91ae092c1973d8975e90a741ee6b987737eaed")

I really don't know where to go now to fix this issue.
Any help is welcome.

Many thanks

---

### Post by NrNice on 2014-01-29
Same issue in this thread
[h=2][[SIZE=2]Ghost headphones flickering in sound settings 		[/SIZE]]("http://ubuntuforums.org/showthread.php?t=2132324")[/h]Any idea?

---

### Post by NrNice on 2014-02-04
I tried the following kernels:
Not good is when I have the flickering audio


[LIST]3.11.0-12 => NOT good
3.10.0-031000 => NOT good
3.9.0-030900 => NOT good
3.5.0-030500 => NOT good
3.3.0-030300 => NOT good
3.2.54-030254 => Good
3.2.0-030200 => Good
2.6.39-02063904 => Good
[/LIST]

So, the issue appears from 3.3.0
However I have anothe issue: Sound has statics like old dusty vinyl increasing and decreasing with sound intensity  [IMG]http://forums.linuxmint.com/images/smilies/icon_cry.gif[/IMG] 
This is more difficult to find a fix for that, I think.
Any idea?

BTW, do I need to install other files after installing 2 headers and 1 image?
I installed a virtual as well and I can see it in the grub list. What is this kernel?
Could you have a look here?
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2.54-precise/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.2.54-precise/")

Thanks

---

