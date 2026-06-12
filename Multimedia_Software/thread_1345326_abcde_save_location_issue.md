---
title: "abcde save location issue"
date: 2009-12-03
forum: Multimedia Software
---

### Post by BlackHatRob on 2009-12-03
Hello all,

I am attempting to modify my $HOME/.abcde.conf file to force abcde to save media files in the following format
```
/home/blackhatrob/Music/Artist-SongTitle.mp3
```

I have been unable to override the default naming convention of
```
/home/blackhatrob/Music/Track.Artist-SongTitle.mp3
```

My /etc/abcde.conf file remains fully commented and my $HOME/.abcde.conf file is at the bottom of this thread. I know that abcde is looking at my custom .conf because the WAVOUPUTDIR has been changed and is working.

Thanks very much in advance

```

# -----------------$HOME/.abcde.conf----------------- #

# Specify the encoder to use for MP3. In this case
# the alternatives are gogo, bladeenc, l3enc, xingmp3enc, mp3enc.
MP3ENCODERSYNTAX=lame 

# Specify the path to the selected encoder. In most cases the encoder
# should be in your $PATH as I illustrate below, otherwise you will 
# need to specify the full path. For example: /usr/bin/lame
LAME=lame

# Specify your required encoding options here. Multiple options can
# be selected as '--preset standard --another-option' etc.
#LAMEOPTS='--preset extreme' 
LAMEOPTS='-m s --vbr-new -b 192 -B 320 -q 0'

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
                               
# Give the base location here for the WAV music files.
WAVOUTPUTDIR="$HOME/Music/Temp/"

# Give the base location here for the encoded music files.
OUTPUTDIR="$HOME/Music/"               

# Decide here how you want the tracks labelled for a standard 'single-artist',
# multi-track encode and also for a multi-track, 'various-artist' encode:
#OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'
#VAOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'
OUTPUTFORMAT='${ARTISTFILE}-${TRACKFILE}'

# Put spaces in the filenames instead of the more correct underscores:
mungefilename ()
{
  echo "$@" | sed s,:,-,g | tr / _ | tr -d \'\"\?\[:cntrl:\]
}

# What extra options?
MAXPROCS=2                              # Run a few encoders simultaneously
#PADTRACKS=y                             # Makes tracks 01 02 not 1 2
EXTRAVERBOSE=y                          # Useful for debugging
EJECTCD=y                               # Please eject cd when finished :-)

```

---

### Post by andrew.46 on 2009-12-04
Hi Rob,

Perhaps you could try:

```
OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${TRACKFILE}'
```

I am not sure if that is what you are after though? BTW you have snipped the free advertising for my site :).

All the best,

Andrew

---

### Post by BlackHatRob on 2009-12-04
Not sure what you mean by snipping your site advertisement. Was this originally your config?

The naming problem I have is that I want the music to all be in one place, like this

/home/rdmenotte/Music/artista-songa.mp3
/home/rdmenotte/Music/artista-songb.mp3
/home/rdmenotte/Music/artistb-songa.mp3
/home/rdmenotte/Music/artistc-songa.mp3

But instead I am getting this

/home/rdmenotte/Music/artista-cdname/1.artista-songa.mp3
/home/rdmenotte/Music/artista-cdname/2.artista-songb.mp3
/home/rdmenotte/Music/artista-cdname/3.artista-songc.mp3
...

no matter what options I seem to change in the .abcdef.conf file, I cannot make abcde save just to /home/rdmenotte/Music/

---

### Post by andrew.46 on 2009-12-04
Hi BlackHatRob,

> **BlackHatRob said:**
> no matter what options I seem to change in the .abcdef.conf file, I cannot make abcde save just to /home/rdmenotte/Music/

The syntax I suggested did not help?

Andrew

---

### Post by mc4man on 2009-12-04
While I don't want what you trying to do, did a quick edit to ~/.abcde and it comes out the way you're looking for. (don't quite get while it's not working, only difference is I'm using the orig. line not adding one, plus none of the lines is commented

relevant area (plus saving to ~/music ,but that shouldn't matter

> OUTPUTDIR="$HOME/music/"               
[COLOR="Blue"]OUTPUTFORMAT='${ARTISTFILE}-${TRACKFILE}'[/COLOR]
VAOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'
ONETRACKOUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}'
VAONETRACKOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}'


screen shows tracks loose in ~/music with new track names (artist-trackname

(I think if i was to do it that way I'd probably go instead

'${ARTISTFILE}-${TRACKNUM}.${TRACKFILE}'

---

