---
title: "how to tell if I'm using vdpau?"
date: 2009-11-09
forum: Mythbuntu
---

### Post by feh on 2009-11-09
Hi folks.

I'm running kubuntu 9.10 and the most recent mythtv in the ubuntu repositories. 

The playback of video isn't real smooth on my machine...how can I determine if I'm using vdpau in mythtv?

Thanks!

---

### Post by nickrout on 2009-11-09
Check you are using the right profile.

[http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)

Look in your frontend logs.

---

### Post by brianafischer on 2009-11-09
I added some information on this to the Wiki.  It is not obvious where the VDPAU settings are in mythfrontend or that they need to be enabled:

[http://www.mythtv.org/wiki/VDPAU#Enabling_VDPAU_in_MythFrontend](http://www.mythtv.org/wiki/VDPAU#Enabling_VDPAU_in_MythFrontend)

---

### Post by feh on 2009-11-10
> **brianafischer said:**
> I added some information on this to the Wiki.  It is not obvious where the VDPAU settings are in mythfrontend or that they need to be enabled:

[http://www.mythtv.org/wiki/VDPAU#Enabling_VDPAU_in_MythFrontend](http://www.mythtv.org/wiki/VDPAU#Enabling_VDPAU_in_MythFrontend)

Thanks for the link.

I'll have to experiment some more...I was trying different settings last night, and couldn't get any vdpau settings to work decently. I was playing back 1080i content, and the video would slow down, speed up, slow down, speed up. CPU usage was low, but the video was unwatchable.

Using other (non-vdpau) options resulted in better playback. I have an on-board GeForce 8200. I know the hardware is capable of providing smooth 1080i playback, as I used to run Windows 7 Media Center on the same box, and the video was great.

---

### Post by Dewey_Oxberger on 2009-11-10
I have an 8300 based board and I was having the same problem.

I made my own profile that used the Bob deinterlacer on all resolutions.

Then I tinkered with the cpu frequency scaling.  On my system the cpu freq was defaulting to 1.0GHz.  Rumor has it that's too low for the 8000 series chips to run well.  I'm not sure if that's true.

I installed cpufrequtils.  Tinkered for a while with cpufreq-info to check the frequency and cpufreq-set to set the min frequency.

After some tinkering I noticed it was working.

So I installed cpufreqd and edited cpufreq.conf to change the ac power = on profile to set the min freq to 1.8G.

Seems to work now.  This is with the stock 9.10 185 driver.

---

