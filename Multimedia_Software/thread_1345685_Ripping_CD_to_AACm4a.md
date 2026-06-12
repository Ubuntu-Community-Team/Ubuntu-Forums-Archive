---
title: "Ripping CD to AAC/m4a"
date: 2009-12-04
forum: Multimedia Software
---

### Post by admay on 2009-12-04
New to Linux and running Karmic on a Dell M1330 laptop. I am trying to rip CDs to AAC format for use with an iPod. So far I have tried both abcde and RubyRipper but without success. It doesn't look as if the problems with either are insurmountable but googling does not throw up any answers.

I have installed abcde v2.4.0.1. If I run it with no configuration file so that it rips to .ogg then it works fine. However if I use the configuration file for converting to aac/m4a using faac from here: [http://www.andrews-corner.org/abcde.html#aac](http://www.andrews-corner.org/abcde.html#aac) it will happily rip to the .wav but just stalls when it gets to the encoding stage. System Monitor does not indicate anything running that may be taking a lot of time. In his piece Andrew mentions an Ubuntu patch but this is for v2.3.99.6 so I am hoping that it has been incorporated into 2.4.0.1 since I cannot find it. 

If I run abcde without the configuration file but give it the command line abcde -o m4a then it will get as far as encoding to m4a but falls over when tagging with the error: 

Tagging track 6 of 21: The Seductress...

nice: /home/andrew/abcde.51115215/track6.m4a: Permission denied

[ERROR] abcde: The following commands failed to run:
tagtrack-m4a-6: returned code 126: nice -n 10 /home/andrew/abcde.51115215/track6.m4a --artist Marsalis, Wynton --album Standard Time, Vol. 3: The Resolution Of Romance --title The Seductress --tracknum 6 --year 1990 --genre Jazz --compilation false --comment  --output /home/andrew/abcde.51115215/track6.m4a-atomic
Finished. Not cleaning /home/andrew/abcde.51115215.
 

This looks to my inexperienced eye as if it might be a permissions problem. The permissions on my home directory are: drwxr-xr-x, the permissions on the temporary directory that abcde produces are drwxr-xr-x and the permissions on the .m4a file that was created are -rw-r&#8212;r--.

Finally I have tried running as root sudo abcde -o m4a but get the same error.

As an alternative a tried using RubyRipper using the commands described here [http://code.google.com/p/rubyripper/issues/detail?id=280](http://code.google.com/p/rubyripper/issues/detail?id=280) to rip using the NeroAAC codec but that just causes RubyRipper to shut-down without warning after completing the initial rip to .wav and creating an .m3u file.

Can anyone with mor experience than me give me any pointer that may help me to get this working.

Thanks,

Andrew

---

### Post by mc4man on 2009-12-04
Have both RR and abcde using neroAacEnc with tagging. Actually prefer abcde though both do about the same.

For abcde you need to patch the script, for RR it's just the command option

Both use AtomicParsley to tag so you need to install that
```
sudo apt-get install atomicparsley
```


The command for RR is this, blue is adjustable for -q,(change name to match yours

```
neroAacEnc -q [COLOR="Blue"]0.65[/COLOR] -if %i -of "%o".m4a && mkdir -p /home/[COLOR="Blue"]doug[/COLOR]/tmp/m4a/%a\ \(%y\)\ %b && AtomicParsley "%o".m4a -o /home/[COLOR="Blue"]doug[/COLOR]/tmp/m4a/%a\ \(%y\)\ %b/%n\ -\ %t.aac --artist "%a" --album "%b" --tracknum "%n" --year "%y" --title "%t"  --genre "%g" && rm "%o".m4a
```

Downside of RR
The files will actually be saved to ~/tmp, will have to be moved afterwards.
It won't work if you attempt to save to .m4a, must be .aac
To batch change after the rip, encode then cd to the folder holding tracks and run
```
for f in *.aac; do mv "$f" "${f%.aac}.m4a"; done;
```

(( maybe these things can be worked out, haven't bothered since abcde woorks better

For abcde you need to patch the abcde script, somewhat described here though for someone you knows abcde well
[http://ubuntuforums.org/showthread.php?t=1322307&page=2&highlight=abcde](http://ubuntuforums.org/showthread.php?t=1322307&page=2&highlight=abcde)

I have made a patched abcde .deb but don't think I can attach here (changed source) though maybe it would be ok..?
The edit is not too hard, open the script and go to line 1143, use what's in the link (abcde patch) from linked post above.



My ~/.abcde

```
# -----------------$HOME/.abcde.conf----------------- #
# 
#   A sample configuration file to convert music cds to 
#      MP3, Ogg Vorbis, FLAC, Musepack & AAC 
#          using abcde version 2.3.99.6
# 
#       http://andrews-corner.org/abcde.html
# -------------------------------------------------- #
#CDROM=/dev/cdrom2

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
 
OUTPUTTYPE="m4a"      # Encode to all 5 formats! only 1

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

---

### Post by mc4man on 2009-12-04
If you were experiencing any trouble editing the abcde script this would be a fairly easy way to get the latest svn (283) and patch it for neroAacEnc

```
sudo apt-get install patch subversion
```

```
mkdir abcde-nero && cd abcde-nero
```

```
svn checkout http://abcde.googlecode.com/svn/trunk/ abcde-read-only
```

Then right click on the attached .diff.gz and "save link as", browse to ~/abcde-nero and save it inside **next to the ** abcde-read-only folder ( don't put inside the abcde-read-only folder and don't extract, leave as is

back at the same terminal

 ```
cd abcde-read-only && zcat ~/abcde-nero/abcde-read-only.diff.gz | patch -p0



```
The terminal should say this start to finish
> doug@doug-desktop:~$ mkdir abcde-nero && cd abcde-nero
doug@doug-desktop:~/abcde-nero$ svn checkout [http://abcde.googlecode.com/svn/trunk/](http://abcde.googlecode.com/svn/trunk/) abcde-read-only
A    abcde-read-only/abcde.conf
A    abcde-read-only/debian
A    abcde-read-only/debian/control
A    abcde-read-only/debian/dirs
A    abcde-read-only/debian/compat
A    abcde-read-only/debian/preinst
A    abcde-read-only/debian/changelog
A    abcde-read-only/debian/copyright
A    abcde-read-only/debian/docs
A    abcde-read-only/debian/rules
A    abcde-read-only/abcde.py
A    abcde-read-only/changelog
A    abcde-read-only/KNOWN.BUGS
A    abcde-read-only/README
A    abcde-read-only/abcde.1
A    abcde-read-only/USEPIPES
A    abcde-read-only/abcde
A    abcde-read-only/TODO
A    abcde-read-only/cddb-tool.1
A    abcde-read-only/FAQ
A    abcde-read-only/cddb-tool
A    abcde-read-only/COPYING
A    abcde-read-only/Makefile
A    abcde-read-only/examples
A    abcde-read-only/examples/abcde.init
A    abcde-read-only/examples/abcded
A    abcde-read-only/examples/musicbrainz-get-tracks
A    abcde-read-only/examples/autorip.sh
A    abcde-read-only/examples/cue2discid
 U   abcde-read-only
Checked out revision 283.
doug@doug-desktop:~/abcde-nero$ cd abcde-read-only && zcat ~/abcde-nero/abcde-read-only.diff.gz | patch -p0
patching file abcde
doug@doug-desktop:~/abcde-nero/abcde-read-only$ 


Then just replace your current abcde in /usr/bin with the patched one ( or if not installed, then install/run abcde as desired

As long as neroAacEnc is in usr/bin aand executable, atomicparsley is installed and you have a ~/.abcde.conf as noted it should work fine

Note - patch  is for -r283, can be manually edited to other -r's

---

### Post by andrew.46 on 2009-12-04
Hi admay,

> **admay said:**
> I have installed abcde v2.4.0.1. If I run it with no configuration file so that it rips to .ogg then it works fine. However if I use the configuration file for converting to aac/m4a using faac from here: [http://www.andrews-corner.org/abcde.html#aac](http://www.andrews-corner.org/abcde.html#aac) it will happily rip to the .wav but just stalls when it gets to the encoding stage.

Looks like mc4man has given some directions to get out of this problem, unfortunately abcde still has a few teething problems and aac tagging is a problem that still persists in some released versions. Hopefully now that work has begun again on this great script there will be fewer glitches in the future and perhaps a single up to date release version...

I have to confess that the page you have drawn that $HOME/.abcde.conf file from is my own and it is *not* actually based on an Ubuntu version of abcde but a [Slackware packaging]("http://slackbuilds.org/slackbuilds/13.0/audio/abcde/abcde.SlackBuil") with an [amalgamated patch]("http://slackbuilds.org/slackbuilds/13.0/audio/abcde/aac_speex_tagging.diff") that I produced. So no guarantees for Ubuntu I'm afraid but if you use the source code available on that page + the patch aac tagging will work fine. But using AtomicParsley and NeroAACenc as described by mc4man sounds like a lot more fun :).

Andrew

---

### Post by mc4man on 2009-12-04
> aac tagging is a problem that still persists in some released versions

It doesn't seem as extensive as from other means (use dbpoweramp running in wine as a sort of benchmark), maybe that can be addressed..?

For our purposes here tagging isn't too big a deal, just enough to allow putting into an ipod for a dock we drag to jobs.

The one tag specified that doesn't work out is genre, but the same happens in rubyripper - I think it needs to be imputed as a binary and isn't.

Ex. 

> $ ffplay '/home/doug/music/m4a/Jackson Browne-Late For The Sky/02.Fountain Of Sorrow.m4a'
................
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/doug/music/m4a/Jackson Browne-Late For The Sky/02.Fountain Of Sorrow.m4a':
  Duration: 00:06:52.25, start: 0.000000, bitrate: 257 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16, 256 kb/s
  Metadata
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: M4A mp42isomndia
    encoder         : Nero AAC codec / 1.3.3.0
    author          : Jackson Browne
    album           : Late For The Sky
    title           : Fountain Of Sorrow
    track           : 2
    year            : 1974


Off topic
I find this interesting, whether a good thing or not, or irrelevant don't know

> Copyright:

Copyright (c) 1998-2001 Robert Woodcock <rcw@debian.org>
Copyright (c) 2003-2009 Jesus Climent <jesus.climent@hispalinux.es>
This code is hereby licensed for public consumption under either the
GNU GPL v2 or greater, or Larry Wall's Artistic license - your choice.

You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software
Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA 02110-1301, USA.

Copyright for this work is to expire January 1, 2010, after which it
shall be public domain.


---

### Post by admay on 2009-12-07
Thanks all. I now have abcde ripping just find to m4a and even have it configured so that I can insert a CD, it will rip in the background and dump the files into a folder, and then eject the CD when finished. Haven't tried syncing with the iPod yet though.

Interestingly I have one CD (Sir John Barbirolli's Mahler 8th) where abcde displays the track titles one line at a time and expects a keypress each time. At the end it displays [End] (much like less) and goes no further. I sort of suspect something in the track information returned to it. Most Odd.

RubyRipper is still proving to be a problem and just shuts down without warning but as abcde is my weapon of choice it is not my top priority.

Thanks again,

Andrew

---

