---
title: "ra0 &quot;Not Configured&quot; -- Why?"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by polo_step on 2006-06-08
[FONT="Courier New"]The internal RT2500 MiniPCI in this notebook works perfectly well in XP -- only not in Linux.  I've been trying various distros all night and though the device is always recognized, it won't work -- at all.  In the Ubuntu network tool, I get the ra0 "not configured" error.

Any ideas where to start on this?

As always, thanks for any help![/FONT]

---

### Post by ComplexNumber on 2006-06-08
can you give me a brief rundown on what you've done to configure your wireless card? then i can get a measure of what sort of help you need, and in what direction.

---

### Post by polo_step on 2006-06-08
[QUOTE=ComplexNumber]can you give me a brief rundown on what you've done to configure your wireless card? [/QUOTE]
[FONT="Courier New"]Honestly not very much, just fiddled ignorantly with **iwconfig**, **ifconfig** and **iwlist**.  No results.

As the little USB zYdas 1211 dongle I had here as a control seems to configure itself as soon as it's plugged in with no added work on my part, I assumed that a MiniPCI card would more or less do the same.

I just pulled the device and it's a Qcom Q802MKG.  It's a very typical example of the RA2500 MiniPCI cards and was used as OEM in very many notebooks in the past year or two.  It uses the generic Ralink drivers for XP and works perfectly (including WPA & WPA2) with the most recent one.  I'm using it now.

Thanks for any pointers![/FONT]

---

### Post by polo_step on 2006-06-08
[FONT="Courier New"]Another thought -- could it be that this ra0 device will not run in "live" mode because it has to have some sort of a .conf file written and saved to be read and loaded at boot?

**sudo ifconfig ra0 up**

...will get the card scanning and working, but in the GUI retwork tool it still shows not configured.[/FONT]

---

### Post by teeds on 2006-06-09
Assuming it is a RT2500 chip try this guide:
[URL="https://wiki.ubuntu.com/WifiDocs/RalinkRT2500"]
https://wiki.ubuntu.com/WifiDocs/RalinkRT2500[/URL]

---

### Post by polo_step on 2006-06-10
[QUOTE=teeds]Assuming it is a RT2500 chip try this guide:
[URL="https://wiki.ubuntu.com/WifiDocs/RalinkRT2500"]
https://wiki.ubuntu.com/WifiDocs/RalinkRT2500[/URL][/QUOTE]
[FONT="Courier New"]Irrelevant in 6.06, according to numerous posts. :( 

Bad, but in someother distros

**ifconfig ra0 up**

Will cause a total system crash, 100% of the time.[/FONT]

---

### Post by teeds on 2006-06-10
Worked for me ok.  I am using a Belkin 7010 (pcmcia card).

I just read through the stuff on /etc/network/interface file and took from it what I needed (there are a few comments and changes to the doc as it goes through)

No worries.

---

### Post by snooo on 2006-06-12
[QUOTE=polo_step][FONT="Courier New"]Another thought -- could it be that this ra0 device will not run in "live" mode because it has to have some sort of a .conf file written and saved to be read and loaded at boot?

**sudo ifconfig ra0 up**

...will get the card scanning and working, but in the GUI retwork tool it still shows not configured.[/FONT][/QUOTE]

Having the exact same problem. I have the same chipset with a 128 bit WEP key... Bought this card because of its supposed Linux support :-/

---

