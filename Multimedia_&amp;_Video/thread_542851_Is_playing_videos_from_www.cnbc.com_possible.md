---
title: "Is playing videos from www.cnbc.com possible?"
date: 2007-09-04
forum: Multimedia &amp; Video
---

### Post by belboz on 2007-09-04
I setup my Uncle with a new Dell system with Feisty installed on it.  Everything is working very good for him.  

He is a news junkie and loves all the various news sites.

A favorite of his is cnbc, but he can't get the videos to play on that site.

I am curious if anyone has been able to figure out a workaround?

Here is a sample link.

[http://www.cnbc.com/id/15840232?video=499963023&play=1](http://www.cnbc.com/id/15840232?video=499963023&play=1)

---

### Post by linuxwizard on 2007-09-05
I was able to view that site. I am using MPlayer with Mozilla-MPlayer plugin

---

### Post by Nangineer on 2007-09-05
I'm using that plugin also, and I can't view it. I see the first frame, then that part of the screen goes black and doesn't produce any sound. I tried watching a CNBC video on a Mac recently--same result.

---

### Post by wolfen69 on 2007-09-05
in my experience streaming media is a hit or miss thing. for some people certain web sites work and for some they don't. i have tried everything under the sun to get certain web sites to work, but they won't. i've given up, and just don't view them.

---

### Post by wolfen69 on 2007-09-05
the following may increase your chances with streaming content:
search in synaptic for- mozilla helix  and  mozilla vlc. they are plugins that may help.

---

### Post by Gremlinzzz on 2007-09-05
I can watch it with mplayer plugin i also installed smplayer seems to give the codecs a little kick.
[http://smplayer.sourceforge.net/en/linux/index.php](http://smplayer.sourceforge.net/en/linux/index.php)
speaking of codecs
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)

---

### Post by afilonov on 2007-11-26
Can anybody see those on Feisty or Gutsy? I'm able to play cnbc.com videos with Mplayer plugin on Dapper, no problem. On Feisty with the same plygin I can only see ad running, no main video. And even ad only plays after firefox just started. Later on, nothing. Opera can't play anything at all.

---

### Post by odius on 2008-01-02
I was having a similar problem. I uninstalled Totem, Totem-mozilla and the totem-gstreamer packages from Synaptic. w32 codecs already installed etc. and also the mplayer, mplayer-mozilla package. As soon as i removed the totem packages...cnbc played!
gLuck

---

### Post by bhold on 2008-01-15
Same problem here - I can't play cnbc web videos either. I have tried watching some of the Fast Money videos at cnbc.com. No luck. I have tried totem and mplayer plugins on Debian Etch, PCLinuxOS 2007, and Ubuntu 7.10. I have also thrown Firefox, Ephphany, and Iceweasle browsers into the mix. Have not found any combination that works. (Works fine on my XP system using IE.) 

I think this possibly has more to do with the content provider (cnbc) and is not necessarily a Linux issue but I don't have enough expertise to comment further. Hope someone who knows more about this might be able to help clarify.

---

### Post by bhold on 2008-01-18
Installed Linux Mint 4.0 today and tested cnbc web videos, they played OK with mplayer plugin from Firefox. Sometimes I needed to hit the "Play" button several times to get the video started, and the sound quality was not the greatest - but they did play. I have not been able to play these at all on Ubuntu 7.10.

I have not taken the time yet to sift through comparisons between my Ubuntu 7.10 partition vs. the Linux Mint partition - kernel version, installed plugins, plugin versions, Firefox version... etc... to see if I can determine what is causing the different behavior - will post here if I spend more time on this and learn anything useful.

---

### Post by ubuntu-freak on 2008-01-18
My how-to will help
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Do all of it for best results. Make sure you remove all the packages it says.
 
Nathan

---

### Post by bhold on 2008-01-23
I've got cnbc video playing now, behaving the same in Firefox / ubuntu 7.10 as Linux Mint 4 using the mplayer plugin.

I did the steps above recommended by reassuringlyoffensive. Still no luck getting the videos to play. Next I tried disabling the Ad Block Plus plugin, exit Firefox, re-run Firefox. I must exit Firefox after disabling the plugin and then re-run Firefox or the cnbc videos will not play at all.

Now the cnbc videos will play, although I do usually need to click on the play button several times. The audio quality is better now on Ubuntu than on Linux Mint, maybe because of reassuringlyoffensive's configuration tips. Anyway, thanks for the suggestions as some combination - I am not sure exactly which - is working. Unfortunately this does seem somewhat hit and miss, as someone mentioned earlier in this thread.

---

