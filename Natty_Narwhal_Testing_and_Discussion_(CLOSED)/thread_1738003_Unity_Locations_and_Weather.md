---
title: "Unity Locations and Weather"
date: 2011-04-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ds_shellback on 2011-04-24
Hi,

I've been using ubuntu - initially KDE and then Gnome since 5.04; so I'm determined to get Unity going and have downloaded and installed the Beta.

As a long time Gnome user it takes a bit of getting used to, but only because I knew where everything was. Unity behaves differently to the Gnome desktop but I'm getting there; need to hunt down a guide.

Couple of questions about desktop layout / customisation:-

1). Is it still possible to add locations and see brief weather info which was under the Time & Date in the top RH corner - I had a couple of locations set which interested me. Is it configurable somewhere or a separate applet or has it been dropped altogether in Unity? 

2). Is it possible to turn off the "Apps Available for Download" section under Applications and just show recent and installed? It's akin to having a "standard" product installed and getting nagged to get the pro version - just niggles me I suppose, but I'll get used to it if needs be.

---

### Post by sparker256 on 2011-04-24
> **ds_shellback said:**
> Hi,

I've been using ubuntu - initially KDE and then Gnome since 5.04; so I'm determined to get Unity going and have downloaded and installed the Beta.

As a long time Gnome user it takes a bit of getting used to, but only because I knew where everything was. Unity behaves differently to the Gnome desktop but I'm getting there; need to hunt down a guide.

Couple of questions about desktop layout / customisation:-

1). Is it still possible to add locations and see brief weather info which was under the Time & Date in the top RH corner - I had a couple of locations set which interested me. Is it configurable somewhere or a separate applet or has it been dropped altogether in Unity? 

2). Is it possible to turn off the "Apps Available for Download" section under Applications and just show recent and installed? It's akin to having a "standard" product installed and getting nagged to get the pro version - just niggles me I suppose, but I'll get used to it if needs be.

For weather the replacement is indicator-weather and you can find it in the software center. Follow this thread if you have trouble installing as some people are having trouble with this and unity. I am not having that problem and both are running fine on my install. 

[http://ubuntuforums.org/showthread.php?t=1704614&highlight=Indicator-Weather]("http://ubuntuforums.org/showthread.php?t=1704614&highlight=Indicator-Weather")

---

### Post by FoundmyTux on 2011-04-24
Thanks sparker256

Not having a weather indicator was the only thing I was missing in Natty.

---

### Post by tlcstat on 2011-04-24
Greetings,
If you are running Natty and Unity it is possible that the weather applet will not work. It is a Gnome applet that is in a state of update for Unity. 
However if you want to try and it won't install from the Software Center you should have success from the command line, "sudo apt-get install indicator-weather". However you probably won't get the panel indicator. 
If it doesn't work you can try to reinstall later but you should remove your previous version first. The current state is that it works for some but not for most. 
tlcstat

---

### Post by mc4man on 2011-04-24
The indicator-weather is in better shape than before and should show up after install.
Then just add your location(s) thru it's preferences, you need to type in the location, then search
(unless your desired location is on the currently very short list in the drop down

It works pretty much as well as the gweather applet except no radar map

---

### Post by mafitzpatrick on 2011-04-24
Just installed and it works fine. You need to start it (Alt-F2, enter indicator-weather). It should start up, appears orange until configured.

[Edit: No need to add it to Startup Applications - Thanks ds_shellback]

Let me know if you have any trouble.

---

### Post by ds_shellback on 2011-04-24
Thanks, that works a treat installed it with

```
sudo apt-get install indicator-weather
```

Don't seem to need to add it to startup applications - it came back ok with a restart.

---

### Post by KStorm on 2011-04-25
Though it pulls in a whole 19 megs worth of dependencies, it really is worth it.:P

---

### Post by cariboo on 2011-04-26
With the default hard drive size of 250GiB or larger in most new computer systems, is 19MiB really that much of a concern?

---

