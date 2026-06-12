---
title: "Mythweather in wide-screen - maps are distorted"
date: 2010-01-01
forum: Mythbuntu
---

### Post by ubnewbie2 on 2010-01-01
When mythweather displays downloaded maps on my widescreen display the aspect ratio is wrong (stretched horizontally).

Any way to fix this?

---

### Post by azmyth on 2010-01-02
What does the very top line say when viewing the map: Static, Animated, etc? Let me know and I'll tell you how to fix.

---

### Post by ubnewbie2 on 2010-01-02
> **azmyth said:**
> What does the very top line say when viewing the map: Static, Animated, etc? Let me know and I'll tell you how to fix.

OK, thanks.  Actually, I have a screen for both static and animated, and in my case they convey quite different info.  I'd like to get both looking great, but particularly the static one, which shows me a radar of all rainfall in the area.

---

### Post by azmyth on 2010-01-02
Okay, it depends on what theme you use. Go to the theme directory you want to change and look for the weather-ui.xml. If it's not there you can edit the one in the default-wide directory. As always make a backup first before editing in case something goes wrong.

For static, go to line 437 or look for the following.

```
<window name="Static Map">

        <textarea name="smdesc" from="basetextarea">
            <area>0,90,1280,40</area>
            <multiline>yes</multiline>
            <align>allcenter</align>
        </textarea>
        <imagetype name="map">
            <area>55,144,1170,480</area>
        </imagetype>
    </window>
```

You'll want to edit this line

<area>55,144,1170,480</area>

the 55 is the x (left to right) starting point of the map, 144 is the y (top to bottom), 1170 is the width, and 480 is the height. Adjust each to your liking and then exit Weather and go back to see the changes.

Go to line 450 or look for

```
    <window name="Animated Map">

        <textarea name="amdesc" from="basetextarea">
            <area>0,90,1280,40</area>
            <multiline>yes</multiline>
            <align>allcenter</align>
        </textarea>

        <imagetype name="animatedimage">
            <area>55,144,1170,480</area>
        </imagetype>
    </window>
```

and edit this line <area>55,144,1170,480</area> like above which will probably end up being the same.

---

### Post by ubnewbie2 on 2010-01-03
Brilliant - worked perfectly!  Thanks heaps.

---

