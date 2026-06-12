---
title: "Snapstream Firefly Mini Keycodes"
date: 2007-11-20
forum: Mythbuntu
---

### Post by twkisner on 2007-11-20
Not wanting to patch the Kernel as suggested in the MythTV wiki I posted the keycodes and instructions on the Mythtv wiki ([http://www.mythtv.org/wiki/index.php/Snapstream_firefly_mini](http://www.mythtv.org/wiki/index.php/Snapstream_firefly_mini)), but since I seached the web previously and couldn't find the keycodes anywhere, I thought I would post them here too:

Close = 175 
Mute = 160 
Last = no keycode in XEV
Exit = 234 
VOL+ = 176 
VOL- = 174 
Option = 134 
Firefly = no keycode in XEV 
Menu = 158 
Record = 177 
Guide = no keycode in XEV 
Stop = 164 
Prev|<< = 144 
Play = 179 
Next>>| = 153 
REW<< = 152 
Pause = 110 
FFWD>> = 180 

Save someone else the trouble of running XEV.

Also, I wanted to know if anyone knew of the "proper" way to modify the keycodes in the xwindows init?  Right now, I just have the settings in a text file and run "xmodmap /mypath/keys.txt" in the startup programs in Xfce. I'm sure this is the easiest way to do it with Mythbuntu, but if I was still running the Fiesty packages that wouldn't have been an option.

I tried to put them in /usr/X11/xinit/Xmodmap and /etc/X11/xinit/xinirrc, but it didn't work.  Not a big deal, just curious if someone knew.

---

### Post by superm1 on 2007-11-20
> **twkisner said:**
> Not wanting to patch the Kernel as suggested in the MythTV wiki I posted the keycodes and instructions on the Mythtv wiki ([http://www.mythtv.org/wiki/index.php/Snapstream_firefly_mini](http://www.mythtv.org/wiki/index.php/Snapstream_firefly_mini)), but since I seached the web previously and couldn't find the keycodes anywhere, I thought I would post them here too:

Close = 175 
Mute = 160 
Last = no keycode in XEV
Exit = 234 
VOL+ = 176 
VOL- = 174 
Option = 134 
Firefly = no keycode in XEV 
Menu = 158 
Record = 177 
Guide = no keycode in XEV 
Stop = 164 
Prev|<< = 144 
Play = 179 
Next>>| = 153 
REW<< = 152 
Pause = 110 
FFWD>> = 180 

Save someone else the trouble of running XEV.

Also, I wanted to know if anyone knew of the "proper" way to modify the keycodes in the xwindows init?  Right now, I just have the settings in a text file and run "xmodmap /mypath/keys.txt" in the startup programs in Xfce. I'm sure this is the easiest way to do it with Mythbuntu, but if I was still running the Fiesty packages that wouldn't have been an option.

I tried to put them in /usr/X11/xinit/Xmodmap and /etc/X11/xinit/xinirrc, but it didn't work.  Not a big deal, just curious if someone knew.
That is the most effective way to do it.  Putting them anywhere else in the filesystem you risk losing them during upgrades.

If this was on feisty's ubuntu-mythtv-frontend, you would have to put them elsewhere and lose it on an upgrade.

---

### Post by SgtDude on 2009-10-07
I've used the above list on previous versions of Ubuntu, but when I upgraded from 8.04 to 9.04 (to get Miro), the firefly's mapping changed on me.

Here's the list for 9.04

Close = 214
Mute = 121
Last = no keycode in XEV
Exit = 166
VOL+ = 123
VOL- = 122
Option = 138
Firefly = no keycode in XEV
Menu = 147
Record = 175
Guide = no keycode in XEV
Stop = 174
Prev|<< = 173
Play = 215
Next>>| = 171
REW<< = 176
Pause = 127
FFWD>> = 216

Thanks to the guys above for saving me time in the past.  Hopefully this list will save other people time in the future.

---

### Post by klc5555 on 2009-10-07
> **superm1 said:**
> That is the most effective way to do it.  Putting them anywhere else in the filesystem you risk losing them during upgrades.

If this was on feisty's ubuntu-mythtv-frontend, you would have to put them elsewhere and lose it on an upgrade.

In Gutsy I discovered that installing k3b would disable the following keycodes: 160, 174, 176, and 144. I don't know why. Uninstalling k3b re-enabled the affected keycodes. 

Otherwise, the Mythtv volume and mute shortcut keys had to be routed to other keycodes on the mini-Firefly. Which made the mini-Firefly remote itself fairly useless, except as a master from which other learning remotes could be programmed. 

I still use my k3b-modified keys.txt from Gutsy in Jaunty (clean install), and haven't experienced the re-mapping described by SgtDude.

---

