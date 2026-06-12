---
title: "Fullscreen in Ubuntu 11.04 w/Unity"
date: 2011-04-29
forum: Mythbuntu
---

### Post by bigbodytad on 2011-04-29
So I upgraded to 11.04 no problem, all is working well.  When I use hulu desktop or youtube in fullscreen mode the top menu bar is not visible, but when running mythtv frontend the top bar is still there. Full screen mode for browsers also hide the top bar. Apparently there is not an autohide option in Unity, I get this...but is there some way to trick it into fullscreen while running mythtv similar to flash videos can?  The last thing I want to watch with my tv is a status bar....

---

### Post by bigbodytad on 2011-04-29
If I boot into Ubuntu with the frontend autolaunch and dont open any programs, it is in full screen!  But when I exit out and relaunch it doesnt go back into full screen again until reboot....

And I already tried the enable legacy full screen workaround in Compiz to no avail...

---

### Post by chicobiker on 2011-04-29
Same problem here today.  Hope this will be addressed as I really want to keep 11.04.

Also will not go full screen for me in Classic desktop.

---

### Post by Blasphemist on 2011-04-29
> **bigbodytad said:**
> If I boot into Ubuntu with the frontend autolaunch and dont open any programs, it is in full screen!  But when I exit out and relaunch it doesnt go back into full screen again until reboot....

And I already tried the enable legacy full screen workaround in Compiz to no avail...

I don't understand this. Could you explain this further? It may be as simple as changing the login settings if you are using auto login or just choosing ubuntu classic at the login screen.

[http://ubuntuforums.org/showthread.php?t=1741293](http://ubuntuforums.org/showthread.php?t=1741293)

---

### Post by williammanda on 2011-04-29
I'm having the same problem. See attached photo.

---

### Post by Blasphemist on 2011-04-29
Finally I understand, but likely can't help. I don't use mythtv. I can only tell you that my browser can go full screen multiple times with F11.

---

### Post by williammanda on 2011-04-30
Here is another screen shot with the bar at the top while mythtv is playing. See attached picture.

---

### Post by mariuskaunietis on 2011-04-30
I've got a similar problem.

---

### Post by williammanda on 2011-04-30
Another issue: When using the keyboard to adjust the volume, F10 doesn't lower the volume but accesses the upper right menu (volume, network, etc...).

---

### Post by myth001 on 2011-04-30
same problem watching Netflix with "Vmware Player Unity"

---

### Post by williammanda on 2011-04-30
Using VLC or Mplayer the top menu bar is not visible.

---

### Post by qrazi on 2011-05-02
It has probably something to do with Compiz (on which Unity operates)... I used to have the same issue in 10.10 and had to adjust some visual effects...

Just upgraded to 11.04 (fresh install actually) and now have same issue... Would be great if someone has a fix with explanation...

---

### Post by kja999 on 2011-05-02
Many programs (especially myth) dont like compiz enabled at all.
Unity, from what I have read, defaults compiz on, although there is a 2D version available.

If you disable compiz the menu will then be able to be backgrounded as you expect.

---

### Post by williammanda on 2011-05-02
I may have found a solution to eliminate the top bar while using Mythtv.

1. I loaded the compiz manager - Advanced Desktop Effects Settings ccsm, using ubuntu software center.
2. Open the compiz manager and select Utility - Workarounds.
3. Check Legacy Fullscreen Support.

Please post any other results.

---

### Post by nickrout on 2011-05-03
compiz has always given difficulties with full screen, and the fix appears to be the same under unity as under gnome in previous versions.

why anyone would want compiz on a mythbuntu machine is beyond me, but if it doubles as a desktop and occasional front end, this is worth bearing in mind.

---

### Post by piginabox on 2011-05-04
> **williammanda said:**
> Another issue: When using the keyboard to adjust the volume, F10 doesn't lower the volume but accesses the upper right menu (volume, network, etc...).

To sort the F10 volume program, open compiz manager and filter for 'unity' then untick the 'ubuntu unity plugin'.
I hope that helps.

EDIT: DON'T DO THAT!!! IT SCREWS UP UNITY

EDIT: I changed the key binding of "Key to open first panel menu" from F10 to alt+F10 and now all is well

---

### Post by nickrout on 2011-05-04
another way might be to change the keybinding for the volume button (vol-down and vol-up are also usually bound to [ and ], if that helps)

---

### Post by rtrevor on 2011-05-05
There's a bug on Launchpad about it here:

[https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/762679]("https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/762679")



And several tickets for it in the MythTV trac:

[http://code.mythtv.org/trac/search?q=compiz]("http://code.mythtv.org/trac/search?q=compiz")

---

### Post by earlneath on 2011-05-10
The bug has been triaged as low importance, presumably because a workaround exists (for as long as legacy mode remains available)

---

### Post by permster on 2011-05-11
I've performed the compiz legacy full screen workaround and now full screen works. The problem now is with Mythfrontend set to autorun at login the top and left bars stay on top of the fullscreen mythfrontend window. The mythfrontend has focus so my remote control still works, but I can't get rid of the bars until I click with the mouse. Once I do that the bars disappear. If I close and restart mythfrontend manually it comes up fullscreen just fine with no bars on the top or left.
 
Actually, my issue looks exactly like [mariuskaunietis]("http://ubuntuforums.org/member.php?u=1291095") screenshot of WoW (earlier in the thread) where both the top and sidebars are showing. Seems to only happen with mythfrontend set to run at login though. Anyone else run into this issue with mythfrontend set for autorun at login?

---

### Post by thatguruguy on 2011-05-12
> **permster said:**
> I've performed the compiz legacy full screen workaround and now full screen works. The problem now is with Mythfrontend set to autorun at login the top and left bars stay on top of the fullscreen mythfrontend window. The mythfrontend has focus so my remote control still works, but I can't get rid of the bars until I click with the mouse. Once I do that the bars disappear. If I close and restart mythfrontend manually it comes up fullscreen just fine with no bars on the top or left.
 
Actually, my issue looks exactly like [mariuskaunietis]("http://ubuntuforums.org/member.php?u=1291095") screenshot of WoW (earlier in the thread) where both the top and sidebars are showing. Seems to only happen with mythfrontend set to run at login though. Anyone else run into this issue with mythfrontend set for autorun at login?


If you're running mythtv frontend at login, you may want to install the xubuntu desktop.  You can select which DE you run at the log-in screen.

---

### Post by jmcvay on 2011-05-17
[Edit - I didn't see this workaround posted on the 2 page of the thread.]

I believe this issue is related to Compiz. I'm using 11.04 Classic - without Unity.

I was able to work around this by:


[LIST]
[*]Installing CompizConfig Settings Manager
[*]Navigate to **Utility** then **Workarounds**
[*]Enable **Legacy Fullscreen Support**
[/LIST]


This has worked for me, your mileage may very.

---

### Post by twyt88 on 2011-05-21
Yep, that's the fix. 

Thanks jmcvay

---

### Post by mnovakovic on 2012-08-21
> **jmcvay said:**
> [Edit - I didn't see this workaround posted on the 2 page of the thread.]

I believe this issue is related to Compiz. I'm using 11.04 Classic - without Unity.

I was able to work around this by:


[LIST]
[*]Installing CompizConfig Settings Manager
[*]Navigate to **Utility** then **Workarounds**
[*]Enable **Legacy Fullscreen Support**
[/LIST]


This has worked for me, your mileage may very.

This worked for me as well, thanks!!

p.s. I have registered just to say thank you, even though I am not the OP :)

---

