---
title: "youtube videos changed color suddenly?"
date: 2012-03-29
forum: Multimedia Software
---

### Post by jorritTyb on 2012-03-29
A recent update (don't exactly know when) seems to have changed the color of ALL youtube videos. All people are now blue (and no, I'm not watching a smurf movie :-) ) and blue colors have turned brown. This is for literally all youtube videos and I tried a lot. This has been working perfectly for months. It it just today that I notice this (but I hadn't been watching youtube videos for a few days so it may have broken earlier).

Videos played using movie player or VLC are correct with colors.

Any ideas? I'm using Chromium btw.

Greetings,

---

### Post by Nuskrad on 2012-03-29
I can confirm this, happened after flashplugin-installer was updated from 11.1.102.63ubuntu0.11.04.1 to 11.2.202.228ubuntu0.11.04.1. Only affecting youtube, other flash video seems to be unaffected

---

### Post by Resplendent Raven on 2012-03-29
Same here also after the recent update. Had a similar problem before with normal videos, but i managed to correct that using the Tint (Hue) slider on Totem player.
I have no idea how to correct this however.

---

### Post by tyle on 2012-03-29
I see the same thing. Disabling hardware acceleration in flash is a workaround that works here.

---

### Post by Bao2 on 2012-03-29
My videos are smurfed, or avatarized. All the people is now blue.

---

### Post by Bao2 on 2012-03-29
Thanks!
Right clicking and turning OFF hardware acceleration worked for me too.:p

---

### Post by Resplendent Raven on 2012-03-29
Hmm.. for some reason i can't click that hardware acceleration window, it responds to nothing.
I have to reload the page to make it go away.

---

### Post by lethalfang on 2012-03-29
> **Bao2 said:**
> Thanks!
Right clicking and turning OFF hardware acceleration worked for me too.:p

That fixed it.....

---

### Post by Resplendent Raven on 2012-03-29
This is quite annoying..seems like i am stuck with the smurfs until a real fix surfaces.
Tried unticking the box using the TAB button, but that doesn't work either.

---

### Post by pootan on 2012-03-29
For people with problems disabling HW acceleration try adding this line to  /etc/adobe/mms.cfg



 ```
EnableLinuxHWVideoDecode=1
```Also have a look at this page and see what works for you.

[http://r3dux.org/2011/12/how-to-partially-workaround-adobe-flash-plugin-issues-on-linux/](http://r3dux.org/2011/12/how-to-partially-workaround-adobe-flash-plugin-issues-on-linux/)

For my part I am using this addon:

[https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/](https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/)

---

### Post by ubuntu27 on 2012-03-29
That's a bug in the new Flash Player. As [discussed here]("ubuntuforums.org/showthread.php?t=1948622")

---

### Post by jorritTyb on 2012-03-30
> **pootan said:**
> For people with problems disabling HW acceleration try adding this line to  /etc/adobe/mms.cfg



 ```
EnableLinuxHWVideoDecode=0
```

Also have a look at this page and see what works for you.

[http://r3dux.org/2011/12/how-to-partially-workaround-adobe-flash-plugin-issues-on-linux/](http://r3dux.org/2011/12/how-to-partially-workaround-adobe-flash-plugin-issues-on-linux/)

For my part I am using this addon:

[https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/](https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/)

I had to create /etc/adobe/mms.cfg but even then it doesn't work for me. The colors are still wrong. Also I can't use that plugin because that seems to be for firefox only and I'm using Chromium.

I also can't change the HW acceleration checkbox in the flash settings itself since that settings window is simply not responding (as reported by others too).

EDIT: Apparently for fixing the bad colors you have to use EnableLinuxHWVideoDecode=1 instead! Not 0! It is ok for me now.

Greetings,

---

### Post by pootan on 2012-03-30
> **jorritTyb said:**
> 

EDIT: Apparently for fixing the bad colors you have to use EnableLinuxHWVideoDecode=1 instead! Not 0! It is ok for me now.

Greetings,Yes, sorry my mistake there. I changed my post accordingly. Glad you have it sorted.

---

### Post by Resplendent Raven on 2012-03-30
> **jorritTyb said:**
> I had to create /etc/adobe/mms.cfg  

I don't have the adobe folder or the mms.cfg file
Also i am not sure how i should create this from scratch, because apparently i can't create folders inside /etc

---

### Post by jorritTyb on 2012-03-30
> **Resplendent Raven said:**
> I don't have the adobe folder or the mms.cfg file
Also i am not sure how i should create this from scratch, because apparently i can't create folders inside /etc

You have to do it as root. Then you can make folders.

Greetings,

---

### Post by defaria on 2012-03-30
I have the same problem. Downgrading to 10.x solves it. I do not want to lose hardware acceleration. This new flash is 11.2. Where's 11.1?

---

### Post by flemur13013 on 2012-03-30
FWIW, I sometimes get the same effect (blue skin, etc) with avidemux, while VLC continues to display files correctly.  I haven't checked into any connection with flash or HW acceleration. Yet.

---

### Post by pootan on 2012-03-30
> **defaria said:**
>  This new flash is 11.2. Where's 11.1?


[http://helpx.adobe.com/flash-player/...-versions.html]("http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html")



*11.1.102.63*   seems to be the latest working version.

---

### Post by flemur13013 on 2012-03-30
FWIW, I sometimes get the same effect (blue skin, etc) with avidemux, while VLC continues to display files correctly.  I haven't checked into any connection with flash or HW acceleration. Yet.

---

### Post by Resplendent Raven on 2012-03-30
Figured it wouldn't be so hard, but i now managed to make the directory by searching how to make a directory as root.
But now i can't figure out how to make the file itself inside the folder:confused:

---

### Post by jorritTyb on 2012-03-30
> **Resplendent Raven said:**
> Figured it wouldn't be so hard, but i now managed to make the directory by searching how to make a directory as root.
But now i can't figure out how to make the file itself inside the folder:confused:

Use a text editor like 'vim'. Or else do this (as root):

```

cd /etc/adobe
cat >mms.cfg
... (the lines you want in mms.cfg)
^D (press ctrl-D to end)

```

---

### Post by Resplendent Raven on 2012-03-30
I tried ```
cat >mms.cfg
```But it's telling me that access is denied, also for some reason cd /etc/adobe
puts me in etc/adobe$

---

### Post by pootan on 2012-03-30
If you are using Ubuntu you can type 

```
gksudo nautilus
```into a terminal and that will allow you to create a text file as root with right click.

---

### Post by LewisTM on 2012-03-30
I installed the latest beta Flash using Firefox's Flash-Aid plugin and that solved it, the Smurfs are gone.

Cheers!

---

### Post by Resplendent Raven on 2012-03-30
First of all, thank you guys for the great help.
But now that i finally made the file with the "EnableLinuxHWVideoDecode=1" line and rebooted, i still have smurfs..

Will there be another update that will fix this, or am i really supposed to fiddle away until i finally find something that works.
Also noticed that the plugin now crashes a lot and that didn't happen before either :(...

---

### Post by pootan on 2012-03-30
The true answer here is adobe released a faulty plugin which they have known about for quite a few months while it was in Beta. They no longer support Firefox with Linux. 

You do have a couple of options. You can roll back your flash plugin to 11.1.102.63 or you can re-enable hardware acceleration which will most likely solve your crashes and use the Flash Video replacer add-on to watch youtube videos. Most other sites should work fine.

---

### Post by Resplendent Raven on 2012-03-30
Those crashes already occured before I made the mms.cfg file.
I will look into the Flash-Aid plugin and the rolling back option.
I watch YT quite a lot, so it quite bothers me.

If I understand you correctly, future versions will still include this bug or is it thinkable that it somehow will be fixed?

---

### Post by pootan on 2012-03-30
Well hopefully someone at Adobe might decide to look into it as I have no doubt the outcry will get louder and louder as more people update or got to watch a video. Adobe hass only promised security updates after this version so your guess is as good as mine if they will fix it. The bug was closed by them when it was reported so I wouldn't hold my breath.

I've gotten used to watching my videos embedded on the youtube page with Mplayer. You can also choose a few options like WebM/Html5

[https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/](https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/)

If you want your flash back the way it was though in the short term your best bet is rolling back.

---

### Post by Resplendent Raven on 2012-03-30
Oke, so if I am rolling back, what do I do exactly?
I imagine I uninstall the current version using synaptic and then select the package via the link you provided earlier.
Is it as easy as click and install or are there other things I should be mindful of?

---

### Post by flemur13013 on 2012-03-30
> **pootan said:**
> 
[https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/](https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/)

If you want your flash back the way it was though in the short term your best bet is rolling back.


FWIW, I've only had the color problem with avidemux, tho ti may have been caused by flash.

I rolled back the current 11.whatever flash to the 10.whatever version in the 10.04 repositories; youtube complained about the version. 

Installed flashvideoreplacer (w/vlc setting) and got blue-skinned youtube videos for the first time! 

Removed the videoreplacer and youtube is fine again, and so far it hasn't complained about the flash version (=10.?).   videoreplacer also had minimal controls on "embedded" display, and no controls except pause on "new tab" (w/vlc), so I'm going to leave it removed.

---

### Post by caloner on 2012-03-30
Same solution worked for me. It was annoying the heck out of me. I'm using 64 bit Ubuntu 10.04. Thanks a lot.

---

### Post by pootan on 2012-03-30
> **flemur13013 said:**
>    videoreplacer also had minimal controls on "embedded" display, and no controls except pause on "new tab" (w/vlc), so I'm going to leave it removed.Yea I found Mplayer to have the best embedded controls and fullscreen as well. Glad your end is working though.


> **Resplendent Raven said:**
> Oke, so if I am rolling back, what do I do exactly?
I imagine I uninstall the current version using synaptic and then select the package via the link you provided earlier.
Is it as easy as click and install or are there other things I should be mindful of?
Yes you should find it in synaptic by searching 'flash' or 'flash-plugin' If you follow the instructions in this post you should be set just make sure you select the right version for your install. 


[http://ubuntuforums.org/showpost.php?p=11803795&postcount=15](http://ubuntuforums.org/showpost.php?p=11803795&postcount=15)

---

### Post by motorcity909 on 2012-03-30
Hi all

Just noticed a problem with some online video.  On some sites, people appear with blue skin - see attached YouTube and CNN screengrabs.

However, other sites are fine - see attached BBC iPlayer, Sky News and Guardian screengrabs. 

This is on Firefox but Chrome seems the same.

I use Flashblock but have turned it off and still the same.  Cleared Flash cache, still the same.  Rebooted PC, still the same.

Any help will be much appreciated.

Da\/e

---

### Post by papibe on 2012-03-30
Hi motorcity909.

Apparently there's a bug on the new flash plug-in. This [thread]("http://ubuntuforums.org/showthread.php?t=1949137&highlight=youtube") offers a couple of solutions.

Hope that helps.
Regards.

---

### Post by motorcity909 on 2012-03-30
Thanks for the super quick reply papibe

The disable hardware acceleration seems to have worked for now and I'll look at the other more permanent fixes like a roll-back tomorrow.

I've got Minitube as well in the meantime.

Thanks again
Dave

---

### Post by lovinglinux on 2012-03-31
> **pootan said:**
> Well hopefully someone at Adobe might decide to look into it as I have no doubt the outcry will get louder and louder as more people update or got to watch a video. Adobe hass only promised security updates after this version so your guess is as good as mine if they will fix it. The bug was closed by them when it was reported so I wouldn't hold my breath.

Adobe is  not even providing support for Linux users anymore. I have received a few reports from users that tried obtain help from Adobe and received a reply stating they are no longer supporting Linux. 

> **flemur13013 said:**
> FWIW, I've only had the color problem with avidemux, tho ti may have been caused by flash.

I rolled back the current 11.whatever flash to the 10.whatever version in the 10.04 repositories; youtube complained about the version. 

Installed flashvideoreplacer (w/vlc setting) and got blue-skinned youtube videos for the first time! 

Removed the videoreplacer and youtube is fine again, and so far it hasn't complained about the flash version (=10.?).   videoreplacer also had minimal controls on "embedded" display, and no controls except pause on "new tab" (w/vlc), so I'm going to leave it removed.

Probably because you are using VLC plugin, which is not a good plugin (the player is excellent, but the plugin isn't). Install gecko-mediaplayer and disable Totem and VLC plugins in about:addons.

---

### Post by sdowney717 on 2012-03-31
screenshot shows this

the other websites like cnn are ok.

I recall this just happened yesterday. Is someone messing with it and how could they?
This happens on ALL youtube vids. The regular screen pictures images are normal.

---

### Post by sdowney717 on 2012-03-31
here some more in Firefox, notice the explosion is totally blue.

Chrome is same way.

---

### Post by philinux on 2012-03-31
> **sdowney717 said:**
> screenshot shows this

the other websites like cnn are ok.

I recall this just happened yesterday. Is someone messing with it and how could they?
This happens on ALL youtube vids. The regular screen pictures images are normal.

Not seeing that have you got a link to the vids.

Looks normal here.

---

### Post by sdowney717 on 2012-03-31
sure enough

[https://www.youtube.com/watch?v=Ul5htxl_Hvk&feature=relmfu](https://www.youtube.com/watch?v=Ul5htxl_Hvk&feature=relmfu)

[http://www.youtube.com/watch?v=diUiHPQEbT8&feature=related](http://www.youtube.com/watch?v=diUiHPQEbT8&feature=related)

[http://www.youtube.com/watch?v=gdamC7jUrjs&feature=context&context=G200f81fFOAAAAAAACAA](http://www.youtube.com/watch?v=gdamC7jUrjs&feature=context&context=G200f81fFOAAAAAAACAA)

---

### Post by philinux on 2012-03-31
> **sdowney717 said:**
> sure enough

[https://www.youtube.com/watch?v=Ul5htxl_Hvk&feature=relmfu](https://www.youtube.com/watch?v=Ul5htxl_Hvk&feature=relmfu)

[http://www.youtube.com/watch?v=diUiHPQEbT8&feature=related](http://www.youtube.com/watch?v=diUiHPQEbT8&feature=related)

[http://www.youtube.com/watch?v=gdamC7jUrjs&feature=context&context=G200f81fFOAAAAAAACAA](http://www.youtube.com/watch?v=gdamC7jUrjs&feature=context&context=G200f81fFOAAAAAAACAA)

All normal here.

Try a reboot if you havent already.

---

### Post by sdowney717 on 2012-03-31
Yes, I had rebooted about 5 minutes ago after more updates today. But I recall it being messed up yesterday also.
Is there some type of color profile setting for flash?
nice pretty blue skinned people.

ok, it is now blue on cnn videos

---

### Post by sdowney717 on 2012-03-31
[http://news.yahoo.com/boat-sinks-texas-man-survives-30-hours-gulf-165253660.html](http://news.yahoo.com/boat-sinks-texas-man-survives-30-hours-gulf-165253660.html)

this site shows normal color!
For me, somehow this color setting is only on certain video sites.

When updates are published, are settings being changed in initialization type of files? Like a programmer playfully makes changes and forgets to change them back before the update? Something that would say youtube and cnn vid make it blue.

---

### Post by Gremlinzzz on 2012-03-31
Looks normal here
[http://dsc.discovery.com/tv/shark-week/](http://dsc.discovery.com/tv/shark-week/)

and at the other sites

---

### Post by philinux on 2012-03-31
> **sdowney717 said:**
> [http://news.yahoo.com/boat-sinks-texas-man-survives-30-hours-gulf-165253660.html](http://news.yahoo.com/boat-sinks-texas-man-survives-30-hours-gulf-165253660.html)

this site shows normal color!
For me, somehow this color setting is only on certain video sites.

When updates are published, are settings being changed in initialization type of files? Like a programmer playfully makes changes and forgets to change them back before the update? Something that would say youtube and cnn vid make it blue.

Thats odd have you got some odd FF addons. How about try safe mode.

---

### Post by sdowney717 on 2012-03-31
I found a reason in a bug report here.

This sounds pretty bad.

We cant have new people coming into ubuntu and getting blue skinned smurf people.
Can this patch be **applied automatically?**
I have not tried the patch which will take me some time to figure out how. A newbie certainly will get discouraged.

[http://www.nvnews.net/vbulletin/showthread.php?p=2541616](http://www.nvnews.net/vbulletin/showthread.php?p=2541616)

>  Adobe Flash Player 11.2 under NVIDIA drivers (hangs, crashes and blue skin color)
In default configuration (i.e. without /etc/adobe/mms.cfg file) Adobe Flash Player 11.2 has the following problems in Linux with NVIDIA drivers:

1) People's skin is blueish, people look like smurfs. Bug report, another bug report (Adobe cannot or more likely doesn't want to reproduce this bug - there's still a possibility that it's indeed NVIDIA's drivers bug).

2) YouTube videos leak through black parts of other windows (Adobe is aware of this bug but they don't want to fix it).

3) Watching YouTube videos causes Flash player to hang, crash the browser or freeze X.org server (A bug in X.org server or NVIDIA drivers as both sides blame each other).

4) It's impossible to read some websites which contain Flash charts. Just open this page and try to smooth scroll it in Mozilla Firefox. CPU usage will jump to 100%, the whole image on the display will be garbled (Most likely a bug in the interaction of X.org server and NVIDIA drivers).

I have also noticed yahoo finance flash stock charts dont load.

---

### Post by dino99 on 2012-03-31
maybe your profile is named April1st :)

---

### Post by philinux on 2012-03-31
Got nVidia here. And 11.2 flash. It says it's using Hardware Accel but I cant untick it or do anything from right click on a flash vid

---

### Post by defaria on 2012-03-31
Great. So are we stuck with blue smurfs - [http://linux.slashdot.org/story/12/03/31/1417245/adobe-releases-last-linux-version-of-flash-player?utm_source=rss1.0mainlinkanon&utm_medium=feed](http://linux.slashdot.org/story/12/03/31/1417245/adobe-releases-last-linux-version-of-flash-player?utm_source=rss1.0mainlinkanon&utm_medium=feed)

---

### Post by sdowney717 on 2012-03-31
Can some one give me a clue as to how to install this patch?

[http://www.nvnews.net/vbulletin/showpost.php?p=2518770&postcount=104](http://www.nvnews.net/vbulletin/showpost.php?p=2518770&postcount=104)

step by step will be nice.

Seeing flash is no longer being developed for linux how long before Adobe fixes this?

---

### Post by philinux on 2012-03-31
> **sdowney717 said:**
> Can some one give me a clue as to how to install this patch?

[http://www.nvnews.net/vbulletin/showpost.php?p=2518770&postcount=104](http://www.nvnews.net/vbulletin/showpost.php?p=2518770&postcount=104)

step by step will be nice.

Seeing flash is no longer being developed for linux how long before Adobe fixes this?

Before patching. How about try a livecd or usb. Install flash etc and see if it's a problem there.

---

### Post by dino99 on 2012-03-31
> **sdowney717 said:**
> Can some one give me a clue as to how to install this patch?

[http://www.nvnews.net/vbulletin/showpost.php?p=2518770&postcount=104](http://www.nvnews.net/vbulletin/showpost.php?p=2518770&postcount=104)

step by step will be nice.

Seeing flash is no longer being developed for linux how long before Adobe fixes this?

adobe have decided to stop the Linux support about Flash, so ...

first, purge then reinstall flashplugin-installer from synaptic, then better to get a new clean .local, remove yours , you'll get a new one on next reboot.

---

### Post by sdowney717 on 2012-03-31
Ok, tried that, purge and reinstall flash.
Deleted .local folder
rebooted

Showing The Blue Hand.
Someone like to share the patch procedure. I cant be the only affected person.

---

### Post by dino99 on 2012-03-31
wonder if it can be related to the theme used or the session used (unity, gnome, GS, ...)

---

### Post by sdowney717 on 2012-03-31
[http://www.nvnews.net/vbulletin/showpost.php?p=2518770&postcount=104](http://www.nvnews.net/vbulletin/showpost.php?p=2518770&postcount=104)

reading this sounds like you would 
1. make a backup of the libvdpau_trace.so file

2. run patch command against  libvdpau_trace.so file

3. then have to modify the start parameter of the browser.
add an "export VDPAU_TRACE=1" line to /usr/lib/firefox-n.n/firefox.sh

4. likely restart system.

What about for the Chrome browser?

patch manual page
[http://linux.die.net/man/1/patch](http://linux.die.net/man/1/patch)

---

### Post by sdowney717 on 2012-03-31
> wonder if it can be related to the theme used or the session used (unity, gnome, GS, ...)

logged out and back in with LXDE and they are still blue smurfs.

---

### Post by terry_gardener on 2012-03-31
i am using arch linux and using flash 11 and nvidia 290.33 driver and had the blue smurf face affect to fix it edit the /etc/adobe/mms.cfg file by removing the # at the front of the hardware acceleration line. save the file and then restart firefox and the smurfs are gone. 

i have attached my mms.cfg file so you can see how it looks.

---

### Post by sdowney717 on 2012-03-31
I dont have an mms.cfg file and I dont have an /etc/adobe folder.

odd? different system?

---

### Post by motorcity909 on 2012-03-31
Hi

I've rolled Flash back to v.11.1.102.63 and the Smurf Manhattan Avatar look has gone.

Thanks to papibe and to posters on the other threads.

Roll on the death of flash!

Cheers
Dave 

:p

---

### Post by zuti on 2012-03-31
> **terry_gardener said:**
> i am using arch linux and using flash 11 and nvidia 290.33 driver and had the blue smurf face affect to fix it edit the /etc/adobe/mms.cfg file by removing the # at the front of the hardware acceleration line. save the file and then restart firefox and the smurfs are gone.

Beware that this will most likely make Flash extremely unstable. The easiest way to get past the Smurf problem is to disable hardware acceleration completely in Flash settings, at least for the time being.

---

### Post by sdowney717 on 2012-03-31
how do you run flash settings?

---

### Post by Sworddragon on 2012-03-31
Here is already a thread about the new troubles: [http://ubuntuforums.org/showthread.php?t=1948622](http://ubuntuforums.org/showthread.php?t=1948622)

---

### Post by lovinglinux on 2012-03-31
> **Sworddragon said:**
> Here is already a thread about the new troubles: [http://ubuntuforums.org/showthread.php?t=1948622](http://ubuntuforums.org/showthread.php?t=1948622)

Merged.

Go back to thread start and check possible solutions.

If nothing suggested in this thread works, you can try to [downgrade flash](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/). Keep in mind, it will be less secure, so use NoScript to block flash content from untrusted sources.

About the situation, Flash on Linux has been suffering with lack of support for hardware acceleration for a long time. Adobe did make it work for some time, but disabled the functionality a couple of versions back. The SMURF problem is not very common, but is not rare either. Since Adobe is no longer supporting flash on Linux, I doubt it will be ever solved. However, this issue comes and go, so it might magically disappear in the next update.

The future is not promising. Google is taking over the development of Flash on Linux. However, they are implementing it through their new Pepper API, which won't be implemented by Mozilla or Opera. So, if the traditional flashplugin stops working, we will have to use Google Chrome to browse flash based web sites.

More info about this at [http://ubuntuforums.org/showthread.php?t=1949908](http://ubuntuforums.org/showthread.php?t=1949908)

---

### Post by sdowney717 on 2012-03-31
What a piece of work, adobe releasing this buggy version which if you read this whole thread, Adobe knew about this bug for a long time and then the Linux Os's accepting it.

what is the easiest clearest way to fix the colors?
and how to do it?
thanks

---

### Post by terry_gardener on 2012-03-31
> **zuti said:**
> Beware that this will most likely make Flash extremely unstable. The easiest way to get past the Smurf problem is to disable hardware acceleration completely in Flash settings, at least for the time being.

it does make the flash plugin crash more often but just reload the page and it works again.

---

### Post by lovinglinux on 2012-03-31
> **sdowney717 said:**
> how do you run flash settings?

Right-click on a flash video.

---

### Post by sdowney717 on 2012-03-31
When i click on the flash video, it will not let me change anything under the settings menu.
cant uncheck hardware acceleration, which someone else said they also cant do.

---

### Post by santosh83 on 2012-03-31
> **Nuskrad said:**
> I can confirm this, happened after flashplugin-installer was updated from 11.1.102.63ubuntu0.11.04.1 to 11.2.202.228ubuntu0.11.04.1. Only affecting youtube, other flash video seems to be unaffected

I'm using the Flash Player plugin supplied by Adobe on their website (version 11.2.202.228, Ubuntu Apt package), and am NOT having this problem with Youtube, or any other video site, as far as I can see.

Running Firefox 11.0 64-bit on Ubuntu 10.10.

---

### Post by lovinglinux on 2012-03-31
> **sdowney717 said:**
> When i click on the flash video, it will not let me change anything under the settings menu.
cant uncheck hardware acceleration, which someone else said they also cant do.

Open /etc/adobe/mms.cfg with an editor using admin privileges.

```
gksudo gedit /etc/adobe/mms.cfg
```

Add this line:

```
EnableLinuxHWVideoDecode=1
```

---

### Post by lovinglinux on 2012-03-31
> **santosh83 said:**
> I'm using the Flash Player plugin supplied by Adobe on their website (version 11.2.202.228, Ubuntu Apt package), and am NOT having this problem with Youtube, or any other video site, as far as I can see.

Running Firefox 11.0 64-bit on Ubuntu 10.10.

This problem only affects nVidia users.

---

### Post by sdowney717 on 2012-03-31
> **lovinglinux said:**
> Open /etc/adobe/mms.cfg with an editor using admin privileges.

```
gksudo gedit /etc/adobe/mms.cfg
```

Add this line:

```
EnableLinuxHWVideoDecode=1
```

yes just tried this set to 1 and flash will crash:(
You have to make that folder and file, mine did not exist.

I can set it to EnableLinuxHWVideoDecode=0 and firefox works without any hardware acceleration, normal colors except it looks awful, chrome still blue, does not respect setting to 0

---

### Post by lovinglinux on 2012-03-31
> **sdowney717 said:**
> yes just tried this set to 1 and flash will crash:(
You have to make that folder and file, mine did not exist.

I can set it to EnableLinuxHWVideoDecode=0 and firefox works without any hardware acceleration, normal colors except it looks awful, chrome still blue, does not respect setting to 0

Try an older version of Flash.

[http://archive.canonical.com/pool/partner/a/adobe-flashplugin/](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/)

---

### Post by mc4man on 2012-03-31
I'd go with an older flash version but if you wish to disable hw acceleration in the flash settings you must do it in the player while it's  in fullscreen
(scrollbars make the settings box unclickable

---

### Post by sdowney717 on 2012-03-31
I am running precise beta and none in that list shows 11.1 for precise.
Do you see one?

---

### Post by sdowney717 on 2012-03-31
> **mc4man said:**
> I'd go with an older flash version but if you wish to disable hw acceleration in the flash settings you must do it in the player while it's  in fullscreen
(scrollbars make the settings box unclickable
Thanks!
This finally worked. make it full screen then uncheck hardware acceleration, skin colors are normal again.
You may have to keep clicking settings, I notice it takes 2 or 3 clicks to bring up the dialog box.
I cant even show that menu with firefox, only with google chrome. Firefox is also missing the fullscreen box, right click to select that, but the flash menu will not appear for me in firefox.
I must be not using the flash player in firefox.

---

### Post by mc4man on 2012-03-31
> **sdowney717 said:**
> Thanks!
This finally worked. make it full screen then uncheck hardware acceleration, skin colors are normal again.
You may have to keep clicking settings, I notice it takes 2 or 3 clicks to bring up the dialog box.
Glad you got it - if performance issues then use an older version & re-enable hw acel

*was wondering where this thread went to - there was no sign of it in the precise forum when I went to reply a while ago..

edit - yeah - 2 clicks here to bring up settings in fullscreen

---

### Post by santosh83 on 2012-03-31
> **lovinglinux said:**
> This problem only affects nVidia users.

Oh right then! My bad for not reading the thread in detail!

---

### Post by sdowney717 on 2012-03-31
I noticed something about Chrome, I removed the flash plugin using synaptic. But Chrome still has flash 11.2 installed. I seem to recall chrome was going to do that having a version of flash built-in.

---

### Post by lovinglinux on 2012-03-31
> **mc4man said:**
> Glad you got it - if performance issues then use an older version & re-enable hw acel

*was wondering where this thread went to - there was no sign of it in the precise forum when I went to reply a while ago..

edit - yeah - 2 clicks here to bring up settings in fullscreen

Sorry. My mistake. I was merging several threads dealing with the SMURF effect in flash and didn't realize one was from the Ubuntu +1 forum.

---

### Post by lovinglinux on 2012-03-31
> **sdowney717 said:**
> I noticed something about Chrome, I removed the flash plugin using synaptic. But Chrome still has flash 11.2 installed. I seem to recall chrome was going to do that having a version of flash built-in.

Type [noparse]about:plugins[/noparse], then diable the version that comes with Chrome.

---

### Post by ouija1979 on 2012-04-02
I have a really weird problem, when i watch a video on YouTube it is appearing like a negative, if, however, i search for the same video through Yahoo and watch it that way playing youtube through Yahoo it is normal. It happened after the update I did yesterday. Videos on my Mac are fine, just my Ubuntu PC, I am using 11.10.

I may be just a complete noob and have done something silly, but it really has me scratching my head :confused:

Oh yeah, and I am using Firefox :)

---

### Post by bobman321123 on 2012-04-02
I had the same problem, and I don't remember which one of these fixes worked, so I'll just give you some links, ok?
[http://askubuntu.com/questions/117127/flash-video-appears-blue](http://askubuntu.com/questions/117127/flash-video-appears-blue)
[http://www.my-guides.net/en/guides/linux/324-how-to-fix-the-blue-tint-on-youtube-videos-problem-flash-and-nvidia](http://www.my-guides.net/en/guides/linux/324-how-to-fix-the-blue-tint-on-youtube-videos-problem-flash-and-nvidia)

Or you could also just go to [HTML5 Youtube]("http://youtube.com/html5"). This will change your youtube from flash (which has the colour problem) to html5, which is looking to become the new industry standard. 

NOTE: Firefox is not officially fully supported in youtube/html5, but I've tried it out, and have no problems with it. Chromium works perfectly.

I hope this helped!

---

### Post by lovinglinux on 2012-04-02
> **ouija1979 said:**
> I have a really weird problem, when i watch a video on YouTube it is appearing like a negative, if, however, i search for the same video through Yahoo and watch it that way playing youtube through Yahoo it is normal. It happened after the update I did yesterday. Videos on my Mac are fine, just my Ubuntu PC, I am using 11.10.

I may be just a complete noob and have done something silly, but it really has me scratching my head :confused:

Oh yeah, and I am using Firefox :)

Thread merged.

Disable hardware acceleration in Flash Settings. See instructions and other suggestions on previous posts.

---

### Post by tlan on 2012-04-03
This is the confirmed resolution, yes the last update ~ 03/29/2012 destroyed flash causing blue tint

goto
[http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html) and download
use version 11.1.102 which will include 32 and 64bit binaries.

via software center
uninstall flash player plugin
gnash
lightspark
and install flash plugin 10

now extract the downloaded 11.1.102
merge the extracted folders to the corresponding folders
copy libflashplayer.so to /usr/lib/mozilla/plugins
reboot
fixed for all mozilla browsers including chrome.

keep the archive just in case, very low CPU utilisation 10% viewing flash sites.

---

### Post by lovinglinux on 2012-04-03
> **tlan said:**
> This is the confirmed resolution, yes the last update ~ 03/29/2012 destroyed flash causing blue tint

goto
[http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html) and download
use version 11.1.102 which will include 32 and 64bit binaries.

via software center
uninstall flash player plugin
gnash
lightspark
and install flash plugin 10

now extract the downloaded 11.1.102
merge the extracted folders to the corresponding folders
copy libflashplayer.so to /usr/lib/mozilla/plugins
reboot
fixed for all mozilla browsers including chrome.

keep the archive just in case, very low CPU utilisation 10% viewing flash sites.


[Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") can do that for you as well. Get the flash player version you need from [Adobe](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html). Extract the archive, find the tar.gz file corresponding to your architecture (don't extract it) and copy it. Open Flash-Aid Advanced mode, select "Custom" in the installation option, paste the tar.gz path in the field. Click the Script tab, then Execute. Flash-Aid will remove all installed flash versions and install the  one from the tar.gz file in the proper location.

---

### Post by terrykiwi83 on 2012-04-03
Well I have got to say that this is pretty unusual so I thought I would share it.

I have noticed that on Youtube videos the colour of the skin has now changed to BLUE, on all videos. Am either going colour blind or just going nuts ?

Anyone experienced this before, or have any solutions?

Attached a screenshot for your amusement.

Cheers

---

### Post by Rodney9 on 2012-04-03
You are not alone - 

[http://ubuntuforums.org/showthread.php?t=1949137](http://ubuntuforums.org/showthread.php?t=1949137)

Some fixes suggested.

Rodney

---

### Post by Rex Bouwense on 2012-04-03
Smurfs!!??

---

### Post by Rodney9 on 2012-04-03
Avatars

[http://askubuntu.com/questions/117127/flash-video-appears-blue](http://askubuntu.com/questions/117127/flash-video-appears-blue)

---

### Post by tlan on 2012-04-05
> **lovinglinux said:**
> [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") can do that for you as well. Get the flash player version you need from [Adobe]("http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html"). Extract the archive, find the tar.gz file corresponding to your architecture (don't extract it) and copy it. Open Flash-Aid Advanced mode, select "Custom" in the installation option, paste the tar.gz path in the field. Click the Script tab, then Execute. Flash-Aid will remove all installed flash versions and install the  one from the tar.gz file in the proper location.


Tried this too it did not work, the only fix was the fix i posted.

---

### Post by lovinglinux on 2012-04-05
> **tlan said:**
> Tried this too it did not work, the only fix was the fix i posted.

Did you extracted and copied the correct file? Because it is working here and several other users also reported that it worked.

---

### Post by Conscript on 2012-04-05
Strange thing happened,  everything I view on youtube now has its colors all messed up.  Haven't the foggiest idea why.  Reinstall flash?  Kind of puzzled.  If I download the video my media player displays colors properly, but when streamed it fouls up the colors.

Any advice would be great, otherwise I'll just get used to blue people. Weird...

---

### Post by lovinglinux on 2012-04-05
Merging with [http://ubuntuforums.org/showthread.php?t=1949137](http://ubuntuforums.org/showthread.php?t=1949137)

---

### Post by DMustaine on 2012-04-06
Good Grief! this is a PITA. I've tried at least 3 of the options here, no go."Global Settings" throws me to the adobe help pages. /usr/lib/adobe-flashplugin/libflashplayer.so fix does nothing, so on...

Hell even finding this page, and the help suggestions sucks. 

I've hated adobe for years, and this is just another reason to despise those jerk-wads.

---

### Post by lovinglinux on 2012-04-06
> **DMustaine said:**
> Good Grief! this is a PITA. I've tried at least 3 of the options here, no go."Global Settings" throws me to the adobe help pages. /usr/lib/adobe-flashplugin/libflashplayer.so fix does nothing, so on...

Hell even finding this page, and the help suggestions sucks. 

I've hated adobe for years, and this is just another reason to despise those jerk-wads.

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

### Post by SeijiSensei on 2012-04-06
This is a [known bug]("https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/967091") with the most recent (and sadly final) release of flashplayer on NVIDIA adapters with hardware acceleration enabled.  Try right-clicking on the video and unchecking the HW acceleration box, then refresh the page.

---

### Post by lovinglinux on 2012-04-06
I have created a thread which explains the easy methods of fixing this:

Please refer to [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by DMustaine on 2012-04-08
> **lovinglinux said:**
> Please attach the firefox-report.txt file generated in your desktop after running the commands below:

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


Thank you for the reply:

```
Ubuntu Architecture

Linux XXXXX 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686 i686 i386 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

Firefox Packages

firefox                        install
firefox-globalmenu                install
firefox-gnome-support                install
firefox-locale-en                install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-11.0/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

ferramroberto-java-natty.list
ferramroberto-java-natty.list.distUpgrade
ferramroberto-java-natty.list.save
kilian-f_lux-natty.list
kilian-f_lux-natty.list.distUpgrade
kilian-f_lux-natty.list.save
tiheum-equinox-natty.list
tiheum-equinox-natty.list.distUpgrade
tiheum-equinox-natty.list.save

Flash packages

adobe-flash-properties-gtk            install
adobe-flashplugin                install
flashplugin-installer                deinstall

Plugin locations

/usr/lib/adobe-flashplugin/libflashplayer.so

/usr/lib/mozilla/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/firefox-addons/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/adobe-flashplugin/libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)

pluginreg.dat

Generated File. Do not edit.

[HEADER]
Version:0.15:$
Arch:x86-gcc3:$

[PLUGINS]
libflashplayer.so:$
/usr/lib/adobe-flashplugin/libflashplayer.so:$
:$
1331854066000:1:1:$
Shockwave Flash 11.2 r202:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$
npica.so:$
/usr/lib/ICAClient/npica.so:$
:$
1329441917000:1:5:$
ICA Plugin (Linux) Version 12.0.0.189834 (/usr/lib/ICAClient/wfica):$
Citrix Receiver for Linux:$
1
0:application/x-ica:Handles ICA connections:ica:$
librhythmbox-itms-detection-plugin.so:$
/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so:$
:$
1327384698000:1:5:$
This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.:$
iTunes Application Detector:$
1
0:application/itunes-plugin:::$
libtotem-cone-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-cone-plugin.so:$
:$
1318914895000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.0.1 plugin handles video and audio streams.:$
VLC Multimedia Plugin (compatible Totem 3.0.1):$
21
0:application/x-vlc-plugin:VLC Multimedia Plugin::$
1:application/vlc:VLC Multimedia Plugin::$
2:video/x-google-vlc-plugin:VLC Multimedia Plugin::$
3:application/x-ogg:Ogg multimedia file:ogg:$
4:application/ogg:Ogg multimedia file:ogg:$
5:audio/ogg:Ogg Audio:oga:$
6:audio/x-ogg:Ogg Audio:ogg:$
7:video/ogg:Ogg Video:ogv:$
8:video/x-ogg:Ogg Video:ogg:$
9:application/annodex:Annodex exchange format:anx:$
10:audio/annodex:Annodex Audio:axa:$
11:video/annodex:Annodex Video:axv:$
12:video/mpeg:MPEG video:mpg, mpeg, mpe:$
13:audio/wav:WAV audio:wav:$
14:audio/x-wav:WAV audio:wav:$
15:audio/mpeg:MP3 audio:mp3:$
16:application/x-nsv-vp3-mp3:NullSoft video:nsv:$
17:video/flv:Flash video:flv:$
18:video/webm:WebM video:webm:$
19:application/x-totem-plugin:Totem Multimedia plugin::$
20:audio/midi:MIDI audio:mid, midi:$
libtotem-narrowspace-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$
:$
1318914895000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.0.1 plugin handles video and audio streams.:$
QuickTime Plug-in 7.6.6:$
5
0:video/quicktime:QuickTime video:mov:$
1:video/mp4:MPEG-4 video:mp4:$
2:image/x-macpaint:MacPaint Bitmap image:pntg:$
3:image/x-quicktime:Macintosh Quickdraw/PICT drawing:pict, pict1, pict2:$
4:video/x-m4v:MPEG-4 video:m4v:$
libtotem-gmp-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$
:$
1318914895000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.0.1 plugin handles video and audio streams.:$
Windows Media Player Plug-in 10 (compatible; Totem):$
13
0:application/x-mplayer2:AVI video:avi, wma, wmv:$
1:video/x-ms-asf-plugin:ASF video:asf, wmv:$
2:video/x-msvideo:AVI video:asf, wmv:$
3:video/x-ms-asf:ASF video:asf:$
4:video/x-ms-wmv:Windows Media video:wmv:$
5:video/x-wmv:Windows Media video:wmv:$
6:video/x-ms-wvx:Windows Media video:wmv:$
7:video/x-ms-wm:Windows Media video:wmv:$
8:video/x-ms-wmp:Windows Media video:wmv:$
9:application/x-ms-wms:Windows Media video:wms:$
10:application/x-ms-wmp:Windows Media video:wmp:$
11:application/asx:Microsoft ASX playlist:asx:$
12:audio/x-ms-wma:Windows Media audio:wma:$
libtotem-mully-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$
:$
1318914895000:1:5:$
DivX Web Player version 1.4.0.233:$
DivX® Web Player:$
1
0:video/divx:AVI video:divx:$
libnpjp2.so:$
/usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libnpjp2.so:$
:$
1304498938000:1:5:$
The next generation <a href="http://java.sun.com">Java</a> plug-in for Mozilla browsers.:$
Java(TM) Plug-in 1.6.0_26:$
34
0:application/x-java-vm:Java&#153 Plug-in::$
1:application/x-java-applet:Java&#153 Plug-in Applet::$
2:application/x-java-applet;version=1.1:Java&#153 Plug-in::$
3:application/x-java-applet;version=1.1.1:Java&#153 Plug-in::$
4:application/x-java-applet;version=1.1.2:Java&#153 Plug-in::$
5:application/x-java-applet;version=1.1.3:Java&#153 Plug-in::$
6:application/x-java-applet;version=1.2:Java&#153 Plug-in::$
7:application/x-java-applet;version=1.2.1:Java&#153 Plug-in::$
8:application/x-java-applet;version=1.2.2:Java&#153 Plug-in::$
9:application/x-java-applet;version=1.3:Java&#153 Plug-in::$
10:application/x-java-applet;version=1.3.1:Java&#153 Plug-in::$
11:application/x-java-applet;version=1.4:Java&#153 Plug-in::$
12:application/x-java-applet;version=1.4.1:Java&#153 Plug-in::$
13:application/x-java-applet;version=1.4.2:Java&#153 Plug-in::$
14:application/x-java-applet;version=1.5:Java&#153 Plug-in::$
15:application/x-java-applet;version=1.6:Java&#153 Plug-in::$
16:application/x-java-applet;jpi-version=1.6.0_26:Java&#153 Plug-in::$
17:application/x-java-bean:Java&#153 Plug-in JavaBeans::$
18:application/x-java-bean;version=1.1:Java&#153 Plug-in::$
19:application/x-java-bean;version=1.1.1:Java&#153 Plug-in::$
20:application/x-java-bean;version=1.1.2:Java&#153 Plug-in::$
21:application/x-java-bean;version=1.1.3:Java&#153 Plug-in::$
22:application/x-java-bean;version=1.2:Java&#153 Plug-in::$
23:application/x-java-bean;version=1.2.1:Java&#153 Plug-in::$
24:application/x-java-bean;version=1.2.2:Java&#153 Plug-in::$
25:application/x-java-bean;version=1.3:Java&#153 Plug-in::$
26:application/x-java-bean;version=1.3.1:Java&#153 Plug-in::$
27:application/x-java-bean;version=1.4:Java&#153 Plug-in::$
28:application/x-java-bean;version=1.4.1:Java&#153 Plug-in::$
29:application/x-java-bean;version=1.4.2:Java&#153 Plug-in::$
30:application/x-java-bean;version=1.5:Java&#153 Plug-in::$
31:application/x-java-bean;version=1.6:Java&#153 Plug-in::$
32:application/x-java-bean;jpi-version=1.6.0_26:Java&#153 Plug-in::$
33:application/x-java-vm-npruntime:::$

[INVALID]

```

---

### Post by lovinglinux on 2012-04-08
> **DMustaine said:**
> Thank you for the reply:

```
Ubuntu Architecture

Linux XXXXX 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686 i686 i386 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

Firefox Packages

firefox                        install
firefox-globalmenu                install
firefox-gnome-support                install
firefox-locale-en                install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-11.0/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

ferramroberto-java-natty.list
ferramroberto-java-natty.list.distUpgrade
ferramroberto-java-natty.list.save
kilian-f_lux-natty.list
kilian-f_lux-natty.list.distUpgrade
kilian-f_lux-natty.list.save
tiheum-equinox-natty.list
tiheum-equinox-natty.list.distUpgrade
tiheum-equinox-natty.list.save

Flash packages

adobe-flash-properties-gtk            install
adobe-flashplugin                install
flashplugin-installer                deinstall

Plugin locations

/usr/lib/adobe-flashplugin/libflashplayer.so

/usr/lib/mozilla/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/firefox-addons/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/adobe-flashplugin/libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)

pluginreg.dat

Generated File. Do not edit.

[HEADER]
Version:0.15:$
Arch:x86-gcc3:$

[PLUGINS]
libflashplayer.so:$
/usr/lib/adobe-flashplugin/libflashplayer.so:$
:$
1331854066000:1:1:$
Shockwave Flash 11.2 r202:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$
npica.so:$
/usr/lib/ICAClient/npica.so:$
:$
1329441917000:1:5:$
ICA Plugin (Linux) Version 12.0.0.189834 (/usr/lib/ICAClient/wfica):$
Citrix Receiver for Linux:$
1
0:application/x-ica:Handles ICA connections:ica:$
librhythmbox-itms-detection-plugin.so:$
/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so:$
:$
1327384698000:1:5:$
This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.:$
iTunes Application Detector:$
1
0:application/itunes-plugin:::$
libtotem-cone-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-cone-plugin.so:$
:$
1318914895000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.0.1 plugin handles video and audio streams.:$
VLC Multimedia Plugin (compatible Totem 3.0.1):$
21
0:application/x-vlc-plugin:VLC Multimedia Plugin::$
1:application/vlc:VLC Multimedia Plugin::$
2:video/x-google-vlc-plugin:VLC Multimedia Plugin::$
3:application/x-ogg:Ogg multimedia file:ogg:$
4:application/ogg:Ogg multimedia file:ogg:$
5:audio/ogg:Ogg Audio:oga:$
6:audio/x-ogg:Ogg Audio:ogg:$
7:video/ogg:Ogg Video:ogv:$
8:video/x-ogg:Ogg Video:ogg:$
9:application/annodex:Annodex exchange format:anx:$
10:audio/annodex:Annodex Audio:axa:$
11:video/annodex:Annodex Video:axv:$
12:video/mpeg:MPEG video:mpg, mpeg, mpe:$
13:audio/wav:WAV audio:wav:$
14:audio/x-wav:WAV audio:wav:$
15:audio/mpeg:MP3 audio:mp3:$
16:application/x-nsv-vp3-mp3:NullSoft video:nsv:$
17:video/flv:Flash video:flv:$
18:video/webm:WebM video:webm:$
19:application/x-totem-plugin:Totem Multimedia plugin::$
20:audio/midi:MIDI audio:mid, midi:$
libtotem-narrowspace-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$
:$
1318914895000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.0.1 plugin handles video and audio streams.:$
QuickTime Plug-in 7.6.6:$
5
0:video/quicktime:QuickTime video:mov:$
1:video/mp4:MPEG-4 video:mp4:$
2:image/x-macpaint:MacPaint Bitmap image:pntg:$
3:image/x-quicktime:Macintosh Quickdraw/PICT drawing:pict, pict1, pict2:$
4:video/x-m4v:MPEG-4 video:m4v:$
libtotem-gmp-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$
:$
1318914895000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.0.1 plugin handles video and audio streams.:$
Windows Media Player Plug-in 10 (compatible; Totem):$
13
0:application/x-mplayer2:AVI video:avi, wma, wmv:$
1:video/x-ms-asf-plugin:ASF video:asf, wmv:$
2:video/x-msvideo:AVI video:asf, wmv:$
3:video/x-ms-asf:ASF video:asf:$
4:video/x-ms-wmv:Windows Media video:wmv:$
5:video/x-wmv:Windows Media video:wmv:$
6:video/x-ms-wvx:Windows Media video:wmv:$
7:video/x-ms-wm:Windows Media video:wmv:$
8:video/x-ms-wmp:Windows Media video:wmv:$
9:application/x-ms-wms:Windows Media video:wms:$
10:application/x-ms-wmp:Windows Media video:wmp:$
11:application/asx:Microsoft ASX playlist:asx:$
12:audio/x-ms-wma:Windows Media audio:wma:$
libtotem-mully-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$
:$
1318914895000:1:5:$
DivX Web Player version 1.4.0.233:$
DivX® Web Player:$
1
0:video/divx:AVI video:divx:$
libnpjp2.so:$
/usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libnpjp2.so:$
:$
1304498938000:1:5:$
The next generation <a href="http://java.sun.com">Java</a> plug-in for Mozilla browsers.:$
Java(TM) Plug-in 1.6.0_26:$
34
0:application/x-java-vm:Java™ Plug-in::$
1:application/x-java-applet:Java™ Plug-in Applet::$
2:application/x-java-applet;version=1.1:Java™ Plug-in::$
3:application/x-java-applet;version=1.1.1:Java™ Plug-in::$
4:application/x-java-applet;version=1.1.2:Java™ Plug-in::$
5:application/x-java-applet;version=1.1.3:Java™ Plug-in::$
6:application/x-java-applet;version=1.2:Java™ Plug-in::$
7:application/x-java-applet;version=1.2.1:Java™ Plug-in::$
8:application/x-java-applet;version=1.2.2:Java™ Plug-in::$
9:application/x-java-applet;version=1.3:Java™ Plug-in::$
10:application/x-java-applet;version=1.3.1:Java™ Plug-in::$
11:application/x-java-applet;version=1.4:Java™ Plug-in::$
12:application/x-java-applet;version=1.4.1:Java™ Plug-in::$
13:application/x-java-applet;version=1.4.2:Java™ Plug-in::$
14:application/x-java-applet;version=1.5:Java™ Plug-in::$
15:application/x-java-applet;version=1.6:Java™ Plug-in::$
16:application/x-java-applet;jpi-version=1.6.0_26:Java™ Plug-in::$
17:application/x-java-bean:Java™ Plug-in JavaBeans::$
18:application/x-java-bean;version=1.1:Java™ Plug-in::$
19:application/x-java-bean;version=1.1.1:Java™ Plug-in::$
20:application/x-java-bean;version=1.1.2:Java™ Plug-in::$
21:application/x-java-bean;version=1.1.3:Java™ Plug-in::$
22:application/x-java-bean;version=1.2:Java™ Plug-in::$
23:application/x-java-bean;version=1.2.1:Java™ Plug-in::$
24:application/x-java-bean;version=1.2.2:Java™ Plug-in::$
25:application/x-java-bean;version=1.3:Java™ Plug-in::$
26:application/x-java-bean;version=1.3.1:Java™ Plug-in::$
27:application/x-java-bean;version=1.4:Java™ Plug-in::$
28:application/x-java-bean;version=1.4.1:Java™ Plug-in::$
29:application/x-java-bean;version=1.4.2:Java™ Plug-in::$
30:application/x-java-bean;version=1.5:Java™ Plug-in::$
31:application/x-java-bean;version=1.6:Java™ Plug-in::$
32:application/x-java-bean;jpi-version=1.6.0_26:Java™ Plug-in::$
33:application/x-java-vm-npruntime:::$

[INVALID]

```

I haven't noticed anything wrong in your report. However, cince you are using adobeflashplugin, there is no need for the npwrapper. You can remove it with this:

```
sudo apt-get purge nspluginwrapper
```

I just noticed that you was trying to disable flash hardware acceleration in "Global Settings". It is just "Settings", not the global one.

---

### Post by motorcity909 on 2012-04-17
For info...

Xubuntu Update Manager advised me Flash v.11.2.202.233 was available so I crossed my fingers there would be no Smurf Avatar effect and ran the update.

Straight to YouTube and there were the blue faces again.

Rolled back to working version 11.1.102.63 and all is fine again.

Dave

---

### Post by tweezak on 2012-04-17
Odd thing happened to me tonight.

MP4 videos play normally.
FLV videos are blue/inverted colors
however...and this is the strange thing...youtube videos are normal

When I last had this problem with blue videos rolling back the flash version to 10.2 fixed it. I am still on that version but now things have gone bad again...except for web videos. Maybe I have a plugin that's fixing it in Firefox.

Anyone got any suggestions for fixing blue non-web flash videos?

UPDATE: Turns out it was the old issue that people mentioned a long time ago about the hue on the totem movie player getting maxed. Switching everything back to defaults makes videos normal again. What the heck causes that to change? I've never messed with those settings before.

---

### Post by DMustaine on 2012-04-18
> **lovinglinux said:**
> I haven't noticed anything wrong in your report. However, cince you are using adobeflashplugin, there is no need for the npwrapper. You can remove it with this:

```
sudo apt-get purge nspluginwrapper
```I just noticed that you was trying to disable flash hardware acceleration in "Global Settings". It is just "Settings", not the global one.

Thanks for the help. From this thread:
[http://ubuntuforums.org/showthread.php?p=11855028#post11855028](http://ubuntuforums.org/showthread.php?p=11855028#post11855028)

I got it resolved, but don't really know how. it just works now.

---

### Post by Fisher on 2012-04-19
The lack of respect for the free software community just make me wish one thing:
Death to flash!!

And say welcome to the new html5!!

---

### Post by sasukeskapa on 2012-05-02
Thank you guys I disabled the harver acceleration and gone to be a html5 trial user, and now everything works. No more avatars :D Thank you.
You really helped me :)

---

### Post by tlan on 2012-05-24
Well my fix in the thread did not work with 12.04. after attempting to fix it in 12.04 64bit using may different versions of flash. i decided to blow out my system and start over, which is much quicker that trying to figure it out.

most of the issues i have had with 12.04 i have been slowly figuring out and fixed so the system is more stable these days..

in 12.04 the version of flash that is the default install is 11.2 r202 and the adobe flash plugin installer is installed in software center, no smurfs

what i do remember that broke my system and caused the smurfs is I installed the ubuntu restricted extras which i have found i really do not need.

just pay attention and stay away from any flash update or the restricted extras and flash should be ok until adobe decides to support linux again or all sites switch to html5.

---

### Post by tlan on 2012-05-24
> **tlan said:**
> Well my fix in the thread did not work with 12.04. after attempting to fix it in 12.04 64bit using may different versions of flash. i decided to blow out my system and start over, which is much quicker that trying to figure it out.

most of the issues i have had with 12.04 i have been slowly figuring out and fixed so the system is more stable these days..

in 12.04 the version of flash that is the default install is 11.2 r202 and the adobe flash plugin installer is installed in software center, no smurfs

what i do remember that broke my system and caused the smurfs is I installed the ubuntu restricted extras which i have found i really do not need.

just pay attention and stay away from any flash update or the restricted extras and flash should be ok until adobe decides to support linux again or all sites switch to html5.

Well as soon as i posted later i noticed i had the smurf/avatar affect and there were no updates. WTF

i went to my original fix for 11.10 and it worked

the key is to get flash player 10 the libflashplayer.so first and follow up with 11.1.102.63

Flash_11.1.102.63_archive, working again

---

### Post by as2000 on 2012-05-25
I just tried fullscreen of YouTube video in FF, right mouse clicked and unchecked hardware acceleration. Restarted browser and tried the video again and voila, no more blue peeps. Seems it is a global thing since it fixed the issue in Chromium.

---

### Post by tjwilli on 2012-05-28
That fixed it for me. Thanks!

---

### Post by xchecker on 2012-05-30
I used the Flash-Aid add-on for Firefox and turned off HWaccel during install which got rid of the smurfs, but flash videos still crash my system.

I'm finding all the various and sometimes conflicting suggestions here confusing.  Can anyone clarify what I should try next?

1) Roll back to an earlier Flash?  (which one and how?)
2) Use HTML5?
3) Turn on or off some other feature?
4) Something else?

I'm using 12.04, 32-bit Firefox and an NVidia graphics card.

---

### Post by tlan on 2012-05-31
> **xchecker said:**
> I used the Flash-Aid add-on for Firefox and turned off HWaccel during install which got rid of the smurfs, but flash videos still crash my system.

I'm finding all the various and sometimes conflicting suggestions here confusing.  Can anyone clarify what I should try next?

1) Roll back to an earlier Flash?  (which one and how?)
2) Use HTML5?
3) Turn on or off some other feature?
4) Something else?

I'm using 12.04, 32-bit Firefox and an NVidia graphics card.

this is what worked for me, no need for the script or disabling HW acceration
1. go to software center and search flash, click adobe flash plugin and click unistall/remove
2. go here and down this file [http://www.4shared.com/archive/EeBNiBpW/install_flash_player_10_linuxt.html](http://www.4shared.com/archive/EeBNiBpW/install_flash_player_10_linuxt.html) or search for install_flash_player_10_linux
extract the file which should be libflashplayer.so
3. now open terminal and type sudo nautilus which will open your file manager with root privileges,
browse to your home dir and the location of the downloaded file and copy it to /usr/lib/mozilla/plugins
4.Reboot
5. Go here and download this file
[http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip)
6. extract the file
7. open the extracted folder and find the version either 32 or 64bit
8. open that folder and extract the file that pertains to your OS
9. launch terminal and type sudo nautilus which will open your file manager
10. browse to the location of the extracted folders and you will see a usr folder, 
11. Copy and paste that folder over the /usr folder at the root
12. also copy and paste the libflashplayer.so file to the /usr/lib/mnozilla/plugins folder overwriting the version10 file from the previous step 3

Reboot

all this must be done using sudo nautilus, and keep the downloaded files handy just in case.

this has worked for all of my PC's running 12.04 that had this problem,

---

### Post by xchecker on 2012-06-02
Thanks tlan for the detailed reply.  Unfortunately it did not solve my problem.  I don't have the 'smurf' issue but flash video is still crashing my system even after reverting flash versions the way you described.

Any other ideas?

---

### Post by tlan on 2012-06-02
> **xchecker said:**
> Thanks tlan for the detailed reply.  Unfortunately it did not solve my problem.  I don't have the 'smurf' issue but flash video is still crashing my system even after reverting flash versions the way you described.

Any other ideas?


what version of flash are you using. 

right click the windows and look for the version #

---

### Post by xchecker on 2012-06-02
version = 10.0.32.18

New thought: Could it be a sound problem?  I've just had the system crash twice now while listening to tunes through Banshee and I wasn't watching any youtube videos at the time.  Hmmmm....

---

### Post by tlan on 2012-06-05
> **xchecker said:**
> version = 10.0.32.18

New thought: Could it be a sound problem?  I've just had the system crash twice now while listening to tunes through Banshee and I wasn't watching any youtube videos at the time.  Hmmmm....


thats the problem you are still using 10.0 which does crash

you need the 11.1.102.63. finish the below steps

5. Go here and download this file
[http://fpdownload.macromedia.com/get...63_archive.zip]("http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip")
6. extract the file
7. open the extracted folder and find the version either 32 or 64bit
8. open that folder and extract the file that pertains to your OS
9. launch terminal and type sudo nautilus which will open your file manager
10. browse to the location of the extracted folders and you will see a usr folder, 
11. Copy and paste that folder over the /usr folder at the root
12. also copy and paste the (11.xx.xx) libflashplayer.so file to the  /usr/lib/mozilla/plugins folder overwriting the version10 file from the  previous step 3

Reboot

all this must be done using sudo nautilus, and keep the downloaded files handy just in case.

---

### Post by Conscript on 2012-06-07
Agreed, right click....tweak hardware acceleration....blue people are gone.  And all is right in the Linux multiverse once more.

---

### Post by xchecker on 2012-06-08
Well, I went through the steps again and Flash now indicates the proper version, but it is still crashing.  I'll go through it again just to double check and see if I get any different result.

The other odd thing that happens with Firefox - and this may be unrelated - is that when I launch it, my homepage does not come up even though I have it set to open upon launch in the Firefox settings.  CLicking on HOME will bring it up OK.  I mention this only because when I completed your instructions this time and rebooted, Firefox actually launched my homepage finally, but after it crashed again the homepage didn't come back on the restart.

---

### Post by justintot on 2012-06-09
> **lovinglinux said:**
> [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") can do that for you as well. Get the flash player version you need from [Adobe]("http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html"). Extract the archive, find the tar.gz file corresponding to your architecture (don't extract it) and copy it. Open Flash-Aid Advanced mode, select "Custom" in the installation option, paste the tar.gz path in the field. Click the Script tab, then Execute. Flash-Aid will remove all installed flash versions and install the  one from the tar.gz file in the proper location.
Thank you. This solution worked perfectly. Make sure you (a) use Advanced Mode [Tools, Flash Aid, Advanced Mode} (b) Check Override GPU Validation and (c) UNCHECK Enable Linux HWVideo decode - If you don't then you cannot jump forward in YouTube playback.

(Ubuntu 12.04 - AMD Quad Core Bulldozer 64Bit - Unity 3D - Firefox 13.0  - NVidia GT 440)

---

### Post by shimoda on 2013-03-28
The solution to use flash 11.1.102 worked since today for me, but now firefox is blocking it for unsafe... :S

any ideas to solve it?

EDIT: I solved it uninstalling libvdpau1, but now audio is choppy... I think I've a problem with jack & pulseaudio when using flash (I'm using Ubuntu Studio)... If I stop jack, all works fine... I'll continue investigating...

---

