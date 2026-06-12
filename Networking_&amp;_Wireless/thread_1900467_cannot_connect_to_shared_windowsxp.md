---
title: "cannot connect to shared windowsxp"
date: 2011-12-26
forum: Networking &amp; Wireless
---

### Post by lux11 on 2011-12-26
Hello: I'm running Ubuntu 11.10. I used to be able to connect to shared folders and printer but now I cannot. The only changes to my system are from Ubuntu updates recently downloaded.

My setup for using a shared printer looks like this: linux>wlan0>windowsXP>printer

On my Ubuntu desktop, if I go to  Places > Network > Windows Network, I can see the 'WORKGROUP' and the computers that are connected to it including the windowsxp with the printer. But I cannot connect to it any more.

One of the computers in the WORKGROUP (a laptop also running windowsxp) connects without a problem (laptop>wlan0>windowsXP>printer = no problem)

I've tried using system-config-printers but no luck. Frustration is starting to set in. Any suggestions are appreciated.

Lux

---

### Post by 2F4U on 2011-12-26
Can you ping the Windows machine from the Ubuntu machine? Did you try to acess the machine from Nautilus using the smb://ip_address notation?

---

### Post by lux11 on 2011-12-26
> **2F4U said:**
> Can you ping the Windows machine from the Ubuntu machine? Did you try to acess the machine from Nautilus using the smb://ip_address notation?
Thanks for the quick reply and for the access tip using Nautilus. That worked. 

Now I can see the shared folders but I cannot find the shared printer.

If I try using gnome-control-center / add a new printer / network I get this message," FirewallD is not running. Network printer detection needs services mdns, ipp, ipp-client and samba-client enabled on firewall." 

So I'm getting warm but gnome-control-center isn't helping much. More ideas are welcome and thanks again for your time.

---

### Post by lux11 on 2011-12-26
SOLVED =D>

NOTE TO SELF:

in nautilus terminal: system-config-printer
   Add - Network Printer - Windows Printer via SAMBA - [then...}
enter smb://[IP address of the windowsXP machine]/[printer name as listed on the Windows machine]
then >Forward
prompt for printer driver
once that's done, printed a test page and voila !

FOOTNOTE:
Application/System Tools/System setting/printer was useless
SAMBA works but took some trial and error

---

### Post by URGettingADull on 2012-01-24
Thank you for posting this, running system-config-printer was what I needed to connect to the Windows connected printer here at the house, theprinter utility in 11.10 is rubbish

---

### Post by vivekjustthink on 2012-10-20
Thank Your Very much lux. your info was very useful to solve my prob. :P

> **lux11 said:**
> SOLVED =D>

NOTE TO SELF:

in nautilus terminal: system-config-printer
   Add - Network Printer - Windows Printer via SAMBA - [then...}
enter smb://[IP address of the windowsXP machine]/[printer name as listed on the Windows machine]
then >Forward
prompt for printer driver
once that's done, printed a test page and voila !

FOOTNOTE:
Application/System Tools/System setting/printer was useless
SAMBA works but took some trial and error

---

### Post by lux11 on 2012-10-21
> **vivekjustthink said:**
> Thank Your Very much lux. your info was very useful to solve my prob. :P

vivekjusthink...you are quite welcome. 

Recently, I changed my ISP and had to purchase a new router to accommodate the fiberoptic cable. That lead me to have to reset my linux>wlan0>windowmachine>printer configuration. I was glad to find my notes from this post to use as a guide. Once I set up things like printers...and they work...I tend to forget the details of how I got it set up in the first place. Nice to have ubuntuforums as a resource for sure.
~Ken

---

