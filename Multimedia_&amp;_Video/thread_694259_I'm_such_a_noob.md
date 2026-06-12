---
title: "I'm such a noob"
date: 2008-02-11
forum: Multimedia &amp; Video
---

### Post by otheracco on 2008-02-11
I'm confused about the 2 billion different repositories and the 1 billion of those that are down.

I'm follow the guide here [http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833) to get all of my media working (especially wma lossless audio) but I'm running into 'package not found' or something similar on gstreamer0.10-pitfdll.

Plus, there's all these different types of repositories, like universe, multiverse, bad, ugly, main is pretty obvious, but all the others too.  Phew, I've really been babied by Windows.

Another thing is I see in my sources.list two entries for each repository, like deb [http://rep.com](http://rep.com) and deb-src [http://rep.com](http://rep.com).

Anyway, how do you people keep up with all of this and what repository should I put in synaptic to get this file?

---

### Post by cozmicharlie on 2008-02-11
It can be confusing but you may be making it more difficult then needed.  You don't need every repository.  For multimedia the main repository to add is the medibuntu repository [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu).  Since you are new I assume you have Gutsy so follow the instructions for adding the Medibuntu repository. These should give you all the packages you need for multimedia.  Follow these steps below and it should get your multimedia working.
[LIST=1]
[*]Install the medibuntu repository.
[*]Also make sure you have all the other repositories open.  Open Synaptic and in the menu go to setting>repository - check all the repositories under "Ubuntu Software" (I uncheck the ones from the cd), "Third Party Software" and check under "Updates" and make sure they are checked (I don't put checks in pre-release or unsupported updates).  Make sure you reload.
[*]In Synaptic install a package called "Build Essential".  
[*]Close Synaptic and open Add/Remove" from the Applications menu.  Click "All" in the left column then search for Ubuntu Restricted Extras" and install them.  This contains most of the packages you need for multimedia.
[/LIST]
You can double check in Synaptic and make sure you have all the gstreamer-10 (good, bad, ugly) installed.  They should be when you install the Ubuntu Restricted Extras.  You may need additional codecs depending on what you do - most can be found in Synaptic by searching.

Don't worry about installing other repositories until you need them.  Hopefully this will also clean up your sourcelist.

---

### Post by johnn1949 on 2008-02-11
Have you tried this page for your version of ubuntu.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

I got gutsy working with this command.

sudo apt-get install ubuntu-restricted-extras

I'm not sure if I have wma or not though.

---

### Post by otheracco on 2008-02-12
John, I already tried that guide and it doesn't allow wma files.

cozmicharlie, I actually already tried the restricted-extras package and it didn't help with wma.
Right now I just followed your link and was able to install a w64codecs package which sounds like it should work, but I'm still unable to play wma through beep, listen, and audacious.

I'm still not able to find the  gstreamer0.10-pitfdll package in there.  and I'm not really sure which good, bad, and ugly gstreamer packages to use.  I see so many different ones, 

I attached my synaptics screenshots.
Do I have to configure the apps to point somewhere to use all these packages?

---

### Post by cozmicharlie on 2008-02-12
I don't have time now to look through your gstreamer but it appears you have most of the ones you need.  I will look it over in more detail tonight.  For now try this.

Install ffmpeg and gstreamer-ffmpeg from Synaptic and check to see if that works.

Also, since you are using Audacious - install the audacious plug ins.  They are in the multimedia Universe repos.

Let us know if that works

---

### Post by cozmicharlie on 2008-02-12
FYI - I have attached my Synaptic screenshot so you can see what gstreamer plug ins I have.  I am able to play wma.

---

### Post by otheracco on 2008-02-12
Ugh, I've tried it all and I still can't play wma's.  I installed everything you have in your screenshots, ffmpeg, and gstreamer0.10-ffmpeg, and the audacious-ugly plugin and the only thing that's happening now is that I no longer get an error message through audacious when selecting a wma file (so no error, but it still doesn't play).

What I really want to use is 'Listen' though, but I did a search in Synaptic for 'Listen' and the only good match was the app itself.

I know you said install the plugins for audacious and that they're in the mutimedia universe repos, but I'm not sure what one that is, not to mention I don't know what they're called.  Do they start with Audacious?  Do they start with something like lib-audiocious, gstreamer-audacious?  I'm so confused.

I'm sorry to be such a noob.

---

### Post by cozmicharlie on 2008-02-12
Not sure why it is not working for you.  Can you play the wma files in Windows?  I am just wondering if the file is OK.  Are you able to play other formats in Ubuntu?

Go into Synaptic and search Audacious - the plug ins should all come up.  I have attached a screenshot with the plug in list.


Don't worry about being a noob - we were all there at one time.

---

### Post by otheracco on 2008-02-12
OK, I guess I have the plugins then.  Here's my screenshot.  Yes, they all work fine in windows.   They are all completely DRM free and unprotected. 
Thank you for your help so far.  I wonder though if I really need some of the packages from that tutorial, like gstreamer0.10-pitfdll and maybe some of the others.  The problem is I don't know how to get them.

---

### Post by cozmicharlie on 2008-02-12
What player are you using to try and play the files?  Are you using Listen to play them?

You can try the other gstreamer but I don't have them installed and I can play wma.  The gstreamer0.10-pitfdll is in the Libraries (universe).  To get there open Synaptic, click on "sections" and scroll to Libraries.

---

### Post by cozmicharlie on 2008-02-12
I just noticed - are you using 64 bit or 32 bit version of Ubuntu?  The reason I ask is you installed the w64codecs.  This is the most important info I need.  If you are using the 64-bit version then I would advise against it - this may be your problem. The 64-bit version does not support as many formats and you have to do some workarounds to get wma to work.   If you are not (i.e. you are using the 32-bit version) then you used the wrong codec - you need the w32codecs not the w64codecs.  Uninstall the w64codecs and install the w32codecs

---

### Post by cozmicharlie on 2008-02-12
Also, check in Synaptic that you have libaudio-wma-perl installed.  If not install it.

---

### Post by otheracco on 2008-02-13
OK, I installed libaudio-wma-perl but still have w64codecs.  It's still not working.  I am using the 64-bit UbuntuStudio.  When I try to go to synaptic and search for w32codecs the only hit I get is the 'non-free-codecs' package, which installs codecs based on architecture.  I just installed it anyway, and it doesn't work.  

I've been trying througout the post with 3 media players, beep, listen, and audacious without any luck.

I don't know how to get w32codecs if synaptic won't let me.

---

### Post by cozmicharlie on 2008-02-13
> **otheracco said:**
> OK, I installed libaudio-wma-perl but still have w64codecs.  It's still not working.  I am using the 64-bit UbuntuStudio.  When I try to go to synaptic and search for w32codecs the only hit I get is the 'non-free-codecs' package, which installs codecs based on architecture.  I just installed it anyway, and it doesn't work.  

I've been trying throughout the post with 3 media players, beep, listen, and audacious without any luck.

I don't know how to get w32codecs if synaptic won't let me.

That is because you have the 64-bit version.  I did a search and found a number of threads that discuss wma in 64-bit - this one is an example [http://ubuntuforums.org/showthread.php?t=98576&highlight=wma](http://ubuntuforums.org/showthread.php?t=98576&highlight=wma).  

You may want to change to a 32-bit system.  If not I will have to do some studying to find out how to get it working in 64-bit.  But, after reading I am convinced the problem is you are using the 64-bit version.

Try Rythmbox.  Listen and Beep do not support wma.  Audacious should but it might not in 64-bit.  I can play wma in Audacious and Rythmbox but not Listen or Beep.

---

### Post by otheracco on 2008-02-13
I've heard that before, but the performance on 64-bit is just so great, and It's the future.  I really don't want to switch, but would it be possible to do a 'jail' as they say?  A 32-bit isolated environment in a 64-bit system?  I could run what apps I need in there for my wma files until 64-bit gets caught up.  

The problem is is that even if I weren't somewhat of a noob, It would probably still be a hard concept.

Another thought I had was would it be possible to use 64 and 32 bit kernels on the same install and select whichever one on boot?  then I could use the 64-bit strictly for music production and the 32 bit for all other use.  But that brings more questions.  What happens with the programs already installed on the first kernel.  Do they carry over to the other?  Do they kernels keep totally seperate diretories?  So many questions, I have a feeling that the kernel question is an unknown to many though.

---

### Post by cozmicharlie on 2008-02-14
Try to follow these instructions [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Mplayer_on_64bit_with_wmv9_support](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Mplayer_on_64bit_with_wmv9_support).  This thread has info also [http://ubuntuforums.org/showthread.php?t=62685t](http://ubuntuforums.org/showthread.php?t=62685t). .  What they are basically doing is running a 32 bit version of mplayer in a 64 bit system.  As you can see from the posts it is not that simple. You can try it and see if it works.   This thread has a lot of good information about 64-bit [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

If you have trouble or get stuck post back and I will help you get through it. 

If the above does not work you could set up a dual boot with a 32 and 64 bit version.  They do not share files - they act as completely independent OS.  Another option I use that may work for you is I install a Ubuntu OS on a portable usb drive (I use a 120 gb Western Digital drive).  I found the easiest way to do this is disconnect your main hard drive, reformat the usb drive to ext3 (or whatever Linux file system you prefer) attach the usb drive, make sure in the boot menu you have it set to boot from the live cd then install Ubuntu on the usb drive.  I have this set up on my Windows laptop.  I set my laptop up so it can boot from the usb drive.  All I do then is plug in the usb drive and boot from the usb drive.  

Also, are all your music files in wma?  The other option is convert them to another format or go back to the originals and format them in flac or a lossless format.  They will sound better than wma even on a 64 bit system.

---

### Post by otheracco on 2008-02-16
Thanks so much, coz, you've been a great help and I've added to your 'thank you' points.
I ended up just converting from WMA to FLAC.  To me, it doesn't seem to sound as good, but I can deal with it.  I think wma/wmv playback will come to 64-bit linux in the future, and I can live with the converted files for now.  I went ahead and installed another kernel on my system 2.6.22-14-generic and the performance is phenomenal.  I can install a program, listen to a playlist, browse the internet, and open the filesystem all at the same time without any hiccups or breaks in my music (like I ALWAYS get in Windows).  I'm amazed.  Anyway, it's perfect for general usage and then I can use the realtime kernel for low-latency music production.  The only problem I'm having is that youtube doesn't work under the generic kernel, but it does work under the realtime kernel after I installed the non-free flash package.  On that I could use a little additional help.  Thank you very much!!

---

### Post by cozmicharlie on 2008-02-16
> **otheracco said:**
> Thanks so much, coz, you've been a great help and I've added to your 'thank you' points.
I ended up just converting from WMA to FLAC.  To me, it doesn't seem to sound as good, but I can deal with it.  I think wma/wmv playback will come to 64-bit linux in the future, and I can live with the converted files for now.  I went ahead and installed another kernel on my system 2.6.22-14-generic and the performance is phenomenal.  I can install a program, listen to a playlist, browse the internet, and open the filesystem all at the same time without any hiccups or breaks in my music (like I ALWAYS get in Windows).  I'm amazed.  Anyway, it's perfect for general usage and then I can use the realtime kernel for low-latency music production.  The only problem I'm having is that youtube doesn't work under the generic kernel, but it does work under the realtime kernel after I installed the non-free flash package.  On that I could use a little additional help.  Thank you very much!!

Great - glad to here you are happy with the setup.  I am surprised flac does not sound as good because it is a lossless format and wma is not so I would expect it to sound better.  Oh well - everyone hears differently.

OK - lets move onto the youtube.  Again, as before we just need to install the correct plug ins.  You may want to play DVD also so I will set that up at the same time.  I like two players; VLC (a great all around player for both audio and video) and smplayer (really just a front end for mplayer).  Once we install these we will have the codecs needed and an updated mplayer so you can watch youtube.

I will assume you are using Firefox.

Lets start with the codecs:
You want to be sure you have libdvdcss2 installed - check via synaptic and if it is not installed go ahead and install it.

Now install VLC - very easy from Synaptic.  Open Synaptic and install vlc and mozilla-plugin-vlc.  You can check at this point and see if youtube works but it may not.

Now install mplayer but we are not going to install from Synaptic.  The version in Synaptic is old.  We are going to follow this [http://ubuntuforums.org/showthread.php?t=684193&highlight=smplayer](http://ubuntuforums.org/showthread.php?t=684193&highlight=smplayer)
These are in what are called deb packages.  They are very easy to install - they are analogous to windows installer.  First make sure you have the Gdeb package installed - open applications>system tools and see if Gdeb package installer is there (I believe it is native in Ubuntu but I don't recall - its been a while).  If it is not then install from Add/remove programs - Applications>Add/remove>system tools and check the box for Gdeb Package Installer>hit apply.  Now go here [http://sourceforge.net/project/downloading.php?groupname=smplayer&filename=mplayer_1.0rc2svn25873_i386.deb&use_mirror=superb-west](http://sourceforge.net/project/downloading.php?groupname=smplayer&filename=mplayer_1.0rc2svn25873_i386.deb&use_mirror=superb-west)
and when the dialog box opens it should give you the option to open with Gdeb installer - if so it will automatically download and install.  If not just download from the site to your desktop and double click on the folder once downloaded - the Gdeb package installer should open and you can install.
Now lets install smplayer.  Click here and follow the same instructions as above. [http://sourceforge.net/project/downloading.php?groupname=smplayer&filename=smplayer_0.6.0rc1_i386.deb&use_mirror=internap](http://sourceforge.net/project/downloading.php?groupname=smplayer&filename=smplayer_0.6.0rc1_i386.deb&use_mirror=internap)

A couple notes: when you install mplayer it may give you a warning that mencoder conflicts.  If so then open Synaptic and uninstall mencoder.  When you install mplayer it will get you a new one.  Also you need to make sure in Synaptic that the mplayer-fonts are installed.

Now you should be able to watch videos.

---

### Post by otheracco on 2008-02-19
Thank you again, but WMA can be lossless as well as lossy, mine were all converted from the CD as lossless.

I don't have time to try what you're suggesting with the youtube problem right now.  I'm setting my JACK up right now for recording, but who would youtube work under one kernel and not the other?  They're both on the same system so I have all the same packages installed (I think):confused:  

Anyway, it's not important.

Thank you for your help!

---

