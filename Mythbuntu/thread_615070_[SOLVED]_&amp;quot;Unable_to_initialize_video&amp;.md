---
title: "[SOLVED] &amp;quot;Unable to initialize video&amp;quot;"
date: 2007-11-16
forum: Mythbuntu
---

### Post by dougsnell on 2007-11-16
I'm trying to get mythbuntu to run on a pvr-350's tv-out (s-video).  Unfortunately, I can't seem to re-direct any video to the port.

Referencing ([https://help.ubuntu.com/community/MythTV_Feisty_hardware_pvr-350_TV-out](https://help.ubuntu.com/community/MythTV_Feisty_hardware_pvr-350_TV-out)),  I hit a brick wall while trying to simply Watch TV.  It comes back with "Unable to initialize video", and won't go any further.  If I plod through and try to make X display on the port, it goes all the way to booting X and then presents an option to reconfigure my graphics card (on my monitor).

I can display the test image on it, and I've verified fb0 and PCI:0:9:0.  Mplayer gives me an error opening/initializing the video_out device (no idea what that means).

I found a similar post ([http://www.backports.ubuntuforums.org/showthread.php?t=583293](http://www.backports.ubuntuforums.org/showthread.php?t=583293)), but a response of "ttt" doesn't mean anything to me.

I'm running a machine which has a PVR-500 card in it, and everything was working fine until I added the 350 and tried to re-direct (output to the onboard video was poor).  I re-built from scratch (didn't have much on there), and still have the same problem.

Also, unchecking the option to put video through the 350's tv-out will re-enable a functional TV ... albeit with poor performance.

-Doug

---

### Post by superm1 on 2007-11-19
> **dougsnell said:**
> I'm trying to get mythbuntu to run on a pvr-350's tv-out (s-video).  Unfortunately, I can't seem to re-direct any video to the port.

Referencing ([https://help.ubuntu.com/community/MythTV_Feisty_hardware_pvr-350_TV-out](https://help.ubuntu.com/community/MythTV_Feisty_hardware_pvr-350_TV-out)),  I hit a brick wall while trying to simply Watch TV.  It comes back with "Unable to initialize video", and won't go any further.  If I plod through and try to make X display on the port, it goes all the way to booting X and then presents an option to reconfigure my graphics card (on my monitor).

I can display the test image on it, and I've verified fb0 and PCI:0:9:0.  Mplayer gives me an error opening/initializing the video_out device (no idea what that means).

I found a similar post ([http://www.backports.ubuntuforums.org/showthread.php?t=583293](http://www.backports.ubuntuforums.org/showthread.php?t=583293)), but a response of "ttt" doesn't mean anything to me.

I'm running a machine which has a PVR-500 card in it, and everything was working fine until I added the 350 and tried to re-direct (output to the onboard video was poor).  I re-built from scratch (didn't have much on there), and still have the same problem.

Also, unchecking the option to put video through the 350's tv-out will re-enable a functional TV ... albeit with poor performance.

-Doug
Yes, use the mythtv package from this ppa:

[https://edge.launchpad.net/~superm1/+archive](https://edge.launchpad.net/~superm1/+archive)

It's referenced in another thread, but *still* hasn't gotten approved into stable release updates.


If it works for you, i've got a bug you need to comment on.

---

### Post by dougsnell on 2007-11-20
I had found a source to add which started with PPA (posted by you, I think ... I can't find it at the moment).  Unfortunately, that source didn't help.  I tried (twice), and both times it always showed up as an update ready to apply (though it appeared to apply properly ... the update icon just stayed orange).  It didn't appear to do anything for the problem, either.

I'll give the link below a show when I get home again tonight.  I'm just curious ... there are a LOT of people with 350s out there.  Are all of them having the same problem?

---

### Post by superm1 on 2007-11-20
> **dougsnell said:**
> I had found a source to add which started with PPA (posted by you, I think ... I can't find it at the moment).  Unfortunately, that source didn't help.  I tried (twice), and both times it always showed up as an update ready to apply (though it appeared to apply properly ... the update icon just stayed orange).  It didn't appear to do anything for the problem, either.

I'll give the link below a show when I get home again tonight.  I'm just curious ... there are a LOT of people with 350s out there.  Are all of them having the same problem?
Activate gutsy-proposed.  It should be coming up there soon.

---

### Post by dougsnell on 2007-11-20
Much appreciated!  To be honest, I'm not sure I'm applying the ppa patch correctly.  I can easily add and wait for the proposed repositories.

---

### Post by dougsnell on 2007-11-25
Just curious ... has the patch been pushed out?  I picked up a bundle of updates, but no luck so far.

---

### Post by superm1 on 2007-11-25
> **dougsnell said:**
> Just curious ... has the patch been pushed out?  I picked up a bundle of updates, but no luck so far.

Yes it is on gutsy proposed. If it works for you on gutsy proposed, please comment on the sru bug. It will hit gutsy updates in about a week after we have enough acks.

---

### Post by dougsnell on 2007-11-28
No ... just confirming that this did not fix the error.  I can turn off the 350 output and it works (though the video card in the machine is horribly choppy).

I do have Gutsy proposed checked off in Synaptec, too.

---

### Post by superm1 on 2007-11-28
Please verify the version numbers of the packages u have installed. You can check by ```
dpkg -l | grep mythtv 
```

---

### Post by dougsnell on 2007-12-01
backend, backend-master, common, database, frontend, and transcode-utils are all 0.20.2+fixes14935-0ubuntu0.

Themes are 0.20-0.1ubuntu1 (I assume that's normal).

(Sorry, I've never figured out how to paste directly from an xterm session.)

---

### Post by superm1 on 2007-12-01
> **dougsnell said:**
> backend, backend-master, common, database, frontend, and transcode-utils are all 0.20.2+fixes14935-0ubuntu0.

Themes are 0.20-0.1ubuntu1 (I assume that's normal).

(Sorry, I've never figured out how to paste directly from an xterm session.)

You don't have the SRU versions.  The versions with the SRU are 0.20.2-0ubuntu10.1

The ones you have are from the weekly builds, which don't necessarily have that patch applied.  I believe we weren't going to add it to the weekly builds until we confirmed the SRU version didn't break for anyone.

---

### Post by dougsnell on 2007-12-03
Hmm.  What'd I miss, then?  I know I checked off gutsy-proposed, and even verified I had all updates before posting.

I'm more concerned with understanding what I did wrong that I'm not getting the updates than I am with the system actually working.  I'm one of those weird people who'd much prefer things not work and have done everything right (and understand what I did), than have no clue and have it working.

---

### Post by dbabe on 2007-12-08
Did this ever get resolved?  I am having the same issue as dougsnell, and have tried all the advice from the previous replies in this post, and I still get "Unable to initialize video" when trying to send TV out of my PVR350 in Mythbuntu.  Any other checks that I can do to see if I am doing anything wrong?  I can see the color bars on my screen when running "/sbin/modprobe saa7127 test_image=1".  Here is my version informaton.  Are my versions the latest and correct ones?

root@mythtv:~# dpkg -l | grep mythtv
ii  mythtv     	0.20.2-0ubuntu10.1         A personal video recorder application (clien
ii  mythtv-backend    0.20.2-0ubuntu10.1    A personal video recorder application (serve
ii  mythtv-backend-master   0.20.2-0ubuntu10.1  Metapackage to setup and configure a "Master
ii  mythtv-common  0.20.2-0ubuntu10.1    A personal video recorder application (commo
ii  mythtv-database    0.20.2-0ubuntu10.1   A personal video recorder application (datab
ii  mythtv-frontend    0.20.2-0ubuntu10.1     A personal video recorder application (clien
ii  mythtv-theme-mythbuntu   0.20071015~ppa2    default MythTV theme used in Mythbuntu
ii  mythtv-themes   0.20-0.1ubuntu1                      Additional themes for MythTV
ii  mythtv-transcode-utils    0.20.2-0ubuntu10.1       Utilities used for transcoding MythTV tasks

Thanks for any help you can provide.  I spent a lot of time over the past couple of weeks learning to setup myth, starting over with a new Hard Drive after barbequing my storage drive, and getting LIRC configured so that everything works, including PC shutdown with the remote.  This is the final hurdle before I can come out of testing and go into the living room on a real TV.  Thanks!

---

### Post by rodea99 on 2007-12-10
Hi. I believe I'm experiencing this same problem. I've just upgraded to Gutsy Mythbuntu I installed superm1's PPA and have:

dpkg -l | grep mythtv
ii  mythtv                                        0.20.2-0ubuntu10.1
ii  mythtv-backend                         0.20.2-0ubuntu10.1 
ii  mythtv-backend-master            0.20.2-0ubuntu10.1
</pre>
and 

ii  xserver-xorg-video-ivtv             1.0.0~svn4049-3~ppa3

but when I start X I get the following:

(EE) IVTV(0): FBIOPUT_VSCREENINFO: Invalid argument
(EE) IVTV(0): Mode init failed

I've attached my xorg.conf file.
Any help appreciated.
Robert.

---

### Post by dbabe on 2007-12-10
So what is the root cause of this?  Is this a problem with the IVTV driver?  I am relatively new to Linux (3 years off and on) and still learning the interelationship of all the pieces.  Has the TV out function on the PVR350 card historically always worked well in Linux, or is this something that broke recently?  Bottom line is that I am trying to get a feel for how pervasive of a problem this is, how many people it affects, and how likely it is to be fixed quickly.  I realize that the guys like superm1 do this work on their own time to benefit the rest of us, and for that I am very grateful.  Does anyone know if a distribution different than Mythbuntu would correct this problem?  Need to know more, so I can decide if the best course of action is to not expect to use TV out, and maybe get a new video card with TV out.  Thanks for any background that any of you can provide.

---

### Post by superm1 on 2007-12-10
here is the basic jist of the situation.

When gutsy was released, no one had yet tested the pvr 350 output.  There are two issues that were then discovered. The first is that you need to install the xorg driver. That package is available on the ppa. The next issues is that the pvr 350 api changed within mythtv. You need to install the package on gutsy proposed to get around this issue. Eventually this package will be copied over to gutsy updates.  If you are not getting it to work after using the package on gutsy proposed, and installing the x driver from the ppa, then you are configuring it incorrectly. 

With this all being said, for the 8.04 version, there will be a method to configure tv out for thepvr350 directly within the installer.

---

### Post by dbabe on 2007-12-11
Remember, although I am not a total newb, I am still learning Linux.  So in Synaptic, under the "Updates" tab, I checked "Pre-released updates (gutsy proposed)".  Then I went to my /etc/apt/sources.list in Terminal and manually added the following two lines at the end of the Sources.list file:

deb [http://ppa.launchpad.net/superm1/ubuntu](http://ppa.launchpad.net/superm1/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/superm1/ubuntu](http://ppa.launchpad.net/superm1/ubuntu) gutsy main

I then clicked on the orange update notify icon near the clock to let Synaptic run updates.  After that I enabled "PVR350 TV Out" in Mythtv setup. Even after running updates, I still get the orange update notification icon, and in the "Update Manager" window in Synaptic, it always says "You can install 1 update" and always shows "linux-ubuntu-modules-2.6.22-14 generic" with a checkbox next to it.  This never goes away even after running update again, or running apt-get update from console.  Am I just missing something easy here?  It sounds like everything is already fixed and I am just applying the update wrong?  :confused: I am not too proud to be corrected by someone with more experience if I am making beginner errors.  I am determined to move away from Windows and be self sufficient in Linux.  Thanks again for all the help.

---

### Post by dbabe on 2007-12-16
Can anyone else answer my questions, above?  TV Out is still not working and I get "Unable to initialize video" in MythTV when trying to go to the TV.  I am totally new to MythTV.  How do I verify that I have all the right versions of packages installed?  If all my packages are correct, does anyone have a current procedure on any other configuration that I need to do?  I know that there are others out there that do not have this working yet, and probably others that have it figured out.  Thanks.

---

### Post by rodea99 on 2007-12-18
Just wanted to update the list and say that I applied superm1s ppa and now have a working mythbuntu with TV out and GUI being displayed using a PVR 350. Back to where I was with Feisty, basically. 

dbabe, I'm certainly no expert but I ran:
apt-get update 
apt-get upgrade
to install the various patches (having modified my source.list file to include superm1's ppa and gutsy proposed)

I then corrected a number of problems in my xorg.conf. One of these was a change in driver name from ivtvdev to ivtv. The other was an invalid mode line (which I think I got away with in the previous version).

Robert.

---

### Post by barryf on 2007-12-19
Any chance you could post your xorg.conf ?

Thanks

-Barry

---

### Post by dbabe on 2007-12-19
Thanks, rodea99 and barryf for jumping in to help.  Here is my Xorg.config.  Do I need to do any edits to Xorg just to view TV out, not any X output?  That has been my initial test, just to see if the patches are applied correctly.  My approach has been, once I can successfully send the TV image from Myth out to the TV, then I can start working on a full X session out to TV.  Let me know if that is the wrong approach.  Also, my previous posts have version number detail, in case you want to verify that the patches applied correctly.  Thanks,

Dan.

---

### Post by andrewb78 on 2007-12-20
> **dbabe said:**
> Thanks, rodea99 and barryf for jumping in to help.  Here is my Xorg.config.  Do I need to do any edits to Xorg just to view TV out, not any X output?  That has been my initial test, just to see if the patches are applied correctly.  My approach has been, once I can successfully send the TV image from Myth out to the TV, then I can start working on a full X session out to TV.  Let me know if that is the wrong approach.  Also, my previous posts have version number detail, in case you want to verify that the patches applied correctly.  Thanks,

Dan.

Just to make your card is set up correctly and everything, try

```
cat something.mpg > /dev/video16
```

in a terminal window (of course, use some actual mpg file in place of something.mpg).  That worked for me even when I was having this problem with Myth.

Assuming that works, there seems to be a bug regarding PVR-350 TV Out in the main Mythbuntu distribution.  Thanks to another thread (and superm1), I added

```
deb http://ppa.launchpad.net/superm1/ubuntu gutsy main
```

to my /etc/apt/sources.list, then did

```
sudo aptitude update && sudo aptitude safe-upgrade
```

from a terminal window.  I may have had to restart mythfrontend as well.  The updates seem to solve the PVR-350 TV Out problem for me.

As far as getting X output on the TV, there are instructions at [https://help.ubuntu.com/community/MythTV_Feisty_hardware_pvr-350_TV-out](https://help.ubuntu.com/community/MythTV_Feisty_hardware_pvr-350_TV-out) that worked quite well for me.  Getting this output is necessary if you want to be able to control the Mythbuntu box entirely on the TV screen.

---

### Post by superm1 on 2007-12-20
> **andrewb78 said:**
> Just to make your card is set up correctly and everything, try

```
cat something.mpg > /dev/video16
```in a terminal window (of course, use some actual mpg file in place of something.mpg).  That worked for me even when I was having this problem with Myth.

Assuming that works, there seems to be a bug regarding PVR-350 TV Out in the main Mythbuntu distribution.  Thanks to another thread (and superm1), I added

```
deb http://ppa.launchpad.net/superm1/ubuntu gutsy main
```to my /etc/apt/sources.list, then did

```
sudo aptitude update && sudo aptitude safe-upgrade
```from a terminal window.  I may have had to restart mythfrontend as well.  The updates seem to solve the PVR-350 TV Out problem for me.

As far as getting X output on the TV, there are instructions at [https://help.ubuntu.com/community/MythTV_Feisty_hardware_pvr-350_TV-out](https://help.ubuntu.com/community/MythTV_Feisty_hardware_pvr-350_TV-out) that worked quite well for me.  Getting this output is necessary if you want to be able to control the Mythbuntu box entirely on the TV screen.
Andrew,
Would you be interested in writing every step that you had to go through on a wiki page?  I think it would go very far as to help people suffering issues in this thread.  It is always really useful to have a single page to refer to rather than a 15 page thread here, an outdated wiki there, a ppa that might work here, etc.

Thanks!

---

### Post by andrewb78 on 2007-12-20
> **superm1 said:**
> Andrew,
Would you be interested in writing every step that you had to go through on a wiki page?  I think it would go very far as to help people suffering issues in this thread.  It is always really useful to have a single page to refer to rather than a 15 page thread here, an outdated wiki there, a ppa that might work here, etc.

Thanks!

Sure.  Any suggestions on where?  I'm quite new to Ubuntu -- the box I'm using is actually one I have built for my girlfriend for Christmas -- so I don't know where the preferred place for such documentation would be.

---

### Post by superm1 on 2007-12-20
> **andrewb78 said:**
> Sure.  Any suggestions on where?  I'm quite new to Ubuntu -- the box I'm using is actually one I have built for my girlfriend for Christmas -- so I don't know where the preferred place for such documentation would be.
This page would be great:

[https://help.ubuntu.com/community/MythTV_Gutsy_hardware_pvr-350_TV-out](https://help.ubuntu.com/community/MythTV_Gutsy_hardware_pvr-350_TV-out)

Perhaps, copy the source of the feisty page to there for a basis, and then make the necessary modifications.

Thanks!

---

### Post by dbabe on 2007-12-20
andrewb78:  I think we are getting somewhere now, at least in determining what pieces are NOT functioning on my system so far.  I cat'd the Mythtv intro .mpg per your instructions above, and all I see is ASCII characters scroll by in the Terminal window NOT on the TV display.  
   Also, if I do:

/sbin/rmmod saa7127
/sbin/modprobe saa7127 test_image=1

I can see the old color bar test pattern on my TV screen.  According to one of the "How to's" that I read, this means that the cable and driver are working.  What would be the next step in the testing tree, knowing that I cannot cat a video to the TV screen?  
   Finally, I have a ton of internal notes on what I have done so far.  Once I get things working, I am certainly willing to condense those into a readable outline, in reference to Mario's recomendation that WIKI text be created.  Some of the more experienced guys would have to proof it for accuracy, but I can do the hand work.  Thanks,

Dan.

*****Revisions, below******

Sorry guys, I made a typo in terminal and need to post one revision here:

In my haste I first typed:

cat intro.mpg /dev/video16
This gave me the ASCII output to terminal. I missed the ">" after file name. 

Then I did:

cat intro.mpg > /dev/video16
and the result was NO video going to the TV, and NO ASCII text scrolling in terminal.

---

### Post by superm1 on 2007-12-20
> **dbabe said:**
> andrewb78:  I think we are getting somewhere now, at least in determining what pieces are NOT functioning on my system so far.  I cat'd the Mythtv intro .mpg per your instructions above, and all I see is ASCII characters scroll by in the Terminal window NOT on the TV display.  
   Also, if I do:

/sbin/rmmod saa7127
/sbin/modprobe saa7127 test_image=1

I can see the old color bar test pattern on my TV screen.  According to one of the "How to's" that I read, this means that the cable and driver are working.  What would be the next step in the testing tree, knowing that I cannot cat a video to the TV screen?  
   Finally, I have a ton of internal notes on what I have done so far.  Once I get things working, I am certainly willing to condense those into a readable outline, in reference to Mario's recomendation that WIKI text be created.  Some of the more experienced guys would have to proof it for accuracy, but I can do the hand work.  Thanks,

Dan.
I wish I had some of this hardware to help nail this process for you guys :)  Once the wiki page outlining the entire correct process is in order, I'll do some work to try to automate as much of this as I can for the hardy installer.

---

### Post by dbabe on 2007-12-20
Sorry guys, I made a typo in terminal and need to post one revision here:

In my haste I first typed:

cat intro.mpg /dev/video16
This gave me the ASCII output to terminal.  I missed the ">" after file name.  

Then I did:

cat intro.mpg > /dev/video16
and the result was NO video going to the TV, and NO ASCII text scrolling in terminal.

---

### Post by andrewb78 on 2007-12-20
Do you know what kind of mpg file you used (as in, MPEG-2 or MPEG-4)?  That might make a difference because, if I understand correctly, the hardware decoder only decodes MPEG-2.  Could you try using a mpg file out of your recordings directory that you think was recorded through the TV input on the PVR-350?

---

### Post by dbabe on 2007-12-20
Good call.  Although my test file was .mpg, it was probably mpeg4.  Found a known good file from my recordings, and it DOES cat to the TV properly.  Moving onto the next troubleshooting items in your earlier post, and will advise of results in a couple of minutes.  Thanks:)

---

### Post by dbabe on 2007-12-20
OK, I went through all the steps that you outlined in post #22,  enabled PVR350 out in Myth, and still get "Unable to initialize video" when going to watch Live TV in Myth.  
   Also, Synaptic is still showing that I can install one update, "linux-ubuntu-modules-2.6.22-14-generic" but this update never actually installs, no matter how many times I check "Install updates".  A couple of others have posted with this same condition, although I don't know if it specifically relates to this problem.  
   Do you have any other checks or procedures for me to try, to get closer to isolating what I am missing?  This is progress.  Now I know that all my hardware is good.  Thanks again for the help.

P.S.  Remember that I am pretty new at this and could be missing a step that is obvious to someone more experienced in Linux administration and configuration.

---

### Post by superm1 on 2007-12-20
> **dbabe said:**
> OK, I went through all the steps that you outlined in post #22,  enabled PVR350 out in Myth, and still get "Unable to initialize video" when going to watch Live TV in Myth.  
   Also, Synaptic is still showing that I can install one update, "linux-ubuntu-modules-2.6.22-14-generic" but this update never actually installs, no matter how many times I check "Install updates".  A couple of others have posted with this same condition, although I don't know if it specifically relates to this problem.  
   Do you have any other checks or procedures for me to try, to get closer to isolating what I am missing?  This is progress.  Now I know that all my hardware is good.  Thanks again for the help.
I can comment here.  This is a known issue with the PPAs.  Some packages will continually try to reinstall themselves.  Once you've installed it the first time, it is installed.

---

### Post by dbabe on 2007-12-20
So the warning to install that module is both benign (doesn't hurt anything) and is also unrelated to the "Unable to initialize video" issue?  If so, I will avoid mentioning it in documentation or future posts.  Let me know.  Thanks :)

---

### Post by superm1 on 2007-12-20
> **dbabe said:**
> So the warning to install that module is both benign (doesn't hurt anything) and is also unrelated to the "Unable to initialize video" issue?  If so, I will avoid mentioning it in documentation or future posts.  Let me know.  Thanks :)
For the curious, here is the bug: [https://bugs.edge.launchpad.net/soyuz/+bug/165230](https://bugs.edge.launchpad.net/soyuz/+bug/165230)

It causes multiple PPA packages to do this.  The warning to reinstall over and over will not do anything to hurt here.  It also should not be related to unable to initialize video.

---

### Post by superm1 on 2007-12-20
While we are here:

People who got it working from the PPA (or gutsy-proposed), please add a comment to this bug:
[https://bugs.edge.launchpad.net/ubuntu/gutsy/+source/mythtv/+bug/158562](https://bugs.edge.launchpad.net/ubuntu/gutsy/+source/mythtv/+bug/158562)

If you don't have it working yet, please hold off until you do before commenting.

---

### Post by andrewb78 on 2007-12-20
I have added a Gutsy HOWTO:

[https://help.ubuntu.com/community/MythTV_Gutsy_hardware_pvr-350_TV-out](https://help.ubuntu.com/community/MythTV_Gutsy_hardware_pvr-350_TV-out)

I make no claims of correctness, so feel free to change anything to improve accuracy, usefulness, and completeness.

---

### Post by superm1 on 2007-12-20
> **andrewb78 said:**
> I have added a Gutsy HOWTO:

[https://help.ubuntu.com/community/MythTV_Gutsy_hardware_pvr-350_TV-out](https://help.ubuntu.com/community/MythTV_Gutsy_hardware_pvr-350_TV-out)

I make no claims of correctness, so feel free to change anything to improve accuracy, usefulness, and completeness.
One thing.

Please do not mix and match debian repositories and ubuntu.  They are source compatible but not binary compatible.

---

### Post by andrewb78 on 2007-12-21
> **superm1 said:**
> One thing.

Please do not mix and match debian repositories and ubuntu.  They are source compatible but not binary compatible.

Good to know!  That happens to be straight out of the Feisty howto, though.  Is there a replacement for the ivtv driver in xorg in Gutsy?

---

### Post by superm1 on 2007-12-21
> **andrewb78 said:**
> Good to know!  That happens to be straight out of the Feisty howto, though.  Is there a replacement for the ivtv driver in xorg in Gutsy?
Yes, it's on that PPA of mine.

---

### Post by dbabe on 2007-12-21
andrewb78 is the hero of the day.  :KS  The ivtv module was not loading automatically.  The following part of his proposed WIKI fixed it for me:

[I]To make sure that the ivtv-fb module loads without errors, in a terminal window, do 

lsmod | grep ivtv_fb
to see whether the module is loaded. If there is no output from the command, the module is not loaded. In this case, execute 

sudo modprobe ivtv_fb[/I]


After adding the ivtv_fb line to /etc/modules, my TV out now works.  Now I can proceed with working on the "X" session out.  It is very likely that this detail is what is stopping video out for the others that have installed superm1's update.  
   Thanks again superm1, andrewb78 and others that have put forth effort towards the solution.

Dan.

---

### Post by andrewb78 on 2007-12-21
superm1:

OK, then, I got rid of the Debian repository info.  I looked at your PPA repository and realized that I actually downloaded the package straight from there and installed with dpkg -i anyway.  I guess the short-term memory wasn't so good. :)

dbabe:

Thanks, I try. :)  Let me know if you run into any other problems.

---

### Post by dougsnell on 2007-12-21
dbabe ... nice find :)  That did indeed do the trick.

Thanks for all the help,superm1!

I may have other questions/issues ... but loading ivtv_fb definitely takes care of the initialization problem.

---

### Post by dougsnell on 2007-12-21
OK ... I spoke a little too soon.  While sudo modprobe ivtv_fb gets TV-out working, simply adding ivtv_fb to /etc/modules doesn't get it working during boot (digging around Google, adding ivtv didn't help, either).  At first I assumed my xorg.conf was wrong, but lsmod | grep ivtv_fb shows nothing immediately post-boot.  I have to manually run sudo modprobe ivtv_fb each time after boot.

Plus, I can't configure X to run on the TV until ivtv_fb is working.

So ... what exactly did you add to your /etc/modules, or where do I start looking to figure out what may be different for me?

> **dbabe said:**
> andrewb78 is the hero of the day.  :KS  The ivtv module was not loading automatically.  The following part of his proposed WIKI fixed it for me:

[I]To make sure that the ivtv-fb module loads without errors, in a terminal window, do 

lsmod | grep ivtv_fb
to see whether the module is loaded. If there is no output from the command, the module is not loaded. In this case, execute 

sudo modprobe ivtv_fb[/I]


After adding the ivtv_fb line to /etc/modules, my TV out now works.  Now I can proceed with working on the "X" session out.  It is very likely that this detail is what is stopping video out for the others that have installed superm1's update.  
   Thanks again superm1, andrewb78 and others that have put forth effort towards the solution.

Dan.

---

### Post by superm1 on 2007-12-21
> **dougsnell said:**
> OK ... I spoke a little too soon.  While sudo modprobe ivtv_fb gets TV-out working, simply adding ivtv_fb to /etc/modules doesn't get it working during boot (digging around Google, adding ivtv didn't help, either).  At first I assumed my xorg.conf was wrong, but lsmod | grep ivtv_fb shows nothing immediately post-boot.  I have to manually run sudo modprobe ivtv_fb each time after boot.

Plus, I can't configure X to run on the TV until ivtv_fb is working.

So ... what exactly did you add to your /etc/modules, or where do I start looking to figure out what may be different for me?
Try adding ivtv-fb instead.

---

### Post by dougsnell on 2007-12-21
I made a few changes and it's working ... but wasn't sure what I had done that all of a sudden it started loading.  It was betwen ivtv-fb and adding "http://ftp.de.debian.org/debian etch main contrib".

X still isn't displaying for me on my TV.  My TV flickers during boot, and my xorg.conf is attached (if it helps anyone).  But essentially the TV displays once booted ... but I can't see the myth front end without my monitor being hooked up.

Also ... do I need the "debian.org/debian etch main contrib"?  I wound up reading it loads the ivtvdev driver, but wasn't sure if the newer version of myth actually needs that (pulled that info off the Feisty howto).

> **superm1 said:**
> Try adding ivtv-fb instead.

---

### Post by superm1 on 2007-12-21
> **dougsnell said:**
> I made a few changes and it's working ... but wasn't sure what I had done that all of a sudden it started loading.  It was betwen ivtv-fb and adding "http://ftp.de.debian.org/debian etch main contrib".

X still isn't displaying for me on my TV.  My TV flickers during boot, and my xorg.conf is attached (if it helps anyone).  But essentially the TV displays once booted ... but I can't see the myth front end without my monitor being hooked up.

Also ... do I need the "debian.org/debian etch main contrib"?  I wound up reading it loads the ivtvdev driver, but wasn't sure if the newer version of myth actually needs that (pulled that info off the Feisty howto).
**Please** don't add debian repositories.  You are in for more trouble than you are bargaining for.

debian and Ubuntu are **NOT** binary compatible for all applications.  This means that if you mix and match deb's that even if one or two works, there are literally hundreds that won't.  They will cause you more trouble down the road.

---

### Post by dougsnell on 2007-12-21
Noted and removed ... though the only thing it pulled down was ivtvdev.

---

### Post by andrewb78 on 2007-12-22
I changed the xorg.conf in the Gutsy HOWTO to reflect that the Driver is "ivtv" not "ivtvdev".  I had neglected to change that from the Feisty HOWTO.  Hopefully, that will end some confusion there.

Also, you don't need the Debian repository to get the ivtv driver.  superm1 has it on his ppa, and I go through how to install it on the Gutsy HOWTO page.

For Google completeness:

[https://help.ubuntu.com/community/MythTV_Gutsy_hardware_pvr-350_TV-out](https://help.ubuntu.com/community/MythTV_Gutsy_hardware_pvr-350_TV-out)

---

### Post by dougsnell on 2007-12-22
> **andrewb78 said:**
> I changed the xorg.conf in the Gutsy HOWTO to reflect that the Driver is "ivtv" not "ivtvdev".  I had neglected to change that from the Feisty HOWTO.  Hopefully, that will end some confusion there.

Also, you don't need the Debian repository to get the ivtv driver.  superm1 has it on his ppa, and I go through how to install it on the Gutsy HOWTO page.

For Google completeness:

[https://help.ubuntu.com/community/MythTV_Gutsy_hardware_pvr-350_TV-out](https://help.ubuntu.com/community/MythTV_Gutsy_hardware_pvr-350_TV-out)

Your comment on the other thread regarding the howto recently going up was the key for me.  The Gutsy howto has everything I was looking for but couldn't figure out on my own.

I greatly appreciate everyone's help.  It's amazing how for a few weeks I've been trying to get everything working, and it all came together within a few hours of getting the right pieces :)  Much thanks to everyone!

---

### Post by musiseb on 2008-11-14
Hi.

I have the same problem. I'm getting a message "Unable to initialize video".
I have a PVR-350 card. I did follow the HOWTO on Gutsy. All the checks I run work fine. 

When I run the command

cat Silhouet2001.mpeg > /dev/video16

I can see a video on my TV out with a big black box on top. 
I did add "deb [http://ppa.launchpad.net/superm1/ubuntu](http://ppa.launchpad.net/superm1/ubuntu) hardy main" to my sources.list file and I run a command:

$ sudo aptitude update && sudo aptitude safe-upgrade

This did not solve the problem. Is there something else I'm missing? I can watch TV when I turn off the PVR-350 hardware output in the Myth Setup, however the output has very poor quality.
I would appreciate all your help. Thanks.

---

### Post by jonkirian on 2009-04-07
> **superm1 said:**
> here is the basic jist of the situation.

When gutsy was released, no one had yet tested the pvr 350 output.  There are two issues that were then discovered. The first is that you need to install the xorg driver. That package is available on the ppa. The next issues is that the pvr 350 api changed within mythtv. You need to install the package on gutsy proposed to get around this issue. Eventually this package will be copied over to gutsy updates.  If you are not getting it to work after using the package on gutsy proposed, and installing the x driver from the ppa, then you are configuring it incorrectly. 

With this all being said, for the 8.04 version, there will be a method to configure tv out for thepvr350 directly within the installer.
just curious if this issue has reoccurred in 8.10 as of recent. i had built my myth box w/ 8.10 a few weeks ago w/o issue, but when i tried rebuilding it this weekend (wanted to change filesystem layout) w/ ubuntu 8.10 & mythbuntu 8.10 i'm getting "unable to initialize video".

i've added the following repos, but still no dice.

deb [http://ppa.launchpad.net/superm1/ubuntu](http://ppa.launchpad.net/superm1/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/superm1/ubuntu](http://ppa.launchpad.net/superm1/ubuntu) intrepid main

any help would be much appreciated!

---

### Post by jonkirian on 2009-04-07
quick update. i re-tested w/ mythbundu 8.04 and it worked w/o issue. my guess is the old issue has reoccurred and likely needs the prev fix applied to the new code...

still, any updates / replies would be cool.

thnx

jon

---

