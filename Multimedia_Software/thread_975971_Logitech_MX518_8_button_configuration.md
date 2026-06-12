---
title: "Logitech MX518 8 button configuration"
date: 2008-11-08
forum: Multimedia Software
---

### Post by Heojaua on 2008-11-08
Ok here we go. I just moved to ubuntu like 3 hours ago and im trying to fix my Logitech MX518 to work properly but im failing.

I want to bind my buttons ( +, -, wheel, back, forward and alt+tab button ) to other buttons like 123456.

I'm really new to Linux's world so i dont know any command or how the system works. I tried to look up on forums but i dont understand a single thing heh.

Thank you very much
Hoping an answer

new user, planning to stay on this platform =)

---

### Post by LycoLoco on 2008-12-02
You might wanna check out lomoco at [http://www.lomoco.org/](http://www.lomoco.org/). This is something that I've wanted from Linux for a long time and apparently lomoco will let you do this. I've actually deleted my Ubuntu partition at the moment but I think this has given me reason to try it out again :) Good luck!

---

### Post by tjvdberg on 2008-12-04
I've had a similar problem, I wanted to get the back and forward button to work in nautilus. After a lot of testing here's how I got it to work in Ubuntu 8.10. I'm not a linux expert and I collected this information from  of guides and posts on this forum and from google searching and some experimenting on my own. I don't know if this can damage your computer in anyway!

Install xvkbd and xbindkeys

```
sudo apt-get install xvkbd xbindkeys
```

Open a terminal and type:
```
cat /proc/bus/input/devices
```

You will get a list of differnt devices, look for something with Logitech USB-PS/2 Optical Mouse in it.

```
I: Bus=0003 Vendor=046d Product=c051 Version=0110
N: Name="**Logitech USB-PS/2 Optical Mouse**"
P: Phys=usb-0000:00:1d.2-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb3/3-2/3-2:1.0/input/input3
U: Uniq=
H: Handlers=mouse1 event3 
B: EV=17
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

```



Open another terminal and Backup and Edit xorg.conf

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
```
sudo gedit /etc/X11/xorg.conf
```

Insert this, and overwrite if necessary:

```
Section "InputDevice"
        Identifier    "Configured Mouse"
        Driver        "mouse"
    Option        "Protocol"        "evdev"
    Option        "Dev Name"        "Logitech USB-PS/2 Optical Mouse"
	[B]Option        "Dev Phys"        "usb-*/input0"
	Option        "Device"        "/dev/input/event3"[/B]     
    Option        "Buttons"        "10"
    Option        "ZAxisMapping"        "4 5"
EndSection 
```

(I'm not sure the underlining is necessary)
Look for this or similar **P: Phys=usb-0000:00:1d.2-2/input0** line in the other terminal and change the ***"Dev Phys"*** input[number] in the xorg.conf to match the terminal output.

Then look for this or similar **S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb3/3-2/3-2:1.0/input/input3** line and change the ***"Device"*** event[number] to match the terminal output (input3 = event3 in xorg.conf)

Save and quit.

Use 1 of the terminals to create .xbindkeysrc
```
gedit ~/.xbindkeysrc
```

insert: 
```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  b:9
```

I've only done the back, forard so buttons in nautilus so far, so I don't know the other functions yet, but they shouldn't be to hard to figure out I think.

save & quit

add xbindkeys to your system->preferences->sessions to startup xbindkeys.
Logout and login.

Good luck!

---

### Post by RaveJunkie on 2009-03-02
I have the same mouse and you reply help me get around in "explorer" much faster THANK YOU  PROPS!!!


tjvdberg   << thank you

---

### Post by steliyan on 2009-03-08
How can I remap left and right horizontal scroll to work as middle click? I'm using the "evdev" driver and as far as I know those buttons and axis mapping doesn't work with "evdev".

Edit: Here what's the output of xmodmap:
```
steliyan@debian:~$ xmodmap -e "pointer = 1 2 3 4 5 6 7 8 9 10 11 12"
Warning: Only changing the first 12 of 32 buttons.
steliyan@debian:~$ xmodmap -e "pointer = 1 2 3 4 5 6 7 8 9 10 11 11"
Warning: Only changing the first 12 of 32 buttons.
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  116 (X_SetPointerMapping)
  Value in failed request:  0xb
  Serial number of failed request:  9
  Current serial number in output stream:  9
```

---

