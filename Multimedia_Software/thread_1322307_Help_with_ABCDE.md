---
title: "Help with ABCDE"
date: 2009-11-10
forum: Multimedia Software
---

### Post by dnitious on 2009-11-10
Hello All!!  I have been trying to rip my music collection with abcde.  I want it to rip to flac (archiving) and mp3 (to put on my player) at the same time.  The problem I'm having is that it will do this only if I type in **abcde -o flac,mp3**.  But when it rips, it rips the mp3 to cbr 128.  I want it to rip to vbr highest quality or cbr 256.  When I type in "**abcde -o mp3:"-V 0**" it does rip to HQ VBR.  When I type "**abcde -o mp3:"-b 256**" it will encode to cbr 256.  But when I type "**abcde -o flac,mp3:"-b 256**" or the same thing but with "**-V 0**" it will only encode the flac and the mp3 @ cbr128.  I want to encode both at the same time but when I do mp3 solo, it works fine and when I do flac and mp3 together it does both but mp3 at 128.  how do I get it to encode both with the mp3 at HQ vbr or 256 cbr?  I've been messing with this for days and can't  seem to solve it.  Below is my abcde conf. file.  thanks in advance for any help.

# System defaults for abcde version 2.2.x
# Nothing in this file is uncommented by default.
# 
# If you wish to override these system-wide settings, create your own
# .abcde.conf file in your home directory.

# CDDB options

# If you wish to use a different CDDB server, edit this line.
# If you just wanted to use a proxy server, just set your http_proxy
# environment variable - wget will use it correctly.
#CDDBURL="http://freedb.freedb.org/~cddb/cddb.cgi"

# The CDDB protocol level.
# Right now 5 is latin1 output and 6 is UTF8 encoding.
#CDDBPROTO=6

# The CDDB protocol requires hello information, including a valid username
# and hostname. If you feel paranoid about giving away such info, edit this
# line - the format is username@hostname.
#HELLOINFO="`whoami`@`hostname`"

# This controls the email address CDDB changes are submitted to.
#CDDBSUBMIT=freedb-submit@freedb.org

# The following options control whether or not fetched CDDB entries
# are cached locally in $CDDBLOCALDIR
#CDDBCOPYLOCAL="n"
#CDDBLOCALDIR="$HOME/.cddb"
#CDDBLOCALRECURSIVE="n"

# If NOSUBMIT is set to y, then abcde will never prompt asking if you
# wish to submit your edited cddb file.
#NOSUBMIT=y

# If NOCDDBQUERY is set to y, then abcde will never even try to access
# the CDDB server; running abcde will automatically drop you into a
# blank cddb file to edit at your leisure.  This is the same as the
# -n option.  NOCDDBQUERY=y implies NOSUBMIT=y.
#NOCDDBQUERY=n

# Select here if you want to use the locally stored CDDB entries.
# This is useful if you do a lot of editing to those CDDB entries. 
# Also, other tools like Grip store CDDB entries under $HOME/.cddb,
# so they can be reused when ripping CDs.
#CDDBUSELOCAL="n"

# List, separated with a comma, the fields we want the parsing function to
# output. Defaults to YEAR and GENRE, for a complete list of fields provided by
# CDDB.
# The fields are not case sensitive. Actually, "y,g" will work as fine as "Y,G"
# or "YEAR, GENRE"
#SHOWCDDBFIELDS=year,genre

# Specify the style of encoder to use here - 
# oggenc, vorbize - for OGGENCODERSYNTAX
# lame, gogo, bladeenc, l3enc, xingmp3enc, mp3enc - for MP3ENCODERSYNTAX
# flac - the only supported for FLACENCODERSYNTAX at the moment
# speexenc - the only encoder for SPEEXENCODERSYNTAX
# mppenc - encoder for MPPENCODERSYNTAX
# default is a valid option for oggenc, lame, flac, speexenc and mppenc.
# Currently this affects the default location of the binary, the variable
# to pick encoder command-line options from, and where the options are
# given.
#MP3ENCODERSYNTAX=lame
#OGGENCODERSYNTAX=default
#FLACENCODERSYNTAX=flac
#SPEEXENCODERSYNTAX=default
#MPPENCODERSYNTAX=default
#AACENCODERSYNTAX=default

# Specify the syntax of the normalize binary here - so far only 'normalize'
# is supported.
#NORMALIZERSYNTAX=default

# CD reader program to use - currently recognized options are 'cdparanoia',
# 'cdda2wav', 'dagrab', 'cddafs' (Mac OS X only) and 'flac'.
#CDROMREADERSYNTAX=cdparanoia

# CUE reader syntax for the CUE reader program to use.
# abcde supports 2 CUE modes: 'mkcue' and 'abcde.mkcue' so you can set the
# MKCUE variable accordingly. The 'abcde.mkcue' uses an internal
# implementation, without the need of an external program.
#CUEREADERSYNTAX=default

# Specify the program to convert a CUE sheet back to a CD disc ID for CDDB queries.
# Select between '/path/to/cue2discid' (provided as an example) or
# 'abcde.cue2discid', implemented internaly.
#CUE2DISCID=abcde.cue2discid

# Keep the wav files after encoding. Set it to "y" and remove "clean" from
# the list of default actions, since we purge the temp directory as default.
#KEEPWAVS=n

# Track padding: force abcde to pad tracks using 0, so every song uses a two
# digit entry. If set to "y", even a single song encoding outputs a file like
# 01.my_song.ext
#PADTRACKS=y

# Define if you want abcde to be non-interactive.
# Keep in mind that there is no way to deactivate it right now in the command
# line, so setting this option makes abcde to be always non-interactive.
#INTERACTIVE=n

# Specify 'nice'ness of the encoder, the CD reader and the distmp3 proc.
# This is a relative 'nice'ness (that is, if the parent process is at a
# nice level of 12, and the ENCNICE is set to 3, then the encoder will
# run with an absolute nice value of 15. Note also, that setting these
# to be empty will result in some default niceness increase (4 in tcsh
# and 10 using the bsdutils' nice).
#ENCNICE=10
#READNICE=10
#DISTMP3NICE=10

# Paths of programs to use
#LAME=lame
#TOOLAME=toolame
#GOGO=gogo
#BLADEENC=bladeenc
#L3ENC=l3enc
#XINGMP3ENC=xingmp3enc
#MP3ENC=mp3enc
#VORBIZE=vorbize
#OGGENC=oggenc
#FLAC=flac
#SPEEXENC=speexenc
#MPPENC=mppenc
#AACENC=faac

#ID3=id3
#ID3V2=id3v2
#CDPARANOIA=cdparanoia
#CDDA2WAV=cdda2wav
#CDDAFS=cp
#CDDISCID=cd-discid
#CDDBTOOL=cddb-tool
#EJECT=eject
#MD5SUM=md5sum
#DISTMP3=distmp3
#VORBISCOMMENT=vorbiscomment
#METAFLAC=metaflac
#NORMALIZE=normalize-audio
#CDSPEED=eject
#VORBISGAIN=vorbisgain
#MKCUE=mkcue
#MKTOC=cdrdao
#DIFF=diff

# Options to call programs with:

# If HTTPGET is modified, the HTTPGETOPTS options should also be defined 
# accordingly. If HTTPGET is changed, the default options will be set,
# if HTTPGETOPTS is empty or not defined.
#HTTPGET=wget
# for fetch (FreeBSD): HTTPGETOPTS="-q -o -"
# for wget: HTTPGETOPTS="-q -O -"
# for curl (MacOSX): HTTPGETOPTS="-f -s"
#HTTPGETOPTS="-q -O -"

# MP3:
#LAMEOPTS='-V 0'
#TOOLAMEOPTS=
#GOGOOPTS=
#BLADEENCOPTS=
#L3ENCOPTS=
#XINGMP3ENCOPTS=
#MP3ENCOPTS=

# Ogg:
#VORBIZEOPTS=
#OGGENCOPTS=

# FLAC:
#FLACOPTS='--verify --best'

# Speex:
#SPEEXENCOPTS=

# MPP/MP+ (Musepack):
# For the encoder options take a look at the manpage. Set them like this:
# MPPENCOPTS='--xtreme' if you wish to set more options then:
# MPPENCOPTS='--xtreme --skip 20 --fade 10'
#MPPENCOPTS=

# M4A/AAC
#AACENCOPTS=

#ID3OPTS=
#ID3V2OPTS=
#CDPARANOIAOPTS="--never-skip=40"
#CDDA2WAVOPTS=
#CDDAFSOPTS="-f"
#CDDBTOOLOPTS=
#EJECTOPTS=
#DISTMP3OPTS=
#NORMALIZEOPTS=
#CDSPEEDOPTS="-x"
#CDSPEEDVALUE=""
#MKCUEOPTS=""
#MKTOCOPTS=""
#DIFFOPTS=""
#VORBISCOMMENTOPTS="-R"
#METAFLACOPTS="--no-utf8-convert"
#DIFFOPTS=""

# Actions to take
# Comma-separated list of one or more of the following:
#  cddb,cue,read,normalize,encode,tag,move,playlist,clean,default
#   encode implies read
#   normalize implies read
#   tag implies cddb,read,encode
#   move implies cddb,read,encode,tag
#   playlist implies cddb
# An action can be added to the "default" action by specifying it along with
# "default", without having to repeat the default ones:
#  ACTIONS=default,playlist
# The default action list (referenced as "default") is defined in the following
# comment:
#ACTIONS=cddb,read,encode,tag,move,clean

# CD device you want to read from
# It can be defined as a singletrack flac file, but since it might change from
# file to file it makes little sense to define it here.
#CDROM=/dev/cdrom
# If we are using the IDE bus, we need CDPARANOIACDROMBUS defined as "d"
# If we are using the ide-scsi emulation layer, we need to define a "g"
#CDPARANOIACDROMBUS="d"

# If you'd like to make a default location that overrides the current
# directory for putting mp3's, uncomment this.
#OUTPUTDIR="$home/music/"

# Or if you'd just like to put the temporary .wav files somewhere else
# you can specify that here
#WAVOUTPUTDIR=`pwd`

# OUTPUTTYPE can be either "ogg", "mp3", "flac" or "spx", or a combination
# of them separated with ",": "ogg,mp3".
#OUTPUTTYPE="mp3,flac"

# Output filename format - change this to reflect your inner desire to
# organize things differently than everyone else :)
# You have the following variables at your disposal:
# OUTPUT, GENRE, ALBUMFILE, ARTISTFILE, TRACKFILE, and TRACKNUM.
# Make sure to single-quote this variable. abcde will automatically create
# the directory portion of this filename.
# NOTICE: OUTPUTTYPE has been deprecated in the OUTPUTFORMAT string.
# Since multiple-output was integrated we always append the file type
# to the files. Remove it from your user defined string if you are getting
# files like ".ogg.ogg".
#OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}--${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}--${TRACKFILE}'

# Like OUTPUTFORMAT but for Various Artists discs.
#VAOUTPUTFORMAT='{Various}/${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'

# Like OUTPUTFORMAT and VAOUTPUTFORMAT but for the ONEFILE rips.
#ONETRACKOUTPUTFORMAT=$OUTPUTFORMAT
#VAONETRACKOUTPUTFORMAT=$VAOUTPUTFORMAT

# Define how many encoders to run at once. This makes for huge speedups
# on SMP systems. Defaults to 1. Equivalent to -j.
#MAXPROCS=2

# Support for systems with low disk space:
# n:	Default parallelization (read entire CD in while encoding)
# y:	No parallelization (rip, encode, rip, encode...)
#LOWDISK=n

# If set to y, enables batch mode normalization, which preserves relative
# volume differences between tracks of an album. 
#BATCHNORM=n

# Enables nogap encoding when using the 'lame' encoder.
#NOGAP

# Set the playlist file location format. Uses the same variables and format
# as OUTPUTFORMAT. If the playlist is specified to be in a subdirectory, it
# will be created for you and the playlist will reference files from that
# subdirectory.
#PLAYLISTFORMAT='${ARTISTFILE}-${ALBUMFILE}.${OUTPUT}.m3u'
# If you want to prefix every filename in a playlist with an arbitrary
# string (such as 'http://you/yourstuff/'), use this option
#PLAYLISTDATAPREFIX=''

#Like PLAYLIST{FORMAT,DATAPREFIX} but for Various Artists discs:
#VAPLAYLISTFORMAT='${ARTISTFILE}-${ALBUMFILE}.${OUTPUT}.m3u'
#VAPLAYLISTDATAPREFIX=''

#This will give the playlist CR-LF line-endings, if set to "y".
#(some hardware players insist on CR-LF line-endings)
#DOSPLAYLIST=n

# Custom filename munging:
# By default, abcde will do the following to CDDB data to get a useful
# filename:
# * Translate colons to a space and a dash for Windows compatibility
# * Eat control characters, single quotes, and question marks
# * Translate spaces and forward slashes to underscores
# * Translate stars into pluses.
# To change that, redefine the mungefilename function.
# mungefilename receives the CDDB data (artist, track, title, whatever)
# as $1 and outputs it on stdout.
#mungefilename ()
#{
#	echo "$@" | sed s,:,\ -,g | tr \ /\* __+ | tr -d \'\"\?\[:cntrl:\]
#}

# Custom genre munging:
# By default we just transform uppercase to lowercase. Not much of a fancy
# function, with not much use, but one can disable it or just turn the first
# Uppercase.
#mungegenre ()
#{
#	echo $CDGENRE | tr "[:upper:]" "[:lower:]"
#}


# Custom pre-read function
# By default it does nothing.
# You can set some things to get abcde function in better ways:
# * Close the CD tray using eject -t (if available in eject and supported by 
#   your CD device.
# * Set the CD speed. You can also use the built-in options, but you can also 
#   set it here. In Debian, eject -x and cdset -x do the job.
# KEEP IN MIND that executables included in pre_read must be in your $PATH or
# you have to define them with full /path/to/binary
# Uncomment and substitute the ":" with your commands.
#pre_read ()
#{
#:
#}

# Custom post-read function
# By default it does nothing.
# You can set some things to get abcde function in better ways:
# * Store a copy of the CD TOC.
# KEEP IN MIND that executables included in post_read must be in your $PATH or
# you have to define them with full /path/to/binary
# Uncomment and substitute the ":" with your commands.
#post_read ()
#{
#:
#}

# If you'd like to have abcde eject the cdrom after all the tracks have been
# read, uncomment the following line.
#EJECTCD=y

# To encode on the remote machines foo, bar, baz, quux, and qiix, as well as
# on the local machine (requires distmp3 to be installed on local machine and
# distmp3host to be installed and running on all remote machines - see README)
#REMOTEHOSTS=foo,bar,baz,quux,qiix

# Set to obtain some information about actions happening in the background
# Useful if you have a slow network or CDDB servers seem unresponsive.
#EXTRAVERBOSE=n

---

### Post by mc4man on 2009-11-10
While i use rubyripper, a member here (Andrew46) uses abcde and has posted some conf's on his website.

[http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)

While he could advise better, what could work is to to look at his 5 in 1 conf and create a flac,mp3 conf for yourself.

As a test I just commented out some lines that seemed appropriate, seems to work as you'd want

 created a file in home folder named .abcde.conf (note the period at beginning

Then pasted this in, saved and ran abcde from terminal.
Files are saved to ~/music/

```
# -----------------$HOME/.abcde.conf----------------- #
# 
#   A sample configuration file to convert music cds to 
#      MP3, Ogg Vorbis, FLAC, Musepack & AAC 
#          using abcde version 2.3.99.6
# 
#       http://andrews-corner.org/abcde.html
# -------------------------------------------------- #

#OGGENCODERSYNTAX=oggenc                # Specify encoder for Ogg Vorbis
MP3ENCODERSYNTAX=lame                  # Specify encoder for MP3
FLACENCODERSYNTAX=flac                 # Specify encoder for FLAC
#MPPENCODERSYNTAX=mppenc                # Specify encoder for Musepack
#AACENCODERSYNTAX=faac                  # Specify encoder for AAC

#OGGENC=oggenc                          # Path to Ogg Vorbis encoder
LAME=lame                              # Path to MP3 encoder
FLAC=flac                              # Path to FLAC encoder
#MPPENC=mppenc                          # Path to Musepack encoder
#AACENC=faac                            # Path to AAC encoder

#OGGENCOPTS='-q 6'                      # Options for Ogg Vorbis
LAMEOPTS='-V 0'            # Options for MP3 
FLACOPTS='--verify --best'             # Options for FLAC
#MPPENCOPTS='--extreme'                 # Options for Musepack
#AACENCOPTS='-q 250 -w -s'              # Options for AAC
 
OUTPUTTYPE="mp3,flac"      # Encode to all 5 formats! [COLOR="Blue"]only 2[/COLOR]

CDROMREADERSYNTAX=cdparanoia            
CDPARANOIA=cdparanoia  
CDPARANOIAOPTS="--never-skip=40"

# Give the location of the CD identification program:       
CDDISCID=cd-discid           
                               
OUTPUTDIR="$HOME/music/"               
OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'
VAOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'
ONETRACKOUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}'
VAONETRACKOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}'

mungefilename ()
{
  echo "$@" | sed s,:,-,g | tr / _ | tr -d \'\"\?\[:cntrl:\]
}
MAXPROCS=2                              # Run a few encoders simultaneously
PADTRACKS=y                             # Makes tracks 01 02 not 1 2
EXTRAVERBOSE=y                          # Useful for debugging
EJECTCD=y                               # Please eject cd when finished :-)
```

The blue wasn't in the conf, and maybe that's the only edit needed from his orig, except for lameopts...?

---

### Post by dnitious on 2009-11-11
Thanks for the reply.  I tried that in my config file and it still encodes the mp3 at 128 cbr.  Any other ideas?

---

### Post by mc4man on 2009-11-11
> Any other ideas? 

Well you could use rubyripper which also does multiple encodings at once but you might want to figure out your lame deal.

I gave abcde a test using the above conf and it produced mp3's at V 0 as expected.
from mediainfo

> General
Complete name                    : /home/doug/music/mp3/Band-Greatest Hits/02.Tears of Rage.mp3
Format                           : MPEG Audio
File size                        : 9.52 MiB
Duration                         : 5mn 20s
Overall bit rate                 : 249 Kbps
Album                            : Greatest Hits
Track name                       : Tears of Rage
Track name/Position              : 02
Performer                        : Band
Genre                            : Rock
Recorded date                    : 2000
Writing library                  : LAME3.98 

Audio
Format                           : MPEG Audio
Format version                   : Version 1
Format profile                   : Layer 3
Duration                         : 5mn 20s
Bit rate mode                    : Variable
Bit rate                         : 249 Kbps
Minimum bit rate                 : 32.0 Kbps
Channel(s)                       : 2 channels
Sampling rate                    : 44.1 KHz
Resolution                       : 16 bits
Stream size                      : 9.52 MiB (100%)
Writing library                  : LAME3.98 
Encoding settings                : -m j -V 0 -q 0 -lowpass 19.5 --vbr-new -b 32



Edit:
I'm wondering how you're determining the br of your mp3's
Using the above Ex. 
nautilus reported thru properties as 96k
mplayer showed as 128k as did vlc (screen 1
All are wrong

screen 2 shows vlc's stream info which is correct
ffplay also reported correctly as did mediainfo above
(noting that the actual br changes during the course of the track

You could also just do a size comparison ( a cbr 128 would be around 55% of a vbr @0

> doug@doug-desktop:~$ ffplay '/home/doug/music/mp3/Band-Greatest Hits/02.Tears of Rage.mp3' 
......................................
Input #0, mp3, from '/home/doug/music/mp3/Band-Greatest Hits/02.Tears of Rage.mp3':
  Duration: 00:05:20.52, start: 0.000000, bitrate: 249 kb/s
    Stream #0.0: Audio: mp3, 44100 Hz, 2 channels, s16, 32 kb/s


---

### Post by dnitious on 2009-11-11
The place I got the info from in determining the mp2 br is the screen from abcde while it is encoding the ripped wav file.  See below...
Encoding track 04 of 8: Hardcore Jollies...
LAME 3.98 32bits ([http://www.mp3dev.org/](http://www.mp3dev.org/))
CPU features: MMX (ASM used), 3DNow! (ASM used), SSE, SSE2
Using polyphase lowpass filter, transition band: 16538 Hz - 17071 Hz
Encoding /home/josh/abcde.66096208/track04.wav
      to /home/josh/abcde.66096208/track04.mp3
Encoding as 44.1 kHz j-stereo MPEG-1 Layer III (11x) 128 kbps qval=3
    Frame          |  CPU time/estim | REAL time/estim | play/CPU |    ETA 
 11562/11562 (100%)|    0:26/    0:26|    0:27/    0:27|   11.594x|    0:00 
-------------------------------------------------------------------------------
   kbps        LR    MS  %     long switch short %
  128.0        3.3  96.7        97.6   1.5   1.0
Writing LAME Tag...done
ReplayGain: -9.0dB
Tagging track 04 of 8: Hardcore Jollies...
Finished.

---

### Post by mc4man on 2009-11-12
I don't see anything like that in the terminal, more like this
> Grabbing track 02: Tears of Rage...
cdparanoia III release 10.2 (September 11, 2008)

Encoding track 01 of 18: The Weight...
Ripping from sector   20655 (track  2 [0:00.00])
	  to sector   44689 (track  2 [5:20.34])

outputting to /home/doug/abcde.25120c12/track02.wav

 (== PROGRESS == [     >                        | 024186 00 ] == :-) 0 ==)   Encoding track 01 of 18: The Weight...
 (== PROGRESS == [           >                  | 028978 00 ] == :-)   ==)   Tagging track 01 of 18: The Weight...
 (== PROGRESS == [                              | 044689 00 ] == :^D * ==)   

Done.



So to re-iterate  (noting this is first time I've used abcde

Copied the conf from prior post into an empty file in home folder named
.abcde.conf

Used just this on the command line
abcde


(there's a how to on rubyripper here
[http://ubuntuforums.org/showthread.php?t=799621](http://ubuntuforums.org/showthread.php?t=799621)

a link to a ppa with pre-built on this page ( post 82

[http://ubuntuforums.org/showthread.php?t=799621&page=9](http://ubuntuforums.org/showthread.php?t=799621&page=9)

Or if desired, I attached a recent rr beta  all.deb in post 86


I am impressed with abcde though and am at a bit of a loss as to why you're getting a -V 3 instead of -V 0

( unless you're using more than just abcde for the command

---

### Post by andrew.46 on 2009-11-12
Hi mc4man,

> **mc4man said:**
> I am impressed with abcde though [...]

I am a great fan as well although I will admit to a suspicion recently that the project was in danger of dying. However over the last month or so there has been a lot of work done:

[http://code.google.com/p/abcde/source/list](http://code.google.com/p/abcde/source/list)

Culminating in a new release which I have to admit I have not looked at yet. This has been incorporated into Lucid Lynx already:

[http://packages.ubuntu.com/lucid/abcde](http://packages.ubuntu.com/lucid/abcde)

I hope to build a package for this on my other distro this weekend and then spend a bit of time updating that abcde page of mine which is alarmingly popular :).

Andrew

---

### Post by mc4man on 2009-11-12
> This has been incorporated into Lucid Lynx already:


Will have to take a look there.. (maybe it can install cleanly into karmic

Can you see any reason why the Op is not getting his intended -V 0 for mp3 ?

( if he was using the modified conf I posted from your site

The only thing I can think of is maybe adding something to the command ( assuming for using a conf one should just use abcde for a whole cd rip and encode

Also thinking there was no need to comment out the encoder lines to limit from 5 to 2, just the line with blue edit..?


Edit: went ahead and installed the lucid deb in karmic, the dep's are the same so no problem there.

Looking at the deps, it should install in any ubuntu release from hardy on.

Another example of media related packages that can go on any recent ubuntu release, either because the deps are the same or if not, the add. deps are 'deadended' so to speak

---

### Post by andrew.46 on 2009-11-12
Hi mc4man,

> **mc4man said:**
> Will have to take a look there.. (maybe it can install cleanly into karmic

With the continued development I might actually track the svn development...

> Can you see any reason why the Op is not getting his intended -V 0 for mp3 ?

( if he was using the modified conf I posted from your site

The only thing I can think of is maybe adding something to the command ( assuming for using a conf one should just use abcde for a whole cd rip and encode

The sequence in order of priority is commandline options, /etc/abcde.conf and $HOME/.abcde.conf in that order. Which is why on my own system I leave /etc/abcde.conf completely commented out, run a detailed $HOME/.abcde.conf and never use the bare commandline except to specify a single track encode with *abcde -1*. This eliminates possible confusion which I suspect is happening here, perhaps the $HOME/.abcde.conf is incorrectly named?
> 
Also thinking there was no need to comment out the encoder lines to limit from 5 to 2, just the line with blue edit..

The magic line is OUTPUTTYPE="mp3,flac", so as you suspected the other lines can be left as is.

All the best,

Andrew

---

### Post by dnitious on 2009-11-14
Ok guys.  I think I finally got it.  I wasn't understanding that there were 2 .abcde.conf files.  The one I create in my home directory and the etc.abcde.conf.  I kept editing an abcde.conf. file somewhere.  I don't know if it was the home one or the other.  I found the one in home dir. and deleted everything and copy and pasted mc4man's conf. file.  It works perfectly.  Except for one thing.  When abcde quarys the cddb, and returns more than one option, I used to be able to enter the option number and it would select that cddb entry.  But now when the quary returns more than one option, I enter the option number and it just beeps and goes end.  How do I select one of the cddb options to move forward with the rip?  When the cddb quary returns only one option for the disc, it works fine.

---

### Post by andrew.46 on 2009-11-14
Hi dnitious,

> **dnitious said:**
>  When abcde quarys the cddb, and returns more than one option, I used to be able to enter the option number and it would select that cddb entry.  But now when the quary returns more than one option, I enter the option number and it just beeps and goes end.  How do I select one of the cddb options to move forward with the rip?  When the cddb quary returns only one option for the disc, it works fine.

You simply press the 'q' key and then select the number of the cddb entry that you wish to use.

Andrew

---

### Post by mc4man on 2009-11-14
> You **simply** press the 'q' key

I think that's one reason why I never used used abcde, couldn't figure that out - tried probably every key, key combo but.

The other reason was i like to encode to aac sometimes with tags for an ipod dock player we drag to jobs and abcde wouldn't use neroAccEnc.

Can say that's no longer true as it's doing it now - atomicparsley tagging was added recently and with a little manual patch to abcde it works fine with the preferred -q 0.X 

with the test track from above
> Complete name                    : /home/doug/music/m4a/Band-Greatest Hits/02.Tears of Rage.m4a
Format                           : MPEG-4
Format profile                   : Base Media / Version 2
Codec ID                         : mp42
File size                        : 9.89 MiB
Duration                         : 5mn 20s
Overall bit rate                 : 259 Kbps
Album                            : Greatest Hits
Track name                       : Tears of Rage
Track name/Position              : 2
Track name/Total                 : 0
Performer                        : Band
Encoded date                     : 2000
Tagged date                      : UTC 2009-11-14 07:58:34
Writing application              : Nero AAC codec / 1.3.3.0
cdec                             : ndaudio 1.3.3.0 / -q 0.65


---

### Post by andrew.46 on 2009-11-14
Hi mc4man,

You have succeeded where I have failed then as I downloaded the svn abcde and failed badly with AtomicParsley which steadfastly refused to tag the aac files. And I see you are also using neroaacenc, can I ask where you picked up this version/patch of abcde?

Andrew

---

### Post by mc4man on 2009-11-14
I found this patch, but the source has changed so had to patch in by hand taking best guess as to where
[http://code.google.com/p/abcde/issues/detail?id=8](http://code.google.com/p/abcde/issues/detail?id=8)

ignored the 2nd part of patch (already done) and wasn't to keen on his accencopts, though they are ok for some uses.
-q is far better for me

Used this instead, noting that while excellent for decent desktop, ect. sound systems, it is a bit much for portable.
 0.375 is around 128k, doesn't increase/decrease linearly  -q auto picks whether lc or he 

AACENCOPTS='-q 0.65'              # Options for AAC

Otherwise note the  edits to .abcde.conf in link


Interesting - I just noticed I have 2 different version on 2 boxes, 2.4 and 2.4.1, I patched 2.4, -  2.4.1 seems to have the same lead-in line as the linked patch, only a different line #

Anyway I'm sure you'll see what to do with either ver. #

For the one I patched (2.4) starting at line # 1144 (figured out why the difference in edit
		
For VERSION='2.4.0.1' just scroll to line 1143 and it matches up as seen in link

for neroAacEnc you get the dl, extract anywhere and chmod +x the neroAacEnc file in the linux folder and move it to /usr/bin

As a side note;
the svn comes with a debian folder that's ready to go, will build to a package off of the rules with command of choice
fakeroot debian/rules binary
dpkg-buildpackage -rfakeroot -D -us -uc
debuild -us -uc


Now I remember, - the 2.4 that  I patched is the abcde file from the 10.4 ubuntu package, the 2.4.1 is a svn from yesterday

Edit:

so ironically ubuntu was patching one the the lines I wanted to patch for nero, that's why the leadin was different. ( plus they removed a ! - interesting there

screen 1 shows ubuntu's patch correcting the comment and removing !
screen 2 I combined both though for nero the corrected line was replaced

---

