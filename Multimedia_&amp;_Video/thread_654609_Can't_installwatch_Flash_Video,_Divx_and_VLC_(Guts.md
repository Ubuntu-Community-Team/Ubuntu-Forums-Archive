---
title: "Can't install/watch Flash Video, Divx and VLC (Gutsy)"
date: 2007-12-31
forum: Multimedia &amp; Video
---

### Post by dESAI on 2007-12-31
Did a fresh install of Gutsy on a new HD for my dads PC. Everything was great and he's happy.

Did a fresh install of Gutsy on a new HD for myself...

Could not install VLC... error says something about conflicting software. 

Can't watch youtube or any site with flash video, when I try to download codecs the error is the same if not very similar. 

Can't watch divx on stage 6, same problem.

So I reinstalled everything again new on another new HD. Same problem...

Now I'm still very much a noob. But since I have reached a level where I can troubleshoot basic issues, I recommended Ubuntu to many people. I've even installed it on my dads PC, thats how impressed and confident I was. But this is just daft.

How can I not watch youtube?

My nerdy reputation is at stake here people! hehe ;)

I know other have had similar problems on the forums. Those posts either went nowhere or ended with me being completely lost in lines of code and giving up.

 I hope that someone out there can help :) 

Cheers!

Oh and all the best to all of you, your families and friends for the new year!!

---

### Post by chewearn on 2007-12-31
Happy New Year!
:popcorn:


Which gutsy you installed?  Ubuntu, Kubuntu, Xubuntu, etc?  32bit or 64bit?

Ubuntu: use Menu > Applications > Add/Remove.

For more specific instructions, please, post back with specific steps you take and error messages, thanks. :)

---

### Post by dESAI on 2007-12-31
> **AstalaVista said:**
> Happy New Year!
:popcorn:


Which gutsy you installed?  Ubuntu, Kubuntu, Xubuntu, etc?  32bit or 64bit?

Ubuntu: use Menu > Applications > Add/Remove.

For more specific instructions, please, post back with specific steps you take and error messages, thanks. :)

Thanks :)

OK I installed Ubuntu 7.10.
I enabled my G-card drivers, got the desktop effects working. Then went online. When i try to watch a vid on YTube, i was asked to install flash. I installed both that were available, Adobe first. Then it says:

"The required software to play this file is not installed. You need to install suntable codecs to play media files. Do you want to search for a codec that supports the selected file?"

Yes...!

The "GStreamer Extra Plug ins" is found... (5 stars!). "Confirm installation of restricted software.... (blah blah)"

Confirmed...

"Cannot install 'gstreamer0.10-plugins-ugly' This application conflicts with other installed software. To install *** the conflicting software most be removed 1st. 

Switch to the 'synaptic' package manager to resolve this conflict. X Close 


 - I've never used the syn'pak'man before.

---

### Post by chewearn on 2007-12-31
> **dESAI said:**
> Thanks :)

OK I installed Ubuntu 7.10.
I enabled my G-card drivers, got the desktop effects working. Then went online. When i try to watch a vid on YTube, i was asked to install flash. I installed both that were available, Adobe first. Then it says:

"The required software to play this file is not installed. You need to install suntable codecs to play media files. Do you want to search for a codec that supports the selected file?"

Yes...!

The "GStreamer Extra Plug ins" is found... (5 stars!). "Confirm installation of restricted software.... (blah blah)"

Confirmed...

"Cannot install 'gstreamer0.10-plugins-ugly' This application conflicts with other installed software. To install *** the conflicting software most be removed 1st. 

Switch to the 'synaptic' package manager to resolve this conflict. X Close 


 - I've never used the syn'pak'man before.

Ok, let's tackle flash first.

1. Open Add/Remove Application
2. select All available applications in the drop down box
3. enter "Macromedia Flash" in the search
4. select the checkbox for that
5. click Apply changes button.

Restart firefox, and go to Youtube; it should work now.

Edit:
Oh, forgot; please remove the other flash (gnash swf viewer).  You should not have both at the same time.

---

### Post by dESAI on 2007-12-31
Thanks, can't believe i didn't install flash this way this time. Done. Exact same problem/result :(

---

### Post by chewearn on 2007-12-31
Maybe your configurations have gotten messed up; try these commands from terminal:

```
sudo aptitude update
sudo aptitude purge gnash mozilla-plugin-gnash flashplugin-nonfree
sudo aptitude install flashplugin-nonfree
```

---

### Post by dESAI on 2007-12-31
> **AstalaVista said:**
> Maybe your configurations have gotten messed up; try these commands from terminal:

```
sudo aptitude update
sudo aptitude purge gnash mozilla-plugin-gnash flashplugin-nonfree
sudo aptitude install flashplugin-nonfree
```

Thanks :)

Done. Can't see any change... Still can't install anything or watch youtube.

---

### Post by dESAI on 2007-12-31
Oh firefox is asking for me to install again. But Macr' Flash is ticked in A/R Programs. 

I will untick and retick :) see if i can reinstall.

---

### Post by sloggerkhan on 2007-12-31
If you go to synaptic package manager and try to install something, I think it should tell you what the conflicting software is, and that might be a big help.

---

### Post by dESAI on 2007-12-31
Reinstalling Mac' flash didn't help with youtube.

---

### Post by dESAI on 2007-12-31
> **sloggerkhan said:**
> If you go to synaptic package manager and try to install something, I think it should tell you what the conflicting software is, and that might be a big help.

Thanks :)

VLC:

Could not mark for installation.

vlc:
 Depends: vlc-nox but it is not going to be installed
 Depends: libsdl-image1.2 (>=1.2.5) but it is not installable
 Depends: ttf-dejavu  but it is not installable

Can't even play DVD's atm :(

---

### Post by sloggerkhan on 2007-12-31
Do you have the universe and medibuntu repositories enabled? That's my first thought.
Have you tried going through and manually installing the component dependencies?
Maybe it won't install one of them cause it conflicts with something already installed.

---

### Post by dESAI on 2007-12-31
> **sloggerkhan said:**
> Do you have the universe and medibuntu repositories enabled? That's my first thought.
Have you tried going through and manually installing the component dependencies?
Maybe it won't install one of them cause it conflicts with something already installed.

Thanks :)

Sorry but no I have not tried that. I can't see how it all fits together. Can you give step by step instructions?

---

### Post by NilsE on 2007-12-31
As far as I know there is still a problem with the flashplug:nonfree in the repositories. 

Try to do a "complete removal" in Synaptic and then install this deb file. Download it and open it with gdebi and let it install even though gdebi tells you there is one in the repo. Make sure FF is shut down when you install.

[http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

---

### Post by dESAI on 2008-01-01
> **NilsE said:**
> As far as I know there is still a problem with the flashplug:nonfree in the repositories. 

Try to do a "complete removal" in Synaptic and then install this deb file. Download it and open it with gdebi and let it install even though gdebi tells you there is one in the repo. Make sure FF is shut down when you install.

[http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

Thanks :)

It's easy to install via Add/Remove, but I'm still inexperienced with downloading/installing like this. Sorry to be a pain, but I'm afraid i need step by step instructions.

Happy new year everyone! :)

---

### Post by dESAI on 2008-01-01
Can't even listen to mp3's :(

---

### Post by chewearn on 2008-01-01
Can you post your /etc/apt/sources.lst

---

### Post by NilsE on 2008-01-01
> **dESAI said:**
> Thanks :)

It's easy to install via Add/Remove, but I'm still inexperienced with downloading/installing like this. Sorry to be a pain, but I'm afraid i need step by step instructions.

Happy new year everyone! :)
This basically was a step by step 1) Remove broken package with Synaptic or add/remove or apt (they are all the same)  2) Install good package via gdebi (package installer)

1) Go into System > Administration > Synaptic Package Manager
2) Click on Search
3) Enter flashplugin
4) Click on Search
5) When found click on the box and select "Mark for Removal"
6) Click apply
7) Exit when done

8) Click on my link above
9) Choose to open with gdebi when prompted
10) Close Firefox when gdebi opens
11) Run gdebi to install
12) Restart Firefox when gdebi is done
13) Try it on YouTube

Alternatively replace 8 - 13 with this

8) Click on my link above
9) Choose to download to desktop when prompted
10) Close Firefox when download is done
11) Double click on downloaded file icon on desktop
12) Select to run in gdebi to install
13) Restart Firefox when gdebi is done
14) Try it on YouTube

In both cases ignore the message that gdebi says there is a version in the repositories and install this version.

---

### Post by gakudva on 2008-01-01
> **dESAI said:**
> Reinstalling Mac' flash didn't help with youtube.

You need to install Macromedia flash manually.
Have a look at: [http://ubuntuforums.org/showthread.php?t=635793](http://ubuntuforums.org/showthread.php?t=635793) (Look at answer by lswest)

---

### Post by dESAI on 2008-01-01
> **AstalaVista said:**
> Can you post your /etc/apt/sources.lst

How do i do that? :confused:

---

### Post by NilsE on 2008-01-01
> **dESAI said:**
> How do i do that? :confused:
Edit that file and copy and paste it's contents here.


In a terminal type:

gedit  /etc/apt/sources.list

---

### Post by cherry316316 on 2008-01-02
i installed divx for linux from the divx website, but I am not able to play
the divx for linux as I am not able to locate where the hell it has installed the run file
I only see *.h files (
any of you has tried divx for linux ?

---

### Post by chewearn on 2008-01-02
> **cherry316316 said:**
> i installed divx for linux from the divx website, but I am not able to play
the divx for linux as I am not able to locate where the hell it has installed the run file
I only see *.h files (
any of you has tried divx for linux ?


I'm assuming you have ubuntu gutsy; there is no need to install divx player from divx website (unless you have some special reason to do so?)  Simply launch the divx file, the totem movie player will prompt you to install the required codec.

---

### Post by dESAI on 2008-01-02
> **NilsE said:**
> Edit that file and copy and paste it's contents here.


In a terminal type:

gedit  /etc/apt/sources.list

Thanks :)

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by dESAI on 2008-01-02
> **NilsE said:**
> This basically was a step by step 1) Remove broken package with Synaptic or add/remove or apt (they are all the same)  2) Install good package via gdebi (package installer)

1) Go into System > Administration > Synaptic Package Manager
2) Click on Search
3) Enter flashplugin
4) Click on Search
5) When found click on the box and select "Mark for Removal"
6) Click apply
7) Exit when done

8) Click on my link above
9) Choose to open with gdebi when prompted
10) Close Firefox when gdebi opens
11) Run gdebi to install
12) Restart Firefox when gdebi is done
13) Try it on YouTube

Alternatively replace 8 - 13 with this

8) Click on my link above
9) Choose to download to desktop when prompted
10) Close Firefox when download is done
11) Double click on downloaded file icon on desktop
12) Select to run in gdebi to install
13) Restart Firefox when gdebi is done
14) Try it on YouTube

In both cases ignore the message that gdebi says there is a version in the repositories and install this version.

Thanks :)

No change. Although there is definately a problem with flash (on the flash homepage "videos being watched right now" - all 5 screens are blue...) I want to concentrate on getting mp3's and stuff to play. 

I still get the same error when I try to watch a vid on youtube... "Search for a suitable codec"... when I to install the codecs I still get the message that it conflicts with other installed software.

---

### Post by dESAI on 2008-01-02
I really appreciate all the help everyone is giving... I can't believe I have so many multimedia problems after all the positive experience with previous versions of Ubuntu. 

Thanks everyone! I hope that this helps others too :)

---

### Post by dESAI on 2008-01-02
> **cherry316316 said:**
> i installed divx for linux from the divx website, but I am not able to play
the divx for linux as I am not able to locate where the hell it has installed the run file
I only see *.h files (
any of you has tried divx for linux ?

Yeah I can't play most stuff at the moment. The best I can do is play some files without audio.

---

### Post by Lacrimstein on 2008-01-02
Try to install Flash manually. Go to the website

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

and choose the .tar.gz option

Unarchive it, then open up the terminal, cd to the extracted folder, and run flashplayer-installer. Hope that helps :)

---

### Post by dESAI on 2008-01-03
> **Lacrimstein said:**
> Try to install Flash manually. Go to the website

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

and choose the .tar.gz option

Unarchive it, then open up the terminal, cd to the extracted folder, and run flashplayer-installer. Hope that helps :)

*Cheer* 
*dances on chair* 
*grabs the cat and dances with the cat*

Youtube works now! Finally some progress :) Thanks so much.!

Why didn't it just work? :(

Divx, Mp3's and DVD's are still not working...

---

