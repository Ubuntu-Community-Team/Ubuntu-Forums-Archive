---
title: "Tried almost everything to setup Wireless"
date: 2011-02-27
forum: Networking &amp; Wireless
---

### Post by everenferno on 2011-02-27
The title says it all. It's been a couple of days since I got my Toshiba NB505-500BL netbook and a friend recommended I use ubuntu granted I never used it before as an operating system. After hours and hours of researching and reinstallations of the netbook remix 10.10 edition, here's every method I can remember trying and not working as of right now:

Clicking on the Network icon only brings up WIRED NETWORK and doesn't even mention WIRELESS NETWORK until I configure it manually, which does absolutely nothing even if I click connect automatically and reboot my computer

I used almost every terminal command listed online but most of them will say access denied and are you root?

My wireless card is not activated by an external button but the wireless light on my netbook is on (and orange) yet Ubuntu does not want to acknowledge it

I downloaded the additional drivers program and it always says there's no proprietary drivers in use on this system.

My wired connection works and that's how I'm on right now.

I can't remember everything but I've constantly been updating always and I've used ndiswrapper and apt-get update. I'm really disheartened that anything will work now so I'm just going to post this and see what anyone will say.

07:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
        Subsystem: Realtek Semiconductor Co., Ltd. Device 8181
        Flags: bus master, fast devsel, latency 0, IRQ 11
        I/O ports at 2000 [size=256]
        Memory at f0100000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

That's what came from lspci -v | less

Do I need a 64 bit version? Is it an access restricton issue? 

I'll try whatever it takes. Just ask me to do it. Thanks.

---

### Post by bkratz on 2011-02-27
You might want to see this thread

[http://guide.ubuntuforums.org/showthread.php?t=1580036](http://guide.ubuntuforums.org/showthread.php?t=1580036)

---

### Post by everenferno on 2011-02-27
thanks I'll give it a try!

---

### Post by everenferno on 2011-02-27
I downloaded the compressed file, extracted it to my netbook desktop, navigated to the folder directory in terminal and executed some commands on the thread you linked to. 

The commands were:
3.3) sudo apt-get install build-essential
3.4) make
3.5) make install

then after rebooting... IT WORKED. AMAZING!

Thank you so much ;)

---

### Post by bkratz on 2011-02-27
Congratulations,

Please return to the thread tools and mark this as [solved] just in case it helps someone else as thanks.

---

