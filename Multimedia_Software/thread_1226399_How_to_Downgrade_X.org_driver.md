---
title: "How to Downgrade X.org driver"
date: 2009-07-29
forum: Multimedia Software
---

### Post by awbranch on 2009-07-29
Hi,

I'm developing a screen capture program that works just fine on 8.04 but has large black blotches in the screencaptures in 8.10 and 9.04. Programatically, its grabbing screen shots using XLib. 

All versions are running on VMWare Fusion on OSX and so the have identical virtual hardware. The main difference seems to me to be X.org video driver:

8.04 - Vendor: The X.Org Foundation: Display Version 1.4.0.90
8.10 - Vendor: The X.Org Foundation: Display Version 1.5.2
9.04 - Vendor:  The X.Org Foundation: Display Version 1.6.0

First off, I assume those version numbers are for the driver version. I got this info from the app "hardinfo" 

I'm thinking that downgrading 9.04 to the driver X.Org that shipped with 8.04 would be a good test, but need some direction on how to do this.

Thanks in Advance
Andrew Branch

---

### Post by igorzwx on 2009-07-29
Just an experiment with Google
[http://www.google.com/search?hl=en&q=ubuntu+How+to+Downgrade+X.org+driver&btnG=Search&aq=f&oq=&aqi=](http://www.google.com/search?hl=en&q=ubuntu+How+to+Downgrade+X.org+driver&btnG=Search&aq=f&oq=&aqi=)

---

### Post by igorzwx on 2009-07-29
I may try this:
[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

---

