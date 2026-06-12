---
title: "Using &quot;appropriate copy or move commands&quot; in a bash script after mythlink.pl runs"
date: 2014-03-29
forum: Mythbuntu
---

### Post by Iago6776 on 2014-03-29
At the mythlink.pl wiki page [http://www.mythtv.org/wiki/Mythlink.pl](http://www.mythtv.org/wiki/Mythlink.pl) the intro paragraph states: "[COLOR=#000000][FONT=sans-serif]Once you have created a directory of readable symlinks, the show can be archived with the link's name using appropriate copy or move commands.[/FONT][/COLOR]"

I have a script that makes a copy of the video file that I intend to use as a User Job.. I can get mythlink.pl to run any time I want it to run and, since I don't use those names to watch the files, I can parse the mythlink.pl command to include the %CHANID% and %STARTTIME%. 

What copy or move commands are needed to use the name of a link to file A ([COLOR=#000000]${INDIR}/${CHANID}_${STARTTIME}.* where * is either mpg or nuv, separate question, see [here]("http://ubuntuforums.org/showthread.php?t=2214013"))[/COLOR] to name file B ([COLOR=#000000]${OUTDIR}/${CHANID}_${STARTTIME})[/COLOR], using %CHANID% and %STARTTIME% to define file A and remove %CHANID% and %STARTTIME% from the name of file B?

Here are the mythlink.pl arguments and the user job so far:
```
[COLOR=#000000][FONT=Ubuntu Mono]mythlink.pl --link /var/lib/mythtv/pretty --format '%T %- %S%-%c_%Y%m%d%H%i%s[/FONT][/COLOR]
```

```
[COLOR=#000000]#! /bin/bash
%STARTTIME 
scriptstarttime=$(date +%F-%H%M%S)

CHANID=$1
STARTTIME=$2

INDIR="/var/lib/mythtv/recordings"
OUTDIR="/home/username/Dropbox"
PROG="/home/username/bin/ffmpeg"
PARAMS="-y -stats -deinterlace -vcodec libx264 -vprofile baseline -level 13 -maxrate 76800 -bufsize 3000000 -acodec libfdk_aac -ac 2 -ab 128k -ar 44100 -sn"

LOGFILE="/home/username/Dropbox/DropboxTranscode.log"
OUTFILE="${OUTDIR}/${CHANID}_${STARTTIME}"

COMMAND="${PROG} -i ${INDIR}/${CHANID}_${STARTTIME}.mpg ${PARAMS} ${OUTFILE}.mp4"

touch $LOGFILE
chown mythtv:mythtv $LOGFILE
chmod 777 $LOGFILE
echo "$scriptstarttime Dropbox Transcode" >> $LOGFILE
echo "${COMMAND}" >> $LOGFILE
$COMMAND >> $LOGFILE 2>&1

[/COLOR]
```

Thanks,
Iago6776

---

### Post by blm-ubunet on 2014-03-30
Sorry don't understand what you are doing.

I think you are trying to use actual recordings & the job queue to perform actions on files (symlinks made by mythlink) to the actual recording file.

If you want to archive an actual file from a symlink you must copy & de-reference the symlink:
```
cp -L source destination-dir
```

Can you break down the problem into small soluble steps?

---

### Post by Iago6776 on 2014-03-30
Say I have a recording a TV series called "Linux" with the subtitle "Ubuntu." the channel ID is, according to the database it's, say, 1085. The recording start time, according to my database, was 20140328190000. That night, mythlink.pl runs in its cron job and makes a link called "Linux - Ubuntu 1085_20140328190000.mpg" in the directory /var/lib/mythtv/pretty that points to /var/lib/mythtv/recordings/1085_20140328190000.mpg. 
With my script, I don't want to do anything but make a shrunken copy of that /var/lib/mythtv/recordings/1085_20140328190000.mpg file in my Dropbox directory but I want to name the h264/aac mp4 file "Linux - Ubuntu.mp4".

---

### Post by steeldriver on 2014-03-30
Are you asking about manipulating a filename string within a shell variable?

To remove a trailing sequence (such as the .mpg) suffix from a variable in bash, the bash recipe is *${var%pattern}* where *var* is the variable name and *pattern* is the sequence you want to remove. A variant *${var**%%**pattern} *is similar but tries to remove the *longest* matching sequence. So for example:

```

$ filename="Linux - Ubuntu 1085_20140328190000.mpg"
$ echo "**${filename%.mpg}**"
Linux - Ubuntu 1085_20140328190000

```

You can extend this using some *shell globbing* tricks e.g. to remove the *longest* trailing sequence consisting wholly of digits followed by .mpg I *think* you could do something like

```
$ echo "**${filename%%*([0-9]).mpg}**"
Linux - Ubuntu 1085_

```

or to remove the longest trailing sequence consisting of a single space followed by *digits*-underscore-*digits*.mpg

```
$ echo "**${filename%% *([0-9])_*([0-9]).mpg}**"
Linux - Ubuntu

```

You could also pipe the string through a variety of true regex based tools (sed, awk, perl...) instead of bash substitutions / globs. I'm not sure which is a better solution. 

You can concatenate the new suffix in the same expression e.g.

```

$ newname="${filename%% *([0-9])_*([0-9]).mpg}.mp4"
$ echo "$newname"
Linux - Ubuntu.mp4

```

See more at [http://tldp.org/LDP/abs/html/string-manipulation.html](http://tldp.org/LDP/abs/html/string-manipulation.html)

---

### Post by Iago6776 on 2014-04-08
More than that, steeldriver, I'm looking to use the name of the link to the first file to name the file I create by running a script on that same file. If I can help it, without having to edit the name of the link.

---

### Post by blm-ubunet on 2014-04-09
Pass the variables %TITLE% & %SUBTITLE$ to your user-job script (along with the filename &/or starttime-chanid)
[http://www.mythtv.org/wiki/User_Jobs](http://www.mythtv.org/wiki/User_Jobs)

I don't see what you need "mythlink" for ?? Was it the nice file naming ?

---

### Post by Iago6776 on 2014-04-13
I haven't been able to find out why %TITLE% and %SUBTITLE% don't work in this script, I've tried using them and found that mythlink works flawlessly where as:
%TITLE% for "Daniel Tiger's Neighborhood" returns "Daniel" 
And
%SUBTITLE% returns the TV episode's description or the movie's... nothing.

---

### Post by blm-ubunet on 2014-04-13
If you are using simple command line parsing then always enclose each parameter (that could have spaces) in quotes.
Your title has spaces which defeats simple parameter passing..

The user-job line in mythtv becomes:
```
/path/my-user-job "%TITLE%"
```

---

