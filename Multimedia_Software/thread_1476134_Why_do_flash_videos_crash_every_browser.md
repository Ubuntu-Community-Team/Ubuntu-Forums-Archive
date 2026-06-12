---
title: "Why do flash videos crash every browser?"
date: 2010-05-07
forum: Multimedia Software
---

### Post by mistermentality on 2010-05-07
I have Ubuntu 10 LTS and have searched the forums and internet yet not resolved this issue so hope I`ve posted in the right place.

I have installed, via the Ubuntu software manager, the latest Adobe Flash as every browser I try crashes within at most ten minutes of trying to play a flash video full screen, usually within four minutes.

I cannot play anything on BBC Iplayer or Youtube fullscreen and I have no idea why. I have the latest Flash plugin and have tried Chromium, Midori, Firefox, Opera, Conkerer (not Konqueror) and Epiphany and every one crashes.

Tried firefox in safe mode and it still happens, Opera just stops playing the video but all the other browsers crash except Chromium which tells me the flash plugin stopped working.

I really need it working and don`t want to have to return to Windows just for Flash so has any one an idea where I can start in solving it?

---

### Post by mistermentality on 2010-05-07
Am puzzled why it crashes so tried the beta of Chrome which when enabled has a built in flash plugin but that also crashes when full screen on Flash.

So every flash plugin for every browser crashes full screen yet I have a standard installation so any help appreciated but it looks like it`s going to have be Windows otherwise.

Alternatively is there a way to view flash without Adobe flash player?

---

### Post by WinterRain on 2010-05-07
Have you tried the flash plugin from adobe's website? [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
Remove the one you installed first.

Btw, are you running 64bit ubuntu?

---

### Post by tgalati4 on 2010-05-07
Try running firefox in terminal:

firefox --debug

Run your flash videos until crash.  Examine what remains in the terminal.

Usually, flash videos are software rendered because there are no provisions for hardware acceleration in linux.  When doing full screen rendering, CPU gets maxed out, frames are dropped and flash does not exit gracefully, often taking the browser with it.

As services move to HTML5, which is an open, multimedia protocol, the need for flash will decrease and hopefully your video experience will be better.

Apple is putting pressure on Adobe by not allowing flash on iPhones for precisely this reason.  They don't want iPhones to crash because of Adobe's crappy flash programming.

I would be surprised if Adobe opens up flash, but that is really what is needed to fix the performance problems in linux.

Send Adobe an email in the meantime describing your experience.  If enough people bother them, they may do something.

Like continue to ignore us.

---

### Post by mistermentality on 2010-05-07
Thanks for the replies.

I can`t download the one from Adobes site as when I click the download link it tells me it`s not an apt package even though it`s the right link.

But the one I installed via the ubuntu software manager was the one from Adobe, it says on the more info about it that it downloads the package from their site so should be the official one.

When I run firefox I see lots of the message....
```
Gdk-WARNING **: XID collision, trouble ahead
```
before it crashes, if run from a terminal.

In Chrome or Chromium (tried both) I get the message the flash plugin has failed along with the unhappy face error picture that Chrome shows.

It`s standard 32 bit Ubuntu 10 LTS, wanted to try a 64 bits OS but was concerned about compatability with my pc hardware.

I`ve tried Youtubes html5 trial, unfortunately it won`t let me zoom videos full screen but it makes them larger than standard youtube videos usually are on screen, which is good.

I don`t know how to uninstall flash, I know I can via the package manager but this would not remove Firefox`s plugin as far as I know and the error was happening before installing the newer Flash from Adobe.

So am still confused.

---

### Post by Yellow Pasque on 2010-05-07
Out of curiosity, what video card/driver are you using?
```
sudo apt-get install mesa-utils
glxinfo
```

---

### Post by lykwydchykyn on 2010-05-07
I see that GID error all the time, and I'm not having troubles with Flash crashing my browser, so I would conclude that they are not necessarily related.

Changing browsers isn't going to make a difference, since they all use the same flash plugin.

Off the top of my head, here are things that could be causing flash to crash the browser:
 
 - incompatibility with your video chipset.  What make/model is it? If you don't know, try running "lspci |grep -i vga" and paste the output here.

 - incompatibility with compiz (desktop effects) when using your video chipset.  Have you tried disabling desktop effects to see if helps?

 - Using an old version of flash, possibly installed to your home directory.  In firefox, go to "about:plugins" to see what version your flash plugin is.  Is it the most recent one shown on Adobe's site and/or the repositories?  If not, look in ~/.mozilla/firefox/plugins to see if an old version of flash is hiding there.

I guess there are other possibilities too, but check those and see if anything comes to light.

---

### Post by mistermentality on 2010-05-07
I have tried the firefox flash plugin, then installed Adobes newest one and tried every browser I can find and all do the same.

I have an Nvidia 7600 GS running on the official Nvidia drivers. Have had the problem since installing Ubuntu, I did today add Compiz to get rid of Video tearing on VLC but this has not made the flash player worse or better so seems to not affect it.

Regarding the flash plugin, some use a different plugin for example the beta of Chrome uses a built in flash plugin (has a g in the name and has to be enabled via the command line). It is the official Adobe one they use but by including it in the program Google believe it should improve stability but this plugin also crashes.

It crashes on Iplayer and Youtube, I know they both use flash but am wondering could it be the video codec? I don`t know if the sites use the same codec but on trying the html5 version of youtube if I enlarge the player and the whole player is on screen at once the video renderer of Chromium crashes.

I know that was a reported bug on 64 bit Ubuntu last year but it was said to have been fixed so not sure.

However I am wondering if this could be as simple as a codec issue somehow, but then can`t see how that would not affect it when out of full screen mode in flash.

---

### Post by tgalati4 on 2010-05-07
Try monitoring your CPU load during flash playback:

sudo apt-get install htop
htop

If you are hitting 100% during full screen playback then you will be dropping frames and flash doesn't handle that very well.

---

### Post by mistermentality on 2010-05-08
I just tried checking cpu usage, bearing in mind that at the time I monitored cpu usage it also has a download manager manager active that uses 28 to thirty five percent of cpu the cpu usage was 62 percent when also running full screen flash.

This is on a dual core pentium D 3.4 Ghz pc with 2 Gigabyte RAM and 520 GB of SATA hard drive space so it seems it`s not cpu usage causing the issue.

It`s really annoying now, I can`t even watch click from the bbc as the iplayer crashes. I`m sure there`s an answer that doesn`t involve Windows.

I hope.

---

### Post by mistermentality on 2010-05-08
I give up, seriously think I`ll have to use Windows which sucks just to play Flash but have even uninstalled flash then reinstalled only the official one and it still happens so looks like while I can Windows doesn`t crack a sweat with flash for some reason the same pc with Linux just doesn`t handle it :(

---

### Post by freedomisok on 2010-05-10
Same problem to me: all the browsers crash when you play full screen but...

... have you tried to watch a fullscreen video on pornhub.com? :)

it doesnt crash!!! it works perfectly!

any suggestion? isn't this weird?

thanx guys

---

