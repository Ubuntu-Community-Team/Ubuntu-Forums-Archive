---
title: "HDMI connection"
date: 2013-03-11
forum: Multimedia Software
---

### Post by gavdari on 2013-03-11
I'm using an HDMI cable to connect my laptop to a TV to watch movies etc. What I'm looking for is somehow automatically do something whenever an HDMI cable is connected:

1. The audio should be transferred to the TV.
2. The display on the laptop should be turned off.

Apparently the first one is something almost impossible. I found this script ([http://askubuntu.com/a/265539](http://askubuntu.com/a/265539)) which I used and at first it worked completely fine, with one little flaw. The sound output switches to HDMI when an HDMI cable is connected, but it won't switch back to the laptop when it's disconnected. But after a few tries it stopped working completely.
The second one is still a mystery, and I hadn't find anything to do that.
Is there anyway to do so without all these hassles? Windows does this easily and it's kind of disappointing to see my beloved OS struggling to work as it should.
Any help is much much appreciated.

---

### Post by uc50_ic4more on 2013-03-11
When I was using XFCE in Arch, I had this script run when the HDMI cable was plugged in:

> #!/bin/bash

# activate HDMI
xrandr --output HDMI1 --mode 1920x1080 --pos 1366x0 --rotate normal --output LVDS1 --mode 1366x768 --pos 0x0 --rotate normal --output DP1 --off --output VGA1 --off

# set audio to HDMI
pactl set-card-profile 0 output:hdmi-stereo+input:analog-stereo

The first part is related to activating, placing and scaling the external device; the second is involved in changing the audio output.

---

### Post by gavdari on 2013-03-11
Perfect. It worked just fine. Thank you. Now I have two scripts named 'hdmi-connect' and 'hdmi-disconnect'. Running each will do exactly what I want. But I have just one more newbie question. How can I set Ubuntu to run the appropriate script automatically?

---

### Post by gavdari on 2013-03-15
Just for future reference, here's what I did.

I created two scripts, named hdmi_connect and hdmi_disconnect. The contents are:

hdmi_connect:
```
#!/bin/bash
xrandr --output HDMI1 --mode 1920x1080
xrandr --output LVDS1 --off
pactl set-card-profile 0 output:hdmi-stereo+input:analog-stereo
```

hdmi_disconnect:
```
#!/bin/bash
xrandr --output HDMI1 --off
xrandr --output LVDS1 --mode 1366x768
pactk set-card-profile 0 output:analog-stereo+input:analog-stereo
```

I have to run these scripts manually when I connect or disconnect HDMI connection. Apparently, there is no way to do it automatically at the moment, because udev only detects 'CHANGE' in HDMI status and doesn't differ between connect and disconnect.

---

### Post by fj401971 on 2013-03-15
You could either link the script to a keybinding or you could link it to an applet icon...

For keybinding, in 10.04, System >> Preferences >> Keyboard Shortcuts
Modify a key and enter your script under the "Command" column.

Applet icon...  Right-click on the top panel, click "Add to Panel" >> Custom Application Launcher

---

### Post by gavdari on 2013-03-16
Yep, that's what I did. I've added two launchers to the unity launcher, which will run the scripts.

---

