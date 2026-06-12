---
title: "How to get Update Manager to be quiet?"
date: 2013-02-17
forum: Mythbuntu
---

### Post by tji on 2013-02-17
I am a long time Mythbuntu user.  It's fantastic, and makes setting up MythTV pretty darn easy.

I recently upgraded from a really old Mythbuntu release to 12.04 in order to upgrade to MythTV 0.26.   In general, it went well, after working out a few issues.


The one thing that has persisted, which is really annoying in a 10-foot interface typically driven by a remote control, is the Update Manager behavior.

It seems like every time I power on my projector, I am greeted with a dialog box for the Update Manager.  It, of course, has the GUI focus, so I cannot use MythTV until I go get my laptop and use VNC to connect in and close the dialog box.

I first set update checking to the least frequent interval, but it still seemed to check more often.  I set it to operate in the background so it wouldn't interrupt MythTV, but it still does.   I have tried several other things, but still get the annoying dialogs.   Yesterday, I turned off Update Manager update checks.  Today, I was greeted with a dialog saying "You must check for updates manually".

Come on!  This is ridiculous.   This behavior may be acceptable on a PC where you're already sitting in front of the keyboard and mouse to operate the system.   But, in a Home Theater this is not acceptable.

To top it all off,  the VNC server in 12.04 doesn't seem to like connections from my Mac, either using the Screens app or the Apple Remote Desktop viewer.  It constantly disconnects (crashes?) making it even more difficult to get rid of the update manager messages.

---

### Post by ibjsb4 on 2013-02-17
Maybe just remove update-manager and update manually.

---

### Post by tji on 2013-02-19
Yeah, I guess I'll have to completely remove Update Manager.

It's almost comical at this point.   As far as I know, I have disabled everything I can.   But, again today when I turned on my display I was greeted by an Update Manager dialog box listing the available updates.   I'm not sure how/why it came up,  but I'm back to VNC to dismiss the windows.


In any case, one of the main reasons I posted here was in the hopes that the Mythbuntu crew would see it and potentially update the behavior, as it is really bad for a "10 foot interface".

As I mentioned,  I love Mythbuntu, I think it's a great project, and I just wanted to give some feedback towards making it great for everyone.

---

### Post by mc4man on 2013-02-19
may not help at all but if keeping update-manager you could try disabling it in your Startup Applications

By default it's hidden so 1st. one needs to un-hide
```
gksudo gedit /etc/xdg/autostart/update-notifier.desktop

```
scroll down towards bottom & change "NoDisplay=true" to 
NoDisplay=false

save, (don't save that annoying 'Untitled..') then open Startup Applications (from cli - gnome-session-properties) & disable (uncheck - screen

---

### Post by PhilWig on 2013-02-20
Agreed, very irritating behaviour in 12.04.
I did this in desktop:

Applications
System
Update manager
Settings (bottom left), give password.
Automatically check for updates = never

You can put them back on again should you need to.

Phil

---

### Post by AlecJ on 2013-02-20
Also got fed up with phone calls from the Mrs, asking how to get rid of the big white box on TV.
on the FE/BE I did the same as Phil

But on the remote IBM Thinkpad frontends, which Update Manager causes  long periods of inactivity. I remove update manager altogether with
```
sudo apt-get remove update-manager-core
```and now I ssh into the old laptops and update with
```
sudo -S apt-get update && sudo apt-get dist-upgrade
```I have to be careful with the backend as a kernel update will stop the TBS cards from working.

works for me.

---

### Post by superm1 on 2013-02-20
The intended behavior is that it's supposed to be popping up "behind" mythfrontend not in front.  Can those affected please file a bug at 

[https://bugs.launchpad.net/ubuntu/+source/update-manager](https://bugs.launchpad.net/ubuntu/+source/update-manager)

Mention that you are using Mythbuntu 12.04.2 and that it's popping up in front of mythfrontend not behind.

The update manager guys should be able to comment on what's going on and work out a fix.

We used to have it set so that it would just render an icon in the tray, but I guess that option must have gotten removed from the update manager code without us noticing.

---

### Post by PhilWig on 2013-02-21
Ok.  Will do.

I’m on 12.04.01 LTS but frozen a few months ago.  Which versions are other posters on?

Can I seek clarification and a view please though superm1?

When an application writes to screen it needs to give a priority for display.  The problem could be that the priority of update manager is too high, but equally could it be that Mythtv is too low.  I say this because there is another screen priority problem which may be related.

When I moved from 9.04 to 12.04, not only did I see this update manager problem, but also a problem with the newly written Mythwelcome.
When exiting mythtv frontend back to welcome, the screen does not paint properly.  Black blocks at top/bottom of screen show (parts of the desktop) but otherwise the screen sticks at frontend.  No part of Welcome screen paints but it may just flick into place a minute or so later.  It typically needs a control/f2 to see it.

My question is whether you think this is a Mythwelcome problem, not an update manger?
 
Phil

---

### Post by superm1 on 2013-02-21
> **PhilWig said:**
> Ok.  Will do.

I’m on 12.04.01 LTS but frozen a few months ago.  Which versions are other posters on?

Can I seek clarification and a view please though superm1?

When an application writes to screen it needs to give a priority for display.  The problem could be that the priority of update manager is too high, but equally could it be that Mythtv is too low.  I say this because there is another screen priority problem which may be related.

When I moved from 9.04 to 12.04, not only did I see this update manager problem, but also a problem with the newly written Mythwelcome.
When exiting mythtv frontend back to welcome, the screen does not paint properly.  Black blocks at top/bottom of screen show (parts of the desktop) but otherwise the screen sticks at frontend.  No part of Welcome screen paints but it may just flick into place a minute or so later.  It typically needs a control/f2 to see it.

My question is whether you think this is a Mythwelcome problem, not an update manger?
 
Phil

Oh this is interesting, is everyone affected having the problem only with mythwelcome?  I think mythwelcome intentionally tries to be the app behind other apps.  Mythfrontend should be in front however.

---

### Post by AlecJ on 2013-02-21
Not using Mythwelcome, never go in standby or turn machine off.

---

### Post by PhilWig on 2013-02-22
If the checkbox ‘automatically start frontend’ (in mythwelcome > i)  is un-ticked then frontend closes cleanly.   Maybe we need a poll to pin it down.  Suggested questions and my answers:

Which version of Mythbuntu are you running?   12.04.01 LTS
Do you use Mythwelcome?    yes                                                                       
Is mythwelcome set to ‘automatically start frontend’ (see mythwelcome, i)?  yes
Do update manager messages intrude over frontend screens (or you have needed to suppress them)?   yes
Ditto ‘Ethernet connected’ warnings.  yes 
                                                              Does mythfrontend close down cleanly and promptly to mythwelcome?  No


Until August 2012 it was:

Which version of Mythbuntu are you running?   9.04
Do you use Mythwelcome?                                                                               yes
Is mythwelcome set to ‘automatically start frontend’ (see mythwelcome, i)?  yes (default or no option)
Do update manager messages intrude over frontend screens (or you have needed to suppress them)?   no
Ditto ‘Ethernet connected’ warnings?        yes
Does mythfrontend close down cleanly and promptly to mythwelcome?         yes

---

