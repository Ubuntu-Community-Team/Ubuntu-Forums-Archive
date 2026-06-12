---
title: "lirc MCE configuration"
date: 2011-10-12
forum: Multimedia Software
---

### Post by Bradburts on 2011-10-12
Hi,
I have Ubuntu Server 11.04. I have lircd 0.8.7.
My lircd.conf files is:- "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"
 
The configuration seems mostly OK. The alphanumeric characters seem OK.
The multimedia keys do not all work. 
Using irw I see escape codes '[14' etc when using volume down. Volume up is blank.
I had expected to see hex code, not character sequences. 
In mplayer I can jump back but pause does not work.
 
My remote is labeled as supporting Windows 2000, XP, MCE & VISTA. Here's the remote:- 
[http://www.amazon.co.uk/gp/product/B001M56DI0](http://www.amazon.co.uk/gp/product/B001M56DI0)
 
How do I figure out which configuration I should be using or how do I make a configuration? 
Alternatively I am happy to be pointed to a cheap amazon remote which will work!
 
EDIT:
When I use irrecord I do not get dots. I get the characters from the alphanumeric pad or I get escape codes. After 10 seconds irrecord times out.
 
EDIT:
lsusb
[FONT=Times New Roman, serif][SIZE=3]Bus 005 Device 002: ID 073a:2230 Chaplet Systems, Inc[/SIZE][/FONT]
 
I am wondering if LIRC is handling this device.

---

### Post by Bradburts on 2011-10-13
Anyone?
I am now fairly convinced that the IR remote is being treated as a keyboard and mouse by Ubuntu & LIRC is not getting a look in.
Spent quite a few hours on this, have googled a load but no joy :(.
If the remote is being treated as a keyboard then maybe I can change the keyboard type?
 
 
I just need the standard media buttons to work. Doesn't matter if thats Ubuntu or LIRC.
The remote works fine in Windows 7.
I would also be happy with links to cheap remotes which do work.
Have tried the LIRC pages but I cannot find stock for the remotes listed. 
 
Anyone recently buy a remote & receiver which works with Ubuntu server 11.04 or 10.04 ?
 
EDIT:
Learning a lot more about devices, slowly:-
 
Pull & fit the dongle:
[ 5016.870029] usb 5-1: new low speed USB device using uhci_hcd and address 3
[ 5017.112065] usb 5-1: config 1 interface 0 altsetting 0 has 2 endpoint descriptors, different from the interface descriptor's value: 1
[ 5017.155276] input: HID 073a:2230 as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input6
[ 5017.155858] generic-usb 0003:073A:2230.0003: input,hidraw1: USB HID v1.10 Keyboard [HID 073a:2230] on usb-0000:00:1d.3-1/input0
 
cat /proc/bus/input/devices
I: Bus=0003 Vendor=073a Product=2230 Version=0110
N: Name="HID 073a:2230"
P: Phys=usb-0000:00:1d.3-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input6
U: Uniq=
H: Handlers=sysrq kbd mouse0 event4 js0
B: PROP=0
B: EV=10001f
B: KEY=837fff002c3027 bf00444400000000 fffffffffffff 10c040b27c007 ffa67bfad941dfff febeffdfffefffff fffffffffffffffe
B: REL=343
B: ABS=100030000
B: MSC=10
 
So I figure the device is being treated as a keyboard & LIRC is not playin at all. Could I try & correct the keyboard type? Any suggestions plz!
 
EDIT (again):
Learning even more:
cat /dev/input/event4 | hexdump
 
shows that I have codes comming through with the 'missing' keys.
So I just need to correct the keyboard mapping or get rid of the keyboard and get LIRC hooked in. Or buy a working remote!
 
EDIT (some more)
Can only find details of [FONT=Courier New]xmodmap [/FONT]which needs a window to work, no good on Ubuntu server.

---

### Post by Bradburts on 2011-10-14
From what I can understand my MCE remote appears as a HID device as keyboard & mouse.
The MCE remote does not get picked up by LIRC.
The regular keys all seem to work. 
Some of the multimedia keys do not send keycodes (AFAIK) & some appear to send the wrong keycodes.
I can identify the device in /dev/input and can throw some code together to monitor events, say /dev/input/event4.
I can access the keypress events so I should be able to detect each key. I will then be able to program responses to keycode. 
I am new to the liniux device model and am not quite clear on what the various devices represent, what its supposed to do, data formats etc. The event code is 24 bytes & so that will take a little research.
 
My hope was that as there are events for the missing key presses then someone could show me a simple, headless, way to add the event code to a keyboard map. 
I am also stuck on how to unhook the HID MCE keyboard/mouse from the system such that the wrong keycodes do not get sent. Perhaps if I read the device the handlers will not happen. If so that would unhook the wrong key code but also I would loose the good working alpha keys and I will then have to figure out their codes as well.
 
I cannot help but think that this is way to complicated and that I am making some newbie mistakes. 
Does anyone else have a working MCE remote which they could give a UK amazon link to?
Or just knowing that, yes this is what its like would help!

---

### Post by s13_mills on 2011-10-23
Do you have ir-keytable installed? If so, you an change the key presses that the remote codes correspond to, and get rid of the escape codes.

I have had success using LIRC only and more recently ir-keytable with LIRC to get remote controls to work, it can be a bit painful, but generally if you get a response of any kind you can get it to work!

If you want to try ir-keytable, you can use 

```
sudo ir-keytable -t
```

And press the buttons to get the scan codes, I prefer it to irrecord, seems to get some things that irrecord misses.

Once you know the codes you can change the key press it corresponds to - prob easier to google ir-keytable than me explain it!

Hope this helps!

---

