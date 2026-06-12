---
title: "Skype or Ubuntu issue: Camera on 10.04 NOT working"
date: 2010-07-27
forum: Multimedia Software
---

### Post by dreamquartz on 2010-07-27
With updating to 10.04, the camera on my EeePC 1000 does not show test picture on my end, but does show picture on other end.
So far:
1. I can talk and be heard
2. I can can hear when talked to
3. I am seen when camera is on
4. I do not see when camera is on on other side.

Used: [http://www.skype.com/intl/en/get-skype/on-your-computer/linux/post-download/](http://www.skype.com/intl/en/get-skype/on-your-computer/linux/post-download/), [http://www.skype.com/go/getskype-linux-beta-ubuntu-32](http://www.skype.com/go/getskype-linux-beta-ubuntu-32)
Tried: "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype" in Terminal; no success.

Running "Multimedia Systems Selector" shows my camera is working.
"Skype->Options->Video Devices->Select webcam:"  shows: "CNF7129(/dev/video0)"

When testing under Skype, GREEN light next to camera goes on, but the word "Test" remains visible. Hitting "Test" in fast succession again, shows complete white screen filling display.

Is this an Ubuntu or Skype issue?
Driver or setting problem?

Is there a solution available?

Tx

---

### Post by aljoriz on 2010-07-29
For ubuntu go to the TERMINAL type:
  sudo gedit /usr/local/bin/skype

copy paste the following on the new window:
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype
(save and close)
Go back to the terminal: 
Code:
$ sudo chmod a+x /usr/local/bin/skype 

your webcam should work

---

### Post by dreamquartz on 2010-08-01
> **aljoriz said:**
> For ubuntu go to the TERMINAL type:
  sudo gedit /usr/local/bin/skype

copy paste the following on the new window:
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype
(save and close)
Go back to the terminal: 
Code:
$ sudo chmod a+x /usr/local/bin/skype 

your webcam should work

Tried this, but it does not work.
I can create the file, but:** $ sudo chmod a+x /usr/local/bin/skype **leads to: *$: command not found*

Any suggestions?

---

### Post by no2498 on 2010-08-01
not sure if a restart would help or not

look in add&remove for

gstreamer good,bad,ugly,and 10

see if there installed

and i just seen yesterday someone say the uvc driver is not loading

did you try the cam in cheese webcam booth
it should be in sound&video

---

### Post by oldsoundguy on 2010-08-01
same issue here .. no go .. terminal work done and all the gstreamer items installed.  Works in cheese, does not work in Skype.

---

### Post by zazootheparrot on 2010-09-05
I have a sony vaio VGN-SZ740 laptop with ubuntu 10.04.
Both my microphone and webcam are not working so I can't really use Skype!!! :((

Could someone tell me what to do?

Thanks

---

### Post by mtopro on 2010-10-14
dreamquartz

Took a bit to find it but I too had this issue and it was solved here:
[http://ubuntuforums.org/showthread.php?t=993262&page=4](http://ubuntuforums.org/showthread.php?t=993262&page=4)

Seems my problem was i'm on 64bit and i needed to reference the 32bit libraries in the script.  Read the post at the top of the page and give that a try..  Hope it helps!

---

### Post by zazootheparrot on 2010-10-16
Thx for the information! 



> **mtopro said:**
> dreamquartz

Took a bit to find it but I too had this issue and it was solved here:
[http://ubuntuforums.org/showthread.php?t=993262&page=4](http://ubuntuforums.org/showthread.php?t=993262&page=4)

Seems my problem was i'm on 64bit and i needed to reference the 32bit libraries in the script.  Read the post at the top of the page and give that a try..  Hope it helps!

---

### Post by Advorec on 2011-05-18
Aljoriz, this worked great for this eeepc 701 running Skype 2.2, after I edited away the $ sign in the last command ;)

> **aljoriz said:**
> For ubuntu go to the TERMINAL type:
```
sudo gedit /usr/local/bin/skype
```

copy paste the following on the new window:
```
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype
```
(save and close)
Go back to the terminal: 
```
sudo chmod a+x /usr/local/bin/skype
```


Thanks a lot, one more happy customer in the Ubuntu world of wonders!
:KS

---

