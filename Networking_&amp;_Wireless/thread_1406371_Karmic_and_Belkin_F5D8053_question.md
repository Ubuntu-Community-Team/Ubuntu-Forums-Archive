---
title: "Karmic and Belkin F5D8053 question"
date: 2010-02-13
forum: Networking &amp; Wireless
---

### Post by Mimsy on 2010-02-13
I have a Belkin F5D8053 USB wireless adapter on my desktop computer. I'm typing from Windows XP right now, where the USB adapter works great. When I'm using the Karmic Koala liveCD the Belkin adapter works to the point where it picks up the available networks and lets me put in my pass phrase and all other configuration stuff... and then it spins the connection symbol for 20+ minutes and then disconnects.

I saw on the wiki Supported Hardware List that my adapter works Out Of The Box (TM) in Jaunty but stops working that way in Karmic, and there is a link to a blog entry telling me how to use Wine and ndiswrapper to make it work, but it doesn't specify which Ubuntu version that is for. So should I follow those instructions for Karmic, or try to get my hands on a copy of Jaunty?

Note that the instructions to make the F5D8053 work involve downloading files, which I am not able to do from my liveCD, and will not be able to do once I have installed the OS.

Blog/instructions for the F5D8053 are here: [https://help.ubuntu.com/community/WifiDocs/Device/Belkin%20F5D8053](https://help.ubuntu.com/community/WifiDocs/Device/Belkin%20F5D8053)

---

### Post by Mimsy on 2010-02-16
I installed Karmic on the PC, using Wubi, for testing a bit more. It can still see my network, but not connect. I tried installing the drivers from my CD via ndiswrapper, but it doesn't seem to make a difference. :(

Now that Karmic is semi-installed, what information should I get from there and post that would be helpful to you?

---

### Post by mark bower on 2010-02-17
I highly recommend using the Belkin F5D7050 USB wireless adapter, which works with the linux native drivers.  I can practically guarantee it working out of the box.  It was recommended in two posts before I purchased mine.  I have used it with Ubu 9.04 and 9.10, three different computers and as many motherboards, with absolutely no problems.  So I keep posting this information.

I purchased the F5D7050 because my PCI wireless adapters did not work.  I have had instant success using ndiswrapper for my Hawking card.  But each time I rebuild a HD due to new Ubu versions or my goofs, I have to go thru the ndiswrapper set up again.  This is not trivial considering WINE setups and a number of  tweaks, copying back to the HD from back-ups, etc, etc.  Maybe even zeroing the HD before rebuilding  as I have found some reinstallations of Ubuntu do not function properly if not starting from "absolute scratch", ie, a zeroed HD.

mark

---

### Post by Mimsy on 2010-02-21
Apologies for the late reply; life interfered.

I guess where I am a bit frustrated is that according to all I've read, my adapter worked out of the box in Jaunty, so it irritates me that when the only version availale to me is Karmic, I'm stuck either being off-line on my PC or buying a new adapter.

Can't I just use Jaunty instead? Does anyone have a torrent?

---

### Post by sect7 on 2010-03-06
Looks like I'm having the same issue. Maybe I'll try installing Jaunty instead. If that doesn't work out I'll just pick up one of the plug-n-play adapters listed in the Ubuntu docs.

---

### Post by sect7 on 2010-03-06
> **sect7 said:**
> Looks like I'm having the same issue. Maybe I'll try installing Jaunty instead. If that doesn't work out I'll just pick up one of the plug-n-play adapters listed in the Ubuntu docs.

Does "out of the box" mean installing Wine isn't necessary? Or do I just install Wine and the ndiswrapper, and the adapter should work. I did the latter on Jaunty and I no wireless networks show up when I open the Belkin wireless utility.

---

### Post by 2hot6ft2 on 2010-03-06
I have the Belkin F5D8053 ver.4001 and I used this how to:
[ [SOLVED] Karmic RT2870 Driver Tutorial_RALINK RT2870STA and RT3070STA USB WiFi Tutorial]("http://ubuntuforums.org/showthread.php?t=1342593")

I used the RT3070STA to get the N speeds along with setting my encryption to WPA2 Personal AES.
I'm using Karmic 9.10

---

