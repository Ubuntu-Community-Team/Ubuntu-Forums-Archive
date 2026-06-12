---
title: "abcde Assistance"
date: 2009-11-03
forum: Multimedia Software
---

### Post by justinmiller87 on 2009-11-03
The following is my .abcde.conf file:
```

# -----------------$HOME/.abcde.conf----------------- #
# 
# A sample configuration file to convert music cds to 
#       MP3 format using abcde version 2.3.99.6
# 
#       Modified from:
#       http://andrews-corner.org/abcde.html
# -------------------------------------------------- #

# Specify the encoder to use for MP3. In this case
# the alternatives are gogo, bladeenc, l3enc, xingmp3enc, mp3enc.
MP3ENCODERSYNTAX=/usr/bin/lame 

# Specify the path to the selected encoder. In most cases the encoder
# should be in your $PATH as I illustrate below, otherwise you will 
# need to specify the full path. For example: /usr/bin/lame
LAME=lame

# Specify your required encoding options here. Multiple options can
# be selected as '--preset standard --another-option' etc.
LAMEOPTS='--preset insane' 

# Output type for MP3.
OUTPUTTYPE="mp3"

# The cd ripping program to use. There are a few choices here: cdda2wav,
# dagrab, cddafs (Mac OS X only) and flac.
CDROMREADERSYNTAX=cdparanoia            
                                     
# Give the location of the ripping program and pass any extra options:
CDPARANOIA=cdparanoia  
CDPARANOIAOPTS="--never-skip=40"

# Give the location of the CD identification program:       
CDDISCID=cd-discid            
                               
# Give the base location here for the encoded music files.
OUTPUTDIR="$HOME/music/"               

# Decide here how you want the tracks labelled for a standard 'single-artist',
# multi-track encode and also for a multi-track, 'various-artist' encode:
OUTPUTFORMAT='${OUTPUT}/${GENRE}/${ARTISTFILE}/${ALBUMFILE}/${TRACKNUM}_-_${ARTISTFILE}_-_${TRACKFILE}'
VAOUTPUTFORMAT='${OUTPUT}/${GENRE}/Various_Artists/${ALBUMFILE}/${TRACKNUM}_-_${ARTISTFILE}-${TRACKFILE}'

# Decide here how you want the tracks labelled for a standard 'single-artist',
# single-track encode and also for a single-track 'various-artist' encode.
# (Create a single-track encode with 'abcde -1' from the commandline.)
ONETRACKOUTPUTFORMAT='${OUTPUT}/${GENRE}/${ARTISTFILE}/${ALBUMFILE}/${ALBUMFILE}'
VAONETRACKOUTPUTFORMAT='${OUTPUT}/${GENRE}/Various_Artists/${ALBUMFILE}/${ALBUMFILE}'

# Put spaces in the filenames instead of the more correct underscores:
mungefilename ()
{
  echo "$@" | sed s,:,-,g | tr / _ | tr -d \'\"\?\[:cntrl:\]
}

# What extra options?
MAXPROCS=2                              # Run a few encoders simultaneously
PADTRACKS=y                             # Makes tracks 01 02 not 1 2
EXTRAVERBOSE=y                          # Useful for debugging
EJECTCD=y                               # Please eject cd when finished :-)

```
When I rip a CD, it creates the proper folder, pulls the files off in wav format, but it didn't copy them over after encoding. I got the following error for all 20 tracks on the disc:
```

[ERROR] abcde: The following commands failed to run:
movetrack-01: returned code 1: mv /home/justin/abcde.170fea14/track01.mp3 /home/justin/music//mp3/soundtrack/Various_Artists/Glee The Music- Season One, Volume One (Extra Tracks)/01_-_Cory Monteith (Finn) & Lea Michelle (Rachel)-Dont Stop Believin.mp3
```

What is code 1 anyway? The files seem to have disappeared as well.

---

### Post by andrew.46 on 2009-11-04
Hi,

Seems a little odd, but try the following in your .abcde.conf file:

```
# Give the base location here for the encoded music files.
OUTPUTDIR="$HOME/music" 
```

which omits the '/' after $HOME/music.

Andrew

---

