---
title: "Internet GONE !URGENT!"
date: 2013-07-01
forum: Networking &amp; Wireless
---

### Post by RonanZer0 on 2013-07-01
OK... I recently replaced Win7 with Ubuntu so for some reason Linux is just generally bad with internet, first of all, steam download limit is capped at 1,024 KB/s, pages load slower etc. I'm NOT on wireless, I'm on wired. Already tried many threads still don't help with steam (Works 100% lightning bolt fast on windows 7, windows 7 speedtest.net says I have 30mbp/s, while on Ubuntu it says I have only like 20 or sometimes even 15 mbp/s)
anyways now on to the "unfixable" problem:
my internet, I just suspened my thing and went to the logon thing and BAM top left corner "Disconnected"
Sure it's not my PC as when going into LIVE mode it works fine (thats how im posting this) nothing i did before that randomly stopped. Tried rebooting, looking it up etc. all I get is
people saying it drops out at random times not totally off... However a little bit before that I followed this thread: [http://ubuntuforums.org/showthread.php?t=1955569](http://ubuntuforums.org/showthread.php?t=1955569) and after following wild man's commands it started working a bit faster... but not perfect. anyways I didn't do much after that just try to install GMOD on steam... then suspended and you know the rest. Please help!


Ubuntu 13.04 64-BIT

(router is a netgear, has nothing to do with this though as it works lightning fast on win7)

---

### Post by RonanZer0 on 2013-07-01
"iptables -I OUTPUT -d 195.246.243.165 -j REJECT"
I actually did that too a bit before it happened. How do I undo it?
please this is URGENT

---

### Post by s1baker on 2013-07-01
I don't know that much about networking, but you may want to try to post this
in the Networking & Wireless forum.

---

### Post by Irihapeti on 2013-07-02
*Thread moved to **Networking & Wireless**.*

---

### Post by chili555 on 2013-07-02
> I just suspened my thing and went to the logon thing and BAM top left corner "Disconnected"Sometimes when you suspened your thing, the internet doesn't resume when the computer resumes because the wireless driver drops. Often it is as simple as re-loading the driver and writing one file to get the driver to reload automatically on resume. Do you know what your driver is? Let's find out by opening a terminal and running and posting:```
lspci -nn | grep 0280
lsusb
```Thanks.

---

