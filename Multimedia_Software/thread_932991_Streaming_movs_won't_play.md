---
title: "Streaming movs won't play"
date: 2008-09-29
forum: Multimedia Software
---

### Post by 4lc0h0l1c on 2008-09-29
This is driving me absolutely nuts.  I've read every thread I can find on the subject.  I've tried every plug in I can find.  I've installed w32codecs and mplayer plugin.  With mplayer plugin, streaming videos go to play and then it says "stopped".  Please help!!  I have to watch videos for an online class and I am unable to complete my work!

---

### Post by Bakon Jarser on 2008-09-29
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by rstu202 on 2008-09-29
"Like?" "Love!" "Want?" "If you want to!" "Then we try!" "Inside a little longer?" "." "Does it hurt?" "A little tight , But also line! "" Comfortable? "" Comfortable "he said." Then we bought this pair of [Jordan shoes](http://www.nikeshoesoffer.com)! "

---

### Post by 4lc0h0l1c on 2008-09-29
Thank you for your reply.  That thread is very comprehensive.  However, it did nothing to solve my problem.  I am at my wit's end.  I need streaming video for a class.  The video works fine on XP.  I really don't want to have to switch back but this is just ridiculous.

Anyone know anything about how to test what plug ins I am using to see if there's a conflict, anything of that nature?

---

### Post by Denestria on 2008-09-29
The mplayer plugin wasn't working for me at first either.  What I had to do was when trying to view the video *right click* on the top-left of the browser window where it says mplayer plugin-embedded media player, choose *configure* and then under *video output* change it to *X11*.  There are a few other options in there as well so if that doesn't work try one of the other settings.  Hope that will help you.

---

### Post by Bakon Jarser on 2008-09-29
Okay, first off some sites just don't work.  I haven't run across any in a while but occasionaly you'll get one that doesn't work.  So the first question is are you only trying your class site or have you tried multiple sites and nothing plays?  Also sometimes mplayer will say loading video for a while and when it gets done it appears to just stop.  If this is what's happening to you, when it stops try hitting the play button.

---

### Post by 4lc0h0l1c on 2008-09-29
I have tried this on several different streaming movs on the web, not just my class site.  The streaming videos on my class site work fine on Windows.  Changing the video output in configuration does nothing.  (Three options there gl, x11, and xv I think)  When I try to use mplayer plugin it appears that it's going to play, says it's loading the playlist for a second, sometimes appears to actually load a URL, then says "stopped".  It does this anytime I hit play also.  VLC plugin actually played audio at one point, but no video.  Most of the time the VLC plugin just shows a blank black screen that says "no video" no matter how long I let it sit.  I ran Firefox from the prompt and the output does appear to show error messages.  I need to conduct a singular test of one attempted playback and post the output.

I am extremely frustrated and upset over this.  I have put about 20 hours into making this work and I just need to watch the videos for my class.  I have followed to the letter every tutorial and thread I found.  I burned a liveCD of Yoper and got the exact same results there.

---

### Post by Bakon Jarser on 2008-09-29
Have you tried Opera?

---

### Post by 4lc0h0l1c on 2008-09-30
Opera is actually my browser of choice.  Opera displays a box that says "plug-in content" and when I click on it, gives a prompt to download the (Windows) plugin from the quicktime download page.  Normally Opera can use Firefox plugins but the only one that shows up in the list is the Flash plugin.

---

### Post by Bakon Jarser on 2008-09-30
Run Opera -> Tools -> Preferences -> Advanced -> Content -> Plug-in Options -> Change Path and make sure you add the directory that contains the Firefox plugins and then click on Find New.

---

### Post by 4lc0h0l1c on 2008-10-02
Thanks for the suggestion.  I gave that a shot.  I did re-enable a plugin directory in Opera that I'd had disabled previously so it could detect the mplayer plugin directory, but it didn't make a difference.

I read about installing the ubuntu-restricted-extras package, so I did that but it didn't appear to affect anything.  For the record, yes, I have enabled the necessary repositories, etc.  And I've tried each different plugin installed separately and in combinations with each other, in each browser.  I also tried kubuntu-restricted-extras, since I run KDE on regular Ubuntu.

I'll give $10.00 or more to anyone who can get this working.  I am dangerously behind in my coursework because of this.  I am about to just wipe and switch back to Windows, where I never had any problems playing a god damn video file, embedded or not.

Any other distro that can do this without problems?  I've put upwards of 25 hours into this now, without having seen anything new since maybe the 3rd hour, and no improvements so far.

Anything else?  I'm pulling my hair out now.

---

### Post by Bakon Jarser on 2008-10-02
Oh man, I thought you were dual booting!  Install wine and then install the windows version of firefox and see if that gets things going temporarily.  If you've got some spare system resources and a windows disk you could install windows in virtualbox and run firefox that way.  Something also may be messed up in your Ubuntu install.  You could do a clean install in virtualbox and run the necessary changes from the first link I posted and see if that works (don't just skip to the streaming part, start at step 1).  This may be a problem with your video driver.  What kind of video card do you have.

---

### Post by Nexusx6 on 2008-10-02
A temp solution would be to run Virtualbox. VB is a free, open source emulator, and if you have a windows disk+key, you can use that to emulate a windows desktop to view your course work from. Its what I do so that I can take online courses that require me to have Internet Explorer and Windows only plugins and so far its worked very very good. 

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

Its an easy setup. The only annoyance is waiting for windows to install itself really. VB itself is also easy to use so hopefully this will be you one stop fix for now.

However, this is akin to taking Day Quil when you have a flu; you feel better, but you're still sick. It'll work and work good right now, but we still want to find out why you're unable to stream movies in Ubuntu. I'll go over the previous posts a little more throughly and search for alternative options to mplayer.

I'm a little confused, are you running Kubuntu or Ubuntu? Also, can you view any movies at all? Is it just the streaming that won't play? If you can view downloaded media, try right-clicking on the link and choosing to "Save As.." the link.

---

### Post by Bakon Jarser on 2008-10-02
This is a better guide for installing virtualbox.

[http://ubuntuforums.org/showthread.php?t=770745](http://ubuntuforums.org/showthread.php?t=770745)

---

### Post by 4lc0h0l1c on 2008-10-02
> 
I'm a little confused, are you running Kubuntu or Ubuntu? Also, can you view any movies at all? Is it just the streaming that won't play? If you can view downloaded media, try right-clicking on the link and choosing to "Save As.." the link.


Running Ubuntu with KDE installed; I uninstalled most of the Gnome packages a while ago.  I only have found problems playing streaming movs.  I can even play streaming wmvs as a result of installing packages to get movs working.  I can watch videos on Youtube, etc (although it is somewhat choppy on all browsers except Konqueror - go figure).  I can play movs in Mplayer, for instance, when there is just a link to download the mov.  But I can't watch embedded streams or open the stream file in Mplayer (it says "invalid stream" or some such).  This happens with any streaming movs I can find when googling for it.  The same videos DO play in Windows.

I have a working VBox installation that I can watch these in.  However that slows down my old computer a lot and makes it very hard to take notes and it takes forever to load the plugins & OS etc.

> 
Something also may be messed up in your Ubuntu install. You could do a clean install in virtualbox and run the necessary changes from the first link I posted and see if that works (don't just skip to the streaming part, start at step 1). This may be a problem with your video driver. What kind of video card do you have.


I did go through that link and I didn't find anything that seemed to remedy; I'll look again.  I did run a live disc of Yoper, which should be able to do this out of the box, and had the exact same issue playing streaming movs when running the live disc.  I have one other partition (aside from swap), an install of PCLinuxOS with barely enough space; I haven't tried it yet there.  It don't think the issue lies in my hardware, since even an emulated Windows can play movs, so perhaps it is a video driver problem.

From memory, Linux detects there is a Radeon IGP 330M / 340M / 350M, or something extremely similar.  This is in a Compaq Presario 2100, if I recall.

---

### Post by Bakon Jarser on 2008-10-02
There are firefox extensions that allow you to download streaming videos.  I suggest you try one.  

I wasn't suggesting that you go through the link again with your current install, I was suggesting that you install Hardy in virtualbox and then go through the steps in that link on the virtualbox install.  Did you try firefox (or opera) in wine?

---

### Post by 4lc0h0l1c on 2008-10-03
Hi folks,
I installed Quicktime and the JRE with Wine.  To get the JRE working, you have to run winecfg and under libraries tell it to override advpack.  (I think that's what it's called.)  Browsers under Wine now have access to the Windows quicktime plugin, and I can play streaming quicktime.

This is not an acceptable solution to me, because I still can't get streaming movs under native Linux.  AFAICT, the latest versions of mplayer and vlc plugins actually just don't work for streaming quicktime.  This is an acceptable temporary workaround because I can load up a browser and navigate to my class site in almost the time it takes natively.

For future reference to anyone with the same problem: I installed the windows JRE under Wine; it didn't seem to work at first.  I may have forgotten to restart the browser before trying to get it to access Java.  (I had to install the JRE because my class site uses applets) I read that if you download advpack.dll and override the library under Winecfg, then install Java, it will work.  This worked for me.  Unfortunately I had installed the JRE first, so after it failed to re-install twice, I renamed the Java directory under my Wine program files directory, then it worked to re-install (you probably want to choose 'advanced options' for the installer, then choose to install Java support for browsers and media - JRE @ time of writing 1.6_7).

I installed quicktime (standalone I believe), restarted browser, and it works.  Only problem: graphics mess up big time when first loading the embedded quicktime player.  Whole screen goes black, video starts playing in middle.  It's one of those things where all your stuff is still there it just wipes the graphics for some reason.  If you mouseover stuff and click in harmless places you will start to get your graphics back (like alt-tabbing back into starcraft ;-p) ).

Other things I can think of to get quicktime plugin working natively that I didn't try yet: finding an old version of the plugin or application (such as Mplayer) and using that; compiling the plugin or application natively; or some combination of the two.

If anyone has any further suggestions, I'd be glad to hear it.  At least for now I *think* I can watch my videos for homework.  Sorry about the long post; I may just post a bug report because I seriously tried every single thing I could find on the web that claimed to be able to get this working and none of them made a difference.

To recap:
Native Mplayer plugin gets playlist, buffers for a half second, then player says "stopped". If I try to open the stream file in Mplayer, it says the stream is invalid.  Installing the Firefox streaming video plugin mentioned above gave a similar error message when launching the player: "no stream found to handle url" and then a WHOLE bunch of gibberish looking url ending in what appeared to be the url from the streaming mov server, rtsp://xxx, or something like that.
The VLC plugin displays a black area that says "no video".  One time it started playing the audio but still said "no video".  I don't know how I got it to do that.
Right-clicking on the mplayer plugin and choose X11 or any other option for video doesn't help.
These plugins exhibited this behavior in every browser I tried, Firefox, Konqueror, and Opera.

Cheers.

---

### Post by Bakon Jarser on 2008-10-03
So you are specifically having trouble with .mov files?  I thought it was all streaming videos.  Open terminal and go to the mozilla plugins.

```
 cd /usr/lib/mozilla/plugins
ls
```

These are all the plugins that should be listed.
```
flashplugin-alternative.so  mplayerplug-in-qt.xpt  mplayerplug-in-wmp.so
mplayerplug-in-dvx.so       mplayerplug-in-rm.so   mplayerplug-in-wmp.xpt
mplayerplug-in-dvx.xpt      mplayerplug-in-rm.xpt  mplayerplug-in.xpt
mplayerplug-in-qt.so        mplayerplug-in.so

```
Your flash plugin may look different but if there are other media plug-ins they may be causing a conflict.  You should move them somewhere else (don't delete them in case they turn out to be important).

Now open firefox.  Go to edit > preferences.  Click the applications tab.  Scroll down and find Quicktime video.  Hmmmm......mine actually says use quicktime plug-in 6.0 / 7.  But when I play [this video]("http://www.pixar.com/theater/shorts/ftb/quicktime/ftb_sneak_320.mov") it definitely uses mplayer.  So if it says something else then I would change it to mplayerplug-in-qt.so

If that doesn't get things going then open vlc media player.  Click File > Open Network Stream.  Click Http/htt[s/ftp/mms and paste this link in the box and click OK.

[http://www.pixar.com/theater/shorts/ftb/quicktime/ftb_sneak_320.mov](http://www.pixar.com/theater/shorts/ftb/quicktime/ftb_sneak_320.mov)

If that works then go into firefox > edit > preferences > applications and change quicktime movies to vlc (Filesystem > usr > bin).  I haven't tried this but I'm pretty sure it will make the video open in vlc so you won't be viewing an embedded video but this should be a better solution then firefox in wine.

---

### Post by 4lc0h0l1c on 2008-10-06
Hi,
sorry if this thread already died.  I've been busy and haven't been able to check.

```

/usr/lib/mozilla/plugins$ ls
flashplugin-alternative.so  mplayerplug-in-qt.so   mplayerplug-in-rm.xpt  mplayerplug-in-wmp.xpt
mplayerplug-in-dvx.so       mplayerplug-in-qt.xpt  mplayerplug-in.so      mplayerplug-in.xpt
mplayerplug-in-dvx.xpt      mplayerplug-in-rm.so   mplayerplug-in-wmp.so

```

Mplayer can play the mov file you linked to but that is not my issue; I can play regular mov files.  I can't play *streaming* mov files, that is, off a quicktime streaming server.  I didn't even know these existed until I started messing around with this stuff.

It looks to me like I don't have any conflicts with plugins.

---

### Post by Bakon Jarser on 2008-10-08
So did you try using one of those links in VLC media player?  Please post a link to a video you can't play.

---

### Post by 4lc0h0l1c on 2008-10-10
Yes I did try them in VLC.  You have to log in to get the link on my school's website; the URL looks like it's randomly scrambled and when I right click mplayer and copy the URL, it looks like this (with a few bits edited out):

[http://my.school.edu/theOnlineLearningModule/someLetters/lc1494874472021.tp1590053684021//RelativeResourceManager?contentID=1670602333011](http://my.school.edu/theOnlineLearningModule/someLetters/lc1494874472021.tp1590053684021//RelativeResourceManager?contentID=1670602333011)

I don't really want to give the actual link to my school's site or my login information.

As I have been searching google for streaming movs to post a link to a video I can't play, I have found that a bunch of videos I couldn't play before now do play, and I have no idea why.  I haven't changed anything, except possibly I (re)installed VLC to give that a try again after the last time I posted here.  However, the videos on my school's site still don't play!

If I can find another streaming video I can't play I will post it.  Thank you.

EDIT: try [http://www.fridu.org/ims/47-linux-mp4-quicktime-streaming](http://www.fridu.org/ims/47-linux-mp4-quicktime-streaming) this page.
Near the bottom there are links to embedded streaming quicktime videos and two direct link URLs.  The links do not play, although they do not fail in the same way as the videos on my school's site.  The videos on my school's site get the playlist, buffer, then the "stop" button activates, which is a common problem on Linux from what I've read and most people seem to solve it by changing their video output to X11, which doesn't work for me.

The videos on the site above always freeze during buffering at some point.  A couple of times when I attempted to play I would see it flash "connection refused" before sitting indefinitely at the "getting playlist" screen.  The first direct link URL works.  The second one causes VLC to exit as soon as I attempt to load it and mplayer says "connection refused."

---

### Post by TBerk on 2008-10-10
Tag along post:

I just installed the Medibuntu "Essential Packages" [http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683"), and am trying out different sites and multimedia content to test it out.

- DVD movies are choppy, a problem I associate w/ it being a Pentium 4 & 512M RAM, (also currently using a basic IDE cable.) But it works.

- Apple Quicktime Trailers: If I choose a 'regular' preview I get a window that reports "get the latest Quicktime" and offers a CLOSE button.  However, if the trailer of choice has HD as an option I can get these resolution previews to work, BUT only if I open them in another TAB. (btw- I'm using Ubuntu 8.04 & Firefox 3.0.3).

So, perhaps you might have some diagnostic luck if you right click on a URL and open the streaming mov file in another TAB. (Something to try, and if anybody could throw me a bone without this being a thread hijack, I'd appreciate it.)


TBerk

---

### Post by Bakon Jarser on 2008-10-11
I don't know what to tell you.  Did you restart firefox after changing video to x11?  I'm out of ideas.  You should really get after your school for using such a crappy format.  They should be using something like xvid which is open source and something that everyone can play.  Write a letter, got talk to somebody, let them know you're not happy with this.  

Just looked at the mplayer plugin site.

> 2008-Jun-24	Version 3.55 Released

    * Make Apple Sites work
    * Fix GTK threading issue
    * Build fixes 

Looks like the new version might possibly give you a fix.  Looks like this requires the latest version of mplayer so I think you would have to upgrade that too.

---

### Post by ruien on 2008-10-16
Hi.

I had similar problems with apple but it's easy to fix. Mepis uses mplayer-plugin 3.55 and ubuntu 3.50. Go to Mepis repo's and get the mozilla mplayer plugins there and extract, copy them over the plugins you have in mozilla plugins folder and quicktime works fine.

---

