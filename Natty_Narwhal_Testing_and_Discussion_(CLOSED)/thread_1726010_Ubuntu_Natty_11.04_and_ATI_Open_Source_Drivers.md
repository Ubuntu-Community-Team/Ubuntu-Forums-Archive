---
title: "Ubuntu Natty 11.04 and ATI Open Source Drivers"
date: 2011-04-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ahlidap on 2011-04-10
Hello,

I've a Laptop with an ATI X1250.
It works perfectly under 10.10 Maverick, with "modeset=0" and some changes in xorg.conf to eliminate glitches (that I've published here in the forum).



Now, in Natty it's a bit strange..
Using beta 1, with all updates, the Unity Desktop launches fine.
In glxgears, I only get something like 10.000FPS. Google Earth ok (slow)



If I disable KMS with the "modeset=0" trick, I get arround 335.881 FPS in glxgears, but the Unity Doesn't work..

It always get to the standard desktop, and google earth always tells that I'm not in DirectX mode..



In both cases "glxinfo" seems ok.
> name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4



Any ideas?
Thanks

---

