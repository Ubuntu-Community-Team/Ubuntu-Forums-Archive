---
title: "Unity side panel gone 'mental'"
date: 2011-02-27
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by macroshaft on 2011-02-27
I had to do a fresh install today, using A2 since ubiquity seems to be broken in the daily builds at the moment. With all updates done and the Nvidia experimental 3D driver active I logged in to find the unity panel going nuts.

Way back when, when unity last worked for me the side panel had begun to auto hide and show up only if I moved the mouse cursor over the logo in the top left corner. It seems it now can't make it's mind up whether to hide or not. Is anyone else having this issue and has anyone found a way round it as it's rather annoying.

---

### Post by mc4man on 2011-02-27
When it goes 'spastic' on a login probably the only way is to do a logout/in or a restart, I see it once and a while
(other than opening ccsm and setting autohide to never

The last upgrade of unity seems to have introduced some potential mis-behavior(s) of the panel when  in any of the 3 hiding modes, this is just one

---

### Post by macroshaft on 2011-02-27
> **mc4man said:**
> When it goes 'spastic' on a login probably the only way is to do a logout/in or a restart, I see it once and a while
(other than opening ccsm and setting autohide to never

The last upgrade of unity seems to have introduced some potential mis-behavior(s) of the panel when  in any of the 3 hiding modes, this is just one

It has nothing to do with logging in, my panel consistantly does this, every login, all the time.

---

### Post by mc4man on 2011-02-27
> It has nothing to do with logging in, my panel consistantly does this, every login, all the time.
Well then you are in the vast minority, try setting autohide to never, restarting and then switching back to one of the 3 modes.

Otherwise maybe A3 will treat you better

---

### Post by MadMan2k on 2011-02-27
> **mc4man said:**
> Well then you are in the vast minority
no he is not. hover slowly the ubuntu logo to see the effect and verify what others say befor starting yelling next time.

---

### Post by mc4man on 2011-02-27
> hover slowly the ubuntu logo to see the effect and verify what others say befor starting yelling next time.
I believe what the Op was reporting ( though could of misunderstood him) is not what you are describing which is the mouse trigger/lock launcher point
By default it is set to 'slide' (slide the launcher out) and 'fade' (dim to bright)
Until the launcher goes 'bright' (locked), it is not usable
If it can't be locked that is a separate issue

---

### Post by SushiR on 2011-02-27
Same here, flashing like crazy. Not alway but often. Loggin in and out (maybe a few times) helps and then it behaves normal. Maybe tomorrows updates brings a fix...

---

### Post by fflopes on 2011-02-27
> **mc4man said:**
> I believe what the Op was reporting ( though could of misunderstood him) is not what you are describing which is the mouse trigger/lock launcher point
By default it is set to 'slide' (slide the launcher out) and 'fade' (dim to bright)
Until the launcher goes 'bright' (locked), it is not usable
If it can't be locked that is a separate issue

I had that same problem.  When I moved the cursor over the logo the left panel wouldn't know whether to show or fade.  I've noticed, though, that if I moved the cursor all the way to the corner (all the way left and all the way up) the left panel would go bright and be accessible.  It doesn't seem to be the expected behavior though.

---

### Post by mc4man on 2011-02-27
> **fflopes said:**
>   It doesn't seem to be the expected behavior though.
Here's some the 'history' of the slight changes to the orig. mouse trigger point.
The size of the trigger/lock point has been increased slightly. (maybe 2x2px, top left corner
You can alter how it works in cssm > unity plugin > experimental

[https://bugs.launchpad.net/unity-2d/+bug/706146](https://bugs.launchpad.net/unity-2d/+bug/706146)
(currently only an open bug on unity 2d

some additional on the adding of 'lock point'
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/721125](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/721125)
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/721003](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/721003)

---

### Post by macroshaft on 2011-02-27
> **fflopes said:**
> I had that same problem.  When I moved the cursor over the logo the left panel wouldn't know whether to show or fade.  I've noticed, though, that if I moved the cursor all the way to the corner (all the way left and all the way up) the left panel would go bright and be accessible.  It doesn't seem to be the expected behavior though.

My issue has nothing to do with the trigger. From the moment I log in the unity bar 'stutters', constantly switching between hidden, half out and visible randomly and very fast. It only stops when an application is full screen or intrudes into the bar's space when it then stays hidden.

---

### Post by ktp on 2011-02-27
I had the same issue with new install (usb persistent) using 2/26 daily live-cd.  Using the opensource Nvidia experimental 3D driver, I get the same issue with side panel.  

Next I went to Nvidia proprietary driver (270.29), and I can login to unity but desktop doesn't refresh (seems like it is frozen/locked).   I can move the mouse and drag folders (only cursor changes, folder/file icons don't).  Switching to tty1 and back to gui, I get black screen.  Seems like there is still going to be more work needed here.

I gave up after while and decided to just stick with classic without any effects, which is the only session that really worked with Nvidia proprietary driver, for me.

---

### Post by SushiR on 2011-02-27
> **macroshaft said:**
> My issue has nothing to do with the trigger. From the moment I log in the unity bar 'stutters', constantly switching between hidden, half out and visible randomly and very fast. It only stops when an application is full screen or intrudes into the bar's space when it then stays hidden.

Most of the time it stops after 90 seconds of wild switching... But if you trigger it, the switching starts again. As I said, only loggin out and in (once or a couple of time) stops this.

May I ask what graphic card (or chip) you have? I'm running a Samsung N150 netbook, so it's an integrated intel thingy...

---

### Post by mc4man on 2011-02-27
macroshaft
returning to your particular issue - as I and others have noted this does happen, the difference being not all the time. Here it only occurs maybe 5% of the time on log in, maybe more frequently for others.

I still think you should open ccsm (compizconfig-settings-manager) and set the hide option to never.
Then restart, at least you'll have a launcher.
At that point re-open ccsm and try any of the 3 hide modes, see if it behaves better. (screen

There has been regressions in the launcher when in any hide mode. Some of these may occur either during a session or directly at log in so don't be surprised if it _occasionally _works poorly.

One of the likely ones here, (during session), is the launcher will expose but can't be locked. In that case tapping the super button usually fixes
(a tap on super will expose and lock a hidden launcher and also open dash.
 A hold or the super button will expose a hidden launcher and show the keyboard shortcuts for 'favorite' icons 0-9 total, and the expo (w), places (f, a

---

### Post by MacUntu on 2011-02-27
Not really too difficult to find in Launchpad. :confused:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/717364](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/717364)

---

### Post by macroshaft on 2011-02-27
> **SushiR said:**
> Most of the time it stops after 90 seconds of wild switching... But if you trigger it, the switching starts again. As I said, only loggin out and in (once or a couple of time) stops this.

May I ask what graphic card (or chip) you have? I'm running a Samsung N150 netbook, so it's an integrated intel thingy...

This time around my launcher is behaving itself, it seems my problem is intermittent after all! My card identifies itself as an Nvidia Geforce Go 6150 and I have a HP TX1000 laptop. Since a few of the posts here hint at people seeming to think I'm making a big deal I'd like to state I expect there to be problems with the system at this time and I'm fairly impressed with how well it has worked considering the scope of the changes going on. Just because I comment on an issue it does not mean I'm getting into a flap about it. I'm looking forward to seeing the finished menus and how unity 'feels' once all the bugs are ironed out.

---

### Post by rubenverweij on 2011-02-27
I'm seeing this too. On login, the panel starts sliding in and out with a yellow (???) background. It only stops when it hides because a window is e.g. maximized. If I try to trigger it by mouse, it doesn't act all weird with the yellow background, but it stays half transparent and inaccessible. I can use the Super+Num short cuts to launch applications, though. The dash also works (sort of) but then the launcher is doing its yellow background thingy again. :) Is there already a bug filed?

---

### Post by VinDSL on 2011-02-27
> **SushiR said:**
> May I ask what graphic card (or chip) you have? I'm running a Samsung N150 netbook, so **[COLOR="Red"]it's an integrated intel thingy[/COLOR]**...
It's happening to me too, and I'm not running an integrated chip.  ;)

See my sig for details (lower left corner)...

---

### Post by mc4man on 2011-02-27
> Is there already a bug filed?
Look for the link in post 14
If it's occurring often and you don't wish to wait for the next unity upgrade then there is a testing ppa linked in the bug report. (comment 10
Use it to upgrade unity and unity-common and this should go away

---

