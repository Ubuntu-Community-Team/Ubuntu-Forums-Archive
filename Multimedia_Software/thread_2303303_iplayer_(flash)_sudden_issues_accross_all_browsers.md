---
title: "iplayer (flash?) sudden issues accross all browsers"
date: 2015-11-17
forum: Multimedia Software
---

### Post by steve234 on 2015-11-17
Hi there,

I have lubuntu running on my netbook and use it to watch iplayer - usually with Midori or FF browser.

I settled down (in an Openbox session) to watch a bit of iplayer this eve and was greeted with:

Midori - "failed to initialise" or plays jerkily without the usual settings cog where I can change the resolution - also has a strange right click menu I've never seen before. The menu takes me to some online options for flash (also never seen before).

FF - as above.

Chromium "you need to install flash player to view this content" - this used to work.

The same issues occur in an LXDE environment 

Did I break something today unwittingly? I've installed claws-mail + tint2 and uninstalled fbpanel. I also installed then removed cairo-dock.
Did something external change?

---

### Post by ajgreeny on 2015-11-17
What version of flash are you using?
By default FF still uses flash 11.2 but you can get the flash 19.0.0.245 if you install the adobe-flashplugin and freshplayerplugin packages, and whilst I am not sure if this is the case, maybe the BBC now demands the latest flash version for iplayer to work.  It certainly works in my newly installed Lubuntu on a netbook with FF and flash 19.0.0.245, though rather haltingly as the hardware is somewhat wanting in resources for decent flash play.

---

### Post by steve234 on 2015-11-17
Installed those and now it is really messed up - how do I revert to stock?

---

### Post by ajgreeny on 2015-11-17
Not sure why installing those two would mess things up unless you kept wharever else you were using for flash before, eg, flashplugin-installer, but just remove those two packages and you shold be back as before.

---

### Post by steve234 on 2015-11-18
Thanks - will remove them. Flash 19 in FF is too heavy for my system (as yours)

I solved the issue - it was my own stupidity - there is no resolution setting in iplayer, I was thinking of youtube.

---

### Post by ajgreeny on 2015-11-18
Well done.

Using freshplayer plugin and flash 19 should not be any heavier that flash 11.2, so I am glad that you have figured this out.

---

### Post by steve234 on 2015-11-19
Morning,

Last night a friend sent me an inline video in a Facebook message and it didn't play (in Midori) just a black box came up with no image. It also didn't play properly in Firefox (was mostly black but displayed one or two frames & looked all corrupted).

I figured this was another "linux" thing and downloaded the video (in mp4 container) via the link on the pop-up box. But the video had the same issues in VLC.

I've searched around, but can only find threads on Facebook video messaging - not iniline videos.

As this seems to be a system wide issue, it leads me to think I'm missing something? A codec perhaps?

---

### Post by ajgreeny on 2015-11-19
In firefox go to the video web-page, hit Ctrl+I ->Media tab to see what file-format the video is in.
That may give us more clue about what is missing.

You can also install the **lubuntu-restricted-extras** package as a start to see if that does the trick.

---

### Post by steve234 on 2015-11-19
It all seemed fine earlier after a shutdown > reboot - however it's  playing up again - perhaps it can't survive a hibernate or suspend  (which I've done a few times today).

I've just installed the restricted-extras package (which I thought I'd already done when I setup this machine).

Video type is .mp4 and the media tab has the following message.

Flash  Player upgrade required You must download and install the latest  version of Adobe Flash Player to view this content. Get Flash Player

---

### Post by ajgreeny on 2015-11-19
It may be one of the sites that demands the latest flash version, and if you are using the default in FF it will be flash 11.2, not 19.0.0.245.  There are not many sites which cause this difficulty, but occasionally it shows and means you may need to ensure you have installed the package adobe-flashplugin from the ubuntu partner repos and freshplayerplugin from the ppa at [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu)

No guarantee, but it is worth trying, I think.

PS:  What hardware do you have?
CPU?
RAM?
Graphic card?

---

### Post by steve234 on 2015-11-20
Morning all,

I had quite a few frustrating experiences over the last few days and on my commute this morning with browsing.

I've decided to amalgamate some previous threads as I think I have system wide flash issues and would like to get a stable setup for my browsers. This is an amalgamation of:
[http://ubuntuforums.org/showthread.php?t=2303303](http://ubuntuforums.org/showthread.php?t=2303303)
[http://ubuntuforums.org/showthread.php?t=2303480](http://ubuntuforums.org/showthread.php?t=2303480)
 
The problem is that browsers are inconsistent with how they display flash content and I'm spending lots of my time trying fixes but getting nowhere. I am increasingly having to use my partner's ancient Win7 laptop for browsing (using chrome), because browsing on my Lubuntu setup is frustrating as I have to constantly switch between browsers :( 

First point is that I like (and use as my main browser) Midori - it is the only "useable" browser I have. By useable, I mean that it loads quickly, and when I type - the text appears straight away. In both FF and Chomium if I type, or open a new tab, there is a sizeable lag.

System is a tiny netbook (hence Lubuntu) spec is:

Atom CPU (x64) but running 32bit OS (Lubuntu 14.04 - LTS)
1gb ram
Intel 3150 onboard graphics. 


The flash problems are:


[LIST]
[*]Midori - BBC iplayer works amazingly with good resolution and no lag/buffering - Facebook in-line videos (flash player with mp4 wrapper) do not display at all.
[/LIST]


[LIST]
[*]FF - BBC iplayer is laggy and generally unwatchable with poor framerate and resolution. - Facebook in-line videos display but are also unwatchable. FF reports as having both a Flash 12 and a Flash 13 plugin. The browser itself is laggy and slow generally.
[/LIST]


[LIST]
[*]Chromium - FB in-line videos work well (I have not tested iplayer) but the browser itself is soooooooo slow.
[/LIST]

I need to test youtube in the above browsers.

I have installed ubuntu-restricted-extras; and the plugins mentioned in the other threads. Perhaps I need to uninstall it all and start again. 

Any advice on how to do the following would be appreciated:

(1) uninstall all flash packages / plugins and start again;
(2) get Flash running (for Facebook) on Midori
(2) get FF or Chrome up to speed for general use; or


ta,

Steve

---

### Post by steve234 on 2015-11-20
Thanks aj -I'm having many different flash issues, so you may be on to something with flash 19. I will give that a go later. 

System spec is:
Atom CPU (x64) but running 32bit OS (Lubuntu 14.04 - LTS)
1gb ram
Intel 3150 onboard graphics. 

I have a few threads open so I am tidying them up into one thread ([http://ubuntuforums.org/showthread.php?t=2303610](http://ubuntuforums.org/showthread.php?t=2303610)) - I think flash needs to be sorted system-wide. The new thread is:

---

### Post by howefield on 2015-11-20
Threads merged.

---

### Post by steve234 on 2015-11-20
Ok so flash 19 has serious problems - I've probably complicated everythign by installing a few more browsers as a comparison (seamonkey, slimjet and bluemoon) and when running flash 19 on Youtube:
 
- the adverts play perfectly; but
- the substantive video plays only audio with a very poor framerate (or black screen) and has unresponsive controls.

So I need to get rid of flash 19 somehow I guess?

---

### Post by steve234 on 2015-11-20
To confirm the above I've done some extensive testing (see below). Sadly Midori, which is my fastest browser, has not done well.

The good news is that if I can persuade chromium to use flash 11, I can use it as my "big fat slow browser" for when I need to use Facebook or view video content. Opera is another contender, but doesn't display FB video well and is slow as f**k. 

I've done some searches on downgrading chromium's flash plugin but they all relate to newer flash versions. Would it be as simple as moving some plugins around?

Testing results:



Midori 0.5.11:
- iplayer (flash 11) "player failed to initialize" message for 5 seconds then starts working. Audio + video working perfectly
- youtube "an error occured" - HTML5 player;
- FB inline video (flash/mp4) - black screen - no audio.


FF 42.0
- iplayer (flash 19) = Audio fine - Video - terrible framerate/black screen;
- youtube (flash 19) = Audio fine - Video - terrible framerate/black screen;
- FB inline video (flash/mp4)  = Audio fine - Video - terrible framerate/black screen.


Chromium 45 
- iplayer (flash 19) = Audio fine - Video - terrible framerate/black screen;
- youtube = fine - uses HTML5;
- FB inline video (flash/mp4) - plays fine.


Opera 12.16
- iplayer (flash 11) =  plays very well
- youtube (flash 11) = - plays very well
- FB inline video (flash/mp4) - plays just about - low-ish framerate and controls disappear and audio and video not in sync
.


Slimjet Version 6.0.2.0 (based on Chromium 46)
- iplayer (flash 19) = Audio fine - Video - terrible framerate/black screen;
- youtube (flash 19) = Adverts play fine - substantive video -Audio fine - Video - terrible framerate/black screen
- FB inline video (flash/mp4)  = Audio fine - Video - terrible framerate/black screen.


Seamonkey 2.39
- youtube (flash 19) = Audio fine - Video - terrible framerate/black screen;
- youtube (flash 19) = Audio fine - Video - terrible framerate/black screen;
-  FB inline video (flash /mp4) - Audio lagging, black screen.


Palemoon 
- iplayer (flash 19) = Audio fine - Video - terrible framerate/black screen;
- youtube (flash 19) = Audio fine - Video - terrible framerate/black screen;
-  FB inline video (flash /mp4) - Audio lagging - terrible framerate.

---

### Post by steve234 on 2015-11-22
I've made a workaround at the moment by creating .desktop files for iplayer, youtube and facebook and putting them in my launcher.

Why would flash 19 play files so badly?

---

