---
title: "can't view Daily Show video"
date: 2009-06-21
forum: Multimedia Software
---

### Post by mnoyes on 2009-06-21
Ubuntu 8.04, Firefox 3.0.11, Flashplugin-nonfree, works on other sites (nytimes.com video, youtube). Problem started yesterday, before that no problems. Daily Show seems to be using new flash player... Anyone else having this problem? Any ideas?

The error message: > Error loading stylesheet. RSL [http://media.mtvnservices.com/global/flex/rsl/framework_3.2.0.3958.swz](http://media.mtvnservices.com/global/flex/rsl/framework_3.2.0.3958.swz) failed to load. Error #2046

---

### Post by rcrane on 2009-06-22
Same problem.  Any ideas?

---

### Post by mnoyes on 2009-06-22
No clue:(

I'm guessing other providers are using the same flash player as Comedy Central, so other Ubuntu/Firefox users should be having this problem...

---

### Post by firebug2 on 2009-06-22
Tried to reinstall the flashplayer and shockwave plugin - didn't help (on hardy - does the same happen on intrepid and/or jaunty?).

The workaround is to watch it on hulu.com :)

---

### Post by Therion on 2009-06-22
> **mnoyes said:**
> 

The error message: Error loading stylesheet... 
Because Jon Stewart HAS no style?









/Rimshot.
//Try the veal.

---

### Post by gamblor01 on 2009-06-22
Open Firefox, type this into the address bar:

```

about:plugins

```

and press enter.  Look for the "Shockwave Flash" entry (specifically, the library should be libflashplayer.so).  What is the version number?  This is just a guess, but perhaps you need flash 10.

I have 8.04 with Firefox 3.0.11 and Flash 9 right here on my work laptop.  I'm going to try upgrading it to Flash 10 right now and then I'll post the results.

---

### Post by gamblor01 on 2009-06-23
Yep, it looks like the flashplugin-nonfree fails (it was version 9.0.159 or something like that?) but the latest from adobe.com (10.0 r22) works fine.  Here are the steps I used to get things working:

1. uninstall flashplugin-nonfree

```

sudo apt-get remove flashplugin-nonfree

```2. Download the .deb file for Ubuntu 8.04+ from adobe's website

[http://www.adobe.com/go/EN_US-H-GET-FLASH](http://www.adobe.com/go/EN_US-H-GET-FLASH)

3. install the package

```

sudo dpkg -i install_flash_player_10_linux.deb

```Works like a champ now.

---

### Post by mnoyes on 2009-06-23
Removed flashplugin-nonfree, followed link -- [http://www.adobe.com/go/EN_US-H-GET-FLASH;](http://www.adobe.com/go/EN_US-H-GET-FLASH;) downloaded flash player 10 deb file for Ubuntu, installed. 

No go: now I get this message: "To view this movie you need the Adobe Flash Player plugin. You also need JavaScript enabled in your browser."

And the synaptic package manager urged me to download a more recent version of Flash 10, 10.0.22.87-2, which I did. 

I checked for the plugin, using about:plugins in the address bar, but flash is not listed.

Still no go. (Java is enabled, by the way.)

What am I missing?

-- from bad to worse: now I can't view video on the New York Times website either. It points me to the adobe flash plugin, then to manual install, which leads to the previous version: 10.0.22.87-1

---

### Post by mnoyes on 2009-06-23
Update:

followed Gamblor01's instructions to the letter and it works. 

I updated to latest version, via update manager, and it still works -- go figure!

Thanks very much for your help!:)

---

### Post by gamblor01 on 2009-06-23
[quote=mnoyes]
I checked for the plugin, using about:plugins in the address bar, but flash is not listed.
[/quote]
It must not have installed the library.  You must have libflashplayer.so somewhere that Firefox looks for it.  Typical locations are places like:

~/.mozilla/plugins
/usr/lib/mozilla/plugins
/usr/lib/adobe-flashplugin/libflashplayer.so

Sometimes it will install where the installer tells it to and then it will create a symbolic link to it inside of ~/.mozilla/plugins or something like that.  If you want to know where you have it on your system try something like this:

```

sudo find / -mount -name libflashplayer.so

```It basically says look in / (the root directory) for a file by the name of libflashplayer.so, and if there are other drives mounted (such as a second hard drive running Windows), don't look on those mounted drives (i.e. only look on the current filesystem).


[quote=mnoyes]
Update:

followed Gamblor01's instructions to the letter and it works. 

I updated to latest version, via update manager, and it still works -- go figure!
[/quote]

I'm not sure what you mean by that but glad to know it works.  What process did you previously follow that didn't work -- Using synaptic to uninstall instead of the command line?

Oh well...it works!

---

### Post by mnoyes on 2009-06-24
For the sake of others who may make the same mistakes:

I uninstalled flashplugin_nonfree, using synaptic package manager, then went to the Adobe site and downloaded the flash 10 .deb file. BUT, instead of saving the file to disk and installing via the command line (as per your suggestion), I chose to install using the option presented when you download (you can choose save to disk or install). This just copied the install file without actually installing the plugin.

When I removed flash and then reinstalled, following your instructions, it worked.

---

### Post by antonioprt on 2009-06-24
I followed the steps provided by gamblor01, but unfortunately they didn't work for me (same error messages as mnoyes, even if I follow the exact steps).

Here is (half) a solution if someone else is having the same problem:

- go to getfirefox.com and download the latest version for linux
- extract the files to a folder of your choosing
- go to: /usr/lib/adobe-flashplugin 
- copy the file libflashplayer.so (it should be 9,6 Mb in size)
- paste it in the 'firefox/plugins' folder of the location where you extracted you new firefox
- go up one level, execute the 'firefox' file and go watch your videos! :)

This is not an efficient solution, but it is working for now.

Note: for this to work, I had to follow the previous suggestions, lose the ability to play any flash videos, and then make the updates suggested by the update manager.

---

### Post by 0x29a on 2009-06-25
@gamblor01:

Man, the sudden failure of the flash plugin at that site was frustrating. I hadn't had time to really work on the issue. Your method made it super simple. Thanks for the tip.

@mnoyes:

Thanks for posting the question. I've followed gamblor01's suggestions and The Daily Show works again.

Andrew

P.S. And what ever happened the "thank user" button?

---

### Post by gorlando on 2009-07-11
i am running Hardy.

i have followed the instructions in this thread and still i am unable to successfully view daily show videos.

i get the same error message 2046

any help with this issue would be appreciated.

gary

------------
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
Java(TM) Plug-in 1.6.0_06-b02

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_06

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
application/x-java-applet;jpi-version=1.6.0_06 	Java 		Yes
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
application/x-java-bean;jpi-version=1.6.0_06 	Java 		Yes
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by gamblor01 on 2009-07-14
Your about:plugins shows that you still have an old version 9 flashplayer installed:

> 
File name: libflashplayer.so
    Shockwave Flash 9.0 r124
I can't be certain which implementation that is (there are many different people who have created flash players), but just run this command and it should take care of any and all flash installed on your system.

```

sudo apt-get remove adobe-flashplugin flashplugin-installer flashplugin-nonfree flashplugin-nonfree-extrasound libflashsupport swfdec-mozilla mozilla-plugin-gnash


```Now go download the .deb file from Adobe's website ([http://www.adobe.com/go/EN_US-H-GET-FLASH](http://www.adobe.com/go/EN_US-H-GET-FLASH)) and install it with the dpkg command like I outlined before.

---

### Post by LiederSinger on 2009-07-18
For me, gamblor10's solution did not take effect until I re-initialized the plugins database following the instructions found at the following link:

[http://support.mozilla.com/en-US/kb/Troubleshooting+plugins?style_mode=inproduct#Re_initializing_the_plugins_database](http://support.mozilla.com/en-US/kb/Troubleshooting+plugins?style_mode=inproduct#Re_initializing_the_plugins_database)

Thanks gamblor10. You saved me a lot of time.

---

### Post by Pythagorean Metronome on 2009-08-11
I finally solved this problem.  I have Ubuntu 9.04.  I couldn't get the videos on The Daily Show to play, but I could watch Youtube.  Here's what I did:

(using synaptic and online tutorials for almost everything)

1. Uninstall everything involving any kind of flash (Adobe, SWF...)
2. Install Firefox 3.5
3. Install Adobe Flash 10
4.  Using Nautilus:  Make a copy of the flashplugin.so from the Adobe folder in Lib and put that copy in the Mozilla plugins folder in LIb.
5.  DELETE the flashplugin-alternate.so that is sitting there in the Mozilla plugins folder.

The "make copy" function and the "paste" function you will use by right clicking are available to you if you open a terminal and type in "sudo nautilus".  Once you have done that you look in these two places:

 Filesystem-->User-->Lib-->adobe
 Filesystem-->User-->Lib-->Mozilla-->Plugins folder.

And what you want to do is replace the flashplugin-alternate.so in the mozilla plugins folder with flashplugin.so from the adobe folder.

Make sure to close everything and open a new firefox browser, then go to Daily Show website and the videos will play.

---

### Post by madjackrogers on 2009-08-14
Thanks a ton, guys.  I've had this problem for a while, and I just now got around to fixing it.  It's pretty great to have a forum like this for Ubuntu.

---

### Post by jshpro2 on 2009-09-24
I get this problem on windows vista in both IE and FF and I have flash 10 player :-/

Still no solution

---

### Post by markbuntu on 2010-01-06
I am using hardy and, not paying a lot of attention installed flash 10 from the adobe site. Of course, it did not work, still showing flash9 in firefox.

To fix it all I had to do was move the usr/lib/adobe-flashplugin/libflashplayer.so to usr/lib/flashplayer-nonfree/. Now I have flash10.0r42 that works with Hulu.

Oops, update manager has a new flash 10 for me...lets see whats up with that...stand by.

Ok, still the same 10.0r42 but there is now a flashplayer.so in usr/lb/adobe-flashplugin that was not there before because I moved it. Hmmmmm,

---

### Post by neu5eeCh on 2010-02-14
I've been working on this, off and on again, ever since installing Linux (about 6 weeks ago). I've tried every suggestion out there (including above) and none of them work. I've tried it on different distros. **Daily Show** just doesn't play on **any** of my Linux boxes or **any** of my distros - and I've read of this problem elsewhere. The weirdest thing is that some users claim they have no problem and their configuration is just the same as the next person's (who **can't** watch the videos). I can't tell if it's a Linux problem or a Flash problem. I'm leaning toward Linux.

But the whole thing mystifies me.

---

### Post by HappyFeet on 2010-02-14
I'm watching an episode right now as I type. Works great. Try installing mozilla-mplayer and non-free-codecs.
```
sudo apt-get install mozilla-mplayer non-free-codecs
```

---

### Post by HappyFeet on 2010-02-14
> **VTPoet said:**
> I've been working on this, off and on again, ever since installing Linux (about 6 weeks ago). I've tried every suggestion out there (including above) and none of them work. I've tried it on different distros. **Daily Show** just doesn't play on **any** of my Linux boxes or *an* of my distros - and I've read of this problem elsewhere. The weirdest thing is that some users claim they have no problem and their configuration is just the same as the next person's (who **can't** watch the videos). I can't tell if it's a Linux problem or a Flash problem. I'm leaning toward Linux.

But the whole thing mystifies me.

How did you install flash? 32 or 64bit? And no, it's not a linux issue. Flash is a third party add-on.

---

### Post by neu5eeCh on 2010-02-14
> **HappyFeet said:**
> I'm watching an episode right now as I type. Works great. Try installing mozilla-mplayer and non-free-codecs.
```
sudo apt-get install mozilla-mplayer non-free-codecs
```

I'm willing to try that. I'm guessing that I should uninstall my current flash installation?

---

### Post by neu5eeCh on 2010-02-14
> **HappyFeet said:**
> How did you install flash? 32 or 64bit? And no, it's not a linux issue. Flash is a third party add-on.

It may not be a linux issue. But if it's not, then why does it work on some linux boxes and not on others? I've read differing opinions. Some linux pros (and I'm not one of them) argue that the problem is with Linux packages. They note that Flash works much better on Open Solaris because it's a backward compatible kernel (may not be the correct terminology).

---

### Post by neu5eeCh on 2010-02-14
> **HappyFeet said:**
> I'm watching an episode right now as I type. Works great. Try installing mozilla-mplayer and non-free-codecs.
```
sudo apt-get install mozilla-mplayer non-free-codecs
```

Well... you're gonna' have to add yourself to the row of tin ducks shot down by my system. I tried your solution and trying to play Daily Show locked up firefox hard and fast. Is Shockwave Flash installed on your system?

---

### Post by neu5eeCh on 2010-02-14
I hereby give up on Linux & the Daily Show.

I can watch Hulu, Youtube, etc... with no problems, but Daily Show locks up every browser I've run - Firefox, Opera, Chrome and SeaMonkey. Presumably, they're all using the same Flash plugin so... I'll be using Windows until the next Linux Flash Update.

But... if anyone has had problems comparable to mine, and has solved them by methods other than Firefox & Flash reinstalls, or by replacing the flashplugin-alternate.so file, let me know.

---

### Post by Yellow Pasque on 2010-02-14
VTPoet, what happens when you start the browser from the terminal? (I'm looking for a specific error message). Also, you never said what video card/driver you have and whether your system was 32-bit or 64-bit (you went off on a tangential rant).

---

### Post by neu5eeCh on 2010-02-15
> **Temüjin said:**
> VTPoet, what happens when you start the browser from the terminal? (I'm looking for a specific error message). Also, you never said what video card/driver you have and whether your system was 32-bit or 64-bit (you went off on a tangential rant).

**Video Info (HP Laptop DV1000)**: 

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

**System**: 32-bit

**Terminal** (*Firefox executed as both User and Sudo - just to see...*)

vtpoet@Traveller:/opt/google/chrome$ **firefox**

(firefox-bin:24153): GLib-WARNING **: g_set_prgname() called multiple times
[FDLProc] canHandle()
[FDLProc] canHandle()
[FDLProc] canHandle()
[FDLProc] canHandle()
[FDLProc] canHandle()
[FDLProc] canHandle()
[FDLProc] canHandle()
Killed
vtpoet@Traveller:/opt/google/chrome$ **sudo firefox**

(firefox-bin:24241): GLib-WARNING **: g_set_prgname() called multiple times
[FDLProc] canHandle()
[FDLProc] canHandle()
^C
vtpoet@Traveller:/opt/google/chrome$ ^C
vtpoet@Traveller:/opt/google/chrome$ 

I killed in the first instance because it simply locked up when waiting for Daily Show.

I ^C'd in the second instance when Firefox joined the realm of the undead. I ran Firefox from the Chrome directory because I executed Chrome from terminal  first, & with the same results.


**Tangential Rant**: 

*I have no idea what you're talking about.*

---

### Post by lidex on 2010-02-17
Just ignore if you've tried this before. This script has worked for many. Right-click this link and "save as" to your home directory:
[http://ukanth.in/files/flash.sh]("http://ukanth.in/files/flash.sh")
Now open a terminal and execute with this command;
```
sudo bash flash.sh
```
You can view the script on this page:
[http://ukanth.in/blog/?p=48]("http://ukanth.in/blog/?p=48")

---

### Post by fixitdude on 2010-03-25
Why didn't someone flag that script above as a possible security problem?

You are downloading something from a strange site (which is down now) and installing it as ROOT!!!

If you used that script YOU MAY BE INFECTED! There was no reason apt-get couldn't have gotten the libcurl etc.. packages, and most likely they were already installed.

I don't know what you could do except uninstall "libcurl3 libnss3-1d libnspr4-0d" and re-install them from your normal apt-get sources. Then hope, because they could have done anything with a script as root.

How hard was it to look and see "http:" to a UNTRUSTED SITE and then just NOT DO IT????


On the upgrade to flash 10 what I found that worked is to simply use the System -> Synaptic Package Manager.

Hit "Reload" so your sources are up to date, and if you haven't updated everything lately you should do that. Close Firefox.

Now find "flashplugin-nonfree" by scrolling down the list. Select it for install (or upgrade).

Don't ask me why Ubuntu / Adobe is so lame about this simple install, but now you need to copy the new "libflashplayer.so" over to your user's plugin folder using a terminal.

If you want to save the old one (if it's still there):

mv ~/.mozilla/plugins/libflashplayer.so ~/libflashplayer-old1.so

sudo cp /usr/lib/adobe-flashplugin/libflashplayer.so ~/.mozilla/plugins/

If you go to Tools --> Add-ons in Firefox and select Plugins, you may see the old version and the new version, but it will use the new version so don't worry. Proof is if Hulu works again. You may need to clean up some directories if this doesn't work, see my next post.

You could probably download the plugin from adobe as previously mentioned, then just copy it into the plugin folder as shown above, but I didn't do it that way so I don't know if that would just work.



For security, and optional, I recommend making a new user that you will use just for flash and heavy javascript sites. This user would have no important files or private data on it so if there is ever a breach with flash or javascript you are OK.

To use firefox from that user, open a terminal window and log in as that user via "local" ssh, it allows quick X11 forwarding.

ssh -2 -Xc blowfish alt-user-name@127.0.0.1

Now type in "firefox &", then hit return. You can run that Firefox while your "normal" user Firefox is running. Very cool. Just leave the terminal window open and when you need to go to a flash site, start the "safe" Firefox.

Don't forget to copy the "libflashplayer.so" over for this new user as shown above.

---

### Post by fixitdude on 2010-03-27
I ran into *other* problems on another system trying to view Hulu shows, the fix is below, after the rant.

Why do these people always want the latest version? Why can't they just be compatible with the older versions, keep track of what versions are hitting the site and WAIT until most of the people visiting are using a newer version.

I don't like being forced to upgrade to a newer, possibly buggy version when I had a perfectly good setup the way it was.

And all those highly paid programmers over at Adobe can't make this a easy thing? WTF? STOP FORCING ME TO UPGRADE TILL YOU GET IT RIGHT, BASTARDS!!! 

Rant done....

If you still have problems, you need to get rid of any possible old copies of the old flash.

You can save the old one if you want, put it somewhere else, don't just rename it in place.

Note: I am not running a 64 bit version!!! As I understand it you need to install the "nspluginwrapper" stuff for that but like I said above don't use that untrusted "deb" file or the script, do it manually.

If you don't know if you are running a 64 bit version, do a "uname -m" and if it says "x86_64" somewhere in the line then you are 64 bit.

Plus, if you aren't running 64 bit, you won't have "nspluginwrapper" available, if I understand right.

Just to be clear, I'm running Hardy.

Check to make sure you have the correct NEW flash version where it should be, look at it's size against the new one you got from Adobe. And get rid of any old versions that may still be in there.

ls -al ~/.mozilla/plugins/

All you need for flash to work is a copy of "libflashplayer.so" in that folder! It doesn't need to be anywhere else!

I also got rid of any other copies in any other place, and had to remove "flashplugin-nonfree" on that system for some reason. And getting rid of "swfdec-mozilla" and "mozilla-plugin-gnash" is a good idea too.


sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

sudo apt-get update
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo apt-get -y purge flashplugin-nonfree

If you are still having problems, check all those directories for "symbolic links" to other places for flash stuff. The above should have removed them but who knows...

That made it work for me. Hope this helps others.

---

### Post by gonvelho on 2010-04-04
No, it still didn't work. Still the same annoying massage in Hulu and The Daily Show :mad:

---

### Post by RedRat on 2010-04-04
Hmm. I can go to the Daily show and watch it. But I am running 8.04, maybe something to do with later versions of Ubuntu. No problem on Comedy Central or YouTube.

---

### Post by lidex on 2010-04-06
Just go here:
[http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")

Scroll down to:
"Flash Optimization"

---

### Post by UserSince2003 on 2010-04-12
Try this.  It worked for me:
[http://kevin.vanzonneveld.net/techblog/article/fix_flash_problems_on_ubuntu/](http://kevin.vanzonneveld.net/techblog/article/fix_flash_problems_on_ubuntu/)

---

