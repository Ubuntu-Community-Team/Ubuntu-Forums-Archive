---
title: "Randomly copying MP3 to USB drive"
date: 2010-05-06
forum: Multimedia Software
---

### Post by LaptopU on 2010-05-06
I had a script before my machine broke recently that would allow me to select a folder then randomly copy MP3's from that folder to a USB drive.  I cannot seem to find it again, the closest I came to is one called 'Randomcopy 0.6b' which has been modified for iPod Shuffle, and also the non-iPod version of the same script which appears to run fine but copies a bit too fast and nothing is placed on the device.

Can anyone help me with how I might randomly sync MP3 files to a USB drive using Ubuntu Lucid please?

---

### Post by LaptopU on 2010-05-06
I have tracked down some more code and tweaked it, so here is the resulting code that now works under both Karmic and Lucid if you want to randomly copy files to a particular directory (such as I wanted to randomly copy MP3's to a USB drive).  Credit to Ubuntuforum's Lapsey for the original code.

```

#!/bin/bash
# randomcopy 0.7
# a general-purpose script for copying random files

bInMB=1048576
window_title="Randomcopy"
window_icon="/usr/share/icons/gnome/16x16/devices/gnome-dev-ipod.png"
searchPattern=".*\.\(aac\|aa\|mp3\)"

minFS=$(($bInMB/2))
maxFS=$(($bInMB*40))

######################################################################

O=$IFS IFS=$'\n' tgtPaths=(`echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"`) IFS=$O

for tgtPath in "${tgtPaths[@]}" ; do
	
	if [ -d "$tgtPath" ] ; then # startof if target directory
		
		# Select....
		O=$IFS IFS=$'\n' srcPaths=(`zenity --file-selection --directory --multiple --separator=$'\n' --title="Select source directories" --window-icon="$window_icon"`) IFS=$O

		# Searching.. quickscan
		(
		echo "10"
		for srcPath in "${srcPaths[@]}" ; do
		#	=$(($srcB+$(echo `dosomething` | bc)))
			srcB=$(($srcB+$(echo `find "$srcPath" -type f -size +$(($minFS-1))c -size -+$(($maxFS+1))c -iregex $searchPattern -print0 | xargs -0 stat -c %s+ ; echo 0` | bc)))		
		done
		echo "100"

		# How many?....
		tgtBFree=$((`stat -f -c %f "$tgtPath"`*`stat -f -c %s "$tgtPath"`)) 
	 	if [ $srcB -lt $tgtBFree ]; 
			then dialog_entry_text=$(($srcB/$bInMB))
			else dialog_entry_text=$(($tgtBFree/$bInMB))
		fi
		remSrcB=$(($bInMB*`zenity --entry --text="$(($srcB/$bInMB))MB of files $(($minFS/$bInMB))-$(($maxFS/$bInMB))MB found. $(($tgtBFree/$bInMB))MB free on device of /$(echo "$tgtPath" | sed 's/^.*\///'). How much to copy?" --entry-text="$dialog_entry_text" --title="$window_title" --window-icon="$window_icon"`))
		initSrcB=$remSrcB

		if [ $srcB -gt 0 ]; then # startof if not 0 Bytes
		
			# Searching.... deepscan
			(
			echo "10"
			for srcPath in "${srcPaths[@]}" ; do
				O=$IFS IFS=$'\n' tempSrcF=( `find "$srcPath" -type f -size +$(($minFS-1))c -size -+$(($maxFS+1))c -iregex $searchPattern` ) IFS=$O
				remSrcF=( "${remSrcF[@]}" "${tempSrcF[@]}" )
			done
			initSrcF="${#remSrcF[@]}"
			echo "100"

			# Copying....
			(
			while [ ${#remSrcF[@]} -gt 0 ] && [ $remSrcB -ge $minFS ] ; do 
				random=$(($RANDOM % $initSrcF)) 
				if [ -n "${remSrcF[$random]}" ] ; then # if element is not empty
					srcFS=$((`stat -c %s "${remSrcF[$random]}"`))
					if [ $srcFS -le $remSrcB ] && ! [ -e "$tgtPath/$(echo "${remSrcF[$random]}" | sed 's/^.*\///')" ] ; then # last condition prevents overwrite
						cp -i -L "${remSrcF[$random]}" "$tgtPath"
						remSrcB=$(($remSrcB-$srcFS)) # post-copy!
						srcCpB=$(($srcCpB+$srcFS))
					fi
					unset remSrcF[$random] # make element empty
				fi
				echo $((100*($initSrcB-$remSrcB)/$initSrcB))
			done
			echo "100"

			zenity --info --text="$(($srcCpB/$bInMB))MB successfully copied to $tgtPath" --title="$window_title" --window-icon="$window_icon"

			) | zenity --progress --auto-close --percentage="$((100*($initSrcB-$remSrcB)/$initSrcB))" --text="copying $(($initSrcB/$bInMB))MB to $(echo "$tgtPath" | sed 's/^.*\///').." --title="$window_title" --window-icon="$window_icon"
			# endof copying pipe

			) | zenity --progress --pulsate --auto-close --percentage=0 --text="deepscanning selected folders.." --title="$window_title" --window-icon="$window_icon"
			# endof deepscan find pipe
		
		fi # endof if not 0 B
	
		) | zenity --progress --pulsate --auto-close --percentage=0 --text="quickscanning selected folders.." --title="$window_title" --window-icon="$window_icon"
		# endof quickscan find pipe
	
	fi # endof if target directory

done
# endof for tgtPath
exit

```

---

### Post by LaptopU on 2012-04-29
I need to ressurect this please - I installed Ubuntu Pangolin today and the script doesn't do anything when I run it.  Can anyone see anything in the script that would stop it running?

Thanks

(Or alternatively, using Rhythmbox, is there a way to send files randomly to a storage device?  I have a 2Gb SD card and want to send random tracks to it, a bit like the shuffle feature in Windows media player).

---

### Post by asalapi on 2013-01-21
You might want to look at [http://ubuntuforums.org/showpost.php?p=8920735&postcount=6](http://ubuntuforums.org/showpost.php?p=8920735&postcount=6)
and at posts 14 and 17 at [http://ubuntuforums.org/showthread.php?t=134998&page=2](http://ubuntuforums.org/showthread.php?t=134998&page=2)

---

