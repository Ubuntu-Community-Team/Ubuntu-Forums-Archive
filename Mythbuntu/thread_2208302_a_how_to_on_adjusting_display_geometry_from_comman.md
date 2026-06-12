---
title: "a how to on adjusting display geometry from commandline, run mythtv as a window"
date: 2014-02-27
forum: Mythbuntu
---

### Post by sdowney717 on 2014-02-27
simply run like this

```
mythfrontend -w --geometry 900x670

```

this fits my old TV screen.

What would be command to run from commandline the mythbackend?

---

### Post by blm-ubunet on 2014-02-27
I wouldn't recommend running frontend in a window..you can use --geometry option with normal full screen.
If you are using multiple monitors & separate X screens, you need to use the -display cmdline option or set the DISPLAY env variable.

BE:
On a normal installation like mythbuntu, mythbackend is run via upstart

sudo service mythtv-backend [status|stop|start]

Mythbuntu has auto-spawning backend script & renames the backend executable to mythbackend.real

So to run from terminal:
sudo service mythtv-backend stop
mythbackend.real -v upnp > locallogfile.txt
(just an example)

You can use <TAB> auto completion with the service & which cmds.
which mythbackend <TAB><ENTER>

---

### Post by sdowney717 on 2014-02-27
My ref idea is along lines of not seeing it in full screen.

I think it is auto starting ok.

---

### Post by blm-ubunet on 2014-02-27
AFAIK The BE has no GUI screen except for the webserver.

mythtv-setup can be launched with --geometry cmdline option

MythTV app & GUI is intended as "10 foot high" from the couch using the whole screen & not really using the mouse.
It works best (IMO) with a multi-media keyboard (IR remotes are just to slow).

---

### Post by sdowney717 on 2014-02-27
I needed the geometry setting to shrink the window to fit on the old TV I have.
The TV is running as a side extension to the primary screen.
This way I can run mythtv on the left and still use the computer on the right.

In fact I have a vid running over there now while typing this in on the primary screen.

If I run in a window, then I can post screen shots for help.

---

### Post by blm-ubunet on 2014-02-28
But you don't need to window mythtv to do either of those things..it really is a full screen app.
And you don't need to use the geometry override, you can use the screen setup wizard to set the viewable screen size.

If you are using the nVidia graphics driver you can adjust the overscan/underscan with viewportin/out or the nvidia-settings GUI tool (version dependent).
A combination of screen wizard & underscan/overscan compensation is good for old CRT TV that have bad geometric distortions.

With nVidia graphics:
Running 2 or more monitors as separate X screens (not twinview) allows complete independence with full screen & video modes (refresh rates).
But if you do this you need to know how to launch mythtv on the correct display.
To launch on the second X screen use:
```
mythfrontend -display :0.1  --geometry XxY
```
or
launch from script via keyboard or menus etc..
```
export DISPLAY=":0.1"
mythfrontend
```

---

### Post by sdowney717 on 2014-03-02
Thank you, that would be easier than dragging and trying to fit to the tv.
I had given up on that as I knew it would be too hard for people in my house to do.

Ideal to use a separate keypad-mouse on that separate x screen.
Is it possible?

---

### Post by blm-ubunet on 2014-03-06
Separate X screens are not independent X servers..There is only one mouse pointer (focus) for the screen collection.
Separate X screens allows video mode independence & guaranteed tear-free full screen VDPAU presentation (requires correctly behaved composite manager).

Inputs from LIRC etc do not follow "focus". So an IR remote does allow control of mythtv (for example) when the focus is on another screen/application.

To utilize multiple myth FEs on one X server you have to use environmental variables to get unique identifiers/config.xml.

Maybe multiple X servers on one box is a better soln..but I think that requires multiple video cards.
Maybe run one FE in a virtual machine, this could have truly terrible video performance on bottom end or old h/w.

---

