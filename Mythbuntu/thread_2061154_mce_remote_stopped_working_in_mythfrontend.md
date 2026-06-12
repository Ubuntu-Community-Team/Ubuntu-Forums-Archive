---
title: "mce remote stopped working in mythfrontend"
date: 2012-09-21
forum: Mythbuntu
---

### Post by majoridiot on 2012-09-21
a real strange one here and stumped...

upgraded to 12.04 a few days ago (clean install) and everything went fine.  have been
using it without problems until today. for no reason the remote stopped working in
mythfrontend.  it won't do anything at all.

lirc is working fine. irw works correctly, as does hulu desktop. no changes were made
to .lircrc or the files in ~/.lirc/

at the time it stopped working all i was doing was looking up metadata in mythvideo
and it just quit accepting remote commands.

no obvious errors in any of the system logs or the backend log.  the only lirc entries in the
frontend log are that it successfully inits lircd. i have been trouble-shooting the
life out of this for hours but there are no bread crumbs to follow.

the box is a combined frontend/master backend.

anyone got any guesses at this heavy-mystery?

---

### Post by nickrout on 2012-09-22
> **majoridiot said:**
> a real strange one here and stumped...

upgraded to 12.04 a few days ago (clean install) and everything went fine.  have been
using it without problems until today. for no reason the remote stopped working in
mythfrontend.  it won't do anything at all.

lirc is working fine. irw works correctly, as does hulu desktop. no changes were made
to .lircrc or the files in ~/.lirc/

at the time it stopped working all i was doing was looking up metadata in mythvideo
and it just quit accepting remote commands.

no obvious errors in any of the system logs or the backend log.  the only lirc entries in the
frontend log are that it successfully inits lircd. i have been trouble-shooting the
life out of this for hours but there are no bread crumbs to follow.

the box is a combined frontend/master backend.

anyone got any guesses at this heavy-mystery?first things first- check the batteries!

---

### Post by majoridiot on 2012-09-22
> **nickrout said:**
> first things first- check the batteries!

thanks nick... but been there and real done that too many times. have been running mythtv 
in ubuntu-land since the days when every module needed to be compiled by hand. even wrote
an early set of ubuntu install instructions and also supported firewire access for years 
before mythbuntu evolved.

the first thing i did was replace batteries, even when irw worked and nothing else did.

was not overstating things when i said that i troubleshooted the life outta
this thing.. at this point it's nearly to death.

have gone through everything from the obvious to the obsucure.  checked memory, storage,
system files... replaced system files, symlinks and everything else i can think of.

the remote works*perfectly* with everything except mythfrontend for no reason i can find.

it worked fine and then it didn't... and still won't... all in the same session
with nothing done other than operating the frontend as intended.

have spent plenty time the last two days sifting through all bug reports, etc. and
there is no explainable reason why this isn't working.

will give it a day or two and then bite the bullet and do another reinstall.

in these cases they say "blame the hardware" and i would... except the hardware toally checks
out ok, the software worked for 3 or so days and then it just refused.

there's a reason why i don't like upgrading... even on fresh intalls. but at least it isn't as bad as windoze or osux.

thanks for trying tho...

---

### Post by nickrout on 2012-09-22
There have been a lot of remote problems with the transition to later kernels where a lot of the remote work is done by devinput instead of, or alternatively to, lirc. It is all a mystery to me, and I don't have to bother with lirc thank the lord. 

But to stop working in the middle of a session is disturbing. There weren't any package updates going on in the background?

---

### Post by Rotak on 2012-09-23
Lirc = Hell.

Support for remotes break on kernel or lirc updates. Nobody knows why.

First of all, make sure that your myth lirc config is in ~/.lirc/mythtv and is linked to ~/.mythtv/lircrc.
Second thing to check is, whether your lircrc file's remote control name and buttons (remote=... and button=... in lircrc) still matches with irw output. I've had a no-name USB remote, which was suddenly recognized as another model after updates.

I had your problem (irw working, but no signals arriving in MythTV) several times. I have several solutions which may possibly work. If none of them works, re-install of the whole system was the only solution that may work on a 50/50 basis. That's why I prefer a cordless keyboard over a remote.

Solution 1 - Reinstall  Lirc:
Use "apt-get purge lirc" to uninstall lirc with all config files. Then reinstall with "apt-get install lirc".

Solution 2 - Lirc from source:
Compile lirc from sources. If the most recent version doesn't work, user 0.8.7 (that sometimes fixes the problem).

Solution 3 - Other kernel:
As an alternative, use another kernel version. Sometimes, the kernel module updates break things.

If nothing works, buy a cordless keyboard and join the "I hate nobody really cares if Lirc breaks when updates are released" mailing list.  :-#

---

### Post by majoridiot on 2012-09-23
> **Rotak said:**
> Lirc = Hell.

Support for remotes break on kernel or lirc updates. Nobody knows why.

First of all, make sure that your myth lirc config is in ~/.lirc/mythtv and is linked to ~/.mythtv/lircrc.
Second thing to check is, whether your lircrc file's remote control name and buttons (remote=... and button=... in lircrc) still matches with irw output. I've had a no-name USB remote, which was suddenly recognized as another model after updates.

I had your problem (irw working, but no signals arriving in MythTV) several times. I have several solutions which may possibly work. If none of them works, re-install of the whole system was the only solution that may work on a 50/50 basis. That's why I prefer a cordless keyboard over a remote.

Solution 1 - Reinstall  Lirc:
Use "apt-get purge lirc" to uninstall lirc with all config files. Then reinstall with "apt-get install lirc".

Solution 2 - Lirc from source:
Compile lirc from sources. If the most recent version doesn't work, user 0.8.7 (that sometimes fixes the problem).

Solution 3 - Other kernel:
As an alternative, use another kernel version. Sometimes, the kernel module updates break things.

If nothing works, buy a cordless keyboard and join the "I hate nobody really cares if Lirc breaks when updates are released" mailing list.  :-#

yeah... i know the woes of lirc and most (but apparently not all) of the workarounds...

the really odd thing is that it was working perfectly and just stopped working mid-session.
i checked the logs and no updates were installed after the initial round of updates after the
fresh install. it was just there one second and gone the next.

have seen and fixed a lot of wonky things on new mythtv installs (like the persistant inability
to correctly configure nvidia driver to work with component 720p without having to edit xorg.conf
by hand) but this one beats all.

have checked all config files, persmissions, etc. and everything is fine.  have tried hard-coding
.lircrc, .lircrc/mythv/mythtv to use only mythtv config for the remote... and even tried pointing
the frontend to the actual location of lircd instead of the /dev/lircd symlink but all
to no avail.

funny you should mention reinstalling lirc... because that's where things get REALLY weird.
i tried that late last night.  after uninstalling lirc, *most* of the remote buttons worked in mythv
but of course failed on everything else, since lirc was no longer existing. how that can be
i have no clue, especially since the frontend log had a glaring failed to init lirc error.

and yes, i did reboot after purging lirc, so it couldn't have been a lingering aftifact.

this one is really, really strange.  i'll give it another couple of days to see if anyone has
insight but i'm betting i'll have to bite the bullet and reinstall and reconfig everything again.
what a pain, especially if this happens again.

thanks for the input, tho!

---

### Post by erlansonc on 2013-01-26
Hey Guys -

Didn't know if this was ever officially solved.  I spent about 2 weeks trying to figure this issue out myself and determined that there were multiple layers to the problem.

I too upgraded (believe it or not, only to Ubuntu vs 11.10 running Mythbuntu 0.24) and all of a sudden my HULUDESKTOP quick working.

Windows remote worked perfectly with MythTV.  No issues at all, so I knew it wasn't the remote.
Ran irw and watched the input that the remote was giving.  AH-HA!  Then my answers started coming to me.

I modified my .huludesktop file to reflect the following:

```
[display]
fullscreen = TRUE
width = 1360
height = 720
pos_x = 0
pos_y = 48

[remote]
[COLOR="blue"]lirc_device = /dev/lircd[/COLOR]
lirc_remote_identifier = mceusb
lirc_release_suffix = _UP
lirc_repeat_threshold = 10
[COLOR="Blue"]button_name_up = KEY_UP
button_name_down = KEY_DOWN
button_name_left = KEY_LEFT
button_name_right = KEY_RIGHT
button_name_select = KEY_OK
button_name_menu = KEY_HOME
[/COLOR]
[flash]
flash_location = /home/~/.mozilla/plugins/libflashplayer.so

[screensaver]
suspend_script = (null)
resume_script = (null)

[version]
latest = (null)
eula_version = 1
```


The first trick was in the [COLOR="Blue"]lirc_device = /dev/lircd[/COLOR] line.  Apparently with some updates, that may have moved?  I'm a little unclear on how Kernel updates work, so I won't try to act like I know what I'm talking about.

The second trick was in the button names!!
How all of that got screwed up, I'll never know.  It may have been one of those frustrating points where I wiped out Huludesktop and started fresh.

Hope this helps you or some other poor soul like me who spent hours upon hours trying to figure this out.

chris

---

