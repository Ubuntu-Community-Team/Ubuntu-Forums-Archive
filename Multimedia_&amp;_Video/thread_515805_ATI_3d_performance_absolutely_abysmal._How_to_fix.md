---
title: "ATI 3d performance absolutely abysmal. How to fix?"
date: 2007-08-02
forum: Multimedia &amp; Video
---

### Post by Ellipsys on 2007-08-02
Hello. I'm sure this is a variation of a question that is asked a lot, but a search and similar threads don't seem to provide the correct answers. 

I have the misfortune of a laptop with an ATI video card and I'd like to run 3d applications and play games in Kubuntu. The card is an ATI Mobility Radeon X600 64mb (128mb hyper memory, which I'd like to use if at all possible.  Some people tell me to just give it up, because it doesn't work. I wanted to ask the community if there was any way to get around this so I don't have to dual boot. 

My Kubuntu installed easily without having to do the manual driver install in the sticky. However, I couldn't get the resolution I wanted without upgrading to fglrx driver.  

If I try to run a 3d application, like Nexuiz or Planet Penguin Racer, the frames per second literally drop to 1 or less, even on a menu screen. Running GLXGEARS on the konsole has them turning incredibly slowly, despite it printing out they are at >100fps.  

I would really appreciate some help if someone was knowledgeable  about ATI.  I promise the next bloody laptop I get is going to have an nVidia card!

---

### Post by Ek0nomik on 2007-08-02
> **Ellipsys said:**
> Hello. I'm sure this is a variation of a question that is asked a lot, but a search and similar threads don't seem to provide the correct answers. 

I have the misfortune of a laptop with an ATI video card and I'd like to run 3d applications and play games in Kubuntu. The card is an ATI Mobility Radeon X600 64mb (128mb hyper memory, which I'd like to use if at all possible.  Some people tell me to just give it up, because it doesn't work. I wanted to ask the community if there was any way to get around this so I don't have to dual boot. 

My Kubuntu installed easily without having to do the manual driver install in the sticky. However, I couldn't get the resolution I wanted without upgrading to fglrx driver.  

If I try to run a 3d application, like Nexuiz or Planet Penguin Racer, the frames per second literally drop to 1 or less, even on a menu screen. Running GLXGEARS on the konsole has them turning incredibly slowly, despite it printing out they are at >100fps.  

I would really appreciate some help if someone was knowledgeable  about ATI.  I promise the next bloody laptop I get is going to have an nVidia card!

Did you end up upgrading to the fglrx driver?

I second your statement about glxgears being worthless.  I ran it last night on my fresh Fedora Linux installation which doesn't have any drivers installed and it spat out over 200 frames per second.  :/

---

### Post by Ellipsys on 2007-08-02
Yes, I installed it per the sticky, except I got the package with Adept instead of Apt-get.   If I go under my monitor settings it reports its using the fglrx driver instead.  Does that mean its working in both 2d and 3d applications? Or is there somewhere else I have to tell it to assume command of 3d?

---

### Post by prodezigner on 2007-08-02
Glxgears on a correctly setup 3D card should be spoutin' THOUSANDS of FPS...

On my little puny Intel GMA950 card it's almost 1,000 by itself, my dad's GeForce 6100 is spoutin' *almost* 2K frames a second... and God knows what my GeForce 7600GT would give me...

I use to have an old ATI card, gave me problems, but that was YEARS ago... so I can't really offer any insight on what's going on.

---

### Post by ajgreeny on 2007-08-02
Are you getting 3D at all?  Try **glxinfo** in terminal and see if you get **direct rendering: Yes** near the top of the output.  If not then no 3D.

---

### Post by Ellipsys on 2007-08-02
> **ajgreeny said:**
> Are you getting 3D at all?  Try **glxinfo** in terminal and see if you get **direct rendering: Yes** near the top of the output.  If not then no 3D.

Direct Rendering = No

Also everything pertaining to OpenGL says "Mesa" GLX Indirect or whatnot. I asssume that's bad...

Also, there's a "Xlib: extension "XFree86-DRI Missing on Display 0,0"

---

### Post by Ek0nomik on 2007-08-02
> **Ellipsys said:**
> Direct Rendering = No

Also everything pertaining to OpenGL says "Mesa" GLX Indirect or whatnot. I asssume that's bad...

Also, there's a "Xlib: extension "XFree86-DRI Missing on Display 0,0"

[http://wiki.cchtml.com/index.php/Verifying](http://wiki.cchtml.com/index.php/Verifying)

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

---

