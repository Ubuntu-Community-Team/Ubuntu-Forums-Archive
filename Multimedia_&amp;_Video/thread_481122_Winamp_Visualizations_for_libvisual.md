---
title: "Winamp Visualizations for libvisual"
date: 2007-06-22
forum: Multimedia &amp; Video
---

### Post by Arasa on 2007-06-22
Dear All,

I was wondering if it was possible to repackage all the equations and presets in existing open source winamp visualizations for libvisual?

The reason is a visualization for winamp called Milkdrop - it is simply amazing and makes basically every single visual for linux such as libvisual or goom look so dated and crap.

Milkdrop is now open source, written in C but for DirectX. 

Thus I was wondering if we could simply borrow the mechanics of Milkdrop and transfer that over to AIGLX/similar based visual like libvisual. 

Views and opinions? Is this possible?

---

### Post by _profox on 2007-06-22
I think it is very hard to do, because DirectX is a completely different technology than OpenGL. AIGLX won't help you either, as that is just a rendering infrastructure to provide a composited environment (has nothing to do with what you want)

The only way that Milkdrop would work on Linux is that someone would completely rewrite it in OpenGL
And that's where luck comes in :) it just so happens that someone did that (I found that out through a Google search) it's called projectM: [http://xmms-projectm.sourceforge.net/](http://xmms-projectm.sourceforge.net/)

It supports libvisual, so you can easily use it in most audio players :) (amarok, xmms...)

---

### Post by Arasa on 2007-06-22
Thanks so so much.

So all I need to do is download and it will be included in libvisual? Or must I specify?

Also, Milkdrop is just so amazing, why dont more people use it? Why does everyone on these forums recommend libvisual 4.0?

---

### Post by _profox on 2007-06-22
> **Arasa said:**
> Thanks so so much.

So all I need to do is download and it will be included in libvisual? Or must I specify?
I don't know, I will try it out myself in a minute :)

> **Arasa said:**
> Also, Milkdrop is just so amazing, why dont more people use it? Why does everyone on these forums recommend libvisual 4.0?
I'll let you in on a little secret: ProjectM uses libvisual :) Libvisual is just a library (intermediate layer) between the audio application and the available visuals. Pretty cool huh. This makes it possible for every application that uses libvisual to use ProjectM (including, but not limited to, Amarok and XMMS)

---

### Post by _profox on 2007-06-22
What's your specific Ubuntu version? I'll try to create a package for projectm with checkinstall

---

### Post by Arasa on 2007-06-25
Thanks so much..

Sorry late post, internet down, British Telecom have the worst customer service..

I have ubuntu 7.04, feisty fawn. 

Perhaps make more people aware that they can add milkdrop to libvisual.

---

### Post by DarkMageZ on 2007-07-01
everytime some zombie uses checkinstall. god gives Bill O'Reilly more power to fight the lesbian gangs (in other words, don't do it).

in other news. i've already packaged libprojectm & libvisual-projectm for ubuntu feisty 7.04 i386.

add this repo if you want it
"deb [http://mirror.randumb.org/darkmagez/libprojectm](http://mirror.randumb.org/darkmagez/libprojectm) /"

"sudo apt-get install libprojectm libvisual-projectm"

Have Fun

---

### Post by diggity on 2007-07-01
Thanks **DarkMageZ**.
Works like a charm in amaroK. Are you going to add xmms-projectm?

---

### Post by DarkMageZ on 2007-07-01
i've built & uploaded xmms-projectm for ya. have fun.

---

### Post by diggity on 2007-07-01
Sweet! Thanks again!

---

### Post by punkrockguy318 on 2007-07-03
Hey, I'm running x86 feisty and I tried your packages.  The xmms one works fine, but I can't get the libvisual projectM to work in rhythmbox/totem (I have libvisual-projectM installed).

For some reason, when I go to the visulation list in rhythmbox/totem, I get GOOM and all of the libvisual-plugins plugins, but the libvisual-projectM plugin does not show up whatsoever.  Does anyone have any ideas?

Thanks

---

### Post by DarkMageZ on 2007-07-03
in your home directory there is a folder called .gstreamer-0.10
you may have to change the settings of your folder browser to allow you to see it.
if you close down rhythmbox/totem/anythingelsegstreamerbased and then rename that folder then start the desired application. this will force gstreamer to regenerate this folder with the new plugins.

this is a gstreamer/libvisual bug :(

have fun

---

### Post by punkrockguy318 on 2007-07-03
I've tried that.  I even completely logged off of X, and deleted the .gstreamer-0.10 directory.  When rhythmbox recreates the plugin list, only the GOOM and libvisual-plugin plugins appear :(  Do you have any other ideas?  I'm using the packages from your repository.

---

### Post by punkrockguy318 on 2007-07-03
When I remove the libvisual plugins and delete the registry file, all of the libvisual plugins are removed and only GOOM remains, no projectM.  When I reinstall the libvisual plugins, I get all the libvisual stock plugins but no ProjectM.  So it looks like gstreamer is ignoring projectM when it reubilds the registry.  Odd.  :(  It stinks using XMMS :(

---

### Post by DarkMageZ on 2007-07-03
oh, lol. /me slaps DarkMageZ.

projectM is an OpenGL visualization which gstreamer cannot handle yet.
totem & rhythmbox omit opengl plugins from their lists cause they WON'T work.
besides, amarok ftw :)

see [http://bugzilla.gnome.org/show_bug.cgi?id=310775](http://bugzilla.gnome.org/show_bug.cgi?id=310775)

sleep does wonders for the thinking

---

### Post by punkrockguy318 on 2007-07-04
Is there any way to go fullscreen with the xmms/bmp version? 

Also, is it possible to do hard cuts and soft cuts?  Or have playlists?   Or manually change the current visualization?  Can you do any of those things that you could do in the original milkdrop somehow?

---

### Post by punkrockguy318 on 2007-07-04
Also, is there any way to access your playlist and change the song like in the original?

---

### Post by DarkMageZ on 2007-07-04
i threw the projectm packages together just so i could have a look @ some more pretty patterns.
the projectm guys would have a much better idea about those sorts of things.

---

### Post by punkrockguy318 on 2007-07-04
> **DarkMageZ said:**
> i threw the projectm packages together just so i could have a look @ some more pretty patterns.
the projectm guys would have a much better idea about those sorts of things.


Well DarkMage, **you** are the man :popcorn::p:popcorn::p

I love me some daft punk and milkdrop :popcorn:

---

### Post by wconstantine on 2007-07-05
> **DarkMageZ said:**
> oh, lol. /me slaps DarkMageZ.

projectM is an OpenGL visualization which gstreamer cannot handle yet.
totem & rhythmbox omit opengl plugins from their lists cause they WON'T work.
besides, amarok ftw :)

see [http://bugzilla.gnome.org/show_bug.cgi?id=310775](http://bugzilla.gnome.org/show_bug.cgi?id=310775)

sleep does wonders for the thinking

So it doesn't work for rhythmbox?

---

### Post by DarkMageZ on 2007-07-05
> **wconstantine said:**
> So it doesn't work for rhythmbox?

correct

---

### Post by punkrockguy318 on 2007-07-05
Nope.  It doesn't work for anything that does visulizatiosn through gstreamer (totem/rhythmbox).  It only works for programs that support libvisual directly (amaroK)

---

### Post by wconstantine on 2007-07-05
> **punkrockguy318 said:**
> Nope.  It doesn't work for anything that does visulizatiosn through gstreamer (totem/rhythmbox).  It only works for programs that support libvisual directly (amaroK)

Aww,

---

### Post by kenjite on 2007-07-25
> **DarkMageZ said:**
> i've built & uploaded xmms-projectm for ya. have fun.
Thanks!!!!!!!!!!!

---

### Post by stercor on 2008-01-12
> **DarkMageZ said:**
> i've built & uploaded xmms-projectm for ya. have fun.
Where are the visualizations located?  I'm using Gutsy Gibbon (7.10) and sorely miss Milkdrop2

---

