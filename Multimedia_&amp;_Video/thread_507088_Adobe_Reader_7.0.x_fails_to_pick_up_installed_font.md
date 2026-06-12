---
title: "Adobe Reader 7.0.x fails to pick up installed fonts"
date: 2007-07-22
forum: Multimedia &amp; Video
---

### Post by wolframarnold on 2007-07-22
I noticed that Adobe reader ([FONT=Courier New]acroread[/FONT] package, installed from [Medibuntu]("https://help.ubuntu.com/community/Medibuntu")) does not pick up all the installed fonts and substitutes fonts silently.

If your PDF document looks shotty, go to File -> Document Properties -> Fronts and check if the listed fonts match the actual fonts.

In my case a bunch of Windows fonts, e.g. Verdana were being substituted, although I had them installed on the machine (via package [FONT=Courier New]msttcorefonts[/FONT]).

I found a hint in the Adobe Reader's help section searching for "fonts," that the [FONT="Courier New"]PSRESOURCE[/FONT] environment variable has to be set to the font paths on the system.  A further web search pointed me to [this Adobe forum]("http://www.adobeforums.com/cgi-bin/webx/.3bc4142e").  The discussion seems to indicate that Adobe Reader is supposed to pick up the font paths from the X fontserver or from xorg.conf directly, but there are issues that are being resolved and future versions may not need the following workaround any more.  What I did and worked was to set [FONT="Courier New"]PSRESOURCE[/FONT] to all the paths listed in xorg.conf:
```

> grep FontPath /etc/X11/xorg.conf
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
```


and added these to [FONT="Courier New"]/etc/environment[/FONT] (for system-wide use both in X and shells):
```
PSRESOURCEPATH="/usr/share/fonts/X11/misc:/usr/share/fonts/X11/100dpi:/usr/share/fonts/X11/75dpi:/usr/share/fonts/X11/Type1:/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
```

---

