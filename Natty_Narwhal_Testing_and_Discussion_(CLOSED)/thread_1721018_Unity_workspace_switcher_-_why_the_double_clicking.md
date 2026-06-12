---
title: "Unity workspace switcher - why the double clicking?"
date: 2011-04-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Zorgoth on 2011-04-03
Why does clicking on a workspace once just highlight it in the unity workspace switcher.  As far as I can tell this achieves no practical effect.  I really wish a single click would just switch the workspace.  I don't like double clicking when single click doesn't do anything with a clear purpose...

---

### Post by ranch hand on 2011-04-04
The whole purpose of Unity is to entertain you with busy work.  Extra clicks are good.

---

### Post by rbrick49 on 2011-04-04
> **ranch hand said:**
> The whole purpose of Unity is to entertain you with busy work.  Extra clicks are good.
very good ranch hand

---

### Post by mc4man on 2011-04-04
> Why does clicking on a workspace once just highlight it in the unity workspace switcher
Never seen that here, all icons in the launcher respond to 1 click inc. the workspace switcher - 1 click should run the switcher (expo)
A second click would return to space/window with focus.

the app (favorite). icons can react to 1 or 2 clicks depending on circumstance, -  scale or focus - that may change soon depending on whether this commit is merged (and could change yet again, don't know

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/688117](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/688117)
(I've tried both recent commits - the last one is probably the more consistent

---

### Post by Zorgoth on 2011-04-04
OK I see what the idea is but it's still a wasted click - the only reason to click on the background of a workspace is to move to it, so why give it focus instead of switching to it immediately?  The final click on the workspace applet is wasted.

---

### Post by mc4man on 2011-04-04
> **Zorgoth said:**
> OK I see what the idea is but it's still a wasted click - the only reason to click on the background of a workspace is to move to it, so why give it focus instead of switching to it immediately?  The final click on the workspace applet is wasted.

You click on the switcher - expo appears
You have to click something to choose, usually  a d. left on space/window you wish to go to
Or do whatever else one may choose to do in expo - rearrange windows, change focus, open new windows, ect.
There is generally no need to click twice on the icon, though you can

( myself generally use 'scroll on desktop', flip,  or unfold to switch spaces - quicker than anything in unity OR gnome-panel

---

### Post by MacUntu on 2011-04-04
Left-click on the launcher = start expose mode.
Right-click on a workspace = switch to workspace.

It's probably not bound to the left-click because that can be used to drag windows around. Anyways, you can change it to your liking in the Expo plugin in CCSM.

---

### Post by beew on 2011-04-04
'Workspace switcher' in Unity is not a real  'workspce switcher'. It only exposes the desktops. A real workspace  switcher allows switching workspace with one single click (the  workspaces are already exposed) like the applet in the Gnome panel, AWN  or the Cairo Dock.

---

### Post by mc4man on 2011-04-04
> Why does clicking on a workspace once just highlight it in the unity workspace switcher.
Zorgoth - sorry - i misunderstood you - thought you meant you had to click  the workspace switcher _icon in the launcher twice_ to get expo

(and as mentioned by MacUntu a right click will immediately switch

---

### Post by MacUntu on 2011-04-04
> **beew said:**
> 'Workspace switcher' in Unity is not a real  'workspce switcher'. It only exposes the desktops. A real workspace  switcher allows switching workspace with one single click (the  workspaces are already exposed) like the applet in the Gnome panel, AWN  or the Cairo Dock.

IIRC there exists a workspace switcher indicator (check OMGUbuntu to find it). Press and hold the mouse button to open the indicator &#8594; choose workspace &#8594; release the mouse button: a "cheated" one click, but it's just one click. :D

---

### Post by Zorgoth on 2011-04-04
Well I suppose that's alright then - it could be engineered with both single click workspace selection and single-click drag and drop, but I guess I can just learn to right click.

---

### Post by aljazek on 2011-04-04
I just love that you have to double click, because you can move, close, open windows without really moving on that workspace. For me, absolute win!

---

### Post by reptilezone2002 on 2011-04-04
to tell u the truth guys the old gnome interface is better... unity is not good .. no desktop effects . may b ill just stick to the 10.10 for ever

---

### Post by MacUntu on 2011-04-04
> **reptilezone2002 said:**
> no desktop effects

Of course there are not desktop effects in Unity 2D. Unity 2D is supposed to be the choice of interface when your GPU can't do 3D acceleration, and if your card can't do 3D acceleration, then there's no compiz (desktop effects).

Install graphics drivers that enable 3D acceleration and use (the real) Unity.

---

### Post by lucazade on 2011-04-04
> **MacUntu said:**
> Of course there are not desktop effects in Unity 2D. Unity 2D is supposed to be the choice of interface when your GPU can't do 3D acceleration, and if your card can't do 3D acceleration, then there's no compiz (desktop effects).

Install graphics drivers that enable 3D acceleration and use (the real) Unity.

You can enable compiz in a Unity2D session, but there is not specific session to choose from login window

"compiz --replace" from terminal does the trick

or 

open gconf-editor
desktop/gnome/session/required_components/windowmanager
from metacity to compiz

---

### Post by ranch hand on 2011-04-04
> **MacUntu said:**
> IIRC there exists a workspace switcher indicator (check OMGUbuntu to find it). Press and hold the mouse button to open the indicator &#8594; choose workspace &#8594; release the mouse button: a "cheated" one click, but it's just one click. :D
That is a nice trick.

---

