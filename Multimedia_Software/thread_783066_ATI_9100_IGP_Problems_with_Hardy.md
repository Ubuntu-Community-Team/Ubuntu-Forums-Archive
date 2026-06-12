---
title: "ATI 9100 IGP Problems with Hardy"
date: 2008-05-05
forum: Multimedia Software
---

### Post by Fusion_GTX on 2008-05-05
I have an ati 9100 igp video card which used to come up under the restricted drivers in Gutsy Gibbon and Feisty Faun. With this I was able to enable advanced desktop effects and such. Now that I upgraded to Hardy, I'm unable to enable any advanced effects.

Has anyone had any success with this card. Is there another thread that anyone can point me to. Any help would be appreciated. I've tried a few things on my own but most of those were fixes to Gutsy, not hardy. So if anyone has had any success with this card please let me know.

Thanks in Advance!

---

### Post by core on 2008-05-06
I just figured out the fix myself! Open the Console and run these two commands:

```

mkdir ~/.config/compiz
echo SKIP_CHECKS="yes" >> $HOME/.config/compiz/compiz-manager
```

And off you go! Reboot and visual effects are on.

It seems Radeon 9100 IGP got blacklisted by compiz, and we have to force compiz to ignore the blacklist.
And I guess it wasn't blacklisted yet by the time Gutsy got out.

Have fun!

---

