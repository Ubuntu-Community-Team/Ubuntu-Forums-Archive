---
title: "Linksys WUSB54AG can't connect, causes crashes: Possible driver issue?"
date: 2006-04-19
forum: Networking &amp; Wireless
---

### Post by snuhbort on 2006-04-19
Alternate thread title:  Yet another wireless USB problem.

I'm presently attempting to connect to my home wireless network using a Linksys WUSB54AG USB network adapter.  As you can probably guess, it's not working.

Here's the situation:  Ubuntu is installed on a secondary machine, set to dual-boot with Windows XP.  Lacking a free PCI slot on this machine, I purchased the aforementioned USB WiFi adapter to connect to my wireless network.  I set up the adapter on my Windows XP partition, and it successfully connected.  In fact, I'm using it to post this.

I then booted to my Ubuntu partition and, not finding any mention of native drivers for this particular model, I used the instructions on this forum for using ndiswrapper to use the included Windows drivers.  Things went relatively smoothly, and the adapter was detected in the Networking settings.  I entered all relevant information therein and got... nothing.  The Link light on the adapter was slowly blinking, and nothing was going through.

I restarted the computer and booted to Windows, with the adapter still connected.  When Windows started, however, the Link light on the adapter started blinking, and I received the error "Access  violation at address 00000000.  Read of address 00000000."  The adapter wouldn't connect.  I unplugged and reinserted the cable, and this time the Link light turned solid and I was connected once again.

So I rebooted into Ubuntu, entered the terminal and ran "sudo modprobe ndiswrapper" once again.  The adapter started blinking.  I double-checked the Networking settings, they were all correct, so I tried unplugging the adapter.  Ubuntu froze.  I rebooted, tried again, and got the same result.  Just to make sure, I then tried again, and got the same result the third time.  Upon rebooting into Windows, I once again got the Access violation error.  Once again, unplugging and re-plugging the cable fixed the issue.

So.  That's the situation.  I'm far from an expert, but I thought it might be a driver issue, since the adapter has problems on startup in both Windows XP and Ubuntu, the problems are largely similar (albeit more severe in Ubuntu), and I'm using the same drivers for both.  I checked the Linksys website for updated drivers, and there are none.

I haven't seen any other discussion regarding this particular model, so I'm at a bit of a loss.  Am I way off-base when I suspect faulty drivers?  Are there any native Linux drivers for this adapter?  Would the WiFi hardware compatibility improvements in Dapper Drake that I've heard about help me at all?  Or, more generally:  Is there anything someone more competent than me (that'd be gosh darn near anybody) can suggest to help me?

---

### Post by frj111 on 2008-04-16
Actually if this device did not work so well under windows XP and Windows Vista 32 I would have abandoned it long ago and moved on.  I am having fits with mywusb54ag under Fedora and Ubuntu as well as Vista64.  I am convinced it&#8217;s a driver issue too.

I am not going to spend a huge amount of time on the Linux solution but will continue to address the Vista64 solution this week.

Like I say it&#8217;s a very neat device with surprising range and convenience that is wonderful.

Rick J

---

