---
title: "[SOLVED] Cinelerrra Install help...."
date: 2007-09-05
forum: Multimedia Production
---

### Post by mramsey on 2007-09-05
Hi I am wanting to install Cinelerra CV version but I am not sure which file to download. I have a Pentium D processor and not sure wich package to get. The following is from here [http://cv.cinelerra.org/getting_cinelerra.php]("http://cv.cinelerra.org/getting_cinelerra.php")

Ubuntu
Feisty Fawn | Edgy Eft | Dapper Drake 
Here are the Ubuntu packages repositories. Detailed instructions for installation can be found in the Manual.

7.04 Feisty Fawn
optimised for UbuntuStudio, with OpenGL, by Valentina Messeri:
deb [http://giss.tv/~vale/ubuntuopengl/](http://giss.tv/~vale/ubuntuopengl/) ./

for AMD64 (and also Core Duo Intel64), by Valentina Messeri:
deb [http://giss.tv/~vale/ubuntu64](http://giss.tv/~vale/ubuntu64) ./

for 64 bits with OpenGL disabled, by Valentina Messeri:
deb [http://giss.tv/~vale/ubuntu64NOopengl/](http://giss.tv/~vale/ubuntu64NOopengl/) ./

for i386, by muzzol:
deb [http://www.kiberpipa.org/~muzzol/cinelerra/feisty-i386/](http://www.kiberpipa.org/~muzzol/cinelerra/feisty-i386/) ./

for i686, by Jure Cuhalev:
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/) ./

for athlonxp, by Jure Cuhalev:
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/athlonxp/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/athlonxp/) ./

for pentium4, by Jure Cuhalev:
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/) ./

---

### Post by Amazona aestiva on 2007-09-05
See the second link in my signature.

---

### Post by mramsey on 2007-09-05
Should I use i686 or pentium4 with the Pentium D processor? I think it is the i686 but am not sure.

---

### Post by Amazona aestiva on 2007-09-05
Have you installed the x86 or the amd64 Ubuntu?
x86->i686
amd64->athlonxp

What type is pentuim D?
So...
pentiumD->pentium4 perhaps

Try pentium4. If it isn't the right, Try i686.
[COLOR="Red"]NO...[/COLOR] start with i686 i think.

---

### Post by mramsey on 2007-09-05
THanks...I will try it tonight when I get home. I will post the results.:)

---

### Post by Shlomir on 2007-09-05
Does the Prescott processor define as part of the P4 build?

---

### Post by mramsey on 2007-09-05
> **Shlomir said:**
> Does the Prescott processor define as part of the P4 build?

Not following you...are you asking about your processor or mine?  If mine pentium d is first generation duo core which according to wikipedia falls into the i686 category .

---

### Post by mramsey on 2007-09-06
Installed with 1 error not sure what to do...Please explain.

---

### Post by Amazona aestiva on 2007-09-06
[COLOR="RoyalBlue"]Solution 1:[/COLOR]
Login as ROOT and type:
```
echo "0x7fffffff" > /proc/sys/kernel/shmmax
```

[COLOR="RoyalBlue"]Solution 2:[/COLOR]
If don't want to login as root: [COLOR="Red"](I haven't tested this)[/COLOR]
Type:
```
gksudo gnome-terminal
```

A new terminal appears and type this into it:
```
echo "0x7fffffff" > /proc/sys/kernel/shmmax
```

---

### Post by mramsey on 2007-09-06
> **Amazona aestiva said:**
> [COLOR="RoyalBlue"]Solution 1:[/COLOR]
Login as ROOT and type:
```
echo "0x7fffffff" > /proc/sys/kernel/shmmax
```

[COLOR="RoyalBlue"]Solution 2:[/COLOR]
If don't want to login as root: [COLOR="Red"](I haven't tested this)[/COLOR]
Type:
```
gksudo gnome-terminal
```

A new terminal appears and type this into it:
```
echo "0x7fffffff" > /proc/sys/kernel/shmmax
```

Followed option #2 and it worked perfectly! No more errors!:guitar:

Thanks for the help!

---

### Post by Amazona aestiva on 2007-09-06
Congratulation!

Be lucky with Cinelerra... quite difficult, but powerful software!

---

