---
title: "streaming video in ubuntu"
date: 2007-02-13
forum: Multimedia &amp; Video
---

### Post by dboss on 2007-02-13
Hi to everyone

I've recently switched to Ubuntu and not yet very good at it...
Want to ask how it is possible to see streaming videos from internet on Ubuntu, some sites block the execution and don't allow to see it with Mozilla browser...
Is there any plugin or codec to install in order to see them?
Probably they are made to run under IE and Windows...
Can anyone help me solve this problem?

Thx

---

### Post by dmizer on 2007-02-13
well, what plugin are you currently using to view embedded media?  if you're using mplayerplug-in, you'll need to install the mplayerplug-in-0.4.xpi firefox add-on (which may or may not work in mozilla).  you can find the add-on here: [http://mplayerplug-in.sourceforge.net/download.php](http://mplayerplug-in.sourceforge.net/download.php) (last in the list)

---

### Post by dboss on 2007-02-13
I have firefox realplayer plugin not yet mplayer, i'll download it and try to work with this one.
I'll try it and tell you if it works

Thx

---

### Post by DrMega on 2007-02-13
I find that the RealPlayer plugin works but with no sound, and the mplayer one doesn't work at all. I didn't know about the FireFox xpi thingy though so I'll try that later.

One thing to note though is this: Have you installed all the multimedia codecs? By default they are not installed in Ubuntu (because technically they are restricted). If you are new to Ubuntu I would suggest the very first thing to install is Automatix2 which can be found here: [http://www.getautomatix.com/]("http://www.getautomatix.com/")

...that will simplify the process of getting all the multimedia stuff installed and configured.

---

### Post by Red Knuckles on 2007-02-17
> **dmizer said:**
> well, what plugin are you currently using to view embedded media?  if you're using mplayerplug-in, you'll need to install the mplayerplug-in-0.4.xpi firefox add-on (which may or may not work in mozilla).  you can find the add-on here: [http://mplayerplug-in.sourceforge.net/download.php](http://mplayerplug-in.sourceforge.net/download.php) (last in the list)

Where do we install 'mplayerplug-in-0.4.xpi' to? How do we install it? How to install an xpi file?

---

### Post by r4ik on 2007-02-17
Try,

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Multimedia_Player_.28Mplayer.29_with_plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Multimedia_Player_.28Mplayer.29_with_plug-in_for_Mozilla_Firefox)

or

[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Multimedia_Player_.28Mplayer.29_with_plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Multimedia_Player_.28Mplayer.29_with_plug-in_for_Mozilla_Firefox)

---

### Post by Red Knuckles on 2007-02-17
> **r4ik said:**
> Try,

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Multimedia_Player_.28Mplayer.29_with_plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Multimedia_Player_.28Mplayer.29_with_plug-in_for_Mozilla_Firefox)

or

[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Multimedia_Player_.28Mplayer.29_with_plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Multimedia_Player_.28Mplayer.29_with_plug-in_for_Mozilla_Firefox)

Mozilla-mplayer is already installed. The question is how to install 'mplayerplug-in-0.4.xpi' which is an xpi file. What I did was download it to '/home/username' and then ran:

$sudo cp mplayerplug-in-0.4.xpi /usr/lib/firefox/extensions
$sudo cp mplayerplug-in-0.4.xpi /usr/lib/swiftfox/extensions

then using 'Alt-F2' I opened Firefox and Swiftfox as root and the xpi install box opened before the browsers so I just clicked on 'install' to install the extension in Firefox and Swiftfox. So far though I don't see any improvement in playing embedded video. Will check fruther.

---

### Post by r4ik on 2007-02-17
It is a Firefox extension. Download the file wherever you want, then in Firefox go to Tools, Extensions. Drag that .xpi file into the Extensions window that should have opened up and it will install it for you.

Providing however that you've installed MPlayer correctly from the repositories, you should not need to do this.

---

