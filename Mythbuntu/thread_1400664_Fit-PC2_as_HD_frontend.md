---
title: "Fit-PC2 as HD frontend"
date: 2010-02-07
forum: Mythbuntu
---

### Post by jensk on 2010-02-07
Has anyone tried the Fit-PC2 as a HD frontend?

As my present Shuttle X27D with intel GMA is nor able to playback HD content without stuttering and 100% taxing of the CPU i'm wondering which new frontend pc to buy.

What i need is DVI or HDMI output. Low noise and low power consumption. I prefer build-in ir-receiver but have a homebuild ir-reciever.

Until now I have looked at an Asrock ION 330HT and  Fit-PC2.

The Asrock is supported in Mythbuntu both the ION graphics and the ir-reciever.

How about the Fit-PC2? 
The Intel chipset Intel US15W SCH and graphics GMA500. Are they supported so I can playback my HD recordings, And what about the Ir-receiver?

Has anyone tried this very low power unit (6 wats) as a HD frontend?

Any feedback is very welcome.

---

### Post by nickrout on 2010-02-09
May I suggest something else? The Revo is only $200 (USA) and can do vdpau, making it a low power and quiet solution.

---

### Post by sydneysuder on 2010-04-09
I just got a demo unit through work and am having  a couple of problems with it. I am going to re-install mythbuntu to make sure I didn't cause the problems myself.

1. Connecting via VGA (1368 etc) to my TV (Bravia 42) gives the wrong resolution to Ubuntu (and can't select the correct one) so there is a an area to the right where it just flickers bits and pieces of the video being displayed elsewhere.
2. Could be from 1 or from the profile configuration but HD playback is jerky, even when connected via ethernet.
3. Same as 1 on an Apple Cinema display 20" but when changing the resolution to the native screen resolution I just get a blank screen.

Other than that it may be worth mentioning that the unit runs very hot.

---

### Post by nickrout on 2010-04-09
> **sydneysuder said:**
> I just got a demo unit through work and am having  a couple of problems with it. I am going to re-install mythbuntu to make sure I didn't cause the problems myself.

1. Connecting via VGA (1368 etc) to my TV (Bravia 42) gives the wrong resolution to Ubuntu (and can't select the correct one) so there is a an area to the right where it just flickers bits and pieces of the video being displayed elsewhere.
2. Could be from 1 or from the profile configuration but HD playback is jerky, even when connected via ethernet.
3. Same as 1 on an Apple Cinema display 20" but when changing the resolution to the native screen resolution I just get a blank screen.

Other than that it may be worth mentioning that the unit runs very hot.

I doubt you will get much in the way of HD playback from that machine. See my earlier post for a better solution. 

Fit is only an atom with no graphics acceleration. You really want an ION solution.

---

### Post by sydneysuder on 2010-04-12
> **nickrout said:**
> I doubt you will get much in the way of HD playback from that machine. See my earlier post for a better solution. 

Fit is only an atom with no graphics acceleration. You really want an ION solution.


> **nickrout said:**
> I doubt you will get much in the way of HD playback from that machine. See my earlier post for a better solution. 

Fit is only an atom with no graphics acceleration. You really want an ION solution.


Well the sales literature makes a big deal about HD playback (it has an intel card). And the Ubuntu wiki on their site has specific commands to install the right drivers and mplayer for HD playback.

Apart from that: I have done a re-install and everything except HD playback is working on Myth.

Here is what I did (Note that this is a secondary be/fe)

1. Install from the live CD as a slave backend with frontend
2. Follow the steps from the fit website wiki to install the video drivers and HD playback stuff. Without this the max resolution is 1024*768)
3. Install all the updates indicated by the update manager. The main benefit seemed to be (from a very casual test) the boot up time was reduced.
4. Activate the mythbuntu repos (0.22) and update. Without this SD (live TV or recordings) streamed from the MB is too jerky and the response times to keyboard inputs is too slow.
The downside is that the little legend "Playback starting ..." at the beginning of recordings and live TV is screwed up and the three dots ("...") show up as a funny random character. But that is a problem with the repos as the same thing happens on my other FEs.
5. Install the firmware for a PCTV 73e (nanostick)
6. Add the nanostick as another capture card and do the normal input configuration stuff.

The result:

1. SD live TV and recordings from the MB work fine.
2. SD Live TV and recordings using the local tuner work fine.
3. HD live TV from the MB pauses every second. (See Note 1)
4. 720P Recordings from the MB pause every few seconds
5. 1080P recordings from the MB pause every second or so.
6. Haven't tried recordings from the local tuner.
7. The MCE remote that I have used on other FEs running mythbuntu doesn't seem to work. I just plugged it in and selected it in the remote setup screen. That was all I had to do on the other frontends but it seems on this one it may need more configuration.


Note1: This could very well be an issue with the wireless network performance as I have only used the wireless on the fitPC2. Considering that I have another front end (mac mini 2Ghz core2duo, 2GBRAM) dualbooting mythbuntu 9.10 and OSX 10.5.8 and that when using the wireless network I can't watch HD tv/recordings on Mythbuntu ( This is not a problem when running OSX.)  I am inclined to think that the performance of the ubuntu wireless drivers that may be causing the jerkiness.

Having said that, the Mythbuntu FE on the MacMini hasn't been updated at all (no updates or mythbuntu repos) and the Myth FE on OSX is tracking the weekly builds so I may be wrong altogether.

---

### Post by nickrout on 2010-04-12
> **sydneysuder said:**
> Well the sales literature makes a big deal about HD playback (it has an intel card). And the Ubuntu wiki on their site has specific commands to install the right drivers and mplayer for HD playback.

Apart from that: I have done a re-install and everything except HD playback is working on Myth.

Here is what I did (Note that this is a secondary be/fe)

1. Install from the live CD as a slave backend with frontend
2. Follow the steps from the fit website wiki to install the video drivers and HD playback stuff. Without this the max resolution is 1024*768)
3. Install all the updates indicated by the update manager. The main benefit seemed to be (from a very casual test) the boot up time was reduced.
4. Activate the mythbuntu repos (0.22) and update. Without this SD (live TV or recordings) streamed from the MB is too jerky and the response times to keyboard inputs is too slow.
The downside is that the little legend "Playback starting ..." at the beginning of recordings and live TV is screwed up and the three dots ("...") show up as a funny random character. But that is a problem with the repos as the same thing happens on my other FEs.
5. Install the firmware for a PCTV 73e (nanostick)
6. Add the nanostick as another capture card and do the normal input configuration stuff.

The result:

1. SD live TV and recordings from the MB work fine.
2. SD Live TV and recordings using the local tuner work fine.
3. HD live TV from the MB pauses every second. (See Note 1)
4. 720P Recordings from the MB pause every few seconds
5. 1080P recordings from the MB pause every second or so.
6. Haven't tried recordings from the local tuner.
7. The MCE remote that I have used on other FEs running mythbuntu doesn't seem to work. I just plugged it in and selected it in the remote setup screen. That was all I had to do on the other frontends but it seems on this one it may need more configuration.


Note1: This could very well be an issue with the wireless network performance as I have only used the wireless on the fitPC2. Considering that I have another front end (mac mini 2Ghz core2duo, 2GBRAM) dualbooting mythbuntu 9.10 and OSX 10.5.8 and that when using the wireless network I can't watch HD tv/recordings on Mythbuntu ( This is not a problem when running OSX.)  I am inclined to think that the performance of the ubuntu wireless drivers that may be causing the jerkiness.

Having said that, the Mythbuntu FE on the MacMini hasn't been updated at all (no updates or mythbuntu repos) and the Myth FE on OSX is tracking the weekly builds so I may be wrong altogether.

1. advertised as HD capable probably relates to windows only. AFAIK there is no intel video acceleration available for linux.

2. Wireless is the first thing to eliminate. Generally G is OKish for SD material, but no good for HD. Bite the bullet, run the wires. I speak from experience.  If just experimenting and don't want to open your walls run a cable through the house, it'll only take you a maximum of an hour to work out if wireless is the problem.( by the way some people report OK quality on N).

if a proper wired network doesn't fix it, report back (in fact report back either way)

---

### Post by sydneysuder on 2010-04-12
> **nickrout said:**
> 1. advertised as HD capable probably relates to windows only. AFAIK there is no intel video acceleration available for linux.

2. Wireless is the first thing to eliminate. Generally G is OKish for SD material, but no good for HD. Bite the bullet, run the wires. I speak from experience.  If just experimenting and don't want to open your walls run a cable through the house, it'll only take you a maximum of an hour to work out if wireless is the problem.( by the way some people report OK quality on N).

if a proper wired network doesn't fix it, report back (in fact report back either way)

ARRGG... typed a long response and it didn't take it....

In short: Using the wired network made things better but still not watchable via Myth.
Copying a 720P file locally worked ONLY with VLC and in window mode (not full screen). I say worked because it was actually watchable. There was stuttering but barely noticeable.
I did not have time to try a 1080P.

I may try windows 7 next. The machine will only be a FE/BE so maybe I can ignore the MS bits.

---

### Post by JMcFly on 2010-04-13
What about this MSI Nettop (bare bones, but includes an ATI Radeon 4330 and dual-core Atom): [Newegg](http://www.newegg.com/Product/Product.aspx?Item=N82E16856167039&Tpk=msi%20nettop)?
Seems like some ram and a compact flash card (or a cheap SATA drive) could get you running with a minimal front end for around $200-250.

---

### Post by sydneysuder on 2010-04-13
> **JMcFly said:**
> What about this MSI Nettop (bare bones, but includes an ATI Radeon 4330 and dual-core Atom): [Newegg](http://www.newegg.com/Product/Product.aspx?Item=N82E16856167039&Tpk=msi%20nettop)?
Seems like some ram and a compact flash card (or a cheap SATA drive) could get you running with a minimal front end for around $200-250.

The main issue with the FIT is the CPU grunt since there is no Intel acceleration support in Linux . I don't know about ATI acceleration support. 

The Atom I was trying was the 1GHZ one. I am exchanging it for the 1.6GHz one. Which is the same as the Nettop 120. 

I will post when I try it and maybe it will apply to the Nettop.

---

### Post by sydneysuder on 2010-04-19
SUCCESS!

I got the replacement unit with the 1.6GHZ CPU. All I had to do was plug in the hard drive from the other unit and BOOM everything works. Even watching HD programs over wireless (g).

The next step was to get the MCE remote working. For some reason the computer does not recognize the IR reader (USB). It is the first computer I come across that does that.  In any case, I managed to get it working with the built-in IR. I had to use irrecord as the codes shown by the receiver are different to those from the MCE receiver. It was a bit painful to record all the keys and map them in mythtv manually but it works.

The only complain is that the response time on the remote is too long. And about 1/3 of the time it ignores the input.

---

### Post by jensk on 2010-04-22
I thought taht trying to get the intel GPU (Poulsbo) to work steady with hw accel on every version was a bit over my head. In stead I ended up with a Acer Sspire Revo 3600 that i bought at amazon.co.uk for 150£

After remove autoboot at the internal linux everything installed without any problems. Running VDPAU and sound over HDMI allmost out of the box. so it could not be much easier.

The Revo has a fan but the fan must be stopped while the revo is running because it doesn't make any noise.

It plays HD 720P taxing the CPU 10 - 15 %

/jensk

---

### Post by MiataMuc on 2010-08-22
Hi,

just wanted to ask: I have a Fitpc 2 running with Kubuntu 10.4, added the GMA500 support as described in the [Fitpc 2 Forum]("http://www.fit-pc2.com/forum/viewtopic.php?f=58&t=1819") and would like to get Mythtv - Backend running (for SD - DVB-T), but I don't find a way of getting a TV-Picture to the screen. Any hints?

Thanks,

Flo

---

