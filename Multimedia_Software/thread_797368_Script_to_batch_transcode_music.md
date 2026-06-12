---
title: "Script to batch transcode music"
date: 2008-05-17
forum: Multimedia Software
---

### Post by insane_alien on 2008-05-17
okay, i have a rather large music collection on my harddrive(all ripped to flac) which is organized by artist. now, i lost the folder containing the .ogg versions(transcoded at time of ripping) and i want to write a script to transcode all of these tracks to .ogg while maintaining the folder structure(lack of structure would mean many would get overwritten).

how would i go about doing this? i've wrote scripts before but those never had to care about folder structure or converting one file to another. they were just ways to automate tasks that required a lot of commands

---

### Post by vanadium on 2008-05-17
- You can mirror the directory structure first:

find <source>/ -type d ! -name . -exec mkdir "<destination>/{}" \;

- then convert the flac files also using the find command

find <source>/ -name "*.flac*" -exec flac "{}" -o "<destination>/{}.ogg" \;

[edit]1) added a quote after flac* 2) added -o which is needed to specify output file[/edit]
In a third step, you can, also using find, rename the .flac.ogg files to .ogg. I am sure there are other and probably better options.

---

### Post by insane_alien on 2008-05-17
that first command doesn't make any directories, it just produces an error saying the directory doesn't exist

---

### Post by vanadium on 2008-05-18
You have to create the <destination>  directory first, obviously.

---

### Post by insane_alien on 2008-05-18
i tried that. it was still giving errors
it also made the longest path ever. it was trying to make the folders in /media/disk/Music/ogged/media/disk/Music/FLAC/

i thought that they would just go into /media/disk/Music/ogged/

source was:   /media/disk/Music/FLAC/
destination:  /media/disk/Music/ogged/

---

### Post by vanadium on 2008-05-18
I see what happened. "{}" substitutes what was found in the mkdir command. <source> should probably be just the current directory. That way, a relative path name will be appended to <destination>.

cd /media/disk/Music/FLAC/
find . -type d ! -name . -exec mkdir "/media/disk/Music/ogged/{}" \;

Now, a directory will be found as "./1973/Pink Floyd/Dark Side Of The Moon" and translate to
"/media/disk/Music/ogged/./1973/Pink Floyd/Dark Side Of The Moon" in the mkdir command, which is valid syntax. I am sorry for this unclarity in my previous instruction. An example is always best, though.

---

### Post by insane_alien on 2008-05-18
okay, the directory structure is cloned(thanks for putting up withme on that, i'm not familiar with the find command) but the second command isn't doing anyhing. 

the console just gives me a > and it sits there till i ctrl+c

---

### Post by vanadium on 2008-05-18
The second part should actually be the easiest. See my edit in previous post for corrected detail.

---

