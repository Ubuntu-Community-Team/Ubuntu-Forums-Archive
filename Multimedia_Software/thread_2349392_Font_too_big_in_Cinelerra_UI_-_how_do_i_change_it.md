---
title: "Font too big in Cinelerra UI - how do i change it?"
date: 2017-01-14
forum: Multimedia Software
---

### Post by acebone on 2017-01-14
How do I get a more normal font-size in Cinelerras UI? (my display 1920x1080)

[ATTACH=CONFIG]273195[/ATTACH]

---

### Post by phylsmith2004 on 2017-02-28
You can increase/decrease the size of the characters in the fonts and icons on your Cinelerra system.  This will make it easier to read the characters if you have trouble seeing the default small/big letters, which have been auto-scaled based on the window geometry. The user-friendly font/icon scaling default is 1. To defeat default auto scaling and get any size characters/fonts, override the setting via shell environment variables.  For example:
    export BC_FONT_SCALE=.5   ! half as big,

    export BC_ICON_SCALE=1.5 ! 1.5x bigger

---

