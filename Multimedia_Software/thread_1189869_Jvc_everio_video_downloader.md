---
title: "Jvc everio video downloader"
date: 2009-06-17
forum: Multimedia Software
---

### Post by dpurple77 on 2009-06-17
I have hacked a small script to autodownload the videos from a jvc everio gz-mg330he camcorder. Should work with other similar models with some path changes in the script maybe. Here goes....


#!/usr/bin/env bash
CAMFOLDER=/media/EVERIO_HDD
VIDEOFOLDER=/media/EVERIO_HDD/SD_VIDEO/
COUNTER=0
FILECOUNTER=0
if [ -d "$CAMFOLDER" ]; then
while ["$OUTFOLDER" != ""]
        do
        OUTFOLDER=$(zenity --title="JVC Everio Video Importer" --file-selection --directory)
        done

VIDEOFOLDERS=$(ls $VIDEOFOLDER | grep -v MGR_INFO)
for i in $VIDEOFOLDERS
        do
        for k in `ls $VIDEOFOLDER$i/*.MOD`
                do
                        let FILECOUNTER+=1
		done
	done
(for i in $VIDEOFOLDERS
	do
	for k in `ls $VIDEOFOLDER$i/*.MOD`
		do
			let COUNTER+=1
			VIDEONAME=`basename "$k"`
			OUTVIDEONAME=`printf "%03d-$VIDEONAME" "$COUNTER"`
			echo "# Copying file $COUNTER of $FILECOUNTER to $OUTFOLDER \nFilename : $OUTVIDEONAME"
			echo "100 * $COUNTER / $FILECOUNTER" | bc 
			cp -r "$k" "$OUTFOLDER/$OUTVIDEONAME"
		done
	done
)|zenity --progress --title="JVC Everio Video Importer" --text="Backing up Videos" --percentage=0 --auto-close --auto-kill
CHOICE=""
CHOICE=$(zenity  --list  --title="JVC Everio Video Importer" --text "Backup Options" --checklist  --column "Check" --column "Options" FALSE "Rename To mpg"); 
if [ "$CHOICE" != "" ]; then
	rename s/.MOD/.mpg/ $OUTFOLDER/*.MOD
fi
zenity --info --title="JVC Everio Video Importer" --text "Back up completed successfully"

else
zenity --warning --title="JVC Everio Video Importer" --text "JVC Camera isn't found plugged in.
Please check if it is mounted under:

/media/EVERIO_HDD

or change the path in the script."
exit 1
fi


it asks for a folder to save the files to. After copying it asks to rename the files from mod to mpg. After downloading you should erase the camera from its menu.

---

### Post by EvilMarshmallow on 2009-06-17
Interesting... so the .mod file is just a .mpg with a new name?

I'll have to give this a shot when I get home.

---

