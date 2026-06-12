---
title: "How to get Hugin to run"
date: 2008-09-04
forum: Multimedia Software
---

### Post by paltwo on 2008-09-04
I have Ubuntu 8.04 installed. I installed Hugin with Synaptic. When I have completed a panorama with some photos and wants to save it, Hugin crasches. I started Hugin from a shell and it says "Could not load pano13". With Hugin libpano12 is installed. I can't install libpano13 with the packet installer (downloaded a .deb). I get the error "Error: Dependency is not satisfiable: libpano13-0".

How do I get Hugin to work? 

Peter

---

### Post by buck2825 on 2009-06-16
not that it matters much now but, i have install and used hugin in 8.10 without any issues other than you must edit a single line. under file --> Preferences then Autopano tab in the Autopano-SIFT section the Arguments text box you need to enter the following

--output %o --points %p %i

I found this in another thread somewhere

good luck

---

