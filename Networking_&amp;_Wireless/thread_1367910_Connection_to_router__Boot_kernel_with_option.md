---
title: "Connection to router / Boot kernel with option"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by Benj_C on 2009-12-30
Hi,

I just installed Ubuntu 9.10 on my Dell Inspiron 710m (wi-fi card: Broadcom). And if Ubuntu manages to connect to my Wi-Fi network, the internet does not work. I've got a signal, Ubuntu tells me it's connected but Firefox don't show any page (the wired connection works though). 

I found that page on the Ubuntu help:
[https://help.ubuntu.com/9.10/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/9.10/internet/C/troubleshooting-wireless.html)
and thought that the section "Check for a connection to the router" was relevant to my situation. I do get an ESSID corresponding to the name of my network. Therefore I believe I just have to boot the kernel with this additional option.

First question: Am I on the right track?

If I am, my second question is: How am I supposed to do that without a file /boot/grub/menu.lst? All the info I found about modifying the boot options use the same strategy: modfy "menu.lst". But I can't even find that file!!
Any idea?

Thanks,

Ben

---

### Post by puppywhacker on 2009-12-30
I think you do not need to add a kernel option pci=noacpi to get your connection to work.

if you run iwconfig and you don't find your ESSID, but you can see the ESSID at iwlist scanning, then you can set connect to your essid with iwconfig wlan0 essid abcde (ofcourse replace abcde with your essid name)
```

iwconfig
iwlist scanning
iwconfig wlan0 essid abcde
```

Then check with ifconfig if you received an ip address from your router with ifconfig and if you do not have an "inet" then you can try to fetch an ip address with dhclient
```

ifconfig wlan0
dhclient wlan0

```

---

### Post by Benj_C on 2009-12-30
Thanks for your reply.

I do have the correct ESSID. And this is what I get with iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:"xxxxxxxxx"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

However, when I try iwlist, I don't get much results:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results


I tried dhclient, but after several attempts it gave up. Any idea?

Best,

Ben

---

### Post by puppywhacker on 2009-12-30
Hi, you don't need to mess around the ACPI or the boot menu.

```
eth1 radio off ESSID:"xxxxxxxxx"
```

Your radio part is switched off. There could be a "kill switch"-button or an  "FN-key + F7" (or something around it) (I've never seen your laptop, so you'll be the eyes)
```

Mode:Managed Channel:0 Access Point: Not-Associated 
```

Once that is enabled you should find that you don't use the non-existent channel 0 anymore and your access-point should be associated

---

### Post by Benj_C on 2009-12-30
Awesome! Thanks a lot for your help!

---

