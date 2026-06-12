---
title: "RTL8187B + ndiswrapper 64 bit"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by uylug on 2009-08-30
I've been stuck with this issue for months. The open source driver rtl8187 has really low transfer rate and when i transfer files I get a max speed of 300KB/s and if i ping my router i get 300ms or so.

I haven't been able to install the 64bit driver using ndiswrapper because my computer just hangs when i do so.

Here's the ouput of lsusb:

```
$ lsusb
Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter

```

Any ideas on how to solve this?

Thanks!

---

### Post by quaker_emu on 2009-09-01
I am having the same problem with the same 0bda:8189 device built into a Toshiba laptop - the open source driver goes at 300-500 Kb/S even when I am a few feet from the access point. :(

So far I have tried:

- Different access points to see if it was an issue with my wireless router. All access points suffer from low speeds.

- Turning WPA2 off to see if it was an encryption issue (it was not).

- NDIS wrappers + all available windows drivers available for the RTL8187B chipset at realtek.com. All loaded but did not recognize the device as being present.

- NDIS wrappers + a windows driver where I hacked the .inf file to include the 8189 code. Driver loaded and said device present but checkbox for enabling wireless in control GUI remained unavailable.

After reading [http://ubuntuforums.org/showthread.php?t=792092&highlight=RTL8187b](http://ubuntuforums.org/showthread.php?t=792092&highlight=RTL8187b) about the RTL8187 ID 8197 I am going to try the following as well:

A) Force rate to 5 Mb/S.

B) Request a linux driver for this ID from realtek via email.

I'll report back on whether I get anywhere. Sorry I can't offer any instant answers but I'd be glad to hear of anything others find.

---

### Post by uylug on 2009-09-01
> **quaker_emu said:**
> I am having the same problem with the same 0bda:8189 device built into a Toshiba laptop - the open source driver goes at 300-500 Kb/S even when I am a few feet from the access point. :(

So far I have tried:

- Different access points to see if it was an issue with my wireless router. All access points suffer from low speeds.

- Turning WPA2 off to see if it was an encryption issue (it was not).

- NDIS wrappers + all available windows drivers available for the RTL8187B chipset at realtek.com. All loaded but did not recognize the device as being present.

- NDIS wrappers + a windows driver where I hacked the .inf file to include the 8189 code. Driver loaded and said device present but checkbox for enabling wireless in control GUI remained unavailable.

After reading [http://ubuntuforums.org/showthread.php?t=792092&highlight=RTL8187b](http://ubuntuforums.org/showthread.php?t=792092&highlight=RTL8187b) about the RTL8187 ID 8197 I am going to try the following as well:

A) Force rate to 5 Mb/S.

B) Request a linux driver for this ID from realtek via email.

I'll report back on whether I get anywhere. Sorry I can't offer any instant answers but I'd be glad to hear of anything others find.

Glad to know I'm not the only one.

So far I've tried changing the rate to 54M but doesn't make any changes at all. I do not get a weak signal but do get a high packet loss unless i run this command:

```
sudo iwconfig wlan0 retry 99999999
```
However, if I transfer files (which is extremely slow btw! been transferring at 90KB/s these days!) when i ping my router i get even 20 seconds which is way too much and this is when i do lose lots of packets!

---

### Post by uylug on 2009-09-03
Sorry to bump this thread... but does anyone know how to solve this?

---

### Post by quaker_emu on 2009-09-04
I retried ndiswrappers + forcing it to associate with 8189 using command lines rather than the GUI so I could see what what was happening. 0bda:8189 appears to be close enough to the other RTL8187B's that the toshiba can get an IP address using DHCP but not close enough to communicate over the link :(.

In the process I messed up the system enough that I am going to have to reinstall. Could you try forcing your link speed to rates < 54 M / sec with the native r8187 driver and report back?

I have a feeling that I am going to end up "solving" this problem by getting a usb key wifi adapter with another chipset...

---

### Post by uylug on 2009-09-05
> **quaker_emu said:**
> I retried ndiswrappers + forcing it to associate with 8189 using command lines rather than the GUI so I could see what what was happening. 0bda:8189 appears to be close enough to the other RTL8187B's that the toshiba can get an IP address using DHCP but not close enough to communicate over the link :(.

In the process I messed up the system enough that I am going to have to reinstall. Could you try forcing your link speed to rates < 54 M / sec with the native r8187 driver and report back?

I have a feeling that I am going to end up "solving" this problem by getting a usb key wifi adapter with another chipset...

That didn't work either. Stil getting the same results.

Set it to 1mbps, 5.5 mbps, 54 mbps... still the same.

---

