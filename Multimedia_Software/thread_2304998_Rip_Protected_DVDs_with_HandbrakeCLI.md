---
title: "Rip Protected DVDs with HandbrakeCLI"
date: 2015-12-01
forum: Multimedia Software
---

### Post by mark bower on 2015-12-01
Using Ubuntu 15.04, Gnome Classic desktop

I want to rip some DVDs, using HandBrakeCLI, which do not boot normally.  That is, "Places" does not see them and they cannot be run as a file in VLC.  They can be run in VLC by opening as a disc, choosing "No DVD menus", then click Play.

I believe I have all the necessary libraries installed for HandBrakeCLI and have completed the checklist given in the link below.  HandbrakeCLI has worked like a champ for a number of my DVDs.  I also set the region code to "1" on the DVD drive via the Regionset app in the Software Ctr.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

What would be the code I need for ripping in HandBrakeCLI that will operate like VLC and ignore the constant scrambling system (CSS) menus in VLC?  I presume this is possible.

Including the parameter "--main-feature" in the complete handbrakeCLI command, I get the following for DVDs "Gone With The Wind" and "Whale Rider":

```
OpenCL:  library not available
dvd:  not a dvd - trying as a stream/file instead
hb_stream_open:  open /media/patty/GONE_WITH_THE_WIND failed
scan:  unrecognized file type
libhb:  scan thread found 0 valid titles
```

---

### Post by T.J. on 2015-12-02
First thing that you should probably know is that ripping protected DVDs is probably illegal in your country if it is a member of the World Trade Organization, and enforced by local laws.  In the United States for example, it does NOT matter if you bought the DVD or not.  The last court cases have pretty much said that ripping it to another format is a felony regardless because you are violating the the U.S. Digital Millennium Copyright Act when you bypass the protection to make a copy.  

Ubuntu does not come with the software necessary to bypass the copy protection, nor is it likely to ever do so, because that would probably make Ubuntu illegal to distribute in many countries.

---

### Post by QIII on 2015-12-02
The last is exactly why.  Being in the US, what you are discussing is clearly indicative of illegal activity, which is prohibited on the forums.

Closed.

---

