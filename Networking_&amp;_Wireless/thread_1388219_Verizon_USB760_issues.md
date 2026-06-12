---
title: "Verizon USB760 issues"
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by efriese on 2010-01-22
I'm able to get my Verizon USB760 using gnome-ppp using the instructions in this thread:[http://ubuntuforums.org/showthread.php?t=1002262&highlight=verizon+usb760](http://ubuntuforums.org/showthread.php?t=1002262&highlight=verizon+usb760)

Initially Network Manager could see the modem, but when I used it to connect it would drop connection. Now Network Manager won't even see the modem. Here's what I've done so far:

> sudo gedit /etc/udev/rules.d/70-persistent-cd.rules
find the line that contains "Novatel_Mass_Storage" and append the following to it:
RUN+="/usr/bin/eject %k"

save and close

sudo gedit /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
Add this in there:

<!-- Verizon USB760-->
<match key="@info.parent:usb.vendor_id" int="0x1410">
<match key="@info.parent:usb.product_id" int="0x6000">
<match key="@info.parent:usb.interface.number" int="0">
<append key="info.capabilities" type="strlist">modem</append>
<append key="modem.command_sets" type="strlist">IS-707-A</append>
</match>
</match>
</match> 

I'm using Ubuntu 9.10 x64. 

Any ideas why Network Manager no longer sees the modem?

---

### Post by pdc on 2010-01-23
what does 

> lsusb

show you in a terminal, with the device plugged in?

---

### Post by efriese on 2010-01-25
Bus 005 Device 003: ID 1410:6000 Novatel Wireless

---

### Post by pdc on 2010-01-25
> Any ideas why Network Manager no longer sees the modem?

No


the ID

> Bus 005 Device 003: ID 1410:6000 Novatel Wireless 

shows that the device has switched; 

If you type

> ls /dev/ttyUSB*

what do you get?

and what does 

> dmesg show

and > sudo tail -f /var/log/messages

after you plug the device in?

wvdial often seems successful at dialling; it may be an option

---

