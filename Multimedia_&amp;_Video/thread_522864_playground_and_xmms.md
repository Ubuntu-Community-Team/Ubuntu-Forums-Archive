---
title: "playground and xmms"
date: 2007-08-11
forum: Multimedia &amp; Video
---

### Post by joekarl on 2007-08-11
Hey there.

I have installed playground 0.3, and am trying to get it working with xmms. The preferences of playground list the xmms plugin, but the controls have no effect. I'm sure I'm doing something simple wrong, but I can't find any docs/FAQ about how to use playground. Can somebody help me?

Thanks,

Joseph.

---

### Post by optim on 2007-08-11
This problem is already on the buglist and there's also some instructions, how to install playground by compiling source code.

[https://bugs.launchpad.net/ubuntu/+source/playground/+bug/109744]("https://bugs.launchpad.net/ubuntu/+source/playground/+bug/109744")

But it doesn't work for me, i get

> configure: error: XMMS library not found

during compilation of playground-xmms.

---

### Post by joekarl on 2007-08-11
Alrighty, after a bit of messing around, I found an old version of gxmms which is now working well. The only other thing I want to do now is to remove the minimized version of xmms from the bottom panel, leaving only gxmms as the visible connection to xmms. Something was mentioned about disabling window decoration, but I don't know where to look. Can anybody help?

---

### Post by Ghazgkull on 2007-10-04
Did you find a version of gxmms which will install on Feisty? (If so, where?)

---

### Post by ouellettesr on 2007-10-24
Anyone figure out how to get around this bug yet? Im using gutsy and this app still has the same problem. Let me know thanks.

---

### Post by flamepanther on 2007-10-27
I'm having the same problem.  I was hoping this would be fixed for Gutsy

---

### Post by stanigator on 2007-10-27
xmms is no longer supported in gutsy. You may want to try audacious (very similar).

---

### Post by Vaderf on 2007-10-29
Hi,

Thanks optim for your link : I solve my problem with playground on Feisty.

> 
But it doesn't work for me, i get

[QUOTE]configure: error: XMMS library not found
during compilation of playground-xmms.
[/QUOTE]

To solve this problem, it is necessary to install the pakage named **xmms-dev**

Thanks for all

---

