---
title: "Need to be able to restart MythFrontend via remote.."
date: 2010-11-23
forum: Mythbuntu
---

### Post by x2aws on 2010-11-23
First off i would like to say Ubuntu/Mythbuntu has been my only Linux distro I have used for the past 4-5 years.  As it stands right now I'm having a big WAF problem.  I am running 2 frontends (both Zotac ION's) along with 2 PS3 Bluetooth remotes.  Both boxes and my Master Backend are running Myth .24.  As everyone knows from time to time software crashes/freezes/becomes unresponsive, etc so I need a way for my wife to be able to "press a button" to restart MythFrontend.  Since I'm not using LIRC for the remotes (Using BlueZ/Blueman) its not as easy as just calling a script after a keypress to check for a running process and either ending, or starting it back up again.
 
Any and all help would be greatly appreciated!!

---

### Post by LowSky on 2010-11-23
if the app freezes how do you quit it now?

im just saying that because thats a WAF moment too,restarting is a secondary issue in this case. if its crashing there is a serious issue to address from the logs. your system should never freeze or crash during playback.

---

### Post by x2aws on 2010-11-24
As it stands right now it has only froze once, but it has on 4 occasions just quit and went back to the desktop.  2 times was when she was switching channels at the same time the backend was recording 2 shows and about to record a 3rd...  The other 2 times was when I was switching themes..  the system just sat there and there I was, Desktop.

Right now I have her plug in the mouse to the USB and select app/multimedia/mythfrontend.  I can see that becoming a pain if she has to do that...  Other than that Myth has been rock solid, heck my DirecTV boxes have crashed more times than this thing has  :D

---

### Post by tgm4883 on 2010-11-24
What version of mythbuntu are you using? You can enable that in the remote section of Mythbuntu control centre.

---

### Post by x2aws on 2010-11-24
> **tgm4883 said:**
> What version of mythbuntu are you using? You can enable that in the remote section of Mythbuntu control centre.

10.10 with .24 autobuilds...  I didn't see that in the remote section..  I'll have to look.. BTW, do you have a screenshot of the area??  for the life of me I can't recall ever seeing that...

---

### Post by tgm4883 on 2010-11-24
> **x2aws said:**
> 10.10 with .24 autobuilds...  I didn't see that in the remote section..  I'll have to look.. BTW, do you have a screenshot of the area??  for the life of me I can't recall ever seeing that...

I can make one.

---

### Post by x2aws on 2010-11-24
OK, I've seen that...  Now since I'm not running LIRC is this going to cause an issue in Myth.  I guess I can map just 1 button to it and have the rest do nothing....  hmmmm  If only I wasn't at work...  if only...

---

### Post by tgm4883 on 2010-11-24
> **x2aws said:**
> OK, I've seen that...  Now since I'm not running LIRC is this going to cause an issue in Myth.  I guess I can map just 1 button to it and have the rest do nothing....  hmmmm  If only I wasn't at work...  if only...

The only thing that does is launch a script to kill and restart the frontend. You could map that script to another button on your remote.

---

### Post by cander611 on 2010-11-27
I check that box to map a button to restart Myth.  Hit apply.  It says it's going to run a script.  I click Ok and nothing happens.  Is there a step I'm missing?

---

