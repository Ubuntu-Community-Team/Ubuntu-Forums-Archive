---
title: "How to install a plugin to GIMP"
date: 2022-07-20
forum: Multimedia Software
---

### Post by satimis on 2022-07-20
Hi all,

GIMP 2.10.32

I have the plugin "color_grading_v174.tar.xz" download on Ubuntu 20.40 desktop

johnlak gimp 
[https://sourceforge.net/projects/johnlakgimp/](https://sourceforge.net/projects/johnlakgimp/)

Whether performing following steps the plugin will be added to my GIMP 2.10.32 ?

On Ubuntu Terminal run;
$ tar -xf color_grading_v174.tar.xz
$ cd color_grading_v174
$ ./configure
$ make
$ sudo make install

Pls advise.  Thanks

Regards

---

### Post by Dennis N on 2022-07-20
Look at the README.txt file inside the archive. Just extract the files shown there from the .tar.xz archive into your Gimp plugins folder.

---

### Post by mIk3_08 on 2022-07-20
> **satimis said:**
> 
On Ubuntu Terminal run;
$ tar -xf color_grading_v174.tar.xz
$ cd color_grading_v174
$ ./configure
$ make
$ sudo make install

These are one of the steps on installation of a package. just follow the steps and make sure the location address of your execution. Regards and cheers.

---

### Post by satimis on 2022-07-20
> **Dennis N said:**
> Look at the README.txt file inside the archive. Just extract the files shown there from the .tar.xz archive into your Gimp plugins folder.
Thanks for your advice.

It took me a while before I can read the README.txt file.  I couldn't read it online.  I must download it to read.

According to the document```

FILES TO COPY:

For normal installation copy:
color_grading_cw_v174.py
colorwheel_150.png

```

After extracting and installing the package somewhere I must copy those 2 files to;```

/home/satimis/.config/GIMP/2.10/plug-ins/

```
**[COLOR="#FF0000"]Is it correct ?[/COLOR]**

If I extracting and installing the package inside the plug-ins folder.  Those 2 files are there

On Terminal run;
$ ls -al /home/satimis/.config/GIMP/2.10/plug-ins/```

total 8
drwxr-xr-x  2 satimis satimis 4096 Nov  1  2020 .
drwxr-xr-x 29 satimis satimis 4096 Jul 20 17:17 ..

```
Now the plug-ins folder is empty.

If I'm wrong, please correct me.  Thanks

Regards

---

### Post by satimis on 2022-07-20
> **mIk3_08 said:**
> These are one of the steps on installation of a package. just follow the steps and make sure the location address of your execution. Regards and cheers.
Thanks for your advice.

Regards

---

### Post by Dennis N on 2022-07-20
> I couldn't read it online. I must download it to read.
Right. You download the .tar.xz file and open it with Archive Manager then open the READMe.txt. 

The plug-ins folder looks right for Gimp installed from Ubuntu repository. A Flatpak has a different folder. The folder is probably empty unless you previously installed plugins.

Be sure the plug-in is executable.

**Tip: **Whatever type of Gimp, you can find the plug-ins folder from Gimp: Edit > Preferences > Folders > Plug-Ins (see screenshot, red arrow). I used a Flatpak install of Gimp, so it's different than yours. You can also open it from here with the folder icon.

---

### Post by Holger_Gehrke on 2022-07-20
I wouldn't get my hopes up. It's a plugin written in Python. In theory there are just two files (color_grading_cw_v174.py and colorwheel_150.png) which you have to copy into your personal plug-in directory ($HOME/.config/GIMP/2.10/plug-ins/). When I do so and start gimp from the command line, I get various errors that all look like the type of thing you get when running an old Python 2 script in Python 3. In theory one could install Python 2.7 and change the '#!' line at the beginning of the script to use that, in practice I'm too afraid of seriously breaking something - a lot of stuff in an Ubuntu system relies on Python - to try that.

Holger

---

### Post by satimis on 2022-07-20
> **Holger_Gehrke said:**
> I wouldn't get my hopes up. It's a plugin written in Python. In theory there are just two files (color_grading_cw_v174.py and colorwheel_150.png) which you have to copy into your personal plug-in directory ($HOME/.config/GIMP/2.10/plug-ins/). When I do so and start gimp from the command line, I get various errors that all look like the type of thing you get when running an old Python 2 script in Python 3. In theory one could install Python 2.7 and change the '#!' line at the beginning of the script to use that, in practice I'm too afraid of seriously breaking something - a lot of stuff in an Ubuntu system relies on Python - to try that.

Holger
Hi Holger,

Thanks for your advice.

I have been aware that Ubuntu uses Python as core app.  Also I'm aware that GIMP can't work properly on Ubuntu 20.04 and plugin relying on Python to work can't be added to GIMP.  I'll carry out this test on an Ubuntu 20.04 VM.  If failure I just delete the VM.

I'm considering replacing GIMP with Darktable.  I would start it later installing Darktable on an Ubuntu 20.04 VM.  Also I'm running Windows 10 and 11 here but I'm reluctant running GIMP on them.

Also I have Ubuntu 22.04 running as VM on my spare PC.  I'll try adding the plugin on it to see what will happen.

Regards

---

