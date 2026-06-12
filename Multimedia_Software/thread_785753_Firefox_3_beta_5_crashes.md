---
title: "Firefox 3 beta 5 crashes"
date: 2008-05-07
forum: Multimedia Software
---

### Post by geovino on 2008-05-07
I've noticed that many youtube videos will crash Firefox. What would cause that. Is it this beta 5 version?

---

### Post by aysiu on 2008-05-07
You could try Firefox 2 to see if it makes a difference:
[http://www.psychocats.net/ubuntu/firefox2hardy](http://www.psychocats.net/ubuntu/firefox2hardy)

---

### Post by indiana_crook on 2008-05-07
> **geovino said:**
> I've noticed that many youtube videos will crash Firefox. What would cause that. Is it this beta 5 version?

You could try Firefox 2, I understand you can actually have both 2 and 3 installed.  When I have problems with Firefox, there is usually an update that comes out in the near future that corrects the issue.

---

### Post by geovino on 2008-05-10
I installed Firefox 2. A youtube video made it crash too. :confused:

---

### Post by Zorael on 2008-05-10
Though I didn't get crashes (and rather just gray boxes where the embedded flash was supposed to be), I've had better luck with Gnash; I installed both the [FONT="Courier New"]flashplugin-nonfree[/FONT] and [FONT="Courier New"]gnash[/FONT] packages, and then changed the [xdg alternative](http://en.wikipedia.org/wiki/Xdg) to point at the gnash plugin.

```
$ sudo aptitude install gnash mozilla-plugin-gnash
$ sudo update-alternatives --config mozilla-flashplugin
```

Some flashes (mostly youtube) still don't show up unless I refresh the page once or twice, but it's better than the flash dying on me completely.

---

### Post by geovino on 2008-05-11
> **Zorael said:**
> Though I didn't get crashes (and rather just gray boxes where the embedded flash was supposed to be), I've had better luck with Gnash; I installed both the [FONT="Courier New"]flashplugin-nonfree[/FONT] and [FONT="Courier New"]gnash[/FONT] packages, and then changed the [xdg alternative](http://en.wikipedia.org/wiki/Xdg) to point at the gnash plugin.

```
$ sudo aptitude install gnash mozilla-plugin-gnash
$ sudo update-alternatives --config mozilla-flashplugin
```

Some flashes (mostly youtube) still don't show up unless I refresh the page once or twice, but it's better than the flash dying on me completely.

I tried to run the command and its says command not found. Also tried as apt-get install and that didn't work either. 

Now Firefox is crashing on other sites too. Somethings wrong.

---

### Post by Zorael on 2008-05-11
> **geovino said:**
> I tried to run the command and its says command not found. Also tried as apt-get install and that didn't work either.
Command not found? For update-alternatives, or aptitude? I'm confused.

Anyway, I tried [pulling libflashsupport from git as described here](http://www.pulseaudio.org/wiki/FlashPlayer9Solution), and now I'm not sure if gnash or flash is the way to go anymore. I still need to refresh pages to get youtubes to show up every now and then, but it seems more stable now.

---

### Post by geovino on 2008-05-12
I don't know why I couldn't run the command, but I used Synaptic and installed gnash. It's ok today so far. I'll see how it goes.

---

### Post by geovino on 2008-05-12
Firefox 3 beta 5 has crashed three times this morning on sites that were all different. I didn't try any videos, that I thought were the problem. I don't know if this is a Firefox problem or a Hardy Heron problem, but this has been the most unstable browser I've used in the past two years of using Ubuntu. 

Does anyone else have this problem?

I also installed FF 2 and it crashed once also.

I'll use Opera 9.5 beta2 and see if its more stable.

---

### Post by gandaran on 2008-05-12
geovino
       the crashes you are experiencing are not a firefox or flash problem.
firefox 3 and adobe flash work fine for most people, only a few have problems like you, I suspect the problem is hardy 8.04/drivers/video-card, just to give you an idea, in ubuntu gutsy 7.10 playing a youtube video took up to 5% of my cpu resources, now in hardy 8.04 it goes up to 70% of my cpu power, but still works fine, a crash would only happen with the cpu at 100%.
try the opera browser [http://www.opera.com/download/?ver=9.50b2](http://www.opera.com/download/?ver=9.50b2) opera is  more lighter than firefox, and don't make the mistake installing gnash or swfdec, use only the flashplugin-nonfree (adobe flash).

---

### Post by Keldek on 2008-05-12
I too have experienced the firefox 3 beta 5 crash... except mine didn't just crash firefox, it crashed my whole system. Everytime I try to view 1 specific site, [http://ubuntuguide.org](http://ubuntuguide.org) , in FF3 B5 my screen goes black, followed by a system reboot approx 1-2 minutes later.

I ended up dropping FF3 altogether and am now running FF2. I can't install some extensions, like DownThemALL; but meh, it's a fair trade from having FF3 crash my whole system.

I hope they find out what's causing the crashes soon and get it fixed as FF2 is quickly becoming obsolete.

I saw a lot of talk about opera, so figured I'd try it out, and as soon as I go to [http://mail.google.com](http://mail.google.com) it crashes with these error messages in my syslog:

[14762.892476] operapluginwrap[15480]: segfault at 0 rip 40e8c3 rsp 7fffd09dede0 error 4

[14809.786246] opera[15390]: segfault at ffffffff rip 7f2cc8131b51 rsp 7fffd2988970 error 4

---

### Post by ubuntu-freak on 2008-05-12
Here's two possible solutions from my how-to:

**sudo apt-get purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install flashplugin-nonfree libflashsupport**

Also, within Firefox, navigate to Edit > Preferences > Security and untick everything except the password option. Next, close Firefox and navigate to Places > Home > View > and select "Show Hidden Files". Inside your home directory, navigate to /.mozilla/firefox and look for a folder with ".default" in it's name, open it and delete any files starting with "urlclassifier".

Most of my problems were cured after doing the above.

Nathan

---

### Post by Keldek on 2008-05-12
> **reassuringlyoffensive said:**
> Here's two possible solutions from my how-to:

**sudo apt-get purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install flashplugin-nonfree libflashsupport**

Also, within Firefox, navigate to Edit > Preferences > Security and untick everything except the password option. Next, close Firefox and navigate to Places > Home > View > and select "Show Hidden Files". Inside your home directory, navigate to /.mozilla/firefox and look for a folder with ".default" in it's name, open it and delete any files starting with "urlclassifier".

Most of my problems were cured after doing the above.

Nathan

Doesn't solve my problem with my system crashing when trying to view ubuntuguide.org :(

Well, I guess at least this time it just kicked me back to the login screen instead of crashing altogether.

---

### Post by ubuntu-freak on 2008-05-12
> **Keldek said:**
> Doesn't solve my problem with my system crashing when trying to view ubuntuguide.org :(

Well, I guess at least this time it just kicked me back to the login screen instead of crashing altogether.

That kind of crash can be hard to pinpoint. It's related to Xorg, but I don't experience that crash at all, so it's something interacting with Xorg. Do you have an Intel graphics chipset? Have you tested how your system behaves with the Epiphany browser? Give it a try:

**sudo apt-get install epiphany-browser**

Also, you might want to try creating a new user account and see if crashes occur in that account as well.

Nathan

---

### Post by Keldek on 2008-05-12
No intel graphics here. I'm running an evga geforce 8800GTS on an msi k9a2 platinum mobo.

I'm sure this doesn't matter, but I've had this problem in the standard "out of the box" ubuntu desktop, ubuntu studio with gnome uninstalled (at least that's what synaptic told me), as well as kubuntu desktop.

I haven't, however, tried the epiphany browser, or creating a new user. Once these file backups complete and I can unmount the drives I'll try that.

---

### Post by geovino on 2008-05-12
Thanks for the insight. I uninstalled gnash completely and will try again. 

Why would Hardy have this problem with video cards? I've have better luck with sidux linux and Mint. I may consider installing Mint when its new version comes out. Mint sometimes does a better job with Ubuntu than Ubuntu does. I wonder why? Do they fix more bugs before the new release?

---

### Post by ubuntu-freak on 2008-05-12
> **geovino said:**
> Thanks for the insight. I uninstalled gnash completely and will try again. 

Why would Hardy have this problem with video cards? I've have better luck with sidux linux and Mint. I may consider installing Mint when its new version comes out. Mint sometimes does a better job with Ubuntu than Ubuntu does. I wonder why? Do they fix more bugs before the new release?

 
Mint isn't as cutting-edge I don't think. Their new version will retain some of Gutsy, but be modified and tweaked and compatible with the Hardy repos.
 
Nathan

---

### Post by geovino on 2008-05-12
I've been running Opera 9.5 beta2 today and it seems OK, but the videos don't play. what does Opera need to play videos? or audio?

Are there Opera plugins in Synaptic?

---

### Post by ubuntu-freak on 2008-05-12
> **geovino said:**
> I've been running Opera 9.5 beta2 today and it seems OK, but the videos don't play. what does Opera need to play videos? or audio?

Are there Opera plugins in Synaptic?

 
It should scan the Firefox plugins folder and use them. Which plugins are you using? Did you try Epiphany?
 
Nathan

---

### Post by gandaran on 2008-05-13
> **geovino said:**
> I've been running Opera 9.5 beta2 today and it seems OK, but the videos don't play. what does Opera need to play videos? or audio?

Are there Opera plugins in Synaptic?

I think opera doesn't work with the totem plugins, I have mine just half working with the mplayer plugin, it works but just with a very small video window, the only plugin fully working in opera is the xine-plugin, as for vlc-plugin I don't know, never tried it. if you want to try other plugins un-install the totem-plugin first.

---

### Post by ubuntu-freak on 2008-05-13
I recommend Gecko Media Player, it's the MPlayerplug-in devs new project:
 
**sudo apt-get remove kaffeine-mozilla mozilla-mplayer mozilla-plugin-vlc totem-mozilla && sudo apt-get install gecko-mediaplayer gnome-mplayer**
 
Then restart Firefox/Opera. I think you can make Opera scan for the new plugins, or it may update itself after a restart like Firefox seems to do now.
 
See my [how-to](http://ubuntuforums.org/showthread.php?t=766683) for more info and help. 
 
Nathan

---

### Post by IcedDante on 2008-05-13
> **Keldek said:**
> I too have experienced the firefox 3 beta 5 crash... 

I hope they find out what's causing the crashes soon and get it fixed as FF2 is quickly becoming obsolete.


Firefox is becoming obsolete? Where did you hear that from?

I had a problem with FF2 crashing all over the place a few weeks ago. The last release that was done had a Javascript garbage collection error that caused Firefox to crash continuously. It has since been fixed so make sure you have the most recent version of FF2.

---

### Post by geovino on 2008-05-13
> **reassuringlyoffensive said:**
> I recommend Gecko Media Player, it's the MPlayerplug-in devs new project:
 
**sudo apt-get remove kaffeine-mozilla mozilla-mplayer mozilla-plugin-vlc totem-mozilla && sudo apt-get install gecko-mediaplayer gnome-mplayer**
 
Then restart Firefox/Opera. I think you can make Opera scan for the new plugins, or it may update itself after a restart like Firefox seems to do now.
 
See my [how-to](http://ubuntuforums.org/showthread.php?t=766683) for more info and help. 
 
Nathan

Is all this supposed to help Firefox or Opera? Once the basic plugins and flash are installed you shouldn't have to do anything. If this is a video card problem, then that is what should be addressed. But when I installed Hardy on April 25th, Firefox 3 beta 5 worked fine for two weeks before it started crashing. 

Maybe this is a bug in Hardy! I thought this version with its LTS was supposed to be solid and stable. As buggy as some things were in Gutsy, I never had this crashing problem. When is Ubuntu going to fix this bug/problem? Maybe it's time to use Mint instead. From what I've seen Mint seems more stable, maybe they fix more bugs before releasing the next version!

---

### Post by ubuntu-freak on 2008-05-13
> **geovino said:**
> Is all this supposed to help Firefox or Opera? Once the basic plugins and flash are installed you shouldn't have to do anything. If this is a video card problem, then that is what should be addressed. But when I installed Hardy on April 25th, Firefox 3 beta 5 worked fine for two weeks before it started crashing. 

Maybe this is a bug in Hardy! I thought this version with its LTS was supposed to be solid and stable. As buggy as some things were in Gutsy, I never had this crashing problem. When is Ubuntu going to fix this bug/problem? Maybe it's time to use Mint instead. From what I've seen Mint seems more stable, maybe they fix more bugs before releasing the next version!
 
LTS only means Long Term Support, not Lovely as Toffee Stability.
 
Did these crashes start after you installed libflashsupport? I had more crashes before I installed that package, but some users experience more problems with it installed. First of all though, physically check Synaptic and make sure you don't have any Gnash or swf package installed.
 
Nathan
 
P.S. Some users have solved their issues with Flash by reverting back to ALSA in System > Preferences > Sound. You will need to tell non-GNOME apps that you're using the ALSA sound server.

---

### Post by geovino on 2008-05-14
"Did these crashes start after you installed libflashsupport? I had more crashes before I installed that package, but some users experience more problems with it installed. First of all though, physically check Synaptic and make sure you don't have any Gnash or swf package installed."

All gnash plugins are uninstalled. I'm not sure about when I installed libflashsupport though. For most browsing in Firefox works fine, it's just when you use certain videos. Very strange. 

I hope Ubuntu comes up with a fix for this problem.

---

### Post by hollowhead on 2008-05-14
I've had a look at this thread my only comment is that firefox and flash crash more than any other part of our gutsy systems.  Usually when my children are watching u-tube or playing on club penguin although I've noticed if you shut the system down with firefox open it reports it as a crash.

---

### Post by timzak on 2008-05-14
I've only had crashes when watching YouTube videos, nowhere else so far.  What happens is randomly, when I click on a video to watch, Firefox will just shut down as if I shut it down myself.  Sometimes I can watch many videos without this happening, other times, it happens nearly every time I click a video.  I hope this is fixed soon!

If your problems are only on YouTube, a temporary workaround is to watch YouTube videos through Totem, which has a new YouTube plugin in Hardy.

---

### Post by ubuntu-freak on 2008-05-14
> **hollowhead said:**
> I've had a look at this thread my only comment is that firefox and flash crash more than any other part of our gutsy systems.  Usually when my children are watching u-tube or playing on club penguin although I've noticed if you shut the system down with firefox open it reports it as a crash.

 
In Gutsy, I had better results when I purged Flash and installed it manually. Have a look at Part 1 of my how-to in my signature.
 
Nathan

---

### Post by geovino on 2008-05-14
> **reassuringlyoffensive said:**
> In Gutsy, I had better results when I purged Flash and installed it manually. Have a look at Part 1 of my how-to in my signature.
 
Nathan

I'll read your links, but this just tells me that Hardy was not ready to be released. These kinds of problems should not happen at all. They don't happen in PCLOS, sidux, Mint. Does that mean they are more stable than Ubuntu?

---

### Post by ubuntu-freak on 2008-05-14
> **geovino said:**
> I'll read your links, but this just tells me that Hardy was not ready to be released. These kinds of problems should not happen at all. They don't happen in PCLOS, sidux, Mint. Does that mean they are more stable than Ubuntu?

 
Adobe Flash needs to be better for Linux, it's not even accelerated like the Windows one. If other distros are using FF3, they will have issues too. Use FF2 or Epiphany. 
 
Ubuntu advertises itself as cutting-edge, so there are going to be some bugs with a brand new release. I don't understand why you threaten to use another distro. use whatever want, it doesn't matter. The Ubuntu devs aren't responsible for Adobe and Mozilla bugs, nor Xorg and proprietary graphics driver bugs.
 
Nathan

---

### Post by Keldek on 2008-05-14
> **reassuringlyoffensive said:**
> That kind of crash can be hard to pinpoint. It's related to Xorg, but I don't experience that crash at all, so it's something interacting with Xorg. Do you have an Intel graphics chipset? Have you tested how your system behaves with the Epiphany browser? Give it a try:

**sudo apt-get install epiphany-browser**

Also, you might want to try creating a new user account and see if crashes occur in that account as well.

Nathan

I've since been able to almost pinpoint the exact issue...

Upon installing Ubuntu, I was using kernel 2.6.24-16-generic.
(No crashes at all with this kernel for me)

After installing ubuntustudio (specifically ubuntustudio-audio), my kernel was upgraded to 2.6.24-16-rt
Lo and behold, as soon as I try to view ubuntuguide.org I get booted back to the login screen. At least it didn't cause an entire system reboot this time heh.

To add further, I notice that it crashes exactly when (every time) it starts "transferring data from googlesyndication.com" something or another; so I'm lead to believe this issue is to do with the new kernel and googlesyndication.com.

I have these 2 components installed for flash: flashplugin-nonfree libflashsupport

I haven't been able to gather any more info from this problem, but I do know that it is kernel 2.6.24-16-rt specific, as I've had 0 problems with FF3B5 using kernel 2.6.24-16-generic... and going back to the generic kernel would mean losing ubuntustudio-audio and require reconfiguring all of my kernel compiled software to recompile for the new (old) kernel... not something I'm looking forward to having to do :P

I am also going to look into the Opera issue I was having (would crash as soon as I opened it, never successfully opened), as it seems this too may be a 2.6.24-16-rt problem, though not yet verified.

I will post back more info as I gather it, but hopefully I've provided enough info for this issue to be looked into.

---

### Post by geovino on 2008-05-15
> **reassuringlyoffensive said:**
> Adobe Flash needs to be better for Linux, it's not even accelerated like the Windows one. If other distros are using FF3, they will have issues too. Use FF2 or Epiphany. 
 
Ubuntu advertises itself as cutting-edge, so there are going to be some bugs with a brand new release. I don't understand why you threaten to use another distro. use whatever want, it doesn't matter. The Ubuntu devs aren't responsible for Adobe and Mozilla bugs, nor Xorg and proprietary graphics driver bugs.
 
Nathan

You are right, I shouldn't be accusing Ubuntu for a problem that is caused by someone else's software program. I have noticed that Opera 9.5 beta2 handles the youtube videos without problems. Overall Ubuntu 8.04 has been very good. I just wonder why these things affect one distro and not another.

---

### Post by mano cazalet on 2008-05-15
hmmmm

maybe [this is]("http://blog.wired.com/monkeybites/2008/05/flash-player-10.html") a good news

:confused:

---

### Post by BrentNewland on 2008-05-25
I've been having crashes when viewing flash videos for about a month under beta 5. I performed the commands on the second and third page (although I didn't install the flash plugin on the second page), and used a guide online to install Flash 10, and so far it seems to be working.

---

### Post by markbuntu on 2008-05-26
I just got Opera9.27 working with an older version of flash and I know the Opera 9.5 works with the new flash.

No more firefox for me, probably ever.

I got so frustrated with firefox crashing and it has nothing to do with playing videos, it would just crash crash crash. Even when it was the only ap open and the only place I went was here in these forums. Even when I had all desktop effects disabled. It wouldn't even crash gracefully but had to freeze up the entire system.

It just got really hard to get anything done.

---

### Post by voodooguru on 2008-05-26
I've had exactly the same problems as you describe. I had them with Gutsy and FF2 and have them again with Hardy and FF3. It's enough to drive me crazy. Geovino's comments about CPU resources being chewed up are interesting but Linux is supposed to be less demanding of hardware, so I'm a bit doubtful about his suggested reason. My impression is that a lot of people are having FF problems, especially with Flash content.

---

### Post by vs8 on 2008-05-26
I've been following this thread and it's interesting because I have problems with FF 3 B5 using Flash too. It's basically the same as you guys. Opera was supposed to suck at Flash but Opera 9.5 b2 works very good (9.27 version supposedly suck's at flash). My brother uses the internet just to watch vids on youtube and Opera has never failed him on Hardy Heron, when we were using PClos it crashed or had the gray screen where the video was supposed to be. The problem was solved with Hardy and Opera.

I've never been into FF, I don't know why people love it that much, since I discovered Opera I fell in love with it,because it's speed and stability. Talking about stability, I was using FF3 B5 to type this and my system crashed, I couldn't even restart X with the keyboard shortcut. I don't know if it was FF or Hardy, but at least I restored the FF session and it saved everything I wrote. So I'll finish writing this and I don't think I'll use FF in a very long while. 

I'll report if Opera works well with youtube on my user profile.

---

### Post by geovino on 2008-05-26
Lately I have had less crashes with youtube, but if it does crash, I can restart the session and it goes back to what I was logged into. I have also installed Opera 9.5 beta 2 and it has not crashed at all with videos. 

I also have been running sidux Linux on my other computer and it has not had any trouble with video crashing at all. Since its a more pure Debian distro they use Iceweasel instead of Firefox and its all the same. I have also installed Opera 9.5 beta 2 in sidux and it works with no trouble. 

So it is hard to pinpoint where the source of the trouble is coming from :confused:

---

### Post by Zorael on 2008-05-26
Opera is a decent browser, I guess, but the showstopper is the lack of extensions. I mean, "widgets" don't do it for me. I don't want an analog clock.

I'm not sure there's a fix yet, unless Flash 10 works awsome? I've heard mixed reports on that. For the time being though, FF3 + (nspluginwrapper) + Flash 9 do not mix well.

---

