---
title: "Realtek 8723 Wireless driver (yet again)"
date: 2012-12-01
forum: Networking &amp; Wireless
---

### Post by Swend on 2012-12-01
I have almost exactly the same problem as the one described, and subsequently solved, in [[COLOR="Blue"]this thread[/COLOR]](http://ubuntuforums.org/showthread.php?t=2017622&highlight=8723).

There is just one problem. I do not have the problem of the space in the folder name, but my make still doesn't work.

```

root@svend-laptop:/home/svend/driver/rtdriver# make
make -C /lib/modules/3.5.0-19-generic/build M=/home/svend/driver/rtdriver modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-19-generic'
  CC [M]  /home/svend/driver/rtdriver/base.o
/home/svend/driver/rtdriver/base.c: In function ‘_rtl_init_mac80211’:
/home/svend/driver/rtdriver/base.c:320:6: error: ‘IEEE80211_HW_BEACON_FILTER’ undeclared (first use in this function)
/home/svend/driver/rtdriver/base.c:320:6: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/home/svend/driver/rtdriver/base.o] Error 1
make[1]: *** [_module_/home/svend/driver/rtdriver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-19-generic'
make: *** [all] Error 2


```

---

### Post by chili555 on 2012-12-01
Perhaps this will help. I might just slightly amend the method to comment out the line; around line 320, I'd do:> 	/* <5> set hw caps */
	hw->flags = IEEE80211_HW_SIGNAL_DBM |
	    IEEE80211_HW_RX_INCLUDES_FCS |
	    [COLOR="Red"]/*[/COLOR] IEEE80211_HW_BEACON_FILTER | [COLOR="Red"]*/[/COLOR]
	    IEEE80211_HW_AMPDU_AGGREGATION |
	    IEEE80211_HW_REPORTS_TX_ACK_STATUS |
	    IEEE80211_HW_CONNECTION_MONITOR |
	    /* IEEE80211_HW_SUPPORTS_CQM_RSSI | */
	    IEEE80211_HW_MFP_CAPABLE | 0;

	/* swlps or hwlps has been set in diff chip in init_sw_vars */Save and close your text editor and try again:```
sudo su
make clean
make
make install
exit
```This is all experimental; we have no idea if it helps, hurts, etc. You will be our test pilot. Congratulations! Fly safe!

[http://forums.gentoo.org/viewtopic-t-935872-start-0.html](http://forums.gentoo.org/viewtopic-t-935872-start-0.html)

---

### Post by Swend on 2012-12-01
First off, I am very honored to be chosen as your test pilot.

Secondly, IT WORKED! :D

I commented out that line (not exactly line 320, but I found it), and the make and make install worked as they should.

I restarted, and now the wireless is working! Or that is, I wish it were as well. But now I have another, probably unrelated problem. I doesn't detect any wireless networks (and I'm sitting next to the router with another laptop that finds it just fine).

But at least the driver was installed successfully, and thats a victory of some sort.

---

### Post by chili555 on 2012-12-01
Let's have a peek at:```
nm-tool
rfkill list all
```Your flying days are just starting! Commenting out a possibly crucial parameter may or may not work. We shall see.

---

### Post by Swend on 2012-12-01
Ok, flying is going well, but I'm seeing some strange stuff here. I haven't done what you told me last post because this happened:

I restarted the computer again, and then the options for wireless were mysteriously gone. I enter this ```
sudo modprobe rtl8723e
``` into the terminal and voila, it's working. But here's the twist: Now it detects networks :O
And then I remember that last time the wireless only started working after I used modprobe.

So I guess it's working now. I think. Just gotta find a way around that 'has to use modprobe to start wireless' thing. I guess.

This post is posted from a wireless connection.

---

### Post by chili555 on 2012-12-01
> voila, it's working. Awesome! A safe landing is a good landing!> Just gotta find a way around that 'has to use modprobe to start wireless' thing.It's easy:```
sudo su
echo rtl8723e >> /etc/modules
exit
```Reboot and see if it's fixed. If so, please reach up to thread tools and mark Solved so the searchers will learn from your experience.

Have fun!

---

### Post by Swend on 2012-12-01
This problem is officially giving me a headache.

I restarted again, and this time the wireless driver was on from the start, as it should. But this time with no detected networks...

So I'm back on my wired connection.

I'll try restarting again as a control.

---

### Post by chili555 on 2012-12-01
> **Swend said:**
> I'll try restarting again as a control.With the ethernet *DE*tached, please.

---

### Post by Swend on 2012-12-01
> **chili555 said:**
> With the ethernet *DE*tached, please.
You were right to say that.

I restart twice. With the ethernet attached, the wireless detected all wireless networks nearby, including the one I want. With ethernet detached it doesn't find anything.

---

### Post by chili555 on 2012-12-01
> **Swend said:**
> You were right to say that.

I restart twice. With the ethernet attached, the wireless detected all wireless networks nearby, including the one I want. With ethernet detached it doesn't find anything.That's actually the way Network Manager is designed to operate. If the faster, more secure ethernet is available, don't activate the wireless.

So...solved?

---

### Post by Swend on 2012-12-01
It's the wrong way round. When there is *no* ethernet it doesn't detect wireless networks :/

---

### Post by chili555 on 2012-12-01
> **Swend said:**
> It's the wrong way round. When there is *no* ethernet it doesn't detect wireless networks :/Wha..??

Did you do the /etc/modules step? Is the module loaded on boot now?```
lsmod | grep rt8
dmesg | grep rtl
```With the ethernet detached, reboot and please provide the information previously requested:```
nm-tool
rfkill list all
```

---

### Post by Swend on 2012-12-01
Ok, I've rebooted this thing at least a thousand times now (I swear) and I've come to what looks like a conclusion.

It's not whether the ethernet is attached or not, its whether *restart* or *shutdown, then start*. The former doesn't work, the latter does. I don't know how I got those mixed up in the first round of testing, but I'm pretty sure about this.

This is the output of mentioned commands as it is now:
```
svend@svend-laptop:~$ lsmod | grep rt8
svend@svend-laptop:~$ dmesg | grep rtl
[   19.579094] firemare: rtl8723fw_B.bin
[   19.796940] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   19.797243] rtlwifi: wireless switch is on
svend@svend-laptop:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        4C:72:B9:91:AB:53

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [TELIA-8F7F7A 1] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723e
  State:             connected
  Default:           yes
  HW Address:        24:EC:99:96:D7:D7

  Capabilities:
    Speed:           18 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Tilgin-qF6cQ4CTctbF: Infra, 00:02:61:79:8B:C8, Freq 2412 MHz, Rate 54 Mb/s, Strength 87 WPA
    TDC-2A8C:        Infra, 00:19:70:35:45:38, Freq 2427 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    Weiskvist:       Infra, C0:3F:0E:A6:7C:F8, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA
    TDC-05CC:        Infra, 00:19:70:23:3B:DE, Freq 2422 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    linksys9CE6:     Infra, 00:23:69:7B:9C:E6, Freq 2472 MHz, Rate 54 Mb/s, Strength 27 WPA
    japan20snart31motiv: Infra, 80:C6:AB:08:C8:71, Freq 2442 MHz, Rate 54 Mb/s, Strength 50 WEP
    *TELIA-8F7F7A:   Infra, 00:24:17:D0:ED:78, Freq 2462 MHz, Rate 54 Mb/s, Strength 88 WPA

  IPv4 Settings:
    Address:         192.168.1.159
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


svend@svend-laptop:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
svend@svend-laptop:~$ ^C
svend@svend-laptop:~$ 

```

---

### Post by Swend on 2012-12-01
And here are the same commands after a restart:

```
svend@svend-laptop:~$ lsmod | grep rt8
svend@svend-laptop:~$ dmesg | grep rtl
[   20.271368] firemare: rtl8723fw_B.bin
[   20.841108] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   20.841429] rtlwifi: wireless switch is on
svend@svend-laptop:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723e
  State:             disconnected
  Default:           no
  HW Address:        24:EC:99:96:D7:D7

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        4C:72:B9:91:AB:53

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.158
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


svend@svend-laptop:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
svend@svend-laptop:~$ 

```

---

### Post by chili555 on 2012-12-01
Which version did you build? rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.*0514.2012* perhaps? May I see:```
modinfo rtl8723e
```Thanks.

---

### Post by tsviatko on 2012-12-23
I have the very same problem.

It's worth mentioning that shutdown has some weird glitch on my laptop. It will tun the laptop off but in a couple of seconds the laptop will turn itself on again all by itself.

Here's the modinfo output:

filename:       /lib/modules/3.5.0-21-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723e/rtl8723e.ko
firmware:       rtlwifi/rtl8723efw.bin
description:    Realtek 8723E 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     C495D10C50D3C85AE360841
alias:          pci:v000010ECd00008723sv*sd*bc*sc*i*
depends:        rtlwifi,mac80211
vermagic:       3.5.0-21-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)

---

### Post by chili555 on 2012-12-24
> It's worth mentioning that shutdown has some weird glitch on my laptop. It will tun the laptop off but in a couple of seconds the laptop will turn itself on again all by itself.I think the failure to shutdown or restart properly is a different and probably not related to wireless problem. I think I'd try to solve it first. There are a number of posts about this: [https://www.google.com/search?source=ig&rlz=&q=ubuntu+won%27t+restart&oq=ubuntu+won%27t+restart&gs_l=igoogle.3..0j0i8j0i8i30j0i8i10i30j0i8i30l3j0i8i10i33i30l2.275468.282872.0.283640.20.14.0.6.6.0.346.2108.0j12j1j1.14.0...0.0...1ac.1.BPkTEO_0nf4#q=site:ubuntuforums.org+ubuntu+won%27t+restart&hl=en&safe=off&tbo=d&source=lnt&tbs=qdr:y&sa=X&ei=fYDYUJ--OceC0QHUs4HoDA&ved=0CB0QpwUoBQ&bav=on.2,or.r_gc.r_pw.r_qf.&bvm=bv.1355534169,d.dmQ&fp=48d58183a0780002&bpcl=40096503&biw=1067&bih=503](https://www.google.com/search?source=ig&rlz=&q=ubuntu+won%27t+restart&oq=ubuntu+won%27t+restart&gs_l=igoogle.3..0j0i8j0i8i30j0i8i10i30j0i8i30l3j0i8i10i33i30l2.275468.282872.0.283640.20.14.0.6.6.0.346.2108.0j12j1j1.14.0...0.0...1ac.1.BPkTEO_0nf4#q=site:ubuntuforums.org+ubuntu+won%27t+restart&hl=en&safe=off&tbo=d&source=lnt&tbs=qdr:y&sa=X&ei=fYDYUJ--OceC0QHUs4HoDA&ved=0CB0QpwUoBQ&bav=on.2,or.r_gc.r_pw.r_qf.&bvm=bv.1355534169,d.dmQ&fp=48d58183a0780002&bpcl=40096503&biw=1067&bih=503)

I had the problem myself and it went away as mysteriously as it arrived! My wireless worked perfectly the whole time.

---

### Post by tsviatko on 2012-12-24
Yeah, I'm trying to solve that problem too, still hoping it might affect the wireless issue.

Can you think of any reason why the wireless would behave like that though?

---

### Post by chili555 on 2012-12-24
> **tsviatko said:**
> Can you think of any reason why the wireless would behave like that though?No, but as I said, I'd try to fix the shutdown/reboot first. I seldom have good luck trying to fix several problems simultaneously; except, of course, when I kicked out my ex-girlfriend.

---

