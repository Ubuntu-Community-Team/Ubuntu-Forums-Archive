---
title: "Display problem on Ubuntu 10.04"
date: 2010-06-20
forum: Multimedia Software
---

### Post by hansum_rahul on 2010-06-20
Ubuntu 8.04 used to detect my display resolutions fine, but this version is unable to detect my max. resolution and I get lock-ups when I use the live disk without the "nomodeset" option.

My display config is:

**lspci | grep -i vga**

*00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)*

Detected resolutions (with nomodeset option):

[I]Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2048 x 2048
VGA connected 1024x768+0+0 (normal left inverted right x axis y axis) 267mm x 200mm
   800x600        85.1 +   85.1     72.2     75.0     60.3     56.2  
   1024x768       60.0* 
   832x624        74.6  
   640x480        85.0     75.0     72.8     75.0     59.9  
   720x400        85.0     70.1  
   640x400        85.1  
   640x350        85.1  
[/I]

The resolution 1152x864 is missed. This was a bug I had earlier reported on Intrepid (9.04).

My OS:

*Linux ubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux*

I downloaded this 2 days ago. Any help?

Also I was stumped at no kernel messages on any virtual terminal! How can I enable the printks?

---

### Post by Ehknaton on 2010-07-06
Hi, I have the same Graphics Device as yours, and I'm also curios if you'll get any responses. I encouter problems with my laptop, as sometimes the screen just goes "crazy". It flickers and flashed, some dots appear and dissapear. The only fix is to restart.

---

