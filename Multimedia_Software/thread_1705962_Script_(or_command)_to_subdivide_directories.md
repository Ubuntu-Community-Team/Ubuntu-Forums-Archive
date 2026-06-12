---
title: "Script (or command) to subdivide directories"
date: 2011-03-13
forum: Multimedia Software
---

### Post by driftless on 2011-03-13
Greetings-  I'm looking for a quick command-line script or command to subdivide directories into alphabetical indexes:

/parent/aardvark/food
/parent/aardvark/etc
/parent/asteroid/help
/parent/asteroid/welcomeoverlords
...
/parent/zebra/blackandwhiteissue
/parent/zebra/bipolar
/parent/zeus/

Into:

/parent/a/
/parent/a/aardvark/food/
/parent/a/aardvark/etc/
/parent/a/asteroid/help/
/parent/a/asteroid/welcomeoverlords/
...
/parent/z/
/parent/z/zebra/blackandwhiteissue/
/parent/z/zebra/bipolar/
/parent/z/zeus/

I have found lots of scripts to merge them all back, but can't seem to nail down one that subdivides. And my how I have looked...

Thanks for your time!

(Posted here thinking it might have to do with music organization... but feel free to move to more appropriate area)

---

### Post by cipherboy_loc on 2011-03-13
Bash scripting is (in my opinion) fairly easy to learn. Googling will teach you most of what you need to know for this.

1) For loops
2) Sed and Grep
3) the Find command.
4) basic file and directory utilities (mv, cp, mkdir, etc).


More or less, in pseudo code:

```

FOR EVERY DIFFERENT first character in directory names
    MAKE directory first_char
    MOVE all directories starting with first_char to first_char
DONE

```


If you would like more help, post back. 

Cipherboy

---

### Post by tanpopo_chan on 2011-03-13
that sounds like a problem with an algorithm solution.

Check these out:

[http://en.wikipedia.org/wiki/Sorting_algorithm#Summaries_of_popular_sorting_algorithms](http://en.wikipedia.org/wiki/Sorting_algorithm#Summaries_of_popular_sorting_algorithms)

PS: it should be recursive since you want to check each letter until everything's sorted.
This might also help you out: [http://www.daniweb.com/software-development/shell-scripting/threads/6042/28366#post28366](http://www.daniweb.com/software-development/shell-scripting/threads/6042/28366#post28366)

---

### Post by rubylaser on 2011-03-13
This will do it for you...
Make a tmp directory to move all the files into...
```
mkdir ~/tmp
```
Then cd into your music directory...
```
cd /parent
```
**In the example below, I use ~/music_test**

Then run this code to move everything into your ~/tmp directory...
```
for f in `ls`; do
    name=`echo "$f"|sed 's/ -.*//'`
    letter=`echo "$name"|cut -c1`
    dir=~/tmp"/$letter/"
    mkdir -p "$dir"
    mv "$f" "$dir"
done
```

This is how it works...
```
Admins-MacBook-Pro ~ $ mkdir music_test tmp
Admins-MacBook-Pro ~ $ ls
Admins-MacBook-Pro ~ $ cd music_test/
Admins-MacBook-Pro music_test $ mkdir -p aardvark/{etc,food,help} asteriod/{welcomeoverlords} zebra/{blackandwhiteissue,bipolar} zeus 
Admins-MacBook-Pro music_test $ for f in `ls`; do
>     name=`echo "$f"|sed 's/ -.*//'`
>     letter=`echo "$name"|cut -c1`
>     dir=~/tmp"/$letter/"
>     mkdir -p "$dir"
>     mv "$f" "$dir"
> done
Admins-MacBook-Pro music_test $ ls
Admins-MacBook-Pro music_test $ cd ../tmp
Admins-MacBook-Pro tmp $ ls
a	z
Admins-MacBook-Pro tmp $ cd a/
Admins-MacBook-Pro a $ ls
aardvark	asteriod
Admins-MacBook-Pro a $ cd aardvark/
Admins-MacBook-Pro aardvark $ ls
etc	food	help

```

Hope that helps.

---

### Post by kaibob on 2011-03-13
Here's another one to try. It loops through the contents of the parent directory, skipping files and any directories that contain only one character. It then makes new directories as needed and copies over the existing directories. 

I tested this script but please use it with some test directories first. I used copy rather than move in the script as a precaution. You can change "cp -r" to "mv" if all appears well. 

```
#!/bin/bash

parent="/home/kaibob/photos"

for dir in "${parent}"/* ; do
  [[ -f "$dir" ]] && continue
  new="${dir##*/}"
  [[ "${#new}" -eq 1 ]] && continue
  mkdir -p "${parent}/${new:0:1}"
  cp -r "$dir" "${parent}/${new:0:1}"
done
```

---

### Post by rubylaser on 2011-03-13
I love seeing how different people do things.  That's a slick script, and looks like it should work great.  It's a good idea to use cp -R instead of mv as a test first, I should change that on my example.

---

### Post by driftless on 2011-03-14
Awesome!

Great work gang - I appreciate the tips and different takes on the challenge.

Y'all have given me enough fuel to mark this thing solved.

---

