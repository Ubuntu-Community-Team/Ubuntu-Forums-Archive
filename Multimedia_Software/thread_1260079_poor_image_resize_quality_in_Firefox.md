---
title: "poor image resize quality in Firefox?"
date: 2009-09-07
forum: Multimedia Software
---

### Post by remi_2 on 2009-09-07
Hi, 

under firefox images look all jaggery/blurred/altered when scaled down, 

whereas under Opera 9.64 or 10.0 resized images look really sharp and clean.

Is there a way to configure the resize algorithm in firefox?

---

### Post by envis on 2010-12-24
im also noticing this, its annoying makes some of my site look less good that i would want. i looked for a solution that would be in the css but what i found doesnt seem to help:

> I discovered this new feature of FireFox:
[http://developer.mozilla.org/En/CSS/Image-rendering](http://developer.mozilla.org/En/CSS/Image-rendering)
So putting this in your CSS will fix it:
image-rendering: -moz-crisp-edges;
Thought I'd share this info. Sorry for answering my own question ;)

source: [http://stackoverflow.com/questions/388492/firefox-blurs-an-image-when-scaled-through-css-or-inline-style](http://stackoverflow.com/questions/388492/firefox-blurs-an-image-when-scaled-through-css-or-inline-style)

anyways i guess the best way to go is probably to use PHP GD to resize the images server side, usually GD always gives nice results in my experience im pretty sure that should work fine but its more work to setup!! thats what i plan to do whenever (if) i ever get the time!!

---

