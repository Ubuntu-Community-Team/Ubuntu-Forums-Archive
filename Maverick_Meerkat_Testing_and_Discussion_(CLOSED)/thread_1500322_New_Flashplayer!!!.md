---
title: "New Flashplayer!!!"
date: 2010-06-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2010-06-03
Flash 10.1 is out!!! Released today--(fixed my problems with flash currently):  [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by VMC on 2010-06-03
Thanks. I think I will try it out. I've had not so good results in the past.

---

### Post by VMC on 2010-06-03
Since I only use Google Chrome, it didn't work. I found a site that shows how to install using menu edit. It worked great!

Here's the link if your using Google Chrome (maybe an easier method, but this works):

[http://www.howtoforge.com/how-to-enable-adobes-flash-player-in-google-chrome-ubuntu-9.04-p2](http://www.howtoforge.com/how-to-enable-adobes-flash-player-in-google-chrome-ubuntu-9.04-p2)

---

### Post by uRock on 2010-06-03
Sweet, hopefully it makes the repos for Lucid. It is annoying to have to boot Windows to chill with YouTube.com.

---

### Post by krazyd on 2010-06-03
64-bit hasn't been updated

[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

---

### Post by glaze on 2010-06-03
It's still a prerelease.

---

### Post by nilarimogard on 2010-06-03
It's release candidate 7, they release one like.. every week :|

---

### Post by taavikko on 2010-06-03
> **nilarimogard said:**
> they release one like.. every week :|

For once, maybe release something that works.... :)

Flash on x86_64 is a PITA

---

### Post by Random_Dude on 2010-06-03
Noob question: How do I install this?

I've tried uncompressing the flashplayer10_1_rc7_linux_060210.so.tar.gz file and running:

```
./configure
make
sudo make install
```

and it doesn't work. :(

I get some error right in the ./configure stage.
Is it supposed to be done in some other way?

Cheers :cool:

---

### Post by taavikko on 2010-06-03
> **Random_Dude said:**
> Noob question: How do I install this?

I've tried uncompressing the flashplayer10_1_rc7_linux_060210.so.tar.gz file and running:

```
./configure
make
sudo make install
```

and it doesn't work. :(

I get some error right in the ./configure stage.
Is it supposed to be done in some other way?

Cheers :cool:

Just extract the .so from the archive (tar.gz) and copy it in ~/.mozilla/plugins/

---

### Post by philinux on 2010-06-03
> **taavikko said:**
> For once, maybe release something that works.... :)

Flash on x86_64 is a PITA

What problems do you get? Seems not bad here apart from full screen a but stuttery but that depends on a site's bandwidth I guess?

---

### Post by taavikko on 2010-06-03
> **philinux said:**
> What problems do you get? Seems not bad here apart from full screen a but stuttery but that depends on a site's bandwidth I guess?

Flash hogs CPU, spikes the X too, which in return reduces usability. Causes the fans to scream out of pain :)
Stuttery video, not related to site's bandwidth, lack of GPU usage.

Malfunctioning buttons/controls

So basically my main gripe is that x86_64 flash is missing the acceleration.

And in overall missing the feature parity over windows counterpart...

---

### Post by philinux on 2010-06-03
> **taavikko said:**
> Flash hogs CPU, spikes the X too, which in return reduces usability. Causes the fans to scream out of pain :)
Stuttery video, not related to site's bandwidth, lack of GPU usage.

Malfunctioning buttons/controls

So basically my main gripe is that x86_64 flash is missing the acceleration.

And in overall missing the feature parity over windows counterpart...

Righto, yeah full screen spikes both cpus here t0 90%. I use compiz zoom sometimes which is no where near as bad, 35% cpu average. Buttons work fine here.
Is there a way to tell if gpu is being used even if hardware acceleration is ticked in flash settings?

Spec.
AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
nVidia 8600GT

---

### Post by taavikko on 2010-06-03
> **philinux said:**
> 
Is there a way to tell if gpu is being used even if hardware acceleration is ticked in flash settings?


If using 64bit flash, no, cause it isn't used ](*,)

Cannot answer for the 32bit version since haven't used it since Gutsy..

"top" should show the effects, if GPU is used, since the X and flash shouldn't hog the CPU as much.

---

### Post by Random_Dude on 2010-06-03
> **taavikko said:**
> Just extract the .so from the archive (tar.gz) and copy it in ~/.mozilla/plugins/

That folder doesn't exist. :|
I've got the ~/.mozilla but there's no plugins folder in there.

All I've got similar to that is some folders on /opt and on /usr, I think...
Which one is the correct one?

---

### Post by philinux on 2010-06-03
> **taavikko said:**
> If using 64bit flash, no, cause it isn't used ](*,)

Cannot answer for the 32bit version since haven't used it since Gutsy..

"top" should show the effects, if GPU is used, since the X and flash shouldn't hog the CPU as much.


Lets hope they sort it then eh. :shock:

---

### Post by philinux on 2010-06-03
> **Random_Dude said:**
> That folder doesn't exist. :|
I've got the ~/.mozilla but there's no plugins folder in there.

All I've got similar to that is some folders on /opt and on /usr, I think...
Which one is the correct one?

You have to create the folder. :P

---

### Post by taavikko on 2010-06-03
> **Random_Dude said:**
> That folder doesn't exist. :|
I've got the ~/.mozilla but there's no plugins folder in there.

All I've got similar to that is some folders on /opt and on /usr, I think...
Which one is the correct one?

```
mkdir ~/.mozilla/plugins
```
and then copy the .so to there.

or you can copy the .so to /usr/lib/mozilla/plugins/

difference is, copying it to $HOME it is only available to you.
Good choice if you're the only user.

Latter makes it available to all users.

---

### Post by taavikko on 2010-06-03
> **philinux said:**
> Lets hope they sort it then eh. :shock:

One of the most yearned features :)


We might see Duke Nukem before that happens...?

---

### Post by Random_Dude on 2010-06-03
> **taavikko said:**
> ```
mkdir ~/.mozilla/plugins
```and then copy the .so to there.

or you can copy the .so to /usr/lib/mozilla/plugins/

difference is, copying it to $HOME it is only available to you.
Good choice if you're the only user.

Latter makes it available to all users.

Thanks :)
I'm the only user but I've copied it to /usr/lib/mozilla/plugins/ just to keep it organized.

Some flash games still blink with this version thought. :\

Do I have to delete some older flashplayer file or something?

Cheers :cool:

---

### Post by DougieFresh4U on 2010-06-03
> **philinux said:**
> Righto, yeah full screen spikes both cpus here t0 90%. I use compiz zoom sometimes which is no where near as bad, 35% cpu average. Buttons work fine here.
Is there a way to tell if gpu is being used even if hardware acceleration is ticked in flash settings?

Spec.
AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
nVidia 8600GT

I am running AMD Athlon 64 x2 Dual Core 5200+ as well
with an ATI Radeon HD3200.
I don't seem to have the CPU spike with full screen, yet :)

---

### Post by VMC on 2010-06-03
It works but barely. Sadly Windows XP works perfectly. 

I get jitters and the voice and mouth are out of sync.

Any tips remedy this?

---

### Post by wojox on 2010-06-03
Cool, thanks for the head's up.

---

### Post by null_pointer_us on 2010-06-03
> **philinux said:**
> Righto, yeah full screen spikes both cpus here t0 90%. I use compiz zoom sometimes which is no where near as bad, 35% cpu average. Buttons work fine here.
Is there a way to tell if gpu is being used even if hardware acceleration is ticked in flash settings?

Spec.
AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
nVidia 8600GT
If even basic video hardware acceleration had been used, the video scaling would have been done on the GPU, so CPU usage would not be spiking to ~90% both cores on your PC during fullscreen video playback.

[Adobe commented in late January]("http://blogs.adobe.com/penguin.swf/2010/01/welcome_to_the_thicket.html") that they would not support GPU-accelerated video decoding on Linux in Flash 10.1 because the supposed lack of a common video decoding/accleration API.

The flash hardware acceleration setting probably means different things on different platforms. From what I've read, Flash is much more than just video playback; it was primarily used for drawing operations like animations and transitions while Flash video playback only became popular later.

How would Adobe get basic 2D/video scaling hardware acceleration in a Mozilla browser plugin on Linux? X extensions? OpenGL? Some kind of special functions in the browser/plugin API? I really don't know.

---

### Post by taavikko on 2010-06-03
> **VMC said:**
> It works but barely. Sadly Windows XP works perfectly. 

I get jitters and the voice and mouth are out of sync.

Any tips remedy this?

[http://forums.adobe.com/community/labs/flashplayer10_64bit](http://forums.adobe.com/community/labs/flashplayer10_64bit)

---

### Post by keypox on 2010-06-03
> **philinux said:**
> Righto, yeah full screen spikes both cpus here t0 90%. I use compiz zoom sometimes which is no where near as bad, 35% cpu average. Buttons work fine here.
Is there a way to tell if gpu is being used even if hardware acceleration is ticked in flash settings?

Spec.
AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
nVidia 8600GT

I thought that there would be no hardware accel in flash for linux?  

[http://www.adobe.com/devnet/flashplayer/articles/fplayer10.1_hardware_acceleration_02.html](http://www.adobe.com/devnet/flashplayer/articles/fplayer10.1_hardware_acceleration_02.html)

"Linux currently lacks a developed standard API that supports H.264 hardware video decoding, and Mac OS X does not expose access to the required APIs."

I believe osx has now exposed the needed apis.

---

### Post by screaminj3sus on 2010-06-03
> **null_pointer_us said:**
> If even basic video hardware acceleration had been used, the video scaling would have been done on the GPU, so CPU usage would not be spiking to ~90% both cores on your PC during fullscreen video playback.

[Adobe commented in late January]("http://blogs.adobe.com/penguin.swf/2010/01/welcome_to_the_thicket.html") that they would not support GPU-accelerated video decoding on Linux in Flash 10.1 because the supposed lack of a common video decoding/accleration API.

The flash hardware acceleration setting probably means different things on different platforms. From what I've read, Flash is much more than just video playback; it was primarily used for drawing operations like animations and transitions while Flash video playback only became popular later.

How would Adobe get basic 2D/video scaling hardware acceleration in a Mozilla browser plugin on Linux? X extensions? OpenGL? Some kind of special functions in the browser/plugin API? I really don't know.
Yeah they have a point, linux is super fragmented when it comes to things like video acceleration, it would probably be a huge PIA for them ti implement something that works for everyone right now.

---

### Post by ranch hand on 2010-06-03
I kind of like reading this thread.

I have a lot of problems with 10.04 and our current FUN but flash just is not one of them.  It has  worked great for me since 9.04.

YouTube on full screen is just great with what ever version of flash is in the repo.

Hope it gets that way for you guys too.

---

### Post by uRock on 2010-06-03
> **ranch hand said:**
> I kind of like reading this thread.

I have a lot of problems with 10.04 and our current FUN but flash just is not one of them.  It has  worked great for me since 9.04.

YouTube on full screen is just great with what ever version of flash is in the repo.

Hope it gets that way for you guys too.
Only in my dreams or with W7. I hope it gets better for Linux soon.

---

### Post by Linuxforall on 2010-06-03
Flash x64 alpha has worked fine here since its release, I just copy libflashplayer.so to /usr/lib/mozilla/plugins and it works fine with FF, Chrome and Opera here. On my dual XEON, the CPU goes up to 15-20% on average per core doing full screen. I have no issues with flash based games on Facebook as well.

---

### Post by zika on 2010-06-03
> **Linuxforall said:**
> Flash x64 alpha has worked fine here since its release, I just copy libflashplayer.so to /usr/lib/mozilla/plugins and it works fine with FF, Chrome and Opera here. On my dual XEON, the CPU goes up to 15-20% on average per core doing full screen. I have no issues with flash based games on Facebook as well.Ditto. I do use ~/.mozilla/plugins folder, instead...

---

### Post by ronacc on 2010-06-03
flash has been solid on my box since the first 64bit version , 7600gs and various drivers both installed with "hardware drivers" or by hand from nvidia .

---

### Post by philinux on 2010-06-03
Well there's always Lightspark in the wings.

[http://en.wikipedia.org/wiki/Lightspark](http://en.wikipedia.org/wiki/Lightspark)

---

### Post by frostwyrm333 on 2010-06-03
Did somebody get lightspark to work? For me it doesn't display any flash content at all.

edit: well, I had to move libflashplayer.so away. It can't play youtube videos (0.4 PPA build), it displays simple banners but without antialiasing, i can't context menu (if there is any) so its still under heavy development.
But I'm interested anyway. If it really renders through opengl and uses multithreading it can easily outperform official flash, even ironed out one.
From what I know flash renders through CPU and thats the reason its so slow.

---

### Post by screaminj3sus on 2010-06-03
I'm just sticking with flash 10 64 bit for now as It seems to be working perfectly for me :)

---

### Post by qwerty2009 on 2010-06-03
**simple script to install the latest version**

[flash.sh]("http://ubuntuone.com/p/5xN/")

make it executable then run in terminal, hope it help's anyone thats having trouble

---

### Post by Starks on 2010-06-03
I think fullscreen flash is busted. I'm getting x server crashes.

(edit: xorg-edgers fault)

---

### Post by mikewhatever on 2010-06-03
> **autocrosser said:**
> Flash 10.1 is out!!! ...

Are you high? It clearly says RC7.

---

### Post by autocrosser on 2010-06-03
> **mikewhatever said:**
> Are you high? It clearly says RC7.

:P:P:P  It's the first RC of 10.1 that worked worth a s*** on my box---& that late of a RC will most likely be final.....As for high--I rather think not.

---

### Post by keypox on 2010-06-03
> **ranch hand said:**
> I kind of like reading this thread.

I have a lot of problems with 10.04 and our current FUN but flash just is not one of them.  It has  worked great for me since 9.04.

YouTube on full screen is just great with what ever version of flash is in the repo.

Hope it gets that way for you guys too.

Yes flash will make great use of those quad core cpus.  But not for those with single core or slow multicore, its another area where linux and mac need to catch up. (Blaming adobe doesnt help anything when its not adobes fault.)

---

### Post by cariboo on 2010-06-03
It is Adobe's fault, because the won't off-load the work to the gpu, the opensource videos drivers are freely available, so that isn't an excuse.

---

### Post by ranch hand on 2010-06-03
I do not know that the cpus I have really help in this case.  I have boinc running as hard as I can on 9.04 which really is too hard on 10.10.  I have it set to run at 99 to 100% all the time so all four are cranked right out.

FF will crash the system with the settings that way but running flash does not seem to effect it at all differently.

I usually run three windows of FF with multible tabs on 9.04 but have cut down to just one usually here on 10.10.

---

### Post by mikewhatever on 2010-06-03
> **keypox said:**
> Yes flash will make great use of those quad core cpus.  But not for those with single core or slow multicore, its another area where linux and mac need to catch up. (Blaming adobe doesnt help anything when its not adobes fault.)

Are you saying Linux and Mac devs should go work for Adobe? Besides, ranch hand, the guy you responded to, wasn't in the least blaming Adobe.:confused:
And just for the record, flash for Linux sucks, and it is none but Adobe's fault.

---

### Post by keypox on 2010-06-03
> **mikewhatever said:**
> Are you saying Linux and Mac devs should go work for Adobe? Besides, ranch hand, the guy you responded to, wasn't in the least blaming Adobe.:confused:
And just for the record, flash for Linux sucks, and it is none but Adobe's fault.

Well in OSX case they never would give access to the api's needed for gpu offloading.  Dont think it was even possible till snow leopard. 

In linux, from my understanding there is no standard api's that adobe can use to do it. 

Edit:  And i would say yes linux/mac employees should work with adobe. Just pointing fingers is going no where. 

Maybe it is adobes fault, but I think its a mixture. And doubt that adobe is going out of there way to harm linux.

---

### Post by screaminj3sus on 2010-06-03
> **cariboo907 said:**
> It is Adobe's fault, because the won't off-load the work to the gpu, the opensource videos drivers are freely available, so that isn't an excuse.

lol the open source drivers for ati/nvidia dont do ANY video acceleration let alone flash. Dont be so quick to blame adobe, they have a point.

---

### Post by Longinus00 on 2010-06-03
> **screaminj3sus said:**
> lol the open source drivers for ati/nvidia dont do ANY video acceleration let alone flash. Dont be so quick to blame adobe, they have a point.

flash is still slower on osx or linux than windows even with no hw acceleration on windows.

---

### Post by mikewhatever on 2010-06-04
> **keypox said:**
> Well in OSX case they never would give access to the api's needed for gpu offloading.  Dont think it was even possible till snow leopard. 

In linux, from my understanding there is no standard api's that adobe can use to do it. 

Edit:  And i would say yes linux/mac employees should work with adobe. Just pointing fingers is going no where. 

Maybe it is adobes fault, but I think its a mixture. And doubt that adobe is going out of there way to harm linux.

I think the problem with flash is much broader then you present it. It's really not limited to Linux and Mac, since as far as I know, there is still no stable version of flash player that does hardware acceleration even on Windows. What's your excuse far that?
Flash is also one of the major causes for Firefox crashes on Windows (according to Mozilla). Who's fault do you think that is? Mozilla's? Microsoft's?
No one is saying that developing a good product is simple, but imo, Adobe has not been doing a good job with its flashplayer on any platform, both quality and security wise.

---

### Post by xir_ on 2010-06-05
i have two ways around the full screen stutter.

1. find the video and let it fully buffer and then do something like

```
vlc /tmp/FLASH*
```
The videos then work perfectly full screen (someone should write a plugin for this to be automatically done in browsers).

Second just use chrome and enable HTML5 but this only works on youtube.

---

### Post by screaminj3sus on 2010-06-05
> **mikewhatever said:**
> I think the problem with flash is much broader then you present it. It's really not limited to Linux and Mac, since as far as I know, there is still no stable version of flash player that does hardware acceleration even on Windows. What's your excuse far that?
Flash is also one of the major causes for Firefox crashes on Windows (according to Mozilla). Who's fault do you think that is? Mozilla's? Microsoft's?
No one is saying that developing a good product is simple, but imo, Adobe has not been doing a good job with its flashplayer on any platform, both quality and security wise.

Flash 10.1 on windows does hardware acceleration.

---

### Post by mikewhatever on 2010-06-05
> **screaminj3sus said:**
> Flash 10.1 on windows does hardware acceleration.

So I heard. It will be interesting to test, when the stable version is released. It's currently at RC7.

---

### Post by uRock on 2010-06-05
I don't really need a newer flash for Windows. It already works without any problems. I can't wait for the day I can say that with Ubuntu.

---

### Post by screaminj3sus on 2010-06-05
I honestly dont have much performance issues with flash in linux, windows does perform slightly better and use less cpu but in linux its perfectly usable. I have a laptop with a 2ghz core2 which isnt a super powerful processor, regular flash vids use around 20-30% cpu and watching 720p flash uses around 50% of cpu and its smooth. (64 bit flash 10)

---

### Post by null_pointer_us on 2010-06-05
CPU usage from video playback should be negligible (i.e. < 5%). On Windows, many media players (including Flash 10.1 previews) are close to this goal. GPU decode and scaling are more efficient both in terms of power usage and of course leaving the CPU free to do other work.

Flash 10.1 previews on Windows have been hit-or-miss. Sometimes they would break major video sites or be unusable with certain hardware, drivers, or browsers. Adobe began providing [a changelog in their release notes]("http://labs.adobe.com/technologies/flashplayer10/releasenotes.pdf") at some point so that you could see what was fixed in each release.

Flash 10 64-bit latest alpha was made available in February, so it'll probably be a long time until we see official 64-bit Flash support on Linux. There's no indication when it will reach version/feature/quality parity with the 32-bit Flash on Linux that is already at 10.1 RC7. Neither 32-bit nor 64-bit Flash on Linux supports GPU accelerated video.

HTML5+WebM will probably be here before official Flash 64-bit on Linux w/ GPU acceleration.

Anyone heard anything about Gnash?

---

### Post by Locke_99GS on 2010-06-05
> **null_pointer_us said:**
> HTML5+WebM will probably be here before official Flash 64-bit on Linux w/ GPU acceleration.

I agree.



> **null_pointer_us said:**
> 
Anyone heard anything about Gnash?

Nothing good.

---

### Post by ubername on 2010-06-06
Is there a 64 bit version newer than 10.0 r45 available? I looked on adobe labs and couldn't find one.

Reason I'm asking - latest version of google-chrome-unstable now keeps telling me 'the following plug-in has crashed: /usr/lib/mozilla/plugins/libflashplayer.so'

---

### Post by xebian on 2010-06-06
> **ubername said:**
> Is there a 64 bit version newer than 10.0 r45 available? I looked on adobe labs and couldn't find one.

Reason I'm asking - latest version of google-chrome-unstable now keeps telling me 'the following plug-in has crashed: /usr/lib/mozilla/plugins/libflashplayer.so'

Don't know why Adobe has been dragging their foot on 64-bit but Jobs is right when saying Adobe is lazy. M$ now has 64-bit so I don't see anymore reason for Adobe not to.  It's about time to let them know if they won't someone will.  Let's hope Google does it.

---

### Post by zika on 2010-06-06
> **ubername said:**
> Is there a 64 bit version newer than 10.0 r45 available? I looked on adobe labs and couldn't find one.

Reason I'm asking - latest version of google-chrome-unstable now keeps telling me 'the following plug-in has crashed: /usr/lib/mozilla/plugins/libflashplayer.so'
Chromium 6.0.427.0 (works)
FF 3.7 daily (works)
FF 3.7 nightly (in a $Home$sub-folder) (crashes)
Google-chrome 6.0.422.0.dev (crashes)
FF 3.6 (crashes)
...

---

### Post by gradinaruvasile on 2010-06-07
It is still prerelease. And i havent seen any improvement in the rcs (used all 7).

---

### Post by _khAttAm_ on 2010-06-07
I am sick of Flash. I have 64bit version from SevenMachines PPA installed, which does not work at all with Firefox and somehow works most of the time with Chromium 6.

I hope youtube sorts the transition to HTML5 out soon, so I don't have to depend on flash much.

---

### Post by pferraro on 2010-06-07
> **_khAttAm_ said:**
> I am sick of Flash. I have 64bit version from SevenMachines PPA installed, which does not work at all with Firefox and somehow works most of the time with Chromium 6.

I hope youtube sorts the transition to HTML5 out soon, so I don't have to depend on flash much.

Join the beta program, and you can watch flash-less youtube videos now:
[http://www.youtube.com/html5](http://www.youtube.com/html5)

---

### Post by Locke_99GS on 2010-06-07
I haven't gotten h264 working on Youtube yet, but WebM does work for me. I'm porobably just forgetting some package.

---

### Post by _khAttAm_ on 2010-06-08
> **pferraro said:**
> Join the beta program, and you can watch flash-less youtube videos now:
[http://www.youtube.com/html5](http://www.youtube.com/html5)

I have joined HTML5 beta several times, checked it and moved back to flash again.

The following issues bother me (sorted by minor to major):
1. In case I want to save the video after watching it, I can't find it in the /tmp like I normally would with Flash...
2. The progress bar displays that the whole of video is played. 
3. For full screen, I need to click the full screen button and then press F11....
4. On slow connection, you will really find jerky video.. it does not show if it has paused playing and waiting for it to buffer as Flash version does.
5. Videos with ads (and there are too many of them) will play with flash player and I need to have it installed anyways.. 

I'd rather use Totem to play videos.. but I may need to comment and do other stuff.. also it is not possible to use Totem to play a video that is embedded in another page than youtube.. Also, there are vimeo and other video sites which I may visit.. I found out FlashVideoReplacer for Firefox and it works as intended but the totem plugin requires the whole video to be streamed first only then it is able to play..

---

### Post by clyderino on 2010-06-09
I have Meerkat Netbook 10.10 alpha edition and cannot get Flash to work in YouTube (or anywhere) in Google Chrome (Flash works in Firefox.) 
HTML5 has been working very well on the YouTube site in Chrome: no problems noted with good speed of upload of videos.

---

### Post by Luke has no name on 2010-06-09
Much as I'm excited about HTML5 video taking over a lot of Flashy things...

I wish Ubuntu would use the x64 prerelease of Flash 10 in the repositories, if allowed. I don't care if it's not "production" by Adobe's claims, it is better than 32 bit Flash on x64. Adobe is foolish to leave this area waiting so long.

---

### Post by Merk42 on 2010-06-09
> **Luke has no name said:**
> <snip> Adobe is foolish to leave this area waiting so long.

More like Canonical is foolish to wait on Adobe

---

### Post by kurros on 2010-06-10
> **Locke_99GS said:**
> I haven't gotten h264 working on Youtube yet, but WebM does work for me. I'm porobably just forgetting some package.

Firefox and Chromium do not support h.264. Well, you can link chromium against a non-free ffmpeg but sites like YouTube wouldn't work because the supported mime types are hard-coded for non Chrome builds.

---

### Post by Locke_99GS on 2010-06-10
/me shakes fist at world

---

### Post by null_pointer_us on 2010-06-10
*world seems unfazed*

EDIT: But I share your sentiment.

---

### Post by joebipp on 2010-06-10
Hi everyone,
I install flash player 10.1 on Ubuntu 10.04  doing the following:
1. download flash player 10_1_rc7_Linux_060210_so.tar.gz and unzip the file libflashplayer.so
2. Opened up home directory, using Ctrl h brought up the hidden files, then open the folder called Mozilla and created the folder called plugins
3. I drag file libflashplayer.so into the desktop
4. Then I drag the file libflashplayer.so into the folder plugins
So far flash player seem to work fine.

---

### Post by Merk42 on 2010-06-10
Welp.

Guess 64bit Ubuntu has one less reason to be not recommended
[**They will have to use the 32bit version of Flash**](http://labs.adobe.com/technologies/flashplayer10/64bit.html)

---

