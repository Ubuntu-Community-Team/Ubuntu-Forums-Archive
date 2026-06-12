---
title: "Fuoco Tools converter and more"
date: 2007-12-29
forum: Multimedia Production
---

### Post by Creative2 on 2007-12-29
[SIZE="6"][CENTER]**[COLOR="Blue"][B]Fuoco Tools**[/COLOR]
[/B][/CENTER][/SIZE]

[SIZE="5"][B] 
Video promo  [/B][/SIZE] [http://www.youtube.com/watch?v=YtFWdlphAs8](http://www.youtube.com/watch?v=YtFWdlphAs8) or  [http://www.youtube.com/watch?v=S75pGGAI1c8](http://www.youtube.com/watch?v=S75pGGAI1c8)
[B]
-for problems you can find more here : [http://fuocotools.byethost13.com/index.php?board=4.0](http://fuocotools.byethost13.com/index.php?board=4.0)[/B]

[SIZE="5"]  don't use [COLOR="DarkRed"]CONFIGURATOR[/COLOR] if you have medibuntun repo on..
.CONVERTER DVDWZARD AND IMAGES2MPG SHOULD WORK FINE!!![/SIZE]
[B]
screenshoot
[/B]

Converter tool 

[[IMG]http://www1.mediafire.com/imgbnc.php/149fa7c6d46486938ffa88c8d8cb62c83g.jpg[/img]](http://www.mediafire.com/imageview.php?quickkey=1eyjmd5znef&thumb=4)

[[IMG]http://www0.mediafire.com/imgbnc.php/0e98d811a89b5a00a385214146a332db3g.jpg[/img]](http://www.mediafire.com/imageview.php?quickkey=32xxtmyp0ib&thumb=4)


[[IMG]http://www2.mediafire.com/imgbnc.php/6ca8932a63c50bc6ad43310265f7b3bd3g.jpg[/img]](http://www.mediafire.com/imageview.php?quickkey=vbu4zb8mzt3&thumb=4)

[[IMG]http://www1.mediafire.com/imgbnc.php/38ac675b8a30c056f18ab45eea4336523g.jpg[/img]](http://www.mediafire.com/imageview.php?quickkey=5gr6ru7itpd&thumb=4)




[SIZE="3"]**What is Fuoco tools?**[/SIZE]

Fuoco tools is born from The same ideas of ConvertIT, so is mainly a converter,but i have added some features, like Dvdwizard and Images2mpg plug in. I thinked to Fuoco like a faster way to learn mencoder , ffmpeg and company (basic learning) 



[CENTER]
**[SIZE="5"]Editing function with interface [/SIZE]**[/CENTER]
You can edit , delete or ADD fuction with this interface how you can see here 



[CENTER][B][SIZE="3"]To load a fuctioon double click on the commandline 
[/SIZE][/B][/CENTER]


[[IMG]http://www2.mediafire.com/imgbnc.php/74c222c2105347a921c6ae842bbbde653g.jpg[/img]](http://www.mediafire.com/imageview.php?quickkey=reoxojn2dwj&thumb=4)



sometime it can happend commanline is not modified as you want, be carefull when you modify commandline with special characters if you have some problem you can edit one file as you can see below

[CENTER][SIZE="5"]**Editing function without interface**[/SIZE][/CENTER]

you can manage your function wiht a text editor with this 

```
nano $HOME/.fuoco/treestore.txt
```
Fuoco has a button to open your prefered text editoryou can choose 

 gedit or kate or nano (gnome or kde) 

a little example  :

```


YouTube?To DOWNLOAD?FLV to AVI Tag Download and convert!example avi conversion?youtube-dl INPUT -o 'OUTDIR/NUMBEROFTHEFILE.flv' ; mencoder 'OUTDIR/NUMBEROFTHEFILE.flv'  -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000  -xvidencopts fixed_quant=4 -o 'OUTDIR/NUMBEROFTHEFILE.avi'


```

?= is a separator so we have

YouTube= **cathegory**
TO DOWNLOAD =** subcathegory**
FLV to AVI =**kind of conversion**  
 Download and convert!example avi conversion  =**tag**
youtube-dl INPUT -o 'OUTDIR/NUMBEROFTHEFILE.flv' ; mencoder 'OUTDIR/NUMBEROFTHEFILE.flv'  -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000  -xvidencopts fixed_quant=4 -o 'OUTDIR/NUMBEROFTHEFILE.avi'= **commandline**



note the command line 
```

youtube-dl  etc etc ; mencoder etc etc 
```
if you put      [SIZE="5"]; [/SIZE]        that command wil be used for every file in your list fist youtube and then mencoder 
instead if i put 
```

youtube etc etc ENDLOOP  mencoder etc etc 
```

This will execute  youtube-dl for every files in your list AND THEN  only 1 time mencoder etc etc 



[CENTER]**[SIZE="6"]INSTALLATION[/SIZE]**[/CENTER]



If you have not medibuntu repo turned on you can use configurator (First loading and documentation)


[CENTER]
[SIZE="4"]--FIRST STEP ADD MEDIBUNTU REPO [/SIZE][/CENTER]




Below are the instructions to add the Medibuntu repository to your system's list of APT repositories. 
Add Medibuntu to your sources.list, as well as its GPG key to your keyring. Make sure to use the correct sources.list that corresponds to your current distribution. 

**Hardy 8.04**

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```


** Ubuntu 7.10 "Gutsy Gibbon":** ```

sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
```

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



[CENTER][SIZE="4"]--SECOND STEP, add the GPG Key  [/SIZE] [/CENTER]
 ```

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
```



[CENTER][SIZE="4"]--THIRD STEP INSTALL THESE "SHELL PROGRAMS"[/SIZE][/CENTER]



this command line installs maybe everythings that you need (NB THERE IS K3B)

```
sudo apt-get install ffmpeg2theora mencoder mplayer  libogg0 libogg-dev libvorbis0a libvorbis-dev vorbis-tools mp32ogg ffmpeg  imagemagick youtube-dl poppler-utils dvdauthor sox mjpegtools ffmpeg toolame gddrescue dvdbackup ccd2iso nrg2iso mdf2iso bchunk transcode k3b kipi-plugins kommander xterm 
```


[B]
youtube-dl issue[/B] i these days youtube has made something...so youtube-dl from ubuntu repo doesn't work anymore , if you are interested, here how fix youtube-dl 
[http://ubuntuforums.org/showthread.php?t=652843&page=5](http://ubuntuforums.org/showthread.php?t=652843&page=5)




i have installed all these programs and all works fine anyway :

ffmpeg2theora---------------------------------------------------------->ESSENTIAL
mencoder---------------------------------------------------------------> ESSENTIAL 
mplayer----------------------------------------------------------------->ESSENTIAL
libogg0 libogg-dev libvorbis0a libvorbis-dev vorbis-tools-------> ESSENTIAL
mp32ogg--------------------------------------------------------------->faster mp3 to ogg encoder 
ffmpeg ----------------------------------------------------------------->ESSENTIAL
imagemagick-----------------------------------------------------------> converter for  photo
youtubedl---------------------------------------------------------------> download youtube video 
poppler-utils------------------------------------------------------------>text converter 
dvdauthor sox mjpegtools ffmpeg toolame------------------------->to run dvdwizard 
 transcode-------------------------------------------------------------->ESSENTIAL (avimerge avisplit are in this pack)
gddrescue dvdbackup ccd2iso nrg2iso mdf2iso bchunk---------> with this you can make dvd back up and convert iso image (nero image etc etc ..)
kipi-plugins--------------------------------------------------------------> to run make a video from my picture, it gets you images2mpg package
kommander-------------------------------------------------------------->ESSENTIAL if you have not you can't use fuoco tools 
k3b----------------------------------------------------------------------->it needs fot dvdwizar and to create a dvd with divx but if you don't plane to use that command line you don't need to install it
xterm-------------------------------------------------------------------->ESSENTIAL ...i know it should be installed by default but i have put in list....
axel----------------------------------------------------------------------> download with serveral connections usefull to download fast 






[CENTER]
[B]
[SIZE="4"]-- FOURTH STEP dvdwizard  installation [/SIZE][/B][/CENTER]



you need also of this 

[http://www.debian-multimedia.org/pool/main/d/dvdwizard/dvdwizard_0.5-0.0_all.deb](http://www.debian-multimedia.org/pool/main/d/dvdwizard/dvdwizard_0.5-0.0_all.deb) 

to install just right button on the file and install it



[CENTER][B]
[SIZE="4"]-- FIVETH STEP  Interface's installation [/SIZE][/B][/CENTER]




you can CHOOSE AND download your version  and UNPACK this

**full version** version has converter and images2mpg and dvdwizard--->1.3  MB

**only converter** version has  converter            --------------------->340  KB 

latest version :

full 0.0.7e **[color=red]NEW![/color]** contains converter 1.0.0        (updated some things..)
[http://www.mediafire.com/?gpedy2oybki](http://www.mediafire.com/?gpedy2oybki)

only converter 1.0.0 **[color=red] NEW![/color]**
[http://www.mediafire.com/?1bqmmlxx9j4](http://www.mediafire.com/?1bqmmlxx9j4)

*debian package (still for 0.0.7c )
[http://fuocotools.byethost13.com/index.php?board=14.0](http://fuocotools.byethost13.com/index.php?board=14.0)






then open in a  terminal and go in your folder (where you have extracted Fuoco tar file) and  type :

```
sudo ./install.sh
 
```

if it doesn't work see if it  is  executable file or not.   if it's not set it ( right button on it---properties--permission--set as executable)

or if you are in that folder


to uninstall just 

```
sudo ./uninstall.sh

```

[SIZE="5"][B]
end [/B][/SIZE]









[SIZE="4"] 
[B]
 DVDWIZARD  [/B][/SIZE]

what can it make ?** [SIZE="3"]organized like title :[/SIZE]**

[IMG]http://dvdwizard.wershofen.net/images/stories/screenshots/Main_Menu_01.png[/IMG]

[B][SIZE="3"]
organized like chapter[/SIZE][/B]
[IMG]http://dvdwizard.wershofen.net/images/stories/screenshots/Chapter_Sel_01.png[/IMG]


Tutorial 

Insert what your movie in the list, you can put what you want mov avi wmv etc... , if you like you can create a video from your picture.., choose your music for Main menu, choose Titile, and Temp folder  (/tmp), the output folder 
then click on the Dvd picture.
it will start to encode, build the menu and then it starts k3b 
 
[I][B]Remember dvdwizard doesnt like name with space or special characters or something of strange(EVEN IF YOU QUOTE), so if you want use it rename the files to avoid failure.
[/B][/I]
[I]
other resource for dvdwizard [/I]

[http://dvdwizard.wershofen.net/index.php?option=com_frontpage&Itemid=1](http://dvdwizard.wershofen.net/index.php?option=com_frontpage&Itemid=1)
[SIZE="4"]
**IMAGES2MPG**[/SIZE]

why have you made this stuff? do you know digikam?

of course i know, but...this can work together with dvdwizard tool :) , if you push little button you can store commandline for dvdwizard....so you don't need to create before mpg from your photo e then load dvdwziard, just load dvdwizard create the slideshow and then close the last interface and go on with dvdwizard.

it's very simple ,  your can use "alone" and it done mpg from your picture with fade effects or you can use for dvdwizard, in that case it will not work after you have clicked on the button but it will store commandline and automatically it will be read from dvdwizard when you close IMAGES2MPG plug in.

NOTE 2 with very big photo for  preview...it can load a bit slower.. preview if you want see the picture faster juste resite for dvd (pal max = 720x540 ntsc max =)


[SIZE="5"]Useful documentation  [/SIZE]

ffmpeg :
[http://ffmpeg.mplayerhq.hu/faq.html](http://ffmpeg.mplayerhq.hu/faq.html)

mencoder

[http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#encoding-guide](http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#encoding-guide)

[SIZE="5"]**Usefull Stuff  ,**[/SIZE]

[SIZE="4"]flvget get video from any website[/SIZE]


[http://www.kde-apps.org/content/show.php/show.php?content=33973&vote=good&tan=45534228](http://www.kde-apps.org/content/show.php/show.php?content=33973&vote=good&tan=45534228)


[SIZE="4"]create a dvd  [/SIZE]

dvd authoring**_ only for kde....it has some problem with sox =( ._**..

[http://dvdauthorwizard.sourceforge.net/view.php/page/Install](http://dvdauthorwizard.sourceforge.net/view.php/page/Install) 

IF YOU HAVE PROBLEM TO DOWNLOAD

[http://www.mediafire.com/download.php?3c11x4xdt1y](http://www.mediafire.com/download.php?3c11x4xdt1y)

before encode your movie  into mpeg with fuoco tools







[SIZE="1"]old versions

[I]version 0.0.0.3 [http://www.mediafire.com/download.php?b4tzkdzxyhm](http://www.mediafire.com/download.php?b4tzkdzxyhm) fixed install.sh
version 0.0.4  [http://www.mediafire.com/?53ztmyg0bxy](http://www.mediafire.com/?53ztmyg0bxy)
version 0.0.4 [http://www.mediafire.com/?0otcnwbyyfz](http://www.mediafire.com/?0otcnwbyyfz)   it seems sometime mediafire is under maintenance

version 0.0.5
host 1
[http://www.mediafire.com/?fxtvy5cnyew](http://www.mediafire.com/?fxtvy5cnyew)
host 2
[url]http://www.freewebs.com/fuocotools/FuocoTools-0.0.5s.tar.gz[/url
[http://www.mediafire.com/?6oknlfzzwxl](http://www.mediafire.com/?6oknlfzzwxl)  Note : i found problems with dvdwizard....pal ntsc button doesn't work and other bugs , Converter is fine 
[http://www.mediafire.com/?bwjgwifj35w](http://www.mediafire.com/?bwjgwifj35w)    0.0.5c 
-0.0.7  (Full version)
[http://www.mediafire.com/?43yiyy25zzd](http://www.mediafire.com/?43yiyy25zzd)

-1.0.0a(only converter )
[http://www.mediafire.com/?5jybmifm9cd](http://www.mediafire.com/?5jybmifm9cd)
][/I][/SIZE]

only converter 1.0.0b
[http://www.mediafire.com/?5tkeybbw0mm](http://www.mediafire.com/?5tkeybbw0mm)
full 0.0.7d
[http://www.mediafire.com/?uepx4eujry4](http://www.mediafire.com/?uepx4eujry4)

---

### Post by oracle2b on 2007-12-29
are you finished now?...this looks good I'll try it tonight. will this work in GNOME? ...looks like a kde app

---

### Post by MepisReign on 2007-12-29
If you need a spanish translation or improve the english documentation for that, let me know, Congrats on doing something that useful!!

"Fuoco": means fire, fuego, right?

Best Regards, :popcorn:

MepisReign

---

### Post by Creative2 on 2007-12-30
mephis :

 yes fuego :), ok for the help  ,before i must finish the english documentation... 

oracle2b : 

yes i have just finished , i have kde in this computer but i have tested on gnome xD and it works, the only thing is not properly working, for now, is maximize the windows but you can resize..so  there is not problem

---

### Post by oracle2b on 2007-12-30
i don't understand where I'm suppose to get this install.sh file. i was able to do every thing but that last step. what do i have to do?
please help.

---

### Post by Creative2 on 2007-12-31
i must finish the documentation , be patient...

 I AM WRITING THIS PAGE.IT IS NOT COMPLETED DON'T USE !!!...

---

### Post by Creative2 on 2007-12-31
ok everyone can test now =)and 

[SIZE="5"][COLOR="Red"]happy new year!!![/COLOR][/SIZE]

---

### Post by kr0n1x on 2008-01-02
interesting application :)

---

### Post by GuySmily on 2008-01-02
Nevermind (I think)

---

### Post by Creative2 on 2008-01-03
for psp 


mencoder has chanded so... but i think you can use this :
```

mencoder INPUT -oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vbitrate=500:acodec=libfaac -af lavcresample=24000 -vf scale=368:208,harddup -lavfopts format=psp -ofps 30000/1001 -o OUTPUT

```
or

```
ffmpeg -i INPUT -acodec aac -ab 128kb -vcodec h264 -b 1200kb -ar 48000 -mbd 2 -coder 1 -cmp 2 -subcmp 2 -s 368x192 -r 30000/1001 -title TITLE -f psp -flags loop -trellis 2 -partitions parti4x4+parti8x8+partp4x4+partp8x8+partb8x8 OUTPUT

```__________________

---

### Post by ErwinC on 2008-01-04
As good as ConverIT but it looks better!
Nice program, I will test it.
Thanks

---

### Post by QwUo173Hy on 2008-01-05
I also can't get the file linked from step 5. I'm looking forward to trying it though.

---

### Post by Creative2 on 2008-01-05
mm strange let me know if you have still problem with downloaing

---

### Post by Creative2 on 2008-01-05
made installer better

---

### Post by QwUo173Hy on 2008-01-06
Now firefox offers me to download a file called 'download.php' or open it with a text editor. When I open with text editor, it's blank. Occasionally I get a new page open when clicking on the link that reports an error with the connection being reset by the site.

---

### Post by Creative2 on 2008-01-06
if you click on the file with right button  and select "save as" you can not save  file, or as you said you can save download.php..,and so it is not usable...

 just left button on the link ....it will open a new windows , mediafire windows  and in that page you will be able to download files tar...(i know maybe is not so easy if you don't know mediafire...but i chose because it's free and fast :)) )
[[IMG]http://www1.mediafire.com/imgbnc.php/2bb90dbbe56552390d7264c82391d0921g.jpg[/IMG]](http://www.mediafire.com/imageview.php?quickkey=2thswlxdeo3&thumb=4)

annyway i will upload somewhere else

---

### Post by QwUo173Hy on 2008-01-06
Still no luck. If I left click, it asks me to download 'download.php' and if I right click and choose 'Open in new window' it gives me a blank page with a dialog offering the same download.

---

### Post by Creative2 on 2008-01-06
well i suppose there is some problem with firefox, try to use opera or try do download from here

[http://www.sendspace.com/file/qdvrqm](http://www.sendspace.com/file/qdvrqm)

---

### Post by Creative2 on 2008-01-07
error in a commnadline....

this is right to add a new track in an avi movie.

mencoder INPUT -oac copy -ovc copy -audiofile 'INDIR/BASENAME.mp3'  -o OUTPUT

---

### Post by Creative2 on 2008-01-09
out 0.0.4

add text editor for command line 
fixed , i hope, psp commandline
fixed add new audio for avi files
added load default functions

---

### Post by Creative2 on 2008-01-10
-.-'' 005 out 
some bug fixed 
add some stuff (converter)

---

### Post by Odd-rationale on 2008-01-10
Wow! This looks great. Thanks a lot!

---

### Post by MepisReign on 2008-01-11
Is it possible to add subtitles on the fly?
If so, how can I add permanent subtitles from a .srt when converting an AVI to a NTSC mpg file?
Also is it possible make the subtitle to display with an specific color?

Best Regards

MepisReign

---

### Post by Creative2 on 2008-01-11
Hola,

1 if there is subtitle mencoder \ ffmpeg use it, if there is not they don't use it , EVEN IF YOU USE COMMANDLINE WITH SUBTITLE 


2unluckly i have used ffmpeg to build mpg for dvd so that it doesn't want  create a stream with subtitle 

3 mm i suggest to create a srt file with some sofware like jubbler (is in ubuntu) that can handle coluour of your subtitle...
this is theory



 for ffmpeg 
```

-newsubtitle SUBTILE
```
 (for mencoder)
```
-sub SUBTITLE -subfont-text-scale 4 
```

I REMEMBER ONLY SRT FILE CAN BE USED....IF YOU WANT TRY TO FORCE MENCODER TO ACEPT OTHER SUBTITLE FILE YOU COULD TRY THIS

```
-sub 'INDIR/BASENAME.yourextenision' -subfont-text-scale 4 
```

this is ONLY AN example....

```
-sub 'INDIR/BASENAME.cucu' -subfont-text-scale 4 
```

you can choose your prefered Subtitle size ( in these examples i write 4 but you can use what you want )


so if you are intersted to create a mpg with subtitle is better for you use mencoder 
[I][B]
PAL[/B][/I] ```


mencoder INPUT -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd:tsaf   -sub SUBTITLE -subfont-text-scale 4 -vf scale=720:576,harddup -srate 48000 -af lavcresample=48000  -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=500:keyint=15:vstrict=0:acodec=ac3:abitrate=192:aspect=16/9 -ofps 25  -o OUTPUT
```


[B][I]
NTSC[/I][/B]

```


mencoder INPUT -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd:tsaf  -sub SUBTITLE -subfont-text-scale 4  -vf scale=720:480,harddup -srate 48000 -af lavcresample=48000   -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=18:vstrict=0:acodec=ac3:abitrate=192:aspect=16/9 -ofps 30000/1001  -o OUTPUT 

 
```

---

### Post by placebo0815 on 2008-01-11
Hi Creative2,

first of all thank you for the app and I think you are so active in the development - highly appreciated.

Do you see a chance to add support for converting .pdf to .doc and .xls? I would be very glad about this.

Thank you and keep up the good work.

Chris

---

### Post by Creative2 on 2008-01-11
if exist command line program you can use with Fuocot tools ....
sorry :) i have no time i will see when i get a bit

---

### Post by MepisReign on 2008-01-11
Thank you for your quick response! :)
I will give mencoder a try

Ciao

MepisReign

---

### Post by Creative2 on 2008-01-13
In the lastest version you should find 

youtube to mp3
youtube to ogg
youtube to flv

this download, extract audio track and encode into these formats.....

mm maybe i forget to add FLV encoding 
```

Video?TO FLV?ANY to flv Tag Flv_LOW quality ?ffmpeg -i INPUT -b 200k -r 30 -ab 128k -ar 22050 -y OUTPUT
Video?TO FLV?ANY to flv Tag Flv_MEDIUM quality ?ffmpeg -i INPUT -b 500k -r 30 -ab 192k -ar 22050 -y OUTPUT
Video?TO FLV?ANY to flv Tag Flv_HIGH quality ?ffmpeg -i INPUT -b 700k -r 30 -ab 256k -ar 44100 -y OUTPUT
Video?TO FLV?ANY to flv Tag Flv_SAME quality ?ffmpeg -i INPUT-sameq -ar 44100 -y OUTPUT
```

---

### Post by finding_my_zen on 2008-01-16
For some reason it won't convert videos to wmv, help! I'm kind of a noob.
:confused:

---

### Post by Creative2 on 2008-01-16
ok :)
HOW CAN I DO A LOG 

1 go in extra and option.....

2set checked         "Show the command line etc etc "

3now when it has finished to convert it will show you the command line,

4copy that command line (you can select with mouse-------- and right buttton.....copy)

5paste in a terminal and see what it say....typically .:

```
m -xy 720 -lavcopts vcodec=wmv2:acodec=wmav2 -o '/home/Sbucatone/Desktop/dsci004
1.wmv' '/media/sda7/a/Video/Videoconvertiti/dsci0041.MPEG'
MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: Genuine Intel(R) CPU           T2060  @ 1.60GHz (Family: 6, Model: 14, Step
ping: 12)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.
success: format: 0  data: 0x0 - 0x807800
MPEG-PS file format detected.
VIDEO:  MPEG2  640x480  (aspect 1)  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:640x480  fps:25.00  ftime:=0.0400
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 64.0 kbit/4.17% (ratio: 8000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [scale]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 640 x 480 (preferred colorspace: Mpeg PES)
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
SwScaler: reducing / aligning filtersize 5 -> 4
SwScaler: reducing / aligning filtersize 5 -> 4
SwScaler: reducing / aligning filtersize 5 -> 4
SwScaler: reducing / aligning filtersize 5 -> 4
[swscaler @ 0x8800710]SwScaler: BICUBIC scaler, from yuv420p to yuv420p using MM
X2
[swscaler @ 0x8800710]SwScaler: using 4-tap MMX scaler for horizontal luminance
scaling
[swscaler @ 0x8800710]SwScaler: using 4-tap MMX scaler for horizontal chrominanc
e scaling
[swscaler @ 0x8800710]SwScaler: using n-tap MMX scaler for vertical scaling (YV1
2 like)
[swscaler @ 0x8800710]SwScaler: 640x480 -> 720x540
videocodec: libavcodec (720x540 fourcc=32564d57 [WMV2])
Writing header...2f ( 1%)  0.00fps Trem:   0min   0mb  A-V:-0.004 [0:0]
ODML: Aspect information not (yet?) available or unspecified, not writing vprp h
eader.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp h
eader.

1 duplicate frame(s)!
Pos:   6.3s    159f ( 9%) 36.82fps Trem:   0min  10mb  A-V:-0.039 [1154:223]
Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp h
eader.

Video stream: 1154.052 kbit/s  (144256 B/s)  size: 911701 bytes  6.320 secs  159                                                                                                    frames

Audio stream:  224.000 kbit/s  (27999 B/s)  size: 189846 bytes  6.780 secs
Sbucatone@ll:~$


```

then write here the message

---

### Post by Creative2 on 2008-01-16
beta out
bug found...ask commanline even if is selected...i will fix

added automatic log
[http://www.mediafire.com/?6oknlfzzwxl](http://www.mediafire.com/?6oknlfzzwxl)

---

### Post by Creative2 on 2008-01-17
several bugs in dvdwizard... fixing

---

### Post by Creative2 on 2008-01-19
dvdwizard GUI fixed 

[http://www.mediafire.com/?bwjgwifj35w](http://www.mediafire.com/?bwjgwifj35w)

NB

if you put too much title i think about 15 it doesnt' work well

if you have much more 15 file use organize like chapter

---

### Post by Creative2 on 2008-01-21
a little error in my function 

youtube upload...

```
YouTube?To UPLOAD?ANY to flv Tag Encode for youtube videos?ffmpeg -i INPUT -b 500k -r 30 -ab 128k -ar 44100 -s 320x240 -ac 2 -y OUTPUT
```

---

### Post by Creative2 on 2008-01-23
this is my last function file :

```
Audio?TO WAV?ANY to wav Tag uncompressed ?mplayer -ao pcm:file=OUTPUT  INPUT
Video?TO OGG?ANY to ogg Tag Ogg MEDIUM quality and resized 640 for 480?ffmpeg2theora -v 5 -a 5 -x 640 -y 480  INPUT -o OUTPUT
Video?TO OGG?ANY to ogg Tag Ogg MEDIUM quality and resized 720 for 576?ffmpeg2theora -v 5 -a 5 -x 720 -y 576  INPUT -o OUTPUT
Video?TO AVI?ANY to avi Tag Resize 720 pixel MEDIUM quality ?mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000 -vf scale -zoom -xy 720 -xvidencopts fixed_quant=5 -o OUTPUT
Video?TO AVI?ANY to avi Tag Resize 720 pixel HIGH quality ?mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=256 -srate 48000 -vf scale -zoom -xy 720 -xvidencopts fixed_quant=3 -o OUTPUT
Video?TO AVI?ANY to avi Tag Resize 720 pixel LOW quality ?mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=128 -srate 48000 -vf scale -zoom -xy 720 -xvidencopts fixed_quant=10 -o OUTPUT
Video?TO AVI?ANY to avi Tag Resize 640 pixel HIGH quality ?mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=256 -srate 48000 -vf scale -zoom -xy 640 -xvidencopts fixed_quant=3 -o OUTPUT
Video?TO AVI?ANY to avi Tag Resize 640 pixel MEDIUM quality ?mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000 -vf scale -zoom -xy 640 -xvidencopts fixed_quant=5 -o OUTPUT
Video?TO AVI?ANY to avi Tag Resize 640 pixel LOW quality ?mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=128 -srate 48000 -vf scale -zoom -xy 640 -xvidencopts fixed_quant=10 -o OUTPUT
Video?TO AVI?ANY to avi Tag Resize 320 pixel HIGH quality ?mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=256 -srate 48000 -vf scale -zoom -xy 320 -xvidencopts fixed_quant=3 -o OUTPUT
Video?TO AVI?ANY to avi Tag Resize 320 pixel MEDIUM quality ?mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000 -vf scale -zoom -xy 320 -xvidencopts fixed_quant=5 -o OUTPUT
Video?TO AVI?ANY to avi Tag Resize 320 pixel LOW quality ?mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=128 -srate 48000 -vf scale -zoom -xy 320 -xvidencopts fixed_quant=10 -o OUTPUT
Video?TO MPEG?ANY to mpeg Tag Resize 640 pixel MEDIUM quality ?ffmpeg -i INPUT -r 25 -f mpeg -vcodec mpeg2video -ar 48000 -b 700k -acodec mp3 -ab 192k -s 640x480 -y OUTPUT
Video?TO MPEG?ANY to mpeg Tag Resize 640 pixel HIGH quality ?ffmpeg -i INPUT -r 25 -f mpeg -vcodec mpeg2video -ar 48000 -b 900k -acodec mp3 -ab 256k -s 640x480 -y OUTPUT
Video?TO MPEG?ANY to mpeg Tag Resize 640 pixel LOW quality ?ffmpeg -i INPUT -r 25 -f mpeg -vcodec mpeg2video -ar 48000 -b 500k -acodec mp3 -ab 128k -s 640x480 -y OUTPUT
Video?TO MPEG?ANY to mpeg Tag Resize 720 pixel MEDIUM quality ?ffmpeg -i INPUT -r 25 -f mpeg -vcodec mpeg2video -ar 48000 -b 700k -acodec mp3 -ab 192k -s 720x540 -y OUTPUT
Video?TO MPEG?ANY to mpeg Tag Resize 720 pixel HIGH quality ?ffmpeg -i INPUT -r 25 -f mpeg -vcodec mpeg2video -ar 48000 -b 900k -acodec mp3 -ab 256k -s 720x540 -y OUTPUT
Video?TO MPEG?ANY to mpeg Tag Resize 720 pixel LOW quality ?ffmpeg -i INPUT -r 25 -f mpeg -vcodec mpeg2video -ar 48000 -b 500k -acodec mp3 -ab 128k -s 720x540 -y OUTPUT
Video?TO MPEG?ANY to mpeg Tag Resize 320 pixel MEDIUM quality ?ffmpeg -i INPUT -r 25 -f mpeg -vcodec mpeg2video -ar 48000 -b 700k -acodec mp3 -ab 192k -s 320x240 -y OUTPUT
Video?TO MPEG?ANY to mpeg Tag Resize 320 pixel HIGH quality ?ffmpeg -i INPUT -r 25 -f mpeg -vcodec mpeg2video -ar 48000 -b 900k -acodec mp3 -ab 256k -s 320x240 -y OUTPUT
Video?TO MPEG?ANY to mpeg Tag Resize 320 pixel LOW quality ?ffmpeg -i INPUT -r 25 -f mpeg -vcodec mpeg2video -ar 48000 -b 500k -acodec mp3 -ab 128k -s 320x240 -y OUTPUT
Video?TO AVI?RM to avi Tag Normal?mencoder INPUT -ofps 25 -ovc lavc -lavcopts vcodec=mpeg4 -oac mp3lame -lameopts abr:br=128 -srate 48000 -o OUTPUT
Video?TO MP4?ANY to mp4 Tag MEDIUM quality?ffmpeg -i INPUT -r 25 -f mp4 -vcodec mpeg4 -ar 48000 -b 700k -acodec aac -ab 192k -y OUTPUT
Video?TO MP4?ANY to mp4 Tag HIGH quality?ffmpeg -i INPUT -r 25 -f mp4 -vcodec mpeg4 -ar 48000 -b 900k -acodec aac -ab 256k -y OUTPUT
Video?TO MP4?ANY to mp4 Tag lOW quality?ffmpeg -i INPUT -r 25 -f mp4 -vcodec mpeg4 -ar 48000 -b 500k -acodec aac -ab 128k -y OUTPUT
Video?TO MOV?ANY to mov Tag Mov works in windows! MEDIUM quality?ffmpeg -i INPUT -r 25 -f mov -vcodec mpeg4 -ar 22050 -b 700k -acodec aac -ab 128k -y OUTPUT
Video?TO MOV?ANY to mov Tag Mov works in windows! HIGH quality try to resize if doesnt work with -s 640x480?ffmpeg -i INPUT -r 25 -f mov -vcodec mpeg4 -ar 22050 -b 900k -acodec aac -ab 256k -y OUTPUT
Video?TO MOV?ANY to mov Tag Mov works in windows! LOW quality?ffmpeg -i INPUT -r 25 -f mov -vcodec mpeg4 -ar 22050 -b 400k -acodec aac -ab 128k -y OUTPUT
Video?TO WMV?ANY to wmv Tag Simple wmv encoder but still wmv2 and wmav2 ?mencoder -oac lavc -lameopts abr:br=128 -ovc lavc -vf scale -zoom -xy 720 -lavcopts vcodec=wmv2:acodec=wmav2 -o OUTPUT INPUT
Video Filter?TO AVI?ANY to AVI Tag Rotate 2?mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=128 -srate 48000 -vf scale -zoom -xy 640 -xvidencopts bitrate=700 -vf rotate=2 -o OUTPUT
Foto ?TO BMP?ANY to bmp Tag Only conversion!?convert  INPUT  OUTPUT
Foto ?TO JPEG?ANY to jpeg Tag Only conversion?convert  INPUT  OUTPUT
Foto ?TO PNG?ANY to png Tag Only conversion?convert  INPUT  OUTPUT
Foto ?TO BMP?ANY to bmp Tag Convert and Resize 800x600?convert  -resize 800x600  INPUT  OUTPUT
Foto ?TO JPEG?ANY to jpeg Tag Convert and Resize 800x600?convert  -resize 800x600  INPUT  OUTPUT
Foto ?TO PNG?ANY to png Tag Convert and Resize 800x600?convert  -resize 800x600  INPUT  OUTPUT  
Video?TO AVI?RMVB to avi Tag Avi encoding medium quality?mencoder INPUT -ofps 25 -oac mp3lame -lameopts preset=64 -ovc xvid -xvidencopts bitrate=600 -of AVI -o OUTPUT
Phone?TO MOTOROLA V3I?ANY to 3GP Tag Motorola v3i ?ffmpeg -i INPUT -s qcif -vcodec mpeg4 -acodec aac -ac 2 -ar 48000 -r 25 -ab 128 -y OUTPUT
Phone?TO NOKIA N800?ANY to mp4 Tag  maybe works?ffmpeg -i INPUT -s 400x240  -vcodec mpeg4 -acodec aac -ac 2 -ar 48000 -r 25 -ab 128k -y OUTPUT
Phone?TO MOTOROLA V3X?ANY to mp4 Tag Motorola v3x ?ffmpeg -i INPUT -s 240x320  -vcodec mpeg4 -acodec aac -ac 2 -ar 48000 -r 25 -ab 128k -y OUTPUT
Phone?TO IPHONE?ANY to mp4 Tag  maybe works, 640x480 160kbr?ffmpeg -i INPUT -s  640x480  -vcodec mpeg4 -acodec aac -ac 2 -ar 48000 -r 30 -ab 160 -y OUTPUT
Iso image?TO ISO ?NRG to iso Tag iso converter ?nrg2iso INPUT  OUTPUT
Iso image?TO ISO ?BIN CUE to iso Tag iso converter ?bchunk PUTINALINE OUTPUT
Portable Device?TO wii?ANY to avi Tag for Wii encoding with ffmpeg ?ffmpeg -i INPUT -r 25  -vcodec mjpeg  -b 300k -acodec pcm_u8  -s 640x480 -y OUTPUT
Portable Device?TO Video ipod?ANY to mp4 Tag Ipod Video?ffmpeg -i INPUT -f mp4 -vcodec mpeg4 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192k -s 320x240 -aspect 4:3 OUTPUT
Portable Device?TO PSP?ANY to mp4 Tag Psp MENCODER?mencoder INPUT -oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vbitrate=500:acodec=libfaac -af lavcresample=24000 -vf scale=368:208,harddup -lavfopts format=psp -ofps 30000/1001 -o OUTPUT
Portable Device?TO PSP?ANY to mp4 Tag Psp FFMPEG?ffmpeg -i INPUT -acodec aac -ab 128kb -vcodec h264 -b 1200kb -ar 48000 -mbd 2 -coder 1 -cmp 2 -subcmp 2 -s 368x192 -r 30000/1001 -title TITLE -f psp -flags loop -trellis 2 -partitions parti4x4+parti8x8+partp4x4+partp8x8+partb8x8 OUTPUT
Phone?TO MP4?ANY to mp4 Tag 176x144 h264 general testing?ffmpeg -i INPUT -s 176x144 -vcodec h264  -ar 48000 -ac 2 -acodec aac -r 25 OUTPUT
eXtRa?TO AVI ?AVI to AVI Tag Increase volume  value 400?ffmpeg -i INPUT -vcodec copy -acodec mp3 -ab 128k -vol 400 -y OUTPUT
eXtRa?TO AVI ?AVI to AVI Tag Increase volume 0=mute nice=400 mad=1000?ffmpeg -i INPUT -vcodec copy -acodec mp3 -ab 128k -vol 400 -y OUTPUT
eXtRa?TO AVI ?AVI to AVI Tag Resyncronizing?mencoder INPUT -ovc copy -oac copy -forceidx -o OUTPUT
eXtRa?TO AVI ?AVI to AVI Tag Split avi every 700 MB?avisplit -s 700  -i INPUT
eXtRa?TO AVI ?AVI to AVI Tag Select and save only a part of the file !!remember , double click on the command line to set the time range?mencoder INPUT -ovc copy -oac copy -ss  hh:mm:ss.ms  -endpos hh:mm:ss.ms  -o 'OUTDIR/BASENAME.avi'
eXtRa?TO EXTRACT?ANY to ac3 Tag Extract Audio from my movie?ffmpeg -i INPUT  -vn -acodec ac3 -ab 128k -y OUTPUT
eXtRa?TO EXTRACT?ANY to mp3 Tag Extract Audio from my movie?ffmpeg -i INPUT  -vn -acodec mp3 -ab 128k -y OUTPUT
eXtRa?TO EXTRACT?ANY to flac Tag Extract Audio from my movie?ffmpeg -i INPUT  -vn -acodec flac -ab 128k -y OUTPUT
eXtRa?TO EXTRACT?ANY to ogg Tag Extract Audio from my movie?ffmpeg -i INPUT  -vn -acodec vorbis -ab 128k -y OUTPUT
eXtRa?TO NEW TRACK FOR MY AVI?AVI to avi Tag New audio for my avi the name of the audio file must be the same of the video?mencoder INPUT -oac copy -ovc copy -audiofile 'INDIR/BASENAME.mp3'  -o OUTPUT
eXtRa?TO EXTRACT?AVI to avi Tag Extract Only the video from my movie this is an example for avi but you can edit command line and replace your prefered format?ffmpeg -i INPUT  -an -vcodec copy -y  OUTPUT
eXtRa?TO DELAY?ANY to avi Tag Example Delay audio 5 seconds you can change the value just double click in the command line ?mencoder -oac copy -ovc copy -audio-delay 05.000  INPUT -o OUTPUT
eXtRa?TO KINO ?ANY to dv Tag PAL KINO?ffmpeg -i INPUT -target pal-dv  OUTPUT
eXtRa?TO KINO ?ANY to dv Tag NTSC KINO?ffmpeg -i INPUT -target ntsc-dv  OUTPUT
eXtRa?TO INSTALL FUOCO PACKAGE?ANY to ANY Tag ONLY UBUNTU, remember turn on medibuntu repo ?xterm -e sudo apt-get install ffmpeg2theora mencoder  mplayer  w32codecs libogg0  libogg-dev  libvorbis0a  libvorbis-dev  vorbis-tools  mp32ogg ffmpeg  imagemagick  youtube-dl poppler-utils transcode  gddrescue dvdbackup ccd2iso nrg2iso mdf2iso bchunk alien
eXtRa?TO DVDBACKUP?ANY to ANY Tag back up my dvd! whole features?dvdbackup -M -i /dev/dvd -o 'OUTDIR'
eXtRa?TO DVDBACKUP?ANY to ANY Tag back up my dvd! Main features?dvdbackup -F -i /dev/dvd -o 'OUTDIR'
Video Filter?TO AVI?ANY to AVI Tag Rotate 1 ?mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=128 -srate 48000 -vf scale -zoom -xy 640 -xvidencopts bitrate=700 -vf rotate=1 -o OUTPUT
Video Filter?TO AVI?ANY to AVI Tag Negative?mencoder INPUT -ofps 25 -ovc xvid -xvidencopts bitrate=700 -oac mp3lame -lameopts abr:br=128 -srate 48000 -vf eq2=1:-1:0:1:1:1:1 -o OUTPUT
Video Filter?TO AVI?ANY to AVI Tag Red passion ?mencoder INPUT -ofps 25 -ovc xvid -xvidencopts bitrate=700 -oac mp3lame -lameopts abr:br=128 -srate 48000 -vf eq2=1:1:0:1:7:1:1 -o OUTPUT
Video Filter?TO AVI?ANY to AVI Tag More saturation?mencoder INPUT -ofps 25 -ovc xvid -xvidencopts bitrate=700 -oac mp3lame -lameopts abr:br=128 -srate 48000 -vf eq2=1:1:0:3:1:1:1 -o OUTPUT
Video Filter?TO AVI?ANY to AVI Tag More Contrast?mencoder INPUT -ofps 25 -ovc xvid -xvidencopts bitrate=700 -oac mp3lame -lameopts abr:br=128 -srate 48000 -vf eq2=1:2 -o OUTPUT
Video Filter?TO AVI?ANY to AVI Tag More Brightness?mencoder INPUT -ofps 25 -ovc xvid -xvidencopts bitrate=700 -oac mp3lame -lameopts abr:br=128 -srate 48000 -vf eq2=1:1:0:1:1:1:1 -o OUTPUT
Video Filter?TO AVI?ANY to AVI Tag More Gamma?mencoder INPUT -ofps 25 -ovc xvid -xvidencopts bitrate=700 -oac mp3lame -lameopts abr:br=128 -srate 48000 -vf eq2=3:1:0:1:1:1:1 -o OUTPUT
Video Filter?TO AVI?ANY to AVI Tag Flip ?mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=128 -srate 48000 -xvidencopts bitrate=700 -vf flip -o OUTPUT
Video Filter?TO AVI?ANY to AVI Tag Scale 640:480 aspect  not fixed?mencoder INPUT -ofps 25 -ovc xvid -oac copy  -vf scale=640:480 -xvidencopts bitrate=700  -o OUTPUT
Video Filter?TO AVI?ANY to AVI Tag Scale 640 aspect ratio fixed ?mencoder INPUT -ofps 25 -ovc xvid -oac copy  -vf scale -zoom -xy 640 -xvidencopts bitrate=700  -o OUTPUT
Video Filter?TO AVI?ANY to AVI Tag Flip and 640 resize 3?mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=128 -srate 48000 -vf scale -zoom -xy 640 -xvidencopts bitrate=700 -vf flip -o OUTPUT
Text?TO HTML?PDF to html Tag Convert your pdf into html layout saved?pdftotext -layout -htmlmeta INPUT OUTPUT
Text?TO HTML?PDF to html Tag Convert your pdf into html ?pdftotext -htmlmeta INPUT OUTPUT
Text?TO TXT?PDF to txt Tag Convert your pdf into txt layer saved?pdftotext -layout INPUT OUTPUT
Text?TO TXT?PDF to txt Tag Convert your pdf into txt?pdftotext INPUT OUTPUT
Text?TO PS?PDF to ps Tag Convert your pdf into ps?pdf2ps INPUT OUTPUT
Text?TO PDF?PS to pdf Tag Convert your  ps file into pdf?ps2pdf INPUT OUTPUT
Text?TO PS?DVI to ps Tag Convert your latex file into ps?divps -o OUTPUT INPUT
Tutorial?TO K3B?all to all Tag See how you can add k3b At your command line?commadlineforconversion ENDLOOP k3b --audiocd 'OUTDIR'
Tutorial?TO double coinversion?all to all Tag usefull when you have problem or cannot find out how convert your file see audio ogg encoding?commandoutput=TEMP.wav  commandinput=INPUT  ; command TEMP.wav  -o OUTPUT ; rm TEMP.wav
Audio Filter?TO effects?ANY to wav Tag Echo?mplayer -ao pcm:file=TEMP.wav INPUT ; sox  TEMP.wav   OUTPUT echo 0.7 06 50 0.2  ; rm TEMP.wav
Audio Filter?TO effects?ANY to wav Tag Chorus?mplayer -ao pcm:file=TEMP.wav INPUT ; sox  TEMP.wav   OUTPUT  chorus 0.6 0.9 50.0 0.4 0.25 2.0 -t 60.0 0.32 0.4 1.3 -s  ; rm TEMP.wav
Audio Filter?TO effects?ANY to wav Tag Fade 5 seconds?mplayer -ao pcm:file=TEMP.wav INPUT ; sox  TEMP.wav   OUTPUT  fade 5  ; rm TEMP.wav
Phone?TO NOKIA N73?ANY to mp4 Tag 400 kbitrate?ffmpeg -i INPUT -s 320x240  -vcodec mpeg4 -acodec aac -ac 2 -ar 48000 -r 25 -ab 128k -b 400k -y OUTPUT
YouTube?To DOWNLOAD?FLV to flv Tag Download youtube videos?youtube-dl INPUT -o 'OUTDIR/NUMBEROFTHEFILE.flv'
YouTube?To DOWNLOAD AND CONVERT?FLV to AVI Tag Download and convert!example avi conversion?youtube-dl INPUT -o 'OUTDIR/NUMBEROFTHEFILE.flv' ; mencoder 'OUTDIR/NUMBEROFTHEFILE.flv'  -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000  -xvidencopts fixed_quant=4 -o 'OUTDIR/NUMBEROFTHEFILE.avi'
YouTube?To DOWNLOAD AND CONVERT?FLV to OGG Tag Download extract audio file and convert in ogg?youtube-dl INPUT -o 'OUTDIR/NUMBEROFTHEFILE.flv' ; ffmpeg -i  'OUTDIR/NUMBEROFTHEFILE.flv' -vn -acodec vorbis -ac 2 -ab 128k -y   'OUTDIR/NUMBEROFTHEFILE.ogg' 
YouTube?To DOWNLOAD AND CONVERT?FLV to MP3 Tag Download extract audio file and convert in mp3?youtube-dl INPUT -o 'OUTDIR/NUMBEROFTHEFILE.flv' ; ffmpeg -i  'OUTDIR/NUMBEROFTHEFILE.flv' -vn -acodec mp3 -ac 2 -ab 128k -y   'OUTDIR/NUMBEROFTHEFILE.mp3' 
YouTube?To DOWNLOAD AND CONVERT?FLV to FLAC Tag Download extract audio file and convert in flac?youtube-dl INPUT -o 'OUTDIR/NUMBEROFTHEFILE.flv' ; ffmpeg -i  'OUTDIR/NUMBEROFTHEFILE.flv' -vn -acodec copy -y   'OUTDIR/NUMBEROFTHEFILE.flac'
eXtRa?TO NEW TRACK FOR MY AVI?AVI to avi Tag New audio for my avi the name of the audio file must be the same of the video?mencoder INPUT -oac copy -ovc copy -audiofile 'INDIR/BASENAME.mp3'  -o OUTPUT
Audio?TO AC3?ANY to ac3 Tag Insane?ffmpeg -i INPUT -ab 384k -acodec aac -y OUTPUT
Audio?TO AC3?ANY to ac3 Tag Increase VOLUME value 400 bitrate 192k?ffmpeg -i INPUT -acodec aac -ab 192k -vol 400 -y OUTPUT
Audio?TO AC3?ANY to ac3 Tag LOW quality?ffmpeg -i INPUT -ab 128k -acodec aac -y OUTPUT
Audio?TO AC3?ANY to ac3 Tag MEDIUM quality?ffmpeg -i INPUT -ab 192k -acodec aac -y OUTPUT
Audio?TO AC3?ANY to ac3 Tag SAME quality?ffmpeg -i INPUT -sameq -acodec aac -y OUTPUT
Audio?TO FLAC?ANY to flac Tag Flac encoding it convert you can add -ab 192k if you want set bitrate?ffmpeg -i INPUT -acodec flac OUTPUT
Audio?TO FLAC?ANY to flac Tag Flac HIGH quality?ffmpeg -i INPUT -acodec flac -ab 256k -y OUTPUT
Audio?TO FLAC?ANY to flac Tag Flac LOW?ffmpeg -i INPUT -acodec flac -ab 128k -y OUTPUT
Audio?TO FLAC?ANY to flac Tag Flac MEDIUM?ffmpeg -i INPUT -acodec flac -ab 192k -y OUTPUT
Audio?TO FLAC?WMA to flac Tag Flac encoding for wma file?mplayer -ao pcm:file=TEMP.wav INPUT; ffmpeg -i TEMP.wav -f flac OUTPUT; rm TEMP.wav
Audio?TO MP3?ANY to mp3 Tag HIGH quality?ffmpeg -i INPUT -ab 256k -acodec mp3 -y OUTPUT
Audio?TO MP3?ANY to mp3 Tag Increase VOLUME value 300 bitrate 192k?ffmpeg -i INPUT -acodec mp3 -ab 192k -vol 300 -y OUTPUT
Audio?TO MP3?ANY to mp3 Tag INSANE quality?ffmpeg -i INPUT -ab 384k -acodec mp3 -y OUTPUT
Audio?TO MP3?ANY to mp3 Tag LOW quality?ffmpeg -i INPUT -ab 128k -acodec mp3 -y OUTPUT
Audio?TO MP3?ANY to mp3 Tag MEDIUM quality?ffmpeg -i INPUT -ab 192k -acodec mp3-y  OUTPUT
Audio?TO MP3?ANY to mp3 Tag SAME quality?ffmpeg -i -sameq INPUT -acodec mp3 -y OUTPUT
Audio?TO OGG?ANY to ogg Tag HIGH quality?mplayer -ao pcm:file=TEMP.wav INPUT ; oggenc -q 10 TEMP.wav  -o OUTPUT ; rm TEMP.wav
Audio?TO OGG?ANY to ogg Tag LOW quality?mplayer -ao pcm:file=TEMP.wav INPUT ;oggenc -q 2 TEMP.wav -o OUTPUT ; rm TEMP.wav
Audio?TO OGG?ANY to ogg Tag MEDIUM quality?mplayer -ao pcm:file=TEMP.wav INPUT ; oggenc -q 5 TEMP.wav -o OUTPUT ; rm TEMP.wav
Creative Command Line?TO DivX and burn a DVD with k3b?ANY to avi Tag  Encode DivX For NTSC tv and Burn them with k3b?mencoder INPUT -ofps 30 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000  -vf scale -zoom -xy 720 -xvidencopts fixed_quant=4 -o OUTPUT ENDLOOP k3b --datadvd 'OUTDIR'
Creative Command Line?TO DivX and burn a DVD with k3b?ANY to avi Tag Encode DivX For PAL tv and  Burn them with?mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000  -vf scale -zoom -xy 720 -xvidencopts fixed_quant=4 -o OUTPUT ENDLOOP k3b --datadvd 'OUTDIR'
DivXPlayer Compatible?TO AVI?ANY to avi Tag HDTV?mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=256 -srate 48000  -vf scale -zoom -xy 720 -xvidencopts bitrate=4000  -o OUTPUT
DivXPlayer Compatible?TO AVI?ANY to avi Tag HDTV with SUBTITLE?mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=256 -srate 48000 -vf scale -zoom -xy 720 -xvidencopts bitrate=4000 -sub SUBTITLE -subfont-text-scale 4 -o OUTPUT
DivXPlayer Compatible?TO AVI?ANY to avi Tag NTSC?mencoder INPUT -ofps 30 -ovc xvid -oac mp3lame -lameopts abr:br=128 -srate 48000 -vf scale -zoom -xy 720  -xvidencopts fixed_quant=4  -o OUTPUT
DivXPlayer Compatible?TO AVI?ANY to avi Tag NTSC with SUBTITLE?mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=128 -srate 48000  -vf scale -zoom -xy 720 -xvidencopts fixed_quant=4  -sub SUBTITLE -subfont-text-scale 4 -o OUTPUT
DivXPlayer Compatible?TO AVI?ANY to avi Tag PAL?mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=128 -srate 48000  -vf scale -zoom -xy 720 -xvidencopts fixed_quant=4  -o OUTPUT
DivXPlayer Compatible?TO AVI?ANY to avi Tag PAL with SUBTITLE?mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=128 -srate 48000  -vf scale -zoom -xy 720 -xvidencopts fixed_quant=4  -sub SUBTITLE -subfont-text-scale 4 -o OUTPUT
DVD?TO MPG?ANY to MPG Tag NTSC Aspect ratio 16:9?ffmpeg -i INPUT -target ntsc-dvd -aspect 16:9 OUTPUT
DVD?TO MPG?ANY to MPG Tag NTSC Aspect ratio 4:3?ffmpeg -i INPUT -target ntsc-dvd -aspect 4:3 OUTPUT
DVD?TO MPG?ANY to MPG Tag PAL=europe Aspect ratio 16:9?ffmpeg -i INPUT -target pal-dvd -aspect 16:9 OUTPUT
DVD?TO MPG?ANY to MPG Tag PAL=europe Aspect ratio 4:3?ffmpeg -i INPUT -target pal-dvd -aspect 4:3 OUTPUT
Video Filter?TO AVI?ANY to avi Tag Merge avi file see documentation?avimerge -o TEMP.avi -i PUTINALINE 
Audio?TO AC3?ANY to ac3 Tag HIGH quality?ffmpeg -i INPUT -ab 256k  -acodec aac -y OUTPUT
Tutorial?TO Create subtitle movie?all to all Tag Add subtitle in your command line FFMPEG remember the name of the srt file must be the same of movie file?ffmpeg -i BLA BLA BLA  -newsubtitle SUBTITLE
Tutorial?TO Create subtitle movie?all to all Tag Add subtitle in your command line MENCODER remember the name of the srt file must be the same of movie file?mencoder INPUT BLA BLA BLA -sub SUBTITLE -subfont-text-scale 4  BLA BLA -o OUTPUT
Video?TO FLV?ANY to flv Tag Flv_HIGH quality?ffmpeg -i INPUT -b 700k -r 25 -ab 256k -ar 44100 -f flv -y OUTPUT
Video?TO FLV?ANY to flv Tag Flv_LOW quality?ffmpeg -i INPUT -b 200k -r 25 -ab 128k -ar 22050 -f flv -y OUTPUT
Video?TO FLV?ANY to flv Tag Flv SAME quality?ffmpeg -i INPUT -sameq -f flv -y OUTPUT
Video?TO FLV?ANY to flv Tag Flv_MEDIUM quality?ffmpeg -i INPUT -b 500k -r 25 -ab 192k -ar 22050 -f flv -y OUTPUT
YouTube?To UPLOAD?ANY to flv Tag Encode for youtube videos?ffmpeg -i INPUT -b 500k -r 30 -ab 128k -ar 44100 -s 320x240 -ac 2 -y OUTPUT

```

---

### Post by Creative2 on 2008-01-24
youtube problem
in these days i tried to download youtube video with youtube-dl
it seems doesn't work anymore...
flv get idem
i think youtube has made something ....-.-''
i will see better -.-''

---

### Post by Odd-rationale on 2008-01-24
Do you plan to put this int the repos sometime? That would be great!

---

### Post by Creative2 on 2008-01-25
i am working around

---

### Post by Creative2 on 2008-01-25
ok youtube-dl doesn't work anymore...sigh...and..sob

---

### Post by Creative2 on 2008-01-26
0.0.6
Improved some thing like log and other little stuff in converter, converter i think it's stable 
added axel to download faster...
other maybe could have some problem (little) but they work

[http://www.mediafire.com/?3zz301vaj3b](http://www.mediafire.com/?3zz301vaj3b)

---

### Post by SammyBoy247 on 2008-01-26
Nice app, nice installer, nice guide....

... Nice work.

---

### Post by Creative2 on 2008-01-28
last function file :

news:

added SWF commandline 

[http://www.mediafire.com/?bzcedwblw56](http://www.mediafire.com/?bzcedwblw56)

---

### Post by Creative2 on 2008-01-28
[SIZE="5"][CENTER]**how fix youtube-dl **[/CENTER]
[/SIZE]
just type 

for kde 

```
sudo kate /usr/bin/youtube-dl 
```

or for gnome
```

sudo gedit /usr/bin/youtube-dl
```

and replace script with the last script patched 

you can find here :
[http://www.arrakis.es/~rggi3/youtube-dl/youtube-dl](http://www.arrakis.es/~rggi3/youtube-dl/youtube-dl)

---

### Post by X3n0n on 2008-01-30
Great app! Thanks!

I have some suggestions, though

You should add the option to place each converted file into the folder of the source. For example if you convert /home/user/song.wma to song.mp3, the mp3 should be in /home/user/song.mp3

Also I found some bugs...
When you don't select a command fuoco continues the progress but without actually converting the files

Also there is a problem with the 'nice' command....I rarely get fuoco to work...It usually fills the log with this error:
```
nice: a command must be given with an adjustment
Try `nice --help' for more information.
```

---

### Post by Creative2 on 2008-01-30
> **X3n0n said:**
> Great app! Thanks!

I have some suggestions, though

You should add the option to place each converted file into the folder of the source. For example if you convert /home/user/song.wma to song.mp3, the mp3 should be in /home/user/song.mp3


this it's a good idea...but you can do by yourself....

example 

conversion into avi 
```

ffmpeg -i INPUT OUTPUT
```

must be replace with 

```
ffmpeg -i INPUT  'INDIR/BASENAME.avi'
```

> **X3n0n said:**
> 

Also I found some bugs...
When you don't select a command fuoco continues the progress but without actually converting the files


yes i know..i will do some day 

> **X3n0n said:**
> 
Also there is a problem with the 'nice' command....I rarely get fuoco to work...It usually fills the log with this error:
```
nice: a command must be given with an adjustment
Try `nice --help' for more information.
```


? 
well you get that message because you use only a normal conversion without ENDLOOP ...it's not a bug ... i don't plan to fix that message  but i will explain about that...

---

### Post by X3n0n on 2008-01-30
Thanks for the reply!

> **Creative2 said:**
> 
? 
well you get that message because you use only a normal conversion without ENDLOOP ...it's not a bug ... i don't plan to fix that message  but i will explain about that...

I didn't quite get it, but as it's not a bug I wait for your explanation :)

---

### Post by Creative2 on 2008-01-30
1  nice = set program priority
2 fuoco function are written in this way:

nice loop-command line ENDLOOP nice after loop commad line

bu if you use only a nomal conversion fuoco load anyway afterloop-command line so  "after loop command line"  is only : nice -n value         

so it prints that,so it's a bug but...i knew  that issue ...if you look at code you will understand what i had in my mind..

---

### Post by Creative2 on 2008-02-03
note 
error in a commandline:
ANY-MP3 MEDIM QUALITY

correction 

Audio?TO MP3?ANY to mp3 Tag MEDIUM quality?ffmpeg -i INPUT -ab 192k -acodec mp3  -y  OUTPUT

---

### Post by Creative2 on 2008-02-03
**psp ffmpeg faster ** xvid

ANY-MP4 

```
ffmpeg -i INPUT -r 29.97 -vcodec xvid -maxrate 1500k -b 1250k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -g 300 -acodec aac -ar 48000 -ab 128k -ac 2 -s 368x208 OUTPUT
```

**psp ffmpeg faster ** h264 **** slower MAYBE SET BITRATE DOWN
 ANY-MP4 
```

ffmpeg -i INPUT -r 29.97 -vcodec h264 -flags +loop -cmp +chroma -deblockalpha 0 -deblockbeta 0 -b 1250k -maxrate 1500k -bufsize 4M -bt 256k -refs 1 -bf 3 -coder 1 -me umh -me_range 16 -subq 7 -partitions +parti4x4+parti8x8+partp8x8+partb8x8 -g 250 -keyint_min 25 -level 30 -qmin 10 -qmax 51 -qcomp 0.6 -trellis 2 -sc_threshold 40 -i_qfactor 0.71 -acodec aac -ab 112k -ar 48000 -ac 2 -s 480x272 OUTPUT
```

---

### Post by Creative2 on 2008-02-06
latest version :

-0.0.7  (Full version)
[http://www.mediafire.com/?43yiyy25zzd](http://www.mediafire.com/?43yiyy25zzd)

-1.0.0a(only converter )
[http://www.mediafire.com/?5jybmifm9cd](http://www.mediafire.com/?5jybmifm9cd)

---

### Post by Creative2 on 2008-02-12
out 

only converter 1.0.0b
[http://www.mediafire.com/?5tkeybbw0mm](http://www.mediafire.com/?5tkeybbw0mm)
full 0.0.7c
[http://www.mediafire.com/?1ymmqtz9sdg](http://www.mediafire.com/?1ymmqtz9sdg)

---

### Post by we_r_disturbed on 2008-02-12
Ok, I have to say that I really love the program.  It's very effective and easy to use.

However...

I too am having issues with "nice" errors.  As far as I can tell it only happens if I have a queue larger than X (don't have an exact number).  It's frustrating not being able to queue more than ~50 videos at once to encode...and I have a large collection that's needing to be converted.

Is there a setting I can change or something in the command? Any help on this would be appreciated.

---

### Post by Creative2 on 2008-02-13
plz tell me more about that problem 
when you put more than 50 files what does it happend?
with the last version 

1.0.0b or 0.0.7c nice error would be fixed
[B]
edit [/B]
i have just converted 122 photo no errors

---

### Post by we_r_disturbed on 2008-02-13
I'm running the latest version.  I installed it last night before I ran my test.

The actual error seems to happen at random.  I don't know if a single file in my group is causing it to stumble or what, but the error I get each time is:

> nice: a command must be given with an adjustment
Try `nice --help' for more information.

Like I said, this seems to happen at random.

**Edit: It does look like certain files are causing the error...I don't know if there was a problem with their original encoding, but I had to remove them one by one until it was happy enough to actually start the process.  It's nice to know if that's the reason it won't run any files...however it's bad that it doesn't say that's the problem, it gives the nice error.**

---

### Post by Creative2 on 2008-02-14
could you make a log  ?
anyway is not nice the issue, but your files . If you want a answer you must make a log and post here

---

### Post by Creative2 on 2008-02-16
**create a DIVX5**

```

mencoder INPUT -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=700:vpass=1 -ffourcc DIVX50 -oac mp3lame  -vf scale -zoom -xy 720  -o OUTPUT  
```

---

### Post by Stochastic on 2008-02-19
hmm I've got some ogg vorbis audio files that I'd like to make into mp3

I've set the program up to do this (using this command: ffmpeg -i -sameq INPUT -acodec mp3 -y OUTPUT) but it finishes (claims it's done) and no resulting mp3 files are made.

---

### Post by Creative2 on 2008-02-19
plz make log and post here :

extra and option set checked "create a log" (select your text editor gnome gedit , kde kate )

---

### Post by Creative2 on 2008-02-19
solved 
error in my commandline :)
this is correct:

ffmpeg -i **INPUT  -sameq ** -acodec mp3 -y OUTPUT

you found some information here 

[http://fuocotools.byethost13.com/index.php?topic=15.msg17#msg17](http://fuocotools.byethost13.com/index.php?topic=15.msg17#msg17)

---

### Post by KoolPenguin on 2008-02-19
First off, excellent work!  Makes my life a lot easier now and I will let others know about this program.

I did find a couple of problems.

- Main Menu, if you click on the "Load Another Function" button and click on the "Cancel" button on the next window, the icons disappear on the conversion list.

- eXtRa > TO NEW TRACK FOR MY AVI function doesn't work.  It attempts to do it and corrupts the AVI file.  If I do it with the command line (Terminal)  manually it works fine. Here is the output from Fuoco:

 1 mencoder '/home/kirsten/mylinux.avi' -oac copy -ovc copy -audiofile '/home/kirsten/mylinux.mp3'  -o '/home/kirsten/mylinux.avi'

MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) D CPU 2.80GHz (Family: 15, Model: 4, Stepping: 7)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0xb5af0ba
AVI file format detected.
[aviheader] Video stream found, -vid 0
VIDEO:  [FMP4]  1680x1040  24bpp  20.000 fps  6525.8 kbps (796.6 kbyte/s)
Audio file file format detected.
[V] filefmt:65536  fourcc:0x34504D46  size:1680x1040  fps:20.00  ftime:=0.0500
videocodec: framecopy (1680x1040 24bpp fourcc=34504d46)
audiocodec: framecopy (format=55 chans=2 rate=44100 bits=16 B/s=16000 sample-0)
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.1s      1f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
Pos:   0.1s      2f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.005 [0:0]
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream: 14811.120 kbit/s  (1851389 B/s)  size: 185139 bytes  0.100 secs  2 frames

Audio stream:  127.999 kbit/s  (15999 B/s)  size: 9613 bytes  0.601 secs

I'm using GNOME if it means anything.

Thanks again.

---

### Post by Creative2 on 2008-02-19
- Main Menu, if you click on the "Load Another Function" button and click on the "Cancel" button on the next window, the icons disappear on the conversion list.

-that i know well reloading fuoco you have icon.

**i will check **for that problem with ANOTHER TRACK FOR MY AVI 

mencoder INPUT -oac copy  -ovc copy -audiofile  'INDIR/BASENAME.mp3'   -o OUTPUT

---

### Post by wayfarer51 on 2008-02-21
With my vast intuitive powers, I've detected the slightest tinge of enthusiasm in Creative2's post.

Seriously, it looks like a valuable tool to add to my media arsenal.  Thanks for your hard work.  I'm reluctant to use KDE apps on my Gnome desktop, but I will if they are useful swissknife apps like this one.

Thanks.

Neill Dumont

---

### Post by Mahyar on 2008-03-04
Thank you for this application.  I have just converted some difficult mpegs to avi.

Much appreciated.

---

### Post by Creative2 on 2008-03-23
update
what's of new:
-work list 
-some bugs fixed
[http://www.mediafire.com/?uepx4eujry4](http://www.mediafire.com/?uepx4eujry4)

---

### Post by Creative2 on 2008-04-02
:) debian package 
[http://fuocotools.byethost13.com/index.php?topic=67.0](http://fuocotools.byethost13.com/index.php?topic=67.0)

---

### Post by Creative2 on 2008-04-09
updated version , fixed progress bar , debian packages , debian and rpm

---

### Post by OttifantSir on 2008-05-05
Thank you very much for this app, it is one of the best video conversion tools I have encountered. I would urge you to take a look at SUPER(c) video conversion for Windows (if you have the chance), and see how they have made a GUI for ffmpeg mencoder and other CLI video converters. Maybe get some ideas on how to make Fuoco more easily available for those (of us) that doesn't deal with CLI too easy.

A general overview of SUPER(c) is selectionboxes to alter the underlying CLI-code of the conversion tools used. But they lack the categories you've made in your application. I believe that if you could somehow make your application have a slightly lower entry-level for the user, it would be THE best video conversion tool out there. SUPER(c) is the only REAL reason I still have an old computer with Windows. After finding this application, I may go all Linux. 

Just wish I didn't have to read through the entire manual on ffmpeg, mencoder and whichever other CLI encoder you use.

---

### Post by Creative2 on 2008-05-05
yes i know super... but there is a difference among super on windows and linux with fuoco... super has a mencoder and ffmpeg but they don't change every time you upgrade your linux version...

ffmpeg and mencoder are always in changing.... i have made fuoco in that way because is very easy change command line that you could find on this forum or in other webpage

so i don't plane to modify the GUI i have written many commnad line 
with HIGH MEDIUM LOW quality so you have not to change nothing only choose your prefered quality anyway there is another converter you could like much more is winff but it's not a universal converter... 

cheers

---

### Post by _atle_ on 2008-05-08
Wanted to thank you for a great program. I am in the process of creating a screencast, and found your tool through ConvertIT, which have worked great for me. But your program seem to be a little better, and have more options. Most of my work has been done already using ConvertIT, so my credits will reflect that. But I plan to make more screencasts, and will be using your program, so I will give credits to you and links to your page. The screencast is in Norwegian, as that is my native language.

I am also thinking about installing Ubuntu Hardy Heron 64bit and wondered if your program works on this version as well, as ConvertIT did not work.

Once again, thank you for your efforts.

atlef.

---

### Post by Creative2 on 2008-05-08
:) 

Well i have started ConvertIT ...then i have decided  to create my personal tool with kommander because is very easy expand the program.. and i think has not so much problem with 64bit system as gambas has

i think it should work without problems on 64 system but i am not pretty sure let me know if it works or not.

cheers

---

### Post by _atle_ on 2008-05-08
Thank you for the quick reply. I will of course report back how it goes. And yes, it was the gambas that seemed to be the problem when I tried that on Hardy 64bit, so I switched to 32bit before I found your program.

atlef.

---

### Post by Creative2 on 2008-05-16
updated


full 0.0.7e **[color=red]NEW![/color]** contains converter 1.0.0        (updated some things..)
[http://www.mediafire.com/?gpedy2oybki](http://www.mediafire.com/?gpedy2oybki)

only converter 1.0.0 **[color=red] NEW![/color]**
[http://www.mediafire.com/?1bqmmlxx9j4](http://www.mediafire.com/?1bqmmlxx9j4)

---

### Post by thewOndErEr57 on 2008-05-16
In case anybody is put off by the youtube-dl script for its lack of a GUI interface, I have written a little software tool that now allows you to download youtube videos in Linux, specifying the desired format, resolution etc... as well as the ability to specify the directory you want all of your videos saved to.

Check it out here:

[http://yourtubedownloader.awardspace.com/]("http://yourtubedownloader.awardspace.com/")

Feedback most welcome !

Thanks

---

### Post by Creative2 on 2008-05-17
there a lots of softwares to do that ........ flvget .... and  pytube second 
and why do you post here your stuff  ?

---

### Post by neilg4rqn on 2008-05-26
Hi, so far I get on very well with Fuoco, thank you. However I have some problems converting to 3gp. I use a Sony Ericsson k750i and have tried using the available routing for "ANY to 3GP Tag Motorola v3i". The conversion works but the video on the phone always stutters about 10 seconds or so from the start, then resumes sometimes repeating the stutter later on. Is there a way I can alter the Motorola routine to improve things?
Thans
Neil

---

### Post by Creative2 on 2008-05-26
have you some informations about your phone ? 

i have seen a bit on google and it seems your phone is mp4 capable.. so don't use **** formats like 3gp

Try with this :

ffmpeg -i INPUT -s 176x144 -vcodec mpeg4 -acodec aac -ac 2 -ar 44100 -r 25 -ab 128k -y OUTPUT


if it's choppy or you feel like it is dropping frame try to replace frame rate from 

-r 25 

to

-r 20

or 

-r 15

---

### Post by neilg4rqn on 2008-05-26
I have tried a few examples of file suffix .mp4 and none will play om my k750i, the manual does not exactly say it will or will not play them as far as I can see. However I have had success with the suggested line modified as you said I might. I am using this "ffmpeg -i INPUT -s 176x144 -vcodec mpeg4 -acodec aac -ac 2 -ar 44100 -r 15 -ab 128k -y OUTPUT" as using -r 25 resulted in long silent pauses during playback, 20 still caused problems, video was not interupted - only the sound which is as before. One thing that might be relevant is that I am saving the video file to the add-on memory card and not to the phones main memory which is not big enough, the card memory access is a bit slower.  I will test further and post anything of interest.
Thank you for your help.
Neil

BTW conversion from mp4 files (I was using .avi before) to 3gp does seem less of a problem with -r 25

---

### Post by Creative2 on 2008-05-27
damned sony ericson  xD

well i have seen on google it seems many users have have your problems with -r 25 .... = frame rate 25 = fluid video.

they suggest to use 15 but in that case your video, i think, will not be so fluid...  they also suggest to use 176x144 because it supports only this resolution... :D motorola rocks 

well will try to use normal command line  with mono audio channel

ffmpeg -i INPUT -s 176x144 -ac 1 -vcodec mpeg4 -acodec aac  -ar 44100 -r 15 -ab 128k -y OUTPUT

(try always to increase framerate...)
 
maybe this is the best you have to test
```

ffmpeg -i INPUT -f mp4 -avcodec mpeg4 -r 16.5 -s qcif -acodec aac -ab 32k -ar 24000 -b 200k -y OUTPUT
```


you could find more information here 

[http://www.esato.com/board/viewtopic.php?topic=117059](http://www.esato.com/board/viewtopic.php?topic=117059)

cheers

---

### Post by neilg4rqn on 2008-05-27
Thank you Creative2, and an apology from me - looking back I see that I said in my first message that the video stutters- I should have said the audio was the main problem, sorry for the typo. I will try your suggestions as soon as time permits.
The video at 15fps is I would say acceptable for the size of the screen and the use I make of it.
Neil

---

### Post by Creative2 on 2008-05-28
no problem

---

### Post by neilg4rqn on 2008-06-02
I have had some time to play and I think I will use 

ffmpeg -i INPUT -s 176x144 -vcodec mpeg4 -acodec aac -ac 2 -ar 44100 -r 15 -ab 128k -y OUTPUT  

for my Sony Ericsson k750i. Perhaps not the best quality but it works.
Many thanks Creative2 for the help. 
Ciao
Neil

---

### Post by Creative2 on 2008-06-02
@Neil
well i will write that command line in the next version for your phone 
bye bye ....

@everybody
one guys has tested fuoco tools on 64bit system and it works fine :)

---

### Post by _atle_ on 2008-06-05
> **Creative2 said:**
> 
@everybody
one guys has tested fuoco tools on 64bit system and it works fine :)

Hi again, Creative2. Sorry for the late response, but I can confirm that it works perfectly well on Hardy Heron 64bit.

Thank you for a very good program.

atlef.

---

### Post by Creative2 on 2008-06-06
well 2 gusy are better than 1 :)

---

### Post by SonicSteve on 2008-06-10
This is awesome, 
A student at my school asked me to convert an AVI to MPEG and thanks to this I was able to get it done for her. Linux has come through so many times this year and it's thanks to the inginuity of its community. 

Fuoco tools is great thanks.
I'm currently using it on gutsy 7.10, I'll try it on my Heron 8.04 laptop later tonight.

Edit,
I just want to again say thanks. This set of tools is amazing. This time a student used her phone to take a video but could use the video because it was .3gp format. These tools perfectly converted it to mpeg. Awesome!!

---

### Post by Creative2 on 2008-06-15
@SonicSteve 
:)

---

