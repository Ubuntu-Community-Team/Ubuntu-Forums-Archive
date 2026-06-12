---
title: "mplayerstart - my resumable/tv-out wrapper script"
date: 2008-05-23
forum: Multimedia Software
---

### Post by IgnorantGuru on 2008-05-23
**[COLOR="Red"]Updated: Nov 10, 2009[/COLOR]** - Updates to the mplayerstart script can now be found at
[http://igurublog.wordpress.com/downloads/script-mplayerstart/](http://igurublog.wordpress.com/downloads/script-mplayerstart/)
The versions below are outdated.


Here is an updated version of the mplayerstart script that adds some functionality to the previous one posted here.  I'm sharing this here in case others want to use it, or use bits of the code in their own scripts.

mplayerstart is a wrapper script for mplayer which allows the user to resume playback of a previously played file, supports a tv-out mode, disables the KDE screensaver, and a few other things.  This version adds a check to see if KDE is running, kmix volume level restoration for each resumed file, support for resuming audio files, automatic playback of the last played file, and acceptance of .resume files on the command line.

Just save this bash script, make it executable (chmod ugo+x mplayerstart), and use it to open media files.  If you make an application shortcut to it or add it to the K menu, you can then associate it with avi and other media files in the file manager.  Then you can just click on the movie or music file to have resumable playback (very slick).

The only thing this script requires is a folder to store the resume files (a few bytes each) and to temporarily store mplayer console output (which can be a few dozen MB, and is deleted when playing the movie is finished).  By default, the script uses the folder ~/.mplayerstart/ for this data.

**What mplayerstart does:**

* This version first checks to see if KDE (kdesktop) is running.  If it isn't, it skips the KDE features automatically.

* mplayerstart plays the media file specified, and when you quit mplayer, saves a .resume file which records where playback was stopped, as well as the kmix volume levels in use when playback was stopped.  mplayerstart also disables the KDE screensaver while playing video files.

* The next time mplayerstart opens a file with the same name as the above media file (regardless of location), it can resume playback, and also set the kmix volume levels to their last used level for this file.

* mplayerstart can also automatically resume the last played file.

* When using the --tv switch, mplayerstart will create an X :1 session and send mplayer's output there, which is useful for NVidia (and other?) video cards with TV-Out.  Just set up your xorg.conf file as described here: [http://en.wikibooks.org/wiki/NVidia/TV-OUT](http://en.wikibooks.org/wiki/NVidia/TV-OUT)

**Usage:**

```
mplayerstart --resume movie.avi
```
plays the movie from the resume point (if any) and creates a new resume point. If you save the above command (mplayerstart --resume) as an application shortcut or add it to the K menu, you can then associate it with avi and other media files in the file manager for one-click resume.

```
mplayerstart movie.avi
```
If you leave out the --resume switch as shown above, mplayerstart will begin playback at the beginning of the media file and will create a new resume point when finished.

```
mplayerstart --resumelast
```
plays the last played media file from the resume point (if any) and creates a new resume point.  If you save the above command as an application shortcut or add it to the K menu, you can then associate it with a keyboard shortcut (I use Windows-R) to quickly resume playback.

```
mplayerstart movie.resume
```
passes a .resume file for playback.  If you associate .resume files with the above command, this allows you to browse the folder of resumeable files (found in ~/.mplayerstart/ by default) and click on a .resume file.  If mplayerstart can't find the media file in it's last known location, it will search up to two folders recursively (configure these folders in the script).

**Notes:**

* mplayerstart plays video files in full screen mode without a GUI.  To quit playback press 'q'.  For other keyboard shortcuts consult 'man mplayer'.

* Audio files are played back in GUI mode.  When the audio file is done playing, press 'q' or close mplayer.  The .resume file will not be saved until you quit mplayer.

* You can customize the location of mplayerstart's .resume files in the script at the top of the file (just load the script into a text editor).

* After playback, mplayerstart will not re-enable the KDE screensaver if other mplayer's are still running.

* This new version of mplayerstart will read the .resume files created by prior versions, but will save .resume files which are NOT compatible with the prior version. You may want to backup your resume folder before testing this version.

**Tips:**

* If you want to quit mplayer without saving the resume point, press Page-Up repeatedly until mplayer quits.  (PageUp fast-forwards 10 minutes - thus the end of file will be reached and no resume point will be saved.)

**The script:**

You can copy and paste it into a text editor or I have attached it as a txt file.
```
#!/bin/bash
# mplayerstart  v1.2.0
# http://kubuntuforums.net/forums/index.php?topic=3094750.0

# === User Data Section =======================================================

# Location of resume files and temp files; 100MB free space required
data=""

# Optional: Parent folder(s) of your audio & video files for
#           searching for moved resumes
#           If you pass a .resume file to mplayerstart which contains
#           an invalid location for the media file (perhaps you moved it),
#           mplayerstart will recursively search these folders for the file
search1=""
search2=""

# =============================================================================

if [ "$1" == "" ] || [ "$1" == "--help" ]; then
	echo
	echo "Disables KDE3/4 screensaver, restores last KDE volume level,"
	echo "starts mplayer in full-screen mode, sends output to TV,"
	echo "and creates resume file for future play."
	echo "Usage: mplayerstart [OPTIONS] ~/video/movie1.avi"
	echo "Usage: mplayerstart [OPTIONS] ~/video/movie1.avi.resume"
	echo "Usage: mplayerstart --resumelast"
	echo "Usage: mplayerstart --resumepre"
	echo "Usage: mplayerstart --rewind"
	echo "Option: --tv            sends output to X :1 (for NVidia TV-out)"
	echo "                        Note: ignored when playing audio files"
	echo "                        Note: --tv must preceed all other options"
	echo "Option: --resume        resumes playing from last stop point"
	echo "                        (requires filename of media file or resume file)"
	echo "Option: --resumelast    resumes playing last played media file"
	echo "Option: --resumepre     resumes playing previous-to-last played media file"
	echo "Option: --rewind        deletes last played resume file"
	echo "Note: Options must preceed filename; --tv must preceed all options"
	echo "Note: Resume files are not created in TV mode."
	echo "Note: Resume files are auto-deleted after 60 days."
	echo "TV Controls:"
	echo "CTRL+ALT+F7   This is the original Xserver with your windomanager"
	echo "              running. Your TV turns black."
	echo "CRTL+ALT+F8   This will be the tv-out. Your monitor turns black."
	echo "Quitting Mplayer will kill the X :1 session - wait several seconds"
	echo "              for the X :0 desktop to reappear."
	echo "You can also kill the X session with Ctrl-Alt-Backspace."
	echo "Set up your NVidia xorg.conf file as described here:"
	echo "   http://en.wikibooks.org/wiki/NVidia/TV-OUT"
	echo
	echo "Current data folder for resume files: $data"
	echo
	exit
fi

# Determine KDE version
kde4=`ps -A | grep " kded4"`
kde3=`ps -A | grep " kdesktop"`
if [ "$kde4" != "" ]; then
	usekde=4
elif [ "$kde3" != "" ]; then
	usekde=3
else
	usekde=0
fi

if (( usekde == 3 )); then
	# Primary kmix volume channel to restore
	master="0"
	# Secondary kmix volume channel to restore
	pcm="2"
	# get initial volume levels
	mastervol=`dcop kmix Mixer0 volume $master`
	pcmvol=`dcop kmix Mixer0 volume $pcm`
elif (( usekde == 4 )); then
	dbus="qdbus org.kde.kmix /Mixer0"
	# Primary kmix volume channel to restore
	master="Master:0"
	# Secondary kmix volume channel to restore
	pcm="PCM:0"
	# get initial volume levels
	mastervol=`$dbus volume $master`
	pcmvol=`$dbus volume $pcm`
fi

# Initializations
curuser=`whoami`
if [ "$data" == "" ]; then
	data="/home/$curuser/.mplayerstart"
fi
filename=""
restime=0
outfile=""
resume=0
resumeplay=""
tv=0
seektime=""
rx=0

mkdir -p "$data/"

if [ "$1" == "--tv" ]; then
	shift
	tv=1
fi

if [ "$1" == "--resume" ]; then
	shift
	resume=1
fi

if [ "$1" == "--resumepre" ]; then
	# Find most recently modified resume file and touch it
	cd "$data"
	lastresume=`ls -1t *.resume 2> /dev/null | head -n 1`
	if [ "$lastresume" == "" ]; then
		echo "No resume file found"
		if (( usekde == 3 )); then
			dcop kded kmilod displayText "No resume file found"
		elif (( usekde == 4 )); then
			kdialog --title "Mplayer" --passivepopup "No resume file found" 1
		fi
		exit
	fi
	touch --date="2000-01-01 00:00" "$data/$lastresume"
	lastresume=""
fi

if [ "$1" == "--resumelast" ] || [ "$1" == "--resumepre" ] || [ "$1" == "--rewind" ]; then
	# Find most recently modified resume file
	cd "$data"
	lastresume=`ls -1t *.resume 2> /dev/null | head -n 1`
	if [ "$lastresume" == "" ]; then
		echo "No resume file found"
		if (( usekde == 3 )); then
			dcop kded kmilod displayText "No resume file found"
		elif (( usekde == 4 )); then
			kdialog --title "Mplayer" --passivepopup "No resume file found" 1
		fi
		exit
	fi
	if [ "$1" == "--rewind" ]; then
		rm "$data/$lastresume"
		if (( usekde == 3 )); then
			dcop kded kmilod displayText "Rewind"
		elif (( usekde == 4 )); then
			kdialog --title "Mplayer" --passivepopup "Rewind" 1
		fi
		exit
	else
		nowplaying="$data/$lastresume"
		resume=1
		shift
	fi
else
	nowplaying="$1"
fi

if [ "$nowplaying" == "" ] || [ ! -e "$nowplaying" ]; then
	echo 'File not found: '"$1"
	if (( usekde == 3 )); then
		dcop kded kmilod displayText "File not found"
	elif (( usekde == 4 )); then
		kdialog --title "Mplayer" --passivepopup "File not found" 1
	fi
	exit
fi

# resume file was passed on the command line?
if [ "${nowplaying##*.}" == "resume" ]; then
	resume=1
fi

# get resume info
if (( resume == 1 )); then
	# locate resume file
	if [ "${nowplaying##*.}" == "resume" ]; then
		# resume file was passed on the command line
		resumefile="$nowplaying"
	else
		resumefile="$data/`basename "$nowplaying"`.resume"
	fi
	# read resume file if present
	if [ -e "$resumefile" ]; then
		lcount=0
		seektime=""
		# Set the field seperator to a newline
		IFS="
		"
		for line in `cat "$resumefile"`;do
			case $lcount in
			0 ) seektime="$line";;
			1 ) resumeplay="$line";;
			2 ) mastervol="$line";;
			3 ) pcmvol="$line";;
			esac
			(( lcount +=1 ))
		done
		IFS=" "
		# compensate for volume loss
		(( mastervol += 3 ))
		(( pcmvol += 3 ))
		if [ "$seektime" != "" ]; then
			if [ "${nowplaying##*.}" == "resume" ]; then
				if [ "$resumeplay" == "" ]; then
					# accomodate prior versions of mplayerstart
					nowplaying=`basename "$nowplaying" ".resume"`
				else
					nowplaying="$resumeplay"
				fi
				if [ "$resumeplay" == "" ] || [ ! -e "$nowplaying" ]; then
					# find resumed file
					cleanname=`basename "$nowplaying"`
					# replace troublesome characters
					cleanname=${cleanname//"["/"\["}
					cleanname=${cleanname//"]"/"\]"}
					cleanname=${cleanname//"^"/"\^"}
					cleanname=${cleanname//"?"/"\?"}
					cleanname=${cleanname//"*"/"\*"}
					cleanname=${cleanname//"&"/"\&"}
					# search
					if [ "$search1" != "" ]; then
						if [ "$search2" == "" ]; then
							nowplaying=`find -H "$search1" -type f -name "$cleanname"`
						else
							nowplaying=`find -H "$search1" "$search2" -type f -name "$cleanname"`
						fi
						# extract the first file listed
						nowplaying=${nowplaying%%$'\n'*}
					else
						nowplaying=""
					fi
				fi
				if [ "$nowplaying" == "" ] || [ ! -e "$nowplaying" ]; then
					echo 'File not found'
					if (( usekde == 3 )); then
						dcop kded kmilod displayText "File not found"
					elif (( usekde == 4 )); then
						kdialog --title "Mplayer" --passivepopup "File not found" 1
					fi
					exit
				fi
			fi
			echo "Resuming at $seektime seconds"
			seektime="-ss $seektime"
			# Resume volume levels
			if (( usekde == 3)); then
				dcop kmix Mixer0 setVolume $master $mastervol
				dcop kmix Mixer0 setVolume $pcm $pcmvol
			elif (( usekde == 4 )); then
				$dbus setVolume $master $mastervol
				$dbus setVolume $pcm $pcmvol
			fi
		fi
	fi
fi

# set output filename
if [ ! -e "$data/resume-lock" ] && (( tv == 0 )); then
	filename=`basename "$nowplaying"`
	outfile="$data/$filename.log"
fi

# cleanup
# delete output files older than 7 days
find -L $data -maxdepth 0 -type f -mtime +7 -name "*.log" -execdir rm {} \;
# delete resume files older than 60 days
find -L $data -maxdepth 0 -type f -mtime +60 -name "*.resume" -execdir rm {} \;

# Get file extension all uppercase
filetype=`echo "${nowplaying##*.}" | tr a-z A-Z`

# Audio or video?
if [ "$filetype" == "MP3" ] || [ "$filetype" == "WMA" ] || [ "$filetype" == "FLAC" ] || [ "$filetype" == "WAV" ] || [ "$filetype" == "OGG" ] || [ "$filetype" == "M4A" ] || [ "$filetype" == "AC3" ] || [ "$filetype" == "AAC" ] || [ "$filetype" == "RM" ] || [ "$filetype" == "RAM" ]; then
	video=0
	# play audio file
	if [ "$outfile" == "" ]; then
		gmplayer $seektime "$nowplaying"
	else
		gmplayer $seektime "$nowplaying" > "$outfile"
	fi
else
	video=1
	# if playing a vob file, use primary audio track
	if [ "$filetype" == "VOB" ]; then
		aid=" -aid 128"
	else
		aid=""
	fi
	#disable KDE screensaver
	if (( usekde == 3 )); then
		dcop kdesktop KScreensaverIface enable false > /dev/null
	elif (( usekde == 4 )); then
		if [ ! -e "$data/mplay-saver-suspend" ]; then
			echo '#!/bin/bash' > "$data/mplay-saver-suspend"
			echo '# keep the screensaver from coming on - KDE4' >> "$data/mplay-saver-suspend"
			echo 'while (( 1 == 1 ))' >> "$data/mplay-saver-suspend"
			echo 'do' >> "$data/mplay-saver-suspend"
			echo 'qdbus org.kde.krunner /ScreenSaver SimulateUserActivity' >> "$data/mplay-saver-suspend"
			echo 'sleep 119' >> "$data/mplay-saver-suspend"
			echo 'done' >> "$data/mplay-saver-suspend"
			chmod u+x "$data/mplay-saver-suspend"
		fi
		"$data/mplay-saver-suspend" &
		saverpid=$!
	fi
	# play video file
	if (( tv == 1 )); then
		# run mplayer in X :1 display (TV-out)
		exec /usr/X11R6/bin/xinit /usr/bin/xterm -ut -e \
		/usr/bin/mplayer -fs$aid $seektime -vo sdl "$nowplaying" -- /usr/X11R6/bin/X :1 -layout tv
	else
		# run mplayer in current display
		if [ "$outfile" == "" ]; then
			mplayer -fs$aid $seektime "$nowplaying"
		else
			mplayer -fs$aid $seektime "$nowplaying" > "$outfile"
		fi
	fi
fi

# process outfile - determine resume time
if [ "$outfile" != "" ] && [ -e "$outfile" ]; then
	mout=`tail --bytes=350 "$outfile"`
	if (( video == 1 )); then
		# did mplayer reach end of file?
		endoffile=${mout##*End of file)}	
		if [ "$endoffile" != "" ]; then
			restime=${mout##* V:}
			restime=${restime%% A-V:*}
			restime=${restime%%.*}
		fi
	else
		# calculate remaining audio seconds
		atime=${mout##*A:}
		atime=${atime%%.*}
		btime=${mout##*of}
		btime=${btime%%.*}
		(( remain = btime - atime ))
		if (( remain > 15 )); then
			restime=$atime
		fi
	fi
	rm "$outfile"
fi

# save resume file
(( rx = restime - 5 ))
if (( rx > 10 )); then
	echo "$rx" > "$data/$filename.resume"
	echo "$nowplaying" >> "$data/$filename.resume"
	if (( usekde == 3 )); then
		mastervol=`dcop kmix Mixer0 volume $master`
		pcmvol=`dcop kmix Mixer0 volume $pcm`
	elif (( usekde == 4 )); then
		mastervol=`$dbus volume $master`
		pcmvol=`$dbus volume $pcm`
	else
		# dummy volume for non-KDE
		mastervol="50"
		pcmvol="50"
	fi
	echo $mastervol >> "$data/$filename.resume"
	echo $pcmvol >> "$data/$filename.resume"
	echo "Resume file created: $rx seconds"
else
	rm -f "$data/$filename.resume"
fi

if (( usekde == 3)); then
	# enable KDE3 screensaver
	dcop kdesktop KScreensaverIface enable true > /dev/null
elif (( usekde == 4 )); then
	# cancel KDE4 saver-suspend
	kill $saverpid
fi

exit

#If reports "user not authorized to run the X server, aborting"...

#Edit file /etc/X11/Xwrapper.config:
#Change this line:
#allowed_users=console
#to
#allowed_users=anybody


#It you want to shutdown the TV-screen session, you can easily use the same procedure as if you want to kill your X-Server.

#   1. Activate the X-Session you want to terminate
#   2. Press ALT + CTRL + BACKSPACE
#   3. Switch back to your regular session
```

---

### Post by IgnorantGuru on 2008-05-23
I just edited the script above to correct one issue.  If you're interested in the details...

I noticed that if the movie was playing for awhile, when mplayer quit it took a long time for the script to finish.  The result was that if you started the same movie before it finished, it appeared the resume was not working correctly.  The problem was the tail command - for some reason it wasn't just outputing 10 lines.  I added a --bytes=350 to the tail command and that appears to have corrected this issue.

---

### Post by IgnorantGuru on 2008-08-26
I have modified the original post and script above with an improved version of mplayerstart.  I've been using it successfully for awhile but please let me know of any issues you encounter.

---

### Post by IgnorantGuru on 2008-10-11
Updated for KDE4 - tested on Kubuntu Intrepid beta.

---

### Post by Gen2ly on 2009-09-07
I'm not using it but I gotta say this is a great script.  Well put together.  Didn't know how to suspend the screensaver before in KDE from the command line so I appreciate it.

---

### Post by IgnorantGuru on 2009-09-07
> **Gen2ly said:**
> I'm not using it but I gotta say this is a great script.  Well put together.  Didn't know how to suspend the screensaver before in KDE from the command line so I appreciate it.

Thanks - glad you found it.  KDE4 gave me more of a problem stopping the screensaver - couldn't get it to work.  So I simulated user activity instead for now.  These two scripts work for both KDE3 and KDE4 for stopping and starting the screensaver.  (the saver-control script calls the saver-suspend script in the case of KDE4)  These use the same method as mplayerstart.  If anyone knows how to do it properly in KDE4 please let me know.

script "saver-control":
```

#!/bin/bash

if [ "$1" != "false" ] && [ "$1" != "true" ]; then
	echo Usage:
	echo saver-control false      disable KDE screensaver
	echo saver-control true       enable KDE screensaver
	exit
fi

if [ "$1" == "false" ]; then
	msg="Screensaver DISabled"
else
	msg="Screensaver Enabled"
fi

kde4=`ps -A | grep kded4`
if [ "$kde4" == "" ]; then
	#KDE3
	dcop kdesktop KScreensaverIface enable $1 > /dev/null
	dcop kded kmilod displayText "$msg"
else
	#KDE4
	if [ "$1" == "false" ]; then
		# following method disabled - not working
		#qdbus org.kde.screensaver /ScreenSaver Inhibit "saver-control" "userrequest"
		saver-suspend &
	else
		#qdbus org.kde.screensaver /ScreenSaver UnInhibit 0
		killall -q -u `whoami` saver-suspend
		killall -q -u `whoami` mplay-saver-suspend
	fi
	kdialog --title "ScreenSaver" --passivepopup "$msg" 1
fi

exit
```

script "saver-suspend":
```

#!/bin/bash
# keep the screensaver from coming on - KDE4

while (( 1 == 1 ))
do
	qdbus org.kde.krunner /ScreenSaver SimulateUserActivity
	sleep 119
done

```

---

### Post by IgnorantGuru on 2009-09-07
Below is v1.3.0 of mplayerstart.  This works a little differently with the TV.  Instead of creating a new X session, it uses xinerama screen #2 for the TV output, which seems to work more conveniently for KDE4.  So this assumes you have xinerama enabled in xorg.conf, and that screen 2 is your TV.  It can also use a separate X screen instead of xinerama if you change the tvdisplay variable at the top as shown in the example.  This version does not create a new X session as v1.2.0 did, but you can paste in the code from that version above if you want it to do so.

Also, with this TV setup, mplayerstart can now create resume files when playing in TV mode.

There are also a few other changes...

There are some additional command line options for controlling TV mode.  These are useful when bound to shortcut keys.  For example, on my system Win+T sets 'tvonce' (play the next video on the TV), Win+Shift+T sets TV mode off (play videos on computer screen), and Win+Ctrl+T sets TV mode on (play all videos on TV).  (If TV mode is on, output will be sent to xinerama screen 2 every time mplayerstart is run, even without '--tv', or only once if --tvonce was set.  If TV mode is off, the xinerama screen 1 will be used unless '--tv' is specified.)

Also, when playing VOB files, it will now automatically choose the english (en) audio track.

I think those are the only changes from 1.2.0.  This version uses the same .resume file format as 1.2.0.  The argument parsing is still clumsy in that it requires all TV options to be first on the command line.  That should be rewritten (the script has outgrown the original simple parser), but for now just be sure any --tv... options precede everything else, and options preceed the filename.

```

#!/bin/bash
# mplayerstart  v1.3.0

# === User Data Section ===========================================================

# Location of resume files and temp files; 100MB free space required
data=""

# Optional: Parent folder(s) of your audio & video files for
#           searching for moved resumes
#           If you pass a .resume file to mplayerstart which contains
#           an invalid location for the media file (perhaps you moved it),
#           mplayerstart will recursively search these folders for the file
search1=""
search2=""
#tvdisplay="-display :0.1"		# for separate X screens
tvdisplay="-xineramascreen 2"   # for TV on second xinerama screen
moptions="-vo xv"

# =================================================================================

curuser=`whoami`
if [ "$data" == "" ]; then
	data="/home/$curuser/.mplayerstart"
fi
if [ "$1" == "" ] || [ "$1" == "--help" ]; then
	echo
	echo "Disables KDE screensaver, restores last KDE volume level,"
	echo "starts mplayer in full-screen mode, sends output to TV,"
	echo "and creates resume file for future play."
	echo "Usage: mplayerstart [OPTIONS] ~/video/movie1.avi"
	echo "Usage: mplayerstart [OPTIONS] ~/video/movie1.avi.resume"
	echo "Usage: mplayerstart --resumelast"
	echo "Usage: mplayerstart --resumepre"
	echo "Usage: mplayerstart --rewind"
	echo "Usage: mplayerstart --tvonce"
	echo "Usage: mplayerstart --tvonce --resume"
	echo "Usage: mplayerstart --tvmode VALUE"
	echo "Option: --tv            sends output to $tvdisplay (for TV-out)"
	echo "                        Note: ignored when playing audio files"
	echo "                        Note: TV options must preceed all other options"
	echo "Option: --tvonce        prepares to play only the next video on TV-out"
	echo "Option: --tvmode 0      turns TV-out mode off for future videos; cancels tvonce"
	echo "Option: --tvmode 1      turns TV-out mode on for future videos"
	echo "Option: --resume        resumes playing from last stop point"
	echo "                        (requires filename of media file or resume file)"
	echo "Option: --resumelast    resumes playing last played media file"
	echo "Option: --resumepre     resumes playing previous-to-last played media file"
	echo "Option: --rewind        deletes last played resume file"
	echo "Note: Options must preceed filename; TV options must preceed all options"
	echo "Note: Resume files are auto-deleted after 60 days."
	echo
	echo "Current data folder for resume files: $data"
	echo
	exit
fi

# Determine KDE version
kde4=`ps -A | grep " kded4"`
kde3=`ps -A | grep " kdesktop"`
if [ "$kde4" != "" ]; then
	usekde=4
elif [ "$kde3" != "" ]; then
	usekde=3
else
	usekde=0
fi

if (( usekde == 3 )); then
	# Primary kmix volume channel to restore
	master="0"
	# Secondary kmix volume channel to restore
	pcm="2"
	# get initial volume levels
	mastervol=`dcop kmix Mixer0 volume $master`
	pcmvol=`dcop kmix Mixer0 volume $pcm`
elif (( usekde == 4 )); then
	dbus="qdbus org.kde.kmix /Mixer0"
	# Primary kmix volume channel to restore
	master="Master:0"
	# Secondary kmix volume channel to restore
	pcm="PCM:0"
	# get initial volume levels
	mastervol=`$dbus volume $master`
	pcmvol=`$dbus volume $pcm`
fi

# Initializations
filename=""
restime=0
outfile=""
resume=0
resumeplay=""
tv=0
seektime=""
rx=0
vf="-fs"

mkdir -p "$data/"

if [ "$1" == "--tv" ]; then
	shift
	tv=1
fi

if [ "$1" == "--tvonce" ]; then
	touch "$data/tv-once"
	rm -f "$data/tv-mode"
	if (( usekde == 3 )); then
		dcop kded kmilod displayText "TV Once"
	elif (( usekde == 4 )); then
		kdialog --title "Mplayer" --passivepopup "TV Once" 1
	fi
	exit
fi

if [ "$1" == "--tvmode" ]; then
	if [ "$2" == "0" ] || [ "$2" == "off" ]; then
		rm -f "$data/tv-mode"
		rm -f "$data/tv-once"
		tvmode="OFF"
	else
		touch "$data/tv-mode"
		tvmode="ON"
	fi
	if (( usekde == 3 )); then
		dcop kded kmilod displayText "TV Mode $tvmode"
	elif (( usekde == 4 )); then
		kdialog --title "Mplayer" --passivepopup "TV Mode $tvmode" 1
	fi
	exit
fi

if [ "$1" == "--resume" ]; then
	shift
	resume=1
fi

if [ "$1" == "--resumepre" ]; then
	# Find most recently modified resume file and touch it
	cd "$data"
	lastresume=`ls -1t *.resume 2> /dev/null | head -n 1`
	if [ "$lastresume" == "" ]; then
		echo "No resume file found"
		if (( usekde == 3 )); then
			dcop kded kmilod displayText "No resume file found"
		elif (( usekde == 4 )); then
			kdialog --title "Mplayer" --passivepopup "No resume file found" 1
		fi
		exit
	fi
	touch --date="2000-01-01 00:00" "$data/$lastresume"
	lastresume=""
fi

if [ "$1" == "--resumelast" ] || [ "$1" == "--resumepre" ] || [ "$1" == "--rewind" ]; then
	# Find most recently modified resume file
	cd "$data"
	lastresume=`ls -1t *.resume 2> /dev/null | head -n 1`
	if [ "$lastresume" == "" ]; then
		echo "No resume file found"
		if (( usekde == 3 )); then
			dcop kded kmilod displayText "No resume file found"
		elif (( usekde == 4 )); then
			kdialog --title "Mplayer" --passivepopup "No resume file found" 1
		fi
		exit
	fi
	if [ "$1" == "--rewind" ]; then
		rm "$data/$lastresume"
		if (( usekde == 3 )); then
			dcop kded kmilod displayText "Rewind"
		elif (( usekde == 4 )); then
			kdialog --title "Mplayer" --passivepopup "Rewind" 1
		fi
		exit
	else
		nowplaying="$data/$lastresume"
		resume=1
		shift
	fi
else
	nowplaying="$1"
fi

if [ "$nowplaying" == "" ] || [ ! -e "$nowplaying" ]; then
	echo 'File not found: '"$1"
	if (( usekde == 3 )); then
		dcop kded kmilod displayText "File not found"
	elif (( usekde == 4 )); then
		kdialog --title "Mplayer" --passivepopup "File not found" 1
	fi
	exit
fi

# resume file was passed on the command line?
if [ "${nowplaying##*.}" == "resume" ]; then
	resume=1
fi

# get resume info
if (( resume == 1 )); then
	# locate resume file
	if [ "${nowplaying##*.}" == "resume" ]; then
		# resume file was passed on the command line
		resumefile="$nowplaying"
	else
		resumefile="$data/`basename "$nowplaying"`.resume"
	fi
	# read resume file if present
	if [ -e "$resumefile" ]; then
		lcount=0
		seektime=""
		# Set the field seperator to a newline
		IFS="
		"
		for line in `cat "$resumefile"`;do
			case $lcount in
			0 ) seektime="$line";;
			1 ) resumeplay="$line";;
			2 ) mastervol="$line";;
			3 ) pcmvol="$line";;
			esac
			(( lcount +=1 ))
		done
		IFS=" "
		# compensate for volume loss
		(( mastervol += 3 ))
		(( pcmvol += 3 ))
		if [ "$seektime" != "" ]; then
			if [ "${nowplaying##*.}" == "resume" ]; then
				if [ "$resumeplay" == "" ]; then
					# accomodate prior versions of mplayerstart
					nowplaying=`basename "$nowplaying" ".resume"`
				else
					nowplaying="$resumeplay"
				fi
				if [ "$resumeplay" == "" ] || [ ! -e "$nowplaying" ]; then
					# find resumed file
					cleanname=`basename "$nowplaying"`
					# replace troublesome characters
					cleanname=${cleanname//"["/"\["}
					cleanname=${cleanname//"]"/"\]"}
					cleanname=${cleanname//"^"/"\^"}
					cleanname=${cleanname//"?"/"\?"}
					cleanname=${cleanname//"*"/"\*"}
					cleanname=${cleanname//"&"/"\&"}
					# search
					if [ "$search1" != "" ]; then
						if [ "$search2" == "" ]; then
							nowplaying=`find -H "$search1" -type f -name "$cleanname"`
						else
							nowplaying=`find -H "$search1" "$search2" -type f -name "$cleanname"`
						fi
						# extract the first file listed
						nowplaying=${nowplaying%%$'\n'*}
					else
						nowplaying=""
					fi
				fi
				if [ "$nowplaying" == "" ] || [ ! -e "$nowplaying" ]; then
					echo 'File not found'
					if (( usekde == 3 )); then
						dcop kded kmilod displayText "File not found"
					elif (( usekde == 4 )); then
						kdialog --title "Mplayer" --passivepopup "File not found" 1
					fi
					exit
				fi
			fi
			echo "Resuming at $seektime seconds"
			seektime="-ss $seektime"
			# Resume volume levels
			if (( usekde == 3)); then
				dcop kmix Mixer0 setVolume $master $mastervol
				dcop kmix Mixer0 setVolume $pcm $pcmvol
			elif (( usekde == 4 )); then
				$dbus setVolume $master $mastervol
				$dbus setVolume $pcm $pcmvol
			fi
		fi
	fi
fi

# one-time tv mode
if [ -e "$data/tv-once" ]; then
	tv=1
	rm "$data/tv-once"
fi

# tv mode
if [ -e "$data/tv-mode" ]; then
	tv=1
fi

# set output filename
if [ ! -e "$data/resume-lock" ]; then
	filename=`basename "$nowplaying"`
	rand=`uuidgen -r`
	rand=${rand:24}
	outfile="$data/$filename.$rand.log"
fi

# cleanup
# delete output files older than 6 days
find -L $data -maxdepth 0 -type f -mtime +6 -name "*.log" -execdir rm {} \;
# delete resume files older than 60 days
find -L $data -maxdepth 0 -type f -mtime +60 -name "*.resume" -execdir rm {} \;

# Get file extension all uppercase
filetype=`echo "${nowplaying##*.}" | tr a-z A-Z`

# Audio or video?
if [ "$filetype" == "MP3" ] || [ "$filetype" == "WMA" ] || [ "$filetype" == "FLAC" ] || [ "$filetype" == "WAV" ] || [ "$filetype" == "OGG" ] || [ "$filetype" == "M4A" ] || [ "$filetype" == "AC3" ] || [ "$filetype" == "AAC" ] || [ "$filetype" == "RM" ] || [ "$filetype" == "RAM" ]; then
	video=0
	# play audio file
	if [ "$outfile" == "" ]; then
		gmplayer $seektime "$nowplaying"
	else
		gmplayer $seektime "$nowplaying" > "$outfile"
	fi
else
	video=1
	# if playing a vob file, use english audio track
	if [ "$filetype" == "VOB" ]; then
		aid=" -alang en"  # OR -aid 129
	else
		aid=""
	fi
	#disable KDE screensaver
	if (( usekde == 3 )); then
		dcop kdesktop KScreensaverIface enable false > /dev/null
	elif (( usekde == 4 )); then
		if [ -e "$data/mplay-saver-suspend" ]; then
			"$data/mplay-saver-suspend" &
			saverpid=$!
		else
			echo '#!/bin/bash' > "$data/mplay-saver-suspend"
			echo '# keep the screensaver from coming on - KDE4' >> "$data/mplay-saver-suspend"
			echo 'while (( 1 == 1 ))' >> "$data/mplay-saver-suspend"
			echo 'do' >> "$data/mplay-saver-suspend"
			echo 'qdbus org.kde.krunner /ScreenSaver SimulateUserActivity' >> "$data/mplay-saver-suspend"
			echo 'sleep 119' >> "$data/mplay-saver-suspend"
			echo 'done' >> "$data/mplay-saver-suspend"
			chmod u+x "$data/mplay-saver-suspend"
			"$data/mplay-saver-suspend" &
			saverpid=$!
		fi
	fi
	# play video file
	if (( tv == 0 )); then
		tvdisplay=""
	fi
	if [ "$outfile" == "" ]; then
		mplayer $moptions $tvdisplay $vf $aid $seektime "$nowplaying"
	else
		mplayer $moptions $tvdisplay -fs$aid $seektime "$nowplaying" > "$outfile"
	fi
fi

# process outfile - determine resume time
if [ "$outfile" != "" ] && [ -e "$outfile" ]; then
	mout=`tail --bytes=350 "$outfile"`
	if (( video == 1 )); then
		# did mplayer reach end of file?
		endoffile=${mout##*End of file)}	
		if [ "$endoffile" != "" ]; then
			restime=${mout##* V:}
			restime=${restime%% A-V:*}
			restime=${restime%%.*}
		fi
	else
		# calculate remaining audio seconds
		atime=${mout##*A:}
		atime=${atime%%.*}
		btime=${mout##*of}
		btime=${btime%%.*}
		(( remain = btime - atime ))
		if (( remain > 15 )); then
			restime=$atime
		fi
	fi
	rm "$outfile"
fi

# save resume file
(( rx = restime - 5 ))
if (( rx > 10 )); then
	echo "$rx" > "$data/$filename.resume"
	echo "$nowplaying" >> "$data/$filename.resume"
	if (( usekde == 3 )); then
		mastervol=`dcop kmix Mixer0 volume $master`
		pcmvol=`dcop kmix Mixer0 volume $pcm`
	elif (( usekde == 4 )); then
		mastervol=`$dbus volume $master`
		pcmvol=`$dbus volume $pcm`
	else
		# dummy volume for non-KDE
		mastervol="50"
		pcmvol="50"
	fi
	echo $mastervol >> "$data/$filename.resume"
	echo $pcmvol >> "$data/$filename.resume"
	echo "Resume file created: $rx seconds"
else
	rm -f "$data/$filename.resume"
fi

if (( usekde == 3)); then
	# enable KDE3 screensaver
	dcop kdesktop KScreensaverIface enable true > /dev/null
elif (( usekde == 4 )); then
	# cancel KDE4 saver-suspend
	kill $saverpid
fi

exit

```

---

### Post by IgnorantGuru on 2009-11-11
Version 1.3.1 and future updates to this script are now posted to my blog at
[http://igurublog.wordpress.com/downloads/script-mplayerstart/](http://igurublog.wordpress.com/downloads/script-mplayerstart/)

---

### Post by IgnorantGuru on 2010-01-22
Version 1.4.0 of mplayerstart is available. This update adds more flexibility for various TV display setups, including Xinerama, separate X displays, and once again the ability to xinit a display just for mplayer. This also adds an “auto” tvmode which uses the current display for playback. Also, mplayerstart now stops the X, KDE3, KDE4, and Gnome screensavers during playback. Plus, mplayerstart pops up dialogs using either Xdialog or kdialog, to give feedback on functions like rewind. The volume level restoration code has also been rewritten to use amixer, which should be more portable.
[http://igurublog.wordpress.com/downloads/script-mplayerstart/](http://igurublog.wordpress.com/downloads/script-mplayerstart/)

---

