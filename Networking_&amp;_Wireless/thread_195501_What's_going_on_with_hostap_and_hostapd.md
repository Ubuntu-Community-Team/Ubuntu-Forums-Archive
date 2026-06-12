---
title: "What's going on with hostap and hostapd?"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by nmuntz on 2006-06-12
It seems that neither of these are working for me in 6.06. 

hostapd would not work with my madwifi card.  It appeared as though hostapd was compiled with madwifi support, but the modules shipped in the release are madwifi-ng(?)   I had to download the source and compile against madwifi to get it to work.   Sorry, I don't have any more details.  I was desperate to get this working and didn't record anything. ;-(

On a different machine, the hostap **driver** is also not working with my fairly generic prism2 card (Senao 2511).   The modules that come with the kernel do this:

Jun 12 07:09:22 stinkpad kernel: [4436639.726000] pccard: PCMCIA card inserted into slot 1
Jun 12 07:09:22 stinkpad kernel: [4436639.726000] pcmcia: registering new device pcmcia1.0
Jun 12 07:09:22 stinkpad kernel: [4436639.728000] hostap_cs: Registered netdevice wifi0
Jun 12 07:09:22 stinkpad kernel: [4436639.768000] hostap_cs: index 0x01: Vcc 3.3, irq 3, io 0x0100-0x013f
Jun 12 07:09:24 stinkpad kernel: [4436641.969000] wifi0: interrupt delivery does not seem to work
Jun 12 07:09:24 stinkpad kernel: [4436641.969000] hostap_cs: Initialization failed

I installed hostap-source and tried to rebuild using module-assistant.  The rebuilt modules give me this:

Jun 12 20:35:32 stinkpad kernel: [4294701.613000] pcmcia: hostap_cs lacks a requisite callback function

I used Dapper quite heavily during the development cycle on both of these machines and never had any of these problems.    I can't seem to find any bugs related to this in launchpad.

Is anyone else having problems?

---

### Post by unrandomsam on 2006-06-17
Do you know how to make dapper use madwifi-ng instead of madwifi-old ? (It appears that modules are there for both madwifi-old and madwifi-ng)
in /lib/modules/*/madwifi and madwifi-ng respectively. I haven't worked out how to blacklist madwifi old properly (I presume there may be just one key module to blacklist and then madwifi-ng would be used)

---

### Post by d0gi on 2006-07-11
I'm having the same problem. Same errors with a Compaq WL100 card :( I tried Knoppix v5.0 and it worked flawlessly. I hope this gets fixed, it's so annoying to install another distro and do the DSDT-fixes again when I just got everything else working :-|

Edit: Ahem.. updated my kernel from 2.6.15-20 to 2.6.15-26 and everything is back to normal :)

---

