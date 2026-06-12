---
title: "Lucid Lynx/Atheros AR5007EG wl problems,no connection"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by dooper on 2010-11-28
Toshiba A210 12U lappy
Dual boot with Vista and Ubuntu 10.04LTS

Atheros pci wireless card 

Vista reports the card as being AR5007EG

lspci reports it as AR5001

It used to work ok pretty much most of the time but now it just wont work.

It cant see my router or list it and i cant connect to it.

If i try,it keeps trying then prompts for my wep/psk password.

It will work perfectly if i reboot to windows Vista.

Occasionally,if i do a full reboot,it will work but then if i shut the lid,go away,come back,it wont connect again.

As far as i know,the drivers are the included ones in the OS package and i havent attempted to use the madwifi drivers.

I am a relative newbie with Linux.

Apart from this issue,everything works fine.

Thanks for any assistance.

---

### Post by uncaspi on 2010-11-28
Have you searched the threads for AR5001?

---

### Post by dooper on 2010-11-28
> **uncaspi said:**
> Have you searched the threads for AR5001?

Hi,,yes i have done lots and lots of reading.

Curiously,it is now working again after i deleted the connection and set up a new one using different encryption settings. There is still an issue in which if i shut the laptop lid,then re-open it to resume,it wont connect..it just keeps trying. After a few open/shut lids and retries,it may connect. It seems like pot luck. I do notice that when i shut the lid,the wireless indicator light on the front panel goes out so presumable the wireless card goes into sleep mode or gets powered down. Maybe this is the issue on resume? I'll search further.

I'm wondering if there is a wireless card that i can use to replace this one which will be more reliable?

Havent dismantled the lappy but im guessing it has some kind of mini pci plug in interface?

---

### Post by uncaspi on 2010-11-29
I can't answer all your questions, but some distros are worse than others. Ubuntu 10.04 32 bits have less problems than i.e. 10.10 64 bits and so on.
8.04 is better than 8.10 and 9.04 is better than 9.10 in my opinion, but I can be wrong. But I've tried all distros since 8.04 LTS and up to 10.04 LTS.
Anyway all in all wireless depends on finding the right driver. If you hit the bulls eye with the driver, modprobe just flow like a dream, and cards shows up in ifconfig and in network-manager at the same time. So the first thing you should investigate is your driver.

---

### Post by dooper on 2011-01-02
I have now "upgraded" to Meerkat form 10.04LTS.

The wireless issue still remains though curiously i have tried something else.

If i untick the "connect automatically" box then open the lid and just log in then select the pre set up home network and click to manually connect,it seems to work so far unless it too becomes glitchy.

Maybe there needs to be a delay between opening lid and connecting and the auto connect makes that delay too short for something to happen eg a driver to load or initiate ??

---

