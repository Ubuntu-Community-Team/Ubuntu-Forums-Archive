---
title: "cue splitter nautilus script and some questions"
date: 2008-08-12
forum: Multimedia Software
---

### Post by araz_233 on 2008-08-12
I've been searching for a while for a good audio format conversion and cue splitter for ubuntu until I found audio-convert script for conversion here:
[https://savannah.nongnu.org/projects/audio-convert/]("https://savannah.nongnu.org/projects/audio-convert/"). 
I tried to write another script like that for cue splitting myself:
> 
#!/bin/bash
set -x

version="0.0.1"
#################################################
#       TRADUCTIONS
        ###### Default = English #####
        title="cue splitter "$version""
        not_cue_file="not a cue file."
        not_cue_tools="you don't have cuetools"
	not_shnsplit="you don't have shntool"
	not_audio_file="expected audio file not found: "
	no_codec="you don't have the right codec to decode the selected file. missin' codec:"
        choix="extension of output file:"
	ask_prefix="Output Files Prefix:"
	splitting="Splitting "
        warning="warning"

#functions
is_cue()
{
	file -b "$1" | grep 'text' || echo $1 | grep -i '\.cue$'
}

is_mp3 ()
{
	file -b "$1" | grep 'MP3' || echo $1 | grep -i '\.mp3$'
}

is_ogg()
{
	file -b "$1" | grep 'Vorbis' || echo $1 | grep -i '\.ogg$'
}

is_mpc()
{
	file -b "$1" | grep 'Musepack' || echo $1 | grep -i '\.mpc$'
}

is_flac()
{
	file -b "$1" | grep 'FLAC' || echo $1 | grep -i '\.flac$'
}

is_mac()
{
	file -b "$1" | grep 'Monkey' && echo $1 | grep -i '\.ape$'
}

is_aac()
{
	file -b "$1" | grep 'AAC' || echo $1 | grep -i '\.aac$'
}

is_wav()
{
	file -b "$1" | grep 'WAVE' || echo $1 | grep -i '\.wav$'
}

is_wma()
{
	file -b "$1" | grep 'Microsoft' || echo $1 | grep -i '\.wma$'
}

TrapBreak () {
  trap "" HUP INT TERM
  # if mplayer or ffmpeg or zenity are still running, kill them
  [ -n "$zenpid" ] && kill "$zenpid" 2>/dev/null
  [ -n "$pid" ] && kill "$pid" 2>/dev/null
  killall mac 2>/dev/null
  exit 1
}


#main program
if !(which cuebreakpoints 2>/dev/null)
then
	zenity --error --title="$warning" --text="$not_cue_tools"
        exit 1
fi
if !(which shnsplit 2>/dev/null)
then
	zenity --error --title="$warning" --text="$not_shnsplit"
        exit 1
fi
if !(is_cue "$1")
then
	zenity --error --title="$warning" --text="$not_cue_file"
        exit 1
fi
audio_file=`echo "$1" | sed 's/.cue/''/'`
if !(ls "$audio_file" | grep -v "^ls")
then
	zenity --error --title="$warning" --text="$not_audio_file '$audio_file'"
        exit 1
fi

depformat="shn wav aiff flac ape ofr lpac wv mp3"

#get output format
while [ ! "$formatout" ] 
do
        formatout=`zenity --title "$title" --list --column="Format" $depformat --text "$choix"`
        if  [ $? != 0 ]; then
                exit 1
        fi
        [ $? -ne 0 ] && exit 2 
done

#does not work yet
#todo: find out how custom encoders work with shnsplit

if [ "$formatout" == "mp3" ]
then
	formatout=`echo "cust ext=mp3 lame %f"`
fi

prefix=`echo "$audio_file" | sed 's/\.\w*$/''/'`
prefix=`zenity --entry --title="$title" --text="$ask_prefix" --entry-text="$prefix"`

#todo: zenity progress does not kill process on cancel when conversion format is flac or ape
trap TrapBreak HUP INT TERM

log_file=`echo "$1" | sed 's/.cue/'.log'/'`

(cuebreakpoints $1 | shnsplit -o $formatout -a $prefix $audio_file) &
pid=$!
#todo: a better look
zenity --progress --auto-kill --pulsate --title="$title" --text="$splitting $1" --auto-close &
zenpid=$!
 

of course it has some problems:
first, I couldn't run shnsplit with custom encoding formats like mp3
second, when encoding format is ape or flac, zenity's cancell button won't kill running processes
third, I tried to create a zenity with text output from shnsplit and percentage like that from terminal but couldn't.

I thought it might be helpfull for some. please give me a hint if you know where I am wrong on doing those things.

anybody know any good audio splitter or audio extracting from video softwares?

cheers

---

### Post by cozmicharlie on 2008-08-13
I am not that familiar with what you doing but maybe I can point you in a direction that might help until someone that knows more than me helps.

This link may have something to help you [http://www.linux.com/feature/132872](http://www.linux.com/feature/132872)

Also, one problem you may be having is shn is very poorly supported in Ubuntu.  The newer ffmpeg should have support for shn but it just does not work very well.

You can install shn though and it may help.  See this tutorial - scroll down to the section on installing shn.

[http://ubuntuforums.org/showthread.php?t=833164&highlight=shn](http://ubuntuforums.org/showthread.php?t=833164&highlight=shn)

---

### Post by araz_233 on 2008-08-18
made some improvements... I've added mp3splt for ogg and mp3 files. but still I can't print stdout into zenity --text-info. not in shnsplit and nor with mp3splt.
do anybody know how this zenity works?

---

### Post by dannymichel on 2009-08-28
> **araz_233 said:**
> made some improvements... I've added mp3splt for ogg and mp3 files. but still I can't print stdout into zenity --text-info. not in shnsplit and nor with mp3splt.
do anybody know how this zenity works?

anybody else test this?

---

