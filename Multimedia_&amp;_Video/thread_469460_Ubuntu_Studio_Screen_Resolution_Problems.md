---
title: "Ubuntu Studio Screen Resolution Problems"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by psesinkclee on 2007-06-09
I've been using Ubuntu Feisty Fawn on my laptop (IBM Thinkpad from 2000) for quite a while now.  I saw the awesome styling in Ubuntu Studio so last night I decided to try it out.  I backed up all my data and installed.  The installation went fine, but when I started it up for the first time The screen resolution was so large that I could only see the top left part of the screen; the bottom bar is not visible and the time on the top bar is not visible either.

I tried to modify the resolution settings and every other resolution other than the default 1024x768 (I believe) appeared scrambled.  

I've run the Update Manager and that hasn't fixed anything.  


Any help would be greatly appreciated.  I'm not to Linux-savy, so it would excellent if you all explain things in as deep detail as possible. :D

-Paul

---

### Post by NeoLithium on 2007-06-09
Do you know which video card that your computer has? It might be easier to install the proper drives, though if you don't, you can always try this first, to get in with a generic driver:

When you log in, use CTL+ALT+BACKSPACE to go out to a command line interface, and type:
```

sudo dpkg-reconfigure xserver-xorg

```
Answer the questions that you know the answers to, those that you don't, leave as default and then it should get you up without the crazy resolution.

---

### Post by trishacupra on 2007-06-10
If you're just after the Ubuntu Studio theme, and not everything else, you don't need to install Studio.

I just wanted the theme, and I even tried installing Studio, but had troubles with my screen resolution, too. Then I realised by reading another thread that I could install Feisty and then get the Studio theme, which is what I did.

The theme is totally awesome. Just search these forums for the commands to install the theme.

But if that's not the only reason, sorry I can't be of more help.

---

