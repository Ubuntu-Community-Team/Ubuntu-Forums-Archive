---
title: "No Audio after TV is turned off, MythFrontEnd"
date: 2015-08-12
forum: Mythbuntu
---

### Post by Antonio_Carballo on 2015-08-12
I'm running the Mythbuntu 14.04 with a LIVA HTPC. I'm connected to my TV via HDMI. MythFrontEnd works great as long as the TV is on. Once it's turned off for a long period (say overnight), the next morning the video is shown but the sound is dead. The problem affects any application that uses audio in Mythbuntu.

When I go to run the "speaker-test" and tell it to test the HDMI, nothing comes out. Total silence. I have done the exact same test when the audio is working and the white noise can be heard.

This is when it gets interesting. I reboot the machine and the sound comes back...well, until the TV is turned off and stays turned off for a long time.

I have gotten a log for MythFrontEnd (before and after the sound goes off) and I cannot find any errors or differences in the log. When I do the sound test inside MythFrontEnd, the TV stays silent. It is almost like something has completely turned off the sound.

At this point I'm at at dead-end. I have researched everywhere and nothing comes up and tells me, 'you dummy, you need to do <fill in action>!". So, I'm asking for help on this issue. Thank you and have a great day.

/Antonio

---

### Post by Lester_Burnham on 2015-08-12
Hi,

I'm no expert on this, but you could try a few things with xrandr.
Maybe run:
```
xrandr --prop
```
before and after it happens and compare the two.

You could also try the following to see if it reconnects.
```
xrandr --auto
```

Once you find the issue, you may be able to just disable the 'useEDID' option in xorg.conf and set it through xrandr. I doubt that's the issue though, as it seems pulse or whatever you are using, thinks it's disconnected.

So, how are you running this system? It's a backend/frontend that runs 24/7, connected to the TV.

Lester

---

### Post by Antonio_Carballo on 2015-08-12
I set up a VirtualBox VM in my MacMini for the back-end v0.27. It runs 24/7 w/o any problems. That part is pretty much hassle-free.

The front-end is another issue. I'm going to turn off the Pulse Audio in my Start-Up settings. I use ALSA for the front-end. The MythTV wiki said to stay away from Pulse and stick with ALSA. Thanks for the feedback.

---

### Post by Antonio_Carballo on 2015-08-13
Oh well. Turning off the Pulse Audio did nothing to prevent the sound from going silent....It's time to try another product as this issue is a deal breaker for everyone in the family.

---

### Post by khPWXxF on 2015-08-15
I wonder if this is the same as the no picture problem?
See
[http://ubuntuforums.org/showthread.php?t=2282465](http://ubuntuforums.org/showthread.php?t=2282465)
Phil

---

### Post by Antonio_Carballo on 2015-08-16
I was aware of that problem but I fixed it by disabling the [COLOR=#333333][FONT=monospace]xfsettingsd in the Start-up. The sound problem could be related to disabling the [/FONT][/COLOR][COLOR=#333333][FONT=monospace]xfsettingsd[/FONT][/COLOR][COLOR=#333333][FONT=monospace]....I'm going to try the patch for the [/FONT][/COLOR][COLOR=#333333][FONT=monospace]xfsettingsd instead of just turning it off completely.

[/FONT][/COLOR]

---

