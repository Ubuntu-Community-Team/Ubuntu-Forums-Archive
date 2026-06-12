---
title: "Debugging lirc (nova-t usb remote)"
date: 2008-04-24
forum: Mythbuntu
---

### Post by tsh on 2008-04-24
I read ([http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-Stick](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-Stick))  that the remote for my USB device (which finally works OK after much digging around) is supposed to work.

I fall at the first hurdle, and need to know where to look:
```
grep -i dvb /proc/bus/input/devices
.. nothing...
```
```
grep -i dvb /var/log/syslog

Apr 24 23:28:43 desktop NetworkManager: <debug> [1209076123.071557] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_2040_7060_4028705256_dvb').
Apr 24 23:28:43 desktop NetworkManager: <debug> [1209076123.074363] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_2040_7060_4028705256_dvb_2').
Apr 24 23:28:43 desktop NetworkManager: <debug> [1209076123.084147] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_2040_7060_4028705256_dvb_0').
Apr 24 23:28:54 desktop kernel: [  147.652620] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
Apr 24 23:28:54 desktop kernel: [  147.693944] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-01.fw'
Apr 24 23:28:55 desktop kernel: [  148.043688] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
Apr 24 23:28:55 desktop kernel: [  148.043753] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Apr 24 23:28:55 desktop NetworkManager: <debug> [1209076135.222719] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_2040_7060_4028705256_dvb').
Apr 24 23:28:55 desktop NetworkManager: <debug> [1209076135.226620] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_2040_7060_4028705256_dvb_0').
Apr 24 23:28:55 desktop NetworkManager: <debug> [1209076135.230033] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_2040_7060_4028705256_dvb_1').
Apr 24 23:28:55 desktop NetworkManager: <debug> [1209076135.463515] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_2040_7060_4028705256_dvb_2').
Apr 24 23:28:56 desktop kernel: [  148.429940] dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.
Apr 24 23:43:52 desktop kernel: [   40.149935] dvb_usb: Unknown parameter `disable_rc_poling'
Apr 24 23:43:52 desktop kernel: [   40.154131] dvb_usb_dib0700: Unknown symbol dvb_usb_get_hexline
Apr 24 23:43:52 desktop kernel: [   40.154421] dvb_usb_dib0700: Unknown symbol dvb_usb_device_init
Apr 24 23:43:52 desktop kernel: [   40.154458] dvb_usb_dib0700: Unknown symbol dvb_usb_device_exit

```
(Just spotted I mis-spelt an option, to ensure the RC is enabled, but it didn't work before that either.)

Clues please...

---

