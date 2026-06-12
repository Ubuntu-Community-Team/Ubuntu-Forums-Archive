---
title: "Flash Videos problem"
date: 2008-12-11
forum: Multimedia Software
---

### Post by amr_essam on 2008-12-11
Dear there , 

could anyone please tell me which libraries i should have in Synaptic manager , so that i can see flash videos like youtube and facebook videos ???

Thanks

---

### Post by gandaran on 2008-12-11
install **flashplugin-nonfree** (adobe flash) or install the full package with flash, java, fonts and codecs **ubuntu-restricted-extras**

---

### Post by wolfen69 on 2008-12-11
first make sure you have all the repos enabled by going to system>administration>software sources.

---

### Post by amr_essam on 2008-12-11
dear gandaran
i did installed them , but when i open any video in youtube , nothing appears 
and when i open a video in facebook , it tells me to install flash video player , which is already installed :|

how can i remove any package related to this , and start over again ?
i am afraid that there is conflict between packages ...

Thanks

---

### Post by amr_essam on 2008-12-11
> **wolfen69 said:**
> first make sure you have all the repos enabled by going to system>administration>software sources.


what is repos ??

---

### Post by wolfen69 on 2008-12-11
go to synaptic (system>administration>synaptic package manager) and completely remove flashplugin-nonfree. then go [here]("http://get.adobe.com/flashplayer/?promoid=DXLUJ") and download the .deb for ubuntu. click to install. restart firefox if open.

---

### Post by wolfen69 on 2008-12-11
> **amr_essam said:**
> what is repos ??

repositories. it is where you get software from.

---

### Post by gandaran on 2008-12-11
> **amr_essam said:**
> dear gandaran
i did installed them , but when i open any video in youtube , nothing appears 
and when i open a video in facebook , it tells me to install flash video player , which is already installed :|

how can i remove any package related to this , and start over again ?
i am afraid that there is conflict between packages ...

Thanks
what version of ubuntu you have, 8.04 or 8.10 and 32-bits or 64-bits?
did you install another flash package like gnash or swfdec, if so remove them

---

### Post by amr_essam on 2008-12-11
Look guys , 
first i have ubuntu 8.04 , 32 bit

second , i removed ( flashplugin-nonfree , gnash , swfdec ) completely 
and i downloaded the flash installer from Adobe site 
but what i have now , is that when i open youtube video it tells me 
"Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player. "
although i installed their package

i am really confused

---

### Post by gandaran on 2008-12-11
> **amr_essam said:**
> Look guys , 
first i have ubuntu 8.04 , 32 bit

second , i removed ( flashplugin-nonfree , gnash , swfdec ) completely 
and i downloaded the flash installer from Adobe site 
but what i have now , is that when i open youtube video it tells me 
"Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player. "
although i installed their package

i am really confused
post the full output of this code, type in firefox url bar
```
about:plugins
```
and also the output of **locate libflash**  (type this in terminal)

---

### Post by amr_essam on 2008-12-11
> **gandaran said:**
> post the full output of this code, type in firefox url bar
```
about:plugins
```
and also the output of **locate libflash**  (type this in terminal)

Hope u can get this

About Plugins

Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
Demo Print Plugin for unix/linux

    File name: libunixprintplugin.so
    The demo print plugin for unix.

MIME Type 	Description 	Suffixes 	Enabled
application/x-print-unix-nsplugin 	Demo Print Plugin for Unix/Linux 	.pnt 	Yes
iTunes Application Detector

    File name: librhythmbox-itms-detection-plugin.so
    This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.

MIME Type 	Description 	Suffixes 	Enabled
application/itunes-plugin 			Yes
Java(TM) Plug-in 1.6.0_07-b06

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_07

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6.0_07 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6.0_07 	Java 		Yes
Totem Web Browser Plugin 2.22.1

    File name: libtotem-basic-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-ogg 	- 	ogg 	Yes
application/ogg 	Ogg multimedia 	ogg 	Yes
audio/ogg 	Ogg Audio 	oga 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogv 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
application/annodex 	- 	anx 	Yes
audio/annodex 	- 	axa 	Yes
video/annodex 	- 	axv 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NullSoft video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)

    File name: libtotem-complex-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealAudio document 	rpm 	Yes
VLC Multimedia Plugin (compatible Totem 2.22.1)

    File name: libtotem-cone-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-vlc-plugin 	unknown 		Yes
application/vlc 	unknown 		Yes
video/x-google-vlc-plugin 	unknown 		Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	Windows Media video 	wmv 	Yes
video/x-wmv 	Windows Media video 	wmv 	Yes
video/x-ms-wvx 	Microsoft ASX playlist 	wmv 	Yes
video/x-ms-wm 	ASF video 	wmv 	Yes
application/x-ms-wms 	Windows Media video 	wms 	Yes
application/asx 	Microsoft ASX playlist 	asx 	Yes
audio/x-ms-wma 	Windows Media audio 	wma 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	QuickTime image 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes



terminal command:

/usr/lib/libflash.so.0
/usr/lib/libflash.so.0.13.0
/usr/lib/libflashsupport.so
/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/mozilla/plugins/libflash-mozplugin.so
/usr/lib/mozilla-firefox/plugins/libflash-mozplugin.so
/usr/lib/openoffice/program/libflash680li.so
/usr/share/doc/libflash-mozplugin
/usr/share/doc/libflash-swfplayer
/usr/share/doc/libflash0c2
/usr/share/doc/libflashsupport
/usr/share/doc/libflash-mozplugin/README
/usr/share/doc/libflash-mozplugin/README.Debian
/usr/share/doc/libflash-mozplugin/changelog.Debian.gz
/usr/share/doc/libflash-mozplugin/copyright
/usr/share/doc/libflash-swfplayer/README
/usr/share/doc/libflash-swfplayer/README.Debian
/usr/share/doc/libflash-swfplayer/changelog.Debian.gz
/usr/share/doc/libflash-swfplayer/copyright
/usr/share/doc/libflash0c2/README
/usr/share/doc/libflash0c2/README.Debian
/usr/share/doc/libflash0c2/changelog.Debian.gz
/usr/share/doc/libflash0c2/copyright
/usr/share/doc/libflashsupport/changelog.Debian.gz
/usr/share/doc/libflashsupport/copyright
/usr/share/lintian/overrides/libflash-mozplugin
/usr/share/lintian/overrides/libflashsupport
/var/cache/apt/archives/libflash-mozplugin_0.4.13-9ubuntu1_i386.deb
/var/cache/apt/archives/libflash-swfplayer_0.4.13-9ubuntu1_i386.deb
/var/cache/apt/archives/libflash0c2_0.4.13-9ubuntu1_i386.deb
/var/cache/apt/archives/libflashsupport_1.9-0ubuntu1_i386.deb
/var/lib/dpkg/info/libflash-mozplugin.list
/var/lib/dpkg/info/libflash-mozplugin.md5sums
/var/lib/dpkg/info/libflash-mozplugin.postinst
/var/lib/dpkg/info/libflash-mozplugin.postrm
/var/lib/dpkg/info/libflash-mozplugin.shlibs
/var/lib/dpkg/info/libflash-swfplayer.list
/var/lib/dpkg/info/libflash-swfplayer.md5sums
/var/lib/dpkg/info/libflash0c2.list
/var/lib/dpkg/info/libflash0c2.md5sums
/var/lib/dpkg/info/libflash0c2.postinst
/var/lib/dpkg/info/libflash0c2.postrm
/var/lib/dpkg/info/libflash0c2.shlibs
/var/lib/dpkg/info/libflashsupport.list
/var/lib/dpkg/info/libflashsupport.md5sums
/var/lib/dpkg/info/libflashsupport.postinst

---

### Post by gandaran on 2008-12-11
well firefox hasn't detected adobe flash, you still have a lot other flash packages installed, you'll have to remove every one and just keep adobe flash
I make a list and post back

---

### Post by gandaran on 2008-12-11
okay look for the following packages to remove, maybe some of them are not installed
mozilla-plugin-gnash
swfdec-mozilla
flashblock
mozplugin or libflash (I dont know the exact package name as I 'm runnig ubuntu 8.10)
libflashsupport (it's only needed if you have flash sound problems with flash 9, conflicts with flash 10)
libflash?

---

### Post by amr_essam on 2008-12-11
well , done 
i removed these packages completely 
what next ?

Thanks

---

### Post by corelx on 2008-12-13
i've the same problem, but i dont have any of those other players/codecs installed.
tried almost everything, downloading from adobe .deb and after tarball, also tried apt-get flashplugin-nonfree, but nothing :(
Java(TM) Plug-in 1.6.0_06 is installed only.
the weird thing is that the locate libflash is only locating some openoffice/libflash0608*.so, and i have libflashplayer.so in the firefox, firefox-3.0, mozilla and adobe-flashplugin directories.

can you experts help us?

---

### Post by amr_essam on 2008-12-13
hey corelx ,
 when i removed all the packages shown in previous posts 
i started all over again by installing missing plugins which Firefox needs
then i installed the adobeflash.deb and it worked

but the problem still exists with facebook videos , it needs the flash player though it's already installed

and another thing , when i play videos on youtube , it is working but slowly ( not buffering slowly ) as it jumps between pics , and the sound is working hardly..

any help for us guys !!!

Regards

---

### Post by corelx on 2008-12-14
I've removed firefox-3.0 yesterday, and after restart tried to install again, but the synaptic get an error with a dependent package, what was actually installed :S
So i went to reinstall the whole system, load up the proper eeepc kernel and acpi patch, then tried the adobeflash, but still no succes :(
As i read the other topics, everybody just saying to check packages, try to reinstall firefox, but the problem still stand.
Maybe i should try to install the 9th version, but i dontknow where can i download that. Already googled around the net and most of the links was dead or linked to the new 10th version.
Somebody can help me out with a link?

---

### Post by gandaran on 2008-12-15
> So i went to reinstall the whole system, load up the proper eeepc kernel and acpi patch, then tried the adobeflash, but still no succes 
corelx
which adobe flash package did you install? from the repos or from adobe.com?
look,I don't know anything yet about the ubuntu eeepc version (I'm planning to buy one eeepc!) but maybe you should stick to just install plugins from synaptic, install only adobe flash from synaptic and nothing else for flash after reinstalling the whole system, it should work!
is the ubuntu eeepc 32-bits or 64-bits? version 8.04 or 8.10? 
> As i read the other topics, everybody just saying to check packages, try to reinstall firefox, but the problem still stand. 
&#7929;ou don't need to remove firefox first (removing it also removes dependencies), you just go to synaptic and mark for reinstall and click the apply button

---

### Post by corelx on 2008-12-15
tried with the one from repo and the official adobe.com version.
i will give it a try, reinstall and setup flash before patches.
64bit? i think there is no 64bit version of eeepc :)
atom is only 32bit, right?!
this is the ubuntu 32bit 8.04.1 version from the ubuntu.com
i will reinstall, but i'm aware of that because its dont remove the dependencies, but when installing again want to install one of the dependenccies what is already installed, and cant removed manually :S
do you know where can i download the 9 version of the flash?

---

### Post by gandaran on 2008-12-15
> do you know where can i download the 9 version of the flash?
well if you running ubuntu 8.04.1 and install adobe flash from synaptic it installs flash 9 (at least the normal 32-bits ubuntu!, don't know about the eeepc version!)
you can check what version of flash installed by going to firefox » tools » addons » plugins » shockwave flash.
you can get flash 9 here [http://download.macromedia.com/pub/flashplayer/updaters/9/flash_player_9_linux_dev.tar.gz](http://download.macromedia.com/pub/flashplayer/updaters/9/flash_player_9_linux_dev.tar.gz) inside you'll find the plugin for firefox and two stand alone players, what you need is the extracted libflashplayer.so file from the plugin, just drop this libflashplayer.so file in a firefox plugin folder, usually /usr/lib/mozilla/plugins or any firefox plugins directory.

---

### Post by corelx on 2008-12-16
in case of reinstalling ubuntu, which version should i install/you recommend?
hardy org 8.10?

---

### Post by corelx on 2008-12-17
Yesterday i've installed intrepid and after completed tried the flashplayer, but the same :(
Now i get back the hardy, install the eeepc kernel and modules only, trying flashplayer now and now succes.
I can't believe this, why is it dont work at me?! :S :(
And default there is no flashplayer installed, at least i cant see one in the about:plugins page.

The output of the installer:
```

corelx@corelx-eee:~/Desktop$ sudo dpkg -i install_flash*.deb
[sudo] password for corelx: 
(Reading database ... 94223 files and directories currently installed.)
Unpacking adobe-flashplugin (from install_flash_player_10_linux.deb) ...
Setting up adobe-flashplugin (10.0.12.36-1hardy1) ...

corelx@corelx-eee:~/Desktop$ 

```

---

### Post by gandaran on 2008-12-17
corelx
maybe the eeepc kernel has a deferent file structure and the adobe-flashplugin won't install in the correct plugins directory? well, has I have said before I don't know anything about the eeepc version, I could be wrong.
in synaptic do you have a flashplugin-nonfree package? you have tried it and it doesn't work too? you don't have anything blocking flash like flashblock installed?
well if all of this fails you can still install the flash plugin manually, remove all flash installed and get the .tar.gz package from adobe.com, extract the contents and just drop the libflashplayer.so file in a browser plugins directory usually /usr/lib/mozilla/plugins or /home/'user'/.mozilla/plugins (make the plugins folder) or even any firefox plugins folder.

---

### Post by sirusdesign on 2008-12-17
Thanks for sharing useful information with you.Just download video with E.M. Youtube video download tool.
It can download video from youtube , myspace, veoh, yahoo or any other video websites autoamtically.Then upload it to facebook.

---

### Post by corelx on 2008-12-17
I've tried that already.
/usr/lib/firefox/plugins
/usr/lib/firefox-3.0/plugins
/usr/lib/mozilla/plugins
/home/corelx/.firefox/plugins
/home/corelx/.mozilla/plugins

These directories i copied the libflashplayer.so from tar.gz version :(

---

### Post by corelx on 2008-12-17
Now i tried with the generic kernel, and the same.
What else could i do?

How can the flash not run, and mozilla doestn recognize it?
Its a standard ubuntu desktop release, from the official site (Hardy 8.04.1)
without localization or any patch.
By default installed Firefox 3.0, and there is no other flashplayer on the system.

---

### Post by gandaran on 2008-12-17
> **corelx said:**
> I've tried that already.
/usr/lib/firefox/plugins
/usr/lib/firefox-3.0/plugins
/usr/lib/mozilla/plugins
/home/corelx/.firefox/plugins
/home/corelx/.mozilla/plugins

These directories i copied the libflashplayer.so from tar.gz version :(
maybe then flash doesn't work on eeepc! ask for help on eeepc forum [http://forum.eeeuser.com/](http://forum.eeeuser.com/)

---

### Post by gandaran on 2008-12-17
> **corelx said:**
> Now i tried with the generic kernel, and the same.
What else could i do?

How can the flash not run, and mozilla doestn recognize it?
Its a standard ubuntu desktop release, from the official site (Hardy 8.04.1)
without localization or any patch.
By default installed Firefox 3.0, and there is no other flashplayer on the system.
try wiping out the current firefox profile, just delete the hidden home user .mozilla folder (backup first) then restart firefox see if it makes any deference

---

### Post by gandaran on 2008-12-17
> /home/corelx/.firefox/plugins
/home/corelx/.mozilla/plugins
why do you have two home firefox profiles? one home .firefox and another .mozilla?
you are supposed to have only the home user .mozilla folder!
or did you install another version of firefox?

---

### Post by corelx on 2008-12-17
sorry its my fault, there are no two dirs, only the .mozilla.

---

### Post by corelx on 2008-12-17
now tried gnash and flash sites are working, but flash videos are not, like youtube.
i've tried (almost?) every solution from the forum and google
and after 2-3 days of trying decided to wipe ubuntu and install back the good'old xp. At least thats working :P
sorry, bye all.

---

### Post by corelx on 2008-12-17
succes!!!! :D
had to update the system, and voila the adobe plugin works perfectly!
uhm almost perfectly, cos i cant adjust the settings, but its ok.
now i just want to know what update is necessary to run that damn plugin,
because i dont want to install all of them, or i should?!

---

