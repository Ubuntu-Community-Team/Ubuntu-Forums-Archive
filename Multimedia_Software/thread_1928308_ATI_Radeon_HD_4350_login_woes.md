---
title: "ATI Radeon HD 4350 login woes"
date: 2012-02-19
forum: Multimedia Software
---

### Post by thedrklion on 2012-02-19
First let me preface this with that  I am a relatively new Linux use and this my first post here so if I've done something keenly moronic feel free to point it out for my benefit but please bear with me . Also, I would like to add that I have found the ubuntu community forums (and various blogs) indispensable.
So in short, thanks for all the help this forum has already provided. Pleasantries over, on with the show.


My problem is relatively simple &#8211; when I connect my TV , a Sharp Aquos 42&#8221;,  to my newly built Home Theater PC running ubuntu 11.10, set to auto-login into Unity 3D, via HDMI and power on the PC the system attempts to log into Ubuntu and is promptly kicked out to the login screen (the screen where you can select the Ubuntu shell, e.g. unity 2D, unity, gnome &#8211; etc)
If I attempt to login again, into that same account the system is set to auto-login to, I am promptly kicked out again.

Here is the kicker, however, I can still login under a Guest account at any time and all is well.
The TV displays everything fine.
So I don't think it is a driver or hardware issue.
 But for good measure I will mention that my Video card is a  ATI Radeon HD 4350 (this is my hdmi out) with FGLRX drivers.


Also, when using a monitor &#8211; via DVI &#8211; I have no problems logging into any accounts or other video problems.


My theories include:
(1)Display setting are causing the problem: I think this because I was able to once log into the auto-login account but was not satisfies with the resolution. After tinkering in the display settings I was kicked out and have never been able to log back in.

(2)Compiz settings causing the problem: I tinkered here quite a bit when things were hooked up via DVI before I was ever tried hooking things up via HDMI, maybe its the OpenGL or something.

(3)Screenlets are causing the problem: I have some running on the auto-login account that autolaunch upon login.

(4)Unity launcher is the causing problem: I seem to have the unity launcher auto ahide problem others have complained about, where the launcher won't show unless you hit the super key


So, please- if anyone has any suggestions, help.
If there is some sort of log I can post simply point me in the direction of how to do so.

Update: I have managed to turn off the auto-login into my main account by connecting a  monitor via DVI. However, while the TV is being used as a display, either solely or in mirror mode with the monitor, the following shells will not grant me access but rather seem to kick me back into the login screen (GDM?): Unity, Unity 2d, Gnome, gnome classic, gnome classic (no effects). KDE, however, does allow me to login and recovery console does as well.
Odd thing is, the guest account can still access Unity no problem - have not tested others.

Since gnome classic does not grant access I assume it cant be a Compiz issue now and is likely a display settings problem.

Furthermore, I attempted to change the resolution settings in guest account under unity to see what would happen and a black screen resulted solved only by a reset. 

Help - pulling hair out.

---

