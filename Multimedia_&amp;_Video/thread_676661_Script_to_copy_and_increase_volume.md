---
title: "Script to copy and increase volume"
date: 2008-01-24
forum: Multimedia &amp; Video
---

### Post by Sutur on 2008-01-24
Hello everyone! :-)

I have an idea for a script that should be quite simple to create, and serve useful for many, many people.

**_The problem_**
[LIST=1]
[*]Music on your mp3 player is too quiet.
[*]Personal amplifiers are expensive, bulky and ugly.
[/LIST]

**_The solution_**
Add music amplification during the copy process between your media and storage, since it's something most of us *have* to do.

What I know, is that we can use audacity and some smaller, less popular programs to amplify our music manually, and save the file to the media, instead of replacing the original, therefore skipping the copy section of the process.

So all we'd need to do is throw a bash script called something like 'ccp' for "CONVERT copy" into the /usr/bin directory to do the following psudocode:

_Example:_

```
ccp /path/to/source/file.mp3 /path/to/media
```

_Process:_

```
[Audio Processing Program Name] [$FILE] [AMPLIFY 200%] [SAVE $PATHTOMEDIA]
```

I just need a program that can force something like 150/200% amplification through the console to an Mp3 file.

Can anyone fill in the blank please? :)

---

### Post by Sutur on 2008-01-24
OK I found a little program to increase Mp3's without losing quality to decoding then recoding the Mp3.

So then, the syntax might be something as simple as this:

```
mp3gain -gc 10 [FILE].mp3
```

Now if you wanted to make sure that as you copy your music the script/program doesn't automatically increase the volume to a point at which you receive distortion, you could use some alternative switches to the above example.
Since a value of 10 is actually quite severe, the imperfections of the mp3 really become apparant to the listener. So you'd have to tweak it to your liking,
I believe something like this is a safer option:

```
mp3gain -r [FILE].mp3
```

But there are problems with the above example. I'm relatively sure I don't have any poorly encoded mp3's, or any that have already had their volume/gain increased beyond clip point (the point at which distortion occurs). But if you do, then obviously the second example is safer for you, but then, many of your mp3's wont be as loud as you want them to be on your mp3 player.


So then, back to the problem - how to make this a bash script incorporated into the copy process?

What I'm stuck with specifically is the part where you can enter a value and have the script use that value, be it the directory or the name of the file:

```
ccp /home/user/music.mp3 /media/player/
```

Should become:

```
cp /home/user/music.mp3 /tmp/music.mp3 && mp3gain -gc 10 /tmp/music.mp3 && cp /tmp/music.mp3 /media/player/
```

Copying the file to the /tmp directory is a good idea because reading and writing files on a removable drive should be slower than copying twice.

All I need to know is how to make the above happen. I'm not a programmer, and I don't know how to make bash scripts. So I need help! Please!!

---

### Post by Sutur on 2008-01-24
Man I **HATE** programming.

Here are some examples I've come up with to match the following command:

```
./ccp /home/user/music.mp3 /media/player/
```

_Script 1:_

```
#!/bin/bash
# Get value for source file.
$FILE=WHAT_GOES_HERE?
# Get value for source directory.
$FILEDIR=WHAT_GOES_HERE?
# Get value for target directory.
$TARGET=WHAT_GOES_HERE?

cp $FILEDIR/$FILE /tmp/$FILE && mp3gain -gc 10 /tmp/$FILE && cp /tmp/$FILE $TARGET
```

_Script 2:_

```
#!/bin/bash

ARRAY=("$@")

echo `cp ${ARRAY[0]} /tmp/${ARRAY[0]}` && echo `mp3gain -gc 10 /tmp/${ARRAY[0]}` && echo `cp /tmp/${ARRAY[0]} ${ARRAY[1]}`
```

The last one gets "close" but I think I misunderstand the way an array works, because it counts everything with a space in between it as a different array value.

lol, as if I know the first f*cking thing about programming...

---

### Post by Sutur on 2008-01-25
[COLOR="Red"]Bumping.[/COLOR]

---

### Post by Sutur on 2008-01-25
**[COLOR="red"]Bumping.[/COLOR]**

---

### Post by Sutur on 2008-01-27
Bumping.

---

### Post by coolen on 2008-01-27
The problem with the spaces is always encountered. To work around it, you have to either wrap the string in quation marks:

```
 ccp "01 - Example.mp3" "01 - Example (gained).mp3"
```

or use the \ escape character:

```
 ccp 01\ -\ Example.mp3 01\ -\ Example\ (gained).mp3
```

This is normal script behaviour. Don't worry about it.


Other than that, it seems as though you're on the right track. You might want to implement the ability to specify the output file as an option, and have the default behaviour append something (you could use sed to do this, I'm sure. Look for the string ".mp3" and replace it with whatever you want) like " (gained)". Another option could overwrite the original file completely.

I've never done a bash script that took switches, though. The best way would be to look for examples, or consult some manuals. I'll look into it.

---

### Post by coolen on 2008-01-28
More info on switches:

It seems that a function called getopts can handle POSIX switches (that is, single-letter switches preceeded by a single dash with multiple options possible, and long options preceeded by two dashes).

[Here]("http://www.mkssoftware.com/docs/man1/getopts.1.asp") is the man page for it. It doesn't seem to be included in Ubuntu.

---

