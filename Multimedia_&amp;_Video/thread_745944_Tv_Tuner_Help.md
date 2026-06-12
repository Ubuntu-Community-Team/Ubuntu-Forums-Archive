---
title: "Tv Tuner Help?"
date: 2008-04-05
forum: Multimedia &amp; Video
---

### Post by ravindukelum on 2008-04-05
:confused:I got ASUS U3000 HYBRID ANALOG/DVB/RADIO USB tuner it's working in xp fine but in my main ubuntu 7.10 ,even dont't recognize the device when I plug the USB port from TV card to machine please help me to find a way to see TV on my loving ubuntu......:guitar:

---

### Post by xc3RnbFO8P on 2008-04-05
This TV tuner is supported by the kernel: [http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices#Asus_My_Cinema-U3000_Mini]("http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices#Asus_My_Cinema-U3000_Mini")

In Terminal (just copy/paste in to Terminal and <return>):
> sudo apt-get install mercurial linux-headers-$(uname -r) build-essential
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
> cd v4l-dvb
> make all
> sudo make install

Restart the computer.

> sudo apt-get install kaffeine

Start Kaffeine,  hopefully you can see the Digital TV button.
If not, show the output (in terminal):
> lsusb
and
> dmesg   (only copy/paste  -dvb-usb information)

---

