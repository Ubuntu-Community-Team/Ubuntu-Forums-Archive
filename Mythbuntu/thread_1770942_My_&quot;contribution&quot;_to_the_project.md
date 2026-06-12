---
title: "My &quot;contribution&quot; to the project"
date: 2011-05-29
forum: Mythbuntu
---

### Post by bcg30506 on 2011-05-29
This is sad, but it's all I know how to do at the moment, and it fixes a bug introduced in the last set of upgrades yesterday.

I use the Blue Abstract theme in 0.24.1 and after doing the updates yesterday, the OSD for program info/browsing was truncating any channel number over 2 digits down to 1.  In other words, channels 700-710 all displayed as channel 7.  This is not good for WAF.

So I snooped around the osd.xml file for the theme in my ~/.mythtv/themes directory as it was installed via the Theme Manager as a downloadable theme, and found the lines to fix it.  It works great now for me on a 1920x1080 40" TV.

Lines 227-242 replacement:
[PHP]        <!-- channel number and name -->
        <textarea name="channum">
            <area>120,635,60,30</area>
            <align>left,vcenter</align>
            <multiline>no</multiline>
            <cutdown>yes</cutdown>
            <font>text_small</font>
        </textarea>

        <textarea name="callsign">
            <area>180,635,95,30</area>
            <align>left,vcenter</align>
            <multiline>no</multiline>
            <cutdown>yes</cutdown>
            <font>text_small</font>
        </textarea>
[/PHP]

Lines 646-661 replacement:
[PHP]        <!-- channel number and name -->
        <textarea name="channum">
            <area>120,635,60,30</area>
            <align>left,vcenter</align>
            <multiline>no</multiline>
            <cutdown>yes</cutdown>
            <font>text_small</font>
        </textarea>

        <textarea name="callsign">
            <area>180,635,95,30</area>
            <align>left,vcenter</align>
            <multiline>no</multiline>
            <cutdown>yes</cutdown>
            <font>text_small</font>
        </textarea>
[/PHP]
In both cases, I just made the channum field 30 pixels wider (from 30 to 60) and moved the callsign field over 30 pixels (from 150 to 180).

I hope this helps someone out.

---

