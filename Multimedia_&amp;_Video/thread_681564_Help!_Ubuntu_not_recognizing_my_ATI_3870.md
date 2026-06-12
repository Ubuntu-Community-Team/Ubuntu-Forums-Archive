---
title: "Help! Ubuntu not recognizing my ATI 3870"
date: 2008-01-29
forum: Multimedia &amp; Video
---

### Post by Adam_S on 2008-01-29
This is not my first Ubuntu install, but im having alot of trouble trying to get this to work.

i have looked through the stickies and none of them worked. I have tried to go through Restricted Drivers but it says they are not needed and closes. I went into Screens and Graphics and changed the default to Radeon, but that only gave me the error "Ubuntu could not recognize your graphics card and is now in low graphics mode" and locked my screen resolution into 800x600 and 76 refresh rate, which is very agonizing when i have a  1680 x 1050 resolution monitor.

I have the Radeon HD3870, and im pulling my hair out trying to get this to work >< really dont want to go back to vista :(

---

### Post by shavenlunatic on 2008-01-29
have you looked into downloading envy?

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)  (there is a deb file to download and run relating to which ubuntu version you have)

if you download and install it, you can run the app from Applications > System Tools.. and just simply select to remove ATI drivers then the option you require (install ATI driver, or something along those lines) and it should do all the setup for you automatically

and if X dies (or if a kernel update stops you from getting to X) you can run envy from the terminal

```
 envy -t 
```

and it will give you the same options, usually a re-install of the drivers after a kernel update works fine.


I don't use envy anymore as the restricted driver manager works fine with my new video card.. but it was a godsend when I had problems getting my video card working a while back... makes life nice and simple.. hope this helps!

---

### Post by Adam_S on 2008-01-29
Thank you for the links :D 

It helped to restore the resolution and refresh rate of my monitor, but unfortunately it did nothing on the graphics side. At least it doesn't seem like it did anything. I still cant use any of the Visual Effects in the Appearance window. Also, the windows, when dragged, create a trail and are laggy, which indicates the drivers were still not installed, guess i just got to wait for ATI to get off their asses and make some driver support :(

---

### Post by shavenlunatic on 2008-01-30
hmm, did you try walking through the

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) guide and looking through ubuntuguide.org?

if you try the guides, it would be a good idea use envy to remove the drivers it installed and start from scratch

---

