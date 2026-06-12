---
title: "Missed Media/trick keys with Kodi"
date: 2018-01-07
forum: Multimedia Software
---

### Post by lindend on 2018-01-07
System: iMon SoundGraph w/Ubuntu 16.04 LTS.   

Stop, rewind, fastforward, skip keys aren't being reliably received by kodi.  The remote control keys are seen with both xev and ir-keytable.

If I use

ir-keytable -t

I see the keys being detected properly for each keypress.

1514870968.417661: event type EV_MSC(0x04): scancode = 0x2b8115b7
1514870968.417661: event type EV_SYN(0x00).
1514870968.671678: event type EV_KEY(0x01) key_up: KEY_FASTFORWARD(0x00d0)
1514870968.671678: event type EV_SYN(0x00).
1514870968.889661: event type EV_MSC(0x04): scancode = 0x2a8195b7
1514870968.889661: event type EV_KEY(0x01) key_down: KEY_REWIND(0x00a8)

Here are the details on the device from ir-keytable

        Driver imon, table rc-imon-pad
        Supported protocols: other rc-6
        Enabled protocols: other
        Extra capabilities: <access denied>

---

### Post by lindend on 2018-01-07
I've disabled all the sound & media keyboard shortcuts in the Unity keyboard settings.  

One odd thing is if I hold down fast forward or rewind, Kodi will occasionally get a single key (while ir-keytable shows the key being held down).  Other times, I see Kodi report a scan code, but no OnKey in the debug log.

In these kodi logging statements, I used xmodmap to map FastForward to the 'f' key to see if something was grabbing XF86AudioForward

13:23:29.909 T:139923952785792   DEBUG: Keyboard: scancode: 0xd8, sym: 0x0066, unicode: 0x0000, modifier: 0x0
13:23:50.395 T:139923952785792   DEBUG: Keyboard: scancode: 0xd8, sym: 0x0066, unicode: 0x0066, modifier: 0x0
13:23:50.395 T:139923952785792   DEBUG: OnKey: f (0xf046) pressed, action is FastForward
13:23:50.395 T:139923952785792   DEBUG: Keyboard: scancode: 0xd8, sym: 0x0066, unicode: 0x0000, modifier: 0x0

---

### Post by lindend on 2018-01-08
Another data point I forgot to mention.  Neither kodi nor xev see the 

KEY_PREVIOUS or KEY_NEXT 

events that ir-keytable reports. 

I even tried connecting a standard MCE remote and it has the same symptoms.  ir-keytable reports the 

KEY_PREVIOUS or KEY_NEXT 

events but nothing is seen by xev or kodi for these events.

Any idea how I can debug who's grabbing these events?  As mentioned earlier, the Unity keyboard settings have all media related shortcuts disabled.

I wonder if the two issues (no KEY_PREVIOUS/KEY_NEXT and mostly missed trick keys) are related?

---

### Post by lindend on 2018-01-09
Experimenting some more trying to figure out why KEY_PREVIOUS and KEY_NEXT aren't seen by xev or kodi while they are detected by ir-keytable.  I brought up the unifi keyboard shortcut settings.  It sees all the media keys except KEY_PREVIOUS and KEY_NEXT too.  Is there something that could be grabbing these keys before unifi shortcuts after ir-keytable sends them or could there be a bug with how ir-keytable is propagating these two events?

---

### Post by lindend on 2018-01-10
Solved the next/previous issue.  After reading a bunch of threads, turns out those values are outside the range for X.  Modified the imod-pad keytable to use KEY_NEXTSONG and KEY_PREVIOUSSONG instead and they work perfectly in Kodi without any additional mapping (they also are detected by Unity).  Now just need to figure out why the rest of the media keys aren't detected reliably.

---

### Post by lindend on 2018-01-10
I think I have a workaround.  Map the media keys at the ir-keytable level rather than with xmodmap.  With initial testing, this seems to work.  However, I'd still like to get to the bottom of what could be causing Kodi to miss media key presses whereas 'F', 'R', 'X' etc seem to work.

---

### Post by fastcoast123 on 2018-11-22
> **lindend said:**
> I think I have a workaround.  Map the media keys at the ir-keytable level rather than with xmodmap.  With initial testing, this seems to work.  However, I'd still like to get to the bottom of what could be causing Kodi to miss media key presses whereas 'F', 'R', 'X' etc seem to work.

I've struggled quite a bit to get ir-keytable / evdev working on my intel NUC running Lubuntu 18.04. I removed LIRC and had ir-keytable installed.  I could get all the buttons to show up when running ir-keytable -t, but not all would register in mythtv frontend, or xev.  For example, the "back" button on the remote wouldn't work in myth or xev, but most other buttons worked.

I tried so many things, even installing an old version of LIRC, which failed.  Finally I was able to change the keybindings that were in place by Openbox to get things to work.  I wanted to share this info in case it helps someone.  

So Lubuntu runs LXDE and Openbox.  Looks like Openbox was "swallowing" certain remote buttons-- the "media keys" and others.  
I was able to modify ~/.config/openbox/lubuntu-rc.xml 
and remove some keybindings there, and success!  All the buttons would register in mythfrontend and xev. However, I couldn't get this to work with autologin.  I could change the settings for my account, but not when autologin was enabled.  I tried modifying the root user openbox configuration, and the config in the /etc, but nothing worked on boot.  I had to log out and log back in for the settings in my home directory to take affect.  This was not good enough. 

The solution:  install xbindkeys

Installing xbindkeys apparently changes how openbox grabbed keys.  I didn't do any configuration.  I just installed.  
Looks like the keybindings I had set up before still work too. 

The web page below is what gave me the idea to try it. 
[https://help.ubuntu.com/community/Lubuntu/Keyboard](https://help.ubuntu.com/community/Lubuntu/Keyboard)

So this was what was plaguing me for weeks.  This may be some corner case, but I had to share.  Good luck to you all! 


Vin

---

### Post by pirk22 on 2019-03-03
Thank you, Vin!!!

I registered just to post this.

Was having the same issue also on a NUC that I recently upgraded to 18.04. All the mappings and stuff from ir-keytable were working perfectly on ubuntu 15.04, but after the upgrade I could only use the arrow keys and enter. Nearly all other combinations would show up on *ir-keytable -t*, but not on xev or Kodi. Really annoying. In my case, I'm using Xubuntu instead of Lubuntu, so the fix is slightly different. But again seems the same problem, the window manager (XFCE) is catching the events and not passing them to the applications. The configuration file is the following: 

```
.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml
```

After doing a backup of that file, I removed all the keyboard shortcuts by replacing the file with this:

```
<?xml version="1.0" encoding="UTF-8"?>
<channel name="xfce4-keyboard-shortcuts" version="1.0">
  <property name="commands" type="empty">
    <property name="default" type="empty">
    </property>
  </property>
</channel>
```

I'm running a user just to run Kodi, so I don't really care about the keyboard shortcuts on the window manager. (Which in any case, runs fine without them.) I also installed *xbindkeys* beforehand, to see if it would make a difference, but I'm not sure it is necessary (didn't repeat the test without it).

A last note from anyone else upgrading from an old version: the key codes from ir-keytable also changed, even though the IR remote hardware was exactly the same. Using the same procedure of catching the codes with ir-keytable -t works fine...

---

### Post by macarro2 on 2019-03-23
Hi, good afternoon.

 I'm experiencing the same issue: No lirc installed, able to map my remote using ir-keytable, events detected, but only certain keys work in kodi, the text editor or any other program. The weird thing is I'm using Mate at the moment and I also tried with Ubuntu (unity), Cinnamon and so on (I think I tried at least 8 different distributions in the last two days). So for me at the moment the issue is not xfce.

Any suggestion about what I should check/remove/modify?

Regards

---

