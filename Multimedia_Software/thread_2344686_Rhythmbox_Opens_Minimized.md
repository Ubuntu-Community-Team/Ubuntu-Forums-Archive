---
title: "Rhythmbox Opens Minimized"
date: 2016-11-27
forum: Multimedia Software
---

### Post by timfinley on 2016-11-27
This isn't the worst thing in the world, just a little irksome and it would be nice if I can stop it from occurring. When I start rhythmbox and put some music on I usually close the window and let the music play in the background. However, if I want to change the album, song, whatever, I click: sound symbol in notification tray > Rhythmbox. It opens minimized and I have to click a second time from the app tray in the left bar. If I press the Super Key and type "Rhythmbox" and open it that way, same thing. It opens minimized and I have to click again or alt+tab to the program. If the program is not playing or running the background, it opens the way I want it to. Is there any way to make it open, while running, expanded and in front? I'd be willing to bet it's something super easy and I'll keep poking around. Most of the problems/solutions I've found on this matter are to make Rhythmbox open minimized, the behavior I'm trying to reverse. 

Thanks ~


Specs:
Ubuntu 16.04 64-bit
Rhythmbox 3.3

---

### Post by timfinley on 2016-11-30
Update: I have tried [this tip found in the wiki]("https://help.ubuntu.com/community/Rhythmbox#Minimizing_at_start_up"), but it did not help with my issue as the plugins > status-bar is depreciated.

This is still pretty annoying and I am still looking for a solution.

---

### Post by mc4man on 2016-11-30
> **timfinley said:**
> Update: I have tried [this tip found in the wiki]("https://help.ubuntu.com/community/Rhythmbox#Minimizing_at_start_up"), but it did not help with my issue as the plugins > status-bar is depreciated.

This is still pretty annoying and I am still looking for a solution.

Well that's the odd thing. For a couple years now there is *no way to start Rb minimized*, users have inquired as to how to do with no solution. 
Is this a fresh 16.04 install or upgraded from older releases?
You could see what happens in a guest session though you'd need to provide a track, copy from a usb stick to guest's Music folder would be easiest.

---

### Post by kostkon on 2016-11-30
It happens in older versions as well, e.g. 12.04 and I'm guessing it is part of the general "indicator apps don't get focus when raised" problem as described [in this really old bug report]("https://bugs.launchpad.net/ayatana-design/+bug/627195").

I guess Unity 8 will solve that, although I doubt Rhythmbox will remain the default media player in the new Unity 8-Snappy-Mir era.

---

### Post by timfinley on 2016-12-01
Sure 'nough, @kostkon, this is exactly the issue I'm having. Thank you for at least putting the problem in more accurate words.

---

### Post by mc4man on 2016-12-01
> **timfinley said:**
> Sure 'nough, @kostkon, this is exactly the issue I'm having. Thank you for at least putting the problem in more accurate words.
Not exactly what you described..
To fix - 
Open ccsm (compizconfig-settings-manager)

Under General options > Focus and Raise Behavior set Focus Prevention Level to Off, see screen
(- there is evidence that Off should be the default but was never done..

---

### Post by timfinley on 2016-12-02
Thank you @mc4man. This fixed the issue 100%. This has been such a frustration!

---

