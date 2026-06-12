---
title: "iptables not loading"
date: 2011-03-09
forum: Networking &amp; Wireless
---

### Post by ant2ne on 2011-03-09
I've written a nice iptables script and put it in /etc/network/if-pre-up.d and /etc/network/if-up.d but it doesn't load the script on reboot. I figured on reboot the interfaces would come up and it loads the script. What is wrong with this reasoning? And what is the solution for loading iptables on boot up?

---

### Post by koszta on 2011-03-09
I know this is probably a stupid idea but why are you trying to put iptables firewall to interface up/down scripts? Why dont you just place your scripts in /etc/init.d and configure them with update-rc.d ? That is where you usually place your firewall scripts.. They will definitelly be run after boot if you configure them with update-rc.d ....

---

### Post by ant2ne on 2011-03-10
> **koszta said:**
> I know this is probably a stupid idea but why are you trying to put iptables firewall to interface up/down scripts? Why dont you just place your scripts in /etc/init.d and configure them with update-rc.d ? That is where you usually place your firewall scripts.. They will definitelly be run after boot if you configure them with update-rc.d ....[URL="https://help.ubuntu.com/community/IptablesHowTo"]
see solution 2[/URL]
This is how I want to do it. But it isn't working and IDK why.

---

### Post by gmargo on 2011-03-10
What is in your **/etc/network/interfaces** file for the interface you're interested in?

What filename does your script have?  The filename must be of a certain format or else it is ignored; see **run-parts( 8 )** man page.

---

### Post by ant2ne on 2011-03-15
```
ant2ne@rampart:/etc/network/if-pre-up.d$ ls -l
total 4
lrwxrwxrwx 1 root root   25 2011-03-02 09:05 hostapd -> ../../hostapd/ifupdown.sh
lrwxrwxrwx 1 root root   16 2011-03-07 10:08 iptables.sc -> /bin/iptables.sc
-rwxr-xr-x 1 root root 3839 2009-12-18 09:15 wireless-tools
lrwxrwxrwx 1 root root   32 2011-03-01 19:41 wpasupplicant -> ../../wpa_supplicant/ifupdown.sh
```iptables.sc is the script. What should it be named?

---

### Post by gmargo on 2011-03-15
Try **iptables-sc**.  (Look at all the other files in /etc/network/if-*.d/.  None of them use dots or underscores.)

---

### Post by ant2ne on 2011-03-16
i will try that and test it out this weekend. thanks

---

