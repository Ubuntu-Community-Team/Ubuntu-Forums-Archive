---
title: "Flashplayer working on some sites, not others"
date: 2008-10-24
forum: Multimedia Software
---

### Post by gaten on 2008-10-24
I have a very odd and frustrating problem. It seems that Abode flash player, installed form their site via the .tar.gz file, works on some sites and not others.

For instance, youtube.com tells me that I need to install the latest flash player, while bestofyoutube.com plays everything just fine. Metacafe works fine as well, but Hulu.com doesn't work at all.

I've uninstalled this plugin every way possible. Using Synaptec, manually deleting libflashplayer.so from the system.

I've tried reinstalling everything above, as we as install flashplugin-nonfree etc etc. Nothing seems to work. I've tried ff 2, ff 3.0.3, and minefield, all with the same results. 

I've also tried disabeling all of my extentions and running firefox like that with no luck.

This happened after the last update. Everything was fine, I was watching Hulu at the time. I updated and went to bed. The next morning I restarted firefox and the problems started. 

Does anyone have any suggestions? This is getting really annoying. 

Thank you in advance.

---

### Post by eternalnewbee on 2008-10-24
Take a look here and see if it helps:
[http://ubuntuforums.org/showthread.php?t=953377](http://ubuntuforums.org/showthread.php?t=953377)

---

### Post by Gausian on 2008-10-24
download and install Flash 10 from adobe's site.  they have .debs now for the installation.

v10 is much better than previous releases.

---

### Post by gandaran on 2008-10-24
can you post here the full results of **about: plugins** type in firefox url bar without spaces

---

### Post by gaten on 2008-10-24
> can you post here the full results of **about: plugins** type in firefox url bar without spaces 	

Here you go.

```
**Shockwave Flash**

 File name:  libflashplayer.so Shockwave Flash 10.0 r12   MIME Type Description Suffixes Enabled    application/x-shockwave-flash Shockwave Flash swf Yes   application/futuresplash FutureSplash Player spl Yes  **Default Plugin**

 File name:  libnullplugin.so The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.   MIME Type Description Suffixes Enabled    * All types .* No  **Java(TM) Plug-in 1.6.0_07-b06**

 File name:  libjavaplugin_oji.so Java(TM) Plug-in 1.6.0_07   MIME Type Description Suffixes Enabled    application/x-java-vm Java 
Yes   application/x-java-applet Java 
Yes   application/x-java-applet;version=1.1 Java 
Yes   application/x-java-applet;version=1.1.1 Java 
Yes   application/x-java-applet;version=1.1.2 Java 
Yes   application/x-java-applet;version=1.1.3 Java 
Yes   application/x-java-applet;version=1.2 Java 
Yes   application/x-java-applet;version=1.2.1 Java 
Yes   application/x-java-applet;version=1.2.2 Java 
Yes   application/x-java-applet;version=1.3 Java 
Yes   application/x-java-applet;version=1.3.1 Java 
Yes   application/x-java-applet;version=1.4 Java 
Yes   application/x-java-applet;version=1.4.1 Java 
Yes   application/x-java-applet;version=1.4.2 Java 
Yes   application/x-java-applet;version=1.5 Java 
Yes   application/x-java-applet;version=1.6 Java 
Yes   application/x-java-applet;jpi-version=1.6.0_07 Java 
Yes   application/x-java-bean Java 
Yes   application/x-java-bean;version=1.1 Java 
Yes   application/x-java-bean;version=1.1.1 Java 
Yes   application/x-java-bean;version=1.1.2 Java 
Yes   application/x-java-bean;version=1.1.3 Java 
Yes   application/x-java-bean;version=1.2 Java 
Yes   application/x-java-bean;version=1.2.1 Java 
Yes   application/x-java-bean;version=1.2.2 Java 
Yes   application/x-java-bean;version=1.3 Java 
Yes   application/x-java-bean;version=1.3.1 Java 
Yes   application/x-java-bean;version=1.4 Java 
Yes   application/x-java-bean;version=1.4.1 Java 
Yes   application/x-java-bean;version=1.4.2 Java 
Yes   application/x-java-bean;version=1.5 Java 
Yes   application/x-java-bean;version=1.6 Java 
Yes   application/x-java-bean;jpi-version=1.6.0_07 Java 
Yes
```

> download and install Flash 10 from adobe's site.  they have .debs now for the installation.

v10 is much better than previous releases. 	

I tried that as well, sorry forgot to mention it. 

eternalnewbee: I'm going to check that out later today, thanks :)

I'd like to reemphasize that flash used to work, and no configuration changes were made by me. I was using flash 10beta still, but it was working fine.

Thanks for all your reply's.

---

### Post by gandaran on 2008-10-24
> Shockwave Flash

 File name:  libflashplayer.so Shockwave Flash 10.0 r12   MIME Type Description Suffixes Enabled    application/x-shockwave-flash Shockwave Flash swf Yes   application/futuresplash FutureSplash Player spl Yes  Default Plugin

 File name:  libnullplugin.so The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.   MIME Type Description Suffixes Enabled    * All types .* No  Java(TM) Plug-in 1.6.0_07-b06

 File name:  libjavaplugin_oji.so Java(TM) Plug-in 1.6.0_07   MIME Type Description Suffixes Enabled    application/x-java-vm Java 
Yes   application/x-java-applet Java 
Yes   application/x-java-applet;version=1.1 Java 
Yes   application/x-java-applet;version=1.1.1 Java 
Yes   application/x-java-applet;version=1.1.2 Java 
Yes   application/x-java-applet;version=1.1.3 Java 
Yes   application/x-java-applet;version=1.2 Java 
Yes   application/x-java-applet;version=1.2.1 Java 
Yes   application/x-java-applet;version=1.2.2 Java 
Yes   application/x-java-applet;version=1.3 Java 
Yes   application/x-java-applet;version=1.3.1 Java 
Yes   application/x-java-applet;version=1.4 Java 
Yes   application/x-java-applet;version=1.4.1 Java 
Yes   application/x-java-applet;version=1.4.2 Java 
Yes   application/x-java-applet;version=1.5 Java 
Yes   application/x-java-applet;version=1.6 Java 
Yes   application/x-java-applet;jpi-version=1.6.0_07 Java 
Yes   application/x-java-bean Java 
Yes   application/x-java-bean;version=1.1 Java 
Yes   application/x-java-bean;version=1.1.1 Java 
Yes   application/x-java-bean;version=1.1.2 Java 
Yes   application/x-java-bean;version=1.1.3 Java 
Yes   application/x-java-bean;version=1.2 Java 
Yes   application/x-java-bean;version=1.2.1 Java 
Yes   application/x-java-bean;version=1.2.2 Java 
Yes   application/x-java-bean;version=1.3 Java 
Yes   application/x-java-bean;version=1.3.1 Java 
Yes   application/x-java-bean;version=1.4 Java 
Yes   application/x-java-bean;version=1.4.1 Java 
Yes   application/x-java-bean;version=1.4.2 Java 
Yes   application/x-java-bean;version=1.5 Java 
Yes   application/x-java-bean;version=1.6 Java 
Yes   application/x-java-bean;jpi-version=1.6.0_07 Java 
Yes

is this the full output? no other flash application or version installed?
Shockwave Flash 10.0 r12 is the latest flash and the same as the last beta release

---

### Post by gaten on 2008-10-24
> is this the full output? no other flash application or version installed?
Shockwave Flash 10.0 r12 is the latest flash and the same as the last beta release 	

That;s the full input. Note that was for minefield.

The flash is from the .deb or the .tar.gz file (can't remember which at this point, i've tried both).

---

### Post by gaten on 2008-10-25
Update.

This morning, I opened up a video on theonion.com and it worked! But, of course, as soon as I selected the *next* video, I got sound with no video at all. So it worked for one whole video, and then stopped. 

I'm thinking my next move will be to remove every version of firefox from my computer, then try it all from scratch. This is really annoying, is no one else having these problems?

---

### Post by jwhiz on 2008-10-26
I am!
I'm going to disable gnash and see if that's interfering (I can't get anything to run on youtube, or the sound/video on iLike in Facbook). I think an older version of Shockwave flash player may still be aorund too. Now that windows xp doesn't want to play nice (not valid after two years? too many installs on my owned copy, which I've used exactly once? bah! - except all the good games are still windows...) I am pushing myself to do more in Linux, why not since main computer is a mac, but laptops too hot for gaming...
yes,the flash or java thing or whatever is pretty annoying.

---

