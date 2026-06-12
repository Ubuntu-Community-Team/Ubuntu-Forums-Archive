---
title: "Kazam Sound recording issues"
date: 2014-07-02
forum: Multimedia Software
---

### Post by seanmancini2010 on 2014-07-02
Hey Everyone,

I just upgraded my kazam screen caster install I was able to record audio before 

I am now unable to record audio I do see that a option was removed from the new version where I can select my input device

I do see that my usb headset is recognized and the output audio is working and the mic seems to be picked up by the sound manager



Here is the output from dmesg for my headset

[88698.407507] usb 4-3: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[88698.407512] usb 4-3: Product: C-Media USB Headphone Set  
[88698.565373] input: C-Media USB Headphone Set   as /devices/pci0000:00/0000:00:13.0/usb4/4-3/4-3:1.3/input/input21
[88698.565702] hid-generic 0003:0D8C:000C.0006: input,hidraw1: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-0000:00:13.0-3/input3


I have also included screen shots any help or ideas would be awesome !

---

### Post by seanmancini2010 on 2014-07-02
Also See the output from kazam 



(kazam:2751): Gtk-WARNING **: Can't set a parent on widget which has a parent




(kazam:2751): Gtk-WARNING **: Can't set a parent on widget which has a parent


Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/kazam/app.py", line 553, in cb_record_clicked
    self.run_counter()
  File "/usr/lib/python3/dist-packages/kazam/app.py", line 802, in run_counter
    self.countdown = CountdownWindow(self.indicator, show_window=prefs.countdown_splash)
  File "/usr/lib/python3/dist-packages/kazam/frontend/window_countdown.py", line 71, in __init__
    self.setupPixman(LIBPIXMAN_NAME)
  File "/usr/lib/python3/dist-packages/kazam/frontend/window_countdown.py", line 122, in setupPixman
    libpixman = cdll.LoadLibrary(name)
  File "/usr/lib/python3.4/ctypes/__init__.py", line 429, in LoadLibrary
    return self._dlltype(name)
  File "/usr/lib/python3.4/ctypes/__init__.py", line 351, in __init__
    self._handle = _dlopen(self._name, mode)
OSError: libpixman-1.so: cannot open shared object file: No such file or directory

---

