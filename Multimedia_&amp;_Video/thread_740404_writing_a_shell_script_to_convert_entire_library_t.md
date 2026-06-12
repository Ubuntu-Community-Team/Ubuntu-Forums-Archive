---
title: "writing a shell script to convert entire library to uniform bitrate"
date: 2008-03-30
forum: Multimedia &amp; Video
---

### Post by kewlfuzz on 2008-03-30
While i now realise that Soundconverter does this well enough for my own needs, i thought i'd share what i already have with the community, possibly get some help finishing it, because it may be useful for others who have very particular lame settings they'd like to use in converting their own libraries that sound converter and other programs do not offer like -V [1-9] instead of the five high-low-medium quality settings available

here is what i have thus far, it is my first REAL shell script so any criticism, and assistance would be helpful


```
# This is a unix shell script developed to run lame so as to encode 
# an entire music library at the same bit rate while retaining tag info.
#
# This script should be ran as rarely as possible, in addition to taking 
# up a lot of time, it will also add a bit of silence to the beginning
# and ending of every file encoded, read about it at 
# http://lame.sourceforge.net/tech-FAQ.txt
# 
# To do this we shall use three nested for loops
#
cd Music #goes to the music folder (it is assumed that the script is running from home)
for #all folders (artist)
	cd {each folder}#cd to that folder not sure what variable to use here
	for #all folers (album)
		cd {each folder}#cd to that folder not sure what variable to use here
		#remove spaces from all files in folder
		for i in *.mp3; do mv "$i" `echo $i | tr ' ' '_'`; done
		
		#got this loop from meng here http://ubuntuforums.org/showthread.php?t=347176
		for filename in `ls *mp3`
		do
		
		# here we need to read tags on the command line and load them into variables
		# strings more precisely named TITLE, ARTIST, ALBUM, YEAR, COMMENT, TRACK, and GENRE

		# this command should create a new file with a _ preceding orginal filename 
		# in stereo VBR Quality 5 with afformentioned tags    		
		lame -m s -V 5 --tt TITLE --ta ARTIST --tl ALBUM --TY YEAR --tc COMMENT --tn TRACK --tg GENRE filename _$filename
		done

		#replace spaces for all new files in folder hopefully ubuntu will ignore leading
		#spaces which should restore original filename
		for i in *.mp3; do mv "$i" `echo $i | tr '_' ' '`; done		
		
		cd #go back to parent directory	
	done
		
	cd #go back to parent directory	
done
```

thanks,
kewlfuzz

---

### Post by scragar on 2008-03-30
replace Music with "$1"```
cd "$1"
```, this way you can open the folder with the script, meaning it's target is not fixed. if not then do it the long way:
```
cd "$HOME/Music"
```

to cd to the above dir use:
```
cd ..
```

---

