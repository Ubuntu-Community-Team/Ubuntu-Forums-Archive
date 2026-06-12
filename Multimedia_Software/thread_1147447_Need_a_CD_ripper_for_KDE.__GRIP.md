---
title: "Need a CD ripper for KDE.  GRIP?"
date: 2009-05-03
forum: Multimedia Software
---

### Post by TomB19 on 2009-05-03
I gave my girlfriend an iPod and now I need to rip about 100 CDs.

KAudioCreator would have been perfect for this job but sadly it's gone now.  What's the best ripper to rip a large stack of CDs?

KAudioCreator was nice in that it would queue ripping and encoding such that you could stuff CDs into a drive as fast as they can be ripped and encoding would catch up as the CPU could.

I've got a quad core CPU now so it's not as much of an issue but I'd like a ripper that has a decent workflow and minimal work per CD.

I don't want to have to use K3B and it seems awkward to rip from Dolphin.

How is GRIP?

---

### Post by logos34 on 2009-05-03
Looks like kaudiocreator has been replaced by Audex.

sudo apt-get install audex

(make sure the **Universe** repo is enabled)

[http://kubuntuguide.org/Jaunty#Audex_CD_Ripper.2FEncoder](http://kubuntuguide.org/Jaunty#Audex_CD_Ripper.2FEncoder)
[http://www.kde-apps.org/content/show.php/Audex?content=77125](http://www.kde-apps.org/content/show.php/Audex?content=77125)
[http://opensource.maniatek.de/cgi-bin/audex/audex/install.html](http://opensource.maniatek.de/cgi-bin/audex/audex/install.html)

Grip is excellent.  So is RubyRipper. 

ABCDE is a great command-line ripper.  I know how to automate it in Gnome but not kde desktop. Basically you need to set your preferred apps to start abcde in terminal when audiocd is inserted, and configure .abcde.conf to run in non-interactive mode.  Then you can just shove one cd after another into the drive.)

good luck

---

### Post by TomB19 on 2009-05-03
Thanks, logos.  :)

Audex seems pretty decent.  It doesn't have quite the work flow of KAudioCreator but it has MusicBrainz functionality that KAC never had.  Overall, I like it.

I appreciate the advice.  :guitar:

---

### Post by pbardet on 2009-05-30
I installed audex.
Unfortunately, the Flac profile is wrong. It does not save tags properly.

By default, it was:
flac -T=Artist="$tartist" -T=Title="$ttitle" -T=Album="$title" -T=Date="$date" -T=Tracknumber="$trackno" -T=Genre="$genre" -o $o $i

Which I changed to: (no = after each -T option)
flac -T Artist="$tartist" -T Title="$ttitle" -T Album="$title" -T Date="$date" -T Tracknumber="$trackno" -T Genre="$genre" -o $o $i

---

### Post by rookcifer on 2009-05-30
Install RubyRipper.  It is the Linux version of EAC on Windows and is very easy to use.  Like EAC, It guarantees "perfect" rips by utilizing checksums.

---

### Post by paxmark1 on 2009-05-30
grip has not had much development in awhile.

If you do not mind the command line    abcde works quite well.  
However you will want to edit the config file

---

### Post by andrew.46 on 2009-06-04
Hi paxmark1,

> **paxmark1 said:**
> If you do not mind the command line abcde works quite well.  However you will want to edit the config file

I am sure the creator of this config file will not mind if I post it here:

```

# -----------------$HOME/.abcde.conf----------------- #
# 
# A sample configuration file to convert music cds to 
#       MP3 format using abcde version 2.3.99.6
# 
#       http://andrews-corner.org/abcde.html
# -------------------------------------------------- #

# Specify the encoder to use for MP3. In this case
# the alternatives are gogo, bladeenc, l3enc, xingmp3enc, mp3enc.
MP3ENCODERSYNTAX=lame 

# Specify the path to the selected encoder. In most cases the encoder
# should be in your $PATH as I illustrate below, otherwise you will 
# need to specify the full path. For example: /usr/bin/lame
LAME=lame

# Specify your required encoding options here. Multiple options can
# be selected as '--preset standard --another-option' etc.
LAMEOPTS='--preset extreme' 

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
OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'
VAOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'

# Decide here how you want the tracks labelled for a standard 'single-artist',
# single-track encode and also for a single-track 'various-artist' encode.
# (Create a single-track encode with 'abcde -1' from the commandline.)
ONETRACKOUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}'
VAONETRACKOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}'

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

Perhaps this will help a litle?

Andrew

---

### Post by cptrohn on 2009-06-04
I just ripped a BUNCH of CD's to the HD and I used Asunder... it wasn't extremely fast, but it did a reasonable job with the tags and ripped everything into flac very well.

---

