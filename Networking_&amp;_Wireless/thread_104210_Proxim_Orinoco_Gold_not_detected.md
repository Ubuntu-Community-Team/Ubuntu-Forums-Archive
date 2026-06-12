---
title: "Proxim Orinoco Gold not detected"
date: 2005-12-15
forum: Networking &amp; Wireless
---

### Post by llamuh on 2005-12-15
Im somewhat of a noob to linux, so please forgive my ignorance.  i say somewhat because ive ran various distros of linux off and on over the last 7 years.  i usually only end up running it for a month or two before i go back to windows for whatever reason.  back then it used to be because of gaming but now i think its because im just too lazy to put forth the effort to get things (like this wifi card) to work.

Anyways, I have a Proxim Orinoco 802.11b Gold wifi card.  The model is listed as 8420-WD with an FCC ID of IMRPC2411B.  From what i gather from a few other forums this card may actually have an atheros chipset and not the hermes chipset used in the 'classic' card.  I am actually surprised that this isnt supported by default, but oh well.  The first step i took was suggested here on the forums in a HOWTO.  i attempted to use ndiswrapper on the windows drivers i obtained from Agere.  ndiswrapper returns with "no vendor."  someone on the #ubuntu channel suggested i try madwifi (though my card isnt listed in the supported devices section of their page)  so i downloaded the current release of madwifi only to find that ubuntu doesnt install the build-essential package by default.  first distro i can remember that hasnt done this.  weird.. i thought they were pretty much 'essential' heh.  so i used apt-get to install the build-essential package with no problems.  now when i try to use 'make' to install the madwifi drivers, i get "Default KERNELPATH not found, using /usr/src/linux  *** KERNELPATH: /usr/src/linux does not exist.  Stop."  so yeah /usr/src/linux is empty which i also found odd that it didnt install the kernel source by default but oh well.  so i attempt to use apt-get to install the linux-source and get "You must put some 'source' URIs in your sources.list"  I know i will also have to get the kernel-headers after this, heh.

This is increasingly becoming a pain and i, for some reason, think that even when i get past these issues my card still will not work.  i already know that i dont have the sharutils so im guessing that will be my next step.

Can anyone offer help on this?   am i doing all of this in vain and is there an easier way to get my card working!?  Any help would be appreciated.  im coming close to just ditching this and going back to windows ;\

Thanks
- Chris

---

### Post by jml on 2005-12-15
llamuh, I feel your pain.  Wireless is one of the most difficult things to get configured in LINUX.  Its the only reason I still dual boot my laptop.  A couple suggestions.  When you installed Ubuntu, did you have the wireless card inserted in the laptop at the time?  If you did not, then one suggestion is to reinstall Ubuntu with it installed.  Its possible the the Prism Oronoco card is not supported, but I would be very supprised.  Then go to the networking application and see if your card is listed.  If it is, highlight it, and then click on the configure.  Fill in the appropriate blanks.  Click OK and then click on Activate.  This step may take several minutes.  When done, back out and you should be set.

If your card is still not reconized, post again here and hopefully you will get some more help.

Joe

---

### Post by Lambert on 2005-12-15
First things first, let's verify what chipset the card is using. Post the output of these commands.

sudo lshw -C network
lspci -v

---

### Post by llamuh on 2005-12-15
btw this is an old Dell Inspiron 4000, if that helps.  unfortunately i dont have any of my 'real' PCs cause im going through a divorce and my wife wont give them to me.  all i got away with is this laptop because it was already in my car heh.

Yes, the card was inserted at the time of installation.  Ive also verified that the PCMCIA is working.  It detects the card but shows it as an "unsupported card."

wish i could cut and paste, but
sudo lshw -C network
*-network
description: Wireless PC Card Model 0111
vendor: Agere Systems
physical id: 0
slot: Socket 1

hm thats how windows identified it also..  i should look into this lshw command to see what you had me do, lol ;)


lspci -v outputs a lot of info so ill sum it up if i can and post what i think is relevant

0000:00:00.0 Host bridge: Intel Corp. 440bx/zx/dx

0000:00:01:0 Pci bridge: Intel Corp. 440bx/zx/dx

0000:00:03:0 CardBus bridge: Texas Instruments PCI1420
subsystem: Dell: unknown device 00b0
0000:00:03:1 Cardbus bridge: Texas Instruments PCI1420
subsystem: Dell: unknown device 00b0

0000:00:07:0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA

0000:00:07:1 IDE interface: Intel Corp. 82371AB etc.

0000:00:07:2 USB Controller: Intel Corp. 82371AB etc.

0000:00:07:3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI

0000:00:08.0 Multimedia audio controller: ESS Technology ES1983S 
Maestro-3i

0000:00:10.0 Communication controller: Lucent Microelectronics WinModem 56k

0000:01:00.0 VGA compatible controller: ATI Tech. Inc. Rage Mobility M3 AGP 2x

i didnt post IRQs or anything because i doubt it would be an IRQ conflict.  or am i wrong? heh

lspci -n shows 104c:ac51 for the cardbus if that helps



edit: Lamber- i was reading through your wireless troubleshooting guide and visited the site [http://linux-wless.passys.nl/](http://linux-wless.passys.nl/) linked in it and according to it, my model 8420-WD uses the wavelan driver not madwifi.  im confused by this though because people on the netstumbler forum say that there are different versions of the proxim orinoco gold card and that if it doesnt say "classic" somewhere on it then it is not using the older hermes chipset.  theyve even gone as far as breaking it down to the FCC ID.  this is why i was lead to believe that i might actually have the atheros chipset.

---

### Post by llamuh on 2005-12-15
anyways so i downloaded the orinoco_cs drivers since im bored and there isnt much else i know to do with this and when i try to make it says "the kernel source is not configured.  stop."  heh this is a different error than before when it claimed it couldnt find the kernelpath.   seems like i get more and more confused as i go ;P

---

### Post by llamuh on 2005-12-16
hate to be bumping myself but i figure i should update.  ive installed the kernel headers and GCC and such.. things that i thought were already installed heh.. anyways so now when i try to make i get:
make -C /usr/src/linux-headers-2.6.12-9-386 M=/home/llamuh/hermes/orinoco-0.15.rc2 modules
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4:
 command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
 CC [M]  /home/llamuh/Desktop/hermes/orinoco-0.15rc2/hermes.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/llamuh/Desktop/hermes/orinoco-0.15rc2/hermes.o] Error 127
make [1]: *** [_module_/home/llamuh/Desktop/hermes/orinoco-0.15rc2/] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [modules] Error 2

---

### Post by ephman on 2005-12-16
hey,

i know this doesn't help your problem but i also have a proxim orinoco gold card that i'm running under 2.6.12-10-686 with a dell inspiron 5100.  now i guess i'm lucky because my card was detected and i haven't had a problem.  so here's some info about my card.  maybe you could compare so that you can rule out hardware problem.

description: Wireless interface
       product: AR5211 802.11ab NIC
       vendor: Atheros Communications, Inc.
       physical id: 1
       bus info: pci@03:00.0
       logical name: ath0
       version: 01
       serial: 00:20:a6:4b:e6:bf
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.6.0 (EXPERIMENTAL) ip=192.168.0.99 multicast=yes wireless=IEEE 802.11b
       resources: iomemory:18800000-1880ffff irq:11

good luck.

thanks for the bandwidth,
ephman

---

### Post by llamuh on 2005-12-16
thanks for the response.  im talking with some people in the #ubuntu channel and they believe it is the older orinoco/hermes chipset and not the atheros.  so far ive been able to load orinoco_cs with modprobe, but it still isnt listed in iwconfig

---

### Post by Lambert on 2005-12-16
With your output I know it's not an atheros chipset. You would have output like ephman.

With the output you gave something doesn't look right. You said you know the pcmcia is working, just showed an un supported card. How did you come to that conclusion?


You don't have a line like this (        bus info: pci@03:00.0) in your lshw output and I don't see the device in the lspci output. 

At the moment I believe your problem is on a device level and not a driver level.

Have you verified the card works in another system or booted into windows?

---

### Post by llamuh on 2005-12-16
the reason i said i know the pcmcia is working is because in KDE when i look at the pcmcia it says that one slot is empty and the other slot contains an unsupported card. i would think that if it has pcmcia even listed and then is able to probe the cards that it would be working.  the card should be working.  unfortunately i dont have another laptop around to verify it with but i used the card to download the kubuntu ISO just before i installed it so i dont see how it would stop working in a matter of an hour or so.
thanks again
- Chris

---

### Post by llamuh on 2005-12-16
eh well its been a week now since ive been able to get on the net on my laptop so i guess im giving up and going to go ahead and reinstall XP.  if anyone has any ideas go ahead and share them though because i would love to be able to use ubuntu in the future.

---

### Post by llamuh on 2005-12-17
just thought that i would add that i cannot find my windows CD at the moment and decided to try SUSE 10.1 and Mandriva 2006.  well, neither of those detected the card either, but the card isnt dead.  i was able to test it in another laptop with windows and it worked great.  from everything ive gathered on other forums, linux in general just doesnt seem to like this particular card and the only success people have had is to manually build the module and recompile the kernel.  only problem with that that i have is the only drivers i can find are for an older kernel so i dont know what to do.

---

### Post by ephman on 2005-12-21
buy a new card.

ephman

---

