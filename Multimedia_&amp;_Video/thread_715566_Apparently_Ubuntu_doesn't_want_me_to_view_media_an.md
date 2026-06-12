---
title: "Apparently Ubuntu doesn't want me to view media anymore"
date: 2008-03-05
forum: Multimedia &amp; Video
---

### Post by KARaidl on 2008-03-05
So plain and simple, media files have simply working for me. I can't play .wmv files or .wav files, nor can I view anything with the Mplayer Firefox plugin.

In Totem, the window will turn that horrible gray and lock up, making me force quit. Mplayer simply does not open the file, and tells me it is unable to. And VLC DOES display the file, but the controls are missing and as soon as I try to click on anything, the window turns gray, so I force quit.

In Firefox, videos will not display at all, and Firefox will lock up, although I don't even get the option of force quitting here. I have to go into System Monitor and kill the process. If I try to shut down while Firefox is experiencing this lock up, Gutsy will freeze entirely, and I have to power off manually.

Since I enjoy a good overkill, I originally tried fixing the problem by completely reinstalling, but the issue showed up a few hours later.

Anyone help?

---

### Post by 6205 on 2008-03-05
Believe me, nothing is better for these file types than properly licenced Fluendo codecs and once you buy them, you will never look back...It's clean, simple, legal and really working solution for defaut Totem Gstreamer movie player in Ubuntu also with smooth video streaming in default Totem Mozilla plugin. And for other formats like Matroska or various DivX files i am using Mplayer anyway (without stolen w32 codecs of course...) [http://ubuntuforums.org/showthread.php?t=639393](http://ubuntuforums.org/showthread.php?t=639393)

Product info >>> [https://shop.fluendo.com/product_info.php?products_id=42&osCsid=npnstpukljngoo0dojsjrl81p1](https://shop.fluendo.com/product_info.php?products_id=42&osCsid=npnstpukljngoo0dojsjrl81p1)

---

### Post by nutz on 2008-03-05
Were you viewing anything offensive? Perhaps the computer got offended and cut you off. This happens when I fire up one of my necropyrobeastiality videos. I think my computer may be trying to censor my activities.

---

### Post by 6205 on 2008-03-05
> **nutz said:**
> Were you viewing anything offensive? Perhaps the computer got offended and cut you off. This happens when I fire up one of my necropyrobeastiality videos. I think my computer may be trying to censor my activities.


LOL, linux has no auto-censoring capabilities, it is not possible even on Windoze. But maybe on Vista with parental controls enabled is certain censorship enabled on some games and comercial DVD's for sure...What are necropyrobeastiality videos anyway and who will like to watch such a sick nonsense :(

---

### Post by nutz on 2008-03-05
> **6205 said:**
> LOL, linux has no auto-censoring capabilities, it is not possible even on Windoze. But maybe on Vista with parental controls enabled is certain censorship enabled on some games and comercial DVD's for sure...What are necropyrobeastiality videos anyway and who will like to watch such a sick nonsense :(


Oh I wasn't watching them. I was producing them...:twisted:

---

### Post by KARaidl on 2008-03-06
> **6205 said:**
> Believe me, nothing is better for these file types than properly licenced Fluendo codecs and once you buy them, you will never look back...It's clean, simple, legal and really working solution for defaut Totem Gstreamer movie player in Ubuntu also with smooth video streaming in default Totem Mozilla plugin. And for other formats like Matroska or various DivX files i am using Mplayer anyway (without stolen w32 codecs of course...) [http://ubuntuforums.org/showthread.php?t=639393](http://ubuntuforums.org/showthread.php?t=639393)

Product info >>> [https://shop.fluendo.com/product_info.php?products_id=42&osCsid=npnstpukljngoo0dojsjrl81p1](https://shop.fluendo.com/product_info.php?products_id=42&osCsid=npnstpukljngoo0dojsjrl81p1)

Well... awesome. But, that doesn't really solve anything.

First off, the website you posted is using some kind of foreign currency I'm not familiar with. (EDIT: Ok, that was the Euro. Now I feel dumb. And 44 bucks?? Ouch...)

Secondly, I've already paid for codecs in Windows, I've paid for my DVD drive, and I've acquired all my media legally. I just don't feel the need to shell out more money.

Thirdly, everything was working just fine before, and this problem has developed the exact same way twice now on two installs. I know it can work, so I'd rather fix it. Plus there's no guarantee that new codecs are going to help, and I'd rather not pay money for something I'm not sure is going to fix the problem.

---

### Post by KARaidl on 2008-03-06
> **nutz said:**
> Were you viewing anything offensive? Perhaps the computer got offended and cut you off. This happens when I fire up one of my necropyrobeastiality videos. I think my computer may be trying to censor my activities.

SICK!! I am NOT into pyro videos! Now I'm just gonna feel dirty while watching my necrobestiality collection.... ugh...

---

### Post by KARaidl on 2008-03-06
Okay, I think I can go ahead and tack on flash videos on this problem, too. As soon as I try to load a site with flash videos, Firefox locks up and I get the grey screen. Again, this wasn't happening before. What the hell is going on??

---

### Post by KARaidl on 2008-03-07
Ker-bump!!

---

### Post by chewearn on 2008-03-08
Let's start with problem with VLC; try invoking it from the terminal, so you get to see any error message that might pop-up:
```
vlc
```

Next, open a video file via the File > Open File menu.  Post back any error message output on the terminal.

---

### Post by KARaidl on 2008-03-08
Wel... it froze and all. But I never got an error message.

```
kyle@Kyle-PC:~$ vlc
VLC media player 0.8.6c Janus
Killed
kyle@Kyle-PC:~$
```.

I did exactly as you said. I opened VLC, everything went fine, then I tried to play a video and it locked up.

Quick update: So Mplayer is back to working. I'm not sure what was going on with the plugin, but it's back to displaying videos in Firefox, and it will now open up videos on my desktop. I guess the issue there was I was trying to play them directly on my Windows partition and they didn't work till I brought them over to Ubuntu. Can't explain why the plugin just suddenly started working though.

Flash videos are still doing the same old freezing thing, although my Real Player plugin is working fine.

---

### Post by chewearn on 2008-03-08
In your first post, you mentioned the problem occurred with wmv (video) and wav  (audio) files.

Can you test with other type of audio and video files (mp3, avi, etc).

If you have a file that is video only and no audio stream (quite rare I know) it is possible to isolate the problem to the video path or audio path.
I'm suspecting it's the audio.

---

### Post by KARaidl on 2008-03-08
M'kay, MP3's, AVI's, and FLV's all cause the same issue. And Mplayer encountered an issue while trying to play the AVI. Take a look...

```
kyle@Kyle-PC:~$ gmplayer
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/kyle/Desktop/2-audio-streams.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
[aviheader] Audio stream found, -aid 2
VIDEO:  [XVID]  624x272  12bpp  23.976 fps  1052.2 kbps (128.4 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.4.1 (build 2178/release)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 624 x 272 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.29:1 - prescaling to correct movie aspect.
VO: [xv] 624x272 => 624x272 Planar YV12 
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
A:  11.4 V:  11.4 A-V:  0.010 ct:  0.015 274/274  1%  1%  0.7% 0 0              
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)     
A:  14.6 V:  14.6 A-V: -0.004 ct:  0.016 350/350  1%  1%  0.7% 3 0              
  =====  PAUSE  =====
gnome_screensaver_control()
Playing /home/kyle/Desktop/2-audio-streams.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
[aviheader] Audio stream found, -aid 2
VIDEO:  [XVID]  624x272  12bpp  23.976 fps  1052.2 kbps (128.4 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.4.1 (build 2178/release)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================


```

And in a pop up box (which I didn't catch in the terminal) it says "Mplayer interrupted by signal 1 in module: ao2.init"

I don't know where to get an audio-less video file. If you have any suggestions, let me know.

---

### Post by chewearn on 2008-03-08
Ok, not sure if this will work, but I think it will worth a try.

1. Disable sound in vlc, by uncheck "Enable audio" in Preferences > Audio

2. Disable sound in mplayer:
```
mplayer -nosound <media file>
```

---

### Post by Jack Jebedee on 2008-03-08
My eyeballs are tracking this thread with great interest because the very same thing just happened to me.  Suddenly, there's no online Java, no online videos, no flash.  VLC works perfectly with videos that are on my hard drive.  The problem seems to be confined to Internet material and it makes no difference whether I use FireFox or Opera.  Mysterious!

... JJ

---

### Post by KARaidl on 2008-03-08
Well congratulations, captain, we have liftoff. Both the AVI and the WMV file opened in VLC and Mplayer with the sound turned off.

(By the way, VLC is saying the AVI file I snagged is broken, so disregard the earlier error I posted. I just got a bad file from Google.)

There's nothing interesting to report in the terminal.

Soooo.... now what?

---

### Post by chewearn on 2008-03-08
> **Jack Jebedee said:**
> My eyeballs are tracking this thread with great interest because the very same thing just happened to me.  Suddenly, there's no online Java, no online videos, no flash.  VLC works perfectly with videos that are on my hard drive.  The problem seems to be confined to Internet material and it makes no difference whether I use FireFox or Opera.  Mysterious!

... JJ

Arrgg!!  Now, I'm under stress...:biggrin:  I'm by no means an expert in this, not by a long shot.  Just try my best to give some (moral) support, since the OP is stuck without good help.  And learn a few things myself in the process.

In any case, you can check your plug-ins first (since it's online contents that are giving problem).  Open up firefox, enter ```
about:plugins
``` in the address bar.  See if the appropriate plug-ins are in place.

I'm not an Opera user, so this might not go anywhere.

---

### Post by Jack Jebedee on 2008-03-08
**[CENTER]But wait, there's more![/CENTER]**

If I login to Google Videos or You-Tube, there's a blank screen (and total silence) in the video window.  I move a mouse over that window and the cursor sprouts a message:  "Click to use this control."  Of course, clicking does absolutely nothing.  The video doesn't play.

HOWEVER...  If I download the video to my desktop, I can double-click on the saved file and the video plays perfectly.

Help!

... JJ

Oops!  I just saw that KARaidl has a completely different problem from mine.  Please put me next in line for help.  Thanks very much!

---

### Post by xc3RnbFO8P on 2008-03-08
> **KARaidl said:**
> Well congratulations, captain, we have liftoff. Both the AVI and the WMV file opened in VLC and Mplayer with the sound turned off.

(By the way, VLC is saying the AVI file I snagged is broken, so disregard the earlier error I posted. I just got a bad file from Google.)

There's nothing interesting to report in the terminal.

Soooo.... now what?

Have you tried to open it with **Avidemux**?

---

### Post by KARaidl on 2008-03-08
> Have you tried to open it with Avidemux?

I just did and it failed to open. So I went and downloaded another AVI file and that one worked fine. Just chalk it up to my unfortunate luck to download a broken file.

---

### Post by Jack Jebedee on 2008-03-08
Add-ons/Extensions:

AddBlock Plus, ChatZilla, Firefox Companion for eBay, PDF Download and Ubufox.  They're all there!

I wish I could know exactly WHEN I lost the online video capability because then I would know what I did immediately before losing it.  Unfortunately, I don't have a clue.

Thanks for the help.  I hope I don't have to re-install Ubuntu!

... JJ

---

### Post by chewearn on 2008-03-08
> **KARaidl said:**
> Well congratulations, captain, we have liftoff. Both the AVI and the WMV file opened in VLC and Mplayer with the sound turned off.

(By the way, VLC is saying the AVI file I snagged is broken, so disregard the earlier error I posted. I just got a bad file from Google.)

There's nothing interesting to report in the terminal.

Soooo.... now what?

A couple of things to check:
1. What audio card do you have?  Have you been required to go thru any extra/special steps to get it working when you first install ubuntu?

2. Anything in particular you can recall being updated in the last few days that might account for the audio problem?  I seemed to remember a new kernel update quite recently.  You could try revert to the previous kernel.

3. Do you have dual boot for Windows (or other OS)?  If yes, you could check if any problem encounter there.  This will eliminate if the problem is recent hardware failure.

4. Is the system audio working?  Go to System > Preferences > Sound, and clik on the [Test] button.

5. This is a blind guess: try a different audio output (e.g. OSS) instead of ALSA.
In VLC preferences > Audio > Output modules > Audio output module; change "Default" to "Linux OSS"
In mplayer:
```
mplayer -ao oss <media file>
```

---

### Post by KARaidl on 2008-03-08
I have integrated sound. As far as I can remember it's a Realtek something or other.... it'd take me a few minutes to find out.

Yes I do have dual boot and no, the problem isn't showing up on Windows.

Testing playback sound caused the same problem until I set it to OSS which leads me to my next point...

It worked! I've got sound in my video files again after setting them to use OSS! Now how can I make that default?

Youtube videos still make Firefox crash. I need to find out if it's possible to use OSS across the board.

---

### Post by chewearn on 2008-03-08
> **KARaidl said:**
> 
It worked! I've got sound in my video files again after setting them to use OSS! Now how can I make that default?

Great!  Once you set it in VLC preferences and save the settings, it will use OSS  every time.  I'm not sure if this will carry over to the VLC Firefox plug-ins as well.  Do you still get the problem there?

As for mplayer, I couldn't get OSS to work in my system.  When I actually try the -ao oss option, it ended up no sound (error message: "Can't open audio device /dev/dsp: Device or resource busy").  Did you get it to work in your system?

EDIT:
I missed that last sentence in your post.  Let me think on it for a while.  You might need to fix ALSA sound, though at this moment I don't know how to do that.

---

### Post by KARaidl on 2008-03-08
Well Mplayer (after I moved the video file over to the Ubuntu partition) was always working perfectly, but you can make that setting under the configuration options in the audio tab.

---

### Post by KARaidl on 2008-03-08
Ugh... the Mplayer plugin is now making my browser crash after playing the file when I try to close the tab.

Going back to the previous kernel is fine by me, if you could tell me how to do that. Or point me in the right direction.

Or even better if there's a way to get ever application to only work with OSS and nothing else, including flash player.

But at the moment it's 2 am and I have to be up at 8 for work. Thanks for all your help, you've been great.

[EDIT]: Actually I just forgot to configure the mplayer plugin to use OSS. It's working fine now.

---

### Post by chewearn on 2008-03-08
Ok, good night :)  I will google for hints.

Please post the type of realtek sound chip you have; maybe a bug might already be posted about it, or there might be a thread about a workaround.

```
lspci | grep Audio
```

---

### Post by KARaidl on 2008-03-08
```
kyle@Kyle-PC:~$ lspci | grep Audio
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
kyle@Kyle-PC:~$ 

```

Well that's odd. In my sound preferences I'm given the option to either use HDA Nvidia or Realtek ALC883. In Windows I had to download the driver from Realtek for sound.

---

### Post by johnnycoma on 2008-03-09
Ugh, add me to the list of people this is happening to. Can't view any media through Firefox or Opera, and I'm sick of the browser crashes. Very frustrating. I love Ubuntu except for this flaw...

---

### Post by chewearn on 2008-03-09
I found the following thread, which appeared to be closest to your problem:
[http://ubuntuforums.org/showthread.php?t=624361](http://ubuntuforums.org/showthread.php?t=624361)

Unfortunately, there is no definite fix; the one suggestion in the thread, to purge and reinstall alsa, worked for one guy, but trash someone else installation.

Here is the bug report filed from that thread:
[https://bugs.launchpad.net/ubuntu/+bug/178520](https://bugs.launchpad.net/ubuntu/+bug/178520)

There is no action on that bug report, if you add to the bug report, there might be more attention given.

---

### Post by johnnycoma on 2008-03-09
OK, I fixed my problem after banging my head against the wall for a little bit.

I followed the instructions in the above thread and didn't have any success. 

I kept running over and over the Firefox plug-in list and realized that I was only running Flash 8 (most websites require Flash 9). Gnash was set as my SWF player and no updates were available so the first thing I did was go to the Adobe website to install their version of Flash player. 

After downloading the .tar.gz file and unpacking, I ran the install in terminal and it went pretty painlessly. 

Next thing I did was check out Synaptic... I did a simple uninstall and reinstall of mozilla-plugin-vlc and now everything works fine. No locking up or anything. I'm all good to go.

---

### Post by KARaidl on 2008-03-09
I'm good too. I remembered that the reason why Flash was locking up for me was because I told it to use the alsa driver while following a troubleshooting guide on the Ubuntu website.

I also followed the steps listed in that thread and they went perfectly for me. As for that guy who got his system broken, my guess would be it was because he had multiple sessions on one install.

AstalaVista, you've been just awesome. Thanks for all your hard work.

---

