---
title: "VLC: sound cuts out (ubuntu 10.04)"
date: 2010-05-15
forum: Multimedia Software
---

### Post by HyperFlexed on 2010-05-15
Hi, I'm running Ubuntu 10.04 with the realtime kernel.

```
johnny@picard:$ uname -r
2.6.31-10-rt

```

VLC is 1.0.6

Symptom: Playing video files works fine, however sometimes the audio just stops playing. The video continues. Only reliable fix is to write down where I left off, close VLC, and restart where I left off. While the audio stops working in VLC, I'm able to play wav files using aplay. The rest of system sounds still work fine.

I'm wondering if anyone else has had this issue, or if I should open up a bug report.

---

### Post by clydacs on 2010-05-17
I've had a similar problem with I first noticed playing Chromium B.S.U.  Shortly after starting a game there is a momentary pause (less than a second) of movement when the sound stops.  My audio is onboard Realtek AC97 on an older P4 2.8 GHZ ATX with 756MB ram.  Audio also doesn't work with youtube or hulu (flash) under firefox 3.6 and the current adobe flash plug-in from Ubuntu software center.

---

### Post by HyperFlexed on 2010-05-18
> **clydacs said:**
> I've had a similar problem with I first noticed playing Chromium B.S.U.  Shortly after starting a game there is a momentary pause (less than a second) of movement when the sound stops.  My audio is onboard Realtek AC97 on an older P4 2.8 GHZ ATX with 756MB ram.  Audio also doesn't work with youtube or hulu (flash) under firefox 3.6 and the current adobe flash plug-in from Ubuntu software center.

You're also using the realtime kernel?

---

### Post by clydacs on 2010-05-18
Actually I'm not running the realtime Kernel - Linux 2.6.32-22 generic.  This is the first time I've worked with Linux and until you mentioned it I didn't know there was a "realtime" Kernel.  Is it possible the sound cut out is related to the graphics driver (NVIDIA)?  It seems that when ever I'm doing something where video hardware acceleration is tapped that's when the sound goes.

---

### Post by HyperFlexed on 2010-05-18
Now that you mention it, that seems to be the case for me as well. Audio players work fine, but as soon as I watch youtube, or use VLC, I have to constantly restart the program to fix the problem.

With the generic kernel, my sound works, but the video will freeze occasionally while the sound runs on. I'm using the NVIDIA drivers as well.

---

### Post by budzis on 2010-05-18
1

---

### Post by budzis on 2010-05-18
I have a Ubuntu 10.04. After installation there was no problem - the video was played, the sound was. But then, after the imposition of a renewal, started the problems. VLC playing video suddenly lost sound. Flash player stops in Firefox and Chromium and the browser stops working altogether. Totem player plays the video and every time stops for 10-30 seconds.

---

### Post by clydacs on 2010-05-18
I spent a little more time on the sound fallout; I installed tried the LXDE envirionment but still had the sound falloff while running Chromium B.S.U. and could not run youtube feeds.  I installed 'latencyTOP" and found delays waiting for the cpu of up to and sometimes over 1second for Xorg, firfox, Compiz, and Jbd2/Sda5-8.  I'm not really sure how to inturpret the results of latancyTOP but from what I understand it appears the there is excessive latency in the video processes when put under higher demand.  My Nvidia card is older with only 64MB however much more demanding applications run well under windows on the same computer (netflix watch now, celestia with high res textures etc.  I still suspect the sound fall out is related to the video drivers.  Maybe there is a buffer issue with older nvidia cards?

---

### Post by JayRobert on 2010-05-19
I don't think it's just older NVIDIA cards - I have a three-month old Gigabyte GeForce GT 240 with the same kind of issues.  I have also tried several realtime kernels to see if it was just lack of NVIDIA support for a particular kernel, since I have read that sometimes NVIDIA support for the realtime kernels lags a bit, but same result with each - see [this thread]("http://ubuntuforums.org/showthread.php?t=1487419") for details.

---

### Post by clydacs on 2010-05-19
It makes sense then that it may be an issue with the NVIDIA drivers.  Additionally, I have a second older computer configured much the same as the one I originally posted about except it has onboard video and doesn't use NVIDIA drivers.  With Ubuntu 10.04 it runs fine without sound fall out although youtube and hulu (and possible other streaming content) seem to run a bit slower than the same system under windows XP.  How does one go about starting a bug report?

---

### Post by JayRobert on 2010-05-19
I've never filed one yet, but found this with a little searching: [Launchpad]("https://launchpad.net/ubuntu").

I have to go into work shortly, or I would figure out how to file it myself.  I will look back at this thread late tonight to see if you were able to do so; if not, I'll try to file a bug report on this.

Thanks!

---

### Post by lidex on 2010-05-20
> **HyperFlexed said:**
> Hi, I'm running Ubuntu 10.04 with the realtime kernel.

```
johnny@picard:$ uname -r
2.6.31-10-rt

```

VLC is 1.0.6

Symptom: Playing video files works fine, however sometimes the audio just stops playing. The video continues. Only reliable fix is to write down where I left off, close VLC, and restart where I left off. While the audio stops working in VLC, I'm able to play wav files using aplay. The rest of system sounds still work fine.

I'm wondering if anyone else has had this issue, or if I should open up a bug report.
What do you have audio output set to in vlc? Firefox/flash:
[http://ubuntuforums.org/showthread.php?t=1455816]("http://ubuntuforums.org/showthread.php?t=1455816")

---

### Post by sojournerC on 2010-05-28
I am using a professional sound card in a PCI slot - Juli@ by EVO - and have the same problems with sound cutting out. 

It happened in Karmic and now in Lucid as well. 

This may isolate it away from drivers. 

Perhaps some buffer numbers in pulse or alsa plugins?

---

### Post by clydacs on 2010-06-03
It's been a while since I've been able to get back to this but I tried the link that lidex posted.  I created the conf file as described and there was no difference.  souournerC, do you have the nvidia driver for video?

---

### Post by chrisinspace on 2010-06-04
I've been having a similar issue, but I haven't been able to find a solution yet.  There's a tons of postings and articles about getting sound to work when it is totally broken, but not much on sound that works fine and then drops from time to time.  This is affecting me across multiple applications (XBMC, VLC, Flash) and I do have the nVidia (195) driver.  The media hangs for a second and then resumes playing, but without sound.

---

### Post by Replicounts on 2010-07-06
Simple test if no sound with VLC etc. -- try with headphones. 

Note that you DO hear system alert tones from the speaker, even if the speaker is turned off in the system settings. At least you do hear the Ubuntu alert on my Netbook. And the default when I downloaded Ubuntu 10 is that the speaker was turned off -- understandably, since $300 netbooks won't spend money for quality speakers.

To check your setting, under **System**, choose **Preferences**, then **Sound**. Click the **Output** tab. Then at "Connector:", make sure it is set to **Analog Speakers**, unless you don't want any audio (except alerts) from the speakers.

---

### Post by HyperFlexed on 2010-07-07
> **Replicounts said:**
> Simple test if no sound with VLC etc. -- try with headphones. 

Note that you DO hear system alert tones from the speaker, even if the speaker is turned off in the system settings. At least you do hear the Ubuntu alert on my Netbook. And the default when I downloaded Ubuntu 10 is that the speaker was turned off -- understandably, since $300 netbooks won't spend money for quality speakers.

To check your setting, under **System**, choose **Preferences**, then **Sound**. Click the **Output** tab. Then at "Connector:", make sure it is set to **Analog Speakers**, unless you don't want any audio (except alerts) from the speakers.

relevance?

---

### Post by Robertm305 on 2010-07-11
hello everybody my sound keeps cutting off after i start playing music on vlc, rythmbox , and movie player but when i press stop and play it starts working again but it still cuts out does any one know how to fix this im really new to ubuntu please i need helppppppppppppppppppppppppppp

---

### Post by Robertm305 on 2010-07-11
hello everybody my sound keeps cutting off after i start playing music on vlc, rythmbox , and movie player but when i press stop and play it starts working again but it still cuts out does any one know how to fix this im really new to ubuntu please i need helppppppppppppppppppppppppppp

---

### Post by medley_44 on 2010-07-26
I'm having a similar problem in Mythbuntu 10.04. Sound will occasionally cut out while watching a movie, which requires me to exit out of the movie and then play it again.

Note that this does not concern VLC, since I use MythTV's "Internal Player". However, my problem seems relevant to this post because I have an older nVidia card and am using the proprietary drivers; so, there may be a connection.

I ran Mythbuntu 9.04 on the same hardward for over a year and never experienced any sound problems.

I'm using the default kernel, by the way.

---

### Post by fernando-madrid on 2010-08-07
Same problem here.

Vlc, youtube, skype work fine for a while then sound stops.

I have Ubuntu Studio Lucid 10.4 (kernel 2.6.31-11-rt) upgraded from 8.04 on a Dell laptop XPS M1330 and all sounds worked fine for a couple of months after upgrade but about 3 weeks ago the sound breaks after a playing for while.  

I've followed Temüjin instructions with asound.conf ([http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)).
I've updated alsa with AlsaUpgrade-1.0.23-2.sh and the problem still persists.

Any ideas?

Thanks in advance.

fer

---

### Post by lidex on 2010-08-07
Does this happen with skype running - how about without?

---

### Post by fernando-madrid on 2010-08-07
> **lidex said:**
> Does this happen with skype running - how about without?

It happens without skype running, if it is skype what I'm using skype's sound (mic and all) stops working.
I don't think it is a vlc or skype issue I think it must be at a lower level.

---

### Post by carlotheman on 2010-08-18
I have the same problem.

I have the realtime kernel and an ATI graphics card running the open source drivers.

I use a my interal sound card, but a PCMCIA sound card is also installed.

It happens mainly using VLC.

---

### Post by roy.nico on 2010-08-20
> **clydacs said:**
> Actually I'm not running the realtime Kernel - Linux 2.6.32-22 generic.  This is the first time I've worked with Linux and until you mentioned it I didn't know there was a "realtime" Kernel.  Is it possible the sound cut out is related to the graphics driver (NVIDIA)?  It seems that when ever I'm doing something where video hardware acceleration is tapped that's when the sound goes.

Hello, for me it was the case. I have been fighting a long time with crackly sound under lucid (with all apps). I found the "solution" yesterdays : i removed the proprietary drivers for my nvidia onboard graphic card, reboot, and it was ok. Now, i can't have the nice 3D desktop effects, but at least i can hear music...

But why the graphics drivers interfere with the sound ... big mystery

nico

---

### Post by supersas on 2010-08-20
hi, 
i have got the problem with sound. whenever i try to play any type of sound it plays for a while then it stops and i have play it again. i notice that when the sound stops then at the same time something happen to the volume controller in the above panel. It shows itself mute for a second then sound stops and then the volume goes up again but i cant here any thing . to listen to it i have to play it again. 
i tried to do solve this problem by using the steps you guys told but nothing worked here..
Please guide me through this problem. i am very sad about my ubunuts sound :(

---

### Post by lidex on 2010-08-20
> **supersas said:**
> hi, 
i have got the problem with sound. whenever i try to play any type of sound it plays for a while then it stops and i have play it again. i notice that when the sound stops then at the same time something happen to the volume controller in the above panel. It shows itself mute for a second then sound stops and then the volume goes up again but i cant here any thing . to listen to it i have to play it again. 
i tried to do solve this problem by using the steps you guys told but nothing worked here..
Please guide me through this problem. i am very sad about my ubunuts sound :(

Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

