---
title: "WiseCom USB 56k modem not found"
date: 2006-02-27
forum: Networking &amp; Wireless
---

### Post by Garyu on 2006-02-27
I couldn't help but spread my joy over Ubuntu to my ex girlfriend, so I forced her to accept my help in installing Ubuntu Breezy on her computer. And of course, she actually accepts it and already considers it nicer than windows even though she is at a very basic user level. :cool:

One problem though. She has an old WiseCom WS-5614UVSG modem used to connect to the Internet. When I installed Ubuntu on her machine, I brought it home to my place where I have ethernet broadband connection. So I installed everything and downloaded lots of nice stuff with Synaptic, amongst other things gnome-ppp. Then I brought the computer back to her place and plugged in the modem, started gnome-ppp and set the modem to /dev/modem. BUT then I get the message that there is no /dev/modem (or modem not available or found or whatever, I'm at my place now so I don't know). Tried searching the forums/wiki, but I only find info on ADSL modems and this is a regular 56k modem.

Any ideas as to what I should try to do and fix this? I can't download anything off the 'net since the modem is down so I just have to hope I installed everything. Unless I can download stuff at my place and then bring it by CD or USB-RAM to her computer...

---

### Post by Garyu on 2006-07-28
OK, just to let everyone know, I solved this issue:

First of all I upgraded my system to Dapper Drake 6.06

Then I downloaded this file:
[http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/slamr-2.6.15-23-386.tgz](http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/slamr-2.6.15-23-386.tgz)

Then I did this:
```

tar zxf slamr-*.tgz
cd slamr-2.6.15-23-386
sudo ./setup
sudo mknod -m 600 /dev/slusb0 c 243 0
sudo modprobe slusb
sudo slmodemd -c SWEDEN /dev/slusb0 &

```

Then I started Kppp and identified my modem easily. But as things are at this point I have to type that last line every time I want to use my modem, so I added this:

sudo gedit /etc/init.d/modem_starter
In that file add "sudo slmodemd -c SWEDEN /dev/slusb0 &" and save.

```

sudo chmod +x /etc/init.d/modem_starter
sudo update-rc.d modem_starter defaults

```

This will make it load every time at startup. :cool:

---

### Post by Garyu on 2006-07-28
Oh, and also, some complimentary info about my modem:

lsusb gives this result:
```
Bus 004 Device 003: ID 0483:7554 SGS Thomson Microelectronics 56k SoftModem

```

tail -f /var/log/messages &
```
[1] 17309
Jul 28 22:47:03 deepblue kernel: [4303931.990000] usb 4-1: USB disconnect, address 2
Jul 28 23:00:58 deepblue kernel: [4304767.128000] slamr: module license 'Smart Link Ltd.' taints kernel.
Jul 28 23:00:58 deepblue kernel: [4304767.131000] slamr: SmartLink AMRMO modem.
Jul 28 23:01:00 deepblue kernel: [4304768.441000] slamr: SmartLink AMRMO modem.
Jul 28 23:03:19 deepblue kernel: [4304907.506000] ST7554 USB Modem.
Jul 28 23:03:19 deepblue kernel: [4304907.507000] usbcore: registered new driver ST7554 USB Modem
Jul 28 23:11:25 deepblue kernel: [4305393.455000] usb 4-1: new full speed USB device using uhci_hcd and address 3
Jul 28 23:11:25 deepblue kernel: [4305393.596000] <6>slusb: slusb0 is found.
```

So the chip name is WS-5614UVSG; the lsusb gives hex identifier (0483:7554).

I tried with [http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/slamr-2.6.12-10-386.tgz](http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/slamr-2.6.12-10-386.tgz) when I was running Breezy Badger, but that did not work with this modem. But I can't say if it was a Breezy issue or a slamr issue or if I just screwed it up myself somehow. I also read about others that got this modem to work with slmodem-2.9.5 with slackware and suse. 

A big up to the ppl at linmodems. :cool:

---

