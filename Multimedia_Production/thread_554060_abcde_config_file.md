---
title: "abcde config file"
date: 2007-09-18
forum: Multimedia Production
---

### Post by citybird on 2007-09-18
Hi all, 
I would like to rip to flac and mp3 at the same time with abcde but direct the output to separate directories. 

is this possible?

ie: 
mp3 files goto /home/user/music/MP3/artist/title/song.mp3
flac files goto /home/user/music/FLAC/artist/title/song.flac

currently both files goto the same dir.

---

### Post by yabbadabbadont on 2007-09-18
I never found a way for it to do that when I was using abcde.  What I ended up doing was just ripping to flac and then using a script called flac2mp3 to create a mirrored directory tree with mp3 files.  There were two versions of the script that I found.  A bash script and a perl script.  I don't remember which one I ended up using.  For that matter, it shouldn't be too difficult to write a bash script to simply recreate your directory tree and move the existing mp3 files to their new home.  :D

---

### Post by andrew.46 on 2007-09-19
Hi,

 I have always wondered how to do this myself and I will admit to having spent too much time over the last 2 days trying to figure it out! Good news is I have solved it.

 I give the example ~/.abcde.conf file below that encodes to both ogg and mp3 and places them in different directories. I have not used flac in thia example as I know nothing of flac encoding / options etc :-) Just substitute your flac settings for the ogg settings, or even run all 3!!

```

OGGENCODERSYNTAX=oggenc                 # Specify encoder for ogg
MP3ENCODERSYNTAX=lame                   # Specify encoder for mp3


CDROMREADERSYNTAX=cdparanoia            # CD reader program to use

OGGENC=/usr/bin/oggenc                  # Path to ogg encoder
LAME=/usr/bin/lame                      # Path to lame encoder
ID3=/usr/bin/id3                        # Path to id3 editor
ID3V2=/usr/bin/id3v2                    # Path to id3v2 editor
CDPARANOIA=/usr/bin/cdparanoia          # Path to cdparanoia
CDDISCID=/usr/bin/cd-discid             # Path to cd-discid
VORBISCOMMENT=/usr/bin/vorbiscomment    # Path to vorbiscomment

OGGENCOPTS='-q 6'                       # Options for ogg
LAMEOPTS='--preset standard'            # Options for mp3  

OUTPUTTYPE="ogg,mp3"                    # mp3 +/- ogg +/- flac ???
OUTPUTDIR="$HOME/music/"                # Base directory for the music

# This divides the music into 2 folders: 
# mp3 goes to $HOME/music/mp3/ 
# ogg goes to $HOME/music/ogg/
OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}--${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}--${TRACKFILE}'

PADTRACKS=y                             # Makes tracks 01 02 not 1 2
EXTRAVERBOSE=y                          # Useful for debugging
EJECTCD=y                               # Please eject cd when finished :-)
```

I have tested this comprehensively and it works flawlessly. What are the chances you could post the flac settings that you use for abcde? I have a small walkthrough on abcde:

[http://people.aapt.net.au/~adjlstrong/ubuntu_cli.html#mp3](http://people.aapt.net.au/~adjlstrong/ubuntu_cli.html#mp3)

 that I was thinking of making a single page and the only missing element is flac about which I know next to nothing :confused:

 Hope this helps!

        Andrew

---

### Post by yabbadabbadont on 2007-09-19
Cool.  I didn't know that the OUTPUT variable was set like that.  Granted, I didn't spend much time on it as I had the flac2mp3 script that did what I needed.  The only special flac setting I used in my .abcde.conf file was ```
FLACOPTS="-f --best"
```  I think that the "-f" is probably not needed.

---

### Post by andrew.46 on 2007-09-19
Hi,
> **yabbadabbadont said:**
> Cool.  I didn't know that the OUTPUT variable was set like that.

Don't worry, I didn't know until today either :-)

                 Andrew

---

### Post by andrew.46 on 2007-09-19
Hi again,

 So here for the record is my ~/.abcde.conf file that encodes to ogg, flac and mp3. Each file type will be placed in a seperate directory, tagged or commented, and I have added in the function to give spaces in filenames:

```

##################################################################
# Andrew's ~/.abcde.conf file to encode to ogg, flac and mp3 at  #
# the same time. The 3 filetypes will then be tagged or          #
# commented and dispersed to seperate directories.               #
# http://people.aapt.net.au/~adjlstrong/ubuntu.html              #
##################################################################

# What are the names of the encoding programs?
OGGENCODERSYNTAX=oggenc                 # Specify encoder for ogg
MP3ENCODERSYNTAX=lame                   # Specify encoder for mp3
FLACENCODERSYNTAX=flac                  # Specify encoder for flac

# What program to rip the tracks from CD?
CDROMREADERSYNTAX=cdparanoia            # CD reader program to use

# Where are the encoding programs?
OGGENC=/usr/bin/oggenc                  # Path to ogg encoder
LAME=/usr/bin/lame                      # Path to lame encoder
FLAC=/usr/bin/flac                      # Path to flac encoder
                 
# Where are the tagging / commenting programs?
ID3=/usr/bin/id3                        # Path to id3 editor
ID3V2=/usr/bin/id3v2                    # Path to id3v2 editor
VORBISCOMMENT=/usr/bin/vorbiscomment    # Path to vorbiscomment
METAFLAC=/usr/bin/metaflac              # Path to metaflac

# Where are the other programs?
CDPARANOIA=/usr/bin/cdparanoia          # Path to cdparanoia
CDDISCID=/usr/bin/cd-discid             # Path to cd-discid

# What options should be used for encoding?
OGGENCOPTS='-q 6'                       # Options for ogg
LAMEOPTS='--preset standard'            # Options for mp3 
FLACOPTS='--best'                       # Options for flac 
OUTPUTTYPE="ogg,mp3,flac"               # mp3 +/- ogg +/- flac

# Where do the encoded tracks go to?
OUTPUTDIR="$HOME/music/"                # Base directory for the music

# This divides the music into 3 folders: 
#  mp3 goes to $HOME/music/mp3/ 
#  ogg goes to $HOME/music/ogg/
# flac goes to $HOME/music/flac/
OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}--${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}--${TRACKFILE}'

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

Those flac files sound great but I need a bigger disk before encoding that way all the time :-)

         Andrew

---

### Post by logos34 on 2007-11-11
Can you override the .conf settings for just, say, a single track (or several)?

**abcde [tracks] -o [filetype][:filetypeoptions]**

e.g.:
[B]
abcde [COLOR="Red"]7[/COLOR] -o mp3:"-b 128" [/B]  -->rip+encode track 7 only to mp3 only@cbr 128

??

The man pages and other docs I've seen only show how to do the ENTIRE cd.

abcde -o vorbis,flac
abcde -o vorbis:"-b 192"

etc.

EDIT: nevermind--it's 'abcde [options] **[tracks]**'.  (staring at me from the top of the man page.).  tracks AFTER options...

---

### Post by citybird on 2007-12-10
SWEET!! thanks for the awesome tip!!

As for flac settings I have not found any. 
It is lossless so I guess that there are no settings.

---

### Post by citybird on 2007-12-10
ok next question: 

Is it possible to get the year that the album was released to appear next to the album folder?

ie: 
/ home / user / music / mp3 / Artist / Album [year] / 01.track.mp3
/ home / user / music / flac / Artist / Album [year] / 01.track.flac


this would be great for me when I need to find something from a particular era

---

### Post by citybird on 2007-12-10
I rip to flac for Archiving/Home listening and to MP3 for the portable player. What would you need ogg for? I know some players support it but mine doesn't. so why mp3 and ogg?

---

### Post by VCSkier on 2007-12-13
Generally speaking, Ogg Vorbis creates files of higher quality (fewer audible compression artifacts) for a given bitrate when compared to MP3.  Also, and more importantly, Vorbis is Free.  :)

---

