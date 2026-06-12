---
title: "session resolution doesn't stick"
date: 2007-12-17
forum: Multimedia &amp; Video
---

### Post by Andy Sapuntzakis on 2007-12-17
Gutsy Gibbon, Gnome, BenQ FP202W (1680x1050), XFX 7600GT (OpenSource Driver)

The login screen is always at the native resolution, but as soon as I login, it switches down to 1280x1024. I can correct it using "Screen and Graphics Preferences" (S&GP), but the next time I login, it's back to the wrong settings.

The FP202W doesn't seem to be a pre-configured model in S&GP (how could I add it?), so I have "LCD Panel 1680x1050" selected.

I'm using the OpenSource driver, since choosing the vendor one doesn't seem to help.

The resolution it's auto-selecting is the "best-fit" if this were a 4:3 display. When I first installed Dapper Drake I had a 4:3 (Dell 2001FP, 1600x1200), but through all my updates I've been getting 1280x1024 on the BenQ. I'm very glad Gutsy introduced S&GP - I lived with "stretchy" desktop to avoid editing xorg.conf - but I'm still having this problem.

Thanks for any tips.

---

### Post by eth on 2007-12-18
have you tried setting your favourite resolution as defaut in /etc/X11/xorg.conf ?

---

### Post by Andy Sapuntzakis on 2007-12-21
i've tried to avoid editing xorg.conf because it's not reasonable to expect users to do so and it works around the problem rather than figuring out

- why it doesn't autodetect the display parameters
- why the settings stick for the login screen, but not the login session
- how to add a new display (to the gtk S&GP, not xorg.conf)

(typo in original post, the card is a 7600GS, not a GT)

---

