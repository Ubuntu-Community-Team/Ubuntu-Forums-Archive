---
title: "Packaging libprojectm"
date: 2007-01-11
forum: Multimedia &amp; Video
---

### Post by ImNtReal on 2007-01-11
First of all, I'm new here, so I'm not sure that this should go here or in a dev catagory, or something.  However, I've been able to easily compile libprojectm, and have created a rpm for it on Fedora, but have been unable to create a deb.  It seems that it demands a package called ftgl, even when the only dependency that's listed is ftgl-dev.  Any ideas?  I'm thinking about re-packaging ftgl-dev, and addding Provides:  ftgl.

---

### Post by Sqwishy on 2007-01-11
When you compile you use the -dev files, but when you actualy use it you need the non-dev files. So for people using the deb package they don't use the -dev dependancys. I think this helps, i'm not quite sure what you are asking!

---

