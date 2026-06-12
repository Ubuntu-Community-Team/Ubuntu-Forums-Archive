---
title: "Complete Streaming, Multimedia &amp; Video How-to"
date: 2008-01-08
forum: Multimedia &amp; Video
---

### Post by ubuntu-freak on 2008-01-08
[COLOR=DarkRed]**FYI, **[/COLOR]This thread has been deprecated in favor of a [new version here]("http://ubuntuforums.org/showthread.php?t=766683").
[COLOR=DarkRed][B]
REVISED ON THE 25TH OF APRIL 2008[/B][/COLOR]
 
 
**[COLOR=darkred]--PART 1/5, ESSENTIAL PACKAGES--[/COLOR]**
**[COLOR=darkred]--PART 2/5, STREAMING WITH FIREFOX--[/COLOR]**
**[COLOR=darkred]--PART 3/5, SOUND & VIDEO CONVERSION--[/COLOR]**
**[COLOR=darkred]--PART 4/5, DVD PLAYBACK/RIPPING/BURNING--[/COLOR]**
**[COLOR=darkred]--PART 5/5, MISCELLANEOUS & TROUBLESHOOTING--[/COLOR]**


**[COLOR=DarkRed]INTRODUCTION[/COLOR]**


[COLOR=DarkRed]**Reason for how-to:**[/COLOR] I still see some users struggling and becoming frustrated over getting streaming media or Java to work, and having general multimedia issues, so I thought I'd post my own how-to on the subject. Please keep in mind however that Ubuntu has a feature where if you click on a certain file, or try to view flash videos, a dialog should pop-up and ask if you want to install proprietary packages that are neccessary to play those formats. This how-to is for users who are still having issues, or simply want as many different formats working as possible with just a few commands.

[COLOR=DarkRed]**Please note:**[/COLOR] You will see a reaccurance of certain packages in different parts of this how-to (Sound & Video Conversion for example), this is just to make certain that you have the necessary packages installed to enable whatever feature you're looking to have available to you on your system. This goes for Part 1 also, as you may have some of the packages installed already. Anything you already have installed will be skipped, it will not cause any problems.

[COLOR=DarkRed]**Unrelated to streaming, multimedia and indeed video:**[/COLOR] I see quite a few newbies have been watching YouTube videos and are curious about the whole 3D rotating desktop feature of Linux, and other such effects. Part 1 of my how-to now includes the CCSM package (compizconfig-settings-manager). Here is a [link]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion") to help you get the most out of it and understand the various plugins and settings.
  
 
[COLOR=darkred]**--PART 1/5, ESSENTIAL PACKAGES--**[/COLOR]
 
  
[COLOR=red]**IMPORTANT:**[/COLOR] If you haven't already, you need to enable the Medibuntu repository. These commands are aimed at Gutsy users, so if you are using a different version of Ubuntu, please edit the first command in your Terminal and change it from "gutsy" to whatever version you are running. Open the Terminal (Applications>Accessories>Terminal or KMenu>System>Terminal Program (Konsole) in Kubuntu and Applications>System>Terminal in Xubuntu) and paste these wget commands into it:
 
**sudo wget [noparse]http://www.medibuntu.org/sources.list.d/hardy.list[/noparse] -O /etc/apt/sources.list.d/medibuntu.list**
 
**wget -q [noparse]http://packages.medibuntu.org/medibuntu-key.gpg[/noparse] -O- | sudo apt-key add - && sudo apt-get update**
 
If that didn't work and you received an error, you will have to add the repositoriess manually, which is actually quite easy. First of all, you need to open the sources file with your default or favourite text editor (replace "gedit" with "kwrite" in Kubuntu and "mousepad" in Xubuntu:

**gksudo gedit /etc/apt/sources.list**

Now just add these lines at the bottom, remembering to change the Ubuntu version accordingly. After you have added the two lines, save the changes and wget the GPG key as instructed above:

[B]deb [noparse]http://packages.medibuntu.org/[/noparse] hardy free non-free
deb-src [noparse]http://packages.medibuntu.org/[/noparse] hardy free non-free[/B]
 
It's also a good idea to make sure the Multiverse and Universe repositories are enabled, although they should be enabled by default on the latest versions of Ubuntu. To make sure they are, or to choose a local server for downloads, navigate to System>Administration>Software Sources and tick whichever sources you wish to use. While you're there, you can also untick the CD-ROM/DVD source and choose a local server instead of using the main server. There are two good reasons for this - Firstly, you give the main server a break because you're using a local mirror, and secondly, it will improve download speeds when updating or installing software on to the system.


**[COLOR=DarkRed]ADOBE FLASH INSTALLATION[/COLOR]** 


There appear to be some users still havng issues installing Adobe Flash. If you tried installing it already and are having issues, read on. First of all, it's worth completely purging the package from your system, along with any others which may be interfering with it and then reinstall it again. Will both 32-Bit and 64-Bit users execute this command:

**sudo apt-get purge flashplugin-nonfree gnash gnash-common && sudo apt-get install flashplugin-nonfree**

Still no joy? Please cut and paste the "purge" part of the command (stop before the "&&" symbols) to completely remove the package. Next, I would suggest following the intructions below for your particular architecture:

**[COLOR=darkred]32-Bit Users:[/COLOR]** Install it manually by downloading the tar [here]("http://www.adobe.com/products/flashplayer/") and extract the contents to your desktop or home folder. Press Alt-F2" and enter "gksudo nautilus" into the run command dialog, another dialog will pop-up asking for your password, enter your password and then navigate to your desktop or home folder within the file browser. Finally, click on the installer and instruct it to install the plugin to "/usr/lib/firefox" (without quotation marks), or to wherever your favourite browser is located, and then you're done. You can now exit the installer. 

**[COLOR=darkred]64-Bit Users:[/COLOR]** It should be harder for you to install the plugin, as it's a 32-Bit package, but thanks to a handy script by Kilz, it's actually quite easy. Please visit [this thread]("http://ubuntuforums.org/showthread.php?t=476924&highlight=gnash") and run the recommended script to install an older and more compatible version of Adobe Flash, along with a wrapper that will enable it to work on your 64-Bit system.

An easy and quick way to install most of the packages you need (Java, codecs for playing/ripping/converting music and video etc) is to use the command line. If you would rather use a graphical application with descriptions of packages, you can either use Add/Remove, Synaptic in Ubuntu and Xubuntu (System>Administration>Synaptic Package Manager in Ubuntu and Applications>System>Synaptic Package Manager in Xubuntu) and Adept in Kubuntu (KMenu>System>Adept). For the sake of speed, I suggest you use the Terminal for most of this how-to. Open the Terminal and paste these commands into it:


**[COLOR=DarkRed]UBUNTU FAMILY 8.04 HARDY HERON USERS ONLY[/COLOR]**


**[COLOR=DarkRed]32-Bit Ubuntu Users:[/COLOR]**
 
**sudo apt-get remove icedtea-gcjwebplugin openjdk-6-jre && sudo apt-get install alsa-oss compizconfig-settings-manager faad gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libflashsupport liblame0 sun-java6-fonts sun-java6-jre sun-java6-plugin unrar w32codecs**
 
**[COLOR=DarkRed]32-Bit Kubunu Users:[/COLOR]**
 
**sudo apt-get remove icedtea-gcjwebplugin openjdk-6-jre && sudo apt-get install alsa-oss libflashsupport libk3b2-extracodecs liblame0 libtunepimp5-mp3 libxine1-ffmpeg sun-java6-fonts sun-java6-jre sun-java6-plugin unrar w32codecs**
 
**[COLOR=DarkRed]32-Bit Xubuntu Users:[/COLOR]**
 
**sudo apt-get remove icedtea-gcjwebplugin openjdk-6-jre && sudo apt-get install alsa-oss libflashsupport liblame0 libxine1-ffmpeg sun-java6-fonts sun-java6-jre sun-java6-plugin unrar w32codecs**
 
**[COLOR=DarkRed]64-Bit Ubuntu Users:[/COLOR]**
 
**sudo apt-get install alsa-oss compizconfig-settings-manager faad gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse icedtea-gcjwebplugin libflashsupport liblame0 unrar w64codecs**
 
**[COLOR=DarkRed]64-Bit Kubuntu Users:[/COLOR]**
 
**sudo apt-get install alsa-oss icedtea-gcjwebplugin libk3b2-extracodecs libflashsupport liblame0 libtunepimp5-mp3 libxine1-ffmpeg unrar w64codecs**
 
**[COLOR=DarkRed]64-Bit Xubuntu Users:[/COLOR]**
 
**sudo apt-get install alsa-oss icedtea-gcjwebplugin libflashsupport liblame0 libxine1-ffmpeg unrar w64codecs**
 
[COLOR=DarkRed]**Kubuntu Users:**[/COLOR] I didn't feel it was suitable to add the command to install the CCSM package above. Go [here]("https://help.ubuntu.com/community/CompositeManager/CompizFusion") for instructions on what you need to enable Compiz Fusion on your system.


**[COLOR=DarkRed]PRE-UBUNTU FAMILY 8.04 HARDY HERON USERS ONLY[/COLOR]**


**[COLOR=DarkRed]32-Bit Ubuntu Users:[/COLOR]**
 
**sudo apt-get install alsa-oss compizconfig-settings-manager faad gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 sun-java6-fonts sun-java6-jre sun-java6-plugin unrar w32codecs**
 
**[COLOR=DarkRed]32-Bit Kubunu Users:[/COLOR]**
 
**sudo apt-get install alsa-oss libk3b2-mp3 liblame0 libtunepimp5-mp3 libxine1-ffmpeg sun-java6-fonts sun-java6-jre sun-java6-plugin unrar w32codecs**
 
**[COLOR=DarkRed]32-Bit Xubuntu Users:[/COLOR]**
 
**sudo apt-get install alsa-oss liblame0 libxine1-ffmpeg sun-java6-fonts sun-java6-jre sun-java6-plugin unrar w32codecs**
 
**[COLOR=DarkRed]64-Bit Ubuntu Users:[/COLOR]**
 
**sudo apt-get install alsa-oss compizconfig-settings-manager faad gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse icedtea-java7-jre icedtea-java7-plugin liblame0 unrar w64codecs**
 
**[COLOR=DarkRed]64-Bit Kubuntu Users:[/COLOR]**
 
**sudo apt-get install alsa-oss icedtea-java7-jre icedtea-java7-plugin libk3b2-mp3 liblame0 libtunepimp5-mp3 libxine1-ffmpeg unrar w64codecs**
 
**[COLOR=DarkRed]64-Bit Xubuntu Users:[/COLOR]**
 
**sudo apt-get install alsa-oss icedtea-java7-jre icedtea-java7-plugin liblame0 libxine1-ffmpeg unrar w64codecs**
 
[COLOR=DarkRed]**Kubuntu Users:**[/COLOR] I didn't feel it was suitable to add the command to install the CCSM package above. Go [here]("https://help.ubuntu.com/community/CompositeManager/CompizFusion") for instructions on what you need to enable Compiz Fusion on your system.


**[COLOR=Red]DID YOU HAVE ERRORS?[/COLOR]**


If you had errors while trying to do the above, one of these following commands may help. Did the Terminal tell you to run "dpkg --configure -a"? All you have to do is add "sudo" to the front of that command, like so:

**sudo dpkg --configure -a** 

Or if it was the install -f command:

**sudo apt-get install -f**

Was that not the error you had? You may have a currupt apt list due to an interrupted "apt-get update". Try these commands instead:

**sudo rm /var/lib/apt/lists/partial/***

**sudo apt-get update**

Now try repeating the command to install the restricted packages for your particular Ubuntu variant.
 
 
**[COLOR=darkred]--PART 2/5, STREAMING WITH FIREFOX--[/COLOR]**
 
 
You may already be happy with your streaming after installing the packages in Part 1, but if you want advanced playback and features, I recommend you give the MPlayer plugin a try:
 
**sudo apt-get remove totem-mozilla mozilla-plugin-vlc xine-plugin kaffeine-mozilla helix-player mozilla-helix-player**
 
**sudo apt-get install mplayer mozilla-mplayer**
 
[COLOR=DarkRed]**Please Note:**[/COLOR] New users of Ubuntu or MPlayer should open the main MPlayer application after installing it for the first time, this will then cause it to create it's default folder in your home directory. Also, please navigate to Preferences>Audio in MPlayer, and then tick the "Enable Software Mixer" option. 

**[COLOR=DarkRed]Option 1 - 32/64-Bit Ubuntu Family Users - All Versions:[/COLOR]** MPlayer will stream virtually all media formats, the most simple method and works on both 
 architectures. Paste either of these commands into the Terminal: (Substitute "gedit" for "kwrite" if you are using Kubuntu and "mousepad" if you are an Xubuntu user)

**gedit $HOME/.mplayer/mplayerplug-in.conf**
 
or if you have multiple users and want them all to use this method for streaming:
 
**gksudo gedit /etc/mplayerplug-in.conf**
 
If you chose to edit the "/etc/" file, please remove the settings already present and make sure that the "$HOME" version is blank or deleted in all user accounts. Now you need to  paste the following settings into the configuraton file:
 
[B]download=1
cachesize=1024
cache-percent=25
keep-download=0
dload-dir=$HOME
noembed=0
autoplay=1
enable-wmp=1
enable-qt=1
enable-rm=1
enable-gmp=1
enable-dvx=1
enable-mpeg=1
enable-mp3=1
enable-midi=0
enable-pls=1
enable-ogg=1
enable-smil=1
enable-helix=1
nomediacache=0
nopauseonhide=1
black-background=1
rtsp-use-http=0
rtsp-use-tcp=0[/B]
 
Close and save the file, then paste this important command into the Terminal:
 
**rm $HOME/.mozilla/firefox/pluginreg.dat** (Firefox recreates it with the updated plugin information).
 
**[COLOR=darkred]Options 2 - 32-Bit Pre-Ubuntu 8.04 Hardy Heron Users Only:[/COLOR]** MPlayer will stream most formats still, but RealPlayer will handle it's native formats. This is a slightly more complicated method and some users may initially have problems with RealPlayer. Also, this method is more suited for 32-Bit users, as RealPlayer isn't packaged for 64-Bit systems. RealPlayer isn't in the repos, so download it [here]("http://archive.canonical.com/ubuntu/pool/partner/r/realplay/realplay_10.0.9-0feisty1_i386.deb"). Don't worry that it's packaged for Fiesty, it should work and install fine. You can remove it in Synaptic or with "sudo dpkg -r realplay". Install it by double or single-clicking on the deb, or by using the right-click context menu. Type your password when prompted.
 
Now that you have installed RealPlayer, we need to configure MPlayer so that it can work together with the RealPlayer browser plugin. Paste either of these commands into the Terminal: (Substitute "gedit" for "kwrite" if you are using Kubuntu and "mousepad" if you are an Xubuntu user)

**gedit $HOME/.mplayer/mplayerplug-in.conf**
 
or if you have multiple users and want them all to use this method for streaming:
 
**gksudo gedit /etc/mplayerplug-in.conf**
 
If you chose to edit the "/etc/" file, please remove the settings already present and make sure that the "$HOME" version is blank or deleted in all user accounts. Now you need to paste the following settings into the configuraton file:
 
[B]download=1
cachesize=1024
cache-percent=25
keep-download=0
dload-dir=$HOME
noembed=0
autoplay=1
enable-wmp=1
enable-qt=1
enable-rm=0
enable-gmp=1
enable-dvx=1
enable-mpeg=1
enable-mp3=1
enable-midi=0
enable-pls=1
enable-ogg=1
enable-smil=0
enable-helix=0
nomediacache=0
nopauseonhide=1
black-background=1
rtsp-use-http=0
rtsp-use-tcp=0[/B]
 
Close and save the file, then paste this important command into the Terminal:
 
**rm $HOME/.mozilla/firefox/pluginreg.dat** (Firefox recreates it with the updated plugin information).

"Keep-download" is an easy way to save streaming media, just change the value to "1" and it will then download to your home directory. For an explaination of what the other settings do check out this [link]("http://mplayerplug-in.sourceforge.net/config.php").
 
[COLOR=DarkRed]**Note:**[/COLOR] Please [COLOR=DarkRed]**REBOOT**[/COLOR] if you are not carrying on with the rest of the how-to, as you have made lot's of changes to your system and could have some strange problems until you start a fresh session. If you still have problems after rebooting with certain applications, please read the "Troubleshooting" section at the bottom.
 
 
[COLOR=DarkRed]**--PART 3/5, SOUND & VIDEO CONVERSION--**[/COLOR]
 
 
**[COLOR=DarkRed]SOUND CONVERSION[/COLOR]**


It is not recommended to convert one group of compressed music files of a certain format, to another type of compressed format. However, if you wish to do so, you can accomplish most tasks with Sound Converter, OggConvert or Sound Konverter. Some GNOME users prefer Sound Konverter despite the fact it is a KDE application (perhaps because it's had better support for AAC audio, such as iTunes music files). Install whichever varient you wish, but make sure you have completed Part 1 of this how-to first:

**sudo apt-get install soundconverter oggconvert**

or the KDE varient:

**sudo apt-get install soundkonverter aacplusenc alac-decoder cdparanoia faac ffmpeg flac lame vorbis-tools**

If you want to try and convert a large number of iTunes m4a files, and keep as much tag information as possible, please refer to this [page]("http://pragmattica.wordpress.com/2008/01/17/convert-itunes-m4a-files-to-mp3-on-linux/").

Tag editing can be done in various music applications, but if you want to try a dedicated tag editor, install Ex Falso:

**sudo apt-get install exfalso**

You may also want to try EasyTag:

**sudo apt-get install easytag easytag-aac**

Kubuntu users might want to install KID3 instead:

**sudo apt-get install kid3**


**[COLOR=DarkRed]VIDEO CONVERSION[/COLOR]**


For video converting, first make sure you have these packages installed:
 
**sudo apt-get install ffmpeg faac**
 
Then download a GUI frontend for FFmpeg called [WinFF]("http://biggmatt.com/winff/"). Install it by double or single-clicking on the deb, or by using the right-click context menu. Type your password when prompted.
 
To make a video for a mobile phone in WinFF, select 3g2 as the type of video you want to make. Use 3gp if you want (doesn't work for me right now however). To increase the audio quality, click on "Options" and in the "Audio Bit Rate" box type "96000" (default is 64000, which is 64kbps). However, your phone might not play it properly with the audio at 96kbps for video, depends really. Test it yourself. For some reason, when you type in the "Video Bit Rate" box to change the default setting, you only have to type in "180" (for example), instead of "180000. I'm not sure why. Also, you may need to change the extension from "3g2" to "mp4" or "3gp" in order for it to play. I suggest mp4 as this worked flawlessly on my W810i, but only with the default settings for some reason. I'd appreciate some feedback on how the videos work on other handsets.

 
[COLOR=darkred]**--PART 4/5, DVD PLAYBACK/RIPPING/BURNING--**[/COLOR]
 
 
**[COLOR=darkred]PLAYBACK[/COLOR]**
 
 
To stop Ubuntu asking for the installation CD when you install these next packages, navigate to System>Administration>Software Sources and untick the CD-ROM/DVD source, or open the Terminal and do the following:
 
**gksudo gedit /etc/apt/sources.list**
 
Go to the line which starts as "deb cdrom" (at the top in my sources list) and just put a # before it. Close and save the file.
 
For the best DVD playback in Ubuntu, including menu support, install this cross-format media player:
 
**sudo apt-get install vlc** 
 
You can also use the Xine engine in Ubuntu for video/DVD playback. This can be done without having to change the backend of Totem -  just install an alternative GNOME frontend for Xine called Gxine (this is optional, VLC will do just fine):
 
**sudo apt-get install gxine libxine1-ffmpeg**
 
To get encrypted DVDs playing properly (check out no. 9 in the "Troubleshooting" section if you are having problems with new DVDs), paste these commands into the Terminal:
 
**sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 build-essential debhelper fakeroot**
 
then:
 
**sudo /usr/share/doc/libdvdread3/install-css.sh**
 
or if you get an error with that command:
 
**sudo /usr/share/doc/libdvdread3/examples/install-css.sh**
 

**[COLOR=DarkRed]VLC AS DEFAULT DVD PLAYER IN UBUNTU 8.04 HARDY HERON SYSTEMS[/COLOR]**


To change the default DVD player in Hardy Heron to VLC (I strongly advise you do), open the Terminal and copy and paste this command into it:          

**gksudo gedit /etc/gnome/defaults.list**
 
Press Ctrl+f and search for "x-content/video", then change the "totem.desktop" entries to "vlc.desktop". Close and save.
 
Next, right-click on "Applications" in the top panel and select "Edit Menus" to open the default menu editor. Navigate down to "Sound & Video" in the left pane and click on it to show all those applications in the pane to the right. Scroll down the list of applications displayed until you see "VLC media player", right-click on it, then click on "Properties" in the context menu to open "Launcher Properties" and change the launch command from "wxvlc %F" to:
 
**vlc --vout-filter deinterlace --deinterlace-mode blend --volume 512 --fullscreen %m**
 
Close the VLC properties dialog and exit the menu editor. Finally, navigate to Nautilus>Edit>Preferences>Media>DVD Video and  select VLC.
 

**[COLOR=DarkRed]VLC AS DEFAULT DVD PLAYER IN PRE-UBUNTU 8.04 HARDY HERON SYSTEMS[/COLOR]**


To set VLC as your default DVD player in a pre-Hardy Heron systems, navigate to  System>Preferences>Removable Drives and Media>Multimedia and replace the existing “Video DVD Discs” command ("totem %m") with:

**vlc --vout-filter deinterlace --deinterlace-mode blend --volume 512 --fullscreen %m**

If you don't want VLC to automatically launch into fullscreen when a DVD movie is inserted, all you have to do is delete the "--fullscreen" part of the command. To exit and enter fullscreen in VLC, just press the "f" key.
 
 
**[COLOR=darkred]RIPPING[/COLOR]**
 
 
You can rip a standard disc image by right-clicking on the disc icon and then selecting the "Write to Disk" option in the context menu. Alternatively, you can open it with your file browser and drag the ISO image to your desktop. For more advanced options, give dvd::rip a try:
 
**sudo apt-get install dvdrip**
 
Kubuntu users might be interested in this application instead:
 
**sudo apt-get install k9copy**
 
 
**[COLOR=darkred]BURNING[/COLOR]**
 
 
Basic burning can be done by right-clicking on an ISO image and then selecting the "Write to Disc" option in the context menu. If you want to burn DVDs for use in standard DVD players, then your best bet is an application called Tovid. Go to the Tovid [Wiki]("http://tovid.wikia.com/wiki/Installing_tovid/Ubuntu") and download the deb file, then just double or single-click to install, or use the right-click context menu. Type your password when prompted. Also, read this [guide]("http://tovid.wikia.com/wiki/Using_the_tovid_GUI#Usage") on using the Tovid GUI and another [guide]("http://ubuntuforums.org/showthread.php?t=183936") on the basics of using Tovid.
 
[COLOR=DarkRed]**Note:**[/COLOR] If you wish to change the region of a DVD drive so you can play/rip foreign discs, you will need to install the following terminal based application:
 
**sudo apt-get install regionset**
 
Please be aware that most drives limit you to about 5 changes (regionset should tell you how many you have left). So maybe it's best to have a secondary external DVD drive and have it set to a different region to the one in your machine. To make the change, put any disc into your drive and type "sudo regionset" into the Terminal and change the region. Here is the list of region codes and which countries they cover:
 
RC1 = North America (USA and Canada) 
RC2 = Europe, Middle East, South Africa and Japan 
RC3 = Southeast Asia, Taiwan, Korea 
RC4 = Latin America, Australia, New Zealand 
RC5 = Former Soviet Union (Russia, Ukraine, etc.), rest of Africa, India 
RC6 = China 


[COLOR=darkred]**--PART 5/5, MISCELLANEOUS & TROUBLESHOOTING--**[/COLOR]
 

**[COLOR=DarkRed]--MISCELLANEOUS--[/COLOR]**


**[COLOR=DarkRed]TOUCHPAD TIPS & TRICKS[/COLOR]**


Using a laptop? If your cursor shoots off all over the place when you type, you might want to (carefully) do the following:

**gksudo gedit /etc/X11/xorg.conf** 

Now find the section concerning your touchpad and copy the bold text below into your conf file, so it look similar to the example below:

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"    "/dev/psaux"
    Option        "Protocol"    "auto-dev"
    Option        "HorizEdgeScroll"    "0"
        **Option          "SHMConfig"             "on"**
EndSection

Make sure it all looks okay and that the "EndSection" text is in the right place, then close and save. Now, navigate to System>Preferences>Sessions and click on "Add". Name it something like "Touchpad Syndaemon", the description can be "Disables touchpad while typing", and the all important command you need is "syndaemon -i .5 -d". For it to take effect, **[COLOR=DarkRed]REBOOT[/COLOR]**. Why isn't it default for laptop users? Well, apparently it's insecure. If you share your laptop with others, technically they could disable your touchpad. Personally, I think there should be an option in System>Preferences>Mouse to enable this feature, with a warning if necessary.


**[COLOR=DarkRed]FONTS TIPS & TRICKS[/COLOR]**


I always insist my fonts are used instead of webpage defaults (Firefox>Preferences>Content>Fonts & Colours>Advanced) and I also increase the minimum font size to "12", that might interest some of you. Make sure you're using DejaVu (Ubuntu default) in Firefox, msttcorefonts are pointless and redundant in my opinion now, so no need to install and use them. I also recommend setting all the font sizes to 9 in System>Preferences>Appearance>Fonts.


**[COLOR=DarkRed]APPLICATIONS & GAMES[/COLOR]**


View and fill in PDF forms online with Adobe Reader and it's browser plugins:

**sudo apt-get remove mozplugger && sudo apt-get install acroread-plugins mozilla-acroread**

Give these audio players a try:
 
**sudo apt-get install exaile audacious** 
 
Exaile is a GTK fork of Amarok and Audacious is a nice small and simple Winamp style audio player. You might also like to try a newish and unfinished jukebox-like media player called [Songbird]("http://www.getdeb.net/app/Songbird"). Just download the correct version for your architecture and give it a whirl. To install the downloaded deb package, just double or single-click on it, or install using the right-click context menu. Type your password when prompted to do so.
 
You might be interested in having Google Earth too:
 
**sudo apt-get install googleearth**
 
For P2P file sharing, give [Frostwire]("http://www.frostwire.com/?id=downloads") a try. Always worked pretty well for me. To install the deb package, just double or single-click on it , or use the right-click context menu. Type your password when prompted.
 
If you want an easy way to edit usplash (Ubuntu loading screen) then you have to try this application:
 
**sudo apt-get install startupmanager**
 
It installs into System>Administration. Keep the colour depth to 16-Bits or you may experience strange shutdown behaviour.
 
Don't forget to check out some of the games in Synaptic. Briquolo is fun, try that. Some games will not create menu entries, make them yourself if that happens (the name of the game is often the command to launch it). 
 
 
**[COLOR=darkred]--TROUBLESHOOTING--[/COLOR]**
 
 
[COLOR=DarkRed]**1.**[/COLOR] If your RealPlayer's playback is terrible (mine was) you have to do some manual editing. First of all, install "alsa-oss" (added to "Essential" in Part 1). Now you need to copy and paste these commands into the Terminal and do some manual editing:
 
**gksudo gedit /usr/bin/realplay**
 
Find the line "echo "Warning: LD_PRELOAD=\"$LD_PRELOAD\"" and underneath "fi" paste these two lines:
 
**LD_PRELOAD="$LDPRELOAD:/usr/lib/libaoss.so"**
**export LD_PRELOAD**
 
Save and close. Also, open RealPlayer's preferences and go to "Transport" and select "Use specified transport". Then go into the two configure options beneath that and untick everything except "http". You can also select your connection speed in preferences and tell RealPlayer not to send connection info back to real.com.
 
[COLOR=DarkRed]**2.**[/COLOR] Sometimes you will click on a video link and Firefox will ask if you want to download it or open it with a certain application. Many times though, you will want to play or open it with a different application to the one offered. Click to choose your own application and navigate to /usr/bin and you will find your audio and video apps there.
 
[COLOR=DarkRed]**3.**[/COLOR] Use the "xv" video driver if you can. Open MPlayer and right click on the video window, then click on "Preferences". Click on the "Video" tab and select "xv", or if you can't use that try "gl". As a last restort you should select "x11" (unaccelerated). [COLOR=DarkRed]**Please note:**[/COLOR] If you are having trouble using the "xv" video driver, you should search the forums and google as it's highly unlikely your card doesn't support it. Some users have to make a few changes to get it working.
 
[COLOR=DarkRed]**4.**[/COLOR] Sometimes MPlayer looks like it is about to start playing a video, but it does not. Try pressing play and don't just give up and navigate away. BBC wmv radio streams take a long time to start playing, the ram streams start quicker and sound better.
 
[COLOR=DarkRed]**5.**[/COLOR] If Firefox doesn't recognise that you have changed your plugins and says "Plugin Required", or something like that, then you need to:
 
**rm $HOME/.mozilla/firefox/pluginreg.dat**
 
You have to do this **[COLOR=DarkRed]EVERYTIME[/COLOR]** you change plugins or edit your mplayerplug-in.conf file. Then open Firefox and type [noparse]"about:plugins"[/noparse] in the address bar and press enter. You should now see a very long list of plugins (Java, Flash, RealPlayer, Windows Media etc).
 
[COLOR=DarkRed]**6.**[/COLOR] Are you using a non-default web browser? You may need to link your plugins folder to that browser. To create a symbolic link, you need to do something like this "ln -s /usr/lib/firefox/plugins /fullpathtobrowser". Rename or delete the plugins folder it already has, or use the "ln -sf" symlink command as it forces the link to replace whatever plugins folder is already present.

[COLOR=DarkRed]**7. **[/COLOR]Having problems with the Adobe Flash plugin after updating? Close Firefox, then cut and paste this command into the Terminal:
 
**sudo apt-get purge flashplugin-nonfree && sudo apt-get install flashplugin-nonfree**

Also, if you don't have any sound in flash videos or you notice strange random behaviour by Firefox, you should try this next solution. Make sure you have the package "alsa-oss" from Part 1 and then paste this command into the Terminal:
 
**gksudo gedit /etc/firefox/firefoxrc**
 
Edit the line "FIREFOX_DSP=”none”" and change "none" to "aoss". Then close and save the file. Restart Firefox.
 
Still having issues? If you're a 64-Bit Ubuntu user, you might get better results using an older version of Adobe Flash. Please refer to the following [thread]("http://ubuntuforums.org/showthread.php?t=476924&highlight=gnash") and use the recommended script.

[COLOR=DarkRed]**8.**[/COLOR] Java not working correctly? Close Firefox and then try this command below. Make sure you select the latest Java, which will be somewhere in /usr/lib:
 
**sudo update-alternatives --config java**
 
Still no go? Ubuntu 32-Bit users who are trying to use Sun Java might want to make sure they don't have IcedTea/OpenJDK Java and it's plugin installed, as it will conflict with the Sun Java plugin:

**sudo apt-get remove icedtea-java7-bin icedtea-java7-jre icedtea-java7-plugin icedtea-gcjwebplugin openjdk-6-jre**

Same goes for 64-Bit users trying to use IcedTea/OpenJDK Java, it might be a good idea to check you don't have any version of Sun Java installed and it's relevant plugin:
 
**sudo apt-get remove sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin sun-java5-bin sun-java5-fonts sun-java5-jre sun-java5-plugin**
 
If you have followed those steps and still can't get IcedTea Java applets working properly, it may be worth adding the unofficial repository for Gutsy, which can be done in System>Administration>Software Sources in Ubuntu, or the command line way:

**gksudo gedit /etc/apt/sources.list**

Then copy and paste these two lines into it:

[B]deb [noparse]http://people.ubuntu.com/~doko/ubuntu/[/noparse] gutsy/
deb-src [noparse]http://people.ubuntu.com/~doko/ubuntu/[/noparse] gutsy/[/B]

Make sure you save your changes, then perform a "sudo apt-get update", or alternatively just reload Synaptic/Adept. After you have refreshed your list of packages you can perform a "sudo apt-get upgrade", or just wait for the update manager to realise there are updates. IcedTea Java will be updated and hopefully work much better than previously.
 
[COLOR=DarkRed]**9.**[/COLOR] Are you having trouble with new DVDs? Please refer to this [link]("http://tobias.rautenkranz.ch/libdvdread_ifo.html") and concentrate on the solution for VLC.
 
[COLOR=DarkRed]**10.**[/COLOR] Still have problems? [COLOR=DarkRed]**REBOOT**[/COLOR]. You have made lots of changes to your system.
 
Enjoy,
 
Nathan

---

### Post by K.Mandla on 2008-01-09
Moved to Multimedia and Video.

Edit: Renamed at the OPer's request.

---

### Post by ubuntu-freak on 2008-01-10
Moved to post above.

Nathan

---

### Post by MaxVK on 2008-01-11
Sorry to re-open an older thread, but Id just like to ask why you suggest NOT installing Java6 and instead using Java5? I'm about to install the restricted extras and Id like to know why this is.

Thanks

Max

> **reassuringlyoffensive said:**
> An easy way to install all restricted formats (codecs, fonts, java) is the following command
 
**sudo apt-get install ubuntu-restricted-extras**

I suggest you do it through synaptic and stop it installing sun java6 and select java5 instead (fonts, plugin, jre)


Nathan

---

### Post by ubuntu-freak on 2008-01-11
I've done some more research on sun java6 and it seems that it works okay now with most apps. I will remove my slightly outdated advice. :)
 
Nathan

---

### Post by MaxVK on 2008-01-11
Ah, many thanks for the reply and the information.

---

### Post by ubuntu-freak on 2008-01-11
Some more advice for ya.
  
Be patient with radio streams as some take a while to start playing even with fast connections, that goes for some video streams too. Don't want you navigating away thinking it wont play.
 
Nathan

---

### Post by msrk on 2008-01-11
The solution posted by Nathan (reassuringlyoffensive) is simple and great.

---

### Post by ubuntu-freak on 2008-01-12
> **msrk said:**
> The solution posted by Nathan (reassuringlyoffensive) is simple and great.

 
Thanks man.:)
 
If anyone has an issue with a hanging usplash and they have a windows partition, try my other how-to.
 
[http://ubuntuforums.org/showthread.php?t=663214](http://ubuntuforums.org/showthread.php?t=663214) 
 
Nathan

---

### Post by mount_evans on 2008-01-12
> **reassuringlyoffensive said:**
> I've done some more research on sun java6 and it seems that it works okay now with most apps. I will remove my slightly outdated advice. :)
 
Nathan

I have followed the advice on this thread, and first of all:  I can listen to web radio!  WooHoo!  But the next time I went scanning for updates I get the following message:

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

According to Synaptic, the broken package is indeed sun-java-6-bin.  Untill I get it fixed, I can't download any more updates.  However, the message doesn't tell me what to ***do*** in Synaptic; I'm afraid that if I remove sun-java-6-bin I may undo whatever your fix does.  I tried the command listed, and it puts me into some thing with a prompt that clearly expects input from me, and I have no idea what it wants me to do.

In case you haven't noticed, I know nothing about the magic box on my desk, I just try to avoid pissing off the Fairies that live in it.  I was told that Ubuntu is safe for people like me; so far, it's doing a lot better than SuSE did, thanks largely in part to people like Nathan.

So, any suggestions?

---

### Post by ubuntu-freak on 2008-01-12
Glad my guide helped. 
 
I read java6 was broken in Hardy and not Gutsy. Did you 
 
sudo apt-get install -f
 
? You should apt-get update before that though. 
 
Nathan

---

### Post by mount_evans on 2008-01-12
Thank you, reassuringlyoffensive.  I will thank you electronically as soon as I can figure out how to do that.  (The word "thank" does not appear in the About file or the FAQ.)  When I go to a web radio station, I am usually given three choices, Windows Media, MP3, and a third one (aaccPlus) that I've never heard of.  The second two options have never worked in Windows, so I am not surprised that they still don't work in Ubuntu; Firefox always wants to open the MP3 as a file in a player rather than do something streamy with it.  The first option though, Windows Media, plays just fine with mplayer using your fix.  The only thing I am missing is the little rectangle that would have contained the stop, pause, play, and volume controls; instead I get a black rectangle with the words "No video".  I can live with that, but is there a tweak that would give me access to these controls?

---

### Post by mount_evans on 2008-01-12
Whoops, I posted another reply upthread before I saw this.  OK, I tried this fix for the broken Java 6, and got the following reply:

dpkg: serious warning: files list file for package `sun-java6-bin' missing, assuming package has no files currently installed.
91228 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 9.0.115.0ubuntu0.7.10 (using flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb) ...
Unpacking replacement flashplugin-nonfree ...
Setting up flashplugin-nonfree (9.0.115.0ubuntu0.7.10) ...
Installing from local file /var/cache/flashplugin-nonfree/install_flash_player_9_linux.tar.gz
Flash Plugin installed.

Mplayer still works, but Java 6 is still broken.

---

### Post by ubuntu-freak on 2008-01-12
Did you need to replace the flash plugin? Didn't youtube work?
 
Which site doesn't show controls? Have you tried others? 
 
Java6 IS broken? Holy moly. Go to synaptic and remove java6 bin, fonts, jre and plugin then install java5 plugin, jre and fonts.
 
To thank someone you just click on the ribbon next to 'Quote' on the right. 
 
Hope that helps.
 
Nathan

---

### Post by jonno on 2008-01-12
> **reassuringlyoffensive said:**
> Glad my guide helped. 
 
I read java6 was broken in Hardy and not Gutsy. Did you 
 
sudo apt-get install -f
 
? You should apt-get update before that though. 
 
The flash plugin is broken in the repo for now.
Here is a temporary solution.

Download it here [http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466")

Save it to your home folder, then open the terminal and paste this: 

sudo dpkg -i flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb
 
Hope that helps those of you unable to fetch it from the repo.
 
Nathan

Hmm, I can't install that package on my 64bit machine. Any ideas?

---

### Post by ubuntu-freak on 2008-01-12
Try this thread
 
[http://ubuntuforums.org/showthread.php?t=617142&highlight=flashplugin+64bit](http://ubuntuforums.org/showthread.php?t=617142&highlight=flashplugin+64bit)
 
You can use some 32bit apps but you need some packages to be installed.
 
Is your flash actually broken? Did you install the restricted extras? Not sure if 64bit flash is broken.

Read here too
 
[http://ubuntuforums.org/showthread.php?t=547431](http://ubuntuforums.org/showthread.php?t=547431) 

Nathan

---

### Post by ubuntu-freak on 2008-01-12
Hey mount_evans did you try installing java6 after you did install -f? Is it broken for sure?
 
Nathan

---

### Post by mount_evans on 2008-01-12
I really made a mess of things here; let me sort them out.

> **reassuringlyoffensive said:**
> Did you need to replace the flash plugin? Didn't youtube work?

Youtube works just fine.  I did the (unnecessary) flash plugin fix because the instructions appeared underneath a statement about Java6 being broken.  I had no idea what I was doing.  Apparently it had nothing to do with the bug I was trying to fix.
 
> Which site doesn't show controls? Have you tried others? 

[www.kcfr.org](www.kcfr.org) and [www.am760.net](www.am760.net) so far; maybe it only applies to left-wing radio stations.
 
> Java6 IS broken? Holy moly. Go to synaptic and remove java6 bin, fonts, jre and plugin then install java5 plugin, jre and fonts.

I went looking for java6 fonts, jre, and plugin and they weren't there; a little lightbulb went on over my head so I marked them for installation and the original java6 bin for "updating", and nothing claims to be broken now.

 
> To thank someone you just click on the ribbon next to 'Quote' on the ribbon

Thank you again.

---

### Post by ubuntu-freak on 2008-01-12
Oh dear! I wasn't misleading was I? The flash fix is for recent Ubuntu installs only.
 
Java6 is fine? Great! Test it at yahoo games and see for sure.
 
The controls thing could be poor site design. Test it at

[www.bbc.co.uk](www.bbc.co.uk)  or [www.bbc.com](www.bbc.com)
 
Nathan

---

### Post by buccaneere on 2008-01-12
[HTML]sudo apt-get update[/HTML] ...returned this:

[HTML]W: GPG error: http://packages.medibuntu.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
[/HTML]

Soooo ... what do I do?


EDIT:
I did update again; same result, and continued ...

Now, how do I ascertain removal of these guys?
[HTML]Also, make sure you completely remove vlc and totem mozilla plugins as they conflict with mplayer.[/HTML]

---

### Post by ubuntu-freak on 2008-01-12
Are you still using Fiesty?
 
Did you paste the wget key thing in the terminal? It's detailed in that first link.
 
How do you know if vlc and totem plugins are removed? If you pasted sudo apt-get remove then they are.
 
Hope you get it working. 
 
Nathan

---

### Post by taheck_ifiknow on 2008-01-13
OK total linux noob here...bear with me folks,

i did the 'sudo apt-get install ubuntu-restricted-extras' line and it downloaded and was in the process of unpacking and well... the configuration page came up for java 6 and i didn't know what to do with it so i closed the terminal thinking it was done as i didn't see any prompts for input on my part and now when i goto install another package i get :

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

so i type in that just as it says and then it tells me: 

dpkg: requested operation requires superuser privilege 

it gives me this when i open my package manager as well...so i tried 'dpkg -C and it tells me that Java6 wasn't configured and needs reinstalled! ack! 

sorry for the long post friends....i know i have a lot of learning to do...

by the way this is a fresh install of ubuntu on its own hard drive with all the updates to today installed...i was just trying to get my mplayer to show me more than an blank screen and error messages :)

---

### Post by ubuntu-freak on 2008-01-13
You have to put sudo at that start mate. Whenever you install, remove, configure etc in the terminal. 
 
Try
  
**sudo apt-get --reinstall install ubuntu-restricted-extras**
 
Pay attention to the java6 prompt and just do what it says. It will say you need another package, but don't worry as it will be installed automatically.
 
Nathan

---

### Post by taheck_ifiknow on 2008-01-13
> **reassuringlyoffensive said:**
> You have to put sudo at that start mate. Whenever you install, remove, configure etc in the terminal. 
 
Try
  
**sudo apt-get --reinstall install ubuntu-restricted-extras**
 
Pay attention to the java6 prompt and just do what it says. It will say you need another package, but don't worry as it will be installed automatically.
 
Nathan

OK just tried that...got this again:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

when i first installed it the terminal went blue (looked like the old DOS type installation screens) and at the bottom of the licence agreement was <OK> but i coudn't click or select it in any way and i didn't know how to proceed... so i just closed it lol ](*,)

---

### Post by ubuntu-freak on 2008-01-13
Have you tried configure -a whatever it is with sudo at the start? That's what superuser is.
 
You couldn't click on ok? Try reinstalling it with synaptic instead. Just search for 'ubuntu restricted' Or see if pressing enter lets you proceed.
 
Didn't it let you apt-get remove?
 
Nathan

---

### Post by taheck_ifiknow on 2008-01-13
> **reassuringlyoffensive said:**
> Have you tried configurd -a whatever it is with sudo at the start? That's what superuser is.
 
You couldn't click on ok? Try reinstalling it with synaptic instead. Just search for 'ubuntu restricted' 
 
Nathan

OK i'll do that... tomorrow hehe as i am jiggered. My synaptic gives me a similar error to the terminal, but, i haven't tried the sudo command on the config yet so maybe i'll muck about with it some more tomorrow and if all else fails i'll just reinstall ubuntu.  I thank you for your help mate and bid you good night from the states! :)

PS: Red Dwarf Rules!

---

### Post by ubuntu-freak on 2008-01-13
Lol how can you sleep on it? It will take 5 mins anyway.
 
Reinstall Ubuntu??? You will NOT need to do that matey. Trust me. 
 
Nathan

---

### Post by taheck_ifiknow on 2008-01-13
well what ya know? it worked! my synaptic is accessable again! whew! says i still have a broken package but i can find it and fix it (i think) at any rate its not closing on me lol.  Yep i just had to sudo the config command and it worked! thanks a bunch Nathan!

---

### Post by slymi2005 on 2008-01-13
What should the configurations be set to when you right click?

---

### Post by ubuntu-freak on 2008-01-13
Right click where? Don't know what you mean.
 
Nathan

---

### Post by slymi2005 on 2008-01-13
For example at apple.com/trailers when you click to watch a trailer the area where the video is. You right click that and it says configure at the bottom of the list.

---

### Post by ubuntu-freak on 2008-01-13
Are you having problems? You shouldn't have to configure that. I never have.
 
Nathan

---

### Post by slymi2005 on 2008-01-13
well when its probably just me but when I click to watch a trailer in medium size it will play for the first 24 seconds and then stop, also the sound and the video are not in line, the video is slower than the sound. But when I choose small size it plays fine.

---

### Post by ubuntu-freak on 2008-01-13
Open MPlayer, go to preferences and then the video driver tab. Select XV, sounds like you are using X11 at the moment.
 
Nathan

---

### Post by slymi2005 on 2008-01-13
well it started out fine and it played longer but then failed after about 50 seconds.

---

### Post by ugm6hr on 2008-01-14
I have just been reading this: [http://ubuntuforums.org/showpost.php?p=4130151&postcount=12](http://ubuntuforums.org/showpost.php?p=4130151&postcount=12)

I followed this how-to, and Quicktime stuff works flawlessly.

But Realmedia on BBC / wmv doesn't allow seeking - which I think is OK for me.

But that post states that Helix has superceded Realplayer (I realise that Realplayer is based on Helix), but I though Helix did not have codecs to play realmedia (and hence the difference).

In any case, Firefox plays **all** BBC streams (wmv / rm) via mplayer now.

Should it be using Helix?  If so, what have I done wrong?

PS: Your how-to should also instruct you to remove xine mozilla plugin too, and even kaffeine plugin (since I had installed every media player to get this working!)

---

### Post by ubuntu-freak on 2008-01-14
> **ugm6hr said:**
> I have just been reading this: [http://ubuntuforums.org/showpost.php?p=4130151&postcount=12](http://ubuntuforums.org/showpost.php?p=4130151&postcount=12)

I followed this how-to, and Quicktime stuff works flawlessly.

But Realmedia on BBC / wmv doesn't allow seeking - which I think is OK for me.

But that post states that Helix has superceded Realplayer (I realise that Realplayer is based on Helix), but I though Helix did not have codecs to play realmedia (and hence the difference).

In any case, Firefox plays **all** BBC streams (wmv / rm) via mplayer now.

Should it be using Helix?  If so, what have I done wrong?

PS: Your how-to should also instruct you to remove xine mozilla plugin too, and even kaffeine plugin (since I had installed every media player to get this working!)

 
Thanks for your tips.
 
Helix doesn't come shipped with propriatry support, but I'm sure it can utilise codecs in the win32codecs package. I'm gonna do more tests. I might end up recomending reals realplayer. Ram radio on the BBC worked once I installed the Helix plugin though.
 
Nathan

---

### Post by TWO on 2008-01-14
> **reassuringlyoffensive said:**
> Where does it tell you that you need plugins? Do you have my settings and all plugins, codecs? 
 
Realplayer is now Helix. That's why you can't find it the repo. Helix plays my radio streams fine.
 
Can you reply in my how-to thread? Keeps it alive.
 
Nathan

> **TWO said:**
> When I click on a media link, be that radio or video and select the rm. stream option, the window appears where the stream should (eventually) play but what I get instead is a message at the top of the window in a yellow bar saying "additional plugins are required to display all the media on this page,"  with a grey button with "install missing plugins" to the right.

On the part of the page where the stream should be, all I get is a green jigsaw piece and below it, the message: "click here to download plugin." 

I have all the settings and plugins/ codecs that you suggested, including the modification of the configuration file of mplayer. The result is better .wmv streaming on the BBC website- albeit after clicking full screen and the back again- but as far as .rm streams are concerned, it's screaming that there are no plugins. 

Real media seems to be a real pain in the you know what on Ubuntu....

(This is the answer to your question in the thread: [http://ubuntuforums.org/showthread.php?t=658970&page=4](http://ubuntuforums.org/showthread.php?t=658970&page=4))

---

### Post by ubuntu-freak on 2008-01-14
Have a look at my post below the how-to. It should fix your problem with FF.
 
Nathan

---

### Post by ubuntu-freak on 2008-01-14
> **ugm6hr said:**
> I have just been reading this: [http://ubuntuforums.org/showpost.php?p=4130151&postcount=12](http://ubuntuforums.org/showpost.php?p=4130151&postcount=12)

I followed this how-to, and Quicktime stuff works flawlessly.

But Realmedia on BBC / wmv doesn't allow seeking - which I think is OK for me.

But that post states that Helix has superceded Realplayer (I realise that Realplayer is based on Helix), but I though Helix did not have codecs to play realmedia (and hence the difference).

In any case, Firefox plays **all** BBC streams (wmv / rm) via mplayer now.

**Should it be using Helix?  If so, what have I done wrong?**

PS: Your how-to should also instruct you to remove xine mozilla plugin too, and even kaffeine plugin (since I had installed every media player to get this working!)

It is using the Helix plugin for audio, which in turn uses the win32 codecs. I watched rm video before Helix was installed interestingly though.

Nathan

---

### Post by ubuntu-freak on 2008-01-14
> **TWO said:**
> (This is the answer to your question in the thread: [http://ubuntuforums.org/showthread.php?t=658970&page=4](http://ubuntuforums.org/showthread.php?t=658970&page=4))

I have completely reviewed and tidied up my how-to today. It includes every single detail to get streaming working properly. Works for me and others. Just scroll down to the --IMPORTANT-- section and try the Firefox solution. It does work.

Hope that helps,

Nathan

---

### Post by ubuntu-freak on 2008-01-15
I've added a DVD playback solution to my second post (newer encrypted DVD's).

Enjoy!

Nathan

---

### Post by bw44 on 2008-01-15
> **reassuringlyoffensive said:**
> **--UPDATED--**

The flash plugin (for YouTube) in the repo is currently broken. **If you are fairly new to Ubuntu and your flash plugin doesn't seem to work**, Do the following

Download it here [http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466")

Save it to your home folder, then open the terminal and paste this 

**sudo dpkg -i flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb**

I still see a lot of people struggling and getting frustrated over this task so I thought I'd post my own howto on the subject.

If you haven't already, you need to enable the medibuntu repo. Go to the link below and follow the instructions for you particular Ubuntu version (Remember to add the GPG key also). Use the Terminal (Applications>Accessories>Terminal) and paste the commands into it.

[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

<snip>

Thanks for your posts -- they've really been a great help.  

The one problem I'm having is with the flashplayer plugin.  I think I originally installed it using some other method (sorry, it was a long time ago).  The version I had was libflashplayer.so Shockwave Flash 9.0 r48.  I followed all your instructions above and also the ones about how to get Firefox to accept the new plugin: > If Firefox doesn't recognize that you have changed your plugins (pops up with "Plugin Required" or something like that) then you need to go to your home folder, click the "View" tab in your file manager, move your cursor down and click on "Show Hidden Files". Then scroll down to your .mozilla folder, open it and then open your firefox folder and delete the file named pluginreg.dat (it will recreate itself). Then reinstall the plugins. Open Firefox and type "about : plugins" (no spaces) in the address bar and press enter. Should show you a very long list of plugins now (Java, Flash, Real Player, Windows Media etc).

But every time I delete the  pluginreg.dat file and restart Firefox I seem to have both the old plugin and the new one, libflashplayer.so  Shockwave Flash 9.0 r115 (which I assume is the one I want.)

Any thoughts on how to get rid of the old version of the plugin?  I'm also puzzled by the fact that the Synaptic Package Manager cannot see either version of the plugin.  Is this normal?

Thanks for any suggestions!

PS I should add that I'm not able to open the YouTube site, much less view videos.

---

### Post by bw44 on 2008-01-15
> **bw44 said:**
> Thanks for your posts -- they've really been a great help.  

The one problem I'm having is with the flashplayer plugin.  I think I originally installed it using some other method (sorry, it was a long time ago).  The version I had was libflashplayer.so Shockwave Flash 9.0 r48.  I followed all your instructions above and also the ones about how to get Firefox to accept the new plugin: 

But every time I delete the  pluginreg.dat file and restart Firefox I seem to have both the old plugin and the new one, libflashplayer.so  Shockwave Flash 9.0 r115 (which I assume is the one I want.)

Any thoughts on how to get rid of the old version of the plugin?  I'm also puzzled by the fact that the Synaptic Package Manager cannot see either version of the plugin.  Is this normal?

Thanks for any suggestions!

PS I should add that I'm not able to open the YouTube site, much less view videos.

Stop the press! I just retried deleting pluginreg.dat and this time the old plugin disappeared and the new one took hold.  I really don't know what I did differently this time.  But YouTube is coming in loud and clear.  Thanks so much!

I also note that the new plugin is now visible with Synaptic Package Manger, although it's listed in the status "Installed -- Local or Obsolete".

Sorry for the false post!

---

### Post by timzak on 2008-01-15
Great howto.  I plan on trying it out next chance I get.  Do any of your instructions need tweaking on 64bit FF?  I currently am running 64bit FF with 32 bit Java.  Flash works and most streaming seems to work okay except the other night I noticed I couldn't stream a Real video.  I'd just like to get this real video stream working but before I try, I thought I'd ask you the 64bit question.

Here is a link to the video stream in question:
[http://media.pbs.org/ramgen/mr_rogers/Picture_Picture/sneaker.rm](http://media.pbs.org/ramgen/mr_rogers/Picture_Picture/sneaker.rm)

(It's clean...Mr. Roger's Neighborhood video from PBS website).

Thanks.

---

### Post by ubuntu-freak on 2008-01-15
> **timzak said:**
> Great howto.  I plan on trying it out next chance I get.  Do any of your instructions need tweaking on 64bit FF?  I currently am running 64bit FF with 32 bit Java.  Flash works and most streaming seems to work okay except the other night I noticed I couldn't stream a Real video.  I'd just like to get this real video stream working but before I try, I thought I'd ask you the 64bit question.

Here is a link to the video stream in question:
[http://media.pbs.org/ramgen/mr_rogers/Picture_Picture/sneaker.rm](http://media.pbs.org/ramgen/mr_rogers/Picture_Picture/sneaker.rm)

(It's clean...Mr. Roger's Neighborhood video from PBS website).

Thanks.

 
Hopefully you will be okay. Obviously you need the w64codecs but settings stay the same.
 
I can't check the stream right now, but rm video streams should work without real or helix. MPlayer handles them with w32 or w64 codecs. It needs helix for ram radio.

Nathan

---

### Post by ubuntu-freak on 2008-01-15
> **bw44 said:**
> Stop the press! I just retried deleting pluginreg.dat and this time the old plugin disappeared and the new one took hold.  I really don't know what I did differently this time.  But YouTube is coming in loud and clear.  Thanks so much!

I also note that the new plugin is now visible with Synaptic Package Manger, although it's listed in the status "Installed -- Local or Obsolete".

Sorry for the false post!

 
Sounds like Firefox is trying to poo poo my how-to.
 
It's a bug. Has to be. You shouldn't even have to delete that dat file, let alone a dozen times.
 
**Please don't give up people. Firefox will pick up your new setup eventually and you will struggle to find streams that don't work.**
 
That's why I'm all over the forums lately giving this how-to link to anyone who even remotely mentions media troubles. :)
 
Nathan

---

### Post by ubuntu-freak on 2008-01-15
If you can't uninstall a plugin for whatever reason
 
**sudo rm /usr/lib/firefox/plugins/pluginname.extension**
 
Or the GUI way
 
**alt+f2** and type **gksu nautilus** and then go find it and delete it.  

Make sure synaptic at least 'thinks' it was uninstalled already.
 
Nathan

---

### Post by K.Mandla on 2008-01-15
Thread renamed at OPer's request.

---

### Post by mount_evans on 2008-01-15
> **reassuringlyoffensive said:**
> I have completely reviewed and tidied up my how-to today. It includes every single detail to get streaming working properly. Works for me and others. Just scroll down to the --IMPORTANT-- section and try the Firefox solution. It does work.

Hope that helps,

Nathan

I followed your instructions earlier; should I go back and do it over with the new version?  Is there anything I need to uninstall before doing it over?

---

### Post by ubuntu-freak on 2008-01-15
> **mount_evans said:**
> I followed your instructions earlier; should I go back and do it over with the new version?  Is there anything I need to uninstall before doing it over?

 
Well I added the xine plugin to the remove command and kaffeine too (just incase).
 
Have you tested other sites? Search 'RealPlayer test' in google.
 
Nathan

---

### Post by timzak on 2008-01-15
```
sudo apt-get install mplayer mozilla-mplayer helix-player mozilla-helix-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mplayer is already the newest version.
mozilla-mplayer is already the newest version.
E: Couldn't find package helix-player
```

Any idea why it can't find helix-player?  Is there no 64 bit version of it?

---

### Post by mount_evans on 2008-01-16
> **reassuringlyoffensive said:**
> Well I added the xine plugin to the remove command and kaffeine too (just incase).
 
Have you tested other sites? Search 'RealPlayer test' in google.
 
Nathan

Actually, youtube videos stutter.

---

### Post by ubuntu-freak on 2008-01-16
> **mount_evans said:**
> Actually, youtube videos stutter.

YouTube is flash not rm. They stutter? Hmm. All the time? Not sure what that is about. You should test some rm streams.

Nathan

---

### Post by ubuntu-freak on 2008-01-16
> **timzak said:**
> ```
sudo apt-get install mplayer mozilla-mplayer helix-player mozilla-helix-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mplayer is already the newest version.
mozilla-mplayer is already the newest version.
E: Couldn't find package helix-player
```

Any idea why it can't find helix-player?  Is there no 64 bit version of it?

Yes there should be one for you. Did it find the helix mozilla plugin? That's the most important thing. MPlayer will use that plugin, you won't see Helix in your browser, just MPlayer.

Nathan

---

### Post by bw44 on 2008-01-16
> **reassuringlyoffensive said:**
> Well I added the xine plugin to the remove command and kaffeine too (just incase).
 
Have you tested other sites? Search 'RealPlayer test' in google.
 
Nathan

Yikes!  I just did as you suggested and visited several RealPlayer test sites.  Results are very mixed.

None of the tests at the Real site [http://service.real.com/test/](http://service.real.com/test/) work on either my desktop or laptop.  The two systems are at the same software level and the only reason I mention them is that on the desktop I can't seem to use vo=xv, but have to use vo=x11 to access BBC and other sites.

In each case there is a brief sequence of messages, starting with "Download complete" then a 'connecting to" the site and then a "Stopped".  It's as if the site is detecting something at my end and quitting.  This is also what happens when I visit the BBC site and try to access their videos.

However, the test at University of Delaware [http://www.udel.edu/UMS/itv/realplayer/test.html](http://www.udel.edu/UMS/itv/realplayer/test.html) works on both systems without any problems.

On the other hand, the test at [http://www.itma.vt.edu/tech/real.ram](http://www.itma.vt.edu/tech/real.ram) gives the same result as the Real site: nada.

The symptoms suggest to me that there is some problem with redirection:  you access one URL, the server redirects you and then mplayer (Firefox? something at the client end) can't follow the redirection.   Just a guess.

Any thoughts?

---

### Post by ubuntu-freak on 2008-01-16
> **bw44 said:**
> Yikes!  I just did as you suggested and visited several RealPlayer test sites.  Results are very mixed.

None of the tests at the Real site [http://service.real.com/test/](http://service.real.com/test/) work on either my desktop or laptop.  The two systems are at the same software level and the only reason I mention them is that on the desktop I can't seem to use vo=xv, but have to use vo=x11 to access BBC and other sites.

In each case there is a brief sequence of messages, starting with "Download complete" then a 'connecting to" the site and then a "Stopped".  It's as if the site is detecting something at my end and quitting.  This is also what happens when I visit the BBC site and try to access their videos.

However, the test at University of Delaware [http://www.udel.edu/UMS/itv/realplayer/test.html](http://www.udel.edu/UMS/itv/realplayer/test.html) works on both systems without any problems.

On the other hand, the test at [http://www.itma.vt.edu/tech/real.ram](http://www.itma.vt.edu/tech/real.ram) gives the same result as the Real site: nada.

The symptoms suggest to me that there is some problem with redirection:  you access one URL, the server redirects you and then mplayer (Firefox? something at the client end) can't follow the redirection.   Just a guess.

Any thoughts?


**I've got it!!!!!!!!!!!!!!!!!!!!!!!!!!**

The frickin Helix plugin isn't being installed properly by Ubuntu!! The fix is stupidly easy

**sudo ln -s /usr/lib/helix/player/mozilla/nphelix.so /usr/lib/firefox/plugins**

[B]sudo ln -s /usr/lib/helix/player/mozilla/nphelix.xpt /usr/lib/firefox/plugins
[/B]

ALL those tests work for me now, and they will for you too.

Enjoy!

Nathan

---

### Post by bw44 on 2008-01-16
> **reassuringlyoffensive said:**
> **I've got it!!!!!!!!!!!!!!!!!!!!!!!!!!**

The frickin Helix plugin isn't being installed properly by Ubuntu!! The fix is stupidly easy

**sudo ln -s /usr/lib/helix/player/mozilla/nphelix.so /usr/lib/firefox/plugins**

[B]sudo ln -s /usr/lib/helix/player/mozilla/nphelix.xpt /usr/lib/firefox/plugins
[/B]

ALL those tests work for me now, and they will for you too.

Enjoy!

Nathan

Thanks, BUT . . . 

I created the symbolic links as you suggested on my desktop system; closed Firefox and re-booted, just to be sure!  After that, everything at the REAL test site played fine -- great!

Now the confusing bit:  I did not create the symbolic links on my laptop, but it started working too!  In fact, I noticed this before I read your post and was trying to think of an excuse why I had posted about the Real test page not working at all.  I just checked and the symbolic links are not present on this system.

And now, with the symbolic links still in place on the desktop system, none of the Real test links are working.](*,)   Same symptoms as described before.

Just tested again and it's working once more!

Is it possible that this is related to my extremely bad ISP performance? The actual bandwidth they deliver is notoriously inconsistent, so much so that a recent investigative news report suggested that you shouldn't bother paying for their "up to 7 Mb" service because it would rarely be delivered.

Anyway, thanks for all your efforts -- I've learned a lot!  As for my problem, I think it's related to my local access, not to do with any of your advice.

Cheers.

---

### Post by timzak on 2008-01-16
> **reassuringlyoffensive said:**
> Yes there should be one for you. Did it find the helix mozilla plugin? That's the most important thing. MPlayer will use that plugin, you won't see Helix in your browser, just MPlayer.

Nathan

No, it can't find the helix mozilla plugin either.  I tried each individually and it says for both that it can't find it.  Is helix in medibuntu?  I did go through the steps to enable the medibuntu repos.

On another topic, I notice when I click on some real videos, it asks me if I want to open it or download it, while on others it automatically tries to play with Mplayer.  However, when I get the choice to open (play) or download to computer, it does not list Mplayer (or any other player) as an option for opening with.  It simply has a "Browse for player" query and I have no idea how to direct it to use Mplayer.

---

### Post by ubuntu-freak on 2008-01-16
> **timzak said:**
> No, it can't find the helix mozilla plugin either.  I tried each individually and it says for both that it can't find it.  Is helix in medibuntu?  I did go through the steps to enable the medibuntu repos.

On another topic, I notice when I click on some real videos, it asks me if I want to open it or download it, while on others it automatically tries to play with Mplayer.  However, when I get the choice to open (play) or download to computer, it does not list Mplayer (or any other player) as an option for opening with.  It simply has a "Browse for player" query and I have no idea how to direct it to use Mplayer.

It should be in the normal repo. I don't know how to help you with that. That's why I'd never install 64bit Ubuntu.

Never come accross that before with rm videos. MPlayer should just kick in on it's own.

Do **gksudo gedit /etc/mplayerplug-in.conf** and change "download=1" to "download=0"

Nathan

---

### Post by ubuntu-freak on 2008-01-16
> **bw44 said:**
> Thanks, BUT . . . 

I created the symbolic links as you suggested on my desktop system; closed Firefox and re-booted, just to be sure!  After that, everything at the REAL test site played fine -- great!

Now the confusing bit:  I did not create the symbolic links on my laptop, but it started working too!  In fact, I noticed this before I read your post and was trying to think of an excuse why I had posted about the Real test page not working at all.  I just checked and the symbolic links are not present on this system.

And now, with the symbolic links still in place on the desktop system, none of the Real test links are working.](*,)   Same symptoms as described before.

Just tested again and it's working once more!

Is it possible that this is related to my extremely bad ISP performance? The actual bandwidth they deliver is notoriously inconsistent, so much so that a recent investigative news report suggested that you shouldn't bother paying for their "up to 7 Mb" service because it would rarely be delivered.

Anyway, thanks for all your efforts -- I've learned a lot!  As for my problem, I think it's related to my local access, not to do with any of your advice.

Cheers.

There is something else important to change.

**gksudo gedit /etc/mplayerplug-in.conf**

Change "download=1" to "**download=0**"

It seems to interfere with rm streaming big time. If you want to download videos to your home folder then change both "download" and "keep-download" to =1.

Nathan

Edit: Actually you can just delete it, keep-download works without it.

---

### Post by ubuntu-freak on 2008-01-16
Added some great advice for getting DVD's to play perfectly in Ubuntu with VLC. It's in my second post on page 1 of this thread.

Apologies for telling you to apt-get install gnome-vlc when it's just plain vlc. I guess you can tell I haven't used it much. (Tis great for DVD playback though)

Nathan

---

### Post by mount_evans on 2008-01-16
A few nitpicks for the sake of ***utter*** noobies like myself:

> **reassuringlyoffensive said:**
> 
To set VLC your default DVD player (**I strongly advise you do**) open the terminal and type

**gksudo gconf-editor**

Now expand **"desktop"** and then** "gnome"**, scroll down to **"volume manager"** but don't expand it, just click on it and look over at the right pane. Scroll down and look for **"autoplay dvd"** and change the dvd command to **/usr/bin/vlc dvd://** by right clicking on it and selecting **"Edit"**, then click on **"Set as Default"**. Do the same for VCD too.

I assume you meant **"autoplay_dvd_command"** and **"autoplay_vcd_command"**, selecting **"Edit Key"**, and entering "/usr/bin/vlc dvd://" as the **"Value"**?  Because I wasn't able to edit much in **"autoplay dvd"**.

> For video converting try Winff (make sure you have ffmpeg from medibuntu). 

[http://biggmatt.com/winff/](http://biggmatt.com/winff/)

I believe you intended for us to look for and download the Debian distro?  (Hey, some of us don't know anything about the fairies that live in the magic box on our desk.)
 
> Save to home folder then do

**sudo dpkg -i filename.deb**  

At the risk of stating the totally obvious, "filename.deb" should be replaced with something like  "winff-0.33-i386.deb".

I am for all practical purposes still a windows user; we need everything explained keystroke-by-keystroke.

---

### Post by bw44 on 2008-01-16
> **reassuringlyoffensive said:**
> There is something else important to change.

**gksudo gedit /etc/mplayerplug-in.conf**

Change "download=1" to "**download=0**"

It seems to interfere with rm streaming big time. If you want to download videos to your home folder then change both "download" and "keep-download" to =1.

Nathan

Edit: Actually you can just delete it, keep-download works without it.

I've always run with download=0 and I believe "keep-download" defaults to 0.  

I've done some more testing now with different rm sites and  am pretty sure that two things affect the chances of successfully viewing them: broken links and network delays.  I don't know what the equivalent of a 404 is when mplayer goes to a broken link, but I don't think you get any message telling you the link is no good; it just stops.  (If anyone knowns different, please post!)

The second problem, network delays, would account for a lot of the intermittent problems I've experienced.  On the RealPlayer test site [http://service.real.com/test/](http://service.real.com/test/)  I can sometimes get anything on the page to play.  At other times, nothing.

If anyone can shed any more light on these intermittent results, I hope they'll post something.

Thanks.

---

### Post by mount_evans on 2008-01-16
OK, I went back and followed all of the instructions from the beginning.  Here is a list of  what I can and cannot play:

Youtube-- isn't stuttering at the moment.  Yay.
BBC video-- plays.
BBC radio-- plays, but there is a black rectangle with the words "(No video)" where the controls should be.
Other radio-- the same as BBC
Apple.com trailers-- black rectangle with "(No video)"
Real media test sites like [http://real.unl.edu/lpe/rm-demo.html](http://real.unl.edu/lpe/rm-demo.html) say "Stopped".

Here is the one I would really like to be able to listen to, though:
[http://www.live365.com/stations/filk_com](http://www.live365.com/stations/filk_com)

This is a non-standard web radio page.  When you click on the "Play" icon, it tries to open a playlist in Rythmbox.  I have no idea why, but that's what it does.  

Other sites use MP3's for streaming content--is there anything that can play those?

---

### Post by mount_evans on 2008-01-16
> **mount_evans said:**
> 
Here is the one I would really like to be able to listen to, though:
[http://www.live365.com/stations/filk_com](http://www.live365.com/stations/filk_com)

This is a non-standard web radio page.  When you click on the "Play" icon, it tries to open a playlist in Rythmbox.  I have no idea why, but that's what it does.  

Other sites use MP3's for streaming content--is there anything that can play those?

Actually, I think if I could make Audacious my default player for .pls or .mp3, that might do it.  How do I change the default player in Ubuntu?

---

### Post by ubuntu-freak on 2008-01-16
> **mount_evans said:**
> A few nitpicks for the sake of ***utter*** noobies like myself:



I assume you meant **"autoplay_dvd_command"** and **"autoplay_vcd_command"**, selecting **"Edit Key"**, and entering "/usr/bin/vlc dvd://" as the **"Value"**?  Because I wasn't able to edit much in **"autoplay dvd"**.



I believe you intended for us to look for and download the Debian distro?  (Hey, some of us don't know anything about the fairies that live in the magic box on our desk.)
 


At the risk of stating the totally obvious, "filename.deb" should be replaced with something like  "winff-0.33-i386.deb".

I am for all practical purposes still a windows user; we need everything explained keystroke-by-keystroke.


Lol yes replace filename.deb with the actual filename. It will change often so no point me giving the current filename.

Gnome is GTK. There is a GTK version of Winff for Debian/Ubuntu.

I thought I was clear about changing your default DVD player. You got it all correct anyway. I will go make it clearer though.


Nathan

---

### Post by ubuntu-freak on 2008-01-16
> **mount_evans said:**
> OK, I went back and followed all of the instructions from the beginning.  Here is a list of  what I can and cannot play:

Youtube-- isn't stuttering at the moment.  Yay.
BBC video-- plays.
BBC radio-- plays, but there is a black rectangle with the words "(No video)" where the controls should be.
Other radio-- the same as BBC
Apple.com trailers-- black rectangle with "(No video)"
Real media test sites like [http://real.unl.edu/lpe/rm-demo.html](http://real.unl.edu/lpe/rm-demo.html) say "Stopped".

Here is the one I would really like to be able to listen to, though:
[http://www.live365.com/stations/filk_com](http://www.live365.com/stations/filk_com)

This is a non-standard web radio page.  When you click on the "Play" icon, it tries to open a playlist in Rythmbox.  I have no idea why, but that's what it does.  

Other sites use MP3's for streaming content--is there anything that can play those?

You have issues with apple.com? I never ever do. That's just weird. Do you hear sound? If you hear sound just change your video driver in MPlayer's preferences.

BBC tells you there is "No Video" for radio?? Errr....okay. How did you do that? The controls only disappeared for me when I used wmv radio (then appeared). Make sure you click on ram. I have that nice new black iPlayer control thing when I choose ram. 

Rm and ram is a bit random sometimes but your apple.com problem should not exist. Not with my settings + w32codecs. Strange.

Nathan

---

### Post by ugm6hr on 2008-01-16
> **mount_evans said:**
> Here is the one I would really like to be able to listen to, though:
[http://www.live365.com/stations/filk_com](http://www.live365.com/stations/filk_com)

This is a non-standard web radio page.  When you click on the "Play" icon, it tries to open a playlist in Rythmbox.  I have no idea why, but that's what it does.  

Other sites use MP3's for streaming content--is there anything that can play those?

Seems like XMMS is recommended: [http://wiki.live365.com/pmwiki.php?n=Listening.Linux](http://wiki.live365.com/pmwiki.php?n=Listening.Linux)

---

### Post by ubuntu-freak on 2008-01-16
Just added faac and faad to the list of important packages in the first post. Once you install ffmeg and Winff you can convert videos for your phone. Choose 3g2 in Winff and it will automatically create a video suitable for most phones.

Nathan

---

### Post by ubuntu-freak on 2008-01-16
> **ugm6hr said:**
> Seems like XMMS is recommended: [http://wiki.live365.com/pmwiki.php?n=Listening.Linux](http://wiki.live365.com/pmwiki.php?n=Listening.Linux)

MPlayer can handle m3u streams cos I listen to bassdrive.com. It claims to support mp3 streams but I dunno. Try Audacious. It's like XMMS except that it's not dead.

Nathan

Edit: I just listened to an mp3 station at shoutcast. You have my settings yeah? It worked right away for me.

---

### Post by timzak on 2008-01-16
> **reassuringlyoffensive said:**
> It should be in the normal repo. I don't know how to help you with that. That's why I'd never install 64bit Ubuntu.

Never come accross that before with rm videos. MPlayer should just kick in on it's own.

Do **gksudo gedit /etc/mplayerplug-in.conf** and change "download=1" to "download=0"

Nathan

I just checked Ubuntu packages and confirmed that neither Helix nor its Mozilla plugin come in a 64bit variety.  But I think there is a way to install 32bit apps in 64bit (Kilz has a howto somewhere), so I will try that.  Honestly, this is the first time since installing Gutsy64 that I've come across an app that is not available in 64bits (besides java).  I've had a great experience and I'm a relative newb.  I use 64bit Firefox and flash and java are fully functional (albeit they are 32bit versions running in 64bit FF).

Thanks for the tip on the download= variable.  I'll try it out tonight.

---

### Post by mount_evans on 2008-01-16
> **ugm6hr said:**
> Seems like XMMS is recommended: [http://wiki.live365.com/pmwiki.php?n=Listening.Linux](http://wiki.live365.com/pmwiki.php?n=Listening.Linux)

Well, whatever players I have installed, I have to somehow convince Firefox to let me open the .pls file in something other than Rythmbox.  I have the choice of Rythmbox or Other.  Other leads to a file browser--not an application browser--so I have to know where the executable for the other player is.  Is there a way to make something else the default player?

Audacity will quite wilingly play a URL, and that works for some Webradio, but this stupid live365 does everything inside of Javascript so I don't have access to a URL.

---

### Post by mount_evans on 2008-01-16
> **reassuringlyoffensive said:**
> You have issues with apple.com? I never ever do. That's just weird. Do you hear sound? If you hear sound just change your video driver in MPlayer's preferences. 

Cranked up the volume and waited a very long time; no sound.

> BBC tells you there is "No Video" for radio?? Errr....okay. How did you do that? The controls only disappeared for me when I used wmv radio (then appeared). Make sure you click on ram. I have that nice new black iPlayer control thing when I choose ram. 

Chose Real Media, got controls.  Thanks.

---

### Post by mount_evans on 2008-01-16
> **reassuringlyoffensive said:**
> MPlayer can handle m3u streams cos I listen to bassdrive.com. It claims to support mp3 streams but I dunno. Try Audacious. It's like XMMS except that it's not dead.

Nathan

Edit: I just listened to an mp3 station at shoutcast. You have my settings yeah? It worked right away for me.

Audacious will play a URL; the catch is that it is not the default player.  If the URL is made available, such as:
[http://www.cpr.org/listen/live_classical_mp3.pls](http://www.cpr.org/listen/live_classical_mp3.pls)
...then I just copy it, open Audacious, select Play from Location, and paste the URL.  But 365live hides this stuff inside of javacript.  You click on the "play" link, and Firefox is trying to open the pls files in Rythmbox.  I need to make something besides Rythmbox the default player.  I can choose "Other" but since I have no idea where the executables for the other players are located or what they are called, that does no good.

---

### Post by ubuntu-freak on 2008-01-16
> **timzak said:**
> I just checked Ubuntu packages and confirmed that neither Helix nor its Mozilla plugin come in a 64bit variety.  But I think there is a way to install 32bit apps in 64bit (Kilz has a howto somewhere), so I will try that.  Honestly, this is the first time since installing Gutsy64 that I've come across an app that is not available in 64bits (besides java).  I've had a great experience and I'm a relative newb.  I use 64bit Firefox and flash and java are fully functional (albeit they are 32bit versions running in 64bit FF).

Thanks for the tip on the download= variable.  I'll try it out tonight.

 
Have considered installing the 32bit Ubuntu? I would.
 
Nathan

---

### Post by ugm6hr on 2008-01-16
> **mount_evans said:**
> Audacious will play a URL; the catch is that it is not the default player.  If the URL is made available, such as:
[http://www.cpr.org/listen/live_classical_mp3.pls](http://www.cpr.org/listen/live_classical_mp3.pls)
...then I just copy it, open Audacious, select Play from Location, and paste the URL.  But 365live hides this stuff inside of javacript.  You click on the "play" link, and Firefox is trying to open the pls files in Rythmbox.  I need to make something besides Rythmbox the default player.  I can choose "Other" but since I have no idea where the executables for the other players are located or what they are called, that does no good.

From "Other" - go to *usr/bin/audacious*

It works.  I just checked.

The benefit of this is that if you *don't* select the "Always do this" option, you can actually close the browser pop-up and continue to listen (as long as you cancel the request to open the silent file).

---

### Post by ubuntu-freak on 2008-01-16
> **mount_evans said:**
> Audacious will play a URL; the catch is that it is not the default player.  If the URL is made available, such as:
[http://www.cpr.org/listen/live_classical_mp3.pls](http://www.cpr.org/listen/live_classical_mp3.pls)
...then I just copy it, open Audacious, select Play from Location, and paste the URL.  But 365live hides this stuff inside of javacript.  You click on the "play" link, and Firefox is trying to open the pls files in Rythmbox.  I need to make something besides Rythmbox the default player.  I can choose "Other" but since I have no idea where the executables for the other players are located or what they are called, that does no good.

 
Firefox opens a tab for me and MPlayer starts streaming the mp3. Am I the chosen one or something? lol.
 
Try Firefox preferences maybe. M3U/mp3 open in browser.
 
Nathan

---

### Post by ugm6hr on 2008-01-16
> **reassuringlyoffensive said:**
> Firefox opens a tab for me and MPlayer starts streaming the mp3. Am I the chosen one or something? lol.
 
Try Firefox preferences maybe. M3U/mp3 open in browser.
 
Nathan

No such option. My preference does say Use this plugin - mplayer.  But live365 doesn't work.  As mount_evans - Rhythmbox is offered as the default app.

---

### Post by ubuntu-freak on 2008-01-16
> **mount_evans said:**
> Cranked up the volume and waited a very long time; no sound.



Chose Real Media, got controls.  Thanks.

 
You must be missing something if apple wont play. 
 
W32codecs let you play apple streams I think. 
 
Make sure everything is installed. Search synaptic.
 
Nathan

---

### Post by ubuntu-freak on 2008-01-16
> **ugm6hr said:**
> No such option. My preference does say Use this plugin - mplayer.  But live365 doesn't work.  As mount_evans - Rhythmbox is offered as the default app.

 
Try [www.shoutcast.com](www.shoutcast.com)
 
Not every site is friendly with non IE and MS users

---

### Post by ubuntu-freak on 2008-01-16
Also, install audacious and then type 
 
locate audacious
 
Then you can set it as your default instead of rhythmbox in FF.
 
Nathan

---

### Post by mount_evans on 2008-01-16
> **ugm6hr said:**
> From "Other" - go to *usr/bin/audacious*

It works.  I just checked.

The benefit of this is that if you *don't* select the "Always do this" option, you can actually close the browser pop-up and continue to listen (as long as you cancel the request to open the silent file).

Thank you!

---

### Post by mount_evans on 2008-01-16
> **reassuringlyoffensive said:**
> Firefox opens a tab for me and MPlayer starts streaming the mp3. Am I the chosen one or something? lol.
 
Try Firefox preferences maybe. M3U/mp3 open in browser.
 
Nathan

M3U's are already opened with mplayer, according to Firefox.  The file in question is a PLS, though.  How do I create a new file association in Firefox?  It looks like I can only edit the ones that already exist, and PLS isn't one of them.

---

### Post by ubuntu-freak on 2008-01-16
I'm on my phone now people so have to help from memory.
 
Remember that 'locate' command though. Comes in handy.
 
Did anyone try my DVD how-to and converter? Menus work nice in VLC and it starts as default DVD player. Virtually ALL DVD's should work too. Plus I made a nice 3g2 vid for my phone in Winff. Sweet!
 
Make sure you install faac and faad. Added them to list in first post.


Nathan

---

### Post by mount_evans on 2008-01-16
> **reassuringlyoffensive said:**
> Also, install audacious and then type 
 
locate audacious
 
Then you can set it as your default instead of rhythmbox in FF.
 
Nathan

How?  The list of "Download Actions" has a button for "change action" and "remove action" but no "create new action for new extension", which I would need to do for the PLS extension.

---

### Post by ubuntu-freak on 2008-01-16
> **mount_evans said:**
> M3U's are already opened with mplayer, according to Firefox.  The file in question is a PLS, though.  How do I create a new file association in Firefox?  It looks like I can only edit the ones that already exist, and PLS isn't one of them.

 
Weird. Pls is in the MPlayer conf settings. It should load. Did you try shoutcast and bassdrive.com?
 
Nathan

---

### Post by mount_evans on 2008-01-16
> **reassuringlyoffensive said:**
> Weird. Pls is in the MPlayer conf settings. It should load. Did you try shoutcast and bassdrive.com?
 
Nathan

Bassdrive played in mplayer, shoutcast crashed Firefox the first time I tried it, played OK in Audacious the second time.  

There is a little applet in the "Other" Applications menu that is supposed to configure file associations, but nothing happens when I click on it.

---

### Post by ubuntu-freak on 2008-01-16
> **mount_evans said:**
> Bassdrive played in mplayer, shoutcast crashed Firefox the first time I tried it, played OK in Audacious the second time.  

There is a little applet in the "Other" Applications menu that is supposed to configure file associations, but nothing happens when I click on it.

 
Shoutcast made FF crash? Geez. Worked fine for me.
 
Did you try the DVD how-to? Tried converting anything with Winff? Make sure you have faac and faad.
 
Nathan

---

### Post by mount_evans on 2008-01-16
> **reassuringlyoffensive said:**
> Shoutcast made FF crash? Geez. Worked fine for me.
 
Did you try the DVD how-to? Tried converting anything with Winff? Make sure you have faac and faad.
 
Nathan

Yes, the DVD autoplay works.  At least on Porn DVDs.  I suppose I should test it on some "legit" DVDs that would have region encoding and stuff.

---

### Post by ubuntu-freak on 2008-01-16
The menu support is awesome. Totem just plays it but VLC lets it bring up the menu for chapters and such.
 
Nathan

---

### Post by timzak on 2008-01-17
One more question:  (I'm the guy w/64bit who can't use helix).  By simply making your configuration changes in Mplayer, I am now able to play that Mr. Rogers Realvideo link I posted (and I don't have realplay installed).  The only problem is that when I link directly to the video (as opposed to navigating to the page it's on and clicking the link there), Totem pops open to try and play it.  I can close Totem and see that it's still loading up in the Mplayer Mozilla plugin.  However, if I navigate to the movie normally through the PBS Kids website, Totem doesn't open and try to play the file.  Any ideas why and how I can keep Totem from popping up at these times?

Thanks.

---

### Post by ubuntu-freak on 2008-01-17
> **timzak said:**
> One more question:  (I'm the guy w/64bit who can't use helix).  By simply making your configuration changes in Mplayer, I am now able to play that Mr. Rogers Realvideo link I posted (and I don't have realplay installed).  The only problem is that when I link directly to the video (as opposed to navigating to the page it's on and clicking the link there), Totem pops open to try and play it.  I can close Totem and see that it's still loading up in the Mplayer Mozilla plugin.  However, if I navigate to the movie normally through the PBS Kids website, Totem doesn't open and try to play the file.  Any ideas why and how I can keep Totem from popping up at these times?

Thanks.

 
MPlayer only needs Helix for ram audio.
 
I think in Firefox preferences you can stop Totem. I will check soon when I get on the laptop.
 
 Nathan

---

### Post by ubuntu-freak on 2008-01-17
Made some serious changes to my how-to. I'm sick of Helix, it doesn't actually do ANYTHING. MPlayer can't handle rm and ram very well. It's very very random. Completely random infact. 

The solution is as follows (if you are new to this how-to, go to the first page please)

**sudo apt-get remove totem-mozilla  mozilla-plugin-vlc xine-plugin kaffeine-mozilla helix-player mozilla-helix-player**

**sudo apt-get install mplayer mozilla-mplayer**

If you followed my how-to before and installed Helix, you need to remove those symlinks I told you to do

**sudo rm /usr/lib/firefox/plugins/nphelix.so**

**sudo rm /usr/lib/firefox/plugins/nphelix.xpt**

Now you need to download the proper RealPlayer. It will also install nphelix plugins, but they will not be restricted like the Helix ones. Real Media playback has been so random that I decided RealPlayer was the best way to go. Download this deb (It works fine in Gutsy and can be removed with apt-get remove)

[http://archive.canonical.com/ubuntu/pool/partner/r/realplay/realplay_10.0.9-0feisty1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/r/realplay/realplay_10.0.9-0feisty1_i386.deb)

Save or move it to your home folder and do

**sudo dpkg -i realplay_10.0.9-0feisty1_i386.deb**

Now make sure that "**enable-rm**" in mplayer's conf file is changed from "**1**" to "**0**". (This is for people who have already followed my how-to previously).

That's it!!


**--STREAMING HOW-TO--**

You don't have to put up with sub-par streaming and use that mediaconnectivity Firefox add-on. This is how I got streaming working great at divx.com, yahoo movies and even on the BBC website, including rm video and ram radio.
 
I posted this in the Debian forums originally.

**gksudo gedit /etc/mplayerplug-in.conf **and delete everything listed (back it up if you're worried) and then cut and paste these settings. They improve streaming a great deal with certain sites which have caused problems.

keep-download=0
cachesize=1024
cache-percent=25
dload-dir=$HOME
noembed=0
autoplay=1
enable-wmp=1
enable-qt=1
**enable-rm=0**
enable-gmp=1
enable-dvx=1
enable-mpeg=1
enable-mp3=1
enable-midi=0
enable-pls=1
enable-ogg=1
**enable-smil=0**
**enable-helix=0**
nomediacache=0
nopauseonhide=1
rtsp-use-tcp=0
rtsp-use-http=0
 
**Please make sure you go to /home/.mozilla/firefox and delete the plugin dat file before starting FIrefox**. (You have to show the hidden folders in "View")

**Sometimes you will click on a video link and Firefox will ask if you want to download it or open it with Totem**. Many times though, Totem won't be able to play whatever it is you clicked on. Click to choose your own application and navigate to **/usr/bin** and you will find RealPlayer and other apps there.

---

### Post by bw44 on 2008-01-17
> **reassuringlyoffensive said:**
> <stufff deleted>

**--IMPORTANT--**

**Sometimes you will click on a video link and Firefox will ask if you want to download it or open it with Totem**. Many times though, Totem won't be able to play whatever it is you clicked on. Click to choose your own application and navigate to **/usr/bin** and you will find RealPlayer and other apps there.

**Use the "xv" video driver if you can**. Open MPlayer and right click on the video window, then click on "Preferences". Click on the "Video" tab and select "xv", or if you can't use that try "gl". As a last restort you should select "x11" (unaccelerated).

**Sometimes MPlayer looks like it is about to start playing a video**, but it does not. Try pressing play and don't just give up and navigate away. BBC wmv radio streams take a long time to start playing, the ram streams start quicker and sound better.

**If Firefox doesn't recognise that you have changed your plugins** (pops up with  "Plugin Required" or something like that) then you need to go to your home folder, click the "View" tab in your file manager, move your cursor down and click on "Show Hidden Files". Then scroll down to your **.mozilla folder**, open it and then open your **firefox folder** and delete the file named **pluginreg.dat** (it will recreate itself, (**you have to do this EVERYTIME you change your mplayerplug-in.conf file**). Then open Firefox and type "**about : plugins**" (no spaces) in the address bar and press enter. Should show you a very long list of plugins now (Java, Flash, Real Player, Windows Media etc). If it still doesn't then paste the following command

<Is there something missing here??>

**--MULTIMEDIA & VIDEO--**
 
To stop Ubuntu asking for the installation CD when you install packages, open the Terminal and do this

**gksudo gedit /etc/apt/sources.list**

<more stuff deleted>

Is there something (the command) missing in the above,  after "if it still doesn't then paste the following command"?

Thanks.

---

### Post by mount_evans on 2008-01-17
I can see the trailers in apple.com now.

I can see controls when I do streaming radio with the "Windows Media Player" option, and the play and pause controls work, but the volume control doesn't seem to do anything.  2 out of 3 aint bad.

Could you please, though, archive the last-but-one version of your HOW-TO?  I always detested "Real Player" when I had to use it in windows-- .rm was my least favorite format, since you never new if the .rm file you had would play on another computer--and it would be nice to keep the instructions for an alternative.

---

### Post by mount_evans on 2008-01-17
> **mount_evans said:**
> I can see the trailers in apple.com now.

I can see controls when I do streaming radio with the "Windows Media Player" option, and the play and pause controls work, but the volume control doesn't seem to do anything.  2 out of 3 aint bad.

I also can play that obscure format that I never knew what to do with--aacPlus--
in the VLC player.  So I can use any of the options that I usually see on an NPR web radio station--Cool!

---

### Post by ubuntu-freak on 2008-01-17
> **bw44 said:**
> Is there something (the command) missing in the above,  after "if it still doesn't then paste the following command"?

Thanks.


No don't worry about that. I've deleted that last sentance. That was cos of Helix being a bitch. RealPlayer is working fiiiiiine.

Nathan

---

### Post by ubuntu-freak on 2008-01-17
> **mount_evans said:**
> I can see the trailers in apple.com now.

I can see controls when I do streaming radio with the "Windows Media Player" option, and the play and pause controls work, but the volume control doesn't seem to do anything.  2 out of 3 aint bad.

Could you please, though, archive the last-but-one version of your HOW-TO?  I always detested "Real Player" when I had to use it in windows-- .rm was my least favorite format, since you never new if the .rm file you had would play on another computer--and it would be nice to keep the instructions for an alternative.

RealPlayer in Linux is totallly different cos they gave it to open source people to make. No nasty things in RealPlayer trust me. It's exactly the same as Helix except that it actually plays rm, ram, rv, ra etc etc.

Nathan

---

### Post by ubuntu-freak on 2008-01-17
It's all been updated and changed now. It's in a Part 1 to Part 5 format. Much better I think. 

Nathan

---

### Post by bw44 on 2008-01-17
> **reassuringlyoffensive said:**
> No don't worry about that. I've deleted that last sentance. That was cos of Helix being a bitch. RealPlayer is working fiiiiiine.

Nathan

I wish it were working fine for me!  I followed your instructions for installing real RealPlayer and now RealPlayer launches and the test clips at the RealPlayer test page play fine (and when there is network congestion at the higher bandwidth settings it displays a helpful message to that effect)  That's all great!

But none of the other Real Player test sites that were working with the previous setup (mplayer with Helix plug-in) work anymore.  Here is a sample of URLs that don't work with the real RealPlayer (for me, anyway):

[http://www.udel.edu/UMS/itv/realplayer/test.html](http://www.udel.edu/UMS/itv/realplayer/test.html)

[http://www.digital-one.fi/realplayer.html](http://www.digital-one.fi/realplayer.html)

[http://www.webpk.de/videotest/test_real_e.html](http://www.webpk.de/videotest/test_real_e.html)

[http://real.unl.edu/lpe/rm-demo.html](http://real.unl.edu/lpe/rm-demo.html)

Now they all return the dreaded "Additional plugins are required to play all media on this page" message.  Clicking the box that says install additional plug-ins says that the RealPlayer 10.5 plugin is available. (But everytime I go further than this, Firefox hangs).  I have tried your suggestions about what to do if Firefox says you need additional plug-ins, but now you say this isn't required because Helix wasn't working.

My experience with the previous setup was that all the above-mentioned sites were working and the RealPlayer test clips would sometimes play and sometimes not. I'm not sure which situation is better, but I have problems either way.

Any further thoughts, suggestions?

---

### Post by ubuntu-freak on 2008-01-17
**IMPORTANT STREAMING INFO**

If your RealPlayer's playback is terrible (mine was) you have to do some manual editing. First of all, install "alsa-oss" (added to "Essential" in Part 1). Now you need to keep the Terminal open and paste this command into it

**gksudo gedit /usr/bin/realplay**

Now you have to find the line "echo "Warning: LD_PRELOAD=\"$LD_PRELOAD\"" and underneath "fi" paste these two lines

[B]LD_PRELOAD="$LDPRELOAD:/usr/lib/libaoss.so"
export LD_PRELOAD
[/B]

Save and close. Also, open RealPlayer's preferences and go to "Transport" and select "Use specified transport". Then go into the two configure options beneath that and untick everything except "http". You can also select your connection speed in preferences and tell RealPlayer not to send connection info back to real.com.

---

### Post by ubuntu-freak on 2008-01-17
> **bw44 said:**
> I wish it were working fine for me!  I followed your instructions for installing real RealPlayer and now RealPlayer launches and the test clips at the RealPlayer test page play fine (and when there is network congestion at the higher bandwidth settings it displays a helpful message to that effect)  That's all great!

But none of the other Real Player test sites that were working with the previous setup (mplayer with Helix plug-in) work anymore.  Here is a sample of URLs that don't work with the real RealPlayer (for me, anyway):

[http://www.udel.edu/UMS/itv/realplayer/test.html](http://www.udel.edu/UMS/itv/realplayer/test.html)

[http://www.digital-one.fi/realplayer.html](http://www.digital-one.fi/realplayer.html)

[http://www.webpk.de/videotest/test_real_e.html](http://www.webpk.de/videotest/test_real_e.html)

[http://real.unl.edu/lpe/rm-demo.html](http://real.unl.edu/lpe/rm-demo.html)

Now they all return the dreaded "Additional plugins are required to play all media on this page" message.  Clicking the box that says install additional plug-ins says that the RealPlayer 10.5 plugin is available. (But everytime I go further than this, Firefox hangs).  I have tried your suggestions about what to do if Firefox says you need additional plug-ins, but now you say this isn't required because Helix wasn't working.

My experience with the previous setup was that all the above-mentioned sites were working and the RealPlayer test clips would sometimes play and sometimes not. I'm not sure which situation is better, but I have problems either way.

Any further thoughts, suggestions?

Works perfect for me. Do you hear sound? Make sure you stopped mplayer trying to handle rm files. I did mention it in my how-to. 

**gksudo gedit /etc/mplayerplug-in.conf**

**enable-rm=0** instead of **1**

Then 
[B]
rm $HOME/.mozilla/firefox/pluginreg.dat
[/B]

Nathan

---

### Post by ubuntu-freak on 2008-01-17
Just a minor thing. Marked in bold. helix and smil need to be 0 too

keep-download=0
cachesize=1024
cache-percent=25
dload-dir=$HOME
noembed=0
autoplay=1
enable-wmp=1
enable-qt=1
**enable-rm=0**
enable-gmp=1
enable-dvx=1
enable-mpeg=1
enable-mp3=1
enable-midi=0
enable-pls=1
enable-ogg=1
**enable-smil=0**
**enable-helix=0**
nomediacache=0
nopauseonhide=1
rtsp-use-tcp=0
rtsp-use-http=0
 
This should all work perfectly now people. RealPlayer is playing every single rm, ram, rv etc. Every single one. Only problem I have now is the BBC having the crummiest wmv streams online. Who cares though, cos RealPlayer works man. I don't have trouble with wmv streams anywhere else though. Even those huge divx.com ones.

Nathan

---

### Post by mount_evans on 2008-01-17
> **reassuringlyoffensive said:**
> 
Don't forget to check some of the games out too. Briquolo is fun.


How do I see a list of the games?

---

### Post by ubuntu-freak on 2008-01-17
Sorry about all the changes made regarding Helix and such. I didn't believe it when people said it doesn't play anything. I guess they were right. It does work now people so start from the beginning if  it makes it easier for you. Make sure helix is removed, mplayer settings replaced with todays, the fix for realplayer should be applied if the playback is stuttering and freezing. Should be all fine then. Go through the how-to carefully before you ask me stuff as I'm getting off the laptop soon so I'd be left helping from pure memory (I'm not bad at that though).

Hope it all goes well for you too,

Nathan

---

### Post by ubuntu-freak on 2008-01-17
> **mount_evans said:**
> How do I see a list of the games?

I just search synaptic. I found a good pinball one. Only has 2 levels so far but it's good. Emelia Pinball.

Did you get RealPlayer working? Please say yes.

Nathan

---

### Post by bw44 on 2008-01-17
> **reassuringlyoffensive said:**
> Works perfect for me. Do you hear sound? Make sure you stopped mplayer trying to handle rm files. I did mention it in my how-to. 

**gksudo gedit /etc/mplayerplug-in.conf**

**enable-rm=0** instead of **1**

Then 
[B]
rm $HOME/.mozilla/firefox/pluginreg.dat
[/B]

Nathan

Did the URLs I listed in my previous post work perfectly too?  Did clicking on them or on the test button on the page they link to cause RealPlayer to be launched?  I must have done something wrong.  

I did disable rm in mplayer (enable-rm=0) and must have restarted Firefox after deleting pluginreg.dat at least half a dozen times.

In your new setup RealPlayer isn't launched as a plug-in is it? Firefox has been told to load the RealPlayer app.  All the links on the RealPlayer test page have a file type  of .ram.  But what if the link's file type is .rm?  Would this cause a problem? Is there some way to tell Firefox to launch RealPlayer for all related file types?

Thanks.

---

### Post by mount_evans on 2008-01-17
> **reassuringlyoffensive said:**
> I just search synaptic. I found a good pinball one. Only has 2 levels so far but it's good. Emelia Pinball.

Did you get RealPlayer working? Please say yes.

Nathan

When I go to:

[http://www.udel.edu/UMS/itv/realplayer/test.html](http://www.udel.edu/UMS/itv/realplayer/test.html)

As before, I get a pop-up that goes through the whole "contacting" and "buffering" thing, ending with the word "Stopped".  Is that success or failure?

However, the trailers at apple.com/trailer go through almost exactly the same sequence, and those DO show me a video.

The only thing I lack is the volume control.  It says "Volume 90%" when I mouse over it, but I can't find any way to change it.

---

### Post by bw44 on 2008-01-17
> **mount_evans said:**
> When I go to:

[http://www.udel.edu/UMS/itv/realplayer/test.html](http://www.udel.edu/UMS/itv/realplayer/test.html)

As before, I get a pop-up that goes through the whole "contacting" and "buffering" thing, ending with the word "Stopped".  Is that success or failure?

However, the trailers at apple.com/trailer go through almost exactly the same sequence, and those DO show me a video.

The only thing I lack is the volume control.  It says "Volume 90%" when I mouse over it, but I can't find any way to change it.

If you get "Stopped" and nothing else, that's "failure" in my book!  I've seen a lot of those at the BBC news site!

When I click on the link above I get the message "Click here to download plugin."  But this is with the "real" RealPlayer installed.

I assume you are still trying to use mplayer with the Helix plugin, as per reassuringlyoffensive's instructions.  They did work for me, and I was able to get the the link you mention to play and the  links on the  RealPlayer test page at [http://service.real.com/test/](http://service.real.com/test/) to work (sometimes).  When I mentioned these tests were erratic, reassuringlyoffensive said that he'd decided that the Helix plugin was no good, and to install the "real" Real Player."  I did this on one of my systems and the RealPlayer links all work, but the above University of Delaware one doesn't. The link has a button which says "RealPlayer Test".   This works for me with mplayer and  the Helix plugin. It links to:

rtsp://handel.udel.edu/theatrium.rm

Try putting that in your Firefox address bar and linking to it.  I get a message that says an external application has to be launched (see attached screenshot).  If I click "launch application" it launches Totem Movie Player"  

I don't know if this will help you, but I hope so.  Where are the "Apple Trailers" you are able to view?  I'd like to try something new, since I have one system with the mplayer + Helix plugin installed and one with the "real" RealPLayer, so I can compare results.  I'll let you know what happens.

Thanks.

---

### Post by ubuntu-freak on 2008-01-17
I don't know know what's wrong with your setup. Every real stream I try works now. It's basically the same as windows realplayer but quicker.
 
Is there a nphelix.so and xpt in the /usr/lib/firefox/plugins folder? Did you delete the broken symlinks before installing realplayer? RP plugin should handle all rm, ram, rv streams now that mplayer has been told not too.
 
Nathan

---

### Post by mount_evans on 2008-01-17
> **bw44 said:**
> If you get "Stopped" and nothing else, that's "failure" in my book!  I've seen a lot of those at the BBC news site!

When I click on the link above I get the message "Click here to download plugin."  But this is with the "real" RealPlayer installed.

I assume you are still trying to use mplayer with the Helix plugin, as per reassuringlyoffensive's instructions.

No, I am using (so far as I know) the most recent version of his instructions,
with the Real "Real Player".  I do not get asked to install any plugins.

> They did work for me, and I was able to get the the link you mention to play and the  links on the  RealPlayer test page at [http://service.real.com/test/](http://service.real.com/test/) to work (sometimes).

That site gives me the same result as the U Delaware one that I mentioned.

> When I mentioned these tests were erratic, reassuringlyoffensive said that he'd decided that the Helix plugin was no good, and to install the "real" Real Player."  I did this on one of my systems and the RealPlayer links all work, but the above University of Delaware one doesn't. The link has a button which says "RealPlayer Test".   This works for me with mplayer and  the Helix plugin. It links to:

rtsp://handel.udel.edu/theatrium.rm

Try putting that in your Firefox address bar and linking to it.  I get a message that says an external application has to be launched (see attached screenshot).  If I click "launch application" it launches Totem Movie Player"  

Yep, that video launches in Totem OK.  Which is weird, since Totem can't play any of the videos I have on disk without searching for Codec's first, even though I  have some pretty old, boring formats like mpg.

> I don't know if this will help you, but I hope so.  Where are the "Apple Trailers" you are able to view?  I'd like to try something new, since I have one system with the mplayer + Helix plugin installed and one with the "real" RealPLayer, so I can compare results.  I'll let you know what happens.
Thanks.

[www.apple.com/trailers](www.apple.com/trailers)

I recommend the Narnia one.

---

### Post by bw44 on 2008-01-17
> **reassuringlyoffensive said:**
> I don't know know what's wrong with your setup. Every real stream I try works now. It's basically the same as windows realplayer but quicker.
 
Is there a nphelix.so and xpt in the /usr/lib/firefox/plugins folder? Did you delete the broken symlinks before installing realplayer? RP plugin should handle all rm, ram, rv streams now that mplayer has been told not too.
 
Nathan

Thanks for all your efforts!  I'll triple check everything out and do some more testing.  When I get it working (!) I'll post the results, if I think anyone else might benefit.

Cheers.

---

### Post by bw44 on 2008-01-17
> **mount_evans said:**
> No, I am using (so far as I know) the most recent version of his instructions,
with the Real "Real Player".  I do not get asked to install any plugins.


That site gives me the same result as the U Delaware one that I mentioned.

Yep, that video launches in Totem OK.  Which is weird, since Totem can't play any of the videos I have on disk without searching for Codec's first, even though I  have some pretty old, boring formats like mpg.

[www.apple.com/trailers](www.apple.com/trailers)

I recommend the Narnia one.

Thanks a lot! Now I know which setup you're using, I'll do some more testing.   I've gotta do something else right now, but I'll check out the Apple link later and see if I can reproduce the problem and hopefully get things working as well as reassuringlyoffensive has. 

I'll be in touch!

---

### Post by ubuntu-freak on 2008-01-17
Broken links can stop packages being installed properly.
 
Just to clarify, Helix wasn't playing jack shat. It was all MPlayer and the w32codecs it uses. MPlayer is just too random with Real Media types.
 
Trust me, you will get it working. Nothing special about my Gutsy. If I installed it for someone else I'd use my how-to.
 
I'm sorry for all the changes made. I just wasn't happy with MPlayer handling RM.
 
Nathan

---

### Post by bw44 on 2008-01-17
> **reassuringlyoffensive said:**
> Broken links can stop packages being installed properly.
 
Just to clarify, Helix wasn't playing jack shat. It was all MPlayer and the w32codecs it uses. MPlayer is just too random with Real Media types.
 
Trust me, you will get it working. Nothing special about my Gutsy. If I installed it for someone else I'd use my how-to.
 
I'm sorry for all the changes made. I just wasn't happy with MPlayer handling RM.
 
Nathan

You're the greatest!  And you were right -- I got it working!  What I missed was your post about also disabling enable-smil=0 and enable-helix=0.  I think I was composing another post and it took me too long and  I didn't go back and check for new posts from you.

I'll try to give mount-evans the benefit of my experience later, if you're going off the air.

Many thanks!

---

### Post by ubuntu-freak on 2008-01-17
> **bw44 said:**
> You're the greatest!  And you were right -- I got it working!  What I missed was your post about also disabling enable-smil=0 and enable-helix=0.  I think I was composing another post and it took me too long and  I didn't go back and check for new posts from you.

I'll try to give mount-evans the benefit of my experience later, if you're going off the air.

Many thanks!

 
At last! The RealPlayer plugin loads up yeah? 
 
Are you both having problems with apple.com? I don't understand that.
 
Do me a favour and point people to my how-to if they post about streaming, java, dvd playback, video conversion, flash etc.
 
It should get everything on par with windows almost. In some cases better.
 
Nathan

---

### Post by mount_evans on 2008-01-17
> **reassuringlyoffensive said:**
> At last! The RealPlayer plugin loads up yeah? 
 
Are you both having problems with apple.com? I don't understand that.


I am not having any problems with any actual videos.  When I click on one of those Real Player test links, I get a popup with a bunch of "contacting" and "buffering" followed by the word "Stopped".  When I go to apple.com/trailers, I get the sequence I just described followed by an actual video instead of "stopped".  So the only thing I can't play is a Real Player test--I can live with that.
 
> Do me a favour and point people to my how-to if they post about streaming, java, dvd playback, video conversion, flash etc.


I have posted a link to this thread in the Ubuntu newsgroup on Usenet.

---

### Post by ubuntu-freak on 2008-01-17
> **mount_evans said:**
> I am not having any problems with any actual videos.  When I click on one of those Real Player test links, I get a popup with a bunch of "contacting" and "buffering" followed by the word "Stopped".  When I go to apple.com/trailers, I get the sequence I just described followed by an actual video instead of "stopped".  So the only thing I can't play is a Real Player test--I can live with that.
 


I have posted a link to this thread in the Ubuntu newsgroup on Usenet.

 
Thanks.
 
All rm streams will be perfect if you install realplayer and disable mplayer from handling them (rm, helix, smil).
 
If playback stutters and freezes use the fix I posted and install alsa-oss.
 
Nathan

---

### Post by mount_evans on 2008-01-17
> **reassuringlyoffensive said:**
> 
 
If playback stutters and freezes use the fix I posted and install alsa-oss.
 
Nathan

I did that pre-emptively--i.e., I didn't wait for there to be a problem.  Was that unwise?

---

### Post by ubuntu-freak on 2008-01-17
> **mount_evans said:**
> I did that pre-emptively--i.e., I didn't wait for there to be a problem.  Was that unwise?

 
Why? alsa-oss should be installed by default.
 
You gonna stick with just MPlayer? It's too random. You don't need Helix by the way. If you try RealPlayer remember to change your conf and delete the symlinks.
 
Nathan

---

### Post by mount_evans on 2008-01-17
> **reassuringlyoffensive said:**
> Why? alsa-oss should be installed by default.
 
You gonna stick with just MPlayer? It's too random. You don't need Helix by the way. If you try RealPlayer remember to change your conf and delete the symlinks.
 Nathan

One more time:  I followed what I believe is the latest version of your instructions.  RealPlayer appears in my Applications menu now, so i assume it got installed.  I deleted the symlinks.  In fact, most of your commands have been executed multiple times by now; I hope that doesn't screw anything up.

---

### Post by ubuntu-freak on 2008-01-17
> **mount_evans said:**
> One more time:  I followed what I believe is the latest version of your instructions.  RealPlayer appears in my Applications menu now, so i assume it got installed.  I deleted the symlinks.  In fact, most of your commands have been executed multiple times by now; I hope that doesn't screw anything up.

 
Nah wont screw anything up. It will skip anything installed already or uninstalled. Does RealPlayer stream on BBC now?

I thought you kept Helix etc that's why I asked in my other post. 

Nathan

---

### Post by mount_evans on 2008-01-18
> **reassuringlyoffensive said:**
> Nah wont screw anything up. It will skip anything installed already or uninstalled. Does RealPlayer stream on BBC now?

I thought you kept Helix etc that's why I asked in my other post. 

Nathan

Ah!  I think I see now--I didn't delete the plugins.dat file.  Once I did, the RealPlayer test files at U of Delaware worked, but the ones at service.real.com don't.  The trailers at apple.com still open in mplayer, which is clunky in some ways--If even attempt to watch one of the high definition trailers, stuff bogs down and even if I exit FireFox, processes remain running.  Should those trailers be opening in mplayer or RealPlayer?  Also, the first time I encountered a .RAM file I told FireFox to open such files in RealPlayer automatically from now on.  I hope that was the right thing to do.  But funny thing is, RAM doesn't show up in FireFox's "File Types" list.

---

### Post by ubuntu-freak on 2008-01-18
> **mount_evans said:**
> Ah!  I think I see now--I didn't delete the plugins.dat file.  Once I did, the RealPlayer test files at U of Delaware worked, but the ones at service.real.com don't.  The trailers at apple.com still open in mplayer, which is clunky in some ways--If even attempt to watch one of the high definition trailers, stuff bogs down and even if I exit FireFox, processes remain running.  Should those trailers be opening in mplayer or RealPlayer?  Also, the first time I encountered a .RAM file I told FireFox to open such files in RealPlayer automatically from now on.  I hope that was the right thing to do.  But funny thing is, RAM doesn't show up in FireFox's "File Types" list.

 
It showed up in mine cos of that official Real test site. Firefox should be asking what you want to do with them. You should tell it to open them with RealPlayer in /usr/bin. It's all in my how-to.
 
MPlayer handles all Quicktime media. It shouldn't be clunky if you're using the xv driver. 
 
Nathan

---

### Post by gvaisman on 2008-01-18
Hello, I am a new user and must be doing something wrong. I have followed the steps in how-to and it accepted all the commands, but when I try to stream video from corbina.tv I get sound after a delay of about 2-3 minutes but no video. Can someone please help.

Thanks

---

### Post by ubuntu-freak on 2008-01-18
> **gvaisman said:**
> Hello, I am a new user and must be doing something wrong. I have followed the steps in how-to and it accepted all the commands, but when I try to stream video from corbina.tv I get sound after a delay of about 2-3 minutes but no video. Can someone please help.

Thanks

 
What type of media was it? Have you tried other sites?
 
Nathan

---

### Post by mount_evans on 2008-01-18
> **gvaisman said:**
> Hello, I am a new user and must be doing something wrong. I have followed the steps in how-to and it accepted all the commands, but when I try to stream video from corbina.tv I get sound after a delay of about 2-3 minutes but no video. Can someone please help.
Thanks

I tried this out with:
[http://www.corbina.tv/flashplayer/player2.php?link=http://sansara.corbina.tv/videoout/Internet_Films/Poskakushechka.flv&idf=14835&ib=161&idc=1293](http://www.corbina.tv/flashplayer/player2.php?link=http://sansara.corbina.tv/videoout/Internet_Films/Poskakushechka.flv&idf=14835&ib=161&idc=1293)
 At first I thought that there was no video, but what had happened is that the media player opened in a new tab but did not make that the current tab, while shrinking the browser window to media player size.  So I was seeing a small rectangle of the page the video was selected from while hearing the sound.  When I re-expanded the window and switched to the tab with the player in it, I saw the video.  However, the playback was stuttery, even if I paused the video and let it load completely first.

---

### Post by ubuntu-freak on 2008-01-18
Is it a flash video? I've heard people using Gnash for flash have that problem. Should use Adobe.
 
Nathan

---

### Post by bw44 on 2008-01-19
> **mount_evans said:**
> I tried this out with:
[http://www.corbina.tv/flashplayer/player2.php?link=http://sansara.corbina.tv/videoout/Internet_Films/Poskakushechka.flv&idf=14835&ib=161&idc=1293](http://www.corbina.tv/flashplayer/player2.php?link=http://sansara.corbina.tv/videoout/Internet_Films/Poskakushechka.flv&idf=14835&ib=161&idc=1293)
 At first I thought that there was no video, but what had happened is that the media player opened in a new tab but did not make that the current tab, while shrinking the browser window to media player size.  So I was seeing a small rectangle of the page the video was selected from while hearing the sound.  When I re-expanded the window and switched to the tab with the player in it, I saw the video.  However, the playback was stuttery, even if I paused the video and let it load completely first.

I just inked to that site and exactly the same things happened on my system (for what that's worth!) I think the corbina site is doing something a bit eccentric with resizing the whole Firefox window, but I don't know why the playback is stuttery.

By the way, did you get the problems you were having with RealPlayer sorted? It's working very well now for me, so I even switched my BBC media player preferences to RealPlayer.  The only odd thing is that when I click on a video link (e.g. [http://www.bbc.co.uk/mediaselector/check/player/nol/newsid_6900000/newsid_6903100?redirect=6903113.stm&news=1&nbram=1&nbwm=1&bbwm=1&bbram=1&asb=1](http://www.bbc.co.uk/mediaselector/check/player/nol/newsid_6900000/newsid_6903100?redirect=6903113.stm&news=1&nbram=1&nbwm=1&bbwm=1&bbram=1&asb=1)) It opens its (BBC's) media reader window, but after a few seconds stops.  If I then click on "open in a standalone player" (bottom left of BBC window) a RealPlayer window opens and plays the video back there with no problems.  I think this problem has to do with the way BBC redirects the link request to their advertising server and then back;  I had a similar problem when using mplayer's WMP plug-in.

I visited the Apple movie page and watched the Narnia trailer as you suggested. (Made me want to see the film!)  It played very well at both small and medium playback levels, but as Nathan mentioned, Firefox uses the mplayer QuickTime plugin for this, so it really doesn' t have anything to do with RealPlayer.

Cheers.

PS I should have mentioned that the corbina site video is FlashPlayer and I viewed it using Adobe Flash

---

### Post by mount_evans on 2008-01-19
> **reassuringlyoffensive said:**
> Is it a flash video? I've heard people using Gnash for flash have that problem. Should use Adobe.
 
Nathan

I have whatever Flash player results from following the very first line of your HOW-TO.

BTW, is the HOW-TO equally applicable to Kubuntu?  Or does someone need to do this all over for the KDE environment?  For some of the other problems I have been having, I get the recommendation "You should have gone with Kubuntu, Gnome is crap."  Of course, back when I ran KDE, I was told "You should have gone with Gnome, KDE is crap."  Sometimes from the same people.

---

### Post by ubuntu-freak on 2008-01-19
> **mount_evans said:**
> I have whatever Flash player results from following the very first line of your HOW-TO.

BTW, is the HOW-TO equally applicable to Kubuntu?  Or does someone need to do this all over for the KDE environment?  For some of the other problems I have been having, I get the recommendation "You should have gone with Kubuntu, Gnome is crap."  Of course, back when I ran KDE, I was told "You should have gone with Gnome, KDE is crap."  Sometimes from the same people.

 
I like KDE but they are talking nonesense. They are the same distro afterall. However, KDE is far from crap. I respect all the work they have and are putting into KDE4.
 
It will work with Kubuntu, just need KMPlayer, 3gpwiz instead of Winff and there's a KDE frontend for VLC too.
 
Nathan 
 
P.S. Are you the one who installed my flash that didn't need to? Make sure you don't have two. Check /usr/lib/firefox/plugins

---

### Post by Bossieman on 2008-01-19
This app doesnt work at all for me. I cant convert .avi to any format exept for .mov. What dependencies do I need?

---

### Post by ubuntu-freak on 2008-01-19
> **Bossieman said:**
> This app doesnt work at all for me. I cant convert .avi to any format exept for .mov. What dependencies do I need?

 
Winff? Did you install all the essential packages in part 1?
 
Nathan

---

### Post by Bossieman on 2008-01-19
> **reassuringlyoffensive said:**
> Winff? Did you install all the essential packages in part 1?
 
Nathan

I get a message that win32 codecs is not available. I didnt install realplayer but is that a must?
I use ffmpeg from  repos.

---

### Post by Bossieman on 2008-01-19
Problem solved. Added medibuntu repos.

---

### Post by ubuntu-freak on 2008-01-19
> **Bossieman said:**
> Problem solved. Added medibuntu repos.

 
Lol nice one. How did you miss that? Make sure you install all of those essential packages. 
 
You didn't do the streaming or DVD section? Worth doing.
 
Glad you got it sorted.
 
Nathan

---

### Post by ubuntu-freak on 2008-01-19
> **Bossieman said:**
> I get a message that win32 codecs is not available. I didnt install realplayer but is that a must?
I use ffmpeg from  repos.

 
If you don't watch much streaming content then I guess you don't have to. You should do the DVD section though. It's easy too.
 
Nathan

---

### Post by Bossieman on 2008-01-19
I still got some problem converting stuff, cant get swf to work but I use a script for swf so it doesnt matter but I try the whole guide and see if it fixes it.

---

### Post by ubuntu-freak on 2008-01-19
> **Bossieman said:**
> I still got some problem converting stuff, cant get swf to work but I use a script for swf so it doesnt matter but I try the whole guide and see if it fixes it.

 
3gp doesn't work for me. 3g2 does though. I'm gonna look into it monday.
 
Nathan

---

### Post by ubuntu-freak on 2008-01-19
Just want to point out this how-to isn't finished yet. Still have some tests to do and see what other packages I should add to the 'Essential' section. I'll be doing that next week. The streaming section is finished though.
 
I'd suggest you go to divx.com, they have some great HD streams you can test MPlayer with.
 
Nathan

---

### Post by rmcder on 2008-01-19
**reassuringlyoffensive:**

I've followed your guide, and all seems to be working well.  I find that I still have installed:
libtotem-plparser7
totem

I also have totem-xine installed, of course, as part of the dvd package from your guide.  Is there any need for the first two, or can I safely uninstall them at this point?

---

### Post by ubuntu-freak on 2008-01-19
> **rmcder said:**
> **reassuringlyoffensive:**

I've followed your guide, and all seems to be working well.  I find that I still have installed:
libtotem-plparser7
totem

I also have totem-xine installed, of course, as part of the dvd package from your guide.  Is there any need for the first two, or can I safely uninstall them at this point?

 
I've found it useful to have a few movie players installed to be honest. I have Totem, MPlayer, VLC and RealPlayer. 
 
I guess if you wanted to remove Totem/Xine you could. Use VLC for DVD's as my how-to suggests and MPlayer for avi's' mpegs' wmv's etc. If MPlayer has a problem with a vid then try it in VLC.
 
Nathan

---

### Post by Scar-face on 2008-01-20
**reassuringlyoffensive**,

I followed your guide but Firefox says java isn't installed any ideas?

I need it for [www.cs-manager.com](www.cs-manager.com), there ain't any other websites i need it for. it just says that java isn't installed :confused:

---

### Post by ubuntu-freak on 2008-01-20
> **Scar-face said:**
> **reassuringlyoffensive**,

I followed your guide but Firefox says java isn't installed any ideas?

I need it for [www.cs-manager.com](www.cs-manager.com), there ain't any other websites i need it for. it just says that java isn't installed :confused:

 
Did you install the ubuntu-restricted-extras? Check Synaptic, system>adminstration and search for sun java. Make sure the plugin is installed for java6, and jre, bin, fonts. If they are, check /usr/lib/firefox/plugins and make sure a java plugin is in there. If it is, try this again
 
rm $HOME/.mozilla/firefox/pluginreg.dat
 
Then start FF and type about ; plugins (no spaces) in the address bar, then enter. Should say you have java and more.
 
Nathan

---

### Post by ubuntu-freak on 2008-01-20
If absolutely none of that works, install sun java5 jre, plugin, fonts (remove java6 first). 
 
You don't have both java5 and 6 installed do you? Might be your problem. If so, remove java5 (plugin, jre, bin, fonts) and reinstall java6.
 
Nathan

---

### Post by Scar-face on 2008-01-20
No, I only have java6 installed with the line you stated in your first post. (I'm on 64 bit so i removed cw32codecs)

I checked in Synaptic, and jre and bin were installed fonts wasn't so I checked fonts for installing. Restarted the browser still same message.

I checked /usr/lib/firefox/plugins, no luck doesn't say anything about java.

Should i do a 'rm $HOME/.mozilla/firefox/pluginreg.dat' ?

Scar-face

---

### Post by ubuntu-freak on 2008-01-20
> **Scar-face said:**
> No, I only have java6 installed with the line you stated in your first post. (I'm on 64 bit so i removed cw32codecs)

I checked in Synaptic, and jre and bin were installed fonts wasn't so I checked fonts for installing. Restarted the browser still same message.

I checked /usr/lib/firefox/plugins, no luck doesn't say anything about java.

Should i do a 'rm $HOME/.mozilla/firefox/pluginreg.dat' ?

Scar-face

 
No only do that rm command if your plugin folder changes. You didn't say if java plugin was showing as installed in synaptic.
 
Nathan

---

### Post by Scar-face on 2008-01-20
what's the name of the plugin :confused: I can't seem to find it in synaptic.
(sorry for the stupid question)

---

### Post by bw44 on 2008-01-20
> **Scar-face said:**
> what's the name of the plugin :confused: I can't seem to find it in synaptic.
(sorry for the stupid question)

sun-java6-plugin

(There's no such thing as a stupid question!)

EDIT  - Sorry -- I didn't know there was no plugin for the 64-bit version of Ubuntu as Nathan points out
below.  (There are no stupid questions, but there are wrong answers!)

---

### Post by ubuntu-freak on 2008-01-20
> **Scar-face said:**
> what's the name of the plugin :confused: I can't seem to find it in synaptic.
(sorry for the stupid question)

 
It's not a stupid question. 64 bit Ubuntu doesn't have a plugin for java cos Sun haven't made one.
 
You can either install the 32 bit Ubuntu and follow my how-to again, or install the 32 bit browser and plugins on your 64 bit system.
 
Personally I would have the 32 bit Ubuntu, but here is the how-to if you wanna have a mixed system
 
[http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435)
 
Nathan

---

### Post by mount_evans on 2008-01-20
> P.S. Are you the one who installed my flash that didn't need to? Make sure you don't have two. Check /usr/lib/firefox/plugins

Here are the contents.  I note that I have m-player rm plugins, but no RealPlayer plugins of any kind.  I also still have helix plugins.  should I be pruning these somehow?

flashplugin-alternative.so
libjavaplugin.so
libunixprintplugin.so
mplayerplug-in-dvx.so
mplayerplug-in-dvx.xpt
mplayerplug-in-qt.so
mplayerplug-in-qt.xpt
mplayerplug-in-rm.so
mplayerplug-in-rm.xpt
mplayerplug-in.so
mplayerplug-in-wmp.so
mplayerplug-in-wmp.xpt
mplayerplug-in.xpt
nphelix.so
nphelix.xpt
nppdf.so

---

### Post by mount_evans on 2008-01-20
> **bw44 said:**
> sun-java6-plugin

(There's no such thing as a stupid question!)

EDIT  - Sorry -- I didn't know there was no plugin for the 64-bit version of Ubuntu as Nathan points out
below.  (There are no stupid questions, but there are wrong answers!)

I have heard one example of a stupid question.  On a long car trip, the driver asks one of the passengers "Do you still have to go to the bathroom?"

---

### Post by ubuntu-freak on 2008-01-20
> **mount_evans said:**
> Here are the contents.  I note that I have m-player rm plugins, but no RealPlayer plugins of any kind.  I also still have helix plugins.  should I be pruning these somehow?

flashplugin-alternative.so
libjavaplugin.so
libunixprintplugin.so
mplayerplug-in-dvx.so
mplayerplug-in-dvx.xpt
mplayerplug-in-qt.so
mplayerplug-in-qt.xpt
mplayerplug-in-rm.so
mplayerplug-in-rm.xpt
mplayerplug-in.so
mplayerplug-in-wmp.so
mplayerplug-in-wmp.xpt
mplayerplug-in.xpt
nphelix.so
nphelix.xpt
nppdf.so

 
The nphelix plugins are RealPlayers. I said in my how-to they have the same name but are unrestricted. It was GNU/Linux people that made the Linux version of RealPlayer, then they made another one, named it Helix and removed propriatry support.
 
Looks like you have flash. It should work. Do you run a 32 bit Ubuntu?
 
Nathan

---

### Post by mount_evans on 2008-01-20
> **reassuringlyoffensive said:**
> The nphelix plugins are RealPlayers. I said in my how-to they have the same name but are unrestricted. It was GNU/Linux people that made the Linux version of RealPlayer, then they made another one, named it Helix and removed propriatry support.

I thought you saind that Helix wasn't doing anything.
 
> Looks like you have flash. It should work. Do you run a 32 bit Ubuntu?
Nathan

Yes, everything works so far as I can tell.
I assume I have 32 bit Ubuntu.  I downloaded the CD image, burned the CD, and did as I was told.  I doubt this machine is 64 bit, so it wouldn't be running if it wasn't 32 bit Ubuntu.

---

### Post by ubuntu-freak on 2008-01-20
> **mount_evans said:**
> I thought you saind that Helix wasn't doing anything.
 


Yes, everything works so far as I can tell.
I assume I have 32 bit Ubuntu.  I downloaded the CD image, burned the CD, and did as I was told.  I doubt this machine is 64 bit, so it wouldn't be running if it wasn't 32 bit Ubuntu.

 
Helix doesn't support rm formats and RealPlayer does.
 
I don't know why you're having problems with flash. It worked before you installed the alternative yeah? I presume you uninstalled the other one as it's not in the plugins folder. 
 
Strange. 
 
Nathan

---

### Post by mount_evans on 2008-01-20
> **reassuringlyoffensive said:**
> Helix doesn't support rm formats and RealPlayer does.

I thought you said that Helix wasn't doing *anything*, and removed it from the HOW-TO.  Any reason to still have plug-ins for it?
 
> I don't know why you're having problems with flash.

The only problems I have been having with Flash is that some videos start and stop (and possibly skip) even if you pause them and give them time to load completely.  But this was true in Windows too, so maybe it's just unfixable.  

I have been posting in this thread mainly for follow-up purposes; for example, I was able to see those Polish videos that the other guy was having problems with.  I can view pretty much every video out there except for some HD ones.  I can listen to most online radio, though this one here just crashed FireFox:

[http://www.filk.com/radio.html](http://www.filk.com/radio.html)

Also it seems to have no volume controls.  Not inoperable, but missing.  That could be poor site design, though.  (I am listening to it now, so it *can* be played, if I am willing to risk the occasional crash.)

> It worked before you installed the alternative yeah? I presume you uninstalled the other one as it's not in the plugins folder. 

I am not aware of having uninstalled it; I just followed directions.  Is there any way I can check?

---

### Post by ubuntu-freak on 2008-01-20
Oh okay. You're alright then. Can't expect every site to be perfect.
 
I've said it before but I'll say it again. RealPlayer's plugins are called nphelix too. I already told you the history of Helix and the Linux version of RealPlayer.
 
Nathan

---

### Post by Payrok on 2008-01-21
I'm having an issue with totem still trying to play video streams of wmv type in firefox, even though I've followed through the steps posted here with no problems, and totem is not listed in the list of "about : plugins" inside the browser.    

I've looked in system->preferences->preffered applications, and rhythmbox is displayed as the default for multimedia.  I've looked in the browser preferences as well, and the strange thing there is this, mplayerplug-in.so is indicated for 70% of the file types, totem is not listed once, but the totem icon appears next to the app inside edit-preferences-content tab-file types-manage.  

Any suggestions how to correct this?  

This was the video I was testing with: mms://mschnlnine.wmod.llnwd.net/a1809/d1/ch9/0/WelcomeDan_s_ch9.wmv

---

### Post by sofasurfer on 2008-01-21
When you say "delete everything listed" do you mean to comment them out?
When I ran 'gksudo gedit /etc/mplayerplug-in.conf', the list that I got showed everything already commented out(#).
My list did not have everything that your list has. And when you said "make sure that "enable-rm" "helix" and "smil" are set to 0", I do not have 'enable-rm'. Should I just add it?

Here is my list...

#debug=0
#vo=xv,x11
#ao=arts,esd,oss
#download=1
#dload-dir=$HOME/tmp
#keep-download=0
#noembed=0
#cachesize=512
#use-mimetypes=0
#enable-ogg=1
#enable-smil=1
#enable-helix=1
#qt-speed=med
#rtsp-use-tcp=0
#nomediacache=0
#framedrop=0
#autosync=0
#mc=1
#black-background=0
#user-agent=NSPlayer

---

### Post by Scar-face on 2008-01-21
thnx nathan,

I'm using 64bit because I was advised to do so. what is the big difference between them?
why should I choose 32bit or 64bit?

sorry for the off-topic but just want everything to work :D

---

### Post by ubuntu-freak on 2008-01-21
> **Scar-face said:**
> thnx nathan,

I'm using 64bit because I was advised to do so. what is the big difference between them?
why should I choose 32bit or 64bit?

sorry for the off-topic but just want everything to work :D

Well to be honest, 64-bit is far better in Linux than Windows. Most 32-bit packages have 64-bit versions. There are some annoyances though. Sun Java don't make a plugin for 64-bit browsers. Adobe don't make a flash plugin for 64-bit browsers either.

The link I posted to the other how-to lets you install a 32-bit browser on your 64-bit system. Ubuntu 32-bit will work fine on your system, but it's up to you. In a way it's odd to let Sun and Adobe have such a big influence on what kind of system you run. So maybe just the browser and plugins is the best way to go.

Nathan

---

### Post by mount_evans on 2008-01-21
> **Payrok said:**
> I'm having an issue with totem still trying to play video streams of wmv type in firefox, even though I've followed through the steps posted here with no problems, and totem is not listed in the list of "about : plugins" inside the browser.    

I've looked in system->preferences->preffered applications, and rhythmbox is displayed as the default for multimedia.  I've looked in the browser preferences as well, and the strange thing there is this, mplayerplug-in.so is indicated for 70% of the file types, totem is not listed once, but the totem icon appears next to the app inside edit-preferences-content tab-file types-manage.  

Any suggestions how to correct this?  

This was the video I was testing with: mms://mschnlnine.wmod.llnwd.net/a1809/d1/ch9/0/WelcomeDan_s_ch9.wmv

I tried that link, and FireFox said that it had received a request to open that file in totem (it didn't give me any way of choosing a different player) and when I agreed, totem said it couldn't play that file.  The file types manager in FireFox says that mplayer is the designated player for anything with a wmv extension; why does it try to open the video in Totem?

---

### Post by Payrok on 2008-01-21
> **mount_evans said:**
> I tried that link, and FireFox said that it had received a request to open that file in totem (it didn't give me any way of choosing a different player) and when I agreed, totem said it couldn't play that file.  The file types manager in FireFox says that mplayer is the designated player for anything with a wmv extension; why does it try to open the video in Totem?

That is my question exactly.  I couldn't find any reason for firefox to open the video in totem, but there it is... :confused:

---

### Post by bw44 on 2008-01-21
> **Payrok said:**
> That is my question exactly.  I couldn't find any reason for firefox to open the video in totem, but there it is... :confused:

I clicked on the link from within my mail program (Thunderbird) when I got the notification of the post.  Firefox** wasn't** launched, but I got the message about needing an external application, totem.  I clicked "Launch application" and totem started and played the video (not very well).

I don't understand why, put if you change the mms to http at the beginning of the link

[http://mschnlnine.wmod.llnwd.net/a1809/d1/ch9/0/WelcomeDan_s_ch9.wmv](http://mschnlnine.wmod.llnwd.net/a1809/d1/ch9/0/WelcomeDan_s_ch9.wmv)

then  Firefox seems able to make the connection and launches mplayer which plays the video successfully.

??

---

### Post by ubuntu-freak on 2008-01-21
> **Payrok said:**
> That is my question exactly.  I couldn't find any reason for firefox to open the video in totem, but there it is... :confused:

 
The main Totem player tries to play it? If so, try right clicking on a wmv vid you have on your comp, then click on the 'Open with' tab. See if MPlayer is in the list, if not type 'gmplayer' in the command bit at the bottom. That should fix it. I think MPlayer will then choose to open it with it's plugin, as I've never had MPlayer try and play a vid in it's main program when the vid is from a webpage.
 
Nathan

---

### Post by mount_evans on 2008-01-21
> **bw44 said:**
> 
I don't understand why, put if you change the mms to http at the beginning of the link

[http://mschnlnine.wmod.llnwd.net/a1809/d1/ch9/0/WelcomeDan_s_ch9.wmv](http://mschnlnine.wmod.llnwd.net/a1809/d1/ch9/0/WelcomeDan_s_ch9.wmv)

then  Firefox seems able to make the connection and launches mplayer which plays the video successfully.

??

I just tried your link, in FireFox, and it does launch mplayer.  Which gives the word "Stopped" rather than playing the video.  :-(

---

### Post by bw44 on 2008-01-22
> **mount_evans said:**
> I just tried your link, in FireFox, and it does launch mplayer.  Which gives the word "Stopped" rather than playing the video.  :-(

This is a long shot, but  there are two mplayerplug-in.conf files:  the one which Nathan mentioned is in /etc and the other is in your home directory ~/.mplayer/ .  When the plugin starts it takes option values from /etc/mplayerplug-in.conf first and then looks at the ones in ~/.mplayer/mplayerplug-in.conf and overwrites with these.  (When you right-click on the mplayer window that is started by Firefox and click on "Configure" you can change some of the values in the ~/ version of the file -- if you edit the file before and after making a change this way, you'll see the values have changed.)

I've had problems in the past because I thought that if you remove all the options in the  ~/ version of the configuration file that everything would be controlled by the one in /etc.  But for some reason values are copied by mplayer  into the ~/ version.  If you then modify an option in the /etc file, it may be overwritten by one in the ~/ file.  

For example, Nathan said to change the enable-smil and enable-helix options to "0" which I did in /etc/mplayerplug-in.conf.  RealPlayer still didn't take over until I changed these options in the ~/.mplayer/mplayerplug-in.conf file as well.

I have also  had problems with mplayer "Stopped" which were caused by this problem.

So check the values in the  ~/.mplayer version of the file and make sure they are as they should be.

Hope it helps.

---

### Post by ubuntu-freak on 2008-01-22
> **bw44 said:**
> This is a long shot, but  there are two mplayerplug-in.conf files:  the one which Nathan mentioned is in /etc and the other is in your home directory ~/.mplayer/ .  When the plugin starts it takes option values from /etc/mplayerplug-in.conf first and then looks at the ones in ~/.mplayer/mplayerplug-in.conf and overwrites with these.  (When you right-click on the mplayer window that is started by Firefox and click on "Configure" you can change some of the values in the ~/ version of the file -- if you edit the file before and after making a change this way, you'll see the values have changed.)

I've had problems in the past because I thought that if you remove all the options in the  ~/ version of the configuration file that everything would be controlled by the one in /etc.  But for some reason values are copied by mplayer  into the ~/ version.  If you then modify an option in the /etc file, it may be overwritten by one in the ~/ file.  

For example, Nathan said to change the enable-smil and enable-helix options to "0" which I did in /etc/mplayerplug-in.conf.  RealPlayer still didn't take over until I changed these options in the ~/.mplayer/mplayerplug-in.conf file as well.

I have also  had problems with mplayer "Stopped" which were caused by this problem.

So check the values in the  ~/.mplayer version of the file and make sure they are as they should be.

Hope it helps.

 
That's interesting. Is that because you edited the one in home before? I only had to disable rm, smil and helix in the main conf. If there are no comments (#) in the main conf, it should supercede anything in your MPlayer home conf.
 
Can someone do a test for me? Put 'download=1' back in the main plugin conf at the top, then see if it buffers properly. The cache option might rely on the download option being present. Don't forget to
 
rm $HOME/.mozilla/firefox/pluginreg.dat
 
I don't have access to Ubuntu til tmoz. Thanks.
 
Nathan

---

### Post by ubuntu-freak on 2008-01-22
If you have anymore problems try
 
gedit $HOME/.mozilla/mplayerplug-in.conf
 
gedit $HOME/.mplayer/mplayerplug-in.conf
 
and then paste your settings in those as well. Then
 
rm $HOME/.mozilla/firefox/pluginreg.dat
 
Nathan

---

### Post by bw44 on 2008-01-22
> **reassuringlyoffensive said:**
> If you have anymore problems try
 
gedit $HOME/.mozilla/mplayerplug-in.conf
 
gedit $HOME/.mplayer/mplayerplug-in.conf
 
and then paste your settings in those as well. Then
 
rm $HOME/.mozilla/firefox/pluginreg.dat
 
Nathan

I did as you  suggested, except I removed everything from $HOME/.mplayer/mplayerplug-in.conf except vo=x11.  See the thumbnails of the two files below.  If I right-clicked on the mplayer window in Firefox and clicked "Configure" it would copy  some (but not all) of the values in the /etc/mplayerplug-in.conf to $HOME/.mplayer/mplayerplug-in.conf.  If these other (old) option values were left in the $HOME version they would override any new options in the /etc version. 

In my experience the download=[0/1] option does not affect the performance of mplayerplug-in.

Cheers.

---

### Post by bw44 on 2008-01-22
> **reassuringlyoffensive said:**
> That's interesting. Is that because you edited the one in home before? I only had to disable rm, smil and helix in the main conf. If there are no comments (#) in the main conf, it should supercede anything in your MPlayer home conf.
 I think you may be mistaken about this. Here's what it says on the mplayer plugin configuration page at [http://mplayerplug-in.sourceforge.net/config.php](http://mplayerplug-in.sourceforge.net/config.php).

> These files are checked for existance and opened and the options are read. The options in the last read file supersedes the options set in the previous file. The read order of the files is:

/etc/mplayerplug-in.conf
$HOME/.mozilla/mplayerplug-in.conf
$HOME/.mplayer/mplayerplug-in.conf

There is no $HOME/.mozilla/mplayerplug-in.conf file on my system, just the other two.

I assume when you say "no comments" you mean that no options are commented out in the /etc version that then appear in the $HOME version.

---

### Post by ubuntu-freak on 2008-01-22
> **bw44 said:**
> I think you may be mistaken about this. Here's what it says on the mplayer plugin configuration page at [http://mplayerplug-in.sourceforge.net/config.php](http://mplayerplug-in.sourceforge.net/config.php).



There is no $HOME/.mozilla/mplayerplug-in.conf file on my system, just the other two.

I assume when you say "no comments" you mean that no values are commented out in the /etc version that then appear in the $HOME version.

 
Yeah I checked that before you posted it. Weird coincedence. The /etc one seems to be the last to be read. 
 
I've not had these problems some people are posting about. What would say is the best advice to give? Should we keep the home version empty or have the same settings in it from the /etc one?
 
I always use the main players vo driver (xv) so I never have that in my conf. 
 
Nathan

---

### Post by bw44 on 2008-01-22
> **reassuringlyoffensive said:**
> Yeah I checked that before you posted it. Weird coincedence. The /etc one seems to be the last to be read. 
 
I've not had these problems some people are posting about. What would say is the best advice to give? Should we keep the home version empty or have the same settings in it from the /etc one?
 
I always use the main players vo driver (xv) so I never have that in my conf. 
 
Nathan

For sure the $HOME version is always read on my system **after** the /etc version.  That's why when I changed embed-smil and embed-helix to 0 in the /etc like you suggested, mplayer was still trying to use its helix plugin -- embed-smil and embed-helix were still set to 1 in $HOME/.mplayer/mplayerplug-in.conf.

I don't feel I'm expert enough to advise people on this, but for myself I plan to leave the settings in /etc/mplayerplug-in.conf alone and make sure whatever options I want are in the $HOME version:  they always seem to override the /etc ones, and** some** of them can be modified on the fly with the "Configure" context menu item on the mplayer screen.

Cheers.
Bob

PS - How do you remember all this stuff without access to your Ubuntu system?!?!

---

### Post by ubuntu-freak on 2008-01-22
> **bw44 said:**
> For sure the $HOME version is always read on my system **after** the /etc version.  That's why when I changed embed-smil and embed-helix to 0 in the /etc like you suggested, mplayer was still trying to use its helix plugin -- embed-smil and embed-helix were still set to 1 in $HOME/.mplayer/mplayerplug-in.conf.

I don't feel I'm expert enough to advise people on this, but for myself I plan to leave the settings in /etc/mplayerplug-in.conf alone and make sure whatever options I want are in the $HOME version:  they always seem to override the /etc ones, and** some** of them can be modified on the fly with the "Configure" context menu item on the mplayer screen.

Cheers.
Bob

PS - How do you remember all this stuff without access to your Ubuntu system?!?!

 
I guess cos I tinker with GNOME like it's KDE. Helps you remember stuff.
 
I think I will advise people to copy their settings to the home version so they don't conflict at all.
 
I didn't think 'download=1' was that important either, until buffering on large vids went weird. Then I read that the cache option works in conjunction with the download option.
 
Nathan

Edit: If the $HOME conf overrides the /etc one, then I might as well change my how-to and tell people to gedit $HOME/.mplayer/mplayerplug-in.conf

---

### Post by bw44 on 2008-01-22
> **reassuringlyoffensive said:**
> I think I will advise people to copy their settings to the home version so they don't conflict at all.
Nathan

But maybe also mention that they shouldn't use the mplayer context menu item "Configure."  Or, if they do use it, warn them that options will be copied from the /etc version to the $HOME version. To illustrate this I've attached a thumbnail of my $HOME/.mplayer/mplayerplug-in.conf file opened just after looking at the configuration and clicking OK in the mplayer window.  Compare it to the thumbnails in my previous posts.  You can see that while it added all the other options to the $HOME version it didn't override my setting of vo=x11.

It's  kind of weird the way mplayer handles this. But being aware of how the plugin configuration files are used should help sort out **some** problems with video streaming.  Hope so.

Bob

---

### Post by bw44 on 2008-01-22
> **reassuringlyoffensive said:**
> Edit: If the $HOME conf overrides the /etc one, then I might as well change my how-to and tell people to gedit $HOME/.mplayer/mplayerplug-in.conf

Yeah, that's my conclusion.  It's also easier to manage the $HOME version. And it gets around the problem of how to allow different users of a single system to have different configurations (though I can't offhand think of why they'd want to!)

---

### Post by ubuntu-freak on 2008-01-22
Edit: Removed for being silly

---

### Post by ubuntu-freak on 2008-01-22
Streaming section of the how-to is all updated now (again...). If it doesn't work for everyone still, I'm gonna kick myself in the balls and give up.
 
Nathan

---

### Post by TJCIB on 2008-01-22
Perfect, thanks.

I set up a Linux box at my school to show the students that there is more than Windows.  They don't need a lot of the frills and fun stuff that Ubuntu can do, but they certainly need this...

Thanks for the easy setup...

-T

---

### Post by mount_evans on 2008-01-22
> **reassuringlyoffensive said:**
> Streaming section of the how-to is all updated now (again...). If it doesn't work for everyone still, I'm gonna kick myself in the balls and give up.
 
Nathan


OK, the "Dan" video plays, but some details that may be relevant:
[LIST=1]
[*]The $HOME version of the mplayer-plugin.conf (or whatever, I am not cutting and pasting the text verbatim) did not previously exist; gedit opened it as a blank file, so there was nothing to delete.  I pasted all of your recommended stuff into it and saved it.  Ditto for the $HOME/.mozilla version, and I went and did the /etc version just in case.
[*]The link [http://mschnlnine.wmod.llnwd.net/a1809/d1/ch9/0/WelcomeDan_s_ch9.wmv](http://mschnlnine.wmod.llnwd.net/a1809/d1/ch9/0/WelcomeDan_s_ch9.wmv) plays just fine in mplayer if you delete the space between the "l" and "c" in "Welcome".  I think **this** was the glitch all along, not a streaming issue.
[*]The link [mms://mschnlnine.wmod.llnwd.net/a1809/d1/ch9/0/WelcomeDan_s_ch9.wmv](mms://mschnlnine.wmod.llnwd.net/a1809/d1/ch9/0/WelcomeDan_s_ch9.wmv) plays OK in Totem, given you delete the space again.  But I still am not given a choice of player.  What the heck is mms, and how do I edit what it chooses to open content with?
[/LIST]

---

### Post by mount_evans on 2008-01-22
Has anyone played with the "keep-download" option?  I like the idea of saving stuff I'm not supposed to have, but I have no idea where it will be saved or what it will be named.

---

### Post by bw44 on 2008-01-22
> **mount_evans said:**
> OK, the "Dan" video plays, but some details that may be relevant:
[LIST=1]
[*]The $HOME version of the mplayer-plugin.conf (or whatever, I am not cutting and pasting the text verbatim) did not previously exist; gedit opened it as a blank file, so there was nothing to delete.  I pasted all of your recommended stuff into it and saved it.
[*]The link [http://mschnlnine.wmod.llnwd.net/a1809/d1/ch9/0/WelcomeDan_s_ch9.wmv](http://mschnlnine.wmod.llnwd.net/a1809/d1/ch9/0/WelcomeDan_s_ch9.wmv) plays just fine in mplayer if you delete the space between the "l" and "c" in "Welcome".  I think **this** was the glitch all along, not a streaming issue.
[*]The link [mms://mschnlnine.wmod.llnwd.net/a1809/d1/ch9/0/WelcomeDan_s_ch9.wmv](mms://mschnlnine.wmod.llnwd.net/a1809/d1/ch9/0/WelcomeDan_s_ch9.wmv) plays OK in Totem, given you delete the space again.  But I still am not given a choice of player.  What the heck is mms, and how do I edit what it chooses to open content with?
[/LIST]There wasn't any space in "Welcome" in my version of the link.

Here's a quote from the Wikipedia article on the mms protocol. >  Microsoft's streaming server Microsoft Media Services (previously called NetShow Services) uses the Microsoft Media Server (MMS) protocol to transfer unicast data. MMS can be transported via UDP or TCP. The MMS default port is UDP/TCP 1755.

Microsoft deprecated MMS in favor of RTSP in 2003 with the release of the Windows Media Services 9 Series, but continued to support the MMS for some time in the interest of backwards compatibility. Support for the protocol was finally dropped in Windows Media Player 11 and Windows Media Services 2008[1].

Note however that Microsoft still recommends[2] using "mms://" as a "protocol rollover[3] URL". As part of protocol rollover a Windows Media Player 11 client opening an "mms://" URL will attempt to connect first with RTSP over UDP and if that fails it will attempt RTSP over TCP. Earlier Windows Media Player clients as well as version 11 after having failed RTSP will attempt MMS over UDP, then MMS over TCP. If MMS fails a modified version of a HTTP over TCP connection will be attempted.

Looks like the  mms protocol isn't handled by Firefox, or not handled properly.  When you change the link to http protocol then Firefox looks at the .wmv file type and says OK I know what to do with that (launch mplayer!)

I don't know the answer to your question about how and what to tell Firefox to open mms files with.  Sorry.

Cheers.

---

### Post by ubuntu-freak on 2008-01-22
> **mount_evans said:**
> OK, the "Dan" video plays, but some details that may be relevant:
[LIST=1]
[*]The $HOME version of the mplayer-plugin.conf (or whatever, I am not cutting and pasting the text verbatim) did not previously exist; gedit opened it as a blank file, so there was nothing to delete.  I pasted all of your recommended stuff into it and saved it.  Ditto for the $HOME/.mozilla version, and I went and did the /etc version just in case.
[*]The link [http://mschnlnine.wmod.llnwd.net/a1809/d1/ch9/0/WelcomeDan_s_ch9.wmv](http://mschnlnine.wmod.llnwd.net/a1809/d1/ch9/0/WelcomeDan_s_ch9.wmv) plays just fine in mplayer if you delete the space between the "l" and "c" in "Welcome".  I think **this** was the glitch all along, not a streaming issue.
[*]The link [mms://mschnlnine.wmod.llnwd.net/a1809/d1/ch9/0/WelcomeDan_s_ch9.wmv](mms://mschnlnine.wmod.llnwd.net/a1809/d1/ch9/0/WelcomeDan_s_ch9.wmv) plays OK in Totem, given you delete the space again.  But I still am not given a choice of player.  What the heck is mms, and how do I edit what it chooses to open content with?
[/LIST]

 
So if you go to .mplayer in your home folder there isn't a plugin conf file? Should've been.
 
I thought I posted a solution to the totem thing the other day. Didn't you see it? Go back a page or two.
 
Nathan

---

### Post by ubuntu-freak on 2008-01-22
> **reassuringlyoffensive said:**
> The main Totem player tries to play it? If so, try right clicking on a wmv vid you have on your comp, then click on the 'Open with' tab. See if MPlayer is in the list, if not type 'gmplayer' in the command bit at the bottom. That should fix it. I think MPlayer will then choose to open it with it's plugin, as I've never had MPlayer try and play a vid in it's main program when the vid is from a webpage.
 
Nathan

 
This one

---

### Post by bw44 on 2008-01-22
> **mount_evans said:**
> [*]The link [mms://mschnlnine.wmod.llnwd.net/a1809/d1/ch9/0/WelcomeDan_s_ch9.wmv](mms://mschnlnine.wmod.llnwd.net/a1809/d1/ch9/0/WelcomeDan_s_ch9.wmv) plays OK in Totem, given you delete the space again.  But I still am not given a choice of player.  What the heck is mms, and how do I edit what it chooses to open content with?
[/LIST]

Here's a link to a page where someone explains how to get Firefox to play mms and rtsp links:

[http://zerlinna.blogweb.de/archives/73-Watching-Video-streams-mms-and-rtsp-protocol.html](http://zerlinna.blogweb.de/archives/73-Watching-Video-streams-mms-and-rtsp-protocol.html)

I haven't tried it, 'cause I don't need it.  Your mileage may vary.

Good luck.

---

### Post by mount_evans on 2008-01-22
> **reassuringlyoffensive said:**
> This one

Yeah, that works if you are able to select "Open With...".  The mms protocol can safely be ignored, as you posted earlier, so I won't worry about it.  But when FireFox passes of the mms link to something else, that something else asks if you open the video in Totem or not, giving you no choice, not even "Open With...".  The only choice is go vs. no-go.  I won't worry about it, since mms is a dying protocol.

---

### Post by mount_evans on 2008-01-22
I just noticed that the brightness and contrast controls in mplayer (Equalizer -> Video) don't seem to change the display.  Is there a video player that does brightness and contrast?  One of the other threads had something about adjusting these in the video card driver, but that was for the entire screen, I think.  I just want to brighten up some dark videos as I play them.

---

### Post by ubuntu-freak on 2008-01-22
> **mount_evans said:**
> Yeah, that works if you are able to select "Open With...".  The mms protocol can safely be ignored, as you posted earlier, so I won't worry about it.  But when FireFox passes of the mms link to something else, that something else asks if you open the video in Totem or not, giving you no choice, not even "Open With...".  The only choice is go vs. no-go.  I won't worry about it, since mms is a dying protocol.


You didn't read it properly. Try again.
 
Nathan

---

### Post by mount_evans on 2008-01-22
> **reassuringlyoffensive said:**
> You didn't read it properly. Try again.
 
Nathan

OK, when I right click on a .WMV (or other video) file in the file browser, mplayer is one of the choices, and has been ever since I installed mplayer.  It is not the top, default choice, which would be nice.

---

### Post by ubuntu-freak on 2008-01-22
> **mount_evans said:**
> OK, when I right click on a .WMV (or other video) file in the file browser, mplayer is one of the choices, and has been ever since I installed mplayer.  It is not the top, default choice, which would be nice.

 
So when you open a wmv on your desktop or file browser, MPlayer starts playing it yeah? 
 
Nathan

---

### Post by ubuntu-freak on 2008-01-22
I don't know what you mean by 'top default'. Doesn't matter which is at the top, you just select which is default by clicking and putting the black dot next to it.
 
Nathan

---

### Post by bw44 on 2008-01-22
> **mount_evans said:**
> OK, when I right click on a .WMV (or other video) file in the file browser, mplayer is one of the choices, and has been ever since I installed mplayer.  It is not the top, default choice, which would be nice.
Right click on a wmv file and select "Properties."  Then select the "Open With" tab and click the radial button beside "Mplayer Movie Player."  Close this and then right click on the wmv file.  Mplayer should now be "at the top" of the properties context menu, i.e., the default Open With. You can also open the file with mplayer by double clicking on the file name.

---

### Post by ubuntu-freak on 2008-01-22
> **bw44 said:**
> Right click on a wmv file and select "Properties."  Then select the "Open With" tab and click the radial button beside "Mplayer Movie Player."  Close this and then right click on the wmv file.  Mplayer should now be "at the top" of the properties context menu, i.e., the default Open With. You can also open the file with mplayer by double clicking on the file name.

 
Oh he didn't go into properties! I should have been clearer, sorry.
 
I had to actually add MPlayer to my 'Open with' list, it wasn't in there already. The command is 'gmplayer' if you need to add it too.

 
Nathan

---

### Post by Dr. Cox on 2008-01-22
hi there.... well, i can view files within firefox now.....

however,  ALL video files i try to watch are NOW totally off in color. sometimes to red, sometimes all too blue, green.... it's awful.  even normal video playback ceased to work in EVERY player i have installed!!

WHAT CAN I DO... HELP!!!!!

---

### Post by ubuntu-freak on 2008-01-22
> **Dr. Cox said:**
> hi there.... well, i can view files within firefox now.....

however,  ALL video files i try to watch are NOW totally off in color. sometimes to red, sometimes all too blue, green.... it's awful.  even normal video playback ceased to work in EVERY player i have installed!!

WHAT CAN I DO... HELP!!!!!

 
Are you using the 'xv' video driver? Sounds like you're using 'gl'. If you can't use 'xv' try 'x11'. The how-to explains it in the important info section. 
 
Nathan

---

### Post by mount_evans on 2008-01-22
> **reassuringlyoffensive said:**
> Oh he didn't go into properties! I should have been clearer, sorry.
 
I had to actually add MPlayer to my 'Open with' list, it wasn't in there already. The command is 'gmplayer' if you need to add it too.

Nathan

No, it somehow got added when I installed it.  But now it is the default player for MPG and WMV videos.  Thanks to you and bw44

---

### Post by ubuntu-freak on 2008-01-22
> **mount_evans said:**
> No, it somehow got added when I installed it.  But now it is the default player for MPG and WMV videos.  Thanks to you and bw44

 
No problem!

---

### Post by ubuntu-freak on 2008-01-22
> **Dr. Cox said:**
> hi there.... well, i can view files within firefox now.....

however,  ALL video files i try to watch are NOW totally off in color. sometimes to red, sometimes all too blue, green.... it's awful.  even normal video playback ceased to work in EVERY player i have installed!!

WHAT CAN I DO... HELP!!!!!

 
Just realised you said ALL players. That's odd. My how-to just installs packages you need and the streaming settings wouldn't do that either. Maybe your xv playback is failing. Did it happen since you updated xorg? That could be the culprit. What graphics chip do you have?
 
Nathan

---

### Post by bw44 on 2008-01-22
> **mount_evans said:**
> No, it somehow got added when I installed it.  But now it is the default player for MPG and WMV videos.  Thanks to you and bw44

Glad to hear it finally works!

---

### Post by sf657 on 2008-01-22
hello- I recently started using 7.10 ubuntu and I can't get videos to play from websites like yahoo music and i- am -bored,etc. I went through your how to and didn't have any luck. Especially with this part-gedit $HOME/.mplayer/mplayerplug-in.conf (overrides the /etc/mplayerplug-in.conf settings)

Delete everything listed (you can keep the "vo" and "ao" options) and then cut and paste these settings. They improve streaming a great deal with certain sites which have caused problems. Make sure that "enable-rm" "helix" and "smil" are set to 0 (This is for people who have already followed my how-to previously).

download=1
cachesize=1024
cache-percent=25
keep-download=0
dload-dir=$HOME
noembed=0
autoplay=1
enable-wmp=1
enable-qt=1
enable-rm=0
enable-gmp=1
enable-dvx=1
enable-mpeg=1
enable-mp3=1
enable-midi=0
enable-pls=1
enable-ogg=1
enable-smil=0
enable-helix=0
nomediacache=0
nopauseonhide=1
rtsp-use-tcp=0
rtsp-use-http=0
                               The settings never showed up for me to change and I couldn't save them in the configuration window that popped up. If you know where I messed up I'd appreciate the help. 
 Thanks

---

### Post by ubuntu-freak on 2008-01-22
> **sf657 said:**
> hello- I recently started using 7.10 ubuntu and I can't get videos to play from websites like yahoo music and i- am -bored,etc. I went through your how to and didn't have any luck. Especially with this part-gedit $HOME/.mplayer/mplayerplug-in.conf (overrides the /etc/mplayerplug-in.conf settings)

Delete everything listed (you can keep the "vo" and "ao" options) and then cut and paste these settings. They improve streaming a great deal with certain sites which have caused problems. Make sure that "enable-rm" "helix" and "smil" are set to 0 (This is for people who have already followed my how-to previously).

download=1
cachesize=1024
cache-percent=25
keep-download=0
dload-dir=$HOME
noembed=0
autoplay=1
enable-wmp=1
enable-qt=1
enable-rm=0
enable-gmp=1
enable-dvx=1
enable-mpeg=1
enable-mp3=1
enable-midi=0
enable-pls=1
enable-ogg=1
enable-smil=0
enable-helix=0
nomediacache=0
nopauseonhide=1
rtsp-use-tcp=0
rtsp-use-http=0
                               The settings never showed up for me to change and I couldn't save them in the configuration window that popped up. If you know where I messed up I'd appreciate the help. 
 Thanks

 
What happened when you tried saving it? Did you look in the folder manually? You have to click on 'view' in the file browser and then the 'hidden' option. Have a look in the .mozilla folder too and see if there is an mplayerplug-in.conf.
 
Nathan

---

### Post by ubuntu-freak on 2008-01-22
Did you install all of the packages in part 1?

---

### Post by sf657 on 2008-01-22
okay- I tried the mplayer config again with your settings and it allowed me to save them. I also installed the packages in step 1 previous to that . Still can't play videos. And I don't even know where to find the .mozilla folder. Thanks again

---

### Post by sf657 on 2008-01-22
also when I run this command- rm $HOME/.mozilla/firefox/pluginreg.dat
it says it cannot delete file -no such file exists. thanks again.

---

### Post by fiskking on 2008-01-22
hello.  I recently followed your instructions on this thread in how to stream videos.  I am able to stream using VLC  but I am having problems after 2 or more videos are streamed.  If possible, could u lend a hand?:confused:

Heres my thread:

[http://ubuntuforums.org/showthread.php?t=675603](http://ubuntuforums.org/showthread.php?t=675603)

---

### Post by ubuntu-freak on 2008-01-22
> **sf657 said:**
> also when I run this command- rm $HOME/.mozilla/firefox/pluginreg.dat
it says it cannot delete file -no such file exists. thanks again.

 
Hmm thats odd. Files and folders with a dot infront of their names are hidden. Click on 'view' like I said before and show them. Then have a look in .mplayer and .mozilla/firefox.
 
Nathan

---

### Post by sf657 on 2008-01-22
> **reassuringlyoffensive said:**
> Hmm thats odd. Files and folders with a dot infront of their names are hidden. Click on 'view' like I said before and show them. Then have a look in .mplayer and .mozilla/firefox.
 
Nathan

I don't know where to look for .mplayer or .mozilla/firefox.

---

### Post by mount_evans on 2008-01-23
> **reassuringlyoffensive said:**
> Hmm thats odd. Files and folders with a dot infront of their names are hidden. Click on 'view' like I said before and show them. Then have a look in .mplayer and .mozilla/firefox.

As I mentioned, the file $HOME/.mplayer/mplayerplug-in.conf did not previously exist for me (though the directory $HOME/.mplayer did, and did have a few files in it) but I had no trouble saving a file with that name.  It may be because I had already told the file browser to show hidden files and directories long before that, I dunno.

I saved copies of mplayerplug-in.conf in $HOME/.mplayer, $HOME/.mozilla, and /etc.  Should that have been $HOME/.mozilla/firefox instead?

---

### Post by Dr. Cox on 2008-01-23
> **reassuringlyoffensive said:**
> Just realised you said ALL players. That's odd. My how-to just installs packages you need and the streaming settings wouldn't do that either. Maybe your xv playback is failing. Did it happen since you updated xorg? That could be the culprit. What graphics chip do you have?
 
Nathan

hi there. i'm using an intel-graphics chip in my old 1,4gh centrino acer tm290.  I haven't updated xorg as such. it was a complete clean new install.

i've now uninstalled every package of your howto and only reinstall vlc.  now the colors are fine again playing regular video files.  

would like to be able to stream video, though. any ideas?

thanks for all the help

---

### Post by ubuntu-freak on 2008-01-23
> **sf657 said:**
> I don't know where to look for .mplayer or .mozilla/firefox.

 
Already told you. They are in your home folder. You just have to show the hidden files and folders. Alphabetical order.
 
Nathan

---

### Post by ubuntu-freak on 2008-01-23
> **fiskking said:**
> hello.  I recently followed your instructions on this thread in how to stream videos.  I am able to stream using VLC  but I am having problems after 2 or more videos are streamed.  If possible, could u lend a hand?:confused:

Heres my thread:

[http://ubuntuforums.org/showthread.php?t=675603](http://ubuntuforums.org/showthread.php?t=675603)

 
No idea pal. Try the MPlayer browser plugin. You can even save your streams.
 
Nathan

---

### Post by ubuntu-freak on 2008-01-23
> **mount_evans said:**
> As I mentioned, the file $HOME/.mplayer/mplayerplug-in.conf did not previously exist for me (though the directory $HOME/.mplayer did, and did have a few files in it) but I had no trouble saving a file with that name.  It may be because I had already told the file browser to show hidden files and directories long before that, I dunno.

I saved copies of mplayerplug-in.conf in $HOME/.mplayer, $HOME/.mozilla, and /etc.  Should that have been $HOME/.mozilla/firefox instead?

 
Are the gedit $HOME and rm $HOME commands named properly? I don't understand why that guy said it couldn't find the pluginreg.dat to delete. No one else mentioned having that problem.
 
Nathan

---

### Post by ubuntu-freak on 2008-01-23
> **Dr. Cox said:**
> hi there. i'm using an intel-graphics chip in my old 1,4gh centrino acer tm290.  I haven't updated xorg as such. it was a complete clean new install.

i've now uninstalled every package of your howto and only reinstall vlc.  now the colors are fine again playing regular video files.  

would like to be able to stream video, though. any ideas?

thanks for all the help

 
You will need the essential packages. You should install them one by one and see what is causing you grief.
 
Nathan

---

### Post by bw44 on 2008-01-23
> **mount_evans said:**
> As I mentioned, the file $HOME/.mplayer/mplayerplug-in.conf did not previously exist for me (though the directory $HOME/.mplayer did, and did have a few files in it) but I had no trouble saving a file with that name.  It may be because I had already told the file browser to show hidden files and directories long before that, I dunno.

I saved copies of mplayerplug-in.conf in the $HOME/.mplayer, $HOME/.mozilla, and /etc.  Should that have been $HOME/.mozilla/firefox instead?

It might help to read the description of these files and the way they are used at:

[http://mplayerplug-in.sourceforge.net/config.php](http://mplayerplug-in.sourceforge.net/config.php)

You put the files in the right places, although I have never had one in $HOME/.mozilla directory, only the other two.  One of the key things to note (from the above referenced page) is > When you use the Configuration Dialog it sets the options in the last file so that the user settings override the system settings.

The "Configuration Dialog" is what appears when you right click in the mplayer window when it's running under Firefox.  When you select "Configure" you get a list of options that you can check or uncheck and two boxes at the bottom labeled "OK" and "Cancel".  If you enter this dialog and click "OK" it will save values previously entered in the /etc file **whether or not you have modified any of the check boxes above.**

I think Nathan modified his instructions to save values in the $HOME/.mplayer version of mplayerplug-in.conf because this file does take precedence over the other two.

I hope this helps.  Someone else was also asking about these files.

---

### Post by ubuntu-freak on 2008-01-23
I've just tested all the commands and they work. It doesn't matter if you haven't already got an mplayerplug-in.conf in home/username/.mplayer, just save it after you add the settings to the empty file. It's deffinately the best place to add the settings. I tested the rm $HOME/.mozilla/firefox/pluginreg.dat command and it removed the file properly as it should. So everything looks fine. Enjoy!

Nathan

---

### Post by GlennW on 2008-01-23
Nathan, thanks for great amount of work that you've done in this how-to. I've been reading through this stuff in an effort to find the answer to my flash and streaming issues. I've gone back to your updated (Jan 22) version and begun to work through it. However, I'm at Part 2, #1 where you say to open RealPlayer to adjust some preferences. The issue is, RealPlayer will not open!

I'm quite the noob so like another poster said precise instructions are appreciated.

BTW, following each of the instructions to this point went without a hitch.

Thanks.

---

### Post by bw44 on 2008-01-23
> **GlennW said:**
> Nathan, thanks for great amount of work that you've done in this how-to. I've been reading through this stuff in an effort to find the answer to my flash and streaming issues. I've gone back to your updated (Jan 22) version and begun to work through it. However, I'm at Part 2, #1 where you say to open RealPlayer to adjust some preferences. The issue is, RealPlayer will not open!

I'm quite the noob so like another poster said precise instructions are appreciated.

BTW, following each of the instructions to this point went without a hitch.

Thanks.

When you say RealPlayer will not open, do you mean when you go to the Applications>Sound & Video menu (upper left of top panel in Ubuntu desktop)  and click on RealPlayer it doesn't open?  Do you get any error message?  If it does open that way, look under the Tools> menu and click preferences to adjust them.

Hope this helps.

PS.  If you don't see RealPlayer in the Applications>Sound & Video menu either it didn't install properly or you may just need to add it to that menu.  (To add it, look under System>Preferences>Main Menu. in the left-hand column look for "Sound & Video", highlight it and then in the right-hand column you will see a list of applications.  Hopefully RealPlayer is there!  Just put a check next to it and close the window.  Now RealPlayer will appear in the Applications>Sound & Video menu.)

---

### Post by ubuntu-freak on 2008-01-23
> **GlennW said:**
> Nathan, thanks for great amount of work that you've done in this how-to. I've been reading through this stuff in an effort to find the answer to my flash and streaming issues. I've gone back to your updated (Jan 22) version and begun to work through it. However, I'm at Part 2, #1 where you say to open RealPlayer to adjust some preferences. The issue is, RealPlayer will not open!

I'm quite the noob so like another poster said precise instructions are appreciated.

BTW, following each of the instructions to this point went without a hitch.

Thanks.

I've never heard of this problem. I had playback issues, but fixed that. I did a quick search and came up with this [http://ubuntuforums.org/archive/index.php/t-55069.html](http://ubuntuforums.org/archive/index.php/t-55069.html)

Hope that helps,

Nathan

---

### Post by GlennW on 2008-01-23
> **bw44 said:**
> When you say RealPlayer will not open, do you mean when you go to the Applications>Sound & Video menu (upper left of top panel in Ubuntu desktop)  and click on RealPlayer it doesn't open?  Do you get any error message?  If it does open that way, look under the Tools> menu and click preferences to adjust them.

Hope this helps.

PS.  If you don't see RealPlayer in the Applications>Sound & Video menu either it didn't install properly or you may just need to add it to that menu.  (To add it, look under System>Preferences>Main Menu. in the left-hand column look for "Sound & Video", highlight it and then in the right-hand column you will see a list of applications.  Hopefully RealPlayer is there!  Just put a check next to it and close the window.  Now RealPlayer will appear in the Applications>Sound & Video menu.)

Thanks for the quick response. Sorry I didn't include enough info. Where to start? RealPlayer 10 is listed under the Apps menu but doesn't respond when clicked. No error message, nothing... 

So, I'm stymied! I've tried to uninstall RealPlayer 10 and then, Nathan, go back and begin the how-to again but it always stonewalls me at this point.

I also don't understand when you say to look under the Tools menu. Is that "System Tools" under the Applications menu? If that's the case there's only: Automatix, Envy, KSysGuard, NTFS Configuration Tool, and nVidia Settings.

---

### Post by ubuntu-freak on 2008-01-23
> **GlennW said:**
> Thanks for the quick response. Sorry I didn't include enough info. Where to start? RealPlayer 10 is listed under the Apps menu but doesn't respond when clicked. No error message, nothing... 

So, I'm stymied! I've tried to uninstall RealPlayer 10 and then, Nathan, go back and begin the how-to again but it always stonewalls me at this point.

I also don't understand when you say to look under the Tools menu. Is that "System Tools" under the Applications menu? If that's the case there's only: Automatix, Envy, KSysGuard, NTFS Configuration Tool, and nVidia Settings.

 
Enable 'rm' in the conf until you get RealPlayer working. Then carry on with the rest of the how-to.  
 
Let me know how that link helps or doesn't help. Sounds like an identical issue though.
 
Nathan

---

### Post by GlennW on 2008-01-23
Thanks Nathan, will keep you posted.

---

### Post by GlennW on 2008-01-23
Well, Nathan, after taking your advise and continuing on with the how-to, I wish I could say that all is well. But, alas, not yet!

Issues:
- I threw a DVD in just on a lark and had no satisfaction. I tried to open it with VLC and Mplayer and Xine to no avail.

- As far as online streaming, there are several sites that are quite important to me. They used to work/stream/flow but not now. It appears to be a similar situation as many in this thread. Mplayer loads the stream, connects (you see the url in the top left of the screen), and then it says "stopped." I right click on the black screen and click "Play," and then the audio comes on for a few seconds and then stutters, stops and starts and then just quits after about 20 secs. There also is no video. Before this exercise, all I had to do was click the link and everything worked smoothly. Hmmmmm.

- My flash (youtube, about.com, etc) is the main reason I went through this. It's only slightly better now in that it stops completely after 35 seconds. No stuttering, buffering, nothing. Both audio and video just stop. When I installed Gutsy, a while back, flash playback was acceptable, with the occasional buffering but at least I could finish the clip. 

As I mentioned before, I'm a linux noob, knowing just enough to be really dangerous. I really need some guidance here.

Thanks for any assistance.

---

### Post by bw44 on 2008-01-23
> **GlennW said:**
> I also don't understand when you say to look under the Tools menu. Is that "System Tools" under the Applications menu? If that's the case there's only: Automatix, Envy, KSysGuard, NTFS Configuration Tool, and nVidia Settings.

That was only if RealPlayer would launch --"Tools" is a menu option for RealPlayer. Sorry for the confusion. 

bw44

---

### Post by ubuntu-freak on 2008-01-23
> **GlennW said:**
> Well, Nathan, after taking your advise and continuing on with the how-to, I wish I could say that all is well. But, alas, not yet!

Issues:
- I threw a DVD in just on a lark and had no satisfaction. I tried to open it with VLC and Mplayer and Xine to no avail.

- As far as online streaming, there are several sites that are quite important to me. They used to work/stream/flow but not now. It appears to be a similar situation as many in this thread. Mplayer loads the stream, connects (you see the url in the top left of the screen), and then it says "stopped." I right click on the black screen and click "Play," and then the audio comes on for a few seconds and then stutters, stops and starts and then just quits after about 20 secs. There also is no video. Before this exercise, all I had to do was click the link and everything worked smoothly. Hmmmmm.

- My flash (youtube, about.com, etc) is the main reason I went through this. It's only slightly better now in that it stops completely after 35 seconds. No stuttering, buffering, nothing. Both audio and video just stop. When I installed Gutsy, a while back, flash playback was acceptable, with the occasional buffering but at least I could finish the clip. 

As I mentioned before, I'm a linux noob, knowing just enough to be really dangerous. I really need some guidance here.

Thanks for any assistance.

 
What sites and streams? Then others can check them. Have you tried other DVD's? It's worked flawlessly for me and others. Make sure you didn't miss anything. You should check synaptic and make sure everything installed okay.
 
What graphics you got? I've never had problems with flash either. Always works. If you have w32codecs MPlayer should be fine. If it only plays sound then the codecs aren't installed.
 
Nathan

---

### Post by GlennW on 2008-01-24
> **reassuringlyoffensive said:**
> What sites and streams? Then others can check them. Have you tried other DVD's? It's worked flawlessly for me and others. Make sure you didn't miss anything. You should check synaptic and make sure everything installed okay.
 
What graphics you got? I've never had problems with flash either. Always works. If you have w32codecs MPlayer should be fine. If it only plays sound then the codecs aren't installed.
 
Nathan

I dropped in a different DVD (Superman Returns) and could only get VLC to respond. Then the playback was jerky at best. It appears, and sounds, as if only half the frames are being played. 

Regarding streaming video sites, [http://freetube.110mb.com/#plays]("http://freetube.110mb.com/#plays"), is one.  I am involved in some rather vigorous-type athletic endeavors and need to keep up on the latest. At this particular site, it just - stops... At some other sites, I could get video by moving MPlayer's config xv to x11. But even here the video window is small. The presentation, both audio and video, while synced, is choppy. The video is very fuzzy even at that small screen size. After 35 seconds, it just quits. I used to have full screen crystal clear streaming video. 

My video card is nVidia GeForce 6200 256Mb. It can't be that since, at the outset, viewing was good.

Synaptic depicts everything as being installed. w32 codecs are in place, Realplayer 10, etc. is all there. 

This is quite frustrating. Worse yet, my wife is getting a bit antsy since some of her favourite streams are down.

---

### Post by ubuntu-freak on 2008-01-24
> **GlennW said:**
> I dropped in a different DVD (Superman Returns) and could only get VLC to respond. Then the playback was jerky at best. It appears, and sounds, as if only half the frames are being played. 

Regarding streaming video sites, [http://freetube.110mb.com/#plays]("http://freetube.110mb.com/#plays"), is one.  I am involved in some rather vigorous-type athletic endeavors and need to keep up on the latest. At this particular site, it just - stops... At some other sites, I could get video by moving MPlayer's config xv to x11. But even here the video window is small. The presentation, both audio and video, while synced, is choppy. The video is very fuzzy even at that small screen size. After 35 seconds, it just quits. I used to have full screen crystal clear streaming video. 

My video card is nVidia GeForce 6200 256Mb. It can't be that since, at the outset, viewing was good.

Synaptic depicts everything as being installed. w32 codecs are in place, Realplayer 10, etc. is all there. 

This is quite frustrating. Worse yet, my wife is getting a bit antsy since some of her favourite streams are down.

 
Yes VLC is best for DVD playback, that's why I told people to make it the default DVD player.
 
Sounds like you have everything installed just fine. In my opinion, your card is having problems with accelerated video playback (hence the DVD and streaming problems). X11 is the worst driver you can use for playback as it's unaccelerated. 
 
Your card does support it though, you just need to do a bit more work. I've only used intel graphics, so not had this problem. Do a forum and google search for something like 'nvidia xv video playback'.
 
Nathan
 
Edit: Are you using open source drivers for your card or nvidia's own drivers?

---

### Post by bw44 on 2008-01-24
> **GlennW said:**
> Regarding streaming video sites, [http://freetube.110mb.com/#plays]("http://freetube.110mb.com/#plays"), is one.  I am involved in some rather vigorous-type athletic endeavors and need to keep up on the latest. At this particular site, it just - stops... At some other sites, I could get video by moving MPlayer's config xv to x11. But even here the video window is small. The presentation, both audio and video, while synced, is choppy. The video is very fuzzy even at that small screen size. After 35 seconds, it just quits. I used to have full screen crystal clear streaming video.Just to let you know some of us tried your reference site.  I was not able to view anything there, but I don't think this has anything to do with following Nathan's How-To.  I tested with two systems, one with vo=xv and the other which has to run with vo=x11.  I linked to the diagnostics page at [http://freetube.110mb.com/diagnose.php](http://freetube.110mb.com/diagnose.php) and attach a screenshot of the results. 

Obviously my sub-par Internet connection is probably the reason I can't access the streams at that site.  For the low-tech sites I visit though, everything works very well.

PS I should also mention that DVDs also play back with no problems using either VLC (my default) or Mplayer Movie Player.  Thanks again to Nathan.

---

### Post by GlennW on 2008-01-24
> **bw44 said:**
> Just to let you know some of us tried your reference site.  I was not able to view anything there, but I don't think this has anything to do with following Nathan's How-To.  I tested with two systems, one with vo=xv and the other which has to run with vo=x11.  I linked to the diagnostics page at [http://freetube.110mb.com/diagnose.php](http://freetube.110mb.com/diagnose.php) and attach a screenshot of the results. 

Obviously my sub-par Internet connection is probably the reason I can't access the streams at that site.  For the low-tech sites I visit though, everything works very well.

PS I should also mention that DVDs also play back with no problems using either VLC (my default) or Mplayer Movie Player.  Thanks again to Nathan.

Thanks bw44 for checking it out. I was going back to some of the sites, one of them being a religious site, [http://joycemeyer.org/OurMinistries/Broadcast/TV/Archive/20080124.htm]("http://joycemeyer.org/OurMinistries/Broadcast/TV/Archive/20080124.htm"), and when I choose to use RealPlayer, I was presented with a choice of player. On a lark I chose Totem and lo and behold, within 5 seconds I had my full screen, crystal clear, non-stuttering stream, no buffering, connecting, blah, blah, blah!!! So, what's up with that? I'd kind of like to have everything set up as Nathan has outlined but the fact is that MPlayer just isn't cutting the mustard. 

How do I make Totem the default player? Or am I missing some simple step somewhere? I've gone through Nathan's how-to several times already and I can't see how my Gutsy setup is much different from most other fresh-to-linux users. I need some advice/help...

---

### Post by ubuntu-freak on 2008-01-24
> **GlennW said:**
> Thanks bw44 for checking it out. I was going back to some of the sites, one of them being a religious site, [http://joycemeyer.org/OurMinistries/Broadcast/TV/Archive/20080124.htm]("http://joycemeyer.org/OurMinistries/Broadcast/TV/Archive/20080124.htm"), and when I choose to use RealPlayer, I was presented with a choice of player. On a lark I chose Totem and lo and behold, within 5 seconds I had my full screen, crystal clear, non-stuttering stream, no buffering, connecting, blah, blah, blah!!! So, what's up with that? I'd kind of like to have everything set up as Nathan has outlined but the fact is that MPlayer just isn't cutting the mustard. 

How do I make Totem the default player? Or am I missing some simple step somewhere? I've gone through Nathan's how-to several times already and I can't see how my Gutsy setup is much different from most other fresh-to-linux users. I need some advice/help...

 
You mean the main Totem player? MPlayer plugin is a bit random with RM streams, that's why I said to use RealPlayer. Are you the guy who can't get it to start? I posted a link to fix that. Didn't work? Did you get xv working?
 
Nathan

---

### Post by bw44 on 2008-01-24
> **GlennW said:**
> Thanks bw44 for checking it out. I was going back to some of the sites, one of them being a religious site, [http://joycemeyer.org/OurMinistries/Broadcast/TV/Archive/20080124.htm]("http://joycemeyer.org/OurMinistries/Broadcast/TV/Archive/20080124.htm"), and when I choose to use RealPlayer, I was presented with a choice of player. On a lark I chose Totem and lo and behold, within 5 seconds I had my full screen, crystal clear, non-stuttering stream, no buffering, connecting, blah, blah, blah!!! So, what's up with that? I'd kind of like to have everything set up as Nathan has outlined but the fact is that MPlayer just isn't cutting the mustard.

I visited that site and chose to view the video with RealPlayer at high bandwidth.  It played fine with RealPlayer.  I also tried the Windows Media Player and QuickTime versions.  Mplayer launched for both:  the WMP version played successfully, but the QuitTime one "Stopped" after apparently downloading the stream.  Don't know what that problem was about, but, hey, 2 out of 3 isn't bad!

I don't mean to crow about this success.  I know how frustrating these problems can be, but stick to it and I'm sure you'll get it working!

---

### Post by ubuntu-freak on 2008-01-24
Some people swear by the xine-plugin. You could experiment with that. You will have to remove mozilla-mplayer, and the nphelix plugin (so and xpt in /usr/lib/firefox/plugins) and delete the pluginreg.dat after you install the xine-plugin. 
 
I prefer mozilla-mplayer due to the extra options, keep-download for example, and that you can use it in conjunction with RealPlayer's nphelix plugin.
 
Nathan

---

### Post by Payteer on 2008-01-24
Hello Nathan,
I have followed what you have said and I have got BBC working, which is top.  I have my flash player going well as well. How ever DivX is a bit temperamental and when I do play the realplayer in BBC I can only view it as external player and not the in bedded  version, this is a minor inconvenience.  The DivX is the biggest problem, on Stage6 I got it working, but no sound, however on other sites, I have got it working on some streams but not others.  I think it is an mplayer problem, would you recommend either another player for DivX or how would I fix it.  
On the flash problem, that is now fixed, that I still think is brilliant.  The closer I get to getting these streaming things working and one other problem totally unrelated to streaming, PocketPC syncing, don't even get me to go there.  However as soon as I get these things fixed then bye bye Vista.
 Cheers
 
Forgot to say I am using 7.10

---

### Post by ubuntu-freak on 2008-01-24
> **Payteer said:**
> Hello Nathan,
I have followed what you have said and I have got BBC working, which is top.  I have my flash player going well as well. How ever DivX is a bit temperamental and when I do play the realplayer in BBC I can only view it as external player and not the in bedded  version, this is a minor inconvenience.  The DivX is the biggest problem, on Stage6 I got it working, but no sound, however on other sites, I have got it working on some streams but not others.  I think it is an mplayer problem, would you recommend either another player for DivX or how would I fix it.  
On the flash problem, that is now fixed, that I still think is brilliant.  The closer I get to getting these streaming things working and one other problem totally unrelated to streaming, PocketPC syncing, don't even get me to go there.  However as soon as I get these things fixed then bye bye Vista.
 Cheers
 
Forgot to say I am using 7.10

 
Thanks! 
 
Your divx problem is very odd. Stage6 is faultless for me (well, except seeking, for now). If you have sound with wmv, qt etc, you should have sound for divx. 
 
Are you using xv video playback? What about the sound driver? Experiment with MPlayer's preferences.
 
Nathan

---

### Post by Payteer on 2008-01-25
Very odd, I turned off last night, turned on today and all the problems have gone away on the sound etc.  the problem with realplayer not playing embedded is still there?  Is there a fix for this? If not don't worry about it and thanks again for your extremely good guide.

---

### Post by bw44 on 2008-01-25
> **Payteer said:**
> Very odd, I turned off last night, turned on today and all the problems have gone away on the sound etc.  the problem with realplayer not playing embedded is still there?  Is there a fix for this? If not don't worry about it and thanks again for your extremely good guide.

I have the same "problem" with RealPlayer at the BBC site.  I have selected RealPlayer in their News Player "Preferences" but when I click on a link the "embedded" RealPlayer launches but then stops.  But if I then click on "Launch in stand-alone player" it opens RealPlayer and plays the clip flawlessly.  Is this what you experience?

You also mentioned problems with DivX on Stage6.  I don't have a fast enough link to be a big user of Stage6, but I tested a couple of short clips and they worked fine.  One thing I have noticed, but have no explanation for:  when I right click on the mplayer window within Firefox and select "Configure" a list of mplayer options appears and sometimes (for no reason I can figure out) the option "Enable DivX support" has been unchecked.  If this is happening on your system, it just might be related to the problem you're having with DivX playback.

I'll post again if I figure anything out.

bw44

---

### Post by olavjunior on 2008-01-26
I don't get this.. I delete the pluginreg.dat everywhere I've found it, but it never gets regenerated! So when I type about: plugins, I just get flash and futuresplash.  And there's nothing like mplayer in the firefox's extensions. I'm using firefox 3 by the way..

EDIT: I copied the nphelix.so and nphelix.xpt to  /opt/firefox/plugins. That gave me the realplayer plugin :) But still no action on stage6 etc
EIDT: Al right.. Created symbolic links to  /usr/lib/firefox/plugins/ and that made the difference! Thanks! Sound was fixed by using the right driver in mplayer config :)

---

### Post by olavjunior on 2008-01-26
> **reassuringlyoffensive said:**
> **REVISED ON 22 JAN 2008**


enable-dvx=1

Nathan

Just want to inform you of this error, should be divx. The reason for people having problems with stage6 ect

---

### Post by bw44 on 2008-01-26
> **olavjunior said:**
> Just want to inform you of this error, should be divx. The reason for people having problems with stage6 ectWell spotted!

Thanks.

---

### Post by ubuntu-freak on 2008-01-26
> **olavjunior said:**
> Just want to inform you of this error, should be divx. The reason for people having problems with stage6 ect

No, that is incorrect. The plugin is called 'mplayerplug-in-dvx.so' and 'xpt'. That's why it's 'enable-dvx=1'.
I never have problems with stage6 and most people following my how-to don't either. One person has accelerated video problems and another had to restart his system.
  
Nathan

---

### Post by bw44 on 2008-01-26
> **reassuringlyoffensive said:**
> No, that is incorrect. The plugin is called 'mplayerplug-in-dvx.so' and 'xpt'. That's why it's 'enable-dvx=1'.
I never have problems with stage6 and most people following my how-to don't either. One person has accelerated video problems and another had to restart his system.
  
NathanNathan, I'm not going to argue with you, but I've changed the option enable-dvx=1 to enable-divx=1 in both my mplayerplug-in.conf files (/etc and $HOME/.mplayer), deleted pluginreg.dat, and restarted Firefox and am (still) able to play divx files at Stage6 and other sites (see below).

I'm starting to wonder what the status of this option is.  On the mplayer playback Configure screen the label of the check box is "Enable DivX Support" (which means nothing, as it's just a label).  But mplayer must be turning the option on and off for reasons of its own, since sometimes the box is checked and sometimes not. 

Also, enable-dvx (or divx as the case may be) is not listed on the mplayer Configuration page at [http://mplayerplug-in.sourceforge.net/config.php](http://mplayerplug-in.sourceforge.net/config.php) (but this may just be a case of documentation being out of date, since DivX plug-in emulation was added back in August, 2006.)

Here are a couple of useful plug-in test pages that are linked to from the mplayer site:

[http://www.linspire.com/products_linspire_whatis.php?tab=compatibility](http://www.linspire.com/products_linspire_whatis.php?tab=compatibility)

[http://fredrik.hubbe.net/plugger/test.html](http://fredrik.hubbe.net/plugger/test.html)

I've found them helpful for quickly checking things out.

Cheers,
bw44

---

### Post by ubuntu-freak on 2008-01-26
> **bw44 said:**
> Nathan, I'm not going to argue with you, but I've changed the option enable-dvx=1 to enable-divx=1 in both my mplayerplug-in.conf files (/etc and $HOME/.mplayer), deleted pluginreg.dat, and restarted Firefox and am (still) able to play divx files at Stage6 and other sites (see below).

I'm starting to wonder what the status of this option is.  On the mplayer playback Configure screen the label of the check box is "Enable DivX Support" (which means nothing, as it's just a label).  But mplayer must be turning the option on and off for reasons of its own, since sometimes the box is checked and sometimes not. 

Also, enable-dvx (or divx as the case may be) is not listed on the mplayer Configuration page at [http://mplayerplug-in.sourceforge.net/config.php](http://mplayerplug-in.sourceforge.net/config.php) (but this may just be a case of documentation being out of date, since DivX plug-in emulation was added back in August, 2006.)

Here are a couple of useful plug-in test pages that are linked to from the mplayer site:

[http://www.linspire.com/products_linspire_whatis.php?tab=compatibility](http://www.linspire.com/products_linspire_whatis.php?tab=compatibility)

[http://fredrik.hubbe.net/plugger/test.html](http://fredrik.hubbe.net/plugger/test.html)

I've found them helpful for quickly checking things out.

Cheers,
bw44

 
Do a google search for 'enable-divx=1 mplayer' and you will get one result only (not including this thread). Then try it with 'dvx'.
 
My main point is that jumping in and telling people to change it from 'dvx' to 'divx' as a cure for problems is just silly. It bugs me. All he had to do was search these forums, google or look at the plugin names before posting.
 
I don't know why it streams with or without it enabled, or why it works with 'divx' too. Shouldn't really. Also, I don't know why it's not on their page. Same with 'download=1', even though they mention it in the cache description and that setting seemed to make my buffering and percentage work.
 
Nathan

---

### Post by bw44 on 2008-01-26
> **reassuringlyoffensive said:**
> Do a google search for 'enable-divx=1 mplayer' and you will get one result only (not including this thread). Then try it with 'dvx'.
 
My main point is that jumping in and telling people to change it from 'dvx' to 'divx' as a cure for problems is just silly. It bugs me. All he had to do was search these forums, google or look at the plugin names before posting.

Good point -- I guess some of us are just  too eager to try and help others because we've gotten so much help ourselves.  Thanks for your patience.

---

### Post by firemaker272 on 2008-01-26
wow dude, thanks you've shown a noob the light to a very dark tunnel

thanks =D

---

### Post by RedRat on 2008-01-26
Ok tried to install Google Earth. But when running the sudo apt-get command as you stated, I  get the following:
 Couldn't find package googleearth

So I went to the Google site and downloaded GoogleEarthLinux.bin
Various attempts to install this package (running it as a command, using sudo dpkg -i, etc) all ended in no installation.

tried the following:
~$ sudo dpkg -i GoogleEarthLinux.bin
dpkg-deb: `GoogleEarthLinux.bin' is not a debian format archive
dpkg: error processing GoogleEarthLinux.bin (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 GoogleEarthLinux.bin
~$ sudo install GoogleEarthLinux.bin
install: missing destination file operand after `GoogleEarthLinux.bin'

Any ideas of how to do this under Ubuntu 7.10

OK Ignore this. I finally realized that you had to install the mediabuntu lists. Did that and all is well!

---

### Post by RedRat on 2008-01-26
> **reassuringlyoffensive said:**
> Are the gedit $HOME and rm $HOME commands named properly? I don't understand why that guy said it couldn't find the pluginreg.dat to delete. No one else mentioned having that problem.
 
Nathan
He probably did not turn on "Show Hidden Files"
In 7.10 that is turned off by default I think, at least in my installation it was. 

Be kind, he is a newbie just like me.:)

---

### Post by ubuntu-freak on 2008-01-26
> **RedRat said:**
> Ok tried to install Google Earth. But when running the sudo apt-get command as you stated, I  get the following:
 Couldn't find package googleearth

So I went to the Google site and downloaded GoogleEarthLinux.bin
Various attempts to install this package (running it as a command, using sudo dpkg -i, etc) all ended in no installation.

tried the following:
~$ sudo dpkg -i GoogleEarthLinux.bin
dpkg-deb: `GoogleEarthLinux.bin' is not a debian format archive
dpkg: error processing GoogleEarthLinux.bin (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 GoogleEarthLinux.bin
~$ sudo install GoogleEarthLinux.bin
install: missing destination file operand after `GoogleEarthLinux.bin'

Any ideas of how to do this under Ubuntu 7.10

 
Wait a second. Did you search synaptic first? You have the medibuntu repo from part 1 yeah? Installing from a bin file is fine, but try a repo or deb first.
 
Nathan
 
P.S. They didn't rename it google-earth did they?

---

### Post by ubuntu-freak on 2008-01-26
> **RedRat said:**
> He probably did not turn on "Show Hidden Files"
In 7.10 that is turned off by default I think, at least in my installation it was. 

Be kind, he is a newbie just like me.:)

 
Nah, he said the actual command didn't work. I tested them again though and they worked. He hasn't come back so it must all be okay now :-)
 
Nathan

---

### Post by ubuntu-freak on 2008-01-26
For some reason I feel like telling you guys and girls why I decided to write this how-to. 
 
At first it was just a streaming how-to, then I decided it was pointless to just write a streaming how-to, cos many people might still be missing packages and such.
 
What do most people want when they install Ubuntu? They want Youtube to work, java (Yahoo! Games), their music, videos, DVD's and maybe even video conversion capabilities. That's why it evolved into a general internet content, multimedia and video how-to, and had to be renamed by the ever responsive forum staff. I also felt it was important to write it here in the forums and not on some website.
 
Also, I don't see why a newbie would want to have to search different threads just to set this kind of system up. Or have to post threads like 'Need flash' or other single issue threads. It's exactly how I set my system up, so almost everything you need/want should be here. 
 
Think I will add a little desktop effects how-to soon. Just a basic one to get newbies goofing around with cubes and painting fire on the desktop. :-)
 
Nathan

---

### Post by RedRat on 2008-01-26
Nathan,
Sorry about the question. Shortly after posting, I figured that the googleearth package had to be somewhere. I installed the mediabuntu repo and all is well, thanks for your tips. It just wasn't clear that that particular repo had to be added to the list. Your post has cleared up quite a bit of this repository stuff for me. I, unfortunately, thought that mediabuntu was turned on in the list. Your tutorial was very helpful.

---

### Post by ubuntu-freak on 2008-01-26
> **RedRat said:**
> Nathan,
Sorry about the question. Shortly after posting, I figured that the googleearth package had to be somewhere. I installed the mediabuntu repo and all is well, thanks for your tips. It just wasn't clear that that particular repo had to be added to the list. Your post has cleared up quite a bit of this repository stuff for me. I, unfortunately, thought that mediabuntu was turned on in the list. Your tutorial was very helpful.

 
No problem.
 
Even if you're happy with your streaming, I'd recomend you install the packages in part 1 and do part 3 as well (DVD section).
 
Nathan

---

### Post by olavjunior on 2008-01-27
ok, sorry.. then I don't know why the divx-preferences gets hooked out

---

### Post by Payteer on 2008-01-27
I was just wondering if there was a faster streaming then XV.  It streams fast, but not as fast as press play and not drops.  I now have to leave it for about 20mins before playing a 45 minute divx.  I have a 100mb connection so that isn't the problem.  I watch Joost and I used to be just able to press play, but now I can't.  I have to say it does play unlike before your help on this, it would be just nice if it played faster.  (Some people are never happy, I know)  If there isn't then don't worry I'll put up with it at this speed.

---

### Post by ubuntu-freak on 2008-01-27
> **Payteer said:**
> I was just wondering if there was a faster streaming then XV.  It streams fast, but not as fast as press play and not drops.  I now have to leave it for about 20mins before playing a 45 minute divx.  I have a 100mb connection so that isn't the problem.  I watch Joost and I used to be just able to press play, but now I can't.  I have to say it does play unlike before your help on this, it would be just nice if it played faster.  (Some people are never happy, I know)  If there isn't then don't worry I'll put up with it at this speed.

 
XV doesn't have any bearing on how fast it streams. You shouldn't have to wait 45 mins but that's nothing to do with the xv driver. It's the best video driver in linux and works perfect for me. 
 
Is it just on divx.com you have this problem? It's not related to the streaming settings or xv driver, that's for sure. 
 
Nathan

---

### Post by ubuntu-freak on 2008-01-27
> **olavjunior said:**
> ok, sorry.. then I don't know why the divx-preferences gets hooked out


Don't worry about it.
 
What do you mean by 'hooked out'? If your sound is fine and you can use the xv driver then divx.com should be fine too.
 
Nathan

---

### Post by Payteer on 2008-01-27
It is just Divx, .  
The download does work but not instantaneous, I have increased the cache etc. but I generally now have to wait as I said before for about 50% of the programme before playing, this is on all websites, Joost being one and stage6.
Could it be to do with a connection problem not showing, even though I have a wired Ethernet at 100MB  driver 8130too 
You say you have no problem on this side of things.  I may have done something wrong then.  I followed your install to the letter and everything works, it is just this issue and two minor issues, the syncing between sound and video is sometimes off by a second or two and this is on the flash streamers as well, but not always, and the BBC one I mentioned before.

---

### Post by ubuntu-freak on 2008-01-27
> **Payteer said:**
> It is just Divx, .  
The download does work but not instantaneous, I have increased the cache etc. but I generally now have to wait as I said before for about 50% of the programme before playing, this is on all websites, Joost being one and stage6.
Could it be to do with a connection problem not showing, even though I have a wired Ethernet at 100MB  driver 8130too 
You say you have no problem on this side of things.  I may have done something wrong then.  I followed your install to the letter and everything works, it is just this issue and two minor issues, the syncing between sound and video is sometimes off by a second or two and this is on the flash streamers as well, but not always, and the BBC one I mentioned before.

 
It's not related to the how-to. Some have said their ethernet is slow in Ubuntu, so do a search of the forums and google. Don't have your cache too high, can effect radio streams and low bandwidth videos. 
 
Do a search for sync issues too. There are usually others who have experienced your problem.
 
Nathan

---

### Post by ubuntu-freak on 2008-01-27
My threads gone all dead. Hmmm :-l 
 
Hope you're all alive 'n' stuff. 
 
Nathan

---

### Post by johnraff on 2008-01-28
> **reassuringlyoffensive said:**
> My threads gone all dead. Hmmm :-l 
 
Hope you're all alive 'n' stuff. 
 
NathanNo your thread's still alive, though I've got nothing to contribute at this point...

---

### Post by ubuntu-freak on 2008-01-28
> **johnraff said:**
> No your thread's still alive, though I've got nothing to contribute at this point...

That's good. Beats having too many problems to mention.

Nathan

---

### Post by Payteer on 2008-01-28
Thanks for this and all your help.  
You could be getting less and less people because your how to is good and most problems have been solved.
Any joy on embedded realplayer on BBC?
Cheers:)

---

### Post by ubuntu-freak on 2008-01-28
> **Payteer said:**
> Thanks for this and all your help.  
You could be getting less and less people because your how to is good and most problems have been solved.
Any joy on embedded realplayer on BBC?
Cheers:)

 
I don't know. They must know people have problems with it and that's why they have the external player option. Some sites with reliable rm streams don't offer the external player option. BBC know they impliment it strangely. It's the genuine RealPlayer don't forget.
 
Nathan

---

### Post by bw44 on 2008-01-28
> **reassuringlyoffensive said:**
> I don't know. They must know people have problems with it and that's why they have the external player option. Some sites with reliable rm streams don't offer the external player option. BBC know they impliment it strangely. It's the genuine RealPlayer don't forget.
 
Nathan

I recently posted to another thread a form letter (email)  I got from BBC after I had repeatedly asked them about problems accessing their site from outside the UK.  Here's the relevant part, which may help answer Payteer's question about the RealPlayer support:> We have ensured that versions of Real player are available as free
downloads for virtually all types of hardware and operating systems
(Windows, Mac, Linux and more), so that everyone can have access to our
content regardless of the equipment that they choose to use.

For your information, we are currently in the process of redeveloping
the way our News and Sport clip content is presented on our site. Within
in the next few months we will be presenting our short clips as Flash
media, embedded within text pages on the News and Sport sites. It is
part of a major project to overhaul the way we present our News and
Sport video and audio coverage, which will also eventually lead to
changes in how we present our live and news programme content coverage.
It is also in line with how BBC programme content is currently offered
within the newly launched BBC iPlayer, which you can see here if you are
in the UK: [http://www.bbc.co.uk/iplayer/](http://www.bbc.co.uk/iplayer/)

I doubt BBC is going to do much about the embedded RealPlayer problem if their plan is to go to Flash! (If you're outside the UK and you try to access the link above you eventually get told you can't view the content.  Maybe Nathan can comment since he's a UK resident.)

---

### Post by ubuntu-freak on 2008-01-28
I thought you could watch them but you have to watch ads first. Odd. I don't think they know exactly what they want to do yet.
 
Lots of their stuff is gonna be on MySpace TV, so check that out. Don't know if it's ready though (I can't check right now), just remember reading about it. 
 
Nathan

---

### Post by bw44 on 2008-01-29
> **reassuringlyoffensive said:**
> I thought you could watch them but you have to watch ads first. Odd. I don't think they know exactly what they want to do yet.
 
Lots of their stuff is gonna be on MySpace TV, so check that out. Don't know if it's ready though (I can't check right now), just remember reading about it. 
 
Nathan
Yeah, with RealPlayer (launched in a standalone window after an annoying series of messages about not finding helix or realplayer in the "system path" -- see screen shot attached) you first get an ad but once it loads you just skip to the news item.

What they want to do is sell advertising.  What they can't do is make it work smoothly.  They've been at it for months.  If you edit the URLs you can bypass the ads by directing mplayer to the news clip.  Haven't found a way and can't be bothered doing the same with RealPLayer

Checked out MySpace and BBC is starting to put stuff up there. Example:

[http://ca.myspace.com/index.cfm?fuseaction=vids.individual&videoid=26677294](http://ca.myspace.com/index.cfm?fuseaction=vids.individual&videoid=26677294)

I doubt they'll be putting up their hourly news clips, though.

---

### Post by ugm6hr on 2008-01-29
Just a quick note re: the how-to in current state.

I just fresh-installed a system, and then followed the how-to.  Since you are now using the mplayer conf file in username/.mplayer, you need to create that directory first.  Presumably mplayer creates it when you first open the program, but following the how-to generates a "no file" error when trying to save the conf file (since I hadn't used mplayer by the time I tried to edit the conf).

Easy for me to fix - but probably not everyone.

---

### Post by ubuntu-freak on 2008-01-29
> **ugm6hr said:**
> Just a quick note re: the how-to in current state.

I just fresh-installed a system, and then followed the how-to.  Since you are now using the mplayer conf file in username/.mplayer, you need to create that directory first.  Presumably mplayer creates it when you first open the program, but following the how-to generates a "no file" error when trying to save the conf file (since I hadn't used mplayer by the time I tried to edit the conf).

Easy for me to fix - but probably not everyone.

 
Did you recently become a staff member?
 
Thanks for that bit of helpful advice. I made some minor changes today and included an instruction which will create that directory.
 
Thanks again.
 
Nathan

---

### Post by pprjack on 2008-01-29
Just a quick question, why has this not been made a sticky? Thanks so much for your great How-To. I just wish I didn't have to dig to find it... =)

---

### Post by ubuntu-freak on 2008-01-29
> **pprjack said:**
> Just a quick question, why has this not been made a sticky? Thanks so much for your great How-To. I just wish I didn't have to dig to find it... =)

 
Thanks. No problem.
 
I don't know how a thread becomes a ''Sticky''. If someone can shed some light I'd be grateful. Tried to find out but gave up after a while.
 
Nathan

---

### Post by evolving_monkey on 2008-01-29
Reassuringlyoffensive........that was easily one of the best "How To's"  I've seen. Very well explained and everything worked brilliantly.  Also thanks to everyone else that contributed. Exactly what I've been looking for.  Once I figure out how to officially thank you in the forum I will.

Thanks again for taking the time.

---

### Post by ubuntu-freak on 2008-01-30
> **evolving_monkey said:**
> Reassuringlyoffensive........that was easily one of the best "How To's"  I've seen. Very well explained and everything worked brilliantly.  Also thanks to everyone else that contributed. Exactly what I've been looking for.  Once I figure out how to officially thank you in the forum I will.

Thanks again for taking the time.

 
Thanks!
 
Once it became a "Almost Everything" kind of how-to, I tried to put myself in a newbies shoes. And yeah, people have contributed by having difficulties, which most haven't, but which made me edit the how-to and include more info to help or cos' it should've been there already. Obviously I didn't magically figure out all of it though, just felt it was odd that no one had already posted a how-to like this. Nice to have it all in one thread isn't it?
 
I would tell you how to thank me, but I won't. Haha. Would be weird. The method is near, that's all I can say.
 
Cheers,
 
Nathan

---

### Post by ubuntu-freak on 2008-01-30
Made some more changes today. 
 
Nathan

---

### Post by Noampod on 2008-01-30
Hi, me tips hat to you for an excellent how to, I'm a complete linux/ubuntu noob and managed to follow it ok. However one problem I'm having is with video play back,  I get a kind of strobe flickering on the screen and if I right click on the screen the options flash on and off also, any ideas?  

Just to add this is in any of the players.

---

### Post by ubuntu-freak on 2008-01-31
> **Noampod said:**
> Hi, me tips hat to you for an excellent how to, I'm a complete linux/ubuntu noob and managed to follow it ok. However one problem I'm having is with video play back,  I get a kind of strobe flickering on the screen and if I right click on the screen the options flash on and off also, any ideas?  

Just to add this is in any of the players.

 
That's odd. Xv playback should be okay with desktop effects enabled. Go to System>Preferences>Appearance and launch it. Then click on the "Effects" tab, and tick "No Effects". See if video playback still misbehaves. If you use Google Earth, it's best to disable effects as it causes some artifacts. If you disable that hints thing from starting up, you can get away with keeping effects enabled though.
 
When did you install Gutsy? What graphics chip/card do you have? 
 
This command could help improve xv playback if you installed Gutsy last year sometime

**sudo dpkg-reconfigure -phigh xserver-xorg**
 
Nathan

---

### Post by Noampod on 2008-01-31
No effects has done the trick thanks once again :)    I installed Gusty back end of last year, I have an ATI x1950 pro card. I do not use google earth.

---

### Post by evolving_monkey on 2008-01-31
Not that you haven't done enough, but do you have a tutorial on how to get VMWare to work in Ubuntu 7.10 Gutsy.  I have been looking around and that still seems to be a challenge.

Just curious, and again, thank you very much for taking the time.

---

### Post by ubuntu-freak on 2008-01-31
> **evolving_monkey said:**
> Not that you haven't done enough, but do you have a tutorial on how to get VMWare to work in Ubuntu 7.10 Gutsy.  I have been looking around and that still seems to be a challenge.

Just curious, and again, thank you very much for taking the time.

 
Afraid not. Hasn't been something I've needed to master. My only other how-to is an unpopular usplash/boot one. I think my windows partition has a fault, that's why most don't need that how-to. Or because they don't dual boot of course.
 
Nathan

---

### Post by ubuntu-freak on 2008-01-31
> **Noampod said:**
> No effects has done the trick thanks once again :)    I installed Gusty back end of last year, I have an ATI x1950 pro card. I do not use google earth.

 
If you can live without effects that's great. Video should display fine though if you leave the window alone.
 
Nathan

---

### Post by Noampod on 2008-01-31
Not sure what effects I'm missing out on, as desktop environment doesn't seem a lot different to me. In my appearances preferences  visual effects was set to custom, should I try some of the other options and see how that affects video play back?

---

### Post by bw44 on 2008-01-31
> **reassuringlyoffensive said:**
> . . . This command could help improve xv playback if you installed Gutsy last year sometime

**sudo dpkg-reconfigure -phigh xserver-xorg**One question about the above command, doesn't it require that you have at hand a lot of technical info about your video card?  I think I remember trying to use it during a painful alternate install of Feisty and having some problems because I didn't know anything about my video hardware.  Should anyone attempting to use it be warned of anything like that?> **reassuringlyoffensive said:**
> . . . My only other how-to is an unpopular usplash/boot one. I think my windows partition has a fault, that's why most don't need that how-to. Or because they don't dual boot of course.

It may be unpopular, but I wish I had known about it two months ago -- it would have saved me a couple of days of futzing around to figure out what you posted! I eventually got help from someone on the forms who pointed me to the utility startupmanager:  It solved the problem. ([http://ubuntuforums.org/showthread.php?t=663214](http://ubuntuforums.org/showthread.php?t=663214))

Cheers.

---

### Post by ubuntu-freak on 2008-01-31
> **bw44 said:**
> One question about the above command, doesn't it require that you have at hand a lot of technical info about your video card?  I think I remember trying to use it during a painful alternate install of Feisty and having some problems because I didn't know anything about my video hardware.  Should anyone attempting to use it be warned of anything like that?

It may be unpopular, but I wish I had known about it two months ago -- it would have saved me a couple of days of futzing around to figure out what you posted! I eventually got help from someone on the forms who pointed me to the utility startupmanager:  It solved the problem.

Cheers.

 
Hello again. 
 
The reconfigure thing auto detects what you have doesn't it? Did with me. It helped in Debian and gave me the latest intel drivers, which totally improved xv playback.
 
Nathan

---

### Post by ubuntu-freak on 2008-01-31
> **Noampod said:**
> Not sure what effects I'm missing out on, as desktop environment doesn't seem a lot different to me. In my appearances preferences  visual effects was set to custom, should I try some of the other options and see how that affects video play back?

 
It's stuff like the 3d cube, wobbly windows etc. Mostly gimmicky. Try the minimal effects, it will get rid of that ugly black line minimise animation.
 
Nathan

---

### Post by bw44 on 2008-01-31
> **reassuringlyoffensive said:**
> Hello again. 
 
The reconfigure thing auto detects what you have doesn't it? Did with me. It helped in Debian and gave me the latest intel drivers, which totally improved xv playback.
 
NathanHi,

You're right, IF it successfully auto detects, which in my case it didn't.  It seemed able to identify the intel chip but wouldn't auto configure.  Win some, lose some, I guess!

Maybe I should be brave and try it again -- if it worked this time I might be able to run vo=vx. Hmm..

Thnx.

bw44

---

### Post by ubuntu-freak on 2008-01-31
> **bw44 said:**
> Hi,

You're right, IF it successfully auto detects, which in my case it didn't.  It seemed able to identify the intel chip but wouldn't auto configure.  Win some, lose some, I guess!

Maybe I should be brave and try it again -- if it worked this time I might be able to run vo=vx. Hmm..

Thnx.

bw44

 
When did you install Gutsy? Is it running on a laptop?
 
The only issue I had was that it didn't pick up the fact I was using a laptop, didn't put the touchpad settings in xorg-conf, had to do it myself (just a matter of cutting and pasting though). 
 
Nathan

---

### Post by ubuntu-freak on 2008-01-31
Tidied my how-to up today. Also added a link for newbies (at the top) wanting to know how to get the best out of compiz fusion. 
 
Nathan

---

### Post by bw44 on 2008-01-31
> **reassuringlyoffensive said:**
> When did you install Gutsy? Is it running on a laptop?
 
The only issue I had was that it didn't pick up the fact I was using a laptop, didn't put the touchpad settings in xorg-conf, had to do it myself (just a matter of cutting and pasting though). 
 
Nathan

Installed Gutsy on my desktop in November -- that's where I had the problem.  Didn't try in on my new laptop earlier this month, as there was no problem with the screen configuration  there. The live CD installed whatever was needed.   I'll give it a try on my desktop early next week.  Thanks for the suggestion -- I may call for help later!

bw44

---

### Post by ubuntu-freak on 2008-01-31
> **bw44 said:**
> Installed Gutsy on my desktop in November -- that's where I had the problem.  Didn't try in on my new laptop earlier this month, as there was no problem with the screen configuration  there. The live CD installed whatever was needed.   I'll give it a try on my desktop early next week.  Thanks for the suggestion -- I may call for help later!

bw44

 
You could try reinstalling Gutsy and have a seperate home partition. That's what they reccomend now. At some point Ubuntu will do that by default, they are just working out how to impliment it (disk size and dual booters have an impact on it will work).
 
Nathan
 
P.S. 10gb should be fine for the root partition.

---

### Post by Noampod on 2008-01-31
Ok Nathan will do. Should make this guide a sticky, it's been most helpful to me and many others judging by the volume of post.

A 1000 thanks :)

---

### Post by ubuntu-freak on 2008-01-31
> **Noampod said:**
> Ok Nathan will do. Should make this guide a sticky, it's been most helpful to me and many others judging by the volume of post.

A 1000 thanks :)

 
Thanks for your comments. There is already a multimedia "sticky". It's missing a few things though. I don't know how a thread becomes a sticky. Maybe the staff just keep an eye out for threads that most users will find useful.
 
Nathan

---

### Post by baxterdog on 2008-01-31
This thread has been helpful but has a boatload of posts to slog through! Got rm files to work though. Thanks!

2 things;

1) Make sure that the website and all of the other dependent sites are whitelisted if you have the noscript add-on for firefox. I usually just whitelist the main site but found that I had to whitelist ALL of them to get mplayer to stream a .rm file.

2) Tried to get mplayer to open in standalone mode but couldn't find any settings for this, any ideas? (Not completely necessary but it's how I prefer it)

---

### Post by ubuntu-freak on 2008-01-31
> **baxterdog said:**
> This thread has been helpful but has a boatload of posts to slog through! Got rm files to work though. Thanks!

2 things;

1) Make sure that the website and all of the other dependent sites are whitelisted if you have the noscript add-on for firefox. I usually just whitelist the main site but found that I had to whitelist ALL of them to get mplayer to stream a .rm file.

2) Tried to get mplayer to open in standalone mode but couldn't find any settings for this, any ideas? (Not completely necessary but it's how I prefer it)

 
The main player? Why? Defeats the object of the plugins. If you would like to view them without it being embeded, change the value of "noembed" to "1" and delete the pluginreg.dat again.
 
Hope that helps.
 
Nathan

---

### Post by baxterdog on 2008-01-31
Wanted the main player in the hopes that I could get some controls back. But rm files are streaming so there is no reverse or skip ahead, just pause. 

Probably saw that line 'noembed=0' 15 times without equating it to embedding it in the browser! Well, changing it to 1 didn't pop up the main player for an rm file and changing it back to 0 didn't prevent the main player from coming up for a smil file. (changed the mplayerplug-in.conf and deleted pluginreg.dat every time)

Really not bothered by any of this, just figured if I could tweak it then all the better.  I'll be playing with this a bit more when I'm not at work or skiing. Actually, I'll probably only bother with this at work as that's the only place I tend to stream media anyhow.

Cheers!

---

### Post by ubuntu-freak on 2008-01-31
Rm? MPlayer doesn't handle those so that noembed wouldn't effect it. Unless you didn't install RealPlayer and changed rm, smil and helix back to 1 of course.
 
Using the main player doesn't mean you will have seek on all streams either.
 
Nathan

---

### Post by baxterdog on 2008-01-31
Looks like I meant a .ram file actually. Also realplayer is installed and smil/helix = 0.

Yep, correct on the main player and streams.

Gotta go, thanks for all of the info you've put on the forums on this one!

---

### Post by ubuntu-freak on 2008-02-01
> **baxterdog said:**
> Looks like I meant a .ram file actually. Also realplayer is installed and smil/helix = 0.

Yep, correct on the main player and streams.

Gotta go, thanks for all of the info you've put on the forums on this one!

 
No problem.

---

### Post by yerf on 2008-02-02
You're a god!!  My video works perfectly now!!  Thanks so much for the post.

---

### Post by ubuntu-freak on 2008-02-02
> **yerf said:**
> You're a god!!  My video works perfectly now!!  Thanks so much for the post.

 
Lol thanks. 
 
Were you missing the codecs? New to Ubuntu? 
 
Glad it helped anyway.
 
Nathan

---

### Post by dado80 on 2008-02-02
First off, thanks to the OP for the wonderful how-to. 
Now, I'm having issues with my streaming.
I followed the instructions on my HP laptop, and it worked perfectly, wmv and stage6 files were great. Two days ago, it stopped working. It will start buffering the video, try to play it at around 20%, then just keep buffering until it hits 99% and stays there. 
If I hit play, it says "PLaying ..." then it just stops, and says "Stopped."
I haven't changed any settings, checked the mplayer plugin conf file, still the same.
I just set up a fresh install on my brand new desktop, kubuntu 7.10, followed the how-to, same thing.
I can download and play videos perfectly, but streaming doesn't work for either WMV or Stage6 divx.
Any ideas?

---

### Post by ubuntu-freak on 2008-02-02
Has MPlayer been updated lately? I invite others to post how divx.com is working for them. Perhaps divx.com have done something silly. Did you try deleting the pluginreg.dat again? Ah...happened on a new install too. Hopefully others will post.
 
Nathan

---

### Post by 5735guy on 2008-02-03
And it works with Ubuntu 8.04 Hardy Heron (Alpha 3):):):):):)

---

### Post by ubuntu-freak on 2008-02-03
> **5735guy said:**
> And it works with Ubuntu 8.04 Hardy Heron (Alpha 3):):):):):)

 
Divx.com works you mean? Or the how-to in general?
 
Nathan

---

### Post by ubuntu-freak on 2008-02-03
How is divx.com streaming for everyone then?
 
Nathan

---

### Post by ubuntu-freak on 2008-02-04
Added a section to Part 3 which lets you change the region of your DVD drive. Use with caution.
 
Nathan

---

### Post by bw44 on 2008-02-04
> **reassuringlyoffensive said:**
> How is divx.com streaming for everyone then?
 
Nathan

Great (subject to the limitation of my relatively low bandwidth connection)!  

The only thing that still bugs me is that for some reason mplayer seems to randomly disable the "enable-dvx" option. The video stream won't start, and when I right-click and select the "Configure" menu item from the mplayer screen, it shows the "Enable-DivX" box is unchecked.  I have to go through checking the box, clicking OK, quitting Firefox, deleting the pluginreg.dat file (as per your instructions) and restarting Firefox.

If anyone knows why this is happening, I'd appreciate hearing  from them.

Thanks.

bw44

---

### Post by ubuntu-freak on 2008-02-04
> **bw44 said:**
> Great (subject to the limitation of my relatively low bandwidth connection)!  

The only thing that still bugs me is that for some reason mplayer seems to randomly disable the "enable-dvx" option. The video stream won't start, and when I right-click and select the "Configure" menu item from the mplayer screen, it shows the "Enable-DivX" box is unchecked.  I have to go through checking the box, clicking OK, quitting Firefox, deleting the pluginreg.dat file (as per your instructions) and restarting Firefox.

If anyone knows why this is happening, I'd appreciate hearing  from them.

Thanks.

bw44

 
I've never ever had that problem. Strange how people can have their own little issues isn't it? How long has it done that?
 
Nathan

---

### Post by bw44 on 2008-02-04
> **reassuringlyoffensive said:**
> I've never ever had that problem. Strange how people can have their own little issues isn't it? How long has it done that?
 
Nathan

I noticed that mplayer was disabling the divx option ever since I installed Gutsy on my desktop and started trying to get the different media stream formats to work.  This was long before I applied your How-to, so I'm sure it doesn't have anything to do with that! 

I haven't used my laptop enough to notice if it also happens there.  If I learn anything useful I'll post it.

Cheers.

---

### Post by peterx2 on 2008-02-04
I have spent several days on this project and I am very thankful that you have put this up as it does work very well. I had thought that I might simplify the process, but in delving into it, I think it best to leave it exactly as shown...this is very much needed, thanks for posting it..

My only other problem that might show up in some boxes is that the proprietary Nvidia driver for my Geforce4 card crashes in one of the boxes (the other is ok) so if the screen garbles, it might be the video driver that caused it.
pete

---

### Post by ubuntu-freak on 2008-02-04
> **peterx2 said:**
> I have spent several days on this project and I am very thankful that you have put this up as it does work very well. I had thought that I might simplify the process, but in delving into it, I think it best to leave it exactly as shown...this is very much needed, thanks for posting it..

My only other problem that might show up in some boxes is that the proprietary Nvidia driver for my Geforce4 card crashes in one of the boxes (the other is ok) so if the screen garbles, it might be the video driver that caused it.
pete

 
Much of it can be done with add/remove or synaptic, but I decided to make it terminal based. It's a good way to show newbies why we like using the terminal so much, the fact it is fast at installing packages when you know what you want. For setting up a system you can't beat it. Once you're done with that you can browse add/remove or synaptic and see the details of other apps you might find useful.
 
I'm glad it helped you.
 
Nathan

---

### Post by ubuntu-freak on 2008-02-04
Should I just ignore posts I consider [pointless](http://ubuntuforums.org/showthread.php?t=685959)? (Third post down). One of the most friendliest forums and I still get in an arguement! 
 
Nathan

---

### Post by TorqueyPete on 2008-02-04
Ok, finally I have to post my problems up.
 When viewing Youtube, sooner or later it'll hang and the screen goes grey, and it will either crash all browsers, or they will all go when I try to close it and have to 'force quit'.
 I can view the BBC stuff apparently without trouble, play their games too. And Real Player works. With some of the test videos at least.
 I went through the 'How To' thoroughly last night, though I haven't done all the DVD playback stuff, just the bit that stops the CD request when I installed the graphics card drivers from Envy. And I don't have VLC.

Any suggestions would be appreciated.

This system spec:
Latest Gutsy
MSI mainboard MS6712
Athlon XP+ 1500
2.2gb RAM
ATI Radeon 8500LE
Cable BB (up to ;) ) 2meg

I just thought, do I have to manually disable the onboard graphics, like in Windoze?
And if so, how?

---

### Post by ubuntu-freak on 2008-02-04
> **TorqueyPete said:**
> Ok, finally I have to post my problems up.
 When viewing Youtube, sooner or later it'll hang and the screen goes grey, and it will either crash all browsers, or they will all go when I try to close it and have to 'force quit'.
 I can view the BBC stuff apparently without trouble, play their games too. And Real Player works. With some of the test videos at least.
 I went through the 'How To' thoroughly last night, though I haven't done all the DVD playback stuff, just the bit that stops the CD request when I installed the graphics card drivers from Envy. And I don't have VLC.

Any suggestions would be appreciated.

This system spec:
Latest Gutsy
MSI mainboard MS6712
Athlon XP+ 1500
2.2gb RAM
ATI Radeon 8500LE
Cable BB (up to ;) ) 2meg

I just thought, do I have to manually disable the onboard graphics, like in Windoze?
And if so, how?

 
If your ATI card was detected okay you should be fine. If you have the option to disable it in bios then you can I guess.
 
Some appear to be having flash problems (mostly AMD systems, strangely). Did you install the one from my how-to? You don't have Gnash installed do you? Also, try viewing YouTube with desktop effects turned off (System>Preferences>Appearance>Effects).
 
Nathan

---

### Post by TorqueyPete on 2008-02-05
Yes, Gutsy detected it on the first install. I'll check the bios in a minute.
 Yeap, flash is from your Howto, and I've just turned off screen effects. Checking. ;)

---

### Post by TorqueyPete on 2008-02-05
I'm really surprised at the difference made by turning off all screen effects! Youtube seems better now, though still occasionally ju ju jumping a little. And full screen still isn't up to much, but viewable jerkyness is better than the scrolling steps that I had while screen effects were on.

I can see Gnash on the Synaptic list, but it's Not installed.

---

### Post by ubuntu-freak on 2008-02-05
> **TorqueyPete said:**
> I'm really surprised at the difference made by turning off all screen effects! Youtube seems better now, though still occasionally ju ju jumping a little. And full screen still isn't up to much, but viewable jerkyness is better than the scrolling steps that I had while screen effects were on.

I can see Gnash on the Synaptic list, but it's Not installed.

 
I'm not surprised. :-)
 
Hopefully your video drivers will improve soon. You will notice a difference by the time Hardy comes along anyway. Strange how it's only flash vids that play up with some people. 
 
Were there no open source drivers for your card? Just propriatry?
 
Nathan

---

### Post by ZED RINO on 2008-02-05
I don't understand why it's so hard to browse multimedia files with Linux-Firefox. It should be ease ease. And what happen if my grand-mother or my little son want to try something else than windows ? I will tell them: just stay on html web pages ! No streaming no video !! I think it should be the first thing to do to the Linux developpement: an easy and full web access.
Thank you

---

### Post by ubuntu-freak on 2008-02-05
> **ZED RINO said:**
> I don't understand why it's so hard to browse multimedia files with Linux-Firefox. It should be ease ease. And what happen if my grand-mother or my little son want to try something else than windows ? I will tell them: just stay on html web pages ! No streaming no video !! I think it should be the first thing to do to the Linux developpement: an easy and full web access.
Thank you

 
They don't cos Ubuntu is free and Canonical would get sued if they shipped Ubuntu with codecs etc. I'd rather it stay free and we do it ourselves. They have made it easier anyway, you can do it in add/remove apparently. At least with this thread you know exactly what you need though.
 
Linux Mint contains all the codecs, but only cos they aren't backed by a wealthy company. Mint is totally illegal to download in the U.S. but not the U.K.
 
I think Ubuntu is better, so don't switch just to get codecs preinstalled. Try to remember that Canonical are wealthy and don't wish to throw it all away. 
 
I'm glad my how-to helped you.
 
Nathan 
 
Edit: Also, read [this](http://www.ubuntu.com/community/ubuntustory/philosophy). All software on a fresh install is truly "free" for philisophical reasons.

---

### Post by siretfel on 2008-02-05
THANK YOU !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!


note: doesn't mplayer when streaming have the option to rewind???? What if i miss a minute or two by accident or want to watch a scene again? Can't i go back?

---

### Post by ubuntu-freak on 2008-02-05
> **siretfel said:**
> THANK YOU !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!


note: doesn't mplayer when streaming have the option to rewind???? What if i miss a minute or two by accident or want to watch a scene again? Can't i go back?

 
Thanks. You seem pleased :-).
 
Sometimes seek will work, and other times not. Try dragging the progress bar with your mouse cursor, that's how I go back/forward. 
 
Nathan

---

### Post by JoshuaRL on 2008-02-05
I just wanted to say thank you in advance and commend you for not only posting this, but also sticking around to help troubleshoot any problems.  Bravo.

---

### Post by ubuntu-freak on 2008-02-05
> **JoshuaRL said:**
> I just wanted to say thank you in advance and commend you for not only posting this, but also sticking around to help troubleshoot any problems.  Bravo.

 
Thanks. No problem.

I've added bits to the how-to cos of issues some people had, so it benifits me and the how-to sticking around to help.
 
Nathan

---

### Post by ubuntu-freak on 2008-02-06
How has totem-xine been working for everyone? How does it compare to gstreamer for you? I've found xine is best for vids and gstreamer is best or fine for audio. Amarok uses xine for audio apparently though.
 
Nathan

---

### Post by bw44 on 2008-02-07
Pretty quiet on this thread!

This isn't exactly a problem but it relates to a comment Nathan has made repeatedly, to the effect, use vo=xv if you have the chocie.:

What exactly to the x11, gl and xv "settings" refer to (yeah, OK, "video output" but ...)?  They're mentioned in lots of threads but I haven't been able to find a simple description of what they mean.  Worse, people often suggest "Try this one, and if it doesn't work, try that one."  

My video requirements aren't very ambitious, and I use the vo=xv setting in mplayer on my laptop and vo=x11 on my older desktop.  I can't figure out which is used with VLC.  But there is no difference I can see between what gets displayed on each machine, and for what I view, they're OK.

Nathan mentioned updating my driver on the desktop, and I've found out that there may be an upgraded driver for the Intel Brookdale-G 845 chip that currently uses the i810 driver.

But I remember someone saying once "If it ain't broke, don't fix it" and I'm a little overwhelmed by the technical advice I've found about upgrading drivers.

Comments anyone?

---

### Post by ubuntu-freak on 2008-02-07
> **bw44 said:**
> Pretty quiet on this thread!

This isn't exactly a problem but it relates to a comment Nathan has made repeatedly, to the effect, use vo=xv if you have the chocie.:

What exactly to the x11, gl and xv "settings" refer to (yeah, OK, "video output" but ...)?  They're mentioned in lots of threads but I haven't been able to find a simple description of what they mean.  Worse, people often suggest "Try this one, and if it doesn't work, try that one."  

My video requirements aren't very ambitious, and I use the vo=xv setting in mplayer on my laptop and vo=x11 on my older desktop.  I can't figure out which is used with VLC.  But there is no difference I can see between what gets displayed on each machine, and for what I view, they're OK.

Nathan mentioned updating my driver on the desktop, and I've found out that there may be an upgraded driver for the Intel Brookdale-G 845 chip that currently uses the i810 driver.

But I remember someone saying once "If it ain't broke, don't fix it" and I'm a little overwhelmed by the technical advice I've found about upgrading drivers.

Comments anyone?

 
The x11 driver is unaccelerated and should be avoided, poorest performance. The gl one is accelerated and okay, but the xv driver is superior and should be used cos desktop effects use OpenGL. Not very pretty having Compiz and videos both using OpenGL.
 
All players use xv by default, including VLC. 
 
The current intel driver is simply "intel", as apposed to "i810", so dpkg-reconfigure -phigh xserver-xorg should benifit you. If xv works with effects enabled though, then I would have thought you're already using "intel". I had to switch to that in Debian to get xv working with compiz. 
 
Nathan

---

### Post by ubuntu-freak on 2008-02-07
Oh and, if it aint broke, you haven't tinkered enough:-)

---

### Post by bw44 on 2008-02-08
> **reassuringlyoffensive said:**
> The x11 driver is unaccelerated and should be avoided, poorest performance. The gl one is accelerated and okay, but the xv driver is superior and should be used cos desktop effects use OpenGL. Not very pretty having Compiz and videos both using OpenGL.
 
All players use xv by default, including VLC. 
 
The current intel driver is simply "intel", as apposed to "i810", so dpkg-reconfigure -phigh xserver-xorg should benifit you. If xv works with effects enabled though, then I would have thought you're already using "intel". I had to switch to that in Debian to get xv working with compiz. 
 
Nathan

Ah, that helps!  So x11, gl and xv are "drivers" but not "device drivers." Do they sort of sit between xorg and the device (driver), or between the application and the device driver through xorg?  Inquiring minds want to know!  I remember there was recently a big update to the xorg server(because they had to fix the update and it took a couple of days), but I never knew  to run  dpkg-reconfigure -phigh xserver-xorg after that. Should I have? 

Anyway, I just ran $ sudo dpkg-reconfigure -phigh xserver-org with the following results:

In the Section "Device" it replaced the the i810 with the "intel" driver, as you said it would (not that I didn't trust you!)

It deleted the following lines (which worries me a bit since I don't really know what they're for):```
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection
```Should I paste them back in to the new xorg.conf in case some application I run needs them?

It also deleted all the subsections in the Section "Screen" after the first one in the list below (from the old xorg.conf) ```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"DELL 1504FP"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```
It also commented out some stuff that had been previously uncommented:

Old xorg.conf:```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```New xorg.conf:```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

Should I reinstate these lines, or wait for something to break?  But since I don't really know what any of this stuff means.  Something must have uncommented the "wacom tablet" lines, but who and why?  And what's the DRI section about?

> **reassuringlyoffensive said:**
> Oh and, if it aint broke, you haven't tinkered enough:-)

If something breaks now, how will I know it was because I tinkered with xorg.conf?   :)

I guess one of the reasons I haven't encountered more problems with the video output drivers is that I don't really like the special desktop effects and turned them off.  I don't remember if I even have compiz installed.

Thanks very much for the help and any answers you can provide!

bw44

PS.  I just googled "wacom tablet" and unless I did some minor editing in Gimp, I can't imagine who would have required it.

PPS. [https://help.ubuntu.com/community/RemoveWacomTabletError](https://help.ubuntu.com/community/RemoveWacomTabletError) clears up that confusion.

---

### Post by TorqueyPete on 2008-02-08
> **reassuringlyoffensive said:**
> I'm not surprised. :-)
 
Hopefully your video drivers will improve soon.
 
Were there no open source drivers for your card? Just propriatry?
 
Nathan

Ah, well downloaded the proprietary driver for it, from the ATI but can't open it. All it does is tell me, 'Could not open "ati-driver-installer-8.28.8.run" Archive type not supported.'
 I'll try it without the installer.
Archive mgr couldn't open the rpm file.
 Did I mention that I'm a beginner? ;)

---

### Post by ubuntu-freak on 2008-02-08
bw44

Xv (Xvideo) sits between the player and the xserver + GPU. Your graphics device does most of the work. X11 sits between the player and the xserver + CPU. Your processor does all the work and your graphics card does nothing except display it. 

It's fine that you have lots missing in xorg.conf, just means that those features or modules are completely default now. Only problem I had in Debian when I reconfigured was that I had to put the touchpad settings and module back. Kinda bad really. Newbies would hate that. 
 
Nathan

---

### Post by ubuntu-freak on 2008-02-08
> **TorqueyPete said:**
> Ah, well downloaded the proprietary driver for it, from the ATI but can't open it. All it does is tell me, 'Could not open "ati-driver-installer-8.28.8.run" Archive type not supported.'
 I'll try it without the installer.
Archive mgr couldn't open the rpm file.
 Did I mention that I'm a beginner? ;)

 
Rpm is for Redhat and Fedora. Ubuntu uses deb packages. Didn't Ubuntu offer to install them with the restricted drivers manager? Or you could try envy, heard good things about that.
 
Nathan 
 
Edit: Try this [sticky thread](http://ubuntuforums.org/showthread.php?t=515573). Hope that helps.

---

### Post by peterthewolf on 2008-02-08
Question about saving BBC streams to disk.
I have set keep-download to 1
I can listen to BBC stream fine
How can I capture the sound to a disk file.

---

### Post by ubuntu-freak on 2008-02-08
> **peterthewolf said:**
> Question about saving BBC streams to disk.
I have set keep-download to 1
I can listen to BBC stream fine
How can I capture the sound to a disk file.

 
It worked with video for me. Make sure you're listening to wma instead of ra. It will take a bit longer to start playing but should work. Test a wmv or apple.com video stream too.
 
Nathan

---

### Post by peterthewolf on 2008-02-08
How do I choose wma

---

### Post by bw44 on 2008-02-08
> **reassuringlyoffensive said:**
> bw44

Xv (Xvideo) sits between the player and the xserver + GPU. Your graphics device does most of the work. X11 sits between the player and the xserver + CPU. Your processor does all the work and your graphics card does nothing except display it. 

It's fine that you have lots missing in xorg.conf, just means that those features or modules are completely default now. Only problem I had in Debian when I reconfigured was that I had to put the touchpad settings and module back. Kinda bad really. Newbies would hate that. 
 
Nathan

Thanks so much for the encouragement!  As a relative newbie, I'm always a little worried about tinkering with something I don't understand at all.  But maybe that's the only way to really learn!

On another topic, the embedded RealPlayer problem (especially at the BBC news site):  two days ago I sent BBC a detailed description with screen shots of what happens when I access their videos.  Yesterday two things happened:  The new version of Firefox was distributed (2.0.0.12) and  for one new BBC link,  RealPlayer launches in embedded mode [http://www.bbc.co.uk/mediaselector/check/player/nol/newsid_7230000/newsid_7233900?redirect=7233935.stm&news=1&bbwm=1&nbram=1&nbwm=1&bbram=1&asb=1](http://www.bbc.co.uk/mediaselector/check/player/nol/newsid_7230000/newsid_7233900?redirect=7233935.stm&news=1&bbwm=1&nbram=1&nbwm=1&bbram=1&asb=1)

Of course my email probably had nothing to do with the link working, but I like to think it did!

I also upgraded the xorg.config file yesterday, but I don't think that corrected the RealPlayer problem.  And since I haven't installed the new Firefox on my laptop yet and the link runs embedded with the older version of Firefox, I conclude BBC has finally figured something out (or is at least doing something different for that link).  I fired off another email congratulating them.  I hope it filters down to the programming staff, in case it was an unintentional  fix.

Anyone who's been frustrated by the RealPlayer problem should try the above link.  It's only one of many and the others I've tried still won't launch embedded, but it's a start.  At least it tells me that there is something that can be done about it at their end.

bw44

---

### Post by peterthewolf on 2008-02-08
Sorry for that DUMB question I could not see the option staring me in the face.
WMA works fine
Where is the saved audio stream put?

---

### Post by ubuntu-freak on 2008-02-08
> **peterthewolf said:**
> Sorry for that DUMB question I could not see the option staring me in the face.
WMA works fine
Where is the saved audio stream put?

 
It should be in your home folder with some wierd name.
 
Nathan

---

### Post by ubuntu-freak on 2008-02-08
> **bw44 said:**
> Thanks so much for the encouragement!  As a relative newbie, I'm always a little worried about tinkering with something I don't understand at all.  But maybe that's the only way to really learn!

On another topic, the embedded RealPlayer problem (especially at the BBC news site):  two days ago I sent BBC a detailed description with screen shots of what happens when I access their videos.  Yesterday two things happened:  The new version of Firefox was distributed (2.0.0.12) and  for one new BBC link,  RealPlayer launches in embedded mode [http://www.bbc.co.uk/mediaselector/check/player/nol/newsid_7230000/newsid_7233900?redirect=7233935.stm&news=1&bbwm=1&nbram=1&nbwm=1&bbram=1&asb=1](http://www.bbc.co.uk/mediaselector/check/player/nol/newsid_7230000/newsid_7233900?redirect=7233935.stm&news=1&bbwm=1&nbram=1&nbwm=1&bbram=1&asb=1)

Of course my email probably had nothing to do with the link working, but I like to think it did!

I also upgraded the xorg.config file yesterday, but I don't think that corrected the RealPlayer problem.  And since I haven't installed the new Firefox on my laptop yet and the link runs embedded with the older version of Firefox, I conclude BBC has finally figured something out (or is at least doing something different for that link).  I fired off another email congratulating them.  I hope it filters down to the programming staff, in case it was an unintentional  fix.

Anyone who's been frustrated by the RealPlayer problem should try the above link.  It's only one of many and the others I've tried still won't launch embedded, but it's a start.  At least it tells me that there is something that can be done about it at their end.

bw44

 
Impressive! They rely on feedback so it could have been your email. I'd wager they support IE much better, so it might be that they changed something to better support Firefox. I doubt it's the RP plugin. 
 
Nathan

---

### Post by ubuntu-freak on 2008-02-08
Made some changes to the how-to today.
 
Added a gstreamer package and java6 fonts to the essential list. The gstreamer package should improve video playback/support. Java6 fonts should be in the extras package, but isn't.
 
Also moved libdvdcss2 to part 3 (not everybody watches DVDs in Ubuntu), moved ffmpeg and faac to part 4 (not everybody converts vids). Makes sense huh?
 
Added DVD ripping/burning apps to part 3 and changed the instructions slightly.
 
Flash has been fixed also, so edited that section.
 
Nathan

---

### Post by oDDWare on 2008-02-09
Wow... I've been a forum member for an hour, and you already touched on 4 of my issues in one post... Thanks!

---

### Post by ubuntu-freak on 2008-02-09
> **oDDWare said:**
> Wow... I've been a forum member for an hour, and you already touched on 4 of my issues in one post... Thanks!

 
Glad to help. How many more issues do you have? I find google is a better way to search these forums. If you get old results, search "gutsy" instead of just "ubuntu" or "site:ubuntuforums.org". Works for me.
 
Nathan

---

### Post by ubuntu-freak on 2008-02-09
> **reassuringlyoffensive said:**
> Rpm is for Redhat and Fedora. Ubuntu uses deb packages. Didn't Ubuntu offer to install them with the restricted drivers manager? Or you could try envy, heard good things about that.
 
Nathan 
 
Edit: Try this [sticky thread](http://ubuntuforums.org/showthread.php?t=515573). Hope that helps.

 
TorqueyPete,
 
Did you try the link above?

---

### Post by rdowell2002 on 2008-02-09
Hi 
I'm not an experienced linux user but decided to do your streaming media how to. When I do the second command (to install the different flash plugin) I get an error message that the file or directory can't be found. What do I need to do? I'm using ubuntu Gutsy.

Thanks for any help.

Bob

---

### Post by ubuntu-freak on 2008-02-09
> **rdowell2002 said:**
> Hi 
I'm not an experienced linux user but decided to do your streaming media how to. When I do the second command (to install the different flash plugin) I get an error message that the file or directory can't be found. What do I need to do? I'm using ubuntu Gutsy.

Thanks for any help.

Bob

 
The flash plugin has been fixed, it's installed with the restricted-extras package along with java, gstreamer codecs, unrar etc.
 
Nathan

---

### Post by ubuntu-freak on 2008-02-09
Damn it! I made a mistake with sun-java-6-fonts. It's supposed to be **sun-java6-fonts**. Can't change it right now cos I'm not near a comp, just using a phone to write this and my how-to is too big to edit on my phone.
 
Nathan

---

### Post by Kilz on 2008-02-09
> **reassuringlyoffensive said:**
> **REVISED ON 8 FEB 2008**


**If you're running a 64-bit system**, my how-to won't solve all of your problems unless you follow another how-to also. There is no java plugin for Firefox as Sun Java don't make one for 64-bit systems. There is no Adobe flash plugin for your 64-bit system either.
 


Nathan

Nathan
Please edit this section. There is indeed a java plugin (icedtea) and [Flash works just fine]("http://ubuntuforums.org/showthread.php?t=476924") in 64bit.

The 32bit option is still ok in case the icedtea plugin has problems.

---

### Post by ubuntu-freak on 2008-02-10
> **Kilz said:**
> Nathan
Please edit this section. There is indeed a java plugin (icedtea) and [Flash works just fine]("http://ubuntuforums.org/showthread.php?t=476924") in 64bit.

The 32bit option is still ok in case the icedtea plugin has problems.

 
Thanks for the heads up. When installing flashplugin-nonfree in 64-bit, the wrapper is now automatically installed yes?
 
Might not be able to make changes til monday.

Thanks,
 
Nathan

---

### Post by NoVista on 2008-02-10
I could use a little help here.
I run FF 2.0.0.12

Multimedia wise, I always have everything working fine.
But about two to four days ago, something broke.
(I've noticed we've had both flash and FF updates).
My flash works fine, and I am now wondering if the problem is related to FF.
This error only appears, AFAIK, at this site, Yahoo News Videos:
[http://news.yahoo.com/video/2776](http://news.yahoo.com/video/2776)
The problem is in the player.

The player comes up, the flash advertisment plays, but now there is nothing showing under where the video plays. Under it is all the other selections, to choose what news video you want  to play on Yahoo.

Anyone else see this break or have a solution to get me right?

---

### Post by TorqueyPete on 2008-02-10
Doh!
 I'm just trying to watch a BBC video with Real Player but Firefox says "Could not find an appropriate hx or realplay in the system to use as an embedded player! :(

Clicked the error applet away 7 times to get rid of it. Then on the BBC News Player page clicking the 'Stand alone got me a file to save. So I can view it with RP 10 but only by right click and 'open with other', as VLC is  default. But even with RP  the vid quality is very poor .

---

### Post by ubuntu-freak on 2008-02-10
> **NoVista said:**
> I could use a little help here.
I run FF 2.0.0.12

Multimedia wise, I always have everything working fine.
But about two to four days ago, something broke.
(I've noticed we've had both flash and FF updates).
My flash works fine, and I am now wondering if the problem is related to FF.
This error only appears, AFAIK, at this site, Yahoo News Videos:
[http://news.yahoo.com/video/2776](http://news.yahoo.com/video/2776)
The problem is in the player.

The player comes up, the flash advertisment plays, but now there is nothing showing under where the video plays. Under it is all the other selections, to choose what news video you want  to play on Yahoo.

Anyone else see this break or have a solution to get me right?

 
The  latest flash is buggy. Try and get hold of the rc48 version, there are threads about it. Make sure you completely remove the current flash you have before installing rc48.
 
Nathan

---

### Post by ubuntu-freak on 2008-02-10
> **NoVista said:**
> I could use a little help here.
I run FF 2.0.0.12

Multimedia wise, I always have everything working fine.
But about two to four days ago, something broke.
(I've noticed we've had both flash and FF updates).
My flash works fine, and I am now wondering if the problem is related to FF.
This error only appears, AFAIK, at this site, Yahoo News Videos:
[http://news.yahoo.com/video/2776](http://news.yahoo.com/video/2776)
The problem is in the player.

The player comes up, the flash advertisment plays, but now there is nothing showing under where the video plays. Under it is all the other selections, to choose what news video you want  to play on Yahoo.

Anyone else see this break or have a solution to get me right?

> **TorqueyPete said:**
> Doh!
 I'm just trying to watch a BBC video with Real Player but Firefox says "Could not find an appropriate hx or realplay in the system to use as an embedded player! :(

Clicked the error applet away 7 times to get rid of it. Then on the BBC News Player page clicking the 'Stand alone got me a file to save. So I can view it with RP 10 but only by right click and 'open with other', as VLC is  default. But even with RP  the vid quality is very poor .

 
Check /usr/lib/firefox/plugins and make sure the nphelix plugins are there. Try that rm $HOME command for the pluginreg.dat also. If playback is choppy in realplayer, try the fix in the important info section of my how-to.
 
Hope that helps.
 
Nathan

---

### Post by ubuntu-freak on 2008-02-10
I'm gonna make some changes to the essential packages section tomorrow which will improve things. Will mainly help Kubuntu, Xubuntu and 64-bit users, but 32-bit Ubuntu users as well.
 
Nathan

---

### Post by NoVista on 2008-02-10
Hmm. I am running the rc48 version, and thought I had a total uninstall, even searching out any remnants.
I've also  been acutely aware on what has just been happening with the flash update and various "fixes", and or install methods.
I'll try a complete un-install again.

I need the Yahoo Video player to work again.
[http://news.yahoo.com/video/2776](http://news.yahoo.com/video/2776)

---

### Post by ubuntu-freak on 2008-02-10
> **NoVista said:**
> Hmm. I am running the rc48 version, and thought I had a total uninstall, even searching out any remnants.
I've also  been acutely aware on what has just been happening with the flash update and various "fixes", and or install methods.
I'll try a complete un-install again.

I need the Yahoo Video player to work again.
[http://news.yahoo.com/video/2776](http://news.yahoo.com/video/2776)

 
Where did you get the rc48 one from? Did you completely remove in synaptic or with sudo apt-get purge?
 
Nathan

---

### Post by brucewagner on 2008-02-10
Now that Ubuntu is being automatically updated with some of the fixes for these media issues...

I'm confused.

On new installs of Ubuntu, am I better off following the install instructions from this thread, "A New Back-Up Solution if You Want It" --- the QuickStart instructions for installing video stuff ( [http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462) )

Or this thread, " Complete Streaming, Multimedia & Video How-to" ( [http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833) ).

I am a newbie myself, but I see that brand new installs of Ubuntu are getting automatic updates now which DO successfully play YouTube videos, for example.  But I don't know about all the other media issues (commercial DVD playback, MP3 , video codecs, streaming video, etc.)...

On new installs for friends, Should I...

(a)   Just let Ubuntu's automatic install update their systems
(b)   Follow the "A New Back-Up Solution if You Want It" how to instructions    ~or~
(c)   Follow the " Complete Streaming, Multimedia & Video How-to" instructions   ?

---

### Post by ubuntu-freak on 2008-02-11
Adobe Flash is proprietary and isn't installed by default, niether is java, codecs for wmv's or mp3's. Only free software is installed by default so it's good to bookmark this how-to. 
 
I'm making some changes monday just so you know. Mostly to part 1 and part 3.
 
Nathan

---

### Post by brucewagner on 2008-02-11
Ok.  Thanks.

I just wish it wasn't such a massive long list of terminal commands.   It's quite intimidating.   Especially for new users...

I wish it were automated.... into a GUI.... like QuickStart is...   (see [http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462) )

(hint, hint ;) )

---

### Post by bw44 on 2008-02-11
> **TorqueyPete said:**
> Doh!
 I'm just trying to watch a BBC video with Real Player but Firefox says "Could not find an appropriate hx or realplay in the system to use as an embedded player! :(

Clicked the error applet away 7 times to get rid of it. Then on the BBC News Player page clicking the 'Stand alone got me a file to save. So I can view it with RP 10 but only by right click and 'open with other', as VLC is  default. But even with RP  the vid quality is very poor .

Just to let you know:  I have managed to get RealPlayer (10.0.9) working quite well by following Nathan's How-To.  BUT, the message you describe is caused by something wrong at the BBC site, and I still get it, (but only sometimes). After getting rid of it (when it shows up) I am able to click on "Launch in Stand Alone Player" and a RealPlayer window opens which plays the video fine.

I don't get the message about saving a file, and although VLC is my default DVD player (again as per Nathan's recommendation),  it isn't used at all by Firefox.  When you say it's the default what do you mean?

bw44

---

### Post by ubuntu-freak on 2008-02-11
> **brucewagner said:**
> Ok.  Thanks.

I just wish it wasn't such a massive long list of terminal commands.   It's quite intimidating.   Especially for new users...

I wish it were automated.... into a GUI.... like QuickStart is...   (see [http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462) )

(hint, hint ;) )

 
I believe you can do it in add/remove, but I think that takes longer tn be honest. Part 1 of my how-to enables multimeda with just one command. The streaming section is optional. I kept the DVD section seperate as some user don't watch DVDs in Ubuntu, same with the video converting section.
  
Nathan

---

### Post by ubuntu-freak on 2008-02-11
Just spent a couple of hours revamping my how-to. Check out dvd::rip and Tovid in part 3.
 
Nathan

---

### Post by bw44 on 2008-02-11
> **reassuringlyoffensive said:**
> Just spent a couple of hours revamping my how-to. Check out dvd::rip and Tovid in part 3.
 
Nathan

You might want to update the revision date in the first line of the How To:  it still says 8 Feb 2008.

---

### Post by ubuntu-freak on 2008-02-11
> **bw44 said:**
> You might want to update the revision date in the first line of the How To:  it still says 8 Feb 2008.

 
Lol yeah I noticed that AFTER it was too late. I can't do it til tomorrow now, don't have a laptop anymore (had to use someone elses). I wonder how many other people give support using a walkman phone....:-)
 
I have some other corrections/edits to make tomorrow also. 
 
Nathan

---

### Post by TorqueyPete on 2008-02-11
> **bw44 said:**
> 
I don't get the message about saving a file, and although VLC is my default DVD player (again as per Nathan's recommendation),  it isn't used at all by Firefox.  When you say it's the default what do you mean?

bw44


When I right click most video files VLC is at the top of the drop down list. But I'm not too clever with all this malarkey, so it'll all go pear shaped soon enough. ;)

---

### Post by ubuntu-freak on 2008-02-11
> **TorqueyPete said:**
> When I right click most video files VLC is at the top of the drop down list. But I'm not too clever with all this malarkey, so it'll all go pear shaped soon enough. ;)

 
You can change how FF deals with certain files in it's preferences. Have a look at the important info section of my how-to.
 
Nathan

---

### Post by brucewagner on 2008-02-11
> **TorqueyPete said:**
> When I right click most video files VLC is at the top of the drop down list. But I'm not too clever with all this malarkey, so it'll all go pear shaped soon enough. ;)

To set which program opens a certain file type:

Right-click the file, select PROPERTIES, the click the OPEN WITH tab.  There you can select which program opens that type of file (by default) from now on.

Far easier than in Windows.... eh?     :)

---

### Post by brucewagner on 2008-02-11
Apparently, the Ubuntu folks are busy at work improving the way things work...

Just thought you'd like to know:

On two brand new Ubuntu Gutsy installs today, this was my experience...

Without installing ANYTHING other than the automatic updates...

I tried to open an MP3 file,
		mp3 – I was prompted to install “Gstreamer extra plugins” (mp3, etc.)
                and the files now play fine.

Upon visiting a YouTube video page, 
	        youtube flash video – I was prompted to install Adobe Flash
                and all the videos play fine now.

I opened an AVI file, 
		divx avi – I was prompted to install “Gstreamer ffmpeg video plugin” 
                   (for divx. mwv)
                now divx avi files play fine.
		wmv – also plays in Totem without installing anything else at all.

I visited a web site that uses Java extensively,
                java -- I was prompted to install “The Java(TM) Plug-in, Java SE 6”
                now the java functions fine.

So all of these things installed automatically (or semi-automatically) with Ubuntu now.

Am I missing anything?

---

### Post by ubuntu-freak on 2008-02-12
That's been a feature for quite a while now. I'm glad it worked flawlessly for you, it's a great feature.
 
Doing it that way won't install everything you might need though. That's why I wrote this how-to. Not to mention my MPlayer plugin advice, DVD playback/ripping/burning solutions and video converting advice.  
 
Nathan

---

### Post by ubuntu-freak on 2008-02-12
Also depends on what your friends want to do with Ubuntu. I think part 1 is quicker than clicking on files and links though, isn't it? It's just one install command.
 
Nathan

---

### Post by ubuntu-freak on 2008-02-12
Made another update to how-to. Forgot to put libdvdnav4 in the dvd section. Made some corrections and added some more tips to the troubleshooting bit (java). Also, tried to make it look a bit better.
 
Nathan

---

### Post by NoVista on 2008-02-12
I now realize, as I suspcted before, that the problem I have posted earlier, about the Yahoo News Player not showing all the selections under the movie window, is not a Flash problem. It's FF.
I run a couple different Gutsy installs here. It doesn't matter here what version of Flash I run, it always works, the flash part. 
But, after I let it automatically update FF three days ago, it breaks the Yahoo News player. Flash, any version, works everywhere, as it always has here. But not now on Yahoo. And it's due to that FF update.

---

### Post by ubuntu-freak on 2008-02-12
Have you reported it as a bug? They will probably release an update for the update soon, it's happened before.
 
Nathan

---

### Post by NoVista on 2008-02-12
No, I haven't reported it. I'll wait a bit myself.

---

### Post by bw44 on 2008-02-12
> **NoVista said:**
> I could use a little help here.
I run FF 2.0.0.12

Multimedia wise, I always have everything working fine.
But about two to four days ago, something broke.
(I've noticed we've had both flash and FF updates).
My flash works fine, and I am now wondering if the problem is related to FF.
This error only appears, AFAIK, at this site, Yahoo News Videos:
[http://news.yahoo.com/video/2776](http://news.yahoo.com/video/2776)
The problem is in the player.

The player comes up, the flash advertisment plays, but now there is nothing showing under where the video plays. Under it is all the other selections, to choose what news video you want  to play on Yahoo.

Anyone else see this break or have a solution to get me right?

I'm running FF 2.0.0.12 and the above Yahoo site works for me.  I don't see the "flash advertisement" you mention though.  Is it on the first page?  What I see is the Heading "Weather & Science Video" and below that a long list of video clips with thumbnails.  If I click on one of those it opens a window with flash player (or mplayer for some clips) and plays the video.

I'm running the FF add-on Adblock Plus, but to test whether it might be blocking the problem, I turned it off for the Yahoo site.  But the only change I could see was a still advertisement for Yahoo that appeared to the right of the first thumbnail at the top of the page.

It's a long shot, but you might try installing Adblock Plus just in case it blocks something that otherwise causes a problem in Firefox.  It wouldn't be a fix, but maybe it would enable you to access the videos.  (And unless you prefer to see ads Adblock Plus is a great tool.)

---

### Post by NoVista on 2008-02-12
Dang it.

The flash advertisement just starts playing in the video window once you select any link to play. The problem here is that, the advertisement plays, but then it never re-directs to actually play the news clip you selected. Also, there is nothing under the video. That is where all the other selections are, to choose whatever you want to play.

Now I'm more stumped than before. here's my next plan of action.
On another machine I have running Gutsy, I have not updated FF yet, and everything is OK. So, I'll go make an image of that drive, then go install the FF update, and see what happens.

Appreciate the info.

---

### Post by bw44 on 2008-02-12
> **NoVista said:**
> Dang it.

The flash advertisement just starts playing in the video window once you select any link to play. The problem here is that, the advertisement plays, but then it never re-directs to actually play the news clip you selected. Also, there is nothing under the video. That is where all the other selections are, to choose whatever you want to play.

Now I'm more stumped than before. here's my next plan of action.
On another machine I have running Gutsy, I have not updated FF yet, and everything is OK. So, I'll go make an image of that drive, then go install the FF update, and see what happens.

Appreciate the info.

OK, now I see what you mean.  Does it make any difference if you select a link to a Flash video or to a non-Flash one?  For example, the first link below causes the Flash plugin to launch in the Yahoo News player:

 [http://news.yahoo.com/video/2776](http://news.yahoo.com/video/2776) "Atlantis blasts off on mission to space station"

But the following one causes the mplayer plugin to launch in the Yahoo News player (on my system anyway):

[http://news.yahoo.com/video/2776](http://news.yahoo.com/video/2776) "Cellphones sprout joysticks"

Anyone else want to try these and let us know what works and what doesn't with the latest Firefox (2.0.0.12) or an earlier one?

I noticed that when the link is to  a non-Flash video that I sometimes have to click on "Video Quality" and select something faster than 56K, which seems to be the default.  Unless I do that, it looks like the video has stopped downloading. 

It's also the case that sometimes the ads play first and sometimes they don't.  Getting their ad video clips into the stream before the news videos has been a huge problem for the BBC site.

I think your plan to try a clean install of the new FF is a good one.  Good luck, and keep us posted on the results!

---

### Post by TorqueyPete on 2008-02-12
I just want to thank you Nathan, for your continuing efforts here. It is appreciated.
 Have a doughnut or three.

These are covered in soft brown sugar.  :grin:

[IMG]http://i81.photobucket.com/albums/j226/chashugh/doughnuts.jpg[/IMG]

---

### Post by NoVista on 2008-02-13
Updates today fixed the problem :)

---

### Post by ubuntu-freak on 2008-02-13
> **NoVista said:**
> Updates today fixed the problem :)

 
That's good. Updates for updates:-)

---

### Post by ubuntu-freak on 2008-02-13
> **TorqueyPete said:**
> I just want to thank you Nathan, for your continuing efforts here. It is appreciated.
 Have a doughnut or three.

These are covered in soft brown sugar.  :grin:

[IMG]http://i81.photobucket.com/albums/j226/chashugh/doughnuts.jpg[/IMG]

 
Thanks! Helps make the how-to better anyway. Don't want it becoming outdated or be incomplete.
 
Nathan

---

### Post by ubuntu-freak on 2008-02-13
If anyone is having issues with Adobe Flash (works, but badly) see paragraph 7 in the troubleshooting section.
 
DVDs play fine but not some new ones? Have a look at paragraph 9.

Nathan

---

### Post by ubuntu-freak on 2008-02-13
Duplicate.

---

### Post by Pandemic187 on 2008-02-14
```

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```
Why would this happen if I'm using sudo?

---

### Post by ubuntu-freak on 2008-02-14
> **Pandemic187 said:**
> ```

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```
Why would this happen if I'm using sudo?

 
You must have had synaptic open while using the terminal, or the update manager was running.
 
Nathan

---

### Post by Pandemic187 on 2008-02-14
> **reassuringlyoffensive said:**
> You must have had synaptic open while using the terminal, or the update manager was running.
 
Nathan
Nope...

---

### Post by ubuntu-freak on 2008-02-14
> **Pandemic187 said:**
> Nope...

 
Is it still doing it now? With any sudo install command?
 
Nathan

---

### Post by Pandemic187 on 2008-02-15
> **reassuringlyoffensive said:**
> Is it still doing it now? With any sudo install command?
 
Nathan
Normally sudo commands work; the ones in this thread do not. This is fresh install I'm running though so I'm not exactly sure what's wrong.

---

### Post by erginemr on 2008-02-15
If you are absolutely sure that you are not running two installers side by side (be it apt-get, aptitude, dpkg, gdebi, add/remove, update-manager or synaptic, you name it) and the problem persists even after a reboot, then this resembles another thread that I have come across in the past. Check out this link, maybe (and hopefully) it will help:

[http://ubuntuforums.org/showthread.php?t=631128](http://ubuntuforums.org/showthread.php?t=631128)

---

### Post by evolving_monkey on 2008-02-15
Hello  and thanks again for the tutorial,

 Since all of the changes you have made from the original I can no longer get this to work.

When I enter the following script I get an error:

sudo apt-get update && apt-get install alsa-oss compizconfig-settings-manager faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 msttcorefonts sun-java6-fonts sun-java6-jre sun-java6-plugin unrar w32codecs

Error:
E: Could not open lock file /var/lib/dpkg/lock - open (13 permissions denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Luckily I think I saved a copy of your original post, unfortunately I don't have that with me. 

Thanks again for your original post.

---

### Post by evolving_monkey on 2008-02-15
O.K.  Figured it out. I need to add "sudo" after the first "&&" and before the first "apt-get". I should have caught that. Seems to be working now......Thanks again....great tutorial.

---

### Post by ubuntu-freak on 2008-02-15
You as well? Geez.
 
Make sure update manager isn't running, or Synaptic etc. That command should work fine. Try doing apt-get update seperate and then apt-get install after. 
 
Nathan

---

### Post by ubuntu-freak on 2008-02-15
> **Pandemic187 said:**
> Normally sudo commands work; the ones in this thread do not. This is fresh install I'm running though so I'm not exactly sure what's wrong.

 
It's my fault completely. Aysiu added a "sudo" after "&&". I'm away from the comp so couldn't edit it myself. I'm on my phone posting this, but the how-to is far too big for my phone to handle. 
 
Sorry to everyone concerned, but it's now fixed. 
 
Nathan

---

### Post by ubuntu-freak on 2008-02-16
Made some minor adjustments today and added some more info to the introduction. One of which was concerning Synaptic Package Manager and Adept, as many new users don't seem to know about them and what they are for.
 
Nathan

---

### Post by bw44 on 2008-02-16
> **reassuringlyoffensive said:**
> Made some minor adjustments today and added some more info to the introduction. One of which was concerning Synaptic Package Manager and Adept, as many new users don't seem to know about them and what they are for.
 
NathanFor those of us who check the How-to for updates (kind of like reading the daily Gazette :) ) could you edit the "Revised on day month" at the beginning when you make changes?

Much appreciated as always!

---

### Post by ubuntu-freak on 2008-02-16
> **bw44 said:**
> For those of us who check the How-to for updates (kind of like reading the daily Gazette :) ) could you edit the "Revised on day month" at the beginning when you make changes?

Much appreciated as always!

 
Haha thanks. I didn't add new packages or anything major though. Sometimes I only correct my grammar and such as well (O.C.D.). :-)
 
Nathan

---

### Post by sunyata on 2008-02-16
Hi,
I have followed this "howto". Still Realplayer looks like this in Firefox ([www.svt.se):](www.svt.se):)
It looks perfect in standalone.

[IMG]http://goto.glocalnet.net/lars_wallgren_test/svt.jpg[/IMG]

Also firefox refuses to "remember" which plugin I prefer.  I have to tick the boxes everytime I try to stream from [www.svt.se](www.svt.se). I have checked that cookies are allowed. 
"Maximizing" the screen doesn't work either. I have to open an external player to view "full-screen".

What to do?

---

### Post by ubuntu-freak on 2008-02-16
What's wrong with how it looks there? Also, problems usually arise due to how some sites implement streaming. So long as it works for Windows and IE they don't mind. Some sites will modify how they implement it if you send them a polite email with the exact problem and what browser, plugins and system you're using.
 
Nathan

---

### Post by jolitical on 2008-02-16
i am having a problem with installing any of the packages for multimedia, specifically, i was trying to install mplayer, i apparently have shockwave flash on firefox.
 most often i am told:
 e: broken packages.

or

 e:you have held broken packages

i am completely new to ubuntu. any really dumbed down help is appreciated.
cheers

---

### Post by ubuntu-freak on 2008-02-17
> **jolitical said:**
> i am having a problem with installing any of the packages for multimedia, specifically, i was trying to install mplayer, i apparently have shockwave flash on firefox.
 most often i am told:
 e: broken packages.

or

 e:you have held broken packages

i am completely new to ubuntu. any really dumbed down help is appreciated.
cheers

 
Try this;


**sudo apt-get update && sudo apt-get dist-upgrade sudo apt-get -f install sudo dpkg --configure -a**
 
Nathan

---

### Post by sunyata on 2008-02-17
> **reassuringlyoffensive said:**
> What's wrong with how it looks there? Also, problems usually arise due to how some sites implement streaming. So long as it works for Windows and IE they don't mind. Some sites will modify how they implement it if you send them a polite email with the exact problem and what browser, plugins and system you're using.
 
Nathan

Thanks for your reply. I have emailed the webmaster at [www.svt.se](www.svt.se) (swedish publc service TV). I will let you know if and when they make any changes. I let them know that Ubuntu is a growing, serious OS giving XP, Vista and MacOS a match.
I still think buttons look a bit funny in Realplayer. It's difficult to know what they do.

/Sunyata

---

### Post by ubuntu-freak on 2008-02-17
Great! User bw44 had positive results when he emailed the BBC. They could be improving Firefox support and changing the names they give streams. 
 
Nathan

---

### Post by jolitical on 2008-02-17
> **reassuringlyoffensive said:**
> Try this;


**sudo apt-get update && sudo apt-get dist-upgrade sudo apt-get -f install sudo dpkg --configure -a**
 
Nathan


now, it tells me:
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: the following signatures couldn't be verified because the public key is not available
NO_PUBKEY 2EBC26B60C5A2783

---

### Post by ubuntu-freak on 2008-02-17
Did you add the medibuntu repo and GPG key? It's marked "IMPORTANT" and there is a link which instructs you how to do it.
 
Nathan

---

### Post by jolitical on 2008-02-17
> **reassuringlyoffensive said:**
> Did you add the medibuntu repo and GPG key? It's marked "IMPORTANT" and there is a link which instructs you how to do it.
 
Nathan

yes, i added medibuntu but i am not sure how to add the gpg key,

joanna

---

### Post by ubuntu-freak on 2008-02-17
It's on the medibuntu page, just below the Gutsy repo add command. You paste the wget command into the terminal. 

Nathan

---

### Post by ubuntu-freak on 2008-02-17
Joanna, it's this command;
 

**sudo wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update**
 
Did you fix your broken packages okay? Try this command again after adding the key; 
 
**sudo apt-get update && sudo apt-get dist-upgrade sudo apt-get -f install sudo dpkg --configure -a**

Then install the packages in part 1 of my how-to.

Hope that sorts you out.
 
Nathan

---

### Post by rosegarden78 on 2008-02-18
Thanks I didn't know FFMPEG had a front end.

---

### Post by ubuntu-freak on 2008-02-18
> **rosegarden78 said:**
> Thanks I didn't know FFMPEG had a front end.

 
Easy to use as well. I'm sure it will be sticking around too. Hopefully it will end up in the repo at some point.
 
Nathan

---

### Post by jolitical on 2008-02-18
> **reassuringlyoffensive said:**
> Joanna, it's this command;
 

**sudo wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update**
 
Did you fix your broken packages okay? Try this command again after adding the key; 
 
**sudo apt-get update && sudo apt-get dist-upgrade sudo apt-get -f install sudo dpkg --configure -a**

Then install the packages in part 1 of my how-to.

Hope that sorts you out.
 
Nathan

Hi Nathan, unfortunately, now it is telling me 'e: has broken packages' again.
i apologize for all of the hassle! this occurs when i try to find the missing plug-in from the  bbc website to stream their radio program. i am directed towards adding mplayer and after it downloads all of the elements the final window simply says there are broken packages. do i have to add all of the repo etc. every time? or, if i added it once is it still there when i add the other components? thanks for all of your help thus far. 
joanna

---

### Post by ubuntu-freak on 2008-02-18
Nah, you add the medibuntu repo and key once. The command in my how-to installs mplayer and mozilla-mplayer. Dunno what you're doing wrong, never had that problem. Doesn't the update manager offer to fix your broken packages? Try 
 
**sudo dpkg --configure -a** 

again. Did you try that command above to fix your packages after you added the GPG key? How did you break them anyway? When did it happen?
 
Nathan

---

### Post by ubuntu-freak on 2008-02-18
Also, the terminal might tell you how to sort problems out sometimes, you just have to put "sudo" infront of the commands. 
 
Nathan

---

### Post by waldorsockbat on 2008-02-18
OK I followed this guide to be able to play dvds on my laptop and now I cant watch streaming videos of any format. Mplayer plugin says connecting to server and does nothing all while cpu is at 100%.Any ideas on where to begin to fix this?

---

### Post by ubuntu-freak on 2008-02-18
> **waldorsockbat said:**
> OK I followed this guide to be able to play dvds on my laptop and now I cant watch streaming videos of any format. Mplayer plugin says connecting to server and does nothing all while cpu is at 100%.Any ideas on where to begin to fix this?

 
What did you stream media with before? Strange. Did you install RealPlayer or are you just using mozilla-mplayer? Are you using the xv driver or x11? (You can check in MPlayer's preferences). Only the x11 driver is CPU intensive. What graphics device do you have? Did you put my plugin settings in the home conf or /etc one? Um what else...did you reboot?
 
Nathan

---

### Post by waldorsockbat on 2008-02-19
I had restricted extras,all gstreamer and flash

yes i installed realplayer 

I tried both xv and x11 with the same resutls

I have the ait200m 

home conf

rebooted several times.

I am sure I missed 1 small thing that is muck'n up the works but I can't find it, I have been over the giude several times before I posted here. Is there a way to purge everything I installed with this guide and start over without making things worse? It took me forever to get compiz to play nice with my ati200m chipset,really dont want to mess that up.


OK quick update..flash is working. the only problem I can see now is mplayer pluging is still doing nothing and using 100%cpu.

---

### Post by ubuntu-freak on 2008-02-19
You don't need to purge it all. Did you have MPlayer before this how-to? Does the main player play vids? If not, maybe you need to change the audio driuer. Did you remove the pluginreg.dat file? Is RealPlayer streaming okay?
 
As a last resort you could remove mozilla-mplayer and RealPlayer and then try streaming with totem-mozilla or the xine-plugin (remember to delete the pluginreg.dat file). You will also need totem-xine and libxine1-ffmpeg if you stream with the xine-plugin.
 
Nathan

---

### Post by roger_1960 on 2008-02-19
Hi
Having followed your how to by pasting commands into terminal, I now get the following error message every time I try to use the Add/Remove facility in Applications... HELP!

AN ERROR OCCURED
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by ubuntu-freak on 2008-02-19
> **roger_1960 said:**
> Hi
Having followed your how to by pasting commands into terminal, I now get the following error message every time I try to use the Add/Remove facility in Applications... HELP!

AN ERROR OCCURED
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

 
You must have interrupted the installation of something or other. Try running the command it told you to in the terminal;
 
```
sudo dpkg --configure -a
```
 
Hope that sorts it.
 
Nathan

---

### Post by roger_1960 on 2008-02-19
Hi again

Yes, its sorted!  Thanks for pointing out the obvious very politely!!

---

### Post by ubuntu-freak on 2008-02-19
> **roger_1960 said:**
> Hi again
 
Yes, its sorted! Thanks for pointing out the obvious very politely!!
 
No problem. Thought I'd tell you like that so if it mentions commands another time, you will know. It's just always always a case of adding "sudo" before them when it's a system command.
 
Nathan

---

### Post by ubuntu-freak on 2008-02-19
**Update** 

Added some commands to help with errors certain users get and added the wget medibuntu repo commands to the how-to. 
 
I'm still unsure whether to use the code boxes in my how-to. Example;
 
```
sudo apt-get update
``` 
 
or just leave it be. What do you think? I'm sure bw44 has an opinion. :-)
 
Nathan

---

### Post by skandia2 on 2008-02-19
I am currently using Kubuntu Gutsy withe Firefox (after using Feisty) and have been trying to get BBC video streaming working reliably for several months.....

After following a previous how-to ( mozilla-mplayer plugin for firefox: BBC, CBC and Stage6 streaming videos micro-howto) I could access the BBC web site streaming video albeit intermittently using Mplayer (using the windows media player format video - real player format did not work).

Usually the embedded player would usually fail but the stand alone player was more reliable, even then some BBC videos would not play at all.

Whenever I test using a Windows XP PC - all BBC videos work.

I have used ZINE. This gave results similar results to Mplayer - usually works in stand alone mode with real player format BBC video. But sometimes crashes Firefox.    

I have tried to follow this how-to - carefully - including the trouble shooting section. 

Alas, neither the windows media player or the real player format videos appear to work.

Using windows media player format videos Mplayer repeatedly connects to the BBC website traffic appears to flow with the occasional sound click but no video.

Using the real player format - realplayer opens as an embedded window but soon gets grayed out and no traffic appears to flow from the PC (Knetwork manager reports 0 bytes Tx & Rx)

Any help / advice would be appreciated.

---

### Post by ubuntu-freak on 2008-02-19
Well it's odd that both don't work. Do the main players work okay? Try downloading a Real Media clip and play it in RealPlayer, and do something similar for MPlayer. 
 
Could it be the update to Firefox? Do flash vids work okay? The how-to works, not sure what's going on with you there. Try removing the pluginreg.dat again.
 
Nathan

---

### Post by thechilipepper0 on 2008-02-19
Hey, I was wondering if you could help me.  I'm a fresh Ubuntu convert, and I'm trying to get DVD playback to work.  I've tried several solutions and have gotten as far as the dvd reads and i can hear the audio in the menus, but there is no video!

i have installed gxine, vlc, totem with xine backend...none of them work.  It's really weird though, when I first installed gxine, the DVD played perfectly in Totem.  But when i tried it again, no video, sigh. oh yeah, and in vlc if i move the window around, the video flickers for a second, then goes out.

i have an ATi x300 and ran some workaround that i found online to get the drivers to work.

Please help!

---

### Post by ubuntu-freak on 2008-02-19
> **thechilipepper0 said:**
> Hey, I was wondering if you could help me.  I'm a fresh Ubuntu convert, and I'm trying to get DVD playback to work.  I've tried several solutions and have gotten as far as the dvd reads and i can hear the audio in the menus, but there is no video!

i have installed gxine, vlc, totem with xine backend...none of them work.  It's really weird though, when I first installed gxine, the DVD played perfectly in Totem.  But when i tried it again, no video, sigh. oh yeah, and in vlc if i move the window around, the video flickers for a second, then goes out.

i have an ATi x300 and ran some workaround that i found online to get the drivers to work.

Please help!

 
Well I always recommend not to use the Xine backend if you can help it. If you follow part 1 and 3 you should be fine. Why move the VLC window around? Just leave it fullscreen. Try turning off desktop effects while you watch a DVD (System>Preferences>Appearance>Effects).
 
Nathan

---

### Post by thechilipepper0 on 2008-02-19
yep, that did it. after i turned off desktop effects, the DVD played perfectly in all players.
it's a bittersweet victory. i like the effects and when i turn it back on i have to customize all that stuff again. sigh. is there any way to reconfig compiz or something so they work together?

At the very least, thanks a lot for helping me figure it out.
-Dan

---

### Post by ubuntu-freak on 2008-02-19
> **thechilipepper0 said:**
> yep, that did it. after i turned off desktop effects, the DVD played perfectly in all players.
it's a bittersweet victory. i like the effects and when i turn it back on i have to customize all that stuff again. sigh. is there any way to reconfig compiz or something so they work together?

At the very least, thanks a lot for helping me figure it out.
-Dan

 
Are you using open source drivers for your ATI device or proprietary? In theory, xvideo playback should be fine with effects enabled. Only quite new Intel and ATI chipsets have issues.
 
Nathan 
 
Edit: From what I've just read, your x300 should've worked just fine when you installed Ubuntu. You installed it recently yes?

---

### Post by bw44 on 2008-02-19
> **reassuringlyoffensive said:**
> I'm still unsure whether to use the code boxes in my how-to. Example;
 
```
sudo apt-get update
``` 
 
or just leave it be. What do you think? I'm sure bw44 has an opinion. :-)
 
NathanHey, every O-C does his own thing! :)  I use code boxes, but the fact is I never even thought about the fact that you don't.  It's the content that counts and bolding works just as well (and takes up less space).

bw44

---

### Post by thechilipepper0 on 2008-02-20
> **reassuringlyoffensive said:**
> Are you using open source drivers for your ATI device or proprietary? In theory, xvideo playback should be fine with effects enabled. Only quite new Intel and ATI chipsets have issues.
 
Nathan 
 
Edit: From what I've just read, your x300 should've worked just fine when you installed Ubuntu. You installed it recently yes?

Yes, that's correct. It did work out of the box with the open source driver, but it wouldn't work with compiz-fusion. so i followed [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.2_Driver_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.2_Driver_Manually") and then it worked fine. i have no idea if DVD worked before then, i never tried it out.

---

### Post by ubuntu-freak on 2008-02-20
> **thechilipepper0 said:**
> Yes, that's correct. It did work out of the box with the open source driver, but it wouldn't work with compiz-fusion. so i followed [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.2_Driver_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.2_Driver_Manually") and then it worked fine. i have no idea if DVD worked before then, i never tried it out.

 
Strange. So you are using ATI's driver instead of the open source one yeah? From what I've read in other threads, effects and xvideo should work with the open driver. Maybe I'm wrong.
 
You should do a fresh install of Hardy when it's released and see if effects work. You will have an easier time using the open source drivers. The open ones are being improved all the time, ATI and Intel release information to the community, unlike NVIDIA. 
 
Nathan

---

### Post by ubuntu-freak on 2008-02-20
> **bw44 said:**
> Hey, every O-C does his own thing! :)  I use code boxes, but the fact is I never even thought about the fact that you don't.  It's the content that counts and bolding works just as well (and takes up less space).

bw44

 
Yeah I think I'll leave it as it is.
 
Nathan

---

### Post by skandia2 on 2008-02-20
Thanks for replaying Nathan

Flash works fine from CNN, Youtube etc

Real player seems erratic Uni of Delaware real player test worked very well. The real player official test site ram files do not automatically play - I have to download then play the ram file which then works OK.

Mplayer plays wmv files OK

I deleted pluginreg.dat and have removed all the Firefox add-ons.

Very confusing!

---

### Post by bw44 on 2008-02-20
> **skandia2 said:**
> I am currently using Kubuntu Gutsy withe Firefox (after using Feisty) and have been trying to get BBC video streaming working reliably for several months.....

After following a previous how-to ( mozilla-mplayer plugin for firefox: BBC, CBC and Stage6 streaming videos micro-howto) I could access the BBC web site streaming video albeit intermittently using Mplayer (using the windows media player format video - real player format did not work).

Usually the embedded player would usually fail but the stand alone player was more reliable, even then some BBC videos would not play at all.

Whenever I test using a Windows XP PC - all BBC videos work.

I have tried to follow this how-to - carefully - including the trouble shooting section. 

Alas, neither the windows media player or the real player format videos appear to work.

Using windows media player format videos Mplayer repeatedly connects to the BBC website traffic appears to flow with the occasional sound click but no video.

Using the real player format - realplayer opens as an embedded window but soon gets grayed out and no traffic appears to flow from the PC (Knetwork manager reports 0 bytes Tx & Rx)

Any help / advice would be appreciated.

I have struggled with the BBC site as well.  Don't assume that it's all your fault -- they have done their share to make it difficult for Linux users (not intentionally, but inadvertently).

Here's what worked best for me and I recommend trying it (again, if you think you already have!)

1. Install RealPlayer as per Nathan's how-to.

2. Be absolutely sure that your mplayer settings in mplayerplug-in.conf are as he describes.  (If you change anything, there, delete pluginreg.dat and restart Firefox -- in fact, do this anyway, to make sure Firefox knows you don't want to use mplayer for helix/RealPlayer streams.)

3. Double-check that in the BBC News Player "Preferences" you have selected RealPlayer as the default media player.

4. Click on a BBC video link.  The BBC News Player should open and the "Real" logo should appear in the window.  After a few seconds, you may see it display "Contacting ad.uk.doubleclick.net" at which point it will appear to die and no further network traffic will arrive.  Now try clicking "Launch in standalone player" in the lower right below the viewing area. RealPlayer should launch in a separate window and the video (prefaced by an ad if you are outside the UK) should begin to play.

5.  Sometimes you will see an alert box like the one attached below.  Don't give up.  There is something wrong with the way the BBC site is handling the Linux Firefox requests.  People have been reporting this for months!   Persevere and click OK several times if necessary and then try launching RealPlayer standalone as in 4 above.

Yes, you are right, this all works under Windows (although I don't use RealPlayer there, but WMP instead), which is what BBC naturally tests most.  But I have experienced everything you described and following the above allows me to view most of the videos most of the time. When things don't work, I've stopped blaming Ubuntu, Linux Firefox, mplayer or RealPlayer and just attribute it to BBC's problems making advertising work.

Good luck and let us know what happens -- good or bad!

PS.  The test pages at [http://service.real.com/test/](http://service.real.com/test/) (which I assume is what you referred to) do work on my system. You should not have to download the files fiirst-- when you click on one of them, what happens?

---

### Post by ubuntu-freak on 2008-02-20
My troubleshooting section has a paragraph which should help you to instruct FF to use RealPlayer to stream on the test site.
 
Nathan

---

### Post by skandia2 on 2008-02-21
BW44, thank you for your detailed response

Re your first 3 points I think I have got them correct as real player appears in the embedded player window with the logo etc but blanks out to gray after a few seconds

Your point 4 is very helpful.

I live in the UK so I have net seen the dreaded doubleclick ad sever on the BBC website but real player embedded mode still appears to  'lock up' for me.

When I clicked on stand alone player Firefox did not know which application to open but manually selecting /usr/bin/realplayer caused the video to open in real player and work well :p

I have now made Firefox remember to do this automatically and the BBC real player videos now work. 

The stand alone mode is not as seamless as Mplayer's standalone mode (when it used to work) - I still get the ram file appear on the firefox download manager and have to manually select the real player tab to select the standalone real player over the blank embedded player to see the video.

I guess this could be a Kubuntu / KDE issue

A question for Nathan.

Should Mplayer support the BBC's windows media player mode or is Mplayer second best to the BBC's real player mode?  

Thanks

Richard

---

### Post by bw44 on 2008-02-21
> **skandia2 said:**
> BW44,thank you for the detailed response . . . The stand alone mode is not as seamless as Mplayer's standalone mode (when it used to work) - I still get the ram file appear on the firefox download manager and have to manually select the real player tab to select the standalone real player over the blank embedded player to see the video.

I guess this could be a Kubuntu / KDE issue

A question for Nathan.

Should Mplayer support the BBC's windows media player mode or is Mplayer second best to the BBC's real player mode?  

Your welcome.  I'm glad you got RealPlayer working with the BBC site, but I don't understand what you mean by "standalone mode" when you still (?) get the ram file appearing on the Firefox download manager.  Sometimes I see the Firefox download manager appear when I click on a link to a PDF file, but never when I click on a link to a RealPlayer (or other) video file. Or is this not what is happening? When you say you have to "manually select the real player tab to select the standalone real player over the blank embedded player" I'm not sure what tab you are referring to.  If you want to bother to describe it again, I'll try to help.

Anyway, if it's a Kubuntu/KDE issue I wouldn't be able to help, as I have almost no experience with KDE.

I think Nathan prefers RealPlayer, but I changed to it only because I couldn't get mplayer to work with the BBC site after they introduced advertising for non-UK residents.  I even figured out a way to doctor their URLs so they would not access the ad server, but go directly to the feature video.  For example the following is the URL for the One-Minute World News summary clip stripped of the stuff that tells it to preface the clip with an ad [http://news.bbc.co.uk/newsa/n5ctrl/summaries/world/bb/video/world_bb.asx?](http://news.bbc.co.uk/newsa/n5ctrl/summaries/world/bb/video/world_bb.asx?) (the fact that this news clip has not been updated for three days is an unrelated problem which BBC says they are working on!!) Try clicking on this link. On my system it bypasses BBC's check on what player you prefer, bypasses the ads (not a problem for you) and launches mplayer (even though my preferences say I prefer RealPlayer). Note, though, that the controls are not displayed.  If it works for you, you can compare and see there is little difference in the image/sound quality (none, as far as I can tell).

So the short answer to your last question is (IMO): No, mplayer is as good as RealPlayer, when it works. :)

bw44

---

### Post by stooshbunutu on 2008-02-21
I'de Just like to say a massive thanks, this is a brilliant tutorial Thanks a lot Mate!

---

### Post by ubuntu-freak on 2008-02-21
> A question for Nathan.

Should Mplayer support the BBC's windows media player mode or is Mplayer second best to the BBC's real player mode?  

Thanks

Richard

 
Yeah I prefer RM to WM on the BBC site. Radio sounds better in RM format as well, and loads quicker. Goodness knows why they don't offer a good mp3 stream though.
 
I've had that download dialog pop up on the Real.com test page as well. Nothing major though, it's just cos they are presented as downloads and less as streams. Didn't happen when I used the MPlayer plugin on the test site though, but then the MPlayer plugin didn't always work, hence why I advised people to use RealPlayer.
 
Nathan

---

### Post by ubuntu-freak on 2008-02-21
> **stooshbunutu said:**
> I'de Just like to say a massive thanks, this is a brilliant tutorial Thanks a lot Mate!

 
No problem mate. 
Thanks for posting your comments, helps keep the thread alive so other forum goers can see it.
 
Nathan

---

### Post by bw44 on 2008-02-21
> **reassuringlyoffensive said:**
> Yeah I prefer RM to WM on the BBC site. Radio sounds better in RM format as well, and loads quicker. Goodness knows why they don't offer a good mp3 stream though.
 
I've had that download dialog pop up on the Real.com test page as well. Nothing major though, it's just cos they are presented as downloads and less as streams. Didn't happen when I used the MPlayer plugin on the test site though, but then the MPlayer plugin didn't always work, hence why I advised people to use RealPlayer.
 
NathanIt's funny how one's mileage can vary.  All the links at the Real test site  [http://service.real.com/test/](http://service.real.com/test/) launch RealPlayer and play fine for me.  My only complaint is with the sound!  Unlike mplayer, RealPlayer resets the volume level to inaudible (or maybe it's the PCM level -- my sound card driver is the pits) whenever I  link to an RM stream.  It's a real pain to have to reset the volume every time.

But on balance since BBC is the site I visit most often, I'm sticking with RealPlayer, too (for now!)

bw44

---

### Post by afeasfaerw23231233 on 2008-02-22
i've followed all the steps in part 1,2,3 and when i played bbc video choosing real pllayer, these showed up. and if i choose windows media player, these showed up. i never get bbc video play correctly.

---

### Post by bw44 on 2008-02-22
> **afeasfaerw23231233 said:**
> i've followed all the steps in part 1,2,3 and when i played bbc video choosing real pllayer, these showed up. and if i choose windows media player, these showed up. i never get bbc video play correctly.Hi, the screen shots help a lot! They look exactly like what I see.  When you get to the third one, try clicking on the words "Launch in stand alone player" in the lower left.  What **should** happen is RealPlayer should open its own window and the video should download and play in the new window. (Nobody I've heard of has got the "embedded" RealPlayer to play in the BBC's window using Linux Firefox.)

Try that and post the results.

As for the mplayer screens, they are also what I see, and **all** I see.  I think because of the way the BBC site is linking to their ad server,  mplayer (or BBC) loses the connection somehow.  If you still have the Firefox mplayer plugin installed, try this link [http://news.bbc.co.uk/newsa/n5ctrl/summaries/world/bb/video/world_bb.asx?](http://news.bbc.co.uk/newsa/n5ctrl/summaries/world/bb/video/world_bb.asx?) which should launch mplayer (even if you have previously specified your preference for RealPlayer) and play the One-minute World News video.  The above URL has the stuff removed which directs your request to BBC's select-the-browser and run-the-ad code.

Nathan:  I hope you don't think I'm trying to co-opt your how-to thread for an off-topic on BBC and its problems.  It seems justified if some people try the BBC site to check out if video streaming works after following your how-to.  But let me know if it bugs you.  

bw44

---

### Post by myviolet on 2008-02-22
Thanks alot for your very nice how-to Nathan!
you did a very good job for us mate!
cheers!

---

### Post by ubuntu-freak on 2008-02-22
> **myviolet said:**
> Thanks alot for your very nice how-to Nathan!
you did a very good job for us mate!
cheers!

 
Thanks. No problem.
 
Nathan

---

### Post by ubuntu-freak on 2008-02-22
> **afeasfaerw23231233 said:**
> i've followed all the steps in part 1,2,3 and when i played bbc video choosing real pllayer, these showed up. and if i choose windows media player, these showed up. i never get bbc video play correctly.

 
BBC site should improve over time, but as bw44 said, you can stream with RealPlayer in stand-alone mode. I recommend you listen to their radio streams in the RM format also, which WILL work embedded.
 
Nathan

---

### Post by jolitical on 2008-02-22
> **reassuringlyoffensive said:**
> Also, the terminal might tell you how to sort problems out sometimes, you just have to put "sudo" infront of the commands. 
 
Nathan

hi nathan, yes i tried all of your suggestions. i am not sure how this happened. i guess it was my overzealousness mixed with little knowledge of how the commands i am typing actually work...in terms of the terminal telling me how to fix the problem. what would i type after "sudo"?  'sudo fix broken package"?
cheers.joanna

---

### Post by ubuntu-freak on 2008-02-22
> **jolitical said:**
> hi nathan, yes i tried all of your suggestions. i am not sure how this happened. i guess it was my overzealousness mixed with little knowledge of how the commands i am typing actually work...in terms of the terminal telling me how to fix the problem. what would i type after "sudo"?  'sudo fix broken package"?
cheers.joanna

 
Still having problems? You sure you added the medibuntu repo and key? I've added the wget commands to the how-to now, if you have Gutsy it's just a cut n paste job. If you only need the key, just wget that. 
 
Did it tell you packages were broken after you tried to install my essential packages? Try the install -f and configure -a commands below the essential packages section in. It's entitled "Did you have errors?" 
 
Not sure what else to tell you. Everything is there as far as I know, including that error section and troubleshooting.
 
Doesn't the update manager offer to fix the broken packages during automatic updates? Has done that for me before.
 
Hope you get it all fixed up. 
 
Nathan

---

### Post by afeasfaerw23231233 on 2008-02-22
> **bw44 said:**
> Hi, the screen shots help a lot! They look exactly like what I see.  When you get to the third one, try clicking on the words "Launch in stand alone player" in the lower left.  What **should** happen is RealPlayer should open its own window and the video should download and play in the new window. (Nobody I've heard of has got the "embedded" RealPlayer to play in the BBC's window using Linux Firefox.)

Try that and post the results.

As for the mplayer screens, they are also what I see, and **all** I see.  I think because of the way the BBC site is linking to their ad server,  mplayer (or BBC) loses the connection somehow.  If you still have the Firefox mplayer plugin installed, try this link [http://news.bbc.co.uk/newsa/n5ctrl/summaries/world/bb/video/world_bb.asx?](http://news.bbc.co.uk/newsa/n5ctrl/summaries/world/bb/video/world_bb.asx?) which should launch mplayer (even if you have previously specified your preference for RealPlayer) and play the One-minute World News video.  The above URL has the stuff removed which directs your request to BBC's select-the-browser and run-the-ad code.
bw44
thanks but still doesn't work. i click 'launch in a standalone player" and this comes up.
when i click your link [http://news.bbc.co.uk/newsa/n5ctrl/summaries/world/bb/video/world_bb.asx?](http://news.bbc.co.uk/newsa/n5ctrl/summaries/world/bb/video/world_bb.asx?) it says Getting playlist --> downloading from http:/bbc......@@@ --> download complete --> done   But nothing shows up!!!
iplayer radio works perfectly.
EDIT: the black and white cat is beautiful. i used to have a similar one in the park.

---

### Post by ubuntu-freak on 2008-02-22
> **afeasfaerw23231233 said:**
> thanks but still doesn't work. i click 'launch in a standalone player" and this comes up.
when i click your link [http://news.bbc.co.uk/newsa/n5ctrl/summaries/world/bb/video/world_bb.asx?](http://news.bbc.co.uk/newsa/n5ctrl/summaries/world/bb/video/world_bb.asx?) it says Getting playlist --> downloading from http:/bbc......@@@ --> download complete --> done   But nothing shows up!!!
iplayer radio works perfectly.
EDIT: the black and white cat is beautiful. i used to have a similar one in the park.

 
Read paragraph 2 of my troubleshooting section.
 
Nathan

---

### Post by intercharger on 2008-02-22
Hi everyone,

first of all many thanks to reassuringlyoffensive for this wonderful howto. It is very well explained and it sure was useful. 

I've got a problem when trying to play stage6 videos on kde4 with firefox and mplayerplug-in, I've been several days now searching for solutions but nothing seems to work.

I know there is a problem with kde4 specifically because I can watch stage6 videos perfectly in kde3 with the same firefox and plug-in. Problem is when I try to play the video in kde4 it loads the mplayer plug-in and also a strange translucid grey window. This window means I cannot see half of the video because it's always on top of everything. Also, when trying to go fullscreen the video doesn't work but the audio does and I can only see the video by clicking with the right mouse button on the screen and only for a fraction of second then it stops working again, (audio always works).

I was wondering if anyone knows what could I try to fix this, or if anyone has this same problem. Maybe I should report this to kde developers? I don't know what to try to fix this.

Thanks in advance.

---

### Post by ubuntu-freak on 2008-02-22
> **intercharger said:**
> Hi everyone,

first of all many thanks to reassuringlyoffensive for this wonderful howto. It is very well explained and it sure was useful. 

I've got a problem when trying to play stage6 videos on kde4 with firefox and mplayerplug-in, I've been several days now searching for solutions but nothing seems to work.

I know there is a problem with kde4 specifically because I can watch stage6 videos perfectly in kde3 with the same firefox and plug-in. Problem is when I try to play the video in kde4 it loads the mplayer plug-in and also a strange translucid grey window. This window means I cannot see half of the video because it's always on top of everything. Also, when trying to go fullscreen the video doesn't work but the audio does and I can only see the video by clicking with the right mouse button on the screen and only for a fraction of second then it stops working again, (audio always works).

I was wondering if anyone knows what could I try to fix this, or if anyone has this same problem. Maybe I should report this to kde developers? I don't know what to try to fix this.

Thanks in advance.

 
Thanks for your comments.
 
Have you tried turning off any special desktop effects KDE4 has? I'm not familar with KDE4, but I know they wanted kwin to have it's own effects and not just rely on Compiz Fusion.
 
Nathan

---

### Post by waldorsockbat on 2008-02-23
ok I still can not get realplayer or windows media to play,the real test site tells me file cant be found.

---

### Post by 5735guy on 2008-02-23
Hi there, as you probably know Ubuntu 8.04 ' Hardy' is shipping with Firefox 3. Currently I am working with Ubuntu 8.04 (Alpha 5), unfortunately Realplayer doesn't seem to want to work with Firefox3. Is there a workaround please ?:confused:

---

### Post by bw44 on 2008-02-23
> **afeasfaerw23231233 said:**
> thanks but still doesn't work. i click 'launch in a standalone player" and this comes up.
when i click your link [http://news.bbc.co.uk/newsa/n5ctrl/summaries/world/bb/video/world_bb.asx?](http://news.bbc.co.uk/newsa/n5ctrl/summaries/world/bb/video/world_bb.asx?) it says Getting playlist --> downloading from http:/bbc......@@@ --> download complete --> done   But nothing shows up!!!
iplayer radio works perfectly.
EDIT: the black and white cat is beautiful. i used to have a similar one in the park.

> **reassuringlyoffensive said:**
> Read paragraph 2 of my troubleshooting section.
 
Nathan

afeasfaerw, 

What Nathan said to do there worked for me -- did you try it?  The fact that the radio streams work means you're almost there!

bw44
PS. The cat lives in Istanbul, where my son photographed it.

---

### Post by intercharger on 2008-02-23
> **reassuringlyoffensive said:**
> Thanks for your comments.
 
Have you tried turning off any special desktop effects KDE4 has? I'm not familar with KDE4, but I know they wanted kwin to have it's own effects and not just rely on Compiz Fusion.
 
Nathan

Hi again. Thanks for the quick response. I've tried this and yes it solves the problem. At least I have a solution, but I'd like to know if there's a way of watching these videos without having to turn on and off the effects everytime. 

I'm saying just in case anyone has come up with a solution for this. I have tried to disable all effects to see if the problem came from a specific type of effect but just activating the "Enable Desktop Effects" option in the System Settings, even with all effects disabled makes the strange window appear again.

So if anyone has this same problem I'd appreciate some information, meanwhile should I report this as a kde4/mozilla-mplayer bug?

---

### Post by afeasfaerw23231233 on 2008-02-23
thanks. it works in a standalone real player now.
what a nice cat!

---

### Post by afeasfaerw23231233 on 2008-02-23
really don't understand. bbc iplayer still play very good yesterday. but now it cannot play any live radio programme [not the archive and the 'listen again' one]. then i click listen using standalone real player and this show up. the embedded plugin real player worked perfectly in iplayer yesterday but know it doesn't work at all. STRANGE!!

---

### Post by ubuntu-freak on 2008-02-23
> **intercharger said:**
> Hi again. Thanks for the quick response. I've tried this and yes it solves the problem. At least I have a solution, but I'd like to know if there's a way of watching these videos without having to turn on and off the effects everytime. 

I'm saying just in case anyone has come up with a solution for this. I have tried to disable all effects to see if the problem came from a specific type of effect but just activating the "Enable Desktop Effects" option in the System Settings, even with all effects disabled makes the strange window appear again.

So if anyone has this same problem I'd appreciate some information, meanwhile should I report this as a kde4/mozilla-mplayer bug?

 
If it didn't do it in the KDE 3 series, then it must be a KDE 4 bug. Keep in mind that KDE4 has, and is going to have quite a few bugs. Canonical won't even let Kubuntu 8.04 Hardy Heron be an LTS release (Long Term Support), as it's going to be buggy due to the inclusion of KDE4. That's what I read anyway.
 
Try the Compiz Forums or KDE.
 
Nathan

---

### Post by ubuntu-freak on 2008-02-23
> **afeasfaerw23231233 said:**
> really don't understand. bbc iplayer still play very good yesterday. but now it cannot play any live radio programme [not the archive and the 'listen again' one]. then i click listen using standalone real player and this show up. the embedded plugin real player worked perfectly in iplayer yesterday but know it doesn't work at all. STRANGE!!

 
That is strange. Try deleting the pluginreg.dat again and restart FF. 
 
Nathan

---

### Post by cozmicharlie on 2008-02-23
Thanks for this great How To.  I got everything working except I am having problems with mms files - for example this mms://media.itatiaia.com.br/Itatiaia from this web site [http://www.itatiaia.com.br/](http://www.itatiaia.com.br/).  When I go to open this in Firefox I get a dialog that it needs to open in an external application and it wants to open using Totem rather than mplayer.  I have uninstalled the Totem plug in and Totem.  Two questions - shouldn't this open in mplayer without having to go to an external app and is their a way to point Firefox to mplayer when it asks to open external applications.  I can open this file in a terminal with 
```
mplayer http://www.itatiaia.com.br/
```

Thanks again for the great How To and all your help.

---

### Post by ubuntu-freak on 2008-02-23
> **5735guy said:**
> Hi there, as you probably know Ubuntu 8.04 ' Hardy' is shipping with Firefox 3. Currently I am working with Ubuntu 8.04 (Alpha 5), unfortunately Realplayer doesn't seem to want to work with Firefox3. Is there a workaround please ?:confused:

 
Are RealPlayer's nphelix plugins in the FF3 plugins folder? Paragraph 6 of the troubleshooting section should help you if they aren't there. If that doesn't help, use MPlayer to stream RM formats for now.
 
Nathan

---

### Post by bw44 on 2008-02-23
> **reassuringlyoffensive said:**
> . . . Canonical won't even let Kubuntu 8.04 Hardy Heron be an LTS release (Long Term Support), as it's going to be buggy due to the inclusion of KDE4. That's what I read anyway. . .
 
Nathan

Where can we read about things like this?  I'd really like to know what the plans are for 8.04.

Thanks.

---

### Post by ubuntu-freak on 2008-02-23
> **bw44 said:**
> Where can we read about things like this?  I'd really like to know what the plans are for 8.04.

Thanks.

 
[http://www.linuxjournal.com/node/1005960](http://www.linuxjournal.com/node/1005960)
 
and
 
[https://bugs.launchpad.net/ubuntu/+source/meta-kde/+bug/182786](https://bugs.launchpad.net/ubuntu/+source/meta-kde/+bug/182786)
 
Nathan

---

### Post by ubuntu-freak on 2008-02-23
Here is a link to the [Hardy Heron Wiki](https://wiki.ubuntu.com/HardyHeron).
 
Nathan

---

### Post by Virgilius on 2008-02-23
I've tried to do *at least* the first part of installing the codecs and whatnot and my console came up with this error: E: Type '--09:57:27--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
What does that mean? and will this post help with the lack of sound on my Feisty box?

---

### Post by ubuntu-freak on 2008-02-23
> **Virgilius said:**
> I've tried to do *at least* the first part of installing the codecs and whatnot and my console came up with this error: E: Type '--09:57:27--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
What does that mean? and will this post help with the lack of sound on my Feisty box?

 
I presume you tried the commands for people who had errors? Did you edit the medibuntu wget command? Rename "gutsy" to "fiesty". Have you tried the comprehensive sound guide? Did sound not work in Gutsy? 
 
Nathan

---

### Post by Virgilius on 2008-02-23
> I presume you tried the commands for people who had errors? Did you edit the medibuntu wget command? Rename "gutsy" to "fiesty". Have you tried the comprehensive sound guide? Did sound not work in Gutsy?

Nathan I use Fiesty and could have spelled the word wrong! :lolflag: I know next to nothing about the Comprehensive Sound Guide, is it to do with the multimedia post by Adamant? and yes, even if I'm using Fiesty, I have no sound! Do you need my box's specifications for this? I hear making such a list makes it handy.

---

### Post by Virgilius on 2008-02-23
P.S: I am getting an error after doing the code after sudo wget that says:
E: Type '--11:07:20--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list when I tried the 
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by dixonstalbert on 2008-02-23
I have got mplayer plugin running so I can watch apple.com trailers and CBC (cbc.ca) videos

but it still will not open the CBC radio links.  They used to work a few months ago with Feisty and mplayer plugin 

you can try them at 

[http://www.cbc.ca/radio/]("http://www.cbc.ca/radio/")

I clean re- installed Gutsy yesterday then followed the tutorial on first page of thread.

The problem appears to be that the links point to an asx playlist, which points to another asx playlist , which in turn points to the mms media file. Mplayerplugin inserts the first asx into mplayer with the -playlist switch. Mplayer -playlist then parses the first asx and finds the 2nd asx and tries to play it as a media stream -which it is not- and crashes after it has loaded the file.

What you see on the screen is the embedded player on the screen load the file for a few seconds then report 'stopped'.


here is the debug log file showing mplayer trying to play the 2nd asx playlist file which is not a valid media file:

```
Playing http://mfile2.akamai.com/9617/live/reflector:37916.asx?bkup=37917.
Resolving mfile2.akamai.com for AF_INET...
Connecting to server mfile2.akamai.com[64.86.101.143]: 80...
STREAM_ASF, URL: http://mfile2.akamai.com/9617/live/reflector:37916.asx?bkup=37917
Resolving mfile2.akamai.com for AF_INET...
Connecting to server mfile2.akamai.com[64.86.101.143]: 80...
size_confirm mismatch!: 22611 20047
Error while parsing chunk header
Failed, exiting.

```

 If you run mplayer with  the 2nd embedded  asx link, mplayer-playlist  will find the mms stream and successfully play it.

```
 mplayer -playlist http://mfile2.akamai.com/9617/live/reflector:37916.asx?bkup=37917

```

the debug log for this shows:

```
Playing mms://a1917.l961737916.c9617.g.lm.akamaistream.net/D/1917/9617/v0001/reflector:37916.
STREAM_ASF, URL: mms://a1917.l961737916.c9617.g.lm.akamaistream.net/D/1917/9617/v0001/reflector:37916
Resolving a1917.l961737916.c9617.g.lm.akamaistream.net for AF_INET...
Connecting to server a1917.l961737916.c9617.g.lm.akamaistream.net[157.238.197.166]: 1755...
Connected

```

I am wondering if someone running Gutsy can confirm that mplayerplugin will not open any of the above radio links.
 If you can run them, could you post your mplayerplug-in.conf and your mplayer.conf

Thanks Dixon


PS: This is one the best written tutorials I have seen. Thank You

---

### Post by ubuntu-freak on 2008-02-23
> **Virgilius said:**
> P.S: I am getting an error after doing the code after sudo wget that says:
E: Type '--11:07:20--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list when I tried the 
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

 
**gksudo gedit /etc/sources.list** 
 
Make sure "fiesty" is spelt correctly in the medibuntu line and that the spaces are correct. Use the other lines as a guide. Save, and then try adding the key again.
 
This isn't a sound how-to, and I'm no expert in that department. One user did tell me his sound worked after following my how-to though, but I'm not sure why. How long have you been using Ubuntu with no sound? 
 
Anyway, the comprehensive sound guide is [here](http://ubuntuforums.org/showthread.php?t=205449). Don't bother asking the author for help though, he's been silent for over two years now.
 
Nathan

---

### Post by Virgilius on 2008-02-23
I've done the update for the Complete Streaming thing for the first part anyway, and there was a couple of the same "couldn't find errors" on my box for Compiz-manager, w32codecs and the icedtea Java, is it because I haven't got them installed, or is this something else? I did the package by doing what the Medibuntu site said which worked. Now going for the next phase :)

---

### Post by ubuntu-freak on 2008-02-23
Dixon,
 
Thanks for the compliment.
 
Do you think they have mucked up by having two playlists? Might be worth emailing them with the detailed info you posted here, and ask them to correct it. 
 
It's a shame mozilla-mplayer doesn't realise it's another playlist though. Perhaps that is a bug, or a needed feature.
 
Nathan

---

### Post by ubuntu-freak on 2008-02-23
> **Virgilius said:**
> I've done the update for the Complete Streaming thing for the first part anyway, and there was a couple of the same "couldn't find errors" on my box for Compiz-manager, w32codecs and the icedtea Java, is it because I haven't got them installed, or is this something else? I did the package by doing what the Medibuntu site said which worked. Now going for the next phase :)

 
You're running a 64-bit system? Then it will be w64codecs. IcedTea isn't in the same line as w32codecs. If you're running Fiesty, don't worry about ccsm as it's for Gutsy and Hardy. It won't find some packages as they aren't available for Fiesty. Codecs should be though.
 
If you're running a 64-bit system, you should install Gutsy or Hardy.
 
Nathan

---

### Post by Virgilius on 2008-02-24
At the moment I'm upgrading to 7.10. Just hope it helps some.

---

### Post by afeasfaerw23231233 on 2008-02-24
> **reassuringlyoffensive said:**
> That is strange. Try deleting the pluginreg.dat again and restart FF. 
 
Nathan

i am a n00b. please tell me where is that pluginreg.dat? the iplayer playing live is completely malfunction!!!!

---

### Post by bw44 on 2008-02-24
> **dixonstalbert said:**
> I have got mplayer plugin running so I can watch apple.com trailers and CBC (cbc.ca) videos

but it still will not open the CBC radio links.  They used to work a few months ago with Feisty and mplayer plugin 

you can try them at 

[http://www.cbc.ca/radio/]("http://www.cbc.ca/radio/")

I clean re- installed Gutsy yesterday then followed the tutorial on first page of thread.

The problem appears to be that the links point to an asx playlist, which points to another asx playlist , which in turn points to the mms media file. Mplayerplugin inserts the first asx into mplayer with the -playlist switch. Mplayer -playlist then parses the first asx and finds the 2nd asx and tries to play it as a media stream -which it is not- and crashes after it has loaded the file.

What you see on the screen is the embedded player on the screen load the file for a few seconds then report 'stopped'.

here is the debug log file showing mplayer trying to play the 2nd asx playlist file which is not a valid media file:

( . . . debug code output deleted, since I did not replicate it . . .  -- bw44)

I am wondering if someone running Gutsy can confirm that mplayerplugin will not open any of the above radio links.

 If you can run them, could you post your mplayerplug-in.conf and your mplayer.conf

Thanks Dixon

PS: This is one the best written tutorials I have seen. Thank You

Dixon,

Sorry to confirm I get the same symptom as you do -- I regularly watch CBC videos but not the radio streams (since I don't have a TV but do live in Canada!).  And I'm not currently having any problem with the BBC's RealPlayer radio streams.

I couldn't replicate your debug output because I don't know how.  There have been many times when trying to access the BBC site that I've wished I could see what their media player was doing.  Could you post the instructions, or point to a link where they are described?

Thanks is advance.

bw44

---

### Post by Virgilius on 2008-02-24
I have finished upgrading to Gutsy and still I have no sound :( Is there anything else I could do?

---

### Post by dixonstalbert on 2008-02-24
> **bw44 said:**
> Dixon,

I couldn't replicate your debug output because I don't know how.  There have been many times when trying to access the BBC site that I've wished I could see what their media player was doing.  Could you post the instructions, or point to a link where they are described?

Thanks is advance.

bw44

To get debug output:

1. open your mplayerplug-in.conf file

```
gedit $HOME/.mplayer/mplayerplug-in.conf

or if you have multiple users and want them all to use this method for streaming;

gksudo gedit /etc/mplayerplug-in.conf
```


2. add the line

```
debug=2
```

3. close file and close firefox if it is open then delete pluginreg.dat

```
rm $HOME/.mozilla/firefox/pluginreg.dat
```


4. open a terminal and type "firefox".  Unmaximize Firefox window so you can see Firefox window and the terminal window you started it from at the same time. Debug info will print in terminal window as you navigate through media links.


I have found that totem-mozilla in Gutsy has code to successfully navigate through nested asx links, like CBC radio , and will also successfully find media links on Bloomberg.com. 

```
http://www.bloomberg.com/news/av/ 
```



For Gutsy, totem-moxilla  seems to be the much better solution than mplayer-plugin.

---

### Post by dixonstalbert on 2008-02-24
to Virgilius

can you open a terminal window and type

```
gedit /etc/apt/sources.list
```

then copy contents and post here

It sounds like something isnt happy in your sources.list and is preventing you from getting  all the required packages

---

### Post by ubuntu-freak on 2008-02-24
> **Virgilius said:**
> I have finished upgrading to Gutsy and still I have no sound :( Is there anything else I could do?

 
Have you tried a Gutsy Live CD? Sometimes config files won't be changed and drivers loaded unless a fresh install is performed. Try running Gutsy off the CD and see if you get any sound. If not, you should try that comprehensive sound guide and load the drivers yourself.
 
Nathan

---

### Post by ubuntu-freak on 2008-02-24
> **afeasfaerw23231233 said:**
> i am a n00b. please tell me where is that pluginreg.dat? the iplayer playing live is completely malfunction!!!!

 
The command is in the how-to, below the mplayer conf settings. Open the terminal and;
 
**rm $HOME/.mozilla/firefox/pluginreg.dat**
 
Then restart Firefox and try the BBC radio streams again, giving them time to load. 
 
Nathan

---

### Post by bw44 on 2008-02-24
Dixon,

Thanks for posting the instructions for starting the mplayer debug log.

Is the totem-mozilla combination able to negotiate the nested links at the BBC site in embedded mode (within the BBC newsplayer framework) or does totem have to launch stand-alone?

Since I got this far and solved so many problems with Nathan's how-to, I'm reluctant to re-install the first thing he recommends un-installing, namely, totem-mozilla. Glad to hear your opinion though.

bw44

---

### Post by bw44 on 2008-02-24
> **reassuringlyoffensive said:**
> [http://www.linuxjournal.com/node/1005960](http://www.linuxjournal.com/node/1005960)
 
and
 
[https://bugs.launchpad.net/ubuntu/+source/meta-kde/+bug/182786](https://bugs.launchpad.net/ubuntu/+source/meta-kde/+bug/182786)
 
NathanThanks a lot.

---

### Post by ubuntu-freak on 2008-02-24
> **bw44 said:**
> Thanks a lot.

 
No problem. Did you see the next post with the Hardy wiki link?
 
Nathan

---

### Post by Virgilius on 2008-02-24
Okay, done the sources.list and this is what it came up with:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

So apparently my box is like that angry Aussie lady from the Yellowpages ad of "NOT HAPPY, JAN!!"

---

### Post by ubuntu-freak on 2008-02-24
Can anyone confirm if RealPlayer works with FF3? You will have to symlink the plugins folder from FF2 if you're not using Hardy. The troubleshooting section details how to do that.
 
Nathan

---

### Post by ubuntu-freak on 2008-02-24
> **reassuringlyoffensive said:**
> Have you tried a Gutsy Live CD? Sometimes config files won't be changed and drivers loaded unless a fresh install is performed. Try running Gutsy off the CD and see if you get any sound. If not, you should try that comprehensive sound guide and load the drivers yourself.
 
Nathan

 Virgilius,
 
Didn't you see this post? Try the Live CD and see if you get sound. If you just upgrade, you keep lots of the same config files.
 
Nathan

---

### Post by Virgilius on 2008-02-24
I don't have a Gutsy live CD, I upgraded from the Fiesty live CD which I got through Linux Magazine

---

### Post by Virgilius on 2008-02-24
P.s: I am currently downloading Gutsy and planning to burn it off soon :) Did I mention that the "edit post" function is rather dodgy? Hence the spamming.

---

### Post by ubuntu-freak on 2008-02-24
> **Virgilius said:**
> I don't have a Gutsy live CD, I upgraded from the Fiesty live CD which I got through Linux Magazine

 
Can't you download the ISO and make your own?
 
Nathan

---

### Post by dixonstalbert on 2008-02-24
to bw44

yes I can watch BBC video embedded in mozilla-totem, but only at 34kps, the player justs sits there if I try at high speed. 

I can play them at 225kps in standalone realplayer and the quality is much better and they load in 5-10 seconds and not 30-45 seconds.

to virgilius
sources.list looks fine. probably best to run liveCD and see if it is hardware or configuration related...

---

### Post by Virgilius on 2008-02-25
> Can't you download the ISO and make your own?

Nathan Downloading takes time, but since it's done. Anyway, it doesn't take rocket science to learn how to burn an ISO thanks to this: [https://help.ubuntu.com/community/BurningIsoHowto#head-41d485cd1f4a2902492b7e5dcc1991af2ec8f564]("https://help.ubuntu.com/community/BurningIsoHowto#head-41d485cd1f4a2902492b7e5dcc1991af2ec8f564")

---

### Post by afeasfaerw23231233 on 2008-02-25
> **afeasfaerw23231233 said:**
> i am a n00b. please tell me where is that pluginreg.dat? the iplayer playing live is completely malfunction!!!!
bump , no one see my post

---

### Post by ubuntu-freak on 2008-02-25
> **reassuringlyoffensive said:**
> The command is in the how-to, below the mplayer conf settings. Open the terminal and;
 
**rm $HOME/.mozilla/firefox/pluginreg.dat**
 
Then restart Firefox and try the BBC radio streams again, giving them time to load. 
 
Nathan

 
I did reply:-)

---

### Post by afeasfaerw23231233 on 2008-02-25
> **reassuringlyoffensive said:**
> I did reply:-)

thanks. it now works again

---

### Post by ubuntu-freak on 2008-02-25
> **afeasfaerw23231233 said:**
> thanks. it now works again

 
Radio works now yeh? Was an odd problem indeed.
 
Nathan

---

### Post by tobydeemer on 2008-02-25
Hi Nathan-

I'm the confused guy who several pages ago was trying to install win32 codecs on a 64bit distro because I saw something about 32 working on 64 somewhere a long time ago, yadda yadda.... Anyway, after fumbling around like an idiot for a while, I got myself sorted out. And now DVD playback works swimmingly. I've even gotten my chops to the point where I installed xfwm4 into Gnome instead of Metacity, and also just installed xfce as a seperate session environment. But anyway.

So here's my odd thing- all multi-media is working well, except flash. In firefox. I've tried remaking the plugin file as directed in previous posts, but nothing seems to get firefox to handle flash properly. Oddly enough, Epiphany handles flash wonderfully. (And I don't mind using Epiphany as it's worlds faster at loading pages...) But do you have any ideas why this would happen? Is there a particular config setting that I'm missing somewhere?

(Be kind if it's just something simple I forgot to do...)

Thanks,

toby

---

### Post by bw44 on 2008-02-25
> **reassuringlyoffensive said:**
> No problem. Did you see the next post with the Hardy wiki link?
 
NathanNo, I missed your second post with the [https://wiki.ubuntu.com/HardyHeron](https://wiki.ubuntu.com/HardyHeron) link.  Thanks for following up!  It's exactly what I was looking for, though the other links are useful too.   (My ISP seems to be testing their throttling algorithms these days, so I'm getting behind on my reading!)

---

### Post by bw44 on 2008-02-25
> **dixonstalbert said:**
> to bw44

yes I can watch BBC video embedded in mozilla-totem, but only at 34kps, the player justs sits there if I try at high speed. 

I can play them at 225kps in standalone realplayer and the quality is much better and they load in 5-10 seconds and not 30-45 seconds.Dixon,

Then it does sound like I should stick with RealPlayer -- That's a comfort, since everything (video/audio streaming, DVD playback) is as good as I've seen it since moving to Ubuntu from
XP four months ago.

Tnx.

bw44

---

### Post by ubuntu-freak on 2008-02-25
> **tobydeemer said:**
> Hi Nathan-

I'm the confused guy who several pages ago was trying to install win32 codecs on a 64bit distro because I saw something about 32 working on 64 somewhere a long time ago, yadda yadda.... Anyway, after fumbling around like an idiot for a while, I got myself sorted out. And now DVD playback works swimmingly. I've even gotten my chops to the point where I installed xfwm4 into Gnome instead of Metacity, and also just installed xfce as a seperate session environment. But anyway.

So here's my odd thing- all multi-media is working well, except flash. In firefox. I've tried remaking the plugin file as directed in previous posts, but nothing seems to get firefox to handle flash properly. Oddly enough, Epiphany handles flash wonderfully. (And I don't mind using Epiphany as it's worlds faster at loading pages...) But do you have any ideas why this would happen? Is there a particular config setting that I'm missing somewhere?

(Be kind if it's just something simple I forgot to do...)

Thanks,

toby

 
How did you get confused when I have seperate commands for 64-bit users?;-)       

What does FF do when you try to watch a YouTube vid? My troubleshooting section, after part 5, has some tips for getting flash to work. Give them a try.
 
Nathan

---

### Post by afeasfaerw23231233 on 2008-02-26
> **reassuringlyoffensive said:**
> Radio works now yeh? Was an odd problem indeed.
 
Nathan

iplayer works perfectly, video player works in standalone realplayer

---

### Post by Virgilius on 2008-02-26
I tried installing from a downloaded and burned .iso, but it was all screwy, so I setup Fiesty again and went from there to Gutsy, even did a few things from the sticky about sound problems. Nothing works :(

---

### Post by ubuntu-freak on 2008-02-26
> **Virgilius said:**
> I tried installing from a downloaded and burned .iso, but it was all screwy, so I setup Fiesty again and went from there to Gutsy, even did a few things from the sticky about sound problems. Nothing works :(

 
Screwy how? Bit vague. You gave up too easy. Making an install disc works for everyone but you? What happened and what did you burn it with?
 
Nathan

---

### Post by prospero96 on 2008-02-27
Many thanks for your comprehensive discussion of a problem I'm sure a lot of newbies have encountered.  I've got as far as:
gksudo gedit /etc/mplayerplug-in.conf
and pasted the code into it, but find I do not have permissions to save the file.
I am the only user on the system, so what have I done wrong?

---

### Post by Virgilius on 2008-02-27
I used the CD/DVD Writer for GNOME. Could it be the burning speed? Because I did mine at 1X instead of default which is maximum.

---

### Post by ubuntu-freak on 2008-02-27
> **Virgilius said:**
> I used the CD/DVD Writer for GNOME. Could it be the burning speed? Because I did mine at 1X instead of default which is maximum.

 
You didn't say what happened when you tried to boot with the disc. Nothing at all? Burning at 1x should make it even more reliable. I had a problem once where the download didn't complete even though Firefox said it did. Make sure the ISO is about 695mb.
 
Nathan

---

### Post by tobydeemer on 2008-02-27
> **reassuringlyoffensive said:**
> How did you get confused when I have seperate commands for 64-bit users?;-)       

What does FF do when you try to watch a YouTube vid? My troubleshooting section, after part 5, has some tips for getting flash to work. Give them a try.
 
Nathan

Eh, it was late, I was dreary, something like that.... anyway.


Firefox tells me that I don't have the latest flashplayer, but I've tried installing the one it leads me to with a link on youtube's homepage, and that didn't work. I tried remaking the plugin registry file a few times as well. I tried the flash purge/reinstall, and got the same thing. Epiphany handles flash fine, though. So... I dunno.

---

### Post by ubuntu-freak on 2008-02-27
> **tobydeemer said:**
> Eh, it was late, I was dreary, something like that.... anyway.


Firefox tells me that I don't have the latest flashplayer, but I've tried installing the one it leads me to with a link on youtube's homepage, and that didn't work. I tried remaking the plugin registry file a few times as well. I tried the flash purge/reinstall, and got the same thing. Epiphany handles flash fine, though. So... I dunno.

 
Make sure don't have that alternative flash in /usr/lib/firefox/plugins. If you do, just press alt+f2 and enter "gksudo nautilus", then your password. After that you can navigate to the plugins folder again and delete the alternative flash plugin.
 
Nathan

---

### Post by ubuntu-freak on 2008-02-27
> **tobydeemer said:**
> Eh, it was late, I was dreary, something like that.... anyway.


Firefox tells me that I don't have the latest flashplayer, but I've tried installing the one it leads me to with a link on youtube's homepage, and that didn't work. I tried remaking the plugin registry file a few times as well. I tried the flash purge/reinstall, and got the same thing. Epiphany handles flash fine, though. So... I dunno.

 
Make sure don't have that alternative flash in /usr/lib/firefox/plugins. If you do, just press alt+f2 and enter "gksudo nautilus", then your password. After that you can navigate to the plugins folder again and delete the alternative flash plugin.
 
Nathan

---

### Post by ubuntu-freak on 2008-02-28
How does RealPlayer fair in Hardy with Firefox 3?
 
Nathan

---

### Post by harambe on 2008-02-29
An excellent article - many thanks - one less reason to move back to Windows.

---

### Post by ubuntu-freak on 2008-02-29
> **harambe said:**
> An excellent article - many thanks - one less reason to move back to Windows.

 
Thanks for your comments. Great to get feedback.
 
Nathan

---

### Post by Virgilius on 2008-02-29
Ubuntu Gutsy had problems loading up and spat the dummy. I reinstalled from Fiesty and upgraded through the Update Manager. It could be the driver for the motherboard though, since I haven't found any for this one: GA-K8N SLI.

---

### Post by ubuntu-freak on 2008-02-29
> **Virgilius said:**
> Ubuntu Gutsy had problems loading up and spat the dummy. I reinstalled from Fiesty and upgraded through the Update Manager. It could be the driver for the motherboard though, since I haven't found any for this one: GA-K8N SLI.

 
Why would it be your motherboard? You could try installing with the alternative ISO. Also, if you still have Windows, you could try installing Hardy alpha 5 with Wubi. It lets you install Ubuntu in Windows as if it's just a program. 
 
Nathan

---

### Post by Airforcefalco on 2008-03-01
I have Gutsy and when i typed in the command line

sudo apt-get install alsa-oss compizconfig-settings-manager faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll icedtea-java7-jre icedtea-java7-plugin liblame0 msttcorefonts unrar w64codecs

it came back with 

E: Couldn't find package gstreamer0.10-pitfdll

I dont know how to edit a command line yet but i was hoping someone could help me out!

Thank you!

P.S. Can someone explain to me what all that stuff means anyway?

---

### Post by ubuntu-freak on 2008-03-01
> **Airforcefalco said:**
> I have Gutsy and when i typed in the command line

sudo apt-get install alsa-oss compizconfig-settings-manager faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll icedtea-java7-jre icedtea-java7-plugin liblame0 msttcorefonts unrar w64codecs

it came back with 

E: Couldn't find package gstreamer0.10-pitfdll

I dont know how to edit a command line yet but i was hoping someone could help me out!

Thank you!

P.S. Can someone explain to me what all that stuff means anyway?

 
Is that the only one it couldn't find? That's really strange. If you had an apt list problem there would be more than one package missing. It should be in the universe repo, search google and it will bring up the Ubuntu packages page which confirms it.
 
Nathan

---

### Post by Airforcefalco on 2008-03-01
> **reassuringlyoffensive said:**
> Is that the only one it couldn't find? That's really strange. If you had an apt list problem there would be more than one package missing. It should be in the universe repo, search google and it will bring up the Ubuntu packages page which confirms it.
 
Nathan

How do i search for it? I'm a linux noob :-(

---

### Post by Airforcefalco on 2008-03-01
> **Airforcefalco said:**
> How do i search for it? I'm a linux noob :-(

I do know how to use google but i just dont know what i am searching for.

---

### Post by mc4man on 2008-03-01
your searching for this  ```
gstreamer0.10-pitfdll
```
try searching in synaptic and see if it shows - if so install and then rerun orig. command  (if needed)

---

### Post by Airforcefalco on 2008-03-01
Well i searched in Synaptic and i found nothing.

I ubuntu package searched and this is what i got

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=gutsy&release=all&keywords=gstreamer0.10-pitfdll&sourceid=mozilla-search]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=gutsy&release=all&keywords=gstreamer0.10-pitfdll&sourceid=mozilla-search")

---

### Post by Airforcefalco on 2008-03-01
It says i386 and i think that has to deal with the processor but i have an Opteron which is kind of both 32 and 64 bit but i am running the 64 bit ubuntu so i am not sure if that will work.

---

### Post by mc4man on 2008-03-01
there is no gstreamer0.10-pitfdll for 64 bit - I'd remove it from the command
I'd also defer to nathan for further instructions as he knows this much better

---

### Post by ubuntu-freak on 2008-03-01
> **mc4man said:**
> there is no gstreamer0.10-pitfdll for 64 bit - I'd remove it from the command
I'd also defer to nathan for further instructions as he knows this much better

 
Ahh that explains it. Unusual for them to not package one for 64-Bit. 
 
Nathan

---

### Post by Airforcefalco on 2008-03-01
> **mc4man said:**
> there is no gstreamer0.10-pitfdll for 64 bit - I'd remove it from the command
I'd also defer to nathan for further instructions as he knows this much better

I dont know how to do that can anyone help me with that?

---

### Post by mc4man on 2008-03-01
```
sudo apt-get install alsa-oss compizconfig-settings-manager faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse icedtea-java7-jre icedtea-java7-plugin liblame0 msttcorefonts unrar w64codecs
```
You would just paste com.  into a new text document and then delete the offending part as above
note: I don't use totem or 64 bit os  - would only guess the above is appro for 64 bit

edit; older thread  [http://ubuntuforums.org/archive/index.php/t-570214.html](http://ubuntuforums.org/archive/index.php/t-570214.html)
bug report [https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-pitfdll/+bug/172258](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-pitfdll/+bug/172258)

---

### Post by ubuntu-freak on 2008-03-01
> **Airforcefalco said:**
> I dont know how to do that can anyone help me with that?

 
I doubt you have to do anything, it will just skip whatever it can't install. I've edited the command now anyway.
 
By the way, to remove a package from a command you don't want to install, you can just delete it in the Terminal with the arrow and delete keys, just make sure you move the cursor back to the end of the line again before pressing enter. Also, you can just cut & paste the packages you want of course. 
 
Nathan

---

### Post by mc4man on 2008-03-01
OT - > you can just delete it in the Terminal with the arrow and delete keys
learn something new every day - thanks

---

### Post by anaconda on 2008-03-02
> **reassuringlyoffensive said:**
> **REVISED ON 25 FEB 2008**
 
[COLOR=red]**IMPORTANT:**[/COLOR] If you haven't already, you need to enable the medibuntu repo. These commands are aimed at Gutsy users, so if you are using a different version of Ubuntu, please edit the first command in your Terminal and change it from "gutsy" to whatever version you are running. 
 
**sudo wget [noparse]http://www.medibuntu.org/sources.list.d/gutsy.list[/noparse] -O /etc/apt/sources.list.d/medibuntu.list**
 
**wget -q [noparse]http://packages.medibuntu.org/medibuntu-key.gpg[/noparse] -O- | sudo apt-key add - && sudo apt-get update**
 

Medibuntu repository for Hardy (8.04) EXISTS, but currently the wget command above (with gutsy changed to hardy) doesnt work! , because there isnt anything behind:
**[noparse]http://www.medibuntu.org/sources.list.d/hardy.list [/noparse]**
(and I understood that there wont be hardy.list before the official release date!!)

instead you have to manually add these lines to the end of your /etc/apt/sources.list -file and then run the second wget command, which gets the gpg keys and updates apt-get.
[B]
## Medibuntu - Ubuntu 8.04 "hardy"
## Please report any bug on  [noparse]https://bugs.launchpad.net/medibuntu/[/noparse]
deb  [noparse]http://packages.medibuntu.org/[/noparse] hardy free non-free
[/B]

PS. thanks for this excellent quide!
PSS. didn't read throuhg all posts, so, if someone already mentioned this. Sorry for repeating.

---

### Post by ubuntu-freak on 2008-03-02
> **anaconda said:**
> Medibuntu repository for Hardy (8.04) EXISTS, but currently the wget command above (with gutsy changed to hardy) doesnt work! , because there isnt anything behind:
**[noparse]http://www.medibuntu.org/sources.list.d/hardy.list [/noparse]**
(and I understood that there wont be hardy.list before the official release date!!)

instead you have to manually add these lines to the end of your /etc/apt/sources.list -file and then run the second wget command, which gets the gpg keys and updates apt-get.
[B]
## Medibuntu - Ubuntu 8.04 "hardy"
## Please report any bug on  [noparse]https://bugs.launchpad.net/medibuntu/[/noparse]
deb  [noparse]http://packages.medibuntu.org/[/noparse] hardy free non-free
[/B]

PS. thanks for this excellent quide!
PSS. didn't read throuhg all posts, so, if someone already mentioned this. Sorry for repeating.

 
Thanks for the info and positive feedback.
 
Nathan

---

### Post by bw44 on 2008-03-02
Just a minor note, for anyone who has followed Nathan's how-to to improve their visits to the BBC news site using RealPlayer (among many other things).

Within the last couple of days, most of the news videos have begun to play in embedded mode (within the BBC's "News Player"). I'm 99.9% sure this improvement occurred because of something BBC did, not a change in my configuration.  Hope it's working for other users.

bw44

---

### Post by ubuntu-freak on 2008-03-03
Made some changes to part 1 and 4. Added instructions for Hardy Heron alpha users so they can add the Medibuntu repo manually, and I've also added a sound conversion section to part 4.
 
Nathan

---

### Post by bw44 on 2008-03-03
> **reassuringlyoffensive said:**
> Made some changes to part 1 and 4. Added instructions for Hardy Heron alpha users so they can add the Medibuntu repo manually, and I've also added a sound conversion section to part 4.
 
Nathan
Nathan,

When Hardy Heron is officially released will it likely be required to modify parts of the How-to?  I don't have enough experience with Linux to have any idea how many of the problems your How-to solves in 7.10 (and earlier releases) might be fixed in 8.04. (I've got other issues with 7.10 I'm hoping will get solved!)

I guess we could see how many of the problems have been fixed by just trying everything we do under a vanilla 8.04 install.  But if something still doesn't work under 8.04, can we just apply your recommended action again?

I guess I'm asking: will it be necessary, and will you have time to check out your How-to under 8.04? (he said, hopefully! :) )

bw44

---

### Post by ubuntu-freak on 2008-03-03
> **bw44 said:**
> Nathan,

When Hardy Heron is officially released will it likely be required to modify parts of the How-to?  I don't have enough experience with Linux to have any idea how many of the problems your How-to solves in 7.10 (and earlier releases) might be fixed in 8.04. (I've got other issues with 7.10 I'm hoping will get solved!)

I guess we could see how many of the problems have been fixed by just trying everything we do under a vanilla 8.04 install.  But if something still doesn't work under 8.04, can we just apply your recommended action again?

I guess I'm asking: will it be necessary, and will you have time to check out your How-to under 8.04? (he said, hopefully! :) )

bw44

 
Hey again,
 
What problems do you want fixing? My how-to just enables all multimedia, has a few tips and offers an alternative streaming method. Some users are happy with the Totem or Xine browser plugins.
 
The Ubuntu version is mostly irrelevant, it's just those packages with version numbers in the name we have to watch out for.
 
Nathan

---

### Post by bw44 on 2008-03-03
> **reassuringlyoffensive said:**
> Hey again,
 
What problems do you want fixing? My how-to just enables all multimedia, has a few tips and offers an alternative streaming method. Some users are happy with the Totem or Xine browser plugins.
 
The Ubuntu version is mostly irrelevant, it's just those packages with version numbers in the name we have to watch out for.
 
Nathan

Thanks.  I didn't know that that the Ubuntu version was mostly irrelevant.  When I look at the Synaptic package list they all seem to have version numbers.  Like I said, I don't have a lot of experience with new Ubuntu software releases. I was wondering if the new version might enable more multimedia, alternative streaming method(s), and might change the default browser plugins (or something).  For example, I was reading the 8.04 alpha release notes you pointed us to, and noticed that the default CD burning software was changing to Brasero and  Firefox will be at release 3.0 (beta).  Weren't you asking the other day how Flash was working with FF 3?  So I assumed that there were issues.

---

### Post by ubuntu-freak on 2008-03-03
> **bw44 said:**
> Thanks.  I didn't know that that the Ubuntu version was mostly irrelevant.  When I look at the Synaptic package list they all seem to have version numbers.  Like I said, I don't have a lot of experience with new Ubuntu software releases. I was wondering if the new version might enable more multimedia, alternative streaming method(s), and might change the default browser plugins (or something).  For example, I was reading the 8.04 alpha release notes you pointed us to, and noticed that the default CD burning software was changing to Brasero and  Firefox will be at release 3.0 (beta).  Weren't you asking the other day how Flash was working with FF 3?  So I assumed that there were issues.

 
Nah, I wondered how RealPlayer was working with Firefox 3. 
 
Ubuntu will never, ever have proprietary codecs installed by default. Totem is the default movie player, that's why totem-mozilla is the default browser plugin. It will only get better anyway, I just like how configurable the MPlayer plugin is.
 
Nathan

---

### Post by crossface on 2008-03-03
Thanks,  I followed your directions for Mplayer to the "t". I run 32 bit gutsy even though I have 64 bit computer. But alas, didn't work. My problem is MLB baseball video. I works fine with VLC plug-in but not with Mplayer. Mplayer video plays but in its own window and will not go full screen, stays in its own little box, vlc expands (double click) to full screen.

---

### Post by ubuntu-freak on 2008-03-03
> **crossface said:**
> Thanks,  I followed your directions for Mplayer to the "t". I run 32 bit gutsy even though I have 64 bit computer. But alas, didn't work. My problem is MLB baseball video. I works fine with VLC plug-in but not with Mplayer. Mplayer video plays but in its own window and will not go full screen, stays in its own little box, vlc expands (double click) to full screen.

 
Not all sites will work perfectly, doesn't mean you can claim the MPlayer plugin "doesn't work". When I first read that I thought streaming wasn't working for you at all. Did it not give you the option to go fullscreen?
 
Try editing the MPlayer config file and change the "noembed" value to "1", then use that rm command to delete the pluginreg.dat. Hopefully you can make it go fullscreen then.
 
Nathan

---

### Post by bw44 on 2008-03-04
> **reassuringlyoffensive said:**
> . . . Ubuntu will never, ever have proprietary codecs installed by default. Totem is the default movie player, that's why totem-mozilla is the default browser plugin. It will only get better anyway, I just like how configurable the MPlayer plugin is.
 
NathanSo, much of the how-to is to help install things that are proprietary and will be needed in 8.04 and any future release.  And the other stuff is just a matter of what currently seems to work better, and/or your preferences.

I guess this was obvious to most people from the beginning, but I didn't get it.  Guess I'm slow :(  -- thanks for explaining.

bw44

---

### Post by ubuntu-freak on 2008-03-04
> **bw44 said:**
> So, much of the how-to is to help install things that are proprietary and will be needed in 8.04 and any future release.  And the other stuff is just a matter of what currently seems to work better, and/or your preferences.

I guess this was obvious to most people from the beginning, but I didn't get it.  Guess I'm slow :(  -- thanks for explaining.

bw44

 
It's like I said before, I just couldn't understand why info and tips were scattered everywhere in various different threads, and lot's of misinformation being given out. People installing mozilla-mplayer and wondering why it didn't work for them, they were only given part of the info they needed. Same with multimedia and video codecs, you need more than just the restricted-extras package. So when I moved from Debian Sid to Ubuntu, I decided to just share exactly how I set everything up.
Actually, to start with it was just a basic streaming how-to, but I just kept adding to it and had one of the forum staff rename the thread. I'm probably just obsessive and that's why it had to be so complete.
 
Nathan

---

### Post by TorqueyPete on 2008-03-04
Uncle Nathan!
I think I've messed up! 
:rolleyes:


 While going through the 'How To' , just to make sure I was up to date with it, I have added the Hardy Heron repositories because I'm a dummy, and just copied and pasted stuff into the terminal without really checking! LOL ! Well I'm usually doing this late at night, when dozyness runs rampant! 
 Hopefully this is all that's causing my current problems. ;)
 As Youtube is freezing Firefox, and eventually crashing it, and none of the Real Player test vids play, and some of BBC vids refuse to start.
 Can I undo the Hardy stuff?

---

### Post by ubuntu-freak on 2008-03-05
> **TorqueyPete said:**
> Uncle Nathan!
I think I've messed up! 
:rolleyes:


 While going through the 'How To' , just to make sure I was up to date with it, I have added the Hardy Heron repositories because I'm a dummy, and just copied and pasted stuff into the terminal without really checking! LOL ! Well I'm usually doing this late at night, when dozyness runs rampant! 
 Hopefully this is all that's causing my current problems. ;)
 As Youtube is freezing Firefox, and eventually crashing it, and none of the Real Player test vids play, and some of BBC vids refuse to start.
 Can I undo the Hardy stuff?

 
Hmmm. You sure you added the Hardy Medibuntu repo? You had to manually open /etc/apt/sources.list to add it. If you removed the pluginreg.dat then RM streams should work. Flash isn't in the Medibuntu repo, so I doubt that caused it.
 
Have a good look at the troubleshooting section.
 
Nathan

---

### Post by anaconda on 2008-03-05
> **reassuringlyoffensive said:**
> Hmmm. You sure you added the Hardy Medibuntu repo? You had to manually open /etc/apt/sources.list to add it. If you removed the pluginreg.dat then RM streams should work. Flash isn't in the Medibuntu repo, so I doubt that caused it.

found a typo! This problem may be related to it..

> sudo gedit etc/apt/sources.list
should be
sudo gedit /etc/apt/sources.list

I haven't had any problems with hardys medibuntu repo. (And even hardy has worked like a dream..)

---

### Post by Canux08 on 2008-03-05
Hi, 

I've followed the guide and I can get streaming video from Apple's movie trailer website to work fine in Firefox using the Mplayer plug-in - if I have visual effects turned off. If Ubuntu's effects are on "normal" or "extra" I get a black screen and only the audio plays. I've tried switching the video output from xv to GL to X11, but it has no effect. 

Any suggestions? I'm using a Dell Latitude D610 with an ATI M300 video card.

---

### Post by Canux08 on 2008-03-05
Figured out how to disablle compiz video playback by using Advanced Desktop Effects Settings. Now streaming video works perfect.

---

### Post by ubuntu-freak on 2008-03-05
> **Canux08 said:**
> Figured out how to disablle compiz video playback by using Advanced Desktop Effects Settings. Now streaming video works perfect.

 
Did desktop videos play okay? Your card isn't blacklisted, so it should work alright with Compiz. If you want effects, you can use x11 instead of xvideo in MPlayer's preferences, but that means your CPU will be doing all of the work instead of the GPU. Or you can just use x11 in the browser by using the "vo=x11" option in MPlayer's plugin config file.
 
Nathan

---

### Post by ubuntu-freak on 2008-03-05
> **anaconda said:**
> found a typo! This problem may be related to it..


should be
sudo gedit /etc/apt/sources.list

I haven't had any problems with hardys medibuntu repo. (And even hardy has worked like a dream..)

 
Thanks for that. I've corrected it now.
 
That wouldn't be causing his problem though, it would have no effect. He must have added Medibuntu with the "wget" commands anyway.

Nathan

---

### Post by impert on 2008-03-06
Hi to all, and thanks to reassuringlyoffensive for the how-to, which seems to have helped a lot of people.

I've tried to follow it religiously, but so far I haven't had much joy. I'm running Ubuntu Gutsy 64-bit (at least I presume it's 64-bit) on an AMD 64 3700+. Some time ago I installed Swiftweasel 32 using Kilz's how-to. SW works well for me except for video/streaming. Firefox is still there and also works.

I started by following the instructions for 64-bit. No luck. Tried installing  RealPlayer, no luck. (It seemed to open and then close immediately). Removed it.

Then I decided to try the 32-bit instructions, and installed the 32-bit packages (without removing the 64-bit ones.) Still no luck.

I've tried fiddling with the settings in  mplayerplugin.config.

Mplayer shows up in the Firefox about.plugins file, but not in the Swiftweasel one, though I've tried to make a symlink to it. ("Cannot overwrite file" or "File exists", depending on whether I use ln -s or ln -sf. Haven't tried sudoing it for fear of breaking something)

On the Apple site I got two videos to work of the dozen or so that that I tried.
The others either say additional plugins required, or no video, after a long wait. On the BBC site Mplayer opens a box and then stops. Same for "stand alone"
On the ABC ([http://abc.net.au](http://abc.net.au)) some things run, some run and then stop, some won't start, and sometimes I get three audio files opening with a slight time lapse, and no picture. Small screen only when I do get something.

Q1	Should I be using the 64-bit or the 32-bit instructions?
Q2	Should I remove all the packages of the other set?
Q3	Should I try another  32-bit browser? FF or Icecat or something?
Q4	Is it possible to use RealPlayer on this machine? Add/Remove and Synaptic don't think so, but can it be done with alien or nsdwrapper or something? A small addition to the how-to here would be most welcome. RealPlayer works well on the Mac.
Q5	Have other AMD 64 users had more success? Is all this just due to my unique combination of ignorance and stupidity, or should I get an Intel box?

Sorry to bother you with this, but I've been at it for a while, and seem to be getting nowhere. Thanks in anticipation.

---

### Post by ubuntu-freak on 2008-03-06
> **impert said:**
> Hi to all, and thanks to reassuringlyoffensive for the how-to, which seems to have helped a lot of people.

I've tried to follow it religiously, but so far I haven't had much joy. I'm running Ubuntu Gutsy 64-bit (at least I presume it's 64-bit) on an AMD 64 3700+. Some time ago I installed Swiftweasel 32 using Kilz's how-to. SW works well for me except for video/streaming. Firefox is still there and also works.

I started by following the instructions for 64-bit. No luck. Tried installing  RealPlayer, no luck. (It seemed to open and then close immediately). Removed it.

Then I decided to try the 32-bit instructions, and installed the 32-bit packages (without removing the 64-bit ones.) Still no luck.

I've tried fiddling with the settings in  mplayerplugin.config.

Mplayer shows up in the Firefox about.plugins file, but not in the Swiftweasel one, though I've tried to make a symlink to it. ("Cannot overwrite file" or "File exists", depending on whether I use ln -s or ln -sf. Haven't tried sudoing it for fear of breaking something)

On the Apple site I got two videos to work of the dozen or so that that I tried.
The others either say additional plugins required, or no video, after a long wait. On the BBC site Mplayer opens a box and then stops. Same for "stand alone"
On the ABC ([http://abc.net.au](http://abc.net.au)) some things run, some run and then stop, some won't start, and sometimes I get three audio files opening with a slight time lapse, and no picture. Small screen only when I do get something.

Q1	Should I be using the 64-bit or the 32-bit instructions?
Q2	Should I remove all the packages of the other set?
Q3	Should I try another  32-bit browser? FF or Icecat or something?
Q4	Is it possible to use RealPlayer on this machine? Add/Remove and Synaptic don't think so, but can it be done with alien or nsdwrapper or something? A small addition to the how-to here would be most welcome. RealPlayer works well on the Mac.
Q5	Have other AMD 64 users had more success? Is all this just due to my unique combination of ignorance and stupidity, or should I get an Intel box?

Sorry to bother you with this, but I've been at it for a while, and seem to be getting nowhere. Thanks in anticipation.


Did you install Ubuntu yourself? Surely you would remember if it's the 64-Bit version or not. Go to System>About and it should tell you. Or type "cat /etc/issue" in the Terminal.

Another thing, the how-to clearly states that RealPlayer is a 32-Bit application, so I'm not sure why you tried to install it. You installed both 32-Bit and 64-Bit packages? That means you have two different Java plugins installed, they will clash for starters. Goodness knows what else will clash. You shouldn't have to use a 32-Bit browser on a 64-Bit system anymore. Remove the 32-Bit applications by copying the install lines again and use "sudo apt-get remove" instead of "install". Then edit MPlayer's plugin config file and change the values of "rm", "smil" and "helix" to "1" so that  MPlayer can stream Real Media for you. Then use the command to remove the pluginreg.dat. Reboot for good measure.

Hopefully that will sort things out.

Nathan

P.S. You can't make a symlink to anywhere except your own account if you don't use "sudo".

---

### Post by impert on 2008-03-06
Thanks for the quick response.

 cat /etc/issue
Ubuntu 7.10 \n \l
I installed it myself and did not try to make it 32-bit, just clicked on a button called i386_amd64 in the download page, if my memory serves. I can't find anything that explicitly says 64-bit though.
From a var/log I get: 
 Mar  6 kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 02:46:46 UTC 2008 (Ubuntu 2.6.22-14.52-generic)

I'll do as you say and get back to you

---

### Post by impert on 2008-03-06
> **reassuringlyoffensive said:**
> 

Another thing, the how-to clearly states that RealPlayer is a 32-Bit application, so I'm not sure why you tried to install it. You installed both 32-Bit and 64-Bit packages? That means you have two different Java plugins installed, they will clash for starters. Goodness knows what else will clash. You shouldn't have to use a 32-Bit browser on a 64-Bit system anymore. Remove the 32-Bit applications by copying the install lines again and use "sudo apt-get remove" instead of "install". Then edit MPlayer's plugin config file and change the values of "rm", "smil" and "helix" to "1" so that  MPlayer can stream Real Media for you. Then use the command to remove the pluginreg.dat. Reboot for good measure.

Hopefully that will sort things out.

Nathan

P.S. You can't make a symlink to anywhere except your own account if you don't use "sudo".

Well, I've done as you said, and things still aren't right.
On the BBC site, mplayer downloads and then stops.Trying stand-alone doesn't help.
I can get one or two of the Apple trailers, most just give a blank screen with "no video"
On the ABC, it varies, some things work, some start and then stop, some don'"t start.

At the time I installed Swiftweasel 32 it was the only way to get Flash. I tried RealPlayer because  I wasn't having any luck with Mplayer, and because I started to think that maybe, since I was using SW 32, I counted as a 32-bit user. I did quite a bit of thrashing around, I probably got the sequence of events wrong in the last post. Basically I wasn't sure what class of user I was. Perhaps there are others out there as dopey as me.

If you don't have a better idea, I think I'll remove the 64-bit stuff as well, and then re-install it, ie do the whole thing from square one.

Thanks for your help. Cheers.

---

### Post by ubuntu-freak on 2008-03-06
> **impert said:**
> Thanks for the quick response.

 cat /etc/issue
Ubuntu 7.10 \n \l
I installed it myself and did not try to make it 32-bit, just clicked on a button called i386_amd64 in the download page, if my memory serves. I can't find anything that explicitly says 64-bit though.
From a var/log I get: 
 Mar  6 kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 02:46:46 UTC 2008 (Ubuntu 2.6.22-14.52-generic)

I'll do as you say and get back to you

 
Yeah sounds like it's 64-Bit. I think if you just remove all the Sun Java packages you will be okay. Most apps will share the same name, and w32codecs won't be in your repo anyway. Don't think I was thinking straight earlier, Java is the only real conflict you have.
 
Does streaming work in Firefox? Should do after you remove the pluginreg.dat. Then use the 64-Bit Swiftfox if you want. Is it really that much faster than Firefox though?
 
Nathan

---

### Post by ubuntu-freak on 2008-03-06
Apple.com should be perfect. Did you try both WMV and RM at the BBC site? RM radio also sounds better than WMA, and worked with MPlayer. 
 
You could try removing mozilla-mplayer, then try the vlc plugin or maybe the xine-plugin. Make sure you delete the pluginreg.dat whenever you change plugins. The xine plugin will require totem-xine, libxine-ffmpeg, libxine-extracodecs etc (see the Kubuntu essential command). VLC plugin needs VLC of course.
 
Nathan

---

### Post by impert on 2008-03-06
Sorry for the delay in replying, dinner got in the way.
I re-installed Java, and made xv the preference in Mplayer.

I am getting some results now. I got the BBC news, complete with sound, using the WMV setting. The quality is a bit underwhelming, but that may be the Beeb's fault. I had to force it to quit when it locked up after I tried to change video.

The Apple site is certainly no better, and tends to close when I do anything daring (like click on a tab, for instance).

The ABC has been funny - the main news works, but the other links have no sound or stop.I'll work through your troubleshooting section. I've still got rather a lot of plugins in the about.plugins, perhaps some need to go.

---

### Post by impert on 2008-03-06
Item 7 on the troubleshooting list:

I got this:
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

I've tried it several times. Also for some reason alsa-oss was missing. I'll keep on.

---

### Post by ubuntu-freak on 2008-03-06
The older version of Adobe Flash will work better anyway. Use Kilz recommended [script](http://ubuntuforums.org/showthread.php?t=476924&highlight=gnash). You uninstalled the Sun Java plugin yeah? IcedTea's plugin should work.
 
Nathan

---

### Post by TorqueyPete on 2008-03-06
> **impert said:**
>  Perhaps there are others out there as dopey as me.


Hi there. ):P

---

### Post by impert on 2008-03-07
> **reassuringlyoffensive said:**
> The older version of Adobe Flash will work better anyway. Use Kilz recommended [script](http://ubuntuforums.org/showthread.php?t=476924&highlight=gnash). You uninstalled the Sun Java plugin yeah? IcedTea's plugin should work.
 
Nathan

Thanks for the reply.

Definite progress here. I followed Kilz' instructions and Flash seems to have installed itself correctly.
Sun java's gone, IcedTea is installed.

BBC and the ABC seem to work well, though the ABC stuff didn't want to go full screen.

On the Apple site, choosing a video caused Firefox to close. I can live without the crap Apple offer, but I'd like to get things working as they're supposed to.
I suppose Apple use Quicktime. According to  about.plugins, the VLC, Totem, and MPlayerplugins are all enabled for Qt, so this is probably the trouble. (?) I'll see if I can't sort this out.

TorqueyPete, I can stuff mine up without even trying. Pleasedtameetcha, anyway.

---

### Post by ubuntu-freak on 2008-03-07
> **impert said:**
> Thanks for the reply.

Definite progress here. I followed Kilz' instructions and Flash seems to have installed itself correctly.
Sun java's gone, IcedTea is installed.

BBC and the ABC seem to work well, though the ABC stuff didn't want to go full screen.

On the Apple site, choosing a video caused Firefox to close. I can live without the crap Apple offer, but I'd like to get things working as they're supposed to.
I suppose Apple use Quicktime. According to  about.plugins, the VLC, Totem, and MPlayerplugins are all enabled for Qt, so this is probably the trouble. (?) I'll see if I can't sort this out.

TorqueyPete, I can stuff mine up without even trying. Pleasedtameetcha, anyway.

 
Glad you're getting there.
 
You don't have the Totem and VLC plugin installed along with the MPlayer plugin do you? They will conflict with each other. If you have, remove them and delete the pluginreg.dat again. If you want try other plugins, you can only have one installed at a time (except for RealPlayer on a 32-Bit system with the MPlayer plugin).
 
Nathan

---

### Post by impert on 2008-03-07
> Glad you're getting there.


Er, well, I thought I was!

> You don't have the Totem and VLC plugin installed along with the MPlayer plugin do you? They will conflict with each other. If you have, remove them and delete the pluginreg.dat again. If you want try other plugins, you can only have one installed at a time (except for RealPlayer on a 32-Bit system with the MPlayer plugin).

I've just removed them using Synaptic. Since then FF has gone flaky, and I've got no picture with Mplayer. Gotta go out now, but I think I might try a reinstall of Firefox. 

Thanks again for your trouble

BTW would it be worth putting a little note in your how-to saying "if you're using a 32- bit browser on a 64-bit system don't do what that idiot Impert did,  go to Kilz' site and change back to 64-bit" or words to that effect?  It is possible to be confused, honest. 
(Not easy to make things foolproof in the literal sense, is it?)

Cheers.

---

### Post by ubuntu-freak on 2008-03-07
> **impert said:**
> Er, well, I thought I was!


I've just removed them using Synaptic. Since then FF has gone flaky, and I've got no picture with Mplayer. Gotta go out now, but I think I might try a reinstall of Firefox. 

Thanks again for your trouble

BTW would it be worth putting a little note in your how-to saying "if you're using a 32- bit browser on a 64-bit system don't do what that idiot Impert did,  go to Kilz' site and change back to 64-bit" or words to that effect?  It is possible to be confused, honest. 
(Not easy to make things foolproof in the literal sense, is it?)

Cheers.

Just incase, try these commands again;

**sudo apt-get remove totem-mozilla mozilla-plugin-vlc xine-plugin kaffeine-mozilla helix-player mozilla-helix-player**

**sudo apt-get install mplayer mozilla-mplayer**

**rm $HOME/.mozilla/firefox/pluginreg.dat **

Nathan

---

### Post by Kivech on 2008-03-07
Thanks a ton for this post, now I can watch DVDs without messing up my other streaming media.

Great guide!

Kivech

---

### Post by ubuntu-freak on 2008-03-07
> **Kivech said:**
> Thanks a ton for this post, now I can watch DVDs without messing up my other streaming media.

Great guide!

Kivech

 
Thanks. :-)
 
How did it mess up streaming before? Curious.
 
Nathan

---

### Post by impert on 2008-03-07
Hi 
Did a reinstall with Synaptic of firefox, Mplayer, Mplayer plugin. 
Ran apt-get autoclean apt-get autoremove, and apt-get check.


> **reassuringlyoffensive said:**
> Just incase, try these commands again;

**sudo apt-get remove totem-mozilla mozilla-plugin-vlc xine-plugin kaffeine-mozilla helix-player mozilla-helix-player**

**sudo apt-get install mplayer mozilla-mplayer**

**rm $HOME/.mozilla/firefox/pluginreg.dat **

Nathan

Tried that, still no joy. (No files removed  'cos they had already gone.)

On the BBC I get Mplayer starting and then stopping. If I  press the "play" button repeatedly the download bar slooowwly fills up. Sometimes get sound, sometimes not. Firefox has a tendency to hang or to keep running after the window has gone when I hit the close button.
Had to kill it and restart just now to reply to you.

On the Apple site I get sound, no picture; These are .mov files.
The ABC works; it's Flash.
On the Mac I'd be frantically repairing permissions, running fsck, and zapping the PRAM. That's all automated with Ubuntu, isn't it?

Thanks again for the trouble

---

### Post by bw44 on 2008-03-07
> **impert said:**
> On the BBC I get Mplayer starting and then stopping. If I  press the "play" button repeatedly the download bar slooowwly fills up. Sometimes get sound, sometimes not. Firefox has a tendency to hang or to keep running after the window has gone when I hit the close button.
Had to kill it and restart just now to reply to you.

I've no experience with a 64-bit system, but on my 32-bit, even after following Nathan's how-to as it concerns mplayer, you have described exactly how my Firefox + mplayer combo fails to work with BBC videos.  That's why I followed his further advice and switched to RealPlayer.  Unfortunately, I gather that option isn't available to you as a 64-bit user.

One thing you could try (if you haven't already) is setting the the following  mplayerplug-in.conf file settings to

enable-rm=1
enable-smil=1
enable-helix=1

(Nathan: did I get them all?) Then do the $ rm pluginreg.dat command to reset Firefox's plugins and change your BBC News Player Preferences setting at their site to RealPlayer.  I haven't actually tried this (don't want my access to BBC to break!), but it might work, given that BBC has recently changed something and improved imbedded RealPlayer functionality (as I experience it anyway).  It's worth a try.

However, remember one thing: BBC has not, in the past, demonstrated a very high commitment to making their news site work well for Linux users.  I would test your mplayer functionality against a site like [http://www.linspire.com/products_linspire_whatis.php?tab=compatibility](http://www.linspire.com/products_linspire_whatis.php?tab=compatibility) (try their Video Compatabiity and other tests).  DON'T use BBC as a test site -- they are constantly fiddling with their system (and gradually making improvements) but may give you  inconsistent results when you haven't changed anything.

Best of luck!

---

### Post by impert on 2008-03-07
Thanks bw44,
The /etc/mplayerplug-in.conf is already as you suggest, and I've zapped the pluginreg.dat file so often the r and m keys are losing their letters. I'll give your site a try.

I'm going to go and paint a wall or two for a change. After that I'll go back and do all the steps in Nathan's how-to again.

Funny that I got the BBC well when I had the Totem and VLC plugins installed as well as the MPlayer ones. It should have been a real no-no.

Cheers

---

### Post by bw44 on 2008-03-07
> **impert said:**
> The /etc/mplayerplug-in.conf is already as you suggest, and I've zapped the pluginreg.dat file so often the r and m keys are losing their letters. I'll give your site a try.

I'm going to go and paint a wall or two for a change. After that I'll go back and do all the steps in Nathan's how-to again.

Funny that I got the BBC well when I had the Totem and VLC plugins installed as well as the MPlayer ones. It should have been a real no-no.

Sorry I didn't provide the magic bullet.  Painting walls should definitely be more satisfying than trying to get the BBC site to work!

Your last comment is interesting, too.  I never figured out how Firefox resolves conflicting plugins (or why it seemed to allow them to get installed in the first place). I definitely had to remove Totem's plugin to get mplayer working, but I never had the VLC plugin installed.  (VLC is my preferred DVD player though.)

*Better* luck in the next round!

---

### Post by Canux08 on 2008-03-07
> **reassuringlyoffensive said:**
> Did desktop videos play okay? Your card isn't blacklisted, so it should work alright with Compiz. If you want effects, you can use x11 instead of xvideo in MPlayer's preferences, but that means your CPU will be doing all of the work instead of the GPU. Or you can just use x11 in the browser by using the "vo=x11" option in MPlayer's plugin config file.
 
Nathan

Desktop videos weren't working either. I tried switching from x11 to xvideo, but it didn't make a difference. The only way to get it to work was to disable compiz video playback.

---

### Post by ubuntu-freak on 2008-03-07
> **impert said:**
> Thanks bw44,
The /etc/mplayerplug-in.conf is already as you suggest, and I've zapped the pluginreg.dat file so often the r and m keys are losing their letters. I'll give your site a try.

I'm going to go and paint a wall or two for a change. After that I'll go back and do all the steps in Nathan's how-to again.

Funny that I got the BBC well when I had the Totem and VLC plugins installed as well as the MPlayer ones. It should have been a real no-no.

Cheers

 
Have you rebooted? Also, seeing as you're not using RealPlayer, you might want to test other browser plugins out. Just remember to only have one installed at a time, and to remove the pluginreg.dat each time you change plugins.
 
Nathan

---

### Post by Kivech on 2008-03-07
> **reassuringlyoffensive said:**
> Thanks. :-)
 
How did it mess up streaming before? Curious.
 
Nathan

In another thread they advised to switch to the xine version of Totem. That worked for DVD playback, but all sound of .wav files and .mov files was completely messed up after that.

With your guide, it all works like a charm. I love the VLC player, which seems to be more suitable for DVDs anyway.

One question: my IcedTea Java Policy Tool crashes when I try to launch it. I filed a bug report on the site it indicated. You don't happen to know a way to fix this, do you?

The error I'm getting is this one:

From the terminal I run:
> /usr/lib/jvm/java-7-icedtea/bin/policytool

And I get this as a response:
> #
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b688973fe11, pid=7426, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /home/marc/hs_err_pid7426.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)


Running it with sudo makes no difference. Any clue if there is anything I can do about this?

Kivech

---

### Post by impert on 2008-03-07
> **reassuringlyoffensive said:**
> Have you rebooted? Also, seeing as you're not using RealPlayer, you might want to test other browser plugins out. Just remember to only have one installed at a time, and to remove the pluginreg.dat each time you change plugins.
 
Nathan

HI again,

Yes to "have you rebooted?", and yes, I'll try the other browser plugins. It'll come right sooner or later, I expect.

bw44:  I got excellent results with Mplayer (before this - haven't tried since.)

Thanks to both for your replies.

---

### Post by ubuntu-freak on 2008-03-07
> **Kivech said:**
> In another thread they advised to switch to the xine version of Totem. That worked for DVD playback, but all sound of .wav files and .mov files was completely messed up after that.

With your guide, it all works like a charm. I love the VLC player, which seems to be more suitable for DVDs anyway.

One question: my IcedTea Java Policy Tool crashes when I try to launch it. I filed a bug report on the site it indicated. You don't happen to know a way to fix this, do you?

The error I'm getting is this one:

From the terminal I run:


And I get this as a response:


Running it with sudo makes no difference. Any clue if there is anything I can do about this?

Kivech

 
Hmm. You can be my test subject then. Try [this thread](http://ubuntuforums.org/showthread.php?t=580792&page=12) and let me know how it goes.
 
Nathan

---

### Post by Kivech on 2008-03-07
> **reassuringlyoffensive said:**
> Hmm. You can be my test subject then. Try [this thread](http://ubuntuforums.org/showthread.php?t=580792&page=12) and let me know how it goes.
 
Nathan

Fixed! Thanks  a ton. You should include this fix in your main thread, it works like a charm.

I'm on Ubuntu Gutsy 64.

Great to see things come together like this!

Kivech

---

### Post by ubuntu-freak on 2008-03-07
> **Kivech said:**
> Fixed! Thanks  a ton. You should include this fix in your main thread, it works like a charm.

I'm on Ubuntu Gutsy 64.

Great to see things come together like this!

Kivech

 
Thanks for confirming that for me. I'm gonna add it to my troubleshooting section. Hopefully it will work from the standard repo when Hardy is released.
 
Nathan

---

### Post by bw44 on 2008-03-07
> **reassuringlyoffensive said:**
> Thanks for confirming that for me. I'm gonna add it to my troubleshooting section. Hopefully it will work from the standard repo when Hardy is released.
 
Nathan

Is there any pressing reason for a 32-bit user to upgrade to iced tea? The few sites I go to that use Java applets seem to work fine under sun-java6.

---

### Post by ubuntu-freak on 2008-03-07
> **bw44 said:**
> Is there any pressing reason for a 32-bit user to upgrade to iced tea? The few sites I go to that use Java applets seem to work fine under sun-java6.

 
It's not really an upgrade. IcedTea's plugin works in 64-Bit, that's the only reason I recommend it. 
 
Nathan

---

### Post by ubuntu-freak on 2008-03-08
I've now added a link to Kilz 64-Bit Adobe Flash script thread in my troubleshooting section. It installs an older version along with the nspluginwrapper (sets it up too), and should cure any problems 64-Bit users are having. Apparently nspluginwrapper doesn't much like the latest Adobe Flash.
 
Also wrote instructions in the troubleshooting section for adding the unofficial IcedTea Java repo, which contains a better and less buggy version. I'm guessing that when Hardy is released IcedTea Java will work straight off.
 
Nathan

---

### Post by wildmanne39 on 2008-03-08
:)Hi,Just wanted to say thanks for your how to it is great, I wish I could get my sound working on this hp v6227cl then I would be great. I have tried everything the other posts say to do nothing works though.

---

### Post by ubuntu-freak on 2008-03-08
> **wildmanne39 said:**
> :)Hi,Just wanted to say thanks for your how to it is great, I wish I could get my sound working on this hp v6227cl then I would be great. I have tried everything the other posts say to do nothing works though.

 
Thanks.
 
Have you tried the latest Hardy pre-release? Search Google with "ubuntu hardy wiki", then make a Live CD and see if sound works okay. 
 
Nathan

---

### Post by fbormann on 2008-03-09
Hi!

I'm wondering if anyone is able to play the Canadian news show "The National" ([http://www.cbc.ca/national/latestbroadcast.html](http://www.cbc.ca/national/latestbroadcast.html)) using MPlayer and the mozilla-mplayer plugin. I believe, I've followed the guide on page 1 to the letter, but unfortunately no luck with "The National". MPlayer always starts up, connects and then stops immediately. I've tried this setup with both 32 and 64-bit ubuntu 7.10 and SuSE 10.2, always got the same result. Other videos from the CBC website play ok.

I've managed to watch "The National" (as well as all other CBC videos) using totem-xine and its firefox plugin, but with this setup lots of videos from other (mostly German) sites (for example [www.n-tv.de](www.n-tv.de)) don't work at all anymore. Also I get long delays when accessing CBC radio broadcasts like "The World at 6" or "The World This Weekend", which I don't have using other players & plugins. Totem-gstreamer seemed to be more stable, unfortunately then the video has totally jerky. It seems with totem-gstreamer X acceleration is turned off in automatic video output mode, because using gstreamer-properties and set video output to X11 gives the same jerky output as before whereas setting it to Xv, I get no video at all (Matrox G550 gfx card).

The most compatible player/plugin I've found so far for the sites I want to access is xine-plugin and xine-ui. Unfortunately, with this setup there doesn't seem to be any option to make the video fullscreen, or is there?

If anyone has some solution to any of the problems mentioned above, I'd be very happy to hear it, I'm going crazy here.

---

### Post by bw44 on 2008-03-09
> **fbormann said:**
> I'm wondering if anyone is able to play the Canadian news show "The National" ([http://www.cbc.ca/national/latestbroadcast.html](http://www.cbc.ca/national/latestbroadcast.html)) using MPlayer and the mozilla-mplayer plugin. I believe, I've followed the guide on page 1 to the letter, but unfortunately no luck with "The National". MPlayer always starts up, connects and then stops immediately. I've tried this setup with both 32 and 64-bit ubuntu 7.10 and SuSE 10.2, always got the same result. Other videos from the CBC website play ok.
. . .
If anyone has some solution to any of the problems mentioned above, I'd be very happy to hear it, I'm going crazy here.

You mention several problems and some partial solutions which I haven't tried. I can only comment on the one above.  I experience exactly what you describe.  The symptoms are very similar to the situation at BBC before I switched to using RealPlayer for their videos.  Unfortunately, CBC doesn't give you that option.  (Of course, if they did give you the option, that's no guarantee it would work.) As a Canadian, if I want to watch the National, I can watch it on TV and don't usually stream it.

Unfortunately, as good as it is, Nathan's how-to can't solve all the problems with video streaming for Ubuntu (Linux) users.   It gets us closer than anything else I've tried, but some problems can only be solved if site owners code and test things with non-Microsoft, non-Mac browsers and plugins.   

Based on what I see happening (or NOT happening) with the National broadcast, I would say the problem is at CBC's end.  As you point out, all their other videos download and play fine with mplayer.  I would send them an email pointing out the facts and see if they don't fix it.  Some problems with the BBC's news site have been fixed after I (and perhaps may others) complained.  Anyway, it wouldn't hurt to try.

Cheers.

---

### Post by impert on 2008-03-09
Hi Nathan,

The little piece of advice in the third post in this thread is a gem and deserves to be in your how-to:
[http://ubuntuforums.org/showthread.php?t=523735]("http://ubuntuforums.org/showthread.php?t=523735")

Cheers

---

### Post by ubuntu-freak on 2008-03-09
> **impert said:**
> Hi Nathan,

The little piece of advice in the third post in this thread is a gem and deserves to be in your how-to:
[http://ubuntuforums.org/showthread.php?t=523735]("http://ubuntuforums.org/showthread.php?t=523735")

Cheers

 
Interesting. Is that only an issue with DVD playback?
 
Nathan

---

### Post by impert on 2008-03-09
Playing from file also.

I've swapped to the Totem plugin for Firefox at the moment; I'm getting 6 out of the 12 formats on the Linspire site,  no sound on three of them (all .avi), blackscreen or stopping on two, and an error message "problem while loading library or decoder (sipr.so)"  with the .rm format. (sipr.so does exist on my machine).

I'll have another play with the mplayer plugin  later: I think that preference thing may just be what's been stuffing me up. Right now I'm working on Totem.

Cheers

---

### Post by Airforcefalco on 2008-03-10
Alright so i followed your how-to to the T but flash still is not working!

I went through pt 2/5 of this guide and flash works on websites but not when trying to watch videos.

Also i tried to download flash from Adobe and I dont know how to run it, it is downloaded to my desktop. I tried cd /home/nick/desktop which is where the package says it is installed. Also tried cd /desktop but to no avail.

Thank you again for your help!

---

### Post by ubuntu-freak on 2008-03-10
> **Airforcefalco said:**
> Alright so i followed your how-to to the T but flash still is not working!

I went through pt 2/5 of this guide and flash works on websites but not when trying to watch videos.

Also i tried to download flash from Adobe and I dont know how to run it, it is downloaded to my desktop. I tried cd /home/nick/desktop which is where the package says it is installed. Also tried cd /desktop but to no avail.

Thank you again for your help!

 
What happens when you try to watch a YouTube vid? Are you running a 32-Bit system or 64-Bit? Most are running Ubuntu 32-Bit, incase you're not sure. Did you try my troubleshooting section?
 
Nathan

---

### Post by Airforcefalco on 2008-03-10
well i did it again and so far it is working! Thanks for the help i will let you know if it acts up again! (Youtube anyway)

Thanks!

Well there is a problem, Java doesnt seem to be working...Going to [http://ffiends.com/Games/StarDart/Game.jsp](http://ffiends.com/Games/StarDart/Game.jsp) for example and clicking on a game. It just comes up with another window and stays gray. 

Thanks again!

---

### Post by WFGeppetto on 2008-03-11
Ok, I have a problem.

Wait, first; will you guys be mad if I don't read all 59 pages?  I'm sure it's possible that the answer is in there, but sheesh, really, 59 pages?  Don't get me wrong, I won't be offended, or cry, if you tell me to just read, I know how forums work, but I've got to try for a shortcut.

Anyway, I'm having two problems that are weird.  I say weird, because I recently had my Ubuntu side (dual boot with Vista - 64 bit btw, for both) working perfectly.  I decided to reinstall, because I didn't have any critical personal files saved, and I am not familiar with properly removing everything (unless it can be done with Synaptic).  I had tried numerous apps to find what I liked, and had finally come up with a list of my favorites.  It seemed easier to me, to simply reinstall, and then configure it the way I wanted, than to figure out how to remove all the junk I didn't want anymore.

Ok, sorry, the weird part:  When I reinstalled, I followed all the same "how-tos" as before, and I know I did everything the same (well, I suppose *know* might be a strong word for it).  Only this time around, my AWN doesn't like applets; I get the white lines, and my streaming isn't all happy.  I'd love help with AWN, but I am in this thread for the streaming, so don't feel obligated, unless you have an answer at hand.

I followed the instructions to the T.  Everything went fine, except the mozilla-helix player.  It was not found.  Perhaps I am missing a repository?  Anyway, I continued on with the instructions, and did absolutely everything else.  Oh, I stopped in after the first section to see if "I was happy with my current streaming", but not everything worked, so I continued.

Google vids don't play, and oddly, usually Youtube does, but not always.  I am patient enough to be sure it has nothing to do with load times.

I went into synaptics, and installed every mozilla, and java thing that I could find that was obviously a plugin, or codec, or whatever (none of the development/creation stuff).  After doing that, flash games would appear, and start loading, but go no further.

Actually, I suspect that its a Java issue, and nothing to do with the helix player.  I am basing this on intuition, not knowledge.  Considering this, I remember that last time, when I got things working, one of my problems was with Frostwire (which I ditched for gnuttella), and I found advice about configuring java.  I used the command listed: something like config --java something, and told it to use Java7, rather than 6.  That fixed my problems with frostwire, and I noticed *better* streaming thereafter as well.  The problem is, I can't find, and don't remember that command, and looking up info java, or help java, doesn't help, because I am almost impotent at the command prompt.  I just don't quite fully understand the syntax yet.

Can you help easily?  Will I have to read all 59 pages?  If there isn't an obvious, or possibly simple answer, I'll just go back to searching, but I'd appreciate the help.  I really don't understand why it all worked the first time, and the second it does not.

For anyone interested, the apps I use now (this coming from a noob) are as follows:

gtk-gnutella for single file downloads
deluge for torrents (holy crap, I love deluge!, I still need to figure out moblocker though)
exaile for music (I love it, and it's the easiest to get mp3s going quickly)
k3b for burning - dvd and cd
qdvdauthor for authoring
ffmpeg for converting (although I wish there were a Gui version, is there?)

I just thought some might be interested in what a noob thought was easy.

---

### Post by iobelisk on 2008-03-11
Hi, I tried all the above instructions but when i rm pluginreg.dat it says file not found. so i go to the .mozilla directory, ls firefox and there is no plugins directory, but a askjasdefault profile directory. i go in there and sure enough is a pluginreg.dat file. i rm it but now about: plugins in firefox does not show up any plugins at all save shockwave, i checked thru this thread and it seems only one person has had this problem and no resolution was posted for it. 

i was hoping somebody could help me figure this out. thanks!

(i'm using firefox 3 beta, hardy heron)

---

### Post by WFGeppetto on 2008-03-11
Ok, now I'm ashamed.  I will read the whole thread.  That guy above me did.

---

### Post by bw44 on 2008-03-11
> **WFGeppetto said:**
> Ok, now I'm ashamed.  I will read the whole thread.  That guy above me did.Why not try searching the thread for something like "64bit" and/or "Java"?  Nathan has often posted information about things specific to these two keywords.

Just a suggestion.  Wish I could help with your issues - but I know nothing! :(

---

### Post by kara.lockard on 2008-03-11
Your suggestion is quite good bw44:lolflag:

I found another Hillary’ous video ..[http://www.youtube.com/watch?v=E7150u9sfCo](http://www.youtube.com/watch?v=E7150u9sfCo)

---

### Post by WFGeppetto on 2008-03-11
I have a suggestion, to amend your suggestion bw44, and thank you.  Btw, nice avatar.

I have searched many times similarly to what you have mentioned.  It only brings up huge amounts of threads, the vast majority of which are irrelevant.  The search function, I suspect, only searches the post bodies, and not the titles (I am not sure of this at all).  The reason I think this, is that if I get even a little bit specific with my search, then it does not return any results at all.  I don't know why it is so difficult for the search function to get so specific, but that is actually my only (imo valid) complaint about the forums.

I did, however, get a great tip from another guy in another thread, about the same search issues.  Ah, how does the code box work? I guess I'll try the normal quote function.

>  site:[http://ubuntuforums.org](http://ubuntuforums.org)

If you put that into Google, with a space before your search item, you get much more accurate, and thorough results.

Thanks for the suggestion, as I'm sure I seem like one of the typical impatient people that doesn't like to look for answers, but the actual reason I am impatient in my above thread is because I have been looking for answers for about a week.  The worst part is, I had found them before, and now I can't.  I suppose I should have to subscribed to every thread that I found that was helpful.  I've apparently got much more reading to do, but I'll be back.

Thanks for trying to help.

---

### Post by WFGeppetto on 2008-03-11
I am double posting to avoid confusion.  I would edit, but I think that this will be clearer.

I figured out how to configure my java, the way that I was hoping to.  I used Google, and input:  'site:[http://ubuntuforums.org](http://ubuntuforums.org) configure java' into the search field.  Most of the results were more than a year old, and I'd advise anyone who uses the google search to look at the dates of the posts, before following any instruction.

In the (don't remember) about 6th returned result, I found what I was looking for.  This is my terminal, right now, verbatim, copied and pasted.
______________________________________________________________________
wfgeppetto@GPTO:~$ sudo update-alternatives --config java
[sudo] password for wfgeppetto:

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/lib/jvm/java-7-icedtea/jre/bin/java
*+        3    /usr/lib/j2se/1.4/bin/java

Press enter to keep the default[*], or type selection number: 2
Using `/usr/lib/jvm/java-7-icedtea/jre/bin/java' to provide `java'.
wfgeppetto@GPTO:~$ sudo update-alternatives --config java
[sudo] password for wfgeppetto:

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
*         2    /usr/lib/jvm/java-7-icedtea/jre/bin/java
 +        3    /usr/lib/j2se/1.4/bin/java

Press enter to keep the default[*], or type selection number: 

___________________________________________________________________

I intentionally did not use code boxes, or quote boxes, because I do not feel that I am knowledgable, or responsible enough to advise proper code use.  I am simply relaying what I did.

It seemed to help.  Many things work now that did not before (I think it may be important to note that I am running 64bit).  Some things still don't work, but then I've been *trying* to break it, by visiting those crappy vid sites with all the crap everywhere (ie: porn, I find that if it works on adult sites, then it will work anywhere)  The remaining problems, may be the fault of the sites, rather than my configuration.

---

### Post by ubuntu-freak on 2008-03-11
My how-to doesn't instruct you to install mozilla-helix-player.
 
You're running a 64-Bit Ubuntu system yeah? The troubleshooting section includes instructions for adding a repo which will get IcedTea Java working properly, and a link to a script which will install an older and better version of flash for 64-Bit systems.
 
Big mistake searching through Synaptic and installing anything that seems to be a plugin for FF. Didn't you read Part 2? Conflicts? Use that remove command in Part 2 and make sure you don't have conflicting packages, and make sure you don't have the sun-java6-plugin installed, or sun-java5-plugin.
 
Hope that helps.
 
Nathan
 
P.S. FF3 is beta, my how-to is for FF2 and Epiphany. The symlink commands mentioned in the troubleshooting section will get FF3 streaming though.

---

### Post by WFGeppetto on 2008-03-11
> **reassuringlyoffensive said:**
> My how-to doesn't instruct you to install mozilla-helix-player.
 
You're running a 64-Bit Ubuntu system yeah? The troubleshooting section includes instructions for adding a repo which will get IcedTea Java working properly, and a link to a script which will install an older and better version of flash for 64-Bit systems.
 
Big mistake searching through Synaptic and installing anything that seems to be a plugin for FF. Didn't you read Part 2? Conflicts? Use that remove command in Part 2 and make sure you don't have conflicting packages, and make sure you don't have the sun-java6-plugin installed, or sun-java5-plugin.
 
Hope that helps.
 
Nathan
 
P.S. FF3 is beta, my how-to is for FF2 and Epiphany. The symlink commands mentioned in the troubleshooting will get FF3 streaming though.

Aha!  That was a remove command.  Well, that helps solve much of my confusion.  I must not have read my log carefully.  I saw something like "no mozilla-helix player found", and stupidly, assumed it couldn't find it to install, but it was trying to remove.  Haha, I feel a bit silly about that one.

I did, infact follow the instructions properly, the first time.  I suppose, the main problem must have been the result of installing java6, as is in one of your commands, rather than using 7.

Thank you very much, I'm sure this will be a great help.  I can easily manage defaults, and conflicts in windows, but I'm still feeling that out, here in Ubuntu.  I will try to remove all the unnecessary plugins that I have installed, and remove all java that is not 7.  I should keep the plugin though, or not?

Perhaps, it would be a better idea to remove all the plugins I can find, and then follow your instructions again, but using java 7 rather than 6.

I must say, I am extremely impressed, and appreciative of the fact that you not only made such a thorough set of instructions, but you also continue to maintain this thread.  Thank you, so very much.  +1 (I just learned how to thank yesterday!)

Edit:  I suppose, considering the fact that I am running 64 bit, I must not have followed the instructions properly the first time.  That was a rather arrogant claim.  I will carefully read every single word, considering the fact that I must have missed something.

---

### Post by bw44 on 2008-03-11
> **WFGeppetto said:**
> . . . I have searched many times similarly to what you have mentioned.  It only brings up huge amounts of threads, the vast majority of which are irrelevant.  The search function, I suspect, only searches the post bodies, and not the titles (I am not sure of this at all).  The reason I think this, is that if I get even a little bit specific with my search, then it does not return any results at all.  I don't know why it is so difficult for the search function to get so specific, but that is actually my only (imo valid) complaint about the forums.

I intentionally did not use code boxes, or quote boxes, because I do not feel that I am knowledgable, or responsible enough to advise proper code use. I am simply relaying what I did.WFGeppetto,

Google can be  good for searching, as someone pointed out, but try the "Search this thread" drop down menu at the top of each page of the thread listing.  (The main Search option and Google **are** overkill sometimes!) I tried searching on "java" and "64bit"with "Search this thread"  and I think it displayed a summary of all the posts where those two keywords appear.

And it's ok to use code boxes!  They aren't authoritative, they just show what code you entered, or should enter.  Whether the code is correct or not is another issue! :)

Anyway, glad you're starting to get things resolved.

bw44

---

### Post by WFGeppetto on 2008-03-11
> **bw44 said:**
> WFGeppetto,

Google can be  good for searching, as someone pointed out, but try the "Search this thread" drop down menu at the top of each page of the thread listing.  

bw44

Now, that is very helpful!  Why is it so easy to miss such simple things.  I need to work on observation, and thoroughness.  Yay, I'm starting to learn again!  Perhaps, I'll be a useful addition one day after all.

---

### Post by levelnext on 2008-03-11
Thankyou for your tips and commands.  Worked great for me!!

---

### Post by Chame_Wizard on 2008-03-11
Why isn't gnash working?i also installed swfdec-mozilla,but it doesn't work either.so confusing when using a 64bit computer.

---

### Post by ubuntu-freak on 2008-03-11
> **levelnext said:**
> Thankyou for your tips and commands.  Worked great for me!!

 
Thanks! I'm always glad when it works first time for people.
 
Nathan

---

### Post by ubuntu-freak on 2008-03-11
> **Chame_Wizard said:**
> Why isn't gnash working?i also installed swfdec-mozilla,but it doesn't work either.so confusing when using a 64bit computer.

 
Why use Gnash? Worth trying the new version when it's in the repos though. Go to the link in my troubleshooting section and install an older version of Adobe Flash. It works in 64-Bit, but the latest version isn't much liked by nspluginwrapper.

---

### Post by iobelisk on 2008-03-11
the symlink fixed everything, thank you very much!

---

### Post by WFGeppetto on 2008-03-11
I think adding those repositories helped.  I still have a few things not working.

[http://www.halo3.com](http://www.halo3.com)  What is that?  I assumed (I know...) java, but I don't know.  It flashes up for a minute, and then goes black.

I am embarrased to admit, I did miss that part in the trouble shooting.  Thank you for pointing that out.

edit:  Crap, I'm jumping the gun, please ignore this post, I need to reboot, and go over it again, to make sure I haven't missed anything.

---

### Post by udh on 2008-03-12
> **WFGeppetto said:**
> I think adding those repositories helped.  I still have a few things not working.

[http://www.halo3.com](http://www.halo3.com)  What is that?  I assumed (I know...) java, but I don't know.  It flashes up for a minute, and then goes black.

I am embarrased to admit, I did miss that part in the trouble shooting.  Thank you for pointing that out.

edit:  Crap, I'm jumping the gun, please ignore this post, I need to reboot, and go over it again, to make sure I haven't missed anything.

**It's adobe flash plugin, you can download it from here (installation instructions given on on the same page)**


> [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

[B]You can check if the plugin is installed properly or not by simply opening the halo3 website or you can check it at this url:
[/B]
> [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

**me just 2 days old to ubuntu/linux :) **

---

### Post by ubuntu-freak on 2008-03-12
> **udh said:**
> **It's adobe flash plugin, you can download it from here (installation instructions given on on the same page)**




[B]You can check if the plugin is installed properly or not by simply opening the halo3 website or you can check it at this url:
[/B]


**me just 2 days old to ubuntu/linux :) **

 
Did you have problems with the one in the repos? Shouldn't have to install from adobe.com, and Shockwave doesn't work in Ubuntu unless you install IE + Shockwave in Wine. 
 
Nathan

---

### Post by ubuntu-freak on 2008-03-13
> **impert said:**
> Hi Nathan,

The little piece of advice in the third post in this thread is a gem and deserves to be in your how-to:
[http://ubuntuforums.org/showthread.php?t=523735]("http://ubuntuforums.org/showthread.php?t=523735")

Cheers

 
Thanks for that.  
 
I've added those instructions to the streaming section as it should be enabled by default. 
 
Nathan

---

### Post by thane1 on 2008-03-13
Many many thanks!!!!
Somewhere along the line recently I lost the ability to play streaming video (although I did have it functional at one point).  After a few inclusions from step 2 I now have it back.  Really appreciative!  The only sticky points I encountered were in the 64 bit firefox setup as follows:
I didn't install RealPlayer as suggested. But I then had worries trying to find the next bit [COLOR="Red"](IIf you decide to use the MPlayer plugin for streaming, make sure you edit the settings so that "enable-rm", "enable-helix" and "enable-smil" are set to "1" instead of "0[/COLOR]".)
The next statement was a bit less (but still somewhat confusing at first)...  [COLOR="Red"]Now you need to download RealPlaye[/COLOR]r.  (The instructions had just said not to install RealPlayer for 64 bit.)  [COLOR="Red"] It will also install plugins for Firefox, enabling reliable streaming of audio and video in that format. Real Media playback has been so random with MPlayer that I decided RealPlayer was the best way to go. Download it here. 
That's it! You have all the important packages for streaming and you have removed packages which will conflict with the MPlayer browser plugin. Now the next step.[/COLOR]

Finally it wasn't until I got to the next part, that I found the previous "helix" and "smil" modification lines (but at first confusingly not the "rm" line, which I imagine is because its something to do with the RealPlayer prog which I didn't install for 64 bit).



[COLOR="Red"]gksudo gedit /etc/mplayerplug-in.conf

Then paste the following settings into it (don't worry if it's empty or if you didn't have this file there already. Also, it's safe to remove the settings already present). This should improve streaming a great deal with certain sites which have caused problems. Make sure you keep "enable-rm" "helix" and "smil" set to "0" (unless you are a 64-Bit user) as RealPlayer will be handling those formats. Also, if you chose to edit the "/etc/" file, make sure the "$HOME" version in your home folder is blank or deleted in all user accounts.

download=1
cachesize=1024
cache-percent=25
keep-download=0
dload-dir=$HOME
noembed=0
autoplay=1
enable-wmp=1
enable-qt=1
enable-rm=0
enable-gmp=1
enable-dvx=1
enable-mpeg=1
enable-mp3=1
enable-midi=0
enable-pls=1
enable-ogg=1
enable-smil=0
enable-helix=0
nomediacache=0
nopauseonhide=1
rtsp-use-tcp=0
rtsp-use-http=0
[/COLOR]
I followed the rest of your excellent how-to and I now have streaming video again (big big happy face).  64 bit has given me a few concerns so far, but I'm determined.  This how-to has definitely helped.  Cheers.

---

### Post by ubuntu-freak on 2008-03-13
Thanks, I'm glad it helped.
 
Nathan
 
P.S. If you're a new user, I'd suggest you install the 32-Bit version of Ubuntu. There's no real advantage to using the 64-Bit version.

---

### Post by WFGeppetto on 2008-03-13
Ok, apparently, I just did it wrong.  It's still not all working.  I'm sure it's a mistake that I made, nothing to do with the instructions.

Would starting back at the top, and simply do it all over again be smart, or even work?  I did download other plugins from synaptics (remember? you said that was a rather bad idea).  I have removed all that I remember of, but I don't doubt that I've missed one or more.

I do have one other idea, especially considering this last post.  I'm running the 64 bit version, and if there really isn't any good reason to, perhaps I should simply download the 32 bit distro.  I have very few files that I'll need to back up.  It would definitely be a pain to reconfigure everything, but if I have a better, cleaner, and more functional install, I'd say it's worth it.  Besides, I am simply not competent enough to attempt getting my system back to the begining without very specific help.

Advice?

---

### Post by bilal.17 on 2008-03-13
great post.. it really helped to get mplayer up and running... also liked google earth

---

### Post by Tyler H on 2008-03-14
Is anyone else having issues with crashing? I'm able to listen to audio streams, but Flash crashes randomly, leaving a black silhouette where it used to be on the desktop.

---

### Post by ubuntu-freak on 2008-03-14
> **WFGeppetto said:**
> Ok, apparently, I just did it wrong.  It's still not all working.  I'm sure it's a mistake that I made, nothing to do with the instructions.

Would starting back at the top, and simply do it all over again be smart, or even work?  I did download other plugins from synaptics (remember? you said that was a rather bad idea).  I have removed all that I remember of, but I don't doubt that I've missed one or more.

I do have one other idea, especially considering this last post.  I'm running the 64 bit version, and if there really isn't any good reason to, perhaps I should simply download the 32 bit distro.  I have very few files that I'll need to back up.  It would definitely be a pain to reconfigure everything, but if I have a better, cleaner, and more functional install, I'd say it's worth it.  Besides, I am simply not competent enough to attempt getting my system back to the begining without very specific help.

Advice?

 
I'm gonna install the 32-Bit version on my sisters AMD 64 HP laptop. Makes more sense for a casual desktop user in my opinion. The 32-Bit version is the most tested, and some solutions or workarounds posted in the forums and elsewhere won't work on a 64-Bit system. 
 
Nathan

---

### Post by ubuntu-freak on 2008-03-14
> **Tyler H said:**
> Is anyone else having issues with crashing? I'm able to listen to audio streams, but Flash crashes randomly, leaving a black silhouette where it used to be on the desktop.

 
Did you try my troubleshooting section?
 
Nathan

---

### Post by ubuntu-freak on 2008-03-14
> **bilal.17 said:**
> great post.. it really helped to get mplayer up and running... also liked google earth

 
Thanks, glad it helped.
 
I redesigned it a bit today. The only text left that is bold and black is the text to be copy and pasted into the Terminal or configuration files.
 
Nathan

---

### Post by Greglu on 2008-03-14
Thank you this was excellent
Cheers
Greg

---

### Post by WFGeppetto on 2008-03-14
> **reassuringlyoffensive said:**
> I'm gonna install the 32-Bit version on my sisters AMD 64 HP laptop. Makes more sense for a casual desktop user in my opinion. The 32-Bit version is the most tested, and some solutions or workarounds posted in the forums and elsewhere won't work on a 64-Bit system. 
 
Nathan

Great, I think I'll back up, and go with that.  I'll come back when I'm done, to tell of the success of this guide (that I know I'll have.

Thanks!

---

### Post by WFGeppetto on 2008-03-15
Alright, I just got finished installing the 32-bit Gutsy.  I looked at the sites I had had trouble with before, just to see what they were doing.  I was prompted once for the Adobe non-free player, and again for gstreamer, automatically, and after installing those, I can't find anything that won't work.

This was rediculously easy.  Thanks for the advice, Reassuringly.  I think the 32-bit is for me.  I didn't need the guide, and it looks like this version is a little bit better dummy proofed.  I'm happy I did it.  I do wish I was a little more savvy, but since I'm not, this is probably better.

---

### Post by ubuntu-freak on 2008-03-15
> **WFGeppetto said:**
> Alright, I just got finished installing the 32-bit Gutsy.  I looked at the sites I had had trouble with before, just to see what they were doing.  I was prompted once for the Adobe non-free player, and again for gstreamer, automatically, and after installing those, I can't find anything that won't work.

This was rediculously easy.  Thanks for the advice, Reassuringly.  I think the 32-bit is for me.  I didn't need the guide, and it looks like this version is a little bit better dummy proofed.  I'm happy I did it.  I do wish I was a little more savvy, but since I'm not, this is probably better.

 
Yeah it's much easier now. It's like my intro says, this how-to was written incase you have more advanced needs. Those features are in 64-Bit as well though.
 
Does streaming work okay with totem-mozilla? Should work the same in 64-Bit. 
 
You will still need to do Part 4 if you wanna watch DVDs. I still think it's worth doing Part 1 also, as you get an extra java package, gstreamer and w32codecs which VLC and MPlayer use, plus more useful packages. 
 
Nathan

---

### Post by Darganot on 2008-03-16
I'm having some problems.  I'm trying to convert a real media video (.rm file) to an avi or some other editable format.  I downloaded it to my home directory via rtsp, and can play the video find locally.

I tried using the program suggested WinFF ([http://biggmatt.com/winff/](http://biggmatt.com/winff/)) but it keeps crashing whenever I try to convert to a format I want.  Is there another program or a way to convert this file with command line?



On a side note - this is video of Bill Gates testifying before congress last wednesday.  I downloaded it from C-SPAN's website and would really like to but some of the more - *FLATTERING* - excerpts on youtube asap.

---

### Post by haggus on 2008-03-16
thank you for the excellent work

---

### Post by WFGeppetto on 2008-03-16
Reassuring...

Yeah, absolutely everything works well, and easily.  I actually don't know if totem is being used.  Firefox prompted me to install plugins, once for gstreamer, once for mplayer, and once for flash.  So far, with those three installs, and their packaged files, I have yet to find anything that won't work.  In fact, my videos now have a play/pause button, and a progress bar (i had neither with the 64bit).

Ironically, one of the only two problems I have now, is concerning winff, as mentioned in the above post.  I use ffmpeg to convert avi, and I'd like to have a GUI for it.  The AWN curves installation gave me the exact same error as the winff installation:

"program is uninstallable.  Wrong architecture 'i386' "

Is this because I am running 32 bit on an AMD 64 machine?  Is there a work around?

Either way, I'm still glad I've switched, and more stuff works more easily.  If these are the only two programs I cannot use, then I'll be fine.  Thanks for your advice Reassuring!

---

### Post by ubuntu-freak on 2008-03-17
> **WFGeppetto said:**
> Reassuring...

Yeah, absolutely everything works well, and easily.  I actually don't know if totem is being used.  Firefox prompted me to install plugins, once for gstreamer, once for mplayer, and once for flash.  So far, with those three installs, and their packaged files, I have yet to find anything that won't work.  In fact, my videos now have a play/pause button, and a progress bar (i had neither with the 64bit).

Ironically, one of the only two problems I have now, is concerning winff, as mentioned in the above post.  I use ffmpeg to convert avi, and I'd like to have a GUI for it.  The AWN curves installation gave me the exact same error as the winff installation:

"program is uninstallable.  Wrong architecture 'i386' "

Is this because I am running 32 bit on an AMD 64 machine?  Is there a work around?

Either way, I'm still glad I've switched, and more stuff works more easily.  If these are the only two programs I cannot use, then I'll be fine.  Thanks for your advice Reassuring!

 
I don't that error. 32-Bit is 32-Bit, makes no difference that your processor is 64-Bit capable.
 
Did you try to install it by double-clicking or dpkg? Have you Googled the error?
 
Nathan

---

### Post by ubuntu-freak on 2008-03-17
> **Darganot said:**
> I'm having some problems.  I'm trying to convert a real media video (.rm file) to an avi or some other editable format.  I downloaded it to my home directory via rtsp, and can play the video find locally.

I tried using the program suggested WinFF ([http://biggmatt.com/winff/](http://biggmatt.com/winff/)) but it keeps crashing whenever I try to convert to a format I want.  Is there another program or a way to convert this file with command line?



On a side note - this is video of Bill Gates testifying before congress last wednesday.  I downloaded it from C-SPAN's website and would really like to but some of the more - *FLATTERING* - excerpts on youtube asap.

 
It's due to some legal ********. Give these two threads a try;
 
[http://ubuntuforums.org/showthread.php?t=572011](http://ubuntuforums.org/showthread.php?t=572011)
 
[http://ubuntuforums.org/showthread.php?t=720427&page=2](http://ubuntuforums.org/showthread.php?t=720427&page=2)
 
I may add instructions for installing the unrestricted FFmpeg package to the "Sound & Video Conversion" section at some point.
 
Nathan

---

### Post by WFGeppetto on 2008-03-17
Thanks, I'll google the error.  It's a weird one.  

Also, your right, it doesn't like to play DVDs, I did the first part of your instructions, and that's now fixed as well.

Rock, you getz another thanx!

---

### Post by WFGeppetto on 2008-03-17
Ok, I found this:

> dpkg -i --force-architecture mypackage-1.0-i386.deb
Where mypackage-1.0-i386.deb is the 32-bit software you wish to install.

The problem is, it tells me I need superuser perms to dpkg, and I don't know how to enable that.

Ok, I figured out to use sudo, now I get this:

```
wfgeppetto@GPTO:~$ sudo dpkg -i --force-architecture winff-0.33-i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package winff.
(Reading database ... 110029 files and directories currently installed.)
Unpacking winff (from winff-0.33-i386.deb) ...
dpkg: dependency problems prevent configuration of winff:
 winff depends on ffmpeg; however:
  Package ffmpeg is not installed.
dpkg: error processing winff (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 winff
wfgeppetto@GPTO:~$ 

```

Edit:  Duhr!  I installed ffmpeg from synaptics, then ran it again.  It worked perfectly.  Now I suppose if I change the AWN curves instructions, at that point in the install, and add the code, it should work too.  I know this isn't all of that relevant to this thread, but, it started here, and I'll post the results.  Hopefully this will be helpful for others, as well.

---

### Post by WFGeppetto on 2008-03-17
Yup, the same --force-architecture code worked for my AWN curves problem as well.

Ubuntu knows I have an AMD64 machine, and it doesn't want to install i386 stuff on it.  I don't know how to say it better than that.  This may not be an entirely acurate statement, but when I try to run these .debs, it says 'Wrong architecture', and later in the error says 'amd64, not i386' so I am left to assume the above.

I replaced this command
```
sudo gdebi *.deb
```

with this
```
sudo dpkg -i --force-architecture *.deb
```

It worked like a charm.  I did lose a couple of applets, but I bet I can find them, and copy them into the appropriate folder, or something.

---

### Post by cornelis spronk on 2008-03-18
Thanks.  After weeks of struggling with Realplayer, and Gutsy, I finally got the BBC to work using steps 1 and 2 out of 5.

---

### Post by WFGeppetto on 2008-03-18
Yup, I've got absolutely everything working now.  The 32 bit installation prompted for most things.  After I installed the prompted software, I followed pat 1/5, and 2/5, which got everything else I needed, then I got vlc for DVDs.  That's all it took for me.  Everything works like a charm.

I would like to suggest that you include [Winff](http://www.winff.org/) in your video conversion section.  It uses ffmpeg, but gives it a front end GUI.  It's so easy to convert using Winff, that it's pretty much rediculous.

---

### Post by ubuntu-freak on 2008-03-18
> **WFGeppetto said:**
> 
I would like to suggest that you include [Winff](http://www.winff.org/) in your video conversion section.  It uses ffmpeg, but gives it a front end GUI.  It's so easy to convert using Winff, that it's pretty much rediculous.

 
Umm...it's been in my how-to ever since it was rewritten in January. :-)
 
Nathan

---

### Post by WFGeppetto on 2008-03-18
Haha, ok, I shutup nao.

---

### Post by Kivech on 2008-03-18
Hi Nathan,

Second time I'm using your guide, different version of Ubuntu this time though.

Since I get bored easily with a good working OS, I decided to give Hardy a try and have the 64 bits version running now. At least there's problems to fix: just the way I like it ;)

I ran into two small problems:

1) The IcedTea Policy Tool also doesn't work here, but adding the repos to the resource.list doesn't work either. So I'm stuck with that. Although it seems to me that IcedTea itself is working fine. Haven't noticed any problems with java itself yet.

2) When trying to set VLC to launch upon inserting a DVD, by your exact instructions (part 4 last paragraph),... it doesn't work. I'm baffled, really. When I change the keys to your command, set them as default and I insert a DVD, this ridden Totem keeps launching.

First I thought it was because the player was designated as cdrom0, but changing dvd into that doesn't do a thing either. Is there another way, that you know that the system is forcing Totem to be the default player for DVDs in Hardy?

If you don't, no worries, I'll be scanning google and stuff to see what I can come up with, but in case you know a quick fix, I'd really appreciate it.

Rest works like a charm, also on Hardy 64.

Cheers!

Kivech

---

### Post by ubuntu-freak on 2008-03-18
> **Kivech said:**
> Hi Nathan,

Second time I'm using your guide, different version of Ubuntu this time though.

Since I get bored easily with a good working OS, I decided to give Hardy a try and have the 64 bits version running now. At least there's problems to fix: just the way I like it ;)

I ran into two small problems:

1) The IcedTea Policy Tool also doesn't work here, but adding the repos to the resource.list doesn't work either. So I'm stuck with that. Although it seems to me that IcedTea itself is working fine. Haven't noticed any problems with java itself yet.

2) When trying to set VLC to launch upon inserting a DVD, by your exact instructions (part 4 last paragraph),... it doesn't work. I'm baffled, really. When I change the keys to your command, set them as default and I insert a DVD, this ridden Totem keeps launching.

First I thought it was because the player was designated as cdrom0, but changing dvd into that doesn't do a thing either. Is there another way, that you know that the system is forcing Totem to be the default player for DVDs in Hardy?

If you don't, no worries, I'll be scanning google and stuff to see what I can come up with, but in case you know a quick fix, I'd really appreciate it.

Rest works like a charm, also on Hardy 64.

Cheers!

Kivech

 
Try [this thread](http://ubuntuforums.org/showthread.php?t=333714) and let me know which solution works with Hardy, cheers.
 
Nathan

---

### Post by Kivech on 2008-03-19
> **reassuringlyoffensive said:**
> Try [this thread](http://ubuntuforums.org/showthread.php?t=333714) and let me know which solution works with Hardy, cheers.
 
Nathan

Doesn't seem to work unfortunately. I went ahead and filed a bug report. It seems that similar issues are popping up in Hardy where changed settings in the gnome configurator are being ignored by the system.

I'll keep you updated when I hear more about this.

Kivech

---

### Post by bilijoe on 2008-03-19
Many thanks to ReassuringlyOffensive for his great article.  I hope I am not being redundant, but I just couldn't bring myself to read through all 50+ screens of replies.  I followed the instructions for making VLC my default DVD player, but when I insert a DVD, Totem still comes up automatically.  What have I missed?

By reading backwards from the last page of replies, I have found info to MOSTLY answer my question.  The only thing I am stuck on now is that, when the disk is inserted, VLC comes up, but playback does not start until I click on the Play button.  It's only a minor annoyance, but I'd like to know if there's a way to get it to start automatically.  When Totem was coming up, it started playback automatically, so I assume there is a way to get VLC to do the same.

---

### Post by ubuntu-freak on 2008-03-19
> **bilijoe said:**
> Many thanks to ReassuringlyOffensive for his great article.  I hope I am not being redundant, but I just couldn't bring myself to read through all 50+ screens of replies.  I followed the instructions for making VLC my default DVD player, but when I insert a DVD, Totem still comes up automatically.  What have I missed?

By reading backwards from the last page of replies, I have found info to MOSTLY answer my question.  The only thing I am stuck on now is that, when the disk is inserted, VLC comes up, but playback does not start until I click on the Play button.  It's only a minor annoyance, but I'd like to know if there's a way to get it to start automatically.  When Totem was coming up, it started playback automatically, so I assume there is a way to get VLC to do the same.

 
Thanks for your comments.
 
That's an odd issue you have there, never come accross it. Try changing the command to one of the alternatives in [this thread](http://ubuntuforums.org/showthread.php?t=333714), or see if a setting needs changing in VLC.
 
Nathan

---

### Post by brucewagner on 2008-03-22
So....   This How To, as it is, will work for us already using Ubuntu 8.04 BETA now...?

---

### Post by mocha on 2008-03-22
> **bilijoe said:**
> The only thing I am stuck on now is that, when the disk is inserted, VLC comes up, but playback does not start until I click on the Play button.  It's only a minor annoyance, but I'd like to know if there's a way to get it to start automatically.  When Totem was coming up, it started playback automatically, so I assume there is a way to get VLC to do the same.


Try going to System - Preferences - Removeable Drives and Media, click on the Multimedia tab, you probably have to modify the command there, like vlc %m or vlc %f, I don't know for certain.

---

### Post by ubuntu-freak on 2008-03-22
> **brucewagner said:**
> So....   This How To, as it is, will work for us already using Ubuntu 8.04 BETA now...?

 
Why not? I just have to keep an eye on package names and versions, the Ubuntu version doesn't matter so much though.
 
Seems there is a problem making VLC the default DVD player in Hardy for now, but it is still a preview release.
 
Nathan

---

### Post by musket85 on 2008-03-23
Hello ReassuringlyOffensive,
I'm new to this thread (and Ubuntu) and need help. I followed the steps in the first post and still cannot see videos in firefox.

Recently got this upon trying
:~$ sudo apt-get purge flashplugin-nonfree && sudo apt-get install flashplugin-nonfree

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

Also when putting in about:plugins into the address bar the only ones displayed are Java, not any of the others you suggest.

It is 32bit Ubuntu and I only did step 1 and troubleshooting, didnt wanna overcomplicate the process with mplayer or anything else.
A little help?
Ben.

---

### Post by ubuntu-freak on 2008-03-23
> **musket85 said:**
> Hello ReassuringlyOffensive,
I'm new to this thread (and Ubuntu) and need help. I followed the steps in the first post and still cannot see videos in firefox.

Recently got this upon trying
:~$ sudo apt-get purge flashplugin-nonfree && sudo apt-get install flashplugin-nonfree

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

Also when putting in about:plugins into the address bar the only ones displayed are Java, not any of the others you suggest.

It is 32bit Ubuntu and I only did step 1 and troubleshooting, didnt wanna overcomplicate the process with mplayer or anything else.
A little help?
Ben.

 
That's really odd. I'm not seeing any posts for 32-Bit Flash being broken, just 64-Bit due to the wrapper. Have you tried going to YouTube and installing it with the Firefox prompt?
 
Do no sites stream with Totem's plugin at all? Might be worthwhile doing Part 2, it's still just a matter of cutting and pasting.
 
Nathan
 
P.S. If you still get the error, check out this manual install method on aysiu's website;
 
[http://www.psychocats.net/ubuntu/flashmanual](http://www.psychocats.net/ubuntu/flashmanual)

---

### Post by musket85 on 2008-03-23
Ah ************* yes!
It works now, cheers man. To be honest this was the sticking point stopping me from transferring from windows. Excellent.
Fyi, the method on psychocats worked, but I did try step2 first and still got the error.
The only prob with the method is that it asks you to close the browser while following the instructions from it, easily solved with a copy and paste though.

---

### Post by jeremycollins08 on 2008-03-23
You mentioned Compizconfig settings manager...do I have to have this installed to run these commands?
Edit: Nevermind :)

-----------------------------------------------------

I recieved this during the install of ```
sudo apt-get install alsa-oss compizconfig-settings-manager faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 msttcorefonts sun-java6-fonts sun-java6-jre sun-java6-plugin unrar w32codecs 
``` in step 1/5:

```
&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring msttcorefonts &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;     
     &#9474;                                                                                                                                                                                                   &#9474;     
     &#9474; msttcorefonts uses defoma                                                                                                                                                                         &#9474;     
     &#9474;                                                                                                                                                                                                   &#9474;     
     &#9474; Msttcorefonts uses the DEbian FOnt MAnager (defoma). If you wish to use the fonts provided by this package under the X Window System, you must configure it to use defoma fonts.                  &#9474;     
     &#9474;                                                                                                                                                                                                   &#9474;     
     &#9474; The easiest way to do so is to use the x-ttcidfont-conf package. For more information, install the x-ttcidfont-conf package and consult its documentation under /usr/share/doc/x-ttcidfont-conf.  &#9474;     
     &#9474;                                                                                                                                                                                                   &#9474;     
     &#9474; For uses of msttcorefonts not related to the X Window System (e.g. printing) this is not required.  
```

---

### Post by ubuntu-freak on 2008-03-23
They should be installed automatically with msttcorefonts. Just make sure they are. Should be okay though.
 
Nathan

---

### Post by jeremycollins08 on 2008-03-24
> **reassuringlyoffensive said:**
> They should be installed automatically with msttcorefonts. Just make sure they are. Should be okay though.
 
Nathan

Oh! Yes, I see now. Thanks for pointing me in the right direction!

---

### Post by bilijoe on 2008-03-25
I'm still perplexed by the "play when loaded" feature for [standard] DVD movies.  A post by tagra123 back in January of 2007 brought me closer to resolving this issue, but also brought up some interesting questions in the process.  The post suggested using "gconf-editor", navigating to the volume manager and changing the "autoplay DVD" command to "/usr/bin/vlc dvd://".  I later found that "vlc %m" produced better results, but that is actually beside the point.  I'll leave out the reasoning that got me there, but since I still was not getting the [exact] results I wanted, I decided to log in as ROOT, and try some things I seemed to be unable to do, as myself.  Please spare me the lectures, I am fully aware of the significant dangers of logging in as ROOT.  I strongly advise anyone who doesn't truly know exactly what they're doing (and, more importantly, what they should NOT do), to stay the H___ out of ROOT mode.  So, now I feel the need to justify accessing my system in ROOT mode.  Twelve years ago, I was, for five years, the primary administrator for a small UNIX system.  Unfortunately, since then, I have forgotten a surprising amount, but I remember enough to know how much damage can be done with a very few keystrokes by a ROOT user--so I exercise an appropriate degree of care.  So, with abundant care, I logged in as ROOT, and executed "gconf-editor".  The "autoplay DVD" command was (of course) still the default "totem %M", so I changed it, this time to "vlc %m" and closed the editor.  The first thing I noticed was that, when I loaded a DVD, the icon included a red banner, identifying the disc as a DVD Movie.  The name of the movie was, as before, shown below the icon.  No sooner had I noticed this, than the VLC window opened and the movie began to play.  Eureka!  Except it was in a tiny little window--not full screen, as I had hoped.  Well, at least it was an improvement.  So I got the H___ out of ROOT mode, changed the "autoplay DVD" command for my login to "vlc %m", and inserted a disc.  But nothing had changed!  The icon did NOT identify the disc as a DVD Movie--it was just the generic disc icon,  And the VLC player opened in its collapsed mode (i.e., no "screen" area, just the controls).  Although, in previous tries, nothing had happened, I decided, for some reason, to click on the Play button.  BAM!  The movie began playing instantly, and in full screen mode.  So help me out here, oh Linux Gurus of the CyberSpace Realm; how do I combine these two behaviors?  Logged in as ROOT, the system recognizes and identifies the disc as a DVD Movie, and starts it playing--in a little tiny box on the screen.  Logged in as a normal user, the system sees only a DVD--it apparently doesn't know what kind, and it pops up its default DVD player, but just lets it sit there.  If I, knowing that the disc contains a movie, click "Play" I immediately get the result I want (i.e., the movie playing in full screen mode), but I have had to intervene.  How does the ROOT environment know the disc is a Movie, and therefore begin playing it, all on its own, but not have the sense to invoke full screen mode, and why does the normal user environment fail to recognize the disc as a Movie, but still have the good sense to default to full screen mode, should someone tell VLC to play the thing.  Some entry in some file, somewhere will make this all good.  Anybody know what that is?  And, just as an aside, does anyone know if there is a list somewhere that lists the myriad of configuration files, and what they all pertain to--a "list of lists"?  Knowledge is a powerful thing, but only if you posses it, and only if it's accurate.  I know I've diverged a bit in this post, and it's been long and wordy--and I apologize.  But I have ADD, and the rambling comes with the territory.  Thank you to those of you who stuck with me, and I hope the essence of what I am asking didn't get buried within all the babble.  And I hope someone can answer my questions.

---

### Post by ubuntu-freak on 2008-03-25
Are you running Hardy or Gutsy? I'm not aware of any problems in Gutsy. Did you execute gconf-editor with "gksudo"? I will do some tests later or tomorrow and see what I come up with.
 
Nathan

---

### Post by bilijoe on 2008-03-26
I'm using Gusty.  I did not use gksudo, either when running the command as ROOT or as myself.  The thing I am most curious about is why, when I am logged in as ROOT, is the DVD recognized as a DVD Movie (and therefore handled differently); when I am logged in as myself, the DVD is recognized only as a (data?) DVD.:confused:

---

### Post by Kivech on 2008-03-26
Well, for the sake of change I'm currently trying the Kubuntu Hardy beta. It seems that quite a few files have changed and the guide does require quite a bit of manual adjustment.
I don't have the chance to compile a list like that now, but later today I'll see if I can take a moment to create a change list (listing obsolete files and their replacements at the current stage of beta).

I'm facing one challenge though:

The Amarok player by default seems to be using the xine engine. Now on my system xine doesn't do a proper job on playing the sound of .wav and .mov files. The sound is all crackling and really very poor quality.

Does anyone know if there is a way to solve this sound playback problem. Streaming and such work fine though, so it probably has to do with particular codecs/plugins.

I do remember that with Ubuntu 7.10 I had the same problem at some point using the xine plugin for Totem. Once I got rid of that the gstream plugin worked much better. I'm actually hoping there is a similar alternative for Amarok under KDE as well.

I'm running the 64 bits version of Kubuntu Hardy btw.

Any help would be highly appreciated.

Kivech

---

### Post by ubuntu-freak on 2008-03-26
> **bilijoe said:**
> I'm using Gusty.  I did not use gksudo, either when running the command as ROOT or as myself.  The thing I am most curious about is why, when I am logged in as ROOT, is the DVD recognized as a DVD Movie (and therefore handled differently); when I am logged in as myself, the DVD is recognized only as a (data?) DVD.:confused:

 
Well it did say to start gconf-editor with gksudo, so I'm not sure why you didn't. I'm gonna do it today cos I have a laptop to setup, I'll let you know what my results are. 
 
Nathan

---

### Post by ubuntu-freak on 2008-03-26
> **bilijoe said:**
> I'm using Gusty.  I did not use gksudo, either when running the command as ROOT or as myself.  The thing I am most curious about is why, when I am logged in as ROOT, is the DVD recognized as a DVD Movie (and therefore handled differently); when I am logged in as myself, the DVD is recognized only as a (data?) DVD.:confused:

 
Try this thread;
 
[http://ubuntuforums.org/showthread.php?p=4580595](http://ubuntuforums.org/showthread.php?p=4580595)
 
Be careful though, and read the whole thread before trying the solutions. I can't test them at the moment.
 
Nathan

---

### Post by ubuntu-freak on 2008-03-26
> **Kivech said:**
> Well, for the sake of change I'm currently trying the Kubuntu Hardy beta. It seems that quite a few files have changed and the guide does require quite a bit of manual adjustment.
I don't have the chance to compile a list like that now, but later today I'll see if I can take a moment to create a change list (listing obsolete files and their replacements at the current stage of beta).

I'm facing one challenge though:

The Amarok player by default seems to be using the xine engine. Now on my system xine doesn't do a proper job on playing the sound of .wav and .mov files. The sound is all crackling and really very poor quality.

Does anyone know if there is a way to solve this sound playback problem. Streaming and such work fine though, so it probably has to do with particular codecs/plugins.

I do remember that with Ubuntu 7.10 I had the same problem at some point using the xine plugin for Totem. Once I got rid of that the gstream plugin worked much better. I'm actually hoping there is a similar alternative for Amarok under KDE as well.

I'm running the 64 bits version of Kubuntu Hardy btw.

Any help would be highly appreciated.

Kivech

 
KDE dropped support for GStreamer, so not much you can do except switch back to Ubuntu.
 
Nathan

---

### Post by Kivech on 2008-03-27
> **reassuringlyoffensive said:**
> KDE dropped support for GStreamer, so not much you can do except switch back to Ubuntu.
 
Nathan

Thanks for the feedback Nathan. I really do like the KDE desktop over Gnome, so I guess I'll have to see if there's anything I can do with Xine.

I'm a bit occupied at the moment, but I do owe you the change list still. One of these days I'll post it here.

Kivech

---

### Post by ubuntu-freak on 2008-03-27
Made some changes to the streaming section, should be even clearer now. Also, I haven't even installed RealPlayer on my new system, the MPlayer plugins are working wonderfully at the moment.
 
Nathan

---

### Post by anaconda on 2008-03-28
> **reassuringlyoffensive said:**
> 
[COLOR="DarkRed"]**Hardy Heron Users:**[/COLOR] For now, you will have to add the repositoriess manually, which is actually quite easy. First of all, you need to open the sources file with your default or favourite text editor (replace "gedit" with "kwrite" in Kubuntu and "mousepad" in Xubuntu;

Hi,
It seems that this special step is no longer necessary for hardy heron users! 
Medibuntu has added the hardy.list file and now this command works!
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
like it does for other ubuntu versions..

---

### Post by ubuntu-freak on 2008-03-28
> **anaconda said:**
> Hi,
It seems that this special step is no longer necessary for hardy heron users! 
Medibuntu has added the hardy.list file and now this command works!
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
like it does for other ubuntu versions..

 
Thanks for letting me know.
 
Nathan

---

### Post by ubuntu-freak on 2008-03-28
I've edited the medibuntu instructions and added some intructions to make installing Adobe Flash much easier for both 32-Bit and 64-Bit users who are having issues with it.
 
Nathan

---

### Post by JermainWijnhard on 2008-03-28
The script didn't work for me. I took a look at it and noticed it does a lot of stuff with /usr/lib/mozilla/

Problem is i don't have a dir called /usr/lib/mozilla, i do have /usr/lib/firefox

Do i just make the dir? or do i replace all mentions of mozilla in the script with firefox?

I run Kubuntu 7.10 btw.

---

### Post by ubuntu-freak on 2008-03-28
> **JermainWijnhard said:**
> The script didn't work for me. I took a look at it and noticed it does a lot of stuff with /usr/lib/mozilla/

Problem is i don't have a dir called /usr/lib/mozilla, i do have /usr/lib/firefox

Do i just make the dir? or do i replace all mentions of mozilla in the script with firefox?

I run Kubuntu 7.10 btw.

 
You don't have a /usr/lib/mozilla directory? That's not right at all. Yes, try creating it and run the script again;
 
**sudo mkdir /usr/lib/mozilla/plugins** 
 
Nathan

---

### Post by JermainWijnhard on 2008-03-28
no succes, here&#347; the output on the ls -al outputs

"ls -al /usr/lib/mozilla/plugins> somefile && ls -al /usr/lib/firefox/plugins>> somefile" gives the following output:

```
total 12
drwxr-xr-x 2 jermain users 4096 2008-03-29 00:04 .
drwxr-xr-x 3 root    root  4096 2008-03-29 00:03 ..
lrwxrwxrwx 1 jermain users   60 2008-03-29 00:04 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
total 20
drwxr-xr-x 2 jermain users 4096 2008-03-28 21:57 .
drwxr-xr-x 5 root    root  4096 2008-03-28 21:02 ..
-rw-r--r-- 1 jermain users 9104 2008-03-25 16:27 libunixprintplugin.so

```

---

### Post by ubuntu-freak on 2008-03-28
Have you asked Kilz? I don't have a clue what's wrong to be honest.
 
Nathan

---

### Post by GlennW on 2008-03-29
Hi Nathan,
This is an awesome how-to that you've put together. I've just run through the first page (which I have done many times in an effort to try and vet my problem(s)). No errors that I can see.

Symptoms: Youtube - clip will load only 35-37 seconds of material, play it then stop. Nothing I do at that point will cause it to continue loading and subsequently play.

I can, however, upon entering the youtube url, cause the entire clip to load by hitting pause. Only then can I watch the clip in its entirety.

Symptoms: Streaming video - MPlayer opens as full screen but stream shows up in upper left hand corner 1.5 x 2.5 inches. It plays 5-7 seconds and then buffers for 5. This pattern is repeated for approximately 35-37 seconds and then quits.

The only way to watch the stream is to download the whole thing and watch it on the desktop

The bizarre thing is that under feisty I had fantastic flash and streaming experiences. Full screen, high res, basically one click and watch. This has become an exercise in futility for me since everything that I attempt results in the aforementioned foolishness or poorer playback.

I'm still quite the newb and, at this point, knew enough to be dangerous.

---

### Post by ubuntu-freak on 2008-03-29
GlennW, 
 
Did you try installing Flash manually? You may notice better performance, others have.
 
Is MPlayer using the Xvideo (xv) driver for playback? Only with x11 have I noticed that problem you mentioned.
 
Nathan

---

### Post by bw44 on 2008-03-29
> **reassuringlyoffensive said:**
> Made some changes to the streaming section, should be even clearer now. Also, I haven't even installed RealPlayer on my new system, the MPlayer plugins are working wonderfully at the moment.
 
NathanSince you first posted your HowTo, you've blown hot and cool on RealPlayer vs mplayer. :)

I've ways wanted to use mplayer if possible, but finally had to install RealPlayer (as per your instructions)  to access the BBC news site video streams.  RealPlayer works passably well since BBC fixed their problems of imbedded playback, but it still resets my (admittedly dodgy, as in "unreliable") sound chip volume settings, while mplayer doesn't.

I can link to the BBC videos with mplayer and it downloads and plays the soundtrack but not the video stream.  I know this is revisiting an old problem, but have you had any further experience or thoughts about what I might try? (Hopefully, though It may well be a problem at the Beeb's end.)

Thanks.

---

### Post by ubuntu-freak on 2008-03-29
> **bw44 said:**
> Since you first posted your HowTo, you've blown hot and cool on RealPlayer vs mplayer. :)

I've ways wanted to use mplayer if possible, but finally had to install RealPlayer (as per your instructions)  to access the BBC news site video streams.  RealPlayer works passably well since BBC fixed their problems of imbedded playback, but it still resets my (admittedly dodgy, as in "unreliable") sound chip volume settings, while mplayer doesn't.

I can link to the BBC videos with mplayer and it downloads and plays the soundtrack but not the video stream.  I know this is revisiting an old problem, but have you had any further experience or thoughts about what I might try? (Hopefully, though It may well be a problem at the Beeb's end.)

Thanks.

 
Hey man, not seen you round these parts for a while. :-)
 
Well, the thing is, MPlayer is streaming RM content on the BBC site fine with the streams I've tested, and embedded too. Also, they are phasing them out anyway, except with the radio streams. 
 
Nathan
 
Edit: I will test their news streams soon, I actually only tested programme previews last week.

---

### Post by bw44 on 2008-03-29
> **reassuringlyoffensive said:**
> Hey man, not seen you round these parts for a while. :-)
 
Well, the thing is, MPlayer is streaming RM content on the BBC site fine with the streams I've tested, and embedded too. Also, they are phasing them out anyway, except with the radio streams. 
 
Nathan
 
Edit: I will test their news streams soon, I actually only tested programme previews last week.Nah, been lying low -- had other issues. :(  -- nice of you to notice.

But what you said made a light go on!  One's got two ways to  access the BBC videos with mplayer.  The first way is to tell their NewsPlayer that you're using Windows format, which causes mplayer to launch handling the .wmv stream.  That's what (still) doesn't work for me.

The other way is to set the  BBC NewsPlayer preferences to RealPlayer, but turn on the mplayer configuration parameters to handle .rm streams.  Bet that's what you're doing, yes?  But tell me (since I've obviously forgotten), is there  a way to disable RealPlayer plugin without completely removing it, so I can test mplayer but drop back to  RealPlayer if necessary?

And, yeah, I noticed that BBC is moving video clips over to Flash.

Thanks.

---

### Post by ubuntu-freak on 2008-03-29
Course I noticed, you've helped people in this thread too.
 
Anyways, back to the macho-geek stuff. Why not do an alt+f2, type in "gksudo nautilus", then press enter and type in your password. Navigate to /usr/lib/firefox/plugins and then rename those nphelix plugins. Or do it via the Terminal I guess. (sudo mv /usr/lib/firefox/plugins/nphelix.so /usr/lib/firefox/plugins/nphelix.sodoff). Same with xpt as well. Don't forget to delete the pluginreg.dat.
 
Nathan
 
P.S. Like my new sig?;-)

---

### Post by bw44 on 2008-03-29
> **reassuringlyoffensive said:**
> Course I noticed, you've helped people in this thread too.
 
Anyways, back to the macho-geek stuff. Why not do an alt+f2, type in "gksudo nautilus", then press enter and type in your password. Navigate to /usr/lib/firefox/plugins and then rename those nphelix plugins. Or do it via the Terminal I guess. (sudo mv /usr/lib/firefox/plugins/nphelix.so /usr/lib/firefox/plugins/nphelix.sodoff). Same with xpt as well. Don't forget to delete the pluginreg.dat.
 
Nathan
 
P.S. Like my new sig?;-)Like the new avatar! :guitar:

Good refresher course.  As I went through the process following your suggestion things came back to me. ( nphelix.sodoff :))

Unfortunately, no joy.  But I'm convinced the problem is still with the way the BBC is including ads in the streams for us non-UK residents (or maybe a problem with their way of doing things plus a difference between Linux mplayer and Windows MP, since the clips play OK with Firefox under XP).  If I doctor the BBC URLs to take out the bit that links to their advertisements, mplayer plays the clips fine (but as wmv, not rm streams? hmm, I should check that, not that it really matters.)

So, reluctantly, it's back to RealPlayer.

bw44

PS.  I checked, and mplayer is currently handling the .rm stream fine (and I strongly suspect will handle the .wvm stream with no problem as well. It's something in the confounded BBC set-up.)  I haven't checked the audio streams yet.

---

### Post by GaryUK on 2008-03-30
Nathan,

Great Howto - many thanks!

I used some of your information to resolve my problem with Flash not working on the BBC site.

1) Found that "about:plugins" was showing Flash 7 still as well as Flash 9 and no amount of removal of the pluginreg.dat seemed to change that.

2) Purged Flash 9 as instructed and then removed/renamed the libflashplayer.so from /usr/lib/firefox and also from $home/.mozilla/plugins. Also removed the flashplayer.xpt from the same directory and also from /usr/lib/firefox/components directory (that I had put there in the first place).

3) Rebooted and checked "about:plugins" - no flash player except Gnash and, most importantly, no Flash 7.

4) In the install_flash_player_9_linux directory that I had got from a manual install, ran the   Flash install script as root, setting the install directory as /usr/lib/firefox.

5) Checked for the pluginreg.dat file and removed it and then rebooted.

6) After rebooting, checked the "about:plugins" and found that only Flash 9 showing now so went to the BBC site and checked the video stream not working and found that it now worked. I can only assume that the BBC site was getting confused when there seemd to be 2 Flash entries in the "about:plugins" page on FF.

Many thanks again and I hope this helps someone.

Gary

---

### Post by GlennW on 2008-03-30
> **reassuringlyoffensive said:**
> GlennW, 
 
Did you try installing Flash manually? You may notice better performance, others have.
 
Is MPlayer using the Xvideo (xv) driver for playback? Only with x11 have I noticed that problem you mentioned.
 
Nathan

Thanks for the response. Do tell as to do a manual install and I'm on it. Also, I've noticed that you and others push xv as the preferred driver. I've tried to use it by changing to it in MPlayer's config box but then playback is the worst. GL playback is somewhat better and x11 is the best of the three but still is terrible.

Suggestions?

---

### Post by ubuntu-freak on 2008-03-30
> **GlennW said:**
> Thanks for the response. Do tell as to do a manual install and I'm on it. Also, I've noticed that you and others push xv as the preferred driver. I've tried to use it by changing to it in MPlayer's config box but then playback is the worst. GL playback is somewhat better and x11 is the best of the three but still is terrible.

Suggestions?

 
Part 1 of my how-to includes instructions for a manual Adobe Flash installation.
 
Xv is best as your GPU handles video processing rather than your CPU. What graphics device do you have? You may need to change your driver, as most chipsets do actually support Xvideo, even if it doesn't work from the outset.
 
Nathan

---

### Post by GlennW on 2008-03-30
> **reassuringlyoffensive said:**
> Part 1 of my how-to includes instructions for a manual Adobe Flash installation.
 
Xv is best as your GPU handles video processing rather than your CPU. What graphics device do you have? You may need to change your driver, as most chipsets do actually support Xvideo, even if it doesn't work from the outset.
 
Nathan

Hi Nathan,

I've already done the manual Adobe Flash install. I have an nVidia Geforce 6200 256MB video card. I would think that should be adequate for this. I must point out that under Feisty there was no issue whatsoever. I'm really at a loss. How can I upgrade the driver to xv?

---

### Post by ubuntu-freak on 2008-03-30
> **GlennW said:**
> Hi Nathan,

I've already done the manual Adobe Flash install. I have an nVidia Geforce 6200 256MB video card. I would think that should be adequate for this. I must point out that under Feisty there was no issue whatsoever. I'm really at a loss. How can I upgrade the driver to xv?

 
Do Totem and VLC work? They are set to xv by default. You should be able enjoy xv no problem, strange. How did you install your graphic driver? How long ago did you install Gutsy? If you used the Restricted Drivers Manager, you could always try disabling the driver in there, reboot, then install the NVIDIA driver with Envy. Have a look at the NVIDIA Sticky thread.
 
Nathan

---

### Post by forceofnature on 2008-03-30
This instructional helped me but all of a sudden I have no ability to play back DVD's.  This just happened today.  Totem says it is encrypted.  VLC doesn't respond and Mplayer locked up.  Anyone else have issues recently?

Here is my VLC output.  I noticed that my libdvdcss2 updated today is that the issue??

VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread patched to play DVDs with DVD-Movie-Protect
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: DVD_VIDEO
libdvdnav: DVD Serial Number: 2E3580ED
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/kevin/.dvdnav/DVD_VIDEO.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000200
libdvdread: Error cracking CSS key for /VIDEO_TS/VIDEO_TS.VOB (0x00000200)
libdvdread: Elapsed time 4
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000035a0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x000035a0)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0001c0c0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x0001c0c0)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001ac360
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_0.VOB (0x001ac360)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001ac380
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x001ac380)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x001c1060
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x001c1060)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001c1080
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x001c1080)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x001d8a60
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_0.VOB (0x001d8a60)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x001d8a80
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x001d8a80)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x001e4d80
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_0.VOB (0x001e4d80)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x001e4da0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_1.VOB (0x001e4da0)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00375c60
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_06_0.VOB (0x00375c60)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00375c80
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_06_1.VOB (0x00375c80)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00375e20
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_07_0.VOB (0x00375e20)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00375e40
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_07_1.VOB (0x00375e40)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x0037ccc0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_0.VOB (0x0037ccc0)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x0037cce0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_1.VOB (0x0037cce0)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x003924e0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_09_0.VOB (0x003924e0)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x00392500
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_09_1.VOB (0x00392500)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x003a5e80
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_10_0.VOB (0x003a5e80)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x003a5ea0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_10_1.VOB (0x003a5ea0)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x003b0160
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_11_0.VOB (0x003b0160)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x003b0180
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_11_1.VOB (0x003b0180)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x003ba520
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_12_0.VOB (0x003ba520)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x003ba540
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_12_1.VOB (0x003ba540)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_0.VOB at 0x003c46c0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_13_0.VOB (0x003c46c0)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x003c46e0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_13_1.VOB (0x003c46e0)!!
libdvdread: Elapsed time 0
libdvdread: Found 13 VTS's
libdvdread: Elapsed time 7
[00000281] main playlist: nothing to play

---

### Post by ubuntu-freak on 2008-03-31
forceofnature,

Try running this command from Part 4 again;

**sudo /usr/share/doc/libdvdread3/install-css.sh**

---

### Post by forceofnature on 2008-03-31
This is what I get from re-running that command.  Still no video playback.  After I ran the command it went and wanted to upgrade again to libdvdcss2 1.2.9-2

--07:01:26--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb)
           => `/tmp/dvdcss-VZ6330/libdvdcss.deb'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 25,178 (25K) [text/plain]

100%[====================================>] 25,178        90.40K/s             

07:01:27 (90.35 KB/s) - `/tmp/dvdcss-VZ6330/libdvdcss.deb' saved [25178/25178]

dpkg - warning: downgrading libdvdcss2 from 1.2.9-2medibuntu4 to 1.2.5-1.
(Reading database ... 120092 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.9-2medibuntu4 (using .../dvdcss-VZ6330/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.5-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

---

### Post by mc4man on 2008-03-31
@ force of nature
your problem should be easily solved, for the moment stick with whatever version of libdvdcss2 you have.
If you are not in region 1 post what region
If you want to post the name of title from previous post (dvd_video) it will be easy to ck. if the key addresses are correct
In the mean time go to home folder, find .dvdcss (hidden), open it up and look for a folder named dvd_video, and delete it - if there is more than one with same name delete them all
then try vlc again
if you feel your better with one particular ver. of libdvdcss2 then you can probably force that ver. in synaptic or go here and pick  [http://download.videolan.org/pub/libdvdcss/](http://download.videolan.org/pub/libdvdcss/)

---

### Post by forceofnature on 2008-03-31
> **mc4man said:**
> @ force of nature
your problem should be easily solved, for the moment stick with whatever version of libdvdcss2 you have.
If you are not in region 1 post what region
If you want to post the name of title from previous post (dvd_video) it will be easy to ck. if the key addresses are correct
In the mean time go to home folder, find .dvdcss (hidden), open it up and look for a folder named dvd_video, and delete it - if there is more than one with same name delete them all
then try vlc again
if you feel your better with one particular ver. of libdvdcss2 then you can probably force that ver. in synaptic or go here and pick  [http://download.videolan.org/pub/libdvdcss/](http://download.videolan.org/pub/libdvdcss/)

I tried deleting the files in .dvdcss and still get the same issue.  I also changed the libdvdcss2 version to the one that I had working in the past and that did not help either.  I am not sure what I did that could have caused it to stop playing DVD's.  I was just watching one the night before last.  The only changes I had made to the system was to enable compiz to show a coworker what that desktop candy looked like.  In fact I enabled it while watching the DVD and had no issues at that time.  

I typically dont use all the compiz features I have it enabled so I can use emerald so my appearance preferences are set to normal.

---

### Post by forceofnature on 2008-03-31
I tried one more desperate attempt by removing everything from  DVD playback tutorial,  then reinstalling and still getting the same errors.

I forgot to post that I am region 1 and set the region to 1.

---

### Post by bw44 on 2008-03-31
> **reassuringlyoffensive said:**
> . . .
Nathan [wrote:]
Like my new sig?;-)

It's great -- a tutorial in itself!  But I'm so used to ignoring signatures I didn't notice the change to it at first -- just your new avatar.
 
New posters to the thread will probably be more observant.

Cheers.

---

### Post by Tobs1 on 2008-03-31
Hi I tried out your **Part 4/5 DVD Playback/Ripping/Burning---** I was only interested in the Playback side of things however It all went well,
I could put a DVD in my drive and up would come Movie Player and the DVD would start playing, Happy Happy It all works fine.
However I was having a problem with my DVD ROM drive sometimes the drawer would open a bit and stick and I had to help it the rest of the way out and also when I would shut the drawer I had to to help it close completely, So I thought I would get a new DVD ROM Drive, I did that and thought everything would work fine, But now when I  put a DVD in my drive I get VLC Media Player coming up and then another box with errors  [COLOR="Red"]unable to open "DVD://"[/COLOR],
I then tried to mount the drive but got Unable to Mount Drive or there is no media
in the drive, Ho no I have a bad DVD ROM Drive I will return it to the store But just to make sure I put my old drive back in ( the one with the sticky drawer ) I then put my DVD in and although I could mount the drive I still got  VLC Media Player coming up and then another box with errors  [COLOR="Red"]unable to open "DVD://"[/COLOR],  So No 1 I think my new Drive is faulty and I will return it
But why am I still getting this problem with VLC when all I did was change the drive, I will get another DVD ROM Drive But I want things to work as they did before  Hope you can Help me  Thanks Tobs

---

### Post by stay gold! on 2008-03-31
Every time I come back to Ubuntu/fresh install this is the first guide I follow.

Works every time thanks :D

---

### Post by ubuntu-freak on 2008-03-31
> **bw44 said:**
> It's great -- a tutorial in itself!  But I'm so used to ignoring signatures I didn't notice the change to it at first -- just your new avatar.
 
New posters to the thread will probably be more observant.

Cheers.

 
Just to let you know, the BBC news clips work for me with the MPlayer plugin, both embedded and in stand-alone mode. Must be due to the adverts that you have trouble with them, MPlayer doesn't seem to like more than one playlist.
 
Nathan

---

### Post by TorqueyPete on 2008-03-31
Well something must be wrong, because suddenly it's all working! \\:D/
 I've been occasionally coming back to this thread and running right through all the instructions. But this time I stopped as soon as I'd run the purge flash and reinstall bit. And now I'm watching Youtube  and BBC 's vids, apparently without probs for the first time in several weeks! :confused: :):KS=D>

So if it behaves itself, even vaguely, I'll never mess with it again!  [-X


Donuts all round I think!

---

### Post by bw44 on 2008-03-31
> **reassuringlyoffensive said:**
> Just to let you know, the BBC news clips work for me with the MPlayer plugin, both embedded and in stand-alone mode. Must be due to the adverts that you have trouble with them, MPlayer doesn't seem to like more than one playlist.
 
NathanThanks for  letting me know.  Wish I had a UK/EU passport!

---

### Post by ubuntu-freak on 2008-03-31
Tobs 1,
 
I'm not sure what's going on there. Maybe you could try running that install-css.sh command again and let it re-update afterward.
 
stay gold!,
 
Thanks, glad you find it useful.
 
Nathan

---

### Post by TorqueyPete on 2008-04-01
> **reassuringlyoffensive said:**
> Just to let you know, the BBC news clips work for me with the MPlayer plugin, both embedded and in stand-alone mode. Must be due to the adverts that you have trouble with them, MPlayer doesn't seem to like more than one playlist.
 
Nathan

Yeap, that's true for me, even when I select Realplayer from the options. And I watched a 1hour Tigers in the jungle prog on the BBC's iplayer. I do get a little 'skipping' every few mins with everything I'm viewing, but I'm not complaining. ;)

---

### Post by bw44 on 2008-04-01
> **reassuringlyoffensive said:**
> Just to let you know, the BBC news clips work for me with the MPlayer plugin, both embedded and in stand-alone mode. Must be due to the adverts that you have trouble with them, MPlayer doesn't seem to like more than one playlist.

> **TorqueyPete said:**
> Yeap, that's true for me, even when I select Realplayer from the options. And I watched a 1hour Tigers in the jungle prog on the BBC's iplayer. I do get a little 'skipping' every few mins with everything I'm viewing, but I'm not complaining. ;)

Just keep rubbing it in, guys! :)

(Actually, it's good to hear another UK BBC viewer confirm Nathan's remark -- I keep (kept) thinking if I just fiddled with the mplayer configuration settings enough I could get it to work.  Sigh.)

Cheers, and thanks (really!).

bw44

---

### Post by ubuntu-freak on 2008-04-01
> **bw44 said:**
> Just keep rubbing it in, guys! :)

(Actually, it's good to hear another UK BBC viewer confirm Nathan's remark -- I keep (kept) thinking if I just fiddled with the mplayer configuration settings enough I could get it to work.  Sigh.)

Cheers, and thanks (really!).

bw44

 
Maybe you could contact the MPlayer people and tell them the plugin doesn't like the stream to contain more than one playlist. I would have thought they knew by now though. Strange.
 
Nathan

---

### Post by bw44 on 2008-04-01
> **reassuringlyoffensive said:**
> Maybe you could contact the MPlayer people and tell them the plugin doesn't like the stream to contain more than one playlist. I would have thought they knew by now though. Strange.
 
NathanI think I did long ago (before you posted your HowTo), and I'm pretty sure I never got a reply. But I'll try again.

bw44

---

### Post by bw44 on 2008-04-01
> **reassuringlyoffensive said:**
> Maybe you could contact the MPlayer people and tell them the plugin doesn't like the stream to contain more than one playlist. I would have thought they knew by now though. Strange.
 
NathanWell I reported the problem to the mplayer project, and learned the mplayer-plugin is a different project/application from mplayer  (which I probably should have known, but didn't).

Anyway, the person who kindly responded wrote:> Also, mplayerplug-in is being decommissioned and being replaced with gecko-mediaplayer/gnome-mplayer. Those apps will [handle?] just about everything at the BBC even in real player mode. He said to check these sites for more information:> gnome-mplayer

[http://groups.google.com/group/gnome-mplayer](http://groups.google.com/group/gnome-mplayer)

gecko-mediaplayer

[http://groups.google.com/group/gecko-mediaplayer](http://groups.google.com/group/gecko-mediaplayer)Had you heard anything about  mplayerplug-in being "decomissioned?"

With mplayerplugin going and BBC moving to Flash, I guess I'll just lie low 'til the dust settles!

---

### Post by ubuntu-freak on 2008-04-01
> **bw44 said:**
> Well I reported the problem to the mplayer project, and learned the mplayer-plugin is a different project/application from mplayer  (which I probably should have known, but didn't).

Anyway, the person who kindly responded wrote: He said to check these sites for more information:Had you heard anything about  mplayerplug-in being "decomissioned?"

With mplayerplugin going and BBC moving to Flash, I guess I'll just lie low 'til the dust settles!

 
I don't see how the plugins or the main app can be decomissioned. I've installed GNOME MPlayer and it's merely a frontend for MPlayer, with less GUI configuration options (cos it's GNOME). Nope, I don't buy it.
 
Nathan

---

### Post by bw44 on 2008-04-01
> **reassuringlyoffensive said:**
> I don't see how the plugins or the main app can be decomissioned. I've installed GNOME MPlayer and it's merely a frontend for MPlayer, with less GUI configuration options (cos it's GNOME). Nope, I don't buy it.
 
NathanI won't argue. However, the guy who answered my inquiry is listed as the author of the plugin on the following page: [http://mplayerplug-in.sourceforge.net/authors.php](http://mplayerplug-in.sourceforge.net/authors.php).  Maybe there's a political angle, but I have no reason (other than your scepticism :) ) to doubt him.

He might think I'm implying he tells falsehoods if I follow up with questions at that site.  Maybe someone else could inquire about whether there are any plans for further development of the mplayer plugin.

I'll await developments.

---

### Post by ubuntu-freak on 2008-04-01
> **bw44 said:**
> I won't argue. However, the guy who answered my inquiry is listed as the author of the plugin on the following page: [http://mplayerplug-in.sourceforge.net/authors.php](http://mplayerplug-in.sourceforge.net/authors.php).  Maybe there's a political angle, but I have no reason (other than your scepticism :) ) to doubt him.

He might think I'm implying he tells falsehoods if I follow up with questions at that site.  Maybe someone else could inquire about whether there are any plans for further development of the mplayer plugin.

I'll await developments.

 
Well, GNOME MPlayer needs MPlayer, as it's just a simple alternative frontend for MPlayer. If developement of the plugins is switching to another dev or devs, I just hope they keep the option to configure it. I'm sure they will though, GNOME is configurable, it's just hidden (gconf-editor).
 
I doubt we have much to worry about, just some packages to rename in my how-to at some point in the future.
 
Nathan

---

### Post by collinp on 2008-04-01
Hello. I love your guide, and most of it works right. The one problem that i am having is when i try to intall the dvd player thing, this command: 
**sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 build-essential debhelper fakeroot . **[FONT=Arial]When i try it, i get this error: 
"Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate".
 [/FONT]

---

### Post by ubuntu-freak on 2008-04-01
> **Hellow said:**
> Hello. I love your guide, and most of it works right. The one problem that i am having is when i try to intall the dvd player thing, this command: 
**sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 build-essential debhelper fakeroot . **[FONT=Arial]When i try it, i get this error: 
"Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate".
 [/FONT]

 
Hmm.,did you add the medibuntu repo from part 1? Were the packages from part 1 installed properly?
 
Nathan

---

### Post by bw44 on 2008-04-01
> **reassuringlyoffensive said:**
> Well, GNOME MPlayer needs MPlayer, as it's just a simple alternative frontend for MPlayer. If developement of the plugins is switching to another dev or devs, I just hope they keep the option to configure it. I'm sure they will though, GNOME is configurable, it's just hidden (gconf-editor).
 
I doubt we have much to worry about, just some packages to rename in my how-to at some point in the future.
 
NathanI wasn't worried, but my curiosity got the better of me, so I poked around and discovered that the author of the mplayer plugin, Kevin DeKorte has developed an alternative to it called the gecko-mediaplayer.  Gnome Mplayer (which he also authored)  is teamed with gecko-mediaplayer to provide the functionality of the mplayer plugin (plus more or better, I assume.)  

Here is his gecko-mediaplayer home site:  [http://dekorte.homeip.net/download/gecko-mediaplayer/](http://dekorte.homeip.net/download/gecko-mediaplayer/)  in case anyone else is curious.

As the principle author/supporter of the mplayer plugin, Kevin seems to be working very hard at its replacement.  I guess that's what he meant when he said that the mplayer plugin was being "decommissioned."

I don't know when it will be packaged for distribution to Debian/Ubuntu, but, as you say, it can probably be included in your HowTo (if judged worthy!) when it's ready for prime time.

---

### Post by GlennW on 2008-04-01
> **reassuringlyoffensive said:**
> Do Totem and VLC work? They are set to xv by default. You should be able enjoy xv no problem, strange. How did you install your graphic driver? How long ago did you install Gutsy? If you used the Restricted Drivers Manager, you could always try disabling the driver in there, reboot, then install the NVIDIA driver with Envy. Have a look at the NVIDIA Sticky thread.
 
Nathan

Hi Nathan,

Totem and VLC don't work either. I upgraded Feisty to Gutsy maybe a month after it was released and had no real significant problems. Gutsy recognized my nvidia card and monitor resolution was spot on. I did install nVidia via envy. The fact that flash and streaming has worked in the past (fullscreen too) indicates to me that it may be a simple setting issue but I have no idea where to look. I guess that's why I need the expertise of you and the others on this forum. I need to have this resolved. I'm thinking, too, that the Hardy release won't fix the issue especially if it's a setting one.

Thanks.

---

### Post by ubuntu-freak on 2008-04-01
> **GlennW said:**
> Hi Nathan,

Totem and VLC don't work either. I upgraded Feisty to Gutsy maybe a month after it was released and had no real significant problems. Gutsy recognized my nvidia card and monitor resolution was spot on. I did install nVidia via envy. The fact that flash and streaming has worked in the past (fullscreen too) indicates to me that it may be a simple setting issue but I have no idea where to look. I guess that's why I need the expertise of you and the others on this forum. I need to have this resolved. I'm thinking, too, that the Hardy release won't fix the issue especially if it's a setting one.

Thanks.

 
You couldn't install the driver with the RDM? You could always try uninstalling the driver and then install it again, hopefully a newer version. Then execute the "sudo dpkg-reconfigure -phigh xserver-xorg" command (or try that now perhaps). Also, search Google with the keywords "yourcard gutsy ubuntu xv x11".
 
Hope that helps. I'm sure you'll get it working again.
 
Nathan

---

### Post by Payteer on 2008-04-02
Hello,  I have just installed Hardy 8.04  and now some of the guide doesn't work anymore.  As Hardy will be coming out in two weeks, is there anyway of updating some of the guide at the start of the mail for the latest version.  I still find this the best guide for all these things on the forum, it is very easy to follow for an idiot like me on terminal. Thank you, it is so much appreciated.

---

### Post by bw44 on 2008-04-02
> **Payteer said:**
> Hello,  I have just installed Hardy 8.04  and now some of the guide doesn't work anymore.  As Hardy will be coming out in two weeks, is there anyway of updating some of the guide at the start of the mail for the latest version.  I still find this the best guide for all these things on the forum, it is very easy to follow for an idiot like me on terminal. Thank you, it is so much appreciated.Sorry to hear you're having problems. I doubt I can help, but when Nathan has a look at your post he will want to know what features of the guide don't seem to be working.

Could you be more specific about the problems you've encountered?

---

### Post by Kivech on 2008-04-02
> **bw44 said:**
> Sorry to hear you're having problems. I doubt I can help, but when Nathan has a look at your post he will want to know what features of the guide don't seem to be working.

Could you be more specific about the problems you've encountered?
 
Just a quick reply:

In Hardy some of the packages are not included anymore and/or have been substituted by newer versions. The only way to find out which is by entering the name of the package in the package manager and taking away character by character from the end of the name to find any similar hits.
This way one can figure out which packages have been upgraded and which have been ditched. I know that at least one package (don't remember which one) was discarted and is not available anymore nor does it have an upgrade included (at least not that I could find).

I promised to make a list of differences but unfortunately lack the time to do so at the moment.

Kivech

---

### Post by bw44 on 2008-04-02
> **Kivech said:**
> . . . In Hardy some of the packages are not included anymore and/or have been substituted by newer versions. The only way to find out which is by entering the name of the package in the package manager and taking away character by character from the end of the name to find any similar hits.

This way one can figure out which packages have been upgraded and which have been ditched. I know that at least one package (don't remember which one) was discarted and is not available anymore nor does it have an upgrade included (at least not that I could find).

I promised to make a list of differences but unfortunately lack the time to do so at the moment.

KivechI was actually replying to Payteer's last post as he seems to be an early adopter of Hardy as well  -- wasn't trying to bug you! 

Searching back through the thread for your earlier posts I see you are using Kubuntu as well as the newer version.  When you do find  time to work on it again, obviously the more specific you can be about the changed packages or other apparent problems the better. I'm sure it'll be helpful to Nathan (and by extension the rest of us).

I see the official release date for Hardy is only 22 days away!

Cheers.

bw44

---

### Post by ubuntu-freak on 2008-04-02
I've made pretty major changes today. There is a dedicated set of instructions for Hardy Heron users, taking into account the changes regarding some package names and different pakcages being used. I've also added libflashsupport to each Hardy Heron command in Part 1, which should fix the sound problems with Adobe Flash (YouTube videos). I checked to see if it was a dependency and it wasn't (will be at some point, and should be), so I added it to the list.

This is like having a volunteer job sometimes, I guess it is though.;)


Nathan

P.S. There will be other teething problems, so don't use Hardy unless you enjoy having issues and filing bug reports.

---

### Post by bw44 on 2008-04-02
> **reassuringlyoffensive said:**
> I've made pretty major changes today. There is a dedicated set of instructions for Hardy Heron users, taking into account the changes regarding some package names and different pakcages being used. I've also added libflashsupport to each Hardy Heron command in Part 1, which should fix the sound problems with Adobe Flash (YouTube videos). I checked to see if it was a dependency and it wasn't (will be at some point, and should be), so I added it to the list.

This is like having a volunteer job sometimes, I guess it is though.;)

Nathan

P.S. There will be other teething problems, so don't use Hardy unless you enjoy having issues and filing bug reports.Nathan,

I periodically save your HowTo to an OpenOffice file.  When you first posted, it was about 6 pages long.  It's now 14,  and counting.

I hope newcomers to the "Complete Streaming, Multimedia & Video How-to" thread appreciate the tremendous amount of volunteer work this represents.  You're part of what makes Ubuntu such a great Linux distribution.

Thanks again.

---

### Post by ubuntu-freak on 2008-04-02
> **bw44 said:**
> Nathan,

I periodically save your HowTo to an OpenOffice file.  When you first posted, it was about 6 pages long.  It's now 14,  and counting.

I hope newcomers to the "Complete Streaming, Multimedia & Video How-to" thread appreciate the tremendous amount of volunteer work this represents.  You're part of what makes Ubuntu such a great Linux distribution.

Thanks again.

Thanks man.:) 

It was about 1 page though, just a streaming how-to to start with. ;)

Nathan

---

### Post by bw44 on 2008-04-02
> **reassuringlyoffensive said:**
> . . . It was about 1 page though, just a streaming how-to to start with. ;)

NathanI stand corrected!  (and I  thought I had the "first edition"! :()

bw44

---

### Post by Payteer on 2008-04-02
Hello Nathan,  top job,  one thing I have found out is that it is better to un-install realplayer if it still on your system from Gutsy or previous edition and reinstall again and follow it from the start again.  Using your new update for Hardy also works a treat. Even BBC works, and that is saying something.
Cheers
:KS

---

### Post by ubuntu-freak on 2008-04-02
> **Payteer said:**
> Hello Nathan,  top job,  one thing I have found out is that it is better to un-install realplayer if it still on your system from Gutsy or previous edition and reinstall again and follow it from the start again.  Using your new update for Hardy also works a treat. Even BBC works, and that is saying something.
Cheers
:KS

Thanks, glad my bit of research paid off.

I usually do a fresh install each time, that's just me. Not sure when I'm gonna install Hardy to be honest, but I do have to keep this thing up-to-date.

Nathan

---

### Post by ubuntu-freak on 2008-04-02
I'm interested to know how OpenJDK compares with Sun Java in Hardy, for 32-Bit users who are normally Sun Java users. Anyone using it? If you installed the restricted-extras package in Hardy, then you're using OpenJDK. I might change the install command for Hardy users if OpenJDK works almost on par with Sun Java. I posted a thread [here](http://ubuntuforums.org/showthread.php?t=743354) but haven't had any replies yet (shock).

Nathan
 
Edit: I don't want my how-to causing conflicts, some may have installed the icedtea plugin before following my how-to. You can't have both plugins installed.

---

### Post by ezechieljhc on 2008-04-04
I have made the steps described above and the result was that the layout of my Opera browser completely changed. The menus in the Opera toolbars changed, they are smaller and the fonts in the address bar, or on the tabs and inside the menus changed their size to almost unreadable.. also reading the fonts inside the web page area has become more difficult and my eyes hurt after a specific time.. I cant find any solution to this issue.. I dont even know where to begin.. Has anyone of you experienced something like this?

[[IMG]http://img233.imageshack.us/img233/1117/screenshotsg0.th.png[/IMG]](http://img233.imageshack.us/my.php?image=screenshotsg0.png)

---

### Post by ubuntu-freak on 2008-04-04
> **ezechieljhc said:**
> I have made the steps described above and the result was that the layout of my Opera browser completely changed. The menus in the Opera toolbars changed, they are smaller and the fonts in the address bar, or on the tabs and inside the menus changed their size to almost unreadable.. also reading the fonts inside the web page area has become more difficult and my eyes hurt after a specific time.. I cant find any solution to this issue.. I dont even know where to begin.. Has anyone of you experienced something like this?

[[IMG]http://img233.imageshack.us/img233/1117/screenshotsg0.th.png[/IMG]](http://img233.imageshack.us/my.php?image=screenshotsg0.png)

 
I'm not sure what you mean. Which steps did you follow? Also, you can change the minimum font size in Opera's preferences.
 
Nathan

---

### Post by barney_xuf on 2008-04-04
While attempting to set up the sources for medibuntu in the section **Part 1/5 Essential Packages**, I get this error:
E: Type '<!DOCTYPE' is not known on line 2 in source list /etc/apt/sources.list.d/medibuntu.list.

While I'm reasonably competent in the DOS/Windows world much of the command line structure of Linux/Ubuntu is foreign to me.  While I think I can recognize the nature of the error, I'm uncertain how to address it.

Oh, I'm using Ubuntu 7.10, Gnome interface.  And I cannot get *any *streaming media to work in Firefox - gtk-gnash loads, but all it does is max out both CPUs - I don't even get an image, just an empty, faint grey block on the web page.

'Preciate any comments.  I've been researching this, but there's a plethora of material, and only so many hours available to peruse it.

---

### Post by ubuntu-freak on 2008-04-04
> **barney_xuf said:**
> While attempting to set up the sources for medibuntu in the section **Part 1/5 Essential Packages**, I get this error:
E: Type '<!DOCTYPE' is not known on line 2 in source list /etc/apt/sources.list.d/medibuntu.list.

While I'm reasonably competent in the DOS/Windows world much of the command line structure of Linux/Ubuntu is foreign to me.  While I think I can recognize the nature of the error, I'm uncertain how to address it.

Oh, I'm using Ubuntu 7.10, Gnome interface.  And I cannot get *any *streaming media to work in Firefox - gtk-gnash loads, but all it does is max out both CPUs - I don't even get an image, just an empty, faint grey block on the web page.

'Preciate any comments.  I've been researching this, but there's a plethora of material, and only so many hours available to peruse it.

 
Okay here it goes. Firstly, execute this command:
 
**sudo rm /etc/apt/sources.list.d/medibuntu.list** 
 
then update:
 
**sudo apt-get update**
 
Now try and add the Medibuntu repo again. 
 
Nathan 
 
P.S. My Adobe Flash section should help you, just cut and paste the "purge" command, but not the "&&" and onwards, then install Flash manually. Follow part 2 for streaming all other videos in Firefox.

---

### Post by ezechieljhc on 2008-04-05
> **reassuringlyoffensive said:**
> I'm not sure what you mean. Which steps did you follow? Also, you can change the minimum font size in Opera's preferences.
 
Nathan

I followed the instructions in part 1/5, skipped adobe flash installation, proceeded with
"sudo apt-get install alsa-oss compizconfig-settings-manager faad gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 msttcorefonts sun-java6-fonts sun-java6-jre sun-java6-plugin unrar w32codecs" and followed the stepps described in part 2/5 Option 1.

I know that it is possible to change some of the fonts in Opera (I had to increase their size from 10 to 14 since using this How-To, because they became very small), but not those in Opera's interface, I mean menu fonts (file, edit, view...), fonts on the toolbars, tabs, right-click menus and fonts used for http addresses showed inside the address bar. Before they looked like Sans 12, now they changed to perhaps Arial 8...? Other applications are looking the same and working just fine.. I tried to use the qtconfig tool, everything is set to Sans 12, just Opera's interface looks different..

---

### Post by ubuntu-freak on 2008-04-05
> **ezechieljhc said:**
> I followed the instructions in part 1/5, skipped adobe flash installation, proceeded with
"sudo apt-get install alsa-oss compizconfig-settings-manager faad gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 msttcorefonts sun-java6-fonts sun-java6-jre sun-java6-plugin unrar w32codecs" and followed the stepps described in part 2/5 Option 1.

I know that it is possible to change some of the fonts in Opera (I had to increase their size from 10 to 14 since using this How-To, because they became very small), but not those in Opera's interface, I mean menu fonts (file, edit, view...), fonts on the toolbars, tabs, right-click menus and fonts used for http addresses showed inside the address bar. Before they looked like Sans 12, now they changed to perhaps Arial 8...? Other applications are looking the same and working just fine.. I tried to use the qtconfig tool, everything is set to Sans 12, just Opera's interface looks different..

 
Part 1 shouldn't effect Opera at all, they are mostly multimedia related or Java. Try purging Opera then reinstall it. Have you Googled your problem? You could try removing the msttcorefonts package and see if that helps.
 
Nathan

---

### Post by ezechieljhc on 2008-04-05
> **reassuringlyoffensive said:**
> Part 1 shouldn't effect Opera at all, they are mostly multimedia related or Java. Try purging Opera then reinstall it. Have you Googled your problem? You could try removing the msttcorefonts package and see if that helps.
 
Nathan

I removed the msttcorefonts package and it worked! :) Opera's interface is now as it used to be. 
Thank you very much Nathan!

---

### Post by ubuntu-freak on 2008-04-05
> **ezechieljhc said:**
> I removed the msttcorefonts package and it worked! :) Opera's interface is now as it used to be. 
Thank you very much Nathan!

 
No problem. :-) 


Bit strange though. You really couldn't find a way to configure it? Install it again if you start using Firefox 3 upon it's release, although, the standard fonts do look better these days.
 
Nathan

---

### Post by ezechieljhc on 2008-04-05
> **reassuringlyoffensive said:**
> No problem. :-) 


Bit strange though. You really couldn't find a way to configure it? Install it again if you start using Firefox 3 upon it's release, although, the standard fonts do look better these days.
 
Nathan

I tried to google this issue, but could'nt find any solution. Just one mention about the gtconfig tool.. I still don't understand why Firefox remained unchanged and just Opera was affected.

---

### Post by ubuntu-freak on 2008-04-05
> **ezechieljhc said:**
> I tried to google this issue, but could'nt find any solution. Just one mention about the gtconfig tool.. I still don't understand why Firefox remained unchanged and just Opera was affected.
There is just one more question: I still experience audio and video lags when trying to play matroska (mkv) video files. I use SMplayer - a known frontend for mplayer. I tried VLC and totem also, with worse results. I already downloaded and installed all possible codecs. Am I missing something?

 
I don't know. Never played that format myself. Where are they from?
 
Regarding Firefox, it can use msttcorefonts, but it doesn't automatically use them and you can change the minimum font size (I always do).
 
Nathan

---

### Post by ezechieljhc on 2008-04-05
> **reassuringlyoffensive said:**
> I don't know. Never played that format myself. Where are they from?
 
Regarding Firefox, it can use msttcorefonts, but it doesn't automatically use them and you can change the minimum font size (I always do).
 
Nathan

Mkv is an alternative to AVI, MOV, MP4, MPg... and it is open source. For more details: [http://www.matroska.org/]("http://http://www.matroska.org/") But nevermind, I have already figured it out.

---

### Post by ubuntu-freak on 2008-04-05
> **ezechieljhc said:**
> Mkv is an alternative to AVI, MOV, MP4, MPg... and it is open source. For more details: [http://www.matroska.org/]("http://http://www.matroska.org/") But nevermind, I have already figured it out.

 
Haha:-) You're not allowed to do that! Please share with me how you cured the problem so I can help others if need be.
 
Nathan

---

### Post by forceofnature on 2008-04-05
I am back with Hardy Heron.  Anyone try this in Hardy yet?

---

### Post by ubuntu-freak on 2008-04-05
> **forceofnature said:**
> I am back with Hardy Heron.  Anyone try this in Hardy yet?

 
I recently updated it and there are dedicated intructions for Hardy in Part 1. Don't forget to change the wget command from gutsy to hardy.
 
Nathan

---

### Post by ericalejandrocasas on 2008-04-05
IT WORKED!!!!!!!!!!!!!!! I LOVE YOU!!!! (in a good way) man even tv-shack wroks without a problem!!! man i about to cry (not really) ive been trying for a looooooooooooong time to fix this! thanks alot man

---

### Post by jorwex on 2008-04-05
I vote for a script. You should make one, Op.

:)

---

### Post by ubuntu-freak on 2008-04-05
> **ericalejandrocasas said:**
> IT WORKED!!!!!!!!!!!!!!! I LOVE YOU!!!! (in a good way) man even tv-shack wroks without a problem!!! man i about to cry (not really) ive been trying for a looooooooooooong time to fix this! thanks alot man

 
You don't seem very grateful. ;-)
 
Glad it helped you, and thanks for your very enthusiastic and complimentry post. :-)
 
Nathan

---

### Post by ubuntu-freak on 2008-04-05
> **jorwex said:**
> I vote for a script. You should make one, Op.

:)

 
Doubt I will ever do that. The guide is too variable for a script, there are important things to read and it's just a matter of cutting and pasting once you know what you need anyway. Teaches you how powerful and fast the Terminal method is also.
 
Nathan

---

### Post by ezechieljhc on 2008-04-06
> **reassuringlyoffensive said:**
> Haha:-) You're not allowed to do that! Please share with me how you cured the problem so I can help others if need be.
 
Nathan

OK, sorry. I thought it was a little bit off topic... Well, I figured out that I might have missed one particaluar codec, but I don't know which it was.. Here ist he solution from the thread **How to play .mkv files** [http://ubuntuforums.org/showthread.php?t=711734&highlight=matroska&page=2]("http://ubuntuforums.org/showthread.php?t=711734&highlight=matroska&page=2"):

First, enable extra repositories in Software Resources.
Second, paste the following commands into the terminal.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```

Everything should be working now.

---

### Post by Kivech on 2008-04-06
Nathan,

I'd like to add something to your Ubuntu Hardy 64 guide. With regards to the "essential-packages" section.

The plugin  icedtea-java7-jre is basically a dummy package that is even recommended to eliminate. What I did is leave that one out and instead I installed icedtea-gcjwebplugin. This seems to work well.

With regards to flash, I have in my install script flashplugin-nonfree which installs flash perfectly. For me flash now even works better than the one on my Vista laptop. So I don't think Hardy users will likely need any alternatives.

If I find anything else, I'll let you know. ;)

Kivech

---

### Post by ubuntu-freak on 2008-04-06
ezechie,
 
Looks a lot like part 1 of my how-to. I'll have to see if it's missing a package. Seems odd though.
 
kivech,
 
Not sure what you mean, cos I've already added that icedtea-gcjwebplugin to my 64-Bit Hardy install command. Is the old icedtea-java7-plugin automatically removed when installing the gcjwebplugin?
I'd be interested to know.
 
Also, what were you saying about Adobe Flash?  Talking about Flash, give swfdec a try, heard great things about the latest version, so try it if it's been packaged for Hardy. 
 
Nathan

---

### Post by Kivech on 2008-04-06
> **reassuringlyoffensive said:**
> kivech,
 
Not sure what you mean, cos I've already added that icedtea-gcjwebplugin to my 64-Bit Hardy install command. Is the old icedtea-java7-plugin automatically removed when installing the gcjwebplugin?
I'd be interested to know.
 
Also, what were you saying about Adobe Flash?  Talking about Flash, give swfdec a try, heard great things about the latest version, so try it if it's been packaged for Hardy. 
 
Nathan

I'll have a look at swfdec in one of the following days, thanks for the tip.

Not sure about the auto removal of the old icedtea-java7-plugin. I personally don't install it and just go for the new version. I'll see if I can find out if this happens automatically or not and then I'll let you know.

With regards to the plugin; on the first page for Ubuntu Hardy 64 you have these two plugins listed:  icedtea-java7-jre icedtea-java7-plugin
While the ones that I use are: icedtea-gcjwebplugin icedtea-java7-plugin

As far as I know, the first one you are using in Hardy is just a dummy. The one I am using seems to work fine (haven't run into any problems with them yet).
Also, as opposed to Gutsy, the Hardy ones work perfectly out of the box. The ones for Gutsy require the unofficial repositories to be added to the sources.list in order to work properly.

Hope that answers your questions.

Kivech

---

### Post by ubuntu-freak on 2008-04-06
> **Kivech said:**
> I'll have a look at swfdec in one of the following days, thanks for the tip.

Not sure about the auto removal of the old icedtea-java7-plugin. I personally don't install it and just go for the new version. I'll see if I can find out if this happens automatically or not and then I'll let you know.

With regards to the plugin; on the first page for Ubuntu Hardy 64 you have these two plugins listed:  icedtea-java7-jre icedtea-java7-plugin
While the ones that I use are: icedtea-gcjwebplugin icedtea-java7-plugin

As far as I know, the first one you are using in Hardy is just a dummy. The one I am using seems to work fine (haven't run into any problems with them yet).
Also, as opposed to Gutsy, the Hardy ones work perfectly out of the box. The ones for Gutsy require the unofficial repositories to be added to the sources.list in order to work properly.

Hope that answers your questions.

Kivech

 
Still don't know what you mean. The install commands for 64-Bit Ubuntu fetch icedtea-gcjwebplugin which itself pulls in openjdk-6-jre. Only the pre-Hardy command installs icedtea-java7-plugin and icedtea-java7-jre. That was one reason I have a Hardy and pre-Hardy section.
 
Nathan

---

### Post by shahin on 2008-04-07
I have a coaxial SPDIF that I wanna use to connect to my tv.  Is this possible?  Can I get video and sound to tv?  BTW, the procedure worked very well, thanks.

---

### Post by Kivech on 2008-04-07
> **reassuringlyoffensive said:**
> Still don't know what you mean. The install commands for 64-Bit Ubuntu fetch icedtea-gcjwebplugin which itself pulls in openjdk-6-jre. Only the pre-Hardy command installs icedtea-java7-plugin and icedtea-java7-jre. That was one reason I have a Hardy and pre-Hardy section.
 
Nathan

I just checked and I stand corrected. :) You are right. At an earlier stage of beta trying to install  icedtea-java7-jre gave an error message saying there was no such package and that there was no release candidate for it. So I assumed it was replaced and not used anymore.

A quick check in synaptic showed that at this point indeed this package was automatically installed with the other ones.

Sorry for the confusion, I just never noticed this had changed.

Kivech

---

### Post by ubuntu-freak on 2008-04-07
> **shahin said:**
> I have a coaxial SPDIF that I wanna use to connect to my tv.  Is this possible?  Can I get video and sound to tv?  BTW, the procedure worked very well, thanks.

Sorry, don't have any experience with that. Did a quick search though and I found [this thread](http://ubuntuforums.org/showthread.php?t=32213). He seems to be having trouble, but if you run into any problems the thread may be of some help to you.

Give it a try and see, seems it should work.

Nathan

---

### Post by ubuntu-freak on 2008-04-07
I've removed msttcorefonts from the install commands. Is it really needed? My fonts look great without it. I use DejaVu in Firefox (Ubuntu uses DejaVu also) and don't allow pages to use their own fonts. Let me know what you think.

Nathan

---

### Post by Kivech on 2008-04-07
> **reassuringlyoffensive said:**
> I've removed msttcorefonts from the install commands. Is it really needed? My fonts look great without it. I use DejaVu in Firefox (Ubuntu uses DejaVu also) and don't allow pages to use their own fonts. Let me know what you think.

Nathan

Couldn't agree more, I never used them myself anyways. ;)

Kivech

---

### Post by WoosterB on 2008-04-08
I can't get your procedures to work for me.  So what I'd like to do is uninstall everything right down to the adobe plugin.  I can uninstall the pluggin (using your command line) but how to I uninstall the Java (and also mplayer)?

-W

---

### Post by ubuntu-freak on 2008-04-08
> **WoosterB said:**
> I can't get your procedures to work for me.  So what I'd like to do is uninstall everything right down to the adobe plugin.  I can uninstall the pluggin (using your command line) but how to I uninstall the Java (and also mplayer)?

-W

 
What are having trouble with? Which Ubuntu varient are you using? To uninstall packages, use "sudo apt-get remove" instead of "sudo apt-get install". Let me try and help you first though.
 
Nathan

---

### Post by WoosterB on 2008-04-08
Ok, though I'd really like to get my browser back to "original status" and start the process over. =)

I'm using 7.1 Ubuntu

My problem is that video (say youtube) is choppy, with no sound.  Sometimes its not choppy with no sound (for same video) and I'm not quite sure what changes I made from one to the other will cause the inconsistency in video playback.

Another problem is again with sound.  If I navigate to a site with music in the background, Firefox will lock up my computer.  At least I think its firefox because it does not happen unless I go to a particular site with music in the background.  Case in point:

[www.hootie.com](www.hootie.com) (the home site for Hootie and Blowfish).  

This will lock up my computer every time.  I've tested in Windows and no problem so I'm led to believe it is something to do with Firefox for linux, whether its a switch not switched or worse.  

Is there anything else I can tell you?
thanks!
-W

EDIT: I am running 32-bit Ubuntu

---

### Post by ubuntu-freak on 2008-04-08
> **WoosterB said:**
> Ok, though I'd really like to get my browser back to "original status" and start the process over. =)

I'm using 7.1 Ubuntu

My problem is that video (say youtube) is choppy, with no sound.  Sometimes its not choppy with no sound (for same video) and I'm not quite sure what changes I made from one to the other will cause the inconsistency in video playback.

Another problem is again with sound.  If I navigate to a site with music in the background, Firefox will lock up my computer.  At least I think its firefox because it does not happen unless I go to a particular site with music in the background.  Case in point:

[www.hootie.com](www.hootie.com) (the home site for Hootie and Blowfish).  

This will lock up my computer every time.  I've tested in Windows and no problem so I'm led to believe it is something to do with Firefox for linux, whether its a switch not switched or worse.  

Is there anything else I can tell you?
thanks!
-W

EDIT: I am running 32-bit Ubuntu

 
Even with a manual Flash plugin install yeah? Press alt+f2 and type "gksudo nautilus", press enter, type your password and then navigate to /usr/lib/firefox/plugins. Once there, take a look and see if you have more than one Flash plugin. If you did perform a manual install, did you purge the repo one first?
 
If that fails, take a look at the troubleshooting section and see if telling Firefox to use alsa-oss helps, presuming you have installed it.
 
Did you try the "rm $HOME/.mozilla/firefox/pluginreg.dat" command?
 
Hopefully one of those steps will help.
 
Nathan

---

### Post by WoosterB on 2008-04-08
ok point by point here.

a) the flash plugin was not manually installed.  It was the "click here to install plugin" that one sees if one finds a page that needs the plugin.  If you think that makes a big difference I'll go through that procedure and manually install.

b) Firefox is setup to use those.  I will make a statement here that I had to fidget with the sound driver as per this thread:
[http://ubuntuforums.org/showthread.php?t=732512&highlight=Soundblaster](http://ubuntuforums.org/showthread.php?t=732512&highlight=Soundblaster)
So it could be that something there puts music on my desktop but refuses to stream.

c) rm $home etc. did not work.

If I need to change anything (like install adobe manually) please let me know how to uninstall the java in your procedure and the other programs you had me install.  It would be a lot better to start from an out of the box firefox, that way I can help pinpoint the problem area.  As it is, I'm not 100% sure its one program or the other (I'm not java/mplayer savy) and I made the horrible mistake of not taking meticulous notes (like I normally do) when I went through your procedure. =)

Thanks!

-W

---

### Post by WoosterB on 2008-04-08
I hate to double post but I went ahead and tried to see if a manual install would work.  It did not.  I have choppy vid and no sound.


-W

---

### Post by ubuntu-freak on 2008-04-08
> **WoosterB said:**
> I hate to double post but I went ahead and tried to see if a manual install would work.  It did not.  I have choppy vid and no sound.


-W

 
Part 1 does state that there is a problem with the normal way of installing Adobe Flash. Did you purge flashplugin-nonfree before installing it manually? Did the troubleshooting section not help? Have you rebooted?
 
Not sure what else it could be.
 
Nathan
 
Edit: Did you try to get Firefox to use alsa-oss? You don't need to remove Java, mozilla-mplayer, as it's just a Firefox issue from what I can tell.

---

### Post by WoosterB on 2008-04-08
Yes, I made sure I had purged the flash player before re-installing.  I tried some of the troubleshooting but to no avail.  Reboot as well.

I can see that mplayer and Java are separate entities and I did some more trouble shooting using Realplayer.  I tuned into BBC7 and once again firefox locked up which certainly says (to me) that firefox is not happy since it does this regardless of plugins.

By " getting firefox to use "alsa-oss" you mean the "none" to "aoss" ?  I've done that.  

I'm going to poke around a bit further by uninstalling/re-installing firefox when I get the time.  Hopefully maybe the problem will iron itself out.  

Again, it COULD be (I don't know really) the way the sound driver is setup.  I get music/sound from desktop apps and tests.  I'll look into this as well.

-W

---

### Post by ubuntu-freak on 2008-04-08
> **WoosterB said:**
> Yes, I made sure I had purged the flash player before re-installing.  I tried some of the troubleshooting but to no avail.  Reboot as well.

I can see that mplayer and Java are separate entities and I did some more trouble shooting using Realplayer.  I tuned into BBC7 and once again firefox locked up which certainly says (to me) that firefox is not happy since it does this regardless of plugins.

By " getting firefox to use "alsa-oss" you mean the "none" to "aoss" ?  I've done that.  

I'm going to poke around a bit further by uninstalling/re-installing firefox when I get the time.  Hopefully maybe the problem will iron itself out.  

Again, it COULD be (I don't know really) the way the sound driver is setup.  I get music/sound from desktop apps and tests.  I'll look into this as well.

-W

 
Certainly is strange. You do have alsa-oss installed from part 1 yeah? Just making sure. How long has this been an issue? Might be worth backing up your bookmarks, purging Firefox, maybe delete it's hidden folder in your home directory and reinstall. I have another idea also, create a new user account and see if Firefox behaves itself in that account.
 
Nathan

---

### Post by WoosterB on 2008-04-08
As a follow up,  I found things wouldn't work in Opera.  So I uninstalled everything internet and plugin related.

a) reinstalled firefox: same problem
b) installed adobe manually: The video is no longer choppy, but no sound with youtube.
c) installed realplayer: I can now listen to BBC7 so sound is good there (and I can listen to "Beyond our Ken" again!)

As an idiot check I made sure the volume settings were ok in youtube =p

So now I'm narrowing the focus to how adobe/firefox get along.  

Just as another idiot check I had copied the line:
sudo apt-get install alsa-oss compizconfig-settings-manager faad gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 sun-java6-fonts sun-java6-jre sun-java6-plugin unrar w32codecs

when I started.  This is what (I assume) you mean by the also-oss since I see that contained as we install the streamer and java contents.  Now if I was JUST wanting to install the essential alsa-oss and not java, at what point would I stop in that long command line?  I'm thinking about just re-installing that particular component.  I want to say I've seen each of these in that package installer so I'll double check there.

-W

---

### Post by ubuntu-freak on 2008-04-08
Not sure what you mean. The Java packages are named sun-java6 etc. Why do you keep mentioning Java though? Did you try creating a new user acount? Did Firefox ever work correctly?
 
Nathan

---

### Post by jorwex on 2008-04-08
ReassuringlyOffensive-

I love your guide. Used it a while ago when I was getting warmed up to Ubuntu and made the transition pretty painless.

I wiped my cousin's laptop this past weekend when he was here and sent him on his way after using your updated guide (32 bit guide). He was driving back (a few hours) and his friends decided to pop in a divx/xvid movie and watch it on his laptop while he drove home. 

I haven't seen it myself, but they said that VLC will launch and the progress meter will move but no audio or video will show up. Similar results with what they said was Movie Player (I dunno if his friends meant mplayer or totem).

They ended up booting to the Gutsy LiveCD I gave him and running the video off of that somehow.

**Do you know where I should begin to troubleshoot all of this?** He's going out of the country in 8 days and I feel bad that I didn't send him off with a totally functioning box. 

Thanks!

-Jordan

---

### Post by WoosterB on 2008-04-08
Actually ReassuringOffensive you answered my question.  The reason I'm harping on the Java is I've managed to uninstall it (with firefox) and now I'm just setting up the individual plugins one at a time and testing the build with each item installed.  I can take that command line in your procedure and cut it up into distinct parts and I was looking to make sure the Java commands were not in there.   

I tried the multi user method but I still had problems.  

The verdict at the moment is that Firefox works with Realplayer for internet radio, however the adobe flash player is suspect since it does not seem to play sound (although the video is smooth).

---

### Post by ubuntu-freak on 2008-04-08
> **WoosterB said:**
> Actually ReassuringOffensive you answered my question.  The reason I'm harping on the Java is I've managed to uninstall it (with firefox) and now I'm just setting up the individual plugins one at a time and testing the build with each item installed.  I can take that command line in your procedure and cut it up into distinct parts and I was looking to make sure the Java commands were not in there.   

I tried the multi user method but I still had problems.  

The verdict at the moment is that Firefox works with Realplayer for internet radio, however the adobe flash player is suspect since it does not seem to play sound (although the video is smooth).

 
See if this thread helps:
 
[http://ubuntuforums.org/showthread.php?p=3633218](http://ubuntuforums.org/showthread.php?p=3633218)
 
If you press alt+f2, type "gksudo firefox", then enter and type your password, does sound in Flash vids work now? 
 
Nathan

---

### Post by WoosterB on 2008-04-08
Ok in that thread the last post routes you to a page where you get a library for Adobe and that fixed my "Youtube" issue with video/sound.

An interesting note however is that the firefox ran as a root user is an out of the box version with no plugins that I could see (about:plugin).  I'm interested in that command and how/why it is used.  I can only assume it gives you root access while still using the GUI.  The other method is of course the terminal Sudo command.  Why firefox is different there than normal I'm not sure of.  That's my research and as far as you are concerned my problem is fixed.  Thanks for the help and the procedure!

-W

EDIT: No thats not a happy face....its a semi colon with a p afterwards.  lol

---

### Post by ubuntu-freak on 2008-04-08
You're using PusleAudio in Gutsy? That's what libflashsupport is for, it's in the Hardy install command because it uses PulseAudio by default.
 
Glad you got it working anyway. :-)
 
Nathan

---

### Post by Timbothecat on 2008-04-09
Hi guys.

I went through the dvd playback section of this great piece of work and was able to play a dvd after that wouldn't play before.

The problem I'm having now though is that VLC auto starts but the movie itself doesn't run. I click the play button at the top but it opens a dialogue box. I go to the "disc" tab and then go to the bottom and click ok and the movie then starts without a hitch. I did this on 4 other dvd's just to make sure it wasn't some sort of stupid one off.

My question then is how do I get it to just run without all the mucking around? Or is this the only way you can do it?

Thanks for your help in advance guys.

All the best,

Tim.

---

### Post by WoosterB on 2008-04-09
I dunno about the PulseAudio, but at the very bottom of the thread it leads you to a site (blog site) where there is a adobelib support package.  I'll post it here in case anyone wants to give it a whirl.

[http://sendderek.wordpress.com/2007/10/20/how-to-fix-the-no-sound-issue-in-firefox-flash/](http://sendderek.wordpress.com/2007/10/20/how-to-fix-the-no-sound-issue-in-firefox-flash/)

Its in .deb format so it can be extract/installed in a shot.
On the flip side however, now the sound is a second before or a second behind the video.  Linux is turning into a sadistic experience.

I've looked again at the thread and this may be a 3rd party script since it originally doesn't seem to come from adobe.  

-W

---

### Post by ubuntu-freak on 2008-04-09
Timbothecat,
 
Let me know if the method here works any better:
 
[http://limulus.wordpress.com/2007/12/10/playing-dvds-in-ubuntu-gutsy/](http://limulus.wordpress.com/2007/12/10/playing-dvds-in-ubuntu-gutsy/)
 
Nathan

---

### Post by ubuntu-freak on 2008-04-09
> **WoosterB said:**
> I dunno about the PulseAudio, but at the very bottom of the thread it leads you to a site (blog site) where there is a adobelib support package.  I'll post it here in case anyone wants to give it a whirl.

[http://sendderek.wordpress.com/2007/10/20/how-to-fix-the-no-sound-issue-in-firefox-flash/](http://sendderek.wordpress.com/2007/10/20/how-to-fix-the-no-sound-issue-in-firefox-flash/)

Its in .deb format so it can be extract/installed in a shot.
On the flip side however, now the sound is a second before or a second behind the video.  Linux is turning into a sadistic experience.

I've looked again at the thread and this may be a 3rd party script since it originally doesn't seem to come from adobe.  

-W

 
Perhaps if you reverse that alsa-oss method I told you to try you might get better results, as it didn't fix your sound issue anyway. Put it back to "none" in the FF config, or whatever it was, or maybe "auto".
 
Nathan

---

### Post by WoosterB on 2008-04-10
Neither did the trick.  I'm looking up now if anyone else had any similar issues.

-W

---

### Post by bilijoe on 2008-04-11
I am having trouble with BitTorrent and Deluge, regarding opening a router port.  I am using Gutsy, but plan on upgrading to Hardy, as soon as it is released.  Should I pursue this problem now, or wait for Hardy?  In other words, is this likely to be a version-specific problem, or will a fix (if I find one) that works for Gutsy be likely to carry over to work in Hardy, as well?

---

### Post by ubuntu-freak on 2008-04-11
> **bilijoe said:**
> I am having trouble with BitTorrent and Deluge, regarding opening a router port.  I am using Gutsy, but plan on upgrading to Hardy, as soon as it is released.  Should I pursue this problem now, or wait for Hardy?  In other words, is this likely to be a version-specific problem, or will a fix (if I find one) that works for Gutsy be likely to carry over to work in Hardy, as well?

 
I don't have much experience with your issue, sorry. Google is your friend though, try searching "site:ubuntuforums.org deluge router port".
 
Nathan 
 
Edit: Sorry, didn't answer part of your post. You may have to repeat the fix, but most likely not. Application settings and configs are usually left alone during an upgrade, especially if they have been modified.

---

### Post by Timbothecat on 2008-04-12
> **reassuringlyoffensive said:**
> Timbothecat,
 
Let me know if the method here works any better:
 
[http://limulus.wordpress.com/2007/12/10/playing-dvds-in-ubuntu-gutsy/](http://limulus.wordpress.com/2007/12/10/playing-dvds-in-ubuntu-gutsy/)
 
Nathan

Nathan.

I offer you my first born! Sure the other 5 will miss him but you deserve it.:lolflag::guitar:

 This worked a treat my friend, thank you so much.

All the best,

Tim.

---

### Post by ubuntu-freak on 2008-04-12
> **Timbothecat said:**
> Nathan.

I offer you my first born! Sure the other 5 will miss him but you deserve it.:lolflag::guitar:

 This worked a treat my friend, thank you so much.

All the best,

Tim.

 
I'm glad it worked, thanks for letting me know how well it works also. I've now added that method to part 4 and I'm gonna do some more tests and research on monday.
 
If any Hardy users could tell me how it works I'd be really grateful.
 
Nathan

---

### Post by 4-PackDad on 2008-04-12
Hey;

Newbie Help...?
I finally jumped in and switched to Ubuntu after gett'n sick of XP.

I've trying to follow along and attemp to understand.

I'm trying to install Adobe Flash 9, (Kidz with to play on Disney.com)
but
I'm lost on part of Step 1...

Finally, click on the installer and **_*instruct it to install the plugin to "/usr/lib/firefox"*_**

??? How do I """instruct it to install the plugin to /usr/lib/firefox ....????

Thnx for the great help on this link
Bill

---

### Post by ubuntu-freak on 2008-04-12
> **4-PackDad said:**
> Hey;

Newbie Help...?
I finally jumped in and switched to Ubuntu after gett'n sick of XP.

I've trying to follow along and attemp to understand.

I'm trying to install Adobe Flash 9, (Kidz with to play on Disney.com)
but
I'm lost on part of Step 1...

Finally, click on the installer and **_*instruct it to install the plugin to "/usr/lib/firefox"*_**

??? How do I """instruct it to install the plugin to /usr/lib/firefox ....????

Thnx for the great help on this link
Bill

 
Hey :-)
 
It's easier than you think, just copy and paste /usr/lib/firefox into the Adobe installer when it asks where to install the plugin and press enter.
 
Welcome to Ubuntu by the way, 
 
Nathan

---

### Post by 4-PackDad on 2008-04-12
Hey;

If it was that easy...

Something must not be quite right.

I click on the "Installer and I get a window that gives me the options:
Run in Terminal, Display, Cancel, Run

Run does not bring up a window asking where to install. (does not bring up ANY window)
Run in Terminal DOES bring up a window and asks to install,
but,
I can not edit the location of the install.

What am I doing wrong...???

Thnx,
Bill

---

### Post by ubuntu-freak on 2008-04-12
> **4-PackDad said:**
> Hey;

If it was that easy...

Something must not be quite right.

I click on the "Installer and I get a window that gives me the options:
Run in Terminal, Display, Cancel, Run

Run does not bring up a window asking where to install. (does not bring up ANY window)
Run in Terminal DOES bring up a window and asks to install,
but,
I can not edit the location of the install.

What am I doing wrong...???

Thnx,
Bill

 
Hmm. It's all there. Did you start the file browser with admin privilages? The "gksudo nautilus" thing, then you navigate to the Adobe installer, click on it and then run in the Terminal, press enter until it asks where you want to install the plugin and then type or paste /usr/lib/firefox.
Restart Firefox. 
 
Nathan

---

### Post by 4-PackDad on 2008-04-12
Nathan;

Ok,
I've done all that...
Went '1' step further with the Terminal.

I 'clicked' "y" for yes for the install expecting to be prompted on where to install.

This is what I got back:

----------- Install Action Summary -----------

Adobe Flash Player 9 will be installed in the following directory:

Mozilla installation directory  = /home/bill/.mozilla

Proceed with the installation? (y/n/q): y

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


Installation complete.


Perform another installation? (y/n): 


*** It would not me type over the installation directory ***

Is this right...?

Thnx,
Bill

---

### Post by ubuntu-freak on 2008-04-12
> **4-PackDad said:**
> Nathan;

Ok,
I've done all that...
Went '1' step further with the Terminal.

I 'clicked' "y" for yes for the install expecting to be prompted on where to install.

This is what I got back:

----------- Install Action Summary -----------

Adobe Flash Player 9 will be installed in the following directory:

Mozilla installation directory  = /home/bill/.mozilla

Proceed with the installation? (y/n/q): y

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


Installation complete.


Perform another installation? (y/n): 


*** It would not me type over the installation directory ***

Is this right...?

Thnx,
Bill

 
I don't know what else to say, you're not following my instructions in part 1. I tried to make it clear. You didn't press alt+f2, type "gksudo nautilus", type your password and then navigate to the Adobe installer. That gives you admin rights to install it into /usr/lib/firefox.
 
Try this guide with screenshots to help:
 
[http://www.psychocats.net/ubuntu/flashmanual](http://www.psychocats.net/ubuntu/flashmanual)
 
Nathan

---

### Post by PhatKat on 2008-04-13
Hi again all! Ok introducing others i know to the wonderful world of Ubuntu and i have helped my niece to install 8.04 but everything runs fine cept the java and i got a 'not working properly' message when i ran a test here:
[http://www.java.com/en/download/help/testvm.xml?ff3](http://www.java.com/en/download/help/testvm.xml?ff3)
It prompts me to install GCj web browser plug in and when i follow instructions it doesn't work cos the problem persists :( Still can play vidoes from most sites though but this is bothering me! I searched the forums and the closest thread which i can find is this ^^ Thanks in advance to anyone who could help!

---

### Post by ubuntu-freak on 2008-04-13
> **PhatKat said:**
> Hi again all! Ok introducing others i know to the wonderful world of Ubuntu and i have helped my niece to install 8.04 but everything runs fine cept the java and i got a 'not working properly' message when i ran a test here:
[http://www.java.com/en/download/help/testvm.xml?ff3](http://www.java.com/en/download/help/testvm.xml?ff3)
It prompts me to install GCj web browser plug in and when i follow instructions it doesn't work cos the problem persists :( Still can play vidoes from most sites though but this is bothering me! I searched the forums and the closest thread which i can find is this ^^ Thanks in advance to anyone who could help!

 
Hardy isn't finished yet and still has bugs.
 
Did you try part 1 of my how-to and install the Sun Java packages, codecs etc? That's the one you want. 
 
Nathan

---

### Post by 4-PackDad on 2008-04-13
Nathan;

Looks like we're both at a loss.

I looked at u're screen shots.

Every thing is correct right up to where it prompts for the "installation Location"
I do NOT get that prompt.

Just asks y/n to install.

How can I manually reconfig...?

Thnx,
Bill

---

### Post by ubuntu-freak on 2008-04-13
> **4-PackDad said:**
> Nathan;

Looks like we're both at a loss.

I looked at u're screen shots.

Every thing is correct right up to where it prompts for the "installation Location"
I do NOT get that prompt.

Just asks y/n to install.

How can I manually reconfig...?

Thnx,
Bill

 
What do you do once you open the file browser with "gksudo nautilus"? Even if you can see the Adobe installer on your desktop, you have to navigate to your desktop using the file browser you opened with alt+f2, cos it has admin privileges. 
 
Nathan

Edit 2: I think the disney.com games require Shockwave, which isn't available for Linux yet sorry. Also, have you gone to YouTube and let the Firefox prompt try and install Adobe Flash for you? I tested it again today and now it works. It's certainly the most easy way to install Adobe Flash.

---

### Post by ubuntu-freak on 2008-04-14
VLC as default DVD player in Ubuntu should work perfect now. Also, VLC will automatically launch in fullscreen with 100% volume in the player itself. Here are the latest intructions I posted today;

To set VLC as your default DVD player (I strongly advise you do), navigate to System>Preferences>Removable Drives and Media>Multimedia and replace the existing “Video DVD Discs” command ("totem %m") with:

**vlc --vout-filter deinterlace --deinterlace-mode blend --volume 512 --fullscreen %m**

If you don't want VLC to automatically launch into fullscreen when a DVD movie is inserted, all you have to do is delete the "--fullscreen" part of the command. To exit and enter fullscreen in VLC, just press the "f" key.

Nathan

---

### Post by 4-PackDad on 2008-04-14
Nathan;

Everything works "exactly" as described in the instructions right up to the point asking for the install location.

The 'only' thing I can think of is that the first time I tried the install I 'clicked' "RUN" instead of 'run in terminal'

Could this have buggered it up...?

Disney & YouTube run fine under my Admin Login where it was installed,
but,
Of course Disney & YouTube do Not run under the other User logins.
It promts for the Adobe Flash Plugin.

If I install the Adobe Flash under every User login in the computer, won't that also make a mess of things...?

Thnx,
Bill

---

### Post by ubuntu-freak on 2008-04-14
> **4-PackDad said:**
> If I install the Adobe Flash under every User login in the computer, won't that also make a mess of things...?

Thnx,
Bill

No, you can do that if you want, I'm just surprised that the easy install method doesn't work for you. It worked for me today when I removed my plugin and let Ubuntu install it automatically when I visited YouTube. You should try that in your other user accounts.

 What about that link I gave you to a working package? All you have to do is double-click on the deb to install. This is giving me headaches. :confused:

Hope you get it working though,

Nathan

---

### Post by Payteer on 2008-04-14
Hello Nathan,

the Java does work in Hardy, just test now for other users.

However I can't find the place to put the VLC as default DVD player bit you added today in Harday, it seems to have changed location and I haven't a clue where to.

---

### Post by ubuntu-freak on 2008-04-14
> **Payteer said:**
> Hello Nathan,

the Java does work in Hardy, just test now for other users.

However I can't find the place to put the VLC as default DVD player bit you added today in Harday, it seems to have changed location and I haven't a clue where to.

 
It's been moved to Nautilus>Edit>Preferences>Media, but it doesn't let you choose VLC or use my special command. I posted today on Launchpad concerning it, you can back me up if you want and help in encouraging them to rectify it:
 
[https://bugs.launchpad.net/f-spot/+bug/191475](https://bugs.launchpad.net/f-spot/+bug/191475)

---

### Post by K.Morgan on 2008-04-14
Hi, I have just gone through all the steps needed in the first post, and i'm glad to say that it has sorted all my problems out bar one.  I can't seem to stream m3u files from one particular website [http://www.streetwisedigital.co.uk/](http://www.streetwisedigital.co.uk/)  Not sure if they are using some different codec or something.  

Mplayer tries to load but then displays a 'stopped' message.  VLC doesn't play it at all, displaying an error message, Unable to open the particular file, the only player that will play it is Amarok.  Amarok loads the files no problem.  I don't want to use amarok though I would like to use either Mplayer or VLC.  Any ideas?


Kristian

---

### Post by ubuntu-freak on 2008-04-14
> **K.Morgan said:**
> Hi, I have just gone through all the steps needed in the first post, and i'm glad to say that it has sorted all my problems out bar one.  I can't seem to stream m3u files from one particular website [http://www.streetwisedigital.co.uk/](http://www.streetwisedigital.co.uk/)  Not sure if they are using some different codec or something.  

Mplayer tries to load but then displays a 'stopped' message.  VLC doesn't play it at all, displaying an error message, Unable to open the particular file, the only player that will play it is Amarok.  Amarok loads the files no problem.  I don't want to use amarok though I would like to use either Mplayer or VLC.  Any ideas?


Kristian

 
What happens when you press play after it loads and stops? I can't do any tests right now as I'm no where near my Ubuntu system. You could try posting your own thread and ask people to test the stream, or hopefully a few people here will test it.
 
Nathan
 
P.S. If you have no luck with the MPlayer plugin, try Audacious - it's a sweet Winamp-like audio player.

---

### Post by bayouoldguy on 2008-04-14
Hi; Just want to thank "reassuringlyoffensive" for the How-To guide. I followed the instructions for the Parts 1 & 2 to get the Essentials & Streaming working. Had to install the mozilla mplayer to view the NASA web page videos. Also had to go back & install the NVidia binary XFree86 4.x/X.Org 'legacy'  driver to run my GeForce2 MX/MX 400 card properly. The proper driver stopped all of the "jerking video" I had been seeing with the updated NVidia drivers. At least now I can view U-Tube & other videos....Thanks again......"G":)
 ( I have a Dual-boot Windows Millenium &  ubuntu 7.10 on an old Compaq AMD Athlon 1.2 Ghz, using as a "toy" to learn ubuntu ! , who knows what I might try next !).

---

### Post by ubuntu-freak on 2008-04-14
> **bayouoldguy said:**
> Hi; Just want to thank "reassuringlyoffensive" for the How-To guide.

 
You're welcome, thanks.
 
Nathan

---

### Post by Payteer on 2008-04-15
Just added to the bug report.  Thanks for your brilliant guide as always.  It is the best here on the forums for video.

---

### Post by ubuntu-freak on 2008-04-15
> **Payteer said:**
> Just added to the bug report.  Thanks for your brilliant guide as always.  It is the best here on the forums for video.

 
Copy and paste this into the Terminal:

**sudo cp /usr/share/applications/vlc.desktop ~/.local/share/applications/vlc.desktop**

Go to your home folder, then click on "View" in the file browser (Nautilus) and select the "Show Hidden Files" option.  Find the folder ".local" in your home folder, open it and then open the folders "share" and "applications". Next, find and right-click on "vlc.desktop" and navigave to Properties>Launcher>Command. Change the command to:

**vlc --vout-filter deinterlace --deinterlace-mode blend --volume 512 --fullscreen %m**

Now, navigate to Edit>Preferences>Media>DVD Video and select VLC.

Delete the "--fullscreen" part if you don't want DVD playback to launch in fullscreen,

Nathan

---

### Post by 4-PackDad on 2008-04-15
Nathan;

Sorry my problems are giving you a headache...

Went back thru the old posts, I can't find the link you were refering too.
***_"What about that link I gave you to a working package?"_***

I tried to let the "auto-install" work on the other user accounts.
Of course it asks for my Admin Password,
But,
Here we go again,
My password fails.

I switch to my admin account, and my password works fine.

Now what...?

Excedrin Migrain works good for me...

Thanks for you Patience...
Bill

---

### Post by ubuntu-freak on 2008-04-15
> **4-PackDad said:**
> Nathan;

Sorry my problems are giving you a headache...

Went back thru the old posts, I can't find the link you were refering too.
***_"What about that link I gave you to a working package?"_***

I tried to let the "auto-install" work on the other user accounts.
Of course it asks for my Admin Password,
But,
Here we go again,
My password fails.

I switch to my admin account, and my password works fine.

Now what...?

Excedrin Migrain works good for me...

Thanks for you Patience...
Bill

 
I think I know why it failed, you have to use their user password on their account. Just use this command in the terminal whilst in your account:
 
**rm $HOME/.mozilla/firefox/libflashplayer.so**
  
Then install it with the Firefox prompt and restart Firefox. That will install it to a system-wide location for all users.
 
Nathan

---

### Post by 4-PackDad on 2008-04-15
Nathan;

Ready for another Migraine...
I know, this is gett'n old.

I did exactly as you said.
Here is the response:

bill@bill-desktop:~$ rm $HOME/.mozilla/firefox/libflashplayer.so
rm: cannot remove `/home/bill/.mozilla/firefox/libflashplayer.so': No such file or directory
bill@bill-desktop:~$ 

I started the flash install again to verify where it installed.
Yes, that is where it "should" be.

Flash will run in my "bill" admin account,
Not in any other user account.

Aren't computers fun...

Thnx,
Bill

---

### Post by ubuntu-freak on 2008-04-15
> **4-PackDad said:**
> Nathan;

Ready for another Migraine...
I know, this is gett'n old.

I did exactly as you said.
Here is the response:

bill@bill-desktop:~$ rm $HOME/.mozilla/firefox/libflashplayer.so
rm: cannot remove `/home/bill/.mozilla/firefox/libflashplayer.so': No such file or directory
bill@bill-desktop:~$ 

I started the flash install again to verify where it installed.
Yes, that is where it "should" be.

Flash will run in my "bill" admin account,
Not in any other user account.

Aren't computers fun...

Thnx,
Bill

 
My fault, sorry. Try this:
 
**rm $HOME/.mozilla/plugins/libflashplayer.so** 
 
Now you should be able to install it system-wide with the Firefox prompt. The manual way was just for people having issues with the FF method.
 
Nathan

---

### Post by Payteer on 2008-04-16
Hello Nathan,  Nope it didn't work, also some things are slightly different in Hardy which could be the reason.

---

### Post by ubuntu-freak on 2008-04-16
> **Payteer said:**
> Hello Nathan,  Nope it didn't work, also some things are slightly different in Hardy which could be the reason.

 
Damn it! That method was ONLY for Hardy, changes taken into account.
 
Did it all seem to work okay but VLC wasn't in the list? Did you reboot? Try changing the command to just "vlc %m". 
 
Nathan

---

### Post by Payteer on 2008-04-16
I'll try that now.  However since the Firefox update this morning, the Mplayer plugin is not recognised anymore in FF. I am going to have to redo the whole think again since this new update.  damn damn and triple damn.  
On this VLC issue, I am going to restart now and tell you in a minute or two what happened with the new code.

---

### Post by ubuntu-freak on 2008-04-16
> **Payteer said:**
> I'll try that now.  However since the Firefox update this morning, the Mplayer plugin is not recognised anymore in FF. I am going to have to redo the whole think again since this new update.  damn damn and triple damn.  
On this VLC issue, I am going to restart now and tell you in a minute or two what happened with the new code.

 
See if this command fixes the FF issue:
 
**rm ~/.mozilla/firefox/pluginreg.dat**
 

Nathan

---

### Post by Payteer on 2008-04-16
Nope, the option in preferences for mplayer aren't there, just the Totem. I suppose uninstall totem should stop it, hold on, i'll try that.....bugger, nope and now when I try BBC in real player, VLM tries to launch.  I am going to start again with this.

---

### Post by Payteer on 2008-04-16
rm: cannot remove `/home/peter/.mozilla/firefox/pluginreg.dat': No such file or directory

This is what I get in terminal

---

### Post by Payteer on 2008-04-16
Where would the FF .dat be?

---

### Post by Payteer on 2008-04-16
I can't understand it up until this morning i had no probs with FF and things.  After the update that had a ff update in it, it has gone kaput.

---

### Post by ubuntu-freak on 2008-04-16
You're confusing me slightly. What preferences? Did you try that new DVD command for VLC? Not MPlayer.
 
Make sure you only have the MPlayer and RealPlayer plugins installed for FF, not the Totem and VLC plugins. Try this command and restart FF:
 
**rm $HOME/.mozilla/firefox/pluginreg.dat** 
 
If it doesn't work again. just find it manually by showing the hidden files (Nautilus>View).
 
Nathan

---

### Post by Payteer on 2008-04-16
Sorry my mistake. 
Okay back to business,  I only have mplayer and realplayer plugins also.
So it is just down to the .dat file, where is it?
I went to nautilus and there was only saved session files there and a metafiles folder

---

### Post by ubuntu-freak on 2008-04-16
> **Payteer said:**
> Sorry my mistake. 
Okay back to business,  I only have mplayer and realplayer plugins also.
So it is just down to the .dat file, where is it?
I went to nautilus and there was only saved session files there and a metafiles folder

 
You went to your home folder, clicked on "View" and then "Show Hidden Files", then looked in the .mozilla folder? Maybe try reinstalling the plugins or keep opening and closing FF. Strange issue.
 
How did that new VLC command work? You need to edit it in that .local folder again.
 
Nathan

---

### Post by Payteer on 2008-04-16
I have deleted it twice in the home folder and both times I got to start the realplayer in BBC and mplayer starts or I am asked for the plugin either mplayer or xine.
Why can't it now see my realplayer.  I have totally reinstalled it also following your guide at the start.
I wish the update hadn't come through this morning now.  Just when everything was working properly also.
On the code for instant starting of VLM for DVDs, no joy there, I am afraid

---

### Post by ubuntu-freak on 2008-04-16
Keep an eye out for other users posting a thread concerning FF later.
 
Not sure what to do about that VLC issue. At least DVD playback has improved in Totem, just waiting for menu support.
 
Nathan

---

### Post by Payteer on 2008-04-16
The VLC issue is a strange one, VLC works however you have to open VLC and launch from there, it will not do it automatically when a DVD is put in the drive.
On the FF issue, I will keep an eye open for it.

---

### Post by 4-PackDad on 2008-04-16
Nathan;

Thank You....!

Worked like a charm.

Now on to my next hurdle.

Thanks again,
Bill

---

### Post by 4-PackDad on 2008-04-16
Nathan;

Forgot about one of the Hurdles...

When I was under XP
I was trying to dube VCR, 8mm camcorder taped over to burn to DVD.
Had a lot of problem dropping frames.
Probably due to old hardware.

Well,
Still have the same hardwre,
What do you suggest I try under Ubuntu...?

Thnx,
Bill

---

### Post by ubuntu-freak on 2008-04-16
> **4-PackDad said:**
> Nathan;

Forgot about one of the Hurdles...

When I was under XP
I was trying to dube VCR, 8mm camcorder taped over to burn to DVD.
Had a lot of problem dropping frames.
Probably due to old hardware.

Well,
Still have the same hardwre,
What do you suggest I try under Ubuntu...?

Thnx,
Bill

 
I'm really not an expert on this, as I've never even attempted it.
 
Can it be connected via USB? It needs to be seen as a video feed/stream instead of just an external drive. Then you have to use something to capture the video, like VLC I think. After you capture it you can use my DVD section to install Tovid and burn it to DVD disc.
 
Might be worth posting your own thread and asking how to make your 8mm camcorder be seen as a feed/stream, if it isn't automatically seen as such when you play the video.
 
Nathan

---

### Post by Payteer on 2008-04-17
Hello Nathan,

Okay on the problem of Real Player not opening, the problem is that I have deleted the .dat file god knows how many times, but the realplayer is not see anymore by Firefox 3 beta 5.

Thanks.

---

### Post by fz43mw on 2008-04-17
Okay, dont know what I was doing most of the time but it worked!!!! I can now watch comerical movies with sound so Thanks much. Will bookmark this so I can maybe correct future problems as I find them

Thanks...

---

### Post by ubuntu-freak on 2008-04-17
> **Payteer said:**
> Hello Nathan,

Okay on the problem of Real Player not opening, the problem is that I have deleted the .dat file god knows how many times, but the realplayer is not see anymore by Firefox 3 beta 5.

Thanks.

 
Remove RealPlayer 10 and just use MPlayer for now (works well anyway). Version 11 of RealPlayer has been released, so give that a try if you're okay with installing bin packages I guess. MPlayer method is much more simple though.
 
Nathan

---

### Post by Payteer on 2008-04-17
Okay, went back to the start again and did it all again and then rebooted and the vlc doesn't crash any more.  However the eject button on the DVD drive doesn't work anymore, only by clicking on the disk icon and selecting eject does it work.
The automatic start however is still not there when you put the DVD in, but I can put up with that. 
Thanks for helping out on this. 
Now the problem of Realplayer, I will see what I can do and report back.

---

### Post by ubuntu-freak on 2008-04-17
> **Payteer said:**
> Okay, went back to the start again and did it all again and then rebooted and the vlc doesn't crash any more.  However the eject button on the DVD drive doesn't work anymore, only by clicking on the disk icon and selecting eject does it work.
The automatic start however is still not there when you put the DVD in, but I can put up with that. 
Thanks for helping out on this. 
Now the problem of Realplayer, I will see what I can do and report back.

 
Ah excellent! VLC launches when you insert a DVD, but you have to press play? If so, try using that long command again in those two files, but without the "--fullscreen" instruction, then reboot. It's safe to delete that "vlc.desktop" file you made before:  

**rm ~/.local/share/applications/vlc.desktop**
 
Nathan

---

### Post by 4-PackDad on 2008-04-17
Nathan;

Yes, I used USB.
I'll try VLC and see what happens.

Thnx,
Bill

---

### Post by Timbothecat on 2008-04-19
Reassuringly_offensive...

In your "How to" you had the following line:

> vlc --vout-filter deinterlace --deinterlace-mode blend --volume 512 --fullscreen %m

which is for users of Gutsy as I understand it. 

How do I set the volume to automatically start at 100% in Hardy Heron? 

Any input would be fantastic.

Thanks in advance,

Tim.

P.S. The first born is still on his way, should be over there soon. :)

---

### Post by ubuntu-freak on 2008-04-19
> **Timbothecat said:**
> Reassuringly_offensive...

In your "How to" you had the following line:



which is for users of Gutsy as I understand it. 

How do I set the volume to automatically start at 100% in Hardy Heron? 

Any input would be fantastic.

Thanks in advance,

Tim.

P.S. The first born is still on his way, should be over there soon. :)

 
Just the volume? What about autoplay and deinterlacing? It's gonna have to be done differently in Hardy due to rewritten code and no official custom command entry option (for now). This isn't in my how-to yet, but should be by Monday.

To change the default DVD player in Hardy Heron to VLC (I strongly advise you do), open the Terminal and copy and paste this command into it:          

**gksudo gedit /etc/gnome/defaults.list**
 
Press Ctrl+f and search for "x-content/video", then change the "totem.desktop" entries to "vlc.desktop". Close and save.
 
Next, right-click on "Applications" in the top panel and select "Edit Menus" to open the default menu editor. Navigate down to "Sound & Video" in the left pane and click on it to show all those applications in the pane to the right. Scroll down the list of applications displayed until you see "VLC media player", right-click on it, then click on "Properties" in the context menu to open "Launcher Properties" and change the launch command from "wxvlc %F" to:
 
**vlc --vout-filter deinterlace --deinterlace-mode blend --volume 512 --fullscreen %m**
 
Close the VLC properties dialog and exit the menu editor. Finally, navigate to Nautilus>Edit>Preferences>Media>DVD Video and  select VLC.

Nathan

---

### Post by ubuntu-freak on 2008-04-21
The above intructions should work perfectly now, sorry.

Nathan

---

### Post by ubuntu-freak on 2008-04-22
Forgot to mention, have a look at the touchpad and fonts tips n tricks in part 5. The fonts advice is worth trying for sure.
 
Nathan

---

### Post by Red Rhino on 2008-04-24
This single note has saved me days of work. Thanks for making 8.04 that much better![http://ubuntuforums.org/images/smilies/star.png](http://ubuntuforums.org/images/smilies/star.png)

---

### Post by ubuntu-freak on 2008-04-24
> **Red Rhino said:**
> This single note has saved me days of work. Thanks for making 8.04 that much better![http://ubuntuforums.org/images/smilies/star.png](http://ubuntuforums.org/images/smilies/star.png)

 
Thank you....but what note? The fonts advice?
 
Nathan

---

### Post by ubuntu-freak on 2008-04-24
Not sure if I like this thread being in the archive. It's been updated for Hardy and could be missed. 
 
Nathan

---

### Post by matthew on 2008-04-25
This thread has been deprecated in favor of a [new version here]("http://ubuntuforums.org/showthread.php?t=766683").

---

