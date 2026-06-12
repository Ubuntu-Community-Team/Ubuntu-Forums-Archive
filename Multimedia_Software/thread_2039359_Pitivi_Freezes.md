---
title: "Pitivi Freezes"
date: 2012-08-08
forum: Multimedia Software
---

### Post by Incarnadine on 2012-08-08
When I start to render my project, Pitivi appears to freeze at 0%. I waited about 10 minutes to see if the render would jump to 1%, but nothing :( I'm not sure what the problem is. Any advice?

---

### Post by valley1967 on 2012-08-08
you might want to try Openshot I'm not sure if they are planing on continuing pitivi at this point

---

### Post by Incarnadine on 2012-08-09
> **valley1967 said:**
> you might want to try Openshot I'm not sure if they are planing on continuing pitivi at this point

The only reason why I tried using Pitivi first is because it's suggested by Ubuntu at this link... [http://www.ubuntu.com/ubuntu/features/photos-and-videos](http://www.ubuntu.com/ubuntu/features/photos-and-videos)

I guess just because Ubuntu supports a program doesn't mean that it will work better than the others :confused:

Thanks for the help. I will give Openshot a try when I get a chance.

---

### Post by valley1967 on 2012-08-10
this is why i read reviews first then select

---

### Post by Adam_GUI on 2012-10-06
I had the same problem with pitivi arranging render time into infinity.
Xubuntu 12.04 pitivi from synaptic.

I headed over to their project page [pitivi.org]("http://www.pitivi.org/?") just to see if I was missing anything.

I ended up adding a gstreamer ppa and some gstreamer libraries.

Load up pitivi and try to import video? 
Big money! No whammies! Crash on import for media select!

A sad panda is me.

So, I purge pitivi from my system with apt-get and install from their source tarball.

Crash on media import.  I don't even have to click OK.  

Merely selecting a video causes a full program crash quit as it tries to load the interface to preview your selection in the side-bar.

That would be pitivi 0.15.2.

However, openshot and LIVES both work and run just fine.
It's a pity.  I loved pitivi in 11.10.

---

