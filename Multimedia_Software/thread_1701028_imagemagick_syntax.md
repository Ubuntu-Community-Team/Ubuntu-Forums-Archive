---
title: "imagemagick syntax"
date: 2011-03-05
forum: Multimedia Software
---

### Post by DrPL on 2011-03-05
Hi,
I don't know if this is the correct place for this question; if not maybe a mod can move it to a new home....? I digress:

I'm experimenting with the imagemagick convert and mogrify commands. I have a lot
of png images that I would like to:
set "black" to being transparent
crop the image so that it is 60x108+124+40
and then resize to 25% of the original size.

I've tried the command: mogrify *.png -alpha set -resize 25% -transparent black -crop 60x108+124+40
but other than change the image size from 26.8 kb to 17.1 kb, it doesn't seem to do anything. 
Even when I re-order the commands into the sequence I'd like them carried out:
mogrify *.png -alpha set -transparent black -crop 60x108+124+40 -resize 25%
- nothing seems to happen.

Can anyone help?

Many thanks!

---

