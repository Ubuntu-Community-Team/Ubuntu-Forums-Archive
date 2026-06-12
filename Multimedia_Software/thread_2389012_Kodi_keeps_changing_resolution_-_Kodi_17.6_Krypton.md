---
title: "Kodi keeps changing resolution - Kodi 17.6 Krypton - SOLVED"
date: 2018-04-10
forum: Multimedia Software
---

### Post by adriaan4 on 2018-04-10
I installed Kodi on Lubuntu, but everytime I started using it my resolutionsettings were screwed. Maybe due to my 2012 HDMI receiver, I don't know.
I am running **Kodi 17.6 Krypton** on Intel NUC. 

Config;
Kodi on Intel NUC <--> connected to receiver with HDMI <--> connected to (old low resolution) TV
The Kodi used to be Isengard on a raspberry Pi, there I did not have the resolution issues. 

What I did (after many hours of search and trial and error):


[LIST]
[*]Your Kodi runs as a certain user, let's say kodi. Go to it's home directory 
[/LIST]
```
cd /home/kodi/.kodi/userdata
```

[LIST]
[*]Modify guisettings.xml 
[/LIST]

I deleted 37 resolution options out of the 38 options and modified the chosen option. That seemed to work.

```

    <videoscreen>
        <blankdisplays default="true">false</blankdisplays>
        <cms3dlut default="true"></cms3dlut>
        <cmsenabled default="true">false</cmsenabled>
        <cmsgamma default="true">220</cmsgamma>
        <cmsgammamode default="true">0</cmsgammamode>
        <cmslutsize default="true">6</cmslutsize>
        <cmsmode default="true">0</cmsmode>
        <cmsprimaries default="true">0</cmsprimaries>
        <cmswhitepoint default="true">0</cmswhitepoint>
        <delayrefreshchange default="true">0</delayrefreshchange>
        <displayprofile default="true"></displayprofile>
        <dither default="true">false</dither>
        <ditherdepth default="true">8</ditherdepth>
        <fakefullscreen default="true">true</fakefullscreen>
        <limitedrange default="true">false</limitedrange>
        <monitor>HDMI1</monitor>
        <noofbuffers default="true">3</noofbuffers>
        <preferedstereoscopicmode default="true">100</preferedstereoscopicmode>
[B]<!--    <resolution>36</resolution> this one I changed to -->
        <resolution>1</resolution>[/B]
        <screen default="true">0</screen>
        <screenmode>00144000576050.00000pstd</screenmode>
        <stereoscopicmode default="true">0</stereoscopicmode>
   
        
    </videoscreen>


<!-- Delete all nonsense 36 resolution options:  -->

        <resolution>
            <description>1440x480@ 60.00 - Full Screen</description>
            <subtitles>463</subtitles>
            <pixelratio>1.000000</pixelratio>
            <refreshrate>60.000000</refreshrate>
            <output>HDMI1</output>
            <xrandrid>0x146</xrandrid>
            <overscan>
                <left>0</left>
                <top>0</top>
                <right>1440</right>
                <bottom>480</bottom>
            </overscan>
        </resolution>

```

**Beware**: I also tried to changing permissions from ```
rw-rw-r
``` to  ```
r--r--r--
```, but that would kill kodi to auto-start on my system, so that I  needed to roll-back these modifications.

---

