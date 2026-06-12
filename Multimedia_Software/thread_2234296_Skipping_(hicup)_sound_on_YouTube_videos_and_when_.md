---
title: "Skipping (hicup) sound on YouTube videos and when playing Music."
date: 2014-07-13
forum: Multimedia Software
---

### Post by carmichaelits on 2014-07-13
**Sound is skipping**, well more of a hicup really. It can be really bad on  **YouTube** and can effect playing music on **Rhythmbox** or** VLC**.

*(Edit: Using Ubuntu 14.04)*

When  the hicup happens its like it has forgotten that it played the last second of audio, so then plays it again. Example, if the song was "la  la I'm singing a song" it would occasionally play "la la I'm singing  singing a song", **like a dirty CD**.

Very strange. I have already done some reading  up on it **on the forums**. People are saying that its got **something to do**  **with Pulse** something or other. I **followed the advice** of a member and ran  a sudo command that I believe was **to remove** said **Pulse**  application/package. After removing this** I went to change my desktop  background** and noticed **my system settings manager had gone**, I have **no  idea** if these are connected in anyway. I **installed the system settings  back on** from the Software Centre. But looks like the **hicup in the audio  is still here**.

It can get really bad on some videos, doing it  every 10-15 secs. Other videos its fine. Same goes for Music, I can go  through 4-5 tracks before I notice it. Very strange.

I'm trying  to pick Ubuntu back up again, I was using it years ago when the fancy  Unity thing'mic'boob wasn't there. I come from a heavy windows IT tech  background and Ubuntu is just so fresh. I have a secret love for Ubuntu I  think. Although this sound thing is chipping away at my moral a little.  I was going to buy a semi-beefy new laptop with no operating system and run it on  Ubuntu, but I couldn't handle it if it had this skipping audio thing.  Its very irritating.

Please help Ubuntu community, I will be forever grateful and be sure to annoy you more in the future, when the next problem arises.
[U]
**System Info (Hardware things that I think may effect the sound if known problematic with Ubuntu):**[/U]

[LIST]
[*]Motherboard: M3N78-PRO - [http://www.asus.com/Motherboards/M3N78_PRO/](http://www.asus.com/Motherboards/M3N78_PRO/) 
[*]Processor: AMD Phenom 9650 
[*]GPU: 9800GTX+ (Using proprietary drivers 331.38 tested) 
[*]Samsung EVO SSD 830 120GB 
[*]No Sound Card, using the built in motherboard sound card. 
[/LIST]

---

### Post by Yellow Pasque on 2014-07-14
Worth a try: [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)

---

### Post by carmichaelits on 2014-07-14
Deleted

---

### Post by carmichaelits on 2014-07-14
Nice one, although; not finding this wiki page now makes me feel like a dirty lazy noob. Although the problem now seems to be fixed, thanks for your help Temujin. 

Here is what I done for other dirty lazy noobs [SIZE=1](disclaimer: this term is not men't in a derogatory manner)[/SIZE] like me.

**System and Hardware**

Running System Ubuntu 14.04 LTS

Download and installed HardInfo aka "System Profiler and Benchmark"- you can find it on the Software Centre searching this. This was just to check what Ubuntu was calling my sound card/driver/chip.

You can find what sound you have under Computer > Summery -] Multimedia > Audio Adapter[INDENT]
In my case it says HDA-Intel - HDA NVidia [/INDENT]

**Testing Method**

I am using this video to test [https://www.youtube.com/watch?v=G9naXmOYAdE](https://www.youtube.com/watch?v=G9naXmOYAdE) This for me seemed to skip a lot during testing.

Testing was done with google chrome with pepper flash disabled. (although having pepper flash disabled probably had nothing to do with this fix)[INDENT]
To disable Pepper flash type chrome://plugins into your url bar (making sure to click the one with the folder icon and not the search icon) and click to disable Adobe Flash Player 14. Doing this will use the the same flash player that firefox uses.[/INDENT]

**Fix Method 1 - HDA Intel Config**

There are two settings you can choose from trying this fix, ether setting the number at the end to a 1 or a 2. Here is what I done.

**_Variation 1_**

Opened terminal and enter:
```
sudo gedit [COLOR=#333333][FONT=Ubuntu Beta]/etc/modprobe.d/alsa-base.conf[/FONT][/COLOR]
```

Enter your user account password.

This will open the HDA Intel sound card configuration file.

Add the following at the bottom (in a new line):
```
# Skipping audio fix
[COLOR=#333333]options snd-hda-intel position_fix=1[/COLOR]
```

Click save and restart[INDENT]_Result on this test for me:_[COLOR=#ff0000]FAILED[/COLOR]
[/INDENT]

[U]**Variation 2**

[/U]Same as above but change the end number to 2.

Click save and restart[INDENT]_Result on this test for me:_[COLOR=#ff0000]FAILED[/COLOR][/INDENT]

**Fix Method 2 - PulseAudio**

Open terminal and enter:
```
sudo gedit [COLOR=#333333][FONT=Ubuntu Beta]/etc/pulse/default.pa[/FONT][/COLOR]
```

Enter your user account password.

This will open a PulseAudio configuration file.

Find and change the following line from:
```
[COLOR=#333333]load-module module-udev-detect[/COLOR]
```
to
```
[COLOR=#333333]load-module module-udev-detect tsched=0[/COLOR]
```

Click save and restart[INDENT]_Result on this test for me:_[COLOR=#008000]PASSED[/COLOR][/INDENT]

Thanks to Temujin for providing the wiki page that I was to lazy to look for.

---

