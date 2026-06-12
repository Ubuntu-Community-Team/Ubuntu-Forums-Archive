---
title: "Installing Flash on Firefox"
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by xVehemencityx on 2008-02-03
I'm having some issues with Flash, as it seems everyone is.  I installed it all three ways suggested (removing it after each failed attempt) and none of the three work.  It always says it successfully installed, but when I go to a flash page, it doesn't work.  On my friends computer, we installed Gnash, and the flash thing would come up, but would never load, so I'm not making that mistake again.  What should I do?  Btw, I'm using 7.10

---

### Post by jrib on 2008-02-03
The flash plugin package was broken after adobe released a new version.  There's a package available in gutsy-proposed that is being tested.  As -proposed repos are really for testing, it is up to you if you want to install it.

You can always just download the tar.gz from adobe and extract the .so file into your ~/.mozilla/plugins directory (create it if it does not exist).

---

### Post by pieisgood4589 on 2008-02-03
Why not let Firefox automatically do it? Just go to a place that requires Flash, like YouTube, open a video, and a bar should appear asking you to install Flash. Hit next a couple-o-tymes, and you're done =)

---

### Post by jrib on 2008-02-03
> **pieisgood4589 said:**
> Why not let Firefox automatically do it? Just go to a place that requires Flash, like YouTube, open a video, and a bar should appear asking you to install Flash. Hit next a couple-o-tymes, and you're done =)

That won't work because it installs the broken flash package unless -proposed repos are enabled

---

### Post by pieisgood4589 on 2008-02-03
> **_jason said:**
> That won't work because it installs the broken flash package unless -proposed repos are enabled

But I just did it 2 minutes ago... :confused:

---

### Post by jrib on 2008-02-03
> **pieisgood4589 said:**
> But I just did it 2 minutes ago... :confused:

check if you have -proposed enabled?

---

### Post by Luigi239 on 2008-02-03
The easiest was I have found to install flash is in this thread:

[http://ubuntuforums.org/showthread.php?t=632604](http://ubuntuforums.org/showthread.php?t=632604)

Good luck :)

---

### Post by gandaran on 2008-02-03
the easy way to install flash is to let firefox install it for you, find a webpage that needs flash, when you get that message flash plugin missing you just click install, your troubles are over, but to do that, first you must remove/deactivate the ubufox addon extension (look it up on firefox menu bar»tools»extras/addons) and restart firefox, you can activate it later if you wish,
uninstall any flash, like flashplugin-nonfree or gnash if you happen to have any of these installed.

this method will install directly from the adobe site, if you have the ubufox activated it will install using synaptic which has the broken flash!
 
gandaran

---

### Post by xVehemencityx on 2008-02-03
> **gandaran said:**
> the easy way to install flash is to let firefox install it for you, find a webpage that needs flash, when you get that message flash plugin missing you just click install, your troubles are over, but to do that, first you must remove/deactivate the ubufox addon extension (look it up on firefox menu bar»tools»extras/addons) and restart firefox, you can activate it later if you wish,
uninstall any flash, like flashplugin-nonfree or gnash if you happen to have any of these installed.

this method will install directly from the adobe site, if you have the ubufox activated it will install using synaptic which has the broken flash!
 
gandaran


Wow.  Thank you so much.  That actually worked, and it took less than 10 seconds.  Thanks a ton, dude.

---

### Post by bharkins on 2008-02-03
> **gandaran said:**
> the easy way to install flash is to let firefox install it for you, find a webpage that needs flash, when you get that message flash plugin missing you just click install, your troubles are over, but to do that, first you must remove/deactivate the ubufox addon extension (look it up on firefox menu bar»tools»extras/addons) and restart firefox, you can activate it later if you wish,
uninstall any flash, like flashplugin-nonfree or gnash if you happen to have any of these installed.

this method will install directly from the adobe site, if you have the ubufox activated it will install using synaptic which has the broken flash!
 
gandaran

That was easy and it worked! Sometimes we can get carried away with the Symanics manager.

---

### Post by Jammy4041 on 2008-02-04
Is it possible to download the rpm and use alien to convert it to a deb and install from there?

---

### Post by gandaran on 2008-02-04
Is it possible to download the rpm and use alien to convert it to a deb and install from there?
__________________

maybe it is possible, try it !
but why you want to do that ? if you don't want to install by my instructions, well  there are .deb packages allready made, download the one you need
 
flash for Ubuntu 7.10 32-bit [http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466](http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466)
flash for Ubuntu 7.10 64-bit [http://ubuntuforums.org/attachment.php?attachmentid=53647&stc=1&d=1198033466](http://ubuntuforums.org/attachment.php?attachmentid=53647&stc=1&d=1198033466)

---

### Post by Jored on 2008-02-04
> **gandaran said:**
> the easy way to install flash is to let firefox install it for you, find a webpage that needs flash, when you get that message flash plugin missing you just click install, your troubles are over, but to do that, first you must remove/deactivate the ubufox addon extension (look it up on firefox menu bar»tools»extras/addons) and restart firefox, you can activate it later if you wish,
uninstall any flash, like flashplugin-nonfree or gnash if you happen to have any of these installed.

this method will install directly from the adobe site, if you have the ubufox activated it will install using synaptic which has the broken flash!
 
gandaran

Gandaran, you are a champ!!

I've wasted 2 full weeks with broken repos and well intentioned advise which didn't work for me.

Your instructions solved the problem in under 3 minutes, including uninstalling flashplugin-nonfree, gnash and disabling the ubufox extension.

Many thanks.

---

### Post by PhilipOwrutsky on 2008-02-10
boo, im running 64 bit and adobe doesn't have the right files...I hope this gets fixed soon...

---

### Post by gandaran on 2008-02-11
> **PhilipOwrutsky said:**
> boo, im running 64 bit and adobe doesn't have the right files...I hope this gets fixed soon...

it's been fixed all ready, about a week ago, I think! or at least the 32-bit package is.
do « sudo apt-get update » then install the flashplugin-nonfree.
if you did install flash to home .mozilla folder delete the plugins folder first or uninstall any other flash first.

---

### Post by jrib on 2008-02-11
You'll need the gutsy-updates repository enabled PhilipOwrutsky.  See [FirefoxAMD64FlashJava]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins?action=show&redirect=FirefoxAMD64FlashJava#head-74ed36356cdab258889ed4e9ad010f068e13ff38").  

By the way, the advantage to using a package to install flash is that you get updates for free without worrying about it.  This time, adobe moved the tar.gz and messed up the package for new users.  Hopefully, someone has come up with a way to avoid this in the future.

---

### Post by PhilipOwrutsky on 2008-02-11
Thanks for the prompt replies and helping me sort this out.  Just in case its important, im running 64 bit 7.10, and all my flash stuff was working fine until about 5 days ago when i did an update.  

If i uninstall, update reinstall via apt-get then its still broken.  However, if I disable the ubufox addon uninstall reinstall then it seems to work, but if I restart it breaks again.  Even weirder, it works for about 5 seconds and then breaks after i restart.  Any ideas whats going on?

Thanks again,
Phil

---

### Post by gandaran on 2008-02-11
> **PhilipOwrutsky said:**
> Thanks for the prompt replies and helping me sort this out.  Just in case its important, im running 64 bit 7.10, and all my flash stuff was working fine until about 5 days ago when i did an update.  

If i uninstall, update reinstall via apt-get then its still broken.  However, if I disable the ubufox addon uninstall reinstall then it seems to work, but if I restart it breaks again.  Even weirder, it works for about 5 seconds and then breaks after i restart.  Any ideas whats going on?

Thanks again,
Phil
installing flash by disabling ubufox is recommended only for 32-bit systems,
flash installed that way won't work on 64-bit.
check your home .mozilla folder, if you find a plugins folder,(flash is installed there by firefox) delete it and  do a install by apt-get or synaptic.

---

### Post by PhilipOwrutsky on 2008-02-11
ok, again it works until i reboot, and then works for a few seconds and dies.  Here is exactly what i did this time after re-enabling ubufox:

sudo rm /home/phil/.mozilla/pluginreg.dat
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

I noticed that now /home/phil/.mozilla no longer has a pluginreg.dat file....

---

### Post by gandaran on 2008-02-11
> **PhilipOwrutsky said:**
> ok, again it works until i reboot, and then works for a few seconds and dies.  Here is exactly what i did this time after re-enabling ubufox:

sudo rm /home/phil/.mozilla/pluginreg.dat
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

I noticed that now /home/phil/.mozilla no longer has a pluginreg.dat file....

it's not a /home/phil/.mozilla/pluginreg.dat but a  /home/phil/.mozilla/plugins

that pluginreg.dat file will be regenerated once you reboot /restart firefox

you don't have to use sudo, this is your home folder, just remove it to trash

---

### Post by PhilipOwrutsky on 2008-02-11
Rebooting again and now it works tho that file was not regenerated which has me a little concerned...Thanks for your help!

---

### Post by gandaran on 2008-02-11
> **PhilipOwrutsky said:**
> Rebooting again and now it works tho that file was not regenerated which has me a little concerned...Thanks for your help!

nothing to worry about, you can delete the whole home .mozilla folder, when you restart firefox you will find the folder back there again, all you loose is your own firefox settings.

---

### Post by PhilipOwrutsky on 2008-02-11
Rebooting again broke it and rebooting again fixed it again...wtf??

---

### Post by gandaran on 2008-02-11
do you have gnash installed ?

very strange your problem!

---

### Post by PhilipOwrutsky on 2008-02-11
no i dont, what is it and should i install it?

---

### Post by gandaran on 2008-02-11
> **PhilipOwrutsky said:**
> no i dont, what is it and should i install it?

no, never! I also don't know if it's available for amd64.

gnash is an open software flash

---

### Post by gandaran on 2008-02-11
PhilipOwrutsky
                        look, this looks like conflicting software, did you try installing flash by another method, like downloading the tarbal from the adobe site? maybe there's another flash installed and your computer doesn't know which one to use, maybe this is the problem.

---

### Post by PhilipOwrutsky on 2008-02-11
I did try direct from adobe at one point.  However, the installer failed because the adobe site only had the 32 bit (I forget the exact error but it yelled at me and aborted)...Is there a way i can make sure it didn't install?

---

### Post by PhilipOwrutsky on 2008-02-12
here is my cache file in case thats relevant:

phil@UBUNTUT61:~$ sudo apt-cache policy flashplugin-nonfree info
flashplugin-nonfree:
  Installed: 9.0.48.0.2+really0ubuntu12.2
  Candidate: 9.0.48.0.2+really0ubuntu12.2
  Version table:
 *** 9.0.48.0.2+really0ubuntu12.2 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/multiverse Packages
        100 /var/lib/dpkg/status
     9.0.48.0.2+really0ubuntu12 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
info:
  Installed: 4.8.dfsg.1-6
  Candidate: 4.8.dfsg.1-6
  Version table:
 *** 4.8.dfsg.1-6 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
        100 /var/lib/dpkg/status

---

### Post by gandaran on 2008-02-12
PhilipOwrutsky

to get the information about flash firefox is using , clear first firefox navigator bar then paste this  » about:plugins   
(having problems here with smileys?)   it's « about : plugins »  without spaces
do this when flash is not working and paste the results back here.

---

### Post by PhilipOwrutsky on 2008-02-12
this is the block about flash:

Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 9.0 r115

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

Also, its not an alternating reboot thing like i had originally thought, rebooting it just makes it work for a little while (5seconds-2min) and then it breaks...I did some more searching and found this [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/184157](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/184157) does that mean im sol?

---

### Post by gandaran on 2008-02-12
seems okay, but I was hopping it would show where it is installed.
noticed you installed the candidate package from the -proposed repository.
I would try the  package from the gutsy-updates/multiverse repository, it must be fixed by now just as the 32-bit is.

---

### Post by Bablefish on 2008-02-12
I had a similar problem in my case updating from Flash 7, which by the way I did as a Firefox addon. You see I love going to Discovery.com the vids they have from their shows are GREAT. But you need Flash 9 in order to play properly. Well I did a little checking and I found these command lines on a Ubuntu site and you know what after my computer rebooted to my surprise I had Flash 9. This is what I ran...

 wget -c [http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.63.3ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.63.3ubuntu3_i386.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/g/gsfonts-x11/gsfonts-x11_0.17ubuntu4_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gsfonts-x11/gsfonts-x11_0.17ubuntu4_all.deb)
sudo dpkg -i gsfont*.deb
sudo dpkg -i flash*.deb

---

### Post by yaitedog on 2008-02-12
Well I used the in firefox method and it installed but it runs poorly. I had previously installed via synaptic so i uninstaleed that version and rebooted still runs very poorly. Videos will play but they stutter along annoyingly. Any suggestions?

---

### Post by PhilipOwrutsky on 2008-02-12
I think I got it working by using someones nspluginwrapper, but now i assume i need to avoid updates for a while...I dont have any stuttering here's a linky [http://ubuntuforums.org/showthread.php?t=636397&page=12](http://ubuntuforums.org/showthread.php?t=636397&page=12)  Thanks for all the help

---

### Post by hugomeeuwes on 2008-02-13
I got an similar problem.
Bij typing about: plugins (no space after : ) in the address bar in firefox, I saw the flash plugin of crossover office on top.
Probably, after updating flash, this one got on top, so every install I tried failed, because it wasn't used.
I just removed the cxoffice flash plugin (~/.cxoffice/win98/desktopdata/cxnsplugin/linux/do sdevices_c^3A_windows_system32_Macromed_Flash_NPSW F32.dll.so) and restarted firefox.
Automatically firefox took the next plugin and worked!

---

### Post by yaitedog on 2008-02-13
I did the about :plugin thingy and have shockwave flash on top and futuresplash under. It would be nice if there was an easy way for noobs like me to manage plugins. Thanks for the suggestions everybody.

---

