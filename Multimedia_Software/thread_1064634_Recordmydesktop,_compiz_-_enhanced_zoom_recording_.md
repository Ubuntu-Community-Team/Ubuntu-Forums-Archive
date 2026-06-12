---
title: "Recordmydesktop, compiz - enhanced zoom: recording two mouse pointer"
date: 2009-02-09
forum: Multimedia Software
---

### Post by placidoaps on 2009-02-09
Hi all, 
 
I am using recordmydesktop. 
 
Everything works find except I am recording two mouse pointers when I zoom in "Compiz/Enhenced ZOOM"

[http://sites.google.com/site/chezplacide/inkscape]("http://sites.google.com/site/chezplacide/inkscape")
 
My parameters are 
 
Mouse behaviour [section]: 
- Sync Mouse - OFF 
- Scale the mouse pointer - ON 
- Dynanic mouse scale pointer - ON 
 
- Hide original mouse pointer - ON 
- Restrain the mouse to the zoom area - OFF 
- Mouse panning - ON 
 
considering that "Hide original mouse pointer" is OFF it souldn't record the mouse pointer that doesn't appear. 
 
Is there a work around? 
 
Thanks.

---

### Post by rajesh213 on 2010-06-23
[QUOTE=placidoaps;6703318]Hi all, 
 
I am using recordmydesktop. 
 
Everything works find except I am recording two mouse pointers when I zoom in "Compiz/Enhenced ZOOM"

[http://sites.google.com/site/chezplacide/inkscape]("http://sites.google.com/site/chezplacide/inkscape")
 
My parameters are 
 
Mouse behaviour [section]: 
- Sync Mouse - OFF 
- Scale the mouse pointer - ON 
- Dynanic mouse scale pointer - ON 
 
- Hide original mouse pointer - ON 
- Restrain the mouse to the zoom area - OFF 
- Mouse panning - ON 
 
considering that "Hide original mouse pointer" is OFF it souldn't record the mouse pointer that doesn't appear. 
 
Is there a work around? 
.................................................................
I typed this command shown below
 recordmydesktop --overwrite --fps 15  --on-the-fly-encoding -o test

 I zoomed my desktop ... I executed all the application of compiz desktop manager i.e. desktop cube ... everything is being shown on the recorded video saved in /home/user/test.ogv

---

