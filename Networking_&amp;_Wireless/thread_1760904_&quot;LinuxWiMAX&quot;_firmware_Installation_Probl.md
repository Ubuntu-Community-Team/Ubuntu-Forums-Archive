---
title: "&quot;LinuxWiMAX&quot; firmware Installation Problem"
date: 2011-05-17
forum: Networking &amp; Wireless
---

### Post by blitzkrieg92 on 2011-05-17
Hello everyone
I'm a new member of ubuntu forums (as well as linux). Earlier this year, I switched from windows to Ubuntu 10.10. But I'm not getting along with it as well as I expected I would :( Specially cause I'm not getting the best out of it due to limited web connectivity. I used to use a usb WiMax modem back in windows (which is also supposed to be supported by linux as my service provider said) for internet. But I'm having a hard time configuring it on my Ubuntu. The modem works fine but I'm failing to install the drivers (From [http://www.linuxwimax.org](http://www.linuxwimax.org)). I used my cell as a temporary modem to get help from the web.

I downloaded:-
i2400m firmware 1.5.0
WiMAX Tools 1.4.5
WiMAX Network Service 1.5.2


According to the documentation, I'm supposed to install the linux kernel 2.6.35 which Maverick comes with anyway.
Then comes the part to install the firmware. The command I used was
```

cd '/home/morshed/Desktop/max/i2400m-fw-1.5.0'

sudo install -o root -g root -m -644 i2400m-fw-usb-1.5.sbcf /lib/firmware
sudo install -o root -g root -m -644 i6050-fw-usb-1.5.sbcf /lib/firmware

```But unfortunately and annoyingly the result is
```
install: invalid mode `-644'
```
I didn't get it. Am I missing any package or something? :confused:
Please give me any suggestions if you have. Like I said, I'm new to linux, so please be a little descriptive :)
Thanks in advance

---

### Post by chili555 on 2011-05-17
I know nothing about Wimax, but I believe it's really supposed to be:```
sudo install -o root -g root -m 644 i2400m-fw-usb-1.5.sbcf /lib/firmware
sudo install -o root -g root -m 644 i6050-fw-usb-1.5.sbcf /lib/firmware
```That is, without the little minus before 644. Please try it.

---

