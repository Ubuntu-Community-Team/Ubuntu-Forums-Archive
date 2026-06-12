---
title: "Burn DATA CD from M3U playlist"
date: 2009-11-27
forum: Multimedia Software
---

### Post by HuckleSmothered on 2009-11-27
Been looking around for a long time for a way to make a DATA cd from a .m3u playlist. The only option that any Ubuntu-available audio application, like Banshee, Rhythmbox or Exaile, has that I found was to burn an audio cd.

So, after much disappointment, I decided to create a little script to do it outside of an application. I've tested it and it seems to work quite well. Hope it can help some of you out there.

Some explanations on why I wrote it the way I did:
I didn't make it all text/terminal based and used some Zenity because of the difficulty in typing in a filename/path without the tab completion, which I hear might be possible in a script but I can't figure it out.
I also didn't make it all arguments to the script itself because, while I did figure out how to do that, I was making in for the purpose of putting several playlists onto one disc. About a dozen to be specific. And as far as I know, the shell only accepts 9 arguments, minus the option flag of something like -f in front of each file means the number of playlists I could add just went well below nine.
I didn't use all Zenity pop-ups because of the need/desire for yes/no questions. Which Zenity's --question option gives an OK/Cancel selection. Plus Zenity is quite a bit slower with its pop-ups than just a line or two of text.
Uses Brasero to burn because that's what I use ... code it for K3B or whatnot. It would be a single line that would need to be changed as long as you know the command to call a new K3B data project with a folder as the argument.

Feel free to post back with questions, comments, constructive criticism, suggestions, etc.

```

#!/bin/bash
# Burn m3u playlists as a data disc via Brasero
# Functions listed at beginning, commands to call them at the bottom

################################################
################## FUNCTIONS ###################
################################################

################################################
######### Ensures Brasero is installed #########
################################################
check_ForBraseroApp ()
{
	if [ -f `which brasero` ]; then
		check_NumberOfM3Us
		else echo "Brasero application is required but not found\nEnsure it is installed correctly and try again\nExiting"
		exit 1
	fi
}

################################################
######## Choose multiple or single m3u #########
################################################
check_NumberOfM3Us ()
{
	read -p "Will multiple playlists be used? (y/n): " YN
	case $YN in
		y)
			id_TempFolder;; 
		n)
			echo -e "Playlist being exported to Brasero ... \n"			
			burn_1M3U;;
		*)
			echo "Answer was not recognized as 'y' or 'n', try again"
			check_NumberOfM3Us;;
	esac
}

################################################
######## Sends a single m3u to Brasero #########
################################################
burn_1M3U ()
{
	M3U=`zenity --title="Select M3U Playlist" --file-selection`
	sed '/^#/d;s/^/"/g;s/$/"/g' $M3U | tr '\n' ' ' | xargs brasero -d &
}

################################################
######## Identify temporary directory ##########
################################################
id_TempFolder ()
{
	if [ -w /tmp ]; then
		TEMPDIR=/tmp
		elif [ -w /temp ]; then
			TEMPDIR=/temp
		elif [ -w $HOME ]; then
			TEMPDIR=$HOME
		else echo -e "Could not find a temp directory with write access\nChecked /tmp, /temp/ and $HOME\n"
			exit
	fi
	make_PlaylistFolder
}

################################################
####### Make the temp playlist folder ##########
################################################
make_PlaylistFolder ()
{
	N=1
	PLAYLISTFOLDER=$TEMPDIR/playlist$N.tmp
	while [ -d $PLAYLISTFOLDER ]
	do
		echo -e "$PLAYLISTFOLDER exists"
		N=$((N+1))
		PLAYLISTFOLDER=$TEMPDIR/playlist$N.tmp
		echo -e "Trying $PLAYLISTFOLDER instead"
	done
	echo "Creating temporary playlist folder at $PLAYLISTFOLDER"
	mkdir $PLAYLISTFOLDER &&
	echo "$PLAYLISTFOLDER created successfully"
	check_M3Uformat
}

##############################################################
##### Confim m3u playlist file names meet specifications #####
##############################################################
check_M3Uformat ()
{
	echo -e "\nM3U Playlists Requirements:\n\t1. Must have the .m3u extension\n\t2. Must contain only ONE period (.) in entire filename"
	read -p "Do the target m3u playlists conform to these specifications? (y/n): " YN
	case $YN in
		y)
			select_M3U;; 
		n)
			echo -e "Rename m3u playlists to meet specifications.\nExiting"
			delete_TempFolder;;
		*)
			echo -e "Answer was not recognized as 'y' or 'n', try again"
			check_M3Uformat;;
	esac
}

################################################
##### Select m3u playlists through Zenity ######
################################################
select_M3U ()
{
	M3U=`zenity --title="Select M3U Playlist" --file-selection`
	# M3U file integrity check
	if [ `echo $M3U | awk -F. '{print $NF}'` == m3u ]; then
		echo "File format validated"
		cp $M3U $PLAYLISTFOLDER/ &&
		make_M3UsubFolder
		check_ForMoreM3Us
		else echo -e "File does not have the required .m3u extension\nEnsure file is in correct format and try again"
		check_ForMoreM3Us
	fi
}

################################################
#### Ask if more m3u files need to be added ####
################################################
check_ForMoreM3Us ()
{
	read -p "Select more m3u playlists? (y/n): " YN
	case $YN in
	y)
		select_M3U;;
	n)
		create_BraseroDisc;;
	*)
		echo "Answer was not recognized as 'y' or 'n', try again"
		check_ForMoreM3Us;;
	esac
}

################################################
####### Make the m3u specific subfolder ########
################################################
make_M3UsubFolder ()
{
	PLAYLIST=`echo $M3U | awk -F/ '{print $NF}' | cut -d. -f1`
	M3UTEMP=`echo $M3U | awk -F/ '{print $NF}'`
	mkdir $PLAYLISTFOLDER/$PLAYLIST/ &&
	import_PlaylistContents
}

##############################################################
##### Populate m3u subdirectories with playlist contents #####
##############################################################
import_PlaylistContents()
{
	sed -i '/^#/d;s/^/"/g;s/$/"/g' $PLAYLISTFOLDER/$M3UTEMP &&
	cat $PLAYLISTFOLDER/$M3UTEMP | xargs ln -st $PLAYLISTFOLDER/$PLAYLIST/ &&
	echo -e "$PLAYLIST.m3u playlist imported successfully"
}

################################################
############# Import to Brasero ################
################################################
create_BraseroDisc ()
{
	read -p "Open data cd with content from m3u playlists in Brasero now? (y/n): " YN
	case $YN in
	y)
		echo -e "Once you have closed Brasero, you will be given an option to clean up temp folders\nThis cannot be done until after the disc is created though"
		brasero -d $PLAYLISTFOLDER/*/
		delete_TempFolder;;
	n)
		echo -e "Skipping Brasero"
		delete_TempFolder;;
	*)
		echo -e "Answer was not recognized as 'y' or 'n', try again"
		create_BraseroDisc;;
	esac
}

################################################
####### Cleanup temporary directories ##########
################################################
delete_TempFolder ()
{
	echo -e "Temp directory still exists with m3u contents"
	read -p "Cleanup now? (y/n): " YN
	case $YN in
	y)
		rm -R $PLAYLISTFOLDER && 
		echo -e "Cleanup finished\nExiting"
		exit 0;;
	n)
		echo -e "$PLAYLISTFOLDER still exists\nExiting"
		exit 0;;
	*)
		echo -e "Answer was not recognized as 'y' or 'n', try again"
		delete_TempFolder;;
	esac
}

################################################
############## END OF FUNCTIONS ################
################################################

clear
echo -e "
***** Burn m3u playlists as a data disc via Brasero *****
"
check_ForBraseroApp



```

---

### Post by joe_newbie on 2012-04-02
Thank you for posting this. I was exactly what I was looking for, and worked perfectly for burning playlists that I had made from MPD.

Joe

---

### Post by Zapata1879 on 2012-05-22
GOOD one! I like this too... :guitar:
thanks for sharing!

---

### Post by epitaph on 2012-10-28
Very good script! I was just going to start working on something like this (though way less featured) and I am glad I found yours.

Thanks again.

---

