---
title: "RaLink RT2860 card not found"
date: 2011-08-06
forum: Networking &amp; Wireless
---

### Post by akshay2419 on 2011-08-06
#nm-tool
# lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:dab00000-dab0ffff

suggest me how to activate my wifi card???

---

### Post by b3organ on 2011-08-18
Same problem here. My wireless card (asus pce n-13, with rt2860 chip?) worked straight away after 10.10 installation but for some reason I tested 10.04-3 and wireless networking disappeared. I reinstalled 10.10 but the wireless remains "dead".

I'm not able to post all the data now (because I'm on other cpu) but the lspci finds the card and that lshw-method results similar findings than above (unclaimed network). iwconfig doesn't show the card (no wireless extensions).

And I have tested that method to install and compile driver manually but when I reach the steps that include "ifconfig wlan0 down" for example it's not working because I don't have "wlan0" device present.

Thanks if somebody wishes to help.

---

### Post by cottfcfan on 2011-08-18
Following post 1 in the following thread worked perfectly for me in 10.04-3, and for some on 10.10. In 11.04 it works out of the box.
[http://ubuntuforums.org/showthread.php?t=1476007&highlight=rt2860sta](http://ubuntuforums.org/showthread.php?t=1476007&highlight=rt2860sta)

---

### Post by b3organ on 2011-08-18
Thanks for reply but that is the method I've tried but with no success. Glad to hear 11.04 works. Maybe I'll install that.

---

### Post by TBABill on 2011-08-18
If you open a terminal do you see more than one driver present when you run ```
lsmod
``` that appears to be related? They will all start with rt, such as rt2x00pci, rt2800pci, etc. If you do, then it may just be a matter of blacklisting the conflicting drivers to get it up and running.

---

### Post by b3organ on 2011-08-18
> **TBABill said:**
> If you open a terminal do you see more than one driver present when you run ```
lsmod
``` that appears to be related?  Nothing related there. Only usbhid, hid, ahci, licahci and pata_atiixp.

---

### Post by TBABill on 2011-08-18
What happens if you ```
sudo modprobe -r rt2860sta
``` and then ```
sudo modprobe rt2860
``` If you wait for a minute does it change anything?

---

### Post by b3organ on 2011-08-18
> **TBABill said:**
> What happens if you ```
sudo modprobe -r rt2860sta
``` and then ```
sudo modprobe rt2860
``` If you wait for a minute does it change anything?

FATAL: Could not load /lib/modules/2.6.38.10-generic/modules.dep: No such file or directory

E: I'm able to get that LINUX-cpu online after couple hours. Then I try this: [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847) , seems legit.

---

### Post by cottfcfan on 2011-08-18
I think the problem might be the kernel you're using.
The 2.6.38 kernel is from Natty.
It installs in 10.04-3 using the stock 2.6.32 kernel & in 10.10 using the 2.6.35 kernel.
If you go back to the correct kernel for the distro you're using, you might find the above instructions work.

---

### Post by TBABill on 2011-08-18
It could also be all the changes you introduced attempting to get it working by downloading the driver and building the module. The stock kernel modules work fine for your chip, but I am not sure what state  your machine is in at this point following the changes you attempted.

---

### Post by cottfcfan on 2011-08-18
Sorry.. Ignore in wrong thread.

---

### Post by b3organ on 2011-08-19
You're both right I believe. Because of "wrong" kernel those instructions fail. Today I try to install 11.04 and hope wireless will work.

---

### Post by b3organ on 2011-08-20
I have had bad luck with installations but for a while it seemed that with "old" kernel and 10.04-3 is was able to find wireless device with iwconfig that I wasn't before. For now, my system refuses to boot but that is handled in another thread.
 
I'll report the end of my story here if I remember but so far it seems that you're able to get a working wireless with linked instructions if you have kernel that "matches".

---

### Post by chili555 on 2011-08-20
> **TBABill said:**
> What happens if you ```
sudo modprobe -r rt2860sta
``` and then ```
sudo modprobe rt2860
``` If you wait for a minute does it change anything?I believe it's rt2860[COLOR="Red"]sta[/COLOR].

---

