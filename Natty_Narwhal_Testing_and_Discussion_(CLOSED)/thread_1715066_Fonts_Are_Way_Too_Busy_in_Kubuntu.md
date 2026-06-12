---
title: "Fonts Are Way Too Busy in Kubuntu"
date: 2011-03-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2011-03-26
Anyone else having this problem? After I updated Kubuntu, I noticed that the fonts in all Qt apps (Dolphin, menus, etc) are all really dark bold and just a pain to look at. In fact, I tried to get used to it but started to develop eyestrain. (Literally). Do you think the Kubuntu devs will tone this down? The fonts are so large and dark that they take focus away from anything else in the window, even icons!

Also, I tried changing all the fonts back to the vanilla KDE defaults manually, but notice that the fonts look horrible with no anti-aliasing, even when I turn anti-aliasing on.

This is very important to me, as I do a LOT of writing. (Even Libre Office looks like garbage). Do you guys think this will be addressed before final release?

Edit: Forgot to mention I'm testing Kubuntu on a laptop with 1440*900 resolution.

---

### Post by Gavin77 on 2011-03-26
I'm running kubuntu natty and my fonts look fine to me.  
I notice you're using Nvidia and I'm on Intel, maybe it's a driver issue.

---

### Post by jlacroix on 2011-03-26
> **Gavin77 said:**
> I'm running kubuntu natty and my fonts look fine to me.  
I notice you're using Nvidia and I'm on Intel, maybe it's a driver issue.
My signature references my desktop. I'm using Kubuntu on my laptop, which uses an integrated intel video card.

---

### Post by ft_ on 2011-03-26
[https://bugs.launchpad.net/ubuntu-font-family/+bug/741813](https://bugs.launchpad.net/ubuntu-font-family/+bug/741813)

intel card for me too, but I'me really not convinced that it's related.
Played with systemsettings : Ubuntu font in font installer looks ok but not in appearence>fonts (eg. size 11 is bold but size 10 is normal).

---

### Post by Gavin77 on 2011-03-26
Ah, I see what you mean.  I use size 9 fonts so I didn't notice anything different.

---

### Post by ft_ on 2011-03-29
some news :
[http://kubuntuforums.net/forums/index.php?topic=3116117.0](http://kubuntuforums.net/forums/index.php?topic=3116117.0)
and I noticed that if I change font smoothing to RVB light, all becomes OK. Ubuntu light and medium behave like it should be. But in that way, firefox 4 shows font in a different way (a little bit thicker).
Medium or total smoothings do not seem to show ubuntu fonts properly (cf previous messages).

---

### Post by tghe-retford on 2011-03-29
I saw the same problem occur at the end of last week and still occurring now. KDE/QT applications have a much heavier look to their anti-aliasing whilst Gnome/GTK apps are unaffected.

---

### Post by ft_ on 2011-03-29
bug posted :
[https://bugs.launchpad.net/bugs/744812](https://bugs.launchpad.net/bugs/744812)

---

### Post by caryb on 2011-03-29
Very ugly with my NVidia card too:( Mind you it's better than some of the breakages in from the past!

Cary

---

