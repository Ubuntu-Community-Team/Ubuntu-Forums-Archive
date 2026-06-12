---
title: "Converting stereo mp3 to mono mp3"
date: 2009-09-24
forum: Multimedia Software
---

### Post by Thumbtack on 2009-09-24
Hi

I need to convert my mp3s (all of them... a lot of mp3s) to mono.  I am deaf in one ear, so I never get to hear half the songs when I use my ipod at work.  I have installed lame, and used the command line to convert a couple of songs to mono using lame -V2 -a input.mp3 output.mp3 but it takes forever doing this one song at a time.  I understand you can create a script (? I think this is what is called, I am new to using ubuntu/linux only been using it for about 4 months) to do this for you automatically.  Can someone help me with writing this?  I would like to be able to just tell it to encode all the files (in their artist folder/album folder/songs.mp3) on it's own copying them to new folders/files with the mono version... if that makes sense.

Also, when encoding with lame -V2 -a etc etc it drops all the ID tags so all mu music shows up as unknown artists?  How do I fix that.

I know this is asking for a lot, but anyone with knowledge on how to do this I would be extremely indebted.

---

### Post by Thumbtack on 2009-09-24
ok I found a script someone wrote for downsizing mp3 files using lame.  I modified it slightly (I think I did it right), but it will not run the second script that is in the same dir.  Here are the scripts.

First one is mp3mono

#!/bin/bash
#
#mp3mono - A script to convert to mono all mp3 files in a
# directory.  This script calls the cptag script which
# must also be in the user's path. cptag depends upon
# lame and mid3v2 (mid3v2 can be found in the
# python-mutagen package).
#
# It is suggested that both the mp3mono and cptag
# scripts be placed in the user's private bin (~/bin).
######################################################

# List mp3's in current directory.
ls *.mp3 > mp3_list
ls *.MP3 >> mp3_list

# Parse the mp3_list and replace spaces with escaped spaces.
sed -i 's: :\\ :g' mp3_list

# Check if resample directory exists and create it if it doesn't.
if
   test -e ./resample
then
   echo "resample directory/file already exists - delete it? (Y/n)"
   read reply
   if
     [ "$reply" != "n" ]
   then
     rm -r resample
     mkdir resample
   else
     exit
   fi
else
   mkdir resample
fi

# Resample each mp3 and write tags using the cptag script
cat mp3_list |while read song
do
   echo "$song"
   cptag "$song"
done

#clean up
if
   test -e mp3_list
then
   rm mp3_list
fi
if
   test -e tag2.txt
then
   rm tag2.txt
fi
exit

*************************************************
This should bring up cptag but it doesn't.  I don't know if it is the path where the scripts are at or what they reside at /home/*myuserid*/bin/

*************************************************
HERE IS cptag

#!/bin/bash
#
#cptag - A script to convert to mono mp3 files with LAME and
#        copy id3v2 tags from the old file to the new one.
#
#####################

# Read id3 tags and write to file
mid3v2 -l "$1" > tag2.txt

# Resample music file

lame -V2 -a --vbr-new --resample 44.1 "$1" "resample/$1"

# Set value of variable 'title'
if
   grep TIT2= tag2.txt > /dev/null  #Test if title tag exists
then
   title=`grep TIT2= tag2.txt | sed "s:TIT2=::"`
   echo $title
else
   echo "Title tag does not exist."
fi

# Set value of variable 'album'
if
   grep TALB= tag2.txt > /dev/null  #Test if album tag exists
then
   album=`grep TALB= tag2.txt | sed "s:TALB=::"`
   echo $album
else
   echo "Album tag does not exist."
fi

# Set value of variable 'artist'
if
   grep TPE1= tag2.txt > /dev/null  #Test if artist tag exists
then
   artist=`grep TPE1= tag2.txt | sed "s:TPE1=::"`
   echo $artist
else
   echo "Artist tag does not exist."
fi

# Set value of variable 'track'
if
   grep TRCK= tag2.txt > /dev/null  # Test if track tag exists
then
   track=`grep TRCK= tag2.txt | sed "s:TRCK=::"`
   echo $track
else
   echo "Track tag does not exist."
fi

# Set value of variable 'genre'
if
   grep TCON= tag2.txt > /dev/null  # Test if genre tag exists
then
   genre=`grep TCON= tag2.txt | sed "s:TCON=::"`
   echo $genre
else
   echo "Genre tag does not exist."
fi

# Write tags to file
mid3v2 -t "$title" -A "$album" -a "$artist" -T "$track" -g "$genre" "resample/$1"

exit

I had to sudo gknautilus to modify the permissions of the files so that I could run them and not just root permission.  I think the mp3mono was supposed to be run by using terminal and CD to the directory of my files and then just typing mp3mono, but that doesn't do anything.  I have to type ~/bin/mp3mono while already in the mp3 file directory.  Then it starts the first script and creates the resample file, but then errors out on all files saying that the command cptag does not exist.

God I hope this makes sense to someone.  

here is the link to the page where the guy who wrote the script put it up on his blog.  As I said I modified it slightly to just convert my files to mono.

[http://http://tuxtweaks.com/2008/08/how-to-resample-mp3-audio-files-on-linux-using-lame/]("http://http://tuxtweaks.com/2008/08/how-to-resample-mp3-audio-files-on-linux-using-lame/")

this is what my terminal spits out:


joe@joe-desktop:~/Desktop/Playlists$ ~/bin/mp3mono
ls: cannot access *.MP3: No such file or directory
resample directory/file already exists - delete it? (Y/n)
y
01-cracker-something_you_aint_got.mp3
/home/joe/bin/mp3mono: line 42: home/joe/bin/cptag: No such file or directory
14-cracker-darling_were_out_of_time.mp3
/home/joe/bin/mp3mono: line 42: home/joe/bin/cptag: No such file or directory
Cracker - (1992) CRACKER - 03 - This Is Cracker Soul.mp3
/home/joe/bin/mp3mono: line 42: home/joe/bin/cptag: No such file or directory
Cracker - (1992) CRACKER - 07 - Someday.mp3
/home/joe/bin/mp3mono: line 42: home/joe/bin/cptag: No such file or directory
Cracker - (1993) KEROSENE HAT - 01 - Low.mp3
/home/joe/bin/mp3mono: line 42: home/joe/bin/cptag: No such file or directory
Cracker - (1993) KEROSENE HAT - 07 - Sweet Potato.mp3
/home/joe/bin/mp3mono: line 42: home/joe/bin/cptag: No such file or directory
Cracker - (1993) KEROSENE HAT - 69 - Euro-Trash Girl.mp3
/home/joe/bin/mp3mono: line 42: home/joe/bin/cptag: No such file or directory
Cracker - (1998) GENTLEMAN'S BLUES - 01 - The Good Life.mp3
/home/joe/bin/mp3mono: line 42: home/joe/bin/cptag: No such file or directory
Cracker - (1998) GENTLEMAN'S BLUES - 02 - Seven Days.mp3
/home/joe/bin/mp3mono: line 42: home/joe/bin/cptag: No such file or directory
Cracker - (1998) GENTLEMAN'S BLUES - 03 - Star.mp3
/home/joe/bin/mp3mono: line 42: home/joe/bin/cptag: No such file or directory
Cracker - (1998) GENTLEMAN'S BLUES - 06 - Been Around The World.mp3
/home/joe/bin/mp3mono: line 42: home/joe/bin/cptag: No such file or directory
Cracker - (1998) GENTLEMAN'S BLUES - 07 - The World Is Mine.mp3
/home/joe/bin/mp3mono: line 42: home/joe/bin/cptag: No such file or directory
Cracker - (1998) GENTLEMAN'S BLUES - 09 - Waiting For You Girl.mp3
/home/joe/bin/mp3mono: line 42: home/joe/bin/cptag: No such file or directory
Cracker - (1998) GENTLEMAN'S BLUES - 15 - Wedding Day.mp3
/home/joe/bin/mp3mono: line 42: home/joe/bin/cptag: No such file or directory
Cracker - (2002) FOREVER - 05 - Ain't That Strange.mp3
/home/joe/bin/mp3mono: line 42: home/joe/bin/cptag: No such file or directory
Cracker - (2002) FOREVER - 11 - Shameless.mp3
/home/joe/bin/mp3mono: line 42: home/joe/bin/cptag: No such file or directory
joe@joe-desktop:~/Desktop/Playlists$

---

### Post by Thumbtack on 2009-09-24
Anyway, I have to go to work, I will check this when I get home tonight ~12:30am.

Thanks for anyone who can help me sort this out.  I really appreciate the guy who wrote this script too!  If I can get it working it will really be nice to hear both channels of the music.

See ya

---

### Post by andrew.46 on 2009-09-24
Hi ThumbTack,

I have not looked in depth at this script but it looks like at the very least you need to create the $HOME/bin directory:

```
mkdir /home/joe/bin
```

and I would suggest adding this to your $PATH, which has been glossed over a little in this guide, by editing $HOME/.bashrc as an ordinary user with gedit, or your favourite editor, and adding:

```
export PATH=$PATH:/home/joe/bin
```

And subsequently running the command:

```
source ~/.bashrc
```

Place the scripts in this directory and follow the directions given on the page you mentioned for making the scripts *executable* via the commandline. BTW you gave a typo in the address, the actual address is:

[http://tuxtweaks.com/2008/08/how-to-resample-mp3-audio-files-on-linux-using-lame/](http://tuxtweaks.com/2008/08/how-to-resample-mp3-audio-files-on-linux-using-lame/)

The script has a couple of requirements:

```
cptag depends upon lame and mid3v2 (mid3v2 can 
be found in the python-mutagen package).
```

so I assume you have installed 'python-mutagen' which I note is included in the Ubuntu repository? With this in place you should be able to run this script with a single command from any directory. Mind you that script could do with a little tightening up in a few areas ...

Andrew

---

### Post by Thumbtack on 2009-09-25
> **andrew.46 said:**
> 
and I would suggest adding this to your $PATH, which has been glossed over a little in this guide, by editing $HOME/.bashrc as an ordinary user with gedit, or your favourite editor, and adding:

```
export PATH=$PATH:/home/joe/bin
```

And subsequently running the command:

```
source ~/.bashrc
```

.......

The script has a couple of requirements:

```
cptag depends upon lame and mid3v2 (mid3v2 can 
be found in the python-mutagen package).
```

so I assume you have installed 'python-mutagen' which I note is included in the Ubuntu repository? With this in place you should be able to run this script with a single command from any directory. Mind you that script could do with a little tightening up in a few areas ...

Andrew

I did not see anything in there about editing the .bashrc file, nor the $PATH stuff either.  As I said I am new to doing things this way, but I have really come to love ubuntu as it works fairly well and have only had a few problems that I have sorted out.  

This script works now, so THANK YOU very much.  It will be nice to hear everything now.  :guitar:

---

### Post by andrew.46 on 2009-09-25
Hi Thumbtack,

Good to hear that it is all working now:

> **Thumbtack said:**
> I did not see anything in there about editing the .bashrc file, nor the $PATH stuff either.

No, he was a little quiet about that, although you will see there is a brief mention within the script itself:

```

#mp3shrink - A script to resample all mp3 files in a
# directory.  This script calls the cptag script which
# **[COLOR="Red"]must also be in the user's path[/COLOR]**. cptag depends upon
# lame and mid3v2 (mid3v2 can be found in the
# python-mutagen package).
#
# It is suggested that both the mp3shink and cptag
# scripts be placed **[COLOR="Red"]in the user's private bin (~/bin)[/COLOR]**.

```

There is an old tradition that system executables, scripts and binaries are all placed in /usr/bin while machine specific files of the same sort are placed in /usr/local/bin. Both of these locations are in your system $PATH, you can see this by typing:

```
echo $PATH
```

So instead of typing in the full path each time you can just use the command 'firefox' instead of '/usr/bin/firefox'. This script asks that you establish your own *private* version of these 'bin' directories in $HOME and for it to work you must add the directory to the $PATH by hand, in our case by adding to $HOME/.bashrc. Now you can run whatever is in this directory without typing in '$HOME/bin/myscript' each time.

Hopefully this explains things a little better?

Andrew

---

### Post by martinbaselier on 2009-09-25
I only read your first post, saw a quite long script and thought: This can be done much simpler. 

You say this is the command to convert an mp3. 
lame -V2 -a input.mp3 output.mp3

Let's say all you mp3's are in ~/mp3

cd ~/mp3
find * -name "*.mp3" -exec lame -V2 -a {} mono.{} \;

This will convert all your mp3's and create new files beginning with mono. This won't solve the tagging problem though.

---

### Post by TVC15 on 2009-11-23
Hello,

To avoid using the command line: there is an application called gnac that does all that you need.
It's basic idea is the same as Sound-converter, but it offers much more possibilities.  One of them is to set the conversion to mono.


Good luck,

Johan

---

### Post by sgosnell on 2009-11-23
A quicker and easier way is to do it in hardware.  You can buy a stereo/mono adapter at almost any store that sells audio hardware.  Just plug the adapter into the jack, then the audio cable or headphones into that, and you have mono.  It may be inconvenient for a small mp3 player, but it works, and will let you listen until you get the conversions done, if you choose to go that way.

---

