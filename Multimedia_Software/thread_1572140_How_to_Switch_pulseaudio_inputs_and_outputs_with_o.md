---
title: "How to: Switch pulseaudio inputs and outputs with one click"
date: 2010-09-10
forum: Multimedia Software
---

### Post by whit on 2010-09-10
With pulseaudio handling sound on Lucid (10.04), when I plug in my USB headset it's recognized, but there was no easy way to have it be used without going to System > Preferences > Sound > Input & Output and checking the radio buttons. Then if it's unplugged, and plugged in again later, the setting has been lost, so it was back through the menus. Not good when the headset's not plugged in and I'm fumbling to answer a Skype call. What would be ideal is if pulseaudio could prioritize and always default to the headset when it's plugged in. But I'm told by one of the pulseaudio gods (Col) that it can't yet.

Here's a way to at least get the switch down to one button on the panel bar.

0. Get all your devices plugged in

1. Find your outputs (speakers, headphones):

> pacmd list-sinks | grep alsa_output

2. Find your inputs (such as a microphone):

> pacmd list-sources | grep alsa_input

3. Write a bash file to choose one or both, like this but with device names appropriate to your system which you've discovered above for the alsa_output.* and alsa_input.* strings.

> #! /bin/bash

pacmd set-default-sink alsa_output.usb-Generic_FREETALK_Everyman_0000000001-00-Everyman.analog-stereo
pacmd set-default-source alsa_input.usb-Generic_FREETALK_Everyman_0000000001-00-Everyman.analog-stereo

exit 0

Save this file and run "chmod 700" to make it executable. 

Then right click on a panel (that is, the bar on the top or bottom of your desktop), choose Add to Panel > Custom Application Launcher > Type: Application, Name: [whatever you like], Command: /path/to/your/bash/file. You can also click on the icon to choose a different one. I like audio-input-microphone.svg I found in /usr/share/icons/Humanity/devices/24, but anything is fine. Now you have a button to switch quickly to the headset you've just plugged in. 

This can of course be used for other switching between sound inputs and outputs too, if you create a button for each.

---

### Post by Furry_Fighter_20x66 on 2010-09-11
Thanks whit:

I found this very useful. I hope they can fix this because I have one user who does the same thing you describe with skype and is a 'I remember the patterns I have to click to make things work' kind of guy. Even simple changes to the usual patterns of clicks really baffles him (you should have seen how crazy he got when the dialog box for Open Office changed after one update). I just recently moved him from 8.04 to 10.04 and while he's doing not bad adapting, trying to explain to him how to change the audio over for his skype calls each week blew his mind.

If you can figure out a way to make it fully automatic that would be even better.

---

### Post by whit on 2010-09-11
> **Furry_Fighter_20x66 said:**
> If you can figure out a way to make it fully automatic that would be even better.

I'm told there should be a way involving putting a file with the right code into /etc/udev/rules.d. It could spot the device being plugged in and run the script then. Spent a while fussing with it, but haven't got the trick of it yet.

---

### Post by Furry_Fighter_20x66 on 2010-09-11
I found this thread on writing rules for USB hard drives.[http://ubuntuforums.org/showthread.php?t=1290438]("http://ubuntuforums.org/showthread.php?t=1290438")

I also have found this link with instructions for adding drivers to a certain brand of USB speakers, with instructions on the very bottom for adding a udev rule that *should* be close to what we need. [http://www.astro.caltech.edu/~mcs/tascam_us122/index.html]("http://www.astro.caltech.edu/~mcs/tascam_us122/index.html")

I will unfortunately not have a chance to try this until about Wednesday of this upcoming week when I can get ahold of his laptop and the USB headset.

---

### Post by whit on 2010-09-12
This was the advice I got on the pulseaudio list from Frode Severin Hatlevik:

> The way to piggyback on plugging in hardware on Debian/Ubuntu is writing udev rules. I recently had to teach myself a bit of rulewriting to fix an issue with ConsoleKit and device node ACL permissions.

If you venture into this, have a look at the manual for the '--attribute-walk' command of udevadm. On my system the command udevadm info --query=name --name=/dev/snd/controlC0 --attribute-walk lists all the possible matching criteria for the controlC0 device node. Also keep in mind that udev seems to only take the first two matching kriteria in a rule into account, and in your case theese should identify the mic uniquely. The rule could the trigger en external script. The rule should be numbered somewhere in the 80's I suppose, since by then most of the other rules dealing with sound have been processed.

So that should provide the clues to integrate with the example in the caltech.edu link you found. In my case, since there is already built in speakers and microphone, the usb headset shows up at /dev/snd/controlC1. Think this should actually go in the low 90s to come after the pulseaudio udev rules, which are 90.

Still can't get the udev method to work though. The caltech.edu example by the way uses some deprecated syntax, which udev will complain about in syslog. Seems easy enough to copy the right syntax from the udevadm output. But it still doesn't yet for me result in the script running successfully. It may be that there's some timing issue, that pacmd isn't ready yet when the command gets to it from the script. Just guessing on that.

---

### Post by spidernik84 on 2010-12-19
Hi whit,
I stumbled upon your thread from Google. Same need to auto-switch to usb on plug, and still no success.
As you said, the udev rules seems to work but it seems not to be able to trigger the switch.
I tried to add a "sleep 5" command in the script with no go. This is my Udev rule, btw:

```
SUBSYSTEMS=="usb", ATTR{idVendor}=="1460", ATTR{idProduct}=="3286", ACTION=="add", GROUP="audio", RUN+="/home/spidernik84/scripts/switch-audio.sh"

```

---

### Post by peyu on 2010-12-27
Hi all, I have a usb mic and I want to set it as the default source once plugged. I googled a bit to find some solutions, and now it works !!!

First, I don't know why, but udev will wait until the rule end to set up the new input, so I run the script in "background". Here is my udev rule:

```
SUBSYSTEMS=="usb", ATTR{idVendor}=="046d", ATTR{idProduct}=="08ae", ACTION=="add", GROUP="audio", RUN+="/bin/bash -c '/home/peyu/callquickcam.sh &'"
```

Here is callquickcam.sh:

```
#!/bin/bash
su peyu -c /home/peyu/quickcam.sh
exit 0

```
And here is quickcam.sh:

```
#! /bin/bash
sleep 4s
pacmd set-default-source alsa_input.usb-046d_Camera-01-default.analog-mono
exit 0

```

You need 2 files because pacmd has to be runned with your username (in my case peyu).
I hope this helps !

---

### Post by c901906 on 2010-12-28
Thanks for this thread you guys!

But... Am I the only one that thinks the “Sound Preferences” dialog should allow a default selection?

;)

---

### Post by afrodeity on 2012-01-25
I have a USB headset and mic which has to be manually set via sound preferences. Is there a way of doing this with one click?

---

