---
title: "loading blender"
date: 2009-07-30
forum: Multimedia Software
---

### Post by JD1994 on 2009-07-30
due to issues with god knows what, when i load blender i am forced to load with a command line, i.e "john@john-desktop:~$ LIBGL_ALWAYS_SOFTWARE=1 blender-bin"

is there a way that i don't have to do this and when i click on 'applications>graphics>Blender' it will run the command line mentioned above automaticly?
Cheers
JD

---

### Post by vinutux on 2009-07-31
Alt+F2 and type **alacarte**

its a menu editor.....in graphicsection right click blender icon > properties > in Type select **application in terminal** on that dropdown menu...

---

### Post by ad_267 on 2009-07-31
Or just right click on the menu and select "edit menus", which will run alacarte.

---

### Post by JD1994 on 2009-07-31
that still doesnt fix the issue, because it then loads blender like normal and doesnt run the command line that i mentioned above!

---

### Post by vinutux on 2009-07-31
> **JD1994 said:**
> that still doesnt fix the issue, because it then loads blender like normal and doesnt run the command line that i mentioned above!
 y.....?

worked 100% sure....perhaps you didn't get that 

its is the same as you typing in terminal [COLOR="Red"]blender[/COLOR]....what is happening there is ....terminal open first and executing cammand blender.....so simple

---

### Post by JD1994 on 2009-07-31
> **JD1994 said:**
> command line, i.e "john@john-desktop:~$ LIBGL_ALWAYS_SOFTWARE=1 blender-bin"


that command line 'LIBGL_ALWAYS_SOFTWARE=1 blender-bin' runs blended in a different way from just using the 'blender' line.

but when i start up blender it loads from the terminal but with Command line 'blender' not the one mentioned before
i need it so it runs the command mentioned before
understand?
JD

---

### Post by vinutux on 2009-07-31
> **JD1994 said:**
> that command line 'LIBGL_ALWAYS_SOFTWARE=1 blender-bin' runs blended in a different way from just using the 'blender' line.

but when i start up blender it loads from the terminal but with Command line 'blender' not the one mentioned before
i need it so it runs the command mentioned before
understand?
JD

undeestood... sorry about confusion...

WOW....my xperiments worked......

here .....

1. Right click home folder and **create a new document**

2. Rename it **[COLOR="DarkGreen"]Tblender.run[/COLOR]**...or anything else..(but**[COLOR="Red"].run[/COLOR]** in end)

3. Right click file** > properties > Permission tab > enable aloow executing file as a program**

4. Double click file and select display (or right click and open with gedit)

5. Copy and paste your cammond there** LIBGL_ALWAYS_SOFTWARE=1 blender-bin** and save file...

6. Open alacarte menu editor > **right click Blender launcher > properties > in [COLOR="DarkGreen"]command[/COLOR] brows and select newly created .run file** (**Tblender.run**)


........DONE................


now you can launch it from menues.......:D:D:D


.

---

### Post by JD1994 on 2009-07-31
'My man' as Denzil Washington would say!
cheers mate runs perfectly
JD

---

