---
title: "Tried to fix DVD no-playback problem, things got worse."
date: 2008-09-12
forum: Multimedia Software
---

### Post by pjbolle on 2008-09-12
Hello. Allow me to preface this post by saying I followed the "pre-Heron" instructions in [this post]("http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+codec") (link isn't showing for me, so here it is just in case:  [http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+codec](http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+codec)) to the letter. Instead of fixing anything, it broke a bunch of things instead.

I use/prefer MPlayer, because if I try to run VLC fullscreen in Enlightenment, it bugs and I hafta kill it. Even if I go back to the default Gnome/Metacity, the problem is no different (except for the fullscreen VLC bit). I have also tried using a few other players; even Totem doesn't fare any better.

I also am forced to stay with Feisty (7.04), because upgrading to Heron completely mangled this HP Pavilion dv6325 -- broke ALL networking, left me in 640x480 max res, etc. I'm too afraid to upgrade beyond that unless someone can assure me the latest distro WILL work with this model of laptop.

I *have* gotten this all somehow working before on this model (after months of searching for answers), but I have little recollection of how it was done as it was a long time ago. All I recall is something about having all the right software sources for synaptic...

Having established all that, below are the details of what I hope someone can help me with. Please... Don't leave this unanswered so I'd have to leave Ubuntu for... *shudder* Vista... :(

Having followed the instructions in the post mentioned above, MPlayer got completely destroyed. I was forced to remove it, but I can't reinstall it now at all. I assume this error means I need another software source, but I can find no answers. Attempting a > sudo apt-get install mplayer results in the following:
```

The following packages have unmet dependencies:
  mplayer: Depends: libamrnb3 but it is not going to be installed
           Depends: libamrwb3 but it is not going to be installed
           Depends: libasound2 (> 1.0.14) but 1.0.13-1ubuntu5 is to be installed
           Depends: libatk1.0-0 (>= 1.20.0) but 1.18.0-0ubuntu1 is to be installed
           Depends: libc6 (>= 2.7) but 2.5-0ubuntu14 is to be installed
           Depends: libcaca0 (>= 0.99.beta13b-1) but 0.99.beta11.debian-2build1 is to be installed
           Depends: libcairo2 (>= 1.6.0) but 1.4.2-0ubuntu1.3 is to be installed
           Depends: libcucul0 (>= 0.99.beta13b-1) but 0.99.beta11.debian-2build1 is to be installed
           Depends: libdbus-1-3 (>= 1.1.1) but 1.0.2-1ubuntu4 is to be installed
           Depends: libdbus-glib-1-2 (>= 0.74) but 0.73-1 is to be installed
           Depends: libfaac0 (>= 1.26) but 1.24clean-0ubuntu4 is to be installed
           Depends: libfreetype6 (>= 2.3.5) but 2.2.1-5ubuntu1.2 is to be installed
           Depends: libfribidi0 (>= 0.10.9) but 0.10.7-4build1 is to be installed
           Depends: libgif4 (>= 4.1.6) but it is not going to be installed
           Depends: libgtk2.0-0 (>= 2.12.0) but 2.10.11-0ubuntu3 is to be installed
           Depends: libjack0 (>= 0.109.2) but it is not installable
           Depends: liblame0 (>= 3.97) but 3.96.1-2ubuntu1 is to be installed
           Depends: libncurses5 (>= 5.6+20071006-3) but 5.5-5ubuntu2 is to be installed
           Depends: libpango1.0-0 (>= 1.20.1) but 1.16.2-0ubuntu1 is to be installed
           Depends: libpulse0 (>= 0.9.8) but 0.9.5-5ubuntu4.2 is to be installed
           Depends: libvorbis0a (>= 1.2.0) but 1.1.2.dfsg-1.2ubuntu2 is to be installed
           Depends: libx264-57 (>= 1:0.svn20071224) but it is not installable
           Depends: zlib1g (>= 1:1.2.3.3.dfsg-1) but 1:1.2.3-13ubuntu4 is to be installed
E: Broken packages
```

The package libdvdcss2, which was installed before with no problems, now gives me this error when I try to install it:

```
The following packages have unmet dependencies:
  libdvdcss2: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is to be installed
E: Broken packages
```

On the DVD playing front, out of 20 or so legally owned Region 1 DVDs (and I have set the region on this player to exactly that, unless a complete reformat & reinstall of Ubuntu requires that to be done over?), only 2 have played (both "older" DVDs), the rest all have the same problem: MPlayer (or any video player) seems to lock up for about a minute, and then just goes back to normal, as if the playback was finished.

I have tried to play the individual .VOBs themselves, but *except* for the first one (the shortest, usually the production company's logo you see pre-film), the rest all fail as if I just tried to play the disc as normal (ie. "Open Disc").

The links, devices, and other kernel-level possible problems I have checked, and they all seem perfect. As mentioned above, I can mount and freely browse the DVDs, but not play any video on them. Also, the following command executes normally and shows only that things are up to date:

> sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade

If anyone can help, I would be immensely greatful. I sat down with intent to relax and watch a movie tonight. That was 5 hours ago, and I haven't seen so much as an opening credit. I'd pull all my hair out... if I had any. :-)

Thank you ever so much for any solutions you can give.,

---

