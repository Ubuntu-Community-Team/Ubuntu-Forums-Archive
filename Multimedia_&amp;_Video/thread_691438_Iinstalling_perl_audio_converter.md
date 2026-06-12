---
title: "Iinstalling perl audio converter"
date: 2008-02-08
forum: Multimedia &amp; Video
---

### Post by thehauss2010 on 2008-02-08
I have some protected m4a files I need converted and the only converter I found that did everything I needed was perl audio converter.  I've spent at least an hour trying to found out how to install it.  Does anyone know how or if it can be installed on ubuntu?

---

### Post by cozmicharlie on 2008-02-08
I use PACPl and have been one of the beta testers so I should be able to help.  Where are you at so far?  Have you downloaded the script?  Have you tried to install? Give me a brief description of what you have done so far.

---

### Post by thehauss2010 on 2008-02-08
I am no where I had found a place that said I could install it using "yum" but whenever I tried that it says it was missing a compenant to yum called "python" and I couldn't find a way to install it

---

### Post by cozmicharlie on 2008-02-08
I am not familiar with Yum.  Are you using Ubuntu Gutsy?  Go to the PACPl web site ([http://www.pacpl.org/downloads.html](http://www.pacpl.org/downloads.html)) and download the source package to your desktop.  You can also try the deb - it is easier but if you do not have the dependencies installed it will not work.  Post back once you have it downloaded.

---

### Post by cozmicharlie on 2008-02-08
I forgot to tell you the package you want is the pacpl-4.0.1.tar.bz2

---

### Post by thehauss2010 on 2008-02-09
Sry for taking so long to post back but I just downloaded the package to my desktop so now what?

---

### Post by cozmicharlie on 2008-02-09
The main problem is you need all the dependencies (these are programs like python) installed to run PACPL.     Luckily there is a script that will do it for you. Follow these steps.
( There is an install file and a readme file that are good to read- you may want to read the install file before you start).

[LIST=1]
[*]Go into synaptic and install a program called "build essential".  Once that is installed, close out of Synaptic and
[*]Extract the pacpl-4.0.1.tar.bz2 folder you downloaded to the desktop (right click>extract here).
[*]In the pacpl-4.0.1 folder you extracted there is another folder called "extra" and in that folder is a file called "mod-install-kubuntu.sh".  That is the script that will install the dependencies.  So what you do is open a terminal and change directories to the extras.  It should be the following command:
```
cd /home/yourusename/Desktop/pacpl-4.0.1/extra 
``` (where yourusername is your user name in ubuntu).  
[*]Next run the script.  At the terminal prompt type (or cut and paste):
```
./mod-install-kubuntu.sh
```
[*]It should start loading all the dependencies for you.  Once you are finished, close the terminal and you are ready to install PACPL.
[*]Open the terminal and change directories to the pacpl-4.0.1 folder you previously extracted to the desktop.
```
cd /home/yourusename/Desktop/pacpl-4.0.1
``` 
[*]type or cut and paste the following commands at the prompt (1 line at a time)
```
./configure
```
```
make
```
```
sudo make install
```
[/LIST]

It should be installed along with all the dependencies.  You run pacpl by opening a terminal and typing pacpl at the prompt.  The folder has instructions on how to use PACPl or check out the web site.  This is a command line program though it does have a gui that can be used.  I find the command line is easier.

---

### Post by thehauss2010 on 2008-02-10
Well thanks alot for the help but I am not very fluent in command line so would it be easy to install the gui, if not I don't want to trouble you though

---

### Post by cozmicharlie on 2008-02-10
The gui will install when you install pacpl.  Though it is not a very good gui.  Another option that may work better for you is SoundKonverter - it is a gui based program.  It is a kde program but it works fine in gnome.  You can install it from Synaptic.  You will though need to install all the codecs for it to work though.  Do you want to try that?  I can walk you through it.

---

### Post by thehauss2010 on 2008-02-10
No cause I need to decode protected m4a and m4v files and I'm pretty sure only pacpl does that.  Well then could you give me the command for this so I can get a feel and figure out how to work this thing cause the "usage" in help didn't really help me.

What command will convert all m4p in the directory "/media/disk/thehauss/My_Music/Complete_Files/Convert/MP4_Protected" to mp3 (And I want  it to keep the original files)

---

### Post by cozmicharlie on 2008-02-10
Below are the list of commands from the PACPl help file.  You use it in the command form
```
usage: pacpl --to <format> <options> [file(s)/directory(s)]

```
So if you are converting from m4a to mp3 and the file is home/music/ledzepplin.m4a.  the simple command would be: 

--to mp3 home/music/ledzepplin.m4a

you also have options that can be added - say you want to tag
```
--to mp3 --artist led zepplin home/music/ledzepplin.m4a
```

say for example you want to move it to a new folder:
```
--to mp3 --outfile home/newfolder home/music/ledzepplin.m4a

```

Note you can also use the shorter commands like -t for --to.  I used the longer ones to help you understand.

It really is not hard.  Especially if you are basically repeating the same commands.  ALso, the GUI will install (see the web site for screen shots).  I am not sure about the protected part.  You may need to email the developer - he is very good about answering questions and helping. 

Perl Audio Converter - 4.0.1

-t, --to   >>>>>> destination format
-r, --recursive  >>>>>> recursively convert directory(s)
-p, --preserve       >>>>>>>preserve directory structure
-f, --formats        >>>>>>>list supported encode/decode formats
-o, --only           >>>>>>>only convert files matching extension
-k, --keep           >>>>>>>keep files matching destination format
-h, --help          >>>>>>> this help menu
-l, --longhelp       >>>>>>complete list of options
-v, --verbose        >>>>>>>show detailed information

user options:

--eopts             >>>>>> user supplied encoder options
--dopts              >>>>>>>user supplied decoder options
--nopts              >>>>>>>user supplied normalize options
--outfile            >>>>>>output file name
--outdir             >>>>>>output directory
--dryrun             >>>>>>do not convert files
--overwrite          >>>>>>>overwrite destination file
--normalize          >>>>>>normalize wav file before encoding
--delete             >>>>>>>remove source file after conversion
--encoder            >>>>>>specify an alternate encoder
--decoder            >>>>>>specify an alternate decoder
--version            >>>>>>>display version information

encoder options:

--bitrate            >>>>bitrate (def. 128)
--freq               >>>>audio frequency (def. 44100)
--channels           >>number of audio channels (def. 2)
--effect             >>>>sox effect (aiff/au/snd/raw/voc/smp/avr/cdr)
--fcomp              >>>>flac/fla compression level (def. 2)
--pcomp              >>>>lpac/pac compression level (def. 3)
--acomp              >>>>ape compression level (def. 3000)
--oggqual            >>>> >>>> ogg quality level (def. 3)
--spxqual             >>>>spx quality level (def. 8)
--aacqual            >>>> aac/mp4/m4a quality level (def. 100)
--mpcqual            >>>> mpc/mpp quality level (def. radio)
--ofmode              >>>>ofr/ofs mode (def. normal)
--ofopt              >>>> ofr/ofs optimization (def. fast)
--bratio             >>>> bonk down sampling ratio (def. 2)
--bquanl            >>>>  bonk quantization level (def. 1.0)
--bpsize              >>>>bonk predictor size (def. 128)

tagging options:

--artist              >>>>set artist information
--title              >>>> set title
--track               >>>>set track number
--year               >>>> set year/date of the album/track
--album              >>>> set album title information
--genre               >>>>set genre
--comment           >>>>  set comments
--taginfo            >>>> show tagging information for selected file

tagging usage: pacpl <options> [file(s)]

ripping options:

--rip                >>>> rip tracks separated by comma or all
--nocddb             >>>> disable cddb
--noinput             >>>>disable cddb interactivity
--nscheme            >>>> naming scheme
--cdinfo             >>>> show cddb information for current disc
--device              >>>>default = /dev/cdrom

rip usage: pacpl --rip [track(s)/all] --to <format> <options>

usage: pacpl --to <format> <options> [file(s)/directory(s)]

---

### Post by thehauss2010 on 2008-02-10
Cool I think I got it thanks alot for the help!

Well I think I got the command line part right but I got an error message;

thehauss@thehauss:~$ pacpl --to mp3 --outfile /media/disk/thehauss/My_Music/Complete_Files/Convert/Converted /media/disk/thehauss/My_Music/Complete_Files/Convert/MP4
Perl Audio Converter - 4.0.1

error: could not find suitable application to encode: mp3

see 'pacpl --help' or 'pacpl --longhelp' for a list of options.

---

### Post by cozmicharlie on 2008-02-11
Good - I think you are close.  This sounds like a codec problem.   Type the following command and read through the list of supported encoders/decoders.  You should have one listed for mp3 (but you probably don't since it is giving you the error).  For example in my output it has mp3 Lame.

```
pacpl -f
```

Most likely you need to download the mp3 encoder.  There are a number of packages you need to download.  I am assuming you are running Gutsy but if not then look on the Medibuntu page for the instructions for whatever version of Ubuntu you are using.

Start by enabling the medibuntu repository (see [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu))
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
Make sure you have all your repsoitories open in Synaptic.  Go to settings>repositories and you have tabs for "Ubuntu Software" and Third PArty Software" - make sure they are all checked.  If not check and run update.
Open Add/remove programs under the Applications menu.  Select "All", scroll down to the "Ubuntu Restricted Extras" and install these.  It will ask you if you want to install packages and give you warnings.  These packages all work fine in Ubuntu, it is just they have restricted licenses that you have to agree to.  This should give you mp3 support but also make sure you have the gstreamer plug-ins installed (this assumes you are using the gstreamer engine - if you have a native Ubuntu install then you are).  Close Add/Remove, open Synaptic and search for "gstreamer".  These should be installed when you install the Ubuntu Restricted Extras but double check and install any gstreamer-10 plug ins (good, bad, ugly) if they are not already installed. 

I also install Lame for mp3.  You can do this through Synaptic also.  Search Lame and install the packages.

Now when you run pacpl -f you should show support for mp3.  You can also look through the list and see if you are missing any other codecs you need.  Most can be installed through Synaptic.  If you follow the above instructions you should have most of the codecs installed.  

I will be out all day today travelling for work but I will check the thread when I get back tonight to see if this worked for you.

---

### Post by thehauss2010 on 2008-02-11
Well thankfully It's all working and it's pretty fast so thank you very much

---

### Post by cozmicharlie on 2008-02-11
Great - glad to here it.  Check back on the PACPL web site once in a while because the developer is very active and he does upgrade fairly frequent.

---

### Post by pemur1 on 2008-03-19
How do I get the gui to work? I'm completely useless at using the terminal.

---

### Post by stoer on 2008-06-10
Hi cozmicharlie,
i've been reading your posts here with interest.
I'm running Linux Mint Elyssa, Gnome and am trying to convert some .ape to mp3 (it's all my sons mp3 player will play....)
I've installed pacpl (debian package) but hit the following error, i was wondering if you could point me (gently) in the right direction, please.

```
 steve@steve-laptop ~ $ pacpl --to mp3 --outfile /home/steve/Music/Santana_Shaman/Smp3 /home/steve/Music/Santana_Shaman/01_Adouma.ape
Perl Audio Converter - 4.0.0-beta1

error: could not find application: mac

see 'pacpl --help' or 'pacpl --longhelp' for a list of options.
 
```

I installed lame but still run accross te "can't find mac"

```

steve@steve-laptop ~ $ pacpl -f

Perl Audio Converter - 4.0.0-beta1

EXT       E   D   ENCODER  DECODER   TAG-READ   TAG-WRITE
---------------------------------------------------------
aac       Y   Y   faac     faad         N          N
ac3       Y   Y   ffmpeg   ffmpeg       N          N
aiff      Y   Y   sox      sox          N          N
ape       Y   Y   mac      mac          N          N
asf       N   Y            mplayer      N          N
au        Y   Y   sox      sox          N          N
avi       N   Y            mplayer      N          N
avr       Y   Y   sox      sox          N          N
bonk      Y   Y   bonk     bonk         N          N
cdr       Y   Y   sox      sox          N          N
divx      N   Y            mplayer      N          N
fla       Y   Y   flac     flac         Y          Y
flac      Y   Y   flac     flac         Y          Y
flv       N   Y            mplayer      N          N
la        Y   Y   la       la           N          N
lpac      Y   Y   lpac     lpac         N          N
m4a       Y   Y   faac     faad         Y          Y
m4v       N   Y            mplayer      N          N
mkv       N   Y            mplayer      N          N
mov       N   Y            mplayer      N          N
mp2       Y   Y   ffmpeg   ffmpeg       N          N
mp3       Y   Y   lame     lame         Y          Y
mp4       Y   Y   faac     faad         Y          Y
mpc       Y   Y   mppenc   mppdec       Y          Y
mpeg      N   Y            mplayer      N          N
mpg       N   Y            mplayer      N          N
mpp       Y   Y   mppenc   mppdec       Y          Y
nsv       N   Y            mplayer      N          N
nuv       N   Y            mplayer      N          N
ofr       Y   Y   ofr      ofr          N          N
ofs       Y   Y   ofs      ofs          N          N
ogg       Y   Y   oggenc   oggdec       Y          Y
ogm       N   Y            mplayer      N          N
pac       Y   Y   lpac     lpac         N          N
psp       N   Y            mplayer      N          N
qt        N   Y            mplayer      N          N
ra        Y   Y   ffmpeg   ffmpeg       N          N
ram       N   Y            ffmpeg       N          N
raw       Y   Y   sox      sox          N          N
rm        N   Y            mplayer      N          N
rv        N   Y            mplayer      N          N
shn       Y   Y   shorten  shorten      N          N
smk       N   Y            mplayer      N          N
smp       Y   Y   sox      sox          N          N
snd       Y   Y   sox      sox          N          N
spx       Y   Y   speexenc speexdec     Y          Y
svcd      N   Y            mplayer      N          N
tta       Y   Y   ttaenc   ttaenc       N          N
vcd       N   Y            mplayer      N          N
vob       N   Y            mplayer      N          N
voc       Y   Y   sox      sox          N          N
wav       Y   Y   mv       cp           N          N
wma       Y   Y   ffmpeg   ffmpeg       Y          Y
wmv       N   Y            mplayer      N          N
wv        Y   Y   wavpack  wvunpack     Y          Y

encode formats: 33 --- decode formats: 55


```

I'd really appreciate any help you might offer.
Cheers.

---

### Post by stoer on 2008-06-10
Hi again,
been playing with this for a couple of hours now,

Found this (installing mac on ubuntu)

[http://aidanjm.wordpress.com/2007/01/26/using-monkeys-audio-ape-files-in-ubuntu/](http://aidanjm.wordpress.com/2007/01/26/using-monkeys-audio-ape-files-in-ubuntu/)

Installed mac,

```

steve@steve-laptop ~/Desktop $ mac
--- Monkey's Audio Console Front End (v 3.99) (c) Matthew T. Ashland ---
Proper Usage: [EXE] [Input File] [Output File] [Mode]

Modes: 
    Compress (fast): '-c1000'
    Compress (normal): '-c2000'
    Compress (high): '-c3000'
    Compress (extra high): '-c4000'
    Compress (insane): '-c5000'
    Decompress: '-d'
    Verify: '-v'
    Convert: '-nXXXX'

Examples:
    Compress: mac.exe "Metallica - One.wav" "Metallica - One.ape" -c2000
    Decompress: mac.exe "Metallica - One.ape" "Metallica - One.wav" -d
    Verify: mac.exe "Metallica - One.ape" -v
    (note: int filenames must be put inside of quotations)


```

and once again ran 

```

steve@steve-laptop ~ $ pacpl --to mp3 --outfile /home/steve/Music/Santana_Shaman/Smp3 /home/steve/Music/Santana_Shaman/01_Adouma.ape

```

This time getting th efollowing error,

```

Perl Audio Converter - 4.0.2

Converting:  [01_Adouma.ape] -> [mp3] decode failed with exit status: 65280


Total files converted: 0, failed: 1


```

Now i'm really stuck ;)

Any help would be greatly appreciated.

---

### Post by cozmicharlie on 2008-06-12
stoer - In a terminal type or cut and paste the following:

pacpl -f

What does it show for ape?

Is your file OK - i.e. can you transcode it on another computer (a windows computer preferably)?  If you do not have access to another computer send me the file and I will see if I can transcode it (you can PM me).

---

### Post by stoer on 2008-06-13
Hi Cozmicharlie,
Thanks for replying, appreciate it.

pacpl -f gives the following...

```

 pacpl -f

Perl Audio Converter - 4.0.2

EXT       E   D   ENCODER         DECODER         TAG-READ   TAG-WRITE
----------------------------------------------------------------------
aac       Y   Y   faac            faad               N          N
ac3       Y   Y   ffmpeg          mplayer            N          N
aif       Y   Y   sox             sox                N          N
aiff      Y   Y   sox             sox                N          N
ape       Y   Y   mac             mac                N          N
asf       N   Y                   mplayer            N          N
au        Y   Y   sox             sox                N          N
avi       N   Y                   mplayer            N          N
avr       Y   Y   sox             sox                N          N
bonk      Y   Y   bonk            bonk               N          N
caf       Y   Y   sndfile-convert sndfile-convert    N          N
cdr       Y   Y   sox             sox                N          N
divx      N   Y                   mplayer            N          N
fap       Y   Y   sndfile-convert sndfile-convert    N          N
fla       Y   Y   flac            flac               Y          Y
flac      Y   Y   flac            flac               Y          Y
flv       N   Y                   mplayer            N          N
ircam     Y   Y   sndfile-convert sndfile-convert    N          N
la        Y   Y   la              la                 N          N
lpac      Y   Y   lpac            lpac               N          N
m4a       Y   Y   faac            faad               Y          Y
m4v       N   Y                   mplayer            N          N
mat       Y   Y   sndfile-convert sndfile-convert    N          N
mat4      Y   Y   sndfile-convert sndfile-convert    N          N
mat5      Y   Y   sndfile-convert sndfile-convert    N          N
mkv       N   Y                   mplayer            N          N
mmf       Y   Y   ffmpeg          ffmpeg             N          N
mov       N   Y                   mplayer            N          N
mp2       Y   Y   ffmpeg          ffmpeg             N          N
mp3       Y   Y   lame            lame               Y          Y
mp4       Y   Y   faac            faad               Y          Y
mpc       Y   Y   mppenc          mppdec             Y          Y
mpeg      N   Y                   mplayer            N          N
mpg       N   Y                   mplayer            N          N
mpp       Y   Y   mppenc          mppdec             Y          Y
nist      Y   Y   sndfile-convert sndfile-convert    N          N
nsv       N   Y                   mplayer            N          N
nuv       N   Y                   mplayer            N          N
ofr       Y   Y   ofr             ofr                N          N
ofs       Y   Y   ofs             ofs                N          N
ogg       Y   Y   oggenc          oggdec             Y          Y
ogm       N   Y                   mplayer            N          N
pac       Y   Y   lpac            lpac               N          N
paf       Y   Y   sndfile-convert sndfile-convert    N          N
psp       N   Y                   mplayer            N          N
pvf       Y   Y   sndfile-convert sndfile-convert    N          N
qt        N   Y                   mplayer            N          N
ra        Y   Y   ffmpeg          ffmpeg             N          N
ram       N   Y                   ffmpeg             N          N
raw       Y   Y   sox             sox                N          N
rm        Y   Y   ffmpeg          mplayer            N          N
rv        N   Y                   mplayer            N          N
sd2       Y   Y   sndfile-convert sndfile-convert    N          N
sf        Y   Y   sndfile-convert sndfile-convert    N          N
shn       Y   Y   shorten         shorten            N          N
smk       N   Y                   mplayer            N          N
smp       Y   Y   sox             sox                N          N
snd       Y   Y   sox             sox                N          N
spx       Y   Y   speexenc        speexdec           Y          Y
svcd      N   Y                   mplayer            N          N
tta       Y   Y   ttaenc          ttaenc             N          N
vcd       N   Y                   mplayer            N          N
vob       N   Y                   mplayer            N          N
voc       Y   Y   sox             sox                N          N
w64       Y   Y   sndfile-convert sndfile-convert    N          N
wav       Y   Y   mv              cp                 N          N
wma       Y   Y   ffmpeg          ffmpeg             Y          N
wmv       N   Y                   mplayer            N          N
wv        Y   Y   wavpack         wvunpack           Y          Y

encode formats: 48 --- decode formats: 69



```

The .ape files i have seem to work flawlessly in windows and convert without a hitch using mac, from eg. .ape to .wav
This means that i can convert to .mp3 or whatever using the windows setup but not yet in Linux.

I think that i'm quite probably missing something quite basic and obvious but what that is exactly....?
For example if i try the conversion using another format in Pacpl, such as .wav or .ac3 then i get...

.wav
```

steve@steve-laptop ~ $ pacpl --to wav --outfile /home/steve/Music/Santana_Shaman/Smp3 /home/steve/Music/Santana_Shaman/01_Adouma.ape
Perl Audio Converter - 4.0.2

Converting:  [01_Adouma.ape] -> [wav] decode failed with exit status: 65280

```

.ogg
```

steve@steve-laptop ~ $ pacpl --to ogg --outfile /home/steve/Music/Santana_Shaman/Smp3 /home/steve/Music/Santana_Shaman/01_Adouma.ape
Perl Audio Converter - 4.0.2

error: could not find suitable application to encode: ogg

```

.wma
```

steve@steve-laptop ~ $ pacpl --to wma --outfile /home/steve/Music/Santana_Shaman/Smp3 /home/steve/Music/Santana_Shaman/01_Adouma.ape
Perl Audio Converter - 4.0.2

error: could not find suitable application to encode: wma

```

.ac3
```

steve@steve-laptop ~ $ pacpl --to ac3 --outfile /home/steve/Music/Santana_Shaman/Smp3 /home/steve/Music/Santana_Shaman/01_Adouma.ape
Perl Audio Converter - 4.0.2

error: could not find suitable application to encode: ac3


```

I'm wondering if i missed something in the set up, such as linking to the encoder/decoders apps.?

Maybe an idea to uninstall everything and try reinstalling again, if this is the way to go i wouldn't mind a hint or two on how to do this aswell.

Again, thanks for the help.

---

### Post by stoer on 2008-06-13
I've reinstalled pacpl, reinstalled ffmpeg (packet from medibuntu) and added oggencoder.

Now instead of an error saying that the encoders cannot be found i'm getting the same error for all conversion as by .ape
eg.
[ogg] decode failed with exit status: 65280

Here's the output from pacpl -f after doing the above mentioned steps.

```

 pacpl -f

Perl Audio Converter - 4.0.2

EXT       E   D   ENCODER         DECODER         TAG-READ   TAG-WRITE
----------------------------------------------------------------------
aac       Y   Y   faac            faad               N          N
ac3       Y   Y   ffmpeg          mplayer            N          N
aif       Y   Y   sox             sox                N          N
aiff      Y   Y   sox             sox                N          N
ape       Y   Y   mac             mac                N          N
asf       N   Y                   mplayer            N          N
au        Y   Y   sox             sox                N          N
avi       N   Y                   mplayer            N          N
avr       Y   Y   sox             sox                N          N
bonk      Y   Y   bonk            bonk               N          N
caf       Y   Y   sndfile-convert sndfile-convert    N          N
cdr       Y   Y   sox             sox                N          N
divx      N   Y                   mplayer            N          N
fap       Y   Y   sndfile-convert sndfile-convert    N          N
fla       Y   Y   flac            flac               Y          Y
flac      Y   Y   flac            flac               Y          Y
flv       N   Y                   mplayer            N          N
ircam     Y   Y   sndfile-convert sndfile-convert    N          N
la        Y   Y   la              la                 N          N
lpac      Y   Y   lpac            lpac               N          N
m4a       Y   Y   faac            faad               Y          Y
m4v       N   Y                   mplayer            N          N
mat       Y   Y   sndfile-convert sndfile-convert    N          N
mat4      Y   Y   sndfile-convert sndfile-convert    N          N
mat5      Y   Y   sndfile-convert sndfile-convert    N          N
mkv       N   Y                   mplayer            N          N
mmf       Y   Y   ffmpeg          ffmpeg             N          N
mov       N   Y                   mplayer            N          N
mp2       Y   Y   ffmpeg          ffmpeg             N          N
mp3       Y   Y   lame            lame               Y          Y
mp4       Y   Y   faac            faad               Y          Y
mpc       Y   Y   mppenc          mppdec             Y          Y
mpeg      N   Y                   mplayer            N          N
mpg       N   Y                   mplayer            N          N
mpp       Y   Y   mppenc          mppdec             Y          Y
nist      Y   Y   sndfile-convert sndfile-convert    N          N
nsv       N   Y                   mplayer            N          N
nuv       N   Y                   mplayer            N          N
ofr       Y   Y   ofr             ofr                N          N
ofs       Y   Y   ofs             ofs                N          N
ogg       Y   Y   oggenc          oggdec             Y          Y
ogm       N   Y                   mplayer            N          N
pac       Y   Y   lpac            lpac               N          N
paf       Y   Y   sndfile-convert sndfile-convert    N          N
psp       N   Y                   mplayer            N          N
pvf       Y   Y   sndfile-convert sndfile-convert    N          N
qt        N   Y                   mplayer            N          N
ra        Y   Y   ffmpeg          ffmpeg             N          N
ram       N   Y                   ffmpeg             N          N
raw       Y   Y   sox             sox                N          N
rm        Y   Y   ffmpeg          mplayer            N          N
rv        N   Y                   mplayer            N          N
sd2       Y   Y   sndfile-convert sndfile-convert    N          N
sf        Y   Y   sndfile-convert sndfile-convert    N          N
shn       Y   Y   shorten         shorten            N          N
smk       N   Y                   mplayer            N          N
smp       Y   Y   sox             sox                N          N
snd       Y   Y   sox             sox                N          N
spx       Y   Y   speexenc        speexdec           Y          Y
svcd      N   Y                   mplayer            N          N
tta       Y   Y   ttaenc          ttaenc             N          N
vcd       N   Y                   mplayer            N          N
vob       N   Y                   mplayer            N          N
voc       Y   Y   sox             sox                N          N
w64       Y   Y   sndfile-convert sndfile-convert    N          N
wav       Y   Y   mv              cp                 N          N
wma       Y   Y   ffmpeg          ffmpeg             Y          N
wmv       N   Y                   mplayer            N          N
wv        Y   Y   wavpack         wvunpack           Y          Y

encode formats: 48 --- decode formats: 69


```

---

### Post by stoer on 2008-06-13
Hi again....
can't stop puzzling away at this one, sorry :)

Ok decided upon a different approach, to test in Linux if my .ape files were convertable or not.

Googled, alot.
Came up with this blog that provided a couple of usable approaches to the problem.

[http://www.gomellow.com/?p=24](http://www.gomellow.com/?p=24)

1. convtoflac.sh
and
2. lossless2lossy.sh

Convtoflac worked seamlessly converting my .apes to .flac files

Lossless2lossy converted my .apes to .wav and .mp3 simultaneously (seemd to take quite a while but resulted in good output).

So now i know that using 3 different conversions and 2 os's that it's not my .ape files that are a problem.  
pacpl is also unlikely to be the culprit,
so i guess that leaves me, screwed something up during installation probably.

---

### Post by cozmicharlie on 2008-06-13
stoer - check your pm I sent you a message.

---

### Post by cozmicharlie on 2008-06-17
For those of you trying to get Monkeys Audio (ape) to work with pacpl or just want a way to decode ape this method works.  It was kindly provided by e630193 as referenced in post #15 here [http://ubuntuforums.org/showthread.php?t=268538&page=2](http://ubuntuforums.org/showthread.php?t=268538&page=2).  For those interested in a script, e601393 has written a nice script for converting ape files and has offered it to the community.  Just send him a PM and he will send a copy.  I did not use the script because once the encoder is installed it works fine in pacpl.


Below is the method for installing ape codecs and converting in pacpl.

You will need the following;
[LIST=1]
[*]The mac binary - built from source available at[/url]http://supermmx.org/download/linux/m...9-u4-b5.tar.gz[/url]
[*]The apeinfo binary (for ape tags) - built from source available at [http://legroom.net/files/software/apeinfo10_source.tgz](http://legroom.net/files/software/apeinfo10_source.tgz) (Good source of info at [http://legroom.net/software/apeinfo](http://legroom.net/software/apeinfo))
[*]The flac binary, installable with your preferred package manager (Synaptic). It also provides metaflac, for flac tags.
[*]Nasm (required by mac), installable with Synaptic or your preferred package manager.
[*]Perl and the Perl File module installed on your Linux box.
[/LIST]

Installing the mac and ape binaries;
[LIST=1]
[*]Install flac & nasm using your favorite package manager (Synaptic).
[*]Unpack the mac source code you downloaded (#2 above) to wherever you please (I recommend the desktop). Right click on the folder>extract here.
[*]Extract the contents of the apeinfo10_.tgz file to the “mac-3.99-u4-b5/src/Examples/Analyze/Sample1” directory. In Ubuntu you double click on the file>extract> in the file browser go to the “mac-3.99-u4-b5/src/Examples/Analyze/Sample1” directory and click OK.
[*]Open a terminal and change directory to the extracted “mac-3.99u4-b5” folder. Build the mac binary: type or cut and paste the following command at the prompt:
```
./configure --disable-shared --enable-static && make
```
```
sudo make install
```
[*]This will install the mac binary as /usr/bin/mac which you can test without arguments. At a terminal prompt type mac and if it's OK, you'll get the usage message.
[*]Next copy the apeinfo binary (built when 'making' mac) from the “mac-3.99-u4-b5/src/Examples/Analyze/Sample1” directory to /usr/local/bin (or where ever you choose).
[/LIST]
That's it. Now test it:

$ pacpl –to mp3 yourmusicfile.ape

Enjoy everyone

---

