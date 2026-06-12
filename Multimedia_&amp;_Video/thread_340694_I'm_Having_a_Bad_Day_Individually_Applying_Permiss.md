---
title: "I'm Having a Bad Day Individually Applying Permissions To All My Music, Help pls?"
date: 2007-01-17
forum: Multimedia &amp; Video
---

### Post by Happy_Man on 2007-01-17
Ok, here's the deal:

I transferred all my music from my ntfs windows partition over to my Ubuntu partition. So it gave the usual yada yada about needing to be root, so I did all that manually. Now, every single folder and file that I transferred is locked to normal users, I have to be super-user to access them. So I right-clicked the folder that had everything in it, and changed its permissions so that I could access it w/o being root. I also clicked the "apply permissions to enclosed files" button. It didn't work. Repeatedly.  ](*,) Nor will it work on any folders inside the parent folder. I have to unlock every single file and folder *manually.* Please help me out, as I do not want to have to sudo a command every time I want to play my music! Thanks.

---

### Post by majoridiot on 2007-01-17
from a terminal:

```
sudo chown -R user:group /path/to/music/directory
```

assminug your user name and group are both "happy" and the music folder is "happymp3"
in your home directory, it would look like:

```
sudo chown -R happy:happy ~/mp3
```

or

```
sudo chown -R happy:happy /home/happy/mp3
```

chown (changes file/folder ownership) and -R (does it recursively), so all you need to do is
point it at the parent folder and it will give you ownership of all of the files it contains
and of all of the files any folders they may contain. 

more info:

```
man chown
```

---

### Post by kebes on 2007-01-17
Well you can avoid doing it manually ... if you don't mind using the commandline! In the following example I use "happyman" as your username because I don't know what your actual username is. Also I'm just making up directory names, but it should be easy to change them to what you want...

So let's say you want to fix the permissions on the folder:
/home/happyman/files/music/
(and all sub-files and sub-folders!)

1. Open a terminal:
Applications > Accessories > Terminal

2. Navigate to the folder where you want to change things, by typing a "cd" (change directory) command like so:
```

cd /home/happyman/files/

```

3. Issue the "[chown]("http://nersp.nerdc.ufl.edu/~dicke3/nerspcs/chown.html")" (change owner) command, using the "-R" option to make it recursive:
```

chown happyman:happyman music/ -R

```
(of course replace happyman:happyman with your username both times...)

4. You may also have to adjust the permissions on the files. If you need to, you can use the "[chmod]("http://unixhelp.ed.ac.uk/CGI/man-cgi?chmod")" (change mode) to do so:
```

chmod 660 music/ -R

```

5. Now all the files should be owned by your user, and you should have read/write power over them... thus, they should be "normal files." Make sure that you do this to the lowest-level directory that you copied over. (Otherwise if the files are contained in a directory you don't have permission for... you still won't be able to see/change them!)

Hopefully those instructions are clear... if you run into problems, feel free to post of course.

---

### Post by Happy_Man on 2007-01-17
Sweet.... I'm definitely gonna have to remember that one. Thanks!8)

---

