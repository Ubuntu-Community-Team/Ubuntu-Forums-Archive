---
title: "Automate DVD RIP with vobcopy and ffmpeg (or similar)"
date: 2008-07-17
forum: Multimedia Software
---

### Post by HornedBeast on 2008-07-17
Hello.

I am trying to backup all my DVDs to my mediaserver which is entirely command-line based.

I have worked out how to use vobcopy to create one large vob file from my dvd - but I cannot work out how to make that vob into a pretty decent quality Xvid AVI.

Does anyone know how to do this using ffmpeg, transcode or mencoder in one simple command?

Also, as a plus, I'd like to automate this for when I put a DVD into the server tower (there is no screen plugged in). But this part is less important.

Cheers in advance.

HB.

---

### Post by notpace on 2008-09-30
I'm looking to do something similar - let me know if you have had any luck.  The closest I have come to a solution is tuxrip ([http://tuxrip.free.fr/index_en.html](http://tuxrip.free.fr/index_en.html)), but the audio track never seems to work correctly.

---

### Post by clancymf on 2008-09-30
You should look into HandBrakeCLI (see [http://ubuntuforums.org/showthread.php?t=835825]("http://ubuntuforums.org/showthread.php?t=835825")  Lots and lots of options to play with, however you may be able to use a preset to get the output you wanted. 

In addition, check out this [http://ubuntuforums.org/showthread.php?t=507934]("http://ubuntuforums.org/showthread.php?t=507934")

---

### Post by mc4man on 2008-09-30
Pretty simple to do with vobcopy or any cli ripping, dumping method

If you want to do, then to prep things, first install gxine. After installing go to file management -> media and see if it's been added as a choice under dvd movie. If so good, set it as default and **skip down to below red line**. If not then first browse to home dir. -> .local -> share and see if there is a folder named applications and if so, is there a file - mimeapps.list inside. If so great, if not you can create the **folder **if needed with this.
```

mkdir ~/.local/share/applications
```

 the run

```
cp /usr/share/applications/gxine.desktop ~/.local/share/applications/gxine.desktop
```

Then run 
```
gedit ~/.local/share/applications/mimeapps.list
```

If it's **empty **then paste this in

```
[Added Associations]
   x-content/video-dvd=gxine.desktop;totem.desktop;

```

If it's **not empty** then paste just this line in
```
x-content/video-dvd=gxine.desktop;totem.desktop;
```

if the **line exists** then just add

```
gxine.desktop;
```

Be careful to keep formatting - no space between entries and end with a ;
[COLOR="Red"]----------------------------------------------------------------------------------------[/COLOR]

Run
```
gedit ~/.local/share/applications/gxine.desktop
```

Find the line 
name=gxine and change to name=Rip

Find the line
Exec=gxine and change to ```
Exec=./rip
```

Now go to home folder, create a empty text file, name it rip and paste this inside
```
#!/bin/bash
gnome-terminal -e "vobcopy -v -m -F 16" /media/*

```
Open a terminal and go 
```
chmod +x rip
```
Check back in file. man. and make sure Rip is selected

Inserting a dvd in your dvd drive will open vobcopy and rip to home dir.

To rip somewhere else here is an example 
```
#!/bin/bash
gnome-terminal -e "vobcopy -v -m [COLOR="Red"]-o /media/test1[/COLOR] -F 16 " /media/*
```
Adding output to a specific dir. ( in this case a mounted partition

You could make 2 or more scripts (rip, rip1, ect.) and then simply change at will in edit menus - properties of Rip - command ( ie. change to ./rip1

note you can use any cli 'ripper' in place of vobcopy, just keep the commands /options inside of the "..."

The /media/* allows you to use any of your dvd drives if you have more than one, you can also do multiple rips at once.
 Just insert a dvd in one drive, wait about 10 secs or so, then insert in the next one.


Note - If for some reason you wanted to use gxine as an app just create a desktop launcher pointing to it. Use command /usr/bin/gxine

Edit;  using an existing .desktop (gxine) because many times it's already a default choice and makes things simple. You could also create your own .desktop with an exec= a script, drop it into .local/share/applications, register it on the dvd line in mimeapps .list and set it as a default

---

