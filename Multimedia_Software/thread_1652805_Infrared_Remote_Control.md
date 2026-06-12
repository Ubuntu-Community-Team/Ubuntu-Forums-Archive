---
title: "Infrared Remote Control"
date: 2010-12-25
forum: Multimedia Software
---

### Post by JonasDK on 2010-12-25
Hello everyone

I've soldered my own USB-infrared receiver and it works! If I use the command "screen /dev/ttyACM0 9600" in my terminal I can receive signals from my TV-remote. I get a different character when I press a different button in my terminal. But now I want to control these signals.

So I've installed 'Infrared Remote Control' from the Ubuntu Software Center. It detects my homemade receiver nicely. But I cannot configure the remote...
My brand of remote is not in the list (Loewe Control 150 TV remote) so I chose Unknown. When I click 'detect' to detect the settings of my remote on the 'Basic Configuration'-tab it gives a 'Could not initialize hardware'-error right away. It complains about 'Remote control daemon not running'.

Is there something I haven't installed or something? Because it doesn't even TRY to detect anything. It just stops right away.

Anyone who knows more about this?
Thank you very much!
Jonas

---

### Post by JonasDK on 2010-12-26
I have found this website: [http://live.gnome.org/gnome-lirc-properties](http://live.gnome.org/gnome-lirc-properties)
I did 
```
lshal --monitor --long
```in my terminal and this is what I received when connecting my IR-receiver:
```
*** 19:45:02.210: lshal: device_added, udi='/org/freedesktop/Hal/devices/usb_device_4d8_a_noserial_if0_serial_unknown_0'
  info.capabilities = {'serial', 'modem'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_4d8_a_noserial_if0'  (string)
  info.product = 'Serial Port'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_4d8_a_noserial_if0_serial_unknown_0'  (string)
  linux.device_file = '/dev/ttyACM0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/tty/ttyACM0'  (string)
  modem.command_sets = {'V.250'} (string list)
  serial.device = '/dev/ttyACM0'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/usb_device_4d8_a_noserial_if0'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'unknown'  (string)

```Should I build a custom logfile for lirc to make it communicate or something?

---

