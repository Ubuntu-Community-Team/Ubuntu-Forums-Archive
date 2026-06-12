---
title: "Random MP3 copy (possibly Rythymbox option?)"
date: 2013-05-06
forum: Multimedia Software
---

### Post by LaptopU on 2013-05-06
Hello, I have an old SD reader on my car radio and it will accept sizes up to 2gb (when I got the radio it was supplied with a 16mb SD card whooo!)

Anyhoo, what this means is if I want to get a sample of my music on there it can't exceed 2gb size.  Until Ubuntu 12.10 I had a random file copy script which was:

```
#!/bin/bash
# randomcopy 0.6
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

Running this code I got a little window that checked how much free space was on a device, how much I wanted to fill, the source directory and off it went randomly copying files.  It worked beautifully until Ringtail.  I copied the script to ~/.gnome2/nautilus-scripts/ and ensured it was still executable.  It does not feature in any of my Nautilus menus and if I try to run it from a shell by typing ./ and the name of the script it does nothing.  I tried sudo too just in case that was a problem, but still nothing.

So my question is - how can I either get this script working in Ringtail, or is there something else - such as in Rythymbox - that will let me drop in an empty SD card and allow random files to be copied?  The last time I used Windows would be about 2008 and the in-built Microsoft media player would allow shuffling then copying to a device.  I've never come across a similar function on Ubuntu.

---

### Post by LaptopU on 2013-05-06
I've solved it, would you believe it was as simple as Ringtail uses a different directory for executable scripts?  It is now:

/home/$USER/.local/share/nautilus/scripts/

The script still runs perfectly :D

---

