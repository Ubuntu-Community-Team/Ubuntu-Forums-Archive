---
title: "Flash 9 Final crashes like crazy! - easy to reproduce"
date: 2007-01-17
forum: Multimedia &amp; Video
---

### Post by sgarman on 2007-01-17
I found that the beta versions, as well as the final release of the Flash player v9 released today crashes Firefox and Epiphany browsers at the drop of a hat.

1. Go to YouTube or any other video site.
2. Start playing a video.
3. Hit your "Home" button or try navigating to a bookmark or other URL.

Result: The entire browser locks up and the "Force Quit" dialog appears after a few seconds when you click the "X" close button. 

Who else is seeing this? I can't be the only one. 

To install the plugin, I simply copied the files flashplayer.xpt and libflashplayer.so into /usr/lib/firefox/plugins as root.

I'm holding out hope that I might just be doing something stupid!

Scott

---

### Post by business.geek on 2007-01-17
> **sgarman said:**
> I found that the beta versions, as well as the final release of the Flash player v9 released today crashes Firefox and Epiphany browsers at the drop of a hat.

1. Go to YouTube or any other video site.
2. Start playing a video.
3. Hit your "Home" button or try navigating to a bookmark or other URL.

Result: The entire browser locks up and the "Force Quit" dialog appears after a few seconds when you click the "X" close button. 

Who else is seeing this? I can't be the only one. 

To install the plugin, I simply copied the files flashplayer.xpt and libflashplayer.so into /usr/lib/firefox/plugins as root.

I'm holding out hope that I might just be doing something stupid!

Scott


I just read [here]("http://www.desktoplinux.com/news/NS4744081663.html") that the new flash player supports only also.  isnt most ubuntu systems running on ESD?

---

### Post by sgarman on 2007-01-17
Thanks for the reply. It's true, Ubuntu uses esd under GNOME sessions. I'm using Ubuntu Edgy, btw. 

I just tried using aoss to run Firefox with "aoss firefox" but I get the same results. Audio sounds fine when playing the video. It seems that any interruption in video causes the plugin/browser to crash.

Scott

---

### Post by dorcssa on 2007-01-17
I had no problem when trying out your instructions..by the way, firefox rarely crashes. But I use the dapper version, 1.5. I heard that ff2 is a little unstable, that's why I want to stuck with 1.5. :)

---

### Post by ThrobbingBrain66 on 2007-01-17
> **sgarman said:**
> I found that the beta versions, as well as the final release of the Flash player v9 released today crashes Firefox and Epiphany browsers at the drop of a hat.

1. Go to YouTube or any other video site.
2. Start playing a video.
3. Hit your "Home" button or try navigating to a bookmark or other URL.

Result: The entire browser locks up and the "Force Quit" dialog appears after a few seconds when you click the "X" close button. 

Who else is seeing this? I can't be the only one. 

To install the plugin, I simply copied the files flashplayer.xpt and libflashplayer.so into /usr/lib/firefox/plugins as root.

I'm holding out hope that I might just be doing something stupid!

Scott

No problems here bro.

open up firefox and type about : plugins (there aren't supposed to be spaces on each side of the colon, but the colon and p kept turning into a smiley) into the address bar.  If the Flash Plugin Header doesn't give 'Shockwave Flash 9.0 r31' as the version, then you may also need to install the .so file to /usr/lib/flashplugin-nonfree/

---

### Post by Shay Stephens on 2007-01-17
I am getting that problem.  I have not deleted that dat file like the instructions said to do, so I am going to try that and see if it makes any difference.

---

### Post by rudder on 2007-01-17
Here's one to add to the discussion of flash player, two days ago I was watching a rather sweet compilation of slow motion explosions on break.com (that was *all* I had running at the time) and my entire system took a dump.  I had to reboot.  I am running Edgy (FF2.0) and the Flash stuff installed ala Automatix.

---

### Post by sgarman on 2007-01-17
Update: I have traced a large majority of the crashes to the Flashblock Firefox extension. When I disable or uninstall it, I can complete the steps I described above without crashing the browser.

However, there are still other circumstances where I've had a couple of browser crashes. I'm trying to make them reproducible and will report back if I'm able to.

---

### Post by Shay Stephens on 2007-01-18
The only extension in firefox I am using is NoScript.  I might try turning that off to see if it makes any difference.

---

### Post by pstglia on 2007-02-05
Hi friend,

I was having the same problem. I had created a symlink on plugin's directory (/usr/lib/firefox/plugins, in my case). Browser (Firefox 2.0.0.1) was crashing when viewing some flash contents (e.g [www.mundocanibal.com.br](www.mundocanibal.com.br), when trying to click animations).

After creating a symlink on ~/.mozilla/plugins, the problem didn't occur anymore.

Hope this helps




> **sgarman said:**
> I found that the beta versions, as well as the final release of the Flash player v9 released today crashes Firefox and Epiphany browsers at the drop of a hat.

1. Go to YouTube or any other video site.
2. Start playing a video.
3. Hit your "Home" button or try navigating to a bookmark or other URL.

Result: The entire browser locks up and the "Force Quit" dialog appears after a few seconds when you click the "X" close button. 

Who else is seeing this? I can't be the only one. 

To install the plugin, I simply copied the files flashplayer.xpt and libflashplayer.so into /usr/lib/firefox/plugins as root.

I'm holding out hope that I might just be doing something stupid!

Scott

---

### Post by jens_acamedia on 2007-02-13
i get this all the time with feisty. pretty much half of the youtube videos cause the kind of lockup where i have to force quit. i have no plugins or unusual stuff...

---

### Post by bpasdar on 2007-02-21
Interesting,

I just installed Feisty Herd 4 and have had a darnedest time getting flash to work without freezing the browser.  It froze out the browser 100% of the time. I disable sage and now it works.  

During this period, I was also playing around with Xgl, AIGLX, and Beryl.  So maybe that had something to do with it as well.  With my most recent test, I disabled Xgl and am running with AIGLX only with no Beryl or Beryl-Manager.

Babak
Security Intelligence in 5 minutes or less!
[http://DailySecurityBriefing.com](http://DailySecurityBriefing.com)

---

### Post by chris90uk on 2007-03-14
I am using Ubuntu Dapper and firefox 2 and am having the same problems as you. I am fine navigating the website and even watching the videos. But when I click back or something the program freezes so I have to force it to quit.

---

### Post by floogy on 2007-03-18
> **pstglia said:**
> Hi friend,

I was having the same problem. I had created a symlink on plugin's directory (/usr/lib/firefox/plugins, in my case). Browser (Firefox 2.0.0.1) was crashing when viewing some flash contents (e.g [www.mundocanibal.com.br](www.mundocanibal.com.br), when trying to click animations).

After creating a symlink on ~/.mozilla/plugins, the problem didn't occur anymore.

Hope this helps

Can you please elaborate which symlinks you created? A symlink got two parts: A source and a target... 

I got the problem after upgrade the "host/amd64"  to edgy. Strange: I had no problem with i386 chroot before. chroot was still upgraded to edgy, without this behaviour.  After upgrading the "host" to edgy too I got this problem.

---

### Post by namrocks on 2007-04-25
I have the same problem with FF freezing. Just installed Feisty. First ever Linux installation. Go to Youtube. Start any video. Watch for a minute. Hit back button to return to Youtube homepage. Click on another video, watch for a minute. Hit the back button. After 3-4 or so rounds of this FF reliably freezes. Force quit works. One time only I had to do a hard shutdown. I thought I left crashes behind with XP. :(

---

### Post by somewhat on 2007-04-28
exact some behavior here as above poster on Feisty - I can normally get through a few videos on youtube etc until firefox locks up. :-k

---

### Post by electragician on 2007-04-28
Exact same behaviour here as well. 

Go to youtube, watch a video, hit the back button, watch another. Somewhere between 1 and 4 videos will get you a guaranteed crash, and you'll have to force quit firefox.

I've had this happen over 3 different Feisty installs in the past few days, and have been unable to find a reliable fix. I've tried installing the non-free plugin from Synaptic and using Automatix to install Flash, and both have the same results.

---

### Post by Irtsi on 2007-04-29
Same problem here.

---

### Post by stryderjzw on 2007-04-29
> **pstglia said:**
> Hi friend,

I was having the same problem. I had created a symlink on plugin's directory (/usr/lib/firefox/plugins, in my case). Browser (Firefox 2.0.0.1) was crashing when viewing some flash contents (e.g [www.mundocanibal.com.br](www.mundocanibal.com.br), when trying to click animations).

After creating a symlink on ~/.mozilla/plugins, the problem didn't occur anymore.

Hope this helps

Hi.

I am having the exact same problem, and after being inspired by pstglia's instructions, it seems to be working fine after watching youtube videos.  Here is what I did.

Navigate to the ~/.mozilla/plugins folder.
```

cd ~/.mozilla/plugins

```

I have two files in there... flashplayer.xpt and libflashplayer.so.  Delete them.
```

rm flashplayer.xpt libflashplayer.so

```

I think then firefox will use the actual proper files located in /usr/lib/flashplugin-nonfree.

Hope that helps.

Justin

---

### Post by The Soundophiliac on 2007-04-29
I didn't have ~/.mozilla/plugins but I did sudo apt-get reinstall flashplugin-nonfree firefox and that seemed to work.

---

### Post by Drew Woodard on 2007-05-04
I am experiencing this same crashing problem.

 I have tried having the plugin in only ~/.mozilla/plugins when you install the plugin via the browser as a normal user
 in only /usr/lib/flashplugin-nonfree (with links to the two files in  /usr/lib/firefox/plugins) which is what you get if you install via the repositories
and having the plugins in both locations, as well as symlinking different locations as mentioned in previous posts

I have also tried the XLIB_SKIP_ARGB_VISUALS=1 in xorg.conf as mentioned here:
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/14911](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/14911)
and everything is running in 24bit color

this is on a fairly clean install of Kubuntu Feisty, everything is 32bit

I am wondering if this is some configuration thing that happened to be fixed by the previous posters reinstalling the plugins (but hasn't been effective for me yet for whatever reason) or perhaps we have some hardware in common and a audio or video driver bug is being triggered.


(relevant software)
Firefox 2.0.0.3 (same behavior can be triggered in Konqueror as well)
flash 9.0.31.0.2ubuntu1
nvidia-glx 1.0.9631

(relevant hardware)
nvidia geforce 7800gt
msi p6n sli-fi motherboard - nforce 650i chipset - realtek ALC888 audio chipset

---

### Post by SigmundFreud on 2007-05-04
I have the exact same problem. Watch a few Youtube vids, press back: guaranteed crash of Firefox. I found a bug report on Launchpad but as always no answers (except that it 'should be solved'). Apparently this only occurs with Firefox, not Opera (using the same Flash plugin). If anyone has a working solution I'd be happy to try it.

---

### Post by reyfer on 2007-05-04
I really don't understand how you installed the plugin? All of you talk about copying certain files to ~/mozilla/plugins and some other stuff. All I did back when I was on Edgy was getting the package from Adobe, unpack it, run the ./flasplayer-installer script, and that's it. I have no problem whatsoever, not even after upgrading to Feisty. Plugin is working great.

---

### Post by Drew Woodard on 2007-05-04
> **reyfer said:**
> I really don't understand how you installed the plugin? All of you talk about copying certain files to ~/mozilla/plugins and some other stuff. All I did back when I was on Edgy was getting the package from Adobe, unpack it, run the ./flasplayer-installer script, and that's it. I have no problem whatsoever, not even after upgrading to Feisty. Plugin is working great.

there are three common ways (that I am aware of) to install the flash plugin:
1.  install flashplugin-nonfree from the repos, which puts libflashplayer.so in /usr/lib/firefox/plugins/
2.  install via the browser when you get the green puzzle piece message saying you are missing a plugin, this puts flashplayer in ~/.mozilla/plugins/
3.  install using the install script from the adobe page like you mentioned, as far as I know this does the same thing as option2 assuming you run it as a normal user

The reason we were talking about moving files around or linking things is some people reported having different results using different install procedures.  Unfortunately some people such as myself have tried all of these different options and are still getting crashes.

---

### Post by LuisGMarine on 2007-05-04
Hey guys, 

since everyone here is talking abotu Youtube and Flash + firefox crashing, I would like to chime in on the matter.  I'm also having the problem, but on top of that I'm having another minor problem.  That is that my sound flickers when listening to videos.

I tried changing things from aoss to alsa to default in the sound options, but still to no avail.  I was just wondering if any of you guys out there were having the same problem and if you found a fix.

Thanks!

---

### Post by neels on 2007-05-06
flash 9 plugin, whichever way installed, hard crashes my entire Feisty.
Still waiting for solutions, if any.

However, I installed the Flash 7 plugin instead. The disadvantage with using 7 is that youtube videos will develop a video/sound skew after a minute or so, which does not appear in Flash 9. The upside to Flash 7 is that you don't have to hard boot your system constantly.

You can get the version 7 plugin from macromedia by replacing the 9 with a 7 in the link:```

wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_7_linux.tar.gz
```

This would be installed using procedure number 3., as mentioned above, by running the installer script found in the package.

---

### Post by LuisGMarine on 2007-05-06
I didn't even think about downgrading my flash version since I didn't know where to get the older versions.  I'm going to go ahead and give them a try, see what I can come up with and see if that might fix my sound problem.

I'm a huge internet surfer, and my biggest time consumed by it is watching YouTube videos and Liveleak, which are all Flash.  It just a bit irritating that my Linux system is working so well but then you have a little thing like flashing giving you problems.  Maybe this fix will work for me, I'm hoping that it might!

Good Luck

---

### Post by Drew Woodard on 2007-05-08
On a whim I disabled my onboard sound chipset in the bios and suddenly I could no longer cause Firefox to crash under the usual circumstances (typically closing a window with flash in it or navigating away from a page with flash in it).
When I turned sound back on it went back to the old behavior of crashing regularly on flash videos.

I still don't know what exactly is triggering this bug, but given that sound seems to be related, at least in my instance, I am wondering if it might be a sound driver issue or an Alsa issue.
I would be curious to know what sound processor is being used by other people encountering this problem.

according to the manufacturer website my audio chipset is "Realtek ALC888"
[http://global.msi.com.tw/index.php?func=proddesc&prod_no=1141&maincat_no=1&cat2_no=170](http://global.msi.com.tw/index.php?func=proddesc&prod_no=1141&maincat_no=1&cat2_no=170)

if I issue the console command:
aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

don't know why Alsa identifies it as an ALC883 when the manufacturer says it is an ALC888, perhaps both models use the same driver.

---

### Post by mam28 on 2007-05-08
It's definitely an onboard audio issue. Switched from onboard audio to sb live 24bit and problem stopped right away.:KS :KS :KS

---

### Post by Drew Woodard on 2007-05-09
> **mam28 said:**
> It's definitely an onboard audio issue. Switched from onboard audio to sb live 24bit and problem stopped right away.:KS :KS :KS

Interesting, do you know what kind of onboard sound you have or what the make of the motherboard is?

---

### Post by mam28 on 2007-05-09
Its realtek hd audio.

---

### Post by garyniger on 2007-05-13
If all else fails, use this "fix" I found on [http://www.mygeeknotes.com/2007/05/08/linux-firefox-flash-9-crash-workaround/](http://www.mygeeknotes.com/2007/05/08/linux-firefox-flash-9-crash-workaround/)

       1. Open up a browser window to some web page that has Flash 9 content on it - Yahoo, Digg, MSN, CNN or whatever - they all have ads in Flash (most times).
       2. Move that browser to another desktop or minimize it - make sure not to close it.
       3. Open a new browser and use that as your primary browser.

You see, the crash occurs when the last window with flash content is closed.  As long as you have a flash animation going on somewhere there will be no crashes. 

Good job Adobe!

---

### Post by deadgobby on 2007-05-13
I use to have the problem. But really no more since I installed 9 and this is how I did it.
[http://ubuntuforums.org/showthread.php?t=279990](http://ubuntuforums.org/showthread.php?t=279990)
 I all so installed flash blocker from Mozilla web site. It blocks all flash programs till I click on the flash player icon. When I do that. the flash player will start.  Most of the flash programs are advertisments and the pages do load faster when flash is blocked.

---

### Post by jlacroix on 2007-05-14
I'm having the same problem and I also have a realtek onboard sound card, please keep me updated if any progress is made. I'd like to get rid of this issue.

---

### Post by Drew Woodard on 2007-05-15
> **garyniger said:**
> If all else fails, use this "fix" I found on [http://www.mygeeknotes.com/2007/05/08/linux-firefox-flash-9-crash-workaround/](http://www.mygeeknotes.com/2007/05/08/linux-firefox-flash-9-crash-workaround/)

       1. Open up a browser window to some web page that has Flash 9 content on it - Yahoo, Digg, MSN, CNN or whatever - they all have ads in Flash (most times).
       2. Move that browser to another desktop or minimize it - make sure not to close it.
       3. Open a new browser and use that as your primary browser.

You see, the crash occurs when the last window with flash content is closed.  As long as you have a flash animation going on somewhere there will be no crashes. 

Good job Adobe!

good find, I tested this myself and it seems to work, hopefully it will help narrow down the problem.  I have mentioned it in the relevant bug reports
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/104470](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/104470)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/114363](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/114363)

---

### Post by jlacroix on 2007-05-15
I will try that too and let you guys know. I may have access to a PCI sound card, would that fix it?

The problem is that the sound card I may be able to use is not 6.1 compatible as much as mine is but I guess its a matter of me choosing the least worst evil.

---

### Post by redtrak on 2007-05-16
I'm having the same problems.  I just did a search for Realtek at Adobe's site and it seems they are having Realtek related issues with several of their products.

---

### Post by Totonno on 2007-05-19
Since this seems to be a pretty big issue and ALL the solutions proposed don't work in my case, I'm switching back to Windows. Amazingly enough, Explorer on Windows crashes less than Firefox on Ubuntu.
Sorry, I don't really care to know where the problem is, or if flash plugins are closed source, or the problem is ALSA or Firefox issue, friends,  I just DON'T CARE. 
I need something that works. I need a browser that browses and an OS that doesn't need hours of tweaking to make it work properly. 

Sadly, now it seems Ubuntu can't give me that.
Believe me, feels so bad switching back to windows after 3 years of being a proud Linux user, but it was getting TRULY annoying. I formatted some hours ago, and right now I'm writing from Explorer 7, and still no crashes. Browsing youtube, and still no crashes. Aaaah.

Seems sometimes we stereotype the fact that Windows crashes so much that we forget to give it a try. 

Totonno

---

### Post by SigmundFreud on 2007-05-22
Well, I experience the 'bug' but it's not that annoying fortunately. Still, if there's _any_ way this can be fixed (not counting the workaround above, which I have not tested yet) I'd be glad.

---

### Post by Kamakazie! on 2007-05-29
Same problem and same Realtek HD onboard audio for me.

Any updates on if this is fixed or anything yet?

---

### Post by jlacroix on 2007-05-29
No, not yet. Adobe is being blamed right now rather than a workaround being discovered. I don't expect a solution soon if at all. It looks like I'll have to buy a new sound card using money that I don't have.

---

### Post by promet on 2007-06-27
A moderate breakthrough, perhaps, for some of you. I have struggled long and hard with the Flash-plugin (various versions) and Firefox crashes. Most posts and howto's refer to different install methods for different flavors of the plugin, xorg.conf 24 bit default color adjustments, etc (if you've browsed the threads, you're aware of the usual suspects...) .

If none of these (quite possible) solutions have helped you, you may want to look into this. I found, after tinkering with my /etc/firefox/firefoxrc file adjusting "aoss", "alsa",  ```
FIREFOX_DSP="****"
``` etc. I figured out that the sound server configuration was affecting my flash-plugin effectiveness. 

After having failed in all other methods I figured I'd go down the "sound server" route. As it turns out, in my case at least, It is not the plugin (I ended up going with the automatically installed plugin in Firefox by removing all previous plugins, -from /home/user/.mozilla/plugins, etc.-  and going to google video and letting the browser do its auto-install of  'flash 9') or Ubuntu per se (I am  using 7.04 Feisty on an oldish laptop - Micron PC Transport GX, Pentium III 700 MHZ, 512 MB of ram) but the way Ubuntu and the Flash plugin interacts (again, in my case) with the sound server.

By [installing the pulseaudio sound server architecture]("http://www.pulseaudio.org/wiki/PerfectSetup") 

```
http://www.pulseaudio.org/wiki/PerfectSetup
```I found, in desperation, that it solved each and every one of the play, crash and usability problems with the flash plugin in 7.04, in fact I am listening to a Google Video lecture right now in an adjacent tab of Firefox as I write this.

I realise this is a rather rambling post, as I've just accomplished this and am too tired for a lucid review;  I just wanted to point this out. Please feel free to message me or respond here with any questions or requests for details. I hope this helps some of you folks out.

I uhhhh...feel rather free!
:p

peas,
Promet

---

### Post by paradoxni on 2007-08-18
anyone else try this pulse audio method?

---

### Post by cb474 on 2007-08-26
I'm having this problem, which I haven't solved yet. I'm currently running through trying the various fixes suggested here. I did discover this troubleshooting guide for Flash and Ubuntu, that has a couple ideas not explained clearly in this thread:

[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

---

### Post by brk3 on 2007-09-01
I have this problem like so many others. Why on earth haven't the devs come up with a suitable fix yet

---

### Post by plumsey on 2007-09-26
My Feisty Fawn was hanging with a white screen when Firefox was trying to run a Flash plug  in (driving me mad & about to give up on Ubuntu)

I installed the following from the Synaptic Package Manager & it fixed the bug :     

       **flashplugin-nonfree** .


:guitar:

---

### Post by plumsey on 2007-09-30
Well it didn't actually fix the bug !!!!

I was still getting intermittent  crashes..... 

I then tried the LIVE CD version of Simply MEPIS 6.5 (which is built on Ubuntu) 

This seems a far better distro - looks better & everything is configured for you i.e. Flash Player . Real Player etc.

I had no Firefox crashes at all using this distro !!!

I then compared the display settings between the 2 distros & found that Simply Mepis screen refresh was 60Hz & Ubuntu had set it to 70Hz.

I changed the setting to 60Hz & have had ( so far ) had no more crashes with Ubuntu & Firefox.

And  I thought Linux was supposed to be stable with one program crashing did not bring down  whole machine  !!

I now have one AMD64 machine dual booting Windows XP & Ubuntu & Simply MEPIS on another PC.

--------------------------------------

I have since tried using Envy ([http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)) to configure my ATI Radeon Xpress 200 graphics card & this has sorted everything out. No more crashes...

Many thanks to Alberto Milone to wrote the utility :)

---

### Post by telemetry on 2007-10-30
promet - thanks for your suggestion about changing firefox dsp.....My default was actually blank and i have just set it to : alsa        It will be interesting to see what happens but I've tried loads of different things with no luck.
I'll see how I get on with this.

---

### Post by SigmundFreud on 2007-11-01
Upgrading to Gutsy seems to have solved this problem for me. No Flash-based crashes yet (though Firefox seems to be relatively unstable itself).

---

### Post by B Rob on 2007-11-06
I've experienced freezes caused by flash objects since I updated Ubuntu to 7.10, usually after closing the second or third flash page or so. I tried deleting the flash plugin files in ~/.mozilla/plugins and I reinstalled flash player through the firefox automated plugin dealie (the puzzle piece icon thingie), This seemed to fix the problem until after about 8-10 flash pages, I fell victim to a crash that forced me to kill the firefox process before I could open another window. The ~/.mozilla/plugins directory is now empty.

Firefox will still freeze, but it's more tolerable now. I am trying to work around the problem, and I haven't tried leaving a window open with a flash object yet. I did find something strange in my investigation. I have /usr/lib/flashplugin-nonfree/libflashplayer.so like I'm supposed to have. I also looked in /usr/lib/firefox/plugins and found a file called flashplugin-alternative.so. I don't know if that is supposed to be here and if it has anything to do with the problem, but nobody has posted anything regarding such a file so I thought I should report it.

---

