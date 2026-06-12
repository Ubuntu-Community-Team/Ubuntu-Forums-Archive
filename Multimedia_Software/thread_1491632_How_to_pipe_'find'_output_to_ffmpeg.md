---
title: "How to pipe 'find' output to ffmpeg"
date: 2010-05-23
forum: Multimedia Software
---

### Post by MrSergeiMosin on 2010-05-23
I am currently using the following script to convert all of the Windows Media Audio files to mp3: 

> #!/bin/bash

for f in *.wma; do ffmpeg -i "$f" -acodec libmp3lame -ab 128k "${f%.wma}.mp3"; doneThe only problem is, this is only good for the current directory. I've looked for ways to use the 'find' command to hunt down individual files and pipe them to something else, but they were all trying to find and remove the files, or send the results to other simple commands. I've tried several variations of these, and I cant seem to get the above script or FFMpeg itself to take the output. 

Ideally, I would like to be able to sit in my ~/Music directory and run a script that will hunt down all *.wma files in that and any sub-folders and convert them all to *.mp3.

Thanks

---

### Post by xzero1 on 2010-05-23
It should look *something* like this command though I'm no expert. You might need to tweak stuff because of blanks and other characters in the file names. This should give you a start.

```
find -name '*.txt' -type f -execdir ls '{}'  \;
```

Note "ls" is the command, and '{}' will be arguments from find. "\;" is an escaped semi to end the command.
This code will recursively find text files starting from your working directory and run the command "ls" on them.

This link should help: [http://content.hccfl.edu/pollock/unix/findcmd.htm]("http://content.hccfl.edu/pollock/unix/findcmd.htm")

---

### Post by mc4man on 2010-05-24
> Ideally, I would like to be able to sit in my ~/Music directory and run a script that will hunt down all *.wma files in that and any sub-folders and convert them all to *.mp3.

While I think it may be better if a folder inside each folder was created and the mp3's sent there - for that I don't know

If you just wanted to have it run thru ~/Music and create same name .mp3's in the dir. the wma's are then pretty simple.

(I had something written to create a list - changing a few lines achieved  the above
Certainly can be done better or differently

I use a ~/bin where script is - in this case because I already have one for wma lossless (wma2mp3), named it wma2mp3f

Script in ~/bin
```
#!/bin/bash
if [ -d "${1}" ] ; then
  cd "${1}" && for f in *.wma; do ffmpeg -i "$f" -acodec libmp3lame -ab 128k "${f%.wma}.mp3"; done 
fi

```

command to launch
```
find ~/Music -type d -exec ~/bin/wma2mp3f "{}" \;

```

or script using lame to encode instead of ffmpeg one above,   V 3 can be any lame commands(s) you wish
```
#!/bin/bash
if [ -d "${1}" ] ; then
  cd "${1}" && for f in *.wma; do ffmpeg -i "$f" -f wav - | lame -V 3 - "${f%.wma}.mp3"; done 
fi
```

---

### Post by MrSergeiMosin on 2010-05-24
> Script in ~/bin
 	Code:
 	#!/bin/bash
if [ -d "${1}" ] ; then
  cd "${1}" && for f in *.wma; do ffmpeg -i "$f" -acodec libmp3lame -ab 128k "${f%.wma}.mp3"; done 
fi 
command to launch
 	Code:
 	find ~/Music -type d -exec ~/bin/wma2mp3f "{}" \;


Outstanding! That was just the ticket. Many thanks!

---

