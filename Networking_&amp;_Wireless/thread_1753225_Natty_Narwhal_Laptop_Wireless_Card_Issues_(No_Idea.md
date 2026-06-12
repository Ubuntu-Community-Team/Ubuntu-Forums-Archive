---
title: "Natty Narwhal Laptop Wireless Card Issues (No Idea what the Problem is)"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by Mr kmil on 2011-05-08
Hello all,

I'm using Natty Narwhal (11.04) on a Compaq N410c Laptop, and a SMC Wireless Cardbus Card. I know, using narwhal on such an old laptop is like teaching an old dog a new trick, but I did it on recommendation from a friend because the new kernal is faster.

Anyway, onto my issue. I can't seem to get Ubuntu to recognize the wireless card, and I have no idea why. It seems to defy me at every turn. I've searched for days, and tried almost every solution I could find. I've even tried installing two separate versions of Madwifi, but everything I've done has failed, either due to a missing directory, or a failed package retrieval. If anyone would like to help me diagnose my issue, you're very welcome and thanked to do so. I'll include links to my items as well.

Thank you very much for any help you can give me!

SMC Card: [http://www.smc.com/index.cfm?event=viewLargeImage&localeCode=EN_USA&cid=5&scid=31&pid=1445](http://www.smc.com/index.cfm?event=viewLargeImage&localeCode=EN_USA&cid=5&scid=31&pid=1445)

Laptop: [http://h18000.www1.hp.com/products/quickspecs/11375_div/11375_div.html](http://h18000.www1.hp.com/products/quickspecs/11375_div/11375_div.html)

---

### Post by josephmills on 2011-05-08
> **Mr kmil said:**
> Hello all,

I'm using Natty Narwhal (11.4) on a Compaq N410c Laptop, and a SMC Wireless Cardbus Card. I know, using narwhal on such an old laptop is like teaching an old dog a new trick, but I did it on recommendation from a friend because the new kernal is faster.

Anyway, onto my issue. I can't seem to get Ubuntu to recognize the wireless card, and I have no idea why. It seems to defy me at every turn. I've searched for days, and tried almost every solution I could find. I've even tried installing two separate versions of Madwifi, but everything I've done has failed, either due to a missing directory, or a failed package retrieval. If anyone would like to help me diagnose my issue, you're very welcome and thanked to do so. I'll include links to my items as well.

Thank you very much for any help you can give me!

SMC Card: [http://www.smc.com/index.cfm?event=viewLargeImage&localeCode=EN_USA&cid=5&scid=31&pid=1445](http://www.smc.com/index.cfm?event=viewLargeImage&localeCode=EN_USA&cid=5&scid=31&pid=1445)

Laptop: [http://h18000.www1.hp.com/products/quickspecs/11375_div/11375_div.html](http://h18000.www1.hp.com/products/quickspecs/11375_div/11375_div.html)
hi there could we please see a ```
lspci -nn
``` and a ```
rfkill list all 
``` thanks

---

### Post by Mr kmil on 2011-05-08
Hello Joseph!

As per request, here is my terminal responce:

(lspci -nn):
00:00.0 Host bridge [0600]: Intel Corporation 82830 830 Chipset Host Bridge [8086:3575] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82830 830 Chipset AGP Bridge [8086:3576] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 Controller [8086:248a] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M6 LY [1002:4c59]
02:02.0 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 41)
02:02.1 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 41)
02:02.2 USB Controller [0c03]: NEC Corporation USB 2.0 [1033:00e0] (rev 02)
02:03.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 02)
02:04.0 Ethernet controller [0200]: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 [8086:1229] (rev 09)
02:04.1 Serial controller [0700]: Agere Systems LT WinModem [11c1:045c]
03:00.0 Network controller [0280]: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] [1260:3890] (rev 01)

With the rfkill list all, I got nothing. It just acted like I typed nothing and hit enter. Just got another command line.

---

### Post by josephmills on 2011-05-08
how about a ```
lsmod
```

---

### Post by chili555 on 2011-05-08
Mr. Mills undoubtedly stepped away to brew the tea; next he wants to see:```
dmesg | grep p54
```If firmware is missing, he wants you to install *linux-firmware-nonfree* and reboot.

Am I trying to up my post count? Yes, just a bit. OK, back to sleep now...

Great, he's back.

---

### Post by Mr kmil on 2011-05-08
> **josephmills said:**
> how about a ```
lsmod
```

Joseph, here you go.

(lsmod):
```
Module                  Size  Used by
p54pci                 17054  0 
p54common              32371  1 p54pci
radeon                896428  2 
mac80211              257001  2 p54pci,p54common
snd_intel8x0           33213  2 
binfmt_misc            13213  1 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
ttm                    65184  1 radeon
cfg80211              156212  2 p54common,mac80211
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
drm_kms_helper         40745  1 radeon
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
joydev                 17322  0 
snd_timer              28659  2 snd_pcm,snd_seq
ppdev                  12849  0 
pcmcia                 39671  0 
drm                   180037  4 radeon,ttm,drm_kms_helper
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27230  0 
irda                  185091  0 
psmouse                73312  0 
pcmcia_rsrc            18292  1 yenta_socket
parport_pc             32111  1 
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_algo_bit           13184  1 radeon
crc_ccitt              12595  2 p54common,irda
shpchp                 32345  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
e100                   40108  0 
floppy                 60032  0 

```

---

### Post by Mr kmil on 2011-05-08
Chili, your code output:
```
[   27.135676] p54pci 0000:03:00.0: enabling device (0000 -> 0002)
[   27.135702] p54pci 0000:03:00.0: PCI INT A -> Link[C0C1] -> GSI 11 (level, low) -> IRQ 11
[   27.135722] p54pci 0000:03:00.0: setting latency timer to 64
[   27.152172] p54pci 0000:03:00.0: Cannot find firmware (isl3886pci)
[   27.171599] p54pci 0000:03:00.0: PCI INT A disabled
[   27.171625] p54pci: probe of 0000:03:00.0 failed with error -2
[  303.408713] p54pci 0000:03:00.0: enabling device (0000 -> 0002)
[  303.408736] p54pci 0000:03:00.0: PCI INT A -> Link[C0C1] -> GSI 11 (level, low) -> IRQ 11
[  303.408758] p54pci 0000:03:00.0: setting latency timer to 64
[  303.418919] p54pci 0000:03:00.0: Cannot find firmware (isl3886pci)
[  303.437409] p54pci 0000:03:00.0: PCI INT A disabled
[  303.437434] p54pci: probe of 0000:03:00.0 failed with error -2

```

---

### Post by josephmills on 2011-05-08
looks like chili555 is right again ):P):P

---

### Post by joshgordonclan on 2011-05-08
> **chili555 said:**
> If firmware is missing, he wants you to install *linux-firmware-nonfree* and reboot.


Looks like Firmware is missing, so I would give it a shot. Should be as simple as ```
sudo apt-get linux-firmware-nonfree 
``` and typing your password.

---

### Post by chili555 on 2011-05-08
> **joshgordonclan said:**
> Looks like Firmware is missing, so I would give it a shot. Should be as simple as ```
sudo apt-get linux-firmware-nonfree 
``` and typing your password.Oops! It's actually:```
sudo apt-get [COLOR="Red"]install[/COLOR] linux-firmware-nonfree 
```

---

### Post by joshgordonclan on 2011-05-08
Duh! I forget that time to time and have to go back and fix it.

---

### Post by Mr kmil on 2011-05-08
Alright, I've installed my firmware and rebooted. What's next?

---

### Post by josephmills on 2011-05-08
```
iwlist scan 
``` thanks

---

### Post by Mr kmil on 2011-05-08
> **josephmills said:**
> ```
iwlist scan 
``` thanks

```

lo      Interface doesn't support scanning.

eth0    Interface doesn't support scanning.

wlan0   No search results

```

---

### Post by joshgordonclan on 2011-05-08
Now it looks like it's seeing your card. Can you see any networks in the networking menu?

---

### Post by Mr kmil on 2011-05-08
> **joshgordonclan said:**
> Now it looks like it's seeing your card. Can you see any networks in the networking menu?

Yes! It's showing up! Thank you guys so much! This has been quite a pain in my backside for about a week now, and now its resolved with a simple firmware upgrade!Man, I feel like such a newbie!

---

### Post by josephmills on 2011-05-08
```
sudo /etc/init.d/networking restart
```anything ?

---

### Post by Mr kmil on 2011-05-08
> **josephmills said:**
> ```
sudo /etc/init.d/networking restart
```anything ?

I got this back:
```

sudo: /ect/init.d/networking: command not found

```

Also I'm still having trouble connecting to the network. I typed in our password, and it seems to be stuck connecting.

---

### Post by joshgordonclan on 2011-05-08
I wouldn't worry about restarting the networking service -- when you try to do it, it says it's depreciated. 

As far as connecting to the network -- do you know how your network is encrypted? I think the specs on the card said it doesn't support WPA2.

---

### Post by Mr kmil on 2011-05-08
> **joshgordonclan said:**
> I wouldn't worry about restarting the networking service -- when you try to do it, it says it's depreciated. 

As far as connecting to the network -- do you know how your network is encrypted? I think the specs on the card said it doesn't support WPA2.

We use a WEP Key that we got on our Verizon router. I've had to read it off to guests before, so I know that's the one we use.

---

### Post by joshgordonclan on 2011-05-08
Ok, the card shouldn't be having trouble with that, then. I've had trouble connecting sometimes since upgrading to Natty. (I'm not sure if it's my network card, some configuration problem, or my router...) I did discover the other day that rebooting my machine fixed it. You might consider doing that...

---

### Post by josephmills on 2011-05-08
> **Mr kmil said:**
> I got this back:
```

sudo: /ect/init.d/networking: command not found

```

Also I'm still having trouble connecting to the network. I typed in our password, and it seems to be stuck connecting.

another typo  **edit**```
sudo /etc/init.d/networking restart 
```wait it was not a typo it worked for me 
could we see a ```
iwlist auth 
```

---

### Post by Mr kmil on 2011-05-08
> **josephmills said:**
> another typo  could we see a ```
iwlist auth 
```

Josh: I'll attempt restarting as soon as I finish this post.

Joseph: Your output is
```

lo     Interface doesn't support scanning.

eth-   Interface doesn't support scanning.

wlan0  Authentication capabilities :
           WPA
           WPA2
           CIPHER-TKIP
           CIPHER-CCMP

```

---

### Post by Mr kmil on 2011-05-08
Alright, restarting has not helped.

Also, I keep getting the password prompt for my network, if that means anything. I think it just means that I can't connect properly.

---

### Post by josephmills on 2011-05-08
please take out your ip and hw address ```
nm-tool
``` and ```
rfkill list 
```

---

### Post by joshgordonclan on 2011-05-08
Yes, it means that it now knows the network, but it's not sure the network key is right.

---

### Post by Mr kmil on 2011-05-08
> **josephmills said:**
> please take out your ip and hw address ```
nm-tool
``` and ```
rfkill list 
```
I got this back:

(nm-tool):
```
NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             unavailable
  Default:           no
  HW Address:        00:D0:59:94:E3:81

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            p54pci
  State:             disconnected
  Default:           no
  HW Address:        00:12:BF:54:69:2C

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    OYRX4:           Infra, 00:1F:90:BF:EB:A8, Freq 2412 MHz, Rate 54 Mb/s, Strength 94 WEP

```
and 
(rfkill list):
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by josephmills on 2011-05-08
how far away are you from the access point? try sitting closer and doing a ```
iwlist scan 
```and a ```
iwconfig
```

---

### Post by Mr kmil on 2011-05-08
> **josephmills said:**
> how far away are you from the access point?

About 20 feet. Its on the other side of my 30'x30' room.

---

### Post by joshgordonclan on 2011-05-08
Any chance you can try a different access point?

---

### Post by Mr kmil on 2011-05-08
> **joshgordonclan said:**
> Any chance you can try a different access point?

I couldn't get to another access point for a couple of days. The plight of real life gives me lots of trouble in that regard.

---

### Post by josephmills on 2011-05-08
please see post #28 lets try update and upgrading too 
```
sudo apt-get update
``` then ```
sudo apt-get upgrade
``` then reboot anything again please see post #28 thanks

---

### Post by Mr kmil on 2011-05-08
> **josephmills said:**
> please see post #28 lets try update and upgrading too 
```
sudo apt-get update
``` then ```
sudo apt-get upgrade
``` then reboot anything again please see post #28 thanks

Joseph, thank you for everything. I just wanted to say that right now.

Update and Upgrade both completed successfully.

Iwlist and iwconfig gave me this back:
```

joe@joe-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

joe@joe-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"OYRX4"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

---

### Post by josephmills on 2011-05-08
can you log into your router and take down the wep and change it to nothing can you connect? If you can I would then set it to wpa2

---

### Post by Mr kmil on 2011-05-08
> **josephmills said:**
> can you log into your router and take down the wep and change it to nothing can you connect? If you can I would then set it to wpa2

That would be getting a little bit too advanced for me. Its a standard Verizon Router, And we just use the WEP key that came with it.

---

### Post by joshgordonclan on 2011-05-08
It's really not that hard to edit settings on the router. Go to [http://192.168.1.1](http://192.168.1.1) and follow [http://xkcd.com/627/](http://xkcd.com/627/) . You'll be an expert in no time flat! :)

---

### Post by Mr kmil on 2011-05-08
> **joshgordonclan said:**
> It's really not that hard to edit settings on the router. Go to [http://192.168.1.1](http://192.168.1.1) and follow [http://xkcd.com/627/](http://xkcd.com/627/) . You'll be an expert in no time flat! :)

I'll attempt it as soon as I find out our username and password.
This will take a while, so please subscribe to the thread, and I'll post the next development. Thank you all for everything so far.

---

### Post by josephmills on 2011-05-08
do you know the model name and number of the router?

---

### Post by joshgordonclan on 2011-05-08
Default for verizon routers: 
Username: admin (or maybe administrator) 
Password: password1

---

### Post by kotkaste on 2011-05-15
> **josephmills said:**
> can you log into your router and take down the wep and change it to nothing can you connect? If you can I would then set it to wpa2

Hello, I'm facing the same problem with the wireless on my old laptop (equipped with PRISM wireless adapter). Wireless was working well in Ubuntu 10.10 (using linux-firmware-nonfree). After upgrade to Natty Narwhal, wireless does not work: wireless networks available in range are listed, but it cannot connect to any network. I use WAP/WAP2 password but I also checked changing AP security settings to use WAP password or no encrpytion at all - stiil cannot connect even if no encryption. It keeps trying to connect but no success.

---

