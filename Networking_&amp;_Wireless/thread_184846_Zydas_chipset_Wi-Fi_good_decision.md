---
title: "Zydas chipset Wi-Fi good decision?"
date: 2006-05-30
forum: Networking &amp; Wireless
---

### Post by DiGiTY on 2006-05-30
For the past 6 weeks I've been looking for a Wi-Fi USB adapter that would work with linux/ubuntu and the best i've come up with is the Zydas chipset, ZD1211.

Is this a good choice? Does it support at least WPA or WEP 64-bit? Is there something slightly better?

TIA

---

### Post by az on 2006-05-30
[QUOTE=DiGiTY]For the past 6 weeks I've been looking for a Wi-Fi USB adapter that would work with linux/ubuntu and the best i've come up with is the Zydas chipset, ZD1211.

Is this a good choice? Does it support at least WPA or WEP 64-bit? Is there something slightly better?

TIA[/QUOTE]
My revision of the 1211 does not work.  I haven't checked with the upstream drivers page in a while ( I konw it will one day work flawlessly with GPLed drivers - Zydas does provide native linux drivers) but not currently.  Its a 1211b.

I don't think they are the most powerful devices, either.

---

### Post by jml on 2006-05-30
USB wireless devices seem to have more problems working with Linux/Ubuntu.  If you have the option of using a PCMCIA wireless card for your connection, you will be more likely to be successful.  The cards that I have found that work with Ubuntu are Atheros based.  Cisco Aironet 350, Aironet 802.11 a/b/g wireless card and NetGear WG511T were all recognized by Ubuntu out of the box.

As for encryption, Ubuntu does not actively support WPA yet.  If you need/want that you need to download, install and configure an application called wpa_supplicant.  I think it can be found in the Universe repository.

Ubuntu does support WEP.  Hope this helps.

Joe

---

### Post by mossholderm on 2006-05-30
I just got a ZyXel AG-225H working, under Dapper. It uses the ZD1211 chipet, but you will need to take a few steps to get it working:

1) Download/extract the driver from [http://zd1211.ath.cx/](http://zd1211.ath.cx/)
2) edit src/zdusb.c  to add a line after this:

     *#define PRODUCT_G220    0x3401*

   that looks like this:

     *#define PRODUCT_AG225H  0x3409*

3) run *make*
4) run *sudo make install*

The downloaded version of the driver also supports wpa_supplicant, using the *wext* driver. Under Dapper this means no need to patch wpa_supplicant. Not sure about Breezy.

    --Matt

---

### Post by DiGiTY on 2006-05-31
thanks for the replies. i can only use USB (for some reason this laptop doesn't have a PC card slot)

i actually went and bought the ZyXEL ZyAIR G-220 USB and it appears to work out the box. i did however download whatever wireless packages i saw in the synaptic package manager before actually buying it, so that's prolly why it worked. i followed the install/config commands on zd1211.ath.cx and bing-bong i was on the net via some poor bloke's unsecured linksys router

that was last night, but after running some ubuntu updates earlier today and installing even more wireless packages, i can't get on a wireless network, not even mine. after running "sudo dhclient wlan0" it says "bound to 192.168.0.101...", but after running ifconfig to see if it sticks, it doesn't (no IP address listed for wlan0). it did stick last night

any ideas???

---

