---
title: "Ubuntu 10.10 and Tweak"
date: 2010-09-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by shadowfax1 on 2010-09-06
Running the 'beta' on my laptop and trying to get the closeout resizing buttons from the left to the right which 'tweak' allows you to do but for some reasons it won't install it.  I know its a 'beta' but just thought someone might have ran into the same problem  If I remember there's a terminal command that allows you to do it...I just forget what it is.
Thanxs

---

### Post by mcduck on 2010-09-06
Just press Alt-F2 (or use a terminal) and run *gconf-editor*. Use that to browse to apps/metacity/general and change the "button_layout" to "menu:minimize,maximize,close".

---

### Post by ajgreeny on 2010-09-06
gconf-editor will do it, but is not encouraged.  The better way, choosing a different theme with buttons on the right, and editing it, is shown for lucid in the stickies of the General section of the forum.  I assume it will be the same for maverick.
[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by mcduck on 2010-09-06
> **ajgreeny said:**
> gconf-editor will do it, but is not encouraged.  The better way, choosing a different theme with buttons on the right, and editing it, is shown for lucid in the stickies of the General section of the forum.  I assume it will be the same for maverick.
[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)
There is absolutely no reason to not use gconf-editor for such purposes. Hand-editing the gconf files, on the other hans, sure isn't encouraged. :D

Most of the options in gconff-editor are exactly the same options you have in your program settings and different configuration dialogs, and the ones that aren't available through such dialogs are absolutely safe to use as long as you red the description for the key you are editing and follow it's instructions about supported values.

Personally, I'd recommend gconf-editor any day over tools like Tweak. Far more options, and far better descriptions about what each option does.

The only reason why one might not recommend gconf-editor for this very purpose would be that the themes are able to change the button alignment on their own, but changing the gconf value doesn't break that feature in any way. The only thing is that editing the theme itself would of course be a more permanent solution for that exact theme (as switching between different themes might result in you having to change the button alignment again in gconf if the theme itself defines a certain alignment).

---

### Post by ajgreeny on 2010-09-06
Whilst I mainly agree with your comments, mcduck, I was simply passing on the info from the lucid sticky, and I quote:-
> **Using gconf-editor is not the right approach as this could bork  future themes. This change makes it easier for themes to do interesting  things with window borders.  Unfortunately, if the wrong approach  spreads, they won't be able to do that.**
It is therefore perhaps better to tell users what the developers are saying, rather than suggest ways which certainly work, but could cause later problems.

---

### Post by mcduck on 2010-09-06
Well, anything you do now could break things in future, if things change enough  :D

The truth is that at this point changing this gconf value doesn't break anything at all, and if the way themes work changes in future they'll really just have to do their changes in a way that works with the gconf without problems, or things are going to break regardless of if you touch this key or not (every single Metacity theme made this far would be broken, as the button layout isn't part of the Metacity themes apart from the hack used to make it work for the themes included in Ubutnu 10.04).

The button layout is something that users have always been able to configure to their own taste, independently from the theme used. Even Ubuntu's current solution for automatically switching the layout based on your theme respects this feature.

If you try changing between a theme that has the buttons on left and a theme that has them on right, you'll actually notice that changing the theme in the Appearance Preferences actually changes the button placement by using *exactly the same* gconf key. And the mechanisms is smart enough to ask you what you want to do if your setting is different than what the theme suggests.

---

### Post by overdrank on 2010-09-06
Moved to Maverick Meerkat Testing and Discussion

---

### Post by ronacc on 2010-09-06
> **ajgreeny said:**
> Whilst I mainly agree with your comments, mcduck, I was simply passing on the info from the lucid sticky, and I quote:-

It is therefore perhaps better to tell users what the developers are saying, rather than suggest ways which certainly work, but could cause later problems.

the best reason to use gconf-editor is that it sets the button order globally and does not depend on a particular theme . If you are using compiz and emerald you can also set the buttons there .

---

### Post by cariboo on 2010-09-06
I use gconf-editor to put the buttons on the correct side in gnome-shell, as by default they are on the right.

---

### Post by 23meg on 2010-09-06
> **ronacc said:**
> the best reason to use gconf-editor is that it sets the button order globally and does not depend on a particular theme .

If you know what you're doing, and it doesn't break your theme(s), it's safe to use it as a temporary kludge. But recommending it as *the* way to set button positions without proper explanation as to what it does is another matter.

---

### Post by ronacc on 2010-09-06
If you know of a theme that it breaks please let me know so that I can play with it , I have been setting my button position ( I always use close far left and min max far right ) for a very long time using both gconf-editor and emerald theme manager and have never noticed anything broken by it .

---

### Post by 23meg on 2010-09-06
> **ronacc said:**
> If you know of a theme that it breaks please let me know so that I can play with it , I have been setting my button position ( I always use close far left and min max far right ) for a very long time using both gconf-editor and emerald theme manager and have never noticed anything broken by it .

Any theme that assumes a particular button order in its design, and suggests it in gtkrc, is highly likely to look incorrect, such as the Equinox set of themes.

Somewhat luckily, when you select a different theme, the key should be set automatically again, and if the theme suggests a button order, gnome-appearance-properties should show an alert box (albeit with an ambiguous, tech-speak warning).

---

### Post by Stainesy on 2010-09-06
By the way Ubuntu Tweak 0.5.6 appears to be playing nicely with 10.10 beta.

---

### Post by Mr. Picklesworth on 2010-09-06
> **23meg said:**
> Any theme that assumes a particular button order in its design, and suggests it in gtkrc, is highly likely to look incorrect, such as the Equinox set of themes.

Somewhat luckily, when you select a different theme, the key should be set automatically again, and if the theme suggests a button order, gnome-appearance-properties should show an alert box (albeit with an ambiguous, tech-speak warning).

As the guy who wrote that (admitedly alarmist sounding) sentence now in the sticky, I should add something. First, 23meg is spot on as usual.

As for my worry of the &#8220;wrong&#8221; approach spreading: when we tell people to go change the button order directly in gconf editor, they'll come right back here wondering why it's back where it was after changing themes ;)

The point of this change is to make theming and button positioning a bit easier to deal with, and it undermines that to work against it.

---

### Post by ronacc on 2010-09-06
@ 23meg  , as promised I d/l'd and played with the equinox theme(s) . My custom button position did not "break" the theme , however the theme did as noted by Mr. Picklesworth break my custom button position , reseting them to proper ( close<>min max ) order showed no ill effects .

---

