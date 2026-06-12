---
title: "A/V Sync Issue with VLC"
date: 2011-05-27
forum: Multimedia Software
---

### Post by Nostigex on 2011-05-27
After upgrading to 11.04, video and audio are out of sync by about one second when playing movies in VLC, or opening a clip on the web. Reinstalling does nothing. Fix? Let me know what other info would be helpful.

---

### Post by Nostigex on 2011-05-28
bump

---

### Post by BicyclerBoy on 2011-05-28
A/V sync can be affected by the video playback method used..
With VLC this would include va-api, xv, x11, opengl..some are obsolete.
VA-API will not be avail unless you build from source etc.

The choice of post-decode filter (scale sharpen de-interlace) add time delays..but these should be corrected by VLC...

---

### Post by Nostigex on 2011-06-03
So what should I do?

---

### Post by BicyclerBoy on 2011-06-06
I would try using a later VLC ..but I have not found any A/V sync problem with stock VLC on 10.04 or 11.04..

What video h/w do you use ? drivers ? What video playback method are you using in VLC ?

You could try changing the video playback method to see if this helps..

---

### Post by andrew.46 on 2011-06-07
Some have had success with this problem by changing the sound output from pulse to alsa. Might be worth a try?

---

### Post by thunderbirdje on 2011-06-15
I experience the same problem here 

It doesn't matter if I play the file with VLC or Totem player.

It all happened after the upgrade to 11.04.

I already installed the newest VLC version, hence 1.1.10 because the 1.1.9 had a memory leak invoking skipping some frames after a while and eventually freezing.

Hope someone can help us :D

---

### Post by hidaarose on 2011-06-16
Last week I purchased a AverMedia AverTV HD DVR to capture some footage from my cable box. I'm using the software that's provided on the website and I get a good quality mpeg2 file (720p60).

When I read the original file, there is no sync problem. I tried reading it with MPC, VLC, PS3, everything is fine.

What I'm trying to do is fit it to a Blu-Ray disc. First thing I did was try to remux it to m2ts with tsmuxer and the audio gets approximately 5sec off by the end of the file (~1h45m). At the beginning of the file, the audio is fine.

I then tried to demux it and I noticed that the audio file is 5sec longer than the video. I also changed the audio delay that tsmuxer detects automatically (159ms), but alas, same thing.

I tried searching/testing for a week, but now I'm out of ideas...

---

### Post by BicyclerBoy on 2011-06-16
This is really a new issue so a new post is in order..

---

### Post by Blingin2Mingin on 2011-06-24
Having the same issues with VLC 1.1.10, whilst Totem plays back in sync both from local disk and over the network via samba.
Changing vlc output from pulse to alsa had little effect.


I then upgraded to later version of VLC by adding the bleed ppa.

```

sudo add-apt-repository ppa:natty-bleed/ppa
sudo apt-get update
sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc

```

My out of Sync issues whilst playing from local disk have now gone away, but whilst it's improved I'm still having sync issues when playing back from a samba share on the network. However I can now always manage to quickly sync up A/V with a couple of presses of the J or K keys.

---

### Post by thunderbirdje on 2011-06-24
Having the same problem here!

I noticed a delay since my upgrade from Ubuntu 10.10 to 11.04. I first thought it was a problem with the bug in VLC (stack overflow) because it also hung after a while (30 min or so).

However, since I've installed the newer version of VLC (without that bug) I still notice a small (irritating) delay between the lips of the characters and the audio when playing a movie. It's kind of brain molesting because what you see and hear is not in sync.

I've noticed that the delay is smaller with MoviePlayer hence there is still a small (but not so big) delay. Like you notice that it's still not perfectly synced.

I've already reinstalled VLC and the Ubuntu restricted packages (for the codecs).

Some any idea or the same experience so we can to a solution together?

Thank you!

---

### Post by beew on 2011-06-24
Same problem here with VLC 1.10 in Ubuntu 11.04 and Nvidia graphic card (G105m), will test on another installation without the Nvidia proprietary graphic card.

---

### Post by beew on 2011-06-24
Tested with another installation of Natty on the same machine but using nouveau instead of the Nvidia proprietary driver, the problem disappears. So it seems to be related to the Nvidia driver. Can other people experiencing the problem confirm this?

EDITED: Just tried another Natty with the nouveau driver but this time the audio and the video is out of sync, guess Nvidia may not be the problem after all.

---

### Post by thunderbirdje on 2011-06-26
Hi Bling,

I've tried the same, however I still have the delay in VLC. I still notice that the delay in Movie player is more or less half the delay in VLC but it's still there.

In both cases I play from local hard drive.

Just wonder what the cause can be...

---

### Post by lidex on 2011-06-26
You may need to wait for 1.2 for fix:
[http://ubuntuforums.org/showthread.php?t=1785715](http://ubuntuforums.org/showthread.php?t=1785715)

---

### Post by andrew.46 on 2011-06-27
vlc 1.2 can be yours a little sooner than that if you are prepared for all the potential problems of a pre-release version:

Howto: Build the development version of vlc under Ubuntu
[http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

But 1.2 release cannot be that far away if you want to wait...

---

### Post by SirPecanGum on 2011-07-01
> **andrew.46 said:**
> Some have had success with this problem by changing the sound output from pulse to alsa. Might be worth a try?

Thanks! That worked for me.

---

### Post by beew on 2011-07-24
I have 2 installations of Natty (Natty a has the Nvidia proprietary driver, Natty b uses nouveau with xorg-edgers)  and one Xubuntu 11.04 (with nouveau with xorg-edgers).  I  experienced the A/V sync problem for VLC 1.10  in all of them

I upgraded to VLC1.11 and this is what happened.

 The problem no longer exists for Natty b (no Nividia closed driver) but audio and video are still out of sync for Natty a and Xubuntu (so it is not a Nvidia driver problem)

After further research I found the following easy workaround that seems to solve the problem completely for my Natty a and Xubuntu 11.04 install and so far I have not experienced any side effect:

In the terminal type```
sudo gedit /etc/pulse/default.pa


```When /etc/pulse/default.pa opens in the text editor look for the line
> load-module module-udev-detectand  add tsched=0 to the end
so it becomes
> load-module module-udev-detect tsched=0Then reboot and that's it.

---

### Post by beew on 2011-07-24
> **andrew.46 said:**
> Some have had success with this problem by changing the sound output from pulse to alsa. Might be worth a try?

That has not worked for me. If I change the output to ALSA I get audio -video in sync briefly but then audio is completely gone if I move the progress bar back or forth or restart. The default sound output is just called "Default", I don't know what it is as it doesn't seem to be pulseaudio either. Changing output from "Default"  to pulseaudio has similar effect as changing it to ALSA, namely audio-video are in sync for a short while then completely no sound. 

Changing output to ALSA never works for any VLC problems I have experienced in the past, it always happened that after a while audio is completely gone.

---

### Post by beew on 2011-07-24
> **lidex said:**
> You may need to wait for 1.2 for fix:
[http://ubuntuforums.org/showthread.php?t=1785715](http://ubuntuforums.org/showthread.php?t=1785715)

It seems that the problem may actually be with us a lot longer  according to this thread
[http://forum.videolan.org/viewtopic.php?f=13&t=91254](http://forum.videolan.org/viewtopic.php?f=13&t=91254)

The VLC guy said they knew the problem for a long time but there was no volunteer to come forward to fix it. Note the date, I doubt that VLC1.2 would be much different.

Maybe someone reading this thread with the knowhow would volunteer. :)

---

### Post by thunderbirdje on 2011-07-25
> **beew said:**
> It seems that the problem may actually be with us a lot longer  according to this thread
[http://forum.videolan.org/viewtopic.php?f=13&t=91254](http://forum.videolan.org/viewtopic.php?f=13&t=91254)

The VLC guy said they knew the problem for a long time but there was no volunteer to come forward to fix it. Note the date, I doubt that VLC1.2 would be much different.

Maybe someone reading this thread with the knowhow would volunteer. :)

If I had the knowhow, I would instantly start and even skip some nights ;-) Hope someone who can will help everyone out so that VLC can keep to be the best player! :-)

---

### Post by kurci2 on 2011-07-25
i have the same problem.
In April i have installed fresh ubuntu 11.04 and everything was perfect. But a few weeks ago my audio in vlc starts to delay.

today i have reinstalled ubuntu 11.04 but that sync problem is still here. very annoying!

hope it will be fixed in next update =)

---

### Post by ADroop on 2011-07-25
I have xubuntu 11.04 x64, and had this out of sync problem too. After reading many of your posts here, which was great and helpful.. I though to try the most simplest way.

I did this:

1) clicked on the sound icon in the right corner,  and changed that to ALSA.

2) Open vlc prefs. and went to audio.
 - a) out-put modual  changed to ALSA
 - b) checked the S/PDIF


This worked super for me.. all is synced.. and I also tried to close the vlc, and start it with a new movie.. and so on.. works fine :)

---

### Post by thunderbirdje on 2011-07-25
> **kurci2 said:**
> i have the same problem.
In April i have installed fresh ubuntu 11.04 and everything was perfect. But a few weeks ago my audio in vlc starts to delay.

today i have reinstalled ubuntu 11.04 but that sync problem is still here. very annoying!

hope it will be fixed in next update =)

Thank you for the information kurci2! I was thinking about reinstalling my whole Ubuntu system as well... Hope some VLC programmer can fix it for all of us. It's annoying to always check the delay. You can use J- and K-key to delay or forward the audio sync. But it's hard to set it every time.

---

### Post by beew on 2011-07-25
> **kurci2 said:**
> i have the same problem.
In April i have installed fresh ubuntu 11.04 and everything was perfect. But a few weeks ago my audio in vlc starts to delay.

today i have reinstalled ubuntu 11.04 but that sync problem is still here. very annoying!

hope it will be fixed in next update =)

Did you try the work around I posted in post #18? It fixed the problem for me.

---

### Post by thunderbirdje on 2011-07-25
> **beew said:**
> Did you try the work around I posted in post #18? It fixed the problem for me.

Thank you beew! The work around works for me! VLC 1.1.11 && Ubuntu 11.04. (Audio output module is also set to ALSA audio output and Use S/PDIF when available is selected).

---

### Post by kurci2 on 2011-07-26
the work around from post 18 worked for me too.
thanks man! That problem was a real pain in the neck.

---

### Post by pilot_po on 2011-07-27
> **ADroop said:**
> I have xubuntu 11.04 x64, and had this out of sync problem too. After reading many of your posts here, which was great and helpful.. I though to try the most simplest way.

I did this:

1) clicked on the sound icon in the right corner,  and changed that to ALSA.

2) Open vlc prefs. and went to audio.
 - a) out-put modual  changed to ALSA
 - b) checked the S/PDIF


This worked super for me.. all is synced.. and I also tried to close the vlc, and start it with a new movie.. and so on.. works fine :)

Ive tried that and seems it works,.... but ..... then you have to watch the piece from beginning till the end, since as soon as you pause and resume playback sound disappears completely and then you got to open preferences and just tick on "use s/pdif....":confused:. Which is annoying. So I'll try post #18.

---

### Post by _rH on 2011-07-28
Thanks guys!

Posts #18 and #23 seemed to solve it for me. 

Just to clarify, I was experiencing VLC/Totem A/V sync problems in 11.04. 
In fact, this had only occurred (inter alia) since I "upgraded" 10.10 to 11.04.

---

### Post by beew on 2011-07-28
If you use the work aroud in #18 you don't need to switch audio output to ALSA. As I said switching output to ALSA kills sound in VLC after pausing or fast forwarding (by dragging the progress bar), at least for me.

---

### Post by Johnny Buffalkill on 2011-07-28
Well, I tried the #18 method, and when I used pulseaudio as the output module, I just got static for sound.  I'm using analog out, because I have analog 5.1 speakers, not S/PDIF.  Maybe that is my problem?

I'll have to settle for switching to ALSA.  I don't lose sound when I navigate the time slider, but it resets the output to stereo instead of 5.1.  I can live with that.  Its way easier to reset that than it is to manually sync audio and video.

---

### Post by shantiq on 2011-07-29
well i too had this a/v sync problem but the 


**Change** settings in audio to alsa and your correct device works for me where nothing else had so far    certainly not countless reinstalls of VLC:KS:KS



So I tried the #18 method to see if it too worked  on natty 64-bit it seems to do the trick too but i would not dismiss the other method

I have set it that way for a week and so far :KS:KS:KS but really it is a **huge** oversight by the vlc dudes   it really wrecks the program   Anyway many are getting aware of the possible fixes

Thank you Beew for this latest one.  

Could anyone explain to the layman what

```
load-module module-udev-detect tsched=0
``` actually does ??

---

### Post by thunderbirdje on 2011-07-29
> **beew said:**
> If you use the work aroud in #18 you don't need to switch audio output to ALSA. As I said switching output to ALSA kills sound in VLC after pausing or fast forwarding (by dragging the progress bar), at least for me.

Good to know! Because I had with some movies problems with the audio (screaming alike sound) while not in Movie player. Switching back from ALSA to Default helped me. Thank agains!

---

### Post by bookcrazy on 2011-08-07
#18 worked for me too until I paused it. Now, it plays static. 

Any ideas?

---

### Post by lidex on 2011-08-16
> **bookcrazy said:**
> #18 worked for me too until I paused it. Now, it plays static. 

Any ideas?

Make sure your audio out in vlc is set to default. It works fine for me but I note I do NOT 
have vlc-plugin-pulse installed.

---

### Post by magnus10 on 2011-08-18
Hi,

I am new to ubuntu and linux (installed ubuntu last week). However, I installed VLC (to view my DVDs on my new NAS) and as all of you write A/V was out of sync. After a few tries with other applications (Xbmc was the one that was closes to work, however, very slow - even with the Nvidia drivers) I concluded VLC was the only option (it is fantastic you can run the movie folder by just right clicking on them in the file browser and is fast in buffering). I fixed it maybe a little too brutally by removing pulseaudio completely (I was pissed off, and had not come across this wonderful thread). Everything is working fine now, however, my question is do I need pulseaudio for anything else or is asla good enough?

---

### Post by beew on 2011-08-18
> **magnus10 said:**
> Hi,

I am new to ubuntu and linux (installed ubuntu last week). However, I installed VLC (to view my DVDs on my new NAS) and as all of you write A/V was out of sync. After a few tries with other applications (Xbmc was the one that was closes to work, however, very slow - even with the Nvidia drivers) I concluded VLC was the only option (it is fantastic you can run the movie folder by just right clicking on them in the file browser and is fast in buffering). I fixed it maybe a little too brutally by removing pulseaudio completely (I was pissed off, and had not come across this wonderful thread). Everything is working fine now, however, my question is do I need pulseaudio for anything else or is asla good enough?

XBMC is very good with the Nvidia card (it uses vdpau) so maybe there is something wrong with your set up.  

I would recommend mplayer (or mplayer2) over VLC especially if you have a recent Nvidia card that supports VDPAU. It uses multicore (versions from ppa, don't know about the one in Ubuntu's official repo) while VLC uses only one, also mplayer uses VDPAU which drastically cuts down cpu usage in hd video playback.

I recommend this ppa for installing mplayer (it is actually mplayer2), don't mind about the coreavc stuff, it is not needed, just install the player and you are good to go.

[https://launchpad.net/~ripps818/+archive/coreavc]("https://launchpad.net/%7Eripps818/+archive/coreavc")

 For a gui front end, I suggest either smplayer or umplayer. You can find umplayer here
[https://launchpad.net/~nilarimogard/+archive/webupd8]("https://launchpad.net/%7Enilarimogard/+archive/webupd8")

Re: pulseaudio I would not remove it if I were you. It is an integral part of the system it seems. Also I find that sound is a lot better with pulseaudio than without.

---

### Post by magnus10 on 2011-08-18
Many thanks! I'll check it out.

---

### Post by bookcrazy on 2011-08-24
> **lidex said:**
> Make sure your audio out in vlc is set to default. It works fine for me but I note I do NOT 
have vlc-plugin-pulse installed.

OK, so I checked and yes my audio out was set to default in VLC.

Next problem was that my microphone crapped out on me and that is when I just gave up. I have undone the original fix and, low and behold my mike started working again :P I will manually sync the video when needed. I really can't wait for the next LTS to come out so I can just download that. 

Thanks again for all your help and suggestions!

---

### Post by swapnilps on 2011-08-28
:guitar:changing audio settings to ALSA in vlc player preferences.. worked for me..
thanks a ton for guidance..:KS


bt seriously.. unity is not so promising!!:(

---

### Post by pakotouch on 2011-08-30
Thank you, it works for me, good luck to the others

---

### Post by jgphreaky on 2011-09-01
post #18 works for me too! Thanks man you saved movie night! 

BTW - I'm using 10.04 with the pulse audio plugin and vlc player 1.1.11

I can skip around the video no problem and the audio works and is in sync. You rock!

---

### Post by shantiq on 2011-09-02
> **beew said:**
> I have 2 installations of Natty (Natty a has the Nvidia proprietary driver, Natty b uses nouveau with xorg-edgers)  and one Xubuntu 11.04 (with nouveau with xorg-edgers).  I  experienced the A/V sync problem for VLC 1.10  in all of them

I upgraded to VLC1.11 and this is what happened.

 The problem no longer exists for Natty b (no Nividia closed driver) but audio and video are still out of sync for Natty a and Xubuntu (so it is not a Nvidia driver problem)

After further research I found the following easy workaround that seems to solve the problem completely for my Natty a and Xubuntu 11.04 install and so far I have not experienced any side effect:

In the terminal type```
sudo gedit /etc/pulse/default.pa


```When /etc/pulse/default.pa opens in the text editor look for the line
and  add tsched=0 to the end
so it becomes
Then reboot and that's it.


I heretofore declare this**[ post]("http://ubuntuforums.org/showpost.php?p=11082570&postcount=18")** the most useful on the  Multimedia & Video forum in the last year         Amen   :KS    (seriously)   VLC is like one of the main organs of a modern PC like the eyes and the heart rolled into one and needs to be shipshape .....

---

### Post by Jimboland on 2011-09-18
> **ADroop said:**
> I have xubuntu 11.04 x64, and had this out of sync problem too. After reading many of your posts here, which was great and helpful.. I though to try the most simplest way.

I did this:

1) clicked on the sound icon in the right corner,  and changed that to ALSA.

2) Open vlc prefs. and went to audio.
 - a) out-put modual  changed to ALSA
 - b) checked the S/PDIF


This worked super for me.. all is synced.. and I also tried to close the vlc, and start it with a new movie.. and so on.. works fine :)


Thanks a lot!
This worked for me:p
One thing: When i selected "Select S/PDIF When available" I didn't have sound.
So for 11.04 XFCE/x64 Users:
In VLC change out-put modual to ALSA, and it works great!

THANKS ADroop!

---

### Post by GarbloJones on 2011-10-15
> **beew said:**
> I have 2 installations of Natty (Natty a has the Nvidia proprietary driver, Natty b uses nouveau with xorg-edgers)  and one Xubuntu 11.04 (with nouveau with xorg-edgers).  I  experienced the A/V sync problem for VLC 1.10  in all of them

I upgraded to VLC1.11 and this is what happened.

 The problem no longer exists for Natty b (no Nividia closed driver) but audio and video are still out of sync for Natty a and Xubuntu (so it is not a Nvidia driver problem)

After further research I found the following easy workaround that seems to solve the problem completely for my Natty a and Xubuntu 11.04 install and so far I have not experienced any side effect:

In the terminal type```
sudo gedit /etc/pulse/default.pa


```When /etc/pulse/default.pa opens in the text editor look for the line
and  add tsched=0 to the end
so it becomes
Then reboot and that's it.


Finally!! This seemed to fix my problem
 --- side note: i also had an issue with audio not playing after resuming from pause - that may have had something to do with using VLC 1.10

so to summarize - I currently am running 11.10 with VLC 1.1.11 (all AV settings to DEFAULT) and i added tsched=0 to my /pulse/default.pa

hope this works for everyone else

Thanks!

---

