---
title: "Hulu isn't working."
date: 2009-04-27
forum: Multimedia Software
---

### Post by skeptics4life on 2009-04-27
Why is it that Hulu shows up as a blank screen.  I have all of the flash updates and I still can't view my TV shows.  What must I install?

---

### Post by gandaran on 2009-04-27
> **skeptics4life said:**
> Why is it that Hulu shows up as a blank screen.  I have all of the flash updates and I still can't view my TV shows.  What must I install?
it depends on what you have installed for flash!
install only adobe flash, don't install gnash and swfdec!

---

### Post by Wiebelhaus on 2009-04-27
Now this is just unacceptable , Hulu MUST WORK!

from our mates @ [www.psychocats.net]("http://www.psychocats.net/ubuntu/flash")

Check the link for all the pretty pictures!

---

### Post by skeptics4life on 2009-04-27
Which flash player should I use? There are 4 options:

YUM for Linux
.tar.gz for Linux
.rpm for Linux
.deb for Ubuntu 8.04+

I think the .deb is the correct one but I'm not sure.

---

### Post by gandaran on 2009-04-28
> **skeptics4life said:**
> Which flash player should I use? There are 4 options:

YUM for Linux
.tar.gz for Linux
.rpm for Linux
.deb for Ubuntu 8.04+

I think the .deb is the correct one but I'm not sure.
the .deb and tar.gz packages are the ones you can install in ubuntu but I wouldn't install any from adobe.com as you wont be able to get updates for flash, rather install flash from the repository, it's exactly the same adobe flash and will be updated when adobe releases a new version!
for ubuntu 8.10 and older install the flashplugin-nonfree from the repositorys/synaptic, for ubuntu 9.04 jaunty install the flashplugin-installer package from synaptic.
make sure you don't have any open source gnash and swfdec flash plugins installed, any one of these installed wont let firefox work with adobe flash.

---

### Post by markbuntu on 2009-04-28
Just do this. It always fixes my flash problems

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by inobe on 2009-04-28
oh crap, i wish i got here sooner.

if this is installed, remove it from synaptic.

**swfdec-mozilla**

i had the same exact problem, had the restricted blah blah and other bells and wistles, uninstalled/ reinstalled, an entire week of trashing my system all i needed was one minute removing that.

---

### Post by skeptics4life on 2009-04-28
I solved the problem by un-installing the mozilla-plugin-gnash.  Now I can view Hulu.

Thanks for all of your help everyone! :)

---

### Post by oscarmeyer51 on 2009-04-28
FYI to all.

I did a completely clean install for JJ and had the same Hulu issue. Turns out the default install does do the swfdec-mozilla. Once I removed that, Hulu worked like a champ. Easy fix, but may not be the best for everyone.

---

### Post by inobe on 2009-04-29
i honestly struggled for an entire week because of swfdec-mozilla that took only a minute to remove.

---

### Post by Foxtraffic on 2009-06-28
It isn't just Hulu that is giving me fits. I can't get any .swf stream to work. My problem I think stems from having a G4 PowerPC. The normal Flash plugin for Firefox will not work. I am told I have to use Gnash or Swfdec. Question is, how do I get these plugins installed for Firefox to use them. I have tried to install them and the site I am trying to play (Twit.tv) has stopped telling me I need the Flash plugin but when I click on the tab for the live stream, the screen just stays blank and I get no sound. If both of these programs are installed, do they conflict? Or, might I have a version of Flash installed somewhere and that be the problem? 

Also, youtube plays but is very jerky.

Thanks
Tony

---

### Post by carl_76 on 2009-07-26
Hi.

I'm running 9.04 on an AMD64 laptop.  Youtube was running but not hulu.  I just got the grey box when I tried to play a hulu video.  I uninstalled swfdec-mozilla using symantec and hulu started to work.  So, I'd like to add one more vote to the forum that this is a solution.

However the black pull-down menu for the channels on the hulu home page only works on the pages where I'm watching an active video.  If I'm not on a video page then I have to just click on the "channel" button and use the menus on the subsequent page.  This isn't much of an inconvenience.  I'm just posting it here as an observation.

Thanks to all on this forum for saving me a lot of trouble.

Carl

---

### Post by lelantus on 2009-08-07
This fixed all my problems. It's got two scripts in this how-to, one will un-install all versions of flash player that you have on your Ubuntu computer, while the other installs the Flash-Player 10 64-bit version that Jaunty needs to play all of your videos, including Hulu, Youtube, MySpace Video, and every other one I've found. I'm running Ubuntu 9.04 installed through Wubi, and I've still not had a single problem with this. Works like a charm!

[http://reformedmusings.wordpress.com/2009/07/03/installing-64-bit-adobe-flash-support-into-ubuntu-jaunty-9-04/](http://reformedmusings.wordpress.com/2009/07/03/installing-64-bit-adobe-flash-support-into-ubuntu-jaunty-9-04/)

---

### Post by HappyFeet on 2009-08-07
> **oscarmeyer51 said:**
> Turns out the default install does do the swfdec-mozilla. Once I removed that, Hulu worked like a champ. Easy fix, but may not be the best for everyone.

I've never seen swfdec-mozilla installed by default. (I install ubuntu for people on a regular basis) Simply by putting **libflashplayer.so** into ~/.mozilla/plugins makes flash work like a champ.

---

### Post by sportsdude81 on 2010-02-01
Try these to uninstall gnash and swfdec and install adobe flash

9.10 32 bit
```
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
```

9.10 64 bit
```
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs ia32-sun-java6-bin icedtea6-plugin libmp3lame0 non-free-codecs openjdk-6-jre unrar
```

---

### Post by bigbad486 on 2010-02-25
I ran the scripts and they fixed youtube and every other flash based page I've tried, but not hulu.  The error I get from hulu has changed from a blank screen that says express install of flash isn't availible for my OS, now saying that "we are unable to stream this video" suggesting I check my internet connection and try again.  I'm running 9.10 on an AMD 64 and I'm a big ubuntnoob.  Can anyone help me?

---

### Post by Chronon on 2010-02-25
I am having that problem now too.  I am running Firefox 3.5.8 in Kubuntu 9.10 on a x86_64 box.  Streaming works perfectly in Hulu Desktop, however, indicating it isn't specifically a flash problem.  I also have an x86 netbook running Ubuntu 9.10 with Firefox 3.5 and it streams just fine via the browser.  

I'm not sure of the root cause of this yet.  I suppose I should update firefox in my netbook and see if the problem appears there.

---

