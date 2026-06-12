---
title: "OK, I have a really weird problem playing videos..."
date: 2007-07-09
forum: Multimedia &amp; Video
---

### Post by hyrule_man on 2007-07-09
OK, I've installed Ubuntu 7.04 many times, but this is the first time this has happened. Whenever I try to play any video, on any media player (VLC, Totem, MPlayer, etc..), the player crashes and closes out. I have the Automatix multimedia codec pack installed.... So WTF? :confused:

---

### Post by hyrule_man on 2007-07-09
Anyone?

---

### Post by Master Orion on 2007-07-09
First a couple of questions:  Your post states that you've installed 7.04 many times, is this a new install on a machine that previously ran just fine or is this an install on a new system?  Either way, what're the specs on the system?

First instinct to a solution for you without that info: automatix loves to install all the new codecs (in particular gstreamer plugins from the ugly set) that haven't been completely tested.  It's nice that they automatically add the new stuff, it's just annoying that it tends to not run as well on the plugins from the "good" set.

You might want to try steering away from automatix (if only in regard to the codecs) and use your package manager (synaptic or adept) to install the codecs manually.  Most likely that'll fix your problem.

Hope that helps!

---

### Post by hyrule_man on 2007-07-10
I've installed it on THIS machine easilly 5 times.... So I doubt the specs matter. And is there like a codec pack or something I can dwnload..?

---

### Post by hyrule_man on 2007-07-10
Bump.

---

### Post by hyrule_man on 2007-07-10
>_< >_< >_< Bump >_< >_< >_<

---

### Post by RomeReactor on 2007-07-11
Hi. If you have Beryl or Compiz (Desktop Effects), try disabling them and then try to open a video application from the terminal (Applciations->Accessories->Terminal), by entering the name of the player (**totem, gmplayer**  or **vlc**); once the player opens, use its menu to open a video and, if the application crashes, post here the error messages left in the terminal.

---

### Post by Bablefish on 2007-07-11
Not to sound dum here but did you install Medibuntu BEFORE installing Automatrix?  Also have you installed the GS Streamer plugins through Add/Remove?

---

### Post by crackling on 2007-07-11
> **RomeReactor said:**
> Hi. If you have Beryl or Compiz (Desktop Effects), try disabling them and then try to open a video application from the terminal (Applciations->Accessories->Terminal), by entering the name of the player (**totem, gmplayer**  or **vlc**); once the player opens, use its menu to open a video and, if the application crashes, post here the error messages left in the terminal.

I was having the same problem, but my video plays flawlessly if I switch the window manager back to Gnome. Does anyone know how to get the videos to play while still running Beryl as a window manager?

---

### Post by RomeReactor on 2007-07-11
> **crackling said:**
> I was having the same problem, but my video plays flawlessly if I switch the window manager back to Gnome. Does anyone know how to get the videos to play while still running Beryl as a window manager?

Hi. Try the scond post from [this thread]("http://ubuntuforums.org/showthread.php?t=485410").

---

### Post by crackling on 2007-07-11
> **RomeReactor said:**
> Hi. Try the scond post from [this thread]("http://ubuntuforums.org/showthread.php?t=485410").

Strange, I'm using Gstreamer and the video test works fine, but it still refuses to play my videos.

---

