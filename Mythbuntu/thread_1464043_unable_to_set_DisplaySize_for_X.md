---
title: "unable to set DisplaySize for X"
date: 2010-04-27
forum: Mythbuntu
---

### Post by alderion on 2010-04-27
all,

mythfrontend is display video in a very narrow vetical bar on my 1280x800 lcd laptop display.  on the mythtv forums someone had me run xdpyinfo which says that it thinks my display is:

screen #0:
  dimensions:    1280x800 pixels (289x21 millimeters)

so, i created an xorg.conf file and set DisplaySize to what i want a la:

   DisplaySize     325 203

in the monitor section.  the x log says it is using the xorg.conf but xdyinfo still reports 21m and mythfront end still displays squashed video.  can someone help me fix this?

thanks,

-peter

---

### Post by pu15e on 2010-04-27
You likely need to set the aspect ratio of your display in the Myth front end settings :-)

Cheers,
 Mattt.

---

### Post by alderion on 2010-04-27
yeah, i tried that.  as well as many of the options under the appearance settings page.  like i said, i ran it through the mythtv list and the answer was the dimensions that X is using are wrong.

thanks,

-peter

---

### Post by nickrout on 2010-04-27
try quoting the DisplaySzze parameters. Not sure if it should be:

```
DisplaySize     "325 203"
``` or ```
DisplaySize     "325" "203"
``` 

Try both and see if it helps.

Also what do tools like xdpyinfo and xrandr tell you?

---

### Post by alderion on 2010-04-28
> **nickrout said:**
> try quoting the DisplaySzze parameters. Not sure if it should be:

```
DisplaySize     "325 203"
``` or ```
DisplaySize     "325" "203"
``` 

Try both and see if it helps.

Also what do tools like xdpyinfo and xrandr tell you?

tried both your suggestions for DisplaySize and it borked x in both cases.  seems x *is* using my xorg.conf but the DisplaySize isn't getting set.

both xdyinfo and xrandr give the correct resolution of 1280x800 but the dimensions in millimeters is wrong on both: 325x21.

i had to boot a lucid live cd in order to fix the x config and interestingly, xdpyinfo in that session showed the resolution and dimensions as 1280x800/325x211 and xrandr showed 1280x800/325x21.  211 is still wrong though, i think.  i thought dimensions should be .254 times resolution.  i.e. 1280*.254 and 800*.254 or 325x203.

i wonder if i should move to lucid.  the issue is that i'd have to install myth from the karmic repos so that it matches my backend and then pin it so that it doesn't upgrade (pita).  stupid protocol issues.

thanks,

-peter

---

