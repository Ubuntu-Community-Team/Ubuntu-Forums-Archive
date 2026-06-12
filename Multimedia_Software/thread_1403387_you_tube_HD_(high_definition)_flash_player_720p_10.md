---
title: "you tube HD (high definition) flash player 720p 1080p"
date: 2010-02-10
forum: Multimedia Software
---

### Post by Claus7 on 2010-02-10
Hello,

lately I had a conversation with a windows user who was asking me about the support of Linux on High Definition videos. Not so familiar with these issues, these are some questions I would like to ask the community, as I was not able to find some answers:

i) [This video on you tube]("http://www.youtube.com/watch?v=7BOhDaJH0m4") gives on the down right side the following options:

> 1080p HD
720p  HD
480p
360p

with a NVIDIA GeForce 4 graphics card I'm unable to see videos more than 480p. Is it a problem of my graphics card?

ii) Which cards in general support this feature and is it related with the drivers linux provides?

iii) I have seen [here]("http://ubuntuforums.org/showthread.php?t=1403283") about high definition in videos. Is this something entirely different than the videos someone can see online? 

iv) Is there any support of using the GPU of our graphics card in order to play such High Definition Videos, and if affirmative is there any special configuration someone has to do in order to achieve such a thing?

v) Which is this feature that my friend boasts about that windows with vista (and on?) supports? 

Hope I did not messed things as I'm not so familiar with this High Definition thing.

Thanks in advance,
Regards!

---

### Post by lovinglinux on 2010-02-10
> **Claus7 said:**
> with a NVIDIA GeForce 4 graphics card I'm unable to see videos more than 480p. Is it a problem of my graphics card?:

Not entirely, although your card is really old and doesn't support VDPAU, a nVidia technology that would take some load off the CPU and put it on the GPU.

My card doesn't have support for VDPAU either, but I have a Core2 Duo CPU, so it isn't affected as much. Nevertheless, CPU usage is really high when viewing HD flash videos and the 1080p is unwatchable. A card with VDPAU support would definitely solve the problem.

> **Claus7 said:**
> ii) Which cards in general support this feature and is it related with the drivers linux provides?

See list [here](http://en.wikipedia.org/wiki/VDPAU#Table_of_NVIDIA_GPUs).

> **Claus7 said:**
> iii) I have seen [here]("http://ubuntuforums.org/showthread.php?t=1403283") about high definition in videos. Is this something entirely different than the videos someone can see online? 

Not entirely. The real problem is when you play streaming flash videos. Flash sucks on Linux and uses too much CPU cycles. While I can't play the 1080p version without heavy stuttering from YouTube, I can play it perfectly locally with gnome-mplayer, smplayer or vlc. The same happens with the 720p, although it is watchable on YouTube.

I have a Core2 Duo 2.9 Ghz, with nVidia 7300 GT (no VDPAU) and 2 Gb DDR2 RAM.

> **Claus7 said:**
> iv) Is there any support of using the GPU of our graphics card in order to play such High Definition Videos, and if affirmative is there any special configuration someone has to do in order to achieve such a thing?

You can try [this trick](http://lovinglinux.megabyet.net/?page_id=220#Flash-Tweaks-2), but I doubt it will help much for HD content.

> **Claus7 said:**
> v) Which is this feature that my friend boasts about that windows with vista (and on?) supports?

[PureVideo](http://en.wikipedia.org/wiki/PureVideo)

---

### Post by Claus7 on 2010-02-10
Hello,

*lovinglinux* thank you very much for your comprehensible answer and your immediate response. 

Reading the post along with all the links you provided there are two more questions that I have.

i) Purevideo seems to me that is not a privilege of an OS alone. It has to do with Nvidia and a closed source driver it provides as long as the graphics card is able to support the VDPAU technology so as for someone to be able to see HD videos using a small amount of CPU. Am I correct?

> On 2008-11-14 NVIDIA released a beta version of a closed-source device driver and API called VDPAU (Video Decode and Presentation API for Unix) with PureVideo support for Linux, FreeBSD and Solaris.[1] (source wikipedia)

ii) Since e.g. vlc can fully support the High Definition feature I can guess that Linux is not inferior to windows in this section. Is this true?
The only problem is that flashplayer itself is not capable of playing the videos in high definition, even without the VDPAU technology as flashplayer cannot take advantage of the CPU. 

So in order to recapitulate: 
[LIST]
[*]someone with a very high cpu power, even with a mediocre video card, can see such videos.
[*]Since it takes much of cpu, this technology is best viewed with a VDPAU support in the graphics card chipset. 
[*]In order for linux users to take advantage of this technology the proprietary drivers from Nvidia should be used, along with some configurations in xorg conf file.
[*]Also the "tool" that someone uses, plays an important role for HD. So, in linux, flashplayer is practically unable to provide support with high definition quality, whereas popular players such as vlc have no problems as they have the necessary codecs.
[/LIST]

Verdict:-->ubuntu users: no flashplayer support, no open source drivers supporting VDPAU

Thanks once again,
Regards!

---

### Post by lovinglinux on 2010-02-10
> **Claus7 said:**
> Hello,

*lovinglinux* thank you very much for your comprehensible answer and your immediate response. 

Reading the post along with all the links you provided there are two more questions that I have.

i) Purevideo seems to me that is not a privilege of an OS alone. It has to do with Nvidia and a closed source driver it provides as long as the graphics card is able to support the VDPAU technology so as for someone to be able to see HD videos using a small amount of CPU. Am I correct?

 (source wikipedia)

ii) Since e.g. vlc can fully support the High Definition feature I can guess that Linux is not inferior to windows in this section. Is this true?
The only problem is that flashplayer itself is not capable of playing the videos in high definition, even without the VDPAU technology as flashplayer cannot take advantage of the CPU. 

So in order to recapitulate: 
[LIST]
[*]someone with a very high cpu power, even with a mediocre video card, can see such videos.
[*]Since it takes much of cpu, this technology is best viewed with a VDPAU support in the graphics card chipset. 
[*]In order for linux users to take advantage of this technology the proprietary drivers from Nvidia should be used, along with some configurations in xorg conf file.
[*]Also the "tool" that someone uses, plays an important role for HD. So, in linux, flashplayer is practically unable to provide support with high definition quality, whereas popular players such as vlc have no problems as they have the necessary codecs.
[/LIST]

Verdict:-->ubuntu users: no flashplayer support, no open source drivers supporting VDPAU

Thanks once again,
Regards!

Yep. I think that's sums it up.

---

### Post by Chromagnum on 2010-02-11
First, I sincerely apologize to the thread owner if I'm out of topic; Second, I didn't know where to put my story and I figured this one seems to (kind of) fits the criteria; and third, English not my native languange so you know... alot of grammar mistakes.

I have P4 dual core 3ghz, 1GB Ram, and Nvidia FX 5500 (no VDPAU, I suppose), using Karmic Koala with the resolution of 1360x768 (16:9 aspect ratio). At first I won't be able to view 720p from youtube without choppyness etc etc. So what I did was downloaded the video as mp4 (used keep-tune.com) and viewed it using Vlc. Another problem arises: in the first 5 or 10 minutes the image got stuck, and the amount of CPU cycle very huge to the point (sometimes) my system just shutdown by it self.

I can play 720p either via youtube or using standalone player just fine in Windows using the same PC. (That would be either .mkv, .avi, .mp4 etc). Now, I can't deal with the fact Windows overpower Ubuntu--no way! (I'm just kidding. I know Windows win (for now) in HD department). So, I did some inspection through out the hardwares and... it came to my surprise that my cpu fan running pretty low. (Bios supposed to report this but I don't know why my PC don't). Anyway, I replaced the cpu fan with the new one; today, btw. 

Image stuck problem, solved. I can watch 720p video via Vlc (using XVideo output) with no interference. And 720p youtube (play it while in Chromium) running smoothly. I tested the enlarge thing (the little L shaped arrow near the volume) on youtube, still running smoothly. The only problem left is fullscreen; in this case still got choppyness.

To sums things up: I can watch 720p video using Vlc without a problem (fullscreen, btw). I can watch youtube HD 720p in the browser with the enlarge view without a problem (no luck in fullscreen, though). 

Advice for other Ubuntu user(s): Lots of you still use old pc, probably same like mine. You might want to check it out the cpu fan or air circulation in your pc. It sure does help me. 

Regards,
Chromagnum.

---

### Post by VertexPusher on 2010-02-11
> **Claus7 said:**
> Verdict:-->ubuntu users: no flashplayer support, no open source drivers supporting VDPAU
Your problem doesn't have anything to do with Ubuntu, Flash, or graphics drivers. The type of graphics card you are using is incompatible with any mainboard built after 2005. So that's how old your computer is: at least **5 years!**

Sorry, but you sound like someone who takes roasted chicken wings to a veterinarian. Your computer is simply **too slow** to play back HD video, and nothing in Windows Vista would change that.

---

### Post by Claus7 on 2010-02-11
Hello,

> **Chromagnum said:**
> First, I sincerely apologize to the thread owner if I'm out of topic; Second, I didn't know where to put my story and I figured this one seems to (kind of) fits the criteria; and third, English not my native languange so you know... alot of grammar mistakes.

Chromagnum.

You do not have to apologize of anything. I'm glad that I opened this topic. The more people they are writing here the more information will be available to all. That way we can learn more and understand about HD technology. By the way I was able to understand without any problem what you were writing!

> **VertexPusher said:**
> Your problem doesn't have anything to do with Ubuntu, Flash, or graphics drivers. The type of graphics card you are using is incompatible with any mainboard built after 2005. So that's how old your computer is: at least **5 years!**

Sorry, but you sound like someone who takes roasted chicken wings to a veterinarian. Your computer is simply **too slow** to play back HD video, and nothing in Windows Vista would change that.

The verdict came out via "conversation" with someone with much newer hardware than mine. I admit that my hardware is 7 years old and I'm really proud of what I can get with that. If my verdict is wrong I won't argue to change it, yet I have my own experience and I compare it with someone else's. Would you mind giving us your specs while you are trying to see HD? If you noticed I had no idea about this technology and really, at least for now, I do not care about it. I wanted just to inform myself and learn more about it, so in case I want to harness it to know what to do. 

About flashplayer I have seen tons of threads here in our community mentioning problems. I do not think that this is a secret. I was able to configure my pc in such a way so as to be able to have minimum problems concerning my needs. And I always welcome new versions better and improved. 

Of course I understand that I have an aged pc way back to support these technologies. If you think that new machines perform nicely and beautifully I would be more than glad to hear about that!

Just FYI: I do not think that I would be able to have Vista on my box, so using my pc more than comfortable with ubuntu on, I guess that this is a comparison way greater than the HD issue alone.

Regards!

---

### Post by efflandt on 2010-02-11
One thing I don't think anyone mentioned in this thread yet is that the speed of your internet connection can influence the speed of streaming HD video with any device.  For example streaming Netflix HD on BluRay or Roku player, etc. may need 3.5-4 Mbps internet speed.  So internet speed could limit streaming video quality.

I also have an older desktop PC from 2004 with Athlon64 3200+ (2 GHz), 2 GB RAM, and 256 MB ATI X1300 AGP video card (now considered a legacy card by AMD).  My cpu lacks the lahf_lm instruction used by real 64-bit flash, so I also had to use flashplugin-lahf-fix someone came up with.  At some point Hulu changed something that broke 64-bit flash in a browser.  64-bit flash supposedly still works with Hulu desktop, but Hulu desktop does not pick up flashplugin-lahf-fix.so, so I had to fall back to flashplugin-installer (32-bit flash w/ nswrapper).

I just got a 32" LG 32LH40 1080p HDTV to use as a monitor DVI to HDMI.  It works fine for DVDs full screen with vlc.  But Hulu desktop was a bit slow full screen unless I drop the resolution back to 1280x720 (720p).  Even then it drops some frames, but is watchable.

I saw some newer AGP video cards at the store, but the one that would have worked with my existing 330 watt power supply was $110.  So instead I got a stand alone LG BD370 BluRay player for $160 that does streaming Netflix (which I hear Linux cannot do right now) and YouTube, besides BluRay which my PC does not have.  That way I am up to speed without getting a whole new computer that may not have fully supported hardware yet.

---

### Post by VertexPusher on 2010-02-12
> **Claus7 said:**
> About flashplayer I have seen tons of threads here in our community mentioning problems. I do not think that this is a secret.
Correct, but Flashplayer is not causing the problems, and that seems to be a secret to most people.

There are exactly three issues that frequently occur with Flash video playback:
[list=1][*]Tearing.[*]High CPU load.[*]No sound.[/list]
#1 is a problem that Flash shares with any other media player on Linux. Since Flash is embedded in a browser window, it doesn't have access to graphics card features such as hardware overlays (XVideo). Software rendering in X11 always results in tearing. This is not the fault of Flash, and it doesn't really affect its capability to decode HD video in realtime if the CPU is fast enough and the network is not congested.

Problems #2 and #3 are caused by either PulseAudio or libflashsupport. Flash accesses sound cards through ALSA, which makes perfect sense because ALSA is the default sound system of the Linux kernel. If you run a pure ALSA system such as Debian or if you uninstall PulseAudio from Ubuntu, sound in Flash will work perfectly and with very little CPU load. However, any attempt to fool Flash into using PulseAudio, Esound or OSS will cause trouble.

PulseAudio's PCM plugin for ALSA is known to cause excessive CPU load (30% or more), so if the same CPU core is busy decoding HD video, things will go haywire and people will blame Flash.

The purpose of the libflashsupport library is to send Flash audio to Esound or, if Esound is not installed, to OSS. However, Esound is missing by default in Ubuntu 9.10, and OSS requires exclusive access to the sound card, so there will be either no sound in Flash or no sound anywhere else, and again people will blame Flash.

---

### Post by lovinglinux on 2010-02-12
> **VertexPusher said:**
> Correct, but Flashplayer is not causing the problems, and that seems to be a secret to most people.

There are exactly three issues that frequently occur with Flash video playback:
[list=1][*]Tearing.[*]High CPU load.[*]No sound.[/list]
#1 is a problem that Flash shares with any other media player on Linux. Since Flash is embedded in a browser window, it doesn't have access to graphics card features such as hardware overlays (XVideo). Software rendering in X11 always results in tearing. This is not the fault of Flash, and it doesn't really affect its capability to decode HD video in realtime if the CPU is fast enough and the network is not congested.

Problems #2 and #3 are caused by either PulseAudio or libflashsupport. Flash accesses sound cards through ALSA, which makes perfect sense because ALSA is the default sound system of the Linux kernel. If you run a pure ALSA system such as Debian or if you uninstall PulseAudio from Ubuntu, sound in Flash will work perfectly and with very little CPU load. However, any attempt to fool Flash into using PulseAudio, Esound or OSS will cause trouble.

PulseAudio's PCM plugin for ALSA is known to cause excessive CPU load (30% or more), so if the same CPU core is busy decoding HD video, things will go haywire and people will blame Flash.

The purpose of the libflashsupport library is to send Flash audio to Esound or, if Esound is not installed, to OSS. However, Esound is missing by default in Ubuntu 9.10, and OSS requires exclusive access to the sound card, so there will be either no sound in Flash or no sound anywhere else, and again people will blame Flash.

Interesting. This is the first time I see someone explaining why flash uses too much CPU. Is there a solution to #2 and #3?

---

### Post by VertexPusher on 2010-02-12
> **lovinglinux said:**
> Interesting. This is the first time I see someone explaining why flash uses too much CPU. Is there a solution to #2 and #3?
Yes. Install gstreamer0.10-alsa and gnome-alsamixer, then remove pulseaudio, gstreamer0.10-pulseaudio, vlc-plugin-pulse and flashplugin-nonfree-extrasound. This will turn Ubuntu in a pure ALSA-driven system, very similar to Debian.

---

### Post by Claus7 on 2010-02-12
Hello,

> **VertexPusher said:**
> Yes. Install gstreamer0.10-alsa and gnome-alsamixer, then remove pulseaudio, gstreamer0.10-pulseaudio, vlc-plugin-pulse and flashplugin-nonfree-extrasound. This will turn Ubuntu in a pure ALSA-driven system, very similar to Debian.

This is what I have done (about a pure alsa system):
[http://ubuntuforums.org/showthread.php?t=1311599](http://ubuntuforums.org/showthread.php?t=1311599)

and my system is working like a charm.

Very glad that things are getting clearer!

Regards!

---

### Post by lovinglinux on 2010-02-12
> **VertexPusher said:**
> Yes. Install gstreamer0.10-alsa and gnome-alsamixer, then remove pulseaudio, gstreamer0.10-pulseaudio, vlc-plugin-pulse and flashplugin-nonfree-extrasound. This will turn Ubuntu in a pure ALSA-driven system, very similar to Debian.

It doesn't make any difference for me. Flash is still using about 30% of CPU on low resolution videos and I still can't watch the 1080p from the first post.

---

### Post by VertexPusher on 2010-02-14
> **lovinglinux said:**
> It doesn't make any difference for me. Flash is still using about 30% of CPU on low resolution videos and I still can't watch the 1080p from the first post.
Try this:

Open a terminal window and enter "gstreamer-properties". On the video tab, select "X Window System (No Xv)", then close the window. Now you have disabled the hardware video overlay in Totem. Launch Firefox and start playing back any 1080p video in YouTube. Pause playback and wait until the entire video has loaded. Don't leave the page yet. Open the /tmp folder and look for a file named like "FlashXXXXXX". This is the buffered YouTube video. Right click it and choose "Open in Movie Player". This will open the video in Totem.

Now watch CPU load in System Monitor while the video is playing. **You'll find out that Totem is exactly as CPU-intensive as Firefox with the Flash plugin.**

Fact is that even mainstream CPUs from 2008 are struggling with 1080p H.264 video. Linux and the Flash plugin can't be blamed here. For the record, those videos play fine on a Core i7, which is what I am using.

---

### Post by lovinglinux on 2010-02-14
> **VertexPusher said:**
> Try this:

Open a terminal window and enter "gstreamer-properties". On the video tab, select "X Window System (No Xv)", then close the window. Now you have disabled the hardware video overlay in Totem. Launch Firefox and start playing back any 1080p video in YouTube. Pause playback and wait until the entire video has loaded. Don't leave the page yet. Open the /tmp folder and look for a file named like "FlashXXXXXX". This is the buffered YouTube video. Right click it and choose "Open in Movie Player". This will open the video in Totem.

Now watch CPU load in System Monitor while the video is playing. **You'll find out that Totem is exactly as CPU-intensive as Firefox with the Flash plugin.**

Fact is that even mainstream CPUs from 2008 are struggling with 1080p H.264 video. Linux and the Flash plugin can't be blamed here. For the record, those videos play fine on a Core i7, which is what I am using.

As I already said previously, I don't have any problems playing locally with gnome-mplayer, smplayer or vlc. BTW, [Video Download Helper](https://addons.mozilla.org/en-US/firefox/addon/3006) can download Youtube videos without waiting them to buffer and manually searching the /tmp folder.

I was expecting that removing pulseaudio would make YouTube embedded flash videos play without eating CPU cycles, but it seems to me it doesn't help. So I don't see why is not Flash fault.

---

### Post by VertexPusher on 2010-02-14
> **lovinglinux said:**
> I was expecting that removing pulseaudio would make YouTube embedded flash videos play without eating CPU cycles, but it seems to me it doesn't help.
It definitely helps to some extent, but it won't magically turn a slow computer into a fast one of course.

> So I don't see why is not Flash fault.
You can kick your legs and scream "But I want to blame Flash!!!" as much as you like. Your computer is too slow, and that's not the fault of Flash, period.

Here's some more background info:

[http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html](http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html)
[http://www.kaourantin.net/2008/05/what-does-gpu-acceleration-mean.html](http://www.kaourantin.net/2008/05/what-does-gpu-acceleration-mean.html)

---

### Post by lovinglinux on 2010-02-14
> **VertexPusher said:**
> It definitely helps to some extent, but it won't magically turn a slow computer into a fast one of course.


You can kick your legs and scream "But I want to blame Flash!!!" as much as you like. Your computer is too slow, and that's not the fault of Flash, period.

Here's some more background info:

[http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html](http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html)
[http://www.kaourantin.net/2008/05/what-does-gpu-acceleration-mean.html](http://www.kaourantin.net/2008/05/what-does-gpu-acceleration-mean.html)

Seriously? I don't that is a good explanation, otherwise, I wouldn't be able to play 1080p videos locally without eating my CPU and without any stuttering. So, IT MUST BE flash fault. Besides, I don't think a Core 2 Duo 2.9 Ghz with 3Mb Cache can be considered slow. It's not high-end, but it's definitely not a slow processor.

> **VertexPusher said:**
> Now watch CPU load in System Monitor while the video is playing. **You'll find out that Totem is exactly as CPU-intensive as Firefox with the Flash plugin.**

No it is not. The SMALL embedded mp4 1080p flash video uses 50% to 70% of both cores, with heavy stuttering. When downloaded and played locally with vlc, the same mp4 1080p video uses 27% to 45% and plays smoothly.

---

### Post by markp1989 on 2010-02-14
> **VertexPusher said:**
> Your problem doesn't have anything to do with Ubuntu, Flash, or graphics drivers. The type of graphics card you are using is incompatible with any mainboard built after 2005. So that's how old your computer is: at least **5 years!**

Sorry, but you sound like someone who takes roasted chicken wings to a veterinarian. Your computer is simply **too slow** to play back HD video, and nothing in Windows Vista would change that.

on my system i can play thje video at 720p but at 1080p i get frame drops, and my system was only built about a year ago. (admitingly the gpu in it sucks, but the cpu is up to it as i have played HD mkvs stored localy) so i think the problem is with the flash player.

---

### Post by mc4man on 2010-02-14
Well with a slower core2duo than mentioned here but a very fast connection can play the bbc 1080p in the orig. and medium sized window no problem - fullscreen in firefox does stutter and drop frames.

> You'll find out that Totem is exactly as CPU-intensive as Firefox with the Flash plugin.

Not really - x11 output from the file played locally uses less cpu and uses both cores - in firefox it's mainly confined to 1 core and overall is higher.
(the best use for local is xv, then sdl, then x11

You needn't confine any test to totem - use vlc with a --vout x11 or sdl , ect

I also don't trust system monitor to any great degree - set up logging with sysstat (mpstat) for more accurate results

---

### Post by VertexPusher on 2010-02-15
> **lovinglinux said:**
> Seriously? I don't that is a good explanation
You will find that it's a good explanation as soon as you read it.

> otherwise, I wouldn't be able to play 1080p videos locally without eating my CPU and without any stuttering. So, IT MUST BE flash fault.
Please stop comparing Flash to regular video players. It makes you look stupid. Flash is a delivery system for interactive content. Video playback is only 10% of what it can do. The problem is that the other 90% require it to operate in the RGB colour space. The articles I linked to in post #16 explain in great detail why Flash cannot take advantage of the XVideo overlay feature used by regular video players. This means it has to use the CPU to do colour space conversion and scaling.

By the way, video embedded in HTML5 pages (i.e. without Flash) will be affected by exactly the same problem.

> Besides, I don't think a Core 2 Duo 2.9 Ghz with 3Mb Cache can be considered slow. It's not high-end, but it's definitely not a slow processor.
It is too slow for Flash content as soon as it involves 1080p video playback. You seem to forget that at the time when your CPU was state of the art, YouTube did not offer any content beyond 480x360.

> No it is not. The SMALL embedded mp4 1080p flash video uses 50% to 70% of both cores, with heavy stuttering. When downloaded and played locally with vlc, the same mp4 1080p video uses 27% to 45% and plays smoothly.
You did not understand what I wrote in post #14. Regular video players such as VLC, Totem and MPlayer use the XVideo overlay to offload colour space conversion and scaling to the GPU. If you turn XVideo off (or use a graphics card that doesn't offer this feature) these players will become just as CPU-intensive as Flash.

You cannot blame Flash. Of course you can blame YouTube, Vimeo and others for using Flash, but then you ignore that their embedded players do more than just display video. They display related videos, annotations, hyperlinks, advertisements etc.

---

### Post by lovinglinux on 2010-02-15
> **VertexPusher said:**
> Please stop comparing Flash to regular video players. It makes you look stupid. 

Don't need to be rude to make your point. Don't even bother to reply, since I'm unsubscribing this thread.

---

### Post by VertexPusher on 2010-02-15
> **lovinglinux said:**
> Don't need to be rude to make your point. Don't even bother to reply, since I'm unsubscribing this thread.
"Don't bother me with facts! I don't care about facts! I want to blame Flash!!!" *kicks and screams*

Welcome to my ignore list.

---

### Post by linuxadore on 2010-02-15
I have laptop with Celeron 1,6 GHz. CPU load was dramaticaly increased with flashplugin in Firefox, Opera, Totem. I messed up my system once before when I try to open in Totem large list of videos...Laptop was overheated, hdd had more and more bad sectors, then died...(Intend to recover data with RIP LiveCD). Installing flashplayer10 deb and tar.gz from Adobe.com failed, Synaptic in Hardy get error 4 flashplugin-nonfree (version 9): sha256 mismatch, flashplayer not installed, 

so I find solution with debug dev flashplayer9 packages - see step-by-step how2 here:

[http://my.opera.com/linuxadore/blog/old-flashplayer9-installing-from-source-in-ubuntu-hardy-8-04](http://my.opera.com/linuxadore/blog/old-flashplayer9-installing-from-source-in-ubuntu-hardy-8-04)

Supose it helps for every distro version and PC architecture, cause it is source package (tar.gz)...

@lovinglinux and @VertexPusher - Tnx 4 your informative and useful posts!

---

