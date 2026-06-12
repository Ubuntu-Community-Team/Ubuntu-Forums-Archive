---
title: "Multimedia converter Try :D"
date: 2007-10-04
forum: Multimedia Production
---

### Post by Creative2 on 2007-10-04
[SIZE="5"][B][COLOR="DarkOrange"] this software will be supported by Brus46 :) plz don't  post  pvt message to me, Creative, :) i will not support this software anymore i have started my personal project [here]("http://fuocotools.byethost13.com")  or if you prefer on this ubuntu forum  [here]("http://ubuntuforums.org/showthread.php?t=776412")
[/COLOR][/B][/SIZE]

[SIZE="5"][B][COLOR="DarkOrange"]1 THIS PAGE  COULD HAVE  MANY ERRORS.&#8230;i will fix&#8230; i need of some time..! We are searching someone to translate it in FRENCH SPANISH CHINESE PLZ HELP US :D,  if you are interested plz write a message in this topic 
[/COLOR][/B][/SIZE]

[SIZE="5"][B][COLOR="DarkOrange"]2 !!!! BETA IS OUT INSTALL FROM REPO!!!!! website (italian only for now) [http://www.sciallo.net/ConvertIT/Indice.html](http://www.sciallo.net/ConvertIT/Indice.html)  here forum [http://www.sciallo.net/modules.php?name=Forums](http://www.sciallo.net/modules.php?name=Forums)
[/COLOR][/B][/SIZE]


[SIZE="5"][B][COLOR="DarkOrange"] 3 WE ARE TESTING THE COMMAND LINE BEFORE TO SAY ONE CONVERSIION DOESN T WORK TRY TO DOWLOAD YOUR FORMAT FROM HERE AND CONVERT IT. [http://samples.mplayerhq.hu/V-codecs/](http://samples.mplayerhq.hu/V-codecs/) 
[/COLOR][/B][/SIZE]
[http://samples.mplayerhq.hu/V-codecs/](http://samples.mplayerhq.hu/V-codecs/)


[SIZE="4"]**ConvertIT is a new mencoder \ffmpeg\ ffmpeg2theora oggenc&#8230;.GUI interface**
[/SIZE]

[IMG]http://img530.imageshack.us/img530/9973/multimediaconveterneweduv0.png[/IMG]
[SIZE="6"]What is it?[/SIZE]

the most converter cannot be fixed without knowladge , i think to bash script... if you don t know bash.. you can not fix it.you must learn the program language ,mencoder and ffmpeg too, and then fix it...i had used several bash script but my mov file doesn't want be converted. 

So after some time i have discovered i need only a stupid parameter (-srate in the mencoder's command line) so it was not a bug but only a lost parameter....

With this converter  if you have problem  you can fix it very easily.how?
[B]
This program is based on funzioni.cit (function.cit); In this  external text file is specificated the commandline, but this file is editable **with any text editor**, and its structure is very easy to understand.[/B]

**So you just find out(internet) your prefered commandline(be sure you are using the right version of  ffmpeg it has changed in this years so often&#8230;.) and set it on this file&#8230;.the interface will have your personal commandline ready to be used.**

[SIZE="6"]Requirements[/SIZE]

To install it, we need to use only terminal and\or an APT front-end (Synaptic, Adept..)

Remember ConvertIT is only a interface, and so it is based on **mencode**r **mplayer ffmpeg** etc..and therefore it need of these programs to install them from medibuntu repo 


[SIZE="4"]FIRST STEP ADD MEDIBUNTU REPO [/SIZE]

Below are the instructions to add the Medibuntu repository to your system's list of APT repositories. 
Add Medibuntu to your sources.list, as well as its GPG key to your keyring. Make sure to use the correct sources.list that corresponds to your current distribution. 

*** Ubuntu 6.06 "Dapper Drake": ***
```

sudo wget [http://www.medibuntu.org/sources.list.d/dapper.list](http://www.medibuntu.org/sources.list.d/dapper.list) -O /etc/apt/sources.list.d/medibuntu.list
```

** Ubuntu 6.10 "Edgy Eft":** 

```

sudo wget [http://www.medibuntu.org/sources.list.d/edgy.list](http://www.medibuntu.org/sources.list.d/edgy.list) -O /etc/apt/sources.list.d/medibuntu.list
```
[B]
 Ubuntu 7.04 "Feisty Fawn":[/B] 
```

sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list
```

** Ubuntu 7.10 "Gutsy Gibbon":** ```

sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
```

[SIZE="4"]Second step Then, add the GPG Key  [/SIZE] 
 ```

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
```



[SIZE="4"]INSTALL THESE "SHELL PROGRAMS"[/SIZE]

```

sudo apt-get install ffmpeg2theora mencoder mplayer w32codecs libogg0 libogg-dev libvorbis0a libvorbis-dev vorbis-tools mp32ogg ffmpeg  imagemagick youtube-dl poppler-utils  
```



[SIZE="4"]
3)[/SIZE]ConvertIT requires also gambas 2(maybe 64 bit doesn t work)&#8230; to install it :

**(if you are using ubuntu)**

```
sudo gedit /etc/apt/sources.list
```
[B]
(if you are using kubuntu)[/B]

```
sudo kate /etc/apt/sources.list
```

at the end of the file add this if you have:


[B]
GUTSY[/B]

no add nothing.


**FEISTY**

#Gambas2
```
deb http://xoomer.alice.it/pixel feisty gambas
```


now save and close text editor.

For older release:

[B]
DAPPER[/B]

#Gambas2
```
deb http://xoomer.alice.it/pixel dapper gambas

```

**EDGY**

#Gambas2
```
deb http://xoomer.alice.it/pixel edgy gambas
```



then in Console type this:

```
sudo apt-get update

```
and this:
```

sudo apt-get install gambas2
```

Now gambas is installed. ;)






[SIZE="6"]HOW CAN I INSTALL CONVERTIT ?[/SIZE]


there are 3 ways to install it:

[B][COLOR="black"][SIZE="3"]1)First way
[/SIZE][/COLOR][/B]



New version 

[COLOR="Blue"]
[http://www.sciallo.net/modules/archivio/archivi/ConvertIT/convertit.deb]("http://www.sciallo.net/modules/archivio/archivi/ConvertIT/convertit.deb")
[/COLOR]


[B]
[SIZE="3"]2)second  way USE THIS BECAUSE THE PROGRAM CHANGES VERY FAST [/SIZE][/B]


add this repo to your list type this in console :

```
sudo gedit /etc/apt/sources.list
``` (for kubuntu use kate instead gedit)

Now add this line at end of the file :

```
 deb http://www.sciallo.net/UbuntuRepo/myrepo binary/
```


[Here ]("http://www.sciallo.net/modules/archivio/archivi/MultimediaConverter/MultimediaConverterDEV.tar.gz")there are the source 

Save the file, close gedit. Now in the console :
```

sudo apt-get update
```

well load synaptic and search convertit&#8230;then install it&#8230;(if you don t know search in google how to install a program from synaptic&#8230;&#8230; i mean the graphical interface)

**[SIZE="3"]3)third way[/SIZE]**
This way is not the best...but anyway

 fo here

[http://www.sciallo.net/ConvertIT/Indice.html](http://www.sciallo.net/ConvertIT/Indice.html)

and  download the binaries

set permission as executable(right button on the file--->permission-----> as executable) 




[SIZE="6"]How can i load it?[/SIZE]




Go in you Audio video section on your ubuntu bar o in multimedia section in kubuntu bar 

to laod with terminal type this:
```

convertit.gambas
```

So now you can see ConvertIT&#8230;&#8230;..but there are not all conversion choices because this program is young&#8230;.in these days we are adding many conversion command line be patient ,if you are not, you can add commandline by yourself !
[B][COLOR="Olive"]

There are Funzioni.cit(for now it's funzioni.cit but you can load , there is not problem.) already made; 

Note ([here]("http://www.mediafire.com/?ebsmfn0zmll") )  you can find much more function..i am writer of the function&#8230;.so please help me to check  commandlines.. (fixed to mpeg conversion)


to load these funzioni.CIT into ConvertIT load  ConvertIT 

and then got --->-built function-->Load

select the file .CIT 

and click on the button----> Load a new function file.
[/COLOR][/B]


[SIZE="6"]How can i add features in my ConvertIT?[/SIZE]

[SIZE="5"] Adding conversion with ConvertIT's interface[/SIZE]

there are video but i think you can understand with this picture 

  [IMG]http://img228.imageshack.us/img228/2892/aggiuntafunzioniyi4.png[/IMG] 

high quality video(20 MB) : [http://www.mediafire.com/?7zwzbtzjkdd](http://www.mediafire.com/?7zwzbtzjkdd)

[youtube video]("http://it.youtube.com/watch?v=VtIa3xw2s3w") ( low quality) 

[SIZE="5"]Adding conversion without interface, editing Funzioni.cit[/SIZE]


!!!!NOTE VERY IMPORTANT!!!!

If you want add commandline by yourself do it well or the file will be not read .


if you want use mencoder to convert a file you must be sure you HAVE to install mencoder &#8230;.if you plan to add some commandline you must be sure to have installated the program.Remember ConvertIT is ONLY A NICE INTERFACE.

To know before try anything:

**to add features to ConvertIT you must edit FUNZIONI.CIT**

[SIZE="5"]where is the funzioni.cit?[/SIZE]

load ConvertIT because in the first loading ConvertIT create one default funzioni.cit in your home&#8230;(/home/YOURNICK/.MultimediaConverter  note it's a hidden folder..so you cannot see it&#8230;..

to see an hidden file

*for ubuntu*

and press **CTRL ;H**

for kubuntu in the windows click on menu visualisation and Show hidden file )

Now go here /home/YOURNICK/.convertit and

double click on funzioni.cit

This file has 3 &#8220;sector&#8221;

##Audio; ##Video;##Mobile

see this example:

##Audio
#
MP3
WAV
Normal
mplayer -ao pcm:file=OUTPUT INPUT
##Video
#
mpeg
OGG
low 640-480
ffmpeg2theora -x 640 -y 480 -v 2 -a 2 INPUT -o OUTPUT
##Mobile
#
3GP
AVI
Normal
ffmpeg -y -i INPUT -f avi -vcodec mjpeg -acodec pcm_s16le OUTPUTif you want add some feature for video put below video, if audio below audio&#8230;&#8230;.

One conversion is made in this way:


#                                       =mean start a new convesion
MOV                                 =Input FORMAT
AVI                                   = Output FORMAT
Norma                               =Label Quality or what you want
ffmpeg -i INPUT -f mp4 -vcodec mpeg4 -ar 48000 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320×240 -aspect 4:3 -y OUTPUT                        = your personal command line

NOTE in the command line must be :

INPUT                      for file input  (NOT INPUT.MOV)
OUTPUT                  for file output (NOT OUTPUT.AVI )

[SIZE="5"]
EXAMPLE HOW CAN I  FIND OUT AND MODIFY THE COMMAND LINE TO BE USABLE INTO funzioni.cit[/SIZE]

if you find command line for your conversion in GOOGLE OR YAHOO like this
(VERY IMPORTANT MANY COMMAND-LIVE WAS TESTED WITH 2000-2006 FFMPEG VERSION WITH FFMPEG 2007 VERSION, GUTSY, you must change some little thing...)

ffmpeg -i** inputfile.avi** -f mp4 -vcodec mpeg4 -ar 48000 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320×240 -aspect 4:3 -y **fileoutput.mp4**
[B]

In your funzioni.cit MUST BE WRITTEN IN THIS WAY(BELOW ##Video ...becasue is a video-conversion...[/B]

[COLOR="Olive"]#
AVI
MP4
my_prefered_name
ffmpeg -i** INPUT** -f mp4 -vcodec mpeg4 -ar 48000 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320×240 -aspect 4:3 -y **OUTPUT**[/COLOR]

What have we made?

Our conversion was for video so we will write it below video sector (##Video)

 (#)         this individualizes a new conversion
(AVI) i     input file format 
(MP4)     output fomat 
**comand line** = ( ffmpeg -i INPUT -f mp4 -vcodec mpeg4 -ar 48000 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320×240 -aspect 4:3 -y OUTPUT).
[B][I]
NOTE NO LEAVE SPACE AMONG CONVERSATIOTN SEE THIS FILE TO UNDERSTAND[/I][/B]

[COLOR="Green"]THIS WORKS

##Audio
#
MP3
OGG
Normal
mplayer -ao pcm:file=OUTPUT INPUT
#
MP3
WAV
Normal
mplayer -ao pcm:file=OUTPUT INPUT
##Video
#&#8230;&#8230;.ECT ETC[/COLOR]
[COLOR="Green"][COLOR="Red"]
THIS DOESN T WORK

##Audio
#
MP3
OGG
Normal
mplayer -ao pcm:file=OUTPUT INPUT
                                   <---no leave space
#
MP3
WAV
Normal
mplayer -ao pcm:file=OUTPUT INPUT
##Video
#&#8230;&#8230;.ECT ETC[/COLOR][/COLOR]

**Adding subtitle**

to load subtitle you must sure subtitles are in the same folder of video file and have the same name of the relative movie ( case sensive).

example: if i want add sutitle to: **myStuPidmovie.avi** i must put** myStuPidmovie.srt **[U]in the same folder.
[/U]

for mencoder just add this **-sub SUBTITLE -subfont-text-scale 4 **
here there is a funzioni.cit EXAMPLE
[B]
note i have written this file with this version of mencoder(2000-2006) and ffmpeg(2000-2006). you can find some conversions here[/B]

[here]("http://www.mediafire.com/?2jdvld5ogdm") you can download a video turtorial...i have tried to do my best..:D





**SOME USEFULL STUFF**
[B]
rotation :[/B]
```

mencoder  INPUT -oac copy -ovc lavc -vf rotate=1  -o OUTPUT
```
THIS is an example but you can use your prefered codecs the option rotate = -vf rotate=1 

                 0    Rotate by 90 degrees clockwise and flip (default).

                 1    Rotate by 90 degrees clockwise.

                 2    Rotate by 90 degrees counterclockwise.

                 3    Rotate by 90 degrees counterclockwise and flip.
[B]

Encode Flac![/B]

example 128kbitrate

```
ffmpeg -i INPUT -ab 128 -acodec flac OUTPUT.flac       
```


[SIZE="5"]SEE HERE IF YOU CANNOT SEE WELL CONVERTIT [/SIZE] 

[SIZE="4"]i have a problem, i can t see very well ConvertIT[/SIZE]

some people have said they cannot see well the program. i don t know why but  to solve this problem you can do this 

create this folder with this command

```
sudo mkdir /etc/qt3
```

then dowload this 2 files and put in that folder

```
 http://xoomer.alice.it/pixel/gutsy64/qtrc
 http://xoomer.alice.it/pixel/gutsy64/qt_plugins_3.3rc

```
you can do it with this bash script
```

#!/bin/bash
 ##
sudo mkdir /etc/qt3
 cd /etc/qt3
 sudo wget http://xoomer.alice.it/pixel/gutsy64/qtrc
 sudo wget http://xoomer.alice.it/pixel/gutsy64/qt_plugins_3.3rc

```
THANK TO 
PIXEL AND SUPREMUS italian\swiss ubuntu user\member


LANGUAGE 

FRENCH FUNZIONI.CIT  i will not support errors in that files....

[http://balba.free.fr/Funzioni.CIT](http://balba.free.fr/Funzioni.CIT)

THANKS to

Jester, because he has helped me to set my computer, Bruse46 for programming ConvertIT with gambas 2 and ITALIAN UBUNTU COMMUNITY, special thanks to irc.freenode.net #ubuntu-it

---

### Post by handband2 on 2007-10-06
I'm using Gnome so I changed the desktop file to have the program pop in my list of **Sound & Video**
```
$ sudo gedit multimediaconverter.desktop
```
OLD:
```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=MultimediaConverter
Comment=With this program you can convert many audio/video files in many formats
Exec=/usr/bin/multimediaconverter.gambas
Icon=/usr/share/pixmaps/multimediaconverter.png
Terminal=false
Type=Application
StartupNotify=true
Categories=Audio;Video;
```

I changed **Categories** to:
```
Categories=Application;AudioVideo;
```
NEW
```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=MultimediaConverter
Comment=With this program you can convert many audio/video files in many formats
Exec=/usr/bin/multimediaconverter.gambas
Icon=/usr/share/pixmaps/multimediaconverter.png
Terminal=false
Type=Application
StartupNotify=true
Categories=Application;AudioVideo;
```

---

### Post by Amazona aestiva on 2007-10-08
I've written about your app [here]("http://ubuntuforums.org/showthread.php?t=529759"). ;)

---

### Post by mocha on 2007-10-14
I was really excited to see an application like this that uses mencoder and has batch and scripting functions.  I'm really confused by your MMC files.  I went to encode a WMV to MPEG and it came out as an XVID with WMA audio...  I checked out the MMC file in the hidden directory and it seems like all the entries are pretty much the same and convert files to XVID.  Were your MMC files just an example of what can be done with the program?

---

### Post by Creative2 on 2007-10-14
Yes i used xvid codec very much. maybe there are some error...:D i have not so much time .. no it was not a example maybe the first step....as i have written THE PROGRAM IS VERY YOUNG(4 week) AND I AM A BIT ALONE TO WRITE FUNCTION....I HAVE NOT  SO MUCH TIME .....anyway thanks for the NEWS.....in the true i hoped someone would fix some commandline... :d this, i think, is  the force of this program.... can be fixed by everyone

i have seen the command line and i think you can choose lavac codec and set the right codec... or force the format.

**i have fixed audio codec mp3 and force format mpeg :D thanks mocha ubuntu user**

very important are: -ofps 25 and -vfscale !!! NOTE YOU CAN USE mpeg1video or mpeg2video for vcodec 

mencoder -oac mp3lame  -lameopts abr:br=128 -srate 48000 -ovc lavc -lavcopts vcodec=mpeg1video:vbitrate=500 -vf scale=320:240 -ofps 25 -of mpeg -o OUTPUT.mpg INPUT

you can test the commandline with Welcome.wmv to download the file go here

[http://samples.mplayerhq.hu/asf-wmv/](http://samples.mplayerhq.hu/asf-wmv/)

---

### Post by Creative2 on 2007-10-14
Fixed file mmc and some litte things

---

### Post by Creative2 on 2007-10-15
Added av i--- dvd ONLY COMMAND LINE these command line convert in mpeg format so you can use mandvd to create a nice dvd....

---

### Post by Creative2 on 2007-10-16
Update Version 0.0.25
subtitle added

[B]note
to load subtitle you must sure subtitles are in the same folder of video file and have the same name of the relative movie ( case sensive).[/B]

example: if i want add sutitle to: **myStuPidmovie.avi** i must put **myStuPidmovie.srt** in th_e same folder._




[B]
Seciton Resize Pda[/B]

##PDA
#
AVI
AVI
Resize per Pda
mencoder INPUT -ovc xvid  -oac copy  -vf scale=320:240 -xvidencopts fixed_quant=7 -o OUTPUT
#
AVI
AVI
Resize per Pda con SUB
mencoder INPUT -ovc xvid  -oac copy  -vf scale=320:240 -xvidencopts fixed_quant=7 -sub SUBTITLE -subfont-text-scale 4  -o OUTPUT


**Section Photo converter and Resize** [SIZE="4"][B]note you must have imagemagick  installeted sudo apt-get install imagemagick
[/B][/SIZE]

##Photo
#
ALL
jpg
Converti a Jpeg
convert INPUT OUTPUT
#
ALL
jpg
Convert to Jpeg and resize to 50 %
convert INPUT -resize 50% OUTPUT

Note 

you can rename your photo with multimedia converter.... :D  (main page---> rename output file...)

---

### Post by Creative2 on 2007-10-17
Photo conversion

you must install:

imagemagick

##Foto
#
ANY
JPG
Converte un qualunque tipo di immagine in jpg senza alterarne qualità o dimensioni
convert INPUT OUTPUT
#
ANY
PNG
Converte un qualunque tipo di immagine in png senza alterarne qualità o dimensioni
convert INPUT OUTPUT
#
ANY
GIF
Converte un qualunque tipo di immagine in gif senza alterarne qualità o dimensioni
convert INPUT OUTPUT
#
ANY
BMP
Converte un qualunque tipo di immagine in bmp senza alterarne qualità o dimensioni
convert INPUT OUTPUT

TEXT CONVERSION

you must install

poppler-utils

##PDF
#
PDF
HTML
PDF2HTML(layout saved)
pdftotext -layout -htmlmeta INPUT OUTPUT
#
PDF
HTML
PDF2HTML(layout not saved)l 
pdftotext -htmlmeta INPUT OUTPUT
#
PDF
TXT
PDF2TXT(layout saved)
pdftotext -layout INPUT OUTPUT
#
PDF
TXT
PDF2TXT(layout not saved)
pdftotext INPUT OUTPUT
#
PDF
PS
 PDF2 PS
pdf2ps INPUT OUTPUT
#
PS
PDF
 PS2PDF
ps2pdf INPUT OUTPUT
#
DVI
PS
DVI (output latex)2PS
divps -o OUTPUT INPUT

---

### Post by Creative2 on 2007-10-17
multimedia converter is develping so fast now we are working for look and style and some features for photo section :D

---

### Post by oxalá on 2007-10-17
this is 
really
really
really cool.

thanks :)

---

### Post by Creative2 on 2007-10-18
oxala'  thanks :D

=( there was an error in last Funzioni.mmc ....

i have written ffMPEG2theora instead of ffmpeg2theora -.-
you can dowload the new file funzionifixed.mmc and load it [here]("http://www.mediafire.com/?5zbyowwnm1o")

or fix by yourself  this is the correction 

#
AVI
OGG
top quality
ffmpeg2theora -v 10 -a 10 INPUT -o OUTPUT
#
AVI
OGG
top 640-480
ffmpeg2theora -x 640 -y 480 -v 10 -a 10 INPUT -o OUTPUT
#
AVI
OGG
medium 
ffmpeg2theora -v 5 -a 5 INPUT -o OUTPUT
#
AVI
OGG
medium 640-480
ffmpeg2theora -x 640 -y 480 -v 5 -a 5 INPUT -o OUTPUT
#
AVI
OGG
low
ffmpeg2theora -v 2 -a 2 INPUT -o OUTPUT
#
AVI
OGG
low 640-480
ffmpeg2theora -x 640 -y 480 -v 2 -a 2 INPUT -o OUTPUT
#
FLV
OGG
top quality
ffmpeg2theora -v 10 -a 10 INPUT -o OUTPUT
#
FLV
OGG
top 640-480
ffmpeg2theora -x 640 -y 480 -v 10 -a 10 INPUT -o OUTPUT
#
FLV
OGG
medium 
ffmpeg2theora -v 5 -a 5 INPUT -o OUTPUT
#
FLV
OGG
medium 640-480
ffmpeg2theora -x 640 -y 480 -v 5 -a 5 INPUT -o OUTPUT
#
FLV
OGG
low
ffmpeg2theora -v 2 -a 2 INPUT -o OUTPUT
#
FLV
OGG
low 640-480
ffmpeg2theora -x 640 -y 480 -v 2 -a 2 INPUT -o OUTPUT
#
MPEG
OGG
top quality
ffmpeg2theora -v 10 -a 10 INPUT -o OUTPUT
#
MPEG
OGG
top 640-480
ffmpeg2theora -x 640 -y 480 -v 10 -a 10 INPUT -o OUTPUT
#
MPEG
OGG
medium
ffmpeg2theora  -v 5 -a 5 INPUT -o OUTPUT
#
MPEG
OGG
medium 640-480
ffmpeg2theora -x 640 -y 480 -v 5 -a 5 INPUT -o OUTPUT
#
MPEG
OGG
low
ffmpeg2theora -v 2 -a 2 INPUT -o OUTPUT
#
MPEG
OGG
low 640-480
ffmpeg2theora -x 640 -y 480 -v 2 -a 2 INPUT -o OUTPUT

---

### Post by Creative2 on 2007-10-19
there was a bug....in multimedia converter we have fixed .....

we are  closer beta release :D

---

### Post by Creative2 on 2007-10-21
if you have upgrade multimedia converter youi can use this wizard....

#
ANY
MPEG
Wizard! preserved aspect ratio 
mencoder INPUT -ofps {PARAM1 Insert Frame For Second recommended value:Europe 25 for Other : 30 } -ovc lavc -lavcopts vcodec={PARAM2 Insert Video Codec Recommended Value mpeg1video or mpeg2video   }:vbitrate={PARAM3 Insert Video Bitrate Recommended Value 700  } -oac mp3lame -lameopts abr:br={PARAM4 Insert Audio Bitrate Recommended Value 128  } -srate {PARAM5 Insert Resamling Value Recommended Value 48000 } -vf scale -zoom -xy \{PARAM6 Insert Rescaling with preserved aspet ratio recommended value 720  } -xvidencopts fixed_quant={PARAM7 high quality and large file=1-30=low quality but small file. Balanced value: 4 } -of mpeg -o OUTPUT
#
ANY
MOV
Wizard!
mencoder -ofps {PARAM1 Insert Frame For Second recommended value:Europe 25 for Other : 30 } -oac faac -faacopts br={PARAM3 Insert Audio Bitrate Recommended Value 192 }:object=2 -channels 2 -srate 22050 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate={PARAM2 Insert Video Bitrate Recommended Value 300  } -of lavf -lavfopts i_certify_that_my_video_stream_does_not_use_b_frames -o OUTPUT INPUT
#
ANY
WMV
Wizard! input tested avi mov
mencoder INPUT -ofps {PARAM1 Insert Frame For Second recommended value:Europe 25 for Other : 30 } -ovc lavc -lavcopts vcodec={PARAM2 Insert Video Codec Recommended Value wmv2   }:vbitrate={PARAM3 Insert Video Bitrate Recommended Value 700  } -oac mp3lame -channels 2 -srate {PARAM4 Insert Resamling Value Recommended Value 48000 } -vf scale -zoom -xy \{PARAM5 Insert Rescaling with preserved aspet ratio recommended value 720  } -xvidencopts fixed_quant={PARAM6 high quality and large file=1-30=low quality but small file. Balanced value: 4 } -of lavf -lavfopts i_certify_that_my_video_stream_does_not_use_b_frames -o OUTPUT
#
ANY
FLV
Wizard!
ffMPEG -i INPUT -b -ofps {PARAM1 Insert Frame For Second recommended value:Europe 25 for Other : 30 } -ar {PARAM2 Insert Audio Bitrate Recommended Value 128  } -r 22050 OUTPUT

---

### Post by Creative2 on 2007-10-22
fixed funzioni mmc

wmv conversion (wmv2 for video codec and mp3 for audio....)

[http://www.mediafire.com/?agdabxk2xz0](http://www.mediafire.com/?agdabxk2xz0)

fixed wizard! wmv

---

### Post by Creative2 on 2007-10-22
fixed bug about "start menu" now multimedia converter will be in the right section multimedia for kde and audio video for gnome

---

### Post by Creative2 on 2007-10-22
testing funzioni.mmc

[http://www.mediafire.com/?exygl4gy10a](http://www.mediafire.com/?exygl4gy10a)

---

### Post by Creative2 on 2007-10-22
if you have updated multimedia converter you can try this new features

load this funzioni.mmc

[http://www.mediafire.com/?2bxwm9mj3ym](http://www.mediafire.com/?2bxwm9mj3ym)

---

### Post by Creative2 on 2007-10-22
i am sorry but ... 
another fixed funzioni.mmc

[http://www.mediafire.com/?52zjivc3iln](http://www.mediafire.com/?52zjivc3iln)

NB USE THE LAST VERSION FROM REPO....

---

### Post by Conspirator45 on 2007-10-24
tyvm. Am converting my first file now :)

---

### Post by Creative2 on 2007-10-24
ok we are very very close beta release i think this week we will release it...

1 the official web site will be ready soon it will have video HOW TO but it will take a bit to be finished

2 multimedia converter will change name 

3 i think i have written the most popul commandline but they can be wrong so please help me. i want repeat this : INSTALL MENCODER AND FFMPEG AND OTHER PROGRAMS WITH MEDIBUNTU REPO ACTIVATED!!!

4 we have made a forum in our site for multimedia converter... so people can share command line....or funzioni.mmc

5maybe this gui can be used in other linux distributioin but i don t know.

---

### Post by Creative2 on 2007-10-24
name xD

TheUltimateConverter --------------------------  2 (50%)
IT-Convert!-----------------------------------------1 (25%)
ConverterPro-------------------------------------- 0 (0%)
IT The Ultimate Converter------------------------ 0 (0%)
ConvertDummyHuman----------------------------0 (0%)
Tera-Converter------------------------------------0 (0%)
TotalConverter-------------------------------------1 (25%)
FAVC file audio video converter---------------- 0 (0%)

*IT = italian  =)

---

### Post by Creative2 on 2007-10-24
-.- 

bug in the latest version commandline are not editable..we will fix..

---

### Post by Creative2 on 2007-10-26
another file funzioni.mmc
added special functioon 
preview delay insert other audio file extract audio file ,extract video only, dvd standrd mpeg 

IMPORTANT CREATE A MOVIE FROM PHOTO DOESNT WORK 
[http://www.mediafire.com/?cqjymxzoxcp](http://www.mediafire.com/?cqjymxzoxcp)

---

### Post by holihue on 2007-10-28
This is a great program.:)

---

### Post by Creative2 on 2007-10-29
thanks holihue

we have changed Name xD into Convert IT 

we are addind feature , like youtube-dl downooader and the last things for beta release...
make a movie from photo collection..for now these 2 features doesn t work... we will add them 

cheers! 
Creative

---

### Post by mahiyar on 2007-10-29
Really an awesome problem and so flexible! exactly what linux epitomizes. However my little niggle is that the programme window is too big for my screen, can you help me there?

---

### Post by Creative2 on 2007-10-29
mm i know about that problem... , well but i think we have fixed... multimedia converter remember the last size you have set, so if you are able to re-size it your problem will be solved. the next time you will open it , it will remember your setting.

if it's not this the problem, as i think plz send me a screen shoot.(use image host website for that and past here the link , i have opened a channel in irc.freenode.net it's name is #ConvertIT

---

### Post by mahiyar on 2007-10-29
I'am sorry but I'am unable to resize it, here are the screen shots, meanwhile I will search and install a good irc programme.

---

### Post by Creative2 on 2007-10-29
:D remember install the lastest version... choose repo way to install it.. :D

---

### Post by mahiyar on 2007-10-29
Great programme, I have tried three to four different conversions and each time it worked flawlessly. Only the graphics need a little work upon, but not much problem about it. Will certainly spread the word!

---

### Post by Creative2 on 2007-10-29
=) unlucky i am not so nice fo graphics i am the ideator an writer of function my team are working around to improve graphics xD :P....would you like translate in indian ?? xD

---

### Post by Creative2 on 2007-10-29
this is free and makes the same.... and better xD

no complex because i have written every damned commandline and i have made wizard ....

---

### Post by Creative2 on 2007-10-29
added subtitle section to divx compatible

[http://www.mediafire.com/?cvmezmymm7f](http://www.mediafire.com/?cvmezmymm7f)

---

### Post by atlfalcons866 on 2007-10-30
how do i convert to playstation 3

---

### Post by Creative2 on 2007-10-31
here you can find some information NOT SURE....SO YOUR OWN  RISK 
I HAVE ONLY FOUND THE LINK 

i THINK you must install  this

[http://pspvc.sourceforge.net/](http://pspvc.sourceforge.net/)

then youi can use ffmpeg read here

[http://ps3wiki.qj.net/index.php/Using_ffmpeg_to_transcode_video_for_the_PS3](http://ps3wiki.qj.net/index.php/Using_ffmpeg_to_transcode_video_for_the_PS3)


here for mencoder but i dont know it seems no audio

mencoder heroes.s02e03.hdtv.xvid-hiqt.avi -ovc x264 -oac aac -x264encopts subq=6:pass=1:bitrate=500:bframes=3:partitions=p8 x8,b8x8,i4x4:weight_b:threads=auto:nopsnr:nossim:f rameref=3:mixed_refs:bime:brdo:level_idc=41:direct _pred=auto:trellis=1 -o experimental.mp4

cheers

---

### Post by Creative2 on 2007-11-02
problem with 3gp ---- mpeg -..-

---

### Post by ErwinC on 2007-11-02
great tool, just what I was looking for! 
Congratulations!

---

### Post by Creative2 on 2007-11-02
thank 

Remember to use the last funzioni.cit you must install the last version of ConvertIT we are workin to delete bug and improve it  so plz install from repo (THE SECOND WAY FOR INSTALLATION)

[http://www.mediafire.com/?ebsmfn0zmll](http://www.mediafire.com/?ebsmfn0zmll)

to use this file load converit and then

Built Functions---->Load-Merge--->Load New Function File

---

### Post by Shampyon on 2007-11-03
I had some troubles getting the converted 3GPs to work on my Motorola V3i. I looked up a command line tip that someone on these forums generously provided me with a while back, and added it as a new option:

ffmpeg -i INPUT -s qcif -vcodec mpeg4 -acodec aac -ac 2 -ar 16000 -r 25 -ab 32 -y OUTPUT

Just in case anyone else has the same problem I did :)

---

### Post by Creative2 on 2007-11-03
Shampyon thank you, 
your function is been added, but i think yu must set...video bitrate..



video bitrate need of k
audio bitrate doesn't need of k 

so i think i can be this 


ffmpeg -i INPUT -s qcif -vcodec mpeg4 -acodec aac  -b 300k -ac 2 -ar 16000 -r 25   -ab 32  -y OUTPUT

---

### Post by AsoSako on 2007-11-03
Thank you so much for making this program.  It works great.  The font would be nicer if it was a bit smaller but other than that I like it...  I will keep you updated if I find any bugs.

---

### Post by adt41287 on 2007-11-04
i absolutely love this program it works so well... there is one question i have about it though... i am trying to convert a .vob(.mpg) dvd file to .avi and it works all well and great but how can i choose what audio track to use from the dvd? i tested it out and seems to work very well... i converted 3 different files with the same setting from the same movie. 1 picked the french track, 1 picked english, and 1 picked directors commentary... can someone shed some light on this? (fyi i wanted all english)

---

### Post by Creative2 on 2007-11-04
thank you all but i  must write one thing : 

i am the i*_deator_* of the program and _i have written maybe the most of command lines_ but the _programer is another italian guy_. We have collaborated to do this interface. another guy have improved the style..and he have made some script ...xD now  there are a little folder and its name is script :D , think...bash script xD , anyway it is still in developing 


now the problem of vob file...

well the problem is this:

i have **1** vob file but i want encode with another audio file...

you can do this :

example with mencoder:

mencoder INPUT -ofps 25 -ovc xvid -oac copy -audiofile NAMEAUDIOFILE_MP3 -xvidencopts fixed_quant=3 -o OUTPUT




but if you have** many vob files **you can t  because the _name of the new audio tracks change_ ... 

but i am thinking there is a option on Convert it ....


 'OUT-NOEXT.MP3'  = mean the name of the outfile without the file extension (but if the name of output it the same of the input file...)

 if you can rename all new audio trank in THIS WAY maybe can work i am not sure:

NAME OF VIDEO FILE
[I]
FILEVOB1.VOB[/I]

NAME NEW AUDIO TRACK 

*FILEVOB1.MP3*

if you can rename for each video file the new adio track in the _same way _you could use this 


mencoder INPUT -ofps 25 -ovc xvid -oac copy -audiofile 'OUT-NOEXT.MP3' -xvidencopts fixed_quant=3 -o OUTPUT

because 

 'OUT-NOEXT.MP3'  = mean the name of the outfile without the file extension
so if the new audio track have the same name of the input file you could be able to encode many vob file without problem....

i know is not so clear  =(

---

### Post by Creative2 on 2007-11-04
Nb 

File Vob New Audio Track And File Encoded Must Be In The Same Folder

---

### Post by ocpaul on 2007-11-04
Cool Stuff but how do I get

Any to Mp4(ipod)
or FLV to Mp4(ipod)

---

### Post by Creative2 on 2007-11-04
mm i think i have fixed that convesion....i remember to you  it's a beta. 

i have not ipod so i can t test maybe you can fix....

if you have ipod  try this  in a terminal 

ffmpeg -i INPUT -f mp4 -vcodec mpeg4 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192k -s 320x240 -aspect 4:3 OUTPUT

then if it is correct you can add this features

I REMEMBER TO YOU : YOU CAN FIX look at  Shampyon's post he has fixed by himself...

cheers.

---

### Post by Creative2 on 2007-11-05
i want convert many vob with english audio, 

1   copy your vob in a folder : example myvideo.vob   myViDEo2.vob  myViideeo3.vob

2 copy your prefered language audio file in the same folder and r_ename it in the same of your vob file._
example : 

 myvideo.MP3  myViDEo2.MP3  myViideeo3.MP3


then you can use this :

mencoder INPUT -ofps {PARAM1 Write Frame for second reccomended value 25 } -ovc xvid -oac copy -audiofile 'OUT-NOEXT.MP3' -srate {PARAM3 Insert Resapling valuer: reccomended value 48000} -vf scale={PARAM4 Insert high and width max reccomended value : 720:576} -xvidencopts fixed_quant={PARAM5 high quality and large file=1-30=low quality but small file. Balanced value: 4 } -o OUTPUT

_if you use ntsc change fps into 30 and use as max size 720:480_

if you do this i think it will work let me know if it does.

---

### Post by Creative2 on 2007-11-06
testing

#merge avi
AVI 
AVI 
Merge file avi (avi file must have the same codec the same resolution etc...)
avimerge -o { PARAM1 Insert Output name: example bigfile.avi} -i { PARAM2 Insert input files example: /path/inputfile1.avi /path/inputfile2.avi}
#Resyncronize 
AVI
AVI
Automatic resyncronizing 
mencoder INPUT -ovc copy -aoc copy --forceidx -o OUTPUT
#Split avi
AVI 
AVI 
For size!Wizard!
avisplit -s { PARAM1 Insert the size, MB, example 700} -i INPUT 
#Split avi
AVI 
AVI 
For Time!Wizard!
avisplit -i INPUT -o OUTPUT -t {PARAM2 Choose the time range example: 00:10:00-00:11:00}

not tested yet

#Portable(psp ipod Pda iPhone)
ANY
MP4
!!TESTING!!Iphone me!
ffmpeg -i INPUT -f mp4 -vcodec mpeg4 -ar 44100 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192k -s 320x240 -r 30000/1001 -aspect 4:3 OUTPUT
#Portable(psp ipod Pda iPhone)
ANY
MP4
!!TESTING!!Wizard!Iphone me!
ffmpeg -i INPUT -f mp4 -vcodec mpeg4 -ar 44100 -maxrate 1000k -b {PARAM2 Insert Video Bitrate. reccomended value : 700k } -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab {PARAM1 Insert Audio Bitrate reccomended value : 192k } -s 320x240 -r 30000/1001 -aspect 4:3 OUTPUT
#PAL 
ANY
AVI
Wizard Divx player (PAL = Europe )  new audio track 
mencoder INPUT -ofps {PARAM1 Write Frame for second reccomended value 25 } -ovc xvid -oac copy -audiofile 'OUT-NOEXT.MP3' -srate {PARAM3 Insert Resapling valuer: reccomended value 48000} -vf scale={PARAM4 Insert high and width max reccomended value : 720:576} -xvidencopts fixed_quant={PARAM5 high quality and large file=1-30=low quality but small file. Balanced value: 4 } -o OUTPUT
#Ipod
ANY
MP4
!!TESTING!! H264
ffmpeg -y -i INPUT -v 1 -threads auto -vcodec h264 -b 500k -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 6 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 640x480 -acodec aac -ab 96 -ar 48000 -ac 2 -f mp4 -pass 2 OUTPUT

---

### Post by MepisReign on 2007-11-06
I would like to run this on my 64 bits system, how can that be done?
I have 2 systems
Kubuntu 7.10 64 bits
Ubuntu 7.10 64 bits

Regards,

MepisReign

---

### Post by Creative2 on 2007-11-06
mm you can try to install gambas2 for 64 systems but....many time gambas in 64 system has  problems.

when you have installed gambas2 i think you can use this interface.

not sure =(

cheers

---

### Post by MepisReign on 2007-11-06
> **Creative2 said:**
> mm you can try to install gambas2 for 64 systems but....many time gambas in 64 system has  problems.

when you have installed gambas2 i think you can use this interface.

not sure =(

cheers

I will try this at once and thank for your quick response, amico mio

Ok, I tried, but when I'm trying to install gambas2 Adept will state that the package is kind of broken. I will hold my horses until you develop a 64 bits version,

In any case Thank you

MepisReign

---

### Post by ocpaul on 2007-11-06
hey i tested your script these are want im getting.

These was all done using the same FLv file.
FLV to MP4

#[aac @ 0xb7dee308]libfaac doesn't support this output format!
#Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height
#ffmpeg -i INPUT -f mp4 -vcodec mpeg4 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192k -s 320x240 -aspect 4:3 OUTPUT

#Buffer overflow
#ffmpeg -i INPUT -f mp4 -vcodec mpeg4 -ar 44100 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192k -s 320x240 -r 30000/1001 -aspect 4:3 OUTPUT

# I keep getting ffmpeg2pass-0.log: No such file or directory
#ffmpeg -y -i INPUT -v 1 -threads auto -vcodec h264 -b 500k -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 6 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 640x480 -acodec aac -ab 96 -ar 48000 -ac 2 -f mp4 -pass 2 OUTPUT

ill try some more out if i get it working ill post back.

---

### Post by Creative2 on 2007-11-06
i dont know if you can install gambas2 32bit in your system, if you can it will work.

if you can't and with 64 bit installation BUT you have bad visiualization see here


i have a problem, i can t see very well ConvertIT

some people have said they cannot see well the program. i don t know why but to solve this problem you can do this

create this folder with this command



```
sudo mkdir /etc/qt3
```

then dowload this 2 files and put in that folder


 [http://xoomer.alice.it/pixel/gutsy64/qtrc](http://xoomer.alice.it/pixel/gutsy64/qtrc)
 [http://xoomer.alice.it/pixel/gutsy64/qt_plugins_3.3rc](http://xoomer.alice.it/pixel/gutsy64/qt_plugins_3.3rc)

you can do it with this bash script
Code:

```

#!/bin/bash
 ##
sudo mkdir /etc/qt3
 cd /etc/qt3
 sudo wget http://xoomer.alice.it/pixel/gutsy64/qtrc
 sudo wget http://xoomer.alice.it/pixel/gutsy64/qt_plugins_3.3rc

```

bueno xD

---

### Post by Creative2 on 2007-11-06
ocpaul  mmm n... xD maybe i have found the problem....

yes i have seen you have right,  that command line doesn t work

when youi choose video bitrate you must write 700k for 700kbitrate in audio instead 
if you write 192 that mean 192KBITRATE so in that command line , i think, there was this errors try this:

ffmpeg -i INPUT  -f mp4 -vcodec mpeg4 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 OUTPUT

---

### Post by ocpaul on 2007-11-06
Ok i been testing and this is the way i got it working on my IPOD VIdeo (5g)

I used a FLV i took from Youtube.

if i use -maxrate or -bufsize 4096 i will end up with buffer overflow or some other error.

Also it seems like it doesnt like -ab 192k
I had to use 128k to make it work.  (maybe this is youtube flv requirements im not sure)

Thanks got it working good on my ipod here is what i used:

FLV(Youtube)
MP4
ffmpeg -i INPUT -f mp4 -vcodec mpeg4 -b 300k -qmin 3 -qmax 5 -g 300 -acodec aac -ab 128k -s 320x240 -aspect 4:3 OUTPUT

---

### Post by Creative2 on 2007-11-06
i have used this


ffmpeg -i INPUT -f mp4 -vcodec mpeg4 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 OUTPUT

and now ffmpeg encode well, but i have not ipod so i don't know if aftter this encoded video are IPOD usable.

---

### Post by Creative2 on 2007-11-07
tested

#TO MOV
ANY
MOV
Wizard!using ffmpeg
ffmpeg -i INPUT -r {PARAM1 Insert Frame For Second recommended value:Europe 25 for Other : 30 } -f mov -vcodec mpeg4 -ar {PARAM2 Insert Video Resampling value Recommended Value 22050  } -b {PARAM2 Insert Video Bitrate Recommended Value 300k  } -acodec aac -ab {PARAM3 Insert Audio Bitrate Recommended Value 192 } -s {PARAM4 Insert Rescaling with preserved aspet ratio recommended value 640x480  } -aspect {PARAM6 Insert aspet ratio  4:3 or 16:9, recommended value: 4:3  } -y OUTPUT
#TO MOV
ANY
MOV
Simple mov
ffmpeg -i INPUT -r 25 -f mov -vcodec mpeg4 -ar 22050 -b 300k -acodec aac -ab 128 -y OUTPUT

#Increase\decrease the volume please! VIDEO
AVI
AVI 
Wizard! Increase volume with ffmpeg
ffmpeg -i INPUT -vcodec copy -acodec {PARAM2 Choose the codec reccomended !!mp3!! or aac ,or, amr_nb} -ab {PARAM3 Insert Audio Bitrate: example 192} -vol {PARAM1 Choose : Insert  How much you want increase\decrease the volume(mute=0-1000=crazy increasing). example : 100 } -y OUTPUT
#Increase\decrease the volume please! VIDEO
AVI
AVI 
Increase volume with ffmpeg
ffmpeg -i INPUT -vcodec copy -acodec mp3 -ab 128 -vol 400 -y OUTPUT
#Increase\decrease the volume please! AUDIO
ANY
ANY
Wizard! Increase volume with ffmpeg
ffmpeg -i INPUT -acodec {PARAM2 Choose the codec: aac ,or, mp3 ,or, amr_nb} -ab {PARAM3 Insert Audio Bitrate: example 192} -vol {PARAM1 Choose : Insert  How much you want increase\decrease the volume(mute=0-1000=crazy increasing). example : 400 } -y 'OUT-NOEXT.{PARAM4 Insert output format: ac3 or mp3 ,or amr}'
#Increase\decrease the volume please! AUDIO
ANY
MP3 
Increase volume with ffmpeg VALUE 100
ffmpeg -i INPUT -acodec mp3 -ab {PARAM3 Insert Audio Bitrate: example 192} -vol 100 -y 'OUT-NOEXT.MP3'

---

### Post by Creative2 on 2007-11-07
under testing 

to install 


gddrescue

dvdbackup

#Portable(psp ipod Pda iPhone)
ANY
MP4
!!TESTING!!Iphone me!
ffmpeg -i INPUT -f mp4 -vcodec mpeg4 -ar 44100 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -r 30000/1001 -aspect 4:3 OUTPUT
#Portable(psp ipod Pda iPhone)
ANY
MP4
!!TESTING!!Wizard!Iphone me!
ffmpeg -i INPUT -f mp4 -vcodec mpeg4 -ar 44100 -maxrate 1000k -b {PARAM2 Insert Video Bitrate. reccomended value : 700k } -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab {PARAM1 Insert Audio Bitrate reccomended value : 192 } -s 320x240 -r 30000/1001 -aspect 4:3 OUTPUT
#PAL 
ANY
AVI
Wizard Divx player (PAL = Europe )  new audio track 
mencoder INPUT -ofps {PARAM1 Write Frame for second reccomended value 25 } -ovc xvid -oac copy -audiofile 'OUT-NOEXT.MP3' -srate {PARAM3 Insert Resapling valuer: reccomended value 48000} -vf scale={PARAM4 Insert high and width max reccomended value : 720:576} -xvidencopts fixed_quant={PARAM5 high quality and large file=1-30=low quality but small file. Balanced value: 4 } -o OUTPUT
#Ipod
ANY
MP4
!!TESTING!! H264
ffmpeg -y -i INPUT -v 1 -threads auto -vcodec h264 -b 500k -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 6 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 640x480 -acodec aac -ab 96 -ar 48000 -ac 2 -f mp4 -pass 2 OUTPUT
#Creative Commandline
ANY
AVI
Encode divx compatible and burn a Dvd of them 
mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=256 -srate 48000 -xvidencopts fixed_quant=4 -o OUTPUT LINKEND k3b --datadvd 'OUTDIR'
#Creative Commandline
ANY
AVI
Encode divx compatible and burn a cd of them 
mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=256 -srate 48000 -xvidencopts fixed_quant=4 -o OUTPUT ; avisplit -s 5 -i 'OUT-NOEXT.AVI' LINKEND k3b --datacd 'OUTDIR' 
#Creative Commandline
ANY
MP3
Convert to mp3 and burn them! 192k
ffmpeg -i INPUT -ab 192k -acodec mp3 OUTPUT LINKEND k3b --audiocd 'OUTDIR' 
#Creative Commandline
DvD
DvD
dvd damaged? try to do an iso image 1 pass (in your home)
ddrescue /dev/dvd DVD.iso DVD.log
#Creative Commandline
DvD
DvD
hard dvd damaged? try to do an iso image 2 pass(in your home)
ddrescue -d -r1 /dev/dvd DVD.iso DVD.log
#Creative Commandline
DvD
DvD
Backup the main feature of the DVD
dvdbackup -F -i /dev/dvd -o 'OUTDIR' 
#Creative Commandline
DvD
DvD
Backup  whole feature of the DVD
dvdbackup -M -i /dev/dvd -o 'OUTDIR'

---

### Post by Creative2 on 2007-11-07
64 bit system and gambas2 issue

well gambas2 has problem and 64 bit debian pack cannot be used. We are talking about that and i think you should install 32bit gambas2 but i dont know how to do it. if someone knows how to do this plz write the solution.

---

### Post by Creative2 on 2007-11-07
testing file.cit
need for convert & burn  k3b

[http://www.mediafire.com/?edv3cmdzu2o](http://www.mediafire.com/?edv3cmdzu2o)

stable funzioni cit

[http://www.mediafire.com/?5yy1tsw1qjm](http://www.mediafire.com/?5yy1tsw1qjm)

---

### Post by Bonster on 2007-11-10
Well if you got 64bit and it doesnt work.

You can give Mediacoder a try.
It work with wine.

---

### Post by Creative2 on 2007-11-12
1 Problem with youtube dowload and convert and youtube dowload...
   we will fix. you can use it with this fuction but you are not able to se the name. 
youtube-dl {PARAM1 Insert link to of the video to download } -o youtube-dl {PARAM1 Insert link to of the video to download } -o  {PARAM2 Insert the output path  and file name.: example /home/myfile.flv}

2 fixed any-ogg( audio ) problem : double .ogg in the name 

[http://www.mediafire.com/?fdzg1dtt4lt](http://www.mediafire.com/?fdzg1dtt4lt)

---

### Post by chacham23 on 2007-11-18
Can someone help me with command to convert MKV to MP4(psp)??

---

### Post by Creative2 on 2007-11-18
what's the problem ?

this command line doesn't work?
```

mencoder INPUT -oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vbitrate=500:acodec=aac -af lavcresample=24000 -vf scale=368:208,harddup -lavfopts format=psp:i_certify_that_my_video_stream_does_not_use_b_frames -ofps 30000/1001 -o OUTPUT
```

---

### Post by chacham23 on 2007-11-19
> **Creative2 said:**
> what's the problem ?

this command line doesn't work?
```

mencoder INPUT -oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vbitrate=500:acodec=aac -af lavcresample=24000 -vf scale=368:208,harddup -lavfopts format=psp:i_certify_that_my_video_stream_does_not_use_b_frames -ofps 30000/1001 -o OUTPUT
```

Thanks m8 works great!!

but can u tell me were I can find a guide to mencoder commands for some adjustments?

---

### Post by Creative2 on 2007-11-19
yes of course 

you can find documentation about mencoder here

[http://www.mplayerhq.hu/DOCS/HTML/en/](http://www.mplayerhq.hu/DOCS/HTML/en/)

if you want a particular language select it here

[http://www.mplayerhq.hu/DOCS/HTML/](http://www.mplayerhq.hu/DOCS/HTML/)

=) but i think you can understand how mencoder work with the first page of this topic 
or if you prefer look at funzioni.cit i think you can understand

---

### Post by chacham23 on 2007-11-19
Thanks a lot Creative2
Ok now I have new problem :( all was working great but now I just check for new updates and it found new mencoder ver and now it doesnt works!!!!

```

mencoder sample.mkv -oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vbitrate=500:acodec=aac -af lavcresample=24000 -vf scale=368:208,harddup -lavfopts format=psp -ofps 30000/1001 -o bla.mp4
MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3200+ (Family: 15, Model: 47, Stepping: 2)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x42d18b7
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AC3), -aid 0, -alang eng
[mkv] Track ID 3: subtitles (S_TEXT/UTF8), -sid 0, -slang eng
[mkv] Track ID 4: subtitles (S_TEXT/UTF8), -sid 1, -slang fre
[mkv] Track ID 5: subtitles (S_TEXT/UTF8), -sid 2, -slang spa
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1280x528  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:31  fourcc:0x31637661  size:1280x528  fps:23.98  ftime:=0.0417
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
** MUXER_LAVF *****************************************************************
REMEMBER: MEncoder's libavformat muxing is presently broken and can generate
INCORRECT files in the presence of B frames. Moreover, due to bugs MPlayer
will play these INCORRECT files as if nothing were wrong!
*******************************************************************************
OK, exit
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
Opening video filter: [scale w=368 h=208]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
Audio LAVC, couldn't find encoder for codec aac.

Exiting...


```

why??????????:confused::confused::confused:

---

### Post by Creative2 on 2007-11-19
well as you see form here

udio LAVC, couldn't find encoder for codec aac.

Exiting...

mencoder or maybe better lavc (""is a part of ffmpeg"") cannot find the encoder :

this can happend :

if you update and the version is changed (ffmpeg and mencoder)
if you have write wrong the command line


i think you could use this I  don t know why some time can be usefull  try  this . post if you have solved
```

mencoder INPUT-oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vbitrate=500:acodec=aac -af lavcresample=24000 -vf scale=368:208,harddup -lavfopts format=psp -ofps 30000/1001 -of lavf -lavfopts i_certify_that_my_video_stream_does_not_use_b_frames -o  OUTPUT
```

---

### Post by Creative2 on 2007-11-19
mm sorry this is correct
```

mencoder INPUT-oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vbitrate=500:acodec=aac -af lavcresample=24000 -vf scale=368:208,harddup -lavfopts format=psp -ofps 30000/1001 -of lavf -lavfopts i_certify_that_my_video_stream_does_not_use_b_frames -o  OUTPUT
```

---

### Post by chacham23 on 2007-11-19
here what I get:
```

/Torrent/The.Departed.2006.HD.DVDRip.720p.x264.AC3-5.1-iLL/!sample$ mencoder The.Departed.2006.HD.DVDRip.720p.x264.AC3-5.1-iLL.sample.mkv -oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vbitrate=500:acodec=aac -af lavcresample=24000 -vf scale=368:208,harddup -lavfopts format=psp -ofps 30000/1001 -of lavf -lavfopts i_certify_that_my_video_stream_does_not_use_b_frames -o  try.mp4
MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3200+ (Family: 15, Model: 47, Stepping: 2)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Option lavfopts: Unknown suboption i_certify_that_my_video_stream_does_not_use_b_frames
Error parsing option on the command line: -lavfopts

Exiting... (error parsing command line)

```

then I was trying to remove the "i_certify..." and then it give me again the message with the "aac"....

I pretty sure the update is the problem but what I can do?

---

### Post by Creative2 on 2007-11-19
yes i see now 2000-2007 you have the lastest version 

mm

i think, libaac, instead of acc and delete " i_certifi" etc etc etc

damn now i must rewrite all command-line = omg

---

### Post by chacham23 on 2007-11-19
> **Creative2 said:**
> yes i see now 2000-2007 you have the lastest version 

mm

i think, libaac, instead of acc and delete " i_certifi" etc etc etc

damn now i must rewrite all command-line = omg

no still didnt work... if u will find solution please post here
```

:~/Torrent/The.Departed.2006.HD.DVDRip.720p.x264.AC3-5.1-iLL/!sample$ mencoder The.Departed.2006.HD.DVDRip.720p.x264.AC3-5.1-iLL.sample.mkv -oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vbitrate=500:acodec=libaac -af lavcresample=24000 -vf scale=368:208,harddup -lavfopts format=psp -ofps 30000/1001 -of lavf -lavfopts format=psp -o  try.mp4
MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3200+ (Family: 15, Model: 47, Stepping: 2)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x42d18b7
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AC3), -aid 0, -alang eng
[mkv] Track ID 3: subtitles (S_TEXT/UTF8), -sid 0, -slang eng
[mkv] Track ID 4: subtitles (S_TEXT/UTF8), -sid 1, -slang fre
[mkv] Track ID 5: subtitles (S_TEXT/UTF8), -sid 2, -slang spa
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1280x528  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:31  fourcc:0x31637661  size:1280x528  fps:23.98  ftime:=0.0417
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
** MUXER_LAVF *****************************************************************
REMEMBER: MEncoder's libavformat muxing is presently broken and can generate
INCORRECT files in the presence of B frames. Moreover, due to bugs MPlayer
will play these INCORRECT files as if nothing were wrong!
*******************************************************************************
OK, exit
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
Opening video filter: [scale w=368 h=208]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
Audio LAVC, couldn't find encoder for codec libaac.

Exiting...


```

---

### Post by chacham23 on 2007-11-21
bumped... someone??

---

### Post by Creative2 on 2007-11-21
mm i am sorry but i have update...but i have still 200-2006 mencoder so i can't fix...
but you can do this  post this command:

mencoder


i have this output 

encoder
MEncoder 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Genuine Intel(R) CPU           T2060  @ 1.60GHz (Family: 6, Model: 14, Stepping: 12)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
No file given

Exiting... (error parsing command line)

---

### Post by chacham23 on 2007-11-21
here:

MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3200+ (Family: 15, Model: 47, Stepping: 2)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
No file given

Exiting... (error parsing command line)

thanks for trying :)

---

### Post by chacham23 on 2007-11-21
OK I succeded with changing the "aac" to "libfaac" thanks m8!!!

---

### Post by disturbedite on 2007-11-23
thanks for making this program.  i would also prefer the buttons to be normal size, but that is ok.

what is the difference between multimediaconverter and convertIT?  only the amount and kind of scripts there are?

---

### Post by Creative2 on 2007-11-24
multimedia converter was the first name of the program  only this we have changed because there were too many "multimedia converter" and because of some issues..

mmmumble i don t remember(we have made 30\40 version ) but maybe .... maybe there are some differences .... multimediaconverter has less feautes for example i think some versions of multimedia converter have not LINKEND feautere(LINKEND stop the loop and start a new command line WITHOUT LOOP)

example :

mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=256 -srate 48000 -xvidencopts fixed_quant=4 -o OUTPUT LINKEND k3b --datadvd 'OUTDIR'

this command line make mencoder conversions for all files when it has finished it starts k3b and say to k3b to open a datacd section with all just converted file 

--datacd Create a new data CD project and add all given files

       --audiocd
              Create a new audio CD project and add all given files

       --videocd
              Create a new video CD project and add all given files

       --mixedcd
              Create a new mixed mode CD project and add all given files

       --emovixcd
              Create a new eMovix CD project and add all given files

       --datadvd
              Cre

---

### Post by Samhain13 on 2007-11-24
Just sharing. I ran the following command line to convert a 3gp video to avi, substituting INPUT with the name of my file plus extension:

```

ffmpeg -y -i INPUT -f AVI -vcodec mjpeg -acodec pcm_s16le OUTPUT

```

I got an "unknown codec" error. Fixed it by making "AVI" lowercase:

```

ffmpeg -y -i INPUT -f avi -vcodec mjpeg -acodec pcm_s16le OUTPUT

```

It worked OK. I just thought you guys should know. Cheers! and thanks for a very informative thread. :D

---

### Post by Creative2 on 2007-11-24
well everything in command line must be lowercase less INPUT and OUTPUT and some special command like OUTDIR or LINKEND 

=) but..... i don t understand why you want convet 3gp into avi and use this uncompressed audio codec pcm_s16le.....
 i think you can use compressed codec like mp3 or aac as you want you will get a nice avi too but much more compressed with the same quality

---

### Post by stinger30au on 2007-11-25
thanks for this, im yet to try it.
certainly looks the goods

---

### Post by Samhain13 on 2007-11-25
> **Creative2 said:**
> =) but..... i don t understand why you want convet 3gp into avi and use this uncompressed audio codec pcm_s16le.....
 i think you can use compressed codec like mp3 or aac as you want you will get a nice avi too but much more compressed with the same quality

I don't know either. I was just trying things out. :D
But I did have trouble loading compressed formats in Cinelerra when I was using Feisty and I got used to just using AVI when editing videos. Although now, I have to admit that I prefer the Theora/Vorbis format and Cinelerra seems to like it as well.

I'll try using MP3 or AAC next time. Thanks for the info.

---

### Post by mahiyar on 2007-11-25
Till now I was using multimediaconverter and was happy with it. Today I downloaded convertIT, and wow! the programme, the interface has really come a long way. It is not much time before it becomes a universal conversion programme capable of converting any type of one file to any other. Keep it up Creative2

---

### Post by Paul Chang on 2007-11-25
I am trying to convert FLV to MOV. After conversion is finished, I got a *.mov file with 0 bit size. The following is the log file. Could anyone tell me what is wrong? Thanks a lot in advance!

[COLOR="Blue"][FONT="Tahoma"]mencoder -oac faac -faacopts br=192:object=2 -channels 2 -srate 22050 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=300 -of lavf -lavfopts i_certify_that_my_video_stream_does_not_use_b_frames -o "/tmp/Sampras_Aggasi_TieBreak.MOV" "/tmp/Sampras_Aggasi_TieBreak.flv"
MEncoder 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Athlon 64 Newcastle,Winchester,San Diego,Venice; Sempron Palermo (Family: 15, Stepping: 0)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
91 audio & 204 video codecs
success: format: 0  data: 0x0 - 0x10eee88
libavformat file format detected.
VIDEO:  [FLV1]  320x240  0bpp  1000.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:35  fourcc:0x31564C46  size:320x240  fps:1000.00  ftime:=0.0010
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 22050 Hz, 2 ch, s16le, 64.0 kbit/9.07% (ratio: 8000->88200)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
OK, exit
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffflv] vfm: ffmpeg (FFmpeg Flash video)
==========================================================================
Building audio filter chain for 22050Hz/2ch/s16le -> 22050Hz/0ch/??...

[/FONT][/COLOR]

---

### Post by Creative2 on 2007-11-25
use this i have tested in windows too with mac player and ti works 

```
ffmpeg -i INPUT -r 25 -f mov -vcodec mpeg4 -ar 22050 -b 700k -acodec aac -ab 128 -y OUTPUT 
```

if you prefer use wizard :

```
ffmpeg -i INPUT -r {PARAM1 Insert Frame For Second recommended value:Europe 25 for Other : 30 } -f mov -vcodec mpeg4 -ar {PARAM2 Insert Video Resampling value Recommended Value 22050  } -b {PARAM2 Insert Video Bitrate Recommended Value 300k  } -acodec aac -ab {PARAM3 Insert Audio Bitrate Recommended Value 192 } -s {PARAM4 Insert Rescaling with preserved aspet ratio recommended value 640x480  } -aspect {PARAM6 Insert aspet ratio  4:3 or 16:9, recommended value: 4:3  } -y OUTPUT
```

---

### Post by Creative2 on 2007-11-25
thanks mahiyar :)
yes is universal i have a lots of command line , convert rpm to debian and many other but i am a bit alone to write these command line so... i need of time.. :)

The final target is write something like nero burning rom .... xD and we are close....i just say dvd wizard xD and photo to mpeg for dvd wizard ......

---

### Post by balba on 2007-12-02
Hi, 

I have just tested your software, especialy for MOV -> AVI ! Very good job !!!
I have some videos in landscape position, and I want to make a 90° rotation. Is it possible by batch commands ? Is it possible to add this function to the software ?

If you want a translation in french, I can do it (english ok, italian not so bad, 3 month in Roma :) ) . I don't know how to do, can you give me the list of sentences of the interface by private message ?

Thank you for your work !

---

### Post by Creative2 on 2007-12-02
yes it's possible (90 degree) ... i am writing funtion but i am a bit busy =) you can do man mencoder and search rotation to search into manual press:

/ rotation

---

### Post by Odd-rationale on 2007-12-02
Wow! Looks cool.

Does ConvertIT support flac?

---

### Post by balba on 2007-12-02
Creative2 > It's ok for the rotation ! I can do it with avidemux !

Send me a private messsage if you want a french translation of your software.

bye

---

### Post by Creative2 on 2007-12-03
rotation :
```

mencoder  INPUT -oac copy -ovc lavc -vf rotate=1  -o OUTPUT
```
THIS is an example but you can use your prefered codecs the option rotate = -vf rotate=1 

                 0    Rotate by 90 degrees clockwise and flip (default).

                 1    Rotate by 90 degrees clockwise.

                 2    Rotate by 90 degrees counterclockwise.

                 3    Rotate by 90 degrees counterclockwise and flip.



> **Odd-rationale said:**
> Wow! Looks cool.

Does ConvertIT support flac?

of course 

example 128kbitrate

```
ffmpeg -i INPUT -ab 128 -acodec flac OUTPUT.flac       
```

but for flac maybe is better:
```

ffmpeg -i INPUT -acodec flac OUTPUT 
```

or more(NOT TESTED) YOU must install sudo apt-get install flac
```

flac INPUT OUTPUT -X 
```

---

### Post by Odd-rationale on 2007-12-03
Thanks! I'll give it a try.

---

### Post by tgpfarm on 2007-12-03
Hello, I have having a problem with ConvertIT.

I am trying to convert a wmv or mpg to FLV.

I get a line like:
```
ffmpeg -i "input.mpg" -b 200 -ofps 30 -ar 128 -r 22050 "output.FLV"
```

but this is not working, I get this error:
```
ffmpeg: unrecognized option '-ofps'
```

---

### Post by Creative2 on 2007-12-04
correction :

```
ffmpeg -i INPUT -r 25 -f flv -ar 22050 -b 700k  -ab 128 -y OUTPUT
```

you can change aresampling (ar 22050 if you want you can use 48000)  for my use i prefer

```
ffmpeg -i INPUT -r 25 -f flv  -y OUTPUT  

```
maybe if you are in america  you want 30 frame for second 

```

ffmpeg -i INPUT -r 30  -f flv  -y OUTPUT
```

wizard
```

ffmpeg -i INPUT -b {PARAM3 Insert Video Bitrate example Value 200k  }  -r {PARAM1 Insert Frame For Second recommended value:Europe 25 for Other : 30 } -ab {PARAM2 Insert Audio Bitrate Recommended Value 128  } -ar  {PARAM4 Insert Audiio resampling Example Value 22050 or 48000  }  -y OUTPUT

```

---

### Post by vishzilla on 2007-12-04
[http://media-convert.com/](http://media-convert.com/) is an online media conversion website. Check it out

---

### Post by Creative2 on 2007-12-04
> **vishzilla said:**
> [http://media-convert.com/](http://media-convert.com/) is an online media conversion website. Check it out

-.-' we know there are win softwares and online softwares...but do you know about  them speed?  here is developing a linux interface so i think is stupid come here and say you have discovered the hot water there are online softwares.

do not spam with this.

---

### Post by vishzilla on 2007-12-04
> **Creative2 said:**
> -.-' we know there are win softwares and online softwares...but do you know about  them speed?  here is developing a linux interface so i think is stupid come here and say you have discovered the hot water there are online software.

do not spam with this.

sorry, my bad...

---

### Post by nrune on 2007-12-04
I have a Nokia N800 internet tablet. it does video very well, but need to be encoded just so. The video needs to be encoded to about 800 kbps or 400x240 screen size  with 96kbps mp3 audio.  I tried changing one of the command lines but it did not work at all.  Can some one help with a conversion code so I can use convertit? 

Thanks!

---

### Post by suffice on 2007-12-04
how about .ogm video files to xvid .avi?....

this app looks amazing, and will change file conversion forever.....

---

### Post by Odd-rationale on 2007-12-04
> **Creative2 said:**
> 
of course 

example 128kbitrate

```
ffmpeg -i INPUT -ab 128 -acodec flac OUTPUT.flac       
```

but for flac maybe is better:
```

ffmpeg -i INPUT -acodec flac OUTPUT 
```

or more(NOT TESTED) YOU must install sudo apt-get install flac
```

flac INPUT OUTPUT -X 
```

None of these are working for me. I'm trying to do .wma to .flac. I have flac installed and do not mind using it.

Right now I'm using a nautilus script I found. I know there is a way to do it with ConvertIT. I really appreciate your help!

Attached is the script. If it would be of any help.

---

### Post by Creative2 on 2007-12-04
> **nrune said:**
> I have a Nokia N800 internet tablet. it does video very well, but need to be encoded just so. The video needs to be encoded to about 800 kbps or 400x240 screen size  with 96kbps mp3 audio.  I tried changing one of the command lines but it did not work at all.  Can some one help with a conversion code so I can use convertit? 

Thanks!

NOKIA ISSUE 

well i suppose your phone can play mpeg4 so try this

mp3 try to change resalping (16000 24000 22050 or 48000)

```
ffmpeg -i INPUT -s 400x240  -vcodec mpeg4 -acodec mp3 -ac 2 -ar 16000 -r 25 -ab 32 -y OUTPUT
```

or with aac codec 

```
ffmpeg -i INPUT -s 400x240  -vcodec mpeg4 -acodec aac -ac 2 -ar 16000 -r 25 -ab 32 -y OUTPUT
```

---

### Post by Creative2 on 2007-12-04
> **Odd-rationale said:**
> None of these are working for me. I'm trying to do .wma to .flac. I have flac installed and do not mind using it.

Right now I'm using a nautilus script I found. I know there is a way to do it with ConvertIT. I really appreciate your help!

Attached is the script. If it would be of any help.

-.-' i have just convertedd into flac with

ffmpeg -i INPUT -acodec flac OUTPUT

plz check if you have installed ffmpeg 2007 from medibuntu repo.

---

### Post by Creative2 on 2007-12-04
> **suffice said:**
> how about .ogm video files to xvid .avi?....

this app looks amazing, and will change file conversion forever.....

well i have nerver xD used this  format.....it's a ogg audio file plus mpeg4  but if you have some problem with any-avi  (mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000 -xvidencopts fixed_quant=4 -o OUTPUT) 

you can do this 

extract video stream with

```
ffmpeg -i INPUT  -an -vcodec copy -y OUTPUT.ogm
```

extract audio stream with

```
ffmpeg -i INPUT  -vn -acodec copy -y OUTPUT
```

and then convert them video avi with

```
mencoder INPUT -ofps 25 -ovc xvid -oac copy -xvidencopts fixed_quant=4 -o OUTPUT
```

and audio with
```

ffmpeg -i INPUT -ab 128 -acodec mp3 OUTPUT
```

 after that with you can put the audio in the video with
```

mencoder INPUT -oac copy -ovc copy -audiofile {PARAM1 Insert audio mp3 file}  -o OUTPUT 
```

---

### Post by Odd-rationale on 2007-12-04
> **Creative2 said:**
> -.-' i have just convertedd into flac with

ffmpeg -i INPUT -acodec flac OUTPUT

plz check if you have installed ffmpeg 2007 from medibuntu repo.

Yes, I have ffmpeg installed from the medibuntu repos.

Actually, I think it is a problem with .wma's (it is a Windows Media Audio Lossless, if that makes any difference). Because I can use ConvertIT to convert other types of media - .mp3, .ogg. etc. But when I try to convert a .wma, I get an error message:

> The filename "Track 01.flac" indicates that this file is of type "FLAC audio". The contents of the file indicate that the file is of type "plain text document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "plain text document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file.

I'm trying to figure out what command the nautilus script issues (I know almost nothing about programming, though). It seems like it convert the the .wma to a .wav. Then the .wav to .flac. Then it deletes the .wav.

Is there a way I can do this in ConvertIT with one command? I can do each individual one with no problems, but that is rather cumbersome.

Thanks!

---

### Post by Creative2 on 2007-12-04
mm well done if you have right you must do double passages:

example here this convert before in wav then use oggenc to encode into ogg format


mplayer -ao pcm:file='OUT-NOEXT.wav'  INPUT; oggenc -q 10 'OUT-NOEXT.wav' OUTPUT; rm 'OUT-NOEXT.wav'

so for yours issue 

'OUT-NOEXT'  this mean path + filename without extension 

so this before extract wav file the use flac to encode into flac and then remove wav file

mplayer -ao pcm:file='OUT-NOEXT.wav'  INPUT ; flac  'OUT-NOEXT.wav' OUTPUT; rm 'OUT-NOEXT.wav'

---

### Post by Creative2 on 2007-12-04
but before to use convertit try to find out how to convert wma....try with console 

1 extract wav file with 

mplayer -ao pcm:file=yourname.wav  INPUT.wma

2 encode with flac 

 flac  yourname.wav ooutputname.flac

---

### Post by Odd-rationale on 2007-12-04
Super! You're awesome!

I used this:
wma -> flac
```
mplayer -ao pcm:file=OUT-NOEXT.wav INPUT; flac -f OUT-NOEXT.wav OUTPUT; rm OUT-NOEXT.wav
```
Requires flac. (sudo apt-get install flac)

Thanks for your help!

---

### Post by nrune on 2007-12-04
Never mind seems to be working, thanks so much for your help!!

---

### Post by Creative2 on 2007-12-05
nrune plz tell us what you have used...

---

### Post by Morgan86 on 2007-12-12
Very good program Creative2 :)
It's the most complete and personalisable convertion tool for linux. In future it will be most know and we will find it on the ufficial repo of ubuntu!
Continuate così, BRAVI
CIAO

---

### Post by EmilyRose on 2007-12-17
Ok, so I'm trying to convert a .mov to .mpeg... it runs and seems to work, but then when I go to open the .mpeg it doesn't play... says 0:00/0:00 in totem as the length.. converting as both normal and resized output is:

> mencoder -oac mp3lame -lameopts abr:br=128 -srate 48000 -ovc lavc -lavcopts vcodec=mpeg1video:vbitrate=700 -ofps 25 -of mpeg -o "/home/emily/march18.MPEG" "/home/emily/Videos/march18.MOV" 
MEncoder 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz (Family: 6, Model: 15, Stepping: 10)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x3b4b606
Quicktime/MOV file format detected.
VIDEO:  [jpeg]  320x240  24bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:7  fourcc:0x6765706A  size:320x240  fps:15.00  ftime:=0.0667
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 8000 Hz, 1 ch, u8, 64.0 kbit/100.00% (ratio: 8000->8000)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
PACKET SIZE: 2048 bytes, deltascr: 245760
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG decoder)
==========================================================================
VDec: vo config request - 320 x 240 (preferred colorspace: Planar 422P)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar 422P as output csp (no 1)
Movie-Aspect is undefined - no prescaling applied.
videocodec: libavcodec (320x240 fourcc=3167706d [mpg1])
INITV: 0.200, 0.160, fps: 25.000
Pos: 129.3s   1941f ( 0%) 126.51fps Trem:   0min   0mb  A-V:0.036 [428:123]


---

### Post by Creative2 on 2007-12-17
your log :

**"VDec: vo config request - 320 x 240 (preferred colorspace: Planar 422P)"**

you have to resize.....add, to your command line

-vf scale -zoom -xy 320 

or 
-vf scale=320:240 

or easly use ffmpeg

---

### Post by Creative2 on 2007-12-17
another thing...you have mencoder 2006.... we are in 2007, i reccomended to upgrade..there is the debian package..so it's very easy

---

### Post by earthtux on 2007-12-21
first of all, good job
I can use some help with the mp4 file i downloaded from google video
[http://video.google.com/videoplay?docid=-1663597729999672400](http://video.google.com/videoplay?docid=-1663597729999672400)

i want to convert it from mp4 to avi

I tried you software but the output file has color flakes which means un-watchable

Could you please help me ? thanks in advance!

---

### Post by RedNikon on 2007-12-21
Converting to MPEG from MKV, how do I keep subtitles?

---

### Post by Creative2 on 2007-12-22
Red nikon:

more information....how is the subtitle ? srt files ?
if you have srt file you can add  to your command line this 

FFMPEG 

-newsubtitle  SUBTITLE

MENCODER

-sub SUBTITLE -subfont-text-scale 4 

BUT THE SUBTITLE MUST HAVE THE SAME NAME OF THE MOVIE...read documentation ...next time...


for
EARTHTUX:

plz i have no time send me (on mediafire or similar a little piece of your movie...
to do it use this 

mencoder INPUT -ovc copy -oac copy -endpos 15 -o OUTPUT 

it will encode only 15 seconds)

---

### Post by MepisReign on 2007-12-25
It would be possible to fix the progress bar display?
I mean, the video file gets converted but the progress bar during converting remains in zero. Besides that small detail the software works flawlessly with no major bugs, Congratulations!!!!!!!

Best Regards!

MepisReign

---

### Post by linkunderscore on 2007-12-25
this doesn't work for me :( 

I need to convert avi to mp4 (ipod) 

it doesn't work and when I try to do it manually using this:

```
ffmpeg -i movie.avi -f mp4 -vcodec mpeg4 -ar 48000 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320×240 -aspect 4:3 -y outputmovie

```

I get a no aac codec error...

---

### Post by Creative2 on 2007-12-26
linkunderscore

**[SIZE="4"]Faq:Ipod[/SIZE]**

**unknow codec aac**

**have you installed ffmpeg from medibuntu repo?**

when you get that error unknow aac codec  means you have not installed correctly ffmpeg with aac support. 

[B]what can i do?
[/B]

you don't need of compile ffmpeg there is a package in medibuntu repo.
 turn on that repo, then sudo apt-get update ,and reinstall it

 --->google---> medibuntu--->how to--->read the documentation.

[B]*and REInstall ffmpeg. *
[/B]

if you write sudo apt-get install ffmpeg it will not work.
 Why?
 because it will say you have already installed ffmpeg. So ... use synaptic or adept and REINSTALL IT or remove and install again it




NOTE FOR YOU linkunderscore.

but your commandline is wrong. You  get the OLD command line. maybe old funzioni.CIT or maybe my mistake, i dont remember.
[I]
ffmpeg 2007 need of "k" for bitrate....[/I]

NOTE I HAVE NOT IPOD, i have creative lol, SO I CAN'T TEST IF WORKS OR NOT.SO IPOD USER WOULD TEST THE COMMANLINE AND SAY ME IF WORKS NOT WORK WHICH THE BEST PARAMETER ETC:

according with ffmpeg documentation :

ANY MP4 320x240 pixel

```
ffmpeg -i INPUT -acodec aac -ab 128k -vcodec mpeg4 -b 1200k  -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x240 -title X output
```

or if you prefer 320x180 pixel

```
ffmpeg -i INPUT -acodec aac -ab 128k -vcodec mpeg4 -b 1200k  -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x180 -title X output
```

you can modify the command line according with ffmpeg documentation see here for HIGH QUALITY
[http://ffmpeg.mplayerhq.hu/faq.html#SEC18](http://ffmpeg.mplayerhq.hu/faq.html#SEC18)

with this

```

-mbd rd -flags +4mv+trell+aic -cmp 2 -subcmp 2 -g 300 -pass 1/2', things to try: '-bf 2', '-flags qprd', '-flags mv0', '-flags skiprd
```

 for example:

```
ffmpeg -i INPUT -acodec aac -ab 128k  -vcodec mpeg4 -b 1200k  -mbd rd -flags +4mv+trell+aic -cmp 2 -subcmp 2 -g 300 -pass 1/2 -s 320x240 -title X OUTPUT 

```


little note 

it can work with kb instead of k

---

### Post by Creative2 on 2007-12-26
> **MepisReign said:**
> It would be possible to fix the progress bar display?
I mean, the video file gets converted but the progress bar during converting remains in zero. Besides that small detail the software works flawlessly with no major bugs, Congratulations!!!!!!!

Best Regards!

MepisReign

mm i don't know, the other guy is a bit busy so it will take time

---

### Post by ron999 on 2007-12-27
Hi Creative2

This is a great program, but I think that there's a bug.

When I convert a track to mp3 such as this:-
03-Booker T. & The MGs - Green onions.wav

The program names the new file:-
03-Booker T.MP3

It's using the '.' after 'Booker T' as the end of the track name.


:cool:

---

### Post by Creative2 on 2007-12-28
yes it's a bug. i have seen.

NOTICE :

well i will say here, it's close the opeing of official forum for convertit.

untill that day i will support as i can convertit here. BUt when it will be opened i will not support anymore here.

VERY IMPORTANT THING.

I HAVE LEFT THE PROJECT....I have made my personal interface :) so i will support that if i will release someday it.

But don't worry the New forum for converIT will help you.

---

### Post by Creative2 on 2007-12-29
ok i have released my converter :)
it's alpha because i haven't make a nice installer anyway...i know it works fine but i need of some time to do documentation etc 

[http://ubuntuforums.org/showthread.php?t=652843](http://ubuntuforums.org/showthread.php?t=652843)

---

### Post by Creative2 on 2008-01-08
ok forum works 

[http://www.sciallo.net/modules.php?name=Forums](http://www.sciallo.net/modules.php?name=Forums)

---

### Post by dotancohen on 2008-01-18
Thanks for the wonderful program. ConvertIt is a very functional application, but it feels very poorly made and ameturish, to the point where I'm embarrased to suggest it to people. For one thing, it is written in Basic. For another the UI is very childish. If you would like, I can help make suggestions regarding UI design. I would suggest that the next version be rewritten in a modern language such as Python.

---

### Post by Creative2 on 2008-01-18
4 weeks ago brus46 started to write it in phyton...you should condider ...we have no time...but convertIT2 will have phyton and glade...one day...

Brus46  ,i remember that he is the programmer, much more expert than me ,  i am sure, he  will create something in phyton much better than converIT first version. but it will take time 

For now there are ConvertIT developed in Gambas and Fuoco Tools,my personal project, developed in kommander one day there will be ConverIT2 written in phyton and glade.

If you want contribute just go here [http://www.sciallo.net/modules.php?name=Forums](http://www.sciallo.net/modules.php?name=Forums) (you must be regirested...)

---

### Post by Creative2 on 2008-01-18
news :)

CONVERTIT2  is coming gtk glade and phyton

[http://www.sciallo.net/modules.php?name=News&file=article&sid=51&mode=&order=0&thold=0](http://www.sciallo.net/modules.php?name=News&file=article&sid=51&mode=&order=0&thold=0)

---

### Post by brus46 on 2008-01-21
yes, now i'm creating the second version of convertit!!

the version creative posted is just a preview ;)

however something starts to work! ;)

i'm looking for a cool new name... if someone has some ideas...
something like: "ConvertIT2, the second conversion" :popcorn:

---

### Post by Creative2 on 2008-01-21
dude :P you are here now :D ! 
 i leave to you the managment of the post

---

### Post by brus46 on 2008-01-21
i belive that i should open a new post for speaking about the new version.
i'll do as soon as the program will work a little more :biggrin:

---

### Post by imon9 on 2008-01-21
dude, brus46,

i like the idea of the convertit2 in python...i think it will be way more neat than gambass :/

anyhow, i downloaded the alpha u placed there at ur website, here's a bit of early comment before this went too far

(1) could you please let someone design the logo for you?
(2) plase use standart icon like tango, tangerine, human from ubuntu...it blends into the theme better (or make them configurable)
(3) really dislike the "side-tabs".. IMHO, tab at the top will be seems cleaner

thanks for the great project

(oh ya, regarding the logo, i volunteer to design too..but if u see what the community did with the logo competition for xmms2, you will be amazed wat a great job the community did)

---

### Post by brus46 on 2008-01-21
they are FULL COSTUMIZABLE!
browse in the folder "picture" and there you can put yours one.

soon the program will have a tool to do this :)

I missed to write in the english post, but into the italian one i ask for some graphician for the logo, the file icons and the conversion icons

i was thinking about a sort of contest for that :)

for the tabs, yeah, good idea. :guitar:

this evening i'll load the new version on my site :) stay tuned ;)

---

### Post by brus46 on 2008-01-21
new version loaded

---

### Post by brus46 on 2008-01-22
Hi, i had put the tango theme on the program :)

if you want the old theme:
- donwload it from the ufficial site (_***Yes, we need help to improve the site***_): [http://www.sciallo.net/ConvertIT2/](http://www.sciallo.net/ConvertIT2/)
- start the program and go into Edit->Preferences->Icon Set and load the file you had just downloaded.

The others options in preferences still don't work. I'll do them when i had fixed some problem with the command executor (if you try the youtube conversion you'll see the program freeze until it ends...)

If some-one wants to create his own iconset should create a tar.gz with the same folders of the one you found on the site.
Please, if you do some themes send me the link and I'll put them into the site

---

### Post by imon9 on 2008-01-22
look much nicer now,

i dunno if my feedback is welcomed at the moment since convertit 2 still in alpha, but here i goes:
(1) add drag-and-drop function for adding files
(2) i added files and the list is long, but convertit2 show really big "?" icon next to each entry and the gap between line is rather big :)

---

### Post by brus46 on 2008-01-22
> **imon9 said:**
> look much nicer now,

i dunno if my feedback is welcomed at the moment since convertit 2 still in alpha, but here i goes:
(1) add drag-and-drop function for adding files
(2) i added files and the list is long, but convertit2 show really big "?" icon next to each entry and the gap between line is rather big :)

good ideas but i fell it's a little earlier :)

for the BIG ? you have to substitute the picture in this location:
/home/yourname/.convertit2/pictures/?.png
another solution is to add the picture for that file format into this folder:
/home/yourname/.convertit2/pictures/ext/#.png
where # is your missing format

for example you want to add an icon for .zip format?
put in that folder a file as name: zip.png


i was thinking about made a theme with the same pictures of these but a little smaller.

try make your own ;) it's really simple!

---

### Post by brus46 on 2008-01-23
new version online.

i suggest you to upgrade.

the new version has many more features and will warn you if there are new versions online (need internet connection of course)

soon on the site i'll post a little guide to create iconsets and fuctions files.
if you create them properly users will be able to know when you change something on the theme and can download the upgrade ;)

soon i will charge a new theme "DefaultLittleVersion"

bye

---

### Post by ernz on 2008-01-24
It's about *!#&!~#% time!! Well done Mosconi! The community (and I personally) have needed a proper, usable alternative to mencoder and other CLI-based conversion apps for a long time. It looks great, hasn't failed me yet and it's really easy to use.

I for one thank and congratulate you on this project! Why isn't this in the repos!??!

---

### Post by brus46 on 2008-01-24
> **ernz said:**
> It's about *!#&!~#% time!! Well done Mosconi! The community (and I personally) have needed a proper, usable alternative to mencoder and other CLI-based conversion apps for a long time. It looks great, hasn't failed me yet and it's really easy to use.

I for one thank and congratulate you on this project! Why isn't this in the repos!??!

Thank you very much!

belive me the second version will be more and more and more and ....... more better than the first one ;)

i've done a little todo in italian, as soon as i've a little time i'll translate it to english so you'll know what it's in my mind for the future of the project. :guitar:

---

### Post by sdowney717 on 2008-01-27
I converted 2 files but now I instantly get the 

Convertit Complete! message,  but it does nothing.

So is it some kind of temporary file issue? I completely uninstalled and then reinstalled but it did not help.

---

### Post by brus46 on 2008-01-27
tell me which tipe of conversion you've tried. probably you haven't got installed all the dependences. (to see them double click on the function and then see the "require" field. you can even try the button "install dependences", it'll work only on ubuntu)


In those days i'm going to have some exams so i'll have to study a little :p
However i've improved the website: [http://www.sciallo.net/ConvertIT2/EN/index.html](http://www.sciallo.net/ConvertIT2/EN/index.html)
better that the other ;) ?

---

### Post by sdowney717 on 2008-01-27
ffmpeg -i INPUT -f mp4 -vcodec mpeg4 -ar 48000 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320×240 -aspect 4:3 -y OUTPUT

What I want to do is take a 75mb mov file and make it as small as possible. I did this

mencoder INPUT -oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vbitrate=500:acodec=aac -af lavcresample=24000 -vf scale=368:208,harddup -lavfopts format=psp:i_certify_that_my_video_stream_does_not_use_b_frames -ofps 30000/1001 -o OUTPUT

and got it to 8mb.

The second one still works, so you must be right about something missing.

I double clicked on the function and dont see a required field. Under the info button, I do see a see dependencies for your functions.  When I click, it says must use apt-get. Then it loads a terminal window and it seems to have them installed.

---

### Post by brus46 on 2008-01-27
ok i was thinking you were using the second version of the program (still unstable)

in that case probably ffmpeg isn't compiled with faac support, but if you get the second one work why tring using the other one which do exactly the same thing? :D

if you want absolutenly the first one work try doing this:
use convertit and try to convert some files, when it finished press see log
then in the log read the terminal output if nothing seems strange copy the command and past it into a terminal and look if the convertion works.

---

### Post by sdowney717 on 2008-01-27
Thanks for helping me with this. If it does the same thing that makes me happy. 
So  is getting it down to 8 mb from 75mb about as small as it can realistically go?

---

### Post by brus46 on 2008-01-27
i think yes... probably you can still work on the height and the width of the video but it's already very small...

---

### Post by philidox on 2008-02-25
This is perfect!  Thanx alot Creative, this is an awesome how to tutorial.  No issues installing or converting. Your the man:D

---

### Post by readyartbrut on 2008-02-27
Can I just echo philidox, this is absolutely perfect, clear installation instructions, converted 2 avis this morning to go onto my psp, where other applications promised and failed, this one worked a treat, thank you very much.

---

### Post by ccclay on 2008-02-27
Hi Brus46, nice to meet you. Creative2 has refered you to me. I dont know if it is right to discuss here otherwise you are welcome to : [http://ubuntuforums.org/showthread.php?p=4419234#post4419234](http://ubuntuforums.org/showthread.php?p=4419234#post4419234) . Thank you very much.

Below I copy my question. 

As a beginner yet, I am looking for the method of automated production starting from easy and simple to complicated job. I believe this will be a help to computer users. With this automated function, we can simply put a mutlimedia file into a folder then it will automatically process the file to our need, such as converting a flv to mpg, converting a wav to mp3, or, rendering a blend file to a 3D photo. Below is my idea using ubuntu to accomplish a simple conversion job.

1. Schedule with cron job at a specified time such as every 3 minutes
2. automatically run the script convertion.py
3. the script will load an conversion application
4. import a flv file from a folder
5. convert the file from flv to mpg
6. save the mpg file , delete the original fla file.

I have tried and know how to do steps from 1 to 3, but my weakness is I dont know how to do the steps from 4 to 5. Is it possible to do those 3 steps ? Has anyone done similar job and script ? Would you give me some guide ? What I want is to write the script with python. Thank you very much for your help !!

Hope Creative2 may see this ~~
( an idea : I just read the post by Creative2 and am deeply impressed for his great job --- ConvertIT--- and is it possible to use ConvertIT for above purpose ? )
_________

---

### Post by flowevd on 2008-02-28
great app...
thanks!

---

### Post by eyecolor on 2008-03-04
really great app...
thanks!

---

### Post by brus46 on 2008-03-09
> **ccclay said:**
> Hi Brus46, nice to meet you. Creative2 has refered you to me. I dont know if it is right to discuss here otherwise you are welcome to : [http://ubuntuforums.org/showthread.php?p=4419234#post4419234](http://ubuntuforums.org/showthread.php?p=4419234#post4419234) . Thank you very much.

Below I copy my question. 

As a beginner yet, I am looking for the method of automated production starting from easy and simple to complicated job. I believe this will be a help to computer users. With this automated function, we can simply put a mutlimedia file into a folder then it will automatically process the file to our need, such as converting a flv to mpg, converting a wav to mp3, or, rendering a blend file to a 3D photo. Below is my idea using ubuntu to accomplish a simple conversion job.

1. Schedule with cron job at a specified time such as every 3 minutes
2. automatically run the script convertion.py
3. the script will load an conversion application
4. import a flv file from a folder
5. convert the file from flv to mpg
6. save the mpg file , delete the original fla file.

I have tried and know how to do steps from 1 to 3, but my weakness is I dont know how to do the steps from 4 to 5. Is it possible to do those 3 steps ? Has anyone done similar job and script ? Would you give me some guide ? What I want is to write the script with python. Thank you very much for your help !!

Hope Creative2 may see this ~~
( an idea : I just read the post by Creative2 and am deeply impressed for his great job --- ConvertIT--- and is it possible to use ConvertIT for above purpose ? )
_________


everything is possible :D

if i had understand everything
the last part of your script should sound like this:

mencoder 'infile.flv'  -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000  -xvidencopts fixed_quant=4 -o 'outfile.avi'
#convert from flv to avi
rm 'infile.flv'
#delete original file

you can even put this function in convertit :D
mencoder '<input>'  -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000  -xvidencopts fixed_quant=4 -o '<output>' && rm '<input>'

AHH
little , big news!!
now i'm writing a site: [www.sciallo.net/ConvertIT2/ConvertIT-Functions/](www.sciallo.net/ConvertIT2/ConvertIT-Functions/)
(it's a beta DON'T USE IT)
With this site all convertit users could shere their functions with all other users.
The best functions will be read, translate and certified by some admins and will automatically update on every convertit! :D
As soon as it will start working well i'll tell you, i promise.

ps. sorry for my absence but i was under examination (i'had 6 exams in 2 months...)

bye

---

### Post by brus46 on 2008-03-09
[http://www.sciallo.net/ConvertIT2/](http://www.sciallo.net/ConvertIT2/)

every minute it became bigger :D

for the future i'm looking for some translators (and someone who understand and write better my english sentences :D )

bye

---

### Post by chek2fire on 2008-03-20
Great app!! thank you :)

---

### Post by corvax on 2008-04-01
Excellent work :)  has any one gotten the flash to work? i cant seem to on gutsy or hardy

---

### Post by AustinMatherne on 2008-04-08
Great application. This is something Ubuntu has needed for a very long time.

Would it be possible to build in some sort of update checker, that would see if there was a new version? It wouldn't even need to install the new version, just let the user know there's a new one out.

Anyway, thanks for the application.
~ Austin

---

### Post by brus46 on 2008-04-08
actually i found out another programmer and we're writing down some standard specifications.

Our ideas include a shell version of convertit.
why?
because in this way you can install convertit on a server and use it to make a great web service of convertion totally free ;)
(and my helper is writting a project on shells and terminals :p)

As soon as we've something i'll update the wiki translating even in english ;)

bye

---

### Post by ethanay on 2008-04-15
this looks like exactly the thing i have been searching for -- i will give it a try.

in the mean time, thanks so much for your work!

ethan

---

### Post by RJ Hythloday on 2008-04-23
I'm installing this in hopes of doing a backwards convert, I have downloaded mp4's that I need on a dvd for some one to watch on an old dvd player.

Fingers crossed

:popcorn:

---

### Post by rykel on 2008-04-28
> **brus46 said:**
> [http://www.sciallo.net/ConvertIT2/](http://www.sciallo.net/ConvertIT2/)

every minute it became bigger :D

for the future i'm looking for some translators (and someone who understand and write better my english sentences :D )

bye

Hi Brus,

I am not a programmer, but I am relatively good in my English.

If you could email me all your sentences in broken English in a text file (line by line), I can try to translate them for you.

I would love to contribute in my own way to open source, so thanks in advance for the privilege.   :)

---

### Post by brus46 on 2008-04-28
just tell me your e-mail :D

---

### Post by spacesearcher on 2008-04-29
Will the instillation instructions that are written for gusty work on hardy?

---

### Post by brus46 on 2008-04-30
don't know!

i'm still using gutsy because i'm not using my personal pc but another one (mine is in a Asus center somewhere in europe for being repaired...)

if you use the python version there shouldn't be any problems instead the gambas version probably must be recompiled with the new version of gambas...

in that case download the source, open it with gambas2 and launch the make package wizard... follow him and you'll have your personal deb for your pc ;)

---

### Post by Weevil on 2008-05-06
I've converted some MTS files to avi using m2tstoavi... now when I try to convert them to any format using ConvertIT the audio goes out of sync pretty soon. I have tested with Kino which can convert them to .dv files with sync audio/video and using Themonospot for information on the video/audio format I have tried different configuration options but they give the same result with all formats.

What am I doing wrong?

---

### Post by Weevil on 2008-05-07
Oops... my videofiles are in AVCHD/H264/AC3 format which seems to be a problem of it's own -- guess this is the wrong thread for that question!
Anyway whomever it may concern I've settled for [winff]("http://www.winff.org"), a GUI for ffmpeg, it handles audio&video fine but doesn't match the experimental HDTV divx quality of ConvertIT as far as I can see.

---

### Post by Nighto on 2008-06-12
Hi, I'd like to help by translating ConvertIT to portuguese, how can I do that?

[]

---

### Post by hoodedthefox on 2008-07-15
I just downloaded convertit and was working on conversions for psp. When I convert though my files dont show up. whats with that?

---

