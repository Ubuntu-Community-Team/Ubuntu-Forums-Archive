---
title: "fglrx works but weird...effects..."
date: 2006-06-30
forum: Multimedia &amp; Video
---

### Post by JavanBuddhi on 2006-06-30
hello everyone.  I just got fglrx working on my 9600xt! problem is...well a picture is worth a thousand words, so this is probably easier ....

[IMG]http://static.flickr.com/76/178279765_e98a82db57.jpg[/IMG]

i did it with this xorg.config 

please help me get rid of this!

btw i run 2.6.25-k7, and did a 8.26.18 intsall (fdrom the installer)

---

### Post by Patrick-Ruff on 2006-06-30
try
```
 
sudo dpkg-reconfigure xserver-xorg

```

try all the default options first.


if it doesn't help I have no idea, sorry.

---

### Post by JavanBuddhi on 2006-06-30
I do that.  Actually, I am thriled to get this far with the fglrx driver. To me it looks like some kind of overlay problem....

---

### Post by dave1507 on 2006-06-30
Thats the problem I've got! Please tell me if you fix it.

---

### Post by JavanBuddhi on 2006-07-01
btw, along with the above visual corruption, x freezes if i attempt to run glxgears

---

### Post by tommohawk on 2006-07-01
Difficult without the full information.  Post the output of glxinfo and fglrxinfo please and we might be able to help you more.

---

### Post by JavanBuddhi on 2006-07-03
[QUOTE=tommohawk]Difficult without the full information.  Post the output of glxinfo and fglrxinfo please and we might be able to help you more.[/QUOTE]

Sorry for both the late post and for not giving the information.  
I had to study for my midterms.

attached is the output of both fglrxinfo and glxinfo 

I am going to try removing the glx module ( i assume that this disables opengl)  and get back to all you guys.

Thanks for all the help

---

### Post by dave1507 on 2006-07-03
My system gives the same output as above and I have the same problems. I am using a Radeon X1600PRO 512mb, which is AGP.

---

### Post by JavanBuddhi on 2006-07-04
perhaps this is an agp issue?

btw to all who don't know, i can't use the ati driver, I have to use vesa.  I have a VIA KT400 board. perhaps, this problem might have something too do with VIA's AGPGART?

---

### Post by dave1507 on 2006-07-04
I can't use ATI either, I'm using vesa as well.

I have a 2.8GHZ P4 on an Asus P4SD-LA motherboard with 1GB of PC2700 RAM.

---

### Post by tommohawk on 2006-07-04
Strange - I had this problem some time ago but it was when I was playing around with Xgl.

Have you tried adding the following to your xorg.conf file

Option  "UseInternalAGPGART"  = "no"

If it is an AGP problem then this may help.  The line needs to be added in the device section where your overlay entries are.

---

### Post by tommohawk on 2006-07-04
Duplicate Post - Forum Error

---

### Post by JavanBuddhi on 2006-07-07
Hmm....I will try that....

---

### Post by EReckase on 2006-07-07
I had this same effect with the 8.25.18 drivers on my ATI Radeon Xpress 200M.  Falling back to the 8.24.8 drivers worked well.  I was unable to get the 8.26.18 drivers to get past the login screen, so 8.24.8 is my best friend right now.

---

### Post by JavanBuddhi on 2006-07-09
I will try that. I am sure that it is my best hope bacause those drivers worked very well in breezy for me.  The prev post (Option "Use....) didn't help.

---

### Post by JavanBuddhi on 2006-07-09
sorry for the noob type question...but...how did you get the 8.24.8 drivers on? They are not in the repo's....

---

### Post by tommohawk on 2006-07-09
> **JavanBuddhi said:**
> sorry for the noob type question...but...how did you get the 8.24.8 drivers on? They are not in the repo's....

You can download the 8.24.8 drivers here

[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27]("https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27")

Have a look at this thread for more information on how to get things working.

[http://www.ubuntuforums.org/showthread.php?t=197471&page=3]("http://www.ubuntuforums.org/showthread.php?t=197471&page=4")

Post back if you get stuck.

---

### Post by JavanBuddhi on 2006-07-11
Thank you so much for your help EReckase and tommohawk! I have wonderful acceleration now and i am locking in my fglrx version. Once again Thank You!

---

