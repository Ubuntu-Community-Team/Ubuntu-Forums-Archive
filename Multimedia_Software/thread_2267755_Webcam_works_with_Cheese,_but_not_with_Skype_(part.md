---
title: "Webcam works with Cheese, but not with Skype (part 2)"
date: 2015-03-03
forum: Multimedia Software
---

### Post by Jere_Tuominen on 2015-03-03
OLD SOLVED ISSUE FOR REFERENCE [CLOSED]
[http://ubuntuforums.org/showthread.php?t=993262](http://ubuntuforums.org/showthread.php?t=993262)

Problem:
Old webcam works with Cheese Webcam Booth but not with Skype. Skype gives just a black screen. I am using all the latest updates and upgrades on Ubuntu 14.04 LTS 64-bit. 

lsusb
```
Bus 004 Device 002: ID 093a:2600 Pixart Imaging, Inc. Typhoon Easycam USB 330K (newer)/Typhoon Easycam USB 2.0 VGA 1.3M/Sansun SN-508
```

Old solution was to edit a script.

[COLOR=#000000]sudo gedit /usr/local/bin/skype[/COLOR]
```

[COLOR=#000000]*#!/bin/bash*[/COLOR]
[COLOR=#000000]*LD_PRELOAD=*[/COLOR]/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so [COLOR=#000000]*/usr/bin/skype*[/COLOR]

```

Skype video keeps as black. [COLOR=#000000][I]What to do? Thanks for your tips!

[/I][/COLOR]

---

### Post by Melano Chole on 2016-02-11
I've got the same issue. kubuntu 14.04 64 bit, Skype 4.3.0.37, kernel 3.13.0-77-generic
Webcamera ***A4Tech PK-130MJ*** gives an appropriate image in guvcview, but in Skype there is only a black window.
First, the modules could not be preloaded in the case of running i386 skype on a x86_64 system. Then the command in the above is ignored. This can be fixed by
```
sudo apt-get install libv4l-0:i386
```
The 32-bit v4l1compat.so and v4l2convert.so are placed in another place, so the right script should read in this case:
```
#! /bin/bash
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype
```
Unfortunately, in my case preloading both of the libraries doesn't help. Skype still shows a black screen.

---

### Post by shantiq on 2016-02-17
well ths is what I do everytime

i open skype check the video and it is black
I leave it open then open cheese and it is black
So I turn it off and grab the cam usb at the back of the computer pull it out and put it back in
Then i fire cheese up again this time [B]it works
[/B]Thw whole time skype is sitting there
So I now turn cheese off; go to the settings on skype and check the video [B]now it works
[/B]done this for over a year now; i do not understand it or wish to think about it; it works that way :]


may give you some idea maybe ...

---

