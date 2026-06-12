---
title: "netbook crash connecting wifi"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by Tijssiej on 2011-04-28
Hello,

Just installed ubuntu 11.04 and it all works fine. :) However, I got a big problem. When I unplug my ethernet cable and turn on my wifi my pc freezes?

All updates are done and there are no drivers. I'm using die eeepc 1001px.

Someone who can help me with this? A netbook isn't usefull without a wifi connection :(

~Tijs

p.s. sorry for bad english. :|

---

### Post by abelmaio on 2011-04-28
This happens to me too.

But only if I try to connect to an hidden network.

I have an Asus EEEpc 1001P. Is this problem related to Atheros Wireless Network Adpater? It seems that the most people that have this problem are trying to install Ubuntu on Netbooks with that Wireless card.

On Ubuntu 10.04 that was not suported. They fixed that on 10.10. Now on 11.04 the computer crash and sometimes appear a lot of lines (I think is a Kernel Panic).

If I access a WPA/WPA2 network that's ok. But if I access my wireless network (Hidden Network, WPA2 Personal) it freezes. In my faculty, when I try to connect to the Network (Hiden, WPA2 Enterprise) it freezes to, and sometimes the Kernel Panic.


Can someone help? I really want to install 11.04 on my netbook. :(

---

### Post by abelmaio on 2011-04-28
Just a little more information about the problem.

I also installed the same ISO of Ubuntu 11.04 on my Toshiba Notebook. I tried to connect to the same hidden network that crashed my netbook and it connected fine.

I'm, at the moment, sending this message by the Wireless that I cannot connect on my Netbook, so the problem is not of my router.



Thank you for any help.

--
AM

---

### Post by cityhuntr on 2011-04-28
I also have major problems regarding wireless connections on my **eeepc 1001P netbook**.

The problem has manifested in three different ways. When using 11.04 in the live cd environment on a usb stick, attempts to connect to my network result in a kernel panic right away.

When 11.04 is installed and updated, attempts to connect to the network result in CPU usage shooting up to 100%, and the system hangs about a second later. The only way to get out of this is to force the netbook off by holding down the power button.

Randomly upon boot up, the networking panel applet doesn't appear, and there is terrible system-wide performance. Even the mouse movement is lagged. This leads to an eventual system hang, which again requires a forced shutdown with the power button.

Thankfully, the wired connection works without issue, so there is hope to get updates and internet connectivity that way. However, there's no doubt that there must be something terribly wrong with the atheros driver or something else related to networking. Wifi worked flawlessly out of the box in 10.10.

---

### Post by abelmaio on 2011-04-28
More information.

I tried to install the drivers with ndiswrapper. Now every time I tried to connect a Kernel Panic appears.

Also I tried the Kubuntu 11.04 and the same thing happens there. When I try to connect it freezes. 

So the problem is again with the Atheros. Why Ubuntu don't like this little Atheros? :(


---
AM

---

### Post by cityhuntr on 2011-04-29
Here's some info I could get from kern.log.

This is what happens when I toggle the wireless switch (function+f2) which enables wireless and makes it automatically connect to my access point:

```

[   42.031913] wlan0: authenticate with 00:18:f8:b1:e0:1e (try 1)
[   42.034761] wlan0: authenticated
[   42.052993] wlan0: associate with 00:18:f8:b1:e0:1e (try 1)
[   42.055860] wlan0: RX AssocResp from 00:18:f8:b1:e0:1e (capab=0x401 status=0 aid=1)
[   42.055871] wlan0: associated
[   42.056999] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   42.064111] BUG: unable to handle kernel NULL pointer dereference at   (null)
[   42.064316] IP: [<f8453f2d>] ath_tx_start_dma+0xdd/0x130 [ath9k]
[   42.064484] *pde = 33bc9067 *pte = 00000000 
[   42.064609] Oops: 0000 [#1] SMP 
[   42.064704] last sysfs file: /sys/devices/system/cpu/cpu1/cache/index2/shared_cpu_map
[   42.064880] Modules linked in: parport_pc ppdev snd_hda_codec_realtek arc4 snd_hda_intel snd_hda_codec snd_hwdep snd_pcm ath9k i915 snd_seq_midi snd_rawmidi binfmt_misc snd_seq_midi_event eeepc_wmi joydev snd_seq sparse_keymap mac80211 snd_timer drm_kms_helper snd_seq_device uvcvideo ath9k_common ath9k_hw snd ath drm videodev cfg80211 psmouse serio_raw soundcore snd_page_alloc i2c_algo_bit video lp parport ahci libahci atl1c
[   42.066153] 
[   42.066202] Pid: 1237, comm: compiz Not tainted 2.6.38-8-generic #42-Ubuntu ASUSTeK Computer INC. 1001P/1005P
[   42.066482] EIP: 0060:[<f8453f2d>] EFLAGS: 00010246 CPU: 1
[   42.066629] EIP is at ath_tx_start_dma+0xdd/0x130 [ath9k]
[   42.066763] EAX: 00000000 EBX: f54cdc04 ECX: ee6ca250 EDX: ef4f9c94
[   42.066916] ESI: ef520750 EDI: ec264c00 EBP: f54cdbc4 ESP: f54cdb9c
[   42.067069]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[   42.067206] Process compiz (pid: 1237, ti=f54cc000 task=f4f09940 task.ti=ec050000)
[   42.067391] Stack:
[   42.067448]  00000002 00000000 ee6cb82c ef4f9234 ee6ca254 ef4fc000 ef510e10 ef4f9ca4
[   42.067713]  ef520750 00000002 f54cdbf0 f8455117 00000072 00000002 ef4f9c94 ef4f9234
[   42.067975]  00000072 f54cdc04 ef4f82c0 ef4f9234 ec264c00 f54cdc24 f844dd4f 0000006b

```

What follows is an enormous list of call traces, which I believe loops until the computer is forced off. Here are a few selections of lines involving ath9k:

```

[   42.068015]  [<f8455117>] ath_tx_start+0x137/0x180 [ath9k]
[   42.068015]  [<f844dd4f>] ath9k_tx+0x8f/0x150 [ath9k]
[   42.069173]  [<f8248a39>] ? ath_hw_cycle_counters_update+0xc9/0x120 [ath]
[   42.069173] EIP: [<f8453f2d>] ath_tx_start_dma+0xdd/0x130 [ath9k] SS:ESP 0068:f54cdb9c
[   42.066482] EIP: 0060:[<f8453f2d>] EFLAGS: 00010246 CPU: 1
[   42.066629] EIP is at ath_tx_start_dma+0xdd/0x130 [ath9k]

```

I'll be happy to supply more, though I'm not sure what exactly is relevant.

---

### Post by acuk on 2011-04-29
I can confirm this. Connecting to a wifi network on 1001PX produces a kernel panic. Not good for such a popular machine.

> **Tijssiej said:**
> Hello,

Just installed ubuntu 11.04 and it all works fine. :) However, I got a big problem. When I unplug my ethernet cable and turn on my wifi my pc freezes?

All updates are done and there are no drivers. I'm using die eeepc 1001px.

Someone who can help me with this? A netbook isn't usefull without a wifi connection :(

~Tijs

p.s. sorry for bad english. :|

---

### Post by giampierosalvi on 2011-04-30
Confirming this on Asus Eee PC 1001PX, AR2427 network adapter. Hope this bug gets a very high priority...

> **acuk said:**
> I can confirm this. Connecting to a wifi network on 1001PX produces a kernel panic. Not good for such a popular machine.

---

### Post by keredson on 2011-04-30
this is also happening to me w/ my broadcom based acer ao-522.  (amd fusion c-30)

---

### Post by macrophenomenal on 2011-04-30
hi this is also happening to me.
I am using a HP2133 with Broadcom STA wireless driver BCM 4312 (Rev 1.0)

I upgraded to 11.04 and my system hangs if I connect to a wireless network.
LAN appears to work fine though.

---

### Post by iswan on 2011-04-30
I have similar problem. Has anyone tried this? [http://bit.ly/jKPouB](http://bit.ly/jKPouB) It is said there that this issue had been resolved by the new kernel but apparently the kernel didn't make it for natty so we need to upgrade it manually.

---

### Post by abelmaio on 2011-04-30
I will try this shortly. 

I'm making an USB Stick with persistent memory so I can update and try it from the USB without the need of reformat the Netbook again. 

Now I'm with Linux Mint 10 on my netbook and works fine. So I don't want to reformat again to install Natty that may still not work.

I'll give news shortly.


---
AM

---

### Post by cityhuntr on 2011-04-30
I just applied the new kernel as instructed in [http://bit.ly/jKPouB](http://bit.ly/jKPouB) and the problem appears to have been resolved for my 1001p netbook. Maybe it needs further testing to be sure, but this is a good sign.

---

### Post by abelmaio on 2011-04-30
I installed Ubuntu Natty on my USB Drive with persistence.

Then boot it, connected the Ethernet cable, open terminal and enter:

```


sudo apt-add-repository ppa:kernel-ppa/pre-proposed

sudo apt-get update


```

Then, open the Update Manager and updated the system. Reboot.

Now I can connect to the network without any freezes.

So I think this solves the problem.

---

### Post by medoix on 2011-04-30
This also fixed all the issues i was having with the Atheros WiFi on my 1000HE EEEPC.

I was also having issues with it booting into the Unity desktop and after upgrading the Kernal in Safe mode, that is now also solved.

Thanks.

---

### Post by drever on 2011-05-01
Abelmaois solution worked fine for me. Thanks!

---

### Post by juancaman80 on 2011-05-01
Hello all,

Just to mention, I tried the steps above, and unfortunately, I still have the same issue.
It works beautifully otherwise though, as long as either the WiFi card is disabled, or the computer is plugged in to the ethernet. What a bummer. Sad thing is, it worked beautifully on WiFi for the first 48 hours. It stopped from one moment to the other without anything new installed.

Any ideas on what else could be tried?

(I should mention, I'm running an Acer Aspire One 522, only modifications done are 2GB RAM and 320GB HD, WiFi works ok under Windows 7...but I'd much rather use a crippled Ubuntu than Windows 7!)

---

### Post by macrophenomenal on 2011-05-01
Hi,

Unfortunately this solution did not work for me either.

As I mentioned above I am using a HP2133 with Broadcom STA wireless driver BCM 4312 (Rev 1.0)
I upgraded to 11.04 and my system hangs if I connect to a wireless network.
LAN appears to work fine though.

I did find another solution: I reinstalled Ubuntu 10.04, then upgraded to 10.10
And wireless works without crashing or freezing the computer now.

---

### Post by Muzzab on 2011-05-03
This solution hasn't worked for me because the kernel-ppa can't be found during the update process. Now what?

---

### Post by adampatch on 2011-05-04
This fixed it for me on my 1001PX. Thanks

---

### Post by kjeLL// on 2011-05-11
> **abelmaio said:**
> I installed Ubuntu Natty on my USB Drive with persistence.

Then boot it, connected the Ethernet cable, open terminal and enter:

```


sudo apt-add-repository ppa:kernel-ppa/pre-proposed

sudo apt-get update


```

Then, open the Update Manager and updated the system. Reboot.

Now I can connect to the network without any freezes.

So I think this solves the problem.

did not work for me. asus 1001px. (installed new kernel headers)
computer crashes completely after 10-30 sec after connecting to my own network. activating the card will not crash the computer.

edit:
after some enabling in update manager i installed the 2.6.38-9 kernel, and wlan is working fine. but in the update i also selected some smb updates, and somehow screwed up ubuntu one badly.

---

### Post by ubusg on 2011-05-11
> **kjeLL// said:**
> did not work for me. asus 1001px. (installed new kernel headers)
computer crashes completely after 10-30 sec after connecting to my own network. activating the card will not crash the computer.
Same here, asus eee pc 1005p. Activating the card without connecting to a network really doesn't lead to crash (disable card at boot and uncheck auto connect at any saved wlan network).

Just to notice: I was able to manually establish a wlan connection to my samsung galaxy, whereas my private connection crashed the system in an instant.

---

### Post by Electric_Bubble on 2011-05-16
Confirming problem for the eee pc 1005, but only upon connection to a protected network. No problems connecting to unprotected networks, maybe thats why you can establish a connection whit your phone.

I will try your solution tomorrow and report back... Hope the bug gets some priority!

---

### Post by Jacobonbuntu on 2011-05-17
to add some information: the problem not only occurs with Ubuntu 11.04, but also with Xubuntu and Lubuntu 11.04... (1001px).
I have been busy installing the past few days :popcorn:...

---

### Post by bambii7 on 2011-05-19
Same here getting 404 errors on  [http://ppa.launchpad.net/kernel-ppa/pre-proposed/ubuntu](http://ppa.launchpad.net/kernel-ppa/pre-proposed/ubuntu)
Not sure what to do from here. Had the same issue yesterday

> **Muzzab said:**
> This solution hasn't worked for me because the kernel-ppa can't be found during the update process. Now what?

---

### Post by bambii7 on 2011-05-19
Looks likes its been included in the most recent updates, just updated and wireless is working fine.

---

### Post by linux_one on 2011-05-19
the problem is with the kernel in 11.04, seems to include all newer asus eeepc's and is solved in latest kernel.
to solve that you can download the latest kernel and install it very easily;
 go to 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)
and download the files; 

linux-headers-2.6.39-999_2.6.39-999.201105191210_all.deb
linux-headers-2.6.39-999-generic_2.6.39-999.201105191210_i386.deb
linux-image-2.6.39-999-generic_2.6.39-999.201105191210_i386.deb

(or different versions depending on time) then install them in exactly same order by the command;

sudo dpkg -i filename

one after the other, then restart the netbook. it worked perfectly for me.

---

### Post by Jacobonbuntu on 2011-05-20
great, great, I did the upgrade, was still waiting for the screen to freeze.... 
didn't happen!
problem solved.

---

### Post by beke on 2011-05-25
Thanks @linux_one -- the 2.6.39-999-kernel helped (although I would have preferred a 666 kernel ;) ).

In case somebody else searches for hours like I did, let me add some more information (because it's weird that this bug was only triggered yesterday on my HP TM2).

I think it was due to my bluetooth dongle -- I usually just pull it off when I don't need it, but yesterday I went to the blueetooth-manager and deactivated the service before unplugging the dongle. At the next boot after that the system froze so badly that the BIOS had to force a shutdown due to dangerous temperature levels... holy bug hell...

So thank you again!!!

---

### Post by quatoria on 2011-07-05
Hi,

Tried the updates, even went through the very long and arduous process of installing the links (download in Xp, cross over to ubuntu via flash pen as xp isn't very good and versions 11.04 doesn't have working samba). All it did was kill my repositories and leave me a red angry looking warning sign that tells me there are unsupported packages and that I should run a partial update, which urges me to uninstall them.

Still have no working wireless, it connects on boot up and then five minutes later after a very very slow time it drops and won't go back up. 

Dual boot laptop and my win xp works fine on same hardware (using it to type this message.) So it has to be natty.

Asus eee 1000 (the one with the 40gb ssd) and until I stuck on the god awful natty 11.04 which ruined the definition of user interface being easy and fast. I was very happy with ubuntu networking with my home network and the internet. 

Anyone any other idea how I can fix what has been broken with the upgrade to 11.04? I don't want to wait till october, or spend three months downloading and installing something that shouldn't have broken between versions.

---

### Post by HughR on 2011-07-16
> **juancaman80 said:**
> 
Just to mention, I tried the steps above, and unfortunately, I still have the same issue.

(I should mention, I'm running an Acer Aspire One 522)

(See also keredson's message 9 in this thread.)

The OP's problem report is for an Atheros AR2427 WiFi chipset.
The ao522 has a Broadcom BCM4313 WiFi chipset.
So the ao522 problem needs another fix.

I too have this problem.  I've added to [bug 785569]("https://bugs.launchpad.net/ubuntu/+source/broadcom-sta/+bug/785569")

---

