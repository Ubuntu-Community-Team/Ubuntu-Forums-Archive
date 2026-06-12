---
title: "Big Desktop Reverts to Clone on Restart"
date: 2008-05-26
forum: Multimedia Software
---

### Post by MianoSM on 2008-05-26
As the title states, everytime I restart my PC, it brings me to the login screen in big desktop mode, and when I login it puts my settings back to clone.

I'm using a SyncMaster 203B, and a VA520 Viewsonic for my monitors, one is 1400x1050, and the other is 1280x1024.

My video card is an ATI Radeon 1650 pro, on Driver Version 8.47.3 and Catalyst Control Center Version 1.8.

Let me know if anymore information would be helpful - or if I missed a thread in my searching beforehand. 

TIA

---

### Post by otwr on 2008-05-26
Using KDE3 with an ATI 3850. I couldn't make Big Desktop stick either. There's probably a better way to do this, but here's what I did:

make ~/.kde/Autostart/xrandr:

----------------------
#!/bin/bash
xrandr --output DVI-I_1/analog --right-of DVI-I_2/analog
----------------------

then "chmod +x" that file and restart X. Hope this helps...

---

### Post by MianoSM on 2008-05-27
I'm assuming if I'm on Ubuntu as opposed to Kubuntu I can do the same in:

~/.gnome/Autostart/xrandr  ?

---

### Post by otwr on 2008-05-27
Here's the first link on a google search for "gnome autostart":

[http://gentoo-wiki.com/HOWTO_Autostart_Programs#GNOME](http://gentoo-wiki.com/HOWTO_Autostart_Programs#GNOME)

Maybe Ubuntu provides some GUI means of doing it. Good luck!

---

### Post by MianoSM on 2008-05-27
It's already correct when the machine restarts though.

It's only after I type in my username/password and it loads the desktop that it reverts to a clone display.

So I go back to my applications > catalyst, reset it to big desktop. It looks great. Then it prompts for a restart, I restart. The login screen is in big desktop mode > I login > back to clone.

I don't think that what I'm after is an autostart. /dunno

---

### Post by dan16384 on 2008-11-03
I have the same problem with two DVI monitors on a Radeon HD 3600.

The ATI Catalyst Control Center settings seem to be lost on log in.
(Running it a root doesn't help either.)

xrandr seems to be a dead-end. xrandr and the GUI version of it (the 'Multiple Screens' package) only see one screen.

Help would be appreciated.

---

### Post by stelekpl on 2008-11-03
Seems I have exactly the same problem. Ihave two monitors: 1600x1200 LCD + 1360x768 TV. On the login screen everything is fine. But after I login the LCd switches to 1360x768, so both monitors have the same resolution. I can switch it back with nvidia-settings and it works fine, but it's really annoying...

---

### Post by cszikszoy on 2009-04-02
I was having the exact same problem, and I found a very simple solution!  I'm on Intrepid (8.10).  Go to System > Preferences > Screen Resolution.

If you have previously enabled "Big Desktop" mode in catalyst, you should see a resolution in the "Resolution" that should be both of your screens put together.  For example, I've got two monitors at 1280x1024 resolution.  When I first logged in, the resolution setting was at "1280x1024".  But, in the resolution drop down, there's one resolution above that, "2560x1024".  After selecting this resolution, and clicking apply, everything works as expected across sessions.

It's a pretty simple fix, hope this saves someone some trouble!

---

### Post by dan16384 on 2009-04-03
> **cszikszoy said:**
> I was having the exact same problem, and I found a very simple solution!  I'm on Intrepid (8.10).  Go to System > Preferences > Screen Resolution.

If you have previously enabled "Big Desktop" mode in catalyst, you should see a resolution in the "Resolution" that should be both of your screens put together. ...After selecting this resolution, and clicking apply, everything works as expected across sessions.


You, sir, are a gentleman and a scholar. This works for me. 

Actually, it seems that it doesn't matter if the resolution set for the one big screen in this preference is correct or not - only that you change something there. (Since it still hasn't added my two screen's resolutions together quite right.)

---

### Post by schlatter on 2011-08-15
Thanks cszikszoy!

I started to get *really* anoyed about this problem. Especially since the opensource driver stopped working properly for my ATI Mobility Radeon HD 3400 in Ubuntu 11.04 (Natty).

Here's how to do it in Natty:

- configure big desktop using catalyst
- then, go to System settings
- open "Monitors" (it should display your big desktop config)
- do not change anything, just click the button "Make Default"

Changing the resolution - as you apparently had to in intrepid - is *not* necessary (and not possible either).

---

