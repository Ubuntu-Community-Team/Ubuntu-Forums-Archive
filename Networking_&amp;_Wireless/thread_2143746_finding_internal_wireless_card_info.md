---
title: "finding internal wireless card info"
date: 2013-05-09
forum: Networking &amp; Wireless
---

### Post by dvdhudson33 on 2013-05-09
Very first post from a newbie Ubuntu 12.10er...

 I'm trying to work out what wireless chipset is running in my desktop &#8211; a four year old HP Pavilion s3680d.  HP's website says it's a *802.11 b/g wireless USB adapter card*, which is not only unhelpful but kinda odd, given that it's internal to the PC, not USB.

Anyway ...
I tried**[FONT=courier new] [COLOR=#0000cd]lspci | grep Network[/COLOR][/FONT]** but it gives no info, just dumps me back to the terminal prompt.

So I tried [COLOR=#0000cd][FONT=courier new]**lshw -C network**[/FONT][/COLOR], which does have lots to say about the PC's brand/model of wired-Ethernet card, but very little about the wireless system:

[FONT=Courier New]description: Wireless interface[/FONT]
 [FONT=Courier New]physical id: 3[/FONT]
 [FONT=Courier New]bus info: usb@1:6[/FONT]
 [FONT=Courier New]logical name: wlan0[/FONT]
 [FONT=Courier New]serial: 00:22:5f:14:d0:a7[/FONT]
 [FONT=Courier New]capabilities: ethernet physical wireless[/FONT]
 [FONT=Courier New]configuration: broadcast=yes driver=rt73usb multicast=yes wireless=IEEE 802.11bg[/FONT]
 
 I should add that I'm not having any problems with the PC, I'm just curious to know what's 'under the hood' (not sure if Americans use that phrase, but I'm sure you get the idea).

 Thanks for any assistance!

---

### Post by TheFu on 2013-05-09
MAC addresses are supposed to be unique. Every maker has a unique set to use and we can look those up to get a little more information.
[http://hwaddress.com/?q=00%3A22%3A5f%3A14%3Ad0%3Aa7](http://hwaddress.com/?q=00%3A22%3A5f%3A14%3Ad0%3Aa7)  is the query that was used. Looks like an USB wifi connection is used, so to get any more data you'll need to use **lsusb** commands.  The driver **rt73usb** is a hint too.

---

### Post by papibe on 2013-05-09
Hi dvdhudson33.

Could you post the result of these commands?
```
lspci -nnk | grep -iA2 net

ifconfig

iwconfig

rfkill list all
```
Regards.

---

### Post by dvdhudson33 on 2013-05-10
Sorry - haven't done this yet, but I will tonite (trying to get a late paper into my professor), but I did take a quick look at [COLOR=#0000cd]rfkill[/COLOR] - that's a great tool.

---

### Post by dvdhudson33 on 2013-05-12
**[COLOR=#0000cd]@HP:~$ lspci -nnk | grep -iA2 net[/COLOR]**
00:0f.0 Ethernet controller [0200]: NVIDIA Corporation MCP73 Ethernet [10de:07dc] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:2a65]
    Kernel driver in use: forcedeth
[B][COLOR=#0000cd]
@HP:~$ iwconfig
[/COLOR][/B]wlan0  IEEE 802.11bg  ESSID:"University"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: D8:C7:C7:4C:86:E1   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: on
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0
lo        no wireless extensions
eth0    no wireless extensions

**[COLOR=#0000cd]@HP:~$ rfkill list all[/COLOR]**
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no[B][COLOR=#0000cd]

[/COLOR][/B]**[COLOR=#0000cd]@HP:~$ [/COLOR]****[COLOR=#0000cd]ifconfig[/COLOR]**
 ... hmm, that seems like a lot of info, I'm not sure I should post it in a public forum...

So, what can I learn from all this?

 - - - - - - - - - - - - 


TheFu:  yes, the rt73usb was certainly a hint!  Thanks for pointing it out.

---

### Post by papibe on 2013-05-15
```
wlan0 IEEE 802.11bg ESSID:"University" 
```
There it is. But it is not using a PCI internal slot.

Could you post the result of this command?
```
lsusb
```
Regards.

---

