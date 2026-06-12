---
title: "A simple piano - vmpk and qsynth"
date: 2013-06-24
forum: Multimedia Software
---

### Post by grantbow on 2013-06-24
In case anyone else wants a simple keyboard piano like I did, here's what I found works on my Ubuntu 12.04 LTS system. In hind sight what I really wanted was to produce MIDI commands (using vmpk) and use a synthesizer (qsynth) to play them. Jack audio isn't needed for this simple setup.

[INDENT]```
sudo apt-get install qsynth vmpk
```[/INDENT]

The trouble is you have to always go into vmpk Edit...Connections... and select the output which keeps changing. Using *aconnect -i* and *acconnect -o* I found the input and outputs I needed. Then to connect the vmpk output the qsynth input I use *acconnect* command instead of the GUI. So to start the programs and connect do:

[INDENT]```
qsynth &
vmpk &
aconnect 128:0 130:0
```[/INDENT]

The *&* backgrounds the processes/commands. I put these three commands in a file */home/<myusername>/bin/piano*. Don't forget to *chmod +x piano* to make it executable and add the line *#!/bin/bash* to the beginning so that when you type piano it runs those commands.

To make it a little prettier I went into qsynth Options... and checked "enable system tray icon" and "start minimized to system tray". Due to some bug I could not get to the quit menu that should have been there so I use *killall qsynth* that I put in a file at */home/<myusername>/bin/killpiano*. Again *chmod +x killpiano* and add the line *#!/bin/bash* to the beginning.

Now to begin I type *piano* and start playing from my keyboard.

When I am done I close the vmpk with the close box and type *killpiano*.

I hope this helps someone follow along the path I spent time finding myself.

---

