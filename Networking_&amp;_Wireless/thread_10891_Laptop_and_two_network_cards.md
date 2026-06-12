---
title: "Laptop and two network cards"
date: 2005-01-12
forum: Networking &amp; Wireless
---

### Post by Wim Sturkenboom on 2005-01-12
A laptop has a PCMCIA nertwork card and a docking station with a second network card.
When running stand-alone, the PCMCIA card is eth0. When running in the docking station, it becomes eth1 (and the card in the docking station becomes eth0).

I think that I understand why this happens (detection sequence).

The docking station always is used in a network with DHCP while the PCMCIA card is used with a fixed IP-address.

Is it possible to prevent this 'switching' as it causes 'annoyance'. Currently I have two networking profiles, but I like not to be bothered with it.

---

### Post by HankB on 2005-01-16
I'm pretty sure that you can do this by aliasing the name of the module that loads for either card in /etc/modules.conf like:

```

alias eth0     <module>
alias eth1     <module>

```

Of course you really want to add this to /etc/modutils/aliases and run update-modules to rebuild /etc/modules.conf.

HTH,
hank

---

### Post by sreid on 2005-01-16
I happen to <strike>be having</strike> have had (see below) the same problem. Laptop with built-in 100Mbps ethernet (Acer Aspire 1300, ethernet is Via Rhine chipset), and a wireless card (SMC2835W with the prism54 chipset).

If I plug the wireless card in after boot, it comes up as eth1, but if I boot with the card in it comes up as eth0 and the on-board is eth1.

I tried your alias suggestion, which seems like it should work, but it does not. Manually rmmod'ing the prism54 and via_rhine modules, then loading them in the correct order (via_rhine first) solves the problem until the next reboot.

While typing the above, it occured to me that forcing the via_rhine module to load first would fix things. So I added via_rhine to the list of modules in /etc/modules, and that did the trick!

I don't know if this will work for the original poster though, as it requires one device that is always present to take the eth0 position.

---

### Post by HankB on 2005-01-16
[QUOTE=sreid]
I tried your alias suggestion, which seems like it should work, but it does not. Manually rmmod'ing the prism54 and via_rhine modules, then loading them in the correct order (via_rhine first) solves the problem until the next reboot.
[/QUOTE]

I wonder what conditions cause that to work or not. I haven't had that problem specifically but I'm aware that you can use the alias to specify a module for a device. Perhaps the issue is that it is a one way association. IOW, something looking for the device will cause the correct module to be loaded but if the module gets loaded and has to find a device, it will be assigned the next available.

One thing to try is to determine what loads the module before the network starts up and defeat it. I found that when I installed hotplug on my (Debian) laptop, it loaded modules for H/W it found causing my 10/100 Ethernet to be displaced by a built in 802.11b wireless card. This can be turned off by putting the modules in /etc/hotplug/blacklist.

And then figure out where else the modules get loaded. On my system I've blacklisted the orinoco modules but they get loaded by the kernel anyway apparently before hotplug runs. So I guess I've got some homework to do before I answer this question. (In my case both the orinoco and Ethernet H/W are built in so all I had to do was modify my network scripts to use eth1 when I wanted to use Ethernet.)

thanks,
hank

---

### Post by Wim Sturkenboom on 2005-01-19
Can only find one thing that sounds like network to me (3C905). Can't figure it out; which outputs need to be posted here (dmesg. lsmode,...) so someone can help.

---

### Post by HankB on 2005-01-19
That certainly sounds like the Ethernet driver.

Unfortunately this gets a lot stickier than I thought. I decided to try to defeat loading of my (no longer used) WiFi modules. I started renamin startup scripts in /etc/init.d to find out what was loading it since I had blacklisted it for hotplug and removed the "auto" attribute in the network settings.

I was up to a dozen scripts not functioning before the drivers remained unloaded. I dicovered that hotplug loaded them regardless of the blacklisting and pcmcia loaded them even though the H/W is mini-PCI. There might have been other startup scripts that also load them but at that point I decided this was more work than I needed to do.

I'm afraid that the issue for you is to identify and defeat anything that's loading the modules by name so that when networking loads them via alias, the alias name takes precedence to identify the device as you desire.

That's a bit more of a tangled mess than I had expected.

---

