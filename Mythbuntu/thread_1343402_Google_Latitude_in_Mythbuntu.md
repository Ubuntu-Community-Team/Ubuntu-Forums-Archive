---
title: "Google Latitude in Mythbuntu"
date: 2009-12-01
forum: Mythbuntu
---

### Post by Singing Dwarf on 2009-12-01
I'm interested in the concept of putting a menu item onto the Mythtv menu, which would then display my latest location as a text string.

I'd also like to do a similar thing when a recording is being watched, mapping a remote control button to a script which will pass my location to the OSD.

Google Latitude provides an API, which passes the necessary information as a JSON or KML file, e.g.

[http://www.google.com/latitude/apps/badge/api?user=-4899040162740511709&type=json](http://www.google.com/latitude/apps/badge/api?user=-4899040162740511709&type=json)

I lack the necessary programming skills to do such a thing - I dont suppose anyone has done anything similar to this already?

I have Goog'd - and someone has done this on VDR, but not on Mythtv as far as I can see:
[http://dalelane.co.uk/blog/?p=991](http://dalelane.co.uk/blog/?p=991)

---

### Post by nickrout on 2009-12-01
I assume you are using a laptop? My myth setup stays exactly where I put it!

For display you probably want mythtvosd, great for "Come and get your dinner" messages :)

[http://www.mythtv.org/wiki/Little_Gems#mythtvosd](http://www.mythtv.org/wiki/Little_Gems#mythtvosd)

---

### Post by nickrout on 2009-12-01
A script something like this:

```
#!/bin/bash

PLACE=$(wget --quiet "http://www.google.com/latitude/apps/badge/api?user=-4899040162740511709&type=json" -O -|grep reverseGeocode|cut -d \" -f 4)
mythtvosd --template=scroller --scroll_text="Google thinks you are at $PLACE"

```

---

### Post by SiHa on 2009-12-02
Sorry to Hijack (a bit, anyway). Can mythtvosd be made interactive? I've been looking at a way I can put up a window saying "I'm going to shut down now" but with a "No thanks" button, I can select with my remote.

---

### Post by Singing Dwarf on 2009-12-02
> **nickrout said:**
> A script something like this:


Wow!  I wasn't expecting a script to appear - thanks very much nickrout!

I have tried it and the 'Google thinks' message scrolls across the screen - but it doesnt actually give a location....  I have checked the feed and that does provide a location.

---

### Post by nickrout on 2009-12-02
Try the individual commands at the commandline.  eg try ```
wget --quiet "http://www.google.com/latitude/apps/badge/api?user=-4899040162740511709&type=json" -O -
``` fist and see that the results look right, then pipe it through the grep command, then through the cut command.

It worked up to that point on my office computer, but I don't have myth at work so couldn't try the mythtvosd part.

---

### Post by Singing Dwarf on 2009-12-03
> **nickrout said:**
> It worked up to that point on my office computer, but I don't have myth at work so couldn't try the mythtvosd part.

Hi nickrout

Sorry, my bad.  For some reason the internet connection on my mythbox has failed - not 100% sure of the reason.  Your script works spot-on from my ubuntu desktop.  Thank you very much for your help!

Chris

---

### Post by nickrout on 2009-12-03
my script isn't that good, it should more gracefully cover the failure to connect to the api - as you have doscovered!

---

### Post by vladigor on 2009-12-09
Hi,
I thought I'd use nickrout's script as a starting point to teach myself a bit of bash scripting.  Attached is my expanded script.

It has a few configuration options you'll to set at the top such as your name, home location (so that it doesn't update when you're at home) and an expiry time (so that it doesn't update you when your location info is stale).  I've also added a toggle that allows it to only update if your location has changed since last time.

I envisage the script to be run from a cronjob - you'll probably want the script's expiry time setting to be the same as the cronjob running frequency.

Also, running the script by hand with --debug should show you what's going on and hopefully enable you to tweak it further to suit your needs.

---

