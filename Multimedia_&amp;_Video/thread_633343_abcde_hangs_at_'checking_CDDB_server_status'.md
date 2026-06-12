---
title: "abcde hangs at 'checking CDDB server status'"
date: 2007-12-06
forum: Multimedia &amp; Video
---

### Post by Perpetual on 2007-12-06
Installed abcde on a brand new Gutsy installation and abcde hangs at the following...

landon@landon-laptop:~$ abcde
Executing customizable pre-read function... done.
Getting CD track info... Querying the CD for audio tracks...
Grabbing entire CD - tracks: 01 02 03 04 05 06 07 08 09 10 11 12
Checking CDDB server status...

Here is my custom  .abcde.conf

```
# Name of the encoder?
MP3ENCODERSYNTAX=lame                  

# What program to rip the tracks from CD?
CDROMREADERSYNTAX=cdparanoia            

# Where is the encoding program?
LAME=lame                     
                 
# Where are the tagging / commenting programs?
ID3=id3                       
ID3V2=id3v2                   

# Where are the other programs?
CDPARANOIA=cdparanoia         
CDDISCID=cd-discid            

# What options should be used for encoding?
LAMEOPTS='--preset extreme'            
OUTPUTTYPE="mp3"                       

# Where do the encoded tracks go to?
OUTPUTDIR="$HOME/ripped/"               

# How do you want the tagging done?
OUTPUTFORMAT='${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'

# Put spaces in the filenames.
mungefilename ()
{
  echo "$@" | sed s,:,-,g | tr / _ | tr -d \'\"\?\[:cntrl:\]
}
# What extra options?
PADTRACKS=y                             # Makes tracks 01 02 not 1 2
EXTRAVERBOSE=y                          # Useful for debugging
EJECTCD=y                               # Please eject cd when finished :-)

```

and my /etc/abcde.conf

```
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
#NOSUBMIT=n

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
#MP3ENCODERSYNTAX=default
#OGGENCODERSYNTAX=default
#FLACENCODERSYNTAX=default
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
#PADTRACKS=n

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
#LAMEOPTS=
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
#FLACOPTS="-f"

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
#CDPARANOIAOPTS=
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
#OUTPUTDIR=`pwd`

# Or if you'd just like to put the temporary .wav files somewhere else
# you can specify that here
#WAVOUTPUTDIR=`pwd`

# OUTPUTTYPE can be either "ogg", "mp3", "flac" or "spx", or a combination
# of them separated with ",": "ogg,mp3".
#OUTPUTTYPE=ogg

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
#OUTPUTFORMAT='${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'

# Like OUTPUTFORMAT but for Various Artists discs.
#VAOUTPUTFORMAT='Various-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'

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
```

It worked in Debian Lenny but I have installed it the same on Gutsy.  I am really confused.  Any thoughts would be appreciated.

Note, if I uncomment #CDDBURL="http://freedb.freedb.org/~cddb/cddb.cgi" in /etc/abcde.conf it moves beyond the CDDB lookup but the results are album not found.  If I go to the freedb site, the album is there.

Edit: do I need to have cddb-tool installed?  I see reference to it when googling but when I 'aptitude search cddb-tool' there are no results.

---

### Post by marsanpin on 2007-12-06
Hi!

Same here (still under Breezy).
Been googling for a while and I can't find a solution.
It happens as well (in another Breezy-box) with EAC under Wine. ! :confused:
Funny thing is tha SoundJuicer can get the info from freedb (or is it cddb?)
Gonna gogle a bit more...

Best of luck

Mario

---

### Post by Perpetual on 2007-12-06
Thanks for the reply.  I feel better that someone else is suffering :)

I have googled and hoven't found crap that has helped....or really even touched on the topic.

---

### Post by eurgain on 2007-12-06
Hi

The Freedb server appears to be broken today.  It is not your setup!

I actually use FreeDB running KAudioCreater on SUSE, and it has not worked all day today, so its nothing to do with Ubuntu or abcde.  A web browser directed to [http://freedb.freedb.org/](http://freedb.freedb.org/) just times out, and the FreeDB forum is down as well.

I'd suggest trying again tomorrow.

Regards
A

---

### Post by Perpetual on 2007-12-06
Thanks eurgain.  I thought that might be the case and just found that k3b can't connect to it either.  I attempted to set a different cddb but must have been doing it wrong.

Thanks!

Hmm...tried freedb2.org and freedb.musicbrainz.org...I can not get anything to work.  Hydrogen forum thread seems people have had luck with the 2 mentioned.  Also tried us.freedb.org and at.freedb.org...

---

### Post by Perpetual on 2007-12-06
Ok, another question, how do I tell abcde to stop querying CDDB?  I can tag the files myself.

---

### Post by yabbadabbadont on 2007-12-06
There is another thread about freedb being down somewhere around here.  In it, someone said that the freedb2.org server is the only mirror that is still up and running.  Try changing your config to use it instead.

---

### Post by Perpetual on 2007-12-06
> **yabbadabbadont said:**
> There is another thread about freedb being down somewhere around here.  In it, someone said that the freedb2.org server is the only mirror that is still up and running.  Try changing your config to use it instead.

Thanks for the response but yeah, freedb2 doesn't work either.  Frustrating :)

---

### Post by logos34 on 2007-12-06
> **Perpetual said:**
> Ok, another question, how do I tell abcde to stop querying CDDB?  I can tag the files myself.

try:

$ abcde -a encode,clean 

look in the WAVOUTPUTDIR 

So freedb2 doesn't work either?  rats...I have like a dozen cds I need to rip and the servers are down just the day I was going to do it, wouldn't you know it!

---

### Post by Perpetual on 2007-12-06
Yeah, I just got some cd's in the mail and wanted to get them on my ipod  :(

Gonna use sound juicer for now.

---

### Post by Jussi Kukkonen on 2007-12-07
[http://freedb.berlios.de/cgi-bin/cddb.cgi](http://freedb.berlios.de/cgi-bin/cddb.cgi) is up

---

### Post by logos34 on 2007-12-07
> **Jussi Kukkonen said:**
> [http://freedb.berlios.de/cgi-bin/cddb.cgi](http://freedb.berlios.de/cgi-bin/cddb.cgi) is up

thanks Jussi.

---

### Post by Jergar on 2007-12-07
only gnudb.gnudb.org is actually working for me. Soundjuicer is working with musicbrainz but I'm using grip.

---

### Post by logos34 on 2007-12-07
I think I'm swtiching to gnudb.gnudb.org

> "A new home for the freedb.org database to make sure it stays free. "

---

### Post by Perpetual on 2007-12-07
Thanks guys for all of the responses.  gnudb.gnudb.org is working.

Thanks!!

---

### Post by VCSkier on 2007-12-13
I'd rather be using musicbrainz for CDDB lookup, because it seems to me to be more consistanly accurate, but can't figure out how to get it working.  I added CDDBMETHOD=musicbrainz to my abcde.conf, as the man page suggested, but this is what I get.```
vcskier@vcskier-gutsy:~$ abcde -1 -M -o flac -V
Executing customizable pre-read function... done.
grep: /status: No such file or directory
grep: /status: No such file or directory
grep: /status: No such file or directory
abcde: internal error: cddb-choice not recorded.

```Any suggestions?  Thanks.

---

### Post by yabbadabbadont on 2007-12-13
> **VCSkier said:**
> I'd rather be using musicbrainz for CDDB lookup, because it seems to me to be more consistanly accurate, but can't figure out how to get it working.  I added CDDBMETHOD=musicbrainz to my abcde.conf, as the man page suggested, but this is what I get.```
vcskier@vcskier-gutsy:~$ abcde -1 -M -o flac -V
Executing customizable pre-read function... done.
grep: /status: No such file or directory
grep: /status: No such file or directory
grep: /status: No such file or directory
abcde: internal error: cddb-choice not recorded.

```Any suggestions?  Thanks.

Do you have the python-musicbrainz package installed?

---

### Post by VCSkier on 2007-12-13
yup.

---

### Post by yabbadabbadont on 2007-12-13
Although I've already got all my CDs ripped to FLAC, I'll download abcde and take a look at the script to see what it is doing.  What version of abcde is included in Gutsy?  (I use the Frisky Fawn ;))

---

### Post by VCSkier on 2007-12-13
```
vcskier@vcskier-gutsy:~$ abcde -v
This is abcde v2.3.99-$Revision: 222M $.
```
Synaptic reports v. 2.3.99.6-1ubuntu2

Thanks!

---

### Post by yabbadabbadont on 2007-12-13
According to the changlog, it looks like musicbrainz support isn't ready yet.
```
abcde (2.3.99.2-1) unstable; urgency=low

  * Adding musicbrainz support. First bits.
```
And in a slightly newer version.
```
abcde (2.3.99.3-1) unstable; urgency=low

  * Initial steps to make abcde working with musicbrainz, although it is not
    ready yet.
```
It isn't mentioned again in the changelog.  Looks like you'll just have to wait.  (or start scripting  :D)

---

### Post by VCSkier on 2007-12-14
lol.  Thanks for pointing that out.  I guess I should be more careful to check the obvious things before I ask for help.  Regardless, I really like abcde so far.  Even with musicbrainz support not finished yet, abcde still looks like our best ripper to me, with regard to features.  Now if only can find a cd burner that can burn the images with embedded cue sheets to cd's...

---

