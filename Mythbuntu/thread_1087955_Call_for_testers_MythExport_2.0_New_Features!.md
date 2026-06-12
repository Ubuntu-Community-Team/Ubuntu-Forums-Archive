---
title: "Call for testers: MythExport 2.0 New Features!"
date: 2009-03-05
forum: Mythbuntu
---

### Post by rhpot1991 on 2009-03-05
I have updated the wiki to include documentation for the new versions: [https://help.ubuntu.com/community/MythExport](https://help.ubuntu.com/community/MythExport)

This is currently available for Jaunty (with the Testing PPA being slightly ahead of the official repo at times) and Intrepid.

I ask that anyone running the current Intrepid version from the Testing PPA visits this thread and leaves some comments in the bugs: [http://ubuntuforums.org/showthread.php?t=1085950](http://ubuntuforums.org/showthread.php?t=1085950)

IF YOU DON'T WANT TO TEST OUT THIS NEW VERSION:
You should follow the thread above and install from Intrepid's Proposed repo.

I would like to stress the ffmpegArgs in /etc/mythexport_settings.cfg.  I went through a great deal of work to expose the ffmpeg arguments to the user so they can tweak these to their needs.  This has seemed to be the greatest drawback of past releases.

So everyone test away, if you find certain ffmpeg args work better for certain devices than the ones I provided post them here and I'll be sure to get them updated.

If you come across any bugs please report them here: [https://launchpad.net/mythexport/+filebug](https://launchpad.net/mythexport/+filebug)

Thanks

---

### Post by theophile on 2009-03-05
Why is this limited to portable devices? :(

---

### Post by rhpot1991 on 2009-03-05
> **theophile said:**
> Why is this limited to portable devices? :(

Technically its not, that is just how the project started.  If you have a device that can play video files and would benefit from a RSS feed then this should work fine for you.  Most of the available presets are for mobile devices but that shouldn't stop you from experimenting and coming up with some good ffmpeg options which can then be included.

---

### Post by rhpot1991 on 2009-03-06
Latest has been pushed to the Mythbuntu Testing PPA (both Intrepid and Jaunty)

---

### Post by Calmor on 2009-03-10
Just wanted to follow up here - and thank you for your quick answer to my post in the old thread!

The apt sources I used to get MythExport this morning are as per the Ubuntu Community Documentation Wiki:

```
deb http://ppa.launchpad.net/mythbuntu-testing/ubuntu intrepid main
deb-src http://ppa.launchpad.net/mythbuntu-testing/ubuntu intrepid main

```
(substituted intrepid for jaunty)

And, the issues I had were:

[LIST]
[*]libhtml-template-perl was required but not shown as a required dependency during installation
[*]Interal Server Error (500) given when attempting to read or write the configuration file (from what I gather from the error logs)
[/LIST]

Thank you again for your rapid response.  Do you want me to enter something in launchpad on this as well?

---

### Post by deffertz on 2009-03-10
I was using Mythexport successfully and I love it.  But I am excited about the new 2.0 features so when it showed up as an update on my Mythubuntu 8.10 box I happily upgraded.

Then my current mythexport failed to work and I too get a 500 internal error when I try to navigate to userjob.cgi, otg.cgi, setup_edit.cgi, save_setup.cgi.

I can access everything else but it is not allowing me to create a job.

All the permissions seem fine and they mirror the same as the pages that do work.

---

### Post by rhpot1991 on 2009-03-10
> **deffertz said:**
> I was using Mythexport successfully and I love it.  But I am excited about the new 2.0 features so when it showed up as an update on my Mythubuntu 8.10 box I happily upgraded.

Then my current mythexport failed to work and I too get a 500 internal error when I try to navigate to userjob.cgi, otg.cgi, setup_edit.cgi, save_setup.cgi.

I can access everything else but it is not allowing me to create a job.

All the permissions seem fine and they mirror the same as the pages that do work.

I can verify this is an issue with the perl config::simple module that I am using, it does not gracefully fail when the config is empty or doesn't exist.  I will be fixing this issue tonight.

---

### Post by rhpot1991 on 2009-03-11
The config issues should be worked out in version 1.99.3, now available on the Testing PPA.  Let me know if this fixes everyone's issues.

---

### Post by danskelly on 2009-03-11
> **rhpot1991 said:**
> The config issues should be worked out in version 1.99.3, now available on the Testing PPA.  Let me know if this fixes everyone's issues.

Doesn't seem to be fixed...

I try to access:
https://home.<domain>.net/mythexport/setup_edit.cgi


And my error.log shows:
```
[Wed Mar 11 10:54:41 2009] [error] [client <IP>] Something went wrong. No supported configuration file syntax found. Either the file is of wrong syntax, or there is a bug in guess_syntax() method. at /usr/share/perl5/Config/Simple.pm line 184, <FH> line 1., referer: https://home.dckelly.net/mythexport/setup.cgi
[Wed Mar 11 10:54:41 2009] [error] [client <IP>] Premature end of script headers: setup_edit.cgi, referer: https://home.<domain>.net/mythexport/setup.cgi

```


```
# apt-cache show mythexport
Package: mythexport
Source: mythexport
Priority: optional
Section: misc
Installed-Size: 272
Maintainer: Ubuntu MythTV Team <ubuntu-mythtv@lists.ubuntu.com>
Architecture: amd64
Version: 1.99.3-0ubuntu1~ppa0.1
Depends: debconf (>= 0.5) | debconf-2.0, perl, atomicparsley, libmyth-perl, libdbi-perl, libdbd-mysql-perl, debconf, apache2, libhtml-template-perl, libconfig-simple-perl, libxml-rss-perl, libproc-daemon-perl, libproc-pid-file-perl, liblog-dispatch-perl, libxml-writer-perl, mysql-client, libavcodec-unstripped-51, libavdevice-unstripped-52, libavformat-unstripped-52, libavutil-unstripped-49, libpostproc-unstripped-51, libswscale-unstripped-0
Pre-Depends: mythtv-backend | mythtv-database
Filename: pool/main/m/mythexport/mythexport_1.99.3-0ubuntu1~ppa0.1_amd64.deb
Size: 28770
MD5sum: a33fc4939421610099100514860d6f19
Description: Export MythTV recording to portable media players
 MythExport is a Perl daemon that can be used with MythTV to export recordings
 into a format playable on portable devices such as iPod Video, iPod Touch, PSP,
 and other devices. Besides converting your recordings, this script also grabs data
 from the MythTV MySQL database and injects it as iTunes data into the exported video
 so that it will show up correctly on your iPod. MythExport may also be used to take
 your recordings "On The Go" and provides a RSS feed to all exported recordings.
```

---

### Post by rhpot1991 on 2009-03-11
> **danskelly said:**
> Doesn't seem to be fixed...

I try to access:
https://home.<domain>.net/mythexport/setup_edit.cgi


And my error.log shows:
```
[Wed Mar 11 10:54:41 2009] [error] [client 66.249.86.249] Something went wrong. No supported configuration file syntax found. Either the file is of wrong syntax, or there is a bug in guess_syntax() method. at /usr/share/perl5/Config/Simple.pm line 184, <FH> line 1., referer: https://home.dckelly.net/mythexport/setup.cgi
[Wed Mar 11 10:54:41 2009] [error] [client 66.249.86.249] Premature end of script headers: setup_edit.cgi, referer: https://home.<domain>.net/mythexport/setup.cgi

```


```
# apt-cache show mythexport
Package: mythexport
Source: mythexport
Priority: optional
Section: misc
Installed-Size: 272
Maintainer: Ubuntu MythTV Team <ubuntu-mythtv@lists.ubuntu.com>
Architecture: amd64
Version: 1.99.3-0ubuntu1~ppa0.1
Depends: debconf (>= 0.5) | debconf-2.0, perl, atomicparsley, libmyth-perl, libdbi-perl, libdbd-mysql-perl, debconf, apache2, libhtml-template-perl, libconfig-simple-perl, libxml-rss-perl, libproc-daemon-perl, libproc-pid-file-perl, liblog-dispatch-perl, libxml-writer-perl, mysql-client, libavcodec-unstripped-51, libavdevice-unstripped-52, libavformat-unstripped-52, libavutil-unstripped-49, libpostproc-unstripped-51, libswscale-unstripped-0
Pre-Depends: mythtv-backend | mythtv-database
Filename: pool/main/m/mythexport/mythexport_1.99.3-0ubuntu1~ppa0.1_amd64.deb
Size: 28770
MD5sum: a33fc4939421610099100514860d6f19
Description: Export MythTV recording to portable media players
 MythExport is a Perl daemon that can be used with MythTV to export recordings
 into a format playable on portable devices such as iPod Video, iPod Touch, PSP,
 and other devices. Besides converting your recordings, this script also grabs data
 from the MythTV MySQL database and injects it as iTunes data into the exported video
 so that it will show up correctly on your iPod. MythExport may also be used to take
 your recordings "On The Go" and provides a RSS feed to all exported recordings.
```

Post the results of ls -la /etc/mythtv/mythexport/

Also what does your /etc/mythtv/mythexport/mythexport_settings.cfg file look like?

---

### Post by danskelly on 2009-03-11
> **rhpot1991 said:**
> Post the results of ls -la /etc/mythtv/mythexport/

Also what does your /etc/mythtv/mythexport/mythexport_settings.cfg file look like?


```
# ls -la /etc/mythtv/mythexport/
total 16
drwxrwxr-x 2 www-data www-data 4096 2009-03-11 09:57 .
drwxr-xr-x 3 root     root     4096 2009-03-11 09:57 ..
-rw-r--r-- 1 www-data www-data   21 2009-03-11 08:52 mythexport.cfg
-rwxrwxrwx 1 mythtv   www-data 1085 2009-03-11 08:56 mythexport_settings.cfg
```


```
# cat /etc/mythtv/mythexport/mythexport_settings.cfg 
[ipod] # Configuration name
removeCommercials=1 # Bit for removing commercials using cut points, 1 for yes 0 or empty for no.
codec=mpeg4 # Export codec
sizeY=240 # Y resolution size
sizeX=320 # X resolution size
aspect=4:3 # Aspect ratio, normally 4:3 or 16:9
videoBR=600kb # Video bitrate in kb or b
threads= # Enable multi threading, sets thread=auto.  1 for yes 0 or empty for no.
device=ipod # Export device
podcastName= # Podcast Name
deletePeriod=30 # Delete period in days
audioBR=128kb # Audio bitrate in kb or b
audioChannels= # Audio channels, empty and this is not used, any integer and this will be the number of channels used.  This may help with recordings that export without any sound, forcing this to 2 seems to help.
ffmpegArgs=-y -acodec libfaac -ab 128kb -vcodec mpeg4 -b 600kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x240 -aspect 4:3 # ffmpeg arguments, these are generated by the web interface using all the options in this config, you may change these to fit your needs
deinterlace=1 # Enable deinterlacing, 1 for enabled 0 or empty for disabled
```

---

### Post by rhpot1991 on 2009-03-11
> **danskelly said:**
> ```
# ls -la /etc/mythtv/mythexport/
total 16
drwxrwxr-x 2 www-data www-data 4096 2009-03-11 09:57 .
drwxr-xr-x 3 root     root     4096 2009-03-11 09:57 ..
-rw-r--r-- 1 www-data www-data   21 2009-03-11 08:52 mythexport.cfg
-rwxrwxrwx 1 mythtv   www-data 1085 2009-03-11 08:56 mythexport_settings.cfg
```


```
# cat /etc/mythtv/mythexport/mythexport_settings.cfg 
[ipod] # Configuration name
removeCommercials=1 # Bit for removing commercials using cut points, 1 for yes 0 or empty for no.
codec=mpeg4 # Export codec
sizeY=240 # Y resolution size
sizeX=320 # X resolution size
aspect=4:3 # Aspect ratio, normally 4:3 or 16:9
videoBR=600kb # Video bitrate in kb or b
threads= # Enable multi threading, sets thread=auto.  1 for yes 0 or empty for no.
device=ipod # Export device
podcastName= # Podcast Name
deletePeriod=30 # Delete period in days
audioBR=128kb # Audio bitrate in kb or b
audioChannels= # Audio channels, empty and this is not used, any integer and this will be the number of channels used.  This may help with recordings that export without any sound, forcing this to 2 seems to help.
ffmpegArgs=-y -acodec libfaac -ab 128kb -vcodec mpeg4 -b 600kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x240 -aspect 4:3 # ffmpeg arguments, these are generated by the web interface using all the options in this config, you may change these to fit your needs
deinterlace=1 # Enable deinterlacing, 1 for enabled 0 or empty for disabled
```

Delete (backup first) mythexport_settings.cfg, then use the web interface to create a new config.

---

### Post by danskelly on 2009-03-11
> **rhpot1991 said:**
> Delete (backup first) mythexport_settings.cfg, then use the web interface to create a new config.

Okay, I renamed the file to, mythexport_settings.cfg.old.

I went into the web interface and used the following settings:

[IMG]http://img519.imageshack.us/img519/9175/mythexportsetting.png[/IMG]

When I clicked 'Submit' I got a 500 Error.

**error.log**:
```
[Wed Mar 11 11:44:49 2009] [error] [client <IP>] couldn't open /etc/mythtv/mythexport/mythexport_settings.cfg: No such file or directory at /var/www/mythexport/save_setup.cgi line 20., referer: https://home.dckelly.net/mythexport/setup_details.cgi
[Wed Mar 11 11:44:49 2009] [error] [client <IP>] Premature end of script headers: save_setup.cgi, referer: https://home.dckelly.net/mythexport/setup_details.cgi
```

---

### Post by rhpot1991 on 2009-03-12
> **danskelly said:**
> Okay, I renamed the file to, mythexport_settings.cfg.old.

I went into the web interface and used the following settings:

[IMG]http://img519.imageshack.us/img519/9175/mythexportsetting.png[/IMG]

When I clicked 'Submit' I got a 500 Error.

**error.log**:
```
[Wed Mar 11 11:44:49 2009] [error] [client <IP>] couldn't open /etc/mythtv/mythexport/mythexport_settings.cfg: No such file or directory at /var/www/mythexport/save_setup.cgi line 20., referer: https://home.dckelly.net/mythexport/setup_details.cgi
[Wed Mar 11 11:44:49 2009] [error] [client <IP>] Premature end of script headers: save_setup.cgi, referer: https://home.dckelly.net/mythexport/setup_details.cgi
```

This should be fixed if you get the latest version from the Testing PPA.

---

### Post by danskelly on 2009-03-12
> **rhpot1991 said:**
> This should be fixed if you get the latest version from the Testing PPA.

Sweet!  Everything seems to be fixed now except the RSS feed.

When I click on "RSS Feed" on the left-hand pane, the right shows me the raw XML code.   Usually Firefox will format it nicely, and also, when I paste the link to the feed into iTunes as a new podcast, it errors.

I get the following error.log entry when I access the RSS Feed:

```
[Thu Mar 12 08:28:05 2009] [error] [client <IP>] Use of uninitialized value $ENV{"HTTP_X_FORWARDED_HOST"} in string ne at /var/www/mythexport/mythexportRSS.cgi line 19., referer: https://home.<domain>.net/mythexport/rss.cgi
```



Any thoughts?

---

### Post by rhpot1991 on 2009-03-12
> **danskelly said:**
> Sweet!  Everything seems to be fixed now except the RSS feed.

When I click on "RSS Feed" on the left-hand pane, the right shows me the raw XML code.   Usually Firefox will format it nicely, and also, when I paste the link to the feed into iTunes as a new podcast, it errors.

I get the following error.log entry when I access the RSS Feed:

```
[Thu Mar 12 08:28:05 2009] [error] [client <IP>] Use of uninitialized value $ENV{"HTTP_X_FORWARDED_HOST"} in string ne at /var/www/mythexport/mythexportRSS.cgi line 19., referer: https://home.<domain>.net/mythexport/rss.cgi
```

Any thoughts?

That is just a warning, it can safely be ignored.

What happens if you click on "Link to this feed" does it format properly then?  Do you have any actual recordings exported and in the RSS at this point?  Pastebin ([http://mythbuntu.pastebin.com/](http://mythbuntu.pastebin.com/)) your RSS and I'll compare that with mine.

---

### Post by danskelly on 2009-03-12
> **rhpot1991 said:**
> That is just a warning, it can safely be ignored.

What happens if you click on "Link to this feed" does it format properly then?  Do you have any actual recordings exported and in the RSS at this point?  Pastebin ([http://mythbuntu.pastebin.com/](http://mythbuntu.pastebin.com/)) your RSS and I'll compare that with mine.

I clicked "Link to this feed" and [this]("http://mythbuntu.pastebin.com/mbe115dc") is what comes out ([http://mythbuntu.pastebin.com/mbe115dc](http://mythbuntu.pastebin.com/mbe115dc)).  Pretty much the same as "RSS Feed" (but without the header.)

---

### Post by Calmor on 2009-03-12
> **rhpot1991 said:**
> The config issues should be worked out in version 1.99.3, now available on the Testing PPA.  Let me know if this fixes everyone's issues.

I installed the new version today and confirmed that everything works as intended.  After working out some issues with ffmpeg for my psp options, it appears to work very well.  Thanks for putting this together and the quick response!

---

### Post by rhpot1991 on 2009-03-12
> **Calmor said:**
> I installed the new version today and confirmed that everything works as intended.  After working out some issues with ffmpeg for my psp options, it appears to work very well.  Thanks for putting this together and the quick response!

Good to hear.  Mind sharing what you had to tweak for the PSP, I don't have one so that portion doesn't get much testing besides user feedback.

---

### Post by Calmor on 2009-03-13
> **rhpot1991 said:**
> Good to hear.  Mind sharing what you had to tweak for the PSP, I don't have one so that portion doesn't get much testing besides user feedback.

I can't give you the actual mythexport_settings.cfg file right now as I don't have ssh access to my server, but here's some information for now:

From [_this site_]("http://www.linuxquestions.org/questions/linux-software-2/ffmpeg-psp-encoding-woes-with-a-solution-619247/") I stole the entire ffmpeg line, as the one created by mythexport was throwing some error messages.  I'd used this ffmpeg line before and confirmed that it worked on my system (Intrepid x64)

To just "make it work" as quickly as possible, I edited the mythexport_settings.cfg and removed all of the text field inputs, and set ffmpeg to the settings in that post's final file, removing the -i -title and -timestamp flags.  The final results were similar to this:

```
-y -bitexact 1 -vcodec libxvid -s 320x240 -r 29.97 -b 1500k -acodec libfaac -ac 2 -ar 24000 -ab 65535 -f psp
```

I'll post back this weekend with the actual mythexport_settings.cfg file, and hopefully also be able to play around with it so that I can see what settings work and what settings don't to get an error-free output.

One issue I do have is that when I visit a site with the PSP, such as Engadget, it asks if I'd like to add the RSS feed to the list.  When I visit my mythexport site, it does not do so, nor does it show a list of available files.  When I visit the site with Firefox, it works correctly.  Unfortunately, I don't understand enough about the PSP's RSS reader to be able to diagnose it more than that at this point, but hope to play around with it again this weekend and see if I can figure out why.

Thanks again for all your hard work!

---

### Post by danskelly on 2009-03-13
> **danskelly said:**
> I clicked "Link to this feed" and [this]("http://mythbuntu.pastebin.com/mbe115dc") is what comes out ([http://mythbuntu.pastebin.com/mbe115dc](http://mythbuntu.pastebin.com/mbe115dc)).  Pretty much the same as "RSS Feed" (but without the header.)

I don't know if anybody else is having this issue....  I'm having another trouble that seems to be MythTV related, and perhaps not mythexport related.  I'll post another threat on it.  But, I'd still like to get my iTunes to download my podcast automatically.

---

### Post by rhpot1991 on 2009-03-13
> **danskelly said:**
> I don't know if anybody else is having this issue....  I'm having another trouble that seems to be MythTV related, and perhaps not mythexport related.  I'll post another threat on it.  But, I'd still like to get my iTunes to download my podcast automatically.

I sent you a PM about the issue with some test links yesterday.  Have a look there and reply back.

---

### Post by Calmor on 2009-03-13
> **rhpot1991 said:**
> Good to hear.  Mind sharing what you had to tweak for the PSP, I don't have one so that portion doesn't get much testing besides user feedback.

Here's my current mythexport_settings.cfg file.  I haven't gotten to play with anything yet and hope to post back later this weekend:

```
; Config::Simple 4.59
; Thu Mar 12 11:39:35 2009

[PSP]
removeCommercials=
codec=
sizeY=
sizeX=
aspect=
videoBR=
threads=
device=psp
podcastName=
deletePeriod=
audioBR=
ffmpegArgs=-y -bitexact 1 -vcodec libxvid -s 320x240 -r 29.97 -b 1000k -acodec libfaac -ac 2 -ar 24000 -ab 65535 -f psp
audioChannels=
deinterlace=

```

---

### Post by deffertz on 2009-03-14
Thanks for the quick update.  That did the trick for me accessing everything.

However my user job says it's executed but it doesn't do anything.

From mythexport log
```
March 14 15:56:49 ubuntu /usr/bin/mythexport-daemon[29675]: Starting Processing:  1237064209
March 14 15:56:49 ubuntu /usr/bin/mythexport-daemon[29675]: ERROR: Directory  is not writeable.
 at line 292 in /usr/bin/mythexport-daemon
March 14 15:56:49 ubuntu /usr/bin/mythexport-daemon[29675]: Creating mysql dump
March 14 15:56:49 ubuntu /usr/bin/mythexport-daemon[29675]: ERROR: mysqldump -hlocalhost -u***** -p***** -P**** mythconverg recorded recordedseek recordedrating recordedprogram recordedmarkup recordedcredits --where="(chanid='1213' and starttime='2009-03-07 12:34:00')" --no-create-db --no-create-info > /mythimport.sql 2>&1 failed. at line 306 in /usr/bin/mythexport-daemon
```


I did do all the commands as suggested to get user permissions correct (or so I think) as it suggested under save_system_setup.cgi.

This might not be mythexport's problem as I was messing with permissions prior to the latest update but I'm stumped.

---

### Post by rjackal on 2009-03-14
> **deffertz said:**
> Thanks for the quick update.  That did the trick for me accessing everything.

However my user job says it's executed but it doesn't do anything.

From mythexport log
```
March 14 15:56:49 ubuntu /usr/bin/mythexport-daemon[29675]: Starting Processing:  1237064209
March 14 15:56:49 ubuntu /usr/bin/mythexport-daemon[29675]: ERROR: Directory  is not writeable.
 at line 292 in /usr/bin/mythexport-daemon
March 14 15:56:49 ubuntu /usr/bin/mythexport-daemon[29675]: Creating mysql dump
March 14 15:56:49 ubuntu /usr/bin/mythexport-daemon[29675]: ERROR: mysqldump -hlocalhost -u***** -p***** -P**** mythconverg recorded recordedseek recordedrating recordedprogram recordedmarkup recordedcredits --where="(chanid='1213' and starttime='2009-03-07 12:34:00')" --no-create-db --no-create-info > /mythimport.sql 2>&1 failed. at line 306 in /usr/bin/mythexport-daemon
```


I did do all the commands as suggested to get user permissions correct (or so I think) as it suggested under save_system_setup.cgi.

This might not be mythexport's problem as I was messing with permissions prior to the latest update but I'm stumped.
I am having the same issue here, I removed mythexport and reinstalled, same issue.

---

### Post by Calmor on 2009-03-15
Not that I know much, but can you post the permissions of the folder you're trying to write the output to?

Mine is:

```

drwxrwxr-x  2 mythtv mythtv   63 2009-03-12 12:40 VideoExport

```

---

### Post by rhpot1991 on 2009-03-15
> **deffertz said:**
> Thanks for the quick update.  That did the trick for me accessing everything.

However my user job says it's executed but it doesn't do anything.

From mythexport log
```
March 14 15:56:49 ubuntu /usr/bin/mythexport-daemon[29675]: Starting Processing:  1237064209
March 14 15:56:49 ubuntu /usr/bin/mythexport-daemon[29675]: ERROR: Directory  is not writeable.
 at line 292 in /usr/bin/mythexport-daemon
March 14 15:56:49 ubuntu /usr/bin/mythexport-daemon[29675]: Creating mysql dump
March 14 15:56:49 ubuntu /usr/bin/mythexport-daemon[29675]: ERROR: mysqldump -hlocalhost -u***** -p***** -P**** mythconverg recorded recordedseek recordedrating recordedprogram recordedmarkup recordedcredits --where="(chanid='1213' and starttime='2009-03-07 12:34:00')" --no-create-db --no-create-info > /mythimport.sql 2>&1 failed. at line 306 in /usr/bin/mythexport-daemon
```


I did do all the commands as suggested to get user permissions correct (or so I think) as it suggested under save_system_setup.cgi.

This might not be mythexport's problem as I was messing with permissions prior to the latest update but I'm stumped.

The directory you are trying to write to should be owned by mythtv.  So, do the following to it:
```
sudo chown mythtv:mythtv /location/you/are/using && sudo chmod 775 /location/you/are/using
```

The On the Go portion does not use the same location that regular exported recordings use, this is by design so people can use removable drives and so they do not end up in the RSS feed.

---

### Post by deffertz on 2009-03-16
> The directory you are trying to write to should be owned by mythtv. So, do the following to it:
Code:
sudo chown mythtv:mythtv /location/you/are/using && sudo chmod 775 /location/you/are/using
The On the Go portion does not use the same location that regular exported recordings use, this is by design so people can use removable drives and so they do not end up in the RSS feed.

I've done as suggested but same result and mythexport.log output.  

I did have this working on MythExport version 1 using the same directory.  I'm using Mythbuntu logging in automatically as another user other than mythtv but that shouldn't matter should it?

---

### Post by pt123 on 2009-03-16
> **danskelly said:**
> ```
# ls -la /etc/mythtv/mythexport/
total 16
drwxrwxr-x 2 www-data www-data 4096 2009-03-11 09:57 .
drwxr-xr-x 3 root     root     4096 2009-03-11 09:57 ..
-rw-r--r-- 1 www-data www-data   21 2009-03-11 08:52 mythexport.cfg
-rwxrwxrwx 1 mythtv   www-data 1085 2009-03-11 08:56 mythexport_settings.cfg
```


I am having similar problems with the 500 internal server. But in my /etc/mythtv/mythexport/ folder there was no mythexport_settings.cfg file.

There was a mythexport.cfg but it was empty
I removed it and restarted mythexport and I still have the 500 internal server problem.

When I ran
sudo dpkg-reconfigure mythexport

No /usr/bin/perl found running; none killed

Then it says 
Enter password:  ( I assume mysql's root)


When I open
[http://localhost/mythexport/setup.cgi](http://localhost/mythexport/setup.cgi)
the page opens fine

---

### Post by Calmor on 2009-03-16
Sorry to come back with another issue...

After a bout with hardware this weekend, Mythexport wanted to update to ppa0.7, which I allowed it to do.

Since the update, I've tried to run a few jobs to transcode to PSP, in the hopes of testing the PSP switches.  Automatically flagged user jobs (set in Mythweb to export to PSP) and manually run jobs (clicked the user job in Mythweb) show as running successfully in Mythweb, but they do not execute in Mythexport. 

Mythexport showed these as jobs in the job queue, but mythexport.log showed no mention of these new jobs, only that the daemon was started at bootup.  Two of them have been in the queue all night, so waiting for system resources is not an issue.  I was able to delete the jobs using the web interface and create new ones using Mythweb.

Restarting the daemon apparently did the trick, and showed a perl error message.

```

$ sudo /etc/init.d/mythexport restart
 * Restarting MythExport Daemon: mythexport                                     No /usr/bin/perl found running; none killed.
                                                                         [ OK ]

```

Trying to restart mythexport again showed:

```

$ sudo /etc/init.d/mythexport restart
 * Restarting MythExport Daemon: mythexport                                     /usr/bin/perl already running.

```

But, the daemon continued to run and the jobs began to be executed.

Anything you'd like me to try out?

Thanks!

Update - As a further test, after the queued jobs were completed, subsequent jobs also needed the daemon restarted to run.  I didn't give them as much time in the queue (about 20 minutes), but they started immediately upon restarting the daemon.

---

### Post by rhpot1991 on 2009-03-16
> **deffertz said:**
> I've done as suggested but same result and mythexport.log output.  

I did have this working on MythExport version 1 using the same directory.  I'm using Mythbuntu logging in automatically as another user other than mythtv but that shouldn't matter should it?

Looking at your logs there is an empty space where it should be telling you which directory failed.  Did you specify a directory on the otg.cgi page?

You should make sure you have the latest version as well, 1.99.4-0ubuntu1

---

### Post by danskelly on 2009-03-16
I'm trying to add my "Link to this [RSS] feed" to iTunes, and iTunes errors and says:
```
There was a problem downloading "https://home.<domain>.net/mythexport/mythexportRSS.cgi?podcastName=". An unknown error occured (-9812).  Please check that the URL is correct and the connection to the network is active and try again.
```

I know you're not an Apple tech support person, or anything, so I sent it over to [feedvalidator.org]("http://www.feedvalidator.org")

It found some issues:

**pubDate**:
```
Incorrect day of week: Thu
<pubDate>Thu, 23 Aug 1999 07:00:00 GMT</pubDate>
```

Looks like the date is just wrong.  1999???  I don't know where it gets this data from.

**lastBuildDate**:  Same thing. (same date.)

And it thinks that the <enclosure> tag needs the 'length' [argument]("http://feedvalidator.org/docs/rss2.html#ltenclosuregtSubelementOfLtitemgt").

It (feedvalidator) also suggested a couple of suggestions:
[LIST]
[*][<item> should contain a 'guid' element]("http://feedvalidator.org/docs/warning/MissingGuid.html")
[*][Missing atom:link with rel="self"]("http://feedvalidator.org/docs/warning/MissingAtomSelfLink.html")
[/LIST]

Thanks for all your help!

---

### Post by danskelly on 2009-03-16
> **danskelly said:**
> 
**pubDate**:
```
Incorrect day of week: Thu
<pubDate>Thu, 23 Aug 1999 07:00:00 GMT</pubDate>
```

Looks like the date is just wrong.  1999???  I don't know where it gets this data from.

**lastBuildDate**:  Same thing. (same date.)


Okay, I found where it's getting these dates... Why is it hard-coded in there?

Also, I took the day of the week out (Thur, ) and changed the date to a more reasonable date, and it didn't throw any errors.

I'm also thinking that most of the iTunes problem is the fact that the SSL cert is messed up...

Thoughts?

---

### Post by rhpot1991 on 2009-03-16
> **danskelly said:**
> I'm trying to add my "Link to this [RSS] feed" to iTunes, and iTunes errors and says:
```
There was a problem downloading "https://home.<domain>.net/mythexport/mythexportRSS.cgi?podcastName=". An unknown error occured (-9812).  Please check that the URL is correct and the connection to the network is active and try again.
```

I know you're not an Apple tech support person, or anything, so I sent it over to [feedvalidator.org]("http://www.feedvalidator.org")

It found some issues:

**pubDate**:
```
Incorrect day of week: Thu
<pubDate>Thu, 23 Aug 1999 07:00:00 GMT</pubDate>
```

Looks like the date is just wrong.  1999???  I don't know where it gets this data from.

**lastBuildDate**:  Same thing. (same date.)

And it thinks that the <enclosure> tag needs the 'length' [argument]("http://feedvalidator.org/docs/rss2.html#ltenclosuregtSubelementOfLtitemgt").

It (feedvalidator) also suggested a couple of suggestions:
[LIST]
[*][<item> should contain a 'guid' element]("http://feedvalidator.org/docs/warning/MissingGuid.html")
[*][Missing atom:link with rel="self"]("http://feedvalidator.org/docs/warning/MissingAtomSelfLink.html")
[/LIST]

Thanks for all your help!

Looks like thats a generic iTunes networking error.  I'd guess it doesn't like your self signed SSL cert.

Try this maybe: [http://schmoil.blogspot.com/2008/09/itunes-and-vague-ssl-error-messages.html](http://schmoil.blogspot.com/2008/09/itunes-and-vague-ssl-error-messages.html)

---

### Post by rhpot1991 on 2009-03-16
> **danskelly said:**
> Okay, I found where it's getting these dates... Why is it hard-coded in there?

Also, I took the day of the week out (Thur, ) and changed the date to a more reasonable date, and it didn't throw any errors.

I'm also thinking that most of the iTunes problem is the fact that the SSL cert is messed up...

Thoughts?

The dates and all but one warning should be fixed in the latest version (I can't fix the last warning with the module that I use).

I also fixed the mime type issue that we talked about in our PMs and the feed should now correctly detect if you are using https.

Let me know if all of these are working, I don't have SSL setup but verified it doesn't break anything if you aren't using SSL.

---

### Post by rhpot1991 on 2009-03-19
> **Calmor said:**
> Sorry to come back with another issue...

After a bout with hardware this weekend, Mythexport wanted to update to ppa0.7, which I allowed it to do.

Since the update, I've tried to run a few jobs to transcode to PSP, in the hopes of testing the PSP switches.  Automatically flagged user jobs (set in Mythweb to export to PSP) and manually run jobs (clicked the user job in Mythweb) show as running successfully in Mythweb, but they do not execute in Mythexport. 

Mythexport showed these as jobs in the job queue, but mythexport.log showed no mention of these new jobs, only that the daemon was started at bootup.  Two of them have been in the queue all night, so waiting for system resources is not an issue.  I was able to delete the jobs using the web interface and create new ones using Mythweb.

Restarting the daemon apparently did the trick, and showed a perl error message.

```

$ sudo /etc/init.d/mythexport restart
 * Restarting MythExport Daemon: mythexport                                     No /usr/bin/perl found running; none killed.
                                                                         [ OK ]

```

Trying to restart mythexport again showed:

```

$ sudo /etc/init.d/mythexport restart
 * Restarting MythExport Daemon: mythexport                                     /usr/bin/perl already running.

```

But, the daemon continued to run and the jobs began to be executed.

Anything you'd like me to try out?

Thanks!

Update - As a further test, after the queued jobs were completed, subsequent jobs also needed the daemon restarted to run.  I didn't give them as much time in the queue (about 20 minutes), but they started immediately upon restarting the daemon.

There were 2 issues which I fixed recently that look like they were affecting you:
[LIST]
[*]The Daemon's priority was higher than MythTV backend's so it would start before the backend was up causing an error
[*]Uncaught errors were thrown away by the daemon and not logged, so the above error was never mentioned and the daemon would just die.
[/LIST]

These are both fixed in the latest version on the PPA, let me know if you are still experiencing these issues.

---

### Post by JerkyChew on 2009-03-19
I'm having some issues. I'm using the Mythbuntu weekly trunk builds, so if .22 trunk isn't supported please yell at me and I'll be quiet :)

I enabled the testing PPA and installed via the instructions. It appeared to attempt to access my database and failed (I saw an error about not being able to connect to mysql database as root with password YES or similar), but the installation continued and appeared to finish.

[http://mymythbox/mythexport](http://mymythbox/mythexport) works, sort of. It just gives me raw html. Clicking on any of the cgi files, setup.cgi for example, just gives me the raw Perl code. I was able to start mythexport manually and here are the contents of my /var/log/mythexport.log file:

```
March 19 20:48:59 magic /usr/bin/mythexport-daemon[6743]: Unable to query mythexport_job_queue table at line 609 in /us
r/bin/mythexport-daemon
DBD::mysql::st fetchrow_array failed: fetch() without execute() at /usr/bin/mythexport-daemon line 611.
DBD::mysql::st execute failed: Table'mythconverg.mythexport_job_queue' doesn't exist at /usr/bin/mythexport-daemon lin
e 609.

```

---

### Post by rhpot1991 on 2009-03-20
> **JerkyChew said:**
> I'm having some issues. I'm using the Mythbuntu weekly trunk builds, so if .22 trunk isn't supported please yell at me and I'll be quiet :)

I'll be honest I haven't touched .22 at all, so I can't tell you either way.  In theory it should work :)

> **JerkyChew said:**
> 
I enabled the testing PPA and installed via the instructions. It appeared to attempt to access my database and failed (I saw an error about not being able to connect to mysql database as root with password YES or similar), but the installation continued and appeared to finish.

You should check the mythconverg DB (with phpmyadmin, or mysql command line, your choice).  See if the tables mythexport and mythexport_job_queue exist.

> **JerkyChew said:**
> 
[http://mymythbox/mythexport](http://mymythbox/mythexport) works, sort of. It just gives me raw html. Clicking on any of the cgi files, setup.cgi for example, just gives me the raw Perl code. I was able to start mythexport manually and here are the contents of my /var/log/mythexport.log file:

```
March 19 20:48:59 magic /usr/bin/mythexport-daemon[6743]: Unable to query mythexport_job_queue table at line 609 in /us
r/bin/mythexport-daemon
DBD::mysql::st fetchrow_array failed: fetch() without execute() at /usr/bin/mythexport-daemon line 611.
DBD::mysql::st execute failed: Table'mythconverg.mythexport_job_queue' doesn't exist at /usr/bin/mythexport-daemon lin
e 609.

```

Sounds like your tables didn't get created, I wonder if the install failed.  Check the tables I mentioned above, you can compare your /etc/apache/sites-available/mythexport with the following: [http://bazaar.launchpad.net/~mythbuntu/mythexport/trunk/annotate/head%3A/etc/apache2/sites-available//mythexport.conf](http://bazaar.launchpad.net/~mythbuntu/mythexport/trunk/annotate/head%3A/etc/apache2/sites-available//mythexport.conf)

If your tables don't exist you should sudo dpkg-reconfigure mythexport, and double check that the sql info you provide is correct.

---

### Post by pt123 on 2009-03-20
I just got an update for mythexport from the update manager, in the terminal it is asking for a "Password:" , it possible to make it more informative by askinging for the "Root mysql password:"

---

### Post by pt123 on 2009-03-20
I completely removed mythexport and installed the package again,
a Gui dialog box comes up with asking for 3 inputs, but then when you click "Forward", the terminal shown asks for "Enter Password:" (not sure what this is for)

When I press enter on that, it finishes by displaying:
> 
 * Reloading web server config apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
   ...done.
 * Starting MythExport Daemon: mythexport 
   ...done.


When I open 
[http://localhost/mythexport/](http://localhost/mythexport/)
I get the 500 error, can you tell us what is the default cgi script it should be running?

The page [http://localhost/mythexport/setup.cgi](http://localhost/mythexport/setup.cgi)
works fine, but when I choose a device like Ipod and submit,
none of the default config values are shown like the config settings file is not being copied over.

Also in the /etc/mythtv/mythexport/ folder there is no mythexport_settings.cfg file. Is there a place we can download one from?

Thanks

---

### Post by pt123 on 2009-03-20
Also after restarting the backend, and starting the frontend and navigating to Media Library -> Watch Recordings , under Job options there is no Ipod option, just the usual transcode & commercials options.

Could this be because I am not logging in as mythtv but another user account, is mythexport using mythtv user account to store files?

Also when I turned on debug the log file has this line not sure if it is an error or not
March 21 12:39:02 compname /usr/bin/mythexport-daemon[8274]: query = select id, type, param from mythexport_job_queue order by id at line 608 in /usr/bin/mythexport-daemon


Thanks

---

### Post by pt123 on 2009-03-20
[https://help.ubuntu.com/community/MythExport](https://help.ubuntu.com/community/MythExport)
> If you get an error about config.xml missing, this can normally be found in the home directory of the user who runs your MythTV Fronend, and can be fixed by creating a symlink in mythtv's home directory (because that is the user who runs the daemon).
I created a sym link to config.xml file but I had to use sudo. Then did chown to mythtv. 
When I start mythexport it says the config file is missing. 
>  * Restarting MythExport Daemon: mythexport                                     No /usr/bin/perl found running; none killed.
No config found; attempting to find mythbackend via UPnP.
No backends found.  Please copy /home/mythtv/.mythtv/config.xml from a working MythTV installation instead.
Compilation failed in require at /usr/bin/mythexport-daemon line 33.
BEGIN failed--compilation aborted at /usr/bin/mythexport-daemon line 33.


Rather than syslink copying across the config.xml file to /home/mythtv/.mythtv/ the file across seemed to get rid of the error

But then opening localhost/mythexport produces this error in the apache error.log file

> [Sat Mar 21 13:13:42 2009] [error] [client 127.0.0.1] No backends found.  Please copy /var/www/.mythtv/config.xml from a working MythTV installation instead.
[Sat Mar 21 13:13:42 2009] [error] [client 127.0.0.1] Compilation failed in require at /var/www/mythexport/file.cgi line 7.
[Sat Mar 21 13:13:42 2009] [error] [client 127.0.0.1] BEGIN failed--compilation aborted at /var/www/mythexport/file.cgi line 7.
[Sat Mar 21 13:13:42 2009] [error] [client 127.0.0.1] Premature end of script headers: file.cgi


so after copying the file it CGI errors have disappeared.

All this copying or sys linking of the config.xml between 2 different locations 
 /var/www/.mythtv/
/home/mythtv/.mythtv

is very confusing, can't they use one location, or the documentation be improved here [https://help.ubuntu.com/community/MythExport](https://help.ubuntu.com/community/MythExport)

Anyway thanks for all your effort into creating this application

---

### Post by rhpot1991 on 2009-03-22
> **pt123 said:**
> 
The page [http://localhost/mythexport/setup.cgi](http://localhost/mythexport/setup.cgi)
works fine, but when I choose a device like Ipod and submit,
none of the default config values are shown like the config settings file is not being copied over.

Unfortunately I ran out of development time, so there are no defaults.  I need to update the wiki and/or web interface to indicate which inputs are required.  Everything from Title to Codec should be filled in, the inputs after Codec are optional.

> **pt123 said:**
> 
Also in the /etc/mythtv/mythexport/ folder there is no mythexport_settings.cfg file. Is there a place we can download one from?

That file doesn't get created until you save one through the web interface.

---

### Post by rhpot1991 on 2009-03-22
> **pt123 said:**
> Also after restarting the backend, and starting the frontend and navigating to Media Library -> Watch Recordings , under Job options there is no Ipod option, just the usual transcode & commercials options.

Could this be because I am not logging in as mythtv but another user account, is mythexport using mythtv user account to store files?

Did you enable a user job via the MythExport web interface?

> **pt123 said:**
> 
Also when I turned on debug the log file has this line not sure if it is an error or not
March 21 12:39:02 compname /usr/bin/mythexport-daemon[8274]: query = select id, type, param from mythexport_job_queue order by id at line 608 in /usr/bin/mythexport-daemon


That is fine, when enabling debugging for the daemon it will spit out all any queries or commands that it runs as well as many variable values, this is of course to help debug an issue.  I'd recommend turning debugging off once everything is running smoothly, this way that log file doesn't get too huge.

---

### Post by pt123 on 2009-03-22
> **rhpot1991 said:**
> 
That file doesn't get created until you save one through the web interface.

is it possible if you can post some config values esp. for the DVB field I was having problems getting the encoding to happen.

---

### Post by rhpot1991 on 2009-03-22
> **pt123 said:**
> [https://help.ubuntu.com/community/MythExport](https://help.ubuntu.com/community/MythExport)

I created a sym link to config.xml file but I had to use sudo. Then did chown to mythtv. 
When I start mythexport it says the config file is missing. 



Rather than syslink copying across the config.xml file to /home/mythtv/.mythtv/ the file across seemed to get rid of the error

But then opening localhost/mythexport produces this error in the apache error.log file



so after copying the file it CGI errors have disappeared.

All this copying or sys linking of the config.xml between 2 different locations 
 /var/www/.mythtv/
/home/mythtv/.mythtv

is very confusing, can't they use one location, or the documentation be improved here [https://help.ubuntu.com/community/MythExport](https://help.ubuntu.com/community/MythExport)

Anyway thanks for all your effort into creating this application

Yes the whole config.xml issue is a mess.  It will get better with Jaunty (or if you are using the MythTV weekly builds) as there will be a /etc/mythtv/config.xml that can be linked to.  The main issue here is that this config needs to exist in a user's home directory for the perl bindings to be able to find the backend, so you need it in /home/mythtv/.mythtv/ (for the daemon) and /var/www/.mythtv (for the web interface), the package should provide symlinks by default but it will never know who your regular user is so it is impossible to do the symlinking automagically (they currently point to /root/.mythtv - which may not contain a working config).  I will clean up the Intrepid version some so dropping a copy (or symlink) into /etc/mythtv/config.xml is all that will be needed.

---

### Post by rhpot1991 on 2009-03-22
> **pt123 said:**
> is it possible if you can post some config values esp. for the DVB field I was having problems getting the encoding to happen.

What kind of device?

---

### Post by pt123 on 2009-03-22
Laptop something with xvid & mp3 audio

> Audio Channels:  * May help with dvb recordings
What should the setting be for this

---

### Post by rhpot1991 on 2009-03-22
> **pt123 said:**
> Laptop something with xvid & mp3 audio


What should the setting be for this

That setting will help if your exported recordings don't have sound, something like 2 (stereo) or 5 (for surround).

If you are having troubles getting things to export, I recommend enabling debugging and checking for the resulting ffmpeg command, try running that by hand and it should tell you what the issues are.  Also worth noting, if the ffmpeg command fails (without debugging enabled), it will end up in the log.

Most of the defaults are going to use AAC for audio.  Here is how you can change this, create your config.  Then edit /etc/mythtv/mythexport/mythexport_settings.cfg switch '-acodec libfaac' with '-acodec libmp3lame'

---

### Post by JerkyChew on 2009-03-22
I uninstalled and attempted to reinstall mythexport, here are my latest issues:

1) Mythexport shows up as version 1.99.4-0 in Synaptic, even though I have the mythbuntu-testing Intrepid repos enabled. 

2) Attempting to install fails - I get an error saying "ln: creating symbolic link './video'; File exists and then the GUI error "E: mythexport: subprocess post-installation script returned error exit status 1"

I'm thinking that the ./video symlink is left over from the old install and is causing the install to bomb out? Where should I look for this link? More importantly, why does it appear to be trying to download an older version?

---

### Post by rhpot1991 on 2009-03-22
> **JerkyChew said:**
> I uninstalled and attempted to reinstall mythexport, here are my latest issues:

1) Mythexport shows up as version 1.99.4-0 in Synaptic, even though I have the mythbuntu-testing Intrepid repos enabled. 

2) Attempting to install fails - I get an error saying "ln: creating symbolic link './video'; File exists and then the GUI error "E: mythexport: subprocess post-installation script returned error exit status 1"

I'm thinking that the ./video symlink is left over from the old install and is causing the install to bomb out? Where should I look for this link? More importantly, why does it appear to be trying to download an older version?

First you should verify your /etc/apt/sources.list contain entries for the Testing PPA for your ubuntu version:
[https://launchpad.net/~mythbuntu-testing/+archive/ppa](https://launchpad.net/~mythbuntu-testing/+archive/ppa)

Someone in IRC hit that same issue with the ~/.video symlink the other day, I have yet to figure out where it is coming from.  Do the following and you should be able to install:
```

sudo dpkg --purge mythexport
sudo rm -rf ~/.video
sudo apt-get update
sudo apt-get install mythexport
```

---

### Post by JerkyChew on 2009-03-22
> **rhpot1991 said:**
> First you should verify your /etc/apt/sources.list contain entries for the Testing PPA for your ubuntu version:
[https://launchpad.net/~mythbuntu-testing/+archive/ppa](https://launchpad.net/~mythbuntu-testing/+archive/ppa)


Not sure if I'm understanding correctly - The only versions of mythexport I see in that list are version 1.99.4-0ubuntu1~ppa11 which is the same version I see in Synaptic. I'm using the repos straight from the mythexport installation instructions, which are:

deb [http://ppa.launchpad.net/mythbuntu-testing/ubuntu](http://ppa.launchpad.net/mythbuntu-testing/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/mythbuntu-testing/ubuntu](http://ppa.launchpad.net/mythbuntu-testing/ubuntu) intrepid main

I'll try the rm -rf now and see what happens :)

Quick update - that seems to have fixed the issue! I believe on the first install I fat-fingered the MySQL password, and on subsequent uninstall/reinstalls it didn't re-prompt me for the password. I wasn't aware of the --purge option. Off to play with this and I will report back!

Incidentally it installed version 1.99.4-0ubuntu1~ppa0.11.

---

### Post by JerkyChew on 2009-03-22
I set up a transcode job and it appeared to be succesful - It showed up in the RSS feed but when I tried viewing it via Firefox I got a file not found. Looking at the file structure it appears there's some kind of symlink loop going on:

matt@magic:/var/lib/mythtv/mythexport/mythexport/mythexport/mythexport$ ls -la
total 8
drwxrwxr-x 2 mythtv mythtv 4096 2009-03-17 20:59 .
drwxr-xr-x 6 root   root   4096 2009-03-17 20:59 ..
lrwxrwxrwx 1 root   root     27 2009-03-17 20:59 mythexport -> /var/lib/mythtv/mythexport/

Thoughts?

---

### Post by rhpot1991 on 2009-03-22
> **JerkyChew said:**
> I set up a transcode job and it appeared to be succesful - It showed up in the RSS feed but when I tried viewing it via Firefox I got a file not found. Looking at the file structure it appears there's some kind of symlink loop going on:

matt@magic:/var/lib/mythtv/mythexport/mythexport/mythexport/mythexport$ ls -la
total 8
drwxrwxr-x 2 mythtv mythtv 4096 2009-03-17 20:59 .
drwxr-xr-x 6 root   root   4096 2009-03-17 20:59 ..
lrwxrwxrwx 1 root   root     27 2009-03-17 20:59 mythexport -> /var/lib/mythtv/mythexport/

Thoughts?

I have verified the circular symlink issue, will be fixed in the next push.  If the info shows up in the RSS feed then ffmpeg should have completed sucessfully, check with the web interface to see where it thinks it should be parking files, and make sure that matches /var/lib/mythtv/mythexport.

---

### Post by joshoekstra on 2009-03-24
I got a problem using mythexport as well, it seems it can't find the export directory:

```
March 24 12:10:22 mythbuntu /usr/bin/mythexport-daemon[12503]: Starting Processing:  1237893022
March 24 12:10:22 mythbuntu /usr/bin/mythexport-daemon[12503]: query = select id, type, param from mythexport_job_queue order by id at line 608 in /usr/bin/mythexport-daemon
Use of uninitialized value $exportdir in concatenation (.) or string at /usr/bin/mythexport-daemon line 133.
March 24 12:10:22 mythbuntu /usr/bin/mythexport-daemon[12503]: exportdir = [COLOR="Red"]MISSING?[/COLOR] at line 133 in /usr/bin/mythexport-daemon
March 24 12:10:22 mythbuntu /usr/bin/mythexport-daemon[12503]: starttime = 2009-03-20 05:00:00 at line 134 in /usr/bin/mythexport-daemon
March 24 12:10:22 mythbuntu /usr/bin/mythexport-daemon[12503]: chanid = 15 at line 135 in /usr/bin/mythexport-daemon
March 24 12:10:22 mythbuntu /usr/bin/mythexport-daemon[12503]: config = iPOD_TEST at line 136 in /usr/bin/mythexport-daemon
Use of uninitialized value $exportdir in substitution (s///) at /usr/bin/mythexport-daemon line 138.
Use of uninitialized value $exportdir in -w at /usr/bin/mythexport-daemon line 147.
Use of uninitialized value $exportdir in concatenation (.) or string at /usr/bin/mythexport-daemon line 147.
March 24 12:10:22 mythbuntu /usr/bin/mythexport-daemon[12503]: ERROR: Directory [COLOR="Red"]MISSING?[/COLOR] is not writeable.
 at line 147 in /usr/bin/mythexport-daemon
Use of uninitialized value $exportdir in concatenation (.) or string at /usr/bin/mythexport-daemon line 148.
Can't use an undefined value as a symbol reference at /usr/bin/mythexport-daemon line 158.
```

I pointed it to one of my shares where the user mythtv:mythtv has read and write privileges. The problem seems to be in the part where $exportdir gets defined. I'm not even sure if it reads:
```
/etc/mythtv/mythexport/mythexport.cfg
```
So I tried to ad the dir=.... to mythexport_settings.cfg, but that didn't work either.
This is with a completely clean install on intrepid.
The version is  1.99.4-0ubuntu1~ppa0.11

---

### Post by paulbawon on 2009-03-24
I have exactly the same problem as mentioned above.

---

### Post by rhpot1991 on 2009-03-24
> **joshoekstra said:**
> I got a problem using mythexport as well, it seems it can't find the export directory:

```
March 24 12:10:22 mythbuntu /usr/bin/mythexport-daemon[12503]: Starting Processing:  1237893022
March 24 12:10:22 mythbuntu /usr/bin/mythexport-daemon[12503]: query = select id, type, param from mythexport_job_queue order by id at line 608 in /usr/bin/mythexport-daemon
Use of uninitialized value $exportdir in concatenation (.) or string at /usr/bin/mythexport-daemon line 133.
March 24 12:10:22 mythbuntu /usr/bin/mythexport-daemon[12503]: exportdir = [COLOR="Red"]MISSING?[/COLOR] at line 133 in /usr/bin/mythexport-daemon
March 24 12:10:22 mythbuntu /usr/bin/mythexport-daemon[12503]: starttime = 2009-03-20 05:00:00 at line 134 in /usr/bin/mythexport-daemon
March 24 12:10:22 mythbuntu /usr/bin/mythexport-daemon[12503]: chanid = 15 at line 135 in /usr/bin/mythexport-daemon
March 24 12:10:22 mythbuntu /usr/bin/mythexport-daemon[12503]: config = iPOD_TEST at line 136 in /usr/bin/mythexport-daemon
Use of uninitialized value $exportdir in substitution (s///) at /usr/bin/mythexport-daemon line 138.
Use of uninitialized value $exportdir in -w at /usr/bin/mythexport-daemon line 147.
Use of uninitialized value $exportdir in concatenation (.) or string at /usr/bin/mythexport-daemon line 147.
March 24 12:10:22 mythbuntu /usr/bin/mythexport-daemon[12503]: ERROR: Directory [COLOR="Red"]MISSING?[/COLOR] is not writeable.
 at line 147 in /usr/bin/mythexport-daemon
Use of uninitialized value $exportdir in concatenation (.) or string at /usr/bin/mythexport-daemon line 148.
Can't use an undefined value as a symbol reference at /usr/bin/mythexport-daemon line 158.
```

I pointed it to one of my shares where the user mythtv:mythtv has read and write privileges. The problem seems to be in the part where $exportdir gets defined. I'm not even sure if it reads:
```
/etc/mythtv/mythexport/mythexport.cfg
```
So I tried to ad the dir=.... to mythexport_settings.cfg, but that didn't work either.
This is with a completely clean install on intrepid.
The version is  1.99.4-0ubuntu1~ppa0.11

It looks like you are doing an OTG export?  Did you specify a location in the web interface on the otg.cgi page?

---

### Post by deffertz on 2009-03-24
I can verify the same exact problem as paulbowan and joshoekstra.  I am **not** using On the Go and have not touched it.  Is there anything I can do to purge the OTG?

---

### Post by joshoekstra on 2009-03-24
On the system setup page I entered a directory, which is owned, readable and writable by the mythtv-user. A normal job entered via mythfrontend doesn't finish either, the errors indicate a script-problem with uninitialized errors...

---

### Post by rhpot1991 on 2009-03-24
If both of your errors are happening on the same lines as the ones pasted above then it is within the OTG Lightweight code.  Can you retrieve what is in your mythexport_user_job table:
```

mysql -u<user> -p mythconverg

mysql> select * from mythexport_job_queue;
```

---

### Post by joshoekstra on 2009-03-24
> **rhpot1991 said:**
> If both of your errors are happening on the same lines as the ones pasted above then it is within the OTG Lightweight code.  Can you retrieve what is in your mythexport_user_job table:
```

mysql -u<user> -p mythconverg

mysql> select * from mythexport_job_queue;
```

The output on the same file, one via mythtv_job, other via OTG:
```

mysql> select * from mythexport_job_queue;
+----+----------+---------------------------------------------------------------+---------------------+
| id | type     | param                                                         | description         |
+----+----------+---------------------------------------------------------------+---------------------+
| 26 | otg-full | chanid=15&starttime=2009-03-20 05:00:00&block=ipod&exportdir= | Total Recordings: 1 | 
| 25 | export   | starttime=20090320050000&chanid=15&config=ipod                | Cursus Spaans:      | 
+----+----------+---------------------------------------------------------------+---------------------+

```
the one with id=25 seems to be running fine for now.

I'll first run a normal job, cause you're right I only ran a OTG job, but my jobs run after 23:00 because of electricity costs ;)
Now my tuners are all busy so changing the job-time cannot be done, probably in a couple of hours.
I'll delete the otg-job first and then run the job from mythtv.
Ok I'v run a 'normal' job and otg, first the normal one:
```

Use of uninitialized value $args in split at /usr/bin/mythexport-daemon line 377.
March 25 00:49:16 mythbuntu /usr/bin/mythexport-daemon[20737]: exportdir = /bigdisk/share/recorded at line 400 in /usr/bin/mythexport-daemon
March 25 00:49:16 mythbuntu /usr/bin/mythexport-daemon[20737]: starttime = 20090323204500 at line 401 in /usr/bin/mythexport-daemon
March 25 00:49:16 mythbuntu /usr/bin/mythexport-daemon[20737]: chanid = 3002 at line 402 in /usr/bin/mythexport-daemon
March 25 00:49:16 mythbuntu /usr/bin/mythexport-daemon[20737]: config = iPOD_TEST at line 403 in /usr/bin/mythexport-daemon
March 25 00:49:16 mythbuntu /usr/bin/mythexport-daemon[20737]: query = SELECT rec.title, rec.subtitle, rec.description, pg.syndicatedepisodenumber, pg.showtype, rec.programid, rec.basename, rec.starttime
    FROM recorded rec LEFT JOIN program pg ON pg.starttime = rec.starttime AND pg.chanid = rec.chanid
    WHERE rec.chanid=? AND rec.starttime=? at line 417 in /usr/bin/mythexport-daemon
March 25 00:49:16 mythbuntu /usr/bin/mythexport-daemon[20737]: Going into new mode
 at line 434 in /usr/bin/mythexport-daemon
March 25 00:49:16 mythbuntu /usr/bin/mythexport-daemon[20737]: query = SELECT callsign FROM channel WHERE chanid=? at line 442 in /usr/bin/mythexport-daemon
Use of uninitialized value $syndicatedepisodenumber in pattern match (m//) at /usr/bin/mythexport-daemon line 466.
Use of uninitialized value $exportdevice in string eq at /usr/bin/mythexport-daemon line 486.
Use of uninitialized value $exportdevice in string eq at /usr/bin/mythexport-daemon line 486.
Use of uninitialized value $exportdevice in string eq at /usr/bin/mythexport-daemon line 486.
Use of uninitialized value $exportdevice in string ne at /usr/bin/mythexport-daemon line 514.
Use of uninitialized value $exportcodec in string ne at /usr/bin/mythexport-daemon line 514.
Use of uninitialized value $exportdevice in string ne at /usr/bin/mythexport-daemon line 514.
Use of uninitialized value $episodenumber in concatenation (.) or string at /usr/bin/mythexport-daemon line 515.
Use of uninitialized value $seasonnumber in concatenation (.) or string at /usr/bin/mythexport-daemon line 515.
March 25 00:49:16 mythbuntu /usr/bin/mythexport-daemon[20737]: command = AtomicParsley '/bigdisk/share/recorded/NL2-Tegenlicht_Hoogvliegen_in_laagland_experts_over_onderwi.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork NL2 --TVShowName "Tegenlicht: Hoogvliegen in laagland: experts over onderwijs en excellence" --TVEpisode "" --TVEpisodeNum  --TVSeason  --description "Thema: Excellence." --title "" 2>&1 at line 555 in /usr/bin/mythexport-daemon
March 25 00:49:16 mythbuntu /usr/bin/mythexport-daemon[20737]: ERROR: AtomicParsley '/bigdisk/share/recorded/NL2-Tegenlicht_Hoogvliegen_in_laagland_experts_over_onderwi.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork NL2 --TVShowName "Tegenlicht: Hoogvliegen in laagland: experts over onderwijs en excellence" --TVEpisode "" --TVEpisodeNum  --TVSeason  --description "Thema: Excellence." --title "" 2>&1 FAILED at line 556 in /usr/bin/mythexport-daemon
rm: cannot remove `/bigdisk/share/recorded/NL2-Tegenlicht_Hoogvliegen_in_laagland_experts_over_onderwi.mp4': No such file or directory
mv: cannot stat `/bigdisk/share/recorded/*temp*': No such file or directory
March 25 00:49:16 mythbuntu /usr/bin/mythexport-daemon[20737]: ERROR: /bigdisk/share/recorded/NL2-Tegenlicht_Hoogvliegen_in_laagland_experts_over_onderwi.mp4 is not available at line 564 in /usr/bin/mythexport-daemon
Use of uninitialized value $otg in string ne at /usr/bin/mythexport-daemon line 566.
March 25 00:49:16 mythbuntu /usr/bin/mythexport-daemon[20737]: query = INSERT into mythexport VALUES(NULL,?,?,?,?,NOW(),DATE_ADD(NOW(),INTERVAL ? DAY),?,?) at line 570 in /usr/bin/mythexport-daemon

```
Here it seems the exportdir is set correctly, however, nothing shows up in the expected directory. Looking into it further, it seems that recordings made from DVB-T end up wrong, recording made with a PVR from Hauppauge go right.
By running:
```

ffmpeg -i /bigdisk/video/hauppauge_PVR.mpg -y -acodec libfaac -ab 160kb -vcodec mpeg4 -b 600kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x240 -aspect 16:9 '/bigdisk/share/recorded/output.mp4'

```
ffmpeg seems to run fine, so I'm sorry to say that it seems to be an config-error. I would appreciate it if people from the Netherlands could give their rule for DVB-T recordings.
Maybe there is a possibiltiy to add more verbose ouptut than the verbose option gives out now?
The OTG I didn't look further into, that's less interesting for me right now. But the difference there seems to be that the exportdir doesn't get set at all.

OTG with same export-settings, kind of file and export-dir(?):
```

Use of uninitialized value $exportdir in concatenation (.) or string at /usr/bin/mythexport-daemon line 133.
March 25 13:16:36 mythbuntu /usr/bin/mythexport-daemon[20737]: exportdir =  at line 133 in /usr/bin/mythexport-daemon
March 25 13:16:36 mythbuntu /usr/bin/mythexport-daemon[20737]: starttime = 2009-03-23 20:45:00 at line 134 in /usr/bin/mythexport-daemon
March 25 13:16:36 mythbuntu /usr/bin/mythexport-daemon[20737]: chanid = 2 at line 135 in /usr/bin/mythexport-daemon
March 25 13:16:36 mythbuntu /usr/bin/mythexport-daemon[20737]: config = ipod at line 136 in /usr/bin/mythexport-daemon
Use of uninitialized value $exportdir in substitution (s///) at /usr/bin/mythexport-daemon line 138.
Use of uninitialized value $exportdir in -w at /usr/bin/mythexport-daemon line 147.
Use of uninitialized value $exportdir in concatenation (.) or string at /usr/bin/mythexport-daemon line 147.
March 25 13:16:36 mythbuntu /usr/bin/mythexport-daemon[20737]: ERROR: Directory  is not writeable.
 at line 147 in /usr/bin/mythexport-daemon
Use of uninitialized value $exportdir in concatenation (.) or string at /usr/bin/mythexport-daemon line 148.
Can't use an undefined value as a symbol reference at /usr/bin/mythexport-daemon line 158.

```

---

### Post by paulbawon on 2009-03-25
I'm now hitting an extremely annoying error that is preventing MythExport from finishing its encoding work and updating my RSS feed.

Looking at my logs I am getting the following message over and over again:

```
DBD::mysql::st execute failed: MySQL server has gone away at /usr/bin/mythexport-daemon line 571.
```

It seems to me that the period between the script issuing its 'connect' command to the database and it actually inputting the data is so big that it is loosing its connection. This is because the encoding process is taking a long time.

Can you update the script to include the connect command before each query of the database, so as to wake this connection up?

---

### Post by rhpot1991 on 2009-03-25
> **paulbawon said:**
> I'm now hitting an extremely annoying error that is preventing MythExport from finishing its encoding work and updating my RSS feed.

Looking at my logs I am getting the following message over and over again:

```
DBD::mysql::st execute failed: MySQL server has gone away at /usr/bin/mythexport-daemon line 571.
```

It seems to me that the period between the script issuing its 'connect' command to the database and it actually inputting the data is so big that it is loosing its connection. This is because the encoding process is taking a long time.

Can you update the script to include the connect command before each query of the database, so as to wake this connection up?

Generally when this happens then the MySQL server isn't running, have you verified that it is?  You may want to try cleaning/optimizing your tables in mythweb, then try again.

---

### Post by paulbawon on 2009-03-25
> **rhpot1991 said:**
> Generally when this happens then the MySQL server isn't running, have you verified that it is?  You may want to try cleaning/optimizing your tables in mythweb, then try again.

Yep, it's running - I can connect to it fine and my config.xml are all present and correct.

It doesn't happen if I pick .mp4 single pass encoding, only on two-pass, which leads me to believe it is to do with the delay in the encoding process.

Is there a 'keep-alive' command that can be issued whilst it is encoding?

---

### Post by rhpot1991 on 2009-03-25
> **joshoekstra said:**
> 
I'll first run a normal job, cause you're right I only ran a OTG job, but my jobs run after 23:00 because of electricity costs ;)
Now my tuners are all busy so changing the job-time cannot be done, probably in a couple of hours.
I'll delete the otg-job first and then run the job from mythtv.
Ok I'v run a 'normal' job and otg, first the normal one:
```

Use of uninitialized value $args in split at /usr/bin/mythexport-daemon line 377.
March 25 00:49:16 mythbuntu /usr/bin/mythexport-daemon[20737]: exportdir = /bigdisk/share/recorded at line 400 in /usr/bin/mythexport-daemon
March 25 00:49:16 mythbuntu /usr/bin/mythexport-daemon[20737]: starttime = 20090323204500 at line 401 in /usr/bin/mythexport-daemon
March 25 00:49:16 mythbuntu /usr/bin/mythexport-daemon[20737]: chanid = 3002 at line 402 in /usr/bin/mythexport-daemon
March 25 00:49:16 mythbuntu /usr/bin/mythexport-daemon[20737]: config = iPOD_TEST at line 403 in /usr/bin/mythexport-daemon
March 25 00:49:16 mythbuntu /usr/bin/mythexport-daemon[20737]: query = SELECT rec.title, rec.subtitle, rec.description, pg.syndicatedepisodenumber, pg.showtype, rec.programid, rec.basename, rec.starttime
    FROM recorded rec LEFT JOIN program pg ON pg.starttime = rec.starttime AND pg.chanid = rec.chanid
    WHERE rec.chanid=? AND rec.starttime=? at line 417 in /usr/bin/mythexport-daemon
March 25 00:49:16 mythbuntu /usr/bin/mythexport-daemon[20737]: Going into new mode
 at line 434 in /usr/bin/mythexport-daemon
March 25 00:49:16 mythbuntu /usr/bin/mythexport-daemon[20737]: query = SELECT callsign FROM channel WHERE chanid=? at line 442 in /usr/bin/mythexport-daemon
Use of uninitialized value $syndicatedepisodenumber in pattern match (m//) at /usr/bin/mythexport-daemon line 466.
Use of uninitialized value $exportdevice in string eq at /usr/bin/mythexport-daemon line 486.
Use of uninitialized value $exportdevice in string eq at /usr/bin/mythexport-daemon line 486.
Use of uninitialized value $exportdevice in string eq at /usr/bin/mythexport-daemon line 486.
Use of uninitialized value $exportdevice in string ne at /usr/bin/mythexport-daemon line 514.
Use of uninitialized value $exportcodec in string ne at /usr/bin/mythexport-daemon line 514.
Use of uninitialized value $exportdevice in string ne at /usr/bin/mythexport-daemon line 514.
Use of uninitialized value $episodenumber in concatenation (.) or string at /usr/bin/mythexport-daemon line 515.
Use of uninitialized value $seasonnumber in concatenation (.) or string at /usr/bin/mythexport-daemon line 515.
March 25 00:49:16 mythbuntu /usr/bin/mythexport-daemon[20737]: command = AtomicParsley '/bigdisk/share/recorded/NL2-Tegenlicht_Hoogvliegen_in_laagland_experts_over_onderwi.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork NL2 --TVShowName "Tegenlicht: Hoogvliegen in laagland: experts over onderwijs en excellence" --TVEpisode "" --TVEpisodeNum  --TVSeason  --description "Thema: Excellence." --title "" 2>&1 at line 555 in /usr/bin/mythexport-daemon
March 25 00:49:16 mythbuntu /usr/bin/mythexport-daemon[20737]: ERROR: AtomicParsley '/bigdisk/share/recorded/NL2-Tegenlicht_Hoogvliegen_in_laagland_experts_over_onderwi.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork NL2 --TVShowName "Tegenlicht: Hoogvliegen in laagland: experts over onderwijs en excellence" --TVEpisode "" --TVEpisodeNum  --TVSeason  --description "Thema: Excellence." --title "" 2>&1 FAILED at line 556 in /usr/bin/mythexport-daemon
rm: cannot remove `/bigdisk/share/recorded/NL2-Tegenlicht_Hoogvliegen_in_laagland_experts_over_onderwi.mp4': No such file or directory
mv: cannot stat `/bigdisk/share/recorded/*temp*': No such file or directory
March 25 00:49:16 mythbuntu /usr/bin/mythexport-daemon[20737]: ERROR: /bigdisk/share/recorded/NL2-Tegenlicht_Hoogvliegen_in_laagland_experts_over_onderwi.mp4 is not available at line 564 in /usr/bin/mythexport-daemon
Use of uninitialized value $otg in string ne at /usr/bin/mythexport-daemon line 566.
March 25 00:49:16 mythbuntu /usr/bin/mythexport-daemon[20737]: query = INSERT into mythexport VALUES(NULL,?,?,?,?,NOW(),DATE_ADD(NOW(),INTERVAL ? DAY),?,?) at line 570 in /usr/bin/mythexport-daemon

```

I don't see any ffmpeg info in here, is this portion of the log complete?  It should say Exporting: <whatever> then the ffmpeg line.  I'll have to look into why thats not happening.

> **joshoekstra said:**
> 
Here it seems the exportdir is set correctly, however, nothing shows up in the expected directory. Looking into it further, it seems that recordings made from DVB-T end up wrong, recording made with a PVR from Hauppauge go right.
By running:
```

ffmpeg -i /bigdisk/video/hauppauge_PVR.mpg -y -acodec libfaac -ab 160kb -vcodec mpeg4 -b 600kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x240 -aspect 16:9 '/bigdisk/share/recorded/output.mp4'

```

ffmpeg seems to run fine, so I'm sorry to say that it seems to be an config-error. I would appreciate it if people from the Netherlands could give their rule for DVB-T recordings.
Maybe there is a possibiltiy to add more verbose ouptut than the verbose option gives out now?

Try making a separate config for your DVB recordings, make all the settings the same, but add a 2 to 'audio channels'.  I have had some reports of that helping DVB recordings in the past.

> **joshoekstra said:**
> 
The OTG I didn't look further into, that's less interesting for me right now. But the difference there seems to be that the exportdir doesn't get set at all.

You are absolutely positive that you defined one in the web interface?  This will not inherit the directory used above and uses its own on a per job basis instead (designed this way so you can plug in a usb hard drive and export to that).

---

### Post by rhpot1991 on 2009-03-25
> **paulbawon said:**
> Yep, it's running - I can connect to it fine and my config.xml are all present and correct.

It doesn't happen if I pick .mp4 single pass encoding, only on two-pass, which leads me to believe it is to do with the delay in the encoding process.

Is there a 'keep-alive' command that can be issued whilst it is encoding?

I'd recommend tweaking some of the MySQL times at this point:
[http://www.mythtv.org/wiki/Troubleshooting:MySQL_server_has_gone_away](http://www.mythtv.org/wiki/Troubleshooting:MySQL_server_has_gone_away)

I'll take into account I need to be more mindful of the connection for the next version, I don't think I'd be able to get that big of a change in at this point as we are already beyond the Feature Freeze.

Let me know if tweaking those numbers helps with the issue.

---

### Post by joshoekstra on 2009-03-26
> **rhpot1991 said:**
> I don't see any ffmpeg info in here, is this portion of the log complete?  It should say Exporting: <whatever> then the ffmpeg line.  I'll have to look into why thats not happening.


That was the thing, it didn't. Later on I edited the exportconfig and then it did run. I'm thinking it was a configuration-erro on my behalf :-|
> 

Try making a separate config for your DVB recordings, make all the settings the same, but add a 2 to 'audio channels'.  I have had some reports of that helping DVB recordings in the past.

[/QOUTE]
I'll do that, the PVR ones seem to run fine
[QOUTE]

You are absolutely positive that you defined one in the web interface?  This will not inherit the directory used above and uses its own on a per job basis instead (designed this way so you can plug in a usb hard drive and export to that).

Well......
nope, after doing that the full-featured one runs fine, but the light-weight one doesn't. It creates the xml and css, but not the sql and doesn't transcode the file with the now working profile.
I'll first try some stuff on my own to see what config-errors I still got.

If I didn't tell you before, I'll do it now: I love this thing! :)

---

### Post by paulbawon on 2009-03-26
> **rhpot1991 said:**
> I'd recommend tweaking some of the MySQL times at this point:
[http://www.mythtv.org/wiki/Troubleshooting:MySQL_server_has_gone_away](http://www.mythtv.org/wiki/Troubleshooting:MySQL_server_has_gone_away)

I'll take into account I need to be more mindful of the connection for the next version, I don't think I'd be able to get that big of a change in at this point as we are already beyond the Feature Freeze.

Let me know if tweaking those numbers helps with the issue.

Thanks, adjusting the MYSQL configs as suggest in that link solved it.

---

### Post by JerkyChew on 2009-03-26
> **rhpot1991 said:**
> I have verified the circular symlink issue, will be fixed in the next push.  If the info shows up in the RSS feed then ffmpeg should have completed sucessfully, check with the web interface to see where it thinks it should be parking files, and make sure that matches /var/lib/mythtv/mythexport.

From /var/www/mythexport if I ls -la my video symlink looks like
 video -> /var/lib/mythtv/mythexport/

And then if I go to var/lib/mythtv/mythexport and ls -la I get:
 mythexport -> /var/lib/mythtv/mythexport/

In the web interface under [http://magic/mythexport/rss.cgi](http://magic/mythexport/rss.cgi) It has a link to [http://magic/mythexport/video/COMEDY-The_Daily_Show_With_Jon_Stewart--20090309230000.mp4](http://magic/mythexport/video/COMEDY-The_Daily_Show_With_Jon_Stewart--20090309230000.mp4) but I get a file not found.

---

### Post by rhpot1991 on 2009-03-30
> **JerkyChew said:**
> From /var/www/mythexport if I ls -la my video symlink looks like
 video -> /var/lib/mythtv/mythexport/

And then if I go to var/lib/mythtv/mythexport and ls -la I get:
 mythexport -> /var/lib/mythtv/mythexport/

In the web interface under [http://magic/mythexport/rss.cgi](http://magic/mythexport/rss.cgi) It has a link to [http://magic/mythexport/video/COMEDY-The_Daily_Show_With_Jon_Stewart--20090309230000.mp4](http://magic/mythexport/video/COMEDY-The_Daily_Show_With_Jon_Stewart--20090309230000.mp4) but I get a file not found.

Did you check /etc/mythtv/mythexport/mythexport.cfg to see where that is pointing at?  It sounds like there is a desync between where the files are being dumped and where the RSS feed thinks they are.  /var/www/mythexport/video will be a symlink, perhaps it is pointing to the wrong spot?

---

### Post by muffinito on 2009-04-11
Hello, every time that I try to upgrade to mythexport 2.0 using both apt-get and synaptic, I got an error (crash).

Mythbuntu 9.04 beta amd64. I am using an DG945GCLF2 intel board.

---

### Post by rhpot1991 on 2009-04-13
> **muffinito said:**
> Hello, every time that I try to upgrade to mythexport 2.0 using both apt-get and synaptic, I got an error (crash).

Mythbuntu 9.04 beta amd64. I am using an DG945GCLF2 intel board.

Can you provide any additional information about this?  Such as: what exact version of mythexport, what exactly the error is, are you doing a fresh install or an upgrade of mythexport?

---

### Post by muffinito on 2009-04-15
user@pvr:~$ sudo apt-get remove mythexport
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  mythexport
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 283kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 117724 files and directories currently installed.)
Removing mythexport ...
 * Reloading web server config apache2                                          apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
 * Stopping MythExport Daemon: mythexport                                       No /usr/bin/perl found running; none killed.
                                                                         [ OK ]
Processing triggers for man-db ...
user@pvr:~$ sudo apt-get install mythexport
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  mythexport
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/29.0kB of archives.
After this operation, 283kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package mythexport.
(Reading database ... 117687 files and directories currently installed.)
Unpacking mythexport (from .../mythexport_2.0-0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up mythexport (2.0-0ubuntu1) ...
ln: creating symbolic link `./video': File exists
dpkg: error processing mythexport (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mythexport
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by rhpot1991 on 2009-04-15
> **muffinito said:**
> user@pvr:~$ sudo apt-get remove mythexport
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  mythexport
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 283kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 117724 files and directories currently installed.)
Removing mythexport ...
 * Reloading web server config apache2                                          apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
 * Stopping MythExport Daemon: mythexport                                       No /usr/bin/perl found running; none killed.
                                                                         [ OK ]
Processing triggers for man-db ...
user@pvr:~$ sudo apt-get install mythexport
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  mythexport
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/29.0kB of archives.
After this operation, 283kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package mythexport.
(Reading database ... 117687 files and directories currently installed.)
Unpacking mythexport (from .../mythexport_2.0-0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up mythexport (2.0-0ubuntu1) ...
ln: creating symbolic link `./video': File exists
dpkg: error processing mythexport (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mythexport
E: Sub-process /usr/bin/dpkg returned an error code (1)

Check for ~/.video
I am betting its a circular reference to itself.  Go ahead and delete it if it exists and doesn't contain anything that you care about, should be able to install then.  Do you recall if you picked a location when it asked you where to save exported recordings?  I'll have to dig some more, I thought this issue was resolved but it looks like it might not be :(

---

### Post by minirx7 on 2009-04-15
> **rhpot1991 said:**
> Check for ~/.video
I am betting its a circular reference to itself.  Go ahead and delete it if it exists and doesn't contain anything that you care about, should be able to install then.  Do you recall if you picked a location when it asked you where to save exported recordings?  I'll have to dig some more, I thought this issue was resolved but it looks like it might not be :(

I have the exact same issue and i cant find this ~/.video file, therefore will not install.

---

### Post by rhpot1991 on 2009-04-15
> **minirx7 said:**
> I have the exact same issue and i cant find this ~/.video file, therefore will not install.

Are you a fresh install or an upgrade of MythExport?

anything that starts with . will be hidden, so do this to see if it exists:
```
ls -lah ~/.video
```
The output of this may be helpful as well:
```
locate .video
```

---

### Post by minirx7 on 2009-04-15
> **rhpot1991 said:**
> Are you a fresh install or an upgrade of MythExport?

anything that starts with . will be hidden, so do this to see if it exists:
```
ls -lah ~/.video
```
The output of this may be helpful as well:
```
locate .video
```

Actually you have to do two things:

you have to remove "video" from the / folder

then you have to remove "/var/www/.mythtv/config.xml" (i think thats the path) as well

I was able to succesfully install mythexport, however now it won't run when the user job is initated.

mythexport.log show sthe following entry:
Couldn't communicate with 127.0.0.1 on port 6543:  IO::Socket::INET::MythTV:  connect:  Connection refused

---

### Post by rhpot1991 on 2009-04-15
> **minirx7 said:**
> Actually you have to do two things:

you have to remove "video" from the / folder

then you have to remove "/var/www/.mythtv/config.xml" (i think thats the path) as well

I was able to succesfully install mythexport, however now it won't run when the user job is initated.

mythexport.log show sthe following entry:
Couldn't communicate with 127.0.0.1 on port 6543:  IO::Socket::INET::MythTV:  connect:  Connection refused

You are going to want to see the config.xml section in the wiki, /var/www/.mythtv/config.xml needs to point to a valid config otherwise the bindings don't know how to communicate with your backend.  Starting in Jaunty there should be a default config in /etc/mythtv/config.xml, otherwise point at the one in your ~/.mythtv/ directory.

---

### Post by minirx7 on 2009-04-15
> **rhpot1991 said:**
> You are going to want to see the config.xml section in the wiki, /var/www/.mythtv/config.xml needs to point to a valid config otherwise the bindings don't know how to communicate with your backend.  Starting in Jaunty there should be a default config in /etc/mythtv/config.xml, otherwise point at the one in your ~/.mythtv/ directory.

Actually i am pretty much a newbie when it comes to linux, however i just copied my config.xml file in all the locations.  This is what is in my config.xml under /var/www/.mythtv/config.xml

Interestingly, i dont think the DBPassword is correct, as i remember during mythbuntu setup, i did specify a password.  will give that shot.



<Configuration>
  <UPnP>
    <UDN>
      <MediaRenderer>c74a60b2-e640-4bb5-84f5-dc2c20cf6771</MediaRenderer>
    </UDN>
    <MythFrontend>
      <DefaultBackend>
        <DBHostName>localhost</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>C1RFOKlE</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>0</DBPort>
      </DefaultBackend>
    </MythFrontend>
  </UPnP>
</Configuration>

---

### Post by muffinito on 2009-04-16
no .video here too.

user@pvr:~$ pwd
/home/user
user@pvr:~$ ls .video
ls: cannot access .video: No such file or directory
user@pvr:~$ ls ~/.video
ls: cannot access /home/user/.video: No such file or directory
user@pvr:~$ ls -lah ~/.video
ls: cannot access /home/user/.video: No such file or directory
user@pvr:~$ locate .video
/usr/share/doc/kbd/cirrus.videomodes
/usr/share/doc/toshset/README.video
user@pvr:~$ 

unfortunately I dont remember about the installation details but is very likely that I choose the defaults.

Thank you

---

### Post by johnelle on 2009-04-18
Getting a syntax error when the transcode starts:

```
2009-04-18 09:15:25.121 Preview: Grabbed preview '/var/lib/mythtv/recordings/1007_20090418083200.mpg' 720x480@64s
2009-04-18 09:16:03.588 JobQueue: Started "Export to Ipod (Medium)" for "Today" recorded from channel 1007 at Sat Apr 18 08:32:00 2009
sh: Syntax error: "(" unexpected
2009-04-18 09:16:03.603 JobQueue: Finished "Export to Ipod (Medium)" for "Today" recorded from channel 1007 at Sat Apr 18 08:32:00 2009.
```

I was just using the settings from the old directions including the name.  I will try a name without "("s in the chance that this causing the problem.

---

### Post by johnelle on 2009-04-18
Oops...I was reading the wrong file.

I got around my config issues by tinkering (hacking?)

I am getting better at manual clean-up but apt-get purge would work better if you did a rm -rf on the .mythtv directory.

---

### Post by johnelle on 2009-04-19
I can only get transcodes working with the ipod target.  All others fail.  

For example if I try an xvid codec / pc target I get:

```
April 19 09:02:20 mythtv /usr/bin/mythexport-daemon[5538]: ERROR: AtomicParsley '/podcast/WMUR-News_9_This_Morning--20090419085700.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork WMUR --TVShowName "News 9 This Morning" --TVEpisode "SH006434360000" --TVEpisodeNum  --TVSeason  --description "" --title "" 2>&1 FAILED at line 555 in /usr/bin/mythexport-daemon
rm: cannot remove `/podcast/WMUR-News_9_This_Morning--20090419085700.mp4': No such file or directory
mv: cannot stat `/podcast/*temp*': No such file or directory
April 19 09:02:20 mythtv /usr/bin/mythexport-daemon[5538]: ERROR: /podcast/WMUR-News_9_This_Morning--20090419085700.mp4 is not available at line 563 in /usr/bin/mythexport-daemon

```

in the log file.

I also tried to use "Custom" and just specified **-target dvd** to let ffmpeg set the parameters for me.  That died with a similiar issue.

Has anyone been able to do anything other than ipod/mp4?

I checked the ffmpeg that comes with mythbuntu and it reports many many formats.

---

### Post by johnelle on 2009-04-19
On any codec other than mp4 I get the AtomicParsley error.

---

### Post by minirx7 on 2009-04-20
> **johnelle said:**
> Getting a syntax error when the transcode starts:

```
2009-04-18 09:15:25.121 Preview: Grabbed preview '/var/lib/mythtv/recordings/1007_20090418083200.mpg' 720x480@64s
2009-04-18 09:16:03.588 JobQueue: Started "Export to Ipod (Medium)" for "Today" recorded from channel 1007 at Sat Apr 18 08:32:00 2009
sh: Syntax error: "(" unexpected
2009-04-18 09:16:03.603 JobQueue: Finished "Export to Ipod (Medium)" for "Today" recorded from channel 1007 at Sat Apr 18 08:32:00 2009.
```

I was just using the settings from the old directions including the name.  I will try a name without "("s in the chance that this causing the problem.


How did you get past that error?  I keep getting the exact error you are mentioning with the "("s

---

### Post by rhpot1991 on 2009-04-20
> **johnelle said:**
> I can only get transcodes working with the ipod target.  All others fail.  

For example if I try an xvid codec / pc target I get:

```
April 19 09:02:20 mythtv /usr/bin/mythexport-daemon[5538]: ERROR: AtomicParsley '/podcast/WMUR-News_9_This_Morning--20090419085700.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork WMUR --TVShowName "News 9 This Morning" --TVEpisode "SH006434360000" --TVEpisodeNum  --TVSeason  --description "" --title "" 2>&1 FAILED at line 555 in /usr/bin/mythexport-daemon
rm: cannot remove `/podcast/WMUR-News_9_This_Morning--20090419085700.mp4': No such file or directory
mv: cannot stat `/podcast/*temp*': No such file or directory
April 19 09:02:20 mythtv /usr/bin/mythexport-daemon[5538]: ERROR: /podcast/WMUR-News_9_This_Morning--20090419085700.mp4 is not available at line 563 in /usr/bin/mythexport-daemon

```

in the log file.

I also tried to use "Custom" and just specified **-target dvd** to let ffmpeg set the parameters for me.  That died with a similiar issue.

Has anyone been able to do anything other than ipod/mp4?

I checked the ffmpeg that comes with mythbuntu and it reports many many formats.

You should enable debugging in MythExport as noted here:
[https://help.ubuntu.com/community/MythExport#Troubleshooting](https://help.ubuntu.com/community/MythExport#Troubleshooting)

Then check your logs for the ffmpeg command it runs, copy that and execute it by hand.  Odds are you need to tweak your ffmpeg args.  I have tried to leave this as wide open as possible so that anyone can use MythExport for any device they want, as a results its pretty easy to give ffmpeg args that it is unhappy about.

---

### Post by johnelle on 2009-04-24
> **minirx7 said:**
> How did you get past that error?  I keep getting the exact error you are mentioning with the "("s
That wasn't actually a fatal error.  It appears in the mythtv log but the real fatal error was found in the mythexport log.

---

### Post by johnelle on 2009-04-25
> **rhpot1991 said:**
> You should enable debugging in MythExport as noted here:
[https://help.ubuntu.com/community/MythExport#Troubleshooting](https://help.ubuntu.com/community/MythExport#Troubleshooting)

Then check your logs for the ffmpeg command it runs, copy that and execute it by hand.  Odds are you need to tweak your ffmpeg args.  I have tried to leave this as wide open as possible so that anyone can use MythExport for any device they want, as a results its pretty easy to give ffmpeg args that it is unhappy about.

Ok I did that but it doesn't really help because the error is **NOT in the ffmpeg**--it dies in the parser (atomicparsley).  Here is the trace with the additional information but I am not really going to dive into debugging the script. 
 
```
April 25 15:44:15 mythtv /usr/bin/mythexport-daemon[32468]: query = select id, type, param from mythexport_job_queue order by id at line 607 in /usr/bin/mythexport-daemon
April 25 15:44:15 mythtv /usr/bin/mythexport-daemon[32468]: exportdir = /podcast at line 396 in /usr/bin/mythexport-daemon
April 25 15:44:15 mythtv /usr/bin/mythexport-daemon[32468]: starttime = 20090425150100 at line 397 in /usr/bin/mythexport-daemon
April 25 15:44:15 mythtv /usr/bin/mythexport-daemon[32468]: chanid = 1002 at line 398 in /usr/bin/mythexport-daemon
April 25 15:44:15 mythtv /usr/bin/mythexport-daemon[32468]: config = Xvid at line 399 in /usr/bin/mythexport-daemon
April 25 15:44:15 mythtv /usr/bin/mythexport-daemon[32468]: query = SELECT rec.title, rec.subtitle, rec.description, pg.syndicatedepisodenumber, pg.showtype, rec.programid, rec.basename, rec.starttime
    FROM recorded rec LEFT JOIN program pg ON pg.starttime = rec.starttime AND pg.chanid = rec.chanid
    WHERE rec.chanid=? AND rec.starttime=? at line 413 in /usr/bin/mythexport-daemon
April 25 15:44:15 mythtv /usr/bin/mythexport-daemon[32468]: Going into new mode
 at line 430 in /usr/bin/mythexport-daemon
April 25 15:44:15 mythtv /usr/bin/mythexport-daemon[32468]: query = SELECT callsign FROM channel WHERE chanid=? at line 438 in /usr/bin/mythexport-daemon
April 25 15:44:15 mythtv /usr/bin/mythexport-daemon[32468]: command = AtomicParsley '/podcast/WGBH-American_Masters-Pete_Seeger_The_Power_of_Song-2009042.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork WGBH --TVShowName "American Masters" --TVEpisode "EP000002880163" --TVEpisodeNum  --TVSeason  --description "Artists from Bob Dylan to the Dixie Chicks relay stories of folk singer Pete Seeger, often misunderstood by critics because of his views on peace, civil rights and ecology." --title "Pete Seeger: The Power of Song" 2>&1 at line 554 in /usr/bin/mythexport-daemon
April 25 15:44:15 mythtv /usr/bin/mythexport-daemon[32468]: ERROR: AtomicParsley '/podcast/WGBH-American_Masters-Pete_Seeger_The_Power_of_Song-2009042.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork WGBH --TVShowName "American Masters" --TVEpisode "EP000002880163" --TVEpisodeNum  --TVSeason  --description "Artists from Bob Dylan to the Dixie Chicks relay stories of folk singer Pete Seeger, often misunderstood by critics because of his views on peace, civil rights and ecology." --title "Pete Seeger: The Power of Song" 2>&1 FAILED at line 555 in /usr/bin/mythexport-daemon
rm: cannot remove `/podcast/WGBH-American_Masters-Pete_Seeger_The_Power_of_Song-2009042.mp4': No such file or directory
mv: cannot stat `/podcast/*temp*': No such file or directory
April 25 15:44:16 mythtv /usr/bin/mythexport-daemon[32468]: ERROR: /podcast/WGBH-American_Masters-Pete_Seeger_The_Power_of_Song-2009042.mp4 is not available at line 563 in /usr/bin/mythexport-daemon
April 25 15:44:16 mythtv /usr/bin/mythexport-daemon[32468]: query = INSERT into mythexport VALUES(NULL,?,?,?,?,NOW(),DATE_ADD(NOW(),INTERVAL ? DAY),?,?) at line 569 in /usr/bin/mythexport-daemon
April 25 15:44:16 mythtv /usr/bin/mythexport-daemon[32468]: query = delete from mythexport_job_queue where id=? at line 636 in /usr/bin/mythexport-daemon
April 25 15:45:16 mythtv /usr/bin/mythexport-daemon[32468]: query = select id, type, param from mythexport_job_queue order by id at line 607 in /usr/bin/mythexport-daemon
April 25 15:46:16 mythtv /usr/bin/mythexport-daemon[32468]: query = select id, type, param from mythexport_job_queue order by id at line 607 in /usr/bin/mythexport-daemon
A
```

Seems like it should be able to the point of video processing by filling out the form otherwise whats the point of the web interface?

---

### Post by mooseman089 on 2009-05-03
> **minirx7 said:**
> How did you get past that error?  I keep getting the exact error you are mentioning with the "("s

I just upgraded to jaunty and mythexport 2 and now I'm getting the error with the "("s I enabled debugging and I'm not sure what is causing the error. Has anybody found a way to fix it? I'm exporting to ipod with the mp4 codec

---

### Post by stong98 on 2009-05-05
> **joshoekstra said:**
> That was the thing, it didn't. Later on I edited the exportconfig and then it did run. I'm thinking it was a configuration-erro on my behalf :-|


I am having the same problem.  I do not see any reference to the ffmpeg command in the logs when I queue a job.  I see the same error with AtomicParsley, but it appears that is happening because there is no transcoded file being generated.  What changes did you have to make, and which file did you edit?  BTW, I am able to run my ffmpeg command manually with success, but it won't run (or provide any errors) as part of the script.

```
May  4 17:17:43 mythbuntu02 /usr/bin/mythexport-daemon[16625]: query = select id, type, param from mythexport_job_queue order by id at line 607 in /usr/bin/mythexport-daemon
May  4 17:17:43 mythbuntu02 /usr/bin/mythexport-daemon[16625]: exportdir = /var/lib/mythtv/mythexport at line 396 in /usr/bin/mythexport-daemon
May  4 17:17:43 mythbuntu02 /usr/bin/mythexport-daemon[16625]: starttime = 20090430220000 at line 397 in /usr/bin/mythexport-daemon
May  4 17:17:43 mythbuntu02 /usr/bin/mythexport-daemon[16625]: chanid = 2301 at line 398 in /usr/bin/mythexport-daemon
May  4 17:17:43 mythbuntu02 /usr/bin/mythexport-daemon[16625]: config = Export at line 399 in /usr/bin/mythexport-daemon
May  4 17:17:43 mythbuntu02 /usr/bin/mythexport-daemon[16625]: query = SELECT rec.title, rec.subtitle, rec.description, pg.syndicatedepisodenumber, pg.showtype, rec.programid, rec.basename, rec.starttime
    FROM recorded rec LEFT JOIN program pg ON pg.starttime = rec.starttime AND pg.chanid = rec.chanid
    WHERE rec.chanid=? AND rec.starttime=? at line 413 in /usr/bin/mythexport-daemon
May  4 17:17:43 mythbuntu02 /usr/bin/mythexport-daemon[16625]: Going into new mode
 at line 430 in /usr/bin/mythexport-daemon
May  4 17:17:43 mythbuntu02 /usr/bin/mythexport-daemon[16625]: query = SELECT callsign FROM channel WHERE chanid=? at line 438 in /usr/bin/mythexport-daemon
May  4 17:17:43 mythbuntu02 /usr/bin/mythexport-daemon[16625]: command = AtomicParsley '/var/lib/mythtv/mythexport/KCRA-HD-Southland-Sally_in_the_Ally-20090430220000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork KCRA-HD --TVShowName "Southland" --TVEpisode "EP011262880005" --TVEpisodeNum  --TVSeason  --description "An unidentified woman is found dead in an alley; Nate's little sister goes missing and secrets from his past are revealed." --title "Sally in the Ally" 2>&1 at line 554 in /usr/bin/mythexport-daemon
May  4 17:17:43 mythbuntu02 /usr/bin/mythexport-daemon[16625]: ERROR: AtomicParsley '/var/lib/mythtv/mythexport/KCRA-HD-Southland-Sally_in_the_Ally-20090430220000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork KCRA-HD --TVShowName "Southland" --TVEpisode "EP011262880005" --TVEpisodeNum  --TVSeason  --description "An unidentified woman is found dead in an alley; Nate's little sister goes missing and secrets from his past are revealed." --title "Sally in the Ally" 2>&1 FAILED at line 555 in /usr/bin/mythexport-daemon
rm: cannot remove `/var/lib/mythtv/mythexport/KCRA-HD-Southland-Sally_in_the_Ally-20090430220000.mp4': No such file or directory
mv: cannot stat `/var/lib/mythtv/mythexport/*temp*': No such file or directory
May  4 17:17:43 mythbuntu02 /usr/bin/mythexport-daemon[16625]: ERROR: /var/lib/mythtv/mythexport/KCRA-HD-Southland-Sally_in_the_Ally-20090430220000.mp4 is not available at line 563 in /usr/bin/mythexport-daemon
May  4 17:17:43 mythbuntu02 /usr/bin/mythexport-daemon[16625]: query = INSERT into mythexport VALUES(NULL,?,?,?,?,NOW(),DATE_ADD(NOW(),INTERVAL ? DAY),?,?) at line 569 in /usr/bin/mythexport-daemon
May  4 17:17:43 mythbuntu02 /usr/bin/mythexport-daemon[16625]: query = delete from mythexport_job_queue where id=? at line 636 in /usr/bin/mythexport-daemon
May  4 17:18:43 mythbuntu02 /usr/bin/mythexport-daemon[16625]: query = select id, type, param from mythexport_job_queue order by id at line 607 in /usr/bin/mythexport-daemon

```

I'm not sure if this matters, but this is running on my slave backend, but all of the referenced directories are local.  It is successfully connecting to the mysql server on the master backend.  

If I can get this running I think this will be a great tool!!  Thx.

---

### Post by rhpot1991 on 2009-05-05
> **stong98 said:**
> I am having the same problem.  I do not see any reference to the ffmpeg command in the logs when I queue a job.  I see the same error with AtomicParsley, but it appears that is happening because there is no transcoded file being generated.  What changes did you have to make, and which file did you edit?  BTW, I am able to run my ffmpeg command manually with success, but it won't run (or provide any errors) as part of the script.

```
May  4 17:17:43 mythbuntu02 /usr/bin/mythexport-daemon[16625]: query = select id, type, param from mythexport_job_queue order by id at line 607 in /usr/bin/mythexport-daemon
May  4 17:17:43 mythbuntu02 /usr/bin/mythexport-daemon[16625]: exportdir = /var/lib/mythtv/mythexport at line 396 in /usr/bin/mythexport-daemon
May  4 17:17:43 mythbuntu02 /usr/bin/mythexport-daemon[16625]: starttime = 20090430220000 at line 397 in /usr/bin/mythexport-daemon
May  4 17:17:43 mythbuntu02 /usr/bin/mythexport-daemon[16625]: chanid = 2301 at line 398 in /usr/bin/mythexport-daemon
May  4 17:17:43 mythbuntu02 /usr/bin/mythexport-daemon[16625]: config = Export at line 399 in /usr/bin/mythexport-daemon
May  4 17:17:43 mythbuntu02 /usr/bin/mythexport-daemon[16625]: query = SELECT rec.title, rec.subtitle, rec.description, pg.syndicatedepisodenumber, pg.showtype, rec.programid, rec.basename, rec.starttime
    FROM recorded rec LEFT JOIN program pg ON pg.starttime = rec.starttime AND pg.chanid = rec.chanid
    WHERE rec.chanid=? AND rec.starttime=? at line 413 in /usr/bin/mythexport-daemon
May  4 17:17:43 mythbuntu02 /usr/bin/mythexport-daemon[16625]: Going into new mode
 at line 430 in /usr/bin/mythexport-daemon
May  4 17:17:43 mythbuntu02 /usr/bin/mythexport-daemon[16625]: query = SELECT callsign FROM channel WHERE chanid=? at line 438 in /usr/bin/mythexport-daemon
May  4 17:17:43 mythbuntu02 /usr/bin/mythexport-daemon[16625]: command = AtomicParsley '/var/lib/mythtv/mythexport/KCRA-HD-Southland-Sally_in_the_Ally-20090430220000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork KCRA-HD --TVShowName "Southland" --TVEpisode "EP011262880005" --TVEpisodeNum  --TVSeason  --description "An unidentified woman is found dead in an alley; Nate's little sister goes missing and secrets from his past are revealed." --title "Sally in the Ally" 2>&1 at line 554 in /usr/bin/mythexport-daemon
May  4 17:17:43 mythbuntu02 /usr/bin/mythexport-daemon[16625]: ERROR: AtomicParsley '/var/lib/mythtv/mythexport/KCRA-HD-Southland-Sally_in_the_Ally-20090430220000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork KCRA-HD --TVShowName "Southland" --TVEpisode "EP011262880005" --TVEpisodeNum  --TVSeason  --description "An unidentified woman is found dead in an alley; Nate's little sister goes missing and secrets from his past are revealed." --title "Sally in the Ally" 2>&1 FAILED at line 555 in /usr/bin/mythexport-daemon
rm: cannot remove `/var/lib/mythtv/mythexport/KCRA-HD-Southland-Sally_in_the_Ally-20090430220000.mp4': No such file or directory
mv: cannot stat `/var/lib/mythtv/mythexport/*temp*': No such file or directory
May  4 17:17:43 mythbuntu02 /usr/bin/mythexport-daemon[16625]: ERROR: /var/lib/mythtv/mythexport/KCRA-HD-Southland-Sally_in_the_Ally-20090430220000.mp4 is not available at line 563 in /usr/bin/mythexport-daemon
May  4 17:17:43 mythbuntu02 /usr/bin/mythexport-daemon[16625]: query = INSERT into mythexport VALUES(NULL,?,?,?,?,NOW(),DATE_ADD(NOW(),INTERVAL ? DAY),?,?) at line 569 in /usr/bin/mythexport-daemon
May  4 17:17:43 mythbuntu02 /usr/bin/mythexport-daemon[16625]: query = delete from mythexport_job_queue where id=? at line 636 in /usr/bin/mythexport-daemon
May  4 17:18:43 mythbuntu02 /usr/bin/mythexport-daemon[16625]: query = select id, type, param from mythexport_job_queue order by id at line 607 in /usr/bin/mythexport-daemon

```

I'm not sure if this matters, but this is running on my slave backend, but all of the referenced directories are local.  It is successfully connecting to the mysql server on the master backend.  

If I can get this running I think this will be a great tool!!  Thx.

See the wiki, enable debugging and the ffmpeg command will be printed to the log, verify you are running it exactly as it is in the log and let it run completely.  Sometimes recording files can have corruptions that will cause ffmpeg to fail on them.

---

### Post by stong98 on 2009-05-05
> **rhpot1991 said:**
> See the wiki, enable debugging and the ffmpeg command will be printed to the log, verify you are running it exactly as it is in the log and let it run completely.  Sometimes recording files can have corruptions that will cause ffmpeg to fail on them.

Unless I am missing something (which is entirely possible) I believe I already had debugging enabled.  Without debugging I did not get nearly as much output.  So even with debugging enabled I do not see any reference to ffmpeg - failing or otherwise - in the logs.  Here is the top of my /etc/init.d/mythexport.  I have gone over the wiki several times and believe that I have done every step, but please let me know what I have overlooked or missed.

```

mythtv@mythbuntu02:~$ head -20 /etc/init.d/mythexport
#! /bin/sh

### BEGIN INIT INFO
# Provides:          mythexport
# Required-Start:    $local_fs $remote_fs $network
# Required-Stop:     $local_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start/Stop the MythExport Daemon.
### END INIT INFO

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/bin/mythexport-daemon
NAME="mythexport"
COMMAND=/usr/bin/perl
ARGS="debug"
DESC="MythExport Daemon"

test -x $DAEMON || exit 0

```

---

### Post by mooseman089 on 2009-05-05
I agree I have been looking and I enabled debugging and I dont see any indication that ffmpeg is running which is why its failing at atomicparsley

---

### Post by rhpot1991 on 2009-05-05
Hmmm, what versions are you guys running and which version of Ubuntu/Mythbuntu.  All you should need to do is add ARGS="debug"
to your /etc/init.d/mythexport then restart it.  Seeing no ffmpeg line and only seeing an atomic parsley error is what happens sometimes when ffmpeg fails silently and then the file doesn't exist for atomic parsley.

---

### Post by mooseman089 on 2009-05-05
I'm running 9.04 but I think I get ffmpeg through the medibuntu jaunty repos

---

### Post by rhpot1991 on 2009-05-05
> **mooseman089 said:**
> I'm running 9.04 but I think I get ffmpeg through the medibuntu jaunty repos

You shouldn't need ffmpeg from medibuntu anymore, last I checked they didn't even make it for Intrepid, not sure if that changed for Jaunty.

---

### Post by stong98 on 2009-05-05
> **rhpot1991 said:**
> Hmmm, what versions are you guys running and which version of Ubuntu/Mythbuntu.

Here are the versions I have installed:

```

ryan@mythbuntu02:~$ cat /etc/issue
Ubuntu 8.10 \n \l

ryan@mythbuntu02:~$ ffmpeg -version
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:48:10, gcc: 4.3.2
FFmpeg r11872+debian_3:0.svn20080206-12ubuntu3.1
libavutil   3212800
libavcodec  3355136
libavformat 3409664
libavdevice 3407872
ryan@mythbuntu02:~$ dpkg -s mythexport
Package: mythexport
Status: install ok installed
Priority: optional
Section: misc
Installed-Size: 276
Maintainer: Ubuntu MythTV Team <ubuntu-mythtv@lists.ubuntu.com>
Architecture: i386
Version: 2.0-0ubuntu1~ppa0.1
Depends: debconf (>= 0.5) | debconf-2.0, perl, atomicparsley, libmyth-perl, libdbi-perl, libdbd-mysql-perl, debconf, apache2, libhtml-template-perl, libconfig-simple-perl, libxml-rss-perl, libproc-daemon-perl, libproc-pid-file-perl, liblog-dispatch-perl, libxml-writer-perl, mysql-client, libavcodec-unstripped-51, libavdevice-unstripped-52, libavformat-unstripped-52, libavutil-unstripped-49, libpostproc-unstripped-51, libswscale-unstripped-0
Pre-Depends: mythtv-backend | mythtv-database
Conffiles:
 /etc/cron.daily/mythexport 2ad1660764096456eac644c1d4740cad
 /etc/apache2/sites-available/mythexport.conf a2302190e349cbb9460ba9f24f6931d5
 /etc/init.d/mythexport 03c64479df0890048b05378b6e5b2001
Description: Export MythTV recording to portable media players
 MythExport is a Perl daemon that can be used with MythTV to export recordings
 into a format playable on portable devices such as iPod Video, iPod Touch, PSP,
 and other devices. Besides converting your recordings, this script also grabs data
 from the MythTV MySQL database and injects it as iTunes data into the exported video
 so that it will show up correctly on your iPod. MythExport may also be used to take
 your recordings "On The Go" and provides a RSS feed to all exported recordings.
Homepage: http://www.mythbuntu.org
Original-Maintainer: John Baab <john.baab@gmail.com>

```

Thanks for your help and for looking into this.

---

### Post by stong98 on 2009-05-07
I found the problem that I was having with ffmpeg not running.  I took a closer look at the actual user job that was created, and the last part of the user job was the config to be used.  The config to be used had spaces and special characters in it, but it was not quoted.  I added quotes around the config and am now able to run the job successfully.

However, I have run into a different issue now.  I have this installed on my slave backend and am only able to transcode files that were recorded on the slave.  Is it possible to transcode recordings from my master backend?  Do I need to install this on both backends?  Will I need different user jobs for each backend?

---

### Post by rhpot1991 on 2009-05-08
> **stong98 said:**
> I found the problem that I was having with ffmpeg not running.  I took a closer look at the actual user job that was created, and the last part of the user job was the config to be used.  The config to be used had spaces and special characters in it, but it was not quoted.  I added quotes around the config and am now able to run the job successfully.

However, I have run into a different issue now.  I have this installed on my slave backend and am only able to transcode files that were recorded on the slave.  Is it possible to transcode recordings from my master backend?  Do I need to install this on both backends?  Will I need different user jobs for each backend?

There are a few ways to go about this, what I would recommend is having the file systems match up on each, then you can either run MythExport on each or on the most powerful one.

What I do is something like this: /mythtv/recordings/<computer_name>
Then setup NFS shares on each so the files will "live" in the same place on all boxes.

That being said, they do not have to be in the same place, as long as they are in a storage group so MythTV can find them.  So look into NFS/samba/etc and give it a try.

---

### Post by LorenzoS on 2009-05-08
Got a segmentation fault when trying to select use multi threading from the gui setup screen.  I'm on 8.10.

The ffmpegArgs line from the setup was:
```
ffmpegArgs=-y -acodec libfaac -ab 192kb -vcodec mpeg4 -b 300kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x240 -threads auto -aspect 4:3
```

Which generated this from ffmpeg:```

lorenzo@Uranus:~$ ffmpeg -i test.mpg -y -acodec libfaac -ab 192kb -vcodec mpeg4 -b 300kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x240 -threads auto -aspect 4:3 out.mp4
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:48:10, gcc: 4.3.2
Input #0, mpeg, from 'test.mpg':
  Duration: 00:29:51.7, start: 0.189256, bitrate: 5188 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 480x480 [PAR 4:3 DAR 4:3], 6000 kb/s, 29.97 tb(r)
    Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 384 kb/s
Output #0, mp4, to 'out.mp4':
    Stream #0.0: Video: mpeg4 (hq), yuv420p, 320x240 [PAR 1:1 DAR 4:3], q=2-31, 300 kb/s, 29.97 tb(c)
    Stream #0.1: Audio: libfaac, 48000 Hz, stereo, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
Segmentation fault0 q=2.0 size=      88kB time=2.7 bitrate= 269.6kbits/s
```

Removing "-threads auto" from ffmpegArgs solved the problem and it runs great now.

---

### Post by rhpot1991 on 2009-05-11
> **LorenzoS said:**
> Got a segmentation fault when trying to select use multi threading from the gui setup screen.  I'm on 8.10.

The ffmpegArgs line from the setup was:
```
ffmpegArgs=-y -acodec libfaac -ab 192kb -vcodec mpeg4 -b 300kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x240 -threads auto -aspect 4:3
```

Which generated this from ffmpeg:```

lorenzo@Uranus:~$ ffmpeg -i test.mpg -y -acodec libfaac -ab 192kb -vcodec mpeg4 -b 300kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x240 -threads auto -aspect 4:3 out.mp4
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:48:10, gcc: 4.3.2
Input #0, mpeg, from 'test.mpg':
  Duration: 00:29:51.7, start: 0.189256, bitrate: 5188 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 480x480 [PAR 4:3 DAR 4:3], 6000 kb/s, 29.97 tb(r)
    Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 384 kb/s
Output #0, mp4, to 'out.mp4':
    Stream #0.0: Video: mpeg4 (hq), yuv420p, 320x240 [PAR 1:1 DAR 4:3], q=2-31, 300 kb/s, 29.97 tb(c)
    Stream #0.1: Audio: libfaac, 48000 Hz, stereo, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
Segmentation fault0 q=2.0 size=      88kB time=2.7 bitrate= 269.6kbits/s
```

Removing "-threads auto" from ffmpegArgs solved the problem and it runs great now.

Yep, the threads option is not well liked by Intrepid's ffmpeg, I'm not entirely sure how well it works with Jaunty, it is more of an experimental option at this point.

---

### Post by JerkyChew on 2009-05-12
I've solved the circular symlink issue by removing the mythexport directory from cd /var/lib/mythtv/ and recreating it, and confirming that the symlink in var/www still points there.

However, when trying to encode an episode of General Hospital (don't laugh, it's for the girlfriend :P), I get the following errors:

magicvm.jerkychew.local /usr/bin/mythexport-daemon[11047]: ERROR: AtomicParsley '/var/lib/mythtv/mythexport/WCVB-General_Hospital--20090511150000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork WCVB --TVShowName "General Hospital" --TVEpisode "EP000018071651" --TVEpisodeNum  --TVSeason  --description "Michael is in trouble; Spinelli promises to come through for Maxie; Luke thinks Tracy knows more than she is admitting." --title "" 2>&1 FAILED at line 555 in /usr/bin/mythexport-daemon
rm: cannot remove `/var/lib/mythtv/mythexport/WCVB-General_Hospital--20090511150000.mp4': No such file or directory
mv: cannot stat `/var/lib/mythtv/mythexport/*temp*': No such file or directory
May 12 08:17:27 magicvm.jerkychew.local /usr/bin/mythexport-daemon[11047]: ERROR: /var/lib/mythtv/mythexport/WCVB-General_Hospital--20090511150000.mp4 is not available at line 563 in /usr/bin/mythexport-daemon
May 12 09:24:27 magicvm.jerkychew.local /usr/bin/mythexport-daemon[11047]: ERROR: AtomicParsley '/var/lib/mythtv/mythexport/WCVB-General_Hospital--20090511150000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork WCVB --TVShowName "General Hospital" --TVEpisode "EP000018071651" --TVEpisodeNum  --TVSeason  --description "Michael is in trouble; Spinelli promises to come through for Maxie; Luke thinks Tracy knows more than she is admitting." --title "" 2>&1 FAILED at line 555 in /usr/bin/mythexport-daemon
rm: cannot remove `/var/lib/mythtv/mythexport/WCVB-General_Hospital--20090511150000.mp4': No such file or directory
mv: cannot stat `/var/lib/mythtv/mythexport/*temp*': No such file or directory
May 12 09:24:27 magicvm.jerkychew.local /usr/bin/mythexport-daemon[11047]: ERROR: /var/lib/mythtv/mythexport/WCVB-General_Hospital--20090511150000.mp4 is not available at line 563 in /usr/bin/mythexport-daemon

The 'cannot remove' errors make sense, I think, since it's trying to remove something that isn't there. But how can I figure out why it's not encoding in the first place? 

The recording is a 1080i HD recording from an HDHomeRun.

---

### Post by rhpot1991 on 2009-05-12
> **JerkyChew said:**
> I've solved the circular symlink issue by removing the mythexport directory from cd /var/lib/mythtv/ and recreating it, and confirming that the symlink in var/www still points there.

However, when trying to encode an episode of General Hospital (don't laugh, it's for the girlfriend :P), I get the following errors:

magicvm.jerkychew.local /usr/bin/mythexport-daemon[11047]: ERROR: AtomicParsley '/var/lib/mythtv/mythexport/WCVB-General_Hospital--20090511150000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork WCVB --TVShowName "General Hospital" --TVEpisode "EP000018071651" --TVEpisodeNum  --TVSeason  --description "Michael is in trouble; Spinelli promises to come through for Maxie; Luke thinks Tracy knows more than she is admitting." --title "" 2>&1 FAILED at line 555 in /usr/bin/mythexport-daemon
rm: cannot remove `/var/lib/mythtv/mythexport/WCVB-General_Hospital--20090511150000.mp4': No such file or directory
mv: cannot stat `/var/lib/mythtv/mythexport/*temp*': No such file or directory
May 12 08:17:27 magicvm.jerkychew.local /usr/bin/mythexport-daemon[11047]: ERROR: /var/lib/mythtv/mythexport/WCVB-General_Hospital--20090511150000.mp4 is not available at line 563 in /usr/bin/mythexport-daemon
May 12 09:24:27 magicvm.jerkychew.local /usr/bin/mythexport-daemon[11047]: ERROR: AtomicParsley '/var/lib/mythtv/mythexport/WCVB-General_Hospital--20090511150000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork WCVB --TVShowName "General Hospital" --TVEpisode "EP000018071651" --TVEpisodeNum  --TVSeason  --description "Michael is in trouble; Spinelli promises to come through for Maxie; Luke thinks Tracy knows more than she is admitting." --title "" 2>&1 FAILED at line 555 in /usr/bin/mythexport-daemon
rm: cannot remove `/var/lib/mythtv/mythexport/WCVB-General_Hospital--20090511150000.mp4': No such file or directory
mv: cannot stat `/var/lib/mythtv/mythexport/*temp*': No such file or directory
May 12 09:24:27 magicvm.jerkychew.local /usr/bin/mythexport-daemon[11047]: ERROR: /var/lib/mythtv/mythexport/WCVB-General_Hospital--20090511150000.mp4 is not available at line 563 in /usr/bin/mythexport-daemon

The 'cannot remove' errors make sense, I think, since it's trying to remove something that isn't there. But how can I figure out why it's not encoding in the first place? 

The recording is a 1080i HD recording from an HDHomeRun.

Enable debugging as mentioned in the wiki, this should spit out the ffmpeg line it runs, run this by hand and see what happens, odds are it will bail out at some point.  Does it just do this for one day or for all days?  I have seen issues with corrupted recordings, otherwise you will need to tweak your ffmpeg to see why it is failing.

---

### Post by JerkyChew on 2009-05-12
I've enabled debug mode and restarted the service, it doesn't appear to be outputting any FFMPEG commands in the logs:

May 12 12:12:13 magicvm.jerkychew.local /usr/bin/mythexport-daemon[12863]: Going into new mode
 at line 430 in /usr/bin/mythexport-daemon
May 12 12:12:13 magicvm.jerkychew.local /usr/bin/mythexport-daemon[12863]: query = SELECT callsign FROM channel WHERE chanid=? at line 438 in /usr/bin/mythexport-daemon
May 12 12:12:13 magicvm.jerkychew.local /usr/bin/mythexport-daemon[12863]: command = AtomicParsley '/var/lib/mythtv/mythexport/WCVB-General_Hospital--20090511150000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork WCVB --TVShowName "General Hospital" --TVEpisode "EP000018071651" --TVEpisodeNum  --TVSeason  --description "Michael is in trouble; Spinelli promises to come through for Maxie; Luke thinks Tracy knows more than she is admitting." --title "" 2>&1 at line 554 in /usr/bin/mythexport-daemon
May 12 12:12:13 magicvm.jerkychew.local /usr/bin/mythexport-daemon[12863]: ERROR: AtomicParsley '/var/lib/mythtv/mythexport/WCVB-General_Hospital--20090511150000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork WCVB --TVShowName "General Hospital" --TVEpisode "EP000018071651" --TVEpisodeNum  --TVSeason  --description "Michael is in trouble; Spinelli promises to come through for Maxie; Luke thinks Tracy knows more than she is admitting." --title "" 2>&1 FAILED at line 555 in /usr/bin/mythexport-daemon
rm: cannot remove `/var/lib/mythtv/mythexport/WCVB-General_Hospital--20090511150000.mp4': No such file or directory
mv: cannot stat `/var/lib/mythtv/mythexport/*temp*': No such file or directory
May 12 12:12:13 magicvm.jerkychew.local /usr/bin/mythexport-daemon[12863]: ERROR: /var/lib/mythtv/mythexport/WCVB-General_Hospital--20090511150000.mp4 is not available at line 563 in /usr/bin/mythexport-daemon
May 12 12:12:13 magicvm.jerkychew.local /usr/bin/mythexport-daemon[12863]: query = INSERT into mythexport VALUES(NULL,?,?,?,?,NOW(),DATE_ADD(NOW(),INTERVAL ? DAY),?,?) at line 569 in /usr/bin/mythexport-daemon
May 12 12:12:13 magicvm.jerkychew.local /usr/bin/mythexport-daemon[12863]: query = delete from mythexport_job_queue where id=? at line 636 in /usr/bin/mythexport-daemon

---

### Post by pcooley on 2009-05-15
I followed the instructions for Jaunty Ubuntu 9.04 - [https://help.ubuntu.com/community/MythExport](https://help.ubuntu.com/community/MythExport)

I set it up with some settings for the iPhone.  Ran it and it worked the first time.

Excellent and Kudos!

---

### Post by rhpot1991 on 2009-05-15
> **JerkyChew said:**
> I've enabled debug mode and restarted the service, it doesn't appear to be outputting any FFMPEG commands in the logs:

May 12 12:12:13 magicvm.jerkychew.local /usr/bin/mythexport-daemon[12863]: Going into new mode
 at line 430 in /usr/bin/mythexport-daemon
May 12 12:12:13 magicvm.jerkychew.local /usr/bin/mythexport-daemon[12863]: query = SELECT callsign FROM channel WHERE chanid=? at line 438 in /usr/bin/mythexport-daemon
May 12 12:12:13 magicvm.jerkychew.local /usr/bin/mythexport-daemon[12863]: command = AtomicParsley '/var/lib/mythtv/mythexport/WCVB-General_Hospital--20090511150000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork WCVB --TVShowName "General Hospital" --TVEpisode "EP000018071651" --TVEpisodeNum  --TVSeason  --description "Michael is in trouble; Spinelli promises to come through for Maxie; Luke thinks Tracy knows more than she is admitting." --title "" 2>&1 at line 554 in /usr/bin/mythexport-daemon
May 12 12:12:13 magicvm.jerkychew.local /usr/bin/mythexport-daemon[12863]: ERROR: AtomicParsley '/var/lib/mythtv/mythexport/WCVB-General_Hospital--20090511150000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork WCVB --TVShowName "General Hospital" --TVEpisode "EP000018071651" --TVEpisodeNum  --TVSeason  --description "Michael is in trouble; Spinelli promises to come through for Maxie; Luke thinks Tracy knows more than she is admitting." --title "" 2>&1 FAILED at line 555 in /usr/bin/mythexport-daemon
rm: cannot remove `/var/lib/mythtv/mythexport/WCVB-General_Hospital--20090511150000.mp4': No such file or directory
mv: cannot stat `/var/lib/mythtv/mythexport/*temp*': No such file or directory
May 12 12:12:13 magicvm.jerkychew.local /usr/bin/mythexport-daemon[12863]: ERROR: /var/lib/mythtv/mythexport/WCVB-General_Hospital--20090511150000.mp4 is not available at line 563 in /usr/bin/mythexport-daemon
May 12 12:12:13 magicvm.jerkychew.local /usr/bin/mythexport-daemon[12863]: query = INSERT into mythexport VALUES(NULL,?,?,?,?,NOW(),DATE_ADD(NOW(),INTERVAL ? DAY),?,?) at line 569 in /usr/bin/mythexport-daemon
May 12 12:12:13 magicvm.jerkychew.local /usr/bin/mythexport-daemon[12863]: query = delete from mythexport_job_queue where id=? at line 636 in /usr/bin/mythexport-daemon

Ok so we need to figure out why that isn't working then, pastebin (mythbuntu.pastebin.com) your /etc/mythtv/mythexport_settings.cfg

---

### Post by JerkyChew on 2009-05-15
Pasted to [http://mythbuntu.pastebin.com/m80cd44d](http://mythbuntu.pastebin.com/m80cd44d)

---

### Post by rhpot1991 on 2009-05-21
> **JerkyChew said:**
> Pasted to [http://mythbuntu.pastebin.com/m80cd44d](http://mythbuntu.pastebin.com/m80cd44d)

Everything looks ok here, I'm having a hard time reproducing these issues, my local install spits out all the info that I'd expect.  Still looking into what may be causing this...

---

### Post by fenx7 on 2009-05-30
I am also getting similiar problems, though I think mine has to do with libfaac. I have taken the configuration and run it manually to produce;

```
ffmpeg -i /var/lib/mythtv/recordings/1022_20090530105100.mpg -y -acodec libfaac -ab 256kb -vcodec mpeg4 -b 1200kb -mbd 2 -flags +4mv+aic -trellis 2 -cmp 2 -subcmp 2 -s 320x240 -ac 2 -aspect 4:3  '/var/lib/mythtv/mythexport/ABC2-In_The_Night_Garden-Slow_Down_Everybody-20090530105100.mp4'
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 50.00 (50/1) -> 25.00 (25/1)
Input #0, mpegts, from '/var/lib/mythtv/recordings/1022_20090530105100.mpg':
  Duration: 00:29:28.77, start: 6211.319011, bitrate: 5303 kb/s
  Program 1 
    Stream #0.0[0x903]: Video: mpeg2video, yuv420p, 720x576 [PAR 64:45 DAR 16:9], 15000 kb/s, 25 tbr, 90k tbn, 50 tbc
    Stream #0.1[0x904](eng): Audio: mp2, 48000 Hz, stereo, s16, 256 kb/s
Output #0, mp4, to '/var/lib/mythtv/mythexport/ABC2-In_The_Night_Garden-Slow_Down_Everybody-20090530105100.mp4':
    Stream #0.0: Video: mpeg4 (hq), yuv420p, 320x240 [PAR 1:1 DAR 4:3], q=2-31, 1200 kb/s, 90k tbn, 25 tbc
    Stream #0.1(eng): Audio: libfaac, stereo, s16, 256 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[libfaac @ 0x9488940]libfaac doesn't support this output format!
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

```

Any ideas what is causing my problems?

nuvexport also gives ffmpeg fatal errors and does not work to ipod.

---

### Post by rhpot1991 on 2009-05-30
> **fenx7 said:**
> I am also getting similiar problems, though I think mine has to do with libfaac. I have taken the configuration and run it manually to produce;

```
ffmpeg -i /var/lib/mythtv/recordings/1022_20090530105100.mpg -y -acodec libfaac -ab 256kb -vcodec mpeg4 -b 1200kb -mbd 2 -flags +4mv+aic -trellis 2 -cmp 2 -subcmp 2 -s 320x240 -ac 2 -aspect 4:3  '/var/lib/mythtv/mythexport/ABC2-In_The_Night_Garden-Slow_Down_Everybody-20090530105100.mp4'
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 50.00 (50/1) -> 25.00 (25/1)
Input #0, mpegts, from '/var/lib/mythtv/recordings/1022_20090530105100.mpg':
  Duration: 00:29:28.77, start: 6211.319011, bitrate: 5303 kb/s
  Program 1 
    Stream #0.0[0x903]: Video: mpeg2video, yuv420p, 720x576 [PAR 64:45 DAR 16:9], 15000 kb/s, 25 tbr, 90k tbn, 50 tbc
    Stream #0.1[0x904](eng): Audio: mp2, 48000 Hz, stereo, s16, 256 kb/s
Output #0, mp4, to '/var/lib/mythtv/mythexport/ABC2-In_The_Night_Garden-Slow_Down_Everybody-20090530105100.mp4':
    Stream #0.0: Video: mpeg4 (hq), yuv420p, 320x240 [PAR 1:1 DAR 4:3], q=2-31, 1200 kb/s, 90k tbn, 25 tbc
    Stream #0.1(eng): Audio: libfaac, stereo, s16, 256 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[libfaac @ 0x9488940]libfaac doesn't support this output format!
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

```

Any ideas what is causing my problems?

nuvexport also gives ffmpeg fatal errors and does not work to ipod.

I've seen this error before but I don't recall why currently.  Try removing the '-ac 2' from the ffmpeg line and try again.

---

### Post by fenx7 on 2009-05-30
actually I found on this thread on page 6 (or something like that) that you can add -ar 48000 to the line in that specifies the ffmpeg arguments.

The post also says that it will be added as an option to the configuration webpage

---

### Post by pchaffey on 2009-06-27
Hi All,

I am running kubuntu 9.04 (amd64)

I have run into a nasty problem - I tried to install mythexport using synaptic and I gave the incorrect mysql username password pair during install. Now mythexport has failed to install - no suprises there, but if I try to uninstall completely this also fails.

Hence I am stuck in the middle - can someone give me some help to firstly uninstall mythexport. Then at lease I can re-install and get to the mysql username password entry. Also the mysql username password pair, should it be the root or mythtv pair ?

Regards, Paul.

---

### Post by rhpot1991 on 2009-06-28
> **pchaffey said:**
> Hi All,

I am running kubuntu 9.04 (amd64)

I have run into a nasty problem - I tried to install mythexport using synaptic and I gave the incorrect mysql username password pair during install. Now mythexport has failed to install - no suprises there, but if I try to uninstall completely this also fails.

Hence I am stuck in the middle - can someone give me some help to firstly uninstall mythexport. Then at lease I can re-install and get to the mysql username password entry. Also the mysql username password pair, should it be the root or mythtv pair ?

Regards, Paul.

Run this and it should let you go back through the setup phase
```
sudo dpkg-reconfigure mythexport
```

Either the root or mythtv mysql user should work, it just needs permission to create a table in mythconverg.

---

### Post by pchaffey on 2009-06-30
[QUOTE=rhpot1991;7529465]Run this and it should let you go back through the setup phase
```
sudo dpkg-reconfigure mythexport
```


Perhaps I am being a bit dumb, but I have tried a few different combinations but still no luck. Here is what is being reported:


sudo apt-get install mythexport
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  mythexport
0 upgraded, 1 newly installed, 0 to remove and 20 not upgraded.
Need to get 29.0kB of archives.
After this operation, 283kB of additional disk space will be used.
Get:1 [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty/universe mythexport 2.0-0ubuntu1 [29.0kB]
Fetched 29.0kB in 0s (65.0kB/s)
Preconfiguring packages ...
Selecting previously deselected package mythexport.
(Reading database ... 134638 files and directories currently installed.)
Unpacking mythexport (from .../mythexport_2.0-0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up mythexport (2.0-0ubuntu1) ...
ln: creating symbolic link `./video': File exists
dpkg: error processing mythexport (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mythexport
E: Sub-process /usr/bin/dpkg returned an error code (1)
paul@server:/var/log/mythtv$ sudo dpkg-reconfigure mythexport
/usr/sbin/dpkg-reconfigure: mythexport is broken or not fully installed

Any other ideas are more than welcome.

---

### Post by rhpot1991 on 2009-06-30
> **pchaffey said:**
> [QUOTE=rhpot1991;7529465]Run this and it should let you go back through the setup phase
```
sudo dpkg-reconfigure mythexport
```


Perhaps I am being a bit dumb, but I have tried a few different combinations but still no luck. Here is what is being reported:


sudo apt-get install mythexport
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  mythexport
0 upgraded, 1 newly installed, 0 to remove and 20 not upgraded.
Need to get 29.0kB of archives.
After this operation, 283kB of additional disk space will be used.
Get:1 [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty/universe mythexport 2.0-0ubuntu1 [29.0kB]
Fetched 29.0kB in 0s (65.0kB/s)
Preconfiguring packages ...
Selecting previously deselected package mythexport.
(Reading database ... 134638 files and directories currently installed.)
Unpacking mythexport (from .../mythexport_2.0-0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up mythexport (2.0-0ubuntu1) ...
ln: creating symbolic link `./video': File exists
dpkg: error processing mythexport (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mythexport
E: Sub-process /usr/bin/dpkg returned an error code (1)
paul@server:/var/log/mythtv$ sudo dpkg-reconfigure mythexport
/usr/sbin/dpkg-reconfigure: mythexport is broken or not fully installed

Any other ideas are more than welcome.

Try this:
```

sudo dpkg --purge mythexport
sudo apt-get install mythexport

```

---

### Post by trakon88 on 2009-07-07
I can't install mythexport.
I get this error, I tried everything recommended in this thread. It didn't help, any suggestions?
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES) 

best greeting from aleX

---

### Post by rhpot1991 on 2009-07-07
> **trakon88 said:**
> I can't install mythexport.
I get this error, I tried everything recommended in this thread. It didn't help, any suggestions?
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES) 

best greeting from aleX

Sounds like you are giving it an incorrect password, this is asking for a MySQL user.  The root MySQL user has an empty password by default, if you haven't set it then it will be empty.  You can also use the mythtv user, who's password will be in /etc/mythtv/mysql.txt

You can start over with the installation by doing the following:
```

sudo dpkg-reconfigure mythexport

or

sudo dpkg --purge mythexport
sudo apt-get install mythexport

```

---

### Post by trakon88 on 2009-07-08
Hi again,

thanks for your answer. But I was never asked for a password during the installation, what's going wrong?

thanx aleX

---

### Post by rhpot1991 on 2009-07-08
> **trakon88 said:**
> Hi again,

thanks for your answer. But I was never asked for a password during the installation, what's going wrong?

thanx aleX

It should ask you a series of questions before installing, maybe describe how you went about installing and I can dig a little.  Also, you should try what I mentioned before and see if that helps.

---

### Post by trakon88 on 2009-07-08
Hi again,,
yeah I tried all your suggestions, you gave them several times in this thread. But it didn't help. I do not get asked any questions during installation. I have a mythbuntu 9.04 upgraded from 8.10. And I didi the install with a ssh session. But now I try direct terminal session.
aleX

this is what I get (sorry german):
alex@alex-desktop:~$ sudo apt-get install mythexport
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Lese Status-Informationen ein... Fertig
Die folgenden NEUEN Pakete werden installiert:
  mythexport
0 aktualisiert, 1 neu installiert, 0 zu entfernen und 29 nicht aktualisiert.
Es müssen noch 0B von 29,3kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 283kB Plattenplatz zusätzlich benutzt.
Vorkonfiguration der Pakete ...
Wähle vormals abgewähltes Paket mythexport.
(Lese Datenbank ... 129146 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke mythexport (aus .../mythexport_2.01-0ubuntu1~ppa1_i386.deb) ...
Verarbeite Trigger für man-db ...
Richte mythexport ein (2.01-0ubuntu1~ppa1) ...
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
dpkg: Fehler beim Bearbeiten von mythexport (--configure):
 Unterprozess post-installation script gab den Fehlerwert 1 zurück
Fehler traten auf beim Bearbeiten von:
 mythexport
E: Sub-process /usr/bin/dpkg returned an error code (1)
alex@alex-desktop:~$

---

### Post by trakon88 on 2009-07-09
Ok I got it! There was /var/www/.mythtv I had to delete by hand. It couldn't be removed because it was a directory. So after that the deinstallation worked an then the installation worked! Everything installed fine now!

---

### Post by mraggie on 2009-07-09
Hi all,
I love mythexport and thanks for all the hard work, but I am having issues it seems with ffmpeg.  This is with mythexport and nuvexport.

when trying to use ffmpeg through nuvexport I get:

Choose a function, or episode(s) to remove:  c
Where would you like to export the files to? [.] 
. isn't writable.
Where would you like to export the files to? [.] /videos/mythxport/ 
Enable Myth cutlist? [Yes] 
Enable noise reduction (slower, but better results)? [No] 
Enable deinterlacing? [Yes] 
Crop broadcast overscan border (0-5%) ? [1.5] 
Audio bitrate? [64] 
Enable iPod compatibility? [Yes] 
Video codec (mpeg4 or h264)? [h264] 
Variable bitrate video? [Yes] 
Multi-pass (slower, but better quality)? [Yes] 
Video bitrate? [384] 
Default resolution based on requested dimensions.
Width? [320] 
Height? [240] 

Now encoding:  Yo Gabba Gabba!:  Find
Encode started:  Thu Jul  9 10:19:43 2009
First pass...
Waiting for mythtranscode to set up the fifos.
Starting ffmpeg.
processed:  0 of 53850 frames at 0 fps (~%, eta: unknown)  

ffmpeg had critical errors:

ffmpeg: unrecognized option '-title'

Cleaning up temp files.
Cleaning up child processes.


I have compiled ffmpeg and x264 with x264 enabled.

when using mythexport I see this in my mythexport.log

Input #0, mpeg, from '/data/recordings/2257_20090622073000.mpg':
  Duration: 00:29:56.60, start: 0.189222, bitrate: 5176 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 8:9 DAR 4:3], 6000 kb/s, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, s16, 384 kb/s
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
Invalid value '1' for option 'loop'
June 23 23:32:26 mythbox /usr/bin/mythexport-daemon[10125]: ERROR: nice -n19 ffmpeg -i /data/recordings/2257_20090622073000.mpg -y -an -v 1 -vcodec h264 -b 600 -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 1 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 320x240 -aspect 4:3 -f mp4 -pass 1 /dev/null FAILED/ at line 540 in /usr/bin/mythexport-daemon
June 23 23:32:26 mythbox /usr/bin/mythexport-daemon[10125]: Exporting /videos/mythxport/NIK-The_Backyardigans-Ranch_Hands_From_Outer_Space-20090622.mp4
June 23 23:32:26 mythbox /usr/bin/mythexport-daemon[10125]: command = nice -n19 ffmpeg -i /data/recordings/2257_20090622073000.mpg -y -v 1 -vcodec h264 -b 600 -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 6 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq blurCplx^(1-qComp) -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 320x240 -aspect 4:3 -acodec libfaac -ab 192 -ar 48000 -ac 2 -f mp4 -pass 2 '/videos/mythxport/NIK-The_Backyardigans-Ranch_Hands_From_Outer_Space-20090622.mp4' 2>&1 at line 539 in /usr/bin/mythexport-daemon
sh: Syntax error: "(" unexpected
June 23 23:32:26 mythbox /usr/bin/mythexport-daemon[10125]: ERROR: nice -n19 ffmpeg -i /data/recordings/2257_20090622073000.mpg -y -v 1 -vcodec h264 -b 600 -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 6 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq blurCplx^(1-qComp) -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 320x240 -aspect 4:3 -acodec libfaac -ab 192 -ar 48000 -ac 2 -f mp4 -pass 2 '/videos/mythxport/NIK-The_Backyardigans-Ranch_Hands_From_Outer_Space-20090622.mp4' 2>&1 FAILED/ at line 540 in /usr/bin/mythexport-daemon

and the following is my mythexport_settings.cfg file

; Config::Simple 4.59
; Wed Jul  1 15:49:55 2009

[Mythtv_2_Ipod]
removeCommercials=1
extension=
codec=mpeg4
sizeY=240
sizeX=320
aspect=4:3
videoBR=600000
threads=
device=ipod
podcastName=Mythbox2Ipod
deletePeriod=
audioBR=192000
ffmpegArgs=-y -acodec libfaac -ab 192000 -vcodec mpeg4 -b 600000 -mbd 2 -flags +4mv+aic -trellis 2 -cmp 2 -subcmp 2 -s 320x240 -deinterlace -aspect 4:3
audioChannels=
deinterlace=1

I am unsure of why I am getting the unrecognized '-title' error.  Any help would be appreciated.  I have "sudo apt-get purge mythexport nuvexport" my system to death.

---

### Post by rhpot1991 on 2009-07-09
> **mraggie said:**
> 
I have compiled ffmpeg and x264 with x264 enabled.


I wouldn't do that, odd are you are going to have a mismatch.  If you just install ffmpeg and the following from apt then your ffmpeg will be able to do x264, aac, etc:
```
libavcodec-unstripped-52, libavdevice-unstripped-52, libavformat-unstripped-52, libavutil-unstripped-49, libpostproc-unstripped-51, libswscale-unstripped-0
```

---

### Post by rhpot1991 on 2009-07-09
> **trakon88 said:**
> Ok I got it! There was /var/www/.mythtv I had to delete by hand. It couldn't be removed because it was a directory. So after that the deinstallation worked an then the installation worked! Everything installed fine now!

Ah, that pesky bug.  I am pretty sure it is fixed in the latest from the Testing PPA.  I'll double check on it and open up a bug if it isn't.

---

### Post by justinj on 2009-07-09
> **JerkyChew said:**
> I've solved the circular symlink issue by removing the mythexport directory from cd /var/lib/mythtv/ and recreating it, and confirming that the symlink in var/www still points there.

However, when trying to encode an episode of General Hospital (don't laugh, it's for the girlfriend :P), I get the following errors:

magicvm.jerkychew.local /usr/bin/mythexport-daemon[11047]: ERROR: AtomicParsley '/var/lib/mythtv/mythexport/WCVB-General_Hospital--20090511150000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork WCVB --TVShowName "General Hospital" --TVEpisode "EP000018071651" --TVEpisodeNum  --TVSeason  --description "Michael is in trouble; Spinelli promises to come through for Maxie; Luke thinks Tracy knows more than she is admitting." --title "" 2>&1 FAILED at line 555 in /usr/bin/mythexport-daemon
rm: cannot remove `/var/lib/mythtv/mythexport/WCVB-General_Hospital--20090511150000.mp4': No such file or directory
mv: cannot stat `/var/lib/mythtv/mythexport/*temp*': No such file or directory
May 12 08:17:27 magicvm.jerkychew.local /usr/bin/mythexport-daemon[11047]: ERROR: /var/lib/mythtv/mythexport/WCVB-General_Hospital--20090511150000.mp4 is not available at line 563 in /usr/bin/mythexport-daemon
May 12 09:24:27 magicvm.jerkychew.local /usr/bin/mythexport-daemon[11047]: ERROR: AtomicParsley '/var/lib/mythtv/mythexport/WCVB-General_Hospital--20090511150000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork WCVB --TVShowName "General Hospital" --TVEpisode "EP000018071651" --TVEpisodeNum  --TVSeason  --description "Michael is in trouble; Spinelli promises to come through for Maxie; Luke thinks Tracy knows more than she is admitting." --title "" 2>&1 FAILED at line 555 in /usr/bin/mythexport-daemon
rm: cannot remove `/var/lib/mythtv/mythexport/WCVB-General_Hospital--20090511150000.mp4': No such file or directory
mv: cannot stat `/var/lib/mythtv/mythexport/*temp*': No such file or directory
May 12 09:24:27 magicvm.jerkychew.local /usr/bin/mythexport-daemon[11047]: ERROR: /var/lib/mythtv/mythexport/WCVB-General_Hospital--20090511150000.mp4 is not available at line 563 in /usr/bin/mythexport-daemon

The 'cannot remove' errors make sense, I think, since it's trying to remove something that isn't there. But how can I figure out why it's not encoding in the first place? 

The recording is a 1080i HD recording from an HDHomeRun.

In case anyone else searches and has this same problem, I thought I'd post what solved it for me.  There is a bug now posted where the title you give your configuration cannot have spaces.  This goes for the .cfg file and the entry into the myth job database.

For example I used "Ipod High Res" and it couldn't find the configuration parameter that matched the "Ipod" configuration.  Thats because there wasn't one, so it ends up passing some empty parameters to atomicparsely.  I deleted the config, started a new one called "Ipod_HR", and reassigned the job to the new configuration, restarted the backend, and I was all set.

A more useful error condition might be if there are required fields that are empty to log a warning message on those fields.

---

### Post by mraggie on 2009-07-09
> **rhpot1991 said:**
> I wouldn't do that, odd are you are going to have a mismatch.  If you just install ffmpeg and the following from apt then your ffmpeg will be able to do x264, aac, etc:
```
libavcodec-unstripped-52, libavdevice-unstripped-52, libavformat-unstripped-52, libavutil-unstripped-49, libpostproc-unstripped-51, libswscale-unstripped-0
```
okay I purged the complied ffmpeg and x264.  I then installed via synaptic the jaunty disto of ffmpeg and x264 plug the files that you listed.  I then restarted the mythtv-backend and mythexport.  

perry@mythbox:/var/log/mythtv$ ffmpeg
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:20:33, gcc: 4.3.3
At least one output file must be specified

electing previously deselected package x264.
(Reading database ... 189109 files and directories currently installed.)
Unpacking x264 (from .../x264_1%3a0.svn20081230-0.0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up x264 (1:0.svn20081230-0.0ubuntu1) ...


1.  I deleted my then current mythexport job via the web and recreated a new one (ipod) no spaces in tile, description, or xml feed title and ran mythexport

from mythexport.log w/debug

FROM recorded rec LEFT JOIN program pg ON pg.starttime = rec.starttime AND pg.chanid = rec.chanid
    WHERE rec.chanid=? AND rec.starttime=? at line 413 in /usr/bin/mythexport-daemon
July  9 13:56:38 mythbox /usr/bin/mythexport-daemon[29746]: Going into new mode
 at line 430 in /usr/bin/mythexport-daemon
July  9 13:56:38 mythbox /usr/bin/mythexport-daemon[29746]: query = SELECT callsign FROM channel WHERE chanid=? at line 438 in /usr/bin/mythexport-daemon
July  9 13:56:38 mythbox /usr/bin/mythexport-daemon[29746]: command = nice -n19 mythtranscode --mpeg2 --honorcutlist --showprogress --chanid 2251 --starttime 20090709080000 2>&1 at line 532 in /usr/bin/mythexport-daemon
July  9 13:57:06 mythbox /usr/bin/mythexport-daemon[29746]: ERROR: cannot remove /videos/mythxport/DISN-Special_Agent_Oso-Carousel_Royale_Leaf_Raker-200907090.mp4.tmp. at line 535 in /usr/bin/mythexport-daemon
July  9 13:57:06 mythbox /usr/bin/mythexport-daemon[29746]: Exporting /videos/mythxport/DISN-Special_Agent_Oso-Carousel_Royale_Leaf_Raker-200907090.mp4
July 10 13:57:06 mythbox /usr/bin/mythexport-daemon[29746]: command = nice -n19 ffmpeg -i /data/recordings/2251_20090709080000.mpg -y -acodec libfaac -ab 192000 -vcodec mpeg4 -b 600000 -mbd 2 -flags +4mv+aic -trellis 2 -cmp 2 -subcmp 2 -s 320x240 -deinterlace -aspect 4:3 '/videos/mythxport/DISN-Special_Agent_Oso-Carousel_Royale_Leaf_Raker-200907090.mp4' 2>&1 at line 539 in /usr/bin/mythexport-daemon

I then ran the same job from nuvexport

You have chosen to export 1 episode:

  1. Special Agent Oso:
     The Living Flashlight; Sand Castle Royale (Sat Jul  4 08:00 AM) 720x480 MPEG2 (4:3)
     No Description

* Separate multiple episodes with spaces, or ranges with '-'

  c. Continue
  n. Choose another show
  q. Quit

Choose a function, or episode(s) to remove:  c
Where would you like to export the files to? [.] 
Enable Myth cutlist? [Yes] 
Enable noise reduction (slower, but better results)? [No] 
Enable deinterlacing? [Yes] 
Crop broadcast overscan border (0-5%) ? [1.5] 
Audio bitrate? [64] 
Enable iPod compatibility? [Yes] 
Using the mpeg4 codec (h.264 mp4/ipod encoding requires the svn version of ffmpeg.)
Variable bitrate video? [Yes] 
Multi-pass (slower, but better quality)? [Yes] 
Video bitrate? [384] 
Default resolution based on requested dimensions.
Width? [320] 
Height? [240] 

Now encoding:  Special Agent Oso:  The Living Flashlight; Sand Castle Royale
Encode started:  Thu Jul  9 14:02:22 2009
First pass...
Waiting for mythtranscode to set up the fifos.
Starting ffmpeg.
processed:  0 of 2990 frames at 0 fps (~%, eta: unknown)  

ffmpeg had critical errors:

ffmpeg: unrecognized option '-title'

Cleaning up temp files.
Cleaning up child processes.
perry@mythbox:/var/log/mythtv$ 

Once again got the "unrecognized option '-title'

version of mythexport: 
mythexport [2.01-0ubuntu1~ppa1]

version of nuvexport
nuvexport [0.21.0-0ubuntu2]

---

### Post by rhpot1991 on 2009-07-09
> **mraggie said:**
> 
1.  I deleted my then current mythexport job via the web and recreated a new one (ipod) no spaces in tile, description, or xml feed title and ran mythexport

from mythexport.log w/debug

FROM recorded rec LEFT JOIN program pg ON pg.starttime = rec.starttime AND pg.chanid = rec.chanid
    WHERE rec.chanid=? AND rec.starttime=? at line 413 in /usr/bin/mythexport-daemon
July  9 13:56:38 mythbox /usr/bin/mythexport-daemon[29746]: Going into new mode
 at line 430 in /usr/bin/mythexport-daemon
July  9 13:56:38 mythbox /usr/bin/mythexport-daemon[29746]: query = SELECT callsign FROM channel WHERE chanid=? at line 438 in /usr/bin/mythexport-daemon
July  9 13:56:38 mythbox /usr/bin/mythexport-daemon[29746]: command = nice -n19 mythtranscode --mpeg2 --honorcutlist --showprogress --chanid 2251 --starttime 20090709080000 2>&1 at line 532 in /usr/bin/mythexport-daemon
July  9 13:57:06 mythbox /usr/bin/mythexport-daemon[29746]: ERROR: cannot remove /videos/mythxport/DISN-Special_Agent_Oso-Carousel_Royale_Leaf_Raker-200907090.mp4.tmp. at line 535 in /usr/bin/mythexport-daemon
July  9 13:57:06 mythbox /usr/bin/mythexport-daemon[29746]: Exporting /videos/mythxport/DISN-Special_Agent_Oso-Carousel_Royale_Leaf_Raker-200907090.mp4
July 10 13:57:06 mythbox /usr/bin/mythexport-daemon[29746]: command = nice -n19 ffmpeg -i /data/recordings/2251_20090709080000.mpg -y -acodec libfaac -ab 192000 -vcodec mpeg4 -b 600000 -mbd 2 -flags +4mv+aic -trellis 2 -cmp 2 -subcmp 2 -s 320x240 -deinterlace -aspect 4:3 '/videos/mythxport/DISN-Special_Agent_Oso-Carousel_Royale_Leaf_Raker-200907090.mp4' 2>&1 at line 539 in /usr/bin/mythexport-daemon


Did ffmpeg run successfully here?  The error listed is a result of trying to remove the commercials (this is new functionality which was submitted to me by another user, so it hasn't been thoroughly tested yet), I would disable that for now until you have everything else working, then you can try enabling it again.

As far as any nuvexport errors, I can't help you much with them.

---

### Post by mraggie on 2009-07-09
> **rhpot1991 said:**
> Did ffmpeg run successfully here?  The error listed is a result of trying to remove the commercials (this is new functionality which was submitted to me by another user, so it hasn't been thoroughly tested yet), I would disable that for now until you have everything else working, then you can try enabling it again.

As far as any nuvexport errors, I can't help you much with them.
Wahoooooooooooo!!!!!!!!!!!, it worked. I actually have an .mp4 file

Thanks for a excellent script

---

### Post by trakon88 on 2009-07-09
hi again,
now everything is installed it doesn't work ... I get this in /var/log/mythtv/mythexport.log
But I can't figure out what that means, help is appreciated ...


July  9 21:23:16 alex-desktop /usr/bin/mythexport-daemon[3389]: ERROR: AtomicParsley '/var/lib/mythtv/mythexport/Das-Erste-Tatort_Die_Frau_im_Zug-Fernsehfilm_Deutschland_20.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork Das-Erste --TVShowName "Tatort: Die Frau im Zug" --TVEpisode "" --TVEpisodeNum  --TVSeason  --description "Kommissar Freddy Schenk ist überarbeitet. Ein abgeschlossener Fall, bei dem er in Notwehr einen russischen Mafiaboss erschoss, lässt ihm keine Ruhe. Er wird daher - gegen seinen Willen - in den Urlaub geschickt." --title "Fernsehfilm Deutschland 2000" 2>&1 FAILED at line 555 in /usr/bin/mythexport-daemon
rm: cannot remove `/var/lib/mythtv/mythexport/Das-Erste-Tatort_Die_Frau_im_Zug-Fernsehfilm_Deutschland_20.mp4': No such file or directory
mv: cannot stat `/var/lib/mythtv/mythexport/*temp*': No such file or directory
July  9 21:23:16 alex-desktop /usr/bin/mythexport-daemon[3389]: ERROR: /var/lib/mythtv/mythexport/Das-Erste-Tatort_Die_Frau_im_Zug-Fernsehfilm_Deutschland_20.mp4 is not available at line 563 in /usr/bin/mythexport-daemon
July  9 21:31:16 alex-desktop /usr/bin/mythexport-daemon[3389]: ERROR: AtomicParsley '/var/lib/mythtv/mythexport/Das-Erste-Tatort_Die_Frau_im_Zug-Fernsehfilm_Deutschland_20.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork Das-Erste --TVShowName "Tatort: Die Frau im Zug" --TVEpisode "" --TVEpisodeNum  --TVSeason  --description "Kommissar Freddy Schenk ist überarbeitet. Ein abgeschlossener Fall, bei dem er in Notwehr einen russischen Mafiaboss erschoss, lässt ihm keine Ruhe. Er wird daher - gegen seinen Willen - in den Urlaub geschickt." --title "Fernsehfilm Deutschland 2000" 2>&1 FAILED at line 555 in /usr/bin/mythexport-daemon
rm: cannot remove `/var/lib/mythtv/mythexport/Das-Erste-Tatort_Die_Frau_im_Zug-Fernsehfilm_Deutschland_20.mp4': No such file or directory
mv: cannot stat `/var/lib/mythtv/mythexport/*temp*': No such file or directory
July  9 21:31:16 alex-desktop /usr/bin/mythexport-daemon[3389]: ERROR: /var/lib/mythtv/mythexport/Das-Erste-Tatort_Die_Frau_im_Zug-Fernsehfilm_Deutschland_20.mp4 is not available at line 563 in /usr/bin/mythexport-daemon

---

### Post by trakon88 on 2009-07-10
Ok I checked it out, the ffmpeg Line makes problems, which may be the wrong parameters :

ffmpeg -i /var/lib/mythtv/recordings/1128_20090703214200.mpg -y -acodec libfaac -ab 192000 -vcodec mpeg4 -b 600000 -mbd 2 -flags +4mv+aic -trellis 2 -cmp 2 -subcmp 2 -s 320x240 -ac 2 -deinterlace -aspect 16:9 '/var/lib/mythtv/mythexport/Das-Erste-Tatort_Die_Frau_im_Zug-Fernsehfilm_Deutschland_20.mp4'
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 50.00 (50/1) -> 25.00 (25/1)
Input #0, mpegts, from '/var/lib/mythtv/recordings/1128_20090703214200.mpg':
  Duration: 01:32:49.17, start: 22401.045133, bitrate: 3261 kb/s
  Program 1 
    Stream #0.0[0x1111]: Video: mpeg2video, yuv420p, 704x576 [PAR 16:11 DAR 16:9], 7000 kb/s, 25 tbr, 90k tbn, 50 tbc
    Stream #0.1[0x1112](ger): Audio: mp2, 48000 Hz, stereo, s16, 192 kb/s
Output #0, mp4, to '/var/lib/mythtv/mythexport/Das-Erste-Tatort_Die_Frau_im_Zug-Fernsehfilm_Deutschland_20.mp4':
    Stream #0.0: Video: mpeg4 (hq), yuv420p, 320x240 [PAR 4:3 DAR 16:9], q=2-31, 600 kb/s, 90k tbn, 25 tbc
    Stream #0.1(ger): Audio: libfaac, stereo, s16, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[libfaac @ 0x9124d00]libfaac doesn't support this output format!
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

---

### Post by andrew.46 on 2009-07-10
Hi trakon88,

> **trakon88 said:**
> 
 ```
[libfaac @ 0x9124d00]libfaac doesn't support this output format!
Error while opening codec for output stream #0.1 - 
maybe incorrect parameters such as bit_rate, rate, width or height

```

I will admit that I was trawling he Forums for FFmpeg information when I bumped into this single post from an obviously long thread, which I have not read in great detail :-). But can I comment that it could very well be that libfaac expects the following in the FFmpeg encoding string:

```
-ar 44100
```

It should be the *default* but perhaps it is required here.

Andrew

---

### Post by rhpot1991 on 2009-07-10
> **andrew.46 said:**
> Hi trakon88,



I will admit that I was trawling he Forums for FFmpeg information when I bumped into this single post from an obviously long thread, which I have not read in great detail :-). But can I comment that it could very well be that libfaac expects the following in the FFmpeg encoding string:

```
-ar 44100
```

It should be the *default* but perhaps it is required here.

Andrew

Someone let me know if that fixes their issues.  You can normally get around that kind of error by specifying your rates in kb, so audio 192kb, video 300kb, etc.  That or I am missing what the actual problem is, so try those two things and respond back.

---

### Post by trakon88 on 2009-07-10
Hi again,
 -ar 44100 did the trick, the commandline on the bottom works. How do I get this into my job - a sugestion? Can I put it in a config file?

best greetings

aleX


 ffmpeg -i /var/lib/mythtv/recordings/1128_20090703214200.mpg -y -acodec libfaac -ar 44100 -ab 192000 -vcodec mpeg4 -b 600000 -mbd 2 -flags +4mv+aic -trellis 2 -cmp 2 -subcmp 2 -s 320x240 -ac 2 -deinterlace -aspect 4:3 '/var/lib/mythtv/mythexport/Das-Erste-Tatort_Die_Frau_im_Zug-Fernsehfilm_Deutschland_20.mp4'

---

### Post by rhpot1991 on 2009-07-10
> **trakon88 said:**
> Hi again,
 -ar 44100 did the trick, the commandline on the bottom works. How do I get this into my job - a sugestion? Can I put it in a config file?

best greetings

aleX


 ffmpeg -i /var/lib/mythtv/recordings/1128_20090703214200.mpg -y -acodec libfaac -ar 44100 -ab 192000 -vcodec mpeg4 -b 600000 -mbd 2 -flags +4mv+aic -trellis 2 -cmp 2 -subcmp 2 -s 320x240 -ac 2 -deinterlace -aspect 4:3 '/var/lib/mythtv/mythexport/Das-Erste-Tatort_Die_Frau_im_Zug-Fernsehfilm_Deutschland_20.mp4'

Just modify /etc/mythtv/mythexport/mythexport_settings.cfg

Tack it onto the end of ffmpegArgs, and keep in mind that changing settings (specifically for this config) in the http interface will overwrite this, so you may need to re-add it at a later point as well.

Did you try changing your -ab to 192kb and -b to 600kb?  I'd be interested to see if that fixes the issue as well, or if I need to make "-ar 44100" added by default.

---

### Post by trakon88 on 2009-07-10
hi
I had to leave -ar 44100 in the commandline, changing to xxxkb solely didn't help

thanx aleX

---

### Post by trakon88 on 2009-07-11
Hi again,
 
I tried to use the cutlist option it didn't work ... see the bottomline ...
Is there any possibility to find out what went wrong, because this maybe a issue with mythtv and not mythexport ... I have no idea. I already did mytharchive on DVD ans thi honored the cutlist.
 
aleX 
 
 
 
July 10 23:06:53 alex-desktop /usr/bin/mythexport-daemon[3383]: ERROR: cannot remove /var/lib/mythtv/mythexport/Das-Erste-Tatort_Die_Frau_im_Zug-Fernsehfilm_Deutschland_20.mp4.tmp. at line 535 in /usr/bin/mythexport-daemon
July 10 23:06:53 alex-desktop /usr/bin/mythexport-daemon[3383]: Exporting /var/lib/mythtv/mythexport/Das-Erste-Tatort_Die_Frau_im_Zug-Fernsehfilm_Deutschland_20.mp4
July 10 23:06:56 alex-desktop /usr/bin/mythexport-daemon[3383]: ERROR: nice -n19 ffmpeg -i /var/lib/mythtv/recordings/1128_20090703214200.mpg -y -acodec libfaac -ar 44100 -ab 192kb -vcodec mpeg4 -b 1200kb -mbd 2 -flags +4mv+aic -trellis 2 -cmp 2 -subcmp 2 -s 320x240 -ac 2 -deinterlace -aspect 4:3 '/var/lib/mythtv/mythexport/Das-Erste-Tatort_Die_Frau_im_Zug-Fernsehfilm_Deutschland_20.mp4' 2>&1 FAILED/ at line 540 in /usr/bin/mythexport-daemon

---

### Post by bob.os on 2009-07-12
I'm not entirely sure if this should go in a separate thread for MythExport or not, but here goes:

Since the release of iPhone software v 3.0, I'm unable to play back the videos I've encoded and downloaded using MythExport on the iPhone.

I had everything set up, the scripts ran, the files downloaded into iTunes and everything played just right on the iPhone.  Once v3.0 came out though, the files download in iTunes and transfer properly to the iPhone, but the podcast no longer shows up on the phone.  I can search for the video files using the new Spotlight feature, but when I find them, they won't play.

I've verified that the files are properly formatted by downloading them in NetNewswire and dropping them into iTunes to sync to the phone.  They play properly on the iPhone that way and also show in the 'TV Shows' section of the Library in iTunes (which they don't when downloaded as a Podcast)

When this started, I was running Ubuntu 8.10 and an early version of MythExport, along with an original iPhone.  I've since upgraded the MythTV machine to Jaunty, and brought MythExport up to current (2.01), along with upgrading to an iPhone 3G_S with no change in the behavior.  (The phone upgrade was incidental, the server upgrades were overdue:p) On the odd chance that remnants of the jailbreak on my original phone was causing problems, I tested a freshly restored iPhone with no luck.

My guess is that some change in iTunes 8.2 or the iPhone 3.0 software is causing this, and that the solution lies in AtomicParsley.  I'm cross-posting to the AtomicParsley support board for that reason.  There seem to be some related Apple Support Forum discussions, all related to iPhone OS 3.0.

Is anyone else having this issue?  Let me know if more info is needed.

---

### Post by rhpot1991 on 2009-07-12
> **bob.os said:**
> I'm not entirely sure if this should go in a separate thread for MythExport or not, but here goes:

Since the release of iPhone software v 3.0, I'm unable to play back the videos I've encoded and downloaded using MythExport on the iPhone.

I had everything set up, the scripts ran, the files downloaded into iTunes and everything played just right on the iPhone.  Once v3.0 came out though, the files download in iTunes and transfer properly to the iPhone, but the podcast no longer shows up on the phone.  I can search for the video files using the new Spotlight feature, but when I find them, they won't play.

I've verified that the files are properly formatted by downloading them in NetNewswire and dropping them into iTunes to sync to the phone.  They play properly on the iPhone that way and also show in the 'TV Shows' section of the Library in iTunes (which they don't when downloaded as a Podcast)

When this started, I was running Ubuntu 8.10 and an early version of MythExport, along with an original iPhone.  I've since upgraded the MythTV machine to Jaunty, and brought MythExport up to current (2.01), along with upgrading to an iPhone 3G_S with no change in the behavior.  (The phone upgrade was incidental, the server upgrades were overdue:p) On the odd chance that remnants of the jailbreak on my original phone was causing problems, I tested a freshly restored iPhone with no luck.

My guess is that some change in iTunes 8.2 or the iPhone 3.0 software is causing this, and that the solution lies in AtomicParsley.  I'm cross-posting to the AtomicParsley support board for that reason.  There seem to be some related Apple Support Forum discussions, all related to iPhone OS 3.0.

Is anyone else having this issue?  Let me know if more info is needed.

Let me know what the final outcome to all of this is.  I can put a new version of AtomicParsley on the testing PPA and get it into Karmic.

---

### Post by rhpot1991 on 2009-07-13
> **trakon88 said:**
> Hi again,
 
I tried to use the cutlist option it didn't work ... see the bottomline ...
Is there any possibility to find out what went wrong, because this maybe a issue with mythtv and not mythexport ... I have no idea. I already did mytharchive on DVD ans thi honored the cutlist.
 
aleX 
 
 
 
July 10 23:06:53 alex-desktop /usr/bin/mythexport-daemon[3383]: ERROR: cannot remove /var/lib/mythtv/mythexport/Das-Erste-Tatort_Die_Frau_im_Zug-Fernsehfilm_Deutschland_20.mp4.tmp. at line 535 in /usr/bin/mythexport-daemon
July 10 23:06:53 alex-desktop /usr/bin/mythexport-daemon[3383]: Exporting /var/lib/mythtv/mythexport/Das-Erste-Tatort_Die_Frau_im_Zug-Fernsehfilm_Deutschland_20.mp4
July 10 23:06:56 alex-desktop /usr/bin/mythexport-daemon[3383]: ERROR: nice -n19 ffmpeg -i /var/lib/mythtv/recordings/1128_20090703214200.mpg -y -acodec libfaac -ar 44100 -ab 192kb -vcodec mpeg4 -b 1200kb -mbd 2 -flags +4mv+aic -trellis 2 -cmp 2 -subcmp 2 -s 320x240 -ac 2 -deinterlace -aspect 4:3 '/var/lib/mythtv/mythexport/Das-Erste-Tatort_Die_Frau_im_Zug-Fernsehfilm_Deutschland_20.mp4' 2>&1 FAILED/ at line 540 in /usr/bin/mythexport-daemon

No promises on the cutlist functionality.  It was submitted by another user, who claims it worked well for them.  My opinion has always been that you should remove commercials by hand first, as the commflaging makes too many errors to be fully trusted.

---

### Post by QuaffAPint on 2009-07-17
First off - It's working great :D

I'm using it to simply export symlinks for backing up to my Windows box with nicer named (ie, more meaningfully named) files.

I've noticed though the file names are, like such...

'CHANNEL-TitleThatIsReall'

Meaning, it cuts off the title at some point (understandable) - But, what I would REALLY like is to have the date in there - right after the channel.

Also, there are no '.mpg' extensions.  I don't know if it was just cut off do to file length, or what - but, it would be nice to retain those.

So, something similar to Knoppmyth's 'pretty' directory filenames, for example:
*Smurfs - 2009-07-09, 9-30 AM - All That Glitters Isn't Smurf; Dreamy's Nightmare.mpg*


Thanks!

---

### Post by trakon88 on 2009-07-18
> **rhpot1991 said:**
> No promises on the cutlist functionality.  It was submitted by another user, who claims it worked well for them.  My opinion has always been that you should remove commercials by hand first, as the commflaging makes too many errors to be fully trusted.

Hi 
I also remove the commercials by hand, but how does mythexport read my cutlist. How do you export your stuff without commercials?

thanx AleX

---

### Post by rhpot1991 on 2009-07-18
> **trakon88 said:**
> Hi 
I also remove the commercials by hand, but how does mythexport read my cutlist. How do you export your stuff without commercials?

thanx AleX

I follow this and do it by hand: [http://www.mythtv.org/wiki/Removing_Commercials](http://www.mythtv.org/wiki/Removing_Commercials)

In theory MythExport should do the same with the cutlist that is generated from the commflagging.  I  haven't had all that much feed back on how well it works though.

---

### Post by smckay79 on 2009-07-31
Hey Guys,

Im trying to figure out how to get this to work as well...

Below is my logs with debug enabled... some help would be much appreciated. 

Cheers

Scott
```

July 31 10:39:50 mythtv /usr/bin/mythexport-daemon[20883]: Going into new mode
 at line 430 in /usr/bin/mythexport-daemon
July 31 10:39:50 mythtv /usr/bin/mythexport-daemon[20883]: query = SELECT callsign FROM channel WHERE chanid=? at line 438 in /usr/bin/mythexport-daemon
July 31 10:39:50 mythtv /usr/bin/mythexport-daemon[20883]: command = nice -n19 mythtranscode --mpeg2 --honorcutlist --showprogress --chanid 1033 --starttime 20090731070000 2>&1 at line 532 in /usr/bin/mythexport-daemon
July 31 10:41:04 mythtv /usr/bin/mythexport-daemon[20883]: ERROR: cannot remove /home/scott/Videos/SLICE-Til_Debt_Do_Us_Part-Gambling_With_Debt-20090731070000.mp4.tmp. at line 535 in /usr/bin/mythexport-daemon
July 31 10:41:04 mythtv /usr/bin/mythexport-daemon[20883]: Exporting /home/scott/Videos/SLICE-Til_Debt_Do_Us_Part-Gambling_With_Debt-20090731070000.mp4
July 31 10:41:04 mythtv /usr/bin/mythexport-daemon[20883]: command = nice -n19 ffmpeg -i /var/lib/mythtv/recordings/1033_20090731070000.mpg -y -an -v 1 -vcodec h264 -b 600kb -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 1 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq blurCplx^(1-qComp) -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 480x320 -aspect 4:3 -f mp4 -pass 1 /dev/null at line 539 in /usr/bin/mythexport-daemon
sh: Syntax error: "(" unexpected
July 31 10:41:04 mythtv /usr/bin/mythexport-daemon[20883]: ERROR: nice -n19 ffmpeg -i /var/lib/mythtv/recordings/1033_20090731070000.mpg -y -an -v 1 -vcodec h264 -b 600kb -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 1 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq blurCplx^(1-qComp) -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 480x320 -aspect 4:3 -f mp4 -pass 1 /dev/null FAILED/ at line 540 in /usr/bin/mythexport-daemon
July 31 10:41:04 mythtv /usr/bin/mythexport-daemon[20883]: Exporting /home/scott/Videos/SLICE-Til_Debt_Do_Us_Part-Gambling_With_Debt-20090731070000.mp4
July 31 10:41:04 mythtv /usr/bin/mythexport-daemon[20883]: command = nice -n19 ffmpeg -i /var/lib/mythtv/recordings/1033_20090731070000.mpg -y -v 1 -vcodec h264 -b 600kb -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 6 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq blurCplx^(1-qComp) -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 480x320 -aspect 4:3 -acodec libfaac -ab 192kb -ar 48000 -ac 2 -f mp4 -pass 2 '/home/scott/Videos/SLICE-Til_Debt_Do_Us_Part-Gambling_With_Debt-20090731070000.mp4' 2>&1 at line 539 in /usr/bin/mythexport-daemon
sh: Syntax error: "(" unexpected
July 31 10:41:04 mythtv /usr/bin/mythexport-daemon[20883]: ERROR: nice -n19 ffmpeg -i /var/lib/mythtv/recordings/1033_20090731070000.mpg -y -v 1 -vcodec h264 -b 600kb -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 6 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq blurCplx^(1-qComp) -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 480x320 -aspect 4:3 -acodec libfaac -ab 192kb -ar 48000 -ac 2 -f mp4 -pass 2 '/home/scott/Videos/SLICE-Til_Debt_Do_Us_Part-Gambling_With_Debt-20090731070000.mp4' 2>&1 FAILED/ at line 540 in /usr/bin/mythexport-daemon
July 31 10:41:04 mythtv /usr/bin/mythexport-daemon[20883]: command = AtomicParsley '/home/scott/Videos/SLICE-Til_Debt_Do_Us_Part-Gambling_With_Debt-20090731070000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork SLICE --TVShowName "Til Debt Do Us Part" --TVEpisode "EP007827980062" --TVEpisodeNum 60 --TVSeason 50 --description "Chris is desperate to win back his wife's trust after his gambling landed them in debt." --title "Gambling With Debt" 2>&1 at line 554 in /usr/bin/mythexport-daemon
July 31 10:41:04 mythtv /usr/bin/mythexport-daemon[20883]: ERROR: AtomicParsley '/home/scott/Videos/SLICE-Til_Debt_Do_Us_Part-Gambling_With_Debt-20090731070000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork SLICE --TVShowName "Til Debt Do Us Part" --TVEpisode "EP007827980062" --TVEpisodeNum 60 --TVSeason 50 --description "Chris is desperate to win back his wife's trust after his gambling landed them in debt." --title "Gambling With Debt" 2>&1 FAILED at line 555 in /usr/bin/mythexport-daemon
rm: cannot remove `/home/scott/Videos/SLICE-Til_Debt_Do_Us_Part-Gambling_With_Debt-20090731070000.mp4': No such file or directory
mv: cannot stat `/home/scott/Videos/*temp*': No such file or directory
July 31 10:41:04 mythtv /usr/bin/mythexport-daemon[20883]: ERROR: /home/scott/Videos/SLICE-Til_Debt_Do_Us_Part-Gambling_With_Debt-20090731070000.mp4 is not available at line 563 in /usr/bin/mythexport-daemon
July 31 10:41:04 mythtv /usr/bin/mythexport-daemon[20883]: query = INSERT into mythexport VALUES(NULL,?,?,?,?,NOW(),DATE_ADD(NOW(),INTERVAL ? DAY),?,?) at line 569 in /usr/bin/mythexport-daemon
July 31 10:41:04 mythtv /usr/bin/mythexport-daemon[20883]: query = delete from mythexport_job_queue where id=? at line 636 in /usr/bin/mythexport-daemon
July 31 10:42:04 mythtv /usr/bin/mythexport-daemon[20883]: query = select id, type, param from mythexport_job_queue order by id at line 607 in /usr/bin/mythexport-daemon
July 31 10:42:04 mythtv /usr/bin/mythexport-daemon[20883]: exportdir = /home/scott/Videos at line 396 in /usr/bin/mythexport-daemon
July 31 10:42:04 mythtv /usr/bin/mythexport-daemon[20883]: starttime = 20090731070000 at line 397 in /usr/bin/mythexport-daemon
July 31 10:42:04 mythtv /usr/bin/mythexport-daemon[20883]: chanid = 1033 at line 398 in /usr/bin/mythexport-daemon
July 31 10:42:04 mythtv /usr/bin/mythexport-daemon[20883]: config = Iphone at line 399 in /usr/bin/mythexport-daemon
July 31 10:42:04 mythtv /usr/bin/mythexport-daemon[20883]: query = SELECT rec.title, rec.subtitle, rec.description, pg.syndicatedepisodenumber, pg.showtype, rec.programid, rec.basename, rec.starttime
    FROM recorded rec LEFT JOIN program pg ON pg.starttime = rec.starttime AND pg.chanid = rec.chanid
    WHERE rec.chanid=? AND rec.starttime=? at line 413 in /usr/bin/mythexport-daemon
July 31 10:42:04 mythtv /usr/bin/mythexport-daemon[20883]: Going into new mode
 at line 430 in /usr/bin/mythexport-daemon
July 31 10:42:04 mythtv /usr/bin/mythexport-daemon[20883]: query = SELECT callsign FROM channel WHERE chanid=? at line 438 in /usr/bin/mythexport-daemon
July 31 10:42:04 mythtv /usr/bin/mythexport-daemon[20883]: command = nice -n19 mythtranscode --mpeg2 --honorcutlist --showprogress --chanid 1033 --starttime 20090731070000 2>&1 at line 532 in /usr/bin/mythexport-daemon

```

---

### Post by rhpot1991 on 2009-07-31
> **smckay79 said:**
> Hey Guys,

Im trying to figure out how to get this to work as well...

Below is my logs with debug enabled... some help would be much appreciated. 

Cheers

Scott
```

July 31 10:39:50 mythtv /usr/bin/mythexport-daemon[20883]: Going into new mode
 at line 430 in /usr/bin/mythexport-daemon
July 31 10:39:50 mythtv /usr/bin/mythexport-daemon[20883]: query = SELECT callsign FROM channel WHERE chanid=? at line 438 in /usr/bin/mythexport-daemon
July 31 10:39:50 mythtv /usr/bin/mythexport-daemon[20883]: command = nice -n19 mythtranscode --mpeg2 --honorcutlist --showprogress --chanid 1033 --starttime 20090731070000 2>&1 at line 532 in /usr/bin/mythexport-daemon
July 31 10:41:04 mythtv /usr/bin/mythexport-daemon[20883]: ERROR: cannot remove /home/scott/Videos/SLICE-Til_Debt_Do_Us_Part-Gambling_With_Debt-20090731070000.mp4.tmp. at line 535 in /usr/bin/mythexport-daemon
July 31 10:41:04 mythtv /usr/bin/mythexport-daemon[20883]: Exporting /home/scott/Videos/SLICE-Til_Debt_Do_Us_Part-Gambling_With_Debt-20090731070000.mp4
July 31 10:41:04 mythtv /usr/bin/mythexport-daemon[20883]: command = nice -n19 ffmpeg -i /var/lib/mythtv/recordings/1033_20090731070000.mpg -y -an -v 1 -vcodec h264 -b 600kb -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 1 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq blurCplx^(1-qComp) -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 480x320 -aspect 4:3 -f mp4 -pass 1 /dev/null at line 539 in /usr/bin/mythexport-daemon
sh: Syntax error: "(" unexpected
July 31 10:41:04 mythtv /usr/bin/mythexport-daemon[20883]: ERROR: nice -n19 ffmpeg -i /var/lib/mythtv/recordings/1033_20090731070000.mpg -y -an -v 1 -vcodec h264 -b 600kb -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 1 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq blurCplx^(1-qComp) -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 480x320 -aspect 4:3 -f mp4 -pass 1 /dev/null FAILED/ at line 540 in /usr/bin/mythexport-daemon
July 31 10:41:04 mythtv /usr/bin/mythexport-daemon[20883]: Exporting /home/scott/Videos/SLICE-Til_Debt_Do_Us_Part-Gambling_With_Debt-20090731070000.mp4
July 31 10:41:04 mythtv /usr/bin/mythexport-daemon[20883]: command = nice -n19 ffmpeg -i /var/lib/mythtv/recordings/1033_20090731070000.mpg -y -v 1 -vcodec h264 -b 600kb -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 6 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq blurCplx^(1-qComp) -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 480x320 -aspect 4:3 -acodec libfaac -ab 192kb -ar 48000 -ac 2 -f mp4 -pass 2 '/home/scott/Videos/SLICE-Til_Debt_Do_Us_Part-Gambling_With_Debt-20090731070000.mp4' 2>&1 at line 539 in /usr/bin/mythexport-daemon
sh: Syntax error: "(" unexpected
July 31 10:41:04 mythtv /usr/bin/mythexport-daemon[20883]: ERROR: nice -n19 ffmpeg -i /var/lib/mythtv/recordings/1033_20090731070000.mpg -y -v 1 -vcodec h264 -b 600kb -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 6 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq blurCplx^(1-qComp) -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 480x320 -aspect 4:3 -acodec libfaac -ab 192kb -ar 48000 -ac 2 -f mp4 -pass 2 '/home/scott/Videos/SLICE-Til_Debt_Do_Us_Part-Gambling_With_Debt-20090731070000.mp4' 2>&1 FAILED/ at line 540 in /usr/bin/mythexport-daemon
July 31 10:41:04 mythtv /usr/bin/mythexport-daemon[20883]: command = AtomicParsley '/home/scott/Videos/SLICE-Til_Debt_Do_Us_Part-Gambling_With_Debt-20090731070000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork SLICE --TVShowName "Til Debt Do Us Part" --TVEpisode "EP007827980062" --TVEpisodeNum 60 --TVSeason 50 --description "Chris is desperate to win back his wife's trust after his gambling landed them in debt." --title "Gambling With Debt" 2>&1 at line 554 in /usr/bin/mythexport-daemon
July 31 10:41:04 mythtv /usr/bin/mythexport-daemon[20883]: ERROR: AtomicParsley '/home/scott/Videos/SLICE-Til_Debt_Do_Us_Part-Gambling_With_Debt-20090731070000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork SLICE --TVShowName "Til Debt Do Us Part" --TVEpisode "EP007827980062" --TVEpisodeNum 60 --TVSeason 50 --description "Chris is desperate to win back his wife's trust after his gambling landed them in debt." --title "Gambling With Debt" 2>&1 FAILED at line 555 in /usr/bin/mythexport-daemon
rm: cannot remove `/home/scott/Videos/SLICE-Til_Debt_Do_Us_Part-Gambling_With_Debt-20090731070000.mp4': No such file or directory
mv: cannot stat `/home/scott/Videos/*temp*': No such file or directory
July 31 10:41:04 mythtv /usr/bin/mythexport-daemon[20883]: ERROR: /home/scott/Videos/SLICE-Til_Debt_Do_Us_Part-Gambling_With_Debt-20090731070000.mp4 is not available at line 563 in /usr/bin/mythexport-daemon
July 31 10:41:04 mythtv /usr/bin/mythexport-daemon[20883]: query = INSERT into mythexport VALUES(NULL,?,?,?,?,NOW(),DATE_ADD(NOW(),INTERVAL ? DAY),?,?) at line 569 in /usr/bin/mythexport-daemon
July 31 10:41:04 mythtv /usr/bin/mythexport-daemon[20883]: query = delete from mythexport_job_queue where id=? at line 636 in /usr/bin/mythexport-daemon
July 31 10:42:04 mythtv /usr/bin/mythexport-daemon[20883]: query = select id, type, param from mythexport_job_queue order by id at line 607 in /usr/bin/mythexport-daemon
July 31 10:42:04 mythtv /usr/bin/mythexport-daemon[20883]: exportdir = /home/scott/Videos at line 396 in /usr/bin/mythexport-daemon
July 31 10:42:04 mythtv /usr/bin/mythexport-daemon[20883]: starttime = 20090731070000 at line 397 in /usr/bin/mythexport-daemon
July 31 10:42:04 mythtv /usr/bin/mythexport-daemon[20883]: chanid = 1033 at line 398 in /usr/bin/mythexport-daemon
July 31 10:42:04 mythtv /usr/bin/mythexport-daemon[20883]: config = Iphone at line 399 in /usr/bin/mythexport-daemon
July 31 10:42:04 mythtv /usr/bin/mythexport-daemon[20883]: query = SELECT rec.title, rec.subtitle, rec.description, pg.syndicatedepisodenumber, pg.showtype, rec.programid, rec.basename, rec.starttime
    FROM recorded rec LEFT JOIN program pg ON pg.starttime = rec.starttime AND pg.chanid = rec.chanid
    WHERE rec.chanid=? AND rec.starttime=? at line 413 in /usr/bin/mythexport-daemon
July 31 10:42:04 mythtv /usr/bin/mythexport-daemon[20883]: Going into new mode
 at line 430 in /usr/bin/mythexport-daemon
July 31 10:42:04 mythtv /usr/bin/mythexport-daemon[20883]: query = SELECT callsign FROM channel WHERE chanid=? at line 438 in /usr/bin/mythexport-daemon
July 31 10:42:04 mythtv /usr/bin/mythexport-daemon[20883]: command = nice -n19 mythtranscode --mpeg2 --honorcutlist --showprogress --chanid 1033 --starttime 20090731070000 2>&1 at line 532 in /usr/bin/mythexport-daemon

```

Have you tried running the ffmpeg lines by hand?  If that fails, adjust them till they work, then modify them in the config.

---

### Post by Kepesk on 2009-08-06
> **Calmor said:**
> I've tried to run a few jobs to transcode to PSP, in the hopes of testing the PSP switches.  Automatically flagged user jobs (set in Mythweb to export to PSP) and manually run jobs (clicked the user job in Mythweb) show as running successfully in Mythweb, but they do not execute in Mythexport. 

Mythexport showed these as jobs in the job queue, but mythexport.log showed no mention of these new jobs, only that the daemon was started at bootup.  Two of them have been in the queue all night, so waiting for system resources is not an issue.  I was able to delete the jobs using the web interface and create new ones using Mythweb.

Restarting the daemon apparently did the trick, and showed a perl error message.

```

$ sudo /etc/init.d/mythexport restart
 * Restarting MythExport Daemon: mythexport                                     No /usr/bin/perl found running; none killed.
                                                                         [ OK ]

```

Trying to restart mythexport again showed:

```

$ sudo /etc/init.d/mythexport restart
 * Restarting MythExport Daemon: mythexport                                     /usr/bin/perl already running.

```

But, the daemon continued to run and the jobs began to be executed.

Anything you'd like me to try out?

Thanks!

Update - As a further test, after the queued jobs were completed, subsequent jobs also needed the daemon restarted to run.  I didn't give them as much time in the queue (about 20 minutes), but they started immediately upon restarting the daemon.

I am having the exact same issue.  Jobs add to Mythexport's job queue okay, but none of them execute till I restart the daemon.  I did see you updated the PPA with a potential fix, but I've never updated from the PPA before, and after searching for an hour, I can't find instructions on how to do that.  Could someone point me in the right direction?

Thanks!

---

### Post by dannyboy79 on 2009-08-08
> **Kepesk said:**
> I am having the exact same issue.  Jobs add to Mythexport's job queue okay, but none of them execute till I restart the daemon.  I did see you updated the PPA with a potential fix, but I've never updated from the PPA before, and after searching for an hour, I can't find instructions on how to do that.  Could someone point me in the right direction?

Thanks!
never updated from a ppa before? all you have to do is enable the ppa within synaptic and add the gpg key. then just update synaptic and do an apply all upgrades and it should automatically update. that's it.

---

### Post by rhpot1991 on 2009-08-19
> **Kepesk said:**
> I am having the exact same issue.  Jobs add to Mythexport's job queue okay, but none of them execute till I restart the daemon.  I did see you updated the PPA with a potential fix, but I've never updated from the PPA before, and after searching for an hour, I can't find instructions on how to do that.  Could someone point me in the right direction?

Thanks!

Easiest way is to use the mythbuntu repos package to enable to the testing PPA:
[http://www.mythbuntu.com/auto-builds](http://www.mythbuntu.com/auto-builds)

---

### Post by lokimon on 2009-09-26
i'm having the same issue that i have not seen a solution listed for.

with debugging enabled or not, i get the following error when i submit a job:

```
September 26 15:29:10 media /usr/bin/mythexport-daemon[388]: ERROR: AtomicParsley '/var/lib/mythtv/mythexport/COMEDY-The_Colbert_Report-Ken_Burns-20090924233000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork COMEDY --TVShowName "The Colbert Report" --TVEpisode "EP007746990660" --TVEpisodeNum 22 --TVSeason 51 --description "Ken Burns." --title "Ken Burns" 2>&1 FAILED at line 555 in /usr/bin/mythexport-daemon
rm: cannot remove `/var/lib/mythtv/mythexport/COMEDY-The_Colbert_Report-Ken_Burns-20090924233000.mp4': No such file or directory
mv: cannot stat `/var/lib/mythtv/mythexport/*temp*': No such file or directory
September 26 15:29:10 media /usr/bin/mythexport-daemon[388]: ERROR: /var/lib/mythtv/mythexport/COMEDY-The_Colbert_Report-Ken_Burns-20090924233000.mp4 is not available at line 563 in /usr/bin/mythexport-daemon


```

atomic parsley seems to fail with line 555 in /usr/bin/mythexport-daemon for some reason.

after reading this thread i:

1) set the ffmpeg args to -ar 44100
2) set up daily updates and installed the very latest mythexport (2.01)
3) tried the basic default settings from the wiki (mpeg4, 240x320, 192kb 600kb)

still no matter what the line 555 error is always there.

any suggestions?

---

### Post by rhpot1991 on 2009-09-27
> **lokimon said:**
> i'm having the same issue that i have not seen a solution listed for.

with debugging enabled or not, i get the following error when i submit a job:

```
September 26 15:29:10 media /usr/bin/mythexport-daemon[388]: ERROR: AtomicParsley '/var/lib/mythtv/mythexport/COMEDY-The_Colbert_Report-Ken_Burns-20090924233000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork COMEDY --TVShowName "The Colbert Report" --TVEpisode "EP007746990660" --TVEpisodeNum 22 --TVSeason 51 --description "Ken Burns." --title "Ken Burns" 2>&1 FAILED at line 555 in /usr/bin/mythexport-daemon
rm: cannot remove `/var/lib/mythtv/mythexport/COMEDY-The_Colbert_Report-Ken_Burns-20090924233000.mp4': No such file or directory
mv: cannot stat `/var/lib/mythtv/mythexport/*temp*': No such file or directory
September 26 15:29:10 media /usr/bin/mythexport-daemon[388]: ERROR: /var/lib/mythtv/mythexport/COMEDY-The_Colbert_Report-Ken_Burns-20090924233000.mp4 is not available at line 563 in /usr/bin/mythexport-daemon


```

atomic parsley seems to fail with line 555 in /usr/bin/mythexport-daemon for some reason.

after reading this thread i:

1) set the ffmpeg args to -ar 44100
2) set up daily updates and installed the very latest mythexport (2.01)
3) tried the basic default settings from the wiki (mpeg4, 240x320, 192kb 600kb)

still no matter what the line 555 error is always there.

any suggestions?

Have a space in your configuration name?

---

### Post by lokimon on 2009-09-27
> **rhpot1991 said:**
> Have a space in your configuration name?

actually, no, i forgot to mention that i replaced the spaces in my configuration names with "."

---

### Post by rhpot1991 on 2009-09-27
> **lokimon said:**
> actually, no, i forgot to mention that i replaced the spaces in my configuration names with "."

Replace them with "_" and then restart everything.  See if that works.

---

### Post by lokimon on 2009-09-27
> **rhpot1991 said:**
> Replace them with "_" and then restart everything.  See if that works.

thanks, here's what i got then, seems like i got past atomic parsley and now am into the realm of ffmpeg errors:

```
September 27 15:01:42 media /usr/bin/mythexport-daemon[388]: Caught SIGTERM:  exiting gracefully
September 27 15:01:42 media /usr/bin/mythexport-daemon[388]: Stopping Processing:  1254078102
September 27 15:01:46 media /usr/bin/mythexport-daemon[4250]: Starting Processing:  1254078106
September 27 15:06:47 media /usr/bin/mythexport-daemon[4250]: Exporting /var/lib/mythtv/mythexport/COMEDY-The_Colbert_Report-Ken_Burns-20090924233000.mp4
sh: Syntax error: "(" unexpected
September 27 15:06:47 media /usr/bin/mythexport-daemon[4250]: ERROR: nice -n19 ffmpeg -i /var/lib/mythtv/recordings/1117_20090924233000.mpg -y -an -v 1 -vcodec h264 -b 600kb -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 1 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq blurCplx^(1-qComp) -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 480x320 -aspect 4:3 -f mp4 -pass 1 /dev/null FAILED/ at line 540 in /usr/bin/mythexport-daemon
September 27 15:06:47 media /usr/bin/mythexport-daemon[4250]: Exporting /var/lib/mythtv/mythexport/COMEDY-The_Colbert_Report-Ken_Burns-20090924233000.mp4
sh: Syntax error: "(" unexpected
September 27 15:06:47 media /usr/bin/mythexport-daemon[4250]: ERROR: nice -n19 ffmpeg -i /var/lib/mythtv/recordings/1117_20090924233000.mpg -y -v 1 -vcodec h264 -b 600kb -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 6 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq blurCplx^(1-qComp) -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 480x320 -aspect 4:3 -acodec libfaac -ab 192 -ar 44100 -ac 2 -f mp4 -pass 2 '/var/lib/mythtv/mythexport/COMEDY-The_Colbert_Report-Ken_Burns-20090924233000.mp4' 2>&1 FAILED/ at line 540 in /usr/bin/mythexport-daemon
September 27 15:06:47 media /usr/bin/mythexport-daemon[4250]: ERROR: AtomicParsley '/var/lib/mythtv/mythexport/COMEDY-The_Colbert_Report-Ken_Burns-20090924233000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork COMEDY --TVShowName "The Colbert Report" --TVEpisode "EP007746990660" --TVEpisodeNum 22 --TVSeason 51 --description "Ken Burns." --title "Ken Burns" 2>&1 FAILED at line 555 in /usr/bin/mythexport-daemon
rm: cannot remove `/var/lib/mythtv/mythexport/COMEDY-The_Colbert_Report-Ken_Burns-20090924233000.mp4': No such file or directory
mv: cannot stat `/var/lib/mythtv/mythexport/*temp*': No such file or directory
September 27 15:06:47 media /usr/bin/mythexport-daemon[4250]: ERROR: /var/lib/mythtv/mythexport/COMEDY-The_Colbert_Report-Ken_Burns-20090924233000.mp4 is not available at line 563 in /usr/bin/mythexport-daemon


```

i tried to run this on the command line:

```
nice -n19 ffmpeg -i /var/lib/mythtv/recordings/1117_20090924233000.mpg -y -an -v 1 -vcodec h264 -b 600kb -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 1 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq blurCplx^(1-qComp) -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 480x320 -aspect 4:3 -f mp4 -pass 1 /dev/null
```

but just got the same error:

-bash: syntax error near unexpected token `('

did i screw up trying to run the command in a shell?

---

### Post by lokimon on 2009-09-29
> **lokimon said:**
> thanks, here's what i got then, seems like i got past atomic parsley and now am into the realm of ffmpeg errors:

```
September 27 15:01:42 media /usr/bin/mythexport-daemon[388]: Caught SIGTERM:  exiting gracefully
September 27 15:01:42 media /usr/bin/mythexport-daemon[388]: Stopping Processing:  1254078102
September 27 15:01:46 media /usr/bin/mythexport-daemon[4250]: Starting Processing:  1254078106
September 27 15:06:47 media /usr/bin/mythexport-daemon[4250]: Exporting /var/lib/mythtv/mythexport/COMEDY-The_Colbert_Report-Ken_Burns-20090924233000.mp4
sh: Syntax error: "(" unexpected
September 27 15:06:47 media /usr/bin/mythexport-daemon[4250]: ERROR: nice -n19 ffmpeg -i /var/lib/mythtv/recordings/1117_20090924233000.mpg -y -an -v 1 -vcodec h264 -b 600kb -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 1 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq blurCplx^(1-qComp) -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 480x320 -aspect 4:3 -f mp4 -pass 1 /dev/null FAILED/ at line 540 in /usr/bin/mythexport-daemon
September 27 15:06:47 media /usr/bin/mythexport-daemon[4250]: Exporting /var/lib/mythtv/mythexport/COMEDY-The_Colbert_Report-Ken_Burns-20090924233000.mp4
sh: Syntax error: "(" unexpected
September 27 15:06:47 media /usr/bin/mythexport-daemon[4250]: ERROR: nice -n19 ffmpeg -i /var/lib/mythtv/recordings/1117_20090924233000.mpg -y -v 1 -vcodec h264 -b 600kb -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 6 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq blurCplx^(1-qComp) -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 480x320 -aspect 4:3 -acodec libfaac -ab 192 -ar 44100 -ac 2 -f mp4 -pass 2 '/var/lib/mythtv/mythexport/COMEDY-The_Colbert_Report-Ken_Burns-20090924233000.mp4' 2>&1 FAILED/ at line 540 in /usr/bin/mythexport-daemon
September 27 15:06:47 media /usr/bin/mythexport-daemon[4250]: ERROR: AtomicParsley '/var/lib/mythtv/mythexport/COMEDY-The_Colbert_Report-Ken_Burns-20090924233000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork COMEDY --TVShowName "The Colbert Report" --TVEpisode "EP007746990660" --TVEpisodeNum 22 --TVSeason 51 --description "Ken Burns." --title "Ken Burns" 2>&1 FAILED at line 555 in /usr/bin/mythexport-daemon
rm: cannot remove `/var/lib/mythtv/mythexport/COMEDY-The_Colbert_Report-Ken_Burns-20090924233000.mp4': No such file or directory
mv: cannot stat `/var/lib/mythtv/mythexport/*temp*': No such file or directory
September 27 15:06:47 media /usr/bin/mythexport-daemon[4250]: ERROR: /var/lib/mythtv/mythexport/COMEDY-The_Colbert_Report-Ken_Burns-20090924233000.mp4 is not available at line 563 in /usr/bin/mythexport-daemon


```

i tried to run this on the command line:

```
nice -n19 ffmpeg -i /var/lib/mythtv/recordings/1117_20090924233000.mpg -y -an -v 1 -vcodec h264 -b 600kb -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 1 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq blurCplx^(1-qComp) -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 480x320 -aspect 4:3 -f mp4 -pass 1 /dev/null
```

but just got the same error:

-bash: syntax error near unexpected token `('

did i screw up trying to run the command in a shell?

i noticed that i had the resolution set wrong (480x320) as opposed to the 320x240 listed on the wiki as the base settings.

i changed the resolution to 320x240 and the job ran, but the audio sync is off.  i will play with the resolution and see what i can get to work, but how can i fix the audio sync issue?

---

### Post by rhpot1991 on 2009-09-29
> **lokimon said:**
> i noticed that i had the resolution set wrong (480x320) as opposed to the 320x240 listed on the wiki as the base settings.

i changed the resolution to 320x240 and the job ran, but the audio sync is off.  i will play with the resolution and see what i can get to work, but how can i fix the audio sync issue?

I would try the -async flag and see if it helps you much.  Try -async 1 or -async 2 and see if the results are any better.  Just add this to the ffmpegargs in /etc/mythtv/mythexport/mythexport_settings.cfg

---

### Post by Clochard on 2009-10-15
This is quite the epic thread, and I hope I'm not posting something that is already solved ...

I've tried setting mythexport up, but it seems to be getting hung up because it can't delete a file that doesn't exist.

Any help is appreciated.  I've read that my config name cannot have a space, which it does not (see config file below).  I'm going to try without a number just for kicks.

```
October 14 22:49:06 freedom /usr/bin/mythexport-daemon[14393]: query = select id, type, param from mythexport_job_queue order by id at line 607 in /usr/bin/mythexport-daemon
October 14 22:49:06 freedom /usr/bin/mythexport-daemon[14393]: exportdir = /srv/exports at line 396 in /usr/bin/mythexport-daemon
October 14 22:49:06 freedom /usr/bin/mythexport-daemon[14393]: starttime = 20091013050000 at line 397 in /usr/bin/mythexport-daemon
October 14 22:49:06 freedom /usr/bin/mythexport-daemon[14393]: chanid = 1057 at line 398 in /usr/bin/mythexport-daemon
October 14 22:49:06 freedom /usr/bin/mythexport-daemon[14393]: config = Archos at line 399 in /usr/bin/mythexport-daemon
October 14 22:49:06 freedom /usr/bin/mythexport-daemon[14393]: query = SELECT rec.title, rec.subtitle, rec.description, pg.syndicatedepisodenumber, pg.showtype, rec.programid, rec.basename, rec.starttime
    FROM recorded rec LEFT JOIN program pg ON pg.starttime = rec.starttime AND pg.chanid = rec.chanid
    WHERE rec.chanid=? AND rec.starttime=? at line 413 in /usr/bin/mythexport-daemon
October 14 22:49:06 freedom /usr/bin/mythexport-daemon[14393]: Going into new mode
 at line 430 in /usr/bin/mythexport-daemon
October 14 22:49:06 freedom /usr/bin/mythexport-daemon[14393]: query = SELECT callsign FROM channel WHERE chanid=? at line 438 in /usr/bin/mythexport-daemon
October 14 22:49:06 freedom /usr/bin/mythexport-daemon[14393]: command = AtomicParsley '/srv/exports/COMEDCP-MADtv-MAD_TV_Ruined_My_Life_The_Outrageous_Sketches.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork COMEDCP --TVShowName "MADtv" --TVEpisode "EP001547960474" --TVEpisodeNum 01 --TVSeason 13 --description "Talk-show host Jerry Springer and his studio audience examine controversial sketches, including "The Wizard of Oz: The Lost Footage" and a music video lampooning the church sex scandals." --title "MAD TV Ruined My Life: The Outrageous Sketches That Shocked a Nation" 2>&1 at line 554 in /usr/bin/mythexport-daemon
October 14 22:49:06 freedom /usr/bin/mythexport-daemon[14393]: ERROR: AtomicParsley '/srv/exports/COMEDCP-MADtv-MAD_TV_Ruined_My_Life_The_Outrageous_Sketches.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork COMEDCP --TVShowName "MADtv" --TVEpisode "EP001547960474" --TVEpisodeNum 01 --TVSeason 13 --description "Talk-show host Jerry Springer and his studio audience examine controversial sketches, including "The Wizard of Oz: The Lost Footage" and a music video lampooning the church sex scandals." --title "MAD TV Ruined My Life: The Outrageous Sketches That Shocked a Nation" 2>&1 FAILED at line 555 in /usr/bin/mythexport-daemon
rm: cannot remove `/srv/exports/COMEDCP-MADtv-MAD_TV_Ruined_My_Life_The_Outrageous_Sketches.mp4': No such file or directory
mv: cannot stat `/srv/exports/*temp*': No such file or directory
October 14 22:49:06 freedom /usr/bin/mythexport-daemon[14393]: ERROR: /srv/exports/COMEDCP-MADtv-MAD_TV_Ruined_My_Life_The_Outrageous_Sketches.mp4 is not available at line 563 in /usr/bin/mythexport-daemon
October 14 22:49:06 freedom /usr/bin/mythexport-daemon[14393]: query = INSERT into mythexport VALUES(NULL,?,?,?,?,NOW(),DATE_ADD(NOW(),INTERVAL ? DAY),?,?) at line 569 in /usr/bin/mythexport-daemon
October 14 22:49:06 freedom /usr/bin/mythexport-daemon[14393]: query = delete from mythexport_job_queue where id=? at line 636 in /usr/bin/mythexport-daemon
October 14 22:50:06 freedom /usr/bin/mythexport-daemon[14393]: query = select id, type, param from mythexport_job_queue order by id at line 607 in /usr/bin/mythexport-daemon
October 14 22:51:06 freedom /usr/bin/mythexport-daemon[14393]: query = select id, type, param from mythexport_job_queue order by id at line 607 in /usr/bin/mythexport-daemon
```

```
root@freedom:/etc/mythtv/mythexport# cat mythexport_settings.cfg 
; Config::Simple 4.59
; Wed Oct 14 22:29:36 2009

[Archos5]
removeCommercials=
extension=
codec=xvid
sizeY=576
sizeX=720
aspect=4:3
videoBR=1000
threads=1
device=archos
podcastName=
deletePeriod=
audioBR=128
ffmpegArgs=-y -acodec libmp3lame -ab 128 -vcodec libxvid -b 1000 -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -aspect 4:3 -s 720x576 -deinterlace -threads auto
audioChannels=
deinterlace=1
```


Update - Yup, that seems to have been the problem.  Renaming the config to characters only (no numbers) brought me to the ffmpeg errors, which are a new kettle of fish.

---

### Post by Clochard on 2009-10-15
This ffmpeg seems to be actually running - will report back once it is done.

Had to change the bitrates by adding '000' to audio and video bitrates, update the trellis flag, and remove the aic flag entirely (unable to determine what this will do).

```
nice -n19 ffmpeg -i /srv/recordings/1057_20091013050000.mpg -y -acodec libmp3lame -ab 128000 -vcodec libxvid -b 1000000 -mbd 2 -flags +4mv -trellis 1 -cmp 2 -subcmp 2 -aspect 4:3 -s 720x576 -deinterlace '/srv/exports/COMEDCP-MADtv-MAD_TV_Ruined_My_Life_The_Outrageous_Sketches.avi'
```

---

### Post by Clochard on 2009-10-16
I can confirm that the following ffmpegArgs line works for the [Archos 5]("http://www.archos.com/products/imt/archos_5/index.html?country=ca&lang=en") (no additional plugins needed).  This is the plain old Archos 5, not the Andriod one released last month.

```
ffmpegArgs=-y -acodec libmp3lame -ab 128000 -vcodec libxvid -b 1000000 -mbd 2 -flags +4mv -trellis 1 -cmp 2 -subcmp 2 -aspect 4:3 -s 720x576 -deinterlace
```

I can't speak to if it is optimized, or ideal, or anything.  But it works fine on the Archos using the "archos" profile as a basis for the configuration.

---

### Post by JerkyChew on 2009-10-29
So I'm back from the dead (aka page 5 or so) and I've tried installing mythexport on my new .22RC1 box. I ran the install and it asked for my MySQL username and password, which I always get wrong the first time. It appears that there's no credential checking, after the install it tries to modify the MySQL database and fails. I tried dpkg --configure mythexport but it tries again to access the MySQL database and bombs out.

I ran sudo apt-get remove mythexport and it uninstalled the program, but when I tried to reinstall I got the error message:

Setting up mythexport (2.01-0ubuntu1~ppa1) ...
ln: creating symbolic link `./video': File exists
dpkg: error processing mythexport (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mythexport
E: Sub-process /usr/bin/dpkg returned an error code (1)

I found that /var/lib/mythexport still existed and rm -rf'ed the directory, as well as /var/www/mythexport, but I can't find where the heck that video symlink exists so I can kill it.

Help?

---

### Post by johnelle on 2009-10-31
What is the current state of Mythexport 2?  Is anybody using it successfully?  I had to reconfigure myth (including export) due to a change in providers and so I am working with completely clean installs.  Only mods are to the LIRC config.  What I am finding:
[LIST=1]
[*]Installing from the main repository creates a version that works for the test config but then gets syntax errors if you change ANY of the fields.  Lots of entries about that issue.
[*]Installation from the testing repository gives me a version that dies with "Cannot Communicate with 127.0.0.1" even though all the config.xml files are correct and in the correct locations.
[*]Uninstall doesn't really work so you have to basically start at the Myth level each time.
[/LIST]
I would like to stop sinking time into debugging this.  Is the easiest workaround to use the "stable" version and fix the configs by hand?

---

### Post by rhpot1991 on 2009-11-06
> **JerkyChew said:**
> So I'm back from the dead (aka page 5 or so) and I've tried installing mythexport on my new .22RC1 box. I ran the install and it asked for my MySQL username and password, which I always get wrong the first time. It appears that there's no credential checking, after the install it tries to modify the MySQL database and fails. I tried dpkg --configure mythexport but it tries again to access the MySQL database and bombs out.

I ran sudo apt-get remove mythexport and it uninstalled the program, but when I tried to reinstall I got the error message:

Setting up mythexport (2.01-0ubuntu1~ppa1) ...
ln: creating symbolic link `./video': File exists
dpkg: error processing mythexport (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mythexport
E: Sub-process /usr/bin/dpkg returned an error code (1)

I found that /var/lib/mythexport still existed and rm -rf'ed the directory, as well as /var/www/mythexport, but I can't find where the heck that video symlink exists so I can kill it.

Help?

Glad to see you back, lets see where I can help out.  Check and see if the .video folder exists in your home directory, it should be empty, and kill it.  That is an old bug which should be fixed by now, not sure why you are seeing it.  After you clean that up run sudo dpkg-reconfigure mythexport and you should be able to re-enter your settings.  The installation package will attempt to read your mysql settings from /etc/mythtv/mysql.txt(if it exists), so make sure those are correct.

---

### Post by rhpot1991 on 2009-11-06
> **johnelle said:**
> What is the current state of Mythexport 2?  Is anybody using it successfully?  I had to reconfigure myth (including export) due to a change in providers and so I am working with completely clean installs.  Only mods are to the LIRC config.  What I am finding:
[LIST=1]
[*]Installing from the main repository creates a version that works for the test config but then gets syntax errors if you change ANY of the fields.  Lots of entries about that issue.
[*]Installation from the testing repository gives me a version that dies with "Cannot Communicate with 127.0.0.1" even though all the config.xml files are correct and in the correct locations.
[*]Uninstall doesn't really work so you have to basically start at the Myth level each time.
[/LIST]
I would like to stop sinking time into debugging this.  Is the easiest workaround to use the "stable" version and fix the configs by hand?

Maybe it would be more helpful if you posted your logs here, and stated some specific issues.  You should also provide the versions of ubuntu/mythtv/mythexport you are using.

---

### Post by johnelle on 2009-11-08
And normally I would have done that (and have done that in the past) but my logs were the same as many others in this thread so it didn't seem productive.  I am more than happy to help in any capacity whether it be as dedicated tester, code reviewer, whatever.  Just send me a note.  I really like the idea of Mythexport 2 but trying to get it working consistently is shall we say a little frustrating.

---

### Post by JerkyChew on 2009-11-08
> **rhpot1991 said:**
> Glad to see you back, lets see where I can help out.  Check and see if the .video folder exists in your home directory, it should be empty, and kill it.  That is an old bug which should be fixed by now, not sure why you are seeing it.  After you clean that up run sudo dpkg-reconfigure mythexport and you should be able to re-enter your settings.  The installation package will attempt to read your mysql settings from /etc/mythtv/mysql.txt(if it exists), so make sure those are correct.

I found the video folder in my home directory and killed it, but it wouldn't let me reconfigure Mythexport. t gave the following:


/usr/sbin/dpkg-reconfigure: mythexport is broken or not fully installed

So, I ran sudo apt-get remove mythexport which removed it, and then ran sudo apt-get install mythexport, but I received the following yet again:

Setting up mythexport (2.01-0ubuntu1~ppa1) ...
ln: creating symbolic link `./video': File exists
dpkg: error processing mythexport (--configure):
 subprocess post-installation script returned error exit status 1

...So there's still a rogue ./video folder somewhere that I can't seem to find?

---

### Post by rhpot1991 on 2009-11-09
> **JerkyChew said:**
> I found the video folder in my home directory and killed it, but it wouldn't let me reconfigure Mythexport. t gave the following:


/usr/sbin/dpkg-reconfigure: mythexport is broken or not fully installed

So, I ran sudo apt-get remove mythexport which removed it, and then ran sudo apt-get install mythexport, but I received the following yet again:

Setting up mythexport (2.01-0ubuntu1~ppa1) ...
ln: creating symbolic link `./video': File exists
dpkg: error processing mythexport (--configure):
 subprocess post-installation script returned error exit status 1

...So there's still a rogue ./video folder somewhere that I can't seem to find?

Check and see what exists here: /usr/share/mythtv/mythexport/
If there is a video folder or anything else go ahead and clean it up
Make sure you run the following as well, so it will re-prompt you for all the questions, you could have an empty directory causing this: sudo dpkg-reconfigure mythexport.

---

### Post by johnelle on 2009-11-11
For anybody looking to output a windows format I am having success with the following procedure.

**First,** rebuild encoders using **[HOWTO: Install and use the latest FFmpeg and x264]("http://ubuntuforums.org/showthread.php?t=786095")** which is probably a good thing regardless of your task.

**Second,** added a section to the /etc/mythtv/mythexport/mythexport_settings.cfg that looks something like:
```

[windooz]
removeCommercials=
codec=wmv2
extension=.wmv
sizeX=640
sizeY=480
aspect=4:3
videoBR=1200kb
device=zune
threads=
podcastName=
deletePeriod=5
audioBR=192kb
audioChannels=
ffmpegArgs=-y -s 640x480 -b 1200kb -vcodec wmv2 -acodec wmav2 -ar 44100 -ab 192kb -ac 2 -aspect 4:3
deinterlace=

```
This produces a fairly large format but you can tweak it pretty easily (remembering from the doc. that from this point on you need to edit the config with the text editor or it gets reset).

I am going to experiment vbr encoding next to see how that works.

---

### Post by mcarse on 2009-11-11
I am getting an error error with mythexport after upgrading to 9.10.

> Setting up mythexport (2.1.3-0ubuntu1) ...
ERROR 2005 (HY000): Unknown MySQL server host '-umythtv' (1)
dpkg: error processing mythexport (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mythexport
E: Sub-process /usr/bin/dpkg returned an error code (1)
Does anyone know how to fix this?

---

### Post by alexyz on 2009-11-11
Install fails - searched this thread and I don't see this error anywhere.

```
Processing triggers for sreadahead ...
Setting up mythexport (2.1.3-0ubuntu1) ...
ERROR 1307 (HY000) at line 8: Failed to CREATE PROCEDURE addcol
dpkg: error processing mythexport (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mythexport
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any suggestions?  This happens after I get prompted for mythexport directory.  I don't see any other prompts.  My /etc/mythtv/mysql.txt file is OK.  After dpkg --purge I still see two tables:  mythexport and mythexport_job_queue .  Drop those and reinstall, same error.

OK, I looked inside the .deb file.  It fails when it tries to execute the following (rather bizarre) bit of SQL:

```
DROP PROCEDURE IF EXISTS addcol;

delimiter '//'
CREATE PROCEDURE addcol() BEGIN
	IF NOT EXISTS(
		SELECT * FROM information_schema.COLUMNS
		WHERE COLUMN_NAME='podcastName' AND TABLE_NAME='mythexport'
	)
	THEN
		ALTER IGNORE TABLE mythexport ADD podcastName varchar(25) default NULL;
	END IF;
END;
//
delimiter ';'
CALL addcol();
DROP PROCEDURE addcol;
```

The point here seems to be to add the podcastName column only if it doesn't exist?  Perhaps this has to do with upgrading vs. a new install.  However if I add the column manually and re-run the install, same error.  Next step:  I'll hack the .deb to remove this SQL (the tables already exist) and try re-installing, but I don't have time to do that now.  Any suggestions would be much appreciated.

---

### Post by rhpot1991 on 2009-11-11
> **mcarse said:**
> I am getting an error error with mythexport after upgrading to 9.10.

Does anyone know how to fix this?

Verify your information in /etc/mythtv/mysql.txt is correct, if it isn't then MythExport will fail when it attempts to use it.

---

### Post by rhpot1991 on 2009-11-11
> **alexyz said:**
> Install fails - searched this thread and I don't see this error anywhere.

```
Processing triggers for sreadahead ...
Setting up mythexport (2.1.3-0ubuntu1) ...
ERROR 1307 (HY000) at line 8: Failed to CREATE PROCEDURE addcol
dpkg: error processing mythexport (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mythexport
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any suggestions?  This happens after I get prompted for mythexport directory.  I don't see any other prompts.  My /etc/mythtv/mysql.txt file is OK.  After dpkg --purge I still see two tables:  mythexport and mythexport_job_queue .  Drop those and reinstall, same error.

OK, I looked inside the .deb file.  It fails when it tries to execute the following (rather bizarre) bit of SQL:

```
DROP PROCEDURE IF EXISTS addcol;

delimiter '//'
CREATE PROCEDURE addcol() BEGIN
	IF NOT EXISTS(
		SELECT * FROM information_schema.COLUMNS
		WHERE COLUMN_NAME='podcastName' AND TABLE_NAME='mythexport'
	)
	THEN
		ALTER IGNORE TABLE mythexport ADD podcastName varchar(25) default NULL;
	END IF;
END;
//
delimiter ';'
CALL addcol();
DROP PROCEDURE addcol;
```

The point here seems to be to add the podcastName column only if it doesn't exist?  Perhaps this has to do with upgrading vs. a new install.  However if I add the column manually and re-run the install, same error.  Next step:  I'll hack the .deb to remove this SQL (the tables already exist) and try re-installing, but I don't have time to do that now.  Any suggestions would be much appreciated.

Thats is there to handle some upgrade situations, it adds the column if it doesn't exist.

It sounds like maybe the procedure already exists, so you could try dropping it by hand, get the user/password information from /etc/mythtv/mysql.txt:
mysql -uroot -p mythconverg
then
DROP PROCEDURE addcol;
then
exit; or quit; (I forget which one)

After that do a sudo dpkg-reconfigure mythexport, and hopefully all goes well.

---

### Post by alexyz on 2009-11-11
rhpot1991, thanks but that didn't work.  Actually the SQL already does drop the procedure before creating it, and I double-checked and the procedure does not exist.

However, I hacked the .deb and just removed the SQL and it installed cleanly. :)  Haven't tried it out yet but I see the web UI so at least the basics are working.

Very strange I would get this error if nobody else has.  Maybe something to do with my mysql configuration?  I've been running mythbuntu about two years and upgraded to 9.10 two weeks ago.  IIRC the mysql instance was created by the mythbuntu install, but I may have done it separately myself.  

Also, after thinking about it I understand why you're creating a procedure - in order to do the conditional logic.  Sorry I said your SQL was bizarre! :redface:  There might be a better way to do that, I'll have to think about it. 

> **rhpot1991 said:**
> It sounds like maybe the procedure already exists, so you could try dropping it by hand...

---

### Post by alexyz on 2009-11-11
Another problem.  I don't have the config file /etc/mythtv/mythexport/mythexport_settings.cfg

Maybe someone can post the default version?

Could it be these problems are because I'm doing a first-time install instead of upgrading an older version?  I don't see this file in the .deb, and the postinst script seems to assume that it exists.

---

### Post by rhpot1991 on 2009-11-11
> **alexyz said:**
> rhpot1991, thanks but that didn't work.  Actually the SQL already does drop the procedure before creating it, and I double-checked and the procedure does not exist.

However, I hacked the .deb and just removed the SQL and it installed cleanly. :)  Haven't tried it out yet but I see the web UI so at least the basics are working.

Very strange I would get this error if nobody else has.  Maybe something to do with my mysql configuration?  I've been running mythbuntu about two years and upgraded to 9.10 two weeks ago.  IIRC the mysql instance was created by the mythbuntu install, but I may have done it separately myself.  

Also, after thinking about it I understand why you're creating a procedure - in order to do the conditional logic.  Sorry I said your SQL was bizarre! :redface:  There might be a better way to do that, I'll have to think about it.

Yep, I forgot I put the drop in before hand, and apparently can't read :)

At this point I'd venture it might be a permission issue within MySQL.  Early on in Karmic development there was a MySQL configuration issue which caused the stored procedure to fail to execute, so this portion has gone through quite a bit of testing and shouldn't have any issues.

I am assuming that your system is up to date at this point?  I'll do a test on my dev box and make sure that any recent MySQL updates haven't broken anything.

---

### Post by alexyz on 2009-11-11
edit:  never mind, I found some example config files.  

> **rhpot1991 said:**
> I am assuming that your system is up to date at this point?

I'm up-to-date but have the config issue described in the above post (sounds like you might not have seen that).

Again, this is the first time I'm installing mythexport so that may have something to do with it.

Another thing that occurs to me is that the mysql instance has been around a while.  It's gone through at least 2, possibly 3, new distro release upgrades.  So I wouldn't be surprised if there were some small differences from a new fresh install.  If you'd like me to check permissions or anything, let me know.  No need for detailed instructions.

---

### Post by moaxey on 2009-12-01
I'm having some issues, mostly related to failure of the ffmpeg steps. I have a newer version of ffmpeg -- although it seems to be out of the main ubuntu-maintained karmic repository.

It requires manual changes to the /etc/mythtv/mythexport/mythexport_settings.cfg command line for h264 ipod encoding as detailed in this post: 
<http://slated.org/howto_transcode_h264_for_ipod_with_ffmpeg>

... now on to working out how to make ffmpeg be able to open the recordings that have been transcoded to mpeg4 nuv files... 




FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1

---

### Post by rhpot1991 on 2009-12-16
I have a ffmpeg update for everyone:

It looks like Medibuntu has released an update to libavcodec-extra-52 which gives us libfaac support again.  The MythExport web interface will default your ffmpeg settings to use MP3, if you update to the Medibuntu package and want to use AAC it should be as simple as removing the libmp3lame from your configuration and replacing it with libfaac.

Hopefully this will help with some of the ipod/itunes issues with files resulting from Karmic.

---

### Post by lingenfr on 2009-12-21
Whenever I try to change the default export directory (or leave it at the default), I get the following error:
-----
Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.
Apache/2.2.12 (Ubuntu) Server at 192.168.1.110 Port 80
------

If I try to change it on the userjob line in mythweb using the exportdir switch, it doesn't work. I am running an up-to-date version of Mythbuntu Karmic. From looking at the daemon code, it appears I have mythexport 2.0. I have not enabled the testing PPA and don't really want to as this is my only backend. Thanks for any assistance.

---

### Post by rhpot1991 on 2009-12-21
> **lingenfr said:**
> Whenever I try to change the default export directory (or leave it at the default), I get the following error:
-----
Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.
Apache/2.2.12 (Ubuntu) Server at 192.168.1.110 Port 80
------

If I try to change it on the userjob line in mythweb using the exportdir switch, it doesn't work. I am running an up-to-date version of Mythbuntu Karmic. From looking at the daemon code, it appears I have mythexport 2.0. I have not enabled the testing PPA and don't really want to as this is my only backend. Thanks for any assistance.

Check your /var/log/apache2/error.log for hints.

---

### Post by lingenfr on 2009-12-21
Here is what it says:

[Sun Dec 20 21:41:24 2009] [error] [client 192.168.1.104] '/etc/mythtv/mythexport/mythexport.cfg' couldn't be opened for writ
ing: Permission denied at /var/www/mythexport/save_system_setup.cgi line 30., referer: [http://192.168.1.110/mythexport/system](http://192.168.1.110/mythexport/system)
_setup.cgi

Here is the output of ls -l

-rwxr-xr-x 1 root root 1126 2009-10-26 01:35 save_system_setup.cgi

Thanks.

---

### Post by rhpot1991 on 2009-12-21
> **lingenfr said:**
> Here is what it says:

[Sun Dec 20 21:41:24 2009] [error] [client 192.168.1.104] '/etc/mythtv/mythexport/mythexport.cfg' couldn't be opened for writ
ing: Permission denied at /var/www/mythexport/save_system_setup.cgi line 30., referer: [http://192.168.1.110/mythexport/system](http://192.168.1.110/mythexport/system)
_setup.cgi

Here is the output of ls -l

-rwxr-xr-x 1 root root 1126 2009-10-26 01:35 save_system_setup.cgi

Thanks.

They should be:
```

-rw-r--r-- 1 www-data www-data   20 2009-12-21 16:21 mythexport.cfg
-rw-r--r-- 1 www-data www-data  373 2009-10-22 00:17 mythexport_settings.cfg

```

So chown www-data:www-data and chmod 644 them (as sudo).

---

### Post by lingenfr on 2009-12-23
That took care of it. Not sure what went wrong with my install or where I missed that instruction.

---

### Post by Calash on 2010-01-03
> **johnelle said:**
> For anybody looking to output a windows format I am having success with the following procedure.

**First,** rebuild encoders using **[HOWTO: Install and use the latest FFmpeg and x264]("http://ubuntuforums.org/showthread.php?t=786095")** which is probably a good thing regardless of your task.

**Second,** added a section to the /etc/mythtv/mythexport/mythexport_settings.cfg that looks something like:
```

[windooz]
removeCommercials=
codec=wmv2
extension=.wmv
sizeX=640
sizeY=480
aspect=4:3
videoBR=1200kb
device=zune
threads=
podcastName=
deletePeriod=5
audioBR=192kb
audioChannels=
ffmpegArgs=-y -s 640x480 -b 1200kb -vcodec wmv2 -acodec wmav2 -ar 44100 -ab 192kb -ac 2 -aspect 4:3
deinterlace=

```
This produces a fairly large format but you can tweak it pretty easily (remembering from the doc. that from this point on you need to edit the config with the text editor or it gets reset).

I am going to experiment vbr encoding next to see how that works.



I am having difficulty getting this to work right.  I can get it to encode it correctly, and while it is encoding the file is readable on both my Ubuntu system and the Windows systems fine.


The problem is that when it finishes, it deletes the file.  The file was good up to the end, and then...Poof....gone.


Here is my export log

```

January  3 21:06:43 linuxserv /usr/bin/mythexport-daemon[1842]: Exporting /storage/TV-Export/TOON-Robot_Chicken-Nightmare_Generator-20091015235900.wmv
January  3 21:38:21 linuxserv /usr/bin/mythexport-daemon[1842]: ERROR: AtomicParsley '/storage/TV-Export/TOON-Robot_Chicken-Nightmare_Generator-20091015235900.wmv' --genre "TV Shows" --stik "TV Show" --TVNetwork TOON --TVShowName "Robot Chicken" --TVEpisode "EP007259620019" --TVEpisodeNum  --TVSeason  --description ""Alien vs. Predator First Date"; scandal at the North Pole; "The A-Team."" --title "Nightmare Generator" 2>&1 FAILED at line 507 in /usr/bin/mythexport-daemon
mv: cannot move `/storage/TV-Export/*temp*' to `/storage/TV-Export/TOON-Robot_Chicken-Nightmare_Generator-20091015235900.wmv': No such file or directory
January  3 21:38:22 linuxserv /usr/bin/mythexport-daemon[1842]: ERROR: /storage/TV-Export/TOON-Robot_Chicken-Nightmare_Generator-20091015235900.wmv is not available at line 514 in /usr/bin/mythexport-daemon

```

Encoding to one of the other formats does not delete the file, but then it is not easily readable on Windows systems.  My end goal is to have the files exported so the Windows systems can read them.  Don't really care the format, but it would have to be WindowsMedia compatable.

---

### Post by rhpot1991 on 2010-01-04
> **Calash said:**
> I am having difficulty getting this to work right.  I can get it to encode it correctly, and while it is encoding the file is readable on both my Ubuntu system and the Windows systems fine.


The problem is that when it finishes, it deletes the file.  The file was good up to the end, and then...Poof....gone.


Here is my export log

```

January  3 21:06:43 linuxserv /usr/bin/mythexport-daemon[1842]: Exporting /storage/TV-Export/TOON-Robot_Chicken-Nightmare_Generator-20091015235900.wmv
January  3 21:38:21 linuxserv /usr/bin/mythexport-daemon[1842]: ERROR: AtomicParsley '/storage/TV-Export/TOON-Robot_Chicken-Nightmare_Generator-20091015235900.wmv' --genre "TV Shows" --stik "TV Show" --TVNetwork TOON --TVShowName "Robot Chicken" --TVEpisode "EP007259620019" --TVEpisodeNum  --TVSeason  --description ""Alien vs. Predator First Date"; scandal at the North Pole; "The A-Team."" --title "Nightmare Generator" 2>&1 FAILED at line 507 in /usr/bin/mythexport-daemon
mv: cannot move `/storage/TV-Export/*temp*' to `/storage/TV-Export/TOON-Robot_Chicken-Nightmare_Generator-20091015235900.wmv': No such file or directory
January  3 21:38:22 linuxserv /usr/bin/mythexport-daemon[1842]: ERROR: /storage/TV-Export/TOON-Robot_Chicken-Nightmare_Generator-20091015235900.wmv is not available at line 514 in /usr/bin/mythexport-daemon

```

Encoding to one of the other formats does not delete the file, but then it is not easily readable on Windows systems.  My end goal is to have the files exported so the Windows systems can read them.  Don't really care the format, but it would have to be WindowsMedia compatable.

The issue here is that you don't want atomic parsley running against this file, odds are it is unhappy with wmv.  I have some exceptions in place to avoid running it on .avi files, so try to use that extension instead.  Let me know if this works or not, I can add an exception for .wmv and push it to the testing PPA at a later point.

---

### Post by Calash on 2010-01-05
> **rhpot1991 said:**
> The issue here is that you don't want atomic parsley running against this file, odds are it is unhappy with wmv.  I have some exceptions in place to avoid running it on .avi files, so try to use that extension instead.  Let me know if this works or not, I can add an exception for .wmv and push it to the testing PPA at a later point.

Worked perfectly.  Thank you so much for the help :)


For anybody curious about my setup:

I have a 1tb Western Digital Wold Book Edition NAS that is mounted on my MythBuntu box.  I am exporting the TV shows into a windows format onto it's drive so that the built-in media server (TWONKY) will share it out to all the windows systems in the house.

---

### Post by jaserb on 2010-01-16
I've run across an issue getting Mythexport running in Mythbuntu Karmic; seems like this thread is pretty active on Mythexport issues but if I should post elsewhere let me know.

The export is failing due to the fact that there is no complete path to my recordings; here is a sample debug output:
[FONT=Courier New]
January 15 21:45:24 mythbox /usr/bin/mythexport-daemon[17309]: command[/FONT][FONT=Courier New] = nice -n19 ffmpeg -i /1058_20100115200000.mpg -y -acodec libmp3lame[/FONT][FONT=Courier New] -ab 192kb -vcodec mpeg4 -b 600kb -mbd 2 -flags +4mv+aic -trellis 2 -cmp 2 -subcmp 2 -s 360x480 -aspect 4:3[/FONT][FONT=Courier New] '/var/lib/mythtv/mythexport/[/FONT][FONT=Courier New]COMEDYP-The_Daily_Show_With_[/FONT][FONT=Courier New]Jon_Stewart-Tom_Brokaw-20100115.mp4' 2>&1 at line 491 in /usr/bin/mythexport-daemon[/FONT]
[FONT=Courier New]
[/FONT] Around line 400 in mythexport-daemon it's trying to get the recording path from the RecordFilePrefix directory in older Myth versions (schemaVer < 1171) and from the Storage Groups config otherwise. I think the problem may be that I'm using MythTV 0.22 without storage groups. I got it working by adding some code to fall back to the RecordFileDir setting if it can't get the path from the Storage Groups but it seems like there should be a more elegant way, since RecordFileDir isn't set by default in 0.22. Has anyone else run into this? Is there a fix?


Thanks,
Jason

---

### Post by 4dognight on 2010-01-16
I have seen it.
Do you have more than 1 myth server?
In my case if it gets scheduled on a different server than where the recording resides it cant find the file because it doesnt have the dir available locally.

---

### Post by jaserb on 2010-01-16
> **4dognight said:**
> I have seen it.
Do you have more than 1 myth server?
In my case if it gets scheduled on a different server than where the recording resides it cant find the file because it doesnt have the dir available locally.

Nope. I've got a fairly buff homebuilt frontend / backend downstairs where all the recordings are stored, and two lightweight frontend only systems upstairs - an Averatec all-in-one and a Dell Zino. Both store nothing locally, they get all their recordings off the main box over 802.11n. 

Like I said, I've gotten a workaround going, it would just be nice if the call to the Storage Groups setting would return /var/lib/mythtv/recordings or whatever even if Storage Groups are not in use.

-Jason

---

### Post by 4dognight on 2010-01-17
the only other thing i can think of is, if you dont have a dir defined in the default group.

---

### Post by smckay79 on 2010-01-20
Does anyone have a working config for iphone exports... my current one is

[iPhone]
removeCommercials=
extension=
codec=mpeg4
sizeY=272
sizeX=480
aspect=16:9
videoBR=300000
threads=
device=ipod
podcastName=MythTV
deletePeriod=
audioBR=128000
ffmpegArgs=-y -acodec libmp3lame -ab 128kb -ar 44100  -vcodec mpeg4 -b 500kb -mbd 2 -flags +4mv+aic -trellis 2 -cmp 2 -subcmp 2 -s 480x320 -ac 2 -aspect 16:9
audioChannels=2
deinterlace=1

which results in video when streaming on my iPhone, however no audio.. sorry im new to this and don't quite understand ffmpeg parameters.

Thanks

---

### Post by Nausser on 2010-02-26
I'm running Mythbuntu 9.10 and so far am getting to enjoy it. I'm running a rather beefy system so I haven't experienced any problems with performance.

Questions for MythExport though...

In the MythExport web page, I have setup several different devices, all with diferent settings from the default ipod(which I don't have) to a droid and even laptop setting. Everything seems to "think" it is working fine. I have experienced no errors from the MythExport web page or the Myth web page. When I add a device such as ipod, droid or laptop, I can see them as an option in Mythweb. When I click on one of them it says that the job is queued. After a minute of refreshing the web page is then states "job completed successfully". First, there is no way the computer could convert an HD hour show in less than one minute. Secondly, I look high and low for any sort of exported file in every Myth related directory and nothing.

When I do an "On the Go", I see the job show up under MythExport, however, that is where it stays.

I've double check that my export directories or chmod and chowned properly which they are. I can't figure out why it would say the job is completed successfully. 

I hope someone else has some answers. I'm often away when my shows are on and would really like to stay up to speed.

Let me know if you would like specific info!

Thanks!

---

### Post by ktmom on 2010-03-01
edit /etc/init.d/mythexport and add "debug" to the ARGS variable then try running an export job and then could you post your /var/log/mythtv/mythexport.log file.

Any errors causing a fail will show up in the log file.

---

### Post by Illydth on 2010-04-25
Regarding the Nov. 11, 2009 Post Regarding Alexyz problem with package installation, I have a permanent and final solution to this issue.

The problem comes in with the MYSQL UPGRADE to version 5.1.37.  The likely cause of the problem stems back to a failure somewhere in this upgrade process that leaves your mythconverg tables and MySQL installation out of whack.

The error above (according to the MySQL Lists) is a Generic MySQL error (Error 1307).  It's what Doctors call "ADR" (Ain't Doing Right).  The reported error:  That it cannot create the procedure, IS in fact correct.

MySQL CANNOT create the procedue.  If you try to do this manually it will ALSO error out on you telling you that it cannot create the procedure.

The fix to the root cause (and potentially the fix to several OTHER root causes due to MYSQL inconsistancy) is to FIX the MYSQL tables.  

First and foremost (YMMV) I found that I had a leftover #MYSQL50#-mythconverge database (something like that) which was a backup that dpkg/apt did when it upgraded from 5.0 to 5.1.  This database was entirely borked and I simply removed it entirely through phpMyAdmin.

Next, I dropped out of phpMyAdmin and ran:

*sudo mysql_upgrade -u root -p*

Typing in the mysql admin (root) password.  This processed all of the remaining tables and updated / upgraded the mysql database to the most recent format. 

After doing this, I was able to go into mysql directly and hand-type the procedure rhpot1991 mentioned was being inserted by the dpkg update.

Once the package was successfully able to be created, I went back out and re-configured the mythexport pacakge and this time it went through successfully...fully installed.

On a further note: possibly due to the dpkg installation failure on my system I found that the mythexport website's configuration file had NOT gotten linked in with Apache, so when I went to the setup file all I got was a CGI listing and when I went to the mythexport directory all I got was a directory listing.

The fix here was to go into /etc/apache2/sites-enabled and link the mythexport.conf file to it with:

*ln -s ../sites-available/mythexport.conf mythexport.conf*

Restarted apache and mythexport is booting like a champ now.

--Illydth

---

### Post by Illydth on 2010-04-25
Sorry to cross post here, but since this is specific to the MythExport app while the MythTV mailing list is a bit less so, I thought I'd see about getting an answer here as well.

I'm trying to transcode a recording to test.  The full output of the ffmpeg run is below...the end result is it's blowing up during the export pretty much immediately with "Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height"

Also tried with -ab 192kb instead of -ab 448kb to the same problem.

On a second note, I'm using libmp3lame for the Audio Codec, according to the mythexport wiki site, the most recent version of libavcodec-extra-52 was SUPPOSED to have given us back libaac encoding, but when I try to use "libfaac" in place of libmp3lame, ffmpeg comes back complaining that it's an invalid codec.

Any help would be appreciated.

--Illydth

douglasw@ghost:~$ ffmpeg -i /video/1021_20100419200000.mpg -y -acodec libmp3lame -ab 448kb -vcodec mpeg4 -b 600kb -mbd 2 -flags +mv4+aic -trellis 2 -cmp 2 -subcmp 2 -s 480x320 -aspect 16:9 '/mnt/varchive/ipodfeed/KTVI-DT-24-Day_8_9_00AM_10_00AM-20100419200000.mp4'
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr  8 2010 20:05:15, gcc: 4.4.1

Seems stream 0 codec frame rate differs from container frame rate: 119.88 (120000/1001) -> 59.94 (60000/1001)
Input #0, mpegts, from '/video/1021_20100419200000.mpg':
  Duration: 00:59:56.56, start: 8750.110567, bitrate: 14678 kb/s
  Program 1
    Stream #0.0[0x31]: Video: mpeg2video, yuv420p, 1280x720 [PAR 1:1 DAR 16:9], 19000 kb/s, 59.94 tbr, 90k tbn, 119.88 tbc
    Stream #0.1[0x34](eng): Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
Output #0, mp4, to '/mnt/varchive/ipodfeed/KTVI-DT-24-Day_8_9_00AM_10_00AM-20100419200000.mp4':
    Stream #0.0: Video: mpeg4 (hq), yuv420p, 480x320 [PAR 32:27 DAR 16:9], q=2-31, 600 kb/s, 90k tbn, 59.94 tbc
    Stream #0.1(eng): Audio: libmp3lame, 48000 Hz, 5.1, s16, 448 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

douglasw@ghost:~$ ffmpeg -version
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr  8 2010 20:05:15, gcc: 4.4.1
FFmpeg SVN-r19352-4:0.5+svn20090706-2ubuntu2.1
libavutil     49.15. 0 / 49.15. 0
libavcodec    52.20. 0 / 52.20. 0
libavformat   52.31. 0 / 52.31. 0
libavdevice   52. 1. 0 / 52. 1. 0
libavfilter    0. 4. 0 /  0. 4. 0
libswscale     0. 7. 1 /  0. 7. 1
libpostproc   51. 2. 0 / 51. 2. 0

---

### Post by GuiGuy on 2010-04-25
Cancelled post.

---

### Post by rhpot1991 on 2010-04-26
> **Illydth said:**
> Sorry to cross post here, but since this is specific to the MythExport app while the MythTV mailing list is a bit less so, I thought I'd see about getting an answer here as well.

I'm trying to transcode a recording to test.  The full output of the ffmpeg run is below...the end result is it's blowing up during the export pretty much immediately with "Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height"

Also tried with -ab 192kb instead of -ab 448kb to the same problem.

On a second note, I'm using libmp3lame for the Audio Codec, according to the mythexport wiki site, the most recent version of libavcodec-extra-52 was SUPPOSED to have given us back libaac encoding, but when I try to use "libfaac" in place of libmp3lame, ffmpeg comes back complaining that it's an invalid codec.

Any help would be appreciated.

--Illydth

douglasw@ghost:~$ ffmpeg -i /video/1021_20100419200000.mpg -y -acodec libmp3lame -ab 448kb -vcodec mpeg4 -b 600kb -mbd 2 -flags +mv4+aic -trellis 2 -cmp 2 -subcmp 2 -s 480x320 -aspect 16:9 '/mnt/varchive/ipodfeed/KTVI-DT-24-Day_8_9_00AM_10_00AM-20100419200000.mp4'
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr  8 2010 20:05:15, gcc: 4.4.1

Seems stream 0 codec frame rate differs from container frame rate: 119.88 (120000/1001) -> 59.94 (60000/1001)
Input #0, mpegts, from '/video/1021_20100419200000.mpg':
  Duration: 00:59:56.56, start: 8750.110567, bitrate: 14678 kb/s
  Program 1
    Stream #0.0[0x31]: Video: mpeg2video, yuv420p, 1280x720 [PAR 1:1 DAR 16:9], 19000 kb/s, 59.94 tbr, 90k tbn, 119.88 tbc
    Stream #0.1[0x34](eng): Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
Output #0, mp4, to '/mnt/varchive/ipodfeed/KTVI-DT-24-Day_8_9_00AM_10_00AM-20100419200000.mp4':
    Stream #0.0: Video: mpeg4 (hq), yuv420p, 480x320 [PAR 32:27 DAR 16:9], q=2-31, 600 kb/s, 90k tbn, 59.94 tbc
    Stream #0.1(eng): Audio: libmp3lame, 48000 Hz, 5.1, s16, 448 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

douglasw@ghost:~$ ffmpeg -version
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr  8 2010 20:05:15, gcc: 4.4.1
FFmpeg SVN-r19352-4:0.5+svn20090706-2ubuntu2.1
libavutil     49.15. 0 / 49.15. 0
libavcodec    52.20. 0 / 52.20. 0
libavformat   52.31. 0 / 52.31. 0
libavdevice   52. 1. 0 / 52. 1. 0
libavfilter    0. 4. 0 /  0. 4. 0
libswscale     0. 7. 1 /  0. 7. 1
libpostproc   51. 2. 0 / 51. 2. 0

You need medibuntu's libavcodec-extra-52 installed ([https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)).

As far as your "Error while opening codec for output stream #0.1" error, try adding "-ac 2" to your ffmpeg line.  This will limit the audio channels to 2, mp3s don't like any more than that. and odds are your device is only stereo at best.

---

### Post by radmofo on 2010-08-09
About 1/2 of all files are fine but some end up complete (yet play fine) but show as a dead link in any rss reader. The "spongebob" listed in the log below is an example. The file as it is in its complete form in the server folder is actually...

NIK-SpongeBob_SquarePants--20100809193000-temp-87689.mp4

any Idea whats causing the additional "-temp-87689" to be added and not taken away?


[PHP]August  9 20:26:43 robbins-mythserver /usr/bin/mythexport-daemon[6414]: Exporting /home/mythserver/storage/ipod/NIK-SpongeBob_SquarePants--20100809193000.mp4
mv: target `/home/mythserver/storage/ipod/NIK-SpongeBob_SquarePants--20100809193000.mp4' is not a directory
August  9 20:34:35 robbins-mythserver /usr/bin/mythexport-daemon[6414]: ERROR: /home/mythserver/storage/ipod/NIK-SpongeBob_SquarePants--20100809193000.mp4 is not available at line 563 in /usr/bin/mythexport-daemon
August  9 20:41:35 robbins-mythserver /usr/bin/mythexport-daemon[6414]: Exporting /home/mythserver/storage/ipod/TVLAND-The_Nanny-The_Boca_Story-20100809200000.mp4
[/PHP]

---

### Post by tsh on 2010-08-16
I just tried installing mythexport, and my best explanation of how it functions is 'garbage'

To start with, it fails to copy the mpg files, because $exportdir is empty.
I can't track down why, but if i force this in the perl to be valid (and it is correct in the config file), then it seems not to pick up any ffmpeg commands. I am also failing to understand that the different modes are supposed to be - the wili page linked to in the help also appears to be in some sort of un-proofred 'brain dump' state.

any clues as to what is really going on?

---

### Post by rhpot1991 on 2010-08-16
> **tsh said:**
> I just tried installing mythexport, and my best explanation of how it functions is 'garbage'

To start with, it fails to copy the mpg files, because $exportdir is empty.
I can't track down why, but if i force this in the perl to be valid (and it is correct in the config file), then it seems not to pick up any ffmpeg commands. I am also failing to understand that the different modes are supposed to be - the wili page linked to in the help also appears to be in some sort of un-proofred 'brain dump' state.

any clues as to what is really going on?

I think you need to start with a lesson in manners.  No one is forcing you to use any software, if you don't like it I'll even give you a refund, oh wait...  Of course there are some issues and a lot of things I would like to improve, but I do what I can with the time that I have.  If you want to help out I'd more than welcome the help.  As a general rule in life: the nicer you are to people, the more they will want to help you.
</rant>

Anyways, onto the helping part.  A good place to start is to list what version you are using.

The export directory comes from /etc/mythtv/mythexport/mythexport.cfg which may also be set from the web interface.  It should look something like:
```
dir=/var/lib/mythtv
```

If you have that setup correctly and it is not working then open up a bug and include your config files, I will then look into it.  It may also be helpful to eliminate any special characters or spaces to see if they are causing an issue.  

As far as the ffmpeg lines, if you enable debugging it should tell you more information in the logs.  You can also post your configs in here, and once again watch out for spaces or special characters (there is a bug open about this, it is caused by the Perl module I am using for the configs).

What question do you have about different modes?

---

### Post by tsh on 2010-08-17
Well, after spending several hours trying to get something working when the previous version I used worked fine (even if it was only command line) I do often wonder if the effort I put into using Myth is worthwhile.

> **rhpot1991 said:**
> 
The export directory comes from /etc/mythtv/mythexport/mythexport.cfg which may also be set from the web interface.  It should look something like:
```
dir=/var/lib/mythtv
```

If you have that setup correctly and it is not working then open up a bug and include your config files, I will then look into it.  It may also be helpful to eliminate any special characters or spaces to see if they are causing an issue.  

I have 
```
dir=/home/mythtv
```
and it does seem to be picked up some of the time because I got something to work(although it is possible that I still left in my override code).

> **rhpot1991 said:**
> 

As far as the ffmpeg lines, if you enable debugging it should tell you more information in the logs.  You can also post your configs in here, and once again watch out for spaces or special characters (there is a bug open about this, it is caused by the Perl module I am using for the configs).

What question do you have about different modes?

So this is all related, and because I don't understand the usage modes, I can't sensibly debug much.

I was misled by the mythexport web interface offering my a list of recorded programs to take 'on the go'. I though that this meant 'export these so I can take them on my portable device', but, seemingly not. For me, that feature is still a mystery, and does not work because of trying to write in the root directory.

After realising that I have to set up a user job, and then manually run that user job on each recording from myth/mythweb (no way to select a series?) I am able to transcode, but cut lists still fail (because they seem to want to write a copy of the file)

When I was getting ffmpeg failed messages, the lists of commands were empty (and I am doing nothing special, just using one of the built-in templates).

Are any directories stored in the job list? I don't have any time to debug this for 2 weeks, but I think maybe some sanity checking of the configuration might not go amiss. (and a clearer guide of the workflow)

---

### Post by rhpot1991 on 2010-08-17
1. I wouldn't use /home/mythtv, in general using home directories with MythTV is asking for permission issues.

2. The OTG functionality was meant for situations where you have a backend in a RV/boat/car, and wanted to take recordings from your backend in your house on the go.  The lightweight OTG option is meant to run on a laptop, using a web browser to display the XML.  The functionality here is minimal, it was more or less a proof of concept and I haven't had much feedback on it.

3. Workflow.  Since we are in Myth here, there are several ways to accomplish just about every task, but here is what I would recommend.  Start in MythExport's web interface, setup a configuration, then setup a user job to use that configuration.  Now schedule a new recording, or edit an existing one, and enable the user job you just created on that recording schedule.  Now every time that recording schedule finishes MythExport will run against it.  In the mean time you may fire off your userjob easily from a recording page on MythWeb or a recording's menu on your frontend.  If you are having ffmpeg troubles it may be helpful to create a manual 1 minute recording to test with.

4. Your ffmpeg issues.  It looks to me like you have an issue with your config if you are seeing empty ffmpeg lines.  Can you pastebin your config files (/etc/mythtv/mythexport) and a portion of your logs file?

Hopefully that clears some of it up?  If not just ask whatever is still confusing.  I'll keep in mind that the wiki page is confusing when I rewrite it for Maverick's release.

---

### Post by johnelle on 2010-11-11
I did a multiple version upgrade and things actually worked initially but now I am running into situations where the queue either has a corrupt job (which causes the daemon to die) or it appears to have a large number of jobs in the queue on the mythweb status but nothing in the queue from the mythexport page and ffmpeg isn't showing up in top (which is how I usually tell that transcoding is underway).

Is there a way to clear the queue to an empty state so I can get some more info on what's going on?  Do I just drop a table in the DB?  Right now I am doing a reinstall to clear things up but thats kind of fat fingered.

---

### Post by rhpot1991 on 2010-11-11
> **johnelle said:**
> I did a multiple version upgrade and things actually worked initially but now I am running into situations where the queue either has a corrupt job (which causes the daemon to die) or it appears to have a large number of jobs in the queue on the mythweb status but nothing in the queue from the mythexport page and ffmpeg isn't showing up in top (which is how I usually tell that transcoding is underway).

Is there a way to clear the queue to an empty state so I can get some more info on what's going on?  Do I just drop a table in the DB?  Right now I am doing a reinstall to clear things up but thats kind of fat fingered.

I would check a few things:
1. That the export directory exists and has the proper permissions, check in the web interface.
2. In the export directory do you see any files named "mythexport.<number>"?

---

### Post by yamaha200 on 2010-11-11
Well, I'm sure I must be missing something simple and stupid but I can't figure out what...

I have followed the install directions here: [http://www.mythbuntu.org/wiki/MythExport](http://www.mythbuntu.org/wiki/MythExport)

After connecting to the web interface, I check one of the 2 configuration, choose User Job #1, and give it a description, then click Submit.

I have restarted both the frontend and the backend but when I am in the frontend and choose a recording I want to run the job on, there are no user jobs under the Job Options. Only "Begin Transcoding" and "Begin Commercial Flagging".

I notice when I run mythtv-setup that the job does show up there, with the name I gave it, and I have checked to allow it to be run.

In the frontend, when setting up a recording, I do have the option to allow post processing using job #1, but it does not have the name i gave it there.

In the mythexport web interface, I notice the "activate medibuntu" link and followed the directions there. However, the link still shows up on the page - should it go away when I have this done correctly or will it always be there?

thanks,
laura

---

### Post by rhpot1991 on 2010-11-11
> **yamaha200 said:**
> Well, I'm sure I must be missing something simple and stupid but I can't figure out what...

I have followed the install directions here: [http://www.mythbuntu.org/wiki/MythExport](http://www.mythbuntu.org/wiki/MythExport)

After connecting to the web interface, I check one of the 2 configuration, choose User Job #1, and give it a description, then click Submit.

I have restarted both the frontend and the backend but when I am in the frontend and choose a recording I want to run the job on, there are no user jobs under the Job Options. Only "Begin Transcoding" and "Begin Commercial Flagging".

I notice when I run mythtv-setup that the job does show up there, with the name I gave it, and I have checked to allow it to be run.

In the frontend, when setting up a recording, I do have the option to allow post processing using job #1, but it does not have the name i gave it there.

In the mythexport web interface, I notice the "activate medibuntu" link and followed the directions there. However, the link still shows up on the page - should it go away when I have this done correctly or will it always be there?

thanks,
laura

That activate medibuntu link will not go away.  I guess I never thought about that being confusing, but will consider improving that in the future.

Have you tried to restart your backend & frontend to see if it shows up then?

---

### Post by yamaha200 on 2010-11-11
> **rhpot1991 said:**
> That activate medibuntu link will not go away.  I guess I never thought about that being confusing, but will consider improving that in the future.

Have you tried to restart your backend & frontend to see if it shows up then?

yep. Restarted both. Then rebooted the whole machine. No luck.

laura

---

### Post by johnelle on 2010-11-13
The answer is that if you have one stuck (i.e. can't be deleted through the System Status menu) then 
sudo apt-get install phpmyadmin
and delete the offending entries in the job queue table.  Takes about 2 minutes including the install.  Definitely a necessary tool on a mythbox.

---

### Post by malaTG on 2010-11-18
Hi guys,

I used to use nuvexport to export my recordings to mythvideo but this is no longer available in a convenient way. I looked around and found mythexport and even though it is marketed as a converter to portable device I don't see any reason why I couldn't use it as a converter to "normal" files. Would you agree with me on that? 

Does anyone use it for this purpose at the moment? And if so do you have any good conversion configuration strings to share? In my box I have 4 different kinds of recordings that I would like to convert with good quality into mythvideo. All are MPEG2 streams with the following specs

1. 16:9 720x576
2. 4:3 720x576
3. 16:9 1280x720
4. 16:9 720x576 within a 4:3 file i.e. I would like to cut off the top and bottom to get a "real" 16:9 file

If anyone could send me in the right direction for maybe one of these I would be grateful

Thx in advance!

Mala

---

### Post by marc.aronson on 2010-11-21
Let me start by thanking the author of mythexport -- this is exactly what I have been looking for! I've installed mythexport into my mythbuntu 10.04 (10.4?) install. When I try to use "on the go" the output file has video but no audio. I am using the "PortableH264HighRes" profile. I suspect this has to do with the AAC licensing issues I've been reading about in various threads, but so far, I have not been able to figure out how to solve this. 

Any help would be greatly appreciated -- I'm very excited about being able to view the transcoded views on my iPad and iPhone!

Marc

---

### Post by rhpot1991 on 2010-11-21
> **marc.aronson said:**
> Let me start by thanking the author of mythexport -- this is exactly what I have been looking for! I've installed mythexport into my mythbuntu 10.04 (10.4?) install. When I try to use "on the go" the output file has video but no audio. I am using the "PortableH264HighRes" profile. I suspect this has to do with the AAC licensing issues I've been reading about in various threads, but so far, I have not been able to figure out how to solve this. 

Any help would be greatly appreciated -- I'm very excited about being able to view the transcoded views on my iPad and iPhone!

Marc

I am assuming you have activated medibuntu?  I've heard from some people that adding "-ar 44100" or "-ar 48000" to the ffmpeg line have helped them with sound issues, you should try that.

---

### Post by marc.aronson on 2010-11-22
> **rhpot1991 said:**
> I am assuming you have activated medibuntu?  I've heard from some people that adding "-ar 44100" or "-ar 48000" to the ffmpeg line have helped them with sound issues, you should try that.

I did activate medibuntu -- did not help -- still could not find the "libfaac" codec. I then changed from "libfaac" to "aac" and I was able to get sound, but the audio quality was degraded -- sounds like being inside a tin can. I then tried [these instructions ]("http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289"), but it looks like the command line options have changed because some of the options in the profile are being rejected.

Marc

---

### Post by rhpot1991 on 2010-11-22
> **marc.aronson said:**
> I did activate medibuntu -- did not help -- still could not find the "libfaac" codec. I then changed from "libfaac" to "aac" and I was able to get sound, but the audio quality was degraded -- sounds like being inside a tin can. I then tried [these instructions ]("http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289"), but it looks like the command line options have changed because some of the options in the profile are being rejected.

Marc

You don't want to do that.  Get back to ubuntu/medibuntu's ffmpeg.

Did you upgrade after you enabled medibuntu, what version of libavcodec-extra and libavformat-extra are installed?

---

### Post by marc.aronson on 2010-11-23
> **rhpot1991 said:**
> You don't want to do that.  Get back to ubuntu/medibuntu's ffmpeg.

Did you upgrade after you enabled medibuntu, what version of libavcodec-extra and libavformat-extra are installed?

First, thank you for helping me out. Yes, I did attempt that upgrade after I enabled medibuntu. I enabled medibuntu these [these instructions]("https://help.ubuntu.com/community/Medibuntu").  I have backed out those changes. I am back to the point where "libfaac" is not found and I am able to get it to work with "-acodec aac", but the audio doesn't sound right. 

I am not certain  how to check the versions of libavcodec-extra and libavformat-extra that I am using -- can you tell me the command?

Thanks again for your help!

Marc

---

### Post by rhpot1991 on 2010-11-23
> **marc.aronson said:**
> First, thank you for helping me out. Yes, I did attempt that upgrade after I enabled medibuntu. I enabled medibuntu these [these instructions]("https://help.ubuntu.com/community/Medibuntu").  I have backed out those changes. I am back to the point where "libfaac" is not found and I am able to get it to work with "-acodec aac", but the audio doesn't sound right. 

I am not certain  how to check the versions of libavcodec-extra and libavformat-extra that I am using -- can you tell me the command?

Thanks again for your help!

Marc

You can find them in synaptec, or by running dpkg -l |grep libavformat-extra

---

### Post by marc.aronson on 2010-11-24
> **rhpot1991 said:**
> You can find them in synaptec, or by running dpkg -l |grep libavformat-extra

Thank you for your help. I now see my mistake. I have properly installed the package and libfaac is working. Thanks again for your help!

Marc

---

### Post by uncle hammy on 2011-01-22
I am trying to install MythExport on a secondary backend.  The installation keeps failing becauase "can't connect to MySQL on localhost".  Naturally, the reason for that is because this is a secondary backend, and the db is on the master.

How do I get around this?

Thanks.

---

### Post by malaTG on 2011-01-23
> **malaTG said:**
> Hi guys,

I used to use nuvexport to export my recordings to mythvideo but this is no longer available in a convenient way. I looked around and found mythexport and even though it is marketed as a converter to portable device I don't see any reason why I couldn't use it as a converter to "normal" files. Would you agree with me on that? 

Does anyone use it for this purpose at the moment? And if so do you have any good conversion configuration strings to share? In my box I have 4 different kinds of recordings that I would like to convert with good quality into mythvideo. All are MPEG2 streams with the following specs

1. 16:9 720x576
2. 4:3 720x576
3. 16:9 1280x720
4. 16:9 720x576 within a 4:3 file i.e. I would like to cut off the top and bottom to get a "real" 16:9 file

If anyone could send me in the right direction for maybe one of these I would be grateful

Thx in advance!

Mala

Bump

---

### Post by lingenfr on 2011-02-09
How long should it take on a reasonably fast 3Ghz/4GB machine to encode a 1.1GB show to the hires profile? Mine has been at it about 7.5 hours. I don't see any errors in the log. Thanks.

---

### Post by rhpot1991 on 2011-02-10
> **uncle hammy said:**
> I am trying to install MythExport on a secondary backend.  The installation keeps failing becauase "can't connect to MySQL on localhost".  Naturally, the reason for that is because this is a secondary backend, and the db is on the master.

How do I get around this?

Thanks.

Check your /etc/mythtv/mysql.txt and make sure that DBHostName is pointing at the right spot, it should read it from there.

---

### Post by rhpot1991 on 2011-02-10
> **malaTG said:**
> I used to use nuvexport to export my recordings to mythvideo but this is no longer available in a convenient way. I looked around and found mythexport and even though it is marketed as a converter to portable device I don't see any reason why I couldn't use it as a converter to "normal" files. Would you agree with me on that? 

Does anyone use it for this purpose at the moment? And if so do you have any good conversion configuration strings to share? In my box I have 4 different kinds of recordings that I would like to convert with good quality into mythvideo. All are MPEG2 streams with the following specs

It could be used for that, if you pointed your output directory to the same directory that mythvideo read from.  The RSS will fill up with stuff you don't care about, but you could clean that up or comment out the code which writes to the MySQL table.

You most likely will need to mess with the configs as most of them are designed for portable devices with a smaller resolution.

---

### Post by rhpot1991 on 2011-02-10
> **lingenfr said:**
> How long should it take on a reasonably fast 3Ghz/4GB machine to encode a 1.1GB show to the hires profile? Mine has been at it about 7.5 hours. I don't see any errors in the log. Thanks.

That seems like way too long.  Can you verify the file is still growing?  It sounds like something crashed and you aren't seeing it in the log.

---

### Post by lingenfr on 2011-03-12
Thanks. I think I actually had some hardware problems with my backend, so I decided it was time for an overhaul. I built a new machine and mythexport seems to be working pretty well. I have a couple of questions.

1) I am flagging commercials before exporting, but the exported files still have the commercials. Is it possible to remove the commercials or preserve the ability for one-click-skip in the exported file?

2) Mythexport leaves behind a file called x264_2pass.log.mbtree. Is it possible to stop that? Not a big deal, but potentially confusing to other family members.

3) Can I apply filters as I export? The quality of my analog signal is not great, so I would like to clean up the recording during export if possible. 

Thanks.

---

### Post by rhpot1991 on 2011-03-12
> **lingenfr said:**
> Thanks. I think I actually had some hardware problems with my backend, so I decided it was time for an overhaul. I built a new machine and mythexport seems to be working pretty well. I have a couple of questions.

1) I am flagging commercials before exporting, but the exported files still have the commercials. Is it possible to remove the commercials or preserve the ability for one-click-skip in the exported file?

2) Mythexport leaves behind a file called x264_2pass.log.mbtree. Is it possible to stop that? Not a big deal, but potentially confusing to other family members.

3) Can I apply filters as I export? The quality of my analog signal is not great, so I would like to clean up the recording during export if possible. 

Thanks.

1. You should do a lossless transcode first with Myth, this will remove the commercials.  Then when you encode with MythExport they will be removed.  This wiki page describes the process: [http://www.mythtv.org/wiki/Removing_Commercials](http://www.mythtv.org/wiki/Removing_Commercials)

2. Easiest way here would be to add a line to the Daemon or cleanup script to remove this file if it exists.  Feel free to open a bug and I'll address it: [https://bugs.launchpad.net/ubuntu/+source/mythexport](https://bugs.launchpad.net/ubuntu/+source/mythexport)

3. If ffmpeg can do this then yes you can.  If you need another tool to do so then this can be done as well, will just require more tweaking of a config to do so.  Use this config as a starting point: [http://www.baablogic.net/mythexport/example_config.pm](http://www.baablogic.net/mythexport/example_config.pm)

---

### Post by yamaha200 on 2011-03-31
> **yamaha200 said:**
> yep. Restarted both. Then rebooted the whole machine. No luck.

laura

Been a while but I'm back and ready to try again!
I added "debug" and output in the logfile now looks like:


March 31 19:19:50 laura-Vostro-200 /usr/bin/mythexport-daemon[25217]: Caught SIGTERM:  exiting gracefully
March 31 19:19:50 laura-Vostro-200 /usr/bin/mythexport-daemon[25217]: Stopping Processing:  1301624390
March 31 19:20:03 laura-Vostro-200 /usr/bin/mythexport-daemon[26630]: Starting Processing:  1301624403
March 31 19:20:03 laura-Vostro-200 /usr/bin/mythexport-daemon[26630]: query = select id, type, param from mythexport_job_queue o
rder by id at line 489 in /usr/bin/mythexport-daemon

That last part of course keeps repeating with updated timestamp as the daemon keeps looping.

My  /etc/mythtv/mythexport/mythexport.cfg looks like this:
dir=/storage/recordings/mobile

I do not seem to have a settings cfg file. I was operating under the assumption that using the web interface to create a user job would create that file. Is that incorrect?

Using myPhpAdmin I have been looking through the database. I have tables for mythexport and mythexport_job_queue but no entries in either one. Still trying to figure out which table has the user jobs to see if an entry is actually getting created from the mythexport web interface.

As a reminder, the problem I'm seeing is that when I use the web interface under mythexportSetup, no user job appears in my mythfrontend (or mythweb) corresponding to the job I just tried to create. Something is getting saved somewhere though because when I go back to the mythexportSetup, the job name is there.

any suggestions?
thanks,
laura

---

### Post by yamaha200 on 2011-03-31
of course as soon as I post I find more...

In the settings table, User Job #1 does indeed have the name I gave it.

In the backend setup, User Job #1 has this same name (obviously since it pulls it from the settings table). And the checkbox allowing use of User Job #1 is checked (and shows up as a 1 in the settings table). However, User Job #1 does not have any command associated with it. As soon as I put something in there and restart the backend, I see that option pop up for my recordings in the frontend.

So the question is, why isn't the web interface to mythexport filling in the command? Or did I miss something in the instructions where I needed to do that?

Thanks,
laura

---

### Post by yamaha200 on 2011-04-06
I knew I was missing something simple ;)

Turns out going to [http://xxx.xxx.x.xx/mythexport](http://xxx.xxx.x.xx/mythexport) and then choosing the mythexport setup was not the right thing to do. As soon as I went to [http://xxx.xxx.x.xx/mythexport/system_setup.cgi](http://xxx.xxx.x.xx/mythexport/system_setup.cgi) and filled in the form, the user job was created perfectly and I could schedule recordings to get processed.

Now to wait and see how they come out!

laura

---

### Post by Huphup on 2011-06-06
Hello, 

Hoping I can ask a newbie question here to try to get mythexport sound working with my mythbuntu 10.04 system. As far as I can tell I haven't been able to get libfaac installed and/or recognized by ffmpeg:

I have installed the medibuntu repositories, and the Medibuntu w32codec package. 

mythexport's log says "Unknown encoder 'libfaac'" when a job is run.

Per the responses to earlier questions from marc aronson, I think that I need to install the proper version of libavformat-extra-52 and libavcodec-extra-52. Here are my current versions:

```
$ dpkg -l | grep libavformat-extra
ii  libavformat-extra-52                 4:0.6.2-1ubuntu2~ppa1~lucid1                       Libav file format library
$ dpkg -l | grep libavcodec-extra
ii  libavcodec-extra-52                  4:0.6.2-1ubuntu2~ppa1~lucid1                       Libav codec library

```

If I use Synaptic to "force version" and select the medibuntu versions of libavformat-extra-52 and libavcodec-extra-52, I get warnings that mythexport (among numerous other packages) will be uninstalled if I force install. 

Before I get myself in a hole, would you let me know the steps I might've missed?

Many thanks!

---

### Post by WittFan on 2011-06-07
> **yamaha200 said:**
> Well, I'm sure I must be missing something simple and stupid but I can't figure out what...

I have followed the install directions here: [http://www.mythbuntu.org/wiki/MythExport](http://www.mythbuntu.org/wiki/MythExport)

After connecting to the web interface, I check one of the 2 configuration, choose User Job #1, and give it a description, then click Submit.

I have restarted both the frontend and the backend but when I am in the frontend and choose a recording I want to run the job on, there are no user jobs under the Job Options. Only "Begin Transcoding" and "Begin Commercial Flagging".

I notice when I run mythtv-setup that the job does show up there, with the name I gave it, and I have checked to allow it to be run.

In the frontend, when setting up a recording, I do have the option to allow post processing using job #1, but it does not have the name i gave it there.

I'm having the exact same problem. Lucid with Mythbuntu 0.24.1. I did a dpkg --purge, dropped the two mythexport tables in mythconverg, reinstalled, configured the export directory on system setup screen, nothing seems to work. Did anybody manage to figure out what was causing this?

---

### Post by yamaha200 on 2011-06-07
> **WittFan said:**
> I'm having the exact same problem. Lucid with Mythbuntu 0.24.1. I did a dpkg --purge, dropped the two mythexport tables in mythconverg, reinstalled, configured the export directory on system setup screen, nothing seems to work. Did anybody manage to figure out what was causing this?
 
 
Did you try my solution from post #224? Did that work for you or not?
Laura

---

### Post by Huphup on 2011-06-13
> **Huphup said:**
> Hello, 

Hoping I can ask a newbie question here to try to get mythexport sound working with my mythbuntu 10.04 system. As far as I can tell I haven't been able to get libfaac installed and/or recognized by ffmpeg:

I have installed the medibuntu repositories, and the Medibuntu w32codec package. 

mythexport's log says "Unknown encoder 'libfaac'" when a job is run.

Per the responses to earlier questions from marc aronson, I think that I need to install the proper version of libavformat-extra-52 and libavcodec-extra-52. Here are my current versions:

```
$ dpkg -l | grep libavformat-extra
ii  libavformat-extra-52                 4:0.6.2-1ubuntu2~ppa1~lucid1                       Libav file format library
$ dpkg -l | grep libavcodec-extra
ii  libavcodec-extra-52                  4:0.6.2-1ubuntu2~ppa1~lucid1                       Libav codec library

```

If I use Synaptic to "force version" and select the medibuntu versions of libavformat-extra-52 and libavcodec-extra-52, I get warnings that mythexport (among numerous other packages) will be uninstalled if I force install. 

Before I get myself in a hole, would you let me know the steps I might've missed?

Many thanks!

Anyone have any suggestions? Thanks in advance for any help.

---

### Post by rhpot1991 on 2011-06-13
> **Huphup said:**
> Anyone have any suggestions? Thanks in advance for any help.

Hmmm, this shouldn't be an issue, if you have MythExport installed then enable medibuntu it should pull everything you need.  Lucid was so long ago :)  I suppose I can setup a VM to make sure this isn't a version issue in the dependencies.  Which version of MythExport are you running, running the testing PPA?

---

### Post by Huphup on 2011-06-14
> **rhpot1991 said:**
> Hmmm, this shouldn't be an issue, if you have MythExport installed then enable medibuntu it should pull everything you need.  Lucid was so long ago :)  I suppose I can setup a VM to make sure this isn't a version issue in the dependencies.

Thanks so much for the reply. Are you saying that clicking the "enable mediabuntu" link on the setup screen is supposed to properly configure my mythbuntu system? If so, I am more confused than before :) Because on my setup, that link just opens the Medibuntu information page with instructions on adding the Medibuntu PPA etc. 

> Which version of MythExport are you running, running the testing PPA?

```
$ apt-cache policy mythexport
mythexport:
  Installed: 2.2.3-0ubuntu1~ppa3
  Candidate: 2.2.3-0ubuntu1~ppa3
  Version table:
 *** 2.2.3-0ubuntu1~ppa3 0
        500 http://ppa.launchpad.net/mythbuntu/testing/ubuntu/ lucid/main Packages
        100 /var/lib/dpkg/status
     2.1.5-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid/universe Packages
```

Thanks again for any direction you can provide!

---

### Post by rhpot1991 on 2011-06-14
> **Huphup said:**
> Thanks so much for the reply. Are you saying that clicking the "enable mediabuntu" link on the setup screen is supposed to properly configure my mythbuntu system? If so, I am more confused than before :) Because on my setup, that link just opens the Medibuntu information page with instructions on adding the Medibuntu PPA etc.

No, you need to enable it like you said.  Then you should:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Huphup on 2011-06-14
I definitely ran apt-get update and apt-get upgrade (several times) and ended up with still no sound. Versions of ffmpeg and libavformats-extra-52 ended up as I posted in my first cry for help.  Note that the ffmpeg version is from lucid-bleed PPA and not medibuntu, but as I said, if I select the medibuntu version for a force install, I get a long list of dependent packages that would be uninstalled.  

Any other thoughts or suggestions? I really appreciate your time.

Greg

---

### Post by Huphup on 2011-06-15
Quick folowup to say that my problem was solved by downgrading my version of ffmpeg from 4:0.6.2 to 4:0.5.x , after which I could install the medibuntu libavcodec-extra-52 package   .... Now mythexport works great. 

In the process, apt uninstalled VLC from my system, so that might have been the conflict. I'm not sure of that, though. 

Thanks for the help!

---

### Post by rhpot1991 on 2011-06-15
> **Huphup said:**
> Quick folowup to say that my problem was solved by downgrading my version of ffmpeg from 4:0.6.2 to 4:0.5.x , after which I could install the medibuntu libavcodec-extra-52 package   .... Now mythexport works great. 

In the process, apt uninstalled VLC from my system, so that might have been the conflict. I'm not sure of that, though. 

Thanks for the help!

Glad you got it working, you may want to consider upgrading from lucid at some point, if you want newer versions of packages and all.

---

### Post by Huphup on 2011-06-15
> **rhpot1991 said:**
> Glad you got it working, you may want to consider upgrading from lucid at some point, if you want newer versions of packages and all.

Re: upgrading, fair enough, but my mythTV setup is "just working" right now, and it took me a long time (and Spousal Aggravation points) to get it that way, so I fear change :D

---

### Post by Huphup on 2011-07-06
Hi, back with another question ...

I have mythexport running great to export to my iPad using the built-in configuration. I have it set up as User Job #3 in myth. What I would like to do is have another User Job #4 set up with a different configuration, so I can export to my kids' portable media players (which don't support h264 video, so I can't use the same ffmpeg settings as the iPad export)

Can I set up two user jobs up with different configuration settings with a single install of mythexport? The web configuration pages for mythexport aren't clear if I can. 

Thanks!

Huphup

---

