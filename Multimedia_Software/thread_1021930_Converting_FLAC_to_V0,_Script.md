---
title: "Converting FLAC to V0, Script"
date: 2008-12-26
forum: Multimedia Software
---

### Post by DJDaveX on 2008-12-26
Hi users...

I'm looking to convert my FLAC collection to V0, for my MP3 player. I found a script online but I'm unsure what dependencies are required, nor how to use it, hopefully someone can help me out. I'm guessing I'll need FLAC and LAME from the repos, and id3v2? 

Unless, of course, someone can point me in the direction of a lightweight FLAC to LAME converter (with a GUI, which this script supposedly has). 

Here's the code. 

flac2mp3.sh

```
#!/bin/bash
#########################################################
# Flac to Mp3 Conversion "Wizard" ;) #
# Script Created by falkano(http://what.cd/user.php?id=46566)#
# Credits: somnorific
# baised on Nick Sklavenitis's Flac to Mp3 Conversion Script#
# as posted in http://what.cd/forums.php?action=viewthread&threadid=13534 by mikkoc(http://what.cd/user.php?id=44649)#
# Date: June 22 2008 #
#########################################################
# modify the lame options to your preference example change -b 320 to -b 128 or -b 192 or -b 256
#lameOptions=" --vbr-new -V 0 -k --ignore-tag-errors "

#some variables used thoughout the script
appTitle="flac2mp3 0.1v";
emptyStr='';
lameOptionsOne="-b 320 --add-id3v2 --ignore-tag-errors";
lameOptionsTwo="-V 0 --vbr-new --add-id3v2 --ignore-tag-errors";
lameOptionsThree="-V 2 --vbr-new --add-id3v2 --ignore-tag-errors";

#greeting
zenity --info --title $appTitle --text "Welcome to the flac2mp3 script 0.1v by falkano";

#get the directory where the flac files are stored
flacDir=$(zenity --file-selection --title "Please select the directory where your flac files reside" --directory);
if [ $flacDir == $emptyStr ];
then
        zenity --error --title $appTitle --text "no location supplied, exitting app";
	exit 0;
else
	zenity --info --title $appTitle --text "You selected $flacDir";
fi

#get the directory to save the mp3s in
mp3Dir=$(zenity --file-selection --title "Please select the directory where your want the encoded mp3 to reside" --directory);
if [ $mp3Dir == $emptyStr ];
then
        zenity --error --title $appTitle --text "no location supplied, exitting app";
	exit 0;
else
	zenity --info --title $appTitle --text "You selected $mp3Dir";
fi

#get LAME encoder options
lameOptions=$(zenity --list --text "LAME Options" --width 400 --height 300 --radiolist --column "Choose" --column "Option" TRUE " $lameOptionsOne" FALSE " $lameOptionsTwo" FALSE " $lameOptionsThree" FALSE " Other" );
if [ $lameOptions == 'Other' ];
then
lameOptions=$(zenity --entry --title "LAME Options" --width 400 --text "Please enter custom LAME encoder options");
fi
if [ $lameOptions == $emptyStr ];
then
exit 0;
fi;
zenity --info --title $appTitle --text "using LAME options: $lameOptions";

# change in the directory where the flacs reside and operate from there
cd "$flacDir";

#loop through all the flac files in the directory and encode them(while storing them in the given mp3 directory) 
for FLAC in *.flac
do
rawFileName=$(basename "$FLAC" .flac);
MP3=$(echo "$mp3Dir/$rawFileName.mp3");

[ -r "$FLAC" ] || { echo can not read file \"$FLAC\" >&1 ; exit 1 ; } ;

#This section pulls the Tag info from flac and stores it as a variable.

TITLE="`metaflac --show-tag=TITLE "$FLAC" | awk -F = '{ printf($2) }'`"
ALBUM="`metaflac --show-tag=ALBUM "$FLAC" | awk -F = '{ printf($2) }'`"
ARTIST="`metaflac --show-tag=ARTIST "$FLAC" | awk -F = '{ printf($2) }'`"
TRACKNUMBER="`metaflac --show-tag=TRACKNUMBER "$FLAC" | awk -F = '{ printf($2) }'`"
GENRE="`metaflac --show-tag=GENRE "$FLAC" | awk -F = '{ printf($2) }'`"
COMMENT="`metaflac --show-tag=COMMENT "$FLAC" | awk -F = '{ printf($2) }'`"
DATE="`metaflac --show-tag=DATE "$FLAC" | awk -F = '{ printf($2) }'`"

#This section handles the conversion of the Flac file to MP3

flac -dc "$FLAC" | lame ${lameOptions} \
--tt "$TITLE" \
--tn "$TRACKNUMBER" \
--tg "$GENRE" \
--ty "$DATE" \
--ta "$ARTIST" \
--tl "$ALBUM" \
--add-id3v2 \
- "$MP3" 2>&1 |responce=$(zenity --title $appTitle --text "now encoding $FLAC..." --progress --pulsate --auto-close --auto-kill);
done;

# if the user needs to copy any album art, logs, nfos that reside in the flac dir to the mp3 dir, give him the option to do so
zenity --question --text "Encoding done succesfully! now do you want to copy any other(png, jpg, log, cue, txt, nfo, m3u...etc) files in the flac directory to directory with the mp3s?(might contain album art, playlists...etc etc";

if [ $? == 0 ];
then
	#anyone know how to improve this???
	#the following code doesn't work very well... cp have problems with the way filenames are been fed to it...
	#specialy when the file names contain spaces...

        #for file in `ls -l|grep -v ".flac"`;
	#do
	#	cp "$file" "$mp3Dir/$file";
	#done;
	
	#try and copy any files found in the given types
	cp *.png "$mp3Dir";
	cp *.jpg "$mp3Dir";
	cp *.jpeg "$mp3Dir";
	cp *.gif "$mp3Dir";
	cp *.log "$mp3Dir";
	cp *.nfo "$mp3Dir";
	cp *.txt "$mp3Dir";
	cp *.cue "$mp3Dir";
	cp *.m3u "$mp3Dir";
fi

#say goodbye!
zenity --info --title $appTitle --text "ok! everything is done, im exsiting now. tc :)";
exit 0;
```

---

### Post by logos34 on 2008-12-26
> **DJDaveX said:**
> 
Unless, of course, someone can point me in the direction of a lightweight FLAC to LAME converter (with a GUI, which this script supposedly has). 


soundconverter is light, and should work fine if all you want to do is convert to -V0 mp3 ('very high'/~256kbps -- it only has a few mp3 presets which is why I don't like it)


I'd also consider K3b--not exactly lightweight but you should probably already be using it as your cd burning app because it's the best by far. It'll convert flac, ogg, mp3, ape, wav.  
> 
sudo apt-get install k3b dvd+rw-tools vcdimager k3b-i18n libk3b2-extracodecs, normalize-audio sox toolame

Finally, there's Foobar2000 (Wine), which a lot of people swear by.  I think it's probably the best non-native linux gui converter.  I converted my library of apple lossless (.m4a/alac) to ogg with it.  Even fetches cddb info.

Finally there's ffmpeg (CLI only).

---

