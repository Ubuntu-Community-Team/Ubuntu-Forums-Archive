---
title: "Set Aramok Default App for IPOD"
date: 2008-08-09
forum: Multimedia Software
---

### Post by MrWES on 2008-08-09
Ok...installed Aramok on my son's box, which he currently was using rhythombox for managing his IPOD. Now he prefers Aramok's look, so how do I make it the default app when he connects his ipod nano?

I tried preferred apps, etc., but with no luck.

Bill

---

### Post by MrWES on 2008-08-10
bump

---

### Post by mc4man on 2008-08-10
While it's relatively simple to set amarok as the default (autostart) player for an ipod in Hardy, there doesn't appear to be a way to have it start totally correct.
The best I've found atm is when the ipod is plugged in, Amarok will start and connect to the ipod. Unfortunately amarok will also _load every track_ on the ipod into a playlist and start playing the first listed.

There doesn't seem to be a parameter or launch command to prevent this.
The only other possibility I see atm is to just have Amarok start and not connect and not load a playlist. You could achieve the same by just opening Amarok manually from apps. menu so nothing much to be gained there.

See screenshot for example of first, you could just either let the playlist play or clear it and proceed as normal. If you want to try this let me know and I'll set you up. 
Note; i only set up an ipod with a couple of albums so the loading of all available tracks at start isn't a big deal

Edit: just found a way to have Amarok autostart, connect to the device(ipod) and not load any tracks, have to run but will post intrs. on that later. see screen2

---

### Post by MrWES on 2008-08-10
Ok...where do I set Hardy to use Aramok as the default...I'm still baffled on this one.

Bill

---

### Post by mc4man on 2008-08-10
> Ok...where do I set Hardy to use Aramok as the default...I'm still baffled on this one.

You can't set it per se, the 'workaround' is very simple, give me about 30 -45 min. and i'll post complete instr.
In the meantime install banshee and after it's installed go to places  -> home folder and click on edit -> preferences -> media. Look under music player and see if banshee is listed. If so good, if not restart pc and ck. again. (if not at all let me know and we'll fix)
```
sudo apt-get install banshee
``` or install from synaptic

Also it's _very important that amarok is configured correctly to connect to your ipod. _By correctly I mean if you plug in the ipod, close out rhythmbox and open amarok can you connect to the ipod as shown on left side of either screenshot above. (ie. it connects and shows music folders, if you see folders like calender, ipod_control, ect. it's not configured properly.

Screenshot below shows where you'll set default device, you won't have the choices I show, that doesn't matter, just that you know where to set.

---

### Post by mc4man on 2008-08-10
Edit : revised method, using copy .desktop (old method at bottom
If you copy and paste you'll be okay
First remove the ipod from pc. (umount or eject, and unplug

Browse to home folder -> .local -> share and see if a folder 'applications' exists, if so good, **if not** you can create the folder 

```
mkdir ~/.local/share/applications
```
then run

```
cp /usr/share/applications/kde/amarok.desktop ~/.local/share/applications/amarok-ipod.desktop

```
Then run

```
gedit ~/.local/share/applications/mimeapps.list
```

Do only one of the following three boxes.

**If it's empty** then paste this in

```
[Added Associations]
x-content/audio-player=amarok-ipod.desktop;rhythmbox.desktop;

```

**If it's not** then paste just this line in

```
x-content/audio-player=amarok-ipod.desktop;rhythmbox.desktop;
```

**If the line exists** then just add to end of line
Be careful to keep formatting - no space between entries and end with a ;

```
amarok-ipod.desktop;
```



Then run

```
gedit ~/.local/share/applications/amarok-ipod.desktop

```

Find the line - Exec=amarok %U and change to

```
Exec=./ipod1
```

Find the line - Name=Amarok and change to Name=Amarok Ipod (or anything you want, I used AmaPod ( use the first instance of name= (the 4th line usually

Save and exit out

Go to places -> home folder, r. click on an empty space and choose create document -> empty file. After it is created name it > ipod1 (what it's called doesn't matter as long as it doesn't conflict with anything in home and is same as above script. ( just use ipod1 

Open ipod1 and copy and paste this into and save and close  

```
#!/bin/bash
 amarok -m %d -m

```

Then open a terminal and run

```
chmod +x ipod1
```

Default for music player is set in System -> Preferences -> file management -> media -> music player (enable in edit menus -> preferences. 
Or just go to home folder -> edit -> preferences -> media -> music player. Check/Set your default to Amarok Ipod (or whatever you named it 

Plug in your ipod and see


Notes: This works perfectly here as l_ong as Amarok is not running_ when the ipod is plugged in. If Amarok is running you'll get the playlist screen but you'll need to click connect.

In Amarok -> settings -> configure amarok under general settings _uncheck_ 'remember current playlist on exit' (optional

If Amarok is not running (no icon in upper panel)  but the ipod is mounted then just r. click on the  desktop icon and choose 'open with Amapod'  (or whatever you named it to in edit menus



Old method 



This looks long but should only take a few minutes
Assuming per previous post that banshee is installed, available as a default choice in ...media -> music player and that your ipod is configured in Amarok properly then here's the method.

Note: you don't have to use banshee, banshee-1 or rhythmbox will also work, but we'll use banshee here. Ck. bottom of post for how to continue to use banshee if desired.



First remove the ipod from pc. (umount or eject, and unplug

Go to ....preferences -> file management -> media -> music player and set banshee as default player, close.

Go to places -> home folder, r. click on an empty space and choose create document -> empty file. After it is created name it > test1 (what it's called doesn't matter as long as it doesn't conflict with anything in home ( just use test1

Open test1 and copy and paste this into and save and close  ([COLOR="Red"]edit[/COLOR] - added a 2nd -m to keep gui visible after amarok opens and connects)
```
#!/bin/bash
 amarok -m %d -m
```

Then open a terminal and run ```
chmod +x test1
```
( After you run that you should be returned to prompt, ie. no error message, if it errors ck. spelling, just use copy and paste on the commands I've posted and you'll be okay

Now right click on Applications and choose edit menus.
Highlight sound & video on left side. On the right side find banshee, r. click -> properties. On the properties screen the only thing that has to be changed is the launch command, the rest is optional. I changed name so as not to confuse with banshee. Delete the current command and insert this as launch command
```
./test1
```
See 1st. screenshot 1 for mine


Close out edit menus and plug in the ipod. After it mounts amarok should open and connect to the ipod as in 2nd screenshot in previous post.
.....................................................................


[U]To continue to use banshee (or whichever app whose app launcher was diverted
[/U]
Right click on desktop -> create launcher. Name it as you please and point towards banshee's exec. (in this case /usr/bin/banshee
see screenshot 2
Then when or if you want to open banshee just click on launcher.

I'd also open synaptic, search banshee, click on it and in task bar choose -> package -> lock version. this will prevent an update from inadvertently overwriting the applications menu launcher for banshee.

You can put banshee back to normal in edits menus, blah, blah, banshee -> properties by clicking revert (works 1 edit back
...........................................................................
Again you must have the 3 conditions from 1st. line satisfied for this to work right

...............................................................................

---

