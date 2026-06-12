---
title: "Seem to have tried it all.."
date: 2012-01-18
forum: Multimedia Software
---

### Post by shadeaux83 on 2012-01-18
I have searched Google and forums for so long now.  Nothing seems to be doing the trick for me with this even though there seems to be a lot of other people that suggestions I've found have worked for.

In Ubuntu 10.10 my System -> Preferences -> Sound is missing.
gnome-media says it is already the newest version.
I've tried reinstalling gnome-media, and gnome-control-center for the gnome-sound-properties package.

I've had sound problems with Pulse for over a month now and finally in the last day or two got everything sound related working again, with the exception of this....which leads me to an issue I think this is related to as well.

My keyboard volume controls are adjusting the wrong sound device and I can't find a way to change which it looks at and everything points you to System -> Preferences -> Sound..which is still missing.

Any help would be greatly appreciated.  Thanks :)

---

### Post by Paddy Landau on 2012-01-19
The only thing you appear to have missing is the actual menu item.

Unfortunately, I don't have 10.10, so I don't know what the menu item should read. Try this:

[LIST]
[*]Open your menu editor (as I recall, it was System > Preferences > Main Menu or something like that).
[*]Find the Preferences section.
[*]See if the Sound entry is still there, but disabled. If it is, enable it.
[*]Otherwise, you can create a new entry. As I say, I don't remember the name of the application, but on my computer (11.04) it is gnome-volume-control.
[/LIST]

---

### Post by MoreOrLess on 2012-01-19
> **Paddy Landau said:**
> Open your menu editor.

YOu can also use this command to do that:
```
alacarte
```

---

