---
title: "svg command line tool"
date: 2011-02-05
forum: Multimedia Software
---

### Post by wolke on 2011-02-05
are there command line tools for manipulating {in particular, merging} svg files? quick googling hasnt turned up anything for me yet.


i need to merge objects from 2 svg files into a 2-layer or 1-layer svg file. i dont need to scale/move/manipulate the objects themselves. i need to do this for dozens of files. {im dynamically injecting text onto an icon set, for use where i need a single icon, and there is no support for using transparency}

i wrote a script to parse the defs and the paths and produce a file containing both, but its incredibly naive. {information was taken from looking at examples of what inkscape did when i pasted an object in, as opposed to researching the specs of svg}

it works MOST of the time.

some changes to the application im writing make the script no longer sufficient. im losing color information in gradients somehow or other.

i dont wanna fully implement merging with all the complexity of svg, when im sure smarter people have already done it. i could probably poke around the inner bits of inkscape and make a cli for some of the operations, but i was wondering if there is already a set of command line tools for manipulating svg.

---

### Post by wolke on 2011-02-05
oh, i can just stick everything under the root <svg/> tag, multiple <defs> and <path>s are allowed. thats easier anyway, but im still seeing gradients having the wrong color. odd, when i put the symbols behind the base, they work, and in front they dont. presumably its overlapping definitions.

im going to attach an example that shows my problem.


merged_sym_on_top.svg is green, which is different than the base.


note that the example i pasted are from two GPLed projects.
[http://xfce-look.org/content/show.php/Battery+status+Icons?content=93749](http://xfce-look.org/content/show.php/Battery+status+Icons?content=93749)
Authors: 
  Franck moi (coolaman)

Red plus symbol in a circle icon taken from wikimedia commons:
  [http://so.wikipedia.org/wiki/File:Nuvola_Red_Plus.svg](http://so.wikipedia.org/wiki/File:Nuvola_Red_Plus.svg)
Authors:
   Anomie
   David Vignoni

---

