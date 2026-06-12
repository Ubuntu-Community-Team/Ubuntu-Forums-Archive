---
title: "Why is the network at work prejudice against Ubuntu?"
date: 2010-05-19
forum: Networking &amp; Wireless
---

### Post by Roasted on 2010-05-19
I work in IT at a school district. There are 7 schools. Most of them have a wireless network with decent coverage. There's one school in particular that has a wireless system that isn't of the same brand as everybody else. It's a standard controller with all access points wired to it. WPA passphrase to get online configured @ the controller.

I have exactly 100 Dell Latitude E5500 laptops with XP Pro SP3 that all work great for the students. There's no issues with them getting online. My laptop however will connect and then drop the connection several times throughout the next half hour. It's extremely frustrating, to the point where this school I just wire up everywhere I go. But that doesn't make sense to do. It shouldn't be this way. And as of recently, I can't even connect to the wireless here. Each time I do it seems to time out and comes back with the SSID + Password box, as if it's asking me to make sure I put the password in right.

Oh, I forgot to mention. My laptop is ALSO a Dell Latitude E5500. All same hardware. Windows works. Ubuntu doesn't.

I know my laptop itself is good because for the last week I've been taking my laptop home and connecting to my wireless network. Then I'll let it turned on/connected with me as I watch TV or work on the desktop. 

Number of disconnects in the last week? Zero. 
Number of issues connecting in the last week? Zero.
Number of hours tested? ~6 hrs/night * 5-6 nights/week = Enough to make my point.

Went to another school which has just two Netgear access points configured with a basic WPA2 passphrase to give wireless to the office area. Laptop connects perfectly.

So what we're finding is this:

- Hardware wise, my laptop is fine, otherwise it wouldn't work flawlessly in numerous other locations.
- Brand/model wise, my laptop should work, since I have 100 identical laptops here with XP that connect to this network fine.
- Security wise, my laptop shouldn't have an issue, since I can connect to other WPA and WPA2 networks just fine and hold the connection indefinitely. 

This begs the obvious question.

Dubya Tee Eff?

---

### Post by foresthill on 2010-05-19
Are you running 10.4 Lucid? If so, that could be your problem. I think there are still a lot of bugs in this version that (I hope) are being ironed out, especially with regard to network connectivity. Or at least that's been my experience.

9.10 seems a lot more stable to me, so I would probably revert to that if I were you and was running 10.4.

---

### Post by teh_drizzle on 2010-05-19
I've actually experienced something similar on my campus (I'm a student). Every time it happens I open wireshark and tell myself "as soon as it happens again, I'll have it logged!" but it never happens a second time. (I don't use my laptop long, perhaps 20-30mins top.) The school uses WPA2-E with AES (also 802.1x for authentication). This happens to pretty much everyone with Ubuntu, but not nearly as often as you describe (maybe once a week), and the OS reconnects automatically.

The school has wireless intrusion prevention systems which monitor packets-per-second busts. They also utilize load-balancing hand-offs which are controlled by the wireless clients (weird setup), so issues pop up now and again.

I would say try capturing the drop, see (what) who is causing is disassociation. Maybe someone is purposely disassociating your client from the access points in that particular building?

---

### Post by Roasted on 2010-05-19
I don't see how anybody could be disassociating me. I've been in that building when it's empty except me there with the problems persisting.

---

### Post by teh_drizzle on 2010-05-19
See if you can grab a tcpdump/wireshark capture while the connection is interrupted. Then you can take a look and see if there's an application acting up that may cause the access point to drop you. (Whatever it is, you'll have a better idea of what's causing the problem.)

Have you tried installing Ubuntu on any of the other E5500's to see if they are similarly dropped? Maybe the Intel 5100 802.11abgn Linux driver doesn't play well with the particular access point you have in that building?

You said it's a standard controller with access points of a different brand than the rest of the school. What brand is that? Are there any known problems with that brand and Intel drivers? A while back we had problems with the Intel 4965 drivers after installing a new set of Cisco controllers (same APs). This problem affected various Windows operating systems, and the solution was to make sure every client had up-to-date drivers. 

Also depending on the wireless controller software you have, you may be able to pull up diagnostics for your wireless client, or put the controller into a "troubleshoot" mode for that client.

---

### Post by Roasted on 2010-05-19
I have not installed Ubuntu on any other system. Considering my system works fine everywhere except with this ONE network I just had no clue what to blame. 

I'm going to go back over there in a little bit and reboot my laptop and see what happens. If the problem acts up I will install WICD and see what happens from there.

---

### Post by Roasted on 2010-05-19
Okay, I went back to this building. WICD didn't connect either. WICD in fact came back and said I had a bad password. I was like, okay, this is getting very old. So I went and found an identical model XP laptop and deleted the wireless entry all together from our network. I added the network back. Key by key, I typed in what I knew was the password. I did this for the XP laptop and Ubuntu laptop side by side.

XP connected.
Ubuntu did not.

Both WICD and Network Manager at this point have failed me. I have no clue what else I can do. Other networks work... 

What do I do? Reinstall? This is getting old. Very. Fast.

---

### Post by teh_drizzle on 2010-05-20
Depending on how smart the access point/wireless controller is, it may have blocked your MAC (Can you still connect in Windows?). Without packet capture or model names for the hardware/software I'm out of ideas. Sorry man :<

---

### Post by Roasted on 2010-05-20
Can anybody tell me anything about this log?

jason@Ubuntu:~$ tail -F /var/log/syslog
May 19 16:53:12 Ubuntu wpa_supplicant[1091]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
May 19 16:53:12 Ubuntu NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> disconnected
May 19 16:53:12 Ubuntu wpa_supplicant[1091]: Authentication with 00:00:00:00:00:00 timed out.
May 19 16:53:12 Ubuntu NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
May 19 16:53:18 Ubuntu NetworkManager: <info>  eth1: link timed out.
May 19 16:53:53 Ubuntu NetworkManager: <info>  Activation (eth1/wireless): association took too long.
May 19 16:53:53 Ubuntu NetworkManager: <info>  (eth1): device state change: 5 -> 6 (reason 0)
May 19 16:53:53 Ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
May 19 16:53:53 Ubuntu NetworkManager: <info>  Activation (eth1/wireless): asking for new secrets
May 19 16:53:53 Ubuntu NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> disconnected
May 19 16:54:07 Ubuntu NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
May 19 16:54:07 Ubuntu NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
May 19 16:54:07 Ubuntu NetworkManager: <info>  (eth1): device state change: 6 -> 4 (reason 0)
May 19 16:54:07 Ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
May 19 16:54:07 Ubuntu NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
May 19 16:54:07 Ubuntu NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
May 19 16:54:07 Ubuntu NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
May 19 16:54:07 Ubuntu NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
May 19 16:54:07 Ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
May 19 16:54:07 Ubuntu NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto Work-Network' has security, and secrets exist.  No new secrets needed.
May 19 16:54:07 Ubuntu NetworkManager: <info>  Config: added 'ssid' value 'Work-Network'
May 19 16:54:07 Ubuntu NetworkManager: <info>  Config: added 'scan_ssid' value '1'
May 19 16:54:07 Ubuntu NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
May 19 16:54:07 Ubuntu NetworkManager: <info>  Config: added 'psk' value '<omitted>'
May 19 16:54:07 Ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May 19 16:54:07 Ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May 19 16:54:07 Ubuntu NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
May 19 16:54:07 Ubuntu NetworkManager: <info>  Config: set interface ap_scan to 1
May 19 16:54:07 Ubuntu NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
May 19 16:55:08 Ubuntu NetworkManager: <info>  Activation (eth1/wireless): association took too long.
May 19 16:55:08 Ubuntu NetworkManager: <info>  (eth1): device state change: 5 -> 6 (reason 0)
May 19 16:55:08 Ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
May 19 16:55:08 Ubuntu NetworkManager: <info>  Activation (eth1/wireless): asking for new secrets
May 19 16:55:08 Ubuntu NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> disconnected
May 19 16:55:23 Ubuntu NetworkManager: <info>  eth1: link timed out.
May 19 16:55:34 Ubuntu NetworkManager: <info>  (eth1): device state change: 6 -> 9 (reason 7)
May 19 16:55:34 Ubuntu NetworkManager: <info>  Activation (eth1) failed for access point (Work-Network)
May 19 16:55:34 Ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
May 19 16:55:34 Ubuntu NetworkManager: <info>  Marking connection 'Auto Work-Network' invalid.
May 19 16:55:34 Ubuntu NetworkManager: <info>  Activation (eth1) failed.
May 19 16:55:34 Ubuntu NetworkManager: <info>  (eth1): device state change: 9 -> 3 (reason 0)
May 19 16:55:34 Ubuntu NetworkManager: <info>  (eth1): deactivating device (reason: 0).
May 19 16:55:34 Ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))

---

### Post by Roasted on 2010-05-20
Update:

Reinstalled 10.04. Did not get updates. Only got Broadcom driver. Problem continued.

Reinstalled 9.10. Got ALL updates/kernels + Broadcom driver. Worked fine.

Going to make a backup image with Clonezilla of my finished 9.10 install. Then I'm going to install 10.04 again, all updates/kernels/whatever's available and try again. I didn't realize until after I left that I don't recall getting all updates.

---

### Post by Roasted on 2010-05-25
oh hi thar. Anybody else having issues?

---

### Post by Roasted on 2010-06-29
Alright, I've had enough. I decided to look on Google shopping results and pulled up an Amazon.com entry for an Intel Wifi Link 1000 b/g/n card that was a pci express half mini card, just the size I need for my laptop.

I'm hoping that by getting the Broadcom 4322 out of my laptop and putting the Intel in, I get better results. I find it laughable that 9.04 works with my card, 9.10 works but sometimes drops me randomly on any network I'm on (rarely on other networks, but very frequently on this particular network at work) and 10.04 won't connect whatsoever to the one network at work.

Like I said, there's 8 wireless networks at work (1 per building) and only 1 acts up.

Hopefully this Intel will prove to be better than the Broadcom.

---

### Post by NoBugs! on 2010-06-29
Sounds like a broadcom chip problem. They can cause problems, especially with advanced features like WPA and multiple wifi stations. You might try a well supported usb [wifi chip]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") to see if it works.

---

### Post by Roasted on 2010-06-29
> **NoBugs! said:**
> Sounds like a broadcom chip problem. They can cause problems, especially with advanced features like WPA and multiple wifi stations. You might try a well supported usb [wifi chip]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") to see if it works.

That was actually my plan, but once I saw how cheap some internal cards are, I figured I'd take my chances with that. If a new Intel card is the money shot, then it's already internal and I don't have to worry about a USB hanging off the side.

I can't say I'm the biggest fan of Broadcom. This opinion stems from experiences prior to this one as well. I find Intel does a good job. Hell, I even had some issues with an Atheros card. My mother has a laptop with Ubuntu 9.04. Atheros works fine. Doesn't connect to any WPA secured networks in 9.10 or 10.04, even with latest kernels.

Perhaps I should grab an Intel card for her too... :P We'll see how the results of my little test pan out first, though.

---

### Post by CharlesA on 2010-06-29
Best of luck. Having your connection randomly drop gets annoying. :(

---

### Post by Roasted on 2010-06-30
Damn, Amazon. They're such liars. They totally told me I would receive my Intel Wifi Link 1000 BGN pci-express half mini card at earliest July 5th. I totally got it today. Can't complain about a week early I suppose! 

I put it in the laptop and fired it up. Connecting to the wireless network here at home is incredibly quick. It's easily 3-4x faster than connecting with the Broadcom. Now, I didn't have any issues with it here at home, though... so I can't say YES the Intel fixed the issue @ work or not. I'll report back tomorrow when I can get my laptop fired up there to see if it fixed it.

I forgot how easy it was to replace things like this, too. It was simply 1 screw, slide the back off, pop the wireless card out, drop the new one in. Brand new, BGN, only 16 bucks with 3 dollars shipping. Can we say... DAMN! :guitar:

Here's to hoping that it fixes my issues @ work... if so, I'll be a very happy camper...

---

### Post by Roasted on 2010-07-01
Welp, looks like I can connect to that stubborn network @ work with Ubuntu 10.04 using this Intel wireless card. Not only can I connect to this network whereas before with my Broadcom I could not, but it connects much faster too. It only takes about 5 seconds or so after logging in before I'm connected, whereas it took upwards of 20-30 with the Broadcom.

I hate to be sippin the hatorade, but I was never a big fan of Broadcom even when I was in Windows land. I think I'll be avoiding this company in the future. Fortunately even if I do grab a laptop in the future that comes with Broadcom, a few bucks and about 60 seconds of my time can change that. :P

---

### Post by ethoms on 2010-07-03
I'm having some problems with drop-out with my Atheros based USB wireless adapter. Using Kubuntu 10.04. Tried wicd and couldn't connect at all. Only thing that fixes it for me is if I physically uplug and re-plug into USB socket. I have no problems with my laptop wireless on same wireless router. I was thinking it was the USB wifi adapter going into some kind of sleep mode, or some internal stack overflowing on it. Searching for a problem with the model number didn't show any known issues with this adapter. This thread however, is making me wonder if it's an issue with a recent driver for Atheros when using certain wifi encryption algs. I usually set up my router with TKIP/AES, this time i put just AES, so maybe it's WPA2PSK using AES that the adapter driver has issues with. Will report back with findings.

---

### Post by ethoms on 2010-07-03
Having read other threads it seems there is issues with Atheros drivers / modules in more recent kernels. I changed my wifi encryption to Auto (TKIP/AES) and applied the wireless kernel backport (below).

```
sudo apt-get install linux-backports-modules-wireless-lucid-generic

```
After several hours away from my PC I came back to find it saying still "Connected" but it wasn't, adapter had no IP address. However, all I had to do was click on the SSID in KNetworkManager and it re-connected. I didn't have to unplug the adapter from its USB socket. Also, wicd was now able to connect. Well it's a lot better anyway. Maybe I need to reboot after uninstalling wicd for KNetworkManager to behave properly, it should reconnect by itself.

---

