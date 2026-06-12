---
title: "alternatives to adobe flashplayer?"
date: 2012-03-31
forum: Multimedia Software
---

### Post by shantiq on 2012-03-31
after the latest update SMURF fiasco i am asking aloud are there ways to avoid using adobe flashplayer or has this company got a stranglehold on us Ubuntuers watching YT videos and other media online 

i heard about something called **[Lightspark]("http://www.unixmen.com/lightspark-a-good-alternative-to-adobe-flash-player-ppa-ubuntu-fedora-rpm/")**  but i  c ould not get it going



Any of you run it?     Are there any other FULLY-FUNCTIONING routes


I personally would be more than happy to be shot of anything ADOBE :KS and use something fully linux

---

### Post by lovinglinux on 2012-03-31
About an hour ago I added the SMURF fiasco to the [Pepper Mozilla bug](https://bugzilla.mozilla.org/show_bug.cgi?id=729481#c43). It is just informational, because Mozilla won't implement Pepper. [This article](http://www.theregister.co.uk/2011/09/12/google_native_client_from_all_sides/page3.html) explains well their reasons.

Flash is still working, but for how long? The SMURF fiasco was a warning that it might stop working sooner that we expect. The issue is clearly related to hardware acceleration, which has been crippled in the Linux version a couple of versions back. It probably won't be fixed, so we can expect "SMURF 2: The Resurrection" any time soon.

Adobe already removed the Flash Beta page and Linux is not included in the Adobe Flash Player Incubator page. Furthermore, Adobe is refusing to address Linux bugs reports, stating Linux is no longer supported.

I don't see much alternative. Lightspark and Gnash cannot fully replace flash yet, since they don't work on every site. 

There are some alternatives, like my [FlashVideoReplacer](https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/), but it just cover a few web sites. There are some [greasemonkey scritps](http://userscripts.org/) that can provide similar functionality for other web sites. For YouTube, you can also use Minitube.

I am really concerned. I hate the idea of using Chrome, specially after this Adobe+Google move. However, it seems it will be the only real long term alternative, unless Lightspark or Gnash receive a boost and become usable on most sites.

BTW, there is an interesting project supported by Mozilla to play SWF using HTML5, but I don't think it will play flash videos: [https://github.com/mozilla/shumway#readme](https://github.com/mozilla/shumway#readme)

---

### Post by shantiq on 2012-03-31
thanx man that is a whole lot of info  [Muito Obrigado]

i tried Lightspark on Opera [ my favored browser for the last 6 month/ trying to have nothing to do with Google as far as i can]

i think it was on YT and it showed a black rectangle where the video was


so back to the drawing board


in effect you are saying no FULLY FUNCTIONAL alternative as yet and it looks as if flashplayer is about to snub us bigtime

I could not program myself out of a room if all i had to do was to open the door:KS      so i shall make an offering to the Gods of Linux programming


and hope for better   



Corporate software is what we try and shun in my horizontal democracy new world


so anyway    thank you for a very thorough reply to my question


 [img]http://img824.imageshack.us/img824/2670/smilie201small.png[/img] [img]http://img824.imageshack.us/img824/2670/smilie201small.png[/img]

---

### Post by lovinglinux on 2012-03-31
> **shantiq said:**
> thanx man that is a whole lot of info  [Muito Obrigado]

i tried Lightspark on Opera [ my favored browser for the last 6 month/ trying to have nothing to do with Google as far as i can]

i think it was on YT and it showed a black rectangle where the video was


so back to the drawing board


in effect you are saying no FULLY FUNCTIONAL alternative as yet and it looks as if flashplayer is about to snub us bigtime

I could not program myself out of a room if all i had to do was to open the door:KS      so i shall make an offering to the Gods of Linux programming


and hope for better   



Corporate software is what we try and shun in my horizontal democracy new world


so anyway    thank you for a very thorough reply to my question


 [img]http://img824.imageshack.us/img824/2670/smilie201small.png[/img] [img]http://img824.imageshack.us/img824/2670/smilie201small.png[/img]

You are welcome.

Unfortunately, I never was able to make Lightspark work. Gnash is functional, but mostly for YouTube. Last time I checked it didn't work on a few sites I needed. It is time for a new series of tests.

---

### Post by sdowney717 on 2012-03-31
Linux support is dead.
After yesterdays update, for me, flash only works on Google Chrome and not firefox.

Hugely buggy and vulnerabilities were being covered up by Adobe. sooner the better it goes for everyone.

[http://9to5google.com/2011/08/10/google-engineer-claims-adobe-hid-embarrassingly-high-number-of-flash-player-bugs/](http://9to5google.com/2011/08/10/google-engineer-claims-adobe-hid-embarrassingly-high-number-of-flash-player-bugs/)

Linux support gone.
[http://9to5google.com/2012/02/22/pepper-based-flash-player-coming-to-chrome-later-this-year-adobe-dropping-standalone-plug-in-download-on-linux/](http://9to5google.com/2012/02/22/pepper-based-flash-player-coming-to-chrome-later-this-year-adobe-dropping-standalone-plug-in-download-on-linux/)

---

### Post by Kimm on 2012-03-31
Its pretty old news that Flash support is being dropped for Linux (in fact there was a thread about this not long ago). As the article states though, it will still work in Chrome, and I believe Firefox will be implementing the technology in due time as well.

Tbh, its about time that Flash died! Only time I ever use it these days is to view videos on YouTube, and that can be achieved just as easily using HTML5.

---

### Post by sdowney717 on 2012-03-31
I just started experiencing this last couple days with flash failing on Firefox and inverting the colors on Chrome. Blue colored Smurf like people. You get this effect with the Nvidia driver, but the bug is in the Adobe flash program. I cant even watch flash on Firefox now. And I see a lot of recent posts where people did updates and flash wont work anymore.

---

### Post by Erik1984 on 2012-03-31
I'm not sure if I'm on the latest version but I fixed the smurfs by unchecking "Enable hardware acceleration".

---

### Post by lovinglinux on 2012-03-31
> **sdowney717 said:**
> Linux support is dead.
After yesterdays update, for me, flash only works on Google Chrome and not firefox.

This bug only affects nVidia users. It is working fine for me on Firefox, Opera and Chrome.

> **Kimm said:**
> Its pretty old news that Flash support is being dropped for Linux (in fact there was a thread about this not long ago). As the article states though, it will still work in Chrome, and I believe Firefox will be implementing the technology in due time as well.

Tbh, its about time that Flash died! Only time I ever use it these days is to view videos on YouTube, and that can be achieved just as easily using HTML5.

It is not being dropped, it has been dropped already. Adobe is not even helping Linux users anymore. Any bug report gets a standard message that Flash is not supported in Linux. However, they promissed security patches for 5 years. Not very helpful, if hardware acceleration doesn't work and won't be fixed.

Google will implement Flash via Pepper API, but Mozilla and Opera are against Pepper and won't implement such technology. So, as long as flash lives and the current version gives problems, people will have to switch to Chrome. 

For more info, see second post in this thread.

---

### Post by souravc83 on 2012-03-31
What if I stop updating?
Maybe I will reach a point where my old versions are not supported by Youtube or other sites, but that's like if I don't update for 2 years.
I had a friend, a big linux geek. His idea was that once you have got a stable system, that you know works, you should never update.
He had an old fedora build, and he never updated unless it was really necessary. I was reminded of him yesterday, when the smurf fiasco happened. 
While updates are the only way to improve your system, they can also end up breaking your system. If all you really care about is basic functionalities, that work well, it might be a reasonable idea to stick to the current versions of chrome,firefox, flash. that way, you are safe unless anything major changes, that is not supported in your old software.
I switched to Ubuntu not long ago, and this is something that has got me thinking.

---

### Post by lovinglinux on 2012-03-31
> **souravc83 said:**
> What if I stop updating?
Maybe I will reach a point where my old versions are not supported by Youtube or other sites, but that's like if I don't update for 2 years.
I had a friend, a big linux geek. His idea was that once you have got a stable system, that you know works, you should never update.
He had an old fedora build, and he never updated unless it was really necessary. I was reminded of him yesterday, when the smurf fiasco happened. 
While updates are the only way to improve your system, they can also end up breaking your system. If all you really care about is basic functionalities, that work well, it might be a reasonable idea to stick to the current versions of chrome,firefox, flash. that way, you are safe unless anything major changes, that is not supported in your old software.
I switched to Ubuntu not long ago, and this is something that has got me thinking.

That's a misguided concept. You need to update to get security and stability patches. That's the main reason people update their software, not considering new features, which are not provided by Ubuntu updates.

If you need stability, then you should install Ubuntu LTS. 

In the particular scenario of Flash, it might be solution to not upgrade the flash package, but you will running an insecure version and it won't last forever. As you  mentioned, it will eventually stop working on most web sites.

---

### Post by RJARRRPCGP on 2012-04-07
I'm concerned that Google is planning to use Pepper as a weapon to ban all other browsers from YouTube. 

And YouTube's TOS can be interpreted as FlashVideoReplacer being outlawed and labelled as a pirate's tool. 
And interpret MPlayer as being outlawed and a pirate's tool.

Google may be committing an anti-competition violation as I'm typing.

TBH, FlashVideoReplacer is legal and the same with MPlayer for playing streams. 
But Google may falsely accuse us of copyright infringement. (Thus commit RIAA and MPAA like behavior.)

---

### Post by RJARRRPCGP on 2012-04-07
> **sdowney717 said:**
> Linux support is dead.


And I'm still not completely out of the woods even if I dump YouTube. 

I'm afraid that Exposure Room videos could fail to play without Flash, even with the FlashVideoReplacer extension. 

And I'm afraid that XR's gonna refuse to support HTML 5. :(

At least YouTube went in the right direction. As a result, XR and Viddler may go backwards. :(

YouTube's overall quality is better than 2008 and most of 2009!  
YouTube was buggy before late November, 2009. Randomly refused to play videos often with a generic message about a problem, including just a black screen with the message "This video is not available" or similar, even when not flagged, which happened to one video in particular and the person apparently had to re-upload a video to solve the problem.

And in 2009, this bug: When uploading, after the upload progress goes to 100 percent, the error "Failed (upload aborted)".

At least, YouTube isn't stuck in the dinosaur age!

---

### Post by lovinglinux on 2012-04-07
> **RJARRRPCGP said:**
> I'm concerned that Google is planning to use Pepper as a weapon to ban all other browsers from YouTube. 

I think they are trying to force other browser vendors to adopt Pepper API and NativeClient.

> **RJARRRPCGP said:**
> And YouTube's TOS can be interpreted as FlashVideoReplacer being outlawed and labelled as a pirate's tool. 
And interpret MPlayer as being outlawed and a pirate's tool.

Google may be committing an anti-competition violation as I'm typing.

TBH, FlashVideoReplacer is legal and the same with MPlayer for playing streams. 
But Google may falsely accuse us of copyright infringement. (Thus commit RIAA and MPAA like behavior.)

Google promotes tools like FlashVideoReplacer in their own app store.

---

### Post by shantiq on 2012-04-08
> **RJARRRPCGP said:**
> I'm concerned that Google is planning to use Pepper as a weapon to ban all other browsers from YouTube. 

And YouTube's TOS can be interpreted as FlashVideoReplacer being outlawed and labelled as a pirate's tool. 
And interpret MPlayer as being outlawed and a pirate's tool.

Google may be committing an anti-competition violation as I'm typing.

TBH, FlashVideoReplacer is legal and the same with MPlayer for playing streams. 
But Google may falsely accuse us of copyright infringement. (Thus commit RIAA and MPAA like behavior.)


**yes let us all beware  ** [img]http://img838.imageshack.us/img838/5745/smilie33.png[/img] 

and how many know that Youtube is owned by Google

> YouTube is a video-sharing website, created by three former PayPal employees in February 2005, on which users can upload, view and share videos.[3] The company is based in San Bruno, California, and uses Adobe Flash Video and HTML5[4] technology to display a wide variety of user-generated video content, including movie clips, TV clips, and music videos, as well as amateur content such as video blogging and short original videos.

Most of the content on YouTube has been uploaded by individuals, although media corporations including CBS, the BBC, VEVO, Hulu, and other organizations offer some of their material via the site, as part of the YouTube partnership program.[5] Unregistered users can watch videos, while registered users can upload an unlimited number of videos. Videos considered to contain offensive content are available only to registered users at least 18 years old. **[COLOR="DarkRed"]In November 2006, YouTube, LLC was bought by Google for US$1.65 billion[/COLOR]**, and now operates as a subsidiary of Google.

so in effect what they are doing is a TOTAL MONOPOLY  DRIVE To control the entire net material


make sure if you want to move or sneeze you have to ask them for permission first

from being a place of freedom the internet becomes a straightjacket controlled by a MONOPOLY


IS what they are going for here

ein reich ein folk ein video-sharing website provider and that is it


We need to remain vigilant here


They are locking it down bit by bit

I first realized that when i tried to open a new YT account 6 months ago

THE ONLY WAY WAS TO HAVE A GOOGLEMAIL ACCOUNT FIRST

LIKE a magic mantra at the gate  [no Google no YT]

So yes expect software that no one else has being rolled out   [iSteveJobs would be proud]

And penalties if trying other routes

This is THE BRAVE NEW INTERNET they are planning

All 3 YT Facebook and Googlemail have recently FORCED new "looks" which do not give you ANY choice

They are grooming us not so subtly for total domination    Pepper will be one of their tools  but no doubt many more in the offing


Thanx for bringing it up it needs to be discussed ... Awareness is everything [img]http://img838.imageshack.us/img838/5745/smilie33.png[/img] [img]http://img838.imageshack.us/img838/5745/smilie33.png[/img]


**ps**    also there cannot be any mileage for those people to have anyone using Linux since it is all about choice/freedom and customization

making it hard for people to view YT or anything like that will bring many back to daddy [Windows] and mummy [mac]

the only way ut is true independence  which spells  LINUX SOFTWARE designed by linux people.   I am no programmer and do not know how feasible that is  but clearly that is the only way not to be at the mercy of what looks more and more like THE INTERNET CORPORATION [EXTREMELY Ltd]

---

### Post by pickarooney on 2012-04-09
Having had the notorious smurf issue with the latest flash version I followed afix which involved copying another so file into the plugin folder. This fixed the blue face but now YouTube videos keep freezing. I enabled the html 5 test but firefighters seems to ignore this and still use flash. Firefox also crashes all over the place. 

What's my best option Here?

---

### Post by PhantomTurtle on 2012-04-09
Some videos just cannot be watched in html5 on youtube. Your best option? Well either you can get rid of it forever and learn to live with that or try and find an alternative for flash player. You could try lightspark, [http://ubuntuguide.net/lightspark-an-alternative-high-performance-free-flash-player]("http://ubuntuguide.net/lightspark-an-alternative-high-performance-free-flash-player"). It is an alternative that is available for 10.10 and higher ubuntu system. It might be completely stable, but worth a try.

---

### Post by motorcity909 on 2012-04-09
For watching Youtube you could try Minitube in the software centre.

Cheers
Dave

---

### Post by pickarooney on 2012-04-09
> **PhantomTurtle said:**
> Some videos just cannot be watched in html5 on youtube. Your best option? Well either you can get rid of it forever and learn to live with that or try and find an alternative for flash player. You could try lightspark, [http://ubuntuguide.net/lightspark-an-alternative-high-performance-free-flash-player]("http://ubuntuguide.net/lightspark-an-alternative-high-performance-free-flash-player"). It is an alternative that is available for 10.10 and higher ubuntu system. It might be completely stable, but worth a try.

I've read that Adobe are not going to make any more versions of flash for linux. I wonder what will happen down the line. There's so much flash content embedded in sites it's going to be very difficult to do without it.

I'll give this lightspark a go and that minitube seems to work OK for Youtube videos.

---

### Post by PhantomTurtle on 2012-04-09
> **pickarooney said:**
> I've read that Adobe are not going to make any more versions of flash for linux. I wonder what will happen down the line. There's so much flash content embedded in sites it's going to be very difficult to do without it.

I'll give this lightspark a go and that minitube seems to work OK for Youtube videos.

I completely forgot minitube. It is a great youtube client. Flash is everywhere on the web, but websites are starting to use html5 as well. This means that eventually it will not even matter to Linux users if flash is available for Linux or not.

---

### Post by pickarooney on 2012-04-09
Lightspark is unfortunately useless. It won't play embedded stuff. I seem to able to view most videos on YouTube with HTML5 but nothing embedded. Unless anyone knows a way to get Firefox to use HTML for these?

---

### Post by philinux on 2012-04-09
Have you tried the flashaid mozzila addon to fix up flash.

---

### Post by motorcity909 on 2012-04-09
I think we all know that Flash is on its way out.  Adobe are no longer developing it for mobile platforms, iPads don't have it, Windows 8 won't have it.

Adobe will be giving security updates for the next five years anyway so I'm not worried that I won't be able to watch online videos in a few years time.

We will know Flash is dead and HTML5 has won when the, er, gentlemen's websites start using it - they always back the winners like VHS and BluRay!

---

### Post by RJARRRPCGP on 2012-04-09
;-)> **lovinglinux said:**
> 



Google promotes tools like FlashVideoReplacer in their own app store.

Good! Because I'm loving the extension to death! ;)

And WebM seems to be fine for the majority of videos, hooray!

I still brought this up, because I noticed some videos failed to come up in WebM mode. :(

---

### Post by lovinglinux on 2012-04-09
Threads merged. 


It seems the only viable alternative in the long term will be to use Chrome browser once they release PepperFlash, because Adobe has ended support for Flash on Linux and handed it to Google. Mozilla and Opera won't implement PepperFlash. Lightspark and Gnash are great initiatives, but sadly don't work. I never was able to make Lightspark work at all and Gnash only works on YouTube as far as I know.

---

### Post by shantiq on 2012-04-10
> **philinux said:**
> Have you tried the flashaid mozzila addon to fix up flash.


[Flash-aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") totally fixed all functionality on Firefox   [Thank you LL /and Philinux for pointing me there]

In my case it had to remove Gnash AND Lightspark which i had tried to use as replacement; did not realize they would clash


SO ALL FUNCTIONALITY RESTORED :KS:KS



PS   ONCE add-on installed one needs to go to the icon and use wizard to complete install, then terminal pops up and shows the changes, very neat.

---

### Post by TenPlus1 on 2012-04-10
In a way I'm happy that flash isn't being developed further on linux with only a few years support for the current version.  This will finally give users and sites a chance to upgrade to html5 and use embedded movies like ogg theora, webm and h.264.  As for flash games, those could still run using the current version and/or the lightspark project once it's up and running properly...

---

### Post by bcschmerker on 2012-04-21
> **lovinglinux said:**
> ...Unfortunately, I never was able to make Lightspark work. Gnash is functional, but mostly for YouTube. Last time I checked it didn't work on a few sites I needed. It is time for a new series of tests.I concur, as Gnash does not interact properly with several user-music and -video Websites, as of April 2012.  A test of Gnash that I did at [SingSnap® Karaoke]("http://www.singsnap.com/karaoke/home/index") back in 2011 was a _fail_, as Gnash did not upstream data in a format that the Website recognizes, unlike all versions of Adobe® Flash Player; specifically, /karaoke/record/wizard did not recognize any return information from Gnash during an attempted audio calibration.

W3C Hypertext Markup Language 5 is not a one-for-one replacement for the proprietary Macromedia® shockwave/flash software architecture still required by many user-music and -video Websites, which have to do major recoding for their pages to function properly in HTML 5 as they used to function in Flash.

---

### Post by ticket on 2012-04-22
The last (11.2?) version of flash does work with the latest Ubuntu (11.10), provided you switch off accelerated rendering.

Adobe struggled to get the accelerated rendering working under Linux for a long time.  Some success was achieved via the VPAU feature for those that had nVidia cards, but ATI users got nothing.  Now both camps are denied the feature.

So if you have a powerful enough CPU that can cope with the task of software rendering of the flash video, you will be ok, even for 1080p resolution videos.  But for older computers, full screen flash will be unusable, and you will only be able to play embedded videos at around 360/480p.

So we have a sort of stop gap, especially for those that have powerful CPUs, until an alternative arrives.

Remember that flash is also used for many on-line games (e.g. runescape), so it will take a while to get those fixed up.

---

### Post by RJARRRPCGP on 2012-04-29
Gnash still appears to be an epic fail for anything other than YouTube! 

It can't even play many ads correctly! :evil:

Looks like people may be flocking back to XP, for at least 1 more year.

Shame on you, Adobe. You make Linux look like a fool and now people may actually go back to Windows XP O_O.

---

### Post by dentaku65 on 2012-04-30
Hi,

I'm experimenting to use the flash plugin of Chrome under FF

The result is quite good, except that the value "dom.ipc.plugins.ebabled" must be set on "true" in about:config options; this is a pity because this option is invoking the "crap" plugin-container process eager of resources (otherwise set on false the result will be 9 out of 10 in an "happy crash" of FF)

Here the step to use Chrome flash plugin under FF:

Install Chrome browser from here [https://www.google.com/chrome?platform=linux&hl=en](https://www.google.com/chrome?platform=linux&hl=en)

Close FF, then:
```
sudo apt-get remove flashplugin-*
```
Then
```
mkdir -p ~/.mozilla/plugins
```
Then
```
cp /opt/google/chrome/libgcflashplayer.so ~/.mozilla/plugins/
```
Then open FF, open about:addons, choose Plugins and disable Shockwave Flash

Plus, I'm testing these mms.cfg settings (derived from Debian). my /etc/adobe/mms.cfg is:
> # Adobe player settings
AVHardwareDisable = 1
FullScreenDisable = 0
LocalFileReadDisable = 1
FileDownloadDisable = 1
FileUploadDisable = 1
LocalStorageLimit = 1
ThirdPartyStorage = 1
AssetCacheSize = 10
AutoUpdateDisable = 1
LegacyDomainMatching = 0
LocalFileLegacyAction = 0
AllowUserLocalTrust = 0
OverrideGPUValidation = 1
[COLOR="Red"]EnableLinuxHWVideoDecode=0[/COLOR]

Set: [COLOR="Red"]EnableLinuxHWVideoDecode=1[/COLOR] if you have VDPAU support.
by

---

### Post by lovinglinux on 2012-04-30
> **dentaku65 said:**
> Hi,

I'm experimenting to use the flash plugin of Chrome under FF

The result is quite good, except that the value "dom.ipc.plugins.ebabled" must be set on "true" in about:config options; this is a pity because this option is invoking the "crap" plugin-container process eager of resources (otherwise set on false the result will be 9 out of 10 in an "happy crash" of FF)

Here the step to use Chrome flash plugin under FF:

Install Chrome browser from here [https://www.google.com/chrome?platform=linux&hl=en](https://www.google.com/chrome?platform=linux&hl=en)

Close FF, then:
```
sudo apt-get remove flashplugin-*
```
Then
```
mkdir -p ~/.mozilla/plugins
```
Then
```
cp /opt/google/chrome/libgcflashplayer.so ~/.mozilla/plugins/
```
Then open FF, open about:addons, choose Plugins and disable Shockwave Flash

Plus, I'm testing these mms.cfg settings (derived from Debian). my /etc/adobe/mms.cfg is:

Set: [COLOR="Red"]EnableLinuxHWVideoDecode=1[/COLOR] if you have VDPAU support.
by

If you use Flash-Aid, you can easily copy the Chrome plugin using the Advanced mode.

Keep in mind that once Google start using the PepperFlash, that technique won't work. The development version of Chrome 64bit already has PPAPI plugin instead of the NPAPI plugin, but it is unusable at the moment.

---

### Post by Chargerbear on 2012-11-26
Solved: The problem is the flashplugin-installer.
from (synaptic package manager (not installed by default in 12.04)) and probably ubuntu software center. Enter search term (adobe flash) Install adobe-flashplayer (version 11.2.202.251-0precise1). This will uninstall flashplugin-installer and you will leave Smurfville. You will now enjoy beautiful flash videos. You're Welcome!

---

