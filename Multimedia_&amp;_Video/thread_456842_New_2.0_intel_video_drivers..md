---
title: "New 2.0 intel video drivers."
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by roger99 on 2007-05-28
I notice from [[COLOR="DarkOrange"]_this_[/COLOR]]("http://www.intellinuxgraphics.org/index.html") site that intel have released their new graphics driver with generally all round better support for their chipsets.  In particular the one thing that really annoys me is blue video when using the composite extension and either beryl or compiz, compcomm or whatever it is these days.....

I notice that in the repos there is ( i thnk anyway ) version 1.9.94 of this driver.  So my question is can this new 2.0 driver be built and used on feisty?

---

### Post by hikaricore on 2007-05-28
I don't see why it couldn't.  Although my past experience with compiling these drivers was a horrible failure.

Perhaps they've fixed their shotty script now?

---

### Post by roger99 on 2007-05-28
Well, that fills me with confidence :frown:.  Maybe, just maybe, somebody out there is compiling .deb's as I type.  ;)

---

### Post by tseliot on 2007-05-28
> **roger99 said:**
> I notice from [[COLOR="DarkOrange"]_this_[/COLOR]]("http://www.intellinuxgraphics.org/index.html") site that intel have released their new graphics driver with generally all round better support for their chipsets.  In particular the one thing that really annoys me is blue video when using the composite extension and either beryl or compiz, compcomm or whatever it is these days.....

The problem with the blue video can be solved by setting configuring totem, kaffeine or mplayer.

You will have to make them use the "xshm" (x11) video driver instead of "auto".

As regards **Kaffeine**:
1) open this file ~/.kde/share/apps/kaffeine/xine-config
get to the following section:
```
# Videodriver to use (default: auto)
# { auto  dxr3  aadxr3  xv  opengl  SyncFB  xshm  none  xxmc  sdl  fb  xvmc }, default: 0
#video.driver:auto
```

and make it look exactly like the following (note that I have also removed the # ):
```
# Videodriver to use (default: auto)
# { auto  dxr3  aadxr3  xv  opengl  SyncFB  xshm  none  xxmc  sdl  fb  xvmc }, default: 0
video.driver:xshm
```


you can do the same thing with **Totem**:
the configuration file is  ~/.gnome2/totem_config to use xshm deferred

NOTE: in Mplayer and Kaffeine you can set the xshm/x11 through the GUI without having to edit the configuration manually

---

### Post by roger99 on 2007-05-28
Well, that problem was easily solved.  Thank you.  No more switching back to metacity when I want to watch some video...... sweet :D  

I think I'm still gonna have a go at compiling those drivers at some point to see if I can get a bit of a performance increase, especially in the 3d department, my onboard graphics havn't got the best rep. in the world, hopefully those new drivers will help a little.

Any advice ... [[COLOR="Orange"]_This_[/COLOR]]("http://www.intellinuxgraphics.org/install.html") is their user guide for installing them, would I have to go through every step on feisty.  Or would agpgart and drm allready be present.  Sorry for the questions but that page baffled me a little when I skimmed over it....

---

### Post by tseliot on 2007-05-28
> **roger99 said:**
> [[COLOR="Orange"]_This_[/COLOR]]("http://www.intellinuxgraphics.org/install.html") is their user guide for installing them, would I have to go through every step on feisty.  Or would agpgart and drm allready be present.  Sorry for the questions but that page baffled me a little when I skimmed over it....
I suggest you don't try that unless you want to break your Ubuntu installation.

---

