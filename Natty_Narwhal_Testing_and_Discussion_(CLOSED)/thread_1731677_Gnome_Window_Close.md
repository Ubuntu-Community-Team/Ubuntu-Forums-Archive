---
title: "Gnome Window Close"
date: 2011-04-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by LifeBound on 2011-04-17
For some reason when I use gnome now none of my windows (for example firefox) have the close minimize and maximize buttons. I think its a error between gnome and unity? Anybody know how to fix this?

---

### Post by 23dornot23d on 2011-04-17
Do you have a screenshot ...... its probably a tweak tool you need .......

---

### Post by LifeBound on 2011-04-17
Here ya go.

---

### Post by 23dornot23d on 2011-04-17
Same as me this is in UNITY ....... with COMPIZ and 3D ...... 

I get the same too .....

Until I go into Gnome-Shell (this is where the tweak tool comes in) or Classic 2D then all is ok ....... 

Not sure of a solution yet - I too need one .......... for UNITY ......

you can do ALT + F2

unity --reset

I think thats the command ..... give me a sec will swap to [UNITY]("http://img812.imageshack.us/img812/5858/screenshot69f.png") to try it .......... ok it works ok for that session ....

then resets back to not borders for the next run

---

### Post by LifeBound on 2011-04-17
Yea unity is fine right now, dont like the desktop enviorment so much should have stayed for netbooks. Need to find a way to fix gnome.

---

### Post by 23dornot23d on 2011-04-17
What is the problem that you have with gnome ?

By Gnome - I presume you mean Gnome-shell

Lets see if we can fix it

---

### Post by LifeBound on 2011-04-17
In the picture as you can see im missing the close, minimize, and maximize buttons. So i am unable to move around windows and make them bigger and smaller. I think its global menu messing it up, but Im not sure why its happening.

---

### Post by 23dornot23d on 2011-04-17
You probably need the tweak too ...... the link is here and some explanation of what it can do .......... [LINK]("http://www.webupd8.org/2011/04/introducing-gnome-tweak-tool-gui-to.html")

---

### Post by LifeBound on 2011-04-17
Cant exactly use gnome tweak tool because its for gnome 3 and im using gnome 2.32

---

### Post by mc4man on 2011-04-17
> **LifeBound said:**
> In the picture as you can see im missing the close, minimize, and maximize buttons. So i am unable to move around windows and make them bigger and smaller. I think its global menu messing it up, but Im not sure why its happening.
The default now for the Classic login is not to have the global menu enabled and it doesn't apppear to be in your screen
(if it is then maybe disable - simplest way is to just remove the applet if it is there. (indicator applet appmenu

Have you opened up compizconfig-settings-manager (ccsm) and made sure the 'Window decoration' plugin is enabled, as well as 'Move window' and 'Resize window' plugins?

---

### Post by 23dornot23d on 2011-04-17
Superb mc4man ..... how did they get disabled - I do not know ....

but that sorted it for me ..... all were un-ticked before ...... now unity works ok .....

[Screenshot]("http://img140.imageshack.us/img140/9816/screenshot73.png") - I now have the window borders back again .... permanently  ... ;)

---

### Post by LifeBound on 2011-04-17
> **mc4man said:**
> The default now for the Classic login is not to have the global menu enabled and it doesn't apppear to be in your screen
(if it is then maybe disable - simplest way is to just remove the applet if it is there. (indicator applet appmenu

Have you opened up compizconfig-settings-manager (ccsm) and made sure the 'Window decoration' plugin is enabled, as well as 'Move window' and 'Resize window' plugins?

I fixed it in compiz thank you for telling me.

---

### Post by mc4man on 2011-04-17
> how did they get disabled
Typically by enabling and or disabling _certain _plugins thru ccsm. In those cases all the plugins get unset, many times people don't know or remember to re-enable the useful ones

(certain plugins are better enabled or disabled thru gconf-editor, _though only some_.
gconf-editor does not resolve conficts, so it should be used carefully.
Hopefully the bug about crashing, unsetting ect. in ccsm will finally get fixed someday.

---

