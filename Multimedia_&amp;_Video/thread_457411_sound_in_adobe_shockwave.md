---
title: "sound in adobe shockwave"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by kanaesin on 2007-05-28
Hey, new Ubuntu user (though not new to Linux). I installed Windows Firefox under wine, and then installed Adobe Shockwave 10 plugin from Adobe's site. It works well, except there's absolutely no sound. I installed the flash plugin as well, and it works with sound under wine. I have the same problem with the Shockwave plugin in IE6 under wine. Any ideas?

[http://www.adobe.com/shockwave/welcome/]("http://www.adobe.com/shockwave/welcome/") is a good place to test the plugins; mouse over the buttons and they'll expand and make a *shick* sort of noise.

---

### Post by PARO on 2007-06-09
BUMP! Same problem for me, sound works for some things in Wine and doesn't for others, specifically Shockwave and IMVU, both of which I'd like to get it working with.  I've messed around with the settings in both alsa and oss, and neither seemed to fix the sound.  When I open winecfg in the terminal it says "JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack" But I have libjack0.100 installed, and since sound works in flash and the like could this really cause the problem? Help would be appreciated.

---

### Post by PARO on 2007-06-09
Fixed the Jack error, and tried the esound driver and jack in winecfg too, no luck.

---

### Post by Chappy7777 on 2007-06-10
I installed Windows Firefox under wine....

Just curious. Well, 1st of all Firefox is not a Windows program. It runs on Macs and comes installed on Ubuntu. The newer the distro of Ubuntu, the newer the version of Firefox, obviously. I have 15.0.12 FFox on 6.06, and 2.0.0.4 on another Linux distro, Xandros.  So, why are you running Wine for Firefox? For shockwave? I am not being a hardarse, just that I am fairly new to this and don't understand. 

The one thing that comes to mind is that you will have the same security risks running Windows on Linux as running Windows (XP?) on Windows. If you get malware, I believe it will only affect your Windows files, but keep your antispyware programs handy. 

(Talking from a NooB POV).

---

### Post by PARO on 2007-06-28
Sorry for the late reply Chappy, I sort of gave up hope. But to answer your question, its for Shockwave support, there is none on Linux, so to get it working you have to run a browser through Wine and install the Windows version of Shockwave for it. I use my Wine browser EXCLUSIVELY for Shockwave, so hope that wont expose me too much :)

---

