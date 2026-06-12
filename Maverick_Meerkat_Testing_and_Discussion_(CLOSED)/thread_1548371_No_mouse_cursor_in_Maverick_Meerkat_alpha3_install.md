---
title: "No mouse cursor in Maverick Meerkat alpha3 install"
date: 2010-08-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by dorutz on 2010-08-08
Hello!

Tested MM alpha 1 and aplha 2, everything worked great (minor glitches here and there, but hey, these are alpha releases).

Today I'veinstalled alpha 3 and neither in install or after I have no cursor!

Machine: IBM X40 with Intel 855 greaphics.

I mean, sure, I know the i8xx problems, but without a pointer, this is point...less :)

Any fix?

---

### Post by 4listair on 2010-08-10
I found this result also on "alpha-3" (actually a recent update of alpha-2). This was on a Dell D505 Laptop.

Although the mouse cursor is not visible, its underlying x,y location is honoured and changable, as normal, with mouse and touchpad movement. Button clicks are also honoured.

I reinstalled all prgs mentioning mouse/curser in Synaptic but no change.

dorutz, feel free to post the bug on Launchpad, if nobody has any suggestions. :)

Edit: This is also on 'normal' screen background settings, no Compiz or such. Changing the cursor design had no effect.

---

### Post by Catharsis on 2010-08-10
This is a known problem. You can follow its development at bug [lpbug]614176[/lpbug].

---

