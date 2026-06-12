---
title: "Audacity libmp3lame0"
date: 2011-03-29
forum: Multimedia Software
---

### Post by TexasRussian on 2011-03-29
Hello,

I am having trouble installing libmp3lame0 so it will work with Audacity.  Currently I cannot export to .mp3.
I have installed libmp3lame0 through source code, but Audacity still is being reluctant to recognise that I have installed it.  

I believe it's because Audacity does not know where to look for the libmp3lame0.  I have followed many instructions and howtos online and every one of them is telling me to use Synaptic, I did, I selected libmp3lame0 and slammed the 'Apply' button and it told me that it could not be found or something.  So I decided to go into terminal and type "sudo apt-get install libmp3lame0" no luck, the terminal replies with,
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libmp3lame0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libmp3lame0' has no installation candidate

```so what do I do?  How do I get audacity to allow me to export to .mp3??
Also I am using Ubuntu 10.10 Maverick Meerkat x64

---

### Post by cotcot on 2011-03-29
Have you done what is described in the subtitle "Setting Audacity to use Lame" in [[COLOR="Blue"]this description[/COLOR]]("http://wiki.audacityteam.org/index.php?title=Lame_Installation#GNU.2FLinux.2FUnix_instructions") ?

---

### Post by TexasRussian on 2011-03-29
yes, but it doesn't seem to work, when I try to Export to .mp3 it says ,"Could not open MP3 encoding library!"

---

### Post by TexasRussian on 2011-03-29
ah I fixed it. For some reason it installed to '/usr/local/lib/" so now it works.. .YAY!

---

### Post by cotcot on 2011-03-29
Maybe you get a more useful error message when you start audacity in terminal.

---

