---
title: "Blank Screen after MythTV update from 0.25 to 0.27"
date: 2014-09-10
forum: Mythbuntu
---

### Post by Lupierus on 2014-09-10
HI All,

I was having an issue on my frontends recently after an upgrade to 0.27 from 0.25, I would get nothing on the screen after boot on my frontend.

The workaround for me was to 'kill mythfrontend' remotely to get back to the desktop.  Then go to mythbuntu control center and disable autostart of Mythtv Frontend.  Once this was done, I could at least boot without the blank screen.

After this, I did notice if you allowed the frontend PC to boot fully to desktop, you could start mythtv frontend normally without issues.  Strange.  Maybe a opengl issue, I dunno...  I am not expert here...

As a temp workaround, I added an autostart shortcut to mythtvfrontend to gnome (home/<usrname>/.config/autostart) with a delay code: bash -c "sleep 10s && myhtfrontend" and things seemed to work okay, just 10 seconds slower now...

If this is not a duct tape and twine fix, i have no idea what is not!! :)

Does anyone have any better more legit ideas on how to fix this besides a full machine wipe and upgrade?

BR,
Lupierus

---

### Post by dibuntux on 2014-10-04
Hi, I do not know if it is the same problem, but I try to describe...I too have upgraded to .27 from .25, and also from 12.04 lts to 14.04 lts (amd64). What I get is that when I boot the system, mythfrontend starts...but in another page...I can see the empty background from the Mythbuntu theme, but no menus...nothing.
If from the keyboard (yes, I have one always connected) I do Alt-Tab, the right page with menus appears. If I exit mythfrontend and start it again, the menus are there and everything is ok. I even tried to autostart mythfrontend not as --service, but it does the same, Alt-Tab needed...
As for your solution: you inserted the line bash -c "sleep 10s && myhtfrontend in mythtv.desktop? I do not have the file mythtvfrontend in home/<usrname>/.config/autostart...

Some more ideas?

---

### Post by neutron68 on 2015-07-14
This exact same thing has been occurring on my Mythbuntu 12.04 machine since I updated from 0.25 to 0.27 a year ago.
Note that this happens after EVERY boot of the machine.

My workaround has been to CTRL-ALT-F1 and then CTRL-ALT-F7, after EVERY boot of the machine.

Given that this is happening the same way to more than 1 user, I'm guessing this is a known bug?

Is more info needed to fix it?
What info/logs are needed?

[IMG]http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu_12-04/20141223_095201_zpsggiitac2.jpg[/IMG]

---

### Post by khPWXxF on 2015-07-17
Hmm.  So it works after you 'kick' the screen.  That sounds a bit like the 'intrusive toolbar' problem in this thread.

[http://ubuntuforums.org/showthread.php?t=2282465](http://ubuntuforums.org/showthread.php?t=2282465)

I wonder if the cause and work around are the same?
Phil

---

### Post by Lester_Burnham on 2015-07-19
Hi,

If they're combined backend/frontend machines, it sounds like the frontend is loading too soon for the backend to be ready for connections.

I always use a button on the remote to launch the frontend. Mainly from the days of auto shutdown and not using myth welcome.

Lester

---

### Post by neutron68 on 2015-07-21
> **Lester_Burnham said:**
> Hi,

If they're combined backend/frontend machines, it sounds like the frontend is loading too soon for the backend to be ready for connections.

I always use a button on the remote to launch the frontend. Mainly from the days of auto shutdown and not using myth welcome.

Lester
My machine is a combined frontend/backend, with an Nividia GT 220 graphics card.

Is there a tweakable control that sets the delay of the frontend start?
Or is this a hard-coded delay and this will need to be fixed via an update?

---

### Post by Lester_Burnham on 2015-07-22
Hi,

I'm just guessing this is the problem from the symptoms and that fix it. The front end logs may reveal the actual cause.
The delay could probable be added to the mythtv.desktop file in ~/.config/autostart. It could also maybe be added to the section in mythbuntu control centre where the autostart check box is. A user defined timeout maybe.

It might not be needed also, if something else is at fault, this is just a band aid fix.

Lester

---

### Post by neutron68 on 2015-08-03
FIXED???  I just downloaded updates on Sunday night and upon reboot, the Mythtv menus appeared, as desired, without any workarounds!

My current version reads as:
mythfrontend version: fixes/0.27 [v0.27.5-3-g9498257] 

Has anyone else seen their system fixed by the updates?

---

### Post by neutron68 on 2015-08-16
Nope...not fixed.  

I rebooted today and it came back to the blue could screen and hung there until I did the CTRL-ALT-F1 and then CTRL-ALT-F7.

---

