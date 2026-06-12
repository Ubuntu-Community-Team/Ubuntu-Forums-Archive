---
title: "can't use pcmcia W-CDMA adapter (NetIndex D01NX)"
date: 2010-04-13
forum: Networking &amp; Wireless
---

### Post by mikey_likesit on 2010-04-13
Hello,

I'm using a Kohjinsha SR6 and trialling the ubuntu 9.10 netbook remix from a USB stick before taking the plunge. I have an Emobile D01NX adapter for internet, but I simply can't get it to work even though e-mobile is in the Japan mobile broadband options in network connections (maybe for some of their USB adapters?).

running lspcmcia -v gives:

Socket 0 Bridge: [yenta_cardbus]         (bus ID: 0000:02:06.0)
Configuration:   state: on         ready: unknown
                        Voltage: 3.3V   Vcc: 3.3V   Vpp: 3.3V
Socket 0  Device 0:      [--no driver--]        (bus ID: 0.0)
             Configuration:    state: on
             Product Name:   NetIndex D01NX
             Identification:     manf_id: 0xc036  card_id: 0x1003
                                      function: 254   (unknown)
                                      prod_id(1): "NetIndex" (0xf2ba4352)
                                      prod_id(2): "D01NX" (0x73bb32c2)
                                      prod_id(3): --- (---)
                                      prod_id(4): --- (---)


one thing that's crossed my mind is that I haven't got persistence on my usb drive, would that be likely to affect anything? As I understand it that just means everything I do needs to be re-done when I reboot right?

I looked up this issue on the Japanese Ubuntu forums ([here]("https://forums.ubuntulinux.jp/viewtopic.php?id=962")) and what I gather is that there is some sort of technical issue with the translation chip (Elan VMB5000?) but that the Sharp Zaurus ([link]("http://en.wikipedia.org/wiki/Sharp_Zaurus")), which runs on a linux variant, has a driver out for my specific device ([here]("http://emobile.jp/products/nx/d01nx/download/Driver/ZaurusDriver/d01nx_dialup_plugin_src_Zaurus.tar.gz")). This may be the answer I'm looking for, but unfortunately my linux ability is largely limited to using the GUI and a few basic text commands so installing or modifying the files is way beyond me.

For anybody who reads Japanese, [here]("http://hp.vector.co.jp/authors/VA012337/misc/d01nx_zaurus.html") is the page I got the driver download link from. I don't know if that stuff is of any help but just in case...

Anyway, I would hugely appreciate anyone's assistance on this as I'm sick of always waiting for XP on my computer but unless I can get the internet working there's no use for me to permanently install ubuntu...

Thanks!
Mike

---

### Post by mikey_likesit on 2010-04-19
alright, in case anybody comes across this post having a similar problem, I found a workaround.

It's probably cheating, but rather than force the issue I'm now using Emobile's Pocket Wifi, which broadcasts a wifi signal over a short range and acts as 3G router.

---

