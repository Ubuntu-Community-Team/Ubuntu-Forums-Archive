---
title: "MCE eHome remote, how to get button press to generate key stroke?"
date: 2012-07-07
forum: Mythbuntu
---

### Post by declanmullen on 2012-07-07
Trying to get a eHome MCE remote working with Mythtv frontend without using LIRC. Taking approach of using Mythtv Frontend's key mapping (Setup->Edit Keys) to define what myth action each button performs. I've had success with mapping some of the buttons. Eg 
The Play action was already mapped to the <Ctl>+P key. I then selected the Edit Key's next available key field for this action and when prompted pressed the remote's Play button. The button press was recognised as the "Play Media" key. The Edit Keys prompt captured the "Play Media" key and mapped it to the Play action. So now, I can get Myth to play by either pressing <Ctl>+P on the keyboard or pressing the remote's Play button.

However some of the remote's buttons don't seem to generate a key. Eg When I'm trying to map the remote's Red button to the myth Delete action, when I press the Red button at the Edit Key's prompt, the prompt fails to detect that there has been any key pressed at all.  

Using ir-keytable -t proves that all the remote's buttons are generating scancodes. Eg pressing the Red button generates the following output:
```
root@pvr:~/mce# ir-keytable 
Found /sys/class/rc/rc0/ (/dev/input/event6) with:
        Driver mceusb, table rc-rc6-mce
        Supported protocols: NEC RC-5 RC-6 JVC SONY LIRC other 
        Enabled protocols: NEC RC-5 RC-6 JVC SONY LIRC other 
        Repeat delay = 500 ms, repeat period = 125 ms

root@pvr:~/mce# ir-keytable -t -d /dev/input/event6
Testing events. Please, press CTRL-C to abort.
1341636662.131471: event MSC: scancode = 800f045b
1341636662.131478: event key down: KEY_RED (0x018e)
1341636662.131480: event sync
1341636662.382230: event key up: KEY_RED (0x018e)
1341636662.382233: event sync

```

I'm running Kubuntu 12.04 x86 32bit with its myth 0.25

How do I configure Kubuntu to generate a particular key stroke for a particular button press so that myth Edit Keys prompt can detect the key stroke ?
     
Do I use xmodmap ? If so what would be the xmodmap syntax to get the above Red button (scancode 800f045b) to generate a recognised key stroke (eg the letter 'D') ? Or should I use another tool to reconfigure Kubuntu ?

Remote's section in /proc/bus/input/devices: 
```
I: Bus=0003 Vendor=147a Product=e03a Version=1201
N: Name="Media Center Ed. eHome Infrared Remote Transceiver (147a:e03a)"
P: Phys=usb-0000:00:12.1-3
S: Sysfs=/devices/pci0000:00/0000:00:12.1/usb5/5-3/5-3:1.0/rc/rc0/input6
U: Uniq=
H: Handlers=kbd event6
B: PROP=0
B: EV=100013
B: KEY=fff 0 0 200 108fc32e 2376051 0 0 0 7 158000 4192 4001 8e9680 0 0 10000000
B: MSC=10

```
Many thanks,
Declan

---

### Post by declanmullen on 2012-07-07
After researching xmodmap a bit, it seems my issue is that some of the remote's buttons are generating keycodes greater than 255 (0xff) and X11 cannot handle those, and that is why myth is not seeing those button presses. Eg the above Red button generates a key code of 398(0x18e).

However one can work around the issue by using the evroute utility to remap such high keycodes to a keycode less than 255. See [http://www-user.tu-chemnitz.de/~klada/?site=projects&id=logitechkbd]("http://www-user.tu-chemnitz.de/~klada/?site=projects&id=logitechkbd")

---

