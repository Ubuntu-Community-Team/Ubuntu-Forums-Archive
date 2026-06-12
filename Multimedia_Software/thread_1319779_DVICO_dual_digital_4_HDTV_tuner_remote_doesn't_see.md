---
title: "DVICO dual digital 4 HDTV tuner: remote doesn't seem to be working"
date: 2009-11-08
forum: Multimedia Software
---

### Post by s3019293 on 2009-11-08
Hi all,

After buying my dvico dual digital 4 HDTV tuner I found what seems to be a pretty simple tutorial to install the hardware on Jaunty at...
[HTML]https://help.ubuntu.com/community/DViCO_Dual_Digital_4[/HTML]

Everything went well in the tutorial until I got to the point where I did a ....

sudo hex /dev/input/irremote

Apparently when viewing this file you should be able to see output as buttons get pressed however this just didn't happen for me.

I installed lirc using ubuntu package manager. 

Has anyone got any hints for me to troubleshoot the problem?

Also, there was a little unusual cable that came with my tuner and it's not really clear from the instructions of what this is for. I think this is the infrared receiver for the remote. Am I right? Does this need to be plugged in and do I need to be pointing the remote at it when pressing buttons?

Thanks for the help

---

### Post by s3019293 on 2009-11-10
bump

---

### Post by Kevin McIsaac on 2009-11-11
Firstly, you need to ensure you have plugged the IR receiver into the card. This is a long black cord with a plug at one end and a square plastic thing at the other end that has the IR "eye". When you use the remote this is the thing that picks up the signal.

This cable plugs into the back of your PC into the DVICO card. If you dont' have this plugged in it will not work.

When you followed the tutorial, did you get the output that are expected, i..e, 

[LIST]
[*]were the devices found in dmesg?
[*]Does HAL create the irremote file and is it liked to the right /dev/input device?
[/LIST]

---

### Post by s3019293 on 2009-11-11
Thanks Kevin. I wish the instructions from the box would have told me what I needed to do with the IR reciever. Thanks for the info.

Yep everything else in the tutorial worked. i.e. Both devices were found and the remote was linked to the first device.

Tonight I will try it with my IR reciever plugged in ;).

---

