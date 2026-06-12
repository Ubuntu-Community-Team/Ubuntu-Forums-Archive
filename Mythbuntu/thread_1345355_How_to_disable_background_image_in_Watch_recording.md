---
title: "How to disable background image in Watch recording."
date: 2009-12-04
forum: Mythbuntu
---

### Post by newbie02 on 2009-12-04
All,
I running mythbuntu 9.10. with Mythbuntu theme.
I havent figured out how to disable the background images 
which pops up for popular shows as you scroll through them in watch recording menu.

While at first I thought it was cool but after a while 
I find it a distraction and some images make it hard to see the text on screen and i would like to disable that feature. Just can not seem to find it.

Thanks
Newbie02

---

### Post by t3chn0b0y on 2009-12-04
> **newbie02 said:**
> All,
I running mythbuntu 9.10. with Mythbuntu theme.
I havent figured out how to disable the background images 
which pops up for popular shows as you scroll through them in watch recording menu.

While at first I thought it was cool but after a while 
I find it a distraction and some images make it hard to see the text on screen and i would like to disable that feature. Just can not seem to find it.

Thanks
Newbie02

I don't think there is an option to disable the fan art, I think it
is based on the theme you are using. If your using jamu, you could
set it up so it doesnt get the fan art when updating the information
to your videos.. that would be the only means I can think of, other
than changing themes. maybe use the retro wide updated theme? someone
more qualified might have a better answer..

---

### Post by Gimp_ on 2009-12-10
> **newbie02 said:**
> All,
I running mythbuntu 9.10. with Mythbuntu theme.
I havent figured out how to disable the background images 
which pops up for popular shows as you scroll through them in watch recording menu.

While at first I thought it was cool but after a while 
I find it a distraction and some images make it hard to see the text on screen and i would like to disable that feature. Just can not seem to find it.

Thanks
Newbie02

Hi,

From what I can see, you can disable the background images by commenting out a couple of lines in the /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml file.

Original:
```

      <imagetype name="fanart">
            <filename>background.png</filename>
            <area>0,0,1280,720</area>
            <preserveaspect>yes</preserveaspect>
        </imagetype>

```Modified:
```

<!--
         <imagetype name="fanart">
            <filename>background.png</filename>
            <area>0,0,1280,720</area>
            <preserveaspect>yes</preserveaspect>
        </imagetype>
-->

```

---

### Post by newbie02 on 2009-12-11
Thanks... My mythtv backend hard drive crashed :( so It will be a couple of days be for I can test this out. 
Thank you for the help.
Newbie02

---

### Post by red321 on 2009-12-11
I ended up moving Fanart from the theme, (as explained above), as I found the frontend was becoming unresponsive. Most of my TV shows dont have fanart, but that didnt speed things up. I guess the frontend was looking for non-existant fanart. Once it was gone, the recording screen became much more responsive.

I for one would like to see the fan art and previews "optional" as they were in older versions of Myth. But once you realize what the problem is, the fix is easy.

---

### Post by newbie02 on 2009-12-12
Thank you. That resolved my issue.
Newbie02

---

### Post by declanmullen on 2011-06-13
> **Gimp_ said:**
> 
From what I can see, you can disable the background images by commenting out a couple of lines in the /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml file.



Many thanks for this. I too found the fan art very annoying.

---

