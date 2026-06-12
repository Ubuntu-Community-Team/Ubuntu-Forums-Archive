---
title: "mythmusic 0.26 browse directory"
date: 2013-08-21
forum: Mythbuntu
---

### Post by daveshep2 on 2013-08-21
Gday everyone, i'm one of those guys that thinks mythmusic took a huge step backwards... selecting music takes way too long - scrolling down/up through an alphabetical list (artist/album whatever) with a remote takes forever. the mrs counted 63 button presses to get the wiggles on for the kids! what happened to the A-D -> {a,b,c,d}, E-H -> {e,f,g,h} etc kind of break up in the older versions?? it's hard not to be too critical because mythtv is such a great package and i haven't paid for it or helped develop it... but man, mythmusic is crap, and the devs just seem to say "no it's not, you just need to use a keyboard like i do"...

so long story short i either had to get the cd player (and all the cd's) down from the attic or fix mythmusic, so i've dodgied up a workaround and figured i'd share it.

note that my music is sorted as Artist/Album/Track. these instructions basically use symlinks to sort your music into 

A-D/a/artists_starting_with_a
A-D/b/artists_starting_with_b
...
E-H/e/artists_starting_with_e
     ...
...
U-Z/u/artists_starting_with_u
...
U-Z/z/artists_starting_with_z

(it's harder than i thought to describe (even a simple) directory structure with text!)

1. assume your music is all in, eg /home/user/Music
2. tell mythmusic your music is in /var/lib/mythtv/music
3. create a file make-by-letter.sh in (for example) /home/user/bin with contents (change DIR and DSTDIR to whatever your "answer" was to 1. and 2.)

```
#!/bin/bash


DIR=/home/user/Music
DSTDIR=/var/lib/mythtv/music


find $DSTDIR -type l -print0 | xargs -0 rm


for BASE in A-D E-H I-L M-P Q-T U-Z 0-9; do
    
if [ $BASE == "A-D" ]; then
        declare -a LETTERS=(a b c d)
    elif [ $BASE == "E-H" ]; then
        declare -a LETTERS=( e f g h )
    elif [ $BASE == "I-L" ]; then
        declare -a LETTERS=(i j k l)
    elif [ $BASE == "M-P" ]; then
        declare -a LETTERS=(m n o p)
    elif [ $BASE == "Q-T" ]; then
        declare -a LETTERS=(q r s t)
    elif [ $BASE == "U-Z" ]; then
        declare -a LETTERS=(u v w x y z)
    elif [ $BASE == "0-9" ]; then
        declare -a LETTERS=(0 1 2 3 4 5 6 7 8 9)
    fi
    
    for LETTER in ${LETTERS[@]}; do
            mkdir -p $DSTDIR/$BASE/$LETTER
            find $DIR -maxdepth 1 -mindepth 1 -iname $LETTER\* | while read PATH; do
                /bin/ln -s "$PATH" $DSTDIR/$BASE/$LETTER
            done
    done
    
done

``` 
4. make your script executable ie ```
sudo chmod a+x /home/user/bin/make-by-letter.sh
```
5. now rescan your music directory and when you want to browse by directory it will be nicely sorted and you won't need 63 button presses to turn on the wiggles
6. you can manually run this script any time you update you music library. i want it to check on every boot so i edited /etc/rc.local to be

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
sh /home/user/bin/make-by-letter.sh &
exit 0

```

NOTE this won't touch your actual music directory (ie /home/user/Music in this example).

hopefully that does the trick and mythmusic will become something you, the wife and the kids can use so you can stop looking for alternatives ;)

---

### Post by obrient on 2013-09-05
I have to say that I am excited to see this script. I too hate the new selection feature on MythMusic. I think I have listened to less music, can't wait to try the script.

---

