---
title: "Can anyone play Mp3's"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by tansu on 2007-04-20
is it really hard?
I did add-remove programs and gstreamer things. I installed codecs.
is it too much demanding an operatin system to play music?

---

### Post by Paul41 on 2007-04-20
I can play them with not problem. Are you sure you got all of the needed codecs?

[https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29%7C%28formats%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29%7C%28formats%29)

---

### Post by disabled_20220313 on 2007-04-20
Ubuntu can play music using the open codecs that it ships with, like Ogg.  

MP3 is encumbered by patents which is why Ubuntu cannot ship with MP3 support, it would mean paying a fee to the Frauenhoffer (sp?) Institute, which would more than likely be passed on to you.

If you want to to get your MP3's to work, then I suggest you look into a something called Automatix or EasyUbuntu. Instructions at [http://ubuntuguide.org/](http://ubuntuguide.org/). 

I'm assuming your using Edgy, in the newest version of Ubuntu, Fiesty Fawn there is an application that is built into Ubuntu that will help you install all sorts of license/patent encumbered software and drivers. Though I havnt used it yet.

In the long run, if you plan on using a Linux based system I would reccomend you start converting your music to OGG and purchasing a player that plays them. You can convert mp3's to ogg, I think there is a command line program called mp32ogg, though you will loose some quality in the transcoding.

Good luck.

---

### Post by ubukool on 2007-04-20
Hi,

The best thing to do is to install automatix:

[http://www.getautomatix.com/](http://www.getautomatix.com/)

and check the option to install codecs.  It will install all the codecs you need for playing mp3 and various video formats as well as DVD.

---

### Post by tansu on 2007-04-20
> **Paul41 said:**
> I can play them with not problem. Are you sure you got all of the needed codecs?

[https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29%7C%28formats%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29%7C%28formats%29)
Yes I am sure. I did everything [here ]("http://ubuntuforums.org/showthread.php?t=413626")and still cant get it working. 
Amarok says , install mp3 support and crashes.

---

### Post by Paul41 on 2007-04-20
I would try the Automatix suggestion from ciaran.mooney and ubukool to see if that will get you going.

---

### Post by tansu on 2007-04-20
> **ciaran.mooney said:**
> Ubuntu can play music using the open codecs that it ships with, like Ogg.  

MP3 is encumbered by patents which is why Ubuntu cannot ship with MP3 support, it would mean paying a fee to the Frauenhoffer (sp?) Institute, which would more than likely be passed on to you.

If you want to to get your MP3's to work, then I suggest you look into a something called Automatix or EasyUbuntu. Instructions at [http://ubuntuguide.org/](http://ubuntuguide.org/). 

I'm assuming your using Edgy, in the newest version of Ubuntu, Fiesty Fawn there is an application that is built into Ubuntu that will help you install all sorts of license/patent encumbered software and drivers. Though I havnt used it yet.

In the long run, if you plan on using a Linux based system I would reccomend you start converting your music to OGG and purchasing a player that plays them. You can convert mp3's to ogg, I think there is a command line program called mp32ogg, though you will loose some quality in the transcoding.

Good luck.

Hi,
Nope I installed Feisty today.
I ve been using Ubuntu as the only operating system for one year, and I am proud..
I had almost no problem with Edgy.

> **ubukool said:**
> Hi,

The best thing to do is to install automatix:

[http://www.getautomatix.com/](http://www.getautomatix.com/)

and check the option to install codecs.  It will install all the codecs you need for playing mp3 and various video formats as well as DVD.

Well I guess I must try that automatix.

thanks

---

### Post by tansu on 2007-04-20
Portland, we have a probem here... And guys, believe me I have absolutely no problems with Edgy.
Cannot install automatix, even I dont get why I should do this.
Just want to play sodding mp3's, And I am tryin on it for (God!!) 5 hours.
In add-remove programs, all necassary stuff seems intsalled.
I go with apt-get and it says for all codec are newest.
Now that automatix cannot be installed and returns with that:

```
automatix2 depends on python2.4; however:
  Package python2.4 is not installed.
 automatix2 depends on python2.4-gtk2; however:
  Package python2.4-gtk2 is not installed.
 automatix2 depends on python2.4-glade2; however:
  Package python2.4-glade2 is not installed.
 automatix2 depends on python2.4-libxml2; however:
  Package python2.4-libxml2 is not installed.
 automatix2 depends on python-vte; however:
  Package python-vte is not installed.
 automatix2 depends on gksu; however:
  Package gksu is not installed.
 automatix2 depends on libgnomeui-0; however:
  Package libgnomeui-0 is not installed.
 automatix2 depends on python-gnome2-extras; however:
  Package python-gnome2-extras is not installed.
 automatix2 depends on python-gtkhtml2; however:
  Package python-gtkhtml2 is not installed.
dpkg: error processing automatix2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 automatix2
Press <enter> to exit...

```

---

### Post by Paul41 on 2007-04-20
I found 1 bug listed in launchpad, but I don't know if it will apply to you.

[https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/95284](https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/95284)

---

### Post by weth on 2007-04-20
> **tansu said:**
> is it really hard?
I did add-remove programs and gstreamer things. I installed codecs.
is it too much demanding an operatin system to play music?

why don't you install  VLC and after that follow the instructions Adamant1988 gives in his sticky posted at the top of the page and then you should have a working multimedia player that plays dvds, avis, mp3 ... I use it and am quite happy with it :)

---

### Post by tansu on 2007-04-20
> **Paul41 said:**
> I found 1 bug listed in launchpad, but I don't know if it will apply to you.

[https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/95284](https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/95284)

thanks, now I am installing python. If automatix dont work again, I will try that.

---

### Post by tansu on 2007-04-20
> **weth said:**
> why don't you install  VLC and after that follow the instructions Adamant1988 gives in his sticky posted at the top of the page and then you should have a working multimedia player that plays dvds, avis, mp3 ... I use it and am quite happy with it :)
Yess. me too.
But for mp3's my one is Amarok.

---

### Post by tansu on 2007-04-20
Yes...
Finally Automatix did the grade..
Thanks to everyone involved.

---

### Post by Chonnawonga on 2007-04-25
For future reference, anyone having trouble playing mp3s in Amarok (after installing codecs, etc.) should check out this thread:

[http://ubuntuforums.org/showthread.php?t=410511&highlight=amarok+no+mp3+support]("http://ubuntuforums.org/showthread.php?t=410511&highlight=amarok+no+mp3+support")

---

### Post by stchman on 2007-05-01
> **tansu said:**
> is it really hard?
I did add-remove programs and gstreamer things. I installed codecs.
is it too much demanding an operatin system to play music?

VLC has the ability to PLAY .mp3 files out of the box.  It has its own built in codec.  

sudo apt-get install vlc will install vlc if not already installed.

If you wish to rip CDs to .mp3 format than follow my procedure here:

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

Hope this helps.

---

### Post by sdowney717 on 2007-05-01
realplayer also plays mp3 out of the box.
I play mp3 with totem-xine.

Since I installed all the codecs, the totem-xine player works well. But it has a few problems with wmv (colors can go wacky)  video that mplayer plays perfectly.

I did not use automatix. Does that automatix cause upgrade problems when upgrading ubuntu releases?

---

### Post by stchman on 2007-05-01
> **sdowney717 said:**
> realplayer also plays mp3 out of the box.
I play mp3 with totem-xine.

Since I installed all the codecs, the totem-xine player works well. But it has a few problems with wmv (colors can go wacky)  video that mplayer plays perfectly.

I did not use automatix. Does that automatix cause upgrade problems when upgrading ubuntu releases?
 Use VLC it plays any media file I throw at it.  It does have issues with Apple Quicktime .mov files but I rarely come across them.

---

