---
title: "DVB-T issues.. Terratec Cinergy T USB XXS (HD)/ T3 stopped working?!"
date: 2011-08-05
forum: Multimedia Software
---

### Post by reutel on 2011-08-05
Hi all,

I'm having issues with a Terratec T3 DVB-T USB stick. It seems that ubuntu is recognizing it, but it isn't usable in Kaffeine or VLC anymore.
The funny thing is that is WAS working, but after installing some codecs, upgrading to a new kernel and rebooting it stopped working, and it is no longer detected by both apps... Kaffeine says "no available device found", VLC gives a similar error.
I've tried booting the machine with the old kernel, but the issue remains. I don't think installing codecs (x264 for example, tried removing it, no success) has anything to do with it, so I wonder what went wrong?

dmesg output after removing and reinserting the stick:
[ 1403.350912] usb 1-1: USB disconnect, address 2
[ 1403.380528] dvb-usb: Terratec Cinergy T USB XXS (HD)/ T3 successfully deinitialized and disconnected.
...
[ 1414.136020] usb 1-2: new high speed USB device using ehci_hcd and address 3
[ 1414.269305] dvb-usb: found a 'Terratec Cinergy T USB XXS (HD)/ T3' in cold state, will try to load a firmware
[ 1414.272171] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[ 1414.477552] dib0700: firmware started successfully.
[ 1414.980196] dvb-usb: found a 'Terratec Cinergy T USB XXS (HD)/ T3' in warm state.
[ 1414.980275] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 1414.981299] DVB: registering new adapter (Terratec Cinergy T USB XXS (HD)/ T3)
[ 1415.181432] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[ 1415.390804] DiB0070: successfully identified
[ 1415.390818] Registered IR keymap rc-dib0700-rc5
[ 1415.390995] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/rc/rc1/input3
[ 1415.391081] rc1: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/rc/rc1
[ 1415.391179] dvb-usb: schedule remote query interval to 50 msecs.
[ 1415.391185] dvb-usb: Terratec Cinergy T USB XXS (HD)/ T3 successfully initialized and connected.

lsusb output:
Bus 001 Device 003: ID 0ccd:10a0 TerraTec Electronic GmbH

ls /dev/dvb/adapter0/ -la
total 0
drwxr-xr-x  2 root root     120 2011-08-05 11:52 .
drwxr-xr-x  3 root root      60 2011-08-05 11:52 ..
crw-rw----+ 1 root video 212, 0 2011-08-05 11:52 demux0
crw-rw----+ 1 root video 212, 1 2011-08-05 11:52 dvr0
crw-rw----+ 1 root video 212, 3 2011-08-05 11:52 frontend0
crw-rw----+ 1 root video 212, 2 2011-08-05 11:52 net0

Oh and one more thing; in gnome device manager there is a question mark next to the stick. So there might be something missing on the system after all. linux-firmware-nonfree was installed and reinstalled 10 times or something, still no go, not even after a reboot.


Thanks in advance

---

### Post by realzippy on 2011-08-05
what happens when reconfiguring kaffeine?
Does it detect the device?

```
kaffeine --config
```

---

### Post by reutel on 2011-08-05
thx for the quick response

it gives me the following error:
kaffeine(2412) DvbLinuxDevice::identifyDevice: couldn't open "/dev/dvb/adapter0/frontend0"

---

### Post by realzippy on 2011-08-06
[ 1414.980196] dvb-usb: found a 'Terratec Cinergy T USB XXS (HD)/ T3' in warm state.

Warm state means firmware loaded.
Disconnect the stick,reboot,then plug in the stick...
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577377](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577377)
A newer kernel seems to help...

---

### Post by reutel on 2011-08-08
that doesn't help, the issue remains
> [   76.732018] usb 1-2: new high speed USB device using ehci_hcd and address 2
[   76.888311] IR NEC protocol handler initialized
[   76.891890] IR RC5(x) protocol handler initialized
[   76.901506] IR RC6 protocol handler initialized
[   76.906545] IR JVC protocol handler initialized
[   76.910215] IR Sony protocol handler initialized
[   76.918349] lirc_dev: IR Remote Control driver registered, major 251 
[   76.921301] IR LIRC bridge handler initialized
[   76.938894] dib0700: loaded with support for 15 different device-types
[   76.939060] dvb-usb: found a 'Terratec Cinergy T USB XXS (HD)/ T3' in cold state, will try to load a firmware
[   76.955023] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   77.157670] dib0700: firmware started successfully.
[   77.660192] dvb-usb: found a 'Terratec Cinergy T USB XXS (HD)/ T3' in warm state.
[   77.661071] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   77.661254] DVB: registering new adapter (Terratec Cinergy T USB XXS (HD)/ T3)
[   77.861426] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[   78.074798] DiB0070: successfully identified
[   78.100017] Registered IR keymap rc-dib0700-rc5
[   78.101032] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/rc/rc0/input2
[   78.101166] rc0: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/rc/rc0
[   78.101303] dvb-usb: schedule remote query interval to 50 msecs.
[   78.101309] dvb-usb: Terratec Cinergy T USB XXS (HD)/ T3 successfully initialized and connected.
[   78.101454] usbcore: registered new interface driver dvb_usb_dib0700

still no go in kaffeine nor vlc

I'm already running the latest kernel:
2.6.38-10-generic-pae

---

