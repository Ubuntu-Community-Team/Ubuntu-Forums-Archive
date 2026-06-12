---
title: "Issues after update to 12.04"
date: 2012-08-12
forum: Mythbuntu
---

### Post by nunrgguy on 2012-08-12
Having a few issues fater updating. 
So far: 
1. Everyone was a smurf - changed hue settings - fixed
2. Log out buttons gone: Added buttons manually to panel - fixed but not as before
3. All my self created launchers gone: fixed, recreated them all
4. Mouse will not change to left handed: Not fixed and this is really bugging me!
5. Flash player keeps crashing in both Chrome and Firefox
6. MS Remote is working fine on remote front end, syste-wise (works A-OK in XBMC), but will not work in Mythtv front end even though it's all still there and setup in the system setup.

Not checked SAMBA and all the rest of if yet, live TV and playback of recordings OK on backend, not upgraded remote front ends yet.

Any help with the mouse issue please? I've tried changing the button order but that resets after a reboot back to right handed again.

---

### Post by nunrgguy on 2012-09-04
Still have mouse and MS remote issues, any ideas????????

---

### Post by nunrgguy on 2012-09-28
bump?

---

### Post by BicyclerBoy on 2012-09-29
You do have a lircrc file in your ~/.mythtv folder?

From the little of lirc I (think) understand..
lirc drivers are in the kernel now (>2.6.36).
So most people don't need to do much except the key mapping stuff.
[http://www.mythtv.org/wiki/MCE_Remote](http://www.mythtv.org/wiki/MCE_Remote)
scroll down to:
"Example lircrc config file"

Each app can have unique key mapping (remote --> key & key actions).
I believe there is a default mapping. Maybe XBMC uses that.

I never used the IR remote with any other program but MythTV.

---

### Post by nunrgguy on 2012-10-05
> **BicyclerBoy said:**
> You do have a lircrc file in your ~/.mythtv folder?

From the little of lirc I (think) understand..
lirc drivers are in the kernel now (>2.6.36).
So most people don't need to do much except the key mapping stuff.
[http://www.mythtv.org/wiki/MCE_Remote](http://www.mythtv.org/wiki/MCE_Remote)
scroll down to:
"Example lircrc config file"

Each app can have unique key mapping (remote --> key & key actions).
I believe there is a default mapping. Maybe XBMC uses that.

I never used the IR remote with any other program but MythTV.
Thanks - I would imagine that if it works in xbmc it works, hardware-wise, with the entire system, Microsoft remote is chosen in the mythtv backend as before but there's no response to ANY button presses within mythtv itself. I'll check the file but things like this shouldn't mess up on upgrades, not really an upgrade is it, more of a ****-up.

Left handed mouse-this is RIDICULOUS. This is 2012, there are left-handed people in the world, we have a right to be able to use a mouse etc in comfort too you know!

---

### Post by BicyclerBoy on 2012-10-05
The changes to lirc etc from kernel 2.6.36 were massive.
These changes meant my IR remote worked (easily) for the 1st time in 5 yrs..

AIUI Each app has a private mapped key response to each remote key press.
Just working in one app does not mean it will work in MythTV.

MythTV needs its own actions for each keypress.
for example:
```

begin
  prog = mythtv
  remote = Hauppauge_Gray #optional
  button = TV
  repeat = 3
  config = ALT+L
  end 
```

This is very flexible but does need some fiddling to get working.

---

### Post by nunrgguy on 2012-10-05
> **BicyclerBoy said:**
> The changes to lirc etc from kernel 2.6.36 were massive.
These changes meant my IR remote worked (easily) for the 1st time in 5 yrs..

AIUI Each app has a private mapped key response to each remote key press.
Just working in one app does not mean it will work in MythTV.

MythTV needs its own actions for each keypress.
for example:
```

begin
  prog = mythtv
  remote = Hauppauge_Gray #optional
  button = TV
  repeat = 3
  config = ALT+L
  end 
```

This is very flexible but does need some fiddling to get working.
OK. Thanks :), I'll give that a try. Personally my remote has always worked straight out of the box with no issues, just select Microsoft remote in the backend and away you go: which is all that should be required, anything apart from that does (LOL) = ****up. I'll put the stars in myself this time. Never realised a male chicken would cause so much fuss.


Left handed mouse anyone?

---

