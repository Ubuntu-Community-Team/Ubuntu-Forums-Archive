---
title: "Why does compiz always forget the top bar of windows?"
date: 2010-06-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-06-10
A lot of times when i use compiz the top bar of windows the one with the close and minimize and maximize is missing and i need to use compiz --replace to fix it all the 
time.

Could it be because i use emerald? 

Thanks in advance.

---

### Post by Jordanwb on 2010-06-10
Do the window decorations suddenly disappear or are they always missing? If the former then compiz crashed, if the later then maybe the window decorations plugin is disabled (this seems unlikely). The compizconfig-settings-manager allows you to configure what plugins are enabled.

---

### Post by aviramof on 2010-06-10
It usually happen after restart the top bar is missing so i either use compiz --replace or the shortcut in applications-others but it is a bit annoying because it always happen when you most need the top bar options:confused:

---

### Post by wiebeest on 2010-06-10
> **aviramof said:**
> It usually happen after restart the top bar is missing so i either use compiz --replace or the shortcut in applications-others but it is a bit annoying because it always happen when you most need the top bar options:confused:

Same here, not always, but quite frequently Ubuntu desktop starts and there's no top bar for my windows. 
Seems to happen more frequently than earlier versions of Ubuntu. 

**_BTW:_** I fix it for a current session through ***compiz fusion icon*** --> and select ***reload windows manager***. 

But my question too is, why does this annoying thing happen anyways??

---

### Post by konqueror7 on 2010-06-10
you could try, using compiz-fusion, to set the rendering, to either 'indirect' or 'loose binding', this usually solve some problems regarding missing window decorations, try that and see if it works...:p

---

### Post by wiebeest on 2010-06-10
> **konqueror7 said:**
> you could try, using compiz-fusion, to set the rendering, to either 'indirect' or 'loose binding', this usually solve some problems regarding missing window decorations, try that and see if it works...:p

Here 'indirect rendering' and 'loose binding' are both allready enabled.... Weird....

---

### Post by aviramof on 2010-06-10
It's was already set as  'indirect' and 'loose binding' or both of them together don't seem to work so well it slow down the opening time of windows so i disabled both maybe this would help.

---

### Post by konqueror7 on 2010-06-10
are there errors or warnings when calling 'compiz --replace'?

---

### Post by clivejo on 2010-06-10
I have the same problem, sometimes after a reboot the title bars don't seem to load.  I use the "Reload window manager" and this fixes it.  Seems to be random, or I haven't seen any pattern.

---

### Post by wiebeest on 2010-06-10
> **clivejo said:**
> I have the same problem, sometimes after a reboot the title bars don't seem to load.  I use the "Reload window manager" and this fixes it.  Seems to be random, or I haven't seen any pattern.

Same here. What could cause it, since it seems random?

---

### Post by aviramof on 2010-06-11
> **konqueror7 said:**
> are there errors or warnings when calling 'compiz --replace'?

I just checked again and there is this:
```
compiz (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

```

I'll try again later and see if there is more errors that need reporting.

---

### Post by juliobahar on 2010-06-23
> **wiebeest said:**
> Same here, not always, but quite frequently Ubuntu desktop starts and there's no top bar for my windows. 
Seems to happen more frequently than earlier versions of Ubuntu. 

**_BTW:_** I fix it for a current session through ***compiz fusion icon*** --> and select ***reload windows manager***. 

But my question too is, why does this annoying thing happen anyways??

Same problem here and I do the same solution to fix it.

I have loose binging and indirect rendering both enabled. I will disable them and see.

Btw, I've noticed that they appear more often on my nVidia based graphic card more than that on my laptop with the intel graphics.

I personally don't know why

---

### Post by psyke83 on 2010-06-24
The problem is most likely a conflict between gtk-window-decorator and emerald.

When compositing is enabled, Ubuntu uses gtk-window-decorator as the default window decorator (which conflicts with emerald).

Instead of running "compiz --replace", maybe try "emerald --replace" to see if it has the same effect.

---

### Post by juliobahar on 2010-06-24
> **psyke83 said:**
> The problem is most likely a conflict between gtk-window-decorator and emerald.

When compositing is enabled, Ubuntu uses gtk-window-decorator as the default window decorator (which conflicts with emerald).

Instead of running "compiz --replace", maybe try "emerald --replace" to see if it has the same effect.

Well I do have emerald manager (or you might say themer) install but never used it. Yet, still decorations at times are missing!!

Will try emerald, after confirming it does happen with loose binding & indirect rendering disabled.

---

