---
title: "mkv -&gt; avi (for Xbox 360)"
date: 2009-02-08
forum: Multimedia Software
---

### Post by jonofan on 2009-02-08
Hi,

I am using jexxie's script from [**_here_**]("http://ubuntuforums.org/showthread.php?t=684780&page=14") to convert 720p mkv's into avi's to play on my 360.

I am getting the following error:
```

./remuxtomp4.sh: line 50: 22856 Aborted                 MP4Box -raw 1 "$DEST.m4a" >> "$log" 2>&1
failed
 [i] Showing the last 5 lines from the logfile (/home/jono/Desktop/log.23:48:22-2009-02-08.txt)...
Processed 1585 seconds...
21705's retcode: 0
success
 [x] Extracting audio from MP4 container (silly neroAacEnc)...22856's retcode: 134
failed

```

Can anyone help me with this?

---

### Post by jexxie on 2009-02-09
I take it MP4Box is installed?  Have you tried extracting a stream manually using a similar command?

---

### Post by ouija on 2009-02-10
Reads like an issue with MP4Box.  Trying uninstalling and re-installing the "gpac" package found using the synaptic package manager and run the script again.

---

### Post by jonofan on 2009-02-10
Reinstalled gpac, same issue.

Is there anything other installing gpac that I need to do for MP4Box?
What kind of similar command would you like me to try?

I have tried **MP4Box -raw 1 file.mp4.m4a** which returns the same error.

---

### Post by jonofan on 2009-02-12
bump

---

### Post by ouija on 2009-02-12
Try using the attached script.

It was taken from [http://www.dufault.info/blog/a-script-to-remux-mkv-videos-into-mp4-videos/](http://www.dufault.info/blog/a-script-to-remux-mkv-videos-into-mp4-videos/) and works excellent for me.  It will even check your system before running and let you know if you are missing certain packages.

I also edited another version of it which will change the "level" bit of the mkv video stream to enable compatibility with xbox360 (the 360 will not support videos with a level of 5.1 or higher - see: [http://blogs.msdn.com/xboxteam/archive/2007/05/09/spring-07-video-playback-faq.aspx](http://blogs.msdn.com/xboxteam/archive/2007/05/09/spring-07-video-playback-faq.aspx)) which I can post too if you like.

Let me know how it works.

---

### Post by jonofan on 2009-02-12
Thanks ouija, that is the same script I am using. When running I get no errors regarding missing packages. Are you able to give me a list of the packages I would need to run the script? I might try on another computer.

---

### Post by ouija on 2009-02-12
> **jonofan said:**
> Thanks ouija, that is the same script I am using. When running I get no errors regarding missing packages. Are you able to give me a list of the packages I would need to run the script? I might try on another computer.

Yes, the required packages are:

[B]mplayer
normalize-audio
mencoder
MP4Box (found in gpac)
mkvinfo (found in mkvtoolnix)
mkvextract (found in mkvtoolnix)
neroAacEnc
[/B]

Just curious which distro of Ubuntu are you using?

---

### Post by jonofan on 2009-02-12
Just tried it on my server, running ubuntu 8.10 server edition, all programs installed fresh except for mencoder. Same deal:

```
./remuxtomp4.sh: line 50: 30282 Aborted                 MP4Box -raw 1 "$DEST.m4a" >> "$log" 2>&1
failed
 [i] Showing the last 5 lines from the logfile (/home/jono/log.15:02:52-2009-02-13.txt)...
Processed 2552 seconds...
28292's retcode: 0
success
 [x] Extracting audio from MP4 container (silly neroAacEnc)...30282's retcode: 134
failed
```

Desktop which I was using before was running 8.10. Perhaps this is some issue with intrepid?

---

### Post by ouija on 2009-02-13
It looks like a problem with the neroAacEnc.


Download and extract from here: [http://ftp6.nero.com/tools/NeroDigitalAudio.zip](http://ftp6.nero.com/tools/NeroDigitalAudio.zip)

then just take the files out from the "linux" folder and chmod them so they are executable. 

Delete any existing files with matching names on your system then copy each of the files to the "/bin" folder.

Fire up the script and try it again.

---

### Post by jonofan on 2009-02-14
Cheers for the link. I think that is the same one I was using, removed the ones I had and used the ones from the link just incase, but doesn't seem to have made a difference.

Still getting the same error.

I'm not sure that it is a nero issue, it still looks like MP4Box, the first line of the error is:

[COLOR="Blue"]./remuxtomp4.sh: line 50:  7954 Aborted                 
MP4Box -raw 1 "$DEST.m4a" >> "$log" 2>&1                                                                                           failed[/COLOR]

and

[COLOR="Blue"][x] Extracting audio from MP4 container (silly neroAacEnc)...22856's retcode: 134
failed[/COLOR]

The part that says "silly neroAacEnc" is actually running an MP4Box command; **MP4Box -raw 1 "$DEST.m4a" >> "$log" 2>&1**

I think if I have time over the next couple of days I will try this on a fresh 8.04 install. Has any one had success with this using 8.10?

---

### Post by ouija on 2009-02-16
I have recently upgraded to Intrepid now after much consideration and ran into the same issue.

However, I may have stumbled upon two fixes.

[https://bugs.launchpad.net/ubuntu/+source/gpac/+bug/273075](https://bugs.launchpad.net/ubuntu/+source/gpac/+bug/273075)

I have gone ahead and removed the gpac and the required gpaclib packages installed in the synaptic package manager for intrepid, and downloaded the two posted near the end of the page for that above link, and then ran the script with root privileges (ie: sudo remuxtomp4.sh file.mkv) and it is working now.  

The two packages can be found here: [http://launchpadlibrarian.net/21606791/gpac_0.4.4-0.3ubuntu3_amd64.deb](http://launchpadlibrarian.net/21606791/gpac_0.4.4-0.3ubuntu3_amd64.deb) and [http://launchpadlibrarian.net/21606802/libgpac0.4.4_0.4.4-0.3ubuntu3_amd64.deb](http://launchpadlibrarian.net/21606802/libgpac0.4.4_0.4.4-0.3ubuntu3_amd64.deb)

However, I never tested running the script as root before using the newer packages that come in the repository so maybe that is the problem all along?  after the remux process is complete without errors I will retry first without running it as root using the attached files, and then again using the files in the repository and running as root and post my results..

**[COLOR="Red"]UPDATE:  The packages that I installed seem to run even without root permissions, so I recommend uninstalling the latest packages from the synaptic package manager and installing the two provided above and this should fix the issue (for now)[/COLOR]**

---

### Post by ouija on 2009-02-16
I have run this now a few times and those packages seem to make the difference.  I remuxed two mkv files and they both worked beautifully on my 360.

---

### Post by jonofan on 2009-02-18
I gave that a go using [_**this deb**_]("http://launchpadlibrarian.net/20748403/gpac_0.4.4-0.3ubuntu3_i386.deb") from the same link (I'm running 32-bit)

Tried with root before hand, and with this new setup but no luck. I'm not sure I've done it correctly though, my steps were:

[COLOR="Blue"]apt-get remove gpac
apt-get build-dep gpac
dpkg -i <above .deb>[/COLOR]

Am I missing something?

---

### Post by ouija on 2009-02-18
Oh I failed to realize you were running 32 bit.

I read that the Hardy versions of gpac and gpaclib will run under Intrepid and solve this issue.  However, I'm not too sure if this indeed is the case.

Give that a try, and if not, then you could always try using the "mp4creator" package to remux mkv's.

Another topic in the forums I found with an updated script using mp4creator is here: [http://ubuntuforums.org/showthread.php?t=811826&page=3](http://ubuntuforums.org/showthread.php?t=811826&page=3)

It too states that the Hardy packages for gpac will run under Intrepid.

Let me know how it goes :)

UPDATE:  Here is another page that details how to remux using mp4creator in a step-by-step process: [http://cantthinkofa.com/platforms/linux/remuxing-mkv-for-the-xbox-360.html](http://cantthinkofa.com/platforms/linux/remuxing-mkv-for-the-xbox-360.html)

---

### Post by jonofan on 2009-02-24
Sorry for the belated reply, I've been overseas for a week.

The second link with the MP4creator script works a treat for me. Thanks so much for all your help!

---

### Post by ouija on 2009-02-25
Good to hear.  Also, that script will fix the level of the mkv file you're converting as well (which the script you were using didn't I believe) so that is an added bonus, as the 360 cannot play mp4/avi with a level greater than 4:1.

---

