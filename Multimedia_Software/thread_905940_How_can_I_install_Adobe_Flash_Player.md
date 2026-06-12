---
title: "How can I install Adobe Flash Player"
date: 2008-08-30
forum: Multimedia Software
---

### Post by ivann92 on 2008-08-30
What can I do to watch videos. For example, on Youtube,

---

### Post by minky311 on 2008-08-30
Go into the synaptic package manager by going to system->administration
and then search for adobe flash and check the adobe flash player for installation. Then apply it.

---

### Post by ivann92 on 2008-08-30
What do I do after that, do I still need to download the Flash Player. It still doesn't work.

---

### Post by minky311 on 2008-08-30
What exactly is happening?
And did you restart firefox?

---

### Post by ivann92 on 2008-08-30
Yes, I restarted Firefox and when I try to view a video on Youtube, this is the message that pops up
Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player. 

There is a link to download the flash player, and when I do I don't know how to install it. I am new to Ubuntu.

---

### Post by aysiu on 2008-08-30
Ignore what YouTube tells you to do and listen to what Firefox tells you to do.

More details (with screenshots) here:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by mike1234 on 2008-08-30
sudo apt-get install ubuntu-restricted-extras

M.

---

### Post by aysiu on 2008-08-30
> **mike1234 said:**
> sudo apt-get install ubuntu-restricted-extras

M.
That installs much more than just Adobe Flash Player.

You're also assuming ivann92 even knows where the terminal is to put that command.

---

### Post by mike1234 on 2008-08-30
> **aysiu said:**
> That installs much more than just Adobe Flash Player.

You're also assuming ivann92 even knows where the terminal is to put that command.

  It fixes any problems associated with media players, browser flash, and java errors. My bad for "assuming" I guess. You can search for it in Synaptic.

M.

---

### Post by ivann92 on 2008-08-30
Aysiu, I did what you told me to do, but I still cannot view videos on Youtube, but I went on another website with videos and downloaded the Flash Player.

---

### Post by aysiu on 2008-08-30
> **ivann92 said:**
> Aysiu, I did what you told me to do, but I still cannot view videos on Youtube, but I went on another website with videos and downloaded the Flash Player.
Can you copy and paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then copy and paste the output back here? ```
cat /etc/lsb-release
uname -m
sudo updatedb
locate libflash
cat /etc/apt/sources.list
dpkg -s swfdec-mozilla
dpkg -s mozilla-plugin-gnash
dpkg -s flashplugin-nonfree
``` *Warning*: the third command may take a minute or two to execute.

---

### Post by aysiu on 2008-08-30
> **mike1234 said:**
> It fixes any problems associated with media players, browser flash, and java errors. My bad for "assuming" I guess. You can search for it in Synaptic.

M.
It doesn't really fix errors. It's a metapackage (or empty pointer to other real packages) composed of various multimedia packages, including *flashplugin-nonfree*, which is what Firefox installs if you follow the *Install missing plugins* drop-down menu after visiting a Flash page.

None of the other multimedia packages that *ubuntu-restricted-extras* will help you play Flash videos.

---

### Post by starcannon on 2008-08-30
> **mike1234 said:**
> sudo apt-get install ubuntu-restricted-extras

M.

+1 to this solution, it will get most media things sorted out and working.

---

### Post by mike1234 on 2008-08-30
> **aysiu said:**
> It doesn't really fix errors. It's a metapackage (or empty pointer to other real packages) composed of various multimedia packages, including *flashplugin-nonfree*, which is what Firefox installs if you follow the *Install missing plugins* drop-down menu after visiting a Flash page.

None of the other multimedia packages that *ubuntu-restricted-extras* will help you play Flash videos.

 I'm well aware of what it does.

M.

---

### Post by aysiu on 2008-08-30
> **starcannon said:**
> +1 to this solution, it will get most media things sorted out and working.
As far as playing Flash videos is concerned, it's no different from visiting a Flash page and following the *Install missing plugins* prompt.

The *Install missing plugins* prompt will install the *flashplugin-nonfree* package, which is the Adobe Flash Player.

*ubuntu-restricted-extras* is just a collection of various nonfree codecs: ```
#

[b]flashplugin-nonfree
    Adobe Flash Player plugin installer[/b] 

#

rec: gstreamer0.10-ffmpeg
    FFmpeg plugin for GStreamer 

#

rec: gstreamer0.10-pitfdll [i386]
    GStreamer plugin for using MS Windows binary codecs 

#

rec: gstreamer0.10-plugins-bad
    GStreamer plugins from the "bad" set 

#

rec: gstreamer0.10-plugins-bad-multiverse
    GStreamer plugins from the "bad" set (Multiverse Variant) 

#

rec: gstreamer0.10-plugins-ugly
    GStreamer plugins from the "ugly" set 

#

rec: gstreamer0.10-plugins-ugly-multiverse
    GStreamer plugins from the "ugly" set (Multiverse Variant) 

#

rec: icedtea-gcjwebplugin
    Java plugin based on IcedTea and gcjwebplugin 

#

rec: libdvdread3
    library for reading DVDs 

#

rec: liblame0
    LAME Ain't an MP3 Encoder 

#

rec: msttcorefonts
    Installer for Microsoft TrueType core fonts
    also a virtual package provided by ttf-liberation 

#

rec: unrar
    Unarchiver for .rar files (non-free version) 
``` If installing *flashplugin-nonfree* by itself doesn't work to play Flash, installing the metapackage that include *flashplugin-nonfree* isn't going to make much of a difference either.

---

### Post by mike1234 on 2008-08-30
> **aysiu said:**
> As far as playing Flash videos is concerned, it's no different from visiting a Flash page and following the *Install missing plugins* prompt.

The *Install missing plugins* prompt will install the *flashplugin-nonfree* package, which is the Adobe Flash Player.

*ubuntu-restricted-extras* is just a collection of various nonfree codecs: ```
#

[b]flashplugin-nonfree
    Adobe Flash Player plugin installer[/b] 

#

rec: gstreamer0.10-ffmpeg
    FFmpeg plugin for GStreamer 

#

rec: gstreamer0.10-pitfdll [i386]
    GStreamer plugin for using MS Windows binary codecs 

#

rec: gstreamer0.10-plugins-bad
    GStreamer plugins from the "bad" set 

#

rec: gstreamer0.10-plugins-bad-multiverse
    GStreamer plugins from the "bad" set (Multiverse Variant) 

#

rec: gstreamer0.10-plugins-ugly
    GStreamer plugins from the "ugly" set 

#

rec: gstreamer0.10-plugins-ugly-multiverse
    GStreamer plugins from the "ugly" set (Multiverse Variant) 

#

rec: icedtea-gcjwebplugin
    Java plugin based on IcedTea and gcjwebplugin 

#

rec: libdvdread3
    library for reading DVDs 

#

rec: liblame0
    LAME Ain't an MP3 Encoder 

#

rec: msttcorefonts
    Installer for Microsoft TrueType core fonts
    also a virtual package provided by ttf-liberation 

#

rec: unrar
    Unarchiver for .rar files (non-free version) 
``` If installing *flashplugin-nonfree* by itself doesn't work to play Flash, installing the metapackage that include *flashplugin-nonfree* isn't going to make much of a difference either.

 Then the "problem" would be elsewhere now wouldn't it? Not a plugin issue.

M.

---

### Post by aysiu on 2008-08-30
> **mike1234 said:**
> Then the "problem" would be elsewhere now wouldn't it? Not a plugin issue.

M.
Exactly, which is why I wanted the OP to copy and paste all those commands in order to diagnose the problem.

I want to know exactly what relevant plugins have been installed, whether the processor is 64-bit or not, and if there are any locally installed plugins that may be overriding the package-manager-installed one(s).

---

### Post by mike1234 on 2008-08-30
> **aysiu said:**
> Exactly, which is why I wanted the OP to copy and paste all those commands in order to diagnose the problem.

I want to know exactly what relevant plugins have been installed, whether the processor is 64-bit or not, and if there are any locally installed plugins that may be overriding the package-manager-installed one(s).

  My synaptic only has 2 packages installed by doing a flash search. ubuntu-restricted-extras and flashplugin-nonfree. My position was simply that these 2 packages take care of all my java, flash and media player issues. I have had problems as a result of more than one flash plugin installed. (no flash playback at all) Hopefully he/she doesn't have more than one enabled.

M.

---

### Post by aysiu on 2008-08-31
> **mike1234 said:**
> My synaptic only has 2 packages installed by doing a flash search. ubuntu-restricted-extras and flashplugin-nonfree. Which is really just one package, since *ubuntu-restricted-extras* isn't a real package. It just lists a bunch of other packages, including *flashplugin-nonfree*. > My position was simply that these 2 packages take care of all my java, flash and media player issues. And my position is simply that if the OP has *flashplugin-nonfree* installed and it's not working, installing all those other multimedia packages won't make Flash work either. > I have had problems as a result of more than one flash plugin installed. (no flash playback at all) Hopefully he/she doesn't have more than one enabled. I agree. That's why I gave the OP all those commands to paste into the terminal. The output will help me determine if there are conflicting plugins.

---

### Post by MeowMoo on 2008-08-31
I had the same problem but downloading from Adobe's site did it for me.

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BUIGP](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BUIGP)

Install the tar.gz one and follow these instructions: [http://www.adobe.com/products/flashplayer/productinfo/instructions/](http://www.adobe.com/products/flashplayer/productinfo/instructions/)


Hope I helped. :KS

---

