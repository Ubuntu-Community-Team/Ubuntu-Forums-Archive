---
title: "Color hue off on Youtube videos and Totem"
date: 2011-03-03
forum: Multimedia Software
---

### Post by Joseph_Dantes on 2011-03-03
My color hue skews red for youtube videos (but not when played on on youtube/leanback). 

I get normal hue on megavideo, and on VLC player. 

On Totem, I get blue hue. 

I tried to adjust in the Totem edit->preferences->video tab, but I don't have a hue balance, only contrast and brightness. 

I tried editing hue in gconf for totem, but the hue keeps resetting after I changed it, even if I lock my changes by setting them as default or mandatory. 

I'm at a loss. 

I'm primarily interested in fixing the Youtube. I think Totem may have developed its hue problem while I was trying various fixes, but I don't need Totem. 

This problem started after I ran a scheduled update using Ubuntu's update manager. 

I am using Ubuntu Lucid Lynx 10.04 LTS.

I'm not sure where to access my video card info, if that's relevant.

---

### Post by Bazint on 2011-03-03
This happened to me today too (for youtube), on Ubuntu 10.10.

As far as I can tell, the problem is not an update from Ubuntu, but an update from youtube. Youtube seems to have just started streaming a buggy video to browsers using flash 10.2, but it only affects linux users.

So far, there are three possible solutions I can think of:


[LIST=1]
[*]Remove the cookie identifying your flash version.
[LIST=1]
[*]When viewing the reddish youtube video, in firefox, click Edit>Preferences
[*]Go to Privacy and click the "Show Cookies" button.
[*]Delete the cookie called "PREF" from youtube.com.
[*]Then refresh the video, and the red tinge should be gone.
[*]You may have to do this process for every video you want to watch, or else find an extension to block that particular cookie.
[/LIST]
 
[*]Block all cookies from youtube.com
[LIST=1]
[*]click Edit>Preferences
[*]Go to Privacy and click the "Exceptions" button.
[*]add youtube.com to the list of blocked cookies
[*]This solution is more permanent, but it means you cannot log in to youtube (to make comments, upvote, etc)
[/LIST]
 
[*]Or simply install a different version of Flash... maybe try an older one? 10.1 or 10.0?
[/LIST]
[I]
Edit: As for totem, try running the program "gstreamer-properties" from the terminal and choose a different video output module.



[/I]

---

### Post by thepanch on 2011-03-03
same thing happened to me, i just installed the latest update, still in 10.10 and youtube in chrome has turned all pinky/redy i might just try "turning it off and on again" that might do the trick

---

### Post by thepanch on 2011-03-03
well the restart didnt fix it :(. my dads computer hasnt had the upgrade but is still displaying normal coloured video (his is a 32-bit version, mine is a 64-bit dont know if that makes any difference) but also the embedded versions of videos dont have the pink effect any help??
i disabled the cookies for youtube.com and that removed the pinkness, but i not signed in or anything :( any other possible fixes?
thanks p

---

### Post by matt1950 on 2011-03-03
I did the update to 10.10 last night and all of my YouTube videos were red.
The upgrade installed version 10.2.152.27 of Flash player.
I was able to get the colors back to normal by downgrading my Flash version.
I went to Synaptic Package Manager and choose Package -> Force version.
Then when I selected "flashplugin-installer" from the package list, it
asked me what version I wanted to downgrade to, so I selected "10.0.45.2ubuntu1".
I applied this change and the YouTube videos look like normal now...

---

### Post by pterion on 2011-03-04
Same here at Ubuntu Lucid 10.04 and the new flash player 10.2.x.
Waiting for YouTube to fix this embarrassment.

See screenshot.

---

### Post by Paddy Landau on 2011-03-04
See this thread for workarounds:
[http://ubuntuforums.org/showthread.php?t=1698956](http://ubuntuforums.org/showthread.php?t=1698956)

---

### Post by thepanch on 2011-03-07
> **matt1950 said:**
> I did the update to 10.10 last night and all of my YouTube videos were red.
The upgrade installed version 10.2.152.27 of Flash player.
I was able to get the colors back to normal by downgrading my Flash version.
I went to Synaptic Package Manager and choose Package -> Force version.
Then when I selected "flashplugin-installer" from the package list, it
asked me what version I wanted to downgrade to, so I selected "10.0.45.2ubuntu1".
I applied this change and the YouTube videos look like normal now...
this method worked for me in google chrome thank you

---

### Post by KeesM on 2012-01-14
I had a recent shift towards blue for YouTube videos. This actually started when I fixed Flash support using the Flash Aid add-on and selected the default 'Adobe Beta' version. Selecting the 'Adobe Stable, from repositories (32 bit)' from the advanced Flash Aid settings solved the color shift. Guess the beta is still beta for a reason. Running Ubuntu 11.04 64 bit.

Edit: Oops, I now get complaints from my wife as Facebook video is no longer working; it needs this latest beta version... So either blue videos but facebook working, or normal video and no facebook?

Edit again: by switching off hardware acceleration, it now seems to work. However, it was some effort to find a site on which I actually could change the settings; on many sites, I can get to the Flash menu (right-click, select Settings), but the menu then freezes (can not click/change anything in the popup, not even close).

---

### Post by DrKaoliN on 2012-03-30
Here's how I solved it: 
shared a youtube video on my facebook, 
went full screen,
and disabled hardware acceleration.

---

### Post by paxh2o on 2012-03-31
> **matt1950 said:**
> I did the update to 10.10 last night and all of my YouTube videos were red.
The upgrade installed version 10.2.152.27 of Flash player.
I was able to get the colors back to normal by downgrading my Flash version.
I went to Synaptic Package Manager and choose Package -> Force version.
Then when I selected "flashplugin-installer" from the package list, it
asked me what version I wanted to downgrade to, so I selected "10.0.45.2ubuntu1".
I applied this change and the YouTube videos look like normal now...


thanks! it worked for me too!

---

### Post by vxd240 on 2012-04-06
Ubuntu 10.10
Downgrade Flash: did not work
Remove/Block cookies: did not work
Disable hardware acceleration: Win!

Using chrome, I got the same "frozen" menu (right-click on flash video-->settings).  However, I used Firefox to do the same thing and it worked (controls both FF & chrome flash playback).

---

### Post by SeijiSensei on 2012-04-06
> **vxd240 said:**
> Disable hardware acceleration: Win!

Wow, that's annoying, especially since the current version of Flash for Linux is the last to ever be released.  Way to go, Adobe, leaving us with a buggy version at the end of the line.

I hadn't noticed this problem until I watched a couple of videos on YouTube this morning.  Turning off HW acceleration and reloading the video eliminated the excessive blue tint entirely.

I have a machine whose CPU is fast enough not to need to use hardware acceleration, but that's not true for lots of other people on lower-powered platforms like early Atom processors.

Is this only true for NVIDIA/VDPAU+Flash, or do machines with ATI adapters also have this problem?  If it's only a problem with NVIDIA cards, maybe the issue is with their proprietary driver and not Adobe's fault.

Update:  It seems to be a problem between Flash 11.2 and VDPAU.  See these bug reports:

[https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/967091](https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/967091)
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/968647](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/968647)

It's probably the result of poor quality control on Adobe's part, and their response so far is, "sorry, but we're done supporting Linux."  Maybe NVIDIA can make some changes to libvdpau1 to compensate for Adobe's carelessness. We'll see.

---

### Post by jt_04 on 2012-04-06
> **DrKaoliN said:**
> Here's how I solved it: 
shared a youtube video on my facebook, 
went full screen,
and disabled hardware acceleration.

this did the trick for me, thanks very much (except I didn't share a video on facebook, just played one on youtube, went full screen, right click -> settings, and turned off hardware acceleration)

---

### Post by Paddy Landau on 2012-04-07
I am surprised to see this is an ongoing issue. I thought it had been fixed months ago.

I have tested on both 11.04 and 12.04 Beta, and both work correctly with hardware acceleration enabled. Are you using older versions perhaps? Or could the hardware in question be making a difference?

---

### Post by balta on 2012-04-10
The hardware acceleration disabling totally did the trick for me.
I was getting totally sick of blueish videos :D
Thanks a lot

---

### Post by BigSilly on 2012-04-11
> **DrKaoliN said:**
> Here's how I solved it: 
shared a youtube video on my facebook, 
went full screen,
and disabled hardware acceleration.

Yup, this did it for me across both of my Linux installs. Many thanks. :)

What a mess though. Massively disappointed.

---

### Post by lovinglinux on 2012-04-13
See [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by ricardisimo on 2012-04-14
Not me. Enabled or disabled, same result. Curiously, the previewer function in the YouTube player accurately renders the colors, as the screenshot shows. Sorry if the content offends, but I asked for skin, and I got it. Notice the previewer of the same image.

11.10 here, everything updated as far as I know.

---

### Post by Paddy Landau on 2012-04-15
> **ricardisimo said:**
> Enabled or disabled, same result.
You may have to log out and in again (or reboot) after disabling. Did you try that?

---

### Post by ricardisimo on 2012-04-15
No change. Still blues. Uggh. Why just YouTube? I don't get it.

---

### Post by SeijiSensei on 2012-04-15
> **ricardisimo said:**
> No change. Still blues. Uggh. Why just YouTube? I don't get it.

Read the bug reports that I linked to [above]("http://ubuntuforums.org/showpost.php?p=11822694&postcount=13").  It's a bad interaction between something called stage video in Flash and the NVIDIA driver.  YouTube uses "stage video" so the problem occurs there.

Just to confirm, you do have an NVIDIA card, and you are using the proprietary driver, correct?  As far as I know, disabling hardware acceleration should fix the problem.

Just to check, if you choose Tools > Add-Ons > Plug-ins, you'll see your Flash version.  What is it?

Those girls were cute in blue, though.

Update:  After re-reading the bug report thread, it looked like NVIDIA might have released a new driver version that includes a hack to deal with the problem.  On my fully-updated 12.04 system with the most recent release of nvidia-current, the problem persists.  I can still cure it by turning off hardware acceleration and closing and re-opening Firefox.

---

### Post by ricardisimo on 2012-04-15
Shockwave Flash 11.2 r202

OK... weird. [This]("http://www.youtube.com/watch?v=oP7JMnIOSP0&feature=related") YouTube video is messed up (along with most every other one I look at), but [this one]("http://www.youtube.com/watch?v=onlIemGdMD4&feature=context&context=G26a16aaRVAAAAAAAAAA") and most other NFL videos are just fine. So, now what's up?

---

### Post by SeijiSensei on 2012-04-16
The model in the first video is definitely flesh-colored here.

NVIDIA 9500GT with driver 295.40-0ubuntu1
libvdpau1 0.4.1-3ubuntu1
Flashplayer 11.2.202.228 with HW acceleration disabled

---

### Post by Paddy Landau on 2012-04-16
> **ricardisimo said:**
> OK... weird. [This]("http://www.youtube.com/watch?v=oP7JMnIOSP0&feature=related") YouTube video is messed up (along with most every other one I look at), but [this one]("http://www.youtube.com/watch?v=onlIemGdMD4&feature=context&context=G26a16aaRVAAAAAAAAAA") and most other NFL videos are just fine.
Right-click on each video. You'll notice that the first one is a Flash video, while the second is done through HTML5. (I don't know the technical differences, but I did notice the difference.)

---

### Post by ricardisimo on 2012-04-23
Not sure what to do about this. Still blue flesh here.   :-(

---

### Post by lovinglinux on 2012-04-23
> **ricardisimo said:**
> Not sure what to do about this. Still blue flesh here.   :-(


Please attach the firefox-report.txt file generated in your desktop after running the commands below:

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'pluginreg.dat' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat ~/.mozilla/firefox/**/pluginreg.dat >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by DiFS on 2012-04-25
I have the same problem of ricardisimo.

> **lovinglinux said:**
> Please attach the firefox-report.txt file generated in your desktop after running the commands below:


---

### Post by lovinglinux on 2012-04-25
> **DiFS said:**
> I have the same problem of ricardisimo.

Have you tried these?

[http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by ricardisimo on 2012-05-01
> **lovinglinux said:**
> Please attach the firefox-report.txt file generated in your desktop after running the commands below:

Please see attached. Thank you so much.

P.S. - "Your file of 26.0 KB bytes exceeds the forum's limit of 19.5 KB for this filetype." Therefore I have split it into two text files.

---

### Post by lovinglinux on 2012-05-01
> **ricardisimo said:**
> Please see attached. Thank you so much.

P.S. - "Your file of 26.0 KB bytes exceeds the forum's limit of 19.5 KB for this filetype." Therefore I have split it into two text files.


I couldn't determine which version of flash you are using. Apparently you have more than one Firefox profile and some haven't be used recently.

These are the versions listed  in their pluginreg.dat:

10.0 r45  /usr/lib/adobe-flashplugin/libflashplayer.so

10.0 r32 /usr/lib/flashplugin-installer/libflashplayer.so

10.1 r85 /usr/lib/flashplugin-installer/libflashplayer.so

Open [noparse]about:plugins[/noparse] and verify which version you really has.

---

### Post by Trucoto on 2012-05-01
This bug is being discussed [here]("https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/967091"). Please go where they say to upvote the Adobe bug so they can fix it.

---

### Post by ricardisimo on 2012-05-02
> **lovinglinux said:**
> Open [noparse]about:plugins[/noparse] and verify which version you really has.

Shockwave Flash

    File: libflashplayer.so
    Version: 
    Shockwave Flash 11.2 r202

MIME Type 	Description 	Suffixes
application/x-shockwave-flash 	Shockwave Flash 	swf
application/futuresplash 	FutureSplash Player 	spl

---

### Post by lastguru on 2012-05-02
I had this problem with latest flash and nvidia card. I actually just installed vdpau, which was not installed for some reason, and everything returned back to normal. Maybe it will help someone else...

---

### Post by ricardisimo on 2012-05-02
Was it vdpau-va-driver you installed? That's all that was in the repositories, and I tried it, but no dice.

---

### Post by lastguru on 2012-05-03
libvdpau1

An interesting observation is that I needed to reinstall this library after nvidia driver upgrade. Probably a bug.

---

### Post by ricardisimo on 2012-05-03
Already installed. Thanks anyway.

---

### Post by ricardisimo on 2012-05-15
Still no love from YouTube. Anyone have any other ideas? Thanks.

---

### Post by johnko99 on 2012-05-18
> **Joseph_Dantes said:**
> My color hue skews red for youtube videos (but not when played on on youtube/leanback). 

I get normal hue on megavideo, and on VLC player. 

On Totem, I get blue hue. 

I tried to adjust in the Totem edit->preferences->video tab, but I don't have a hue balance, only contrast and brightness. 

I tried editing hue in gconf for totem, but the hue keeps resetting after I changed it, even if I lock my changes by setting them as default or mandatory. 

I'm at a loss. 

I'm primarily interested in fixing the Youtube. I think Totem may have developed its hue problem while I was trying various fixes, but I don't need Totem. 

This problem started after I ran a scheduled update using Ubuntu's update manager. 

I am using Ubuntu Lucid Lynx 10.04 LTS.

I'm not sure where to access my video card info, if that's relevant.
I solved the same problem in Firefox/youtube using [http://www.youtube.com/html5](http://www.youtube.com/html5)! Just join the HTML5 use!

---

### Post by johnko99 on 2012-05-18
I solved the same problem in Firefox/youtube using [http://www.youtube.com/html5](http://www.youtube.com/html5)! Just join the HTML5 use!

---

### Post by lovinglinux on 2012-05-19
> **johnko99 said:**
> I solved the same problem in Firefox/youtube using [http://www.youtube.com/html5](http://www.youtube.com/html5)! Just join the HTML5 use!

Well, that doesn't work for all YT videos. Since they still cannot pipe ads on HTML5, I doubt they will fully replace flash.

---

### Post by ricardisimo on 2012-05-19
> **lovinglinux said:**
> Well, that doesn't work for all YT videos. Since they still cannot pipe ads on HTML5, I doubt they will fully replace flash.

Well, it is working so far for me. I saw that it doesn't support h.264, so most likely a decent number of these will revert to Flash... or no? Will I just not be able to see them? Is Flash eventually going to be fixed?

---

### Post by lovinglinux on 2012-05-19
> **ricardisimo said:**
> Well, it is working so far for me. I saw that it doesn't support h.264, so most likely a decent number of these will revert to Flash... or no? Will I just not be able to see them? Is Flash eventually going to be fixed?

Yes, it will fallback to flash if your browser doesn't support the html5 encoding.

Flash is not going to be fixed. Adobe has dropped support for Flash on Linux and will only provide security updates. However, they also made a deal with Google so they can deliver PepperFlash with Chrome. Bottom-line, only Chrome will have new major flash versions and bug fixes.

---

### Post by Paddy Landau on 2012-05-20
> **ricardisimo said:**
> I saw that it doesn't support h.264...
Me too. I am concerned about that, because eventually Flash will die and HTML5 will completely take over. Will we Linux users be stuck after that?

> **lovinglinux said:**
> ... However, they also made a deal with Google so they can deliver PepperFlash with Chrome. Bottom-line, only Chrome will have new major flash versions and bug fixes.
Interesting. That may persuade a few people to change to Chrome, but most users (I believe) use Internet Explorer and will remain doing so.

---

### Post by lovinglinux on 2012-05-20
> **Paddy Landau said:**
> Me too. I am concerned about that, because eventually Flash will die and HTML5 will completely take over. Will we Linux users be stuck after that?


Interesting. That may persuade a few people to change to Chrome, but most users (I believe) use Internet Explorer and will remain doing so.

Firefox, Opera and Chrome supports WebM. Chrome supports h.264 as well. So, Linux users will still have the ability play h.264 and flash, using Chrome.

Mozilla recently decided to support h.264 on mobile and possibly will support it on desktop. Only time will tell.

---

### Post by westniall on 2012-07-17
@DrKaoliN  WORKED!  Tnx

---

### Post by rizal23 on 2012-07-17
> **Bazint said:**
> This happened to me today too (for youtube), on Ubuntu 10.10.

As far as I can tell, the problem is not an update from Ubuntu, but an update from youtube. Youtube seems to have just started streaming a buggy video to browsers using flash 10.2, but it only affects linux users.

So far, there are three possible solutions I can think of:


[LIST=1]
[*]Remove the cookie identifying your flash version.
[LIST=1]
[*]When viewing the reddish youtube video, in firefox, click Edit>Preferences
[*]Go to Privacy and click the "Show Cookies" button.
[*]Delete the cookie called "PREF" from youtube.com.
[*]Then refresh the video, and the red tinge should be gone.
[*]You may have to do this process for every video you want to watch, or else find an extension to block that particular cookie.
[/LIST]
 
[*]Block all cookies from youtube.com
[LIST=1]
[*]click Edit>Preferences
[*]Go to Privacy and click the "Exceptions" button.
[*]add youtube.com to the list of blocked cookies
[*]This solution is more permanent, but it means you cannot log in to youtube (to make comments, upvote, etc)
[/LIST]
 
[*]Or simply install a different version of Flash... maybe try an older one? 10.1 or 10.0?
[/LIST]
[I]
Edit: As for totem, try running the program "gstreamer-properties" from the terminal and choose a different video output module.



[/I]
I agree with this solution, because I've proved it does work. 
Thank you.

---

