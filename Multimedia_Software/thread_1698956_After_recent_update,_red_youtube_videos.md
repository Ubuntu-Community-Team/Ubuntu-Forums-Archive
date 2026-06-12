---
title: "After recent update, red youtube videos?"
date: 2011-03-03
forum: Multimedia Software
---

### Post by nslegacy163 on 2011-03-03
After the recent update my OS went through requiring a restart, all the videos I play on youtube.com from Chrome or Chromium are red. Like a red filter on them. Mozilla works fine. I'm assuming it has something to do with the flash update in Chromium? 

 Any suggestions on a fix or if I should bring this up another chain?

---

### Post by t2491tom on 2011-03-03
I'm having the same problem. I have been using HTML5 instead of Flash Player. You can use HTML5 instead by joining the beta at youtube.com/html5.

---

### Post by nslegacy163 on 2011-03-03
> **t2491tom said:**
> I'm having the same problem. I have been using HTML5 instead of Flash Player. You can use HTML5 instead by joining the beta at youtube.com/html5.

 I signed up (I'm assuming. I clicked the "join" link and it changed to a "leave" link), and restarted my browser (Chrome) and still get the red filter of death.

---

### Post by t2491tom on 2011-03-03
Not all youtube videos will work with HTML5. I am going to try downgrading my Flashplayer.

---

### Post by nslegacy163 on 2011-03-03
Yeah, I tried a couple. And I just watched an embedded youtube video in my RSS reader and it played fine. 

sigh.

---

### Post by nslegacy163 on 2011-03-03
> **t2491tom said:**
> Not all youtube videos will work with HTML5. I am going to try downgrading my Flashplayer.

Did downgrading work and what's the easiest/best way to roll flash back?

---

### Post by t2491tom on 2011-03-03
I have found a fix! Uninstall flashplugin-installer and then install flashplayer .deb from [http://get.adobe.com/flashplayer/?no_redirect](http://get.adobe.com/flashplayer/?no_redirect).

---

### Post by t2491tom on 2011-03-03
Just FYI uninstalling flashplugin-installer also uninstalls Boxee (of course you can reinstall it).

---

### Post by nslegacy163 on 2011-03-03
...what if I use Chrome and Flash is "already built in?" 

Will this uninstall and reinstall off adobe's site work with it?

---

### Post by t2491tom on 2011-03-03
It worked for me and I'm on Chromium. We appear to be having the same problem though so...

---

### Post by t2491tom on 2011-03-03
Okay the problem appears to be back for me. This is weird.

---

### Post by nslegacy163 on 2011-03-03
> **t2491tom said:**
> It worked for me and I'm on Chromium. We appear to be having the same problem though so...

It looked like that worked...I uninstalled the flashplugin and then cleared Chrome and restarted it and watched two videos: one I hadn't viewed previously and one I had. They both played with no redness but then I clicked on another and the redness came back. 

sigh x2.

---

### Post by t2491tom on 2011-03-03
I guess this problem is not fixable. They will probably fix it tomorrow. So I guess all we can do is wait.

---

### Post by nslegacy163 on 2011-03-03
> **t2491tom said:**
> I guess this problem is not fixable. They will probably fix it tomorrow. So I guess all we can do is wait.

](*,)

---

### Post by smithsmg on 2011-03-03
Got same problem on my 10.04 :(

---

### Post by gimspang on 2011-03-03
Solved! Ubuntu 10.10 64bit Desktop.
- Close Chromium
- Unistall flash (see previous posts)
- Open Firefox
- Try access youtube video
- Get an error message and a button to load plug-ins
- Install Gnash
- Close Firefox
- Open Chromium
- Access youtube videos
PS: Gnash has always worked better than Adobe's plugins for me.
Enjoy.

---

### Post by insm0d on 2011-03-03
I have 10.04 32 bit and had this problem yesterday too.  Just logged in about 10 minutes ago and there were security updates for firefox, pango, and xulrunner.  The updates haven't helped any.

I'm only having this red video problem with youtube.  Other flash video players work.  I'm just going to shoot youtube tech support an email and see if they know what's going on.

---

### Post by wonderart on 2011-03-03
I'm having the same problem...but after reinstall Chromium all fine :)

---

### Post by andypearce on 2011-03-03
Just discovered I have this problem too... even after all the updates. My BBC iplayer and Channel 4OD (UK) both work fine... youtube orangy/red on the flash but the thumbnails on youtube are fine....I am on the search for a solution....Ubuntu 10.4 Adobe flash player 10.2.152.27
A

---

### Post by MrEgg on 2011-03-03
Same problem here since this morning, on Lucid 32 bit. No problem on Maverick 64 bit.

The problem disappears if the PREF youtube cookie is erased. It comes back with the cookie, though.

Temporary workaround : erase the PREF cookie + block all youtube cookies.

YouTube videos will then play fine, but you won't be able to log into your account.

Egg

---

### Post by calder76 on 2011-03-03
Confirmed - removing PREF cookie removes pink layer. Unfortunately, it also blocks watching videos in full screen mode.

---

### Post by MrEgg on 2011-03-03
Yeah, you're right about full screen mode. You'll have to use the Desktop Zoom effect from Compiz, to sort of emulate full screen until this is resolved.

---

### Post by calder76 on 2011-03-03
Solution that works for me:

1. Uninstall current Flash plugin through Synaptic (package adobe-flashplugin or flashplugin-installer).
2. Download latest Adobe Flex 4.1 SDK from [http://opensource.adobe.com/wiki/display/flexsdk/download?build=4.1.0.16076&pkgtype=1](http://opensource.adobe.com/wiki/display/flexsdk/download?build=4.1.0.16076&pkgtype=1) (you have to check "I have read the License Agreement (...)" to get the download link).
3. Unzip flex_sdk_4.1.0.16076.zip, go to runtimes/player/10.1/lnx and find file libflashplayer.so.tar.gz.
4. Unpack the file with "tar xf libflashplayer.so.tar.gz" and you'll get the plugin libflashplayer.so.
5. Copy libflashplayer.so to /usr/lib/mozilla/plugins and restart the browser.

Enjoy it.

---

### Post by calder76 on 2011-03-03
The problem seems to affect all versions of Flash player 10.2, it does not affect 10.1 nor 10.0. The PREF cookie stores the version of your player and it probably helps Youtube to determine the stream to serve. The new versions of the streams, dedicated specifically to 10.2 seem to be broken somehow (or the Linux version of the plugin cannot handle them properly). This explains why the video works fine until the PREF cookie gets set by Youtube.
I noticed the problem to appear once a while on some of the videos just yesterday, and today I got all videos obviosuly lacking one of RGB channels. It seems that the problem is not related to Ubuntu updates, but to the changes YT probably has just introduced to their infrastructure.

---

### Post by Paddy Landau on 2011-03-03
I have this problem, too. It affects some, but not all, YouTube videos, in both Firefox and Chromium.

I'll wait a couple of days to see if it's fixed.

Do you know if anyone has reported this as a bug?

---

### Post by oracle2b on 2011-03-03
I hope this issue gets fixed in a update soon before I have to go mucking around an ugly hack.

---

### Post by unrater on 2011-03-03
I'm also with this problem. It happened **after last update**!

---

### Post by Neosano on 2011-03-03
Same problem, affects some videos only.

---

### Post by calder76 on 2011-03-03
Paddy, I don't know if anyone has reported it yet. Downgrading Flash to 10.1 (which I had to extract from Flex SDK, because Adobe does not provide versions earlier than 10.2 officially) worked for me, so I'm going to stick with it for now.
Lessons learned:
1. Don't upgrade Adobe software until you absolutely have to.
2. Steve Jobs was right, Flash is a crap ;)

---

### Post by unrater on 2011-03-03
For me the problem is only in the youtube.com domain!

The videos work like normally in other sites, like youtube.

I purged it, but did not worked :(

---

### Post by johntaylor1887 on 2011-03-03
I'm glad I havn't updated in a while. I won't be updating either, until this is fixed. Has anyone reported this bug?

---

### Post by komputes on 2011-03-03
Would those experiencing this problems please post if:
-It affects Firefox, Chromium or both
-The name of the flash package installed (and source if not from repos) - if no package, state manual install (flashplugin.so)
-Your settings in gstreamer-properties (Video > Default Output)
-Your video card make/model/PCI ID*/driver*

*PCI ID and driver can be obtained in the output of the following command:
```
lspci | grep -i VGA | awk '{print "sudo lspci -knn -s "$1}' | bash
```

---

### Post by knappster on 2011-03-03
for a temporary solution, just turn off and delete the cookies for youtube. you cant be signed in to your youtube account however. but deleting the cookies for youtube will work.

 ok it was working lol. now it doesnt play at all. are cookies needed to play youtube videos? yeah im a noob

---

### Post by nslegacy163 on 2011-03-03
> **johntaylor1887 said:**
> I'm glad I havn't updated in a while. I won't be updating either, until this is fixed. Has anyone reported this bug?

Where shall we all report this bug to? Youtube and/or Adobe?

---

### Post by nslegacy163 on 2011-03-03
> **komputes said:**
> Would those experiencing this problems please post if:
-It affects Firefox, Chromium or both
-The name of the flash package installed (and source if not from repos) - if no package, state manual install (flashplugin.so)
-Your settings in gstreamer-properties (Video > Default Output)
-Your video card make/model/PCI ID*/driver*

*PCI ID and driver can be obtained in the output of the following command:
```
lspci | grep -i VGA | awk '{print "sudo lspci -knn -s "$1}' | bash
```

Hi, 

 Yes it is on both Chromium (and Chrome, I have both) and Firefox. 
 My flash is from the repos/built into Chrome
 My output for the above code is:
 01:00.0 VGA compatible controller [0300]: ATI Technologies Inc R430 [Radeon X800 XL] (PCIe) [1002:554d]
	Subsystem: ATI Technologies Inc Device [1002:0302]
	Kernel driver in use: radeon
	Kernel modules: radeon

 Also, there is no red filter on embedded youtube videos. 
 Thanks!

---

### Post by Freezer52000 on 2011-03-03
> **komputes said:**
> Would those experiencing this problems please post if:
-It affects Firefox, Chromium or both
-The name of the flash package installed (and source if not from repos) - if no package, state manual install (flashplugin.so)
-Your settings in gstreamer-properties (Video > Default Output)
-Your video card make/model/PCI ID*/driver*

*PCI ID and driver can be obtained in the output of the following command:
```
lspci | grep -i VGA | awk '{print "sudo lspci -knn -s "$1}' | bash
```

- Affects both Chrome and Firefox
- Chrome: built-in flash [COLOR=#000000][FONT=Times New Roman][FONT=Arial]10.2.154; Firefox: [/FONT][/FONT][/COLOR]  libflashplayer.so 10.2 r152
- gstreamer default output: v4l2
- video card: Intel Corporation 82G33/G31 Express Integrated Graphics Controller [8086:29c2] (rev 10)
- Kernel driver in use: i915

---

### Post by Neosano on 2011-03-03
WORKAROUND:
those red videos usually have "Pop out" button right to the quality change drop down. Popped out video is normal.

---

### Post by iuno on 2011-03-03
> **Neosano said:**
> WORKAROUND:
those red videos usually have "Pop out" button right to the quality change drop down. Popped out video is normal.

yeah, that works... :KS

---

### Post by Ralph_de_Rijke on 2011-03-03
> **komputes said:**
> Would those experiencing this problems please post if:
-It affects Firefox, Chromium or both
-The name of the flash package installed (and source if not from repos) - if no package, state manual install (flashplugin.so)
-Your settings in gstreamer-properties (Video > Default Output)
-Your video card make/model/PCI ID*/driver*

*PCI ID and driver can be obtained in the output of the following command:
```
lspci | grep -i VGA | awk '{print "sudo lspci -knn -s "$1}' | bash
```


Yep, same problem here since yesterday's automatic software upgrade. Red cast (and sometimes two sets of images at different sizes) in embedded YouTube videos. Pop-out and non-YT Flash content works correctly, as described. In my case:
- Firefox 3.16.14, Chrome 9.0.597.107
- Flashplugin (using the Flash-Aid extension in Firefox)
- gstréamer-properties: Default Output = autodetect
- Intel Corp Mobile / 945GM/GMS, 943/940GML / 8086:27a2 [rev 03] / i915

You'd think developers would check FB first thing... :-)

---

### Post by t2491tom on 2011-03-03
I reported the problem to youtube. The latest versions of VLC allow you to play youtube by simply adding the video URL.

---

### Post by insm0d on 2011-03-03
I'm hardly an expert at anything but it seems to me the cyan channel is twice as big as the normal sized magenta channel and the green channel doesn't appear at all.

---

### Post by Ants_A on 2011-03-03
> **komputes said:**
> Would those experiencing this problems please post if:
-It affects Firefox, Chromium or both
-The name of the flash package installed (and source if not from repos) - if no package, state manual install (flashplugin.so)
-Your settings in gstreamer-properties (Video > Default Output)
-Your video card make/model/PCI ID*/driver*

*PCI ID and driver can be obtained in the output of the following command:
```
lspci | grep -i VGA | awk '{print "sudo lspci -knn -s "$1}' | bash
```
- Affects both. On both if the PREF cookie is deleted, then the first video plays correctly, but if it gets set subsequent pageloads play the video with a red cast.
- Package: flashplugin-installer           
  Version: 10.2.152.27ubuntu0.10.10.1
- Whatever the default is on Kubuntu 10.10.
- Video card info:
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M24GL [Mobility FireGL V3200] [1002:3154] (rev 80)
        Subsystem: IBM Device [1014:0570]
        Kernel driver in use: radeon
        Kernel modules: radeon, radeonfb

---

### Post by ironhoof on 2011-03-04
Yea, me too both players after update, all red with a zoomed in purplish video playing in the corner, looks like the video is divided into its RGB components.

However since I have two boots of Linux on this machine. I booted into my second boot (Kubuntu) without the update, and it played 1 video fine, and then it all changed to RED. This might be a youtube issue...

---

### Post by andypearce on 2011-03-04
Firefox only
Ubuntu 10.4 32bit
flash Adobe 10.2.152.27
video output autodetect
I do not know what soundcard
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RC410 [Radeon Xpress 200M] [1002:5a62]
	Kernel driver in use: radeon
	Kernel modules: radeonfb, radeon

---

### Post by sles on 2011-03-04
> **knappster said:**
> for a temporary solution, just turn off and delete the cookies for youtube. 

thank you, it helps for some time.
btw, in my case youtube video doesn't work at all because of plugin crash.
deleting cookies helps, but not forever :-(

---

### Post by MrEgg on 2011-03-04
Affects both FF & Chromium; YT video expand or fullscreen also affected.
Affects : only YT videos.

Lucid 32 bit
libflashplayer 10.2r152
FF 3.6.14
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
	Kernel driver in use: i915
	Kernel modules: i915

---

### Post by MsKK on 2011-03-04
-Chrome only in Ubuntu 10.4 32bit
-adobe-flashplugin version 10.2.152.27-0lucid1
-video default output autodetect
-Video card info
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
	Kernel driver in use: i915
	Kernel modules: i915

The redness filter of death (RFOD) goes away when I click on the popout option in youtube.

---

### Post by Gaygerbil on 2011-03-04
There's a couple of solutions to this for the meantime. Hopefully this gets fixed. Leave it Adobe to screw Linux users once again lol.

First is deleting and blocking cookies.

Second is favoriting vids and viewing them from your channel, you can't see them in fullscreen though. But you can zoom in on those vids to reproduce a similar effect. 

Third is to use this:
[http://www.youtube.com/html5](http://www.youtube.com/html5)

Fullscreen doesn't work with this either but still.

Hopefully it gets fixed, I use Youtube a lot and this is bothering me, I was just starting to really enjoy the new Flashplayer too, it loads HD vids so much faster and plays em' way smoother than before.

---

### Post by MrEgg on 2011-03-04
System NOT affected :

Ubuntu 10.10 64bits
Firefox 3.6.14 (haven't tried Chromium)
Works fine in all modes (embedded, expanded, full screen)
flashplugin64-installer : 10.3.162.29-0ubuntu0~sevenmachines2
from : ppa:sevenmachines/flash

00:02.0 VGA compatible controller [0300]: Intel Corporation Sandy Bridge Integrated Graphics Controller [8086:0102] (rev 09)
	Subsystem: ASUSTeK Computer Inc. Device [1043:844d]
	Kernel driver in use: i915
	Kernel modules: i915

---

### Post by weirdguille on 2011-03-04
I fixed mine by downgrading flashplugin-installer to 10.1

Just run
```
sudo apt-get remove flashplugin-installer
```

Then download either
```
http://gt.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.85.3ubuntu1_i386.deb
```
or
```
http://gt.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.85.3ubuntu1_amd64.deb
```
depending on your system, and install the .deb.

Then lock the flashplugin-installer version in synaptic (it will stop it from updating). Unlock it once we know 10.2 is bug-free.

Now, I use chromium-browser (daily ppa), and there is a little inconvenience: it'll always ask for the plugin to be updated. So you just need to click on "run this time", and it'll work normally. But the next time you open another youtube video, it'll ask for the update again.

Ah, by the way, this proves that it's not a youtube issue (I thought it had to do with the new layout, but apparently it doesn't), but a flashplugin 10.2 issue.

---

### Post by Paddy Landau on 2011-03-04
> **Gaygerbil said:**
>  use this:
[http://www.youtube.com/html5](http://www.youtube.com/html5)
Not for Firefox version 3, though.


> **Neosano said:**
> "Pop out" button
Ooh, clever! Thanks, that works.


> **komputes said:**
> Would those experiencing this problems please post...
* Affects:* Both Firefox (3.6.14) and Chromium (9.0.597.107 (75357) Ubuntu 10.04)
* Flash from repos:* 10.2.152.27ubuntu10.04.1
* gstreamer-properties:* Video for Linux 2 (v4l2)
* Video card:*
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
    Kernel driver in use: i915
    Kernel modules: i915


I wonder whether there is a difference between people using **32-bit** and **64-bit**? I have 64-bit Ubuntu installed.

---

### Post by MrEgg on 2011-03-04
> **Paddy Landau said:**
> 
I wonder whether there is a difference between people using **32-bit** and **64-bit**? I have 64-bit Ubuntu installed.

You bet! I'm not affected on my Maverick 64 bit. See post #49.

Egg

---

### Post by Paddy Landau on 2011-03-04
> **MrEgg said:**
> You bet! I'm not affected on my Maverick 64 bit. See post #49.
Oh, that's interesting. My 64-bit is affected.

However, I notice you say you have flashplugin64-installer. I have flashplugin-installer.

I wonder, as an experiment, what would happen if I uninstall flashplugin-installer and install flashplugin64-installer. The only thing is, I don't know where to find flashplugin64-installer.

---

### Post by MrEgg on 2011-03-04
You have to get it from the ppa I mentioned in post #49

---

### Post by saalikr on 2011-03-04
> **weirdguille said:**
> I fixed mine by downgrading flashplugin-installer to 10.1

Just run
```
sudo apt-get remove flashplugin-installer
```

Then download either
```
http://gt.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.85.3ubuntu1_i386.deb
```
or
```
http://gt.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.85.3ubuntu1_amd64.deb
```
depending on your system, and install the .deb.

Then lock the flashplugin-installer version in synaptic (it will stop it from updating). Unlock it once we know 10.2 is bug-free.

Now, I use chromium-browser (daily ppa), and there is a little inconvenience: it'll always ask for the plugin to be updated. So you just need to click on "run this time", and it'll work normally. But the next time you open another youtube video, it'll ask for the update again.

Ah, by the way, this proves that it's not a youtube issue (I thought it had to do with the new layout, but apparently it doesn't), but a flashplugin 10.2 issue.

Thanks weirdguille. I followed your advice and now it works perfectly.
I am so glad I am a Linux user with knowledge and assistance like this so readily available.
Keep up the good work all.

---

### Post by Katten Jansson on 2011-03-04
[B][SIZE=3]How to fix this![/SIZE]

[/B]*This procedure worked for me. The reasons given why it works is speculations.*Youtube use faulty/outdated preferences for showing video, it get those from cookies that the site have set previously. Youtube seem to use some kind of "super cookie" (it use reduntant places to store information in order to make it harder for you to delete it), so you have to clean out both flash cookies and web-browser cookies and cache, otherwise youtube will restore the old preference after some time and  go back to displaying pink videos.
[B]
Close all Youtube, Google, et.c. affiliated pages in the browser(s).[/B]
[B]
[SIZE=1]Remove flash cookies
[/SIZE][/B][SIZE=1]Use a tool like better privacy or do it manually.

[B]Remove browser cookies and clear cache
[/B]Do this for all browsers that you use (or it will reset the Flash preferences shared by all browsers).


**Update: **I found a Wikipedia-article describing these kind of cookies:
[/SIZE][http://en.wikipedia.org/wiki/Evercookie](http://en.wikipedia.org/wiki/Evercookie)

---

### Post by nilarimogard on 2011-03-04
I've made a list of all the possible fixes and how to apply them: [Fix red YouTube videos bug]("http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html"). 

I hope it helps...

---

### Post by Paddy Landau on 2011-03-04
> **MrEgg said:**
> You have to get it from the ppa I mentioned in post #49
Thanks. I struggled to find out how to do that, but I have found out now:
```
sudo apt-add-repository ppa:sevenmachines/flash
```I uninstalled flashplugin-installer, installed flashplugin64-installer (version 10.3.169.29-0ubuntu0~sevenmachines2), installed all updates, and rebooted just in case. Unfortunately, it has not fixed the problem. :(

---

### Post by MrEgg on 2011-03-04
> **Paddy Landau said:**
> I uninstalled flashplugin-installer, installed flashplugin64-installer (version 10.3.169.29-0ubuntu0~sevenmachines2), installed all updates, and rebooted just in case. Unfortunately, it has not fixed the problem. :(

Since your system was originally affected by the bug, maybe you can try clearing out all YouTube cookies and all cache again.

---

### Post by Paddy Landau on 2011-03-04
> **MrEgg said:**
> Since your system was originally affected by the bug, maybe you can try clearing out all YouTube cookies and all cache again.
I did that. It worked -- until I logged in again! I'll use the pop-out method until this is fixed.

---

### Post by Dr Heelhook on 2011-03-04
I am having the exact same problem as well. Pink tinted Youtube. My  flash also crashes quite often, especially in connection to Youtube. 

I have Maverick Meerkat, Firefox and Flash version 10,2,152,27. I also cannot access settings.

BTW, thanks for the popout tip.

---

### Post by amanetta on 2011-03-04
I haven't red youtube videos but if a video of youtube is playing in firefox it  appears on every board of firefox...

I post a link to give a better explanation....

[http://img846.imageshack.us/i/schermata2.png/](http://img846.imageshack.us/i/schermata2.png/)

thank u

---

### Post by Kupfer on 2011-03-04
Thanks to user Liakoni from the Linux Mint Forums I can report a solution this problem. You need to disable hardware acceleration in the flash settings.

Step 1. Right click on a flash content (I went to this flash site [http://moodstream.gettyimages.com/](http://moodstream.gettyimages.com/) and simply right clicked on the page)
Step 2. Choose the entry "Settings..."
Step 3. Unclick entry "Enable hardware acceleration"
Step 4. Click "Close"

For me this fixed the issue on all of my browesers (Firefox, Chrome stable, Chromium). No more thick red filter on youtube videos.

Thanks again to Liakoni for discovering this solution.

---

### Post by Ralph_de_Rijke on 2011-03-04
> **Kupfer said:**
> Thanks to user Liakoni from the Linux Mint Forums I can report a solution this problem. You need to disable hardware acceleration in the flash settings.

Step 1. Right click on a flash content (I went to this flash site [http://moodstream.gettyimages.com/](http://moodstream.gettyimages.com/) and simply right clicked on the page)
Step 2. Choose the entry "Settings..."
Step 3. Unclick entry "Enable hardware acceleration"
Step 4. Click "Close"

For me this fixed the issue on all of my browesers (Firefox, Chrome stable, Chromium). No more thick red filter on youtube videos.

Thanks again to Liakoni for discovering this solution.


Worked for me. I'd call it a workaround rather than a solution, but thanks anyway. :-)

---

### Post by Col-1023 on 2011-03-04
THANK YOU VERY MUCH Kupfer.

Your suggestion to turn off hardware acceleration has worked for me, I really appreciate it.

---

### Post by Paddy Landau on 2011-03-04
> **Kupfer said:**
> You need to disable hardware acceleration in the flash settings.
Thank you, works for me!

---

### Post by amanetta on 2011-03-04
work for me too...

---

### Post by weirdguille on 2011-03-04
> **Kupfer said:**
> Thanks to user Liakoni from the Linux Mint Forums I can report a solution this problem. You need to disable hardware acceleration in the flash settings.

Step 1. Right click on a flash content (I went to this flash site [http://moodstream.gettyimages.com/](http://moodstream.gettyimages.com/) and simply right clicked on the page)
Step 2. Choose the entry "Settings..."
Step 3. Unclick entry "Enable hardware acceleration"
Step 4. Click "Close"

For me this fixed the issue on all of my browesers (Firefox, Chrome stable, Chromium). No more thick red filter on youtube videos.

Thanks again to Liakoni for discovering this solution.
Worked for me, and it's more convenient than the workaround I posted (no requests to update all the time).

Thanks.

---

### Post by logruszed on 2011-03-04
Thanks! It worked a treat.



> **Kupfer said:**
> Thanks to user Liakoni from the Linux Mint Forums I can report a solution this problem. You need to disable hardware acceleration in the flash settings.

Step 1. Right click on a flash content (I went to this flash site [http://moodstream.gettyimages.com/](http://moodstream.gettyimages.com/) and simply right clicked on the page)
Step 2. Choose the entry "Settings..."
Step 3. Unclick entry "Enable hardware acceleration"
Step 4. Click "Close"

For me this fixed the issue on all of my browesers (Firefox, Chrome stable, Chromium). No more thick red filter on youtube videos.

Thanks again to Liakoni for discovering this solution.

---

### Post by [censored] on 2011-03-04
> **calder76 said:**
> Solution that works for me:

1. Uninstall current Flash plugin through Synaptic (package adobe-flashplugin or flashplugin-installer).
2. Download latest Adobe Flex 4.1 SDK from [http://opensource.adobe.com/wiki/display/flexsdk/download?build=4.1.0.16076&pkgtype=1](http://opensource.adobe.com/wiki/display/flexsdk/download?build=4.1.0.16076&pkgtype=1) (you have to check "I have read the License Agreement (...)" to get the download link).
3. Unzip flex_sdk_4.1.0.16076.zip, go to runtimes/player/10.1/lnx and find file libflashplayer.so.tar.gz.
4. Unpack the file with "tar xf libflashplayer.so.tar.gz" and you'll get the plugin libflashplayer.so.
5. Copy libflashplayer.so to /usr/lib/mozilla/plugins and restart the browser.

Enjoy it.

Worked for Calder. Thanks!

---

### Post by Paddy Landau on 2011-03-04
I have reported this as a bug:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/729307](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/729307)

If it affects you, please go there and vote for it (the green text on the left almost at the top).

Thank you to David Bensimon, who has been helping me report the bug and who will forward it to Adobe.

---

### Post by bagy on 2011-03-04
I can't disable hardware acceleration -.-

---

### Post by donut123 on 2011-03-04
> **nslegacy163 said:**
> After the recent update my OS went through requiring a restart, all the videos I play on youtube.com from Chrome or Chromium are red. Like a red filter on them. Mozilla works fine. I'm assuming it has something to do with the flash update in Chromium? 

 Any suggestions on a fix or if I should bring this up another chain?



Hello...try this
 [http://www.ultimateeditionoz.com/forum/viewtopic.php?f=166&t=1526](http://www.ultimateeditionoz.com/forum/viewtopic.php?f=166&t=1526)

---

### Post by jfloydb on 2011-03-04
I've read many, but not all, of the posts on this thread. Forgive me if this answer has been covered. The fix, for me, was to go to the Synaptic Package Manager, choose the flashplugin-installer 10.2, goto the Package menu, click Force Version..., and "downgrade" to Flash 10.0; after which, I clicked Lock Version, so it will not "upgrade" with the next updates. That's it; everything is working fine.

I know many Windows users who have never upgraded their Flash plugin, and they never seem to have any problems. For all they (or I) know, they are using Flash version 1, or 5, or whatever. So I'm not concerned about using an older Flash plugin. I might "upgrade" when the current problems are fixed.

---

### Post by bou3lam on 2011-03-04
> **t2491tom said:**
> It worked for me and I'm on Chromium. We appear to be having the same problem though so...
didnt helped :(

---

### Post by Roush 427r on 2011-03-05
On UNE 10.04 x86, Same problem on Firefox & chromium.

---

### Post by Marzata on 2011-03-05
-

---

### Post by Marzata on 2011-03-05
> **Neosano said:**
> WORKAROUND:
those red videos usually have "Pop out" button right to the quality change drop down. Popped out video is normal.
Thank you!

---

### Post by MrEgg on 2011-03-05
> **Kupfer said:**
> Thanks to user Liakoni from the Linux Mint Forums I can report a solution this problem. You need to disable hardware acceleration in the flash settings.

Step 1. Right click on a flash content (I went to this flash site [http://moodstream.gettyimages.com/](http://moodstream.gettyimages.com/) and simply right clicked on the page)
Step 2. Choose the entry "Settings..."
Step 3. Unclick entry "Enable hardware acceleration"
Step 4. Click "Close"

For me this fixed the issue on all of my browesers (Firefox, Chrome stable, Chromium). No more thick red filter on youtube videos.

Thanks again to Liakoni for discovering this solution.

Excellent, works for me too! Thanks for figuring this workaround out!

---

### Post by zipizap on 2011-03-05
> **Kupfer said:**
> Thanks to user Liakoni from the Linux Mint Forums  I can report a solution this problem. You need to disable hardware  acceleration in the flash settings.

Step 1. Right click on a flash content (I went to this flash site [http://moodstream.gettyimages.com/](http://moodstream.gettyimages.com/) and simply right clicked on the page)
Step 2. Choose the entry "Settings..."
Step 3. Unclick entry "Enable hardware acceleration"
Step 4. Click "Close"

For me this fixed the issue on all of my browesers (Firefox, Chrome  stable, Chromium). No more thick red filter on youtube videos.

Thanks again to Liakoni for discovering this solution.
  
It fixed it for me too - I'm using Ubuntu 10.04 with Firefox and Chrome
Thanks Kupfer for the share, and shame on adobe...

---

### Post by bellial on 2011-03-05
I'm having a problem, it started happening after recent updates on both firefox and chromium and the OS itself, whenever I start a youtube video on firefox, the first audio second loops for about 3 seconds and my computer restarts. It was happening on chromium too, but then I cleared the cache and it played fine. On FF even clearing the cache doesn't work. Other flash things like facebook games work fine. Can I fix this?
By the way, I'm using Ubuntu 10.04.
According to this site, [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)
I'm using flash version 10,2,152,27 installed.

---

### Post by Paddy Landau on 2011-03-05
> **bellial said:**
> I'm having a problem...
Did you [disable hardware acceleration]("http://ubuntuforums.org/showthread.php?p=10520930#post10520930")?

---

### Post by bagy on 2011-03-05
I can't uncheck "enable hardware acc".

---

### Post by bellial on 2011-03-05
> **Paddy Landau said:**
> Did you [disable hardware acceleration]("http://ubuntuforums.org/showthread.php?p=10520930#post10520930")?

I did, but nothing.:(

---

### Post by gradinaruvasile on 2011-03-05
The vanilla Adobe flash is buggy as hell (version 10.2.152.27). It is supposed to have hardware decoding (Stage Video) implemented for the newer nvidia/ati cards (with the proprietary driver) but it seems it doesnt work all the time and crashes as hell.

I use the Chrome's included flash player (version 10.2.r154) in all my browsers (mainly Opera). This works fine (the hw decoding is disabled for good though).

[http://www.nvnews.net/vbulletin/showthread.php?t=148409&page=7](http://www.nvnews.net/vbulletin/showthread.php?t=148409&page=7)

---

### Post by bellial on 2011-03-05
> **gradinaruvasile said:**
> The vanilla Adobe flash is buggy as hell (version 10.2.152.27). It is supposed to have hardware decoding (Stage Video) implemented for the newer nvidia/ati cards (with the proprietary driver) but it seems it doesnt work all the time and crashes as hell.

I use the Chrome's included flash player (version 10.2.r154) in all my browsers (mainly Opera). This works fine (the hw decoding is disabled for good though).

[http://www.nvnews.net/vbulletin/showthread.php?t=148409&page=7](http://www.nvnews.net/vbulletin/showthread.php?t=148409&page=7)

Where can I download it? I don't really like the way chromium deals with flash games, it's too laggy.

---

### Post by t2491tom on 2011-03-05
Here are a bunch of fixes from webupd8: [http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html#more](http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html#more)

---

### Post by newbuntuxx on 2011-03-05
> **weirdguille said:**
> I fixed mine by downgrading flashplugin-installer to 10.1

Just run
```
sudo apt-get remove flashplugin-installer
```

Then download either
```
http://gt.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.85.3ubuntu1_i386.deb
```
or
```
http://gt.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.85.3ubuntu1_amd64.deb
```
depending on your system, and install the .deb.

Then lock the flashplugin-installer version in synaptic (it will stop it from updating). Unlock it once we know 10.2 is bug-free.

Now, I use chromium-browser (daily ppa), and there is a little inconvenience: it'll always ask for the plugin to be updated. So you just need to click on "run this time", and it'll work normally. But the next time you open another youtube video, it'll ask for the update again.

Ah, by the way, this proves that it's not a youtube issue (I thought it had to do with the new layout, but apparently it doesn't), but a flashplugin 10.2 issue.

Worked! But I guess the problem is with hardware acceleration. I read that part after following the directions in your post. 

Thanks.

---

### Post by cntmn8td2006 on 2011-03-05
> **Paddy Landau said:**
> Did you [disable hardware acceleration]("http://ubuntuforums.org/showthread.php?p=10520930#post10520930")?

Thank you, your solution worked just fine.

---

### Post by MsKK on 2011-03-05
> **Kupfer said:**
> Thanks to user Liakoni from the Linux Mint Forums I can report a solution this problem. You need to disable hardware acceleration in the flash settings.

Step 1. Right click on a flash content (I went to this flash site [http://moodstream.gettyimages.com/](http://moodstream.gettyimages.com/) and simply right clicked on the page)
Step 2. Choose the entry "Settings..."
Step 3. Unclick entry "Enable hardware acceleration"
Step 4. Click "Close"

For me this fixed the issue on all of my browesers (Firefox, Chrome stable, Chromium). No more thick red filter on youtube videos.

Thanks again to Liakoni for discovering this solution.

This worked for me, thanks ;) I wonder what "side-effects" are there for this workaround... anyone?

---

### Post by mannyweb.ca on 2011-03-06
> **weirdguille said:**
> I fixed mine by downgrading flashplugin-installer to 10.1

Just run
```
sudo apt-get remove flashplugin-installer
```Then download either
```
http://gt.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.85.3ubuntu1_i386.deb
```or
```
http://gt.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.85.3ubuntu1_amd64.deb
```depending on your system, and install the .deb.

Then lock the flashplugin-installer version in synaptic (it will stop it from updating). Unlock it once we know 10.2 is bug-free.

Now, I use chromium-browser (daily ppa), and there is a little inconvenience: it'll always ask for the plugin to be updated. So you just need to click on "run this time", and it'll work normally. But the next time you open another youtube video, it'll ask for the update again.

Ah, by the way, this proves that it's not a youtube issue (I thought it had to do with the new layout, but apparently it doesn't), but a flashplugin 10.2 issue.

This worked like a charm even got my facebook photo uploader working.

Thanks a million! :D

---

### Post by dooper on 2011-03-06
[http://gt.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.85.3ubuntu1_amd64.deb](http://gt.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.85.3ubuntu1_amd64.deb)

reprots no such file ??

---

### Post by buckyb on 2011-03-06
I recently updated some packages, which may have included flash, and now youtube doesn't work properly. I tried playing HD flash videos in other websites, and they all seem to work fine.

 Some of the problems I've been having include: Video plays in Black and White, Progress Bar is choppy, freezes even though the video is playing, and sometimes when I maximize to fullscreen the video goes black, but you continue to hear it playing. If I minimize the video, it goes back to normal. 

The problem occurs in both Chrome and Firefox, and I'm using **Fedora 14. **

I've gone through several workarounds/solutions none of them work to my satisfaction:
1. Disable Hardware Acceleration: Video Freezes when I go to fullscreen
2. Uninstall most recent flashplugin and install an older version i.e. 10.1: Won't work for me because I primarily use Chrome
3. Use the Pop-Out Option: Works perfectly even in full screen for the first few seconds but then flash crashes in both Chrome and Firefox.
4. Uninstall flash and use gnash: Wont work for Chrome
5: Delete cookies and restart browser: Nada

The best workaround I've found so far is either zoom with compiz or vlc network stream, neither of which is as convenient as double clicking to go to fullscreen. 

Anyone have any decent solutions? Maybe a VLC extension for chrome....mmmm VLC extension in Chrome, now that's a thought to salivate over.

---

### Post by beew on 2011-03-06
The best solution would be to either use the flashvideoreplacer plugin for Firefox or install minitube 1.4 to watch Youtube. That way you don't need flash at all.

---

### Post by Paddy Landau on 2011-03-06
> **MsKK said:**
> I wonder what "side-effects" are there for this workaround... anyone?
I have found that videos sometimes pause briefly. Otherwise, none.

---

### Post by mfratus2001 on 2011-03-06
I've been experiencing this for a while, but it even crashes with embedded video.

You have to install an older version, but it conflicts with your current install, so in terminal, say:

sudo apt-get remove adobe-flashplugin

Then install the version you can download from here:

[http://gt.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.85.3ubuntu1_i386.deb](http://gt.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.85.3ubuntu1_i386.deb)

Thanks, weirdguille, for the links.
Works like it used to.

---

### Post by beew on 2011-03-06
> **mfratus2001 said:**
> I've been experiencing this for a while, but it even crashes with embedded video.

You have to install an older version, but it conflicts with your current install, so in terminal, say:

sudo apt-get remove adobe-flashplugin

Then install the version you can download from here:

[http://gt.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.85.3ubuntu1_i386.deb](http://gt.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.85.3ubuntu1_i386.deb)

Thanks, weirdguille, for the links.
Works like it used to.

Why would you rather go through the troubles to downgrade flash than to use flash alternatives (with better results even if flash works)? Since Youtube appears to be the only problem  it can be easily handled by the alternatives I suggested.

---

### Post by DalaiDakkar on 2011-03-06
I have a [Radeon X1200 Series] on my laptop, and started suffering red videos after last update of ubuntu 9.10,  I tried the fix suggested on another post and it worked for me. go to [http://moodstream.gettyimages.com/](http://moodstream.gettyimages.com/)   then right click the flash animation and click settings from the pop up menu and look for the enable hardware acceleration and disable it, refresh youtube page and works fine now :)

---

### Post by YodaJones on 2011-03-07
I am also affected with this problem.
I have noticed that if I am playing a youtube video with the red tint and I click the browser refresh I get the crash error "The Adobe Flash plugin has crashed" send crash report.  After sending the report and refresing the video will again play WITH the red tint.  If I click refresh the flash player will again crash.
This happens every single time and is repeatable.  Every other refresh will crash the flash player.

Has anyone else noticed that it crashes gmail somehow also?  Why does gmail use flash?

-------------------

Would those experiencing this problems please post if:
-It affects Firefox, Chromium or both

= BOTH Google Chrome 9.0.597.107 and Firefox 3.6.14

-The name of the flash package installed (and source if not from repos) - if no package, state manual install (flashplugin.so)

= Unsure

-Your settings in gstreamer-properties (Video > Default Output)

Default Output
Plugin: Autodetect
Device: greyed out
Pipeline: Greyed out

Default Input
Plugin: Video for Linux 2 (v4|2)
Device: Default
Pipeline: Greyed out

-Your video card make/model/PCI ID*/driver*

= Unsure

*PCI ID and driver can be obtained in the output of the following command:

OUTPUT:

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)] [1002:5b60]
	Kernel driver in use: radeon
	Kernel modules: radeonfb, radeon

---

### Post by Nikola Georgiev on 2011-03-07
Yeah, and gogle translator too.
Hope they fix it soon.


Thanks about the Disable Hardware Acceleration thing, it worked, but I think it just treats the symptom.

---

### Post by markthekdeguy on 2011-03-07
In Firefox there is a fun little plugin (add-ons) called FlashVideoReplacer
which forces Youtube videos to play in a proper media player. VLC, Kplayer, KMPlayer, Smplayer Kaffeine, Xine, Mplayer, Totem Dragonplayer or whatever. all work, but " FlashVideoReplacer " seems a little flaky on my system so far. i even uninstalled Flash to test, and Youtube was sweet.i prefer it to Flash now.

---

### Post by Orographic on 2011-03-08
This is why I love Ubuntu and the forums here; so many good heads looking at solutions. :-)

I have a related problem and am using Flash 10.2.152.27. In Ubuntu 10.10 32 bit, I can view full screen fine in YouTube but when I select another YouTube video in small screen with the videos on the right, I get a message that says, 'Adobe Flash Player has crashed please reload' and all works fine after I reload. I can't select the settings at all via right mouse click in YouTube but if I go to iView website, I can select to 'uncheck hardware acceleration' option but then YouTube wont leave fullscreen and I have to do a Alt-F12 then ctrl-alt-del to restart.

This problem is only occuring in Forefox 3.6.14 for me since the last Flash update and it doesn't seem to be occuring in Chromium in standard or fullscreen. I got my flash via installing 'Ubuntu Restricted Extras' and it has been working perfectly until the last update.

I've just found that Adobe Settings page and will look at that and fiddle around with a few things. I also make clonezilla images of my setup so I can easily restore an earlier version of 10.10 or just downgrade Flash and lock it.

Just trying to delete all Flash cookies via their online settings manager and deleted my own cache, cookies etc in Firefox and Chromium but the Flash Player in Firefox still crashed but works fine on reload in small and fullscreen. Chromium seems to work perfectly for me.

System: Core i3 540 with Gigabyte H55-USB3 motherboard and on-chip HD graphics.

---

### Post by Paddy Landau on 2011-03-08
> **Nikola Georgiev said:**
> Thanks about the Disable Hardware Acceleration thing, it worked, but I think it just treats the symptom.
Correct. However, Canonical has confirmed this as a "High" rated [bug]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/729307"), and Canonical has passed the bug to Adobe (who is responsible for it).

---

### Post by Motorhead Kaze on 2011-03-08
THANKS!

I am so glad I decided to come check the forum to see if anyone else had this problem!

```
sudo apt-get remove adobe-flashplugin
```

Then install the version you can download from here:
[http://gt.archive.ubuntu.com/ubuntu/...untu1_i386.deb]("http://gt.archive.ubuntu.com/ubuntu/...untu1_i386.deb")

Thanks everybody who posted & reposted these links!

PS that pop-out idea on YouTube was spiffy too.

---

### Post by Paddy Landau on 2011-03-08
> **Motorhead Kaze said:**
> PS that pop-out idea on YouTube was spiffy too.
The easiest method is to [disable hardware acceleration]("http://ubuntuforums.org/showthread.php?p=10520930#post10520930"), although several people have used Firefox's [flashvideoreplacer plugin]("https://addons.mozilla.org/en-us/firefox/addon/flashvideoreplacer/").

---

### Post by Dr Heelhook on 2011-03-08
I was starting to think I was being punished for watching too much YouYube, then I switched to Flash 10.1 and now it's all dandy (HELLZ yeah!).

---

### Post by jaci87 on 2011-03-08
You can also try with the 10.3 beta version of adobe flash player: [http://labs.adobe.com/downloads/flashplayer10-3.html]("http://labs.adobe.com/downloads/flashplayer10-3.html")
I've installed and it seems to work fine. :)

---

### Post by Orographic on 2011-03-08
> **Paddy Landau said:**
> The easiest method is to [disable hardware acceleration]("http://ubuntuforums.org/showthread.php?p=10520930#post10520930"), although several people have used Firefox's [flashvideoreplacer plugin]("https://addons.mozilla.org/en-us/firefox/addon/flashvideoreplacer/").

Doing that makes my system crash. I'm using a core i3 540 with on-chip graphics and the H-55 Gigabyte motherboard.

I've had a look in Natty Alpha 3 (11.04) and it still crashed Flash in YouTube but its easily recoverable on my system via a reload. I might just wait for an update to the newer Flash when it comes out.

Html5 runs quite well on my system also, both in Natty and 10.10.

Edit: I've just tried about fifty YouTube videos on Chromium and not one of them crashed Flash, so that is interesting.

---

### Post by relgames on 2011-03-09
I think I have found another workaround. It's for Chrome but there definitely should be similar extension for FireFox.

1. Install [Edit This Cookie]("https://chrome.google.com/extensions/detail/fngmhnnpilhplaeedifhccceomclgfbg") extension
When installed, a new icon appears near the Settings icon

2. Go to YouTube, open any video. Press F5 several times (to be sure cookies are loaded)

3. Click Edit This Cookie icon. Locate PREF cookie. It contains something like "f1=50000000&fv=10.2.154"

4. Change it's value to "ee" (doesn't really matter, but I used "ee").
Click Submit Cookie Changes.

5. Locate PREF cookie again. Click "Set as readonly"

That's it, if you load any Youtube video it should work. At least it works for me ;)

You can verify your changes by going to "Edit This Cookie" -> Preferences. If you did everything right, you should see:
```
  Domain: .youtube.com      Name: PREF      Value: ee
```

You can undo your changes by going to "Edit This Cookie" icon -> Preferences and deleting all cookies listed here.

---

### Post by Paddy Landau on 2011-03-10
Google support thread:
[http://www.google.com/support/forum/p/youtube/thread?tid=24c59369d9181cf7](http://www.google.com/support/forum/p/youtube/thread?tid=24c59369d9181cf7)

---

### Post by attila82 on 2011-03-10
Great!!!

---

### Post by libssd on 2011-03-11
Thank goodness for the forum search function, which precluded my opening a new thread on this. I first noticed the "red" problem on Youtube last night. Oddly, it wasn't 100% consistent; links to Youtube videos from other sites seemed to play with full color, while videos opened in Youtube usually (but not always) were monochrome red. 

My first hypothesis was that since I have extensions synced for Chrome browser, the recent Cr-48 Chrome OS update changed Flash when I ran Chrome browser on my Ubuntu netbook, so I disabled syncing of extensions in Chrome, and restored from backup. Video is now playing in technicolor, and I am applying all Ubuntu updates since my last backup to see if the problem returns.

Now I have to go back and read through this thread from the beginning. There is nothing like an active and knowledgeable community of users.

**Update:** I started reading this thread from the first post, then realized it might be more productive to start from the last. ;) 

I just disabled hardware acceleration pref for Flash, which has restored full color Youtube videos. I'm surprised that this problem has been around for at least a week, without being resolved by the Adobe/Google/Linux community (disabling hardware acceleration just being a work-around).

---

### Post by lovinglinux on 2011-03-13
> **markthekdeguy said:**
> In Firefox there is a fun little plugin (add-ons) called FlashVideoReplacer
which forces Youtube videos to play in a proper media player. VLC, Kplayer, KMPlayer, Smplayer Kaffeine, Xine, Mplayer, Totem Dragonplayer or whatever. all work, but " FlashVideoReplacer " seems a little flaky on my system so far. i even uninstalled Flash to test, and Youtube was sweet.i prefer it to Flash now.

I have released version 2.1.0, which has new cool features and improvements.

[http://www.webgapps.org/addons/flashvideoreplacer](http://www.webgapps.org/addons/flashvideoreplacer)

It works best with Firefox 4. I had to reduce the download link results in Firefox 3.x when viewing YouTube, because of performance issues. But it is still a lot better than flash.

The extension also has the ability to automatically redirect to webm page if you are using Firefox 4, so you can watch without any plugin. I prefer to use gecko-mediaplayer than webm tho.

---

### Post by Paddy Landau on 2011-03-13
Are you people still getting this problem? I've removed all workarounds (which, in my case, was simply re-enabling hardware acceleration) and it works.

Either YouTube has fixed whatever needed fixing, or I'm lucky today.

---

### Post by vanadium on 2011-03-13
Problem is still there.

---

### Post by JoeloRoss on 2011-03-13
> **libssd said:**
> Thank goodness for the forum search function, which precluded my opening a new thread on this. I first noticed the "red" problem on Youtube last night. Oddly, it wasn't 100% consistent; links to Youtube videos from other sites seemed to play with full color, while videos opened in Youtube usually (but not always) were monochrome red. 

My first hypothesis was that since I have extensions synced for Chrome browser, the recent Cr-48 Chrome OS update changed Flash when I ran Chrome browser on my Ubuntu netbook, so I disabled syncing of extensions in Chrome, and restored from backup. Video is now playing in technicolor, and I am applying all Ubuntu updates since my last backup to see if the problem returns.

Now I have to go back and read through this thread from the beginning. There is nothing like an active and knowledgeable community of users.

**Update:** I started reading this thread from the first post, then realized it might be more productive to start from the last. ;) 

I just disabled hardware acceleration pref for Flash, which has restored full color Youtube videos. I'm surprised that this problem has been around for at least a week, without being resolved by the Adobe/Google/Linux community (disabling hardware acceleration just being a work-around).

It works for me. PERFECT!!!!

---

### Post by dizzydaryluk on 2011-03-14
> **Kupfer said:**
> Thanks to user Liakoni from the Linux Mint Forums I can report a solution this problem. You need to disable hardware acceleration in the flash settings.

Step 1. Right click on a flash content (I went to this flash site [http://moodstream.gettyimages.com/](http://moodstream.gettyimages.com/) and simply right clicked on the page)
Step 2. Choose the entry "Settings..."
Step 3. Unclick entry "Enable hardware acceleration"
Step 4. Click "Close"

For me this fixed the issue on all of my browesers (Firefox, Chrome stable, Chromium). No more thick red filter on youtube videos.

Thanks again to Liakoni for discovering this solution.

Great thanks this works a treat. :popcorn:

---

### Post by The Real Pelana on 2011-03-15
Hi everyone!

It worked for me too; thanx a lot yall.

---

### Post by mattasus on 2011-03-15
> **Katten Jansson said:**
> [B][SIZE=3]How to fix this![/SIZE]

[/B]*This procedure worked for me. The reasons given why it works is speculations.*Youtube use faulty/outdated preferences for showing video, it get those from cookies that the site have set previously. Youtube seem to use some kind of "super cookie" (it use reduntant places to store information in order to make it harder for you to delete it), so you have to clean out both flash cookies and web-browser cookies and cache, otherwise youtube will restore the old preference after some time and  go back to displaying pink videos.
[B]
Close all Youtube, Google, et.c. affiliated pages in the browser(s).[/B]
[B]
[SIZE=1]Remove flash cookies
[/SIZE][/B][SIZE=1]Use a tool like better privacy or do it manually.

[B]Remove browser cookies and clear cache
[/B]Do this for all browsers that you use (or it will reset the Flash preferences shared by all browsers).


**Update: **I found a Wikipedia-article describing these kind of cookies:
[/SIZE][http://en.wikipedia.org/wiki/Evercookie](http://en.wikipedia.org/wiki/Evercookie)

This worked for me! for now a least! Thanks

---

### Post by mattasus on 2011-03-15
Never mind the problem came back after a browsed elsewhere on Chrome and came back. The I re-resolved it by deleting recent cookies. Deleting the cookies solved the problem in firefox as well.

---

### Post by Paddy Landau on 2011-03-16
@mattasus: This is documented elsewhere in this thread. If you read this thread, you'll find only three permanent workarounds. You'll find the easiest workaround in [post #63]("http://ubuntuforums.org/showthread.php?p=10520930#post10520930"), but it doesn't work for everyone.

---

### Post by bagy on 2011-03-22
Problem fixed with 10.2.153.1 version.

---

### Post by Paddy Landau on 2011-03-22
> **bagy said:**
> Problem fixed with 10.2.153.1 version.
Thank you. I've uninstalled version 10.3.162.29 (which had its own set of problems) and installed 10.2.153.1, and it works now.

---

### Post by nslegacy163 on 2011-03-22
Indeed! Looks like the red filter of death is gone thanks to the updates.

---

### Post by Marzata on 2011-03-23
Finally a Flash update for 10.04.2 (lucid). It works!

---

### Post by dangmc on 2011-12-24
> **t2491tom said:**
> I have found a fix! Uninstall flashplugin-installer and then install flashplayer .deb from [http://get.adobe.com/flashplayer/?no_redirect](http://get.adobe.com/flashplayer/?no_redirect).

Just want to say that after using Flash-Aid (Firefox add-on) to install the latest Flash beta version everything turned blue! After reading these posts I used Flash-Aid to to the latest Adobe Flash stable version. My videos returned to normal. This is by far, the easiest way to deal with any issues involving Flash. For me, AdBlock Plus and Flash-Aid are the greatest Firefox extensions out there.
 Xubuntu 11.10 X_64 install with Gnome 3 added; I'm using Gnome (no effects) Firefox 8

---

### Post by lovinglinux on 2011-12-24
> **dangmc said:**
> Just want to say that after using Flash-Aid (Firefox add-on) to install the latest Flash beta version everything turned blue! After reading these posts I used Flash-Aid to to the latest Adobe Flash stable version. My videos returned to normal. This is by far, the easiest way to deal with any issues involving Flash. For me, AdBlock Plus and Flash-Aid are the greatest Firefox extensions out there.
 Xubuntu 11.10 X_64 install with Gnome 3 added; I'm using Gnome (no effects) Firefox 8

Glad to read that, specially considering Ad Block Plus has more than 10 million users and mine just 20 thousand. :-)

---

