---
title: "Connecting a modem router with a mobile broad band umts connection ?"
date: 2011-02-17
forum: Networking &amp; Wireless
---

### Post by AfrikaDietmar on 2011-02-17
Hi,

sometimes our ADSL connection gives up and we are left without internet connection for days until the problem gets fixed. I mean by this problem along the phone line.
It affects all machines that connect to the internet through a Netgear WIFI Modem Router. I recently tried an alternative when this happens is to use a USB Huawei Mobile Broadband UMTS connection which works when you insert it in 1 laptop. Is there a way i could get the Netgear WIFI modem router to connect on that usb stick or PC that is online on that usb stick and give access to other machines that will want to connect to the web ?

---

### Post by quixote on 2011-02-19
I'm the wrong person to answer this, but I find it a fascinating question.  I hope somebody more knowledgeable jumps in!

Meanwhile, just to think out loud: If I understand correctly, what you want to do is use the hub capabilities of the Netgear when it's not getting a signal.  How many ethernet jacks has it got? Could you daisychain it to the PC+Huawei and turn off its wireless for the time being??

---

### Post by AfrikaDietmar on 2011-02-21
Hi quixote!

nice that you like the idea/project of this challenge :)

> If I understand correctly, what you want to do is use the hub capabilities of the Netgear when it's not getting a signal.Yes, when our ADSL line is down, to make the Netgear WIFI Modem/Router use the Mobile Broadband UMTS connection. The modem router can be configured within a browser and usually connects itself to the web. The modem of that netgear router is i think in this case unrelevant when ADSL is down, it should somehow manage or distribute the internet connection of that machine that has connected to the web on that Broadband Mobile Router.

> How many ethernet jacks has it got?
4, and i have also connected to it 1 switch so that i have additional 5 ethernet jacks.

I know that before Modem Routers were available, a PC had to be connected to the web and a router would manage the connections for the others, i guess its a bit something similar we are trying to do with some new technologies ?

What do you think ?

bye bye,
Dietmar

---

### Post by inobe on 2011-02-21
it would be easier just unplugging the router and using a wireless card.

[http://www.net42.co.uk/os/linux/sharing_3g_with_hostapd.html](http://www.net42.co.uk/os/linux/sharing_3g_with_hostapd.html)

or for the device, eth, or wlan go into properties and share the device.

like so

[IMG]http://aslakjohansen.files.wordpress.com/2009/10/screenshot-editing-share-connection.png?w=379&h=503[/IMG]

---

### Post by AfrikaDietmar on 2011-02-21
> it would be easier just unplugging the router and using a wireless card.

No, the broadband umts USB doesn't send out a signal for other computers to detect it and then simply surf on it as a WIFI connection. The PC which is connected on that broadband umts usb stick can go online but it cannot be shared in that way as you described, also if i select according to your screenshot "Shared with all computers" nothing happens, the apply button remains unactivated.

We still need to use the router anyway because we share files across the network.

Maybe ubuntu machines can be set to surf through that pc by going through the router?... hmm...

---

