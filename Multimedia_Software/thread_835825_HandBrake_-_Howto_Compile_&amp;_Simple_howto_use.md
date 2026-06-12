---
title: "HandBrake - Howto Compile &amp; Simple howto use"
date: 2008-06-20
forum: Multimedia Software
---

### Post by BurkDP on 2008-06-20
This post can broken into 2 main parts:
1) Compiling Handbrake
2) A quick'n'simple howto for the CLI


-I don't know spit about coding so there are probably errors or redundancies
-I have plenty of hard drive space so installing a plethora of packages is not a problem for me
-yasm makes happiness for amd64
I'm posting here because I'm sure some of what I've done is unnecessary or incorrect so anyone telling me I'm wrong and why would be appreciated.
-if someone wants to clean this up and post it in the Tips & Tutorials forums as a proper howto feel free and I'd be glad if I got some credit. Or the Handbrake forums or wiki. Really I <3 this program so if anyone thinks this is worthwhile spread the love.
-svn 1531 compiles and runs fine with only one or two errors at the end
-terminal commands are in Italics


## ------------------------------------------------------------
## INTRODUCTION AND MISC.
## ------------------------------------------------------------


If you don't know what HandBrake is, it is love. It rips DVDs to video files. There are much better descriptions than that, but an explanation of HandBrake is not the purpose of this post. Still, I will say that it runs from the terminal but it's **very** easy so don't let that scare you away. I rip my DVDs because I've splurged on a smexy iPod Touch that I can enjoy them on, and for streaming them to my Xbox 360 using ushare (look into it if you have a 360). As such, the fact that the rips I make can have named chapters like a DVD and are of a supremely high quality for their size are amazingly awesome features. I've found that with it's ability to call .csv chapter files, and since TV shows generally have the same chapter titles, it's more convenient than the GUI version. I use VLC with the deinterlace option off to check if they're interlaced though.

I know there are probably better guides out there, and I fall into the power-user with no coding experience spectrum, but I was getting frustrated by the latest HandBrakeCLI svn version not compiling for me. I have a computer I use as a headless server with a minimal Ubuntu install, and since I don't write code I don't have a plethora of -dev packages that compiling it requires. So after tooling around google to see what missing dependencies generate what errors, and painstakingly reading through the scrawl to see where any errors occurred, I've gotten it to work. The rest of the guide was something I put together for a friend and decided to include it as well.

Don't fear the terminal. All of the terminal commands are copy'n'pasteable.

Why the latest svn? Because I can, in short. No real reason given that HandBrake v0.9.2 works perfectly fine. I just like to have the latest and greatest is all. I know and accept it's "at your own risk", but it's never broken anything for me so why not?

At the very end of this post I've got a how to for compiling v0.9.2 from the source If you'd rather not play fast and loose with an svn version. Make sure to read the yasm section (it's right after the package list). 

Sorry if there are some formatting quirks but that's what you get from pasting from a text editor.



## ------------------------------------------------------------
## LIST OF PACKAGES TO COMPILE HANDBRAKECLI FROM SVN
## ------------------------------------------------------------

automake
build-essential
ftjam
g77
g++
gcc
gfortran
libbz2-dev
libtool
patchutils
subversion
wget
zlib1g-dev

I thought I'd get this out of the way up here because I haven't found a good list anywhere. If this's all you need than here you go.



## ------------------------------------------------------------
## YASM
## ------------------------------------------------------------

x264 requires yasm - If you install the above packages, you should be safe as far as dependencies go.

*cd*

( ^ I like to keep things in my home library, makes it easy with ~/ )

*wget [http://www.tortall.net/projects/yasm/releases/yasm-0.7.1.tar.gz](http://www.tortall.net/projects/yasm/releases/yasm-0.7.1.tar.gz)*

*tar xvf yasm*.gz && rm yasm*.gz && cd ~/yasm-0.7.1 && ./configure && make && make install*




## ------------------------------------------------------------
## QUICK SETUP GUIDE FOR HANDBRAKECLI LATEST SVN ON UBUNTU
## ------------------------------------------------------------

2) Install dependencies for building (very poorly documented, but I've managed to
cobble together a working list) and build (jam can take awhile, but it's their
recommended method). I keep my stuff in my home folder so cd there.

*sudo apt-get update && sudo apt-get install gcc g++ gfortran g77 wget build-essential ftjam automake libbz2-dev libtool patchutils zlib1g-dev && svn co svn://svn.handbrake.fr/HandBrake/trunk hb-svn && cd ~/hb-svn && make*



## ------------------------------------------------------------
## COMPILING HANDBRAKE FROM THE LATEST SVN
## ------------------------------------------------------------

## Installs the packages required to compile HandBrackeCLI from the latest svn
*sudo apt-get update && sudo apt-get install gcc g++ gfortran g77 wget build-essential ftjam automake libbz2-dev libtool patchutils zlib1g-dev*

## Creates the directory hb-svn wherever you issue the svn check and retrieves
## the latest svn
*svn co svn://svn.handbrake.fr/HandBrake/trunk hb-*

*cd hb-svn && svn up && make*

***edit: Message from the Latest svn of HandBrake

> ~/hb-svn$ cd ~/hb-svn && svn up && ./configure && ftjam
At revision 1794.

System: Linux
Endian: little

* Mac and Linux:

   Don't run configure by hand, make runs it automatically.

   No, really. That's it. Just type 'make' and hit return.

   You're supposed to be building with make, not jam.
   If you were going to use jam--which you shouldn't--you'd run:
    './jam' on a Mac, or
    'jam' on Linux

* Windows:

   Be sure to always run configure (this script) before building.
   Then, run:
    'jam'

To make jam, boil fruit with sugar and an acid until pectins are released.



## ------------------------------------------------------------
## COMPILING HANDBRAKE-0.9.2 FROM THE SOURCE CODE
## ------------------------------------------------------------

## Installs the packages required to compile HandBrackeCLI
[I]sudo apt-get update && sudo apt-get install gcc g++ gfortran g77 wget build-essential ftjam automake libbz2-dev libtool patchutils zlib1g-dev/I]

## Downloads the source code to your home directory
*cd && wget [http://handbrake.fr/rotation.php?file=HandBrake-0.9.2.tar.gz](http://handbrake.fr/rotation.php?file=HandBrake-0.9.2.tar.gz)*

## Unpacks the source code and removes the downloaded archive
*tar xvf HandBrake*.tar.gz && rm HandBrake*.tar.gz*

## Compiles HandBrake
*cd ~/HandBrake && make*



## ------------------------------------------------------------
## CLI USAGE NOTES
## ------------------------------------------------------------

## An example rip
./HandBrakeCLI -i ~/Naruto_Uncut_DVDs/NarutoUncut_BoxSet7_D1/VIDEO_TS -L -c 1-5 -o ~/Naruto_79.m4v --markers=/home/danielburk/hbchapters/naruto.csv --preset="iPhone / iPod Touch" -s 1 --deinterlace=slower -a 2 ; 

( ^ note that you need the *full* path to where your .csv chapter maker file is stored)

*Because it's compiled with jam and not make I can't get it to install (like how make has sudo make install), but you can just cd to the HandBrake directory (usually ~/HandBrake or ~/hb-svn) and use: ./HandBrakeCLI

Basically the format I use goes:
1) ./HandBrakeCLI (duh)
2) Select input source, either a DVD or VIDEO_TS folder
3) title and chapter information
[INDENT]-L     tells it to look for the longest title (good for movies or TV shows that have all episodes on the disc in one title)
-t     alternatively, specify a title to encode (0 to scan only)
-c     select chapters (e.g. 1-3 for chapters 1 to 3, or 3 for chapter 3 only, default: all chapters)[/INDENT]
4) Set output file name and destination (.m4v = .mp4 extension that plays happier with iTunes/iPods)
5) I've found it works happiest if you put the chapter marker file here, before everything else
6) Select a built-in preset
[INDENT]./HandBrakeCLI -z     See a list of available built-in presets *When using presets Capitalization matters, and if the preset name has spaces, surround it with double quotation marks.[/INDENT]
[INDENT]I'd hazard a geuss that the AppleTV preset might be your best bet because **the Xbox 360 preset is a lie**.[/INDENT]
[INDENT][INDENT]"HandBrake's settings for the AppleTV, including Dolby Digital 5.1 AC3 sound. Provides a good balance between quality and file size, and optimizes performance." *does add chapter markers, but I've only seen quicktime/itunes/ipods "see" them[/INDENT][/INDENT]
7) Extra options, like a subtitle track different audio or de-interlacing
[INDENT]-The built-in presets don't use de-interlacing, so add the argument here
-fun fact - iTunes/iPods now support multiple audio tracks, so now you can include a commentary track for the hell of it (e.g. -a 1,2)
-Any subtitles are hard coded i.e. burned into the picture and not disable-able[/INDENT]

*If you wish to import chapter names from a csv file, you can do so using the following: --markers="/full/path/to/chapters_file.csv" The CSV file should be formatted as follows:

1,Chapter One
2,Chapter Two
3,Chapter Three

Note: Should you use a comma in your chapter name: e.g 1,Chapter, Name you must place a backslash before it like so: 1,Chapter\, Name (This slash will not actually appear in the chapter name)

( ^ you probably already know that .csv is just a .txt by another extension)

** I've found it useful to keep my old .csv chapter files lying around by adding them to a .7z archive. Why? Because I've lost an encode or if it turns out that it has a screwy bit but I didn't find out till later I was glad I'd kept them. 7-zip because it compresses ridiculously small (1/2 the size of a .zip the same size).

*7z a -t7z ~/hbchapters/hbchapters_archive.7z ~/hbchapters/file.csv && rm ~/hbchapters/file.csv*



## ------------------------------------------------------------
## BEST DVD RIPPER ON UBUNTU
## ------------------------------------------------------------

*sudo apt-get install dvdbackup*

## Example usage: mirroring (copying) a DVD to home directory
[I]mount /dev/dvd
dvdbackup -i /DVD/mount/point -o ~/ -M -n <DVD folder name you want>
sudo eject /DVD/mount/point[/I]



## ------------------------------------------------------------
## INSTALLING MEDIBUNTU REPOSITORIES FOR UBUNTU
## ------------------------------------------------------------

## To edit the repository list
*sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup*

*sudo nano /etc/apt/sources.list*

************************************************************************************

## +++ Medibuntu +++
## Packages that can't be included in Ubuntu for legal reasons
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

************************************************************************************

( ^ copy'n'paste into source list )

## Adds the repository key, so you can use it
*wget [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -*

---

### Post by arkixml on 2008-07-02
Thanks so much! That worked great. I've been trying to make HandBrake work for a long time.

Some people might have a problem with the
wget http://www.tortall.net/projects/yasm/releases/yasm-0.7.1.tar.gz 
command because this forum software shortens links. You can uncheck "Automatically parse links in text" to disable this feature.

---

### Post by BurkDP on 2008-07-02
Thanks for letting me know that I've actually given good advice, and not simply posted broken instructions. *Any* replies would be appreciated. I'm not fishing for gratitude or anything, it's just that this is the first time someone has ever replied to a post and not simply left me dangling in the wind.

I would like to add that I can't compile as of svn revision 1553. I think it's because of change 1550
> Added Paul Kendalls ffmpeg AAC-LATM codec. Allows HB to decode AAC-LATM 
MPEG-TS DVB streams.

If you ever want to go back in the svn tree, becuase it no longer works, you do it thusly:

cd hb-dev && svn co (revision number)

here's the RSS feed of the changes in the trunk btw: [feed://trac.handbrake.fr/timeline?milestone=on&ticket=on&changeset=on&wiki=on&max=50&daysback=90&format=rss]("feed://trac.handbrake.fr/timeline?milestone=on&ticket=on&changeset=on&wiki=on&max=50&daysback=90&format=rss")

---

### Post by BurkDP on 2008-07-02
I suppose this is what happens when you get too eager to reply, and do it while you're compiling HandBrake in screen.

Sometimes it helps when it won't compile to just **junk** the whole folder and start again with a virgin svn checkout.

> sudo rm -r hb-dev

OR it may have been because I added this package: 
> linux-kernel-devel
After a fruitless google search for what "io.h" is - something in the kernel I think so I added this. It didn't fix that particular make line, but it now compiles sooo...I have no idea if it helped, but I'm adding it to my original post on the off chance it did.

---

### Post by driven1 on 2008-09-25
OK, so I have a HandBrakeCLI binary that was already compiled for AMD64 (downloaded from another user). What do I do so that it is located where it needs to be and the system can use it?

I've used OSX version, but I'm still an Ubuntu noob. I've also downloaded the gui front, that I'll try to install afterwards. I've read through various threads, but haven't seen anything that works for me. thanks

---

### Post by BurkDP on 2008-09-25
short reply till I can get to my home computer:

test to see if it runs

<code>
./HandBrakeCLI -z
</code>

*should list built in presets

<code>
sudo mv -v HandBrakeCLI /usr/bin/
</code>

*makes it so you can run from terminal by typing it without navigating to its folder and a ./
*the -v gives you verbose output so it tells you what it's doing

Test it with the previous test command.

if it has a ".deb" at the end:

<code>
sudo dpkg -i [whatever .deb is called]
sudo apt-get -f install
</code>

Test as above.

A better explanation by tomorrow. The delay on notification emails means it'll probably be up by the time you know about this one.

---

### Post by moore.bryan on 2008-09-25
why not just ```
mencoder dvd:// -oac lavc -pvc lavc -o movie.avi
```?

---

### Post by BurkDP on 2008-09-25
if you want a no question asked .avi than then mencoder will do the job. But if you want something that looks good for an iPod, or has selectable chapters, or - well there are alot of reasons. If you've never used it, or don't know what it does, check the website. It's a rather amazing piece of software.

That and mencoder scares me. In my experience it's one of those programs that if you have to ask how to use it then you shouldn't be using it. But I may have simply had a bad time. It will always have my respect though for being the only (free) solution I've had luck with for converting realmedia, but handbrake is just so much simpler when you try to anything other than straight DVD->.avi. (and does your command discriminate between titles, or does it rip the entire DVD to .avi?)

---

### Post by driven1 on 2008-09-25
> **BurkDP said:**
> short reply till I can get to my home computer:

test to see if it runs

<code>
./HandBrakeCLI -z
</code>

*should list built in presets

<code>
sudo mv -v HandBrakeCLI /usr/bin/
</code>

*makes it so you can run from terminal by typing it without navigating to its folder and a ./
*the -v gives you verbose output so it tells you what it's doing

Test it with the previous test command.

if it has a ".deb" at the end:

<code>
sudo dpkg -i [whatever .deb is called]
sudo apt-get -f install
</code>

Test as above.

A better explanation by tomorrow. The delay on notification emails means it'll probably be up by the time you know about this one.

it wasn't a deb, but the first commands worked like charm. I'm still not confident with CLI, but I'll try it out tomorrow. Thanks. I may attempt to compile Rippedwire for amd64 sometime soon.

---

### Post by driven1 on 2008-09-25
btw is <alt> F2 the best way to run it? I gave it a quick try but didn't see anything happen.

---

### Post by BurkDP on 2008-09-26
well, I don't know what "<alt> F2" means but here's a quick little thing to cap off the night.

(basically using this "\" allows you to escape things which means that you spread things out - there's more to it than that but you can ask someone more knowledgeable than me)

So what you could do, to make it easier to read than one long line is use this -> \ to spread it out vertically.

xxxxxx\
[]yyyyyy\
[]zzzzzz\

( ^ the [] indicate a space - it is important because  the "\" means mush together and without the spaces it would all run together: xxxxxx yyyyyy zzzzzz without spaces becomes xxxxxxyyyyyyzzzzzz)


HandBrakeCLI -i /<path to>/VIDEO_TS\
[]-t <number>\
[]-c <number-number>\
[]-o /<path to where you save file>/<filename>.<type>\
[]--markers=/<full path to chapter file>/<filename>.csv\
[]--preset="<if you use one, and why wouldn't you?>"\
[]<and so on>

When you paste it in like that (replacing the [] with a space) and hit enter it'll run it like it was all on one line. It may help make it a bit easier to read this way, separating out the arguments spatially.

The chapter markers are optional. As to finding out where your DVD is mount I'm not sure, it's probably like /mnt/<something>/VIDEO_TS. You can use VLC to find out the chapter title information. or use 

HandBrakeCLI -i /<path to>/VIDEO_TS -t 0

to print a list of all of the chapters titles. Movies are usually the longest one but TV shows are all the same length or mushed together in one uber title.

There's alot of extra stuff you could add to the end but the built in presets have never failed me. Except the Xbox 360 one.

It is a lie.

And there's links to their documentation and stuff...and stuff...I could add, but I am very tired. I go bed now.

---

### Post by moore.bryan on 2008-09-26
> **BurkDP said:**
> if you want a no question asked .avi than then mencoder will do the job. But if you want something that looks good for an iPod, or has selectable chapters, or - well there are alot of reasons. If you've never used it, or don't know what it does, check the website. It's a rather amazing piece of software.

That and mencoder scares me. In my experience it's one of those programs that if you have to ask how to use it then you shouldn't be using it. But I may have simply had a bad time. It will always have my respect though for being the only (free) solution I've had luck with for converting realmedia, but handbrake is just so much simpler when you try to anything other than straight DVD->.avi. (and does your command discriminate between titles, or does it rip the entire DVD to .avi?)
fair enough...

---

### Post by clancymf on 2008-09-26
Thanks for the info.. 

Any idea how to update the presets?  Or if one has been created for the Creative Zen mp3 player.

Thanks,

---

### Post by BurkDP on 2008-09-26
I had a similar question and I found out that, unfortunately, you can't change the built-in presets for the CLI (even if you compile from source/svn). It may change in the future. I don't know about the Linux GUI but the Mac/Windows GUI has always been able to.


[COLOR="blue"][HandBrake Forum: Devices]("http://forum.handbrake.fr/viewforum.php?f=7")[/COLOR]

Search there, maybe somebody has put together a good setting for your device that you can copy->modify->paste. But search first. They put together this amazing program on their own time *and* maintain a forum so they understandably dislike getting unnecessary posts (ie the same simple question over and over that a simple type in the forum search would solve, not looking at the wiki first, etc.)

+++++++++++++++++++++++++An Aside++++++++++++++++++++++++

I recommend keeping a text file of all of your HandBrake encode commands so you can easily modify them for each time instead of typing it out. Or just a skeleton one that you can copy->modify->paste

mine ends up looking like this:

./HandBrakeCLI -i ~/CLONE_WARS/video_ts -L -c 20 -o ~/Chapter_20.m4v -I -w 480 -e x264 -b 960 --crop 2:2:0:0 --deinterlace="slower" -E faac -B 128 -R 48 -x level=30:cabac=0:ref=1:analyse=all:me=umh:subq=6:no-fast-pskip=1 ; 

./HandBrakeCLI -i ~/DeathNote_Volume4/VIDEO_TS -L -c 1-5 -o ~/Death_Note_13.m4v --markers=/home/danielburk/hbchapters/deathnote.csv --preset="iPod High-Rez" -s 1 --deinterlace="slower" -a 2 ; ./HandBrakeCLI -i ~/DeathNote_Volume4/VIDEO_TS -L -c 6-10 -o ~/Death_Note_14.m4v --markers=/home/danielburk/hbchapters/deathnote.csv --preset="iPod High-Rez" -s 1 --deinterlace="slower" -a 2 ; 

( ^ I do keep them in alpha order by DVD, but that's because i'm like that. My original goal with my post wasn't to be a general CLI guide, that's here: [COLOR="blue"][Handbrake wiki CLIGuide]("http://trac.handbrake.fr/wiki/CLIGuide")[/COLOR] so if you didn't know using the "<space>;<space" you can chain together encodes in a mamoth copy'n'paste)

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++


Well, there is a long painful way that involves modifying the source code to get custom CLI presets, but at that point is it really worth it? (if you want to brave it, search their forums)

Here's the link to their wiki article listing the built-in prests: [COLOR="Blue"][BuiltInPresets]("http://trac.handbrake.fr/wiki/BuiltInPresets")[/COLOR]

Or to see them in your terminal from HandBrake itself:

./Handbrake -z

(the ./ is not necessary if you've moved it to /usr/bin)

Then you can just copy paste and modify as you need.

---

### Post by clancymf on 2008-09-29
Thanks will do!!

---

### Post by BurkDP on 2008-10-09
If anybody still checks this thread I have a question about a compile error with svn r1817+. I don't want to bother any developers b/c I can't contribute anything and I'm sure I'm just doing something wrong. Basically, I can't get anything above svn r1816 to compile. It was after this change: [Change pthread mutex's to be explicitly NORMAL instead of relying on the default on a per OS basis.]("http://trac.handbrake.fr/changeset/1817") If someone could has any idea what's wrong or whatever - I can't post debug code at the moment and it hasn't broken my previous build so it's not vitally important

---

