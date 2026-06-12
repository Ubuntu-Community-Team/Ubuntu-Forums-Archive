---
title: "Maya2012 libtiff.so.3"
date: 2014-04-15
forum: Multimedia Software
---

### Post by john173 on 2014-04-15
[SIZE=7]Hi[/SIZE] [SIZE=6]There!<<!![/SIZE]):P):P
***[SIZE=4]<< [/SIZE]***_***[SIZE=4]Issue libtiff.so.3[/SIZE]***_***[SIZE=4] >>[/SIZE]***

I am searching this heck issue since one month i have read almost everyting but nothing made MAYA work 

Input :
user@user-desktop ~ $ ```
maya
```
Output :
```
[B]/usr/autodesk/maya2012-x64/bin/maya.bin: error while loading shared  libraries: libtiff.so.3: cannot open shared object file: No such file or  directory
user@user-desktop[/B] ~ $
```

I have made a link into the folder 
I have deleted the link ..Tried again with* "maya" command* still the same
Recreating the link ..Still nothing

I am waitings your magical instructions my **[SIZE=4]linux[/SIZE]** dudes

---

### Post by Yellow Pasque on 2014-04-15
What version of Ubuntu are you running?  If 13.10/Saucy, try this:
```
sudo ln -s /usr/lib/x86_64-linux-gnu/libtiff.so.4.3.6 /usr/lib/libtiff.so.3
sudo ldconfig
maya
```

---

### Post by john173 on 2014-04-16
I am using Linux Mint 16 "Petra"

The whole commands that you gave and answers that popped-up
```
user@user-desktop ~ $ sudo ln -s /usr/lib/x86_64-linux-gnu/libtiff.so.4.3.6 /usr/lib/libtiff.so.3
[sudo] password for user: 
user@user-desktop ~ $ sudo ldconfig
user@user-desktop ~ $ maya
/usr/autodesk/maya2012-x64/bin/maya.bin: error while loading shared libraries: libfam.so.0: cannot open shared object file: No such file or directory
user@user-desktop ~ $
```

So now the problem is :
```
/usr/autodesk/maya2012-x64/bin/maya.bin: error while loading shared libraries: libfam.so.0: cannot open shared object file: No such file or directory
```
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[SIZE=6]So[/SIZE] [SIZE=5][FONT=arial black]attention[/FONT][/SIZE] my fellas , this it's kindly simple go to your synaptic manager and find libfam0 mark it and then apply 


Now the only issue is to find the activation license code 
If you don't have(as I)you don't have any chance to run maya on linux as i only have found crack for windows OS and I can not activate the trial version either


Thanks for your support mate:p



If words like{crack} are not available correct me

---

