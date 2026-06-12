---
title: "Connecting to X Font Server"
date: 2008-05-01
forum: Multimedia Software
---

### Post by JasonRivers on 2008-05-01
Hi to all.

I am trying to set my Ubuntu system up to connect to a font server - the font server is running on a Suse 10.3 box, there is a couple of company orientated fonts we use, for example "dyalog std" if I execute:

fslsfonts -server fontserver:7100 |grep "dyalog std"

I get the following:

```

-misc-dyalog std tt-bold-i-normal--0-0-0-0-c-0-iso8859-1
-misc-dyalog std tt-bold-i-normal--0-0-0-0-c-0-microsoft-symbol
-misc-dyalog std tt-bold-o-normal--0-0-0-0-c-0-iso8859-1
-misc-dyalog std tt-bold-o-normal--0-0-0-0-c-0-microsoft-symbol
-misc-dyalog std tt-bold-r-normal--0-0-0-0-c-0-iso8859-1
-misc-dyalog std tt-bold-r-normal--0-0-0-0-c-0-microsoft-symbol
-misc-dyalog std tt-medium-i-normal--0-0-0-0-c-0-iso8859-1
-misc-dyalog std tt-medium-i-normal--0-0-0-0-c-0-microsoft-symbol
-misc-dyalog std tt-medium-o-normal--0-0-0-0-c-0-iso8859-1
-misc-dyalog std tt-medium-o-normal--0-0-0-0-c-0-microsoft-symbol
-misc-dyalog std tt-medium-r-normal--0-0-0-0-c-0-iso8859-1
-misc-dyalog std tt-medium-r-normal--0-0-0-0-c-0-microsoft-symbol

```

so it can see them, I have modified my xorg.conf so the section "Files" now looks like the following:

```

Section "Files"
        FontPath        "tcp/fontserver:7100"
EndSection

```

note: I have taken out all my local font paths. however:

"xset -q" shows the following:

```

Font Path:
tcp/fontserver:7100,/usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType

```


at this point you can have a look at the attached screenshot: you'll notice that the Dyalog STD font doesn't show up.

I'm a little confused for a number of reasons - first, my local font directories are still showing up - which is possibly a good thing if it can't get the fonts from the font server - but also because well, it can't get the fonts from the font server. 

if anyone knows how to setup the font server or has any idea why this might be happening (and yes i've tried restarting X)  then any help would be great.

Thanks.

Jason.

---

