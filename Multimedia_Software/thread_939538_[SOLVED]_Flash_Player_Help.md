---
title: "[SOLVED] Flash Player Help"
date: 2008-10-06
forum: Multimedia Software
---

### Post by mrmaster on 2008-10-06
Hello,

I'm a brand new ubuntu user that recently switched from vista and I'm encountering some problems. The flash videos from the porn sites that I go to will not load and I'm not sure why. I've installed the flash player from adobe, gnash swf viewer and swfdec flash player and none of them are loading. I just get a black screen where the video's are supposed to have loaded. Even youtube does not work.

I do not know anything about linux and would appreciate it if you can keep the instructions very detailed. 

Thanks

---

### Post by saggitheman on 2008-10-06
HAHA! did you install the flashplayer by that instructions that is in adobe's site? Or have you turned Java off??

---

### Post by minky311 on 2008-10-06
First uninstall gnash swf viewer and swfdec flash player by going to System->Administration->Synaptic package manager. Then do a search for flash player.The only thing you should have installed is flashplugin-nonfree.
If that still doesn't solve it post back here.

---

### Post by rlj1965 on 2008-10-06
> **mrmaster said:**
> Hello,

I'm a brand new ubuntu user that recently switched from vista and I'm encountering some problems. The flash videos from the porn sites that I go to will not load and I'm not sure why. I've installed the flash player from adobe, gnash swf viewer and swfdec flash player and none of them are loading. I just get a black screen where the video's are supposed to have loaded. Even youtube does not work.

I do not know anything about linux and would appreciate it if you can keep the instructions very detailed. 

Thanks

HA HA! Writing into a frum to ask for help viewing free porn! That's funny!

---

### Post by mrmaster on 2008-10-07
Hi,

I have followed the directions on the site and installed adobe correctly since it gave me installation complete message after i was done. 

I've also went into synaptic package manager and uninstalled gnash and swf view player. The flash videos are still not showing. In youtube i keep getting this message " Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player. "

I have firefox 3 installed and javascript enabled. I went into Adobes sight and had their flash player installed. 

In synaptic manager i have marked as installed
-flashplugin nonfree 9.0.124 

What should I try next?

---

### Post by gandaran on 2008-10-07
this is what you get when you install a lot of things without knowing what you doing!

type **about: plugins** (without spaces) in firefox url bar, paste the full output here

---

### Post by mrmaster on 2008-10-08
The only way to try to learn something is break it first i guess :). I typed about:plugins in the firefox URL and this is what i got


Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
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
GCJ Web Browser Plugin (using IcedTea) 1.0

    File name: gcjwebplugin.so
    The GCJ Web Browser Plugin (using IcedTea) executes Java applets.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	IcedTea 	class,jar 	Yes
application/x-java-applet 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-applet;jpi-version=1.6.0_00 	IcedTea 	class,jar 	Yes
application/x-java-bean 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-bean;jpi-version=1.6.0_00 	IcedTea 	class,jar 	Yes

---

### Post by HappyHenry on 2008-10-08
An honest person!! Yeah! We all have had a peek now and then.
Lighten up on, "this is what you get..."
If we are afraid to try things then we never learn. So maybe a few conflicts with plugins. no big deal. It can always be fixed with Ubuntu.
There is a great sticky on the very begging of this section of Multimedi&video that I followed and got everything working, even boobie movies, lol. Ill come back and post link to the tutorial. If you follow it step by step you should have no problems.

HERE IT IS, [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Good luck. Be sure to read and apply each step as you go. It is five pages and seems like a lot at first glance but if you follow it from step one and on, it will be worth it. It only took me about a half hour the first time through the tutorial. You can copy and paste the commands given into your Terminal, so as, not to make a typo. Read through each step and make sure you understand what is being explained. There is also a trouble shooting section at the end of the tutorial. (dont skip down and start trying stuff. There are steps in the tutorial that purge files you need to purge for new files to work correctly, [COLOR="Red"]step by step works[/COLOR].) This tutorial worked great for me on many diff systems and even Firefox 3. Firefox 3 sucks and you may want to change back to the older Firefox. The older one works much faster and far less problems than the new one. Surely all the porno will work on the older Firefox....ur, so I've been told, LOL ;)
I have subscribed to your post and will check back to see how you are doing. If you decide you want to change, to the older Firefox, we can get you set for that or if you have problems with the tutorial above post what happens. _I _prob dont know the answer but I'm sure it's here (in the forums) some where and I (and many others im sure) will be happy in helping you find the answers that will get it workin' for ya.

---

### Post by ellalan on 2008-10-08
Hi
Go to synaptics and remove the following:1.swfdec,2.gnash,3.flash plugin-nonfree.
Then still in synaptics, see whether "sun-java6" is installed, all of them EXCEPT the ones with extensions -doc and-source(ex;sun-java6-doc).
Now you can go to any site using flashplayer(like youtube) and install the player from that site(it will give you the option to install "flash plugin-non free and you can accept it).
This all you have to do to install the flashplayer. HTH

---

### Post by mrmaster on 2008-10-10
Apparently all I was missing was sun-java6 jdk. After installing it the video's work fine. I can finally switch to Ubuntu. Thank you everyone :)

---

### Post by SuperSonic4 on 2008-10-10
Don't forget to mark the thread as solved so others know what to do :)

---

