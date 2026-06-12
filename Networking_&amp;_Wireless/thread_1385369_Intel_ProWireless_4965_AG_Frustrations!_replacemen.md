---
title: "Intel Pro/Wireless 4965 AG Frustrations! replacement suggestions please."
date: 2010-01-19
forum: Networking &amp; Wireless
---

### Post by LakeWind on 2010-01-19
After wading through all of the bug reports filed regarding the Intel 4965 AG wireless adapter, trying various suggestions and not finding any solutions to my problem, I've finally decided to scrap the idea of actually being able to get my Toshiba laptop to connect reliably to my wireless network with Ubuntu 9.10. 

This wireless adapter worked absolutely flawlessly with 8.04 Hardy. I took the plunge once again this week and thought I'd try again to get 9.10 working on my laptop but it's a no go with the Intel wireless adapter (same problem with 9.04, it just doesn't work). You would think with newer versions of drivers and kernels that the same hardware that worked in a previous version, would continue working with newer versions.

Anyway, enough of my frustrated ranting... I need to find a replacement wireless adapter for my laptop that WORKS FLAWLESSLY with 9.10. When I say flawlessly, I mean you plug it in, boot up the laptop and it works all the time, every time. No fooling around with drivers etc... Either a PCMCIA or a USB wireless adapter that is currently available for purchase. I've waded through the sticky on the forum about which adapters are supposed to work, but I'm really hoping that someone here is using either a PCMCIA card or USB card and could please point me in the right direction.

It's kind of funny, I purchase my Toshiba laptop because I read reviews here in the forum about how great it worked with Ubuntu 8.04. How all the hardware was recognized and worked out of the box. It did... with 8.04. Everything still works with 9.10 except the wireless. 

Any suggestions for a replacement wireless adapter would be greatly appreciated. But please don't suggest that I stick with 8.04... I need a few of the updated programs in 9.10 that are not available with 8.04. 

Thank you!

---

### Post by chili555 on 2010-01-19
The 4965 is normally very reliable. What does, or doesn't happen correctly? What have you tried so far to fix it? Will you please tell Dr. Chili where it hurts?

---

### Post by LakeWind on 2010-01-20
> **chili555 said:**
> The 4965 is normally very reliable. What does, or doesn't happen correctly? What have you tried so far to fix it? Will you please tell Dr. Chili where it hurts?

Thanks very much for responding. Here's my setup and what is going on:

Ubuntu 9.10 64 bit fresh clean install (not an upgrade).

Wireless network:
Hidden ssid wireless network running wpa2 encryption. Static IP.

Problem: With network manager, intermittent connections to the network. It connects when it wants to and right in the middle of online work, disconnects for no apparent reason. Then it won't re-connect even after a re-boot. One of the many known bugs I've found is listed here (among multiple other places): 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/277634](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/277634)

Trying some of the suggestions listed in the bug report resulted in no change.

I replaced network manager with Wicd (which I was using with 8.04 as well). Unable to connect at all with wicd. Tried various settings etc... Finally copied my previous settings (etc/network/interfaces file and /etc/wicd/wireless-settings.conf file from working 8.04 wicd. Didn't work. Deleted var/lib/wicd/configuration file, rebooted and presto it worked for a while then in the middle of online work, it just disconnected again for no apparent reason. I checked the wicd wireless-settings.conf file and found it had changed itself. Changed it back to original working file (with 8.04), re-booted, and nothing. Checked it again, it was changed. Deleted var/lib/wicd/configuration file and then copied my old wicd wireless-settings.conf file back to the etc/wicd/. re-boot and it worked fine again for a while, then disconnected during internet activity again. Again all files had changed. Tried setting the var/lib/wicd/configuration file and the /etc/wicd/wireless-settings.conf file to read only. They change back to read write all the time and my config files are constantly changed.

Bottom line is this: I can get my wireless working most times at least for a while, if I do the following:

1. Prior to shutting down I must delete the var/lib/wicd/configuration file.

2. Prior to shutting down I must copy my old wireless-settings.conf file back to the etc/wicd/ directory.

Then most times I will be connected immediately upon bootup. Sometimes even with these efforts, it does not work. It's very frustrating but as I said, I do need the upgraded programs that are available with 9.10 so going back to 8.04 is not an option at this point.

I had a similar problem with 9.04 not being able to connect but I also had issues with the intel video. It was just unusable.

Our netbook (asus eeepc) is contently running 9.10 (not the netbook remix) and using network manager even with the hidden ssid and it works consistently, every single time with no loss of connection ever. Fortunately the wireless adapter is an Atheros AR242x. No issues ever with this.

Any help is greatly appreciated. I would much rather get my 4965 wireless working than replace it.

Thanks again.

---

### Post by chili555 on 2010-01-20
Please try this:```
sudo su
echo options iwlagn swcrypto=1 >> /etc/modprobe.d/iwlagn.conf
```Reboot *without* all these steps:> 1. Prior to shutting down I must delete the var/lib/wicd/configuration file.

2. Prior to shutting down I must copy my old wireless-settings.conf file back to the etc/wicd/ directory.Is the behavior improved? If not, please let us see:```
dmesg | grep iwl
```Thanks.

---

### Post by LakeWind on 2010-01-20
Thanks for the reply. I tried the above but it didn't help. Here's the output of dmesg | grep iwl:

[   18.362155] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   18.362159] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   18.379096] iwlagn 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   18.379134] iwlagn 0000:05:00.0: setting latency timer to 64
[   18.379204] iwlagn 0000:05:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   18.436057] iwlagn 0000:05:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   18.436170] iwlagn 0000:05:00.0: irq 32 for MSI/MSI-X
[   18.450677] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   18.521683] iwlagn 0000:05:00.0: firmware: requesting iwlwifi-4965-2.ucode
[   18.598082] iwlagn 0000:05:00.0: loaded firmware version 228.61.2.24
[   18.815889] Registered led device: iwl-phy0::radio
[   18.815914] Registered led device: iwl-phy0::assoc
[   18.815933] Registered led device: iwl-phy0::RX
[   18.815951] Registered led device: iwl-phy0::TX

Thank you again!

---

### Post by chili555 on 2010-01-20
Your dmesg looks entirely normal. That's a good thing, because there are no irregularities to resolve at the driver level. Whew!

Now let's take a look at what happens, or not, when the interface tries to connect. Please let us see:```
dmesg | grep wlan
```Thanks.

---

### Post by LakeWind on 2010-01-21
Here's the output of:

dmesg | grep wlan

while trying to connect (this is without deleting /var/lib/wicd/configuration file & without copying the old /etc/wicd/wireless-settings.conf file).


[   11.789605] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.310270] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   85.764750] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   93.039673] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  133.729564] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  220.919066] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  259.392650] wlan0: deauthenticating by local choice (reason=3)
[  299.427781] ADDRCONF(NETDEV_UP): wlan0: link is not ready


Thanks Doc Chili!!!!

---

### Post by LakeWind on 2010-01-21
Here's the output after it finally connects properly (with my usual intervention, after deletion of /var/lib/wicd/configuration file, copying of old wicd wireless-settings.conf file and re-boot):

[   15.039677] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.767729] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.611132] wlan0: authenticate with AP 00:18:39:fa:0b:47
[   28.611166] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   80.722646] wlan0: deauthenticating by local choice (reason=3)
[   82.480176] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   89.729869] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   91.474191] wlan0: authenticate with AP 00:18:39:fa:0b:47
[   91.476209] wlan0: authenticated
[   91.476217] wlan0: associate with AP 00:18:39:fa:0b:47
[   91.478772] wlan0: RX AssocResp from 00:18:39:fa:0b:47 (capab=0x431 status=0 aid=1)
[   91.478779] wlan0: associated
[   91.498944] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  102.300115] wlan0: no IPv6 routers present


Thanks!

---

### Post by chili555 on 2010-01-21
Very weird! First, I'd like to make sure that Wicd and your old pal Network Manager are not both running, or at least, trying to run. Please open System -> Administration -> Synaptic and search for network. Make certain that Network Manager is removed, along with network-manager-gnome and everything else with network-manager in its name.

Second, let's try another driver parameter:```
sudo su
echo options iwlagn disable_hw_scan=1 > /etc/modprobe.d/iwlagn.conf
```That command will get rid of our older, non-functional parameter and substitute a new one.

Next, please post your wireless-settings.conf. Disguise any identifiable bits.

Last, reboot without any extraordinary steps and let's see if our new changes have had any effect.

---

### Post by LakeWind on 2010-01-21
Chili, thank you for your help!

Before I read your last post I tried uninstalling wicd and re-installing network manager. After about 15 minutes of screwing around with settings in network manager, I was able to connect to my hidden wireless network. So far so good! I think maybe the swcrypto setting may have made a difference for network manager.

At this point I have re-booted my laptop about 10 times and network manager is automatically connecting to my wireless access point without issue. So far, it has not disconnected me either. Time will tell though. I'm going to try these settings for a while and see if my wireless connection is reliable and repeatable. 

The only issue that I have right now with network manager is that I can't seem to connect to my wireless access point after assigning a static IP address. It works fine with dhcp though and for now, that's fine with me.

Thanks again for all your help. You have no idea how much I appreciate it. I will post in this thread in a few days to update my progress either way.

Thank You very much!!!!!!!!!!!!
:D

---

### Post by chili555 on 2010-01-21
> I will post in this thread in a few days to update my progress either way.Please do, so the searchers can learn from our sweat and tears.

I was happy to help; glad it is going well for you!

---

### Post by LakeWind on 2010-01-31
Here's an update. It's been a while now since I re-installed network manager and so far I've had much success with the workaround mentioned in response number 4 of this thread (swcrypto workaround). 

Occasionally network manager will not connect at startup to my wireless network but rebooting and waiting a minute or two after login results in an eventual connection. 

Most of the time network manager connects upon login without issue and stays connected without the bandwidth slow down and without the intermittent disconnects I originally reported (in response 3 above).

I hope the 4965 driver issues are resolved in the near future so the above described workaround will no longer be necessary. You can do further reading about this bug at the following links:

[https://bugzilla.redhat.com/show_bug.cgi?id=519154](https://bugzilla.redhat.com/show_bug.cgi?id=519154)   (shows the swcrypto workaround in post #10)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/277634](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/277634)

[http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1700](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1700)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264104](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264104)

Thanks again for all the help Chili and I hope this post will help others with similar issues.

---

### Post by LakeWind on 2010-02-08
I have a couple of questions regarding the use of the swcrypto=1 config. First what does the swcrypto=1 statement do? Is it turning off the software encryption? If so, is that making my wireless network vulnerable? Could someone in my local area potentially read my encryption key for my wpa2 network?

The reason I ask is that while doing a search for swcrypto=1 I ran across several websites talking about remote exploits and packet injection. Have I made my wireless connection less secure by using this parameter?

---

### Post by chili555 on 2010-02-08
> while doing a search for swcrypto=1 I ran across several websites talking about remote exploits and packet injection. Have I made my wireless connection less secure by using this parameter?The reaon you've read about packet injection, etc. associated with swcrypto=1 is that that parameter is needed in iwlagn chipsets to get packet injection to work. I have not found any reports that it makes your wireless vulnerable. If you have seen some, please share them with us.

Encryption can be done in hardware, that is coded in to the chip itself, or in software, that is, in the operating system. In most cases, including iwlagn, a default is set to use hardware encryption. This is from modinfo iwlagn:> $ modinfo iwlagn
filename:       /lib/modules/2.6.31-19-generic/updates/cw/iwlagn.ko
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2009 Intel Corporation <ilw@linux.intel.com>
version:        1.3.27ks
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
--- snip ---
[COLOR="Blue"]parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)[/COLOR]
As you can see, the default is hardware. We have told the driver that we prefer to use software, that is, wpa_supplicant, conf files, etc.

Of course, we want to use software because hardware doesn't work correctly!

For what it's worth, on one of my laptops, I have a card that uses the ipw2200 driver. It defaults to *software* and requires setting a parameter to get it to use *hardware*!

I feel certain that if we examined various wireless drivers, we'd see both implementations. I think some device drivers  do not allow setting the parameter and if it doesn't work correctly, well that's just tough.

I will continue to goog this. I am confident that you are reasonably safe with WPA2 however it's implemented. The packet injectors and hackers are always active and a determined hacker has a very slight chance of getting into a WPA2 network. However, if he is going to invest the time and trouble to do so, why hack poor old Chili? Why not just go straight to the bank, hack their system and make a huge withdrawal?

---

### Post by LakeWind on 2010-02-08
Thanks for the explanation Chili. The reason I asked is because when I did a google search of swcrypto=1 (to find out basically what it did) I ran across a couple of links; one of them was a website called remote-exploit.org, the other was aircrack-ng. I didn't really understand a lot of what was said on those pages so I figured I would ask here since the website names were alarming to me.

The reasoning behind using the swcrypto parameter now makes sense after your explanation. Thanks again!

---

### Post by CJay554 on 2010-02-16
Hey guys! Thank you for your problem solving thus far! Although it didnt completely work for me.
My typical problem ith wireless: AGN 4965:

At startup wireless can connect to my router with no problem (WPA encryption, i havent tried non-encrypted.

After a few minutes of being connected and using the internet (im guessing the network load) and i get abruptly disconnected. When i try to connect again it doesn't let me.

Next step for me is to rmmod iwlagn and then modprobe iwl4965 to reload the driver. Then i can connect again to my wireless, but a few minutes later it disconnects again.

Also when restarting i get "Mac is in deep sleep" being flooded in terminal mode, sometimes it just hangs on the desktop (but i have a feeling in the tty1 its flooding mac is in deep sleep...)

In either case, that is my problem. I tried the swcrypto with no avail, and the fix suggested in post 9 of this thread. 

Please help? =(
This laptop is a friends and they decided they would like to try out Ubuntu... but i can't get the wireless to cooperate!

Here's my dmesg as soon as it disconnects:

```
[  606.012290] iwlagn 0000:0c:00.0: Error setting new RXON (-28)
[  606.212281] iwlagn 0000:0c:00.0: No space for Tx
[  606.212294] iwlagn 0000:0c:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28

```
(this message repeats countless times)
Also when i try to connect to wireless after disconnect it gives me this same message.



Im using the beforementioned card:

```

                product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection

```

And anything else you may require:

```

mac80211              181236  2 iwlagn,iwlcore
cfg80211               93052  3 iwlagn,iwlcore,mac80211

```

---

### Post by autumnraine on 2010-03-13
Are people still having trouble with this card? I'm considering buying one as a replacement for the s#*t realtek card in my girlfriend's MSI Wind u90.

---

### Post by rykel on 2010-09-26
Hi, I am still UNABLE to connect to any wireless network in Ubuntu Lucid (2.6.32-24-generic-pae kernel) with the Intel PRO/Wireless 4965 AG or AGN [Kedron] adaptor. I am using a Dell XPS M1330.

It can see all the networks but just cannot connect to any of them.

VERY frustrated, because it means Linux is now basically a Brick on my system, and I have to revert it to Windows.

Or is there a solution??

---

### Post by bayvista on 2011-04-02
Not sure if you are still having problems. I am running wifi through this chip into an HP 9520 Pavilion laptop OK using Wicd Network Manager. Main problem was disconnecting after about 10-15 mins. This seems to be solved by rotating the laptop 45 deg. Now it stays connected.

---

### Post by wspc on 2011-04-02
There has to be a bug with Ubuntu.  Have you tried other distros? I found the intel 4965 connected at 130Mbps when I tested Mandriva 2010 and Fedora 14.  Don't know why, but the last three versions of Ubuntu have all failed in this regard, but of course the product is fine in other areas.

---

