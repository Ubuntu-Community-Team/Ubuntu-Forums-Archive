---
title: "Removing OpenShot killed Video Playback"
date: 2009-12-20
forum: Multimedia Software
---

### Post by Weet on 2009-12-20
Hi everyone,

I tried searching the forums for an answer to my problems but haven't found anything of use, partly because I'm not sure what I'm looking for in this case.  Here's my problem:

I recently installed OpenShot, played around with it, and then removed it from my system.  Following this I ran the package cleaner in UbuntuTweak.  Apparently, that was a bad idea.

Problem is, I can't play back any video now in Miro, Totem, or VLC. Just for kicks I tried reinstalling OpenShot to see if that would solve my problems.  I had no luck, though OpenShot ran and played back video perfectly fine.  Likewise I can still watch youtube, hulu, etc.

I get an "Internal Data Stream Error" in Totem and an error saying "VLC does not support the audio or video format XVID" in VLC; however, I do get audio in VLC which is more than I'm getting with Totem.  I've tried a number of different video formats with no luck.  

I checked Synaptic and, without really knowing what I'm looking for, the major xine libraries *seem* to be installed along with the Ubuntu Restricted Extras.

Any ideas?

---

### Post by muse3332 on 2009-12-20
try running this in terminal sudo apt get "flash plugin" without quotations i know you said youtube and hulu work fine butt give it a shot

---

### Post by mc4man on 2009-12-20
It was installing openshot (the dev ppa version) that broke the repo vlc, totem. (don't see the value of ubuntu tweak other than causing eventual issues.

A properly built vlc  or openshot can co-exist (if either or both is compiled with built-in ffmpeg support

To fix, various ways to same result
[http://ubuntuforums.org/showthread.php?t=1281367](http://ubuntuforums.org/showthread.php?t=1281367)

Edit: the above was initially for jaunty (9.04), if you're using karmic (9.10) then don't install the 'unstripped' ffmpeg libs, you want the 'extra' versions only.

a good repo to add to karmic before reinstalling the ffmpeg libs is shown under part C [here]("http://ubuntuforums.org/showthread.php?t=1117283")

An alternate openshot that uses the ubuntu shared ffmpeg libs
[http://ubuntuforums.org/showthread.php?t=1346952&highlight=openshot](http://ubuntuforums.org/showthread.php?t=1346952&highlight=openshot)

---

### Post by Weet on 2009-12-20
Ah thank you very much; those were very helpful.  I'm not sure why that didn't turn up in search - Oh well.

For the record I used these instructions to solve the problem:

> Originally Posted by narcisgarcia  
Follow strictly these steps to fix the problem with a clean result:
Open Synaptic package manager
In the Settings menu, open the Repositories option.
In the Third-Party Software tab, remove the "ppa...openshot" lines.
Close the small Software Sources window, and use the Reload button to update repositories.
Search libpostproc and mark any installed package for removal; no problem marking other dependent software to be removed.
Search libswscale and mark any installed package for removal; no problem marking other dependent software to be removed.
Search libavcodec and mark any installed package for removal; no problem marking other dependent software to be removed.
Search libavformat and mark any installed package for removal; no problem marking other dependent software to be removed.
In the File menu, use the Save Markings As option, and use a name like synaptic.txt
Once the markings are saved, perform the actions with the Apply button.
Open the synaptic.txt file with a text editor.
Replace all the words deinstall with install and save the file.
Return to Synaptic and load synaptic.txt with the Read Markings option in the File menu.
Use the Apply button and after the process your software will be as before OpenShot.

If you want to install OpenShot, don't use the PPA Instructions from the Download section; use the DEB Instructions. (once downloaded, install first the dependencies and then OpenShot).

---

### Post by Roasted on 2009-12-20
I just installed OpenShot.

Is this to say if I remove it, I'm going to have a little problem on my hands?

---

### Post by Zeedok on 2009-12-20
Not necessarily. If you installed from the new report, you'll be fine (see the website for a blog post about it).

If not, then check the synaptic history to see which packages were installed or removed. Note these in case you need them later.

---

### Post by LuisGMarine on 2009-12-20
I'm going to have to give this fix a try and see what my results are.  I did install openshot and when I removed it I noticed that my video playback went to hell.  I thought it was another issue with 64-bit ubuntu, but I think I could be wrong.  Lets hope this fix works.

---

### Post by Roasted on 2009-12-21
*sigh*

removing a program = video problems? really?

I downloaded mine from the web site. I hope that's the fixed version.

---

### Post by mc4man on 2009-12-21
If it's not obvious, vlc and or totem won't decode several formats, then just ck. what version of libavcodec is installed.

If it's 4:0.5+svn20090926-0ubuntu3..... then you used [this openshot ppa]("https://launchpad.net/~openshot.developers/+archive/ppa") which updates your ffmpeg and libs. ( the 'bad'

If it's 4:0.5+svn20090706..... then you installed the deb which leaves your ffmpeg libs as is, [ppa seen here]("https://launchpad.net/~jonoomph/+archive/openshot-edge")


edit: 
> removing a program = video problems? really?

Just to repeat, **it's adding the dev ppa** for openshot and having your ffmpeg libs updated that causes the issues, **not removing openshot** after it's been installed.
All that removing openshot does is to  remove openshot

---

### Post by VertexPusher on 2009-12-21
> **Roasted said:**
> *sigh*

removing a program = video problems? really?
If the program replaces/overwrites system libraries with its own versions, then removes them entirely when being uninstalled, then yes, you'll have some problems.

OpenShot has a reputation for causing these troubles. It seems that its developers/maintainers don't have a clue what they're doing.

Fortunately no one really needs OpenShot. There are better video editors available.

---

### Post by Perturbed Penguin on 2009-12-21
Ok so I came across this same problem, BAD Openshot! Anyways this is what I did to fix things up. Go to synaptic and search for libavcodec, there should be a package named 'libavcodec-extra-52' that is installed. Click on this package then go to the package menu up top and select 'force version'. It will ask you which version you want to use, I forget the exact name but select the one that is a little older and doesn't have 'ppa' in its name. Next it will give you a list of packages that are being changed/unchanged/removed, please take notice of any other software that it is uninstalling so that you can reinstall that software later on - for example it uninstalled blender and vlc when I did this fix and I had to go back and reinstall both of those packages later on. Now go ahead and let synaptic make the change. Afterwards you will likely have to reinstall a few gstreamer plugins as well, I just searched for gstreamer plugins in the software center and installed the missing ones. Once you have done all of this, if you have UbuntuTweak, then you can go and purge the old cache files and such else so you are completely rid of all the devilish openshot packages forever! Hope this helps anyone else having this issue. ;)

Btw this is the link where I found this fix just for reference:
[http://old.nabble.com/Openshot-video-editing-software-Karmic-Koala-td26152070.html](http://old.nabble.com/Openshot-video-editing-software-Karmic-Koala-td26152070.html)

---

### Post by LuisGMarine on 2009-12-21
I tried what was said in the earlier post and everything is back to normal.  I'm back to square one, now I have to figure out how to fix my videos not being interlaced.  Thanks for the work around!

---

