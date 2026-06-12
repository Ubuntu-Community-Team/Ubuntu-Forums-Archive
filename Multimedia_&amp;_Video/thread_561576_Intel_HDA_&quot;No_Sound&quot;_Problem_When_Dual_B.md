---
title: "Intel HDA &quot;No Sound&quot; Problem When Dual Boot With XP"
date: 2007-09-27
forum: Multimedia &amp; Video
---

### Post by dumshi on 2007-09-27
Hi,

It so happened that one day i was watching movie on my newly installed Ubuntu using Totem Movie Player. Then suddenly Totem Movie Player did not respond when i used the Volume Dial on my laptop ( but the movie was still playing ). 

The next day, i brought my Laptop to my College and boot into XP. Since, i was in class i quickly lowered the volume and mute the Volume using the Volume Dial button mounted on my Laptop. Then i went on note-taking and that's how my day ended.  But night was about to unfold something else. Something that took me about 2 hrs to figure out.  Yes! I had no sound on Ubuntu when i truly recall having sound on XP. Then i went solution hunting but with no luck. Disabled/Enabled anything that said Jack,ALSA,OSS, even disabled the ALSA service in fear of some audio program trying to hi-jack my audio device.

SOLUTION:

Then I remember that i mute'ed the VOLUME on XP and thought would that silence the whole audio device ? To my surprise after i un-mute the volume  on XP and increase the volume and went back to Ubuntu and TADA .. there's the Sound.

It's strange how Linux couldn't do it on it's own. This shouldn't be a problem for most single booters and so people in IRC couldn't solve it. But i am glad i went there and saw so many people trying to figure out and solve other's problem. Cheers Guys!!


in Short:

Boot into XP / VISTA 
Un-mute the Volume (Increase it to a bit might help as well)
Restart and Boot to Ubuntu
Sound should be heard...

:)

*Note: It might not work for everybody. I am just posting because i think it's a solution because it worked for me. :D

---

### Post by lisati on 2007-09-27
My best guess is that there's something in your hardware that Vista used to change your settings, that carried over to Ubuntu.

---

### Post by Xinef on 2007-09-30
That sounds like bad news for me.
I have been trying everything to get sound on my machine and it didn't work.
I admit I haven't tried your solution yet, as a matter of fact, I uninstalled windows to work with Linux...
Does anyone have a windows live boot CD that can control sound to suggest ?
Or a work around for this... orz

---

### Post by vizitorq on 2007-10-01
i am having the same issue on my dual-boot ubuntu/XP pavilion laptop. except, when i tried your method, that didn't work for me. i am considering getting rid of windows altogether specifically for this reason. i hate windows anyway, but i do NOT want windows to win this one because sound works on windows and not on linux.

it used to work on linux, then one day i boot into windows, and then reboot into linux, no sound... i am irate. what do i do? i have literally tried EVERYTHING. i even recompiled the newest version of alsa. no dice. i need help!

---

### Post by dumshi on 2007-10-02
Hi,

Did you try un-mute'ing via OEM drivers rather then Windows Built in ?


I have "Intel HDA " on Toshiba Tecra M7 and i installed every driver that is available from Toshiba Website for XP and Vista including Sound (Realtek ). So, booting just from Windows PE CD or Via windows drivers won't do the trick ? (maybe) .. 

Just a guess, haven't tested anything yet..

Good Luck ..

---

### Post by Xinef on 2007-10-02
After a few more hours fighting with the thing, I tried throwing in a Knoppix CD and guess what ? Sound came out, not from the speakers but from the headphones only. At least it was a proof that Windows was not involved. So after compiling the latest RC of the test alsa drivers and forcing my USB built-in webcam microphone to be recognized not as a sound card, I finally got sound coming out of my speakers. It is not a perfectly working setting (built-in mic not working, one of the headphone plugs not working...) but at least I got sound and this is as close to normal I could get.
So if your sound is not working, try to boot a live CD like Knoppix and just in case, plug your headphones, that is if unmuting under windows didn't work...

---

### Post by wolfen69 on 2007-10-02
try this [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_work_with_Intel_Integrated_Sound_Cards](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_work_with_Intel_Integrated_Sound_Cards) it has worked for me.

---

