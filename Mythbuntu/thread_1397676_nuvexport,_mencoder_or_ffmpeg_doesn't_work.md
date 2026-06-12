---
title: "nuvexport, mencoder or ffmpeg doesn't work"
date: 2010-02-03
forum: Mythbuntu
---

### Post by Darklighter on 2010-02-03
Hi folks,
This is my first post.
I have:
P4 with 1Gig of RAM. Two HD 30Gig with Hauppauge WinTV-HVR-1600 on a Mythbuntu 9.10.

My goal is only record tv show and convert in a different fromat like xvid to be able to watch with something else.

I try and try, read different post and no luck.
Try this one:
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)
and this
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

I always have the same problem. 
With nuvexport-xvid, after two minutes, this is the error[INDENT]ffmpeg died early.Please use the --debug option to figure out what went wrong.
[http://www.mythtv.org/wiki/index.php/Nuvexport#Debug_Mode](http://www.mythtv.org/wiki/index.php/Nuvexport#Debug_Mode)
[/INDENT]I try --debug and this is the error:[INDENT]system call:
mkdir -m 0755 /tmp/fifodir_3054/

forking:
/usr/bin/nice -n19 /usr/bin/mythtranscode --showprogress -p '0' -c '2004' -s '2010-01-27T21:00:00' -f "/tmp/fifodir_3054/" --honorcutlist --fifosync 2>&1

forking:
cat /tmp/fifodir_3054/audout > /dev/null

forking:
/usr/bin/nice -n19 ffmpeg -y -f s16le -ar  -ac  -f rawvideo -pix_fmt yuv420p -s 480x480 -aspect 1.33333333333333 -r 29.970 -i /tmp/fifodir_3054/vidout -aspect 1.33333333333333 -r 29.970 -deinterlace -croptop    6 -cropright 6 -cropbottom 6 -cropleft  6 -s 512x384  -vcodec libxvid -b '768k' -minrate '32' -maxrate '1536k' -bt '32k' -bufsize 65535 -flags +mv4+trell+loop -aic 1 -mbd 1 -cmp 2 -subcmp 2 -cgop 1 -b_qfactor '150' -b_qoffset '100' -bf '1' -pass 1 -passlogfile '/tmp/xvid.3054.log' -f avi /dev/null 2>&1
Final pass...
Use of uninitialized value in concatenation (.) or string at /usr/share/nuvexport/export/ffmpeg.pm line 261, <STDIN> line 14.
Use of uninitialized value in concatenation (.) or string at /usr/share/nuvexport/export/ffmpeg.pm line 261, <STDIN> line 14.

system call:
mkdir -m 0755 /tmp/fifodir_3054/

forking:
/usr/bin/nice -n19 /usr/bin/mythtranscode --showprogress -p '0' -c '2004' -s '2010-01-27T21:00:00' -f "/tmp/fifodir_3054/" --honorcutlist 2>&1

forking:
/usr/bin/nice -n19 ffmpeg -y -f s16le -ar  -ac  -i /tmp/fifodir_3054/audout -f rawvideo -pix_fmt yuv420p -s 480x480 -aspect 1.33333333333333 -r 29.970 -i /tmp/fifodir_3054/vidout -aspect 1.33333333333333 -r 29.970 -deinterlace -croptop    6 -cropright 6 -cropbottom 6 -cropleft  6 -s 512x384  -vcodec libxvid -b '768k' -minrate '32' -maxrate '1536k' -bt '32k' -bufsize 65535 -flags +mv4+trell+loop -aic 1 -mbd 1 -cmp 2 -subcmp 2 -cgop 1 -b_qfactor '150' -b_qoffset '100' -bf '1' -pass 2 -passlogfile '/tmp/xvid.3054.log' -acodec libmp3lame -async 1  -ab '128k' -f avi '/mnt/sdb1/mythexport/4 (RC) - Wed Jan 27 21-00-00 2010.avi' 2>&1
[/INDENT]I try with mencoder[INDENT]mencoder /mnt/recordings/test.mpg -oac mp3lame -lameopts "abr:br=128" -ovc lavc -lavcopts "vcodec=mpeg4:vhq:v4mv:vqmin=2:vbitrate=1500" -vf "pp=de,
crop=0:0:0:0,scale=480:-2" -o "/home/mythtv/outfile.avi"
[/INDENT]And received something like[INDENT]...too many audio packets in the buffer...

[/INDENT]Someone have an idea? That will be really appreciate...

---

### Post by GuiGuy on 2010-02-12
I'm probably not much help here if you want to stick with nuvexport (I think the author has lost interest). I  switched to this:

[http://web.aanet.com.au/~auric/?q=node/6](http://web.aanet.com.au/~auric/?q=node/6)

You'll find a more user friendly guide here

[http://www.xpmediacentre.com.au/community/mythtv-combined-front-backend/35847-transcoding-h-264-beginner-s-guide.html](http://www.xpmediacentre.com.au/community/mythtv-combined-front-backend/35847-transcoding-h-264-beginner-s-guide.html)

NB: You may have better luck with mencoder - change the /etc/nuvexportrc file to use mencoder instead of ffmpeg. Be warned though, I couldn't get mencoder to work either. 



Cheers

---

### Post by Darklighter on 2010-02-15
Thanks GuiGuy,
I'll try and give we you a feedback asap.

---

### Post by Darklighter on 2010-02-27
GuiGuy,
I try your link and this is the error I received:

users@mythtv:/var/lib/mythtv/recordings$ mythnuv2mkv.sh --contype=avi --quality=high --pass=one /var/lib/mythtv/recordings/2005_20100227133000.mpg
27/02,16:01 [23543] INFO Changed to avi,lavc.
27/02,16:01 [23543] INFO Changed to high quality.
27/02,16:01 [23543] INFO Changed to one pass.
27/02,16:01 [23543] INFO Unknown 480x480 NA 16:9 (Found in Default) 29.970 FPS Audio Rate 0 Channels 0
[COLOR=Red]27/02,16:01 [23543] ERROR Audio channels 0 invalid.[/COLOR]
--------------------------------------------------------------------------------
27/02,16:01 [23543] INFO Exiting. Errored.

Any idea?

Thanks for your help

---

### Post by Beirdo on 2010-03-14
This really isn't the right forum to try to get support for nuvexport.  The main author does not use ubuntu, and I (the secondary author) do, but rarely bother to look here to support things.

nuvexport is normally supported the same way as the rest of mythtv, primarily using mythtv's trac instance ([http://svn.mythtv.org/trac](http://svn.mythtv.org/trac)) and secondarily on IRC.

Most of these issues are being caused by ffmpeg and their insistence on changing their command line arguments with no warning, and also with hopelessly useless version numbers coming from ffmpeg.  Obviously, this doesn't fix the mencoder problem.

For instance, if you use the latest version of ffmpeg in hardy-security or hardy-updates, ffmpeg --version reports itself as SVN-rUNKNOWN.  This is obviously of no use to any scripts that want to know its version.

I will be working on getting nuvexport working, but it may require first of all that you not use the ubuntu package for nuvexport for a while and use SVN.  A release of mythtv is coming soon, and once there are debs for all that, hopefully some of that problem will go away.  Until then, the SVN version is the "current" version.

As for lack of -xvid support, I don't know what to say.  If the ubuntu-ized ffmpeg wasn't built with xvid support, you may just have to find a different version, or compile ffmpeg yourself.

---

