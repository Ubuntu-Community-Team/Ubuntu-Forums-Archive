---
title: "Dapper Kills Wireless"
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by Hygelac on 2006-06-02
I have an HP zv6000 with a Broadcom wireless card.  It ran fine (with ndiswrapper) under Kubuntu Breezy; I used the instructions here (at the bottom of the page): [https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsHewlettPackard](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsHewlettPackard).  Now I have done a clean install of Dapper and I cannot activate the card (by the same method).  It sees the card as 'eth0' (with the wired card as 'eth1;' Breezy saw the wireless as 'wlan0' and the wired as 'eth0'); might that be causing the problem?  I heard someone say that Dapper's kernel loaded some kind of "dodgy" Broadcom module that has to be disabled (I do not know anything more detailed than this) for ndiswrapper to work; does anyone know how to do this?  I really need help here; I don't want to revert to Breezy after nuking it... :confused:

EDIT: If I type "sudo ifconfig eth0 up" it says "SIOCSIFFLAGS: No such file or directory" and if I type "sudo ifconfig wlan0 up" it says "wlan0: ERROR while getting interface flags: No such device."

---

### Post by Metro on 2006-06-02
I had a laptop working great with my network that have wap and wep protection but after update to kernel 686 stop working:(

---

### Post by skb on 2006-06-03
> **Hygelac]I have an HP zv6000 with a Broadcom wireless card.  It ran fine (with ndiswrapper) under Kubuntu Breezy said:**
> https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsHewlettPackard[/url].  Now I have done a clean install of Dapper and I cannot activate the card (by the same method).  It sees the card as 'eth0' (with the wired card as 'eth1;' Breezy saw the wireless as 'wlan0' and the wired as 'eth0'); might that be causing the problem?  I heard someone say that Dapper's kernel loaded some kind of "dodgy" Broadcom module that has to be disabled (I do not know anything more detailed than this) for ndiswrapper to work; does anyone know how to do this?  I really need help here; I don't want to revert to Breezy after nuking it... :confused:

EDIT: If I type "sudo ifconfig eth0 up" it says "SIOCSIFFLAGS: No such file or directory" and if I type "sudo ifconfig wlan0 up" it says "wlan0: ERROR while getting interface flags: No such device."


Do you know which Broadcom chipset your card uses? If it's a BCM43xx based card you can manually extract the firmware from the Windows driver by using a utility called bcm43xx-fwcutter, and copy it to your /lib/firmware directory.

I've got a tutorial on how I did this here:

[http://www.ubuntuforums.org/showthread.php?t=186538](http://www.ubuntuforums.org/showthread.php?t=186538)

You'd want to use the steps on downloading and using fwcutter, and skip the NDIS stuff. :)

Hope this helps.

--skb

---

### Post by mike983 on 2006-06-03
I have the same problem with a HP Pavilion zd8000.

---

### Post by mike983 on 2006-06-03
Whit this procedure is all ok!!!!!!!!!!!!!

[http://www.ubuntuforums.org/showthread.php?t=186538](http://www.ubuntuforums.org/showthread.php?t=186538)

Thanks skb!!!!!!!!!!!!!!!!!!!

---

### Post by Hygelac on 2006-06-03
It runs!  I wasn't on the forums until I got the wireless running just a moment ago.  I used the wonderful fwcutter as explained here: [https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx).  I guess this will be useful for Debian Etch too, won't it?  Thanks everyone! \\:D/  Next step is to get DHCP working again...

P.S.: My Broadcom chipset is 4318.

---

