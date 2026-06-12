---
title: "combo script Ogg to MP3 or m4a to MP3"
date: 2007-08-21
forum: Multimedia &amp; Video
---

### Post by grimmier on 2007-08-21
I had a common problem a lot of others have.  In that my well organized music collection, has a mixed array of file types. 

Now normally i wouldn't care, except the cd player in my car can only play wma and mp3 files. 
so i needed to convert all my ogg and m4a files over to mp3. 

I found a couple of converter scripts on the web that could do one type each. 
so i felt the need to combine them. 

for Ogg 2 Mp3 conversions i use this script
[http://marginalhacks.com/bin/ogg2mp3]("http://marginalhacks.com/bin/ogg2mp3")
it works great although it does not work recursively through my music directories.

for m4a to Mp3 conversions i use this script.
[http://www.minigeek.org/index.php/2007/07/08/linux-m4a-to-mp3-conversion-script/]("http://www.minigeek.org/index.php/2007/07/08/linux-m4a-to-mp3-conversion-script/")
This script has a bonus feature, in that it works recursivly. 

So in my combining  i mostly used the m4a script as a base. 
First i added in a mini menu to chose which converter you wish to use. 
This makes it so you can still use the recursive functionality for both converters.

Then you get the option to either keep your original files or delete them.
after finding all the files to convert, it will display the list to you. and wait for you to proceed.

For all ogg conversions it calls the perl script for ogg2mp3 conversions.

here is the modified script
```

#!/bin/bash
#convert2mp3.sh
#Original script can be found at
# http://www.minigeek.org/index.php/2007/07/08/linux-m4a-to-mp3-conversion-script/
Pause()
{
    key=""
    echo "Press 'Ctrl-C' to cancel batch"
    echo or 
    echo -n Hit any key to continue....
    stty -icanon
    key=`dd count=1 2>/dev/null`
    stty icanon
}
LOGFILE="convertLog.txt"
count=0
help_convert()
{
	echo
	echo "This software is licensed under the GNU General Public License"
	echo "For the full text of the GNU GPL, see:"
	echo "http://www.gnu.org/copyleft/gpl.html"
	echo "No guarantees of any kind are associated with use of this software."
	echo "requirements: faad, lame"
	echo
	echo "Usage: $0 [-h] [-r] [-d path]"
	echo "Options: "
	echo "-h displays this help"
	echo "-r recursively scans directories"
	echo "-d specifies a path other the current path"
	exit 1
}

# handle options passed in by the user
recursive=0
directory=`pwd`
while getopts "hrd:" opt
do 
	case $opt in
		h) help_convert;;
		r) recursive=1;;
		d) directory="$OPTARG";;
		*) help_convert;;
	esac
done
# Choose Conversion method to invoke. 
echo
echo "Choose Conversion type:"
echo "[0] m4a -> MP3 (Default)"
echo "[1] Ogg-Vorbis -> MP3"
echo -n "Enter Choice: "
read CON_TYPE
if [ $CON_TYPE ];then
if [ $CON_TYPE == 1 ]; then
dectype="ogg";
CONVERTER=1
else
dectype="m4a";
CONVERTER=2
fi
else
CONVERTER=2
dectype="m4a"
fi
echo
echo "Preparing scripts to convert $dectype to Mp3"
echo
echo "<=============================================>"
echo "Do you wish to keep the oringial files?"
echo "[0] Delete originals after conversion (default)"
echo "[1] Keep the Original"
echo -n "Enter Choice: "
read KEEP
if [ $KEEP ];then
if [ $KEEP == 1 ]; then
keep=1
else
keep=0
fi
else
keep=0
fi
# This nifty IFS line is from:
# http://www.issociate.de/board/post/420747/files_and_directories_with_spaces_in_bash_script.html
IFS=$'\n'
echo `date` >> $LOGFILE
# if not recursive, then limit the find to the directory itself.
if [ $CONVERTER == 1 ]; then
if [ $recursive == 1 ]; then
	total_files=`find ${directory} -iname '*.ogg' -print`
	echo `find ${directory} -iname '*.ogg' -print | wc -l `" ogg files to begin with" >> $LOGFILE
else
	total_files=`find ${directory} -maxdepth 1 -iname '*.ogg' -print`
	echo `find ${directory} -maxdepth 1 -iname '*.ogg' -print | wc -l `" ogg files to begin with" >> $LOGFILE
fi
else
if [ $recursive == 1 ]; then
        total_files=`find ${directory} -iname '*.m4a' -print`
        echo `find ${directory} -iname '*.m4a' -print | wc -l `" m4a files to begin with" >> $LOGFILE
else
        total_files=`find ${directory} -maxdepth 1 -iname '*.m4a' -print`
        echo `find ${directory} -maxdepth 1 -iname '*.m4a' -print | wc -l `" m4a files to begin with" >> $LOGFILE
fi
fi 
echo
echo "<============== START =========================>"
echo "$total_files"
echo "<=============== END ==========================>"
echo "Are all the files found for conversion"
echo
Pause
for i in $total_files
	do
		if [ $CONVERTER == 1 ]; then
			x=`echo "$i"|sed -e 's/\.ogg/\.wav/'`
			y=`echo "$i"|sed -e 's/\.ogg/\.mp3/'`
		else
			x=`echo "$i"|sed -e 's/\.m4a/\.wav/'`
			y=`echo "$i"|sed -e 's/\.m4a/\.mp3/'`
		fi
		echo "X: $x"
		echo "Y: $y"
		# if the directory name doesn't start with a / then prepend the path
		# to the directory name.
		if [[ "$directory" =~ ^[^/] ]]
		then 
			x=`pwd`/`echo ${x}|sed -e 's/^\.\///'`
			y=`pwd`/`echo $y|sed -e 's/^\.\///'`
			orig=`pwd`/`echo ${i}|sed -e 's/^\.\///'`
		else
			orig=$i
		fi
	if [ $CONVERTER == 1 ]; then
# THIS IS WHERE THE OGG SCRIPT GETS CALLED
# You can change this line to include any extra toggles you wish
#See the ogg2mp3 file for options
#example: ./ogg2mp3  [options] ${orig}
			./ogg2mp3 ${orig}
	fi
	if [ $CONVERTER == 2 ]; then 
		faad ${orig}
		echo "X: $x"
		echo "Y: $y"

		faad -i ${orig} 2>.trackinfo.txt
		sed -i '23s/unknown: /title: /' .trackinfo.txt
		sed -i '24s/unknown: /artist: /' .trackinfo.txt

		year=`grep 'date: ' .trackinfo.txt|sed -e 's/date: //'`

		sed -i 's/unknown: iTunes/iTunes: iTunes/' .trackinfo.txt

		genrecount=`grep -c 'genre: ' .trackinfo.txt`
		unknowncount=`grep -c 'unknown: ' .trackinfo.txt`

		if [ "$genrecount" -eq 1 ] && [ "$unknowncount" -eq 2 ]; then
			sed -i '25s/unknown: /composer: /' .trackinfo.txt
			sed -i '26s/unknown: /album: /' .trackinfo.txt
			genre=`grep 'genre: ' .trackinfo.txt|sed -e 's/genre: //'`
		fi

		if [ "$genrecount" -eq 1 ] && [ "$unknowncount" -eq 1 ]; then
			sed -i '25s/unknown: /album: /' .trackinfo.txt
			genre=`grep 'genre: ' .trackinfo.txt|sed -e 's/genre: //'`
		fi

		if [ "$genrecount" -eq 0 ] && [ "$unknowncount" -eq 3 ]; then
			sed -i '25s/unknown: /composer: /' .trackinfo.txt
			sed -i '26s/unknown: /album: /' .trackinfo.txt
			sed -i '27s/unknown: /genre: /' .trackinfo.txt
			genre='other'
		fi

		if [ "$genrecount" -eq 0 ] && [ "$unknowncount" -eq 2 ]; then
			sed -i '25s/unknown: /album: /' .trackinfo.txt
			sed -i '26s/unknown: /genre: /' .trackinfo.txt
			genre='other'
		fi
	
		title=`grep 'title: ' .trackinfo.txt|sed -e 's/title: //'`
		artist=`grep 'artist: ' .trackinfo.txt|sed -e 's/artist: //'`
		album=`grep 'album: ' .trackinfo.txt|sed -e 's/album: //'`
		track=`grep 'track: ' .trackinfo.txt|sed -e 's/track: //'`

		lame --alt-preset 192 --id3v2-only --tt "$title" --ta "$artist" --tl "$album" --tg "$genre" --tn "$track" --ty "$year" "$x" "$y"
		rm .trackinfo.txt
		rm "$x"
# if you want to rename the files, then here's the place.
		#mv "$y" "$artist - $title.mp3"
	fi
	if [ $keep == 0 ]; then
		rm ${orig}
	fi
		((count++))
echo "$orig converted" >> $LOGFILE
done
echo "$count files converted"


```

to use you will need both the code above copy and paste as
convert2mp3.sh
and the [ogg2mp3]("http://marginalhacks.com/bin/ogg2mp3") script. 

Requirements:
[LIST]
[*]Lame or notlame encoder
[*]oggdec
[*]faad
[*]ogginfo
[*]id3tool
[/LIST]

Usage: ./convert2mp3.sh [-h] [-r] [-d path]

NOTE: Make sure you set chmod +x to both scripts. 
you may need root priv, you should be able to sudo it though =).

---

