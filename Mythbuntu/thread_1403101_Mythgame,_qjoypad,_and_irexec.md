---
title: "Mythgame, qjoypad, and irexec"
date: 2010-02-09
forum: Mythbuntu
---

### Post by Lepy on 2010-02-09
I have a few questions regarding mythgame.
I'm running 9.10 with Revision: 23426 Branch: /release-0-22-fixes

#1)
I have a script that enables qjoypad + a custom configuration for mythtv using a 360 controller on start up. 
I have a button on my remote that uses irexec to run a script to kill emulators and re-enable the custom qjoypad config for mythtv when I'm done playing.

I have custom qjoypad configs for each emulator and would like to be able to enable them when launching from mythgame. I have all the emulators launching properly using default player settings (e.g. pSX -f %s).

I have tried creating a wrapper script as the wiki suggests, but with nothing to go by, I'm obviously getting something wrong. This example script (for pSX) seems to work correctly, except it always complains about not being able to load the cd. 
```
#!/bin/sh
/usr/local/bin/qjoypad 360psx &
/usr/local/bin/pSX -f %s
```
I guess this has something to do with %s in the script not acting like it does when launching directly from mythgame. I'm sure I just need to use another variable like $1 or basename or something to get around it, I just don't know what!

#2)
ScummVM launches fine from mythgame (using wiki directions) and works perfectly with my keyboard trackpad.

I have a custom qjoypad config for scummvm which has the joystick axes mapped to the mouse. It works fine on the desktop (@ 1280x720) but when I try to use it inside scummvm or a scummvm game (usually @ 1024x768 or 640x480) the mouse will hover in the center of the screen until I press the joystick. At this point, the mouse pointer jumps to the bottom right of the screen and stays there unless the trackpad is used.

Other buttons work (I set the X connect button to the F5 global scumm menu), so I think this may be a resolution, not a mythtv problem. Anyone run into this before? Is there a certain variable I can set?

#3)
I want to use the remote to savestates (and other things would be nice too). I have tried following the wiki's xmacro-warp guide but have been unsuccessful thus far. Essentially, I'd like to (using pSX as the example again) set keypad buttons 1 2 3 as quicksave (F5 F6 and F7 in pSX) and 4 5 6 as quickload (F1 F2 and F3 in pSX).

I know I could set each keypad button the execute F buttons using irexec, but then I'd lose functionality in other programs. I assume the wiki's instructions are the best bet to make this a reality, but like I said, I've had no success at all with the xmacro-warp. 

#4)
Finally, I can't get boxart working. In .21 it worked fine since individual paths could be set for each player, but now that there is a single boxart directory, boxart has stopped working. 

I'm using the same name scheme for the jpg files from .21 to .22, but boxart does not show up even when I place them in the newly specified boxart directory.

While I'm at it, I inserted the romdb table in the database, and it seems to have worked flawlessly with all mame roms, but some other roms...not so much. Especially all my pSX cds which I have ripped and converted to .cdz to save space. Would this be because of CRC mismatches? Could I fix this by renaming the files to how they are referenced in the romdb table?

Sorry for the long post, and thanks if you've read this far. Any tips?

---

### Post by Lepy on 2010-02-14
Does this mean I am the only user of mythgame?

I'll again try to set up xmacro to answer question #3, but I have no clue about my other questions...especially boxart, which hasn't worked for months since I upgraded to .22.

---

### Post by Lepy on 2010-02-23
I did a fresh install of 9.10 and .22 (as opposed to an upgrade from 9.04 and .21), but boxart, the one thing I thought might work with a fresh install, is still not working. Any ideas?

---

### Post by Lepy on 2010-03-03
Manually editing the metadata through the gui works as always...but this is time consuming and should be done automatically. Does anyone have boxart working in .22? I've been trying to solve this for months.

---

### Post by anthortic on 2010-05-04
your not on your own! just a message of support friend. same issues on boxart, but sadly i havent the knowledge to fix it

---

### Post by Lepy on 2010-05-05
Glad to hear I'm not alone.

Upgrading to 10.04/.23 did nothing to fix the boxart issue. Editing metadata manually works and opens directly to the boxart/fanart/screenshot folders specified in the mythgame setup screen. 

I have found this:

```
~$ mythfrontend -v important mythgame
2010-04-22 04:38:51.254 mythfrontend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-04-22 04:38:51.255 Using runtime prefix = /usr
2010-04-22 04:38:51.255 Using configuration directory = /home/xbmc/.mythtv
2010-04-22 04:38:51.945 Empty LocalHostName.
2010-04-22 04:38:51.950 New DB connection, total: 1
2010-04-22 04:38:51.952 Closing DB connection named 'DBManager0'
2010-04-22 04:38:51.991 Enabled verbose msgs: important
2010-04-22 04:38:52.232 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-04-22 04:38:52.235 New DB connection, total: 2
2010-04-22 04:38:52.451 Cannot load language en_us for module mythbrowser
2010-04-22 04:38:52.452 Cannot load language en_us for module mythbrowser
2010-04-22 04:38:52.464 MediaMonitorUnix::AddDevice() - empty device path.
2010-04-22 04:38:52.464 MediaMonitorUnix::AddDevice() - empty device path.
2010-04-22 04:38:52.464 MediaMonitorUnix::AddDevice() - empty device path.
2010-04-22 04:38:52.465 MediaMonitorUnix::AddDevice() - empty device path.
2010-04-22 04:38:52.465 MediaMonitorUnix::AddDevice() - empty device path.
2010-04-22 04:38:52.465 MediaMonitorUnix::AddDevice() - empty device path.
2010-04-22 04:38:52.465 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-04-22 04:38:52.465 Cannot load language en_us for module mythgallery
2010-04-22 04:38:52.468 Cannot load language en_us for module mythgame
2010-04-22 04:38:52.470 Cannot load language en_us for module mythmovies
2010-04-22 04:38:52.496 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-04-22 04:38:52.498 Cannot load language en_us for module mythmusic
2010-04-22 04:38:52.502 Cannot load language en_us for module mythnetvision
2010-04-22 04:38:52.504 Cannot load language en_us for module mythnews
2010-04-22 04:38:52.518 Cannot load language en_us for module mythvideo
2010-04-22 04:38:52.522 Cannot load language en_us for module mythweather
2010-04-22 04:38:52.552 MythPlugin::init() dlerror: /usr/lib/mythtv/plugins/libmythmythgame.so: cannot open shared object file: No such file or directory
2010-04-22 04:38:52.552 Unable to initialize plugin 'mythmythgame'.
2010-04-22 04:38:52.552 Unable to run plugin 'mythmythgame': not initialized
```

It looks like the plugin  /usr/lib/mythtv/plugins/libmythmythgame.so instead of the correct /usr/lib/mythtv/plugins/libmythgame.so is called. 

Now, running this command causes mythgame to opens and function like normal...with the exception of metadata, so no idea if this is the cause or even a bug at all. I submitted a launchpad bug a while back, but have heard nothing back about it.

Problems 1, 2, and 3 above have all been fixed...mainly by using a diNovo edge and scrapping the use of qjoypad for all emulators with built in joypad configs. I'll try tackling those at a later date if I feel like it.

---

### Post by straxus on 2010-05-06
No, you aren't alone.  I haven't actively used MythGame in almost a year though.  It's not the app's fault.  I just have never been keen on pulling out ye old USB-PSX adapter/controller combo.  With all my consoles on wireless controllers, I just had a mental block on stringing that mess out for a quick game.  

I got ahold of the 360 wireless USB dongle a few months ago, but didn't realize until yesterday that there was a way to get it working in Linux.  I was thinking I'd need a bluetooth adapter for my PS3 controller.  (Which I'd still like to get)  Once I get finished pulling in metadata in MythVideo, I think I'll turn my attention to MythGame.

---

### Post by Lepy on 2010-05-06
It can be quite a mess and chore to pull out the psx pad and adapter. The 360 wireless works very well with few exceptions, though it does feel a little like cheating. The PS3 pad would definitely fix that.

If you make any progress on the boxart, please report back.

---

### Post by chipppy on 2010-05-07
Good Morning

firstly you are not alone.  There is heap of people using MythGame.

I have been trying for ages to get the boxart to work as an automagic job but still no luck.  

I really want to get this darn thing to work.
If you every crack it please, oh please tell us all with a nice how to.

cheers 
chipppy

---

### Post by andree_b on 2010-05-07
> **Lepy said:**
> 
I have custom qjoypad configs for each emulator and would like to be able to enable them when launching from mythgame. I have all the emulators launching properly using default player settings (e.g. pSX -f %s).

I have tried creating a wrapper script as the wiki suggests, but with nothing to go by, I'm obviously getting something wrong. This example script (for pSX) seems to work correctly, except it always complains about not being able to load the cd. 
```
#!/bin/sh
/usr/local/bin/qjoypad 360psx &
/usr/local/bin/pSX -f %s
```I guess this has something to do with %s in the script not acting like it does when launching directly from mythgame. I'm sure I just need to use another variable like $1 or basename or something to get around it, I just don't know what!


May be a bit late but anyway:
You can't use the "%s"-syntax used inside mythtv-configuration inside your shell script.
You have to use the shell's command line variables syntax there:
```
#!/bin/sh
/usr/local/bin/qjoypad 360psx &
/usr/local/bin/pSX -f $*
```But you still have to use the %s inside mythtv-configuration to call your shell script!

I don't know if $* = all parameters is enough here (not sure what psX expects there) - i might check it tonight when i try to install mame+scummvm on my newly installed mythbox.

---

### Post by Lepy on 2010-05-25
Thanks for the help andree_b.

Your solution works great for file names with no spaces but fails on the others with something like "failed to load [word before first space]." I tried adding 's and "s inside the script and in the launcher line, but couldn't find the right combination.

---

### Post by egh on 2010-05-28
$* expands to all passed arguments; if you are only passing one you can use this instead:

```
#!/bin/sh
/usr/local/bin/qjoypad 360psx &
/usr/local/bin/pSX -f "$1"
```

You will probably want to put quotes around the %s in the mythgame config.

Another solution is to avoid using spaces in files on unix, it generally causes trouble.

---

### Post by Lepy on 2010-05-28
And thank you egh for fixing my problem and teaching me some syntax! No quotes were needed in the mythgame config, just the "$1" change in the script.

I ripped many of the images before ever using linux, so I didn't plan ahead; now, I think spaces make mythgame look neater. 

However, since switching to linux, I have made it a habit to avoid spaces for many filetypes: I prefer periods. KRename works wonders too.

---

### Post by egh on 2010-05-28
Glad to help!

---

