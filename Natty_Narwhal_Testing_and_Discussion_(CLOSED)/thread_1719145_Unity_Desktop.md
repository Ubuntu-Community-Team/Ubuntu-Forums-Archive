---
title: "Unity Desktop"
date: 2011-04-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by gdonwallace on 2011-04-01
Prior to upgrading to Natty Beta, I was running "Ubuntu Classic" (Gnome Desktop).  When the beta for Natty came out, I decided to give Unity another go and see if there had been any updates.  So at login, I choose the desktop "Ubuntu" thinking it will launch with the Unity desktop.  However; I get logged in, and all I get is my wall paper.  There are no panels at the top of bottom of the screen, and no launcher on the left hand side.

When I switch back to Gnome (the only way to do this is CTRL+ALT+Backspace and login under Ubuntu Classic) everything seems ok.

Any others having this problem, or anyone know of a way to fix it.

---

### Post by julianb on 2011-04-01
That has happened to me, but not since natty was in alpha 1 or maybe alpha 2.

first thing i would do is make sure the system is fully up to date and then re-try booting in to Natty. In the alpha stage some of the display stuff worked off-and-on rather than being consistent.

a fresh install might have different results (but i suggest you check whether it works from an up-to-date liveUSB or liveCD first).

---

### Post by gdonwallace on 2011-04-01
Ran Synaptic Package Manager, there where some files that needed to be updated.  Letting that run will try again once I get home this afternoon and see if that fixed the problem.

---

### Post by safarin on 2011-04-01
> **gdonwallace said:**
> Prior to upgrading to Natty Beta, I was running "Ubuntu Classic" (Gnome Desktop).  When the beta for Natty came out, I decided to give Unity another go and see if there had been any updates.  So at login, I choose the desktop "Ubuntu" thinking it will launch with the Unity desktop.  However; I get logged in, and all I get is my wall paper.  There are no panels at the top of bottom of the screen, and no launcher on the left hand side.

When I switch back to Gnome (the only way to do this is CTRL+ALT+Backspace and login under Ubuntu Classic) everything seems ok.

Any others having this problem, or anyone know of a way to fix it.

I got the same problem and also in "Ubuntu Classic" right now.

My scenario, the monitor and application inside ubuntu blinking and then got compiz error. Worst case, even terminal blinking and this application slowly move bit a bit to down like being drag every-time it blink.. hehehe..

Still have no solution :D Maybe they will fixed it.

---

### Post by cariboo on 2011-04-01
Have you got 3D drivers of some sort enabled?

---

### Post by stanz on 2011-04-01
I've had these unwanted results also.
Most of the time I only had wallpaper, so I ran unity in a terminal [if I had key-cuts working!]
while I searched for clues.
:)
Sometimes even to right-click on the application icon, brings on a crash [apport says compiz stoped].

Good progress with the image, I'd say.

---

### Post by jerrylamos on 2011-04-01
If Unity 3D (really Compiz) doesn't want to play, log in Classic mode then use Synaptic to install Unity 2D.  Looks very similar to 3D but doesn't use Compiz hence not as much eye candy.  2D runs on all my pc's.  3D & Compiz run on a couple and of course Compiz is still crashing.

Jerry

---

### Post by safarin on 2011-04-01
> **jerrylamos said:**
> If Unity 3D (really Compiz) doesn't want to play, log in Classic mode then use Synaptic to install Unity 2D.  Looks very similar to 3D but doesn't use Compiz hence not as much eye candy.  2D runs on all my pc's.  3D & Compiz run on a couple and of course Compiz is still crashing.

Jerry

Hi Jerry,

How to install Unity 2D?

---

### Post by thiebaude on 2011-04-01
that happened to me one time so what i did was: alt f2 then gnome-panel then i was able to log out and when i got the log in prompt, i loged-in differently this time and had no problems.

---

### Post by ranch hand on 2011-04-01
> **safarin said:**
> Hi Jerry,

How to install Unity 2D?
Look in synaptic.  it's in there.

---

### Post by ranch hand on 2011-04-01
Unity is now working on my upgraded install.

Be nice to try it on a clean install but I am just a bit too gun shy of the images to try that.

Lubuntu alpha3 and XubuntuB1 both work and boot fine.

---

### Post by safarin on 2011-04-02
> **ranch hand said:**
> Look in synaptic.  it's in there.

Thank you, I accidentally miss to read the word synaptic in previous post.. :P

---

### Post by Bazon on 2011-04-02
On my old hardware, the same thing happens as there is no more nvidia 173 driver, only a "nvidia experimental" driver which seems to not be able to start unity.
however, that driver starts normal compiz in the classic session.

---

### Post by safarin on 2011-04-02
I have installed this unity-2d but how to activate it?? :confused:
already restart my computer.. nothing happen :P

---

### Post by ranch hand on 2011-04-02
> **safarin said:**
> I have installed this unity-2d but how to activate it?? :confused:
already restart my computer.. nothing happen :P
after you click on the login look at your bottom panel on the login page.  You want to look at the "session" box and make sure that you are booting to "Unity2D" instead of "Ubuntu" or "Ubuntu Classic".

---

### Post by safarin on 2011-04-02
> **ranch hand said:**
> after you click on the login look at your bottom panel on the login page.  You want to look at the "session" box and make sure that you are booting to "Unity2D" instead of "Ubuntu" or "Ubuntu Classic".

Thanks.. in Unity2D right now! :popcorn:

---

### Post by ranch hand on 2011-04-02
Great.  Mark the thread solved so others can find out what you did.

It is done under "Thread Tools" top right of this page.

---

### Post by iggykoopa on 2011-04-02
I had the same issue, I had to install compiz-config-settings-manager and enable the unity plugin. May not be your issue, but you can give it a try.

---

### Post by safarin on 2011-04-02
> **ranch hand said:**
> after you click on the login look at your bottom panel on the login page.  You want to look at the "session" box and make sure that you are booting to "Unity2D" instead of "Ubuntu" or "Ubuntu Classic".

Do you know how to change this Unity2D to default session? Need to select Unity2D everytime when login.. Huhuhu

---

### Post by safarin on 2011-04-02
> **iggykoopa said:**
> I had the same issue, I had to install compiz-config-settings-manager and enable the unity plugin. May not be your issue, but you can give it a try.

hi iggykoopa,
I just installed ccsm, I already can get into Ubuntu session (not classic or unity2D) without monitor blinking problem anymore. Just having gnome panel problem here (notice no icon where my mouse cursor have been point). If I run gnome-panel, the application program menu will disappear (such as no close, minimize and maximize icon). Hehehe..

Anyway.. Thanks

[ATTACH]187850[/ATTACH]

---

### Post by ranch hand on 2011-04-02
It should stay there unless you change it to something else.

I know there is a some conformation file that has that in it but I can't for the life of me remember where the bugger is.  It will set a default or leave it where ever you last used it.  Sorry.

You might check in /.gconf/desktop/gnome/session or there about and just check the files.  Could be in /etc/gdm or maybe /usr/share/gdm.  Too tired to think.

---

### Post by safarin on 2011-04-02
> **ranch hand said:**
> It should stay there unless you change it to something else.

I know there is a some conformation file that has that in it but I can't for the life of me remember where the bugger is.  It will set a default or leave it where ever you last used it.  Sorry.

You might check in /.gconf/desktop/gnome/session or there about and just check the files.  Could be in /etc/gdm or maybe /usr/share/gdm.  Too tired to think.

Hahaha.. Thank you for hardly remember it. I will try to explore it..

Anyway, Thanks

---

### Post by cariboo on 2011-04-02
> **safarin said:**
> hi iggykoopa,
I just installed ccsm, I already can get into Ubuntu session (not classic or unity2D) without monitor blinking problem anymore. Just having gnome panel problem here (notice no icon where my mouse cursor have been point). If I run gnome-panel, the application program menu will disappear (such as no close, minimize and maximize icon). Hehehe..

Anyway.. Thanks

[ATTACH]187850[/ATTACH]

The reason you're losing the home button is because Unity doesn't use gnome-panel. When you start the panel it is covering up the home button.

What problem are you trying to solve by starting gnome-panel?

---

### Post by safarin on 2011-04-02
> **cariboo907 said:**
> The reason you're losing the home button is because Unity doesn't use gnome-panel. When you start the panel it is covering up the home button.

What problem are you trying to solve by starting gnome-panel?

I realize unity doesn't use gnome-panel. What I want is this thing (icon, I don't know what to call, maybe "unity start panel")
This picture I screenshot from "Unity-2D" session.

[ATTACH]187851[/ATTACH]

---

### Post by cariboo on 2011-04-02
That's what I was referring to as the Home button.

---

### Post by cor2y on 2011-04-02
i cant get unity 3d session to launch/run  on login, unity 2d session works and classic ubuntu session works but not unity 3d, now i know it works because if i run it on either the 2D or classic session it launches and works, but since i have no panels or working shortcut keys in the unity 3D session theres nothing i can do to launch it, i want to know whats the cause, is it me? hidden config files? did something get borked in the install/upgrade?

---

### Post by cariboo on 2011-04-02
You should be able to create a terminal launcher on the desktop when you are in 2D or the Classic desktop, then switch to Unity , open the terminal and type:

```
unity --reset
```

It more than likely is something in your home directory causing the problem, but once you get Unity running, you shouldn't have a problem from there.

---

### Post by cor2y on 2011-04-02
Well it worked for a while until i decided to mess with compiz via cssm and then it crashed and i was back to square one, what hidden folder do you think i should delete in my home folder?
I've tried compiz, gconf, gconfd, i dont want to do gnome or gnome2.

---

### Post by safarin on 2011-04-03
> **cariboo907 said:**
> That's what I was referring to as the Home button.

Ohh.. so thing is call home button. I try your "unity --reset" then get this outcome.

```

safarin@journey:~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
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
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing scale options...done
Initializing session options...done
** (<unknown>:2350): DEBUG: Unity accessibility initialization

Screen geometry changed:
  Monitor 0(primary)
   0x0x1024x768
  Monitor 1
   0x0x1024x768

unity-panel-service: no process found
unity-panel-service: no process found
Initializing unityshell options...done
** (<unknown>:2350): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (<unknown>:2350): DEBUG: PlaceEntry: Applications
** (<unknown>:2350): DEBUG: PlaceEntry: Commands
** (<unknown>:2350): DEBUG: PlaceEntry: Files & Folders

(<unknown>:2350): libindicator-WARNING **: Shortcut Group does not have key 'TargetEnvironment' falling back to deprecated use of 'OnlyShowIn' and 'NotShowIn'.
** (<unknown>:2350): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus


** (<unknown>:2350): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window60823792: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

** (<unknown>:2350): DEBUG: Connected to proxy
** (<unknown>:2350): DEBUG: Connected to proxy
** (<unknown>:2350): DEBUG: Connected to proxy

(<unknown>:2350): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:2350): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:2350): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:2350): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:2350): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed

(<unknown>:2350): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
** (<unknown>:2350): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:2350): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:2350): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:2350): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:2350): DEBUG: IndicatorAdded: libme.so
** (<unknown>:2350): DEBUG: IndicatorAdded: libsession.so
** (<unknown>:2350): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:2350): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:2350): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:2350): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:2350): DEBUG: IndicatorAdded: libme.so
** (<unknown>:2350): DEBUG: IndicatorAdded: libsession.so
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
** (<unknown>:2350): DEBUG: Setting to primary screen rect: x=0 y=0 w=1024 h=768


```

There is still no home panel.

---

### Post by gdonwallace on 2011-04-04
In reading all the posts in the thread, I wanted to say thanks to everyone trying to help resolve this.

I have a 3D card installed.  Unity was running previous to the Alpha 3 update.  After that, no panel only wallpaper.

I am currently running "Ubuntu Classic" desktop with no issues.

I have tried running the "unity --reset" command, and am told that I don't have unity installed. (??) Pretty odd since it is the default desktop, and one I was using fine.

The error file .xsession-error in my ~/home directory was the same as the one posted in this thread.  

I may try to install Unity, but I would already think that it was installed.  I wouldn't expect the update process to uninstall it, as I was not running it when I did the update to alpha3.  

Pretty odd.

---

### Post by gdonwallace on 2011-04-04
Update to previous post.

I installed unity, and ran the unity --reset command.  It appears to have worked, but I ran it through a terminal instead of a CLI interface.  

Also I had a couple things up and running, it had some pretty weird effects on them as well.

Will have to switch to alt terminal and try it from there with everything shutdown.  Will update and let you know what happens.

---

### Post by ibrrfarr on 2011-04-04
Identical problems.  What worked for me is going to terminal and typing **Unity --reset **.  Now I can run in all start up types I want.

There was a bit of a drag in time; however, when it all reset and I rebooted no problems.

It appears, to me, that as Unity (or whatever gives the left sidebar  icons and top toolbar) requires Desktop Wall and when you enable Rotate  Cube you remove that from Compiz.  Don't know a lot about it; however,  this strikes me as an issue between the OS itself and the features of  Compiz. 

I really don't like all the eye candy to begin with so I am hopeful that if Cannonical (or whomever pulls the strings) will begin to put together some layman's-type tutorials for these programs which are automatically shipped w/each new instalment.  With that said, I realize that that this is Beta and all that, but one would think that so close to the end result and w/all the hype that simple things like this would be hammered out.

I am *not* slamming them nor the WONDERFUL folks on here whom help code, test, etc.  If, though, we as a community do not offer up _constructive criticism_ then we are doomed to continue to repeat the mistakes of the past.

I am running an Acer Aspire One D255.  Intel Atom N450 1.66GHz, 512 cache, 1GB memory.

Want to note here that I did check Unity in the Compiz settings.  Sorry adding this late.

---

### Post by gdonwallace on 2011-04-05
I finally got Unity working.  What I had to do was go to ALT-F1 and type " Unity --reset", and that forced unity to start.  But it also completely jacked up my open windows.  I didn't close everything down before doing issuing the reset command.  But Unity did come up.  I reset my computer, chose "Ubuntu" as the desktop environment and everything seems to be working fine.  

Still not sure what happened to cause Unity to stop working, but it was Alpha 3 that I downloaded, so that could have been the issue.  Anyway, its fixed and working now.  Will continue testing and using, see if Unity will work for me.  But the real test will be a dual monitor setup.

---

