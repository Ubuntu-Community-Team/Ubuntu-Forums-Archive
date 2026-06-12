---
title: "Open Random MythVideo file in directory (and subdirectories)"
date: 2009-06-03
forum: Mythbuntu
---

### Post by xioustic on 2009-06-03
Hey guys,

I realize this feature has been requested before but I'm sure there's some temporary solution I just can't find.

Preface: I have 700+ full movies in my movie directory, and around 2000+ video files of TV Show episodes.

The directory structure is such:
/media/MythMedia (all media)
/media/MythMedia/Movies (all movies)
/media/MythMedia/TV Shows[/Show name[/ Season #]]
/media/MythMedia/Anime[/Anime Series[/ Season #]

So I have a relatively large household that wants to watch these. But the hardest part they have (now that our collection is so massive now) is deciding what to watch. On GBPVR, we had the ability to shuffle and then pick from the shuffled results.

There's no way I'm going back to Windows. I love MythTV/MythBuntu, and I've worked way too hard to go back. But I need some sort of way to play a random media file (either through a shell script or some such thing).

Ideally, I would want a file in the root MythMedia, Movies, TV Shows, Anime, each Show/Series and each Season directories that would launch a random media file in that directory. This would allow my household to play a random video from a show that they wanted to watch, or all the TV Shows, or all the Movies, or just a random video from a show from a particular season.

I use VLC for just about all my playback. I would like to discover a solution that takes care of mplayer, VLC, and xine users in one fell swoop but that doesn't seem all that likely.

So, any ideas?

A couple leads:
[MythTV Wiki playRandom.sh]("http://www.mythtv.org/wiki/MythVideo:playRandom.sh")
[Setting Up MythVideo For Playlists]("http://blog.codedread.com/archives/2006/12/17/setting-up-mythvideo-for-playlists/")

I'm sure this isn't too uncommon of a request, so maybe we can get a HOWTO going or some such thing (if there isn't one already).

**Related: **What does the %s return in the MythVideo external player configuration? Is it just the filename or is it the full path?

---

### Post by xioustic on 2009-06-07
Bump. ):P

---

### Post by xioustic on 2009-06-22
Still no ideas?
:popcorn:

---

### Post by breakin494 on 2010-02-10
I am looking to do the same thing. I understand how to create a random number with a script, but I'm having an issue figuring out how to associate a randomization to files. Once that is done all you need to do is have a command in the script like:

vlc $random_vid


I would also like to know how a script could randomize file selection between the root directory and any sub directories (i.e. tv show and seasons). If anyone has an idea how to associate randomizing with file selection I could throw together a quick script and toss it up here. Thanks.

---

### Post by spongebob1981 on 2011-01-31
Seeing no one is helping you, thought I'could chime in.

If I where in your shoes, I'd do it with perl.
Without giving much thought, so I'm being VERY prone to errors, you could list all files in the directories, (ls -R *.mp4, for instance) or even <cat> several lists into a big file.
Afterwards, you can give each file a number (should be easy as pie) and
a) store the relationship in a file.
b) create it on the fly each time you need a new random file.

Then, you will generate a random number and use that number as an index to that data structure created before.

100 chars as fully qualified file names, times 2000 files, plus 2000 integers, totals about 2 megs.

You can, even, re-randomize the array each week, if you code a little more :lolflag:

Sorry if its not a solution for you, can't afford to code it for you right now, sorry! But give it a try, its not that hard and opens up a whole universe of fun
see yA!

---

### Post by nickrout on 2011-01-31
> **spongebob1981 said:**
> Seeing no one is helping you, thought I'could chime in.

If I where in your shoes, I'd do it with perl.
Without giving much thought, so I'm being VERY prone to errors, you could list all files in the directories, (ls -R *.mp4, for instance) or even <cat> several lists into a big file.
Afterwards, you can give each file a number (should be easy as pie) and
a) store the relationship in a file.
b) create it on the fly each time you need a new random file.

Then, you will generate a random number and use that number as an index to that data structure created before.

100 chars as fully qualified file names, times 2000 files, plus 2000 integers, totals about 2 megs.

You can, even, re-randomize the array each week, if you code a little more :lolflag:

Sorry if its not a solution for you, can't afford to code it for you right now, sorry! But give it a try, its not that hard and opens up a whole universe of fun
see yA!

All the video files are in the database anyway, so you don't need to make a further list.

What i would do is [LIST=1]
[*]make a script that counts how many entries there are in the videometadata table (call it N)
[*]get a random number between 1 and N (call it M)
[*]Extract the filename of the Mth entry in the videometadata table
[*]use the network control interface to execute play file $FILENAME
[*]optionally keep a list of M's so you don't get repeats.
[*]make a menu entry in mythtv to execute the script.
[/LIST]

---

### Post by Icculus on 2011-08-25
> **nickrout said:**
> All the video files are in the database anyway, so you don't need to make a further list.

What i would do is
[LIST=1]
[*]make a script that counts how many entries there are in the videometadata table (call it N)
[*]get a random number between 1 and N (call it M)
[*]Extract the filename of the Mth entry in the videometadata table
[*]use the network control interface to execute play file $FILENAME
[*]optionally keep a list of M's so you don't get repeats.
[*]make a menu entry in mythtv to execute the script.
[/LIST]


7. Post your results on Ubuntu forums ;-)

---

### Post by SL666 on 2011-11-18
Hi guys, found this thread while trying to do this myself, just made a quick and dirty that has heaps of limitations - but might be a starting point.


Basically the premis is, that i use a script vlc_script.sh to play most of my mythvideo files with - so i can force spdif output and actually have it play.

limitation one - all your video needs to be in the one directory.


limitation two - can't have any spaces or special characters in your directories (files are fine)

limitation three - once you start playing, you have to stop each individual file


none the less here it is..

```
#! /bin/bash

function random_file()
{
	#echo RANDOM
	ind=0
#declare an array to load all the files in the directory
	declare -a vid_files
	echo $temp_val2 >> /tmp/vlc_script.log
	file_dir=${temp_val2%#RANDOM#*}'*.*'
	echo $file_dir  >> /tmp/vlc_script.log
	for file_name in $file_dir
	do
		#echo "in first loop"  >> /tmp/vlc_scripts.log

		if [[ $file_name == *#RANDOM#* ]]
		then
			echo found myself >> /tmp/vlc_scripts.log
		else
			vid_files[$ind]=$file_name
		#	echo $ind $file_name ${vid_files[$ind]}
			ind=$(($ind + 1))
		fi
	done
	ind=$(($ind - 1))
	for (( c=0; c<=$num_rand - 1; c++ ))
	do
		#echo $c
		#echo ${vid_files[*]}
		get_id=$[ ( $RANDOM % $ind ) ] 
		#echo $get_id
		#echo ${vid_files[$get_id]}
		vlc --spdif -f "${vid_files[$get_id]}" vlc://quit
		#echo ${random_vid_files[$c]}
		#echo ${vid_files[$get_id]}  = ${vid_files[$ind]}
		vid_files[$get_id]=${vid_files[$ind]}
		ind=$(($ind - 1))
	done	
	#vlc --spdif -f "${random_vid_files[*]}" vlc://quit
}

temp_val="$1"

echo $temp_val >> /tmp/vlc_script.log
temp_val2=${temp_val/"myth://Videos@192.168.1.110:6543/"/"/data/videogroup/video/"}
echo $temp_val2 >> /tmp/vlc_script.log
temp_val3=${temp_val2##*/#}
#echo $temp_val3
if [ ${temp_val3%#*} == 'RANDOM' ]
then
	num_rand=${temp_val3:7:2}
	#echo $num_rand
	random_file
fi
vlc --spdif -f "$temp_val2" vlc://quit

```


sorry for the lack of comments i'll have another go at it when i make a revision.

basically i put a file in the directory with a name like #RANDOM#xx.mkv

where xx is the number of files i want to play and the extension (in this case .mkv is one played with vlc

so pretty much when i play

#RANDOM#03.mkv

it plays 3 random files from that directory.

---

### Post by Professor Anthrax on 2013-02-18
This may be too late for the original poster, but I figured out a way that works well enough for my purposes (even though I know next to nothing about shell scripting), so I may as well pass it on.

I've got a single frontend/backend machine, with MythTV 0.25. I have a bunch of cartoons (all either .mp4 or .m4v files) in a few different directories that have names like "Cartoons - MGM" or "Cartoons - Warner Brothers", and wanted to pull a random video from any one of these directories and play it.

Step 1: the script
```

#! /bin/bash

files=(/mythtv/videos/Cartoons*/*[.]{m4v,mp4})
# create an array of the files in the specified directories
# regular expression says (roughly) match files ending with .m4v and .mp4 in directories starting with "Cartoons"
N=${#files[@]}          # Set N to number of members in the array
((pick=RANDOM%N))       # Set "pick" to random value with N
randomfile=${files[$pick]}  # Set "randomfile" to be element of array that corresponds to value of "pick"

mythavtest "$randomfile" # use internal Myth player to play selected file

```Step 2: Save the script (for me, as randomCartoon.sh) in some handy location (for me, /mythtv/scripts), and make it executable

Step 3: Add a "Random Cartoon" item to "Media Library" in the default menu by editing /usr/share/mythtv/themes/defaultmenu/library.xml (below is XML, perhaps obviously)
[HTML]
    <button>
        <type>VIDEO_BROWSER</type>
        <text>Random Cartoon</text>
        <description>Pick a random cartoon and play it</description>
        <action>EXEC /mythtv/scripts/randomCartoon.sh</action>
    </button>
[/HTML](the value of "type" only affects the icon this menu item uses)

Now I can have it pick a cartoon for me instead of having to scroll through long lists. It seems to work well enough with about 400 files so far, though I suspect that serious users can find some flaws with the script. Hope it helps someone else!

---

### Post by wildmanne39 on 2013-03-14
Old thread closed!

---

