---
title: "Unity technical thread"
date: 2010-11-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by castrojo on 2010-11-12
> **plun said:**
> Well... tried to build it from source but it fails...:---)


See if this helps. Feel free to update the instructions as you find problems.

[https://wiki.ubuntu.com/Unity/InstallationGuide](https://wiki.ubuntu.com/Unity/InstallationGuide)

---

### Post by Bou on 2010-11-12
So, first impressions:

[LIST]
[*]The launcher looks much better than its previous incarnation,  the panel looks the same.
[*]Multiple-window launchers have dots that also look great.
[*]There are no arrows to indicate active launchers; instead, inactive (pinned) lunchers have an empty, black background.
[*]The indicators are all to the left.
[*]Global menu isn't working.
[*]Maximized windows' titlebars don't blend with the panel.
[*]The dash, places or apps don't work. You need to place an additional panel somewhere to actually launch apps.
[*]You can't do anything with the launcher, beyond clicking or dragging it up and down.  Right-clicking launchers doesn't work.
[/LIST]

All in all, it's much slicker than the previous unity, but with much reduced functionality.

---

### Post by Framli on 2010-11-12
For now, Compiz is segfaulting on me...

---

### Post by plun on 2010-11-12
> **whiprush said:**
> See if this helps. Feel free to update the instructions as you find problems.

[https://wiki.ubuntu.com/Unity/InstallationGuide](https://wiki.ubuntu.com/Unity/InstallationGuide)

Ok... thanks...build it from source without any problems..!

sudo make install also for unity

But it got bugs...:lolflag:

A user must probably be a terminal-freak for the moment.... but I have no problem with that.

It also seems to break posting with Firefox.....  

But it runs....:lol:=D>

---

### Post by MacUntu on 2010-11-12
Do you guys also have the GNOME3 PPA enabled? I wonder if they work together or fight each other.

---

### Post by plun on 2010-11-12
> **MacUntu said:**
> Do you guys also have the GNOME3 PPA enabled? I wonder if they work together or fight each other.

I have it enabled....   terminal knowledge is a must at least for the bzr version.....  start and kill apps....O:)

For example the panel is crazy....

---

### Post by MacUntu on 2010-11-12
"You gotta know the CLI to run the GUI" - sounds like Linux. :D

---

### Post by godhika on 2010-11-12
Sounds like people have way to much fun here. Btw is Ctrl+Alt+t working for anyone since the switch to compiz 0.92?

---

### Post by plun on 2010-11-12
> **godhika said:**
> Sounds like people have way to much fun here. Btw is Ctrl+Alt+t working for anyone since the switch to compiz 0.92?

Yup... opens the terminal for me...

---

### Post by godhika on 2010-11-12
> **plun said:**
> Yup... opens the terminal for me...

Well, seems like another bug to file.Thanks

---

### Post by Amaranth on 2010-11-12
No need, we're temporarily using the ini configuration backend and a very limited set of plugins so all of your configuration and GNOME integration is missing.

---

### Post by go7Ul1ai on 2010-11-12
Okay so I'm having an issue with the Compiz-based Unity.. I know it's a pre-alpha but I was wondering if anyone else was having trouble with it?

Well, I can't take a screenshot to show you, or can't bring up a 'run' dialogue.. I also can't open new applications that aren't on the launcher (firefox, evolution, empathy, totem and workspace switcher), also if I delete the bottom panel which is strangely still there, everything freezes (I think it's trying to switch to Mutter or something) and I have to hard-reset..

Anyone having similar issues?

Edit: For the time being I've decided to add a menu bar on the bottom panel (since I can't add anything to the top one) so I can access my applications :)

Double Edit: Can now take a screenshot:

[IMG]http://imgur.com/iHMf7l.jpg[/IMG]

---

### Post by MacUntu on 2010-11-12
How unfair! My launcher icons are half white until I launch the application for the first time in the session.

[img]http://img.xrmb2.net/images/890767.png[/img]

Else it seems to be pretty pre-alpha on my machine, BUT: no more mutter CPU thrashing. Everything's smooth and snappy. :D

The UNE session in GDM now sends me to a white screen.

---

### Post by Starks on 2010-11-12
Unity isn't that bad.

My first impressions are 10x more positive than Gnome-Shell.

---

### Post by smellyman on 2010-11-12
> **Starks said:**
> Unity isn't that bad.

My first impressions are 10x more positive than Gnome-Shell.

I can't wait to see the final of both.  It will be good to have choice.

---

### Post by DBO on 2010-11-13
> **MacUntu said:**
> How unfair! My launcher icons are half white until I launch the application for the first time in the session.

[img]http://img.xrmb2.net/images/890767.png[/img]

Else it seems to be pretty pre-alpha on my machine, BUT: no more mutter CPU thrashing. Everything's smooth and snappy. :D

The UNE session in GDM now sends me to a white screen.

Sorry about that, we are working on it. It seems to be somewhat specific to 32-bit machines. Can you give any details about your current machine?

---

### Post by simpleblue on 2010-11-13
> [IMG]http://imgur.com/iHMf7l.jpg[/IMG]

This is looking quite good. I especially like the workspace switcher in the panel. As well as a text input search for programs...

But, I guess I should just wait!! :p

---

### Post by MacUntu on 2010-11-13
Compiz seems to randomly die when closing either gnome-apperance-properties after enabling desktop effects or the ccsm.

Edit: not so randomly:

It segfaults[LIST][*] when the plugin is enabled, I activate desktop effects in g-a-p, accept the new settings, and close g-a-p
[*] when I close cssm after activating the plugin while compiz is runing, and
[*] when I disable and re-enable the plugin in ccsm while compiz is running[/LIST]

Should we already report such things or better wait a bit (I'm sure having the old panels active at the same time doesn't add to stability :D).

> **DBO said:**
> Sorry about that
Heh, no need to be - it's pre-alpha, I'm not expecting everything to be ready. :)

> **DBO said:**
> we are working on it. It seems to be somewhat specific to 32-bit machines. Can you give any details about your current machine?

Not a 32-bit machine, but indeed running 32-bit Natty. AMD Opteron 144, nForce4 based motherboard, GeForce 6600GT (NV43), BLOB 260.19.06.

Edit: it's weird, sometimes I only get those four launcher icons (half white before activating the first time), and sometimes I get the "real deal" including the workspace switcher and all running applications (icons painted correctly). It also seems to flip between those two from time to time.

Having auto-hide enabled I saw something funny yesterday: out of nowhere a folded launcher icon (I guess it was the icon of the window list applet in the gnome-panel) flew in slomo from the bottom of the launcher bar (which still was hidden) to the top. This is so much more fun than using things that just work. :P

---

### Post by plun on 2010-11-13
About the bzr version:

How do I update my source  ??

```
bzr up 
```

doesn't seem to see new revisions ??

[https://code.launchpad.net/~unity-team/unity/trunk](https://code.launchpad.net/~unity-team/unity/trunk)

Much more work to remove the unity-folder and download evrything again.

---

### Post by MacUntu on 2010-11-13
Natty: seems I'm missing boost headers/libraries. I installed libboost1.42-all-dev, but that's maybe overkill? Would be good to have the right packages added to the dependencies in the [wiki](https://wiki.ubuntu.com/Unity/InstallationGuide).

**Edit:**
All the launcher issues seem to be fixed in the upstream code. :) Still getting the crashes, though.

> **plun said:**
> About the bzr version:

How do I update my source  ??

```
bzr up 
```

doesn't seem to see new revisions ??

```
bzr pull
```

**Another Edit:**
Sometimes the indicator placement is wrong:
[img]http://img.xrmb2.net/images/552274.png[/img]

---

### Post by MacUntu on 2010-11-13
To change the default launchers, you can edit '/usr/share/glib-2.0/schemas/com.canonical.Unity.gschema.xml' to include all the .desktop files you want (for correct file names look into '/usr/share/applications'). Then compile them like:```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas
```

**Edit:**
If 'glib-compile-schemas' cannot be found, install the package 'libglib2.0-bin'.

---

### Post by plun on 2010-11-13
> **MacUntu said:**
> 


```
bzr pull
```



```
plun@plun-laptop:~/unity$ bzr pull
Using saved parent location: http://bazaar.launchpad.net/~unity-team/unity/trunk/
No revisions to pull.    
```

Thank you....;)

Howto rebuild it with new revisions..... ??

---

### Post by MacUntu on 2010-11-13
Not sure, I'd remove and re-create the 'build' dir and if there were any config changes I'd also re-run the config line.

---

### Post by DBO on 2010-11-13
> **MacUntu said:**
> Compiz seems to randomly die when closing either gnome-apperance-properties after enabling desktop effects or the ccsm.

SNIP

Having auto-hide enabled I saw something funny yesterday: out of nowhere a folded launcher icon (I guess it was the icon of the window list applet in the gnome-panel) flew in slomo from the bottom of the launcher bar (which still was hidden) to the top. This is so much more fun than using things that just work. :P

Can you try with the latest version of trunk. The half white icons wont be fixed but I am hoping the wandering icons will be. They are somewhat time based and I am not totally sure what is causing it yet either. Never been able to reproduce the issue actually.

---

### Post by autocrosser on 2010-11-13
Interesting question---I would like my desktop icons back---going to gconf I find that the preference is not writeable--any ideas?

---

### Post by DBO on 2010-11-13
> **autocrosser said:**
> Interesting question---I would like my desktop icons back---going to gconf I find that the preference is not writeable--any ideas?

That is not actually unity-compiz related... we dont touch that stuff right now.

---

### Post by MacUntu on 2010-11-13
> **DBO said:**
> Can you try with the latest version of trunk. The half white icons wont be fixed but I am hoping the wandering icons will be. They are somewhat time based and I am not totally sure what is causing it yet either. Never been able to reproduce the issue actually.

See the edit of post #164: I already tried the trunk version and the flying launcher icons seem to be gone - and so are the half white launcher icons!

However, the icons now seem to disappear after a while (the launchers are there, just the icons aren't displayed).

**Edit:** Hm, I changed '/desktop/gnome/session/required_components_list' to not include the panel and the flying icon was the one from the gnome-panel's window list applet, so maybe that's why I'm not seeing it anymore. Will revert and test again.

**Edit 2:** It didn't fly, but that icon popped up again in the launcher:

[img]http://img.xrmb2.net/images/203322.png[/img]

Any way to find out what it is? 

**Edit 3:** And now all launchers but this one disappeared (they are really gone, not just the icons).

---

### Post by DBO on 2010-11-13
> **MacUntu said:**
> See the edit of post #164: I already tried the trunk version and the flying launcher icons seem to be gone - and so are the half white launcher icons!

However, the icons now seem to disappear after a while (the launchers are there, just the icons aren't displayed).

**Edit:** Hm, I changed '/desktop/gnome/session/required_components_list' to not include the panel and the flying icon was the one from the gnome-panel's window list applet, so maybe that's why I'm not seeing it anymore. Will revert and test again.

**Edit 2:** It didn't fly, but that icon popped up again in the launcher:

[img]http://img.xrmb2.net/images/203322.png[/img]

Any way to find out what it is? 

**Edit 3:** And now all launchers but this one disappeared (they are really gone, not just the icons).

its something to do with 32 bit. All my timestamps are getting screwed up. I am setting up a netbook right now with the hopes of debugging this crap by monday. This is insane, I have no idea why this is failing so hard on 32 bit versions...

Again to all 32 bit users. You will be experiencing terrible bugs for a while yet. It turns out the entire dev team runs 64 bit now (oops) so we are busy setting ourselves up some 32 bit dev boxes to make sure we dont make this mistake again.

---

### Post by MacUntu on 2010-11-13
Which brings me back to my question: does it make sense (at least for 32-bit users) to report bugs/crashes before Alpha 1 or will this just add noise?

---

### Post by DBO on 2010-11-13
> **MacUntu said:**
> Which brings me back to my question: does it make sense (at least for 32-bit users) to report bugs/crashes before Alpha 1 or will this just add noise?

Yeah its fine to report bugs, we are okay at triage :)

---

### Post by MacUntu on 2010-11-13
Good! And thanks for the info/feedback - we usually don't see many devs around here. ):P

---

### Post by DBO on 2010-11-13
> **MacUntu said:**
> Good! And thanks for the info/feedback - we usually don't see many devs around here. ):P

Well I feel bad about the way this thing turned out on 32 bit, so I am trolling around a bit trying to do damage control

---

### Post by plun on 2010-11-14
Running rev 604, 64 bits  (just rebuild it with the same commands)

One observation, when the Unity plugin is enabled Conky is "on top".....

[[IMG]http://img607.imageshack.us/img607/2643/snapshot77.th.png[/IMG]](http://img607.imageshack.us/i/snapshot77.png/)

---

### Post by bash on 2010-11-14
> **MacUntu said:**
> **Edit 2:** It didn't fly, but that icon popped up again in the launcher:

[img]http://img.xrmb2.net/images/203322.png[/img]

Any way to find out what it is? 

That should be the icon of gnome-panel.

---

### Post by MacUntu on 2010-11-14
> **bash said:**
> That should be the icon of gnome-panel.
Yeah, you are right: /usr/share/icons/hicolor/scalable/apps/gnome-panel.svg.

---

### Post by plun on 2010-11-14
> **MacUntu said:**
> To change the default launchers, you can edit '/usr/share/glib-2.0/schemas/com.canonical.Unity.gschema.xml' to include all the .desktop files you want (for correct file names look into '/usr/share/applications'). Then compile them like:```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas
```

Tested this and it works just fine.... Thanks ! :)

I have had some segmentation faults when I am closing apps.....  cannot do anything else then to log out.

---

### Post by autocrosser on 2010-11-14
OK--I'm FINALLY in--took long enough.....using the PPA version......Couple of "interesting" things--I normally auto-start BOINC on login & that "explodes" Unity, so right now I'm starting it a minute or so afterwards--thinking I'll need to do a "sleep-10" to make it play nice.....Took 3~4 logins to get the icons to work "right" & the BOINC icon shows as Empathy (??)--I compile BOINC & run it from my /home, so it looks like Unity can't place icons that are not in a .desktop format?

Anyway--it's working good, so I'm not going to muck around more with it today......

---

### Post by Rifester on 2010-11-14
Will we be able to change the icons in the Unity Launcher (In Appearances)?  I am running Unity now in Maverick and am curious if this feature will be ready for Natty...

---

### Post by MacUntu on 2010-11-14
> **Rifester said:**
> Will we be able to change the icons in the Unity Launcher (In Appearances)?  I am running Unity now in Maverick and am curious if this feature will be ready for Natty...

You can change the icons in the .desktop files, eg.```
Icon=/path/to/different/icon.svg
``` - else they follow the icon themes.

---

### Post by sgage on 2010-11-14
Any idea when compiz is going to be fixed? I'd love to check out unity-compiz, but I can't even get compiz to work...

---

### Post by plun on 2010-11-14
> **sgage said:**
> Any idea when compiz is going to be fixed? I'd love to check out unity-compiz, but I can't even get compiz to work...

It is fixed but I must first remove all Compiz packages and then reinstall them. (easiest with Synaptic)

A  compiz --replace command is then needed for the moment with Unity.

---

### Post by sgage on 2010-11-14
Ah, that did the trick! Thanks!

Not much to say at this point. I will have to poke around a bit more, but it seems you can't really do much with it. I am running a 32-bit system, so maybe there are still some issues...

---

### Post by DBO on 2010-11-14
> **sgage said:**
> Ah, that did the trick! Thanks!

Not much to say at this point. I will have to poke around a bit more, but it seems you can't really do much with it. I am running a 32-bit system, so maybe there are still some issues...

I made a rather non-trivial change last night to try to fix 32-bit systems. It seems we were having some issues with our timers coming back all sorts of weird. If you could test and make sure things seem to generally be working that would be great!

---

### Post by sgage on 2010-11-14
> **DBO said:**
> I made a rather non-trivial change last night to try to fix 32-bit systems. It seems we were having some issues with our timers coming back all sorts of weird. If you could test and make sure things seem to generally be working that would be great!

Happy to do it. I realize that it's early days, and I guess I don't have a very clear idea of what is supposed to be working at this point. E.g., I couldn't even figure out a way to launch a program. Basically, what was running when I invoked Unity was what I had to work with. I couldn't find any sort of launching menu or way to pin apps to the vertical bar. Also the half-white icon thing.

Anyway, if I knew what to expect I could test more effectively...

Thanks for your efforts!

---

### Post by DBO on 2010-11-14
> **sgage said:**
> Happy to do it. I realize that it's early days, and I guess I don't have a very clear idea of what is supposed to be working at this point. E.g., I couldn't even figure out a way to launch a program. Basically, what was running when I invoked Unity was what I had to work with. I couldn't find any sort of launching menu or way to pin apps to the vertical bar. Also the half-white icon thing.

Anyway, if I knew what to expect I could test more effectively...

Thanks for your efforts!

Basically I am interested in the half white icon thing and the wandering icon thing.

---

### Post by fluteflute on 2010-11-14
Compiz won't load for me in VirtualBox. This is with up to date Natty plus the PPA.

```
greg@natty-VirtualBox:~$ compiz
Backend     : ini
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Initializing composite options...done
Backend     : ini
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Initializing composite options...done
compiz (core) - Fatal: Software rendering detected.
compiz (opengl) - Error: initScreen failed
compiz (core) - Error: Couldn't activate plugin 'opengl'
compiz (core) - Error: Plugin 'opengl' not loaded.

Initializing decor options...done
Initializing resize options...done
Initializing move options...done
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: InitPlugin 'scale' failed
compiz (core) - Error: Couldn't activate plugin 'scale'
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: InitPlugin 'unityshell' failed
compiz (core) - Error: Couldn't activate plugin 'unityshell'
Initializing place options...done
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: InitPlugin 'expo' failed
compiz (core) - Error: Couldn't activate plugin 'expo'
Initializing mousepoll options...done

```

---

### Post by DBO on 2010-11-14
> **fluteflute said:**
> Compiz won't load for me in VirtualBox. This is with up to date Natty plus the PPA.

```
greg@natty-VirtualBox:~$ compiz
Backend     : ini
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Initializing composite options...done
Backend     : ini
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Initializing composite options...done
compiz (core) - Fatal: Software rendering detected.
compiz (opengl) - Error: initScreen failed
compiz (core) - Error: Couldn't activate plugin 'opengl'
compiz (core) - Error: Plugin 'opengl' not loaded.

Initializing decor options...done
Initializing resize options...done
Initializing move options...done
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: InitPlugin 'scale' failed
compiz (core) - Error: Couldn't activate plugin 'scale'
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: InitPlugin 'unityshell' failed
compiz (core) - Error: Couldn't activate plugin 'unityshell'
Initializing place options...done
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: InitPlugin 'expo' failed
compiz (core) - Error: Couldn't activate plugin 'expo'
Initializing mousepoll options...done

```

You dont have the required hardware support in virtual box.

---

### Post by MacUntu on 2010-11-14
> **DBO said:**
> Basically I am interested in the half white icon thing and the wandering icon thing.

Have been playing around all day and not seen both (that is with the trunk version without your changes - only got those bugs with the PPA).

---

### Post by fluteflute on 2010-11-14
> **DBO said:**
> You dont have the required hardware support in virtual box.
Any idea how I go about changing that fact?

---

### Post by DBO on 2010-11-14
> **MacUntu said:**
> Have been playing around all day and not seen both (that is with the trunk version without your changes - only got those bugs with the PPA).

What revision?

---

### Post by DBO on 2010-11-14
> **fluteflute said:**
> Any idea how I go about changing that fact?

Not a clue :) Hardware acceleration in virtual machines is still not the worlds most stable thing :/

---

### Post by MacUntu on 2010-11-14
> **dbo said:**
> what revision?
601.

---

### Post by plun on 2010-11-14
> **MacUntu said:**
> 601.

Running the same with 64 bit....and it works.

My seg fault crashes (a few) probably comes from firefox 4.
```

(firefox-4.0-bin:30625): Gdk-WARNING **: XID collision, trouble ahead
```

Another issue I can see is this error

```
** (<unknown>:30521): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

```

---

### Post by MacUntu on 2010-11-14
[QUOTE=plun]```
** (<unknown>:30521): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

```[/QUOTE]

I can confirm that one. Just hadn't enough time to collect backtraces for bug reports yet.

---

### Post by plun on 2010-11-14
Ok... checked my logfiles and found this.....

```
Nov 14 10:26:06 plun-laptop kernel: [ 6232.967997] unity-panel-ser[4588] general protection ip:7fe6c349fc2d sp:7fff5ad00b80 error:0 in libc-2.12.1.so[7fe6c3422000+17a000]
Nov 14 10:26:06 plun-laptop kernel: [ 6232.981922] compiz[2285] general protection ip:7f28c9de7c2d sp:7ffffa97d8e0 error:0 in libc-2.12.1.so[7f28c9d6a000+17a000]
Nov 14 10:26:41 plun-laptop kernel: [ 6268.851818] polkit-gnome-au[1803] general protection ip:7f8e148418a8 sp:7fff5cd9f4e0 error:0 in libglib-2.0.so.0.2703.0[7f8e1481a000+e8000]
```

---

### Post by DBO on 2010-11-14
> **MacUntu said:**
> I can confirm that one. Just hadn't enough time to collect backtraces for bug reports yet.

Thats a warning from libbamf. It has to do with the dbus object falling off the bus before the close signal makes it to the consumer. It probably could just silently fail but I like it noisy during development cycles.

---

### Post by Merk42 on 2010-11-14
> **fluteflute said:**
> Any idea how I go about changing that fact?

Did you install the virtualbox additions?

---

### Post by kaldor on 2010-11-14
I'm using Virtualbox with Guest Additions and also have no luck with Unity.

---

### Post by cariboo on 2010-11-14
I've never been able to get 3D support in VIrtual Box, no matter what version and even if the guest additions installed.

We may have to wait for Oracle to catch up again. During the last couple of release cycles Vbox didn't work at the start of the cycle, but was working properly before the final release.

---

### Post by autocrosser on 2010-11-14
Several "interesting' crashes today....Using a OpenGL game "works", but will lockup Unity partway back to the desktop--My test with UT2004 was interesting...the side panel & top panel stayed during the full-screen game & the desktop partly redrew when I closed the game.  After a couple of reboots (took that for everything to come back up) did a "killall conky"--result was a Unity crash/hard lockup & then I was editing a .conkyrc script & had another crash when I saved & conky reloaded. Last crash was with Shotwell--opened the app & had a crash when I tried to enlarge one photo...all crashes locked the system up hard......

Couple of bug reports: [https://bugs.launchpad.net/unity/+bug/669109](https://bugs.launchpad.net/unity/+bug/669109)  (for OpenGL)
                                 [https://bugs.launchpad.net/unity/+bug/675334](https://bugs.launchpad.net/unity/+bug/675334)  (for killall & Conky)

All-in-all a "interesting" time was had.....My Unity install is kind'a b0rked now & its late, so no more for tonight.....

---

### Post by woodbj on 2010-11-14
I built Unity from source and go to enable it in the CompizConfig Settings Manager, the only problem I have is all the window bars and gnome-panels disappear after closing the ccsm, but it works perfectly fine while it is open.
Does this happen to anybody else?

---

### Post by Anduu on 2010-11-15
> **woodbj said:**
> I built Unity from source and go to enable it in the CompizConfig Settings Manager, the only problem I have is all the window bars and gnome-panels disappear after closing the ccsm, but it works perfectly fine while it is open.
Does this happen to anybody else?

It does that to me as well.

Once I logout and then log back in Unity stays running.

---

### Post by sgage on 2010-11-15
> **DBO said:**
> Basically I am interested in the half white icon thing and the wandering icon thing.

The half-white thing seems to be fixed as of Monday morning. And the icons don't seem to be wandering.

I ran compiz --replace with a few apps running. When I closed Thunderbird, it crashed: the vertical panel went away and I couldn't raise any of the other running apps. Logging out is the only way out of this that I could find. I've had the same thing happen closing other apps. 

Will keep testing.

Whoops! Logged bag in, ran compiz --replace, and have half-white, wandering icons. Too weird!

---

### Post by DBO on 2010-11-15
> **sgage said:**
> The half-white thing seems to be fixed as of Monday morning. And the icons don't seem to be wandering.

I ran compiz --replace with a few apps running. When I closed Thunderbird, it crashed: the vertical panel went away and I couldn't raise any of the other running apps. Logging out is the only way out of this that I could find. I've had the same thing happen closing other apps. 

Will keep testing.

Whoops! Logged bag in, ran compiz --replace, and have half-white, wandering icons. Too weird!

poop... can you try to get a second confirmation and ensure you are up to date?

---

### Post by sgage on 2010-11-15
> **DBO said:**
> poop... can you try to get a second confirmation and ensure you are up to date?

Alas, updated as of 1:40 EST, and still have half-white wandering icons. The strange thing is that my first try this morning worked nicely - the vertical panel was good, icons whole, everything in the top panel present and functioning.

Then I closed an app that had been running, and there was no window decoration. I could bring up a "run program" dialog, but not type into it.

When I logged out and back in, it was back to the half-white thing, and missing items on the top panel. I tried it several times, and I have since rebooted entirely but still no joy.

This is 32-bit natty, fully updated, nvidia GeForce 8500 GT running latest proprietary drivers.

---

### Post by DBO on 2010-11-15
> **sgage said:**
> Alas, updated as of 1:40 EST, and still have half-white wandering icons. The strange thing is that my first try this morning worked nicely - the vertical panel was good, icons whole, everything in the top panel present and functioning.

Then I closed an app that had been running, and there was no window decoration. I could bring up a "run program" dialog, but not type into it.

When I logged out and back in, it was back to the half-white thing, and missing items on the top panel. I tried it several times, and I have since rebooted entirely but still no joy.

This is 32-bit natty, fully updated, nvidia GeForce 8500 GT running latest proprietary drivers.

Can you make sure it is loading libunityshell.so and not libunity.so. There was a name change recently. Failing that do you think you could make it break on "IconVisibleProgress" in gdb (after attaching when its bugging) and getting me as much data as you can.

This is if you are comfortable enough with gdb of course :)

---

### Post by sgage on 2010-11-15
> **DBO said:**
> Can you make sure it is loading libunityshell.so and not libunity.so. There was a name change recently. Failing that do you think you could make it break on "IconVisibleProgress" in gdb (after attaching when its bugging) and getting me as much data as you can.

This is if you are comfortable enough with gdb of course :)

I'm afraid I don't have the gdb chops - if you can give me the steps, I'd be glad to give it a try...

---

### Post by DBO on 2010-11-15
> **sgage said:**
> I'm afraid I don't have the gdb chops - if you can give me the steps, I'd be glad to give it a try...

That is quite alright, I am concerned that you are not actually up to date. It is quite common to end up with old versions of unity hanging around.

---

### Post by sgage on 2010-11-15
> **DBO said:**
> That is quite alright, I am concerned that you are not actually up to date. It is quite common to end up with old versions of unity hanging around.

I have the 3.1.3-0ubuntu2 version - evidently the latest from the PPA - and the same version number of libunity3.

---

### Post by DBO on 2010-11-15
> **sgage said:**
> I have the 3.1.3-0ubuntu2 version - evidently the latest from the PPA - and the same version number of libunity3.

Oh me gusta, I thought you were running trunk. The next PPA update should fix this issue.

---

### Post by autocrosser on 2010-11-15
Do you have a idea when it will be updated?  I'm running the PPA also......

---

### Post by MikeMLP on 2010-11-15
If this chart is accurate, then Thursday, Nov. 18th!

[https://launchpad.net/unity/+series](https://launchpad.net/unity/+series)

---

### Post by autocrosser on 2010-11-15
Crossing fingers & waiting............:)

---

### Post by cariboo on 2010-11-17
I've broken up the Mega thread into to threads, one for Unity discussions and the other for technical questions.

---

### Post by cariboo on 2010-11-17
When I run:

```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas
```

I get the following output:

```
sudo: glib-compile-schemas: command not found
```

What am I missing?

---

### Post by autocrosser on 2010-11-17
> **cariboo907 said:**
> When I run:

```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas
```I get the following output:

```
sudo: glib-compile-schemas: command not found
```What am I missing?

I installed some of the libglib dev libraries & some other glib stuff---at work so I can't be more accurate......

---

### Post by MacUntu on 2010-11-19
It's in the libglib2.0-bin package.

---

### Post by dext on 2010-11-19
> **cariboo907 said:**
> I've broken up the Mega thread into **to** threads, one for Unity discussions and the other for technical questions. didnt you mean _two_ :p

---

### Post by sgage on 2010-11-19
A new Unity is in the ppa now. It is not much better than the last one. After a couple of minutes of poking around, the icons in the vertical bar suddenly just disappeared. And still no way to add a launcher to the bar that I can see. You get Firefox and Empathy and Totem, and whatever is running at the time you invoke Unity. 

I guess you could say I'm a bit disappointed - I hoped for something usable on this go-round. I'll wait for the next release...

---

### Post by Anduu on 2010-11-19
> **sgage said:**
> A new Unity is in the ppa now. It is not much better than the last one. After a couple of minutes of poking around, the icons in the vertical bar suddenly just disappeared. And still no way to add a launcher to the bar that I can see. You get Firefox and Empathy and Totem, and whatever is running at the time you invoke Unity. 

I guess you could say I'm a bit disappointed - I hoped for something usable on this go-round. I'll wait for the next release...

This new build is broken for me...no launcher appears and the top panel is totally unresponsive (ie can't even click username to logout now...)

---

### Post by cariboo on 2010-11-19
> **sgage said:**
> A new Unity is in the ppa now. It is not much better than the last one. After a couple of minutes of poking around, the icons in the vertical bar suddenly just disappeared. And still no way to add a launcher to the bar that I can see. You get Firefox and Empathy and Totem, and whatever is running at the time you invoke Unity. 

I guess you could say I'm a bit disappointed - I hoped for something usable on this go-round. I'll wait for the next release...

Did you see [this]("http://ubuntuforums.org/showpost.php?p=10111328&postcount=21") thread

---

### Post by MacUntu on 2010-11-19
PPA version seems to work fine here (Go 7600 GT). Looks like we'll get our quicklists back soon. :)

I'm also glad to see Unity working fine with the experimental Nouveau 3D drivers (I'm using 'libgl1-mesa-dri-experimental' from the [xorg-edgers PPA](https://launchpad.net/~xorg-edgers/+archive/ppa)).

---

### Post by cecilpierce on 2010-11-19
so far i trashed two natty installs trying unity, all i get is a white screen of death! tried to install the iso and it goes half way and craps out but for some reason it works on one of my mavericks and not the other ??? weird !
guess i give up.

---

### Post by autocrosser on 2010-11-20
Hmmm--Unity working very well here--PPA version (current 3.14) Source-updated Maverick-to-Natty--all current as of this evening....only "real" change I see in Unity is moving the desktop switcher into its own location at bottom left....

---

### Post by MacUntu on 2010-11-20
```
The following packages have unmet dependencies:
 libx11-xcb-dev : Depends: libx11-xcb1 (= 2:1.3.3-3ubuntu1) but 2:1.3.4+git20100720.554da76e-0ubuntu0sarvatt3 is to be installed
```

Booo, [building from source](https://wiki.ubuntu.com/Unity/InstallationGuideFromSource) isn't xorg-edgers friendly. ;-)

Also, there's no package 'libmetacityprivate-dev'. Should this be 'libmetacity-dev' or 'libmetacity-private0'?

---

### Post by plun on 2010-11-20
> **MacUntu said:**
> ```
The following packages have unmet dependencies:
 libx11-xcb-dev : Depends: libx11-xcb1 (= 2:1.3.3-3ubuntu1) but 2:1.3.4+git20100720.554da76e-0ubuntu0sarvatt3 is to be installed
```

Booo, [building from source](https://wiki.ubuntu.com/Unity/InstallationGuideFromSource) isn't xorg-edgers friendly. ;-)

Also, there's no package 'libmetacityprivate-dev'. Should this be 'libmetacity-dev' or 'libmetacity-private0'?

Well... I believe its the gnome3 ppa which is the problem not xorg-edgers.

For the moment I also cannot ppa-purge the gnome3 ppa

The ubuntu Compiz version then crashes with pixbuf-errors **if the unity plugin is enabled**.

No problem to build Unity without libmetacityprivate-dev, rev 614

I have also compiz installed with [Soreaus script]("http://gitweb.compiz.org/?p=users/soreau/scripts;a=summary") as an extra /opt install, works just fine. But I cannot build the unity plugin because of cmake errors with the GIT version...:---).

The bleeding edge....:D

---

### Post by MacUntu on 2010-11-20
Don't have the GNOME3 PPA enabled. ;)

If you want to build following the Wiki, you also need 'python-dev' and 'cython' (for compizconfig-python and ccsm). Also, those two must be installed with sudo, but they need the environment variables set - no idea how, I simply did 'sudo su' and repeated the three exports.

I'm halfway through, hope it'll work. :)

**Edit:**

Oh dear, built all but unity and it fails:```
warning: D-Bus GLib is deprecated, use GDBus
.../libunity/unity-io.vala:55.48-55.48: error: Argument 2: Cannot convert from `int' to `GLib.ReallocFunc?'
    var output = new MemoryOutputStream (null, 0, realloc, null);
                                               ^
.../libunity/unity-io.vala:59.43-59.48: error: Argument 1: Cannot convert from `void*' to `uint8[]'
        numread = yield input.read_async (buffer, buffer_lenght,
                                          ^^^^^^
.../libunity/unity-io.vala:65.27-65.32: error: Argument 1: Cannot convert from `void*' to `uint8[]'
        output.write_all (buffer, numread, out numwritten, null);
                          ^^^^^^
Compilation failed: 3 error(s), 1 warning(s)
make[2]: *** [libunity/unity-place-activation.c] Error 1
make[1]: *** [libunity/CMakeFiles/unity.dir/all] Error 2
make: *** [all] Error 2
```

---

### Post by plun on 2010-11-20
> **MacUntu said:**
> Don't have the GNOME3 PPA enabled. ;)

If you want to build following the Wiki, you also need 'python-dev' and 'cython' (for compizconfig-python and ccsm). Also, those two must be installed with sudo, but they need the environment variables set - no idea how, I simply did 'sudo su' and repeated the three exports.



Ok... I don't follow the wiki beacause of the Soreau script.... I am too lazy building every Compiz-package....:D 

The script also at the beginning checks and install all Compiz dependencies. 

After that we also have the glib-mainloop which I doesn't understand the meaning with...:confused:
[http://gitweb.compiz.org/?p=users/dbo/compiz-with-glib-mainloop;a=summary](http://gitweb.compiz.org/?p=users/dbo/compiz-with-glib-mainloop;a=summary)

My first priority is to remove the gnome3 ppa....;)

---

### Post by MacUntu on 2010-11-20
I'm not sure ppa-purge works right now (with Natty?). I had to manually remove the xorg-edgers PPA cause it always complained about "Could not find package list for PPA". I think it needs a '*Packages' file in '/var/lib/apt/lists' but I only see '*Packages.gz' files there.

---

### Post by plun on 2010-11-20
> **MacUntu said:**
> I'm not sure ppa-purge works right now (with Natty?). I had to manually remove the xorg-edgers PPA cause it always complained about "Could not find package list for PPA". I think it needs a '*Packages' file in '/var/lib/apt/lists' but I only see '*Packages.gz' files there.

Ok... I managed to build unity with Compiz from GIT but it fails during start.....

```
Initializing opengl options...done
Initializing decor options...done
Initializing water options...done
/opt/compiz++/bin/compiz (core) - Error: Plugin 'core' has ABI version '20080618', expected ABI version '20101111'.

/opt/compiz++/bin/compiz (core) - Error: InitPlugin 'unityshell' failed
/opt/compiz++/bin/compiz (core) - Error: Couldn't activate plugin 'unityshell'


```

:tongue:

---

### Post by MacUntu on 2010-11-20
r614 builds for you? Great, then I'm missing something. :D

@ Mods: maybe we should split this thread into PPA vs. source?

---

### Post by plun on 2010-11-20
> **MacUntu said:**
> r614 builds for you? Great, then I'm missing something. :D



Yep......  you told me about the bzr pull...):P

but the ABI error is strange when starting Compiz....:rolleyes:

---

### Post by MacUntu on 2010-11-20
Crap. :P Looking at the signature of the MemoryOutputStream constructor, the problem is definitely this D-Bus GLib  vs. GDBus thing, but I have no idea what I'm missing. I checked out all those branches today, so I should be up-to-date.

---

### Post by plun on 2010-11-20
OK...;)

Another strange issue is that I must use this syntax for building the unity plugin
```

cmake .. -DCMAKE_INSTALL_PREFIX=/opt/compiz++
```

and the wiki syntax fails...

```
cmake .. -DCMAKE_BUILD_TYPE=Debug -DCOMPIZ_PLUGIN_INSTALL_TYPE=package -CMAKE_INSTALL_PREFIX=/opt/compiz++

```

but... it cannot be a package if you install from source....:confused:

---

### Post by MacUntu on 2010-11-20
> **plun said:**
> and the wiki syntax fails...

Yes, I guess it's a typo and should be -DCMAKE instead of -CMAKE. After changing that, it compiled fine for me.

---

### Post by plun on 2010-11-20
> **MacUntu said:**
> Yes, I guess it's a typo and should be -DCMAKE instead of -CMAKE. After changing that, it compiled fine for me.

Yep, works but still the ABI error after compilation and install

cmake "configure" OK !

```
plun@plun-laptop:~/unity/build$ cmake .. -DCMAKE_BUILD_TYPE=Debug -DCOMPIZ_PLUGIN_INSTALL_TYPE=package -DCMAKE_INSTALL_PREFIX=/opt/compiz++
-- GSettings schemas will be installed into /usr/share/glib-2.0/schemas/
-- Configuring done
-- Generating done
-- Build files have been written to: /home/plun/unity/build

```

---

### Post by MacUntu on 2010-11-20
I just removed all the files that gave me errors (unity-io.vala, unity-place.vala, unity-appinfo-manager.vala), compiled, and it started without ABI error, but when I enabled the decorator plugin in ccsm, I got a crash. Visually there seems to be no difference between PPA and upstream code right now.

---

### Post by plun on 2010-11-20
> **MacUntu said:**
> I just removed all the files that gave me errors (unity-io.vala, unity-place.vala, unity-appinfo-manager.vala), compiled, and it started without ABI error, but when I enabled the decorator plugin in ccsm, I got a crash. Visually there seems to be no difference between PPA and upstream code right now.

Ok... I remember the good old Beryl days when such a thing was fixed in a minute....:D

---

### Post by MacUntu on 2010-11-20
Seems the information I got on IRC was inaccurate. You need 'libmetacity-dev' and not 'libmetacity-private0' (but I think the latter is installed by default anyway).

Edit: or not. Still no window decorators. Will go back to the PPA version. :P

---

### Post by plun on 2010-11-20
> **MacUntu said:**
> 
@ Mods: maybe we should split this thread into PPA vs. source?

Well... I forgot to comment this.....

Is this the newbies corner or a development fora ??

Its a real shame with *buntu" users makes a shame of themselves at upstream project or for example Phoronix discussions shouting for a PPA...:-k

Building something is basic stuff after leaving the newbie stadium, IMHO..;)

---

### Post by zika on 2010-11-20
> **plun said:**
> Well... I forgot to comment this.....

Is this the newbies corner or a development fora ??

Its a real shame with *buntu" users makes a shame of themselves at upstream project or for example Phoronix discussions shouting for a PPA...:-k

Building something is basic stuff after leaving the newbie stadium, IMHO..;)There is one ingredient You've left out of Your equation: spare time.  Sometimes it is just sheer enthusiasm that keeps us at the bleeding edge... Do not be so strict...

---

### Post by MacUntu on 2010-11-20
> **plun said:**
> Is this the newbies corner or a development fora ??
It's a testing & discussion forum. ;-) Being able to build things enables you to test changes earlier, but that's more a plus than a must.

---

### Post by plun on 2010-11-20
> **zika said:**
> There is one ingredient You've left out of Your equation: spare time.  Sometimes it is just sheer enthusiasm that keeps us at the bleeding edge... Do not be so strict...

Well.... I just want Ubuntu be more "intelligent"....;)

"upstream" laughs at *buntu" users when they come upstream and shouts for a PPA.....

The Unity wiki was also changed and the bzr way removed.... so an old wiki revision must be used....(partly wrong) ;)

---

### Post by NCLI on 2010-11-20
> **MacUntu said:**
> It's a testing & discussion forum. ;-) Being able to build things enables you to test changes earlier, but that's more a plus than a must.
What is in the repos is what we're testing, and what is proposed for inclusion. If the devs want us to test a new version of a package proposed for inclusion, they should build it, and upload it to the repos. We're providing a service for them; testing their unstable software for free. Building the packages for us is the least they can do.

Of course, anyone who wants to pull bzr branches and build their own stuff from source should be free to do so, but it should never be expected.

That's the way I look at it.

---

### Post by cariboo on 2010-11-20
> **plun said:**
> Well... I forgot to comment this.....

Is this the newbies corner or a development fora ??

Its a real shame with *buntu" users makes a shame of themselves at upstream project or for example Phoronix discussions shouting for a PPA...:-k

Building something is basic stuff after leaving the newbie stadium, IMHO..;)

I split the two threads because all the other discussions where getting in the way of any problems and solutions. It was getting pretty noisy in that thread.

---

### Post by plun on 2010-11-20
> **cariboo907 said:**
> I split the two threads because all the other discussions where getting in the way of any problems and solutions. It was getting pretty noisy in that thread.

Well, I am sorry about the discussion which occurred....

But I refuses to leave Ubuntu and go to for example Arch for using and build great software from source....;)

---

### Post by MacUntu on 2010-11-20
> **plun said:**
> "upstream" laughs at *buntu" users when they come upstream and shouts for a PPA.....

As NCLI pointed out: we are helping developers by testing their software. If they can afford to laugh about users that ask for easier testing, so be it. 

If I'd see an upstream project with that attitude I'd stop reporting bugs.

Buuuut, let's get back to topic. :)

---

### Post by plun on 2010-11-20
> **MacUntu said:**
> As NCLI pointed out: we are helping developers by testing their software. If they can afford to laugh about users that ask for easier testing, so be it. 

If I'd see an upstream project with that attitude I'd stop reporting bugs.

Buuuut, let's get back to topic. :)

OK....;)

Maybe we needs another forum for using software from source..... I cannot understand how Ubuntu can recruit new bug-hunters or developers if we are just testing ready packages..... recruit those from Arch or Gentoo...:confused:

Well, no more revisions today.... maybe in the private bzr...;)

---

### Post by NCLI on 2010-11-20
> **plun said:**
> OK....;)

Maybe we needs another forum for using software from source..... I cannot understand how Ubuntu can recruit new bug-hunters or developers if we are just testing ready packages..... recruit those from Arch or Gentoo...:confused:

Well, no more revisions today.... maybe in the private bzr...;)
What's the big difference in testing pre-built packages, and testing by building from source? If anything, having users test pre-built packages is an advantage to the developers, since they know exactly what version of their application users are testing.

Now, developers occasionally ask us here in the testing forum or on Launchpad to build an application from source if we've had issues they hope to fix with the latest bzr revision, and we usually do it, because the developer has taken time to address our issue, and the least we can do is to help them find out whether our issue has been solved before they go through the trouble of a general deployment through the repos.

However, to expect users to test all major packages by building them from source is just madness, and would also make widespread testing improbable, since most people have other things to do with their computer than building the latest revision of an unstable piece of software from source.

I'm sorry if I come off as being a little pissy, but you suggesting splitting the testing forum in "testing source" and "testing packages," actually does **** me off. It would mean that, in order to do any relevant testing on a package, we would have to pull the latest revision from bzr or git, then build it, use it, and repeat the process when a new version comes out. Those of us who simply don't have the time to do so would essentially be testing outdated software which has already been tested by the source testers.

It would make those who don't have the time to build from source feel less motivated, and would probably end up resulting in less active testers.

---

### Post by plun on 2010-11-20
> **NCLI said:**
> What's the big difference in testing pre-built packages, and testing by building from source? If anything, having users test pre-built packages is an advantage to the developers, since they know exactly what version of their application users are testing.



Well... its a big difference if you look att the Linux eco-system.

*buntu" users makes a joke of themselves everywhere when they visit a upstream-project.

For me this is EOD and I am following this wiki:

[https://wiki.ubuntu.com/Unity/InstallationGuideFromSource](https://wiki.ubuntu.com/Unity/InstallationGuideFromSource)

I am also building Compiz with Soreus script and I have no help from U-F with this... the Compiz forum is also a rather empty place for the moment..:^o

Lets move on....:D

---

### Post by NCLI on 2010-11-20
> **plun said:**
> Well... its a big difference if you look att the Linux eco-system.

*buntu" users makes a joke of themselves everywhere when they visit a upstream-project.

For me this is EOD and I am following this wiki:

[https://wiki.ubuntu.com/Unity/InstallationGuideFromSource](https://wiki.ubuntu.com/Unity/InstallationGuideFromSource)

I am also building Compiz with Soreus script and I have no help from U-F with this... the Compiz forum is also a rather empty place for the moment..:^o

Lets move on....:D

Ok, let's move on, but I very much disagree with your suggestion that expecting developers who want their software tested to provide a pre-built package = making a fool out of themselves.

I also don't think asking for PPAs from upstream is making a fool of oneself so much as illustrating the huge difference between the Ubuntu project's approach to the end user, compared to most other open source projects' approach. 

I'm not saying either of them are right are wrong, but I am starting to see why Ubuntu is the most popular Linux distro.

---

### Post by plun on 2010-11-20
> **NCLI said:**
> 
I'm not saying either of them are right are wrong, but I am starting to see why Ubuntu is the most popular Linux distro.

Well... a second EOD...:D

Ubuntu needs bug-hunters, packagers and real developers and somewhere those must be recruited.... my english is so bad and if it was a little better I join directly for bug-hunting and packaging...;)  

So somehow we must deal with source-code....;)  a challenge for the future... !!

Still getting ABI error when starting Compiz....:tongue:

---

### Post by moore.bryan on 2010-11-21
Hopefully you fine folks can help me on this one. I've followed the explicit build [instructions]("https://wiki.ubuntu.com/Unity/InstallationGuideFromSource) for Unity on Maverick and ran into very few problems--one was a permissions problem where /opt/unity wasn't writable because the instructions never tell you to change it's permissions. 

Also, on a side-note, shouldn't *all* the commands in the instructions use "sudo" since they're all writing to /opt?

Anyway... everything compiled fine--took ages--and then I logged-out, loggged-back in, launched ccsm and there was no Unity plugin. I followed that process three times with no such luck. Then I thought to go into the /opt/unity/bin directory. I saw ccsm and launched it from there, thinking--apparently wrongly--that would be the one I needed. Alas, still no Unity plugin.

So, I'm stuck. How the hell can I get Unity to work?

Thanks, in-advance.

EDIT:
Trying to rebuild gets me this error when trying to cmake unity:
```

bryan@blue-asus:~/unity/build$ cmake .. -DCMAKE_BUILD_TYPE=Debug -DCOMPIZ_PLUGIN_INSTALL_TYPE=package -CMAKE_INSTALL_PREFIX=/opt/unity
loading initial cache file MAKE_INSTALL_PREFIX=/opt/unity
CMake Error: Error processing file:MAKE_INSTALL_PREFIX=/opt/unity
-- GSettings schemas will be installed into /usr/share/glib-2.0/schemas/
-- Configuring incomplete, errors occurred!

```

---

### Post by plun on 2010-11-21
> **MacUntu said:**
> I'm not sure ppa-purge works right now (with Natty?). I had to manually remove the xorg-edgers PPA cause it always complained about "Could not find package list for PPA". I think it needs a '*Packages' file in '/var/lib/apt/lists' but I only see '*Packages.gz' files there.

Ok... found this troublemaker with ppa-purge
[https://bugs.launchpad.net/ubuntu/+source/ppa-purge/+bug/677961](https://bugs.launchpad.net/ubuntu/+source/ppa-purge/+bug/677961)

So its broken for the moment.

I managed to rebuild everything today and I have no ABI errors....but also no unity....

Loads OK but also brakes gnome-panel....

```
Setting Update "active_plugins"
Initializing unityshell options...done
Setting Update "launcher_autohide"
Setting Update "launcher_float"
IndicatorAdded: libappmenu.so
IndicatorAdded: libapplication.so
IndicatorAdded: libsoundmenu.so
IndicatorAdded: libmessaging.so
IndicatorAdded: libdatetime.so
IndicatorAdded: libme.so
IndicatorAdded: libsession.so

```

---

### Post by MacUntu on 2010-11-21
I haven't yet figured out how to combine those two ```
python setup.py install --prefix=/opt/unity
``` things with sudo - they obviously need it as you pointed out (and they also need the environment variables set a few steps earlier). But you don't need to change any permissions. Just run 'sudo su', log in, run the three 'export' lines from the wiki, then build/install the two components compizconfig-python and ccsm, 'exit' and continue with the rest.

As for your build problem: it's a typo and it should be```
cmake .. -DCMAKE_BUILD_TYPE=Debug -DCOMPIZ_PLUGIN_INSTALL_TYPE=package -DCMAKE_INSTALL_PREFIX=/opt/unity
```

Will fix this in the wiki.

Let's keep compile and PPA talk in the other thread. :)

---

### Post by moore.bryan on 2010-11-21
Trying this now, MacUntu; thanks. Where's the "other" thread?

EDIT:
Doesn't work. Compiz version replies 0.9.2.1, but Unity replies 0.2.46. How can I get the Unity I built to run?

EDIT2:
In the process of recompiling/rebuilding everything from scratch; will post-back results.

---

### Post by Elfy on 2010-11-21
the other thread is this one now that your post got moved ;)

---

### Post by moore.bryan on 2010-11-21
Thanks, forestpiskie!

---

### Post by plun on 2010-11-21
> **moore.bryan said:**
> 

EDIT2:
In the process of recompiling/rebuilding everything from scratch; will post-back results.

Well, another option for building Compiz is with Soreaus script....

Info:
[http://gitweb.compiz.org/?p=users/soreau/scripts;a=summary](http://gitweb.compiz.org/?p=users/soreau/scripts;a=summary)

Script download and to run it:
```
git clone git://anongit.compiz.org/users/soreau/scripts && ./scripts/build_compiz++

```
Default build location is /opt/compiz++

So all wiki commands must be changes for above location.

Much easier then to compile every compiz-package.... Soreaus script also builds everything.

Start command
```

/opt/compiz++/bin/compiz++ --replace
```

---

### Post by moore.bryan on 2010-11-21
No love at all... won't work for me. :-( Stuck with ugly old Unity.

---

### Post by lidex on 2010-11-22
Thought I'd give this a whirl, per the wiki method. Seems to do fine until I get to the make portion for unity. Any ideas what may be causing these errors:
```
[ 72%] Built target unityshell
[ 73%] Generating unity-place-activation.c, unity-place-browser.c, unity-place.c, unity-io.c, unity-appinfo-manager.c, unity.vapi, unity.h, unity_internal.h
warning: D-Bus GLib is deprecated, use GDBus
/home/lidex/unity/libunity/unity-io.vala:55.48-55.48: error: Argument 2: Cannot convert from `int' to `GLib.ReallocFunc?'
    var output = new MemoryOutputStream (null, 0, realloc, null);
                                               ^
/home/lidex/unity/libunity/unity-io.vala:59.43-59.48: error: Argument 1: Cannot convert from `void*' to `uint8[]'
        numread = yield input.read_async (buffer, buffer_lenght,
                                          ^^^^^^
/home/lidex/unity/libunity/unity-io.vala:65.27-65.32: error: Argument 1: Cannot convert from `void*' to `uint8[]'
        output.write_all (buffer, numread, out numwritten, null);
                          ^^^^^^
Compilation failed: 3 error(s), 1 warning(s)
make[2]: *** [libunity/unity-place-activation.c] Error 1
make[1]: *** [libunity/CMakeFiles/unity.dir/all] Error 2
make: *** [all] Error 2

```

---

### Post by MacUntu on 2010-11-22
> **lidex said:**
> ```
[ 72%] Built target unityshell
[ 73%] Generating unity-place-activation.c, unity-place-browser.c, unity-place.c, unity-io.c, unity-appinfo-manager.c, unity.vapi, unity.h, unity_internal.h
warning: D-Bus GLib is deprecated, use GDBus
/home/lidex/unity/libunity/unity-io.vala:55.48-55.48: error: Argument 2: Cannot convert from `int' to `GLib.ReallocFunc?'
    var output = new MemoryOutputStream (null, 0, realloc, null);
                                               ^
/home/lidex/unity/libunity/unity-io.vala:59.43-59.48: error: Argument 1: Cannot convert from `void*' to `uint8[]'
        numread = yield input.read_async (buffer, buffer_lenght,
                                          ^^^^^^
/home/lidex/unity/libunity/unity-io.vala:65.27-65.32: error: Argument 1: Cannot convert from `void*' to `uint8[]'
        output.write_all (buffer, numread, out numwritten, null);
                          ^^^^^^
Compilation failed: 3 error(s), 1 warning(s)
make[2]: *** [libunity/unity-place-activation.c] Error 1
make[1]: *** [libunity/CMakeFiles/unity.dir/all] Error 2
make: *** [all] Error 2

```

Open 'libunity/CMakeLists.txt', go to line 50 (vala_precompile...) and delete the two lines saying 'unity-io.vala' and 'unity-appinfo-manager.vala'.

---

### Post by cecilpierce on 2010-11-22
I installed unity and compiz and when I enable unity plug-in the top and bottom gnome-panels are still there. The screen shots on Compiz based Unity don't show them, what am I missing ?

---

### Post by MacUntu on 2010-11-22
I *think* this is normal right now, if you start it from within a GNOME session.

---

### Post by castrojo on 2010-11-22
There's a new bamf release: [https://lists.ubuntu.com/archives/natty-changes/2010-November/001736.html](https://lists.ubuntu.com/archives/natty-changes/2010-November/001736.html)

This should help with stability issues; if I can get some feedback if this solves flakiness when minimizing windows and overall stability that would help. The version is 0.2.62-0ubuntu1

---

### Post by cariboo on 2010-11-22
Is anyone else seeing a double list of directories when going to Places? This is just a new 32-bit install fully up to date. See screen shot.

---

### Post by cecilpierce on 2010-11-22
> **MacUntu said:**
> I *think* this is normal right now, if you start it from within a GNOME session.

Is there another way to start unity with out gnome-shell ?

I have a Maverick install with unity and I can switch from it to gnome with logout and choose between netbook or ubuntu desktop.

---

### Post by cariboo on 2010-11-22
Unity is a compiz plugin, so the only way to enable is to open compizconfig-settings-manager, the command is **ccsm**, to enable the plugin. You can turn it off, by disabling the plugin.

---

### Post by cecilpierce on 2010-11-22
> **cariboo907 said:**
> Is anyone else seeing a double list of directories when going to Places? This is just a new 32-bit install fully up to date. See screen shot.

I get that to, I noticed you have no panels top or bottom like I do, how did you get rid of them ?

---

### Post by MacUntu on 2010-11-22
I still have decorator problems. If I enable decorators, compiz crashes. If I start compiz with the decorator plugin enabled, the borders are there but I cannot move windows.

[[img]http://img.xrmb2.net/122051.jpg[/img]](http://img.xrmb2.net/images/122051.png)

Also interesting: the workspace switcher sticks to the bottom left when enabling autohide. Float causes a weird empty launcher slot:

[[img]http://img.xrmb2.net/973187.jpg[/img]](http://img.xrmb2.net/images/973187.png)

[If you are wondering why I don't have gnome-panels - I simply removed 'panel' from the list of required components of a GNOME session: gconf-editor > /desktop/gnome/session/required_components_list]

> **cariboo907 said:**
> Is anyone else seeing a double list of directories when going to Places? This is just a new 32-bit install fully up to date. See screen shot.

PPA: Even multiple times. Probably has a cause related to [bug 670950](https://bugs.launchpad.net/ubuntu/+source/indicator-appmenu/+bug/670950).
> **whiprush said:**
> if I can get some feedback if this solves flakiness when minimizing windows [...]
At least this one seems to work better after some short testing. :)

---

### Post by Framli on 2010-11-22
You may have noticed that Unity now accepts icon theming. 
Behold Unity + Ubuntu-mono-dark panel + Faenza :

---

### Post by MacUntu on 2010-11-22
Now it "just" needs to follow the GTK theme too. :P

---

### Post by MacUntu on 2010-11-23
> **MacUntu said:**
> the borders are there but I cannot move windows.

How about enabling the "Move Window" plugin in Compiz, stupid!? ](*,)

Guess that's the result of not using Compiz during the past years - I didn't notice which plugins I need and by default all were disabled.

---

### Post by cecilpierce on 2010-11-23
Is this normal when restart or shut down ?

---

### Post by go7Ul1ai on 2010-11-23
> **cecilpierce said:**
> Is this normal when restart or shut down ?

I get the same message as that, I guess it will be fixed over time.

---

### Post by cecilpierce on 2010-11-23
> **lee.jarratt said:**
> I get the same message as that, I guess it will be fixed over time.

Thanks! I don't fell so alone now  :D

---

### Post by NCLI on 2010-11-23
> **cecilpierce said:**
> Thanks! I don't fell so alone now  :D
I get it too ;)

---

### Post by lidex on 2010-11-25
> **MacUntu said:**
> Open 'libunity/CMakeLists.txt', go to line 50 (vala_precompile...) and delete the two lines saying 'unity-io.vala' and 'unity-appinfo-manager.vala'.

Thanks for that - seems to have done the trick, however it doesn't run correctly. I'll try recompiling from scratch when I get time. Any tips for doing so? Thanks again. ;)

---

### Post by MacUntu on 2010-11-25
I think this has already be changed in trunk (so you don't need to edit that file anymore). I'm currently building the whole fun on a second machine following the guide: [https://wiki.ubuntu.com/Unity/InstallationGuideFromSource](https://wiki.ubuntu.com/Unity/InstallationGuideFromSource)

Will report back later. :)

---

### Post by Quackers on 2010-11-25
Please excuse my complete Unity n0obness but can conky run in Unity? Or is that a silly question?

Edit: I see from post #33 that it is :-)  Please ignore me!

---

### Post by youoh on 2010-11-25
new Version of Unity installed and cant get tomboy and Firefox away bei editing /usr/share/glib-2.0/schemas

---

### Post by cariboo on 2010-11-25
Did you run:

```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas
```

After making the changes to the schemas file?

---

### Post by itemguy10 on 2010-11-25
building now :cool:

---

### Post by lidex on 2010-11-25
> **MacUntu said:**
> I think this has already be changed in trunk (so you don't need to edit that file anymore). I'm currently building the whole fun on a second machine following the guide: [https://wiki.ubuntu.com/Unity/InstallationGuideFromSource](https://wiki.ubuntu.com/Unity/InstallationGuideFromSource)

Will report back later. :)

Interesting, in just doing the first step again I get everything is already latest version except this:
```
The following NEW packages will be installed:
  libmetacity-dev

```
Apparently I never had that package??:-k

---

### Post by MacUntu on 2010-11-26
I added this a couple of days ago. Originally there was a dependency called "libmetacityprivate-dev" but that doesn't exist, so I changed it to "libmetacity-private0". As it seems this package is part of a default installation anyway, so I again changed it to "libmetacity-dev" (during configuration of one of the compiz packages you won't get metacity theme support for the decorator without that package so I guess that's the right one).

---

### Post by cecilpierce on 2010-11-26
How did all these new icons get put in and what does the "check mark 0" mean ?
Is there a way to add or subtract icons ?

---

### Post by ronacc on 2010-11-26
started unity ( repo version , not built from source or PPA) by checking unity plugin in CCSM , I was looking to see if there was a way to get rid of the sidebar , did not find one so I killed unity by rerunning CCSM and unchecking the unity plug in . When I was returned to the gnome desktop MY icons were offset as if the sidebar was still there and the desktop was non functional , gnome menu was there but clicks did nothing , terminal could be opened but could not be typed into or closed or even moved . pannels were there but non functional , had to use alt>sysrq>k to kill and restart the desktop .

---

### Post by plun on 2010-11-26
Well.... Unity bzr seems to be in broken state over the weekend..

```
plun@plun-laptop:~/unity/build$ cmake .. -DCMAKE_BUILD_TYPE=Debug -DCOMPIZ_PLUGIN_INSTALL_TYPE=package -DCMAKE_INSTALL_PREFIX=/opt/compiz++
CMake Error at CMakeLists.txt:79 (find_package):
  Could not find module FindCompiz.cmake or a configuration file for package
  Compiz.

  Adjust CMAKE_MODULE_PATH to find FindCompiz.cmake or set Compiz_DIR to the
  directory containing a CMake configuration file for Compiz.  The file will
  have one of the following names:

    CompizConfig.cmake
    compiz-config.cmake
CMake Error at CMakeLists.txt:80 (include):
  include could not find load file:
    CompizPlugin
CMake Error at CMakeLists.txt:81 (compiz_plugin):
  Unknown CMake command "compiz_plugin".
-- Configuring incomplete, errors occurred!

```

Ubuntu Compiz version also in broken state......
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/677391](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/677391)

Soreus GIT script works just fine.....

Still doesn't understand the meaning with DBOs mainloop ???


----

---

### Post by plun on 2010-11-26
Follow up... latest Ubuntu Compiz this evening gives this for me  (GIT Ok)

```
glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: call to empty boost::function


```

---

### Post by plun on 2010-11-27
Findings this morning after another update.

Ubuntu version:

- ini backend cannot be used (seg fault), **gconf backend starts but the Glib-plugin must be disabled** before with ccsm

If the Glib-plugin is enabled this error occurs
```
GLib:ERROR:/build/buildd/glib2.0-2.27.3/glib/gmain.c:2218:g_main_dispatch: assertion failed: (source)
```

If the glib-plugin is disabled, unity cannot be enabled.....:---)


Bzr version:

Still broken for me to build

GIT version:
Ok with Soreaus script without the "mainloop".....

EDIT also this happens:

```
(process:5428): GLib-CRITICAL **: g_source_unref: assertion `source != NULL' failed

glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: call to empty boost::function

aborting...
Trace/breakpoint trap

```


--

---

### Post by MacUntu on 2010-11-27
Nice, brrrreakage!!! :-) Will try to reproduce.

---

### Post by plun on 2010-11-27
> **MacUntu said:**
> Nice, brrrreakage!!! :-) Will try to reproduce.

Yup.....:D

The glib-mainloop seems to be a weak point....:-k

---

### Post by MacUntu on 2010-11-27
I actually have no idea what this mainloop integration is for (I once read this enables you to directly connect to signals instead of looking at all of them and picking the ones you need - guess this is less code and faster), but if there's an extra repo for it, I guess it's worth it. :P

---

### Post by dino99 on 2010-11-27
i'm surprised: update-manager list much more new packages than synaptic

---

### Post by plun on 2010-11-27
> **MacUntu said:**
> I actually have no idea what this mainloop integration is for (I once read this enables you to directly connect to signals instead of looking at all of them and picking the ones you need - guess this is less code and faster), but if there's an extra repo for it, I guess it's worth it. :P

Well a pure compiz-core version must be preferred, IMHO...;)

Can you confirm the other observations ?  ini, gconf and glib, glibmm ??

---

### Post by MacUntu on 2010-11-27
> **plun said:**
> Well a pure compiz-core version must be preferred, IMHO...;)

AFAIK it will land in Compiz soon! ;)

> **plun said:**
> Can you confirm the other observations ?  ini, gconf and glib, glibmm ??
Building everything from scratch on a slooooow machine. :D

---

### Post by terry_gardener on 2010-11-27
i updated today and rebooted and found that unity plugin was auto activated whixh surprised me a little. 
had to add a menu to bottom but not big deal, but will come later.  

at least it is working better than 2 weeks ago the last time i tried it.

---

### Post by MacUntu on 2010-11-27
> **plun said:**
> Can you confirm the other observations ?  ini, gconf and glib, glibmm ??

So I can confirm the segfault with the ini backend (first I see the launcher bar with workspace switcher and trash, then it goes *boom*), I cannot switch to gconf backend (probably missed to enable it in the build options), if I enable the GLib option I get the same warning.

Edit: Also no luck with Unity from the main repo (using its compiz configuration).

---

### Post by plun on 2010-11-27
> **MacUntu said:**
> So I can confirm the segfault with the ini backend (first I see the launcher bar with workspace switcher and trash, then it goes *boom*), I cannot switch to gconf backend (probably missed to enable it in the build options), if I enable the GLib option I get the same warning.

Well.... i have it running....:D   lost a dev-package during all compiz package updates....after that it was Ok to build the Unity plugin.

But.... I am running the pure Compiz GIT version (soreaus script) with the unity-bzr version.

The glib-plugin is NOT enabled.

[[IMG]http://i.imgur.com/ErPdps.jpg[/IMG]](http://imgur.com/ErPdp)

Testing....:D

---

### Post by MacUntu on 2010-11-27
Just purged every compiz related thing from this system (it was installed back then when having a rotating cube was super cool) and installed Unity from main => Can't make it work. Gconf or ini backend, GLib enabled = nothing, GLib disabled = looks fine, but dies after "IndicatorAdded: libsession.so".

---

### Post by plun on 2010-11-27
> **MacUntu said:**
> Just purged every compiz related thing from this system (it was installed back then when having a rotating cube was super cool) and installed Unity from main => Can't make it work. Gconf or ini backend, GLib enabled = nothing, GLib disabled = looks fine, but dies after "IndicatorAdded: libsession.so".

Ok... it really unstable  ;)..... crashes if I tries to enable a plugin...

```
Starting gtk-window-decorator
Setting Update "command_terminal"
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
Terminated

(process:5170): GLib-CRITICAL **: g_source_unref: assertion `source != NULL' failed

```

---

### Post by plun on 2010-11-27
Up and running efter several logout/logins ...;)

Next test, the new patched nm-applet

First a warning..
> Btw, your mommy always told you not to accept candy from strangers. The packages below are like candy from a stranger, except worse; and can eat your data, turn your computer into a zombie, or really make you curse. Use at your own risk.

[https://launchpad.net/~mathieu-tl/+archive/nm-indicator](https://launchpad.net/~mathieu-tl/+archive/nm-indicator)

Works just fine....:KS

[[IMG]http://i.imgur.com/Pz98Fs.jpg[/IMG]](http://imgur.com/Pz98F)

---

### Post by MacUntu on 2010-11-27
Nice. If I only had time to make a [not sucking system-applet replacement](http://www.youtube.com/watch?v=RrLSH958iHc)... cause that's the only thing left before I can really use Unity.

---

### Post by plun on 2010-11-27
> **MacUntu said:**
> Nice. If I only had time to make a [not sucking system-applet replacement](http://www.youtube.com/watch?v=RrLSH958iHc)... cause that's the only thing left before I can really use Unity.

Ok... I have conky running for checking processes....

[IMG]http://imgur.com/9AfsC.png[/IMG]

Another issue is a rather messy Unity panel....

[IMG]http://imgur.com/jaI0b.png[/IMG]

Testing...;)

---

### Post by andrek on 2010-11-27
I'm not sure if I'm having the same problem as you guys, but after todays update I'm unable to start the "Ubuntu Desktop Edition" (Unity) from gdm. The "Ubuntu Classic Desktop" starts without the compiz. Running compiz from a terminal gives me "segmentation fault" and compiz --debug :

```
andrzej@dell:~$ compiz --debug
compiz (core) - Debug: Could not stat() file /home/andrzej/.compiz-1/plugins/libcore.so : No such file or directory
compiz (core) - Debug: Could not stat() file /usr/lib/compiz/libcore.so : No such file or directory
compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

Launching fallback window manager

```

Is this some kind of a common issue nowadays, or is this something wrong with my system?

---

### Post by plun on 2010-11-27
> **andrek said:**
> I'm not sure if I'm having the same problem as you guys, but after todays update I'm unable to start the "Ubuntu Desktop Edition" (Unity) from gdm. The "Ubuntu Classic Desktop" starts without the compiz. Running compiz from a terminal gives me "segmentation fault" and compiz --debug :

```
andrzej@dell:~$ compiz --debug
compiz (core) - Debug: Could not stat() file /home/andrzej/.compiz-1/plugins/libcore.so : No such file or directory
compiz (core) - Debug: Could not stat() file /usr/lib/compiz/libcore.so : No such file or directory
compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

Launching fallback window manager

```

Well the package version doesn't work for me......

Is this some kind of a common issue nowadays, or is this something wrong with my system?


Well the package version doesn't work for me......

Try this...

- Remove the settings folder .compiz-1

- start ccsm and enable plugins again

- **Swith to gconf backend  !!!  (ccsm>preferences)**

- compiz --replace

---

### Post by andrek on 2010-11-27
> **plun said:**
> Well the package version doesn't work for me......

Try this...

- Remove the settings folder .compiz-1

- start ccsm and enable plugins again

- **Swith to gconf backend  !!!  (ccsm>preferences)**

- compiz --replace

This indeed makes compiz work again on the standard gnome desktop, yet unity doesn't start at all. I thought I could start unity manually by unity --replace but it states that I don't have 'unity' package installed, which obviously is rubbish.

---

### Post by plun on 2010-11-27
> **andrek said:**
> This indeed makes compiz work again on the standard gnome desktop, yet unity doesn't start at all. I thought I could start unity manually by unity --replace but it states that I don't have 'unity' package installed, which obviously is rubbish.

No... unity is a Compiz-plugin and must be enabled from CCSM

As i earlier wrote Compiz crashes with this error if the Glib plugin is enabled

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/677391](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/677391)

Git and Bzr works....

---

### Post by andrek on 2010-11-27
> **plun said:**
> No... unity is a Compiz-plugin and must be enabled from CCSM

As i earlier wrote Compiz crashes with this error if the Glib plugin is enabled

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/677391](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/677391)

Git and Bzr works....

Oh, thanks.
I have the glib plugin disabled yet it still crashes. I guess I'll have to wait till some updates come.

---

### Post by plun on 2010-11-27
I am trying to figure out howto add gnomenu to the Unity panel... or top panel....:confused: but everything fails  (also with docky)

About:
[https://launchpad.net/gnomenu](https://launchpad.net/gnomenu)

Maybe someone could ask "Whise" if he wants to work with Unity....with Screenlets he did a great work !

---

### Post by autocrosser on 2010-11-27
I have started another bug: [https://bugs.launchpad.net/unity/+bug/682215](https://bugs.launchpad.net/unity/+bug/682215)

Just posted this in the "repos" thread, but I thought I'd see if anyone here has seen it...I was moving 30G+ files/folders within the Unity install & Nautilus <REALLY> choked. From my "normal" Natty install into my Unity install I get 35/40Mb/s transfer--Transferring to  the Unity install (from within) I'm doing good to get 2.5/4Mb/s...pretty poor.

Moving multiple files in the Unity install causes my system to slow to a  crawl....This is with a i7-940 system with 2T worth of 7200rpm SATA2  drives......:eek:

---

### Post by moore.bryan on 2010-11-27
Can anyone help me on this one? I'm finally at a loss.

I'm trying to build from source for my Maverick install. I pull the unity folder, head into the tools dir, and build compiz. Then, I start from step one of the install from source directions and everything completes correctly, with no errors; however, there is no unity plugin in ccsm.

Any ideas?

---

### Post by plun on 2010-11-28
The menu challenge solved with Cardapio, great little Docky menu helper..;)

About:
[http://www.webupd8.org/2010/11/cardapio-menu-update-brings-docky.html#more](http://www.webupd8.org/2010/11/cardapio-menu-update-brings-docky.html#more)

[[IMG]http://i.imgur.com/Gyr6Ss.jpg[/IMG]](http://imgur.com/Gyr6S)

---

### Post by lucazade on 2010-11-28
> **plun said:**
> The menu challenge solved with Cardapio, great little Docky menu helper..;)

About:
[http://www.webupd8.org/2010/11/cardapio-menu-update-brings-docky.html#more](http://www.webupd8.org/2010/11/cardapio-menu-update-brings-docky.html#more)

[[IMG]http://i.imgur.com/Gyr6Ss.jpg[/IMG]](http://imgur.com/Gyr6S)

Using Unity You can still use:
Alt+F1 open gnome main menu
Alt+F2 open run application dialog

i think they are enough :)

---

### Post by plun on 2010-11-28
> **lucazade said:**
> Using Unity You can still use:
Alt+F1 open gnome main menu
Alt+F2 open run application dialog

i think they are enough :)

Aha.....  Alt-F1...:D   Thanks !!

Well, now I have two good menus...;)

---

### Post by MacUntu on 2010-11-28
If compiz fails to start for you and you see the following console output, then [here's a bug]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/682345") waiting for confirmation (original Unity from main repo w/o any PPAs):

```
[13:29] ~ $ compiz --replace
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing vpswitch options...done
Initializing gnomecompat options...done
Initializing move options...done
Initializing resize options...done
Initializing mousepoll options...done
Initializing place options...done
Initializing wall options...done
Initializing animation options...done
Initializing session options...done
Initializing fade options...done
Initializing scale options...done
Initializing expo options...done
Initializing ezoom options...done
Initializing staticswitcher options...done

** (<unknown>:9619): WARNING **: Unable to load GDesktopAppInfo for 'ubiquity-gtkui.desktop'

** (<unknown>:9619): WARNING **: Unable to load GDesktopAppInfo for 'ubuntuone-control-panel-gtk.desktop'
Initializing unityshell options...done
Setting Update "run_command_window_screenshot_key"
Setting Update "command_terminal"
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
IndicatorAdded: libappmenu.so
IndicatorAdded: libapplication.so
IndicatorAdded: libsoundmenu.so
IndicatorAdded: libmessaging.so
IndicatorAdded: libdatetime.so
IndicatorAdded: libme.so
IndicatorAdded: libsession.so
Segmentation fault
```

---

### Post by dino99 on 2010-11-28
natty i386, compiz activated as "normal" without unity

oem@oem-desktop:~$ compiz --replace
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing snap options...done
Initializing vpswitch options...done
Initializing gnomecompat options...done
Initializing mousepoll options...done
Initializing wall options...done
Initializing resize options...done
Initializing place options...done
Initializing move options...done
Initializing animation options...done
Initializing expo options...done
Initializing fade options...done
Initializing session options...done
Initializing scale options...done
Initializing resizeinfo options...done
Initializing ezoom options...done
Initializing staticswitcher options...done
Initializing workarounds options...done
compiz (core) - Error: Plugin 'text' not loaded.

compiz (ring) - Warn: No compatible text plugin loaded
Initializing ring options...done
Setting Update "command_terminal"
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"

nothing else, get stuck there.

---

### Post by plun on 2010-11-28
Just a little demo how it looks för the moment....

[http://www.youtube.com/watch?v=WhhGjwR-xIY](http://www.youtube.com/watch?v=WhhGjwR-xIY)

;)

---

### Post by rubenverweij on 2010-11-28
Hi all!
I'm testing the new unity with compiz on natty, and it's working quite well with my dual-monitor nouveau setup.
However, I believe my gnome-panel top panel is still present underneath the one drawn by unity. For example, Alt+F2 still runs the gnome panel launcher and pressing Alt+F1 gives me the applications menu.
My question is: how do I get rid of gnome-panel?
Thanks!

---

### Post by MacUntu on 2010-11-28
Ok, above bug was caused by those two missing .desktop files, so I simply reset the favorites with:```
gsettings set com.canonical.Unity.Launcher favorites "['gnome-terminal.desktop', ...]"
``` and now it runs fine. :)
> **rubenverweij said:**
> how do I get rid of gnome-panel?

I simply started gconf-editor and removed "panel" from the list located at "/desktop/gnome/session/required_components_list".

Edit: Oh, and make sure "/desktop/gnome/session/required_components/windowmanager" says "compiz", else you'll have no shell/panels at all. :D But be aware: I don't know how this is supposed to work, so it maybe cause troubles at a later time when devs change the session to not start with panels.

---

### Post by rubenverweij on 2010-11-28
> **MacUntu said:**
> I simply started gconf-editor and removed "panel" from the list located at "/desktop/gnome/session/required_components_list".

Thanks for your reply. I couldn't remove panel - just remove the value of panel (change "gnome-panel"->""). If I kill gnome-panel, it just restarts again. Any thoughts?

---

### Post by MacUntu on 2010-11-28
Under "/desktop/gnome/session/required_components_list" you should have a list:

[[img]http://img.xrmb2.net/693121.jpg[/img]](http://img.xrmb2.net/images/693121.png)

I just removed the "panel" entry, and in the "required_components" folder I set the window manager to "compiz" (left the panel entry alone):

[[img]http://img.xrmb2.net/308490.jpg[/img]](http://img.xrmb2.net/images/308490.png)

---

### Post by gnomeuser on 2010-11-28
using the package in Natty I can get Compiz to run and load the unity plugin but no launcher thingy appears, the top panel acts strangely like there is an offset between icons visual placement and actual placement making it hard to figure out how to access the correct application indicator. The global menu doesn't work anymore either.

In other words right now a total and utter failure on my machine, I think I will sit out on Unity testing for a while. Messing with it hampers Banshee work for little return right now. Perhaps past Alpha 2 I'll give it a try again.

---

### Post by plun on 2010-11-29
Two important updates today...

Compiz:
[https://lists.ubuntu.com/archives/natty-changes/2010-November/002115.html](https://lists.ubuntu.com/archives/natty-changes/2010-November/002115.html)

The nm-applet (with Unity support)
[https://lists.ubuntu.com/archives/natty-changes/2010-November/002158.html](https://lists.ubuntu.com/archives/natty-changes/2010-November/002158.html)

I noticed it yesterday that nm-applet is a little jumpy and it seems to be a memory leakage.

[https://bugs.launchpad.net/ubuntu/+source/appmenu-gtk/+bug/682786](https://bugs.launchpad.net/ubuntu/+source/appmenu-gtk/+bug/682786)

nm-applet jumps between 0 to 3 % all the time. Memory usage for this process is for the moment 70MB (yesterday after a whole day it was 120MB)

[IMG]http://imgur.com/8WEYV[/IMG]

---

### Post by MacUntu on 2010-11-29
> **plun said:**
> I noticed it yesterday that nm-applet is a little jumpy and it seems to be a memory leakage.

[https://bugs.launchpad.net/ubuntu/+source/appmenu-gtk/+bug/682786](https://bugs.launchpad.net/ubuntu/+source/appmenu-gtk/+bug/682786)

nm-applet jumps between 0 to 3 % all the time. Memory usage for this process is for the moment 70MB (yesterday after a whole day it was 120MB)


Plus tons of those in .xsession-errors:

```
(nm-applet:435): Gtk-CRITICAL **: IA__gtk_image_get_storage_type: assertion `GTK_IS_IMAGE (image)' failed

(nm-applet:435): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nm-applet:435): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

```

---

### Post by plun on 2010-11-29
> **MacUntu said:**
> Plus tons of those in .xsession-errors:

```
(nm-applet:435): Gtk-CRITICAL **: IA__gtk_image_get_storage_type: assertion `GTK_IS_IMAGE (image)' failed

(nm-applet:435): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nm-applet:435): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

```

Yup... confirmed.. "tons of them"...  Du you add it to the bug report ?


Another Compiz update is coming with a rather strange changelog..:confused:

> - use our own keybindings with new Compiz wm_name
      (note, upstream one faily try to install them ignoring DESTDIR, keep in mind when fixed to keep ours)

[https://lists.ubuntu.com/archives/natty-changes/2010-November/002165.html](https://lists.ubuntu.com/archives/natty-changes/2010-November/002165.html)



---

### Post by MacUntu on 2010-11-30
> **plun said:**
> Yup... confirmed.. "tons of them"...  Du you add it to the bug report ?

No, I doubt it's releated. Don't know if that's something to report against network-manager-gnome unless it's officially an indicator-applet. :)

```
[14:26] ~ $ cat .xsession-errors | grep -c "invalid (NULL) pointer instance"
7718
```

Uptime: six hours. :D

---

### Post by ccw on 2010-11-30
So what is the expected behavior with a gnome session right now? I'm just looking for a baseline.

I got 2 machines:
1)a workstation which as of today has no window manager, no unity, no gnome panel.
2) a laptop which as both gnome panel and the unity left hand thing (which doesn't seem very useful unless I want to open firefox or a tomboy note)

(I'll still use it but I just installed kubuntu-desktop as a backup)

---

### Post by cariboo on 2010-11-30
See the screenshot to see what my desktop looks like, I haven't done much customizing yet, but you can add applications to the panel using the instructions [here]("http://ubuntuforums.org/showpost.php?p=10176271&postcount=6")

---

### Post by ccw on 2010-11-30
> **cariboo907 said:**
> See the screenshot to see what my desktop looks like, I haven't done much customizing yet, but you can add applications to the panel using the instructions [here]("http://ubuntuforums.org/showpost.php?p=10176271&postcount=6")

ok... that's what the laptop looks like. Thanks.

---

### Post by godhika on 2010-11-30
> **cariboo907 said:**
> See the screenshot to see what my desktop looks like, I haven't done much customizing yet, but you can add applications to the panel using the instructions [here]("http://ubuntuforums.org/showpost.php?p=10176271&postcount=6")

No need for that procedure anymore with the latest version of Unity (3.2.2 ) right clicking the icon lets you pin/unpin your applications. To start an application which is not in the launcher, click he Circle of friends icon, which opens now /usr/share/applications, as a temporarily substitute for the not yet implemented/ported Unity places.

---

### Post by zika on 2010-11-30
> **ccw said:**
> So what is the expected behavior with a gnome session right now? I'm just looking for a baseline.

I got 2 machines:
1)a workstation which as of today has no window manager, no unity, no gnome panel.
2) a laptop which as both gnome panel and the unity left hand thing (which doesn't seem very useful unless I want to open firefox or a tomboy note)

(I'll still use it but I just installed kubuntu-desktop as a backup)On 1) I would do:```
gksu gedit ~/.gconf/desktop/gnome/session/required_components/%gconf.xml
```
and change **compiz** to **metacity**...

---

### Post by cariboo on 2010-11-30
> **godhika said:**
> No need for that procedure anymore with the latest version of Unity (3.2.2 ) right clicking the icon lets you pin/unpin your applications. To start an application which is not in the launcher, click he Circle of friends icon, which opens now /usr/share/applications, as a temporarily substitute for the not yet implemented/ported Unity places.

I see that now, I just did the another update 15 minutes ago.

---

### Post by autocrosser on 2010-11-30
Is theming working yet? I'm getting tired of orange.......

---

### Post by mc4man on 2010-11-30
> Is theming working yet? I'm getting tired of orange.......
Well everything in appearances preferences is usable, (using the r. click on desktop to open, any other means like gnome control center crashes unity or something
though the control center works ok for most else

---

### Post by cpatrick08 on 2010-12-01
when i go to the login screen i can select a session called ubuntu classic desktop which looks like the previous versions of ubuntu with the global menu

---

### Post by Harry33 on 2010-12-01
> **cpatrick08 said:**
> when i go to the login screen i can select a session called ubuntu classic desktop which looks like the previous versions of ubuntu with the global menu

Yes the "Ubuntu Classic" is exactly the same as Gnome-Panel.
The "Ubuntu Desktop Environment" in login screen opens Unity, which is the default desktop from now on.
If you have installed package gnome3-session, there is the third option in login screen:
"Gnome3", which opens Gnome-shell.

---

### Post by MacUntu on 2010-12-01
> **autocrosser said:**
> Is theming working yet? I'm getting tired of orange.......

If you call recompiling with different colors "theming", then yes! :p

[[img]http://img.xrmb2.net/176813.jpg[/img]](http://img.xrmb2.net/images/176813.png)

:KS:KS

---

### Post by cecilpierce on 2010-12-01
So far every thing seems to work good !  :)

---

### Post by MacUntu on 2010-12-01
Don't know what it is with the screenshot tool always getting in the way. :-/

---

### Post by go7Ul1ai on 2010-12-01
> **MacUntu said:**
> If you call recompiling with different colors "theming", then yes! :p

[[img]http://img.xrmb2.net/176813.jpg[/img]](http://img.xrmb2.net/images/176813.png)

:KS:KS

You never fail to impress me with your theming abilities :)

---

### Post by cecilpierce on 2010-12-01
Soon as you said that now my screenshot icon bring up "Eye of Gnome" junk but Print Scrn button don't ???

---

### Post by MacUntu on 2010-12-01
> **lee.jarratt said:**
> You never fail to impress me with your theming abilities :)

Credit where credit is due - *I* didn't "create" anything, just changed colors from dark to light and from light to dark. I'm just not the dark theme guy. Unfortunately my customizations get overwritten with every Unity update, so I really hope we'll soon be able to edit stuff more user-friendly. :D

> **cecilpierce said:**
> Soon as you said that now my screenshot icon bring up "Eye of Gnome" junk but Print Scrn button don't ???

Probably the "Ubuntu Trial Edition" bug: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/683623](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/683623) :D

---

### Post by cecilpierce on 2010-12-01
Probably the "Ubuntu Trial Edition" bug: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/683623](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/683623) :D[/QUOTE]

Thats real cool ! How do you find all these things?
I'm getting a head ache ! I think I'll go ride my bike for awhile, later :p

---

### Post by MacUntu on 2010-12-01
> **cecilpierce said:**
> Thats real cool ! How do you find all these things?

It's stormy and cold outside and boring inside. :D Or maybe it's a talent! :KS

---

### Post by castrojo on 2010-12-01
Just an FYI guys, didrocks passes along that if you want to turn unity off just log out and log back into the GNOME Classic session, going into CCSM and turning it off will probably crash.

Actually, if you notice that clicking things in ccsm can make it crash. The bugs are filed and they're working on it, just an FYI to avoid you having to lose your session. See here for more info: [http://penguindroppings.wordpress.com/2010/12/01/compiz-vs-ubuntu-classic-desktop/](http://penguindroppings.wordpress.com/2010/12/01/compiz-vs-ubuntu-classic-desktop/)

> 
- Do not disable the Unity plugin in CompizConfig Settings Manager while in Unity (or enable it when not in Unity)
- To use Unity, login to GDM with ‘Ubuntu Desktop’
- To use the traditional desktop, login to GDM with ‘Ubuntu Classic Desktop’
- If after logging in to the Ubuntu Classic Desktop your window manager does not start, this might be bug #683686. To work around it, logout, move your ~/.config/compiz-1 aside (logging into a console first), then log back in with GDM like normal. This bug is actively being worked on.
- There is a known bug with compiz and the gnome-panel that may cause applets to not load. Logging out and back in again usually solves this. This bug is actively being worked on.


---

### Post by MacUntu on 2010-12-01
Thanks! I just like to add that you do not lose your session if Compiz/Unity crashes. You can always go to a virtual terminal (Ctrl-Alt-F1) and run ```
DISPLAY=:0.0 metacity --replace &
``` to at least be able to manage your windows. ;)

---

### Post by zika on 2010-12-01
> **MacUntu said:**
> Thanks! I just like to add that you do not lose your session if Compiz/Unity crashes. You can always go to a virtual terminal (Ctrl-Alt-F1) and run ```
DISPLAY=:0.0 metacity --replace &
``` to at least be able to manage your windows. ;)Or```
sudo nano ~/.gconf/desktop/gnome/session/required_components/%gconf.xml
```and replace *compiz* with *metacity*...:popcorn:

---

### Post by godhika on 2010-12-02
@ cecilpierce

Have you activated alpha transparency or is this a hint of things to come?

---

### Post by cecilpierce on 2010-12-02
> **godhika said:**
> @ cecilpierce

Have you activated alpha transparency or is this a hint of things to come?

No and yes, its already working well, just takes a little getting use to :)

---

### Post by Starks on 2010-12-02
I'm rather pissed at how Unity handles window decorations.

If my I move my app's window decorator off-screen within my current workspace, there is no way to drag it back or right-click "Move" it back.

---

### Post by MacUntu on 2010-12-02
Alt-Click and move?

---

### Post by ratcheer on 2010-12-02
> **Starks said:**
> I'm rather pissed at how Unity handles window decorations.

If my I move my app's window decorator off-screen within my current workspace, there is no way to drag it back or right-click "Move" it back.

I agree. I have been using Alt+Tab, but I am not sure this is the same thing you are referring to.

Tim

---

### Post by Starks on 2010-12-02
No, that's not it at all.

Some apps like SMPlayer creep up past the top panel.

Alt-Tab has nothing to do with this.

I'm talking about the lack of right-click options in Unity.

---

### Post by MacUntu on 2010-12-02
> **Starks said:**
> Some apps like SMPlayer creep up past the top panel.

Well, that sounds like a bug.

---

### Post by mc4man on 2010-12-02
It would seem that most media players, when going from a windowed mode to fullscreen and then back will end up attached to upper bar in left corner.
Meanwhile losing decoration, previous window size and obviously previous position (probably a compiz issue

Actually the idea that anyone would want/like the disconnect between players and their 'taskbar'  on a desktop  is hard to understand

---

### Post by VeeDubb on 2010-12-02
> **MacUntu said:**
> Alt-Click and move?

Just tested this.  Works great for me.

---

### Post by Starks on 2010-12-02
> **mc4man said:**
> It would seem that most media players, when going from a windowed mode to fullscreen and then back will end up attached to upper bar in left corner.
Meanwhile losing decoration, previous window size and obviously previous position (probably a compiz issue

Actually the idea that anyone would want/like the disconnect between players and their 'taskbar'  on a desktop  is hard to understand

I'll file a bug if one doesn't already exist.

---

### Post by mc4man on 2010-12-02
> I'll file a bug if one doesn't already exist. 
The Alt+click can pull it back, though it shouldn't be doing that in the first place. Trying out the 'classic' desktop see the same thing, so maybe compiz?

---

### Post by lidex on 2010-12-03
> **mc4man said:**
> The Alt+click can pull it back, though it shouldn't be doing that in the first place. Trying out the 'classic' desktop see the same thing, so maybe compiz?

Yeah, and if I do it repeatedly it moves further and further off screen. Just tried wmv file open in vlc and it is completely off-screen. (This is in classic double-clicking on the file in nautilus.) Mpg doing the same.

Edit: AVI doing the same but it's somewhat random. If I change from one format to another it opens onscreen the first time.
Subsequent opening of that same format goes off-screen.??

---

### Post by mc4man on 2010-12-03
Don't really see any increasing offset from repeated actions, but notice something else.
Any app (window) that can be fullscreened will after returning from  fullscreen be able to be moved completly off screen to the top  ie. the panel is no longer a 'barrier'.
While i'm not aware of whether 'unity' is in 'effect' whatsoever while on the classic desktop it seems a bit suspect.
- unity has no 'border' so to speak at the top  (that bar is an overlay of sorts) and the default placement of a newly opened window is upper top left, just where these windows are heading when coming out of fullscreen mode.

(though I'd still think compiz is at fault here

Edit:
Am curious, if known, - where does "gsettings set com.canonical.Unity.Launcher favorites" write to?

Re-edit
While vlc doesn't keep moving (using 1.2+), just tried w/ totem and totem-xine. In this case yes, repeated fullscreen > windowed does increase the offset. After 4 cycles totem is 'gone' completly, but still playing. Can be retrieved enough to grab by re-opening.

---

### Post by Anduu on 2010-12-03
> **mc4man said:**
> Don't really see any increasing offset from repeated actions, but notice something else.
Any app (window) that can be fullscreened will after returning from  fullscreen be able to be moved completly off screen to the top  ie. the panel is no longer a 'barrier'.
While i'm not aware of whether 'unity' is in 'effect' whatsoever while on the classic desktop it seems a bit suspect.
- unity has no 'border' so to speak at the top  (that bar is an overlay of sorts) and the default placement of a newly opened window is upper top left, just where these windows are heading when coming out of fullscreen mode.

(though I'd still think compiz is at fault here

Edit:
Am curious, if known, - where does "gsettings set com.canonical.Unity.Launcher favorites" write to?

Re-edit
While vlc doesn't keep moving (using 1.2+), just tried w/ totem and totem-xine. In this case yes, repeated fullscreen > windowed does increase the offset. After 4 cycles totem is 'gone' completly, but still playing. Can be retrieved enough to grab by re-opening.

Definitely not limited to Unity.This happens to me without the Unity plugin enabled.

---

### Post by gacb on 2010-12-03
Is there a way to modify the launcher; i.e smaller icons, move to the bottom, autohide?

---

### Post by MacUntu on 2010-12-03
> **gacb said:**
> Is there a way to modify the launcher; i.e smaller icons,
No.
> **gacb said:**
> move to the bottom,
No.
> **gacb said:**
> autohide?
Yes. Open 'ccsm' (compizconfig-settings-manager), browse down to the unity plugin and enable the autohide checkbox.

---

### Post by plun on 2010-12-03
One more time......;)

What is the meaning with glib-mainloop  :confused:

I am building a clean Compiz without the glib-mainloop and it works just fine without the glib-mainloop.

I have no clue what the glib-mainloop is good for ??

For the nerds:
[http://gitweb.compiz.org/?p=users/dbo/compiz-with-glib-mainloop;a=summary](http://gitweb.compiz.org/?p=users/dbo/compiz-with-glib-mainloop;a=summary)

:confused:

---

### Post by ratcheer on 2010-12-03
I don't know whether this is a Unity question or a Natty question, but under Natty/Unity, several apps do not display their menus, while others do. Firefox does have its menus, while Nautilus, Tomboy, and KeePassX do not. In some of these apps, it is impossible to perform certain activities without using the menus.

Is this common? Am I doing something wrong such that the menus are not being displayed?

While this should be clear, I am attaching a couple of screenshots, one showing an app with its menus and another app that does not show its menus.

Tim

---

### Post by jmmL on 2010-12-03
The menu should appear in the top bar. I've attached a screenshot as an example.

---

### Post by MacUntu on 2010-12-03
Are you running Compiz/Unity? The menus are supposed to be in the top panel (and here they are for the programs you mentioned).

Else see: [http://askubuntu.com/questions/6784/is-it-possible-to-make-indicator-appmenu-ignore-a-specific-application](http://askubuntu.com/questions/6784/is-it-possible-to-make-indicator-appmenu-ignore-a-specific-application)

---

### Post by mc4man on 2010-12-03
> Else see: <url>thank you for that - can at least return menus to media players where they belong
Ex. atm,  new launch command for vlc in a .desktop

> Exec=env QT_X11_NO_NATIVE_MENUBAR=1 vlc %U

And audacious
> Exec=env UBUNTU_MENUPROXY=0 audacious2 %U

---

### Post by cariboo on 2010-12-03
> **MacUntu said:**
> Are you running Compiz/Unity? The menus are supposed to be in the top panel (and here they are for the programs you mentioned).

Else see: [http://askubuntu.com/questions/6784/is-it-possible-to-make-indicator-appmenu-ignore-a-specific-application](http://askubuntu.com/questions/6784/is-it-possible-to-make-indicator-appmenu-ignore-a-specific-application)

There isn't a separate Unity for netbooks at the moment, we get the same version as the desktop.

---

### Post by MacUntu on 2010-12-03
> **cariboo907 said:**
> There isn't a separate Unity for netbooks at the moment, we get the same version as the desktop.

I wasn't suggesting there is. :) I just asked, because I have seen programs fail to show a menubar in a classic GNOME session even without having the appmenu applet added to the panel (but they worked in Unity).

---

### Post by ratcheer on 2010-12-03
> **jmmL said:**
> The menu should appear in the top bar. I've attached a screenshot as an example.

Oh! So they are. I never would have thought of that. This is becoming more and more like a Mac.

Thanks.

Tim

---

### Post by VeeDubb on 2010-12-03
> **ratcheer said:**
> Oh! So they are. I never would have thought of that. This is becoming more and more like a Mac.

Thanks.

Tim

Sort of.  I see it as taking the best of mac, win and older versions of gnome.  I was really impressed when I saw unity for netbooks.  My first thought was that it was infinitely better than gnome shell, but simply missing some key functionality to make it useful for the desktop.  Re-tooling it to add the functionality we expect for desktops, and making it a compiz plugin, instead of a standalone shell that conflicts with compiz the way gnome-shell does, was a stroke of genious.

---

### Post by youoh on 2010-12-03
is it possible to assign a key to the Workspace Switcher?

would like to have it like in gnome-shell with the super-key

---

### Post by mc4man on 2010-12-03
> Workspace Switcher?
 it's just expo (super+e

---

### Post by moore.bryan on 2010-12-05
Could someone *please* help explain this to me?

I am compiling/building from source, as per the Ubuntu Wiki directions, because I want to use Unity on my Maverick install; however, even though *everything* builds properly *without a single* error and even though Compiz launches *without a single* error, ccsm shows no available Unity plugin.

Huh?

---

### Post by cariboo on 2010-12-05
Natty uses a compiz version written specifically for Unity. What version of compiz are you using?

compiz version: 1:0.9.2.1+glibmainloop2-0ubuntu4

---

### Post by plun on 2010-12-05
> **moore.bryan said:**
> Could someone *please* help explain this to me?

I am compiling/building from source, as per the Ubuntu Wiki directions, because I want to use Unity on my Maverick install; however, even though *everything* builds properly *without a single* error and even though Compiz launches *without a single* error, ccsm shows no available Unity plugin.

Huh?

Are you starting the new ccsm from the opt-folder ?

I am building with Soreus script without the glib-mainloop and for me the command is /opt/compiz++/bin/ccsm++

In your case probably /opt/unity/bin/ccsm

Just to check the /opt folder.

---

### Post by moore.bryan on 2010-12-05
> **cariboo907 said:**
> Natty uses a compiz version written specifically for Unity. What version of compiz are you using?

compiz version: 1:0.9.2.1+glibmainloop2-0ubuntu4
I used the script in the Unity /tools dir to build/compile Compiz from scratch. Typing *compiz --version* gets me *Compiz 0.9.2.1*.

> **plun said:**
> Are you starting the new ccsm from the opt-folder ?

I am building with Soreus script without the glib-mainloop and for me the command is /opt/compiz++/bin/ccsm++

In your case probably /opt/unity/bin/ccsm

Just to check the /opt folder.
I have the *++* suffixed items in my ~/staging/bin dir, but not in /opt; and, yes, everything's starting from /opt/unity/bin.

Thanks, for the input!

---

### Post by plun on 2010-12-05
> **moore.bryan said:**
> 
I have the *++* suffixed items in my ~/staging/bin dir, but not in /opt; and, yes, everything's starting from /opt/unity/bin.

Thanks, for the input!

Ok... checked the wiki again and for Maverick it points to Unitys source and a build-script inside /tools.

[https://wiki.ubuntu.com/Unity/InstallationGuideFromSource](https://wiki.ubuntu.com/Unity/InstallationGuideFromSource)

Its Moreaus script modified with the glib-mainloop (DBO)... !

Must test it myself...;)

---

### Post by mc4man on 2010-12-06
Whether there will be a configuration tool sometime to selectivly return menus to apps don't know.
In the absence such a tool had previously mentioned using a .desktop(s) to set a env, whether in /usr/share/applications or ~/.local/share/applications.

While .desktops are great for creating specific use versions of a binary and are generally immune to app updates in this case may better to 'adjust' the binary itself. This way it will apply to all possible uses of that binary/app, whether menu, r. click or terminal, ect.

Using a method seen in a smplayer fix seems to work well here.
the 2 previous examples of vlc and audacious, run as 2 commands of 4 & 3 lines respectively.
aud.
```
sudo bash -c "cat > /usr/bin/audacious2.helper" <<EOF
export UBUNTU_MENUPROXY=0 
exec  audacious2.real "\$@"
EOF
```
```
sudo chmod 755 /usr/bin/audacious2.helper
sudo mv /usr/bin/audacious2{,.real}
sudo ln -sf audacious2.helper /usr/bin/audacious2
```

vlc
```
sudo bash -c "cat > /usr/bin/vlc.helper" <<EOF
export QT_X11_NO_NATIVE_MENUBAR=1
exec vlc.real "\$@"
EOF
```
```
sudo chmod 755 /usr/bin/vlc.helper
sudo mv /usr/bin/vlc{,.real}
sudo ln -sf vlc.helper /usr/bin/vlc

```
If the app updates then the 3 line command (actually just the last 2 lines) will restore

---

### Post by plun on 2010-12-09
Well, latest Compiz-code (without the glib-mainloop) and Unity Bzr code works just fine....

[[IMG]http://i.imgur.com/FCCNHs.jpg[/IMG]](http://imgur.com/FCCNH)

Intellihide works just fine.... I also would prefer a auto-hide function !

But... Unity is rather "ugly", It must be possible to make the Launcher including icons smaller... rather "grotesque" for the moment..;)

---

### Post by VMC on 2010-12-09
> **plun said:**
> ...

But... Unity is rather "ugly", It must be possible to make the Launcher including icons smaller... rather "grotesque" for the moment..;)
I asked that question, and it appears the size of the icons is the reason the border is so large. 48x48, making it 32x32 would smear the icons, it was stated.

---

### Post by plun on 2010-12-10
The famous Cube (for me a sphere) seems to be stone-dead with latest code....:-k

---

### Post by mc4man on 2010-12-10
It would seem, (at least here), that the latest unity will not hide the launcher unless a window is occupying it's space. If so and intentional then that is quite unfortunate.

---

### Post by godhika on 2010-12-10
> **mc4man said:**
> It would seem, (at least here), that the latest unity will not hide the launcher unless a window is occupying it's space. If so and intentional then that is quite unfortunate.

I assume you are talking about the autohide functionality. It is indeed intentional

---

### Post by mc4man on 2010-12-10
> It is indeed intentional
Possibly it was the plan overall, hate to think it was just in response to the bugfix it mentions, gaining 54px. in a certain scenario. (though M.S. response seems to indicate planned behavior
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/685861](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/685861)

If 'unity desktop' was actually meant to be used on a real desktop (ext. monitor), then it would seem that an additional option to actually autohide the launcher could be useful.

---

### Post by ratcheer on 2010-12-10
Well, Unity is kaput, on my system anyway. It was great through yesterday, but now I get my wallpaper background and a spinning cursor that never completes whatever it is waiting for. I have tried Ctrl+Alt+F1, then "sudo service gdm restart", but that doesn't help. I'm not sure what else, if anything, to try. I received and installed a new Unity package at 3:15 PM CST, today, and I hoped it would fix the problem, but it didn't.

The Ubuntu Classic Desktop (i.e., regular Gnome), works fine. Except, Visual Effects cannot be enabled.

I don't know if all this is because of the Python changes, or something else. I haven't had any packages removed by aptitude, though. Oddly, this afternoon, new packages of both Python 2.6 and 2.7 were installed, simultaneously.

I'm not complaining, just stating my current status.

Tim

---

### Post by coffeecat on 2010-12-10
> **ratcheer said:**
> Well, Unity is kaput, on my system anyway. It was great through yesterday, but now I get my wallpaper background and a spinning cursor that never completes whatever it is waiting for.

Sounds familiar! Fear not, you are treading where others have gone before. :) Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1641092](http://ubuntuforums.org/showthread.php?t=1641092)

Go to my post at #84 - I think you'll find that the same. There's some discussion going on from that and cariboo907 at #110 is going to put in a bug report. Long story short: log into classic desktop and then back into unity desktop and the spinning cursor will change to an ordinary arrow pointer. Now ctrl-alt-T for a terminal, and:

```
unity &
```... will give you most of Unity back except for an empty upper panel. Subsequent updates have cured the non-starting Unity for me, but the upper panel is still empty.

---

### Post by cecilpierce on 2010-12-10
I like that new auto-hide gizmo's :D  

Before it wouldn't stay long enough to click on what I was looking for !

---

### Post by cariboo on 2010-12-10
I feel like I'm repeating myself here, :) I have the same problem on one system at boot, except all I get is the mouse cursor. What I do is open a terminal using Ctrl-Alt-T, then type:

```
compiz --replace
```

then I move the terminal to desktop 4 and do something else for a few minutes. I can then go back and close the terminal, unity goes away and comes back a few seconds later. Strangely enough, if I close the terminal right after running the above command I immediately go back to a naked desktop. :)

---

### Post by cecilpierce on 2010-12-10
How can I get the calender to display when I click on the time gadget on the top panel ?

All I get is 'Friday, 10 December 2010' and 'Time & Date Settings'.

---

### Post by mc4man on 2010-12-10
> I like that new auto-hide gizmo's
I gather then that will be the general opinion. Though previously as long as the mouse was in the launcher it wouldn't hide.

For curiosity have, atm, returned the  'true' autohide to the current unity (3.2.6), I prefer it that way on a desktop w/ a wide screen monitor.

The calender works (displays) fine here, maybe install gnome-system-tools, (.?) though you won't be able to directly adjust time and date ( that requires auth which the unity 'bar' can't provide.
I'd think that will be addressed at some point in some fashion

---

### Post by MacUntu on 2010-12-10
Spinning cursor is a crash: [https://bugs.launchpad.net/unity/+bug/685418](https://bugs.launchpad.net/unity/+bug/685418)

Restarting GDM works fine here.

---

### Post by kyleabaker on 2010-12-10
> **coffeecat said:**
> Sounds familiar! Fear not, you are treading where others have gone before. :) Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1641092](http://ubuntuforums.org/showthread.php?t=1641092)

Go to my post at #84 - I think you'll find that the same. There's some discussion going on from that and cariboo907 at #110 is going to put in a bug report. Long story short: log into classic desktop and then back into unity desktop and the spinning cursor will change to an ordinary arrow pointer. Now ctrl-alt-T for a terminal, and:

```
unity &
```... will give you most of Unity back except for an empty upper panel. Subsequent updates have cured the non-starting Unity for me, but the upper panel is still empty.

Yep, thats where I'm at. Hopefully I can remember the keyboard shortcuts I need until it gets fixed. :D

---

### Post by ratcheer on 2010-12-11
Thanks, everyone. After this morning's updates, Unity is working again, without intervention. However, as others have said, there are no indicator applets in the right side of the top panel.

Tim

PS - You know, it is very odd to me that, even though I am keeping my system fully updated, usually two or three times daily, I keep encountering new problems on my system that everyone else had a  day or two earlier. I'm just saying.

---

### Post by coffeecat on 2010-12-11
> **ratcheer said:**
> However, as others have said, there are no indicator applets in the right side of the top panel.

Here's something interesting. On my main desktop Natty I've been through the broken Unity with only wallpaper and spinning cursor, then a half-mended Unity with updates, leading to a usable Unity but blank upper panel as ratcheer's screenshot shows. My screenshot of this is the first one below.

On my laptop, by neglecting updates for a couple of days, I managed to skip over whichever update(s) caused this breakage, and when I did update yesterday, Unity remained in one piece. So, this morning, I cloned the root Natty partition on my laptop to a spare partition on my desktop. I'm posting from it now. Screenshot #2 below and, as you see, upper panel OK. Both versions are similarly updated so I'm wondering if the updates that caused all this have changed some configuration somewhere.

To be clear: two installations of Natty on different partitions on the same machine. Both fully updated as of a couple of hours ago. One has a blank top panel; in the other the panel is fine.

Curious.

---

### Post by kyleabaker on 2010-12-11
> **coffeecat said:**
> Here's something interesting. On my main desktop Natty I've been through the broken Unity with only wallpaper and spinning cursor, then a half-mended Unity with updates, leading to a usable Unity but blank upper panel as ratcheer's screenshot shows. My screenshot of this is the first one below.

On my laptop, by neglecting updates for a couple of days, I managed to skip over whichever update(s) caused this breakage, and when I did update yesterday, Unity remained in one piece. So, this morning, I cloned the root Natty partition on my laptop to a spare partition on my desktop. I'm posting from it now. Screenshot #2 below and, as you see, upper panel OK. Both versions are similarly updated so I'm wondering if the updates that caused all this have changed some configuration somewhere.

To be clear: two installations of Natty on different partitions on the same machine. Both fully updated as of a couple of hours ago. One has a blank top panel; in the other the panel is fine.

Curious.

Any chance you can run a diff on the two so we can find out where the problem is? I'm still without icons in the top panel.

---

### Post by coffeecat on 2010-12-11
> **kyleabaker said:**
> Any chance you can run a diff 

Hmmm. That could be fun. I've never used diff before but I get the idea. Where do you think I should start? Parts/whole of /etc? Hidden home stuff?

---

### Post by MacUntu on 2010-12-11
Here too: one system fully up-to-date, everything works fine. The other one is up-to-date too but no indicators. Both using nvidia, both i386, both using the same indicators. 

Tis Unity is teh weeeeeeeeird stuff! :D

---

### Post by cariboo on 2010-12-11
If you are going to try diff, i'd suggest starting on the individual directories in ~/.config

---

### Post by jaco223 on 2010-12-11
> **coffeecat said:**
> Here's something interesting. On my main desktop Natty I've been through the broken Unity with only wallpaper and spinning cursor, then a half-mended Unity with updates, leading to a usable Unity but blank upper panel as ratcheer's screenshot shows. My screenshot of this is the first one below.

On my laptop, by neglecting updates for a couple of days, I managed to skip over whichever update(s) caused this breakage, and when I did update yesterday, Unity remained in one piece. So, this morning, I cloned the root Natty partition on my laptop to a spare partition on my desktop. I'm posting from it now. Screenshot #2 below and, as you see, upper panel OK. Both versions are similarly updated so I'm wondering if the updates that caused all this have changed some configuration somewhere.

To be clear: two installations of Natty on different partitions on the same machine. Both fully updated as of a couple of hours ago. One has a blank top panel; in the other the panel is fine.

Curious.

@coffeecat

is it safe to update at this time? update manager is offering only partial upgrade so
i'm reluctant to do that. i had to wipe my imac today and reinstall everything (painful)
i have a fresh install of alpha1 and am afraid to update i don't want to lose my
panel indicators. should i just wait as everything is running fairly smoothly at the moment?

thanks!

jaco

---

### Post by cariboo on 2010-12-11
@jaco223, If you are still being offered a partial up grade, I'd suggest you try System->Administration->Synaptic Package Manager. Once the application is open, click the status button on the lower left, that won't make what's displayed look so complicated.

Click the reload button in the upper right, once it's finished, click the Mark All Upgrades, then click Apply, this will bring up a windows telling you what will be removed, installed and upgraded.

You shouldn't be presented with a partial upgrade anymore.

---

### Post by coffeecat on 2010-12-12
> **jaco223 said:**
> @coffeecat

is it safe to update at this time? update manager is offering only partial upgrade

I'm no expert, but I think the reason I avoided  the blank panel issue in one installation was because I skipped over whichever update caused a configuration problem (only a theory, this) and did an update after a couple of days' neglect. So I would say it is safe to update now. However, don't use Update Manager. See [here.]("http://ubuntuforums.org/showthread.php?t=1641400") Follow cariboo907's advice. I'm trying both 'sudo apt-get upgrade' and 'sudo aptitude safe-upgrade' at the moment to see what's on offer. The aptitude option seems marginally less risky at the moment for my purposes.

> **cariboo907 said:**
> If you are going to try diff, i'd suggest starting on the individual directories in ~/.config

Thanks. I'll look there. I tried a recursive diff of ~ last evening and quickly realised that was not a good idea. :| But it did throw up something interesting in the two ~/.xsession-errors files. There were some blood-curdling messages about the panel in the system with a blank panel. I'll investigate further and perhaps post back, but I have to go out (reluctantly) to do some shopping soon, so it won't be for some time.

---

### Post by coffeecat on 2010-12-12
> **coffeecat said:**
> There were some blood-curdling messages about the panel in the system with a blank panel. I'll investigate further and perhaps post back

OK, just quickly before braving the crowds. If I 'cat ~/.xsession-errors | grep panel' in my "working" Natty, I get no output. Grepping .xsession-errors in the blank-panel Natty in the same way gives me:

```
** (unity-panel-service:1639): DEBUG: Loading: /usr/lib/indicators/4/libdatetime.so
** (unity-panel-service:1639): DEBUG: Evaluating bitmask for '%l:%M %p'
** (unity-panel-service:1639): DEBUG: Checking against 2 posible times
** (unity-panel-service:1639): DEBUG: Guessing max time width: 62
(unity-panel-service:1639): GLib-GObject-WARNING **: specified instance size for type `DbusmenuGtkClient' is smaller than the parent type's `DbusmenuClient' instance size
(unity-panel-service:1639): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
(unity-panel-service:1639): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
(unity-panel-service:1639): GLib-GObject-WARNING **: invalid (NULL) pointer instance
(unity-panel-service:1639): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
(unity-panel-service:1639): GLib-GObject-WARNING **: cannot register existing type `DbusmenuGtkMenu'
(unity-panel-service:1639): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
(unity-panel-service:1639): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtkmenu_get_client: assertion `DBUSMENU_IS_GTKMENU(menu)' failed
(unity-panel-service:1639): GLib-GObject-CRITICAL **: g_object_set_data: assertion `G_IS_OBJECT (object)' failed
(unity-panel-service:1639): LIBDBUSMENU-GLIB-CRITICAL **: dbusmenu_client_add_type_handler: assertion `DBUSMENU_IS_CLIENT(client)' failed
** (unity-panel-service:1639): DEBUG: Loading: /usr/lib/indicators/4/libappmenu.so
** (unity-panel-service:1639): WARNING **: Unable to find the file menu stock item
** (unity-panel-service:1639): DEBUG: New Desktop Window: 1600024
** (unity-panel-service:1639): DEBUG: Loading: /usr/lib/indicators/4/libsession.so
WARNING: Couldn't load panel from installed services, so trying toload panel from known location: /usr/lib/unity/unity-panel-service
WARNING: Unable to connect to the unity-panel-service Error calling StartServiceByName for com.canonical.Unity.Panel.Service: Timeout was reached
```There seems to be some leads there. I'll have a look when I've finished with Santa, but no doubt someone else will find something while I'm out.

---

### Post by cecilpierce on 2010-12-12
What happen to the desktop cube ?
All I get is slider.

---

### Post by jaco223 on 2010-12-12
> **cariboo907 said:**
> @jaco223, If you are still being offered a partial up grade, I'd suggest you try System->Administration->Synaptic Package Manager. Once the application is open, click the status button on the lower left, that won't make what's displayed look so complicated.

Click the reload button in the upper right, once it's finished, click the Mark All Upgrades, then click Apply, this will bring up a windows telling you what will be removed, installed and upgraded.

You shouldn't be presented with a partial upgrade anymore.

@cariboo

thanks so much for the info, will do as you suggest. i'm a little dense cariboo ...so update all packages with synaptic...then do my upgrade from the terminal? apt-get -f dist-upgrade? coffeecat suggested update manager might not be ideal ..

@coffeecat thanks for the advice am about to follow the link you dropped

keeping my fingers crossed :)

thanks guys!

jaco

---

### Post by MacUntu on 2010-12-12
> **cecilpierce said:**
> What happen to the desktop cube ?
All I get is slider.
Unity depends on "Desktop Wall" which conflicts "Cube", so it's not supposed to work.

PS: Without "Desktop Wall" it doesn't switch workspaces if you click on a running launcher of a program on a different workspace. If "Cube" can do this too, maybe Unity should depend on "Desktop Wall" OR "Cube" - in that case I suggest you file a bug report or use the ayatana mailing list.

---

### Post by jaco223 on 2010-12-12
> **jaco223 said:**
> @cariboo

thanks so much for the info, will do as you suggest. i'm a little dense cariboo ...so update all packages with synaptic...then do my upgrade from the terminal? apt-get -f dist-upgrade? coffeecat suggested update manager might not be ideal ..

@coffeecat thanks for the advice am about to follow the link you dropped

keeping my fingers crossed :)

thanks guys!

jaco

@cariboo

i did as you said....it seems ubuntu want's to downgrade python 2.7 to
to 2.6dev....which will remove my ubuntu tweak. why the downgrade?
am holding off for now .....
thanks
jaco

---

### Post by cariboo on 2010-12-12
> **jaco223 said:**
> @cariboo

i did as you said....it seems ubuntu want's to downgrade python 2.7 to
to 2.6dev....which will remove my ubuntu tweak. why the downgrade?
am holding off for now .....
thanks
jaco

Ubuntu Tweak probably hasn't been updated yet. I was using aptitude safe-upgrade until there weren't any packages held back, then went back to using synaptic..

---

### Post by MacUntu on 2010-12-12
Drag and drop support is near:

[[img]http://i4.ytimg.com/vi/o_xNWqBn5LI/default.jpg[/img]](http://www.youtube.com/watch?v=o_xNWqBn5LI)

---

### Post by kyleabaker on 2010-12-12
> **MacUntu said:**
> Drag and drop support is near:

[[img]http://i4.ytimg.com/vi/o_xNWqBn5LI/default.jpg[/img]](http://www.youtube.com/watch?v=o_xNWqBn5LI)

:guitar:

---

### Post by kyleabaker on 2010-12-12
So the Ubuntu opening the Applications folder is [only temporary]("http://www.ubuntu.com/testing/natty/alpha1"), but I'm wondering what the "Application place" feature will look like or if it will just be a new and improved menu system? Any clues?

---

### Post by MacUntu on 2010-12-12
I guess it will be an improved version of Maverick's dash (I guess that's what this overlay is called).

[img]http://farm2.static.flickr.com/1116/5165184298_5ef8890638_z.jpg[/img]

---

### Post by Quackers on 2010-12-12
Very nice :-)

---

### Post by kyleabaker on 2010-12-13
So it looks like we will be getting the initial places view on Thursday (16th) along with several other Unity updates:
[https://launchpad.net/unity/+milestone/3.2.8](https://launchpad.net/unity/+milestone/3.2.8)

...such a long wait, lol.

---

### Post by cariboo on 2010-12-13
didrocks setup a Thursday release schedule during the Maverick testing cycle, it looks like he's sticking to it for Natty too.

---

### Post by mc4man on 2010-12-13
> What happen to the desktop cube ?
All I get is slider.
Apparently this was a change in the last unity version ( 3.2.6

> Unity depends on "Desktop Wall" which conflicts "Cube", so it's not supposed to work

If you had previously enabled the cube then the update would not change that and the cube works quite fine with the current unity and probably with versions to come.
With the cube enabled there would be no viewpoint switcher in the launcher which doesn't matter - it's really just expo and always available with super+e (Edit - actually you can have the 'workspace switcher icon with cube/rotate cube

What currently does happen is with the cube enabled, if you go into ccsm and switch back to desktop wall then you are prevented from re-enabling the cube without disabling the unity plugin. (just tried.


Without knowing all the particulars about this decision, it does seem to be a rather poor choice, as said, the cube works perfectly here as does unity itself. ( I see no need to limit peoples choices in this area and a few others with unity like the intelli-hide or whatever it's called... 

Will certainly file a bug and look into the source to see if this is adjustable.


Edit:
Found [the bug]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/683211") that caused this - such nonsense

---

### Post by cecilpierce on 2010-12-13
I have this problem to with only one Natty out of 4 installed.
The other 3 the cube works fine,
Thanks.

---

### Post by mc4man on 2010-12-13
Any install that used unity 3.2.2 or early AND had the cube enabled will be unaffected by this change unless you disable the unity plugin and then try to enable.

This change, if one wants to revert, can either be done in source or simply by editing a .xml before trying to enable the cube/rotate cube

The file location is /usr/share/compiz/unityshell.xml
Open in a text editor and remove the line in blue (remove the complete line, not just text.
```
	    <requirement>
		<plugin>opengl</plugin>
		[COLOR="Blue"]<plugin>wall</plugin>[/COLOR]
	    </requirement>
```

Save (probably should then restart) and then enable the cube with method of choice - I just do while in unity,(have no choice since I've removed the gnome-panel packages), unity will crash, a Ctrl+Alt+Backspace once or twice squares things up.

---

### Post by zekopeko on 2010-12-13
I want my top panel back :(  

Menu and indicators are missing for me.

---

### Post by MacUntu on 2010-12-13
> **mc4man said:**
> Edit:
Found [the bug]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/683211") that caused this - such nonsense

Thanks, that's my bug report. :P

At that time non of those plugins were enabled after installing Unity, so I requested to at least depend on one of those plugins that made "workspace-follows-focus" work. Didn't knew it works with other plugins too.

Anyways, the development cycle is the right time to find good settings - no need to be afraid about such changes being final. If you feel things could be improved, report bugs or use the appropriate mailing lists.

> **zekopeko said:**
> I want my top panel back :(  

Menu and indicators are missing for me.

I'm still curious why I only see this happen on one of my systems. Although, the "working" panel got stuck today. I clicked on the clock applet and the clock suddenly went from 9:28 to 10:34 (don't use alpha versions on productive systems - I missed an appointment due to that :P).

---

### Post by coffeecat on 2010-12-13
**To those with a blank upper panel in Unity:**

I'm still running my two parallel Natties on the same machine - one with a blank panel, the other with a working panel. Both were fully upgraded within the last couple of hours and the situation is still the same. I'm beginning to doubt whether an update will fix this, but I still don't understand where the breakage is. I've tried creating yet another user account in the "broken" installation but I get a blank panel again. Which makes me think the problem is not in user configuration files so I've abandoned my diff attempts.

The only lead I've got is those lines from ~/.xsession-errors that I posted in post #265. I tried reinstalling all the dbus and unity-related packages - to no effect. If anyone has any other ideas I'd be glad to hear them. I'm ready to abandon the "broken" installation but that hardly helps others with this problem.

---

### Post by jaco223 on 2010-12-13
> **MacUntu said:**
> I guess it will be an improved version of Maverick's dash (I guess that's what this overlay is called).

[IMG]http://farm2.static.flickr.com/1116/5165184298_5ef8890638_z.jpg[/IMG]

that overlay is so much nicer than what natty is offering atm, will we see this kind of overlay as natty moves forward?

jaco

---

### Post by jaco223 on 2010-12-13
> **coffeecat said:**
> **To those with a blank upper panel in Unity:**

I'm still running my two parallel Natties on the same machine - one with a blank panel, the other with a working panel. Both were fully upgraded within the last couple of hours and the situation is still the same. I'm beginning to doubt whether an update will fix this, but I still don't understand where the breakage is. I've tried creating yet another user account in the "broken" installation but I get a blank panel again. Which makes me think the problem is not in user configuration files so I've abandoned my diff attempts.

The only lead I've got is those lines from ~/.xsession-errors that I posted in post #265. I tried reinstalling all the dbus and unity-related packages - to no effect. If anyone has any other ideas I'd be glad to hear them. I'm ready to abandon the "broken" installation but that hardly helps others with this problem.

@coffeecat

thanks for all the info, dang! i want to update/upgrade but don't want to break the panel.
i hope this gets resolved soon as i definitely need an upgrade.

jaco

---

### Post by kyleabaker on 2010-12-13
> **jaco223 said:**
> that overlay is so much nicer than what natty is offering atm, will we see this kind of overlay as natty moves forward?

jaco

Seriously? Just answered this on the previous page. ;)

> **kyleabaker said:**
> So it looks like we will be getting the initial places view on Thursday (16th) along with several other Unity updates:
[https://launchpad.net/unity/+milestone/3.2.8](https://launchpad.net/unity/+milestone/3.2.8)...

---

### Post by coffeecat on 2010-12-13
> **jaco223 said:**
> i want to update/upgrade but don't want to break the panel.
i hope this gets resolved soon as i definitely need an upgrade.

I'm fairly sure, but not 100%, that if you update now you won't get a broken panel. This seems to be associated with updates that came through about 4 or so days ago. See my post in this thread #257. The installation that missed those updates is still OK - updated with ~100MB updates this morning. The broken one was broken some days ago and updates do not mend it.

---

### Post by kyleabaker on 2010-12-13
> **coffeecat said:**
> I'm fairly sure, but not 100%, that if you update now you won't get a broken panel. This seems to be associated with updates that came through about 4 or so days ago. See my post in this thread #257. The installation that missed those updates is still OK - updated with ~100MB updates this morning. The broken one was broken some days ago and updates do not mend it.

I reinstalled since the broken panel wasn't getting any better and the updates worked fine, so that should be over now unless I just got lucky during my updates. :D

---

### Post by coffeecat on 2010-12-13
> **kyleabaker said:**
> I reinstalled since the broken panel wasn't getting any better and the updates worked fine, so that should be over now unless I just got lucky during my updates. :D

Whatever. :) I'm beginning to think the only solution to this blank upper panel problem is to reinstall with the latest daily live. I'm with you there. Normally I hate suggesting a re-install because, theoretically, almost any system should be repairable. But if hunting down the reason for this issue isn't going to help the dev team, then it's probably better to be done with it and get on with a system with a working panel. I'm OK, I can simply abandon the broken install but I'm still curious as to what went wrong.

---

### Post by Harry33 on 2010-12-13
> **coffeecat said:**
> Whatever. :) I'm beginning to think the only solution to this blank upper panel problem is to reinstall with the latest daily live. I'm with you there. Normally I hate suggesting a re-install because, theoretically, almost any system should be repairable. But if hunting down the reason for this issue isn't going to help the dev team, then it's probably better to be done with it and get on with a system with a working panel. I'm OK, I can simply abandon the broken install but I'm still curious as to what went wrong.

Sometimes a buggy update installs some messy lines, that are not reversed or removed later even with a fixed update.
That explains why a setup ones updated with a buggy update still is not working well even if it is updated later.
And a setup with the same newest updates works well, if it had never been updated with a buggy update.

This same thing happened with Natty just a few days ago with a buggy libcanberra update. The only solution was to purge the buggy update and then install the fixed update. See this thread here:
[http://ubuntuforums.org/showthread.php?t=1641092&page=7](http://ubuntuforums.org/showthread.php?t=1641092&page=7)
and then this #61

---

### Post by MacUntu on 2010-12-13
Margaret Thatcher, 1984: "I want my indicators back!"

I don't believe in fixing things with a system reinstallation anymore. I'm a Linux user, dammit! :P

---

### Post by JOHNNYG713 on 2010-12-13
:p[ http://www.webupd8.org/2010/12/get-your-favourite-gnome-panel-applets.html ]("http://www.webupd8.org/2010/12/get-your-favourite-gnome-panel-applets.html")
for natty!

---

### Post by ratcheer on 2010-12-13
This afternoon's batch of updates (but not this morning's) finally fixed my top panel in Unity.

Tim

---

### Post by MacUntu on 2010-12-13
Latest updates got my indicators back. Also my Compiz configuration was reset (plus, the Unity plugin was disabled).

---

### Post by kyleabaker on 2010-12-13
> **MacUntu said:**
> Latest updates got my indicators back. Also my Compiz configuration was reset (plus, the Unity plugin was disabled).

What had you changed that was reset?

---

### Post by MacUntu on 2010-12-13
I always disable the shadow effect, so it's pretty obvious when the configuration changes.

---

### Post by Quackers on 2010-12-13
Yes, the new Unity package disabled my Unity plugin too. It has happened before and I suspect it will again :-)

---

### Post by kyleabaker on 2010-12-13
> **Quackers said:**
> Yes, the new Unity package disabled my Unity plugin too. It has happened before and I suspect it will again :-)

Yea, did mine too. I opened CCSM and enabled it again then restarted and Unity/Compiz appears to load and crash almost immediately. Once I start it with a bash script (compiz &) it works fine. Maybe this will resolve itself in an update, either way..everything seems to be working fine after I manually start compiz.

---

### Post by rajeev1204 on 2010-12-13
Dont know about unity , but the visual effects tab has disappeared from appearances.

---

### Post by kyleabaker on 2010-12-13
> **rajeev1204 said:**
> Dont know about unity , but the visual effects tab has disappeared from appearances.

Good eye! This latest update also fixed the issue where shutdown or restart prompts you about Compiz not responding. Finally a clean shutdown. :D

---

### Post by rajeev1204 on 2010-12-13
> **kyleabaker said:**
> Good eye! This latest update also fixed the issue where shutdown or restart prompts you about Compiz not responding. Finally a clean shutdown. :D


It could mean a few more options are due to appear under appearances, probably unity / classic desktop switcher.A revised visual effects tab i guess.I dont see any other reason why a whole tab would disappear.

---

### Post by Quackers on 2010-12-13
Re-posted from compiz-gnome thread (for your information)

I just noticed wobbly windows had gone so I went to desktop effect in Appearance and it's gone! Vanished!
So I went to ccsm and enabled it - oops, windows borders disappeared, unity disappeared and cairo-dock disappeared.
Hmm so I clicked on the compiz diamond in Applications (from the Ubuntu icon, which fortunately I had already opened) and everything returned! Happy again!

---

### Post by kyleabaker on 2010-12-13
> **rajeev1204 said:**
> It could mean a few more options are due to appear under appearances, probably unity / classic desktop switcher.A revised visual effects tab i guess.I dont see any other reason why a whole tab would disappear.

Hopefully it wasn't just removed to "clean up" the  Appearance menu. Change for the sake of change. :/

> **Quackers said:**
> ...So I went to ccsm and enabled it - oops, windows borders disappeared, unity disappeared and cairo-dock disappeared...

I try not to mess with ccsm unless necessary since enabling/disabling nearly anything crashes Compiz for me.

---

### Post by nm_geo on 2010-12-13
Is this the same version and kernel you have?

```
greg@greg-Latitude-D620:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu natty (development branch)"
greg@greg-Latitude-D620:~$ uname -r
2.6.37-7-generic
greg@greg-Latitude-D620:~$ uname -v
#19-Ubuntu SMP Tue Nov 30 23:46:45 UTC 2010

```

I sure thought I saw another kernel come down the pipe today when updated. 
Unity is just not working here.  The classic gnome panel seems to be stable but is that really testing?

---

### Post by cariboo on 2010-12-13
It looks like you're a couple of kernel versions behind:

```
uname -r
2.6.37-9-generic
```

came in with todays updates.

---

### Post by nm_geo on 2010-12-13
That is what I thought.  Guess I will try again to update..

Hmmmm.. Okay that's why noobs are not used for testing.  I just checked my grub and saw both 
newer kernels.  Then "boink" I remembered my Grub2 is addressed in my Lucid version sda5 partition.. shhh

ok..

```
uname -r
2.6.37-9-generic
 uname -v
#22-Ubuntu SMP Fri Dec 10 10:05:11 UTC 2010
```My testing might go better now    ](*,)

---

### Post by kyleabaker on 2010-12-14
You've proved it, its official! GRUB, E=MC^2...

Graphic Related Updates Blow... and don't reboot most of the time ..and..
Erroneous-code = Massive Chaoes^2... and no more unity

Testing = Someone who can save the world =... [IMG]http://img820.imageshack.us/img820/7002/norris.gif[/IMG]

---

### Post by ratcheer on 2010-12-14
> **ratcheer said:**
> This afternoon's batch of updates (but not this morning's) finally fixed my top panel in Unity.

Tim

This morning's updates blew it (Unity) away, again. I have a plain desktop with wallpaper and a mouse pointer, nothing else. I'll be reading the threads to try to find a workaround.

Tim

---

### Post by coffeecat on 2010-12-14
> **ratcheer said:**
> This morning's updates blew it (Unity) away, again. I have a plain desktop with wallpaper and a mouse pointer, nothing else. I'll be reading the threads to try to find a workaround.

Log out, log in to the classic desktop, log out again and back into Unity. For some weird reason this seems to help for me. At some point you may have to open ccsm in Unity and make sure the Unity plugin as ticked. Although quite how I did that with alt-ctrl-T not working to give you a terminal on the blank desktop, I've now forgotten.

---

### Post by ratcheer on 2010-12-14
> **coffeecat said:**
> Log out, log in to the classic desktop, log out again and back into Unity. For some weird reason this seems to help for me. At some point you may have to open ccsm in Unity and make sure the Unity plugin as ticked. Although quite how I did that with alt-ctrl-T not working to give you a terminal on the blank desktop, I've now forgotten.

Logging in to Classic, logging out, and logging in again to Unity DE did not work, for me. I still got a completely empty desktop with wallpaper and mouse pointer, only.

ccsm is not installed on my system. I do see how to install it, but it seems like a big pain.

Thank you,
Tim

---

### Post by afv on 2010-12-14
> **ratcheer said:**
> Logging in to Classic, logging out, and logging in again to Unity DE did not work, for me. I still got a completely empty desktop with wallpaper and mouse pointer, only.

ccsm is not installed on my system. I do see how to install it, but it seems like a big pain.

Thank you,
Tim

*apt-get install compizconfig-settings-manager* ?

---

### Post by zika on 2010-12-14
> **afv said:**
> *apt-get install compizconfig-settings-manager* ?sudo apt-get install compizconfig-settings-manager... ?

---

### Post by Quackers on 2010-12-14
Available from Synaptic.

---

### Post by ratcheer on 2010-12-14
> **afv said:**
> *apt-get install compizconfig-settings-manager* ?

Sorry, I didn't mean a pain to install it, I meant that I shouldn't be forced to use something like that. Unity has been working without it, I shouldn't need it. I am a minimalist of the KISS persuasion.

Thanks, Tim

---

### Post by mc4man on 2010-12-14
> **MacUntu said:**
> Thanks, that's my bug report. :P

Wasn't directed at the report, just the idea of using "required" to set an option that has a viable alt.

I'm sure this will be adjusted (tested setting the requirement as one or the other, similar to how packages do the same and woked fine.

(Seeing how much work/fixes is being done to unity/compiz in such a short time it's certainly understandable that the fix of the bug didn't account for all possibilities.

> **ratcheer said:**
> Sorry, I didn't mean a pain to install it, I meant that I shouldn't be forced to use something like that. Unity has been working without it, I shouldn't need it. I am a minimalist of the KISS persuasion.

Thanks, Tim
 would think that is the idea, but..
ccsm does have value other that effects, sometimes it's useful to make display related setting's or disable some plugins or settings that may be default enabled.
There is also the possibility that an update to compiz could unset previous plugins/settings, some you may need or have been taking advantage of.

---

### Post by ratcheer on 2010-12-14
> **mc4man said:**
> 


 would think that is the idea, but..
ccsm does have value other that effects, sometimes it's useful to make display related setting's or disable some plugins or settings that may be default enabled.
There is also the possibility that an update to compiz could unset previous plugins/settings, some you may need or have been taking advantage of.

Ok. Then, how do I run ccsm in Unity if I can't get into Unity?

Thanks,
Tim

---

### Post by ratcheer on 2010-12-14
Never mind. I ran ccsm under the Classic DE and checked the Unity plugin. Then I logged out of Classic and back in to Unity, and Unity is now working just fine.

I apologize. I suppose I am the one being a pain.

Tim

---

### Post by coffeecat on 2010-12-14
No, I think Unity is the one going through a painful phase. I've now got unresponsive menus.

This is much more "fun" than I remember Maverick being at this stage of the game.

---

### Post by cariboo on 2010-12-14
Personally, i think ccsm should be installed by default, at least until things get a little more mature.

---

### Post by mc4man on 2010-12-14
> how do I run ccsm in Unity if I can't get into Unity?

While i see you're squared away, keep in mind for future that even if unity crashes you usually can  open a working terminal or use any desktop shortcuts, ect.

(while not quite sure of the difference other than the obvious, you can log in to unity thru either the Ubuntu Desktop or Classic Desktop option.

---

### Post by ratcheer on 2010-12-14
> **ratcheer said:**
> Never mind. I ran ccsm under the Classic DE and checked the Unity plugin. Then I logged out of Classic and back in to Unity, and Unity is now working just fine.



I guess I spoke too soon. I went off for about 30 minutes to do some housework. When I came back, Unity was frozen solid. All menus and icons were unresponsive, and I couldn't even type into the terminal window I had left open. I had to reset the PC to reboot.

Tim

---

### Post by mc4man on 2010-12-14
> I had to reset the PC to reboot.
While there are various ways you might consider enabling Ctrl+Alt+Backspace for ease of logging out.

Also what's useful atm is to have access to gnome-control-center. It can be added to the launcher and or a desktop shortcut in case the launcher is unavailable.

You may find that atm unity is more stable for you if you log into unity thru the Classic option, (edit - or is that what's giving you trouble?), though I'd log in thru the Desktop Edition option and check thru your ccsm options there.
(if unity crashes then just do a log out when done in ccsm

---

### Post by nm_geo on 2010-12-14
> **mc4man said:**
> While there are various ways you might consider enabling Ctrl+Alt+Backspace for ease of logging out.
 
I like that one going to try it out. I have just about worn my power off/on button out on the unity freezes. "Orderly shutdown" a new and better concept. Of course, I should stop messin' with all the options in the ccsm.

---

### Post by cariboo on 2010-12-14
Unless your whole system is locked up you can still use the console to shut down, and if you have another system on your network, you can ssh in and shut the system down without having to use the power button.

---

### Post by nm_geo on 2010-12-14
> **cariboo907 said:**
> Unless your whole system is locked up you can still use the console to shut down, and if you have another system on your network, you can ssh in and shut the system down without having to use the power button.
 
This is the only linux box on my home network and there have been times I could not open anything at all. I will say the freezes are getting fewer and fewer after finding and using the errr... newer kernels.. LOL 
 
It seems I was at least a few weeks behind the curve.;)

---

### Post by cariboo on 2010-12-14
<offtopic>

[Putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/") works great if you need to ssh into your Ubuntu system from Windows.

</offtopic>

---

### Post by nm_geo on 2010-12-14
Thanks I will look into it.

---

### Post by jmmL on 2010-12-14
> **nm_geo said:**
> This is the only linux box on my home network and there have been times I could not open anything at all. I will say the freezes are getting fewer and fewer after finding and using the errr... newer kernels.. LOL 
 
It seems I was at least a few weeks behind the curve.;)

In addition to SSH, you should be able to access a TTS (console) using the ctrl+alt+f1 shortcut. There you can log-in, update / shutdown / whatever.

---

### Post by Quackers on 2010-12-14
And there's always holding down ctrl + alt + Sys Rq and then R E I S U B one at a time. Much more civilised reboot for your pc :-)

---

### Post by nm_geo on 2010-12-14
Thanks for all your information. Somehow, someway I have even locked down my keyboard a few times and it appeared I had one option at the time to power down.  I know Linux likes to close everything orderly and then power down, and I really like to try new things thus Natty..;)

Well I just installed PuTTY on the home desktop (XP Home) and added a few ssh packets to my laptop and did an orderly shutdown -h -P now .. and guess what IT WORKED... most excellent..  Oh yeah, it was not a single line command but a normal terminal..

  [http://www.chiark.greenend.org.uk/~sgtatham/putty/]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/")

---

### Post by matt_symes on 2010-12-14
> And there's always holding down ctrl + alt + Sys Rq and then R E I S U B one at a time. Much more civilised reboot for your pcOr if you just want to shut down (no reboot) same as above but...

R E I S U O

BTW: On my laptop i just have to press Alt Gr and Sys Rq. That is the right hand Alt key next to the space bar (Alt Gr). One less key to press. Does this work on others?

---

### Post by nm_geo on 2010-12-14
> **matt_symes said:**
> Or if you just want to shut down (no reboot) same as above but...

R E I S U O

BTW: On my laptop i just have to press Alt Gr and Sys Rq. That is the right hand Alt key next to the space bar (Alt Gr). One less key to press. Does this work on others?

My Dell D620 works just like yours Matt. I will obviously try that first before the PuTTY ssh.. Maybe not .. :D

---

### Post by Quackers on 2010-12-14
> **matt_symes said:**
> Or if you just want to shut down (no reboot) same as above but...

R E I S U O

BTW: On my laptop i just have to press Alt Gr and Sys Rq. That is the right hand Alt key next to the space bar (Alt Gr). One less key to press. Does this work on others?

Yes :-) Altr Gr + Sys Rq does the same! That's one finger less I need :-)

---

### Post by QQi on 2010-12-15
need option click minimize to unity by click on icon(1 window) 

not need to click on (-) on title bar

---

### Post by mc4man on 2010-12-15
The latest update to compiz should resolve compiz updates  from preventing unity from starting. (spinning cursor
Though it will require probably opening the unity plugin once more to re-enable the autohide if desired (intelli-hide version, a 'true' autohide option is under consideration for a later date, though can be enabled in source.

If using the cube than an edit to the .xml is again nessasary, (and will be each time compiz updates till that 'required' is redone, if it is.

---

### Post by kyleabaker on 2010-12-15
Is it just on my installation or is the Unity panel not hiding for the "Appearance Preferences" window? It seems to intellihide as expected for all other windows.

---

### Post by godhika on 2010-12-15
> **kyleabaker said:**
> Is it just on my installation or is the Unity panel not hiding for the "Appearance Preferences" window? It seems to intellihide as expected for all other windows.

Didn't realize it til now but I see the same behavior over here. Just saw Jason Smith added fixes for the intellihide behavior to Unitys trunk. So maybe we see this one fixed with tomorrows update.

---

### Post by kyleabaker on 2010-12-15
In case its not, I reported it a little while ago here:
[https://bugs.launchpad.net/unity/+bug/690918](https://bugs.launchpad.net/unity/+bug/690918)

---

### Post by plun on 2010-12-17
Well.... it looks like a complete mess for the moment.

Soreau fixed the script for building Compiz but Unity seems to be complete broken.....

```
[ 25%] Generating unity-place-activation.c, unity-place-browser.c, unity-place.c, unity-io.c, unity-appinfo-manager.c, perf-logger.c, unity.vapi, unity.h, unity_internal.h
warning: D-Bus GLib is deprecated, use GDBus
/home/plun/unity/libunity/unity-io.vala:49.48-49.54: error: Argument 2: Cannot convert from `GLib.realloc' to `size_t'
    var output = new MemoryOutputStream (null, realloc, null);
                                               ^^^^^^^
/home/plun/unity/libunity/unity-io.vala:58.5-58.30: error: Assignment: Cannot convert from `void*' to `uint8[]'
    data = output.steal_data();
    ^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/plun/unity/libunity/unity-io.vala:50.5-52.56: warning: unhandled error `GLib.Error'
/home/plun/unity/libunity/unity-io.vala:56.5-56.23: warning: unhandled error `GLib.Error'
    output.close (null);
    ^^^^^^^^^^^^^^^^^^^
Compilation failed: 2 error(s), 3 warning(s)
make[2]: *** [libunity/unity-place-activation.c] Error 1
make[1]: *** [libunity/CMakeFiles/unity.dir/all] Error 2
make: *** [all] Error 2

```

A mess... IMHO... but it just Alpha 1....;)

---

### Post by mc4man on 2010-12-17
I see packages for 3.2.8, though haven't tried as of yet
[https://launchpad.net/ubuntu/+source/unity/3.2.8-0ubuntu1/+build/2101946](https://launchpad.net/ubuntu/+source/unity/3.2.8-0ubuntu1/+build/2101946)

---

### Post by plun on 2010-12-17
> **mc4man said:**
> I see packages for 3.2.8, though haven't tried as of yet
[https://launchpad.net/ubuntu/+source/unity/3.2.8-0ubuntu1/+build/2101946](https://launchpad.net/ubuntu/+source/unity/3.2.8-0ubuntu1/+build/2101946)

Package is built and available at least from "main".... testing;)

---

### Post by mc4man on 2010-12-17
Will have to give it ( an update), a try - later would like to try  a re-build if 'autohide' is still only available in 'intelli-hide' mode. (most likely, any consideration of a true 'autohide', if any, may come later.

Though seem to be missing 1 build-dep atm, libdee-dev (>= 0.5.0)

Edit: unity 3.2.8 up and running, some nice additions, though initial window placement with unity in the intelli-hide mode is still not correct with some apps, better when autohide is disabled as far as that goes.

(found likely area to re-enable a true-hide mode, libdee-dev ( 0.5.2 ) is now available
edit: - no problem enabling a true-hide mode though as the launcher becomes more interesting may be inclined to keep visible, or may not. Could see using intelli-hide on one machine and true-hide on another.
At the end of the day  having a choice would be good.

---

### Post by plun on 2010-12-17
New Compiz package available and Unity works again.....

[https://lists.ubuntu.com/archives/natty-changes/2010-December/004005.html](https://lists.ubuntu.com/archives/natty-changes/2010-December/004005.html)

---

### Post by keeperofdakeys on 2010-12-29
I'm trying to compile unity on 10.10, but I seem to get the same error as [this](http://ubuntuforums.org/showpost.php?p=10249844&postcount=339) post. Is there something I'm doing wrong, or do I need to use the latest beta of Ubuntu?

I'm following the instructions from [here](https://wiki.ubuntu.com/Unity/InstallationGuideFromSource).

---

### Post by cecilpierce on 2010-12-29
You should just try the daily live 11.04 version of Unity

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by Amaranth on 2010-12-29
I imagine the vapi for glib/gio has changed between 10.10 and natty and vala is very strict about types, even if C itself isn't.

---

### Post by plun on 2010-12-29
> **Amaranth said:**
> I imagine the vapi for glib/gio has changed between 10.10 and natty and vala is very strict about types, even if C itself isn't.

Hello !

Can you tell us what the purpose is with the Glib-mainloop and why this isn't merged with Compiz-core ?

It feels faster for me but I am unsure....  I have one another clean Compiz install with Soreaus script to compare with.

Bzr is broken for the monent so I cannot build the Unity-plugin.

---

### Post by Amaranth on 2010-12-29
The glib mainloop is how glib processes events and calls callbacks for registered signals. The reason the glib-mainloop branch of compiz isn't merged in to master is because it still has issues like odd signal-related crashes and causing at least 60 wakeups per second due to inefficient glib timers.

This is the branch we're using in Ubuntu natty packages though and I imagine once the issues get sorted out it will be merged in to master.

The only way it would feel faster is if there was an issue with our previous timer setup causing it to miss frames. Otherwise we still just plug things in to the mainloop to get called and the rest of compiz does event handling like it always has.

---

### Post by plun on 2010-12-29
> **Amaranth said:**
> The glib mainloop is how glib processes events and calls callbacks for registered signals. The reason the glib-mainloop branch of compiz isn't merged in to master is because it still has issues like odd signal-related crashes and causing at least 60 wakeups per second due to inefficient glib timers.

This is the branch we're using in Ubuntu natty packages though and I imagine once the issues get sorted out it will be merged in to master.

The only way it would feel faster is if there was an issue with our previous timer setup causing it to miss frames. Otherwise we still just plug things in to the mainloop to get called and the rest of compiz does event handling like it always has.

OK, Thank you Amaranth !!!

Well, we have seen some questions about this already and Intels PowerTop.

Can you describe howto change Soreaus script to also include the Glib-Mainloop...  ?

[http://gitweb.compiz.org/?p=users/soreau/scripts;a=summary](http://gitweb.compiz.org/?p=users/soreau/scripts;a=summary)

and I don't know where to ask.....

---

### Post by Amaranth on 2010-12-29
I hacked my way through that script but I didn't see any easy way to change where it pulls compiz from. I'm probably overlooking something but I think it would be easier to see if you could use the natty packages instead.

Actually, you'd have to patch compiz on top of the changes made in that branch in order to get unity to work correctly anyway so I would say give up on building from source for now.

---

### Post by plun on 2010-12-29
> **Amaranth said:**
> I hacked my way through that script but I didn't see any easy way to change where it pulls compiz from. I'm probably overlooking something but I think it would be easier to see if you could use the natty packages instead.

Actually, you'd have to patch compiz on top of the changes made in that branch in order to get unity to work correctly anyway so I would say give up on building from source for now.

Yup, the script is rather complicated, at least for me...;)

Unity build is also broken for me because of a strange bzr trouble
[https://bugs.launchpad.net/ubuntu/+source/bzr/+bug/695540](https://bugs.launchpad.net/ubuntu/+source/bzr/+bug/695540)

:confused::confused:

---

### Post by mc4man on 2010-12-29
The 'main' bzr bug is here
[https://bugs.launchpad.net/bzr/+bug/693880](https://bugs.launchpad.net/bzr/+bug/693880)

atm the best way is to co with python 2.6 though there haven't been to many rev's to unity as of late.
(or take the current unity source and apply the .diff's and see how things work or don't

---

### Post by Starks on 2010-12-30
I have an i945gm (with partial fragment shader and occlusion enabled) and Unity/Compiz is now crashing within 5 seconds of loading on a fresh install.

I'm sticking with the panel until Unity sucks less and has a legit application menu.

---

### Post by jerrylamos on 2010-12-30
> **Starks said:**
> I have an i945gm (with partial fragment shader and occlusion enabled) and Unity/Compiz is now crashing within 5 seconds of loading on a fresh install.

I'm sticking with the panel until Unity sucks less and has a legit application menu.

Starks, do you or anyone know where Unity is going?  The reason I run Ubuntu is to get to my applications.  Whatever desktop gets me to my applications fastest with the least keystrokes, least mouse clicks, and least windows is the desktop I will use the most.

Right now I'm using Natty "classic", Lubuntu, and Tiny Core.  "classic" I'm most used to and has the most function.  Lubuntu uses LXDE & Chromium which I find a bit awkward.  Perhaps I'm not used to yet.  Tiny Core is a "build it yourself linux" and if all I want to do is access Internet Tiny Core boots faster and runs faster and uses a custom version of SwiftFox which I like.

Unity will run on one of my four test systems - crashes on the other three, launchpad bugs written - I'll give Unity a try if I have a clue what to do with it.  Can I get faster and easier to Internet, Picasa, Write, Skype, spreadsheet, local network printer, local network file sharing, Ubuntu file & folder management, ... ?

Jerry

---

### Post by Starks on 2010-12-30
I have no idea where Unity is going. Likewise, I'm baffled as to why Zeitgeist hasn't been included yet.

The panel is still vastly superior in every way save for perhaps desktop real estate efficiency.

---

### Post by ELD on 2011-01-02
Okay so currently the only way i can do anything is the classic desktop.

Unity doesn't seem to load up, it just brings me to a blank screen with the background.

On ATI hardware with proprietary drivers.

---

### Post by cariboo on 2011-01-02
As usual with every testing version, you have to wait for AMD/ATI to get all their ducks in a row. :)

---

### Post by ELD on 2011-01-02
Ah so it is because of the proprietary drivers then. As the open source drivers didn't load up anything either so for now i am completely stuck?

---

### Post by Harry33 on 2011-01-02
I wouldn't say completely stuck.
The gnome-classic works very well atm.
For unity, we just have to wait.
But then again, the fun is where the alfa-versions are.
This is testing, breakages are expected, some of us are even waiting for them.

And yet, gnome-shell is not ready either.
We do not even get to see it officially in Natty.
I am therefore thankful for the ricotz PPA.

---

### Post by coffeecat on 2011-01-02
> **cariboo907 said:**
> As usual with every testing version, you have to wait for AMD/ATI to get all their ducks in a row. :)

Or be lucky enough to have an ATI card (Radeon HD4350 in my case) that works well with the open source driver. Posting from Unity desktop in Natty Alpha using said ATI card. :smug_look:

:wink:

---

### Post by andrek on 2011-01-02
I can also confirm that Unity works well on open-source ATi drivers (ATi Mobility 4570 @ Dell Studio 1555) but doesn't not even start on the proprietary ones.

---

### Post by anders_c_ on 2011-01-02
Using a Radeon HD 5850 with xorg-edgers ppa.
Unity crashes when i enable/disable plugins in ccsm and when i alt-tab. Don't know if its the drivers or Unity though...everything else works fine. Without edgers ppa it doesn't start at all.

Edit: proprietary won't work at all.

---

### Post by jerrylamos on 2011-01-02
> **coffeecat said:**
> Or be lucky enough to have an ATI card (Radeon HD4350 in my case) that works well with the open source driver. Posting from Unity desktop in Natty Alpha using said ATI card. :smug_look:

:wink:

Alpha 1 "Unity" works with this ati radeon xpress 200.  That's one of my four test pc's.  With the ati radeon mobility 7500, "classic" can be made to work by doing a bunch of acrobatics.  "Unity" is out of sight.  Two other pc's have intel integrated video graphics so they will never run "Unity" no matter how useful and capable those pc's are.

So "Unity" can run on one of my four pc's.  Puzzles me that Ubuntu Natty Alpha 1 boots assuming that "Unity" will run while I'm getting a 75% failure rate for me at this level of development.

Now on the one pc that will run "Unity" I don't because with my level of un-familiarity and this level of development it takes more keystrokes and more screens to use my applications than gnome.  ?  That for the "default" desktop?

Oh, well, fun chasing bugs anyway.  Jerry

---

### Post by tock on 2011-01-13
I just got a new netbook and couldn't wait to push windows over to make room for Ubuntu.  Went to the Ubuntu site and found the install for netbooks.  Installed and now I get something I don't recognise at all.  Usability is minimal at best.  It looks to be designed for tablets not a netbook.  I've searched but have been unable to find anything on network sharing.  Is that possible with this version?  Also, How to I customize it?  The only thing I've been able to change so far is the icons on the side bar.  Can I not have icons on the desktop anymore?  How about the area that opens when clicking on the Ubuntu symbol, can anything be added or changed there?  If this is in beta why are they pushing it as a finished product for the netbook users?   What's funny is there is NO documentation on the Ubuntu netbook site except for the "features" section..  I guess this is Ubuntu wishing me a Happy New Year with a swift kick in the ....  Well anyways, Hope everyone's having a great year so far!:D

---

### Post by tock on 2011-01-13
I just got a new netbook and couldn't wait to push windows over to make room for Ubuntu.  Went to the Ubuntu site and found the install for netbooks.  Installed and now I get something I don't recognise at all.  Usability is minimal at best.  It looks to be designed for tablets not a netbook.  I've searched but have been unable to find anything on network sharing.  Is that possible with this version?  Also, How to I customize it?  The only thing I've been able to change so far is the icons on the side bar.  Can I not have icons on the desktop anymore?  How about the area that opens when clicking on the Ubuntu symbol, can anything be added or changed there?  If this is in beta why are they pushing it as a finished product for the netbook users?   What's funny is there is NO documentation on the Ubuntu netbook site except for the "features" section..  I guess this is Ubuntu wishing me a Happy New Year with a swift kick in the ....  Well anyways, Hope everyone's having a great year so far!:D

---

### Post by andrek on 2011-01-13
When logging in, at the bottom panel, set Session to "Classic Ubuntu Session" *(or Classic Gnome Session, don't remember that)*.

---

### Post by cariboo on 2011-01-13
> **tock said:**
> I just got a new netbook and couldn't wait to push windows over to make room for Ubuntu.  Went to the Ubuntu site and found the install for netbooks.  Installed and now I get something I don't recognise at all.  Usability is minimal at best.  It looks to be designed for tablets not a netbook.  I've searched but have been unable to find anything on network sharing.  Is that possible with this version?  Also, How to I customize it?  The only thing I've been able to change so far is the icons on the side bar.  Can I not have icons on the desktop anymore?  How about the area that opens when clicking on the Ubuntu symbol, can anything be added or changed there?  If this is in beta why are they pushing it as a finished product for the netbook users?   What's funny is there is NO documentation on the Ubuntu netbook site except for the "features" section..  I guess this is Ubuntu wishing me a Happy New Year with a swift kick in the ....  Well anyways, Hope everyone's having a great year so far!:D

It sounds like you installed the Maverick version of Unity, there are quite a few problems with it, I would suggest you use the gnome-desktop, if you want o keep the version you have now. The new version of Unity, to be released in April, is quite a bit different from the version you are using now, most of your complaints have been resolved.

If you are willing to test the new version and report bugs, the daily iso is available [here]("http://cdimage.ubuntu.com/daily-live/current/"). One thing to note is that there isn't a separate netbook version anymore.

---

### Post by tock on 2011-01-13
This is the version I installed:  [http://www.ubuntu.com/netbook](http://www.ubuntu.com/netbook)

---

### Post by tock on 2011-01-13
session options are Recovery,Ubuntu Desktop Edition,Ubuntu Desktop Edition(safe mode),Ubuntu Netbook Edition, and User Defined.  Clicking on Desktop Edition got me where I want to be.  Thank You for your help!!

---

### Post by jennybrew on 2011-01-13
Hopefully Im in the right thread here ..it seems to drift a little.
The issue I want to address is Firefox integration with Unity.
Specifically will it ever happen. 
In particular the global menu looks, and is, a real mess and we have Firefox showing its header as usual and this is then repeated on the top panel...ugh!
Is it fixable or alternatively are there plans to fix it?
Keep smiling :)

---

### Post by kyleabaker on 2011-01-13
> **jennybrew said:**
> Hopefully Im in the right thread here ..it seems to drift a little.
The issue I want to address is Firefox integration with Unity.
Specifically will it ever happen. 
In particular the global menu looks, and is, a real mess and we have Firefox showing its header as usual and this is then repeated on the top panel...ugh!
Is it fixable or alternatively are there plans to fix it?
Keep smiling :)

You should probably direct Firefox integration [here]("http://ubuntuforums.org/showthread.php?t=1666311"). The duplicate headers (I'm assuming you mean the top panel title and window title bar) will be fixed eventually for Unity.

---

### Post by cariboo on 2011-01-13
> **jennybrew said:**
> Hopefully Im in the right thread here ..it seems to drift a little.
The issue I want to address is Firefox integration with Unity.
Specifically will it ever happen. 
In particular the global menu looks, and is, a real mess and we have Firefox showing its header as usual and this is then repeated on the top panel...ugh!
Is it fixable or alternatively are there plans to fix it?
Keep smiling :)

See the thread [here]("http://ubuntuforums.org/showthread.php?t=1666311")

---

### Post by VeeDubb on 2011-01-14
> **cariboo907 said:**
> See the thread [here]("http://http://ubuntuforums.org/showthread.php?t=1666311")

Forum staff posting a bad link?  lol

Try [this]("http://ubuntuforums.org/showthread.php?t=1666311")

---

### Post by zika on 2011-01-14
> **VeeDubb said:**
> Forum staff posting a bad link?  lolWhy not. We're all humans, last time I've checked... lol...

---

### Post by cariboo on 2011-01-14
That's what I get for not proofreading the post. :)

---

### Post by dext on 2011-01-14
**2D Unity** [http://www.phoronix.com/scan.php?page=news_item&px=OTAxMg](http://www.phoronix.com/scan.php?page=news_item&px=OTAxMg)

---

### Post by jerrylamos on 2011-01-14
> **dext said:**
> **2D Unity** [http://www.phoronix.com/scan.php?page=news_item&px=OTAxMg](http://www.phoronix.com/scan.php?page=news_item&px=OTAxMg)
Verrry interesting!  I've four test pc's.  Two don't have hardware for 3D acceleration and so run classic.  I'd like to try Unity 2D on them with autohide.

3rd pc, IBM Thinkpad T40 with ati radeon mobility 7500 crashes with Unity, can be made to run classic with a bunch of command line stuff.  Forget Unity even though the hardware should be capable.  Feels like an Alpha bug.  Not much action on the launchpad bug.

4th pc, will run Unity or Classic for about 5 to 10 minutes before the desktop disappears.  Compiz hang.  Launchpad bug entered.  With login option classic "no effects" runs fine.

Jerry

---

### Post by dext on 2011-01-14
> **jerrylamos said:**
> Verrry interesting!  I've four test pc's.  Two don't have hardware for 3D acceleration and so run classic.  I'd like to try Unity 2D on them with autohide.

3rd pc, IBM Thinkpad T40 with ati radeon mobility 7500 crashes with Unity, can be made to run classic with a bunch of command line stuff.  Forget Unity even though the hardware should be capable.  Feels like an Alpha bug.  Not much action on the launchpad bug.

4th pc, will run Unity or Classic for about 5 to 10 minutes before the desktop disappears.  Compiz hang.  Launchpad bug entered.  With login option classic "no effects" runs fine.

Jerry

you might wanna take a look at this, seems there's a lot of compiz bugs fixed [http://smspillaz.wordpress.com/2011/01/13/the-super-new-compiz-debugging-tool/](http://smspillaz.wordpress.com/2011/01/13/the-super-new-compiz-debugging-tool/) which has a lot to do with Unity probably Crashing

---

### Post by go7Ul1ai on 2011-01-14
The new unity updates are cool, it's looking slicker and slicker!

[IMG]http://i.imgur.com/vP7gzl.jpg[/IMG]

---

### Post by lidex on 2011-01-15
> **jerrylamos said:**
> Verrry interesting!  I've four test pc's.  Two don't have hardware for 3D acceleration and so run classic.  I'd like to try Unity 2D on them with autohide.

3rd pc, IBM Thinkpad T40 with ati radeon mobility 7500 crashes with Unity, can be made to run classic with a bunch of command line stuff.  Forget Unity even though the hardware should be capable.  Feels like an Alpha bug.  Not much action on the launchpad bug.

4th pc, will run Unity or Classic for about 5 to 10 minutes before the desktop disappears.  Compiz hang.  Launchpad bug entered.  With login option classic "no effects" runs fine.

Jerry

More on 2D plus PPA for install info. Looks like this version has Dash:
[http://www.webupd8.org/2011/01/unity-2d-qt-now-available-in-ppa-for.html](http://www.webupd8.org/2011/01/unity-2d-qt-now-available-in-ppa-for.html)

---

### Post by mozgu on 2011-01-15
Hi,

how to disable animation of autohide launcher? I don't see this option in ccsm... Is there any way?

---

### Post by mozgu on 2011-01-15
Hi,

how to disable animation of autohide launcher? I don't see this option in ccsm... Is there any way?

---

### Post by mozgu on 2011-01-15
Hi,

how to disable animation of autohide launcher? I don't see this option in ccsm... Is there any way?

---

### Post by mozgu on 2011-01-15
Hi,

how to disable animation of autohide launcher? I don't see this option in ccsm... Is there any way?

---

### Post by mozgu on 2011-01-15
Hi,

how to disable animation of autohide launcher? I don't see this option in ccsm... Is there any way?

---

### Post by mozgu on 2011-01-15
Hi,

how to disable animation of autohide launcher? I don't see this option in ccsm... Is there any way?

---

### Post by terry_gardener on 2011-01-15
> **mozgu said:**
> Hi,

how to disable animation of autohide launcher? I don't see this option in ccsm... Is there any way?

in ccsm goto the unity plugin  and then the experimental tab, should find what you want in there.

---

### Post by terry_gardener on 2011-01-15
> **mozgu said:**
> Hi,

how to disable animation of autohide launcher? I don't see this option in ccsm... Is there any way?

in ccsm goto the unity plugin  and then the experimental tab, should find what you want in there.

---

### Post by mozgu on 2011-01-15
> **terry_gardener said:**
> in ccsm goto the unity plugin  and then the experimental tab, should find what you want in there.

I know, but I mean something else. I mean the pop-up animation of the bar.

---

### Post by mozgu on 2011-01-15
> **terry_gardener said:**
> in ccsm goto the unity plugin  and then the experimental tab, should find what you want in there.

I know, but I mean something else. I mean the pop-up animation of the bar.

---

### Post by mozgu on 2011-01-15
> **terry_gardener said:**
> in ccsm goto the unity plugin  and then the experimental tab, should find what you want in there.

I know, but I mean something else. I mean the pop-up animation of the bar.

---

### Post by mozgu on 2011-01-15
> **terry_gardener said:**
> in ccsm goto the unity plugin  and then the experimental tab, should find what you want in there.

I know, but I mean something else. I mean the pop-up animation of the bar.

---

### Post by mozgu on 2011-01-15
> **terry_gardener said:**
> in ccsm goto the unity plugin  and then the experimental tab, should find what you want in there.

I know, but I mean something else. I mean the pop-up animation of the bar.

---

### Post by mozgu on 2011-01-15
> **terry_gardener said:**
> in ccsm goto the unity plugin  and then the experimental tab, should find what you want in there.

I know, but I mean something else. I mean the pop-up animation of the bar.

---

### Post by mozgu on 2011-01-15
> **terry_gardener said:**
> in ccsm goto the unity plugin  and then the experimental tab, should find what you want in there.

I know, but I mean something else. I mean the pop-up animation of the bar.

---

### Post by mozgu on 2011-01-15
> **terry_gardener said:**
> in ccsm goto the unity plugin  and then the experimental tab, should find what you want in there.

I know, but I mean something else. I mean the pop-up animation of the bar.

---

### Post by ManasT on 2011-02-12
Just started using Unity now in Natty. I have got one question:

I accidentally clicked 'Ignore Future Crashes' when compiz crashed inside Unity. Now I do not get any option to restart compiz when it crashes and all I am left with is the open window (no panel, no launcher) nothing works. How do I get the option to restart compiz again ?

---

### Post by PaulW2U on 2011-02-13
> **ManasT said:**
> I accidentally clicked 'Ignore Future Crashes' when compiz crashed inside Unity. Now I do not get any option to restart compiz when it crashes and all I am left with is the open window (no panel, no launcher) nothing works.
I think I may have done this too. Due to the very frequent problems with Unity here, I'm using the Classic desktop for now as having to restart my computer every ten or twenty minutes is no fun and I want to report some bugs. :wink:

> **ManasT said:**
> How do I get the option to restart compiz again?Anyone?

---

### Post by JohnSGruber on 2011-02-14
> **ManasT said:**
> Just started using Unity now in Natty. I have got one question:

I accidentally clicked 'Ignore Future Crashes' when compiz crashed inside Unity. Now I do not get any option to restart compiz when it crashes and all I am left with is the open window (no panel, no launcher) nothing works. How do I get the option to restart compiz again ?

I usually just restart X and login again. There are (at least) two ways. The first requires a set-up.

Go to the keyboard application, the Layouts tab, and press the Options button. Find the "Key Sequence to Kill the X Server" and set up Control-Alt-Backspace to kill X. Then you can kill X when you get a crashed desktop and log back in. (Keyboard shortcuts, on the other hand, must be implemented by the window manager, so they don't work when compiz has crashed, this particular setting is one X itself looks for).

Or...without setting anything up, when compiz has died, press control-alt-F1 and log in to the virtual terminal. Enter the command
*ps aux | grep X*
X is capitalized.

Note the process number of the X session that isn't going to do you any good anymore and kill it with:
*sudo kill #* where # is the process number you just discovered.

When X is killed off (assuming it is the only one running) the system restarts gdm on a new X session and that gives you the opportunity to log into the graphical desktop again, including a new instance of compiz.

I hope that helps.

---

### Post by webme on 2011-02-14
> **mozgu said:**
> Hi,

how to disable animation of autohide launcher? I don't see this option in ccsm... Is there any way?

In CCSM/Unity plugin/Hide launcher you will find 4 hiding types: "Never", "Autohide", "Dodge Windows", "Dodge Active Window"

---

### Post by 3rdalbum on 2011-02-14
> **JohnSGruber said:**
> I usually just restart X and login again. There are (at least) two ways. The first requires a set-up.

No, it doesn't. Rather than set up Control-Alt-Backspace as a "kill X" key combination, you could just hit the default "kill X" key combination: Alt-PrintScreen(SysRq)-K.

---

### Post by zika on 2011-02-15
> **JohnSGruber said:**
> I usually just restart X and login again. There are (at least) two ways. The first requires a set-up.

Go to the keyboard application, the Layouts tab, and press the Options button. Find the "Key Sequence to Kill the X Server" and set up Control-Alt-Backspace to kill X. Then you can kill X when you get a crashed desktop and log back in. (Keyboard shortcuts, on the other hand, must be implemented by the window manager, so they don't work when compiz has crashed, this particular setting is one X itself looks for).

Or...without setting anything up, when compiz has died, press control-alt-F1 and log in to the virtual terminal. Enter the command
*ps aux | grep X*
X is capitalized.

Note the process number of the X session that isn't going to do you any good anymore and kill it with:
*sudo kill #* where # is the process number you just discovered.

When X is killed off (assuming it is the only one running) the system restarts gdm on a new X session and that gives you the opportunity to log into the graphical desktop again, including a new instance of compiz.

I hope that helps.Or, just, use, simple: **sudo service gdm restart** in tty1...

---

### Post by Framli on 2011-02-15
> **ManasT said:**
> Just started using Unity now in Natty. I have got one question:

I accidentally clicked 'Ignore Future Crashes' when compiz crashed inside Unity. Now I do not get any option to restart compiz when it crashes and all I am left with is the open window (no panel, no launcher) nothing works. How do I get the option to restart compiz again ?
My method : Ctrl+Alt+F1 **unity** Ctrl+Alt+F7

---

### Post by JohnSGruber on 2011-02-16
There seem to be more ways to recover than I imagined. Restarting gdm, however, does seem to restart any other sessions I happen to have going on other virtual consoles.

I was unable to restart by just switching to tty1 and typing *unity*. Is there more to it? When I try it I get a complaint that the DISPLAY variable isn't set properly (it isn't set at all).

ALT-SYSRQ-K worked great for me, I'm going to try to remember that--one set of keystrokes, no setup necessary, and it only kills off the one session (if there are other sessions I could switch to them and log back on). That's my favorite.

Since maintenance last Friday unity (and compiz and nux) seem more stable for me. Fewer crashes to recover from.

---

### Post by Framli on 2011-02-17
This is weird about the DISPLAY error, because here, Unity automagically assumes DISPLAY=:0 when I don't set it and only warns me with "WARNING : no DISPLAY variable set, setting it to :0".
So, if you want to restart unity, without losing opened windows :

Ctrl+Alt+F1 
**export DISPLAY=:0** *(optional step?)*
**unity** 
Ctrl+Alt+F7

---

### Post by JohnSGruber on 2011-02-18
> **Framli said:**
> This is weird about the DISPLAY error, because here, Unity automagically assumes DISPLAY=:0 when I don't set it and only warns me with "WARNING : no DISPLAY variable set, setting it to :0".
So, if you want to restart unity, without losing opened windows :

Ctrl+Alt+F1 
**export DISPLAY=:0** *(optional step?)*
**unity** 
Ctrl+Alt+F7
My mistake. I must not have been logging onto tty1 with the same userid. When I tried it again it worked. :)

---

