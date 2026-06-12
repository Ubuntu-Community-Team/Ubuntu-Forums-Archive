---
title: "Find DVD using command line"
date: 2014-08-03
forum: Multimedia Software
---

### Post by aaron50 on 2014-08-03
Hi All,

i just installed ubuntu 14.04 using my optical drive. I inserted a dvd into it, how do I find that dvd from the command line? This is a headless server and I am trying to write a bash scrip to detect my dvd. My script was 

```
if [ $ID_CDROM_MEDIA_DVD" == "" ]
then
     echo "No DVD detected" >> /etc/udev/rules.d/DetermineMediaType.log
else
     echo "DVD detected" >> /etc/udev/rules.d/DetermineMediaType.log
fi
exit 0
```

this code returns "no dvd detected" even though there is a dvd in my drive.

i now am manually trying to see if I can see the dvd in a folder but my /media/cdrom is empty, where is my dvd stored? I am completely new to ubuntu so I am not sure if I have to mount (not quite sure what this means) it or something first to see the dvd, but like I said I know the drive works because I installed ubuntu from the drive. Thanks for any help.

---

### Post by sudodus on 2014-08-03
I think this command will find it, it is often **/dev/sr0** in Ubuntu systems, might be another number than zero, and devices are listed with links in **/dev/disk/by-id**

```
[COLOR=#0000cd]ls -l /dev/disk/by-id| grep sr[0-9]$|tr -s ' ' ' '|cut -d ' ' -f 9,11 |sort -k2|grep -e \^a -e \^u|sed 's#../..#/dev#'[/COLOR]
ata-HL-DT-STDVD+-RW_GSA-H21L /dev/sr0
```

Edit: I realize that you want not only to check that the DVD drive is recognized, but if there is a disk inserted.

The command ***cdir*** can do that for cd disks

```
cdir -sd /dev/sr0
cdir -vd /dev/sr0
```

See ```
man cdtool
```

And for DVD disks you can use ***dvd+rw-mediainfo***

```
dvd+rw-mediainfo /dev/sr0
```

See ```
man dvd+rw-mediainfo
```

And you can use the response of those commands to identify what is in the DVD drive.

---

### Post by mc4man on 2014-08-03
> where is my dvd stored?
Not sure about if a server is any different but currently on desktops the filesystem on a dvd is automounted to /media/<username>/volume_label
You could override that in fstab if desired,  ex. (using a new created folder - cdrom0 & assuming drive is /dev/sr0

sudo mkdir -p /etc/cdrom0

Then in fstab a new line
```
/dev/sr0  /media/cdrom0  udf,iso9660 user,noauto,exec    0  0
```

---

### Post by aaron50 on 2014-08-03
Thank you for those responses. I put this into my fdisk
 /dev/cdrom  /mnt/cdrom   auto    noauto,user          0 0

then mounted the drive and I can see the dvd in the drive /media/cdrom. When I run blkid i see this 

/dev/sr0: LABEL="Name of movie" TYPE="udf"

not sure what udf is, but I can see the dvd. Now I need some time of identifier for my if statement in my bash code to see if there is a dvd in the drive. This is not working 

If ["$ID_CDROM_MEDIA_DVD" == "" ]

what needs to go in my if statement to say if there is a dvd in the drive or not. I tried if blkid /dev/sr0:TYPE = "udf" but nothing happened. It skipped the entire statement. Thanks for any help.

---

### Post by mc4man on 2014-08-03
Not too sure you needed the fstab, just mentioned in case you needed a known location for whatever it is you want done.
Maybe look at using mount command somehow  - 
```
mount -t udf
```
will produce output of device & location if a dvd is mounted (or at least most dvd's ???), nothing if not found.

---

### Post by aaron50 on 2014-08-03
Well, I am not quite sure how to implement this into my bash code. Maybe if I explained my overall goal that would help you. I am trying to create a bash script that I will run when I put a disc into the cdrom. The script will output a log file indicating if there is a disc in the tray and if the disc in the tray is a dvd. The overall goal is that if there is a dvd in the tray I will fire off a script that will rip the dvd and store it on my hard drive. I think I have the script that will rip the dvd, but I need the bash script here to detect the disc and determine if it a dvd and kick off the script to rip the dvd. Thanks again for all of your help.

---

### Post by sudodus on 2014-08-03
You can test what is in the drive with

```
dvd+rw-mediainfo /dev/sr0
```

and depending on the result start the job or not. Either use the text output or the exit code. Maybe it is easiest with the exit code (0 if a DVD inserted).

```

#!/bin/bash

dvd+rw-mediainfo /dev/sr0
if [ $? -eq 0 ]
then
     echo "DVD detected" >> /etc/udev/rules.d/DetermineMediaType.log
     echo "do the job"
else
     echo "No DVD detected" >> /etc/udev/rules.d/DetermineMediaType.log
fi

```

But you should also check if /dev/sr0 is the correct device name (see post #2). You can probably do that once (for each computer).

Edit: If you don't want the output to the screen, redirect it to /dev/null

---

### Post by aaron50 on 2014-08-03
That worked!! Thank you so much. Now I need to try to fix my dvd rip code, Ha. Maybe you know something about this?

Here is my script:
```

#!/usr/bin/env sh

DVD="!1"
HANDBRAKE=HandBrakeCLI
LOG="logger -p daemon.info -t ripdvd.sh

OUTDIR="/home/amotto11/media/movies/"

function beep_success() {    beep -f 750 -l 80 -r 5 -D 20
}


function beep_failure() {
    beep -f 200 -l 900
}


function dvdrip() {
    $LOG "Beginning rip of $DVD"
    local LABEL=`file -s "$DVD" | cut -f 2- -d "'" | cut -f 1 -d "'" | sed -e 's/ *$//'`
    $LOG "$DVD contains $LABEL"
    $LOG $HANDBRAKE --verbose 9 --input "$DVD" --output "$OUTDIR/$LABEL.mkv"
    $HANDBRAKE --verbose 9 --input "$DVD" --output "$OUTDIR/$LABEL.mkv" 2>&1 > $OUTDIR/HandBrake.log
    local STATUS="$?"
    $LOG "Finished importing $LABEL from $DVD (status = $STATUS)"
    return $STATUS
}


if dvdrip; then
    beep_success
else
    beep_failure
fi


eject

```


The error I am getting is
```
/usr/bin/ripdvd.sh: 13: /usr/bin/ripdvd.sh: Syntax error: "(" unexpected
```


when I change the first line to #!/usr/bin/env bash, I am getting these errors
```
/usr/bin/ripdvd.sh: line 21: Syntax error near unexpected token '('
/usr/bin/ripdvd.sh: line 21: 'function dvdrip() {'
```

any suggestions are greatly appretiated. Thanks

---

### Post by sudodus on 2014-08-03
```
function dvdrip() {
```

In bash scripts (which I know best), functions are not written with (). I don't know about sh, but try like this

```
function dvdrip {
```

---

### Post by dave131 on 2014-08-03
I think you're missing an ending quote here:

#!/usr/bin/env sh

DVD="!1"
HANDBRAKE=HandBrakeCLI
LOG="logger -p daemon.info -t ripdvd.sh[COLOR=#ff0000][/COLOR][COLOR=#ff0000]" <--[/COLOR]
[COLOR=#ff0000][/COLOR]

---

### Post by aaron50 on 2014-08-03
Dave,

I am sorry I am doing this on a headless machine, hence the beeps as a notification, so I had to retype the code. That line actually reads

```
LOG="logger -p daemon.info -t ripdvd.sh --"
```

sudodus,

i tried that that and now I am getting a lot more errors when I run sudo bash /usr/bin/ripdvd.sh
```
/usr/bin/ripdvd.sh: line 21: function: command not found
/usr/bin/ripdvd.sh: line 23: local: can only be used in a function
Missing input device. Run HandBrakeCLI --help for syntax
/usr/bin/ripdvd.sh: line 27: local: can only be used in a function
/usr/bin/ripdvd.sh: line 29: return: can only 'return' from a function or sourced script
/usr/bin/ripdvd.sh: line 30: syntax error near unexpected token '}'
/usr/bin/ripdvd.sh: line 30: '}'

```

for reference this is the script:

```
#!/usr/bin/env bash

DVD="!1"
HANDBRAKE=HandBrakeCLI
LOG="logger -p daemon.info -t ripdvd.sh --"

OUTDIR="/home/amotto11/media/movies/"

function beep_success {    
   beep -f 750 -l 80 -r 5 -D 20
}

function beep_failure {
    beep -f 200 -l 900
}

function dvdrip {
    $LOG "Beginning rip of $DVD"
    local LABEL=`file -s "$DVD" | cut -f 2- -d "'" | cut -f 1 -d "'" | sed -e 's/ *$//'`
    $LOG "$DVD contains $LABEL"
    $LOG $HANDBRAKE --verbose 9 --input "$DVD" --output "$OUTDIR/$LABEL.mkv"
    $HANDBRAKE --verbose 9 --input "$DVD" --output "$OUTDIR/$LABEL.mkv" 2>&1 > $OUTDIR/HandBrake.log
    local STATUS="$?"
    $LOG "Finished importing $LABEL from $DVD (status = $STATUS)"
    return $STATUS
}

if dvdrip; then
    beep_success
else
    beep_failure
fi
eject
```

I am an ubuntu newbie, so here is the tutorial I am following if your wondering [http://www.phillomath.com/node/4](http://www.phillomath.com/node/4)

thank you so much again!

---

### Post by sudodus on 2014-08-03
I checked, and in sh, function declarations have (), but there must be a space before and after (), so 

```
function dvdrip() {
```

should be

```
function dvdrip () {
```

I suggest that you stay in sh, because there are several other things that differ too (and create problems).

---

### Post by aaron50 on 2014-08-03
Okay I put the () in with space on each side and changed the first line to #!/usr/bin/env sh

I'm running it like this 
amotto11@LaptopMediaServer: /usr/bin$ ./ripdvd.sh

im getting the error of
./ripdvd.sh: 13: ./ripdvd.sh: Syntax error: "(" unexpected. What am I doing wrong? Thanks

---

### Post by sudodus on 2014-08-03
You must show the current script. Otherwise we can only guess what is in line 13. Maybe another instance of () without a space before it.

---

### Post by aaron50 on 2014-08-03
Okay here is the script:

```
#!/usr/bin/env sh

# Acknowledge that we are starting
beep -f 1400 -l 250


DVD="$1"
HANDBRAKE=HandBrakeCLI
LOG="logger -p daemon.info -t ripdvd.sh --"


#Change this to reflect where you store your dvd rips
OUTDIR="/home/amotto11/media/movies/"


function beep_success () {
beep -f 750 -l 80 -r 5 -D 20
}


function beep_failure () {
beep -f 200 -l 900
}


fuction dvdrip () {
$LOG "Beginning rip of $DVD"
local LABEL=`file -s "$DVD" | cut -f 2- -d "'" | cut -f 1 -d "'" | sed -e's/ *$//'`
$LOG "$DVD contains $LABEL"
$LOG $HANDBRAKE --verbose 9 --input "$DVD" --output "$OUTDIR/$LABEL.mkv"
$HANDBRAKE --verbose 9 --input "$DVD" --output "$OUTDIR/$LABEL.mkv" 2>&1 > $OUTDIR/HandBrake.log
local STATUS="$?"
$LOG "Finished importing $LABEL from $DVD (status = $STATUS)"
return $STATUS
}


if dvdrip; then
beep_success
else
beep_failure
fi


eject
```

and here is the output

```
amotto11@LaptopMediaServer:~$ cd /usr/bin/amotto11@LaptopMediaServer:/usr/bin$ ./ripdvd.sh 
./ripdvd.sh: 13: ./ripdvd.sh: Syntax error: "(" unexpected
amotto11@LaptopMediaServer:/usr/bin$
```

---

### Post by sudodus on 2014-08-03
fuction dvdrip
n is missing

---

### Post by aaron50 on 2014-08-03
I'm not quite sure I understand what your saying. I'm sorry if it's quite obvious and don't see it. Thanks

---

### Post by mc4man on 2014-08-03
> **aaron50 said:**
> I'm not quite sure I understand what your saying. I'm sorry if it's quite obvious and don't see it. Thanks

He meant your missing an n in  fuction dvdrip () { 
Your script works ok here started  manually though I'd note 2 things - 
I'd probably remove the fstab entry as eject may not work as a user otherwise
You need to use the ppa version of handbrake or the conversion will fail as the repo libav source is not built with libfaac support 
(- [https://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg1198390.html](https://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg1198390.html)

Edit: by working I meant to add using bash, not sh (after fixing missing n

---

### Post by dave131 on 2014-08-04
The missing "n" is in the word "function" for dvdrip  - you show " fuction dvdrip () { " instead of " function dvdrip () { " if you didn't see it.

---

### Post by mc4man on 2014-08-04
You also should look at the handbrake cli options as your current HandBrakeCLI command will produce pretty low quality encodes
[https://trac.handbrake.fr/wiki/CLIGuide](https://trac.handbrake.fr/wiki/CLIGuide)

---

### Post by aaron50 on 2014-08-04
I have updated my script to add the n in function:

```
#!/usr/bin/env sh

# Acknowledge that we are starting
beep -f 1400 -l 250




DVD="$1"
HANDBRAKE=HandBrakeCLI
LOG="logger -p daemon.info -t ripdvd.sh --"


#Change this to reflect where you store your dvd rips
OUTDIR="/home/amotto11/media/movies/"


function beep_success () {
   beep -f 750 -l 80 -r 5 -D 20
}


function beep_failure () {
   beep -f 200 -l 900
}


function dvdrip () {
$LOG "Beginning rip of $DVD"
local LABEL=`file -s "$DVD" | cut -f 2- -d "'" | cut -f 1 -d "'" | sed -e's/ *$//'`
$LOG "$DVD contains $LABEL"
$LOG $HANDBRAKE --verbose 9 --input "$DVD" --output "$OUTDIR/$LABEL.mkv"
$HANDBRAKE --verbose 9 --input "$DVD" --output "$OUTDIR/$LABEL.mkv" 2>&1 > $OUTDIR/HandBrake.log
local STATUS="$?"
$LOG "Finished importing $LABEL from $DVD (status = $STATUS)"
return $STATUS
}


if dvdrip; then
beep_success
else
beep_failure
fi


eject
```

but I am still getting an error

```
amotto11@LaptopMediaServer:~$ cd /usr/bin/amotto11@LaptopMediaServer:/usr/bin$ ./ripdvd.sh ./ripdvd.sh: 13: ./ripdvd.sh: Syntax error: "(" unexpected
amotto11@LaptopMediaServer:/usr/bin$
```

Also I removed the fstab code that I had input.

mc4man,
i am not quite sure I understand what your saying in you post about the ppa version of handbrake. I am sorry, this is all pretty new to me.
when I ran the code in bash I got the following and the disc ejected. No beeps and nothing in /home/amotto11/media/movies/HandBrake.log
```
amotto11@LaptopMediaServer:~$ cd /usr/bin/amotto11@LaptopMediaServer:/usr/bin$ sudo bash ./ripdvd.sh Missing input device. Run HandBrakeCLI --help for syntax
amotto11@LaptopMediaServer:/usr/bin$
```

as far as your link [https://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg1198390.html](https://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg1198390.html) I don't know where the /test/test file is located. Thanks

---

### Post by mc4man on 2014-08-04
Well as I can only comment on this as seen on a desktop install maybe only a little value.

As far as bash vs. dash, the script works with bash. Otherwise see the same error as did someone commenting in the blog where you got the script. That users 'solution' to "ripdvd.sh: 13: ./ripdvd.sh: Syntax error: "(" unexpected" makes no sense or effect here. (he/she says removing the space here fixed, [COLOR="#FF0000"]X[/COLOR] is the space
--output "$OUTDIR/$LABEL.mkv"[COLOR="#FF0000"]X[/COLOR]2>&1
The only thing here that does is add a 2 to file extension, ie. .mkv2

If you were manually testing then it's -  <script>  <device> so for example here the script is named ripdvd & it's in a bin folder so - 
:~$ ripdvd /dev/sr0
That works fine 

As far as handbrake - 
The repo version uses system shared libav libraires so among other issues it can't encode audio to aac as Hb uses libaac & the repo libav does not. (hence that bug report I linked

The ppa builds use their own ffmpeg libs & are really the only good handbrake builds.
There aren't any stable releases for 14.04 in the ppa so you need to use the snapshot ppa which may work fine or may not, depends on the day I guess.
For instance yesterdays would not use the high profile preset, todays build does. (6262svn 
ppa is here - 
[https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-snapshots](https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-snapshots)

As far as the script & Hb - 
The hb command in the script will just encode to MPEG-4 Visual which is pretty bad unless your screen is 5" or so. I haven't spent much time with hb so don't know the ins or out, some of the presets seem ok.
(to see them run -
 HandBrakeCLI -z

The Normal is ok but no ac3, only aac stereo.
The High Profile is pretty good as is AppleTV 3, Id go with the former. 
I'd assume one could use a preset & override any individual parameter ??

So here the script line here for hb- 
```
$HANDBRAKE --verbose 9 --input "$DVD" --output "$OUTDIR/$LABEL.mkv" --preset="High Profile" 2>&1 > $OUTDIR/HandBrake.log
```

As far as beep - 
doesn't produce any sound here on desktop, doesn't cause any error, irrelevant..

In the blog they were using halevt to detect & pass device to the script, that's no longer avail. so I  gather that's the real purpose of this thread. In this case as I'm on a desktop install so can't really help,...
(on a desktop install one can simply set dvd insertion to autorun the script

---

### Post by aaron50 on 2014-08-05
Mc4man,

so I tried to run the script like you said with the first line as #!/usr/bin/env and it gave me the line 13 error again, so I changed the first line to end in bash. Have no idea what the difference is, I thought the # commented out the line, so not quite sure why it let the code run as bash. Here is the script that I used, I used your suggestion and change the handbrake line below as well:

```
#!/usr/bin/env bash

# Acknowledge that we are starting
beep -f 1400 -l 250


DVD="$1"
HANDBRAKE=HandBrakeCLI
LOG="logger -p daemon.info -t ripdvd.sh --"


#Change this to reflect where you store your dvd rips
OUTDIR="/home/amotto11/media/movies/"


function beep_success () {
beep -f 750 -l 80 -r 5 -D 20
}


function beep_failure () {
beep -f 200 -l 900
}


function dvdrip () {
$LOG "Beginning rip of $DVD"
local LABEL=`file -s "$DVD" | cut -f 2- -d "'" | cut -f 1 -d "'" | sed -e's/ *$//'`
$LOG "$DVD contains $LABEL"
$LOG $HANDBRAKE --verbose 9 --input "$DVD" --output "$OUTDIR/$LABEL.mkv"
$HANDBRAKE --verbose 9 --input "$DVD" --output "$OUTDIR/$LABEL.mkv" --preset="High Profile" 2>&1 > $OUTDIR/HandBrake.log
local STATUS="$?"
$LOG "Finished importing $LABEL from $DVD (status = $STATUS)"
return $STATUS
}


if dvdrip; then
beep_success
else
beep_failure
fi


eject
```

as far as the ppa, when I first installed handbrake I ran this one
```
sudo add-apt-repository ppa:noobslab/apps
```
now I don't know how to remove it or if that matters, but I ran your suggestion
```
sudo add-apt-repository ppa:stebbins/handbrake-snapshots
```
like I said I don't know if I have to remove the first one, but I didn't.

then I ran the code as you suggested, not changing the test/test.c file at all. The code "worked" somewhat. It created a log file and the movie.mkv. This all happened in 10sec so I know it didn't fully download, and the movie didn't play on anything when I accessed it from my file sharer, samba and was only a couple of kb. When I did run the script I noticed through the output that there were some errors. Unfortunately I can't execute the code remotely, it only goes so far then quits and ejects, when I run it on the server itself it goes through many steps, here is what it says when I run it remotely

```
amotto11@LaptopMediaServer:/usr/bin$ sudo ripdvd.sh dev/sr0
[20:02:59] hb_init: starting libhb thread
HandBrake 0.9.9 (2013121000) - Linux i686 - http://handbrake.fr
1 CPU detected
Opening dev/sr0...
[20:02:59] hb_scan: path=dev/sr0, title_index=1
libbluray/bdnav/index_parse.c:162: indx_parse(): error opening dev/sr0/BDMV/index.bdmv
libbluray/bdnav/index_parse.c:162: indx_parse(): error opening dev/sr0/BDMV/BACKUP/index.bdmv
libbluray/bluray.c:1725: nav_get_title_list(dev/sr0) failed (0xb5c00490)
[20:02:59] bd: not a bd - trying as a stream/file instead
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat dev/sr0
No such file or directory
libdvdnav: vm: failed to open/read the DVD
[20:02:59] dvd: not a dvd - trying as a stream/file instead
[20:02:59] hb_stream_open: open dev/sr0 failed
[20:02:59] scan: unrecognized file type
[20:02:59] libhb: scan thread found 0 valid title(s)
No title found.
HandBrake has exited.
amotto11@LaptopMediaServer:/usr/bin$
```

when I run from the server the few errors I can still see on the screen are here:

```
ERROR: dvdnav: Read Error, Error reading NAV package.
ERROR: Last error repeated 3 times
ERROR: dvdnav: Read Error, Error reading from DVD
```

could this have something to do with the workaround you were talking about? We're is the test/test.c file that other link was referring to.

---

### Post by steeldriver on 2014-08-05
dev/sr0 is not the same thing as **/**dev/sr0 (unless you are running this from / of course - which you're not)

Also I'm not sure why you need to use anything other than the simple shebang #!/bin/bash - using #!/usr/bin/env is only usually necessary for portability across systems where the interpreter might be in different places, and afaik bash is pretty much always going to be in /bin (unless you are running some local version of bash?)

---

### Post by aaron50 on 2014-08-05
I updated the code to be #!/bin/bash and ran sudo ripdvd.sh /dev/sr0

```
[COLOR=#000000][FONT=Ubuntu Mono]#!/bin/bash[/FONT][/COLOR]
# Acknowledge that we are starting
beep -f 1400 -l 250

DVD="$1"
HANDBRAKE=HandBrakeCLI
LOG="logger -p daemon.info -t ripdvd.sh --"

#Change this to reflect where you store your dvd rips
OUTDIR="/home/amotto11/media/movies/"

function beep_success () {
beep -f 750 -l 80 -r 5 -D 20
}

function beep_failure () {
beep -f 200 -l 900
}

function dvdrip () {
$LOG "Beginning rip of $DVD"
local LABEL=`file -s "$DVD" | cut -f 2- -d "'" | cut -f 1 -d "'" | sed -e's/ *$//'`
$LOG "$DVD contains $LABEL"
$LOG $HANDBRAKE --verbose 9 --input "$DVD" --output "$OUTDIR/$LABEL.mkv"
$HANDBRAKE --verbose 9 --input "$DVD" --output "$OUTDIR/$LABEL.mkv" --preset="High Profile" 2>&1 > $OUTDIR/HandBrake.log
local STATUS="$?"
$LOG "Finished importing $LABEL from $DVD (status = $STATUS)"
return $STATUS
}

if dvdrip; then
beep_success
else
beep_failure
fi [COLOR=#000000][FONT=Ubuntu Mono]eject[/FONT][/COLOR]
```

I am still getting some errors and i noticed when the output was going by about 3-4 red lines in addition to the errors that i had before. I cant tell what these are and i cant go back to see them. I tried ****+pgup, but i can't go up that far. Here is what the log says when the script is done and it creates it in /home/amotto11/media/movies/HandBrake.log

```
^MEncoding: task 1 of 1, 0.00%^MEncoding: task 1 of 1, 0.00%^MEncoding: task 1 of 1, 0.00%^MEncoding: task 1 of 1, 0.00%
```

Im not sure what i am doing wrong. The Movie it outputs is only about 1Kb or so, obviously as the log says there was no task completed. Thanks for your continued help.

Edit: here is the red part of the output from a picture from my ipad.

---

### Post by steeldriver on 2014-08-05
Sorry I don't know anything about handbrake, however it seems odd to me that it would accept the raw block device (i.e. /dev/sr0) as its input - normally, you would need to mount the device somewhere in the filesystem, and give the mountpoint to your application

---

### Post by aaron50 on 2014-08-05
I am not sure, I may need to mount it first, but from the website I was following it didn't look like they did.

---

### Post by mc4man on 2014-08-05
What package of handbrake are you using? 
The Ubuntu repo version will fail because of no faac support. I guess if using then you'll need to prevent hb from doing an aac track. As mentioned only the ppa builds are any good.

The red lines aren't important (I don't believe) as they only are messages about the ac3 tracks, I marked some below.

Note - handbrake isn't 'accepting the raw block device', the script is... (though it appears to pass along to hb

> doug@doug-Lenovo-IdeaPad-Y510P:~$ ripdvd
Missing input device. Run HandBrakeCLI --help for syntax.
doug@doug-Lenovo-IdeaPad-Y510P:~$ ripdvd /dev/sr0
[22:04:54] hb_init: starting libhb thread
HandBrake svn6262 (2014080401) - Linux x86_64 - [http://handbrake.fr](http://handbrake.fr)
8 CPUs detected
Opening /dev/sr0...
[22:04:54] CPU: Intel(R) Core(TM) i7-4700MQ CPU @ 2.40GHz
[22:04:54]  - Intel microarchitecture Haswell
[22:04:54]  - logical processor count: 8
[22:04:54] OpenCL: library not available
[22:04:54] hb_scan: path=/dev/sr0, title_index=1
libbluray/bdnav/index_parse.c:162: indx_parse(): error opening /media/doug/ETERNAL_SUNSHINE_OF_THE_SPOT/BDMV/index.bdmv
libbluray/bdnav/index_parse.c:162: indx_parse(): error opening /media/doug/ETERNAL_SUNSHINE_OF_THE_SPOT/BDMV/BACKUP/index.bdmv
libbluray/bluray.c:2182: nav_get_title_list(/media/doug/ETERNAL_SUNSHINE_OF_THE_SPOT) failed
[22:04:54] bd: not a bd - trying as a stream/file instead
[22:04:54] dvd: Region mask 0xfe
libdvdnav: Using dvdnav version 5.0.0
libdvdnav: DVD Title: ETERNAL_SUNSHINE_OF_THE_SPOT
libdvdnav: DVD Serial Number: 30fc874a
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/doug/.dvdnav/ETERNAL_SUNSHINE_OF_THE_SPOT.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000153
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000079fb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00007c81
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0033149e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x003314a2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0034a2d2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0034a2d6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0037dcb3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0037dcb7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x003c3a94
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003c3a98
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003e1ce9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003e1ced
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003edd4f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003edd53
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003f0680
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003f0684
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x003f1e46
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x003f1e4a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x003f447f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x003f4483
libdvdread: Elapsed time 0
libdvdread: Found 10 VTS's
libdvdread: Elapsed time 0
[22:04:54] scan: DVD has 11 title(s)
[22:04:54] scan: scanning title 1
[22:04:54] scan: opening IFO for VTS 1
[22:04:54] scan: duration is 01:47:41 (6461166 ms)
[22:04:54] pgc_id: 1, pgn: 1: pgc: 0x7fcedc019060
[22:04:54] scan: vts=1, ttn=1, cells=0->21, blocks=0->3315692, 3315693 blocks
[22:04:54] scan: checking audio 1
[22:04:54] scan: id=0x80bd, lang=English (AC3), 3cc=eng ext=0
[22:04:54] scan: checking audio 2
[22:04:54] scan: id=0x89bd, lang=English (DTS), 3cc=eng ext=0
[22:04:54] scan: checking audio 3
[22:04:54] scan: id=0x82bd, lang=Francais (AC3), 3cc=fra ext=0
[22:04:54] scan: checking audio 4
[22:04:54] scan: id=0x83bd, lang=English (AC3), 3cc=eng ext=3
[22:04:54] scan: checking subtitle 1
[22:04:54] scan: id=0x20bd, lang=English, 3cc=eng ext=0
[22:04:54] scan: checking subtitle 2
[22:04:54] scan: id=0x21bd, lang=Espanol, 3cc=spa ext=0
[22:04:54] scan: checking subtitle 3
[22:04:54] scan: id=0x22bd, lang=Francais, 3cc=fra ext=0
[22:04:54] scan: title 1 has 21 chapters
[22:04:54] scan: chap 1 c=0->0, b=0->122469 (122470), 221934 ms
[22:04:54] scan: chap 2 c=1->1, b=122470->346546 (224077), 407166 ms
[22:04:54] scan: chap 3 c=2->2, b=346547->439570 (93024), 174166 ms
[22:04:54] scan: chap 4 c=3->3, b=439571->571678 (132108), 251867 ms
[22:04:54] scan: chap 5 c=4->4, b=571679->635910 (64232), 117467 ms
[22:04:54] scan: chap 6 c=5->5, b=635911->810856 (174946), 336500 ms
[22:04:54] scan: chap 7 c=6->6, b=810857->902015 (91159), 168500 ms
[22:04:54] scan: chap 8 c=7->7, b=902016->1135148 (233133), 427500 ms
[22:04:54] scan: chap 9 c=8->8, b=1135149->1383520 (248372), 477500 ms
[22:04:54] scan: chap 10 c=9->9, b=1383521->1579670 (196150), 382000 ms
[22:04:54] scan: chap 11 c=10->10, b=1579671->1665565 (85895), 164667 ms
[22:04:54] scan: chap 12 c=11->11, b=1665566->1893805 (228240), 430400 ms
[22:04:54] scan: chap 13 c=12->12, b=1893806->2009852 (116047), 208500 ms
[22:04:54] scan: chap 14 c=13->14, b=2009853->2405277 (395425), 776333 ms
[22:04:54] scan: chap 15 c=15->15, b=2405278->2572763 (167486), 337667 ms
[22:04:54] scan: chap 16 c=16->16, b=2572764->2657430 (84667), 174000 ms
[22:04:54] scan: chap 17 c=17->17, b=2657431->2880436 (223006), 442166 ms
[22:04:54] scan: chap 18 c=18->18, b=2880437->3004216 (123780), 247000 ms
[22:04:54] scan: chap 19 c=19->19, b=3004217->3244074 (239858), 493000 ms
[22:04:54] scan: chap 20 c=20->20, b=3244075->3315687 (71613), 221834 ms
[22:04:54] scan: chap 21 c=21->21, b=3315688->3315692 (5), 1000 ms
[22:04:54] scan: aspect = 1.77778
[22:04:54] scan: decoding previews for title 1
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
[22:04:54] scan: title angle(s) 1
Scanning title 1 of 1, preview 1, 10.00 %[22:04:54] scan: audio 0x89bd: dca, rate=48000Hz, bitrate=768000 English (DTS) (5.1 ch)
[COLOR="#FF0000"][ac3 @ 0x7fcedc061b00] frame sync error
[ac3 @ 0x7fcedc0624c0] frame sync error[/COLOR]
[22:04:54] scan: audio 0x83bd: ac3, rate=48000Hz, bitrate=192000 English (AC3) (Director's Commentary 1) (2.0 ch) (Dolby Surround)
[COLOR="#FF0000"][ac3 @ 0x7fcedc064ba0] frame sync error[/COLOR]
[22:04:54] scan: audio 0x80bd: ac3, rate=48000Hz, bitrate=448000 English (AC3) (5.1 ch)
[COLOR="#FF0000"][ac3 @ 0x7fcedc068440] frame sync error
[ac3 @ 0x7fcedc067a00] frame sync error[/COLOR]
[22:04:54] scan: audio 0x82bd: ac3, rate=48000Hz, bitrate=384000 Francais (AC3) (5.1 ch)
Scanning title 1 of 1, preview 10, 100.00 %[22:04:57] scan: 10 previews, 720x480, 23.976 fps, autocrop = 6/14/0/0, aspect 16:9, PAR 32:27
[22:04:57] libhb: scan thread found 1 valid title(s)
+ title 1:
  + vts 1, ttn 1, cells 0->21 (3315693 blocks)
  + duration: 01:47:41
  + size: 720x480, pixel aspect: 32/27, display aspect: 1.78, 23.976 fps
  + autocrop: 6/14/0/0
  + support opencl: no
  + support hwd: not built-in
  + chapters:
    + 1: cells 0->0, 122470 blocks, duration 00:03:42
    + 2: cells 1->1, 224077 blocks, duration 00:06:47
    + 3: cells 2->2, 93024 blocks, duration 00:02:54
    + 4: cells 3->3, 132108 blocks, duration 00:04:12
    + 5: cells 4->4, 64232 blocks, duration 00:01:57
    + 6: cells 5->5, 174946 blocks, duration 00:05:37
    + 7: cells 6->6, 91159 blocks, duration 00:02:49
    + 8: cells 7->7, 233133 blocks, duration 00:07:08
    + 9: cells 8->8, 248372 blocks, duration 00:07:58
    + 10: cells 9->9, 196150 blocks, duration 00:06:22
    + 11: cells 10->10, 85895 blocks, duration 00:02:45
    + 12: cells 11->11, 228240 blocks, duration 00:07:10
    + 13: cells 12->12, 116047 blocks, duration 00:03:29
    + 14: cells 13->14, 395425 blocks, duration 00:12:56
    + 15: cells 15->15, 167486 blocks, duration 00:05:38
    + 16: cells 16->16, 84667 blocks, duration 00:02:54
    + 17: cells 17->17, 223006 blocks, duration 00:07:22
    + 18: cells 18->18, 123780 blocks, duration 00:04:07
    + 19: cells 19->19, 239858 blocks, duration 00:08:13
    + 20: cells 20->20, 71613 blocks, duration 00:03:42
    + 21: cells 21->21, 5 blocks, duration 00:00:01
  + audio tracks:
    + 1, English (AC3) (5.1 ch) (iso639-2: eng), 48000Hz, 448000bps
    + 2, English (DTS) (5.1 ch) (iso639-2: eng), 48000Hz, 768000bps
    + 3, Francais (AC3) (5.1 ch) (iso639-2: fra), 48000Hz, 384000bps
    + 4, English (AC3) (Director's Commentary 1) (2.0 ch) (Dolby Surround) (iso639-2: eng), 48000Hz, 192000bps
  + subtitle tracks:
    + 1, English (iso639-2: eng) (Bitmap)(VOBSUB)
    + 2, Espanol (iso639-2: spa) (Bitmap)(VOBSUB)
    + 3, Francais (iso639-2: fra) (Bitmap)(VOBSUB)
+ Using preset: High Profile
[22:04:57] 1 job(s) to process
[22:04:57] starting job
[22:04:57] yadif thread started for segment 0
[22:04:57] yadif thread started for segment 1
[22:04:57] yadif thread started for segment 2
[22:04:57] yadif thread started for segment 3
[22:04:57] yadif thread started for segment 7
[22:04:57] yadif thread started for segment 5
[22:04:57] yadif thread started for segment 6
[22:04:57] decomb filter thread started for segment 5
[22:04:57] decomb filter thread started for segment 0
[22:04:57] decomb filter thread started for segment 1
[22:04:57] decomb check thread started for segment 4
[22:04:57] decomb check thread started for segment 7
[22:04:57] decomb filter thread started for segment 4
[22:04:57] mask filter thread started for segment 1
[22:04:57] decomb filter thread started for segment 6
[22:04:57] decomb filter thread started for segment 7
[22:04:57] mask filter thread started for segment 7
[22:04:57] decomb check thread started for segment 0
[22:04:57] mask erode thread started for segment 2
[22:04:57] decomb check thread started for segment 3
[22:04:57] mask erode thread started for segment 4
[22:04:57] mask erode thread started for segment 5
[22:04:57] mask erode thread started for segment 7
[22:04:57] decomb filter thread started for segment 3
[22:04:57] mask filter thread started for segment 0
[22:04:57] mask dilate thread started for segment 4
[22:04:57] mask dilate thread started for segment 5
[22:04:57] mask filter thread started for segment 3
[22:04:57] mask dilate thread started for segment 7
[22:04:57] mask filter thread started for segment 5
[22:04:57] mask filter thread started for segment 6
[22:04:57] decomb check thread started for segment 2
[22:04:57] mask erode thread started for segment 0
[22:04:57] mask erode thread started for segment 1
[22:04:57] decomb check thread started for segment 1
[22:04:57] mask erode thread started for segment 3
[22:04:57] decomb filter thread started for segment 2
[22:04:57] decomb check thread started for segment 5
[22:04:57] mask erode thread started for segment 6
[22:04:57] decomb check thread started for segment 6
[22:04:57] mask dilate thread started for segment 0
[22:04:57] mask dilate thread started for segment 1
[22:04:57] mask dilate thread started for segment 2
[22:04:57] mask dilate thread started for segment 3
[22:04:57] yadif thread started for segment 4
[22:04:57] mask filter thread started for segment 2
[22:04:57] mask dilate thread started for segment 6
[22:04:57] mask filter thread started for segment 4
[22:04:57] sync: expecting 154913 video frames
[22:04:57] job configuration:
[22:04:57]  * source
[22:04:57]    + /dev/sr0
[22:04:57]    + title 1, chapter(s) 1 to 21
[22:04:57]  * destination
[22:04:57]    + /home/doug//ETERNAL_SUNSHINE_OF_THE_SPOT.mkv
[22:04:57]    + container: Matroska (libavformat)
[22:04:57]      + chapter markers
[22:04:57]  * video track
[22:04:57]    + decoder: mpeg2video
[22:04:57]      + bitrate 9800 kbps
[22:04:57]    + filters
[22:04:57]      + Decomb (default settings)
[22:04:57]      + Framerate Shaper (0:27000000:1126125)
[22:04:57]        + frame rate: same as source (around 23.976 fps)
[22:04:57]      + Crop and Scale (720:460:6:14:0:0)
[22:04:57]        + source: 720 * 480, crop (6/14/0/0): 720 * 460, scale: 720 * 460
[22:04:57]    + loose anamorphic
[22:04:57]      + storage dimensions: 720 * 460, mod 2
[22:04:57]      + pixel aspect ratio: 32 / 27
[22:04:57]      + display dimensions: 853 * 460
[22:04:57]    + encoder: H.264 (libx264)
[22:04:57]      + preset:  medium
[22:04:57]      + profile: high
[22:04:57]      + level:   4.1
[22:04:57]      + quality: 20.00 (RF)
[22:04:57]  * audio track 1
[22:04:57]    + decoder: English (AC3) (5.1 ch) (track 1, id 0x80bd)
[22:04:57]      + bitrate: 448 kbps, samplerate: 48000 Hz
[22:04:57]    + mixdown: Dolby Pro Logic II
[22:04:57]    + encoder: AAC (libavcodec)
[22:04:57]      + bitrate: 160 kbps, samplerate: 48000 Hz
[22:04:57]  * audio track 2
[22:04:57]    + decoder: English (AC3) (5.1 ch) (track 1, id 0x80bd)
[22:04:57]      + bitrate: 448 kbps, samplerate: 48000 Hz
[22:04:57]    + AC3 Passthru
[22:04:57] dvd: Region mask 0xfe
libdvdnav: Using dvdnav version 5.0.0
libdvdnav: DVD Title: ETERNAL_SUNSHINE_OF_THE_SPOT
libdvdnav: DVD Serial Number: 30fc874a
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/doug/.dvdnav/ETERNAL_SUNSHINE_OF_THE_SPOT.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000153
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000079fb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00007c81
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0033149e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x003314a2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0034a2d2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0034a2d6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0037dcb3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0037dcb7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x003c3a94
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003c3a98
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003e1ce9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003e1ced
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003edd4f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003edd53
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003f0680
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003f0684
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x003f1e46
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x003f1e4a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x003f447f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x003f4483
libdvdread: Elapsed time 0
libdvdread: Found 10 VTS's
libdvdread: Elapsed time 0
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
[22:04:57] encx264: min-keyint: 24, keyint: 240
[22:04:57] encx264: encoding at constant RF 20.000000
[22:04:57] encx264: unparsed options: level=4.1:vbv-bufsize=78125:vbv-maxrate=62500
x264 [info]: using SAR=32/27
x264 [info]: using cpu capabilities: MMX2 SSE2Fast SSSE3 SSE4.2 AVX AVX2 FMA3 LZCNT BMI2
x264 [info]: profile High, level 4.1
[22:04:57] reader: first SCR 146 id 0xe0 DTS 22254
[22:04:57] mpeg2video: "Chapter 1" (1) at frame 0 time 3003
[22:04:57] sync: first pts is 3003
[22:04:57] 1.001000s: Video -> Film
[22:06:00] mpeg2video: "Chapter 2" (2) at frame 5334 time 20004484
ect., ect...

As far as website - they were using halvert to allow autorun of headless server. 
(- I assume you have no means to set an autorun on dvd insertion like here in a desktop install?

---

### Post by aaron50 on 2014-08-06
This is the website that I used to download handbrake since the original tutorial was not set up for 14.04. Here is the site I used [http://www.noobslab.com/2013/12/handbrake-video-converter-for.html?m=1](http://www.noobslab.com/2013/12/handbrake-video-converter-for.html?m=1)
```
Terminal Commands:
sudo add-apt-repository ppa:noobslab/apps
sudo apt-get update
sudo apt-get install handbrake-gtk handbrake-cli
``` 
But now I have downloaded the repository that was suggested on here, so I dont know how to take the noobslolab one off If I need to.

Can you tell me if I'm using the correct version of handbrake and what I need to do to make it work. Thank you again for all your help.

Edit: my end goal is the get it to authoring upon inserting the disk. I have researched many ways to do this, but I have to make the script work be for I can auto run it. How were you able to capture the whole output? I tried and it only let me go back so many lines. If I could capture it that may help you. I tried to video it, but the forum doesn't allow files that large to be uploaded.

---

### Post by dave131 on 2014-08-07
I think there may be a couple of steps to get back to a clean point before installing from the stebbins ppa:

(1) *IF* you have already added the stebbins ppa:

sudo apt-get purge handbrake-gtk handbrake-cli      (the handbrake-cli might not be found)
sudo add-apt-repository --remove ppa:whatever/ppa  (substitute the stebbins ppa in this line)

(2) Try again to clear the original ppa

sudo apt-get purge handbrake-gtk handbrake-cli  (these might not be found at all now and that's okay)

sudo add-apt-repository --remove ppa:noobslab/apps

(3) Now go back and add the stebbins ppa and install from there

I found the add-apt-repository --remove in another post so I hope it does work.

Also - I noticed that in your output you were getting messages about the region code - it may be that the defaulted region code doesn't allow actually processing the DVD.

Also - the screen capture of the red error lines also shows read errors on the media prior to those errors.

To dump the output to a file so you can review it, I *think* you could test by adding > somefilename  - I don't know for sure but it might put all the messages that would otherwise be echoed to the console in to that file instead.

---

### Post by aaron50 on 2014-08-07
Thank you dave. I have removed both repositories and handbrake like you said, the repositories removed with that line. Then I redownloaded the stebbins repository and handbrake gtk and cli. When I get home tonight I will run the script again and try to put something in it to record the output like you were suggesting.  I will let you know how it goes. Thanks

---

### Post by aaron50 on 2014-08-07
Well, I tried to re run the script and the same thing is happening. Runs, 5 sec later disc pops out and the log says the same thing and the "movie" is super small. I tried to put >some file name, in my script to capture the output! but I have no idea where to put it. Can you help me on where to put the notation to capture the output in a log. Thanks

---

### Post by mc4man on 2014-08-07
If you can just run a command then maybe try this, adjust blue as needed - 
```
HandBrakeCLI --input /dev/sr0 --preset="High Profile" --output 1.mkv 2>&1 |tee -a  [COLOR="#0000FF"]/path/to/hb.log[/COLOR]
```

That should log from the very start of hb_init:

---

### Post by aaron50 on 2014-08-07
I put your code in the command line and this is the entire output that i received, Thanks for the help.
```
[20:46:05] hb_init: starting libhb threadHandBrake svn6272 (2014080701) - Linux i686 - http://handbrake.fr
1 CPU detected
Opening /dev/sr0...
[20:46:05] CPU: AMD Turion(tm) 64 Mobile Technology ML-34
[20:46:05]  - logical processor count: 1
[20:46:05] OpenCL: library not available
[20:46:05] hb_scan: path=/dev/sr0, title_index=1
libbluray/bdnav/index_parse.c:162: indx_parse(): error opening /dev/sr0/BDMV/index.bdmv
libbluray/bdnav/index_parse.c:162: indx_parse(): error opening /dev/sr0/BDMV/BACKUP/index.bdmv
libbluray/bluray.c:2182: nav_get_title_list(/dev/sr0) failed
[20:46:05] bd: not a bd - trying as a stream/file instead
[20:46:05] dvd: Region mask 0xfe
libdvdnav: Using dvdnav version 5.0.0
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: BLUSBRO
libdvdnav: DVD Serial Number: 24F68086
libdvdnav: DVD Title (Alternative): BLUSBRO
libdvdnav: Unable to find map file '/home/amotto11/.dvdnav/BLUSBRO.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdread: Encrypted DVD support unavailable.
[20:46:08] scan: DVD has 10 title(s)
[20:46:08] scan: scanning title 1
[20:46:08] scan: opening IFO for VTS 1
[20:46:08] scan: duration is 02:27:36 (8856600 ms)
[20:46:08] pgc_id: 1, pgn: 1: pgc: 0xb5d16e80
[20:46:08] scan: vts=1, ttn=1, cells=0->61, blocks=0->2526925, 2526926 blocks
[20:46:08] scan: checking audio 1
[20:46:08] scan: id=0x80bd, lang=English (AC3), 3cc=eng ext=1
[20:46:08] scan: checking subtitle 1
[20:46:08] scan: id=0x23bd, lang=English (Closed Caption), 3cc=eng ext=5
[20:46:08] scan: checking subtitle 2
[20:46:08] scan: id=0x24bd, lang=Espanol, 3cc=spa ext=1
[20:46:08] scan: checking subtitle 3
[20:46:08] scan: id=0x25bd, lang=Francais, 3cc=fra ext=1
[20:46:08] scan: title 1 has 48 chapters
[20:46:08] scan: chap 1 c=0->0, b=0->126121 (126122), 477367 ms
[20:46:08] scan: chap 2 c=1->2, b=126122->182148 (56027), 156333 ms
[20:46:08] scan: chap 3 c=3->4, b=182149->249846 (67698), 287766 ms
[20:46:08] scan: chap 4 c=5->5, b=249847->268301 (18455), 84000 ms
[20:46:08] scan: chap 5 c=6->6, b=268302->308859 (40558), 148433 ms
[20:46:08] scan: chap 6 c=7->7, b=308860->353080 (44221), 107800 ms
[20:46:08] scan: chap 7 c=8->9, b=353081->410791 (57711), 171666 ms
[20:46:08] scan: chap 8 c=10->10, b=410792->432496 (21705), 80200 ms
[20:46:08] scan: chap 9 c=11->12, b=432497->491420 (58924), 233501 ms
[20:46:08] scan: chap 10 c=13->13, b=491421->554943 (63523), 175133 ms
[20:46:08] scan: chap 11 c=14->15, b=554944->667348 (112405), 439400 ms
[20:46:08] scan: chap 12 c=16->16, b=667349->717502 (50154), 168567 ms
[20:46:08] scan: chap 13 c=17->17, b=717503->741439 (23937), 83166 ms
[20:46:08] scan: chap 14 c=18->18, b=741440->792251 (50812), 163333 ms
[20:46:08] scan: chap 15 c=19->19, b=792252->836524 (44273), 174400 ms
[20:46:08] scan: chap 16 c=20->20, b=836525->923551 (87027), 331166 ms
[20:46:08] scan: chap 17 c=21->21, b=923552->971437 (47886), 143266 ms
[20:46:08] scan: chap 18 c=22->22, b=971438->1025244 (53807), 179767 ms
[20:46:08] scan: chap 19 c=23->23, b=1025245->1063753 (38509), 164133 ms
[20:46:08] scan: chap 20 c=24->24, b=1063754->1145615 (81862), 258300 ms
[20:46:08] scan: chap 21 c=25->25, b=1145616->1182147 (36532), 139333 ms
[20:46:08] scan: chap 22 c=26->27, b=1182148->1237326 (55179), 158667 ms
[20:46:08] scan: chap 23 c=28->28, b=1237327->1290115 (52789), 201500 ms
[20:46:08] scan: chap 24 c=29->30, b=1290116->1368875 (78760), 286500 ms
[20:46:08] scan: chap 25 c=31->31, b=1368876->1400859 (31984), 114633 ms
[20:46:08] scan: chap 26 c=32->32, b=1400860->1469003 (68144), 247834 ms
[20:46:08] scan: chap 27 c=33->33, b=1469004->1505348 (36345), 145533 ms
[20:46:08] scan: chap 28 c=34->34, b=1505349->1532072 (26724), 100967 ms
[20:46:08] scan: chap 29 c=35->35, b=1532073->1567704 (35632), 139767 ms
[20:46:08] scan: chap 30 c=36->36, b=1567705->1617147 (49443), 158867 ms
[20:46:08] scan: chap 31 c=37->38, b=1617148->1709003 (91856), 335633 ms
[20:46:08] scan: chap 32 c=39->40, b=1709004->1826071 (117068), 377067 ms
[20:46:08] scan: chap 33 c=41->42, b=1826072->1865529 (39458), 150233 ms
[20:46:08] scan: chap 34 c=43->44, b=1865530->1931316 (65787), 212866 ms
[20:46:08] scan: chap 35 c=45->45, b=1931317->1965881 (34565), 106300 ms
[20:46:08] scan: chap 36 c=46->46, b=1965882->1995992 (30111), 113300 ms
[20:46:08] scan: chap 37 c=47->47, b=1995993->2040821 (44829), 184200 ms
[20:46:08] scan: chap 38 c=48->48, b=2040822->2061298 (20477), 82834 ms
[20:46:08] scan: chap 39 c=49->49, b=2061299->2086758 (25460), 100166 ms
[20:46:08] scan: chap 40 c=50->50, b=2086759->2126175 (39417), 134800 ms
[20:46:08] scan: chap 41 c=51->52, b=2126176->2197870 (71695), 208500 ms
[20:46:08] scan: chap 42 c=53->53, b=2197871->2245450 (47580), 169867 ms
[20:46:08] scan: chap 43 c=54->55, b=2245451->2337817 (92367), 328567 ms
[20:46:08] scan: chap 44 c=56->56, b=2337818->2364576 (26759), 98200 ms
[20:46:08] scan: chap 45 c=57->57, b=2364577->2407821 (43245), 119166 ms
[20:46:08] scan: chap 46 c=58->58, b=2407822->2445917 (38096), 108433 ms
[20:46:08] scan: chap 47 c=59->60, b=2445918->2526920 (81003), 304699 ms
[20:46:08] scan: chap 48 c=61->61, b=2526921->2526925 (5), 500 ms
[20:46:08] scan: aspect = 1.77778
[20:46:08] scan: decoding previews for title 1
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!
[20:46:08] scan: title angle(s) 1
ERROR: dvdnav: Read Error, Error reading NAV packet.
[20:46:08] Warning: Could not read data for preview 1, skipped


Scanning title 1 of 1, preview 2, 20.00 %[ac3 @ 0xb5d4a300] frame sync error


Scanning title 1 of 1, preview 2, 20.00 %[ac3 @ 0xb5d49bc0] frame sync error
[ac3 @ 0xb5d49bc0] exponent out-of-range
[ac3 @ 0xb5d49bc0] error decoding the audio block
[20:46:08] scan: audio 0x80bd: ac3, rate=48000Hz, bitrate=448000 English (AC3) (5.1 ch)
[20:46:09] Broken timestamps detected.  Reordering.


Scanning title 1 of 1, preview 3, 30.00 %[20:46:09] Warning: Could not read data for preview 4, skipped
libdvdread: Can't seek to block 1169880
[20:46:09] Warning: Could not read data for preview 5, skipped
libdvdread: Can't seek to block 1170027
libdvdread: Can't seek to block 1170027
libdvdread: Can't seek to block 1170027
libdvdread: Can't seek to block 1170027
libdvdread: Can't seek to block 1170027
[20:46:09] scan: content PAR gives wrong aspect 1.78; using container aspect 1.78
[20:46:09] scan: 2 previews, 720x480, 29.970 fps, autocrop = 0/0/0/0, aspect 1.78:1, PAR 853:720
[20:46:09] libhb: scan thread found 1 valid title(s)
+ title 1:
  + vts 1, ttn 1, cells 0->61 (2526926 blocks)
  + duration: 02:27:36
  + size: 720x480, pixel aspect: 853/720, display aspect: 1.78, 29.970 fps
  + autocrop: 0/0/0/0
  + support opencl: no
  + support hwd: not built-in
  + chapters:
    + 1: cells 0->0, 126122 blocks, duration 00:07:57
    + 2: cells 1->2, 56027 blocks, duration 00:02:36
    + 3: cells 3->4, 67698 blocks, duration 00:04:48
    + 4: cells 5->5, 18455 blocks, duration 00:01:24
    + 5: cells 6->6, 40558 blocks, duration 00:02:28
    + 6: cells 7->7, 44221 blocks, duration 00:01:48
    + 7: cells 8->9, 57711 blocks, duration 00:02:52
    + 8: cells 10->10, 21705 blocks, duration 00:01:20
    + 9: cells 11->12, 58924 blocks, duration 00:03:54
    + 10: cells 13->13, 63523 blocks, duration 00:02:55
    + 11: cells 14->15, 112405 blocks, duration 00:07:19
    + 12: cells 16->16, 50154 blocks, duration 00:02:49
    + 13: cells 17->17, 23937 blocks, duration 00:01:23
    + 14: cells 18->18, 50812 blocks, duration 00:02:43
    + 15: cells 19->19, 44273 blocks, duration 00:02:54
    + 16: cells 20->20, 87027 blocks, duration 00:05:31
    + 17: cells 21->21, 47886 blocks, duration 00:02:23
    + 18: cells 22->22, 53807 blocks, duration 00:03:00
    + 19: cells 23->23, 38509 blocks, duration 00:02:44
    + 20: cells 24->24, 81862 blocks, duration 00:04:18
    + 21: cells 25->25, 36532 blocks, duration 00:02:19
    + 22: cells 26->27, 55179 blocks, duration 00:02:39
    + 23: cells 28->28, 52789 blocks, duration 00:03:22
    + 24: cells 29->30, 78760 blocks, duration 00:04:47
    + 25: cells 31->31, 31984 blocks, duration 00:01:55
    + 26: cells 32->32, 68144 blocks, duration 00:04:08
    + 27: cells 33->33, 36345 blocks, duration 00:02:26
    + 28: cells 34->34, 26724 blocks, duration 00:01:41
    + 29: cells 35->35, 35632 blocks, duration 00:02:20
    + 30: cells 36->36, 49443 blocks, duration 00:02:39
    + 31: cells 37->38, 91856 blocks, duration 00:05:36
    + 32: cells 39->40, 117068 blocks, duration 00:06:17
    + 33: cells 41->42, 39458 blocks, duration 00:02:30
    + 34: cells 43->44, 65787 blocks, duration 00:03:33
    + 35: cells 45->45, 34565 blocks, duration 00:01:46
    + 36: cells 46->46, 30111 blocks, duration 00:01:53
    + 37: cells 47->47, 44829 blocks, duration 00:03:04
    + 38: cells 48->48, 20477 blocks, duration 00:01:23
    + 39: cells 49->49, 25460 blocks, duration 00:01:40
    + 40: cells 50->50, 39417 blocks, duration 00:02:15
    + 41: cells 51->52, 71695 blocks, duration 00:03:29
    + 42: cells 53->53, 47580 blocks, duration 00:02:50
    + 43: cells 54->55, 92367 blocks, duration 00:05:29
    + 44: cells 56->56, 26759 blocks, duration 00:01:38
    + 45: cells 57->57, 43245 blocks, duration 00:01:59
    + 46: cells 58->58, 38096 blocks, duration 00:01:48
    + 47: cells 59->60, 81003 blocks, duration 00:05:05
    + 48: cells 61->61, 5 blocks, duration 00:00:01
  + audio tracks:
    + 1, English (AC3) (5.1 ch) (iso639-2: eng), 48000Hz, 448000bps
  + subtitle tracks:
    + 1, English (Closed Caption) (iso639-2: eng) (Bitmap)(VOBSUB)
    + 2, Espanol (iso639-2: spa) (Bitmap)(VOBSUB)
    + 3, Francais (iso639-2: fra) (Bitmap)(VOBSUB)
+ Using preset: High Profile
[20:46:09] 1 job(s) to process
[20:46:09] starting job
[20:46:09] sync: expecting 265433 video frames
[20:46:09] decomb check thread started for segment 0
[20:46:09] mask filter thread started for segment 0
[20:46:09] decomb filter thread started for segment 0
[20:46:09] mask erode thread started for segment 0
[20:46:09] mask dilate thread started for segment 0
[20:46:09] yadif thread started for segment 0
[20:46:09] job configuration:
[20:46:09]  * source
[20:46:09]    + /dev/sr0
[20:46:09]    + title 1, chapter(s) 1 to 48
[20:46:09]  * destination
[20:46:09]    + 1.mkv
[20:46:09]    + container: Matroska (libavformat)
[20:46:09]      + chapter markers
[20:46:09]  * video track
[20:46:09]    + decoder: mpeg2video
[20:46:09]      + bitrate 9800 kbps
[20:46:09]    + filters
[20:46:09]      + Decomb (default settings)
[20:46:09]      + Framerate Shaper (0:27000000:900900)
[20:46:09]        + frame rate: same as source (around 29.970 fps)
[20:46:09]      + Crop and Scale (720:480:0:0:0:0)
[20:46:09]        + source: 720 * 480, crop (0/0/0/0): 720 * 480, scale: 720 * 480
[20:46:09]    + loose anamorphic
[20:46:09]      + storage dimensions: 720 * 480, mod 2
[20:46:09]      + pixel aspect ratio: 853 / 720
[20:46:09]      + display dimensions: 853 * 480
[20:46:09]    + encoder: H.264 (libx264)
[20:46:09]      + preset:  medium
[20:46:09]      + profile: high
[20:46:09]      + level:   4.1
[20:46:09]      + quality: 20.00 (RF)
[20:46:09]  * audio track 1
[20:46:09]    + decoder: English (AC3) (5.1 ch) (track 1, id 0x80bd)
[20:46:09]      + bitrate: 448 kbps, samplerate: 48000 Hz
[20:46:09]    + mixdown: Dolby Pro Logic II
[20:46:09]    + encoder: AAC (libavcodec)
[20:46:09]      + bitrate: 160 kbps, samplerate: 48000 Hz
[20:46:09]  * audio track 2
[20:46:09]    + decoder: English (AC3) (5.1 ch) (track 1, id 0x80bd)
[20:46:09]      + bitrate: 448 kbps, samplerate: 48000 Hz
[20:46:09]    + AC3 Passthru
[20:46:09] dvd: Region mask 0xfe
libdvdnav: Using dvdnav version 5.0.0
libdvdread: Encrypted DVD support unavailable.


Encoding: task 1 of 1, 0.00 %libdvdnav: DVD Title: BLUSBRO
libdvdnav: DVD Serial Number: 24F68086
libdvdnav: DVD Title (Alternative): BLUSBRO
libdvdnav: Unable to find map file '/home/amotto11/.dvdnav/BLUSBRO.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Suspected RCE Region Protection!!!


Encoding: task 1 of 1, 0.00 %[20:46:10] encx264: min-keyint: 30, keyint: 300
[20:46:10] encx264: encoding at constant RF 20.000000
[20:46:10] encx264: unparsed options: level=4.1:vbv-bufsize=78125:vbv-maxrate=62500
x264 [info]: using SAR=853/720
x264 [info]: using cpu capabilities: MMX2 SSE2Slow SlowCTZ
x264 [info]: profile High, level 4.1
libdvdnav: Suspected RCE Region Protection!!!
[20:46:10] reader: first SCR 146 id 0xe0 DTS 13915
ERROR: dvdnav: Read Error, Error reading NAV packet.
ERROR: Last error repeated 6 times
ERROR: dvdnav: Read Error, Error reading from DVD.
[20:46:10] reader: done. 1 scr changes


Encoding: task 1 of 1, 0.00 %[20:46:10] mpeg2video: "Chapter 1" (1) at frame 0 time 3003
[20:46:10] work: average encoding speed for job is 0.000000 fps
[20:46:10] sync: got 1 frames, 265433 expected
[20:46:10] decomb: deinterlaced 0 | blended 0 | unfiltered 0 | total 0
[20:46:10] render: lost time: 0 (0 frames)
[20:46:10] render: gained time: 0 (0 frames) (0 not accounted for)
[20:46:10] mpeg2video-decoder done: 1 frames, 0 decoder errors, 0 drops
[20:46:10] ac3-decoder done: 0 frames, 0 decoder errors, 0 drops
[20:46:10] ac3-decoder done: 0 frames, 0 decoder errors, 0 drops
[20:46:10] mux: track 0, 0 frames, 0 bytes, 0.00 kbps, fifo 8
[20:46:10] mux: track 1, 0 frames, 0 bytes, 0.00 kbps, fifo 8
[20:46:10] mux: track 2, 0 frames, 0 bytes, 0.00 kbps, fifo 8


Muxing: this may take awhile...[20:46:10] libhb: work result = 0


Encode done!
HandBrake has exited.

```

---

### Post by mc4man on 2014-08-08
> libdvdread: Encrypted DVD support unavailable
run this -  (assumes libdvdread4 is installed which it appears to be
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
That will install libdvdcss2 which is needed for access & decrypting css

Edit: you likely don't need/want to run your dvd ripping script as root.

---

### Post by dave131 on 2014-08-08
I'm curious to see how this all works out - I have a Raspberry Pi I'm using as a media center, but I want to move that over to an Ubuntu based headless server (*if* I can find stuff for a complete novice to get going with a server).  Having a script like this would allow me to rip DVD's with no intervention other than putting the DVD in the drive.  This would be great for me.

I wondered about the css stuff myself - would this also cause the errors kicking out about the region code of the DVD? (perhaps those errors aren't fatal?)

---

### Post by mc4man on 2014-08-08
> **dave131 said:**
> 
I wondered about the css stuff myself - would this also cause the errors kicking out about the region code of the DVD? (perhaps those errors aren't fatal?)
There could be some discs that have issue when there is no region set on a drive so it should be set *once*. 
Unlicensed players/apps don't enforce region coding so for example  having a drive set to region 1 won't prevent accessing a disc that's another region.
(the exception there is most Matshita laptop drives which do enforce region coding.

---

### Post by dave131 on 2014-08-08
Thank you.  I'll move back to the sidelines and observe some more now.

---

### Post by aaron50 on 2014-08-08
Well, I have an update. I ran your suggestion then updated ubuntu, then upgraded. I then ran the script and it looks to be running successfully. As you could tell this is a 1 core laptop, so not much power. It looks like it is ripping chapter 3 now and it has been about 40 minutes. When the script finishes I will let you know if it worked and how the quality is.

Dave, if I can create a headless server then I am sure you can. Give it a try! I have set mine up with samba, ps3mediaserver, and hopefully the ripping capability. My next tackle after this is to get xbmc to run headless. In the end I hope to have a really nice headless home server that can act like a personal cloud outside the house as well, then go and mimic the same thing on a machine I build that is much more powerful.

---

### Post by dave131 on 2014-08-09
When this is indeed all working for you, would you mind:

- posting back the final version of the script
- posting back what steps where needed to set it up - location, permissions, where in what system folder/file to get this to "auto-run" when a DVD is inserted, etc.

I would greatly appreciate that so I can try to do the same thing, and once that works I can keep it for when I do my server.

You are doing exactly what I want to:  a headless server to be used for local storage (in my case, an "in-house" cloud), used as a media server as well - with XBMC.

---

### Post by aaron50 on 2014-08-09
It worked, streams perfectly from my old laptop. I can even skip to any part of the movie with no lag!! Took a long time to download, but there were 48 chapters in that movie. I can't work on it this weekend, but I would like to know if what i have is the best quality i can get. It looks great now and sounds great, but i was wondering if there is even better. Space is not an issue, so if you know of anything that would be great. Also does it only use mkv as the output or is this something i can configure? Thanks for all the help!!

Dave, i will not be able to work on it this weekend, but i will definitely post my scripts late Sunday night. Thanks to everyone once again!! I can also give you helpful links to tutorials about samba and PS3 mediaserver to get you a start on your server.

---

### Post by aaron50 on 2014-08-11
Dave,

Here is my code as it sits right now. Like i said it might change if i can find a better quality or something to that matter. I also will probably not keep creating a log file as well.

```
amotto11@LaptopMediaServer:/usr/bin$ sudo vi /usr/bin/ripdvd.sh#!/bin/bash


# Acknowledge that we are starting
beep -f 1400 -l 250


DVD="$1"
HANDBRAKE=HandBrakeCLI
LOG="logger -p daemon.info -t ripdvd.sh --"


#Change this to reflect where you store your dvd rips
OUTDIR="/home/amotto11/media/movies/"


function beep_success () {
        beep -f 750 -l 80 -r 5 -D 20
}


function beep_failure () {
        beep -f 200 -l 900
}


function dvdrip () {
        $LOG "Beginning rip of $DVD"
        local LABEL=`file -s "$DVD" | cut -f 2- -d "'" | cut -f 1 -d "'" | sed -e's/ *$//'`
        $LOG "$DVD contains $LABEL"
        $LOG $HANDBRAKE --verbose 9 --input "$DVD" --output "$OUTDIR/$LABEL.mkv"
        $HANDBRAKE --verbose 9 --input "$DVD" --output "$OUTDIR/$LABEL.mkv" --preset="High Profile" 2>&1 > $OUTDIR/HandBrake.log
        local STATUS="$?"
        $LOG "Finished importing $LABEL from $DVD (status = $STATUS)"
        return $STATUS
}


if dvdrip; then
        beep_success
else
        beep_failure
fi


eject



```

---

### Post by dave131 on 2014-08-19
Thank you VERY much!!   It is greatly appreciated!

---

### Post by aaron50 on 2014-08-20
I can post everything I did if you would like? it may be hard to follow from the forum. Let me know

---

