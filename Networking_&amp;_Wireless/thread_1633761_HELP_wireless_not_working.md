---
title: "HELP wireless not working"
date: 2010-11-29
forum: Networking &amp; Wireless
---

### Post by mmsmc on 2010-11-29
I am extremly new to this ubuntu, i just downloaded 10.10 my dell insperon mini
the wireless icon says device not ready firmware missing
i have a sprint mifi2200 5F8 (not a usb and no ethernet cable) i have wreless built into my computer and works fine on windows xp

---

### Post by thenetminder33 on 2010-11-29
Okay, before we start trying lots of things go to this forum...

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

Check to see if your card is on the list of cards that work... 
Then execute the commands from the wireless "ticket" on that same forum to get us some info about your card.

---

### Post by mmsmc on 2010-11-29
no i dont see it, Sprint is the manufacturer, they said if i had wifi built in it should work

---

### Post by thenetminder33 on 2010-11-29
Ok no worries... but now go here and get this info so we can dig a little deeper

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

You can post the output of these commands after executing in the terminal... please try to cut out stuff we don't need if you can.

---

### Post by mmsmc on 2010-11-29
here

---

### Post by mmsmc on 2010-11-29
here is the full one

---

### Post by thenetminder33 on 2010-11-29
okay thanks try this command
```
sudo ifconfig wlan0 up
```
let me know what happens then if you scan for networks

---

### Post by mmsmc on 2010-11-29
the code return is no such file or directory

---

### Post by thenetminder33 on 2010-11-29
Ok my mistake... I looked back at the outputs from your tests again and saw that your network card was listed as DISABLED. The ubuntu documentation says that this most likely means that the device is turned off. It may have a hardware switch or it may be able to be turned off and on in windows. Check these things and get back to me.

---

### Post by mmsmc on 2010-11-29
heres the weird paert, the device is on, and when i switch to windows it automatically connects the network, so windows works fine with it

---

### Post by thenetminder33 on 2010-11-29
Try this: Check online to see if their is a linux driver available for you card.
If there is not you might be able to use the Windows Driver through a program called NDISwrapper(*System>Preferences>Windows Wireless Drivers*). If your card came with a cd with the driver on it use that or you could also download it from the internet. Under ndiswrapper select Add Driver then browse for a file ending in .inf use this. If there are more than one option you should use the XP driver in most cases.

---

### Post by mmsmc on 2010-11-29
thank you

---

### Post by thenetminder33 on 2010-11-29
Is it possible that your laptop has a way to turn wireless on and off with the keyboard (A button above the keyboard or a combination using the [COLOR="Blue"]fn[/COLOR] key)?

If so, try turning on your wireless card this way before booting into ubuntu.

---

### Post by mmsmc on 2010-11-29
ive nevr tried that before
help me through this, ubuntu is dual booted with windows xp, so when i pick ubuntu then do i click it? or what?

---

### Post by BCMerlin on 2010-11-29
Hi,

Yesterday I opened a topic about the same prob and I'm also very new in this. I will add the link to my topic here, so you can check mine in the same time. Gives us more options to dissolve...

[http://ubuntuforums.org/showthread.php?p=10172708#post10172708](http://ubuntuforums.org/showthread.php?p=10172708#post10172708)

---

### Post by mmsmc on 2010-11-29
cool

---

### Post by mmsmc on 2010-11-29
BCMerlin, you are having the EXACT same problems im having
HA
THIS SUCKS

---

### Post by mmsmc on 2010-11-29
[[SIZE=1][COLOR=#000000]thenetminder33[/COLOR][/SIZE]]("http://ubuntuforums.org/member.php?u=1148308")[SIZE=1] [/SIZE]: it did not do anything

---

### Post by thenetminder33 on 2010-11-29
What didn't do anything... the ndiswrapper or the turning on the wireless card?

---

### Post by mmsmc on 2010-11-29
the wireless card
what about the  ndiswrapper  i got side tracked

---

### Post by thenetminder33 on 2010-11-29
Okay then, see if you can figure out ndiswrapper using either a driver from a cd or one you downloaded.
Remember to use the .inf file and there should be a corresponding .sys file as well(one with the same name).

Good luck.
I may not be able to get back on till Wednesday or Thursday.
Keep an eye on that other forum as well, your problems appear to be almost identical.

---

### Post by mmsmc on 2010-12-01
solved, this is the post i used 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10012083](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10012083)
This Works

---

### Post by larrystechservice on 2010-12-02
try this:

in terminal run:
rfkill list


if it shows that the device is "sotware blocked" or "hardware blocked" then type:

sudo rfkill unblock wlan

---

