---
title: "not sure how to install the gimp's-save-for-web plugin"
date: 2017-03-23
forum: Multimedia Software
---

### Post by ronjjjg8885 on 2017-03-23
can you explain it to me?
i've tried to download and run gimp-save-for-web-master.zip from github but it wasn't working and the instructions were vague
edit:
i think ive found a link about how to install it properly
let me try to read it

edit:
im trying to follow this:
[https://ubuntuforums.org/showthread.php?t=1874280](https://ubuntuforums.org/showthread.php?t=1874280)

but i can't access the gimp folder (the third step)

let me know how

edit:
i've tried to
> tar -xvf gimp-save-for-web-0.29.3 -C ~/.gimp-2.8/plug-ins/

but get > tar: gimp-save-for-web-0.29.3: Cannot read: Is a directorytar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now




---

### Post by deadflowr on 2017-03-23
Seems like you already extracted the directory from the tarball, so the error output reflects that.
Now simply try running the commands
```
cd gimp-save-for-web-0.29.3
./configure
make
sudo make install
```
**caveat: install the package checkinstall and use that in place of make install and it'll build a debian package which can later be easily removed with Ubuntu's package manager system:
[Checkinstall]("https://help.ubuntu.com/community/CheckInstall")

---

### Post by SeijiSensei on 2017-03-23
What's the difference between this and simply choosing to export to PNG or JPEG from GIMP's File menu?

---

### Post by ronjjjg8885 on 2017-03-24
the plugins folder empty

as for what you said SeijiSensei

i think that it is better and smaller in size than exporting

anyhow it is alsp easier for me if i've more than one task to perform.

---

### Post by ronjjjg8885 on 2017-04-03
hi again
i've typed:
> cd ~/.gimp-2.8.18

to enter the directory but got
> bash: cd: gimp-2.8.18: No such file or directory

can you tell what should i do?
(if it was not clear i could not performed what you have suggested)

---

### Post by howefield on 2017-04-03
> **ronjjjg8885 said:**
> bash: cd: gimp-2.8.18: No such file or directory

The error is telling you what is wrong. There is no directory by that name.

Try using the terminals autocomplete function, eg cd ~/.gimp and then press the tab button or open up the File manager and check the name of the folder.

---

### Post by ronjjjg8885 on 2017-04-03
when i open the file manager i don't know how to make gimp's folder visible.

i will try the auto complete

edit:
the autocomplete does not do a thing. nothing happens

---

### Post by deadflowr on 2017-04-03
> when i open the file manager i don't know how to make gimp's folder visible.

press ctrl + H to show hidden folder/files.

---

### Post by ronjjjg8885 on 2017-04-03
ok

but now:
when i do


> sudo make install


i get:


> make: *** No rule to make target 'install'.  Stop.




edit
let me know what i can do
i must go to sleep
i will see it soon i hope

---

### Post by howefield on 2017-04-03
Why not install gimp-plugins-registry which includes the save-for-web plugin ?

```
apt-cache show gimp-plugins-registry
safe-for-web (0.29.0): Save for Web
     Allows to experiment with various popular web format options. It shows
     an automatically updated preview and file size statistics.
```

```
sudo apt intall gimp-plugins-registry
```

---

### Post by ronjjjg8885 on 2017-04-05
i've got 
```
$ sudo apt-cache show gimp-plugins-registryN: Unable to locate package gimp-plugins-registry
E: No packages found
```

---

### Post by howefield on 2017-04-06
> **ronjjjg8885 said:**
> i've got 
```
$ sudo apt-cache show gimp-plugins-registryN: Unable to locate package gimp-plugins-registry
E: No packages found
```

Re read my post, if you want to show the details for that package, use..

```
apt-cache show gimp-plugins-registry
```

no need for sudo nor the "N" at the end.

---

### Post by ronjjjg8885 on 2017-04-06
[ATTACH=CONFIG]274453[/ATTACH]

---

### Post by howefield on 2017-04-06
Many apologies, my mistake with the package name.

Try..
```
apt-cache show gimp-plugin-registry
```

---

### Post by ronjjjg8885 on 2017-04-06
ok
but now
do i have to give you the output of this command?

---

### Post by howefield on 2017-04-06
The output is only for your benefit so that you see what the package contains and be sure it is for you. *I* don't care what it says.

There is more to the package than the "save for web" feature that you want, but it is less than 5MB to download and takes up less than 15 MBs of installed disk space, so pretty small and a simple way for you to get the desired feature.

---

### Post by ronjjjg8885 on 2017-04-06
well
i'm actually not sure about what are you suggestion for how to install the plugin

what do i need to do for installing it?

edit:
i've it now. thanks
i've typed
> sudo apt install gimp-plugin-registry



and now it is listed under the "file menu"

---

### Post by howefield on 2017-04-06
> **ronjjjg8885 said:**
> well
i'm actually not sure about what are you suggestion for how to install the plugin

what do i need to do for installing it?

Cool, I see from your edit that you got it .. feel free to mark the thread as solved if you wish to aid others :)

---

