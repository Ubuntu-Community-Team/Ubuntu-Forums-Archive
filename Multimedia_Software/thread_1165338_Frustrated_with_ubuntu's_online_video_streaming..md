---
title: "Frustrated with ubuntu's online video streaming."
date: 2009-05-20
forum: Multimedia Software
---

### Post by bhishan on 2009-05-20
I have tried almost all tutorials, read all posts in this forum to fix this problem I have, but am frustrated now. Nothing seems to help me. When I play videos online they flicker and freeze a lot in fullscreen mode. In the small/normal viewing mode it works good, but in the fullscreen mode, it simply does not work. I am using Jaunty in my Dell Inspiron 1525 laptop. I did not have this problem in Intrepid.

---

### Post by lovinglinux on 2009-05-20
Welcome to the club.

I also have issues not in full screen. I have managed to improve it with some tweaks, but I still have a lousy experience with flash on Jaunty.

---

### Post by fooman on 2009-05-20
same here with flash.

not sure about other sites....but for youtube,  i have found a very nice workaround:

install the greasemonkey extension for firefox,  then follow that up with the "youtube without flash" script form here:

[http://userscripts.org/scripts/show/41722](http://userscripts.org/scripts/show/41722)

fullscreen flash has never been clearer or smoother running.

enjoy.

---

### Post by @ntonius on 2009-05-20
Try to disable the visual effects
i had a same problem and was solved this way.

You can disable the effects by doing :
right click in desktop --> visual effects --> and select NONE

if this does not help there may be a flash prob. (i had that problem as well when upgraded from 8.10 to 9.04)
You can try to solve it by uninstalling all flash from the repositories
after that you reboot and you can install them again with the latest flash from adobe.

no need to follow any exotic command lines.only the simple steps above
i solved my probs this way.....you have nothing to loose to try

---

### Post by qjmoss on 2009-05-20
Alright guys, I've ran into this thread about 10 times, and this fixes it 9 outa 10 times ; ).


(in Jaunty only) by going to synaptic and clicking on Search (not quick search) and typing flash. The only packages you should see installed are ubuntu-restricted-extras and adobe-flashplugin. Any swfdec* or gnash packages should be marked for complete removal! (It will not break anything, it's the equivalent of purge remove)

---

### Post by qjmoss on 2009-05-20
And also, you will notice a tremendous in Jaunty, if you have an Intel chip. I've read the new kernel is not supporting it, and there is bugs,  I've fixed this problem for me too.


1. Download & install the 2.6.29.3 kernel, based on your architecture: 

i386 users
```
$ wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.3/linux-headers-2.6.29-02062903-generic_2.6.29-02062903_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.3/linux-headers-2.6.29-02062903_2.6.29-02062903_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.3/linux-image-2.6.29-02062903-generic_2.6.29-02062903_i386.deb
$ sudo dpkg -i linux-headers-2.6.29-02062903-generic_2.6.29-02062903_i386.deb linux-headers-2.6.29-02062903_2.6.29-02062903_all.deb linux-image-2.6.29-02062903-generic_2.6.29-02062903_i386.deb
```

64 bit
```
$ wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.3/linux-headers-2.6.29-02062903-generic_2.6.29-02062903_amd64.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.3/linux-headers-2.6.29-02062903_2.6.29-02062903_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.3/linux-image-2.6.29-02062903-generic_2.6.29-02062903_amd64.deb
$ sudo dpkg -i linux-headers-2.6.29-02062903-generic_2.6.29-02062903_amd64.deb linux-headers-2.6.29-02062903_2.6.29-02062903_all.deb linux-image-2.6.29-02062903-generic_2.6.29-02062903_amd64.deb
```


or visit

[http://http://ubuntuforums.org/showthread.php?t=1130582&highlight=Intel+chip+jaunty]("http://http://ubuntuforums.org/showthread.php?t=1130582&highlight=Intel+chip+jaunty")

---

### Post by lovinglinux on 2009-05-20
> **qjmoss said:**
> Alright guys, I've ran into this thread about 10 times, and this fixes it every time.

I think you should lower your statistics to "9 in 10 times", because I removed swfdec and gnash a long time ago, but flash experience is still terrible. 

I tried flash 9, flash 10, swfdec, gnash, different versions of nVidia driver and other tweaks. I'm currently only using flashplugin-nonfree with nVidia 173 driver. It works bad on Firefox, Opera, Shiretoko, Epiphany, you name it...

---

### Post by qjmoss on 2009-05-20
> **lovinglinux said:**
> I think you should lower your statistics to "9 in 10 times", because I removed swfdec and gnash a long time ago, but flash experience is still terrible. 

I tried flash 9, flash 10, swfdec, gnash, different versions of nVidia driver and other tweaks. I'm currently only using flashplugin-nonfree with nVidia 173 driver. It works bad on Firefox, Opera, Shiretoko, Epiphany, you name it...

This is strange, is it ONLY flash that you are having difficulty with, because..

Well like I said about the intel chips?

---

### Post by lovinglinux on 2009-05-20
> **qjmoss said:**
> This is strange, is it ONLY flash that you are having difficulty with, because..

Yes, just flash. When I use greasemonkey with a script to replace the flash player with gecko-mediaplayer it plays just fine. I don't have mplayer issues whatsoever and if I download the flv files and play them with VLC, it works flawlessly. Is not a bandwidth issue, because I have plenty of bandwidth and I see the loading bar way ahead of what I'm playing.


> **qjmoss said:**
> Well like I said about the intel chips?

Like I said, I don't use integrated graphics and I have nVidia, not Intel.

---

### Post by qjmoss on 2009-05-20
> **lovinglinux said:**
> Yes, just flash. When I use greasemonkey with a script to replace the flash player with gecko-mediaplayer it plays just fine. I don't have mplayer issues whatsoever and if I download the flv files and play them with VLC, it works flawlessly. Is not a bandwidth issue, because I have plenty of bandwidth and I see the loading bar way ahead of what I'm playing.

Well, I'm sorry that my little bit of information didn't help you. I've seen this solve problems like this many times.  But good luck, and I hope it helps the other guy..





> Like I said, I don't use integrated graphics and I have nVidia, not Intel.
I'm sorry i've must have missed that.

---

### Post by lovinglinux on 2009-05-20
BTW, I went to a web site where I had the option to use a fancy new flash player or a simpler old flash player. The old one had much better performance, which makes me guess that the problem is within flash plugin itself.

---

### Post by qjmoss on 2009-05-20
That's weird ](*,)


I'll look into this, and if I find anything that I think is even a little helpful i'll post it on this thread

---

### Post by lovinglinux on 2009-05-20
> **qjmoss said:**
> That's weird ](*,)


I'll look into this, and if I find anything that I think is even a little helpful i'll post it on this thread

Thanks. Youl will make a lot of people happy if you find the solution.

---

### Post by bhishan on 2009-05-20
> **fooman said:**
> same here with flash.

not sure about other sites....but for youtube,  i have found a very nice workaround:

install the greasemonkey extension for firefox,  then follow that up with the "youtube without flash" script form here:

[http://userscripts.org/scripts/show/41722](http://userscripts.org/scripts/show/41722)

fullscreen flash has never been clearer or smoother running.

enjoy.

Thank you for the reply. The option to make the video fullscreen disappears in without flash mode. How do I make the video fullscreen in without flash mode? And this works only for youtube.

---

### Post by bhishan on 2009-05-20
> **@ntonius said:**
> Try to disable the visual effects
i had a same problem and was solved this way.

You can disable the effects by doing :
right click in desktop --> visual effects --> and select NONE

if this does not help there may be a flash prob. (i had that problem as well when upgraded from 8.10 to 9.04)
You can try to solve it by uninstalling all flash from the repositories
after that you reboot and you can install them again with the latest flash from adobe.

no need to follow any exotic command lines.only the simple steps above
i solved my probs this way.....you have nothing to loose to try

Thanks for the reply. Disabling the visual effects still didn't work. I have tried uninstalling all flash and installing the one from adobe more than 20 times. Still doesn't work. What else do u think might be wrong?

---

### Post by fooman on 2009-05-20
> **bhishan said:**
> Thank you for the reply. The option to make the video fullscreen disappears in without flash mode. How do I make the video fullscreen in without flash mode? And this works only for youtube.

try pressing the "f" key or just do a quick double-click on the video as it plays.

and yeah...only for youtube afaik

---

### Post by bhishan on 2009-05-20
> **qjmoss said:**
> Alright guys, I've ran into this thread about 10 times, and this fixes it 9 outa 10 times ; ).


(in Jaunty only) by going to synaptic and clicking on Search (not quick search) and typing flash. The only packages you should see installed are ubuntu-restricted-extras and adobe-flashplugin. Any swfdec* or gnash packages should be marked for complete removal! (It will not break anything, it's the equivalent of purge remove)

When I did as u mentioned, there were three packages installed: ubuntu-restricted-extras, adobe-flashplugin and flashplugin-installer. swfdec* or gnash packages are not installed.

---

### Post by lovinglinux on 2009-05-20
> **bhishan said:**
> When I did as u mentioned, there were three packages installed: ubuntu-restricted-extras, adobe-flashplugin and flashplugin-installer. swfdec* or gnash packages are not installed.

Wait a second. I don't have any adobe-flashplugin, just flashplugin-installer, flashplugin-nonfree (which is just a transitional package) and flashplugin-nonfree-extrasound (which I guess is the equivalent of the libflashsupport). Where did you get that?

---

### Post by Ceiber Boy on 2009-05-20
this is a really annoying problem as BBC iplayer uses flash, dont care about ITV and MS Silverlight even thought that is another can of worms!

Dose anyone out their have a definitive solution to this problem?

---

### Post by qjmoss on 2009-05-20
> **lovinglinux said:**
> Wait a second. I don't have any adobe-flashplugin, just flashplugin-installer, flashplugin-nonfree (which is just a transitional package) and flashplugin-nonfree-extrasound (which I guess is the equivalent of the libflashsupport). Where did you get that?

Okay update me on where your at in this.

Let's try to get this figured out

---

### Post by bhishan on 2009-05-21
I didn't know till yesterday that my CPU supports 64 bits. I installed 64 bit ubuntu yesterday. After the installation I installed adobe-flashplugin and all of a sudden online videos began to work fine. But the videos from [http://cnettv.cnet.com/](http://cnettv.cnet.com/) doesnot work. Anyway overall, it is better than before.

---

### Post by durand on 2009-05-21
Just remembered something. If you right click on a flash program and click on settings, is "Enable hardware acceleration" ticked?

---

### Post by bhishan on 2009-05-21
> **durand said:**
> Just remembered something. If you right click on a flash program and click on settings, is "Enable hardware acceleration" ticked?

Yes it is ticked. And about the videos from cnettv I mentioned earlier, whenever I try to play them, firefox freezes and I have to force quit.

---

### Post by durand on 2009-05-21
Hmm, I also still have this problem :S It seems to work properly in crunchbang linux (32bit) but not in ubuntu (64bit) and I'm not really sure why.

---

### Post by Orographic on 2009-05-21
I'm having this issue too. I have a Gigabyte 945GZM--S2 with intel onboard graphics. This same setup worked perfectly on Intrepid for full screen video but both iView and YouTube wont run properly in Jaunty on this same machine.

This is about as big as I can run iView on my 21.5" Benq, 1920 x 1080. Any bigger and it fragments and crashes. It worked perfectly in Intrepid.

[http://www.blackheathweather.com/whirlpoolimages/iViewscreenshot1b.png](http://www.blackheathweather.com/whirlpoolimages/iViewscreenshot1b.png)

---

### Post by geezer70 on 2009-05-21
> **qjmoss said:**
> Alright guys, I've ran into this thread about 10 times, and this fixes it 9 outa 10 times ; ).


(in Jaunty only) by going to synaptic and clicking on Search (not quick search) and typing flash. The only packages you should see installed are ubuntu-restricted-extras and adobe-flashplugin. Any swfdec* or gnash packages should be marked for complete removal! (It will not break anything, it's the equivalent of purge remove)


Thanks very much..I only had to remove swfdec since gnash was never loaded and now
I have no more black screens. Full view also works. Video card is nVidia GeForce 6200.
New to Ubuntu 9.04 and have never used any Ubuntu OS's before but I like the looks
and ease of operation. I have used Red Hat, Suse, and PClinux in the past.  PClinux 2009 OS loaded video driver and necessary video streaming files during setup.  Thanks

---

### Post by primat3 on 2009-05-21
> **qjmoss said:**
> Alright guys, I've ran into this thread about 10 times, and this fixes it 9 outa 10 times ; ).


(in Jaunty only) by going to synaptic and clicking on Search (not quick search) and typing flash. The only packages you should see installed are ubuntu-restricted-extras and adobe-flashplugin. Any swfdec* or gnash packages should be marked for complete removal! (It will not break anything, it's the equivalent of purge remove)


I think I love you... I had tried everything for days!! and this simple fix did it for me. Thanks!!!   ):P

---

### Post by Orographic on 2009-05-22
When I do that 'flash' search, I have Adobe Flash Player plugin installer and Adobe Flash Player plugin installer (transitional package) and Ubuntu Restricted Areas.

Is that okay?

I still have fragmented, stuttery video at full screen with these installed. It was perfect in Intrepid on the same machine.

---

### Post by warroomcbw on 2009-05-22
quick question.

There is a video stream I am having trouble with.  It's not a pirate thing or anything like that.  It's just a worship and prayer room that never stops 24/7 out of Kansas City.  You have to have a subscription for it to handle the demand on their end.


I can get the audio to play(smplayer) pasting the url
I can get the video to play (smplayer or firefox.)
But not together...I can open two instances, one video and the other audio
but they aren't in sink.  I followed the "how to" for jaunty

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

alsa and pulse audio.

Is there a magic command I'm missing here?  This is the best version of ubuntu I've ever tried.  It has really come a long way.  First time everything (almost) worked after install.

newbie compared to you guys,
cbw

---

### Post by polytropos on 2009-05-23
> **qjmoss said:**
> Alright guys, I've ran into this thread about 10 times, and this fixes it 9 outa 10 times ; ).


(in Jaunty only) by going to synaptic and clicking on Search (not quick search) and typing flash. The only packages you should see installed are ubuntu-restricted-extras and adobe-flashplugin. Any swfdec* or gnash packages should be marked for complete removal! (It will not break anything, it's the equivalent of purge remove)

I tried this, but it did not improve my fullscreen video when streaming from Firefox--the video still jerks, although the audio is fine.

Also, trying this fix changed the font that text appears in Firefox--I'd like the old font back, but this is a minor issue compared to the fullscreen video jerking.

Any help?

---

### Post by JaguarXJ7 on 2009-05-26
Thanks [B]qjmoss

I followed your directions and can now enjoy video streaming again.  The only thing I did different was I marked the [/B]Flash Player plugin installer **to reinstall**; I figured what the heck.

---

### Post by steelsparky on 2009-05-26
Another thanks to qjmoss, had a bunch of mozilla add-ons in there. Works great now

---

### Post by Jerbil on 2009-05-27
I also cannot play certain videos properly. Youtube videos work fine in standard view, but in fullscreen it was unwatchable, too choppy. The BBC iPlayer is unwatchable in bot standard view and fullscreen, even when I downloaded the file it was still unwatchable, so maybe its a problem with the flash player. I also had this problem with Intrepid, I hoped the upgrade to Jaunty would help, but it didn't

---

### Post by Orographic on 2009-05-28
Go into the Video forums, there is a clear help setup there, it fixed my problems completely which were the same as yours.

---

### Post by union two levers on 2009-05-30
thank-you so much for this fix, i am not proud of my ignorance of using linux but this solved my problem.thanks qjmoss

---

### Post by elevashun on 2009-05-30
> **union two levers said:**
> thank-you so much for this fix, i am not proud of my ignorance of using linux but this solved my problem.thanks qjmoss

I'm having the same problems. Which solution are you referring to?

---

### Post by gliding4me on 2009-05-30
More thanks to qjmoss. Your adobe-flashplugin and ubuntu-restricted-extras flash package selection fix has just worked for me also.

---

### Post by Muskegman on 2009-06-02
Im also having some grief with flash, only seems to happen in firefox, I am also using a Nvidia card,all my games work flawlessly .

---

### Post by joem1 on 2009-06-09
despite following the advice of qjmoss, i am still having this problem.  When i searched for flash in the synaptic, the only other ones i had installed were the installers.  but i completely removed them and still the flickering full screen.  I just installed ubuntu 9.04 on a compaq presario 2200 laptop, running an intel celeron.  I had plenty of ram to run video with windows xp.

thanks.

---

### Post by elevashun on 2009-06-15
Also tried the recommended fix, still no fix. Anyone have any other suggestions?

---

### Post by polytropos on 2009-06-22
It's been four weeks since my last post to this thread, and still the problem persists.  My problem, again, occurs only when attempting to watch a stream in full-screen mode, and the problem is only with glitchy video--the audio streams perfectly.  Advice?

---

### Post by durand on 2009-06-22
Not really a solution but I just zoom in with compiz to watch a video when it is not in fullscreen.

---

### Post by zevans on 2009-06-23
> **polytropos said:**
> It's been four weeks since my last post to this thread, and still the problem persists.  My problem, again, occurs only when attempting to watch a stream in full-screen mode, and the problem is only with glitchy video--the audio streams perfectly.  Advice?

Since you didn't say in your original post... you on ATI, Intel, or nVidia?

---

### Post by swisstone198 on 2009-06-27
Make sure unredirect fullscreen windows is turned OFF in compiz config settings manager (under the general options). 

This has just sorted the problem for me. 

I'm a very happy boy now.

---

### Post by durand on 2009-06-27
> **swisstone198 said:**
> Make sure unredirect fullscreen windows is turned OFF in compiz config settings manager (under the general options). 

This has just sorted the problem for me. 

I'm a very happy boy now.

WOW, thanks! Works in karmic :D

---

### Post by Plumtreed on 2009-06-28
Thanx GJMoss,:KS I removed one reference to swfdec and that fixed my video/sound difficulties on 9.04.

I very much appreciate your help.....:D  I was searching for things to add not remove.

---

### Post by joem1 on 2009-07-12
Hello,

I am having the problem with choppy full screen video.  I have searched for answers to this problem, but can't find the solution.  I am running a compaq pasario 2200 with an intel celeron.  

I followed the tutorial here to a tea:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

One important thing is that i am working on a fresh install of 9.04.  and immediately after the install, without any changes, the screen is perfect on a restart.  after i followed the first 2 parts of the tutorial, now while the OS is booting up, there is a short screen glitch, followed by about 1 second of 1 inch green bars (like a bar code across the entire screen) at the top just before the ubuntu introduction screen (with the progress bar).  This was not there before i followed this tutorial, and i followed it very closely, without noticing any errors.  I thought everything went well.  Now it is there every time (as well as an instantaneous screen glitch on shut down).

Also, I have checked the [qjmoss]("http://ubuntuforums.org/member.php?u=664993") fix from this thread (i only had the recommended packages installed, so i didn't change anything).

Also, I wanted to try to turn off the unredirect fullscreen windows in compiz config settings manager, but i honestly don't know where to find the compiz config settings.

I have yet to try the workaround with greasemonkey, but i am hoping to be able to use flash...

I have tried it with the visual effects on and off, and it doesn't make a difference to the video performance.  

Oh, and i have not tried the "[HOWTO: Jaunty Intel Graphics Performance Guide]("http://ubuntuforums.org/showthread.php?t=1130582")" yet, because i am scared of messing things up.

Anyone have ideas?  I would really like to be able to stream video in full screen.  

Thanks,
Joe

---

### Post by durand on 2009-07-12
You need to install the compiz settings manager. Search for compizconfig-settings-manager in synaptic (System>Administration>Synaptic Package Manager) or click this link: [apt:compizconfig-settings-manager]("apt:compizconfig-settings-manager")

---

### Post by joem1 on 2009-07-12
Hi,
Thanks Durand.  So i turned off the unredirect fullscreen windows in compiz config settings manager, and it didn't improve the performance of the fullscreen video...

though, now the laptop touchpad works less well during videos (whether it is in full screen or regular size).

Any other ideas?

---

### Post by durand on 2009-07-12
Try watching the video without desktop effects. My last resort was to use compiz zoom on the small scale video and watch it like that. I really, really have no idea why flash is so bugged.

---

### Post by joem1 on 2009-07-12
I have tried it without the effects.  And i could do the zoom.  but i think there is a bigger issue going on.  as evidence by the green bar code like thing before the ubuntu startup screen.  and also, i am noticing that websites seem to consistently go static.  this happened before i followed the tutorial, but it seems strange...

--------------

So, now i followed the tutorial here:
**"HOWTO: Jaunty Intel Graphics Performance Guide"**
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)
and now I can't get any full screen streaming video.  the screen just goes gray. the sounds still works and it returns to the normal screen very easily with the "esc" key.

also, I tried a couple of the adjustments from this page, but it didn't seem to help:
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

I also get more static just before the computer powers down when i restart or shutdown.  a page that is 60% static quickly flashes on the screen just before the power goes off.  with shutdown, there is a beep noise before the flash of static prior to powering down.

---------------
one last thing, many webpages don't seem to fully load any more.  they load to the degree necessary to see everything and to fully function, but the progress bar never fully completes.  there is often just a tiny bit left...

any ideas?
sorry i am having such a problem with this...

---

### Post by hdemarzo on 2010-11-22
I find that no matter what browser I am using, the streaming video is choppy, and a little buggy when i come out of full screen.  I tried the visual effects thing, but the stream just freaks.  I also installed prelinking. It helped to make the overall OS be a little snappier.  Why does windows have such better streaming video, other than its windows and its a paid program.  Is it just the flash plugin that makes the quality so crappy??  Can anyone help?  ive been using Ubuntu 10.04 for about 3 months with a 3 week windows stint in the middle of it.  I love most everything about linux except for the fullscreen streaming video performance.  PLEASE HELP!  can we plead with conical to shy away from unity and focus on the streaming video problem??  Also i am having trouble with my microphone, help with that also??

---

### Post by bhishan on 2010-11-23
I find it a little slower but it works fine while playing videos for me. I am using Ubuntu 10.10 though. Although, sometimes when I try to play videos on full screen the video freezes while the audio plays on. I have to repeatedly switch between normal screen and full screen for it to work.

---

### Post by hdemarzo on 2010-11-23
I cant get 10.10 to work for me

---

### Post by durand on 2010-11-23
It's a combination of crappy flash player and crappy graphics drivers, both of which are closed source and both of which ubuntu can do nothing about. Sorry :( You could try running Firefox or something in wine and then install flash player in that. It might work.

---

### Post by hdemarzo on 2010-11-23
like install flash in wine?  i am also currently running firefox, opera, and chrome( not at the same time of coarse lol)

---

### Post by durand on 2010-11-23
Yeah, I've heard that's worked before but it's not a particularly great solution. I've even heard of using the flash player with wine embedded in a linux web browser but I can't find much info on it anymore.

---

### Post by hdemarzo on 2010-11-23
I just found a way to get streaming video from the web working.....using the default movie player that comes with ubuntu...or whatever flavor of linux you are using,  get the download address of the video you want to watch.   Then choose open location and paste the address in the box.  *poof*  the video can be played in full screen with no lag or choppy pixles!!!   hope it works for you guys  good luk

---

### Post by MTZ4 on 2011-02-16
Hi, i looked all over this forum and nothing helped me. tried it all. Maby i didn't had the same problem, i have a Nvidia, gaforce 8200 (not labtop) using ubuntu 10.10 and my flash worked really bad (youtube and flash games). then all i did was to change the flash settings, i unmarked "unable hardware acceleration". and all works really good now. Don't know if it will help.. worth to try.

---

### Post by avocadorange on 2011-03-15
I have been frustrated with this problem too and have posted in other threads about this. I tried the suggestion of re-installing Adobe Flash in synaptic and making sure I only had the Ubuntu restricted extras, but that made no difference.

I should add that the first few weeks of Ubuntu, streaming video worked fine. For a few months now I've had this problem though. I'm trying to be patient and work on finding a solution when I have time. Any other help will be much appreciated.

---

### Post by 1fstwgn on 2011-03-19
This worked for me flash video couldn't be smoother now if your running a 64bit processor it may work for you too.
[http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

---

### Post by nosmokenofire on 2011-03-22
I have this problem also.

I watch films using Quicksilverscreen. Before no problem, but now impossible to watch due to choppiness. The video seems to buffer well (the buffering indicator races ahead of the playback) so it doesn't seem to be a problem of bandwidth.

I have checked all the posts, some solutions I have tried to no avail others are a bit technical for me and others (for example right click on a flash window doesn't allow me to choose "settings" only "global settings") i cant get to work.

Any help would be greatly appreceated. I'm using lucid 32bit.

many thanks.

---

### Post by kelvin spratt on 2011-03-22
> **bhishan said:**
> Yes it is ticked. And about the videos from cnettv I mentioned earlier, whenever I try to play them, firefox freezes and I have to force quit.
Try unticking it some cards can't handle video exelaration

---

### Post by gmolivier on 2011-04-10
> **@ntonius said:**
> Try to disable the visual effects
i had a same problem and was solved this way.

You can disable the effects by doing :
right click in desktop --> visual effects --> and select NONE

if this does not help there may be a flash prob. (i had that problem as well when upgraded from 8.10 to 9.04)
You can try to solve it by uninstalling all flash from the repositories
after that you reboot and you can install them again with the latest flash from adobe.

no need to follow any exotic command lines.only the simple steps above
i solved my probs this way.....you have nothing to loose to try
Advice given @ntonius: 
"You can disable the effects by doing :
right click in desktop --> visual effects --> and select NONE"

When i right click in desktop i don't get "visual effects"...so, where is visual effects

---

### Post by nosmokenofire on 2011-05-23
I have solved my problem:

I removed the 4 years worth of dust from the cooling system in my laptop. It looked like a 3mm thick piece of felt... Streaming is now back to normal. I am fairly sure that this is what solved my problem. Can anyone confirm that an overheating processor would slow things up like this? (probably a very stupid question...)

Many thanks.

---

