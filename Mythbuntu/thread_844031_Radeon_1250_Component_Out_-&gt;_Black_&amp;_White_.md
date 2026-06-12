---
title: "Radeon 1250 Component Out -&gt; Black &amp; White (well, Sepia)"
date: 2008-06-29
forum: Mythbuntu
---

### Post by dsbw on 2008-06-29
I'm sort of guessing no one will be able to help with this one but I'm going to post anyway in case others have similar issues.

OK, so I have my ATI-based mobo system set up and it works pretty well. (If I use the latest 8.6 drivers the myth menu gets jumbled, as noted elsewhere, so I'm using Envy and 8.47.3. I've had this problem with 8.5 as well, though, and maybe some of the earlier drivers.)

Curiously enough, despite recognizing that it's connected to a TV, the ATI Catalyst only offers PC-type resolutions, like 1024x768, 800x600, 640x480, etc.

But the main issue is that while the S-Video input works, the component-out produces only a sepia-colored picture. If I plug in the green by itself, I get a B&W image of the desktop, but the blue and the red just make a very mild noise if plugged in by themselves. If plugged in with the green plug, they make the picture more sepia-colored.

Oh, and, while booting, the BIOS logo and other pre-loaded imagery look to be correctly colored. :confused:

If anyone has any thoughts, I'm interested.

---

### Post by jlagrone on 2008-06-29
Take a look at this, I had the same problem with an nvidia card about a year or so ago.  

[http://www.fedoraforum.org/forum/showthread.php?p=721770#post721770](http://www.fedoraforum.org/forum/showthread.php?p=721770#post721770)


I know it the guide is for an nvidia card, but if I remember correctly, this was the most important part (along with making sure component out was enabled)
```
Option	    "AddARGBGLXVisuals" "True"
```

---

### Post by haneymike on 2008-06-29
> **jlagrone said:**
> Take a look at this, I had the same problem with an nvidia card about a year or so ago.  

[http://www.fedoraforum.org/forum/showthread.php?p=721770#post721770](http://www.fedoraforum.org/forum/showthread.php?p=721770#post721770)


I know it the guide is for an nvidia card, but if I remember correctly, this was the most important part (along with making sure component out was enabled)
```
Option	    "AddARGBGLXVisuals" "True"
```

Thanks a lot!  That link saved me after spending a week trying to get Myth to connect to my old HD set through component cables.  I was so frustrated I was about to abandon Myth, but now I'm back in business.

---

