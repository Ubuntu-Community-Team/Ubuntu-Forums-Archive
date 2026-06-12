---
title: "Nvidia EN8600GT and CODE::BLOCKS"
date: 2007-09-02
forum: Multimedia &amp; Video
---

### Post by ekh on 2007-09-02
This is my first post at Ubuntu, a great forum.

I have recently converted from Mandriva, and been busy making everything work under Ubuntu.

I have 2 other computers running CODE::BLOCKS IDE installed with synaptic, they work as expected.

This problematic computer has an ASUS P5AD2 motherboard 
[http://www.pcper.com/article.php?aid=59&type=expert](http://www.pcper.com/article.php?aid=59&type=expert)

with an ASUS EN8600GT graphic card.
[http://www.asus.com/products.aspx?l1=2&l2=6&l3=514&l4=0&model=1642&modelmenu=1](http://www.asus.com/products.aspx?l1=2&l2=6&l3=514&l4=0&model=1642&modelmenu=1)

The default installation runs fine with the Nvidia card, except for the missing 3D support.

CODE::BLOCKS started here but about half way drawing the CODE::BLOCKS window it stopped, and I had to force close it.

I thought that installing the Nvidia driver would solve the problem.

I have just followed another thread and got the Nvidia driver  NVIDIA-Linux-x86-100.14.11-pkg1
installed, apparently successfully .

Now Varicad works with 3D :-), but...

CODE::BLOCKS just shows the Ubuntu time glass for a while, no window appears just a field at the status line, and then after 16 seconds it exits.

Any hints on this ?

---

### Post by ekh on 2007-09-03
This problem is not related to the Nvidia card, it works fine.

>codeblocks --safe-mode

shows the source of the error.

The thread below describes problems with a missing library Code::Blocks need, and a workaround, it works for me.

[http://forums.codeblocks.org/index.php?topic=6837.msg52408](http://forums.codeblocks.org/index.php?topic=6837.msg52408)

---

