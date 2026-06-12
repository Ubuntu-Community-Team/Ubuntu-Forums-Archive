---
title: "Problems ripping CD audio file"
date: 2010-01-30
forum: Multimedia Software
---

### Post by Crimson_Tider on 2010-01-30
I am trying to rip an audio CD file to my mp3 player as an mp3. I have tried several different application, but they all have problems identifying my CD-RW drive and identifying the track on the CD-ROM. Sound Juicer, which was my first app to try, doesn't seem to think that there is any disc in the drive. Another, abcde, gives me the following feedback:

```
*******@*******:~$ abcde
[ERROR] abcde: CDROM has not been defined or cannot be found

```

and then when I actually specified the path and name of the CD-RW device:

```
*******@*******:~$ abcde -d /dev/cdrom1 -o mp3
Executing customizable pre-read function... done.
Getting CD track info... Querying the CD for audio tracks...
[WARNING] something went wrong while querying the CD... Maybe a DATA CD?
[INFO] The disc does not contain any tracks. Giving up...

```

Can anyone help?

By the way, I am still an Ubuntu/Linux beginner; please speak at my level. Thanks!

---

### Post by andrew.46 on 2010-01-31
Hi Crimson_Tider,

Perhaps you could add in the option to produce debug output? I am not completely sure if this will be terribly useful but hopefully :). Something like:

```
abcde -d /dev/cdrom1 -o mp3 -D 2>$HOME/Desktop/abcde_debug
```

should leave a debug file on your Desktop.

Andrew

---

### Post by Crimson_Tider on 2010-01-31
Okay; I have a debug file. I'm not sure what it's telling me for the most part, but one thing I did notice that sounds relevant is

```
Verifying CDDA command set...
	Could not find any audio tracks on this disk.
```

---

### Post by andrew.46 on 2010-01-31
Hi Crimson_Tider,

Could you post the full log?

Thanks,

Andrew

---

### Post by Crimson_Tider on 2010-01-31
That would help, wouldn't it?  I really shoulda thought to do that!

```
+ getopts 1a:bBc:C:d:Defghj:klLmMnNo:pPr:s:S:t:T:UvVxX:w:W:z opt
+ shift 5
+ '[' n = y ']'
+ echo /dev/cdrom1
+ grep -i '.flac$'
+ '[' -n '' ']'
+ '[' cdparanoia = flac ']'
+ '[' cdparanoia = '' ']'
+ '[' '' = y ']'
+ '[' 0 -gt 0 ']'
+ DOCDDB=n
+ DOREAD=n
+ DONORMALIZE=n
+ DOPREPROCESS=n
+ DOENCODE=n
+ DOPOSTPROCESS=n
+ DOTAG=n
+ DOMOVE=n
+ DOREPLAYGAIN=n
+ DOPLAYLIST=n
+ DOCLEAN=n
+ '[' '' '!=' y ']'
+ DOCUE=n
++ echo cddb,read,encode,tag,move,clean
++ tr , ' '
+ for ACTION in '$(echo $ACTIONS | tr , \ )'
+ case $ACTION in
+ DOCDDB=y
+ for ACTION in '$(echo $ACTIONS | tr , \ )'
+ case $ACTION in
+ DOREAD=y
+ for ACTION in '$(echo $ACTIONS | tr , \ )'
+ case $ACTION in
+ DOENCODE=y
+ DOREAD=y
+ for ACTION in '$(echo $ACTIONS | tr , \ )'
+ case $ACTION in
+ DOTAG=y
+ DOREAD=y
+ DOENCODE=y
+ DOCDDB=y
+ for ACTION in '$(echo $ACTIONS | tr , \ )'
+ case $ACTION in
+ DOMOVE=y
+ DOTAG=y
+ DOREAD=y
+ DOENCODE=y
+ DOCDDB=y
+ for ACTION in '$(echo $ACTIONS | tr , \ )'
+ case $ACTION in
+ DOCLEAN=y
+ '[' n = y ']'
++ echo year,genre
++ tr , ' '
+ for SHOWCDDBFIELD in '$(echo $SHOWCDDBFIELDS | tr , \ )'
+ case $SHOWCDDBFIELD in
+ SHOWCDDBYEAR=y
+ for SHOWCDDBFIELD in '$(echo $SHOWCDDBFIELDS | tr , \ )'
+ case $SHOWCDDBFIELD in
+ SHOWCDDBGENRE=y
+ '[' X/dev/cdrom1 '!=' X ']'
+ '[' cdparanoia = cdda2wav ']'
+ '[' '!' -e /dev/cdrom1 -a Xy = Xy ']'
+ '[' X = Xy ']'
+ '[' X = Xy ']'
+ '[' n = y ']'
+ '[' Xmp3 = X ']'
+ case "$CDROMREADERSYNTAX" in
+ CDROMREADER=cdparanoia
+ CDROMREADEROPTS=--never-skip=40
+ case "$NORMALIZERSYNTAX" in
+ NORMALIZER=normalize-audio
+ NORMALIZEROPTS=
+ echo mp3
+ grep :
++ echo mp3
++ tr , ' '
+ for OUTPUT in '$(echo $OUTPUTTYPE | tr , \ )'
+ case $OUTPUT in
+ '[' lame = default ']'
+ '[' y = y ']'
+ NEEDTAGGER=y
+ '[' n = y ']'
+ case "$MP3ENCODERSYNTAX" in
+ MP3ENCODEROPTS='--preset extreme'
+ MP3ENCODER=lame
+ case "$OGGENCODERSYNTAX" in
+ case "$FLACENCODERSYNTAX" in
+ case "$SPEEXENCODERSYNTAX" in
+ case "$MPPENCODERSYNTAX" in
+ case "$AACENCODERSYNTAX" in
+ '[' 2 = 1 ']'
+ TAGGER=id3v2
+ TAGGEROPTS=
+ '[' n = y ']'
+ case "$CUEREADERSYNTAX" in
+ CUEREADEROPTS=/dev/cdrom1
+ CUEREADER=mkcue
+ case "$CDDBTOOL" in
+ '[' X = Xogg ']'
+ '[' 10 ']'
+ ENCNICE='-n 10'
+ '[' 10 ']'
+ READNICE='-n 10'
+ '[' 10 ']'
+ DISTMP3NICE='-n 10'
+ '[' '' ']'
+ '[' n = y ']'
+ '[' y = y ']'
+ NEEDEJECT=y
+ '[' '!' y = n ']'
+ '[' y = y ']'
+ '[' cddb = cddb ']'
+ NEEDHTTPGET=y
+ '[' n = y ']'
+ '[' X '!=' X ']'
+ PIPERIPPER_cdparanoia=-
+ PIPERIPPER_debug=-
+ PIPERIPPER_flac='-c '
+ PIPE_lame=-
+ PIPE_bladeenc=-
+ PIPE_oggenc=-
+ PIPE_flac=-
+ '[' '' = y ']'
+ for X in '$CDROMREADER' '$CDDISCID' '${NEEDTAGGER+$TAGGER}' '$MP3ENCODER' '$OGGENCODER' '$FLACENCODER' '$SPEEXENCODER' '$MPPENCODER' '$AACENCODER' '${NEEDATOMICPARSLEY+$ATOMICPARSLEY}' '${NEEDHTTPGET+$HTTPGET}' '${NEEDDISTMP3+$DISTMP3}' '${NEEDCOMMENTER+$VORBISCOMMENT}' '${NEEDMETAFLAC+$METAFLAC}' '${NEEDNORMALIZER+$NORMALIZER}' '${NEEDEJECT+$EJECT}' '${NEEDDISKTOOL+disktool}' '${NEEDCDSPEED+$CDSPEED}' '${NEEDVORBISGAIN+$VORBISGAIN}' '${NEEDMP3GAIN+$MP3GAIN}' '${NEEDMPPGAIN+$MPPGAIN}' '${NEEDCUEREADER+$CUEREADER}' '${NEEDCUE2DISCID+$CUE2DISCID}'
+ checkexec cdparanoia
+ '[' '!' cdparanoia = '' ']'
++ cut '-d ' -f2
++ echo cdparanoia
+ X=cdparanoia
+ '[' cdparanoia '!=' cdparanoia ']'
++ which cdparanoia
+ '[' /usr/bin/cdparanoia = '' ']'
++ which cdparanoia
+ '[' '!' -x /usr/bin/cdparanoia ']'
+ for X in '$CDROMREADER' '$CDDISCID' '${NEEDTAGGER+$TAGGER}' '$MP3ENCODER' '$OGGENCODER' '$FLACENCODER' '$SPEEXENCODER' '$MPPENCODER' '$AACENCODER' '${NEEDATOMICPARSLEY+$ATOMICPARSLEY}' '${NEEDHTTPGET+$HTTPGET}' '${NEEDDISTMP3+$DISTMP3}' '${NEEDCOMMENTER+$VORBISCOMMENT}' '${NEEDMETAFLAC+$METAFLAC}' '${NEEDNORMALIZER+$NORMALIZER}' '${NEEDEJECT+$EJECT}' '${NEEDDISKTOOL+disktool}' '${NEEDCDSPEED+$CDSPEED}' '${NEEDVORBISGAIN+$VORBISGAIN}' '${NEEDMP3GAIN+$MP3GAIN}' '${NEEDMPPGAIN+$MPPGAIN}' '${NEEDCUEREADER+$CUEREADER}' '${NEEDCUE2DISCID+$CUE2DISCID}'
+ checkexec cd-discid
+ '[' '!' cd-discid = '' ']'
++ echo cd-discid
++ cut '-d ' -f2
+ X=cd-discid
+ '[' cd-discid '!=' cd-discid ']'
++ which cd-discid
+ '[' /usr/bin/cd-discid = '' ']'
++ which cd-discid
+ '[' '!' -x /usr/bin/cd-discid ']'
+ for X in '$CDROMREADER' '$CDDISCID' '${NEEDTAGGER+$TAGGER}' '$MP3ENCODER' '$OGGENCODER' '$FLACENCODER' '$SPEEXENCODER' '$MPPENCODER' '$AACENCODER' '${NEEDATOMICPARSLEY+$ATOMICPARSLEY}' '${NEEDHTTPGET+$HTTPGET}' '${NEEDDISTMP3+$DISTMP3}' '${NEEDCOMMENTER+$VORBISCOMMENT}' '${NEEDMETAFLAC+$METAFLAC}' '${NEEDNORMALIZER+$NORMALIZER}' '${NEEDEJECT+$EJECT}' '${NEEDDISKTOOL+disktool}' '${NEEDCDSPEED+$CDSPEED}' '${NEEDVORBISGAIN+$VORBISGAIN}' '${NEEDMP3GAIN+$MP3GAIN}' '${NEEDMPPGAIN+$MPPGAIN}' '${NEEDCUEREADER+$CUEREADER}' '${NEEDCUE2DISCID+$CUE2DISCID}'
+ checkexec id3v2
+ '[' '!' id3v2 = '' ']'
++ echo id3v2
++ cut '-d ' -f2
+ X=id3v2
+ '[' id3v2 '!=' id3v2 ']'
++ which id3v2
+ '[' /usr/bin/id3v2 = '' ']'
++ which id3v2
+ '[' '!' -x /usr/bin/id3v2 ']'
+ for X in '$CDROMREADER' '$CDDISCID' '${NEEDTAGGER+$TAGGER}' '$MP3ENCODER' '$OGGENCODER' '$FLACENCODER' '$SPEEXENCODER' '$MPPENCODER' '$AACENCODER' '${NEEDATOMICPARSLEY+$ATOMICPARSLEY}' '${NEEDHTTPGET+$HTTPGET}' '${NEEDDISTMP3+$DISTMP3}' '${NEEDCOMMENTER+$VORBISCOMMENT}' '${NEEDMETAFLAC+$METAFLAC}' '${NEEDNORMALIZER+$NORMALIZER}' '${NEEDEJECT+$EJECT}' '${NEEDDISKTOOL+disktool}' '${NEEDCDSPEED+$CDSPEED}' '${NEEDVORBISGAIN+$VORBISGAIN}' '${NEEDMP3GAIN+$MP3GAIN}' '${NEEDMPPGAIN+$MPPGAIN}' '${NEEDCUEREADER+$CUEREADER}' '${NEEDCUE2DISCID+$CUE2DISCID}'
+ checkexec lame
+ '[' '!' lame = '' ']'
++ echo lame
++ cut '-d ' -f2
+ X=lame
+ '[' lame '!=' lame ']'
++ which lame
+ '[' /usr/bin/lame = '' ']'
++ which lame
+ '[' '!' -x /usr/bin/lame ']'
+ for X in '$CDROMREADER' '$CDDISCID' '${NEEDTAGGER+$TAGGER}' '$MP3ENCODER' '$OGGENCODER' '$FLACENCODER' '$SPEEXENCODER' '$MPPENCODER' '$AACENCODER' '${NEEDATOMICPARSLEY+$ATOMICPARSLEY}' '${NEEDHTTPGET+$HTTPGET}' '${NEEDDISTMP3+$DISTMP3}' '${NEEDCOMMENTER+$VORBISCOMMENT}' '${NEEDMETAFLAC+$METAFLAC}' '${NEEDNORMALIZER+$NORMALIZER}' '${NEEDEJECT+$EJECT}' '${NEEDDISKTOOL+disktool}' '${NEEDCDSPEED+$CDSPEED}' '${NEEDVORBISGAIN+$VORBISGAIN}' '${NEEDMP3GAIN+$MP3GAIN}' '${NEEDMPPGAIN+$MPPGAIN}' '${NEEDCUEREADER+$CUEREADER}' '${NEEDCUE2DISCID+$CUE2DISCID}'
+ checkexec wget
+ '[' '!' wget = '' ']'
++ echo wget
++ cut '-d ' -f2
+ X=wget
+ '[' wget '!=' wget ']'
++ which wget
+ '[' /usr/bin/wget = '' ']'
++ which wget
+ '[' '!' -x /usr/bin/wget ']'
+ for X in '$CDROMREADER' '$CDDISCID' '${NEEDTAGGER+$TAGGER}' '$MP3ENCODER' '$OGGENCODER' '$FLACENCODER' '$SPEEXENCODER' '$MPPENCODER' '$AACENCODER' '${NEEDATOMICPARSLEY+$ATOMICPARSLEY}' '${NEEDHTTPGET+$HTTPGET}' '${NEEDDISTMP3+$DISTMP3}' '${NEEDCOMMENTER+$VORBISCOMMENT}' '${NEEDMETAFLAC+$METAFLAC}' '${NEEDNORMALIZER+$NORMALIZER}' '${NEEDEJECT+$EJECT}' '${NEEDDISKTOOL+disktool}' '${NEEDCDSPEED+$CDSPEED}' '${NEEDVORBISGAIN+$VORBISGAIN}' '${NEEDMP3GAIN+$MP3GAIN}' '${NEEDMPPGAIN+$MPPGAIN}' '${NEEDCUEREADER+$CUEREADER}' '${NEEDCUE2DISCID+$CUE2DISCID}'
+ checkexec eject
+ '[' '!' eject = '' ']'
++ echo eject
++ cut '-d ' -f2
+ X=eject
+ '[' eject '!=' eject ']'
++ which eject
+ '[' /usr/bin/eject = '' ']'
++ which eject
+ '[' '!' -x /usr/bin/eject ']'
+ '[' '' = y ']'
++ which diff
+ '[' -x /usr/bin/diff ']'
+ :
+ CDROMREADER='cdparanoia --never-skip=40'
+ CDDBTOOL='cddb-tool '
+ HTTPGET='wget -q -nv -e timestamping=off -O -'
+ export CDDBTOOL ABCDETEMPDIR TRACKQUEUE LOWDISK EJECTCD EJECT EJECTOPTS
+ export CDROM CDDBDATA REMOTEHOSTS MAXPROCS HTTPGET MD5SUM
+ '[' y = y ']'
+ vecho -n 'Executing customizable pre-read function... '
+ '[' xy '!=' x ']'
+ case $1 in
+ echo -n 'Executing customizable pre-read function... '
+ pre_read
+ :
+ vecho done.
+ '[' xy '!=' x ']'
+ case $1 in
+ echo done.
+ case "$CDDBMETHOD" in
+ do_discid
+ '[' -z '' ']'
+ vecho -n 'Getting CD track info... '
+ '[' xy '!=' x ']'
+ case $1 in
+ echo -n 'Getting CD track info... '
+ '[' '' = OSX ']'
+ case "$CDROMREADERSYNTAX" in
+ case "$CDDBMETHOD" in
++ cd-discid /dev/cdrom1
+ TRACKINFO='02000801 1 150 10'
+ '[' '!' 0 = 0 ']'
+ '[' '' = OSX ']'
+ WEHAVEACD=y
++ echo 02000801 1 150 10
++ cut -f1 '-d '
+ DISCID=02000801
+ '[' y = y ']'
+ TRACKNUMPADDING=2
++ echo 02000801 1 150 10
++ cut -f1 '-d '
+ ABCDETEMPDIR=/home/[My username]/abcde.02000801
+ '[' -z '' ']'
+ '[' '!' '' = n ']'
+ case "$CDROMREADERSYNTAX" in
+ '[' y = y ']'
+ vecho 'Querying the CD for audio tracks...'
+ '[' xy '!=' x ']'
+ case $1 in
+ echo 'Querying the CD for audio tracks...'
++ cdparanoia --never-skip=40 -d /dev/cdrom1 -Q --verbose
+ CDPARANOIAOUTPUT='cdparanoia III release 10.2 (September 11, 2008)

Using cdda library version: 10.2
Using paranoia library version: 10.2
Checking /dev/cdrom1 for cdrom...
	Testing /dev/cdrom1 for SCSI/MMC interface
		SG_IO device: /dev/sr0

CDROM model sensed sensed:  WSM-52Z 1.10 

Checking for SCSI emulation...
	Drive is ATAPI (using SG_IO host adaptor emulation)

Checking for MMC style command set...
	Drive is MMC style
	DMA scatter/gather table entries: 1
	table entry size: 131072 bytes
	maximum theoretical transfer: 55 sectors
	Setting default read size to 27 sectors (63504 bytes).

Verifying CDDA command set...
	Could not find any audio tracks on this disk.

Unable to open disc.'
+ RET=1
+ '[' '!' 1 = 0 ']'
+ log warning 'something went wrong while querying the CD... Maybe a DATA CD?'
+ BLURB=warning
+ shift
+ case $BLURB in
+ echo '[WARNING] something went wrong while querying the CD... Maybe a DATA CD?'
[WARNING] something went wrong while querying the CD... Maybe a DATA CD?
++ echo 'cdparanoia III release 10.2 (September 11, 2008)

Using cdda library version: 10.2
Using paranoia library version: 10.2
Checking /dev/cdrom1 for cdrom...
	Testing /dev/cdrom1 for SCSI/MMC interface
		SG_IO device: /dev/sr0

CDROM model sensed sensed:  WSM-52Z 1.10 

Checking for SCSI emulation...
	Drive is ATAPI (using SG_IO host adaptor emulation)

Checking for MMC style command set...
	Drive is MMC style
	DMA scatter/gather table entries: 1
	table entry size: 131072 bytes
	maximum theoretical transfer: 55 sectors
	Setting default read size to 27 sectors (63504 bytes).

Verifying CDDA command set...
	Could not find any audio tracks on this disk.

Unable to open disc.'
++ egrep '^[[:space:]]+[[:digit:]]'
++ tail -n 1
++ get_first
++ '[' X = X ']'
+++ cat
++ tr -d .
++ echo
++ tr '\n' ' '
+ TRACKS=' '
+ CDPARANOIAAUDIOTRACKS=' '
+ echo ' '
+ grep '[[:digit:]]'
+ log info 'The disc does not contain any tracks. Giving up...'
+ BLURB=info
+ shift
+ case $BLURB in
+ echo '[INFO] The disc does not contain any tracks. Giving up...'
+ exit 0
```

---

### Post by jomo56 on 2010-01-31
This might work.Rip the cd using Grip,convert the file into a mp3 file using soundkonverter then try to load it onto your mp3 player.

---

### Post by SuperSonic4 on 2010-01-31
do you have more than one cd drive?

---

### Post by sports.car.guy on 2010-01-31
DRM on newer CD's causes computer mp3 ripping software to come back stating no audio tracks are present.

I am betting most likely that is what you are encountering more then hardware issues.

---

### Post by andrew.46 on 2010-01-31
Hi Crimson_Tider,

I suspect you have a configuration file in place as well in HOME/.abcde.conf? I thought I recognised some of [my own settings]("http://www.andrews-corner.org/abcde.html") in there :). The problem appears to be with cdparanoia, does this work on its own? The following command should move you to your Desktop and extract the cd contents to wav files, a single file per track:

```

cd $HOME/Desktop
cdparanoia -B

```

If this fails try both of the following:

```

cd $HOME/Desktop
cdparanoia -B -d /dev/cdrom1 
cdparanoia -B -g /dev/cdrom1 

```

It would be unlikely that the -g option should work... As a final effort try simply running abcde using *sudo*, this has been mentioned as possible fix on[ a Slackware site]("http://slackbuilds.org/repository/13.0/audio/abcde/").

All the best,

Andrew

---

