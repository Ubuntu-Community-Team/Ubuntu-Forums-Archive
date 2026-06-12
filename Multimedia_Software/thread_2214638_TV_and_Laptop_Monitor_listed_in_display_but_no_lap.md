---
title: "TV and Laptop Monitor listed in display but no laptop"
date: 2014-04-02
forum: Multimedia Software
---

### Post by rackit on 2014-04-02
Running 12.04 LTS on a box with hdmi output to a tv screen. In display settings, laptop and TV are listed. When I change any settings, the dialog confiming my changes doesn't appear (I assume it is showing up on the non-existent "laptop" display). After the timeout period, the settings revert. I've plugged in a monitor to the d-sub jack and it shows up in display seperate from TV and laptop and the "revert" dialog still doesn't show up on any connected displays. When I turn off the laptop in the display settings, the TV goes blank until the timeout is reached. When I set the resolution on the TV in the display settings, the TV resolution changes until the timeout is reached.

Any ideas as to how I may get the settings (i.e. HDMI resolution) to stick? Ideally, I'd like all dialog to show on the HDMI display too. No proprietary drivers used.

---

### Post by efflandt on 2014-04-03
Some hardware info may help someone help you, like possibly someone with similar hardware that has resolved that. Otherwise all you may get is wild guesses if that does not happen with other hardware. For example it may not happen if someone connects a laptop with 1080p display to a 1080p HDTV.

What make/model laptop, what graphics chip and drivers (default drivers or other), what is the native resolution of the laptop display and what resolution are you in when the laptop fails to display? It is possible that something is switching to a resolution that your TV can display, but your laptop cannot match, if you are mirroring the display instead of extended desktop.

---

### Post by rackit on 2014-04-03
Good point, [**[COLOR=#000000]efflandt[/COLOR]**]("http://ubuntuforums.org/member.php?u=937632")...

Intel Dual Core Atom D2550 1.86GHz
Chipset    Intel® NM10
VGA Graphics    Intel GMA 3650

It's not a laptop - there is no monitor connected other than the 1080p TV. Default drivers. The device looks like this: 
[IMG]http://is.gd/Gbffji[/IMG]

---

### Post by 23dornot23d on 2014-04-03
You could try either of these methods - on entry into the desktop

arandr or ( kde - settings - system settings - monitor settings - change to what you need then save as default ) 

> 
sudo apt-get update
sudo apt-get install arandr


[IMG]http://i.minus.com/ibsMKokdWX4HYT.png[/IMG]

* ( possibly giving warnings above on my setup - as I am running another graphics display driver - but its just to give an idea of what you will see )

> 
One way that worked well was in kde and is through using kde .... settings - system settings - display and monitor / that seems to work better in some cases and save the settings as default once you have changed them to what you need for your own system to work properly.
 
But this way is only if you run the KDE desktop and it will work on starting the desktop up - even though the login screen may remain at a lower resolution.


---

### Post by rackit on 2014-04-04
In xubuntu, both displays are listed but I have the option as to where to position them. If I position them in the same place as the other, it all works fine. I'll have a look at randr too. Thanks [**[COLOR=#000000]23dornot23d[/COLOR]**]("http://ubuntuforums.org/member.php?u=953253")

---

