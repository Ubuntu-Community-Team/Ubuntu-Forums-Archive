---
title: "abcde Very Slow For Corrections"
date: 2010-09-05
forum: Multimedia Software
---

### Post by jim_deadlock on 2010-09-05
I use abcde for ripping CDs and on the whole I'm very happy with it. Normally it will rip a whole CD in a few minutes and produce perfect files. The problem I have is when a CD track is imperfect (skips or whatever), abcde will still rip a perfect copy, however, it takes forever to do so.

The example below took well over 14 hours for one track! The original track was rather messed up but still, 14 hours? Is there a  way to configure abcde to take less time while still maintaining the  quality of the output file?

```
Grabbing track 08: Brandenburg Concerto No. 6 In B Flat Major, BWV 1051
cdparanoia III release 10.2 (September 11, 2008)

Ripping from sector  216339 (track  8 [0:00.00])
      to sector  242278 (track  8 [5:45.64])

outputting to /home/jim/abcde.b610750c/track08.wav

 (== PROGRESS == [  +++++VVVVVVV+V+V+V+         | 242278 00 ] == :^D * ==)   

Done.
```

---

### Post by andrew.46 on 2010-09-05
Hi Jim,

This delay is coming from cdparanoia rather than abcde itself. The 'V' error refers to an uncorrected error/skip and I suspect this means there is a problem with the cd itself. By default cdparanoia will retry 20 times if there are skips of this type, do you have any settings in ~/.abcde.conf to influence this? These would be under CDPARANOIAOPTS, or perhaps specified from the commandline.

Andrew

---

### Post by jim_deadlock on 2010-09-05
No these are the only options I'm using:

```
LAME=lame
PADTRACKS=y
OUTPUTTYPE=mp3
OUTPUTFORMAT='${ARTISTFILE}/${ALBUMFILE}/${TRACKNUM} ${TRACKFILE}'
OUTPUTDIR='/home/jim/Music'
EJECTCD=y
mungefilename ()
{
echo "$@"
}

```As you say, this only happens on tracks that have errors/skipping and it is nice to have a perfect track at the end of the process, so if it takes 14 hours then I suppose I'll just have to live with it unless anyone has a better idea.

---

### Post by andrew.46 on 2010-09-05
Hi jim,

> **jim_deadlock said:**
>  I suppose I'll just have to live with it unless anyone has a better idea.

I have not tried it myself but perhaps see if you get better performance using cdda2wav instead of cdparanoia? I suspect the Ubuntu package for cdda2wav will actually be the debian fork 'icedax' but I am on the wrong partition to check this at the moment :(.

Andrew

---

### Post by mc4man on 2010-09-05
> I suspect the Ubuntu package for cdda2wav will actually be the debian fork 'icedax'

That it will, but the 'real' cdda2wav can be used instead, just adjust the line in abcde (if written this way
CDDA2WAV=icedax to CDDA2WAV=cdda2wav

cdda2wav can be built from source or gotten here
[https://launchpad.net/~brandonsnider/+archive/cdrtools/+packages](https://launchpad.net/~brandonsnider/+archive/cdrtools/+packages)

One could add the ppa for easy install and  the other burning replacement libs or just download the cdrtools package - extract and put cdda2wav in a /bin in  path
(removing icedax if installed is a good idea if not using the ppa

Edit: I'd describe his ppa as trustworthy

---

### Post by BobvanderPoel on 2010-09-05
Sorry if I'm hijacking this thread ... but my problem may be the same as the OPs.

I've got 2 cdrom drives on my system. Both are CD/DVD rw. Basically, they should preform the same.

Drive 1: a LG HL-DT-ST DVDRAM GH22NS50. This is on a SATA connector.

Drive 2: an older Sony   DVD RW DRU-800A. This is on a PATA connector.

I have tried both drives on a windows box and they appear to be about the same in speed. If anything, the LG is a bit faster. But, on my Linux machine the LG is dog slow. I did some testing with hdparm, and it appears that the Sony performs at around twice the rate.

According to hdparm -t:

/dev/cdrom:  (the sony)
 Timing buffered disk reads:    8 MB in  3.17 seconds =   2.52 MB/sec

/dev/cdrom2: (the LG)
 Timing buffered disk reads:    4 MB in  3.95 seconds =   1.01 MB/sec

Things get worse when I try to rip an audio disk. Using the sony drive and ripit (a perl front end using cdparanoia) I get a rip in about 5 minutes with the sony and 24 minutes with the LG. Yeah, 5 times slower.

I've searched everywhere I can think of and find nothing relevant.

The full story of the drive is:

 sudo hdparm -I /dev/cdrom2

/dev/cdrom2:

ATAPI CD-ROM, with removable media
	Model Number:       HL-DT-ST DVDRAM GH22NS50                
	Serial Number:      K00998K1011         
	Firmware Revision:  TN01    
	Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6
Standards:
	Likely used CD-ROM ATAPI-1
Configuration:
	DRQ response: 50us.
	Packet size: 12 bytes
	cache/buffer size  = unknown
Capabilities:
	LBA, IORDY(can be disabled)
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns

Everything looks okay?

Suggestions? Or should I just donate the drive and install another Sony?

---

### Post by jim_deadlock on 2010-09-06
Andrew & mc4man thanks for the suggestion, cdda2wav is indeed a lot quicker, it does the job in about 3 seconds flat, but unfortunately it also reproduces all the original errors from the CD, it doesn't do any cleanup unlike cdparanoia. At least it does give me an alternative though so thanks again.

Edit: for anyone else wanting to try this, you also need this line in abcde.conf:

CDROMREADERSYNTAX=cdda2wav

---

### Post by mc4man on 2010-09-06
try either of these in your abcde.conf

CDDA2WAVOPTS="-paranoia "

or (probably not what you want with heavily damaged cd's

CDDA2WAVOPTS="-paranoia -paraopts=proof"

Ck. man cdda2wav

---

### Post by jim_deadlock on 2010-09-06
> **mc4man said:**
>  CDDA2WAVOPTS="-paranoia "   ... makes a clean copy in under 4 hours which is a marked improvement  over cdparanoia. If -paraopts=proof gives any further speed gain I'll  post it here but for now I'm marking this SOLVED with many thanks :D

Edit: Oh and here is the error info from this track (which cdparanoia doesn't give me):

100%  track  8 recorded with audible retry/skip errors (173839.3% problem sectors)
100%  0 rderr, 3877 skip, 45085903 atom, 4123 edge, 0 drop, 0 dup, 0 drift
100%  2378956 overlap(0.5 .. 0.75)

And another thing - the cdda2wav process is much less intensive, 25% cpu as opposed to 60-90% for cdparanoia.

---

### Post by jim_deadlock on 2010-09-06
> **mc4man said:**
> CDDA2WAVOPTS="-paranoia -paraopts=proof"

... has shaved another hour off! Woohoo!

---

### Post by mc4man on 2010-09-06
Glad you're making progress
Thought I'd post up this page by Andrew - you may find interesting and some sample .conf's
[http://andrews-corner.org/abcde.html](http://andrews-corner.org/abcde.html)

I use his 5 in 1 modified slightly to encode to m4a using neroAacEnc (created a new abcde package - abcde-nero
Atm it's set to just do m4a, things can be changed by commenting or uncommenting lines and or adding to the OUTPUTTYPE= line.



```

# -----------------$HOME/.abcde-nero.conf----------------- #
# 
#   A sample configuration file to convert music cds to 
#      MP3, Ogg Vorbis, FLAC, Musepack & AAC 
#          using abcde version 2.4.2
#      Modified for neroAacEnc and atomicParsley from
#       [http://andrews-corner.org/abcde.html](http://andrews-corner.org/abcde.html)
#      Uses either cdparanoia or Jörg Schilling's cdda2wav
# -------------------------------------------------- #
CDROM=/dev/cdrom

#OGGENCODERSYNTAX=oggenc                # Specify encoder for Ogg Vorbis
MP3ENCODERSYNTAX=lame                  # Specify encoder for MP3
FLACENCODERSYNTAX=flac                 # Specify encoder for FLAC
#MPPENCODERSYNTAX=mppenc                # Specify encoder for Musepack
AACENCODERSYNTAX=neroAacEnc                 # Specify encoder for AAC

#OGGENC=oggenc                          # Path to Ogg Vorbis encoder
LAME=lame                              # Path to MP3 encoder
FLAC=flac                              # Path to FLAC encoder
#MPPENC=mppenc                          # Path to Musepack encoder
AACENC=neroAacEnc                            # Path to AAC encoder
ATOMICPARSLEY='AtomicParsley'

#OGGENCOPTS='-q 6'                      # Options for Ogg Vorbis
LAMEOPTS='-V 0'            # Options for MP3 
FLACOPTS='--verify --best'             # Options for FLAC
#MPPENCOPTS='--extreme'                 # Options for Musepack
AACENCOPTS='-q 0.65'              # Options for AAC
 
OUTPUTTYPE="m4a"      # Encode to all 5 formats! only 1 here

#CDROMREADERSYNTAX=cdparanoia
#CDPARANOIA=cdparanoia 
CDROMREADERSYNTAX=cdda2wav 
CDDA2WAV=cdda2wav            
#CDPARANOIAOPTS="--never-skip=40"
CDDA2WAVOPTS="-paranoia"

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

Edit: note that there are some things commented out in the conf that don't really need to, never have 'cleaned up' in that regard

---

### Post by bgiannes on 2010-09-10
just try turning the speed down

ie

abcde -S 1


some CD's don't read very well at what ever the standard is on my DVD/CD drive



doing this i when from +12hours to ripping the CD in 8 minutes :) 


> **jim_deadlock said:**
> I use abcde for ripping CDs and on the whole I'm very happy with it. Normally it will rip a whole CD in a few minutes and produce perfect files. The problem I have is when a CD track is imperfect (skips or whatever), abcde will still rip a perfect copy, however, it takes forever to do so.

The example below took well over 14 hours for one track! The original track was rather messed up but still, 14 hours? Is there a  way to configure abcde to take less time while still maintaining the  quality of the output file?

```
Grabbing track 08: Brandenburg Concerto No. 6 In B Flat Major, BWV 1051
cdparanoia III release 10.2 (September 11, 2008)

Ripping from sector  216339 (track  8 [0:00.00])
      to sector  242278 (track  8 [5:45.64])

outputting to /home/jim/abcde.b610750c/track08.wav

 (== PROGRESS == [  +++++VVVVVVV+V+V+V+         | 242278 00 ] == :^D * ==)   

Done.
```

---

