---
title: "No thumbnails on new recordings in mythweb"
date: 2010-03-05
forum: Mythbuntu
---

### Post by benlyboy on 2010-03-05
Hi all

My system crashed after an update. Well that is to say the front end and the backend setup both stopped working. Got all this working great again. The only fly in the ointment is that now when I look at the recorded programs page in mythweb, all the recordings made since the crash do not have thumbnails and I can't watch these recordings on flowplayer.

I looked at the backend log and noticed that it was looking for but not finding files ending with ".mpg.64" the recordings that worked ( the one recorded before the crash) had a file ending with ".mpg.64.png" , however the ones that did not work didn't have this file.

So I made a copy of a thumbnail files, in one of the recordings that was not working. I used a file ending with a mpg.png and renamed it adding the "64" making a thumbnail file with a mpg.64.png. this recording now works as it should. So I now know that this file missing is the problem.

But I don't know where to go from here. What is it that creates these file and places then in the directory? 

thanks for any help

---

### Post by benlyboy on 2010-03-06
Can anyone give me an idea of where to look?

I know that there is a missing file just don't know how that file is generated



thanks

---

### Post by benlyboy on 2010-03-06
found this bug report but still not sure what i need to do


> 

Hi,

Between trunk 23547 and 23613 which was my next update, the <recording>.mpg.64.png and <recording>.mpg.64.100x75.png thumbnails are no longer generated for new recordings in the recordings folder. The <recording>.mpg.png is created, though, so I can see it in mythfrontend.

Reverting to 23547, gets the missing thumbnails generated and mythweb shows them ok. At that commit, the .png files for any new recordings are created ok. Updating to latest trunk stops again the creation of the .64 and .64.100x75 png files.

Please include all output in bug reports.
MythTV Version : 23668M
MythTV Branch : trunk
Network Protocol : 56
Library API : 0.23.20100302-1
QT Version : 4.5.3
Options compiled in:
linux release using_oss using_alsa using_jack using_backend using_directfb using_dvb using_firewire using_frontend using_hdpvr using_iptv using_ivtv using_libfftw3 using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmc_vld using_xvmcw using_bindings_perl using_bindings_python using_opengl using_vdpau using_ffmpeg_threads using_libavc_5_3 using_live using_mheg


Is this a bug or am I missing something?

Tia

Yianni. 



---

### Post by benlyboy on 2010-03-11
Ok I have a question for all you programers out there.

How hard would it be to write a program that would up date the recordings folder twice an hour? (say just after the hour and half hour) this would be just after the start of most recordings. 

It would be nice if it could be set up to boot when the system boots so that it would be running in the background right from the start

It could go though looking for files ending with "mpg.png" then look to see if there is a file with the same name but ending in "mpg.64.png". If there is no such file it could create one using a copy of the mpg.png and renaming it adding the 64.

I know this is only a patch, but it would get my mythweb working right till a better fix came along.

---

### Post by ian dobson on 2010-03-12
Hi,

You can manually force the backend process to create a thumbnail for one recording using:-
mythbackend --generate-preview --chanid XXXXX --starttime YYYY

It shouldn't bee too have to write a script that calls the backend process for all new files that don't have a thumbnail image.

edit:- Here's a simple hack that calls the thumb generation code when no thumb exists for a recording:-

```

#!/usr/bin/perl -w
#  Check MythTV recordings for thumbs and create then if they are missing


my $REC= $ARGV[0];

if ( $REC eq "" ) {
 print "Command line options:-\n $0 /path/to/myth/recordings/\n";
 exit;
}

print "Scanning directory $REC\n";

@files = glob("$REC*.mpg");
foreach $FILE(@files) {
  print "Checking Recording $FILE\n";
  my @thumbs = glob("$FILE*png");
  my  $thumbs= @thumbs;
  if ($thumbs==0){
    print "THUMBS MISSING\n";
    $FILE =~ s/$REC//;
    $FILE =~ s/.mpg//;
    my @Parts=split(/_/,$FILE);
    system ("mythbackend --generate-preview --chanid @Parts[0] --starttime @Parts[1]");
  }
}

exit;

```


Regards
Ian Dobson

---

### Post by benlyboy on 2010-03-12
Thanks for your help I will try it out


One question though, will this generate a full set of thumbs or just the 64 I need...?

Thanks again for the help, will play with it over the weekend.

---

### Post by ian dobson on 2010-03-13
Hi,

My script just calls mythbackend --generate-preview for any mpg recording that doesn't have a png file of the same name.

If mythbackend generates a 64 png then it'll be created,if not is the 64.png the same as a .mpg.png? If yes the code just needs to copy the new png file to the new name.

Just make sure you run the script as your "mythtv" user, otherwise you'll have permission problems.

Regards
Ian Dobson

---

### Post by russell5 on 2010-03-14
Thanks for you script. 

I ran it and it found some but i still dont have thumbnails. 

i get these errors in mythbackend.log

2010-03-14 12:39:13.284 ProgramInfo(): Updated pathname '':'' -> '1004_20100301213000.mpg'
2010-03-14 12:39:13.372 Preview Error: Run() file not local: '/var/lib/mythtv/livetv/1004_20100301213000.mpg.64'


Do know what that means?

Ok if i edit 1004_20100301213000.mpg.png to be 1004_20100301213000.mpg.64 the preview works. And i am able to play form mythweb via flash.

---

### Post by ian dobson on 2010-03-14
Hi,

Do you mean mpg.64 or mpg.64.png?

If the worst comes to the worst you could just add one line code to the program that copies the mpg.png file to mpg.64.png.

Something like:-
copy($filetobecopied, $newfile);

Just after the system command.

Regards
Ian Dobson

---

### Post by russell5 on 2010-03-14
yeah i created a script that makes a copy of the file then renames it. 

the file name it wants is .mpg.64 instead of .mpg.png

---

### Post by benlyboy on 2010-03-14
Thanks all 

I wrote a program in python...I'm no programmer by any means, but I had fun doing it, and it did the job. 
It looks in the directory for files that end with .mpg.png, then checks to see if there is a matching file that ends with .mpg.64.png. If it fails to find one it makes a copy and renames it adding the 64. It seems to be working great. 

The only down side is that I have to run the program to update the files. But I already have an idea of how to rewrite it so it will check and update as need say twice an hour. So I may try that next weekend.

If someone wants it I will post my program but as I say I'm no programmer so didn't want to give you all a laugh...:p

Thanks again for the help, couldn't keep my system working with out you guys and girls

---

### Post by tgm4883 on 2010-03-14
> **benlyboy said:**
> Thanks all 

I wrote a program in python...I'm no programmer by any means, but I had fun doing it, and it did the job. 
It looks in the directory for files that end with .mpg.png, then checks to see if there is a matching file that ends with .mpg.64.png. If it fails to find one it makes a copy and renames it adding the 64. It seems to be working great. 

The only down side is that I have to run the program to update the files. But I already have an idea of how to rewrite it so it will check and update as need say twice an hour. So I may try that next weekend.

If someone wants it I will post my program but as I say I'm no programmer so didn't want to give you all a laugh...:p

Thanks again for the help, couldn't keep my system working with out you guys and girls

Don't rebuild the wheel. Use cron (or crontab)

---

### Post by benlyboy on 2010-03-14
> Don't rebuild the wheel. Use cron (or crontab)

use what or what...?

Sorry if I took the hard why around the problem, but as I said i'm no programmer so used the only tool i had any idea how to use.

---

### Post by tgm4883 on 2010-03-14
> **benlyboy said:**
> use what or what...?

Sorry if I took the hard why around the problem, but as I said i'm no programmer so used the only tool i had any idea how to use.

Google is fun. [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by benlyboy on 2010-03-19
Hay all I thought I would let you know that I have my thumbs back :D


The python scrip I wrote worked great and I have had thumbs since I started using it. The only down side was that the thumbs wouldn't appear until after it had finished the recording... no big deal really.

But today I did an update and my thumbs are back :o So I guess what updates taketh away updates giveth back...:)

 Thanks all

---

