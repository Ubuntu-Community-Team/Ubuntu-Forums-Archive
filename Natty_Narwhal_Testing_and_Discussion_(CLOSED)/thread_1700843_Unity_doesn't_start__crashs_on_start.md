---
title: "Unity doesn't start / crashs on start"
date: 2011-03-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Bazon on 2011-03-05
On a fresh 11.04 alpha installation, unity doesn't start:

when logging in as "desktop edition", I got nothing but a desktop background picture. (unity compiz plugin is enanbled) when opening a terminal there, I can't type in.

when logging in as "classic desktop", compiz works as it shoulds. (using "experimental 3d support for nvidia card" nvidia driver in additional drivers)
when typing "unity" in the terminal, it doesn't start, but I get this:

```

$ unity
unity-panel-service: no process found
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
compiz (core) - Error: InitPlugin 'unitymtgrabhandles' failed
compiz (core) - Error: Couldn't activate plugin 'unitymtgrabhandles'
Initializing scale options...done
Initializing session options...done
** (<unknown>:5887): DEBUG: Unity accessibility initialization
unity-files-daemon: no process found
unity-applications-daemon: no process found
unity-files-daemon: no process found
unity-applications-daemon: no process found
Initializing unityshell options...done
** (<unknown>:5887): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (<unknown>:5887): DEBUG: Loading Place: /usr/share/unity/places/applications.place
** (<unknown>:5887): DEBUG: PlaceEntry: Applications
** (<unknown>:5887): DEBUG: Loading Place: /usr/share/unity/places/files.place
** (<unknown>:5887): DEBUG: PlaceEntry: Files & Folders

(<unknown>:5887): libindicator-WARNING **: Shortcut Group does not have key 'TargetEnvironment' falling back to deprecated use of 'OnlyShowIn' and 'NotShowIn'.

(<unknown>:5887): libindicator-WARNING **: Shortcut Group does not have key 'TargetEnvironment' falling back to deprecated use of 'OnlyShowIn' and 'NotShowIn'.
** (<unknown>:5887): DEBUG: Loading Place: /usr/share/unity/places/applications.place
** (<unknown>:5887): DEBUG: PlaceEntry: Applications
** (<unknown>:5887): DEBUG: Loading Place: /usr/share/unity/places/files.place
** (<unknown>:5887): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:5887): DEBUG: Connected to proxy
** (<unknown>:5887): DEBUG: Connected to proxy
** (<unknown>:5887): DEBUG: setting to primary screen rect: x=0 y=0 w=1280 h=1024
Segmentation fault (core dumped)


```

any ideas?
thanks!

---

### Post by cariboo on 2011-03-05
Try:

```
unity --reset 
```

in a terminal and note what errors you get.

---

### Post by Bazon on 2011-03-05
nearly the same as before:

```

$ unity --reset
unity-panel-service: no process found
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
compiz (core) - Error: InitPlugin 'unitymtgrabhandles' failed
compiz (core) - Error: Couldn't activate plugin 'unitymtgrabhandles'
Initializing scale options...done
Initializing session options...done
** (<unknown>:1546): DEBUG: Unity accessibility initialization
unity-files-daemon: no process found
unity-applications-daemon: no process found
unity-files-daemon: no process found
unity-applications-daemon: no process found
Initializing unityshell options...done
** (<unknown>:1546): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (<unknown>:1546): DEBUG: Loading Place: /usr/share/unity/places/applications.place
** (<unknown>:1546): DEBUG: PlaceEntry: Applications
** (<unknown>:1546): DEBUG: Loading Place: /usr/share/unity/places/files.place
** (<unknown>:1546): DEBUG: PlaceEntry: Files & Folders

(<unknown>:1546): libindicator-WARNING **: Shortcut Group does not have key 'TargetEnvironment' falling back to deprecated use of 'OnlyShowIn' and 'NotShowIn'.

(<unknown>:1546): libindicator-WARNING **: Shortcut Group does not have key 'TargetEnvironment' falling back to deprecated use of 'OnlyShowIn' and 'NotShowIn'.
** (<unknown>:1546): DEBUG: Loading Place: /usr/share/unity/places/applications.place
** (<unknown>:1546): DEBUG: PlaceEntry: Applications
** (<unknown>:1546): DEBUG: Loading Place: /usr/share/unity/places/files.place
** (<unknown>:1546): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:1546): DEBUG: Connected to proxy
** (<unknown>:1546): DEBUG: Connected to proxy
** (<unknown>:1546): DEBUG: setting to primary screen rect: x=0 y=0 w=1280 h=1024

** (<unknown>:1546): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:1546): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1546): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `GParam'

(<unknown>:1546): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1546): WARNING **: bool IconLoader::ProcessGIconTask(IconLoader::IconLoaderTask*): Unable to load icon banshee-1 at size 104
Segmentation fault (core dumped)

```


additional, after that I lose window borders and the ability to put windows in the foreground. panels are also gone.

---

### Post by Bazon on 2011-03-06
OK, I think, I'm a bit closer to the reason of the crash:
in 10.10, for this computer the **nvidia-173** driver is installed.
this driver is NOT proposed in the "additional drivers" application (jochey I suppose), instead a "experimental 3D support for NVIDIA graphics cards" is suggested.

When I try to install nvidia-173 from synaptic, synaptic proposes to **remove** a bunch of packets, **including ubuntu-desktop and xorg**.

So is it possible, that unity simply won't run on that card? it's not soooo old, only a few years....

---

### Post by MiD-AwE on 2011-04-21
I'm getting similar results with GTX 260 NVIDIA. I cannot get past bootscreen. I hit escape to see what's happening and get to login (command only). I tried "unity start" and get:
```
warning: no Display variable set, setting it to 0
unity-panel-service: no process found
compiz (core) - Error: Couldn't load plugin 'start'
compiz (core) - Fatal: Couldn't open display :0
```:confused:

I upgraded from 10.10 just this morning to help out with this kinda stuff, so I'm not that upset, but if anyone has any suggestions I'd love to hear them.

Thanks in advance.

---

### Post by cariboo on 2011-04-21
> **MiD-AwE said:**
> I'm getting similar results with GTX 260 NVIDIA. I cannot get past bootscreen. I hit escape to see what's happening and get to login (command only). I tried "unity start" and get:
```
warning: no Display variable set, setting it to 0
unity-panel-service: no process found
compiz (core) - Error: Couldn't load plugin 'start'
compiz (core) - Fatal: Couldn't open display :0
```:confused:

I upgraded from 10.10 just this morning to help out with this kinda stuff, so I'm not that upset, but if anyone has any suggestions I'd love to hear them.

Thanks in advance.

Start in recovery mode and choose failsafeX from the menu, this should get you to a working desktop, where you can install the proper graphics driver.

---

### Post by MiD-AwE on 2011-04-21
> **cariboo907 said:**
> Start in recovery mode and choose failsafeX from the menu, this should get you to a working desktop, where you can install the proper graphics driver.
Thanks, I'll give that a try.

---

### Post by MiD-AwE on 2011-04-21
I started Ubuntu with failsafeX and it worked, but when I checked for correct graphics driver it says that the recommended driver is installed but not in use. :confused: How do I tell it to use the installed driver?

---

### Post by Duncan Williams on 2011-04-21
sort of same here, I got `nvidia 173 driver' show up in `additional drivers' after installing/changing from (nouveau/experimental) now I have to boot into unity 2D to get usable desktop.

---

### Post by MiD-AwE on 2011-04-22
Well, basically, Ubuntu 11.04 will not work unless I use failsafeX.

I've tried all I know but the drivers install and I'm told to restart but it will not load Ubuntu until I use failsafeX no matter what I try.

I'll have to wait 6 more days and try again. So, I'm using Kubuntu 10.10 until then and hopefully it will work.:(

---

