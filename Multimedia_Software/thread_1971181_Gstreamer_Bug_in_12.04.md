---
title: "Gstreamer Bug in 12.04"
date: 2012-05-02
forum: Multimedia Software
---

### Post by jzemeocala on 2012-05-02
Hey everyone. I have recently upgraded to 12.04 and one of my favourite programs has become broken as a result (Minitube). After some digging around it appears that this is due to the new version of Gstreamer that is in the precise repos. For those that wish to replicate this bug quickly, it also happens in the youtube addon for Totem, as well as spitting out an error about missing codecs. So I tried to downgrade gstreamer and its various packages but there does not seem to be any old versions available. I also tried to use gstreamer's developers repo, but that was an epic fail on my part. I have also tried to change the dependencies of the minitube .deb to rely on phonon-backend-vlc instead of phonon-backend-gstreamer but I was quickly lost. If you google around you will see that this is a confirmed bug with gstreamer but there has yet to be a fix or workaround.

Any help would be appreciated.

---

### Post by mc4man on 2012-05-02
I have that bug on decoding & also one on allowing the vlc backend, not much progress. Also suggested to the webupd8 ppa to redo their package, no luck there

Anyway very simple to edit the .deb, - I'll try to lay out

You might as well use the 1.7 package so will get from the webupd8 ppa & fix, should take less than a min.
The wget's are good unless ppa updates names, [page here ]("https://launchpad.net/~nilarimogard/+archive/webupd8/+packages?field.name_filter=&field.status_filter=published&field.series_filter=precise")for manual download if needed

In terminal

```
mkdir Desktop/fix && cd Desktop/fix
```

If on 64 bit install
```
wget https://launchpad.net/~nilarimogard/+archive/webupd8/+files/minitube_1.7.1-1%7Ewebupd8%7Eprecise_amd64.deb

```

If on 32 bit install
```
wget https://launchpad.net/~nilarimogard/+archive/webupd8/+files/minitube_1.7.1-1%7Ewebupd8%7Eprecise_i386.deb

```

After download completes **leave terminal open**, open the fix folder on your Desktop, right click on the .deb > extract here
Once extracted delete the .deb, leaving just the folder - screen 1

Open  the folder > DEBIAN. Inside will be a control file, open in text editor
On the Depends: line you'll see _phonon-backend-gstreamer,_ you want to add this between  the r & , add a space after the r
```
| phonon-backend-vlc
```
So that looks like  - see screen 2
```
phonon-backend-gstreamer | phonon-backend-vlc,
```

Save the control file, close text-editor

Back at the terminal you left open (at the **:~/Desktop/fix$** prompt

For 64 bit
```
 dpkg -b ./minitube_1.7.1-1~webupd8~precise_amd64
```

For 32 bit
 ```
dpkg -b ./minitube_1.7.1-1~webupd8~precise_i386 
```

Once the new deb is built install with gdebi or Sc

After install open synaptic, search phonon-
Install the vlc backend & then remove the gstreamer backend 
(edit: unless you already have the vlc backend install, if so then you're good to go after the minitube install

---

### Post by jzemeocala on 2012-05-03
Thanks so Much. This solved the issue. Now I'm gonna forward this thread to flavio so that he can implement this minor but crucial change into Minitube. I still feel that Gstreamer should fix thing on their end though.

---

### Post by mc4man on 2012-05-03
This bug I had on that, too bad not implemented - they had a couple of months to do so
[https://bugs.launchpad.net/ubuntu/+source/minitube/+bug/941586](https://bugs.launchpad.net/ubuntu/+source/minitube/+bug/941586)

---

### Post by guygong on 2012-05-03
I followed the directions to add the VLC backend but when I entered the last command, I got an error that there was no file. I'm new at this. Is there a step I'm missing?
dpkg -b  ./minitube_1.7.1-1~webupd8~precise_i386

---

### Post by mc4man on 2012-05-03
> **guygong said:**
> I followed the directions to add the VLC backend but when I entered the last command, I got an error that there was no file. I'm new at this. Is there a step I'm missing?
dpkg -b  ./minitube_1.7.1-1~webupd8~precise_i386

Assuming you have exactly like in screenshot 1 & have edited the control file inside
Then open a terminal &
```
cd Desktop/fix
```
```
dpkg -b ./minitube_1.7.1-1~webupd8~precise_i386
```

Example
doug@doug-XPS-M1330:~$ cd Desktop/fix
doug@doug-XPS-M1330:~/Desktop/fix$ dpkg -b  ./minitube_1.7.1-1~webupd8~precise_i386
dpkg-deb: building package `minitube:i386' in `./minitube_1.7.1-1~webupd8~precise_i386.deb'.
doug@doug-XPS-M1330:~/Desktop/fix$

---

### Post by guygong on 2012-05-03
Thanks MC4MAN.

I think you nailed it for me. I was in a rush to get ready for work and I don't think I noticed if the I had extracted the contents of the folder correctly. I'll have to look at it tonight.

---

### Post by guygong on 2012-05-04
Got it installed now. It's better in that it will play video but it still does skip videos intermittently. Hopefully, it will get better with newer updates. Not a big problem since I also downloaded the plugin for Firefox that allows me to play videos off of Youtube without having to use flash. Too bad it doesn't work for video on sites like yahoo or some other local news websites.:):(

---

### Post by mc4man on 2012-05-04
> **guygong said:**
> Got it installed now. It's better in that it will play video but it still does skip videos intermittently. Hopefully, it will get better with newer updates. Not a big problem since I also downloaded the plugin for Firefox that allows me to play videos off of Youtube without having to use flash. Too bad it doesn't work for video on sites like yahoo or some other local news websites.:):(

There is another bug on minitube concerning crashing. Changing backends does not fix that though I've found the vlc backend to be less prone to it, though it will happen from time to time

Also there just was a commit to fix some issue with very long vids & non gstreamer backends, never has been an issue here. The fix is in the current master source, will be included in the next minitube release

( I 'debianized' the current master & can attach on request for those interested in building their own package

---

### Post by guygong on 2012-05-05
I can live with it until the next fix. Thanks.:)

---

### Post by jzemeocala on 2012-05-05
I think its funny how a lot of less-knowledgeable users like myself were going nuts trying to fix this. And after a week of serious digging for a solution, I get a good workaround within 24 hours of asking for help here. However, When I asked on Flavios forum[ HERE]("http://flavio.tordini.org/forums/topic/linux-minitube-1-7-1-skips-playing-videos"), he flat out ignored me and acted as though there was nothing he could do about the original bug with the gstreamer backend and basically told ubuntu users that nothing could be done and that they would have to wait until gstreamer or ubuntu fixes it. But when I pointed out this thread with a decent fix for the issues that works great from the users perspective, He acted like this was an obvious workaround that he knew of from the start. But I guess it wasn't good enough in his eyes or whatever because it wasn't using gstreamer. 

As much as I like his software, he seems a little arrogant to me. ANd I think that he should just edit his .deb to allow users to choose there own backend.

---

### Post by mc4man on 2012-05-08
As per a request & considering the current non addressing of the decode & allow either backend bugs, - a simple build of current minitube 1.7.1 source with adjusted control file & a patch for a remote vlc backend issue

Will be done in a single terminal, to prep download attached and extract the minitube_build folder.

Then cd to minitube_build in a terminal, ie, prompt will end with - 
minitube_build$

Then just a few simple commands

```
sudo apt-get build-dep minitube
```

When done  - 
```
sudo apt-get install devscripts
```

 ```
dpkg-source -x minitube_1.7.1-2+nmu1.dsc
```
Should show this - Ex.
> doug@doug-XPS-M1330:~/Desktop/minitube_build$ dpkg-source -x minitube_1.7.1-2+nmu1.dsc dpkg-source: warning: extracting unsigned source package (minitube_1.7.1-2+nmu1.dsc)
dpkg-source: info: extracting minitube in minitube-1.7.1
dpkg-source: info: unpacking minitube_1.7.1.orig.tar.gz
dpkg-source: info: unpacking minitube_1.7.1-2+nmu1.debian.tar.gz
dpkg-source: info: applying disable-update-check
dpkg-source: info: applying proper-tempfiles
dpkg-source: info: applying vlc-backend.patch
doug@doug-XPS-M1330:~/Desktop/minitube_build$

Then finish up - 
```
cd minitube-1.7.1 && debuild -us -uc
```

Then use gdebi or Software-center to install

Note - if you have the previous ppa package installed & if  it is   seen as higher version, (shouldn't), either remove first or use sudo dpkg -i /path/to/nameofthe.deb

screen show your build folder when done

---

### Post by mc4man on 2012-05-10
Just a note on the decoding issue with gstreamer in 12.04
We've tracked it to a specfic plugin in the gstreamer bad plugins package.
So until fixed, (if ever) then can be worked around with 
```
sudo mv /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so.bak
```

---

### Post by boysha on 2012-05-11
> **mc4man said:**
> I have that bug on decoding & also one on allowing the vlc backend, not much progress. Also suggested to the webupd8 ppa to redo their package, no luck there

Anyway very simple to edit the .deb, - I'll try to lay out

You might as well use the 1.7 package so will get from the webupd8 ppa & fix, should take less than a min.
The wget's are good unless ppa updates names, [page here ]("https://launchpad.net/~nilarimogard/+archive/webupd8/+packages?field.name_filter=&field.status_filter=published&field.series_filter=precise")for manual download if needed

In terminal

```
mkdir Desktop/fix && cd Desktop/fix
```

If on 64 bit install
```
wget https://launchpad.net/~nilarimogard/+archive/webupd8/+files/minitube_1.7.1-1%7Ewebupd8%7Eprecise_amd64.deb

```

If on 32 bit install
```
wget https://launchpad.net/~nilarimogard/+archive/webupd8/+files/minitube_1.7.1-1%7Ewebupd8%7Eprecise_i386.deb

```

After download completes **leave terminal open**, open the fix folder on your Desktop, right click on the .deb > extract here
Once extracted delete the .deb, leaving just the folder - screen 1

Open  the folder > DEBIAN. Inside will be a control file, open in text editor
On the Depends: line you'll see _phonon-backend-gstreamer,_ you want to add this between  the r & , add a space after the r
```
| phonon-backend-vlc
```
So that looks like  - see screen 2
```
phonon-backend-gstreamer | phonon-backend-vlc,
```

Save the control file, close text-editor

Back at the terminal you left open (at the **:~/Desktop/fix$** prompt

For 64 bit
```
 dpkg -b ./minitube_1.7.1-1~webupd8~precise_amd64
```

For 32 bit
 ```
dpkg -b ./minitube_1.7.1-1~webupd8~precise_i386 
```

Once the new deb is built install with gdebi or Sc

After install open synaptic, search phonon-
Install the vlc backend & then remove the gstreamer backend 
(edit: unless you already have the vlc backend install, if so then you're good to go after the minitube install

[COLOR="Blue"]This helped me too! Thank you! Cheers![/COLOR]

---

### Post by guygong on 2012-05-11
> **mc4man said:**
> Just a note on the decoding issue with gstreamer in 12.04
We've tracked it to a specfic plugin in the gstreamer bad plugins package.
So until fixed, (if ever) then can be worked around with 
```
sudo mv /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so.bak
```
Does the code only work for the 64 bit systems?

---

### Post by jaaprumping on 2012-05-11
> **mc4man said:**
> Just a note on the decoding issue with gstreamer in 12.04
We've tracked it to a specfic plugin in the gstreamer bad plugins package.
So until fixed, (if ever) then can be worked around with 
```
sudo mv /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so.bak
```

THanks - this is the magic line I was looking for :)
Jaap

---

### Post by mc4man on 2012-05-11
> **guygong said:**
> Does the code only work for the 64 bit systems?

That was for 64 bit - 
On a 32 bit install something like

```
sudo mv /usr/lib/i386-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so /usr/lib/i386-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so.bak

```

I didn't see any loss of function by removing that plugin but if any is found please note here or in bug
[https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/973014](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/973014)

---

### Post by guygong on 2012-05-12
> **mc4man said:**
> That was for 64 bit - 
On a 32 bit install something like

```
sudo mv /usr/lib/i386-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so /usr/lib/i386-linux-gnu/gstreamer-0.10/libgstvideoparsersbad.so.bak

```

I didn't see any loss of function by removing that plugin but if any is found please note here or in bug
[https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/973014](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/973014)
Thanks MC4MAN. I'll have to try it when or if I re-install the gstreamer. I reinstalled Minitube with your newest process and it works better than just editing the control file with "phonon-backend-vlc but still have problems with videos skipping. Strange thing is that I can sometimes go back to the skipped video and it will play. But at least it doesn't skip in the middle of a video.

---

### Post by guygong on 2012-05-12
> **guygong said:**
> Thanks MC4MAN. I'll have to try it when or if I re-install the gstreamer. I reinstalled Minitube with your newest process and it works better than just editing the control file with "phonon-backend-vlc but still have problems with videos skipping. Strange thing is that I can sometimes go back to the skipped video and it will play. But at least it doesn't skip in the middle of a video.
I did the new installation procedure. It seems to work better but seems like long videos that are anywhere from 9 minutes or longer don't play and it skips through them until it finds a length it can play. I tried reinstalling the gstreamer phonon and got the same results. However, the only difference is that it didn't skip to the next video. It allowed me to manually skip ahead instead. I tested it on video searches of Star Trek Phase 2 and Bicycle Commuting. Videos less than 9 minutes went smoothly while those longer than 9 minutes wouldn't play. Not very scientific but thats what I tested on so far.

---

### Post by guygong on 2012-05-13
> **guygong said:**
> I did the new installation procedure. It seems to work better but seems like long videos that are anywhere from 9 minutes or longer don't play and it skips through them until it finds a length it can play. I tried reinstalling the gstreamer phonon and got the same results. However, the only difference is that it didn't skip to the next video. It allowed me to manually skip ahead instead. I tested it on video searches of Star Trek Phase 2 and Bicycle Commuting. Videos less than 9 minutes went smoothly while those longer than 9 minutes wouldn't play. Not very scientific but thats what I tested on so far.
Tested some other videos from searches on bike to work day and how stuff works which had some pretty long videos and those did play. Since I've never uploaded a video to youtube before, is there more than one video format flash can play and that is missing from either gstreamer or vlc phonon? I currently can watch any youtube video from VLC.

---

### Post by guygong on 2012-05-23
I just wanted to add that I can watch videos that get skipped by setting up the option to stop at the end of the video option so that it doesn't start playing the next video. It would be nice to have as a default function versus something the user has to set.

---

### Post by sunson565 on 2012-07-01
Hello
I tried the fix by [mc4man]("http://ubuntuforums.org/member.php?u=320715"), on ubuntu 12.04 precise, it didn't work for me, always the same cannt install package
I'm totally new to ubuntu, Idon't know if I'm missing something obvious.
someone have any suggestions for me
thx 
(I have of course googled the problem but didn't find a solution yet)
```
(Reading database ... 100% (Reading database ... 194684 files and directories currently installed.) 
Unpacking libwildmidi-config (from .../libwildmidi-config_0.2.3.4-2.1_all.deb) ... 
dpkg: error processing /var/cache/apt/archives/libwildmidi-config_0.2.3.4-2.1_all.deb (--unpack): 
 trying to overwrite '/etc/wildmidi/wildmidi.cfg', which is also in package libwildmidi0 0.2.2-3 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 /var/cache/apt/archives/libwildmidi-config_0.2.3.4-2.1_all.deb 
dpkg: dependency problems prevent configuration of libwildmidi1: 
 libwildmidi1 depends on libwildmidi-config; however: 
  Package libwildmidi-config is not installed. 
dpkg: error processing libwildmidi1 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of gstreamer0.10-plugins-bad: 
 gstreamer0.10-plugins-bad depends on libwildmidi1 (>= 0.2.3); however: 
  Package libwildmidi1 is not configured yet. 
dpkg: error processing gstreamer0.10-plugins-bad (--configure): 
 dependency problems - leaving unconfigured
```

---

### Post by mc4man on 2012-07-01
> **sunson565 said:**
> Hello
I tried the fix by [mc4man]("http://ubuntuforums.org/member.php?u=320715"), on ubuntu 12.04 precise, it didn't work for me, always the same cannt install package
I'm totally new to ubuntu, Idon't know if I'm missing something obvious.
someone have any suggestions for me
thx 
(I have of course googled the problem but didn't find a solution yet)
```
(Reading database ... 100% (Reading database ... 194684 files and directories currently installed.) 
Unpacking libwildmidi-config (from .../libwildmidi-config_0.2.3.4-2.1_all.deb) ... 
dpkg: error processing /var/cache/apt/archives/libwildmidi-config_0.2.3.4-2.1_all.deb (--unpack): 
 [COLOR="Blue"]trying to overwrite '/etc/wildmidi/wildmidi.cfg', which is also in package[/COLOR] [COLOR="Red"]libwildmidi0 0.2.2-3[/COLOR] 

```

You must have upgraded to 12.04 from either lucid or maverick, that is not the version being used in 12.04, it's now libwildmidi[COLOR="Red"]1[/COLOR] (0.2.3.4-2.1
You could try - open a terminal, copy & paste, press enter
```
sudo apt-get purge libwildmidi*
```

Followed by
```
sudo apt-get update && sudo apt-get install gstreamer0.10-plugins-bad
```


As far as what you  were doing relative to this thread you didn't mention, there were 2 workarounds in here

(myself have just gone ahead & fixed the  gstreamer0.10-plugins-bad plugin so it decodes all video's, the bug on that is active & totally ignored

Take care of the libwildmidi issue & then proceed or ask further

---

### Post by sunson565 on 2012-07-02
[mc4man]("http://ubuntuforums.org/member.php?u=320715") : 
Actually I installed 12.04, it is my first experience with Ubuntu no Upgrade ! 
However thank you very much, this worked smoothly !

---

### Post by mc4man on 2012-07-02
> **sunson565 said:**
> [mc4man]("http://ubuntuforums.org/member.php?u=320715") : 
Actually I installed 12.04, it is my first experience with Ubuntu no Upgrade ! 
However thank you very much, this worked smoothly !

How you ended up with libwildmidi0 0.2.2-3 in a new 12.04 install is a bit of a mystery, currently it's not available except in lucid @ - 0.2.2-2
Starting in 11.04 it was changed to 0.2.3.2-2 as libwildmidi1 

Very odd!

---

### Post by sunson565 on 2012-07-02
mmm, honestly I have no Idea !

---

### Post by cppdeveloper on 2012-09-01
The issue is not solved, why is the title saying "solved"?

I have clean installed Ubuntu 12.04.1 32-bit, have installed all package updates, and the issue remains.

Only when I manually installed gstreamer-bad version 0.10.23, the issue was fixed.


Here is what I posted at the bug report:

[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014/comments/57](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014/comments/57)

---

### Post by mc4man on 2012-09-01
> **cppdeveloper said:**
> The issue is not solved, why is the title saying "solved"?

I have clean installed Ubuntu 12.04.1 32-bit, have installed all package updates, and the issue remains.

Only when I manually installed gstreamer-bad version 0.10.23, the issue was fixed.


Here is what I posted at the bug report:

[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014/comments/57](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014/comments/57)

It's been solved to the OP's satisfaction which was to get a working minitube with these type files.
Additionally a proper fix wasn't committed until 5/16, a couple of weeks after this thread..

As far as using gstreamer-bad version 0.10.23 release, (Feb 21), it's as broken in this regard as ubuntu's .22 version
(that's why there is also a Debian bug filed, Debian is using the .23 release + some opus patches

> 1. I uninstalled the packages:

gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
libgstreamer-plugins-bad0.10-0
You could have stopped right there because that's basically all you've done
(the bad plugin is not needed to decode these files, but when the currently broken .22/.23 releases are installed, (properly), the plugin becomes a blocker

---

### Post by cppdeveloper on 2012-09-01
> **mc4man said:**
> It's been solved to the OP's satisfaction which was to get a working minitube with these type files.
Additionally a proper fix wasn't committed until 5/16, a couple of weeks after this thread..

As far as using gstreamer-bad version 0.10.23 release, (Feb 21), it's as broken in this regard as ubuntu's .22 version
(that's why there is also a Debian bug filed, Debian is using the .23 release + some opus patches

You could have stopped right there because that's basically all you've done
(the bad plugin is not needed to decode these files, but when the currently broken .22/.23 releases are installed, (properly), the plugin becomes a blocker

Thank you for your reply.

After removing Ubuntu 12.04.1's gstreamer bad 0.10.22 packages, and installing gstreamer bad 0.10.23 from its sources, all my mp4 files that were not playing in Totem and Banshee, play normally here.

This is what I wrote in the bug report (Comment #57): [https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014)


So the gstreamer bad 0.10.23 plugin version is not becoming a blocker when installed from its source; at least for my mp4 files that experience the issue.

The source file is: [http://gstreamer.freedesktop.org/src/gst-plugins-bad/gst-plugins-bad-0.10.23.tar.xz](http://gstreamer.freedesktop.org/src/gst-plugins-bad/gst-plugins-bad-0.10.23.tar.xz)


Another approach can be, Ubuntu 12.04/12.10 providing Ubuntu 11.10's gstreamer bad plugin version, that works OK.

---

### Post by mc4man on 2012-09-01
> at least for my mp4 files that experience the issue.

Maybe not the ones the bug was referring to?
What does this return, may have to install gstreamer-tools
```
gst-inspect |grep videoparsersbad
```

---

### Post by cppdeveloper on 2012-09-01
> **mc4man said:**
> Maybe not the ones the bug was referring to?
What does this return, may have to install gstreamer-tools
```
gst-inspect |grep videoparsersbad
```

After installing the gstreamer bad 0.10.23 manually, the command you mentioned returns nothing.

Also the command:
```

root@ioannis-VirtualBox:~# gst-inspect |grep -i videoparser

```

returns nothing.

---

### Post by mc4man on 2012-09-01
> **cppdeveloper said:**
> After installing the gstreamer bad 0.10.23 manually, the command you mentioned returns nothing.

Also the command:
```

root@ioannis-VirtualBox:~# gst-inspect |grep -i videoparser

```

returns nothing.
That means while you've installed .23 it's not in a location that it will be used.
This has the effect of 'fixing' your playback issues by not having the parser plugin available.
Many of the bad plugins are a bit obscure, some are useful depending on use case.
This is what is normally returned
> $gst-inspect |grep videoparsersbad
videoparsersbad:  h263parse: H.263 parser
videoparsersbad:  h264parse: H.264 parser
videoparsersbad:  diracparse: Dirac parser
videoparsersbad:  mpegvideoparse: MPEG video elementary stream parser
videoparsersbad:  mpeg4videoparse: MPEG 4 video elementary stream parser

If you were to remove your build then you'd notice no difference.

If interested in keeping an active bad plugin & fixing this I've a simple how-to here for 12.04 
(I've extended the patch for 12.10 to inc. all h264 commits in the .10 branch & enable opus support, haven't posted yet - may not

[http://ubuntuforums.org/showpost.php?p=12118375&postcount=6](http://ubuntuforums.org/showpost.php?p=12118375&postcount=6)

i don't see Ubuntu fixing 12.04 or even 12.10. When Ubuntu moves to gstreamer1.0 then this won't be an issue as the 1.0 branch was fixed at the same time as the .10 one last May 15

---

### Post by cppdeveloper on 2012-09-01
> **mc4man said:**
> i don't see Ubuntu fixing 12.04 or even 12.10. When Ubuntu moves to gstreamer1.0 then this won't be an issue as the 1.0 branch was fixed at the same time as the .10 one last May 15

Why don't they go back to the gstreamer plugins used in Ubuntu 11.10?

---

### Post by mc4man on 2012-09-02
> **cppdeveloper said:**
> Why don't they go back to the gstreamer plugins used in Ubuntu 11.10?
It is actually the same in 11.10,12.04,12.10, it works in 11.10 but not in 12.04/12.10
For whatever reason Ubuntu hasn't seen fit to update/upgrade the bad plugin source  in over 1 year.
You'll notice in my bug report that not one peep from any Ubuntu dev, bug triage(r), no one.

---

