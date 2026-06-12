---
title: "Multi Monitor on ubnuntu 11.10"
date: 2012-02-22
forum: Multimedia Software
---

### Post by Advente on 2012-02-22
sorry if this has been asked a few to many times but i reccently switched all my computers from windows :P to ubuntu..
 
I have a desktop with 3 montiors hooked up over 2 nivida graphic cards...
\What i need to configure is i need 3 montiors with th ability to have different windows opened on each and 3d support (or at the very least wine support).
 
I read osmeone who said nvidia realsed something called mosaic support or something?
 
Anyone able to help me configure this please?

---

### Post by wolfen69 on 2012-02-22
[http://askubuntu.com/questions/21144/how-do-i-get-three-monitors-working](http://askubuntu.com/questions/21144/how-do-i-get-three-monitors-working)

---

### Post by BicyclerBoy on 2012-02-22
Mosaic is only supported (by nVidia) on quadro video cards. The quadro h/w is no different to consumer cards, just costs more..
nVidia twinview only supports (2) monitors so you have to leave one as a separate X screen or all (3) as separate....

Don't think that Xorg Xinerama will help because it breaks your openGL..

The multi-monitor experience with *buntu is just not as good as windows.

AMD eye-finity is probably as good as it gets with linux.

Separate X screens can easily do the things you desire but there is a learning curve.

---

### Post by Advente on 2012-02-24
Ok well that askubuntu link was borderline useless to me...
 
So far in my search ive heard issues that unity runs on one screen making the others useless?
 
I really dont wanan downgrade to 10.10 for montior support...
 
So what is the learning curve?
 
Im not gonna go back to a inferior OS ( such as windows) just cause theres new stuff to learn..

---

### Post by pqwoerituytrueiwoq on 2012-02-24
you can try using xdotool to move between separate x screens
i have used it to get a mouse from one screen to the next with dead space in between the screens
i figure if it can move my mouse like that maybe it can move a window (happy bash scripting)
[http://manpages.ubuntu.com/manpages/oneiric/man1/xdotool.1.html](http://manpages.ubuntu.com/manpages/oneiric/man1/xdotool.1.html)

i believe nouveau has better multi-screen support than the nvidia driver

---

### Post by BicyclerBoy on 2012-02-24
But the OP wants openGL GLX performance.

What does work is Gnome classic session or any other non-compiz desktop manager. Altho' compiz behaves on *buntu 10.04..
Gnome classic works well on 11.04.

Separate X screens allows you:
- to move mouse between screens.
- You get menus on each screen.
- Most apps stay on the screen they are launched from, but if the do not then you use a launcher script that exports the DISPLAY$ variable.
- No icons on 2nd screen.
- independent video modes/refresh rates 
- full openGL(X) VDPAU in sync on both screens

Disclaimer:
I'm biased & have not used multi-monitor with unity on 11.04/11.10.

---

