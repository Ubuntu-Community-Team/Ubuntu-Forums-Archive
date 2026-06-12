---
title: "display on hdtv offset"
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by emjay on 2007-11-24
{edit}i've fixed the issue, or rather found a work-around{/edit}

Hi.

I'm hoping someone can help with my display problems.

I am running (k)ubuntu on a PC connected via VGA cable to my LG LCD TV.

THe problem I am having is that the display is offset off the screen. I need to move it right and down. The screen size appears to be correct, just in the wrong position!

I tried 'xvidtune' but i get back a message saying "video are not settable on this chip". The xorg.conf file has:
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "vesa"
        Monitor         "LG TV"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes          "1366x768"
        EndSubSection
EndSection

```

The ASUS motherboard I'm using has a built-in graphics adapter which isn't particularly exciting, but should work (in fact, <i>does</i> work, just in the wrong place!!)

Many of the forum posts I've seen suggest using the controls on the monitor to move the image, but I can't do this on the TV.

And, without wanting to whinge too much "it works in wondows"

The exact same offset is apparent in both kde and gnome, so it must be the x configuration tht needs to be modified, but i can't find anything which tells me that i cant set something like 
```

xoffset=250px
yoffset=50px

```

or similar, which is what i really need

Can anyone help??

Thanks in advance

---

### Post by clk99 on 2008-01-03
I have this same problem.  What was the workaround you found?

---

### Post by voca on 2008-01-05
Can anybody help with this?

---

