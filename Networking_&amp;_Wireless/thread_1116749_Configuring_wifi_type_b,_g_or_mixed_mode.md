---
title: "Configuring wifi type b, g or mixed mode"
date: 2009-04-05
forum: Networking &amp; Wireless
---

### Post by SnappyU on 2009-04-05
Ubuntu build: Intrepid and Jaunty Beta

Hi all,

I'm using Network Manager 0.7 to connect to the wifi router and it is working ... somewhat.

I'm trying to determine why "Connection Information" for the connection shows random or fluctuating connection speed.

I also notice that there is no option for selecting the interface mode, as in, whether to use b, g, or bg mixed mode.

In Windows, I could select the mode, with the Network Manager, I cannot.

Is NM0.7 configuring the interface mode (b,g,bg) automatically, and if so, how can I find out the status and change the mode if I want to.

Am I alone with this?  
Thanks for any insight! :)

---

### Post by SnappyU on 2009-04-06
*bump*

---

### Post by sgosnell on 2009-04-06
You can set the allowed modes on the router.  The mode on the PC is set by the hardware wifi adapter, AFAIK, not the OS.

---

### Post by SnappyU on 2009-04-11
You are right in that the AP's mode is set at the router.
But the client's mode can be set as well, and would determine if it connect to an AP or not.

If a client is set at mixed mode, it can connect to b and g APs, but is not so efficient (I think).
If AP is pure g mode, client should be set to pure g mode for best results.
If AP is pure b mode, client should be set to pure b mode for best results.

Oh come on, am I the only one wondering?

---

### Post by sgosnell on 2009-04-12
You should only set the router to b if you have devices that can only operate in b.  PalmOS devices, and some other older handhelds require b, so I keep mine set to mixed mode.  I allow my computers and Palms to connect with whatever mode they like, and it all works fine for me.  If an AP is set to only g, then my Palm can't connect.

---

### Post by SnappyU on 2009-04-13
I actually have my router set to g mode.  The examples I gave are just that, examples.
I'm trying to see how I can force my notebook wifi to g mode, 'cos I believe the mixed mode in my nb is not v efficient.

So my question remains: "How do I set/force my notebook wifi to g mode?"

---

### Post by sgosnell on 2009-04-13
The notebook should be using one or the other.  The mixed mode is on the router, AFAIK, not on a PC.  What is telling you the notebook is using mixed mode?

---

### Post by SnappyU on 2009-04-17
> **sgosnell said:**
> The notebook should be using one or the other.  The mixed mode is on the router, AFAIK, not on a PC.  What is telling you the notebook is using mixed mode?

The point is that I have no *clear* way of telling the mode that my notebook is in, nor any way of setting the mode.

It simply connects to an AP regardless of whether it is b or g mode.  That seem to tell me that it could be in a bg mode.

iwconfig gives
> wlan0     IEEE 802.11bg  ESSID:"SpeedTouch4C3ACB"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: ##:##:##:##:##   
          Bit Rate=18 Mb/s   Tx-Power=13 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=46/100  Signal level:-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


iwconfig always returns "wlan0     IEEE 802.11bg" for my machine as well.  But no indication in NetworkManager says whether my notebook is in b, g or mixed mode.

---

### Post by SnappyU on 2009-04-22
*bump*

---

### Post by SnappyU on 2009-04-22
*bump*

---

### Post by dimamali on 2009-12-15
I am having the same problem! Very slow wLAN transfers. My router is set to G and my laptop card is ser to G by default...However my desktop card is in bg mode and i want to change that.
Anyone?

---

### Post by sgosnell on 2009-12-15
One more time:  Set the router to whatever mode you want, and the computers which connect to it must use that mode.

---

### Post by msbohn on 2009-12-16
I think the OP's point was that his client is *not* setting to the router's b/g/mixed mode.

I've got the same problem.  My router is set to g only and my connection speed is only 5 to 9 Mb/sec which sounds like it is trying b mode.

More info:  I set my router from g mode to mixed mode.  Now, I see in Connection Information a bit rate of 36 Mb/s but still no connection.  Weird that changing from g to mixed would cause the client to bump up from 5-9 Mb/s to 36 Mb/s.

---

### Post by sgosnell on 2009-12-16
If the router is set to g only, devices cannot connect using b.  Devices which are b only can't connect, but if they can use either, they can only connect using g.  If the router is set to mixed, then devices can connect using either.  The speed isn't set solely by the mode, it is also affected by the connection quality.

---

### Post by msbohn on 2009-12-16
> **sgosnell said:**
> If the router is set to g only, devices cannot connect using b.  Devices which are b only can't connect, but if they can use either, they can only connect using g.  If the router is set to mixed, then devices can connect using either.  The speed isn't set solely by the mode, it is also affected by the connection quality.

So why does the same hardware connect at g speeds under XP but can't connect at all under Ubuntu?

---

### Post by sgosnell on 2009-12-16
Settings, or lack of a correct driver.

---

### Post by msbohn on 2009-12-16
> **sgosnell said:**
> Settings, or lack of a correct driver.

Absolutely!  But my driver is correct b43 and we've already established that there are no settings on the client-side for b/g.

---

### Post by sgosnell on 2009-12-16
You said 'can't connect at all'.  That likely isn't a function of the mode, but of bad settings, if you have the correct driver for your wifi radio.  If it's a speed problem, it's still settings, somewhere.  It's hard to diagnose from long distance, especially with a laptop, with proprietary hardware.  The wiki may have information that will help you.

---

### Post by msbohn on 2009-12-17
> **sgosnell said:**
> You said 'can't connect at all'.  That likely isn't a function of the mode, but of bad settings, if you have the correct driver for your wifi radio.  If it's a speed problem, it's still settings, somewhere.  It's hard to diagnose from long distance, especially with a laptop, with proprietary hardware.  The wiki may have information that will help you.

Yes, that makes sense.  I have spent a lot of time on the forum, but I'll dig in to the wiki some more.

Thanks for your help.

---

### Post by SnappyU on 2010-02-01
> **sgosnell said:**
> You said 'can't connect at all'.  That likely isn't a function of the mode, but of bad settings, if you have the correct driver for your wifi radio.  If it's a speed problem, it's still settings, somewhere.  It's hard to diagnose from long distance, especially with a laptop, with proprietary hardware.  The wiki may have information that will help you.

I have updated my WinXP drivers and now I can connect to my router @ 300Mbps in Windows.  But in Jaunty, it just connects to whatever speed it can, which is sometimes G speed 54Mbps, but mostly 30+Mbps.  And as msbohn and dimamali also encountered, the connection speed is not optimal.

---

