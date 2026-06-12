---
title: "Workspaces"
date: 2011-03-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by cecilpierce on 2011-03-06
Does any body know how to add workspaces ?
I only have two and would like to have four because I enabled the desktop cube and when I flip it, it looks like a flat panel, not a cube.
:confused:

---

### Post by mc4man on 2011-03-06
ccsm > general options > desktop size
(1 vertical X horizontal (typically 4

---

### Post by cecilpierce on 2011-03-06
> **mc4man said:**
> ccsm > general options > desktop size
(1 vertical X horizontal (typically 4

Thanks, that gave me the cube back.

---

### Post by mc4man on 2011-03-07
> **cecilpierce said:**
> Thanks, that gave me the cube back.

I use rotate/cube here instead of wall,  fits unity much  better for me 
(along with scroll on desktop
Unfold is also a decent option to expo (workspace switcher in launcher), though there some useful things about expo - 

the launcher is active when in expo so apps can be opened on specific workspaces though that's sometimes a little sketchy atm as to which WS it opens in
A slight downside is when moving windows in expo you aren't prevented from leaving the window top in the unity panel which is not ideal

---

### Post by beew on 2011-03-07
@mc4man

How do you use the cube with Unity? I tried enabling desktop cube in ccsm, then it said enabling desktop cube would disable disktop wall, which would disable Unity.

According to this link there will probably be no cube in 11.04.
[www.webupd8.org/2011/03/no-more-compiz-desktop-cube-plugin-in.html]("www.webupd8.org/2011/03/no-more-compiz-desktop-cube-plugin-in.html")

I am willing to take a wait and see approach about Unity as it is still early, but i have to say so far I am not impressed at all. I am not opposing to experimenting with new ideas, but it would be a step in the wrong direction if they take away functioinality and choice.

---

### Post by mc4man on 2011-03-07
to enable cube (and you should also enable rotate for various reasons)

Before trying to set in ccsm
```
gksudo gedit /usr/share/compiz/unityshell.xml
```
remove the line marked in blue entirely, save and then open ccsm to enable cube and rotate (_you may want to do a logout/in before proceeding to ccsm_
```
             <requirement>
                <plugin>opengl</plugin>
                [COLOR="Blue"]<plugin>wall</plugin>[/COLOR]
            </requirement>
```

It's likely when you do this in ccsm that compiz will crash and you'll unset most if not all compiz plugins.
Even though compiz crashes just continue on enabling at least the basic's or all you want enabled, then do a logout/in to set

!! You may want to note what plugins are enabled first if you wish to set them all back on. _If you start ccsm from the terminal it will list all of the enabled plugins for you_
If you intend to use that list to re-enable from make sure you move the terminal to the side before you crash compiz
 - myself i disable some from the default set, and change the setting's for some others

Edit: technically there is no reason not to have cube/rotate, it works quite fine - a bit of history as to why wall was made a requirement (still disagree with this 

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/683211](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/683211)

---

### Post by beew on 2011-03-07
Thanks, I will try that out.

---

### Post by beew on 2011-03-07
@mc4man (or anyone who can help)

I carried out your instructions and have successfully disabled desktop wall and enabled desktop cube and rotating cube in ccms and reboot, while the settings in ccms seem alright but I still have no cube (cube and rotating cube enabled, unity enabled, desktop wall disabled).  Clicking the desktop switcher just display 4 flat desktops like it was before.

Thanks in advance for any help

---

### Post by mc4man on 2011-03-07
> Clicking the desktop switcher just display 4 flat desktops like it was before.
The so called 'desktop switcher' has nothing to do with rotate, cube or wall, it's another plugin called 'expo'

Sounds like you should ck. out the settings and test wall or rotate and viewport switcher and possibly cube if interested in cube stuff

I don't actually use cube . Do however like rotate instead of wall, rotate being a bit simpler and works on 1 vertical 'set' of workspaces at a time.
(rotate needs 'something' to rotate, that's why cube gets enabled.
My preferred method to rotate is to  use scroll on desktop (in viewport switcher plugin), to switch (flip) desktops, though there are several other ways

Wall has more settings and extra stuff than rotate, slides instead of flipping and can use more than 1 vertical at the same time

Anyway some basic default bindings -  wall uses some of same
keyboard -
for rotate - Ctrl+Alt+left or right arrow
for cube - Ctrl+Alt+mouse button 1+mouse movement
for unfold - Ctrl+Alt+arrow down > l or r

mouse - (for desktop based switching when cursor is on desktop
cube - middle mouse button click (depress scroll wheel)+ mouse movement
rotate  - scroll wheel  or scroll area on touchpad

There are also many other keyboard and or mouse bindings ect. ect. for any and all

---

### Post by beew on 2011-03-07
Hi, I can now rotate  with the ctr+alt+left+right. But is there  any way to use the switcher thing on the Unity bar to do that. I use the  key combination on Maverick (gnome 2) sometimes but I can also use the  switcher on Cairo Dock.

Thanks!

---

### Post by mc4man on 2011-03-07
> But is there any way to use the switcher thing on the Unity bar to do that.
Atm or forever ?, no
While it's the same name (workspace switcher) as the applet in gnome-panel it is actually just a launcher for the expo plugin (super+e)
It's not interactive
If you open expo you can, among other things,  switch workspaces either by clicking, the arrow keys or scroll -  wheel or scroll area

---

### Post by mc4man on 2011-03-07
beew - 
there is a unity upgrade today (some interesting fixes), so be aware that the unityshell.xml will be replaced and the wall requirement will be back.

The require doesn't affect use, only enabling the unity plugin so nothing will change. Still, it's advisable to edit it back out in case the unity plugin gets unset for some reason...

---

### Post by beew on 2011-03-07
Thanks for the heads up!

---

### Post by beew on 2011-03-07
Just did the upgrade and rebooted, the cube is still there.

---

### Post by mc4man on 2011-03-07
> Just did the upgrade and rebooted, the cube is still there.
I might of been not so clear there - 
The unity plugin doesn't ck. against the requirements in the .xml after it's been enabled, only when enabling the plugin.

So if the .xml changes the enabled  unity plugin is 'unaware' so to speak, - 
 if for any reason you had to re-enable the unity plugin then it would ck. and if wall was again a require in the .xml the unity plugin would 'insist' upon enabling it and disabling cube which would then disable rotate.

---

### Post by beew on 2011-03-13
While works after hacking like mc4man instructed, the rotating cube looks odd in Unity, it just looks wrong and I suddenly realize what is wrong. The upper panel doesn't rotate along with the desktop (neither does the dock, but it is the upper panel that makes it look weird). So far the upper panel and the dock in unity are completely unmovable and have little customizability.

---

### Post by mc4man on 2011-03-13
> While works, the rotating cube looks odd in Unity, it just looks wrong ....
Both rotate (flip) and wall (slide)  only move the viewports, not the launcher (if exposed) or the bar.

So if wanting to switch viewports using any of the mouse/keyboard methods available w/ either i'd just use the one you like better.
If I was to use wall w/ 4 viewports would probably keep the 2x2 so it could go continually in one dir. or the other.

Here I use a transparent bar so  it doesn't bother me, didn't really anyway.
With the launcher now being resizeable am more inclined to leave exposed (never mode), though still like/use autohide.
Have set up a toogle switch so it's simple to switch between either mode.

---

### Post by beew on 2011-03-13
@mc4man

Which bar did you make transparent? How?

Thanks.

---

### Post by mc4man on 2011-03-14
I guess technically it is called 'Panel'
(happen to use a subdued darker desktop so the mono dark icons work well w/ the trans. panel

---

### Post by beew on 2011-03-14
Thanks.

---

