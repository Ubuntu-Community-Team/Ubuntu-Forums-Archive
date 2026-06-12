---
title: "Need audio format converting help"
date: 2009-02-27
forum: Multimedia Software
---

### Post by Dwiman89 on 2009-02-27
Hi, can someone please tell me how to convert .aif(AIFF/Amiga/Mac audio) into .wav? or what program to use thats reasonable...

Also does anyone have any clue where the directory is that hold the sound files for pidgin?

---

### Post by mc4man on 2009-02-27
ffmpeg will convert aif to wav very fast (app.1.5 sec/track
To do a batch convert keeping the same names you just make a simple script, cd to the directory with the .aif's and call the script.
The basic script will create .wav's in the same directory, you can easily modify any number of ways to do what you want.
(move the .wavs somewhere, move the .aifs somewhere, save the .wavs elsewhere, remove the .aifs (delete), ect. ect.

The basic convert script would be this

```
#!/bin/bash
for f in *.aif; do ffmpeg -i "$f" "${f%.aif}.wav"; done 

```

The possibilities of what you do to separate the .aif's and .wav's are numerous, here's a very simple example, move .aif's to temp dir.

```
#!/bin/bash
mkdir temp
for f in *.aif; do ffmpeg -i "$f" "${f%.aif}.wav"; done
mv *.aif ./temp
```

If you want to save the .wav some where else the path goes directly in front of this in command 
"${f%.aif}.wav";

Another 'simple' Ex, Create a dir. in ~/Music named temp, save .wav's there

```
#!/bin/bash
mkdir ~/Music/temp
for f in *.aif; do ffmpeg -i "$f" ~/Music/temp/"${f%.aif}.wav"; done

```

And so on and so on, you can do what you want.

edit: it's such a simple thing you don't need to use a script if you don't want to, just cd to the folder and run the convert comm.(however you want to structure it), then run any add. commands to move, remove ect. based on wildcard *
If you have quite a number of folders to convert then a script is handy

> the directory is that hold the sound files for pidgin?
don't use pidgin but take a look here
/usr/share/sounds/purple

---

### Post by Dwiman89 on 2009-02-28
thank you. it worked perfectly. Yeah I was trying to change the sounds that pidgin makes. I wanteded to use some sounds that adium uses but they where in aif for mac. I was able to change the sounds it makes!
   I would like to change some things with the GUI of pidgin... I know its not skinnable but it has to be possable to chage it in ways. my goal is to make a black simi-transparent buddy list and in chat boxes. pidgin gets its information fo the GUI from the systems GTK theme, there has to be a way to maybe point it to a seporite GTK theme with a black simi-transpartent input box. 
it would be REALLY cool to have it like adiums chat box were it has the messages in bubbles with your friends picture by every message....

---

### Post by Thirtysixway on 2009-02-28
sudo apt-get install soundconverter

Go to Applications > Sound & Video > Sound Converter

---

