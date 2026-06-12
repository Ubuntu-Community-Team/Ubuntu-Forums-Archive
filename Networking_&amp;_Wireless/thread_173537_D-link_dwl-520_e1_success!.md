---
title: "D-link dwl-520 e1 success!"
date: 2006-05-10
forum: Networking &amp; Wireless
---

### Post by ouroboros1827 on 2006-05-10
Switching my mom's computer from slackware 10.2 to ubuntu 5.10, my main issue was getting the cheapo wireless working again. I moved the box to an ethernet landline, and followed all of the directions listed [here]("https://wiki.ubuntu.com/WifiDocs/Device/DWL-520vE1"). This is for 5.04, but I assume that doesn't really matter. I had trouble loading the firmware, and google searches didn't find much recent info. I really do not know how well that works.

So, I went back to what I had been using on slackware, linux-wlan-ng - they're generally considered outdated and inferior to hostap, but....they work. I can set them up, and it's not hard. 

If you have a dwl-520 e1 and don't mind using linux-wlan-ng, this is for you, keep reading.

What I did:
Pre-install: I wiped hostap and orinoco from my system as best I could. I put 'orinoco', 'orinoco_pci', 'hostap', and 'hostap_pci' in /etc/hotplug/blacklist as to avoid issues with those. To avoid bootup lag resolving the ntp server (time sync), I disabled eth0 (Network -> Properties, uncheck the box).

[LIST=1]
[*]Get the tarball from [ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/](ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/) - I used 0.2.3. Have the readme open, most of install is in there.
[*]Untar it, cd into it, make config (say y to pci), make, make install (I had to install gcc-3.4 after screwing around with my hostap gcc, I don't know if it's installed by default but make config wants gcc-3.4 installed -> landline needed)
[*]modprobe prism2_pci
[*]wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
[*]wlanctl-ng wlan0 lnxreq_autojoin ssid=<your APs SSID, I put linksys> authtype=opensystem
[*]dhclient wlan0 (for dhcp only, use ifconfig for static)
[/LIST]

To get connected on every reboot, nano /etc/init.d/linux-wlan-ng, and put steps 3 - 6 into it, line by line. ctrl-o, ctrl-x, chmod +x /etc/init.d/linux-wlan-ng, and finally update-rc.d linux-wlan-ng defaults

That's it. I'm not going to make a wiki or post this anywhere else, do what you want. This card is not incompatible with linux, it's really not hard with linux-wlan-ng. Thanks for reading! :-D

---

### Post by Protoss on 2006-05-20
Hey great job on finding a shorter, and less complicated way of getting this card working with Ubunutu. I somehow got this method to work on Kubuntu 5.10 x64, but couldn't do it again on Ubuntu Dapper Drake 32bit. What do I need to point it to when it asks for the kernel source tree? Do I need to symlink anything? 

UPDATE: I've gotten it to make and make install perfectly. Problem now is there isn't a wlan0 interface. I have not the slightest clue as to what to do now. 
Here is what I found in /var/log/dmesg
> [4294691.111000] hfa384x_corereset: corereset: Timed out waiting for cmd register.
[4294691.111000] prism2sta_probe_pci: prism2_pci: hfa384x_corereset() failed.
[4294691.121000] ACPI: PCI interrupt for device 0000:02:09.0 disabled
[4294691.121000] prism2_pci: probe of 0000:02:09.0 failed with error -5


Thnx, Protoss

---

### Post by This_is_me on 2006-06-08
I'm using Xubuntu Dapper 32bit. When I type "wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable" it tells me
```
message=lnxreq_ifstate
  ifstate=enable
  resultcode=implementation_failure
```
and dmesg says this:
```
[  591.999359] hfa384x_docmd_wait: hfa384x_cmd timeout(1), reg=0x8000.
[  591.999746] hfa384x_drvr_start: Initialize command failed.
[  592.000082] hfa384x_drvr_start: Failed, result=-110
[  592.000360] prism2sta_ifstate: hfa384x_drvr_start() failed,result=-110
```

I'm using the same card, the DWL-520 revision E1. I had this driver working under Debian at one point last year, but I wasn't having this problem then.
Should I try an older version of the driver, or is the problem with Ubuntu?

---

### Post by greenwom on 2006-06-10
I followed the Wiki and it worked great the trick was the .hex firmware file listed in the wiki is wrong.  It was somthing like **103 when the last digit should have been a 4.  

I was cutting and pasting the instructions and it didn't work until I changed the digit :) silly.  Other than that it was easy.....  

now I'm getting ready to do upgrade to dapper and I want to make sure I don't mess up Host-Ap...  I'm wondering if I do a dist-upgrade will It all get messed up?

---

