---
title: "How to blacklist module for only one of three tuners"
date: 2010-10-03
forum: Mythbuntu
---

### Post by jensk on 2010-10-03
I have a single backend setup of several Anysee E30 combo tuners picking up DVB-C. Now I need the have one of the tuners to pick up DVB-T while the two others still pick up DVB-C.

The E30 combo has the following modules:
DVB-C: tda10023
DVB-T: zl10353

The E30 combo picks up DVB-C by default. When i installed the first E30 mythsetup told me it was a DVB-C tuner and everything worked out-of-the-box.

To have the E30 to pick up DVB-T i need to blacklist the module that picks up DVB-C in /etc/modprobe.d/blacklist.conf.

If i just blacklist tda10023 the other two tuners won't be able to pickup DVB-C.

So how do I blacklist a module for only one of the tuners? 
Alternatively how to force the one tuner to use the DVB-T module?

Thanks

---

### Post by ian dobson on 2010-10-03
Hi,

Looking in the driver source code:-

```
/* debug */
  static int dvb_usb_anysee_debug;
  module_param_named(debug, dvb_usb_anysee_debug, int, 0644);
  MODULE_PARM_DESC(debug, "set debugging level" DVB_USB_DEBUG_STATUS);
  static int dvb_usb_anysee_delsys;
  module_param_named(delsys, dvb_usb_anysee_delsys, int, 0644);
  MODULE_PARM_DESC(delsys, "select delivery mode (0=DVB-C, 1=DVB-T)");
  DVB_DEFINE_MOD_OPT_ADAPTER_NR(adapter_nr);
```

I see the module options delsys (DVB-C/T) and adapter_nr so maybe you could blacklist the dvb_usb_anysee and then load the driver 3 times using:-

dvb_usb_anysee adapter_nr=0 delsys=0
dvb_usb_anysee adapter_nr=1 delsys=0
dvb_usb_anysee adapter_nr=2 delsys=1

Just an idea but it might be worth a try.

EDIT:-
modinfo -p dvb-usb-anysee
adapter_nr:DVB adapter numbers
delsys:select delivery mode (0=DVB-C, 1=DVB-T)
debug:set debugging level (debugging is not enabled)

Regards
Ian Dobson

---

### Post by jensk on 2010-10-03
Hi Ian.
thank you for your answer. I am not enough skilled to fully understand your answer. What I have done is:

I /etc/modules i have entered:
dvb_usb_anysee adapter_nr=0 delsys=0
dvb_usb_anysee adapter_nr=1 delsys=0
dvb_usb_anysee adapter_nr=2 delsys=1

In /etc/modprobe.d/blacklist.conf I have entered
dvb_usb_anysee

lsmod shows that the server still load the module tda10023 (DVB-C) on three instances. The module zl10353 (DVB-T) has a 0 (zero) - as I understand it all three tuners loads in DVB-C mode.

is it somewhere else I should have entered your solution?

Thanks

---

### Post by ian dobson on 2010-10-03
Hi,

First off all we need to blacklist the dvb drivers so edit the file /etc/modprobe.d/blacklist.conf and add the line 
blacklist dvb_usb_anysee 
blacklist zl10353
blacklist tda10023

save the file are reboot. Now you don't have any video tuner devices available, to check this type 
ls /dev/dvb 
This should show no devices.

Now we try and load the dvb driver once with the DVB-C tuner, type:-
modprobe dvb_usb_anysee adapter_nr=0 delsys=0

now type dmesg and have a look at the messages that the kernel/module produced. if that looks ok now type:-
modprobe dvb_usb_anysee adapter_nr=1 delsys=0

and see the output of dmesg again, if thats ok type
modprobe dvb_usb_anysee adapter_nr=1 delsys=1

If this is OK then just edit the file /etc/rc.local and add the following lines to it just before the exit 0 line:-
modprobe dvb_usb_anysee adapter_nr=0 delsys=0
modprobe dvb_usb_anysee adapter_nr=1 delsys=0
modprobe dvb_usb_anysee adapter_nr=2 delsys=1


Note: All this is just an idea and I'm just guessing that it'll work. But everything goes wrong you just need to edit the blacklist.conf and rc.local file. I hoping that blacklisting the zl10353 and tda10023 and then loading the dvb_usb_anysee driver will cause the correct tuner driver to be loaded.

Regards
Ian Dobson

---

### Post by jensk on 2010-10-03
Hi Ian.
Thank you for the details. For the next couple of hours I will be killed if I take down the backend so i will have to wait til tomorrow to try you recomendations.

I will post the results

Thanks
Jens

---

### Post by jensk on 2010-10-03
I was granted 10 minutes downtime of the backend between wife and youngsters view'ing of recordings so i tried the suggested edit of /etc/modprobe.d/blacklist.conf. The boot.

A look at dmesg stated that dvb_usb_anysee was still loaded and was now missing tda10023 and zl10353 modules.

In /deb/dvb there was directories adapter1 adapter2 and adapter3.

Due to the missing tuner modules myth was reporting no free inputs.

I checked the blacklist.conf entries and they are:
blacklist dvb-usb_anysee (that gets loaded)
blacklist tda10023 (that doesn't get loaded)
blacklist zl10353 (that doesn't get loaded)

So the question here is how to stop dvb_usb_anysee from loading.
Thanks 
Jens

---

### Post by ian dobson on 2010-10-03
Hi,

If you put the driver in /etc/modprobe.d/blacklist.conf (blacklist dvb-usb_anysee) then it shouldn't load. Let me have a think about this.

Let me have a think about this.

Regards
Ian Dobson

---

### Post by ian dobson on 2010-10-04
Hi,

OK another idea. Remove all the blacklist crap from blacklist.conf (dvb_usb_anysee tda10023 zl10353) and reboot.

The system should load all the drivers required. Now go to the terminal prompt and unload the dvb_usb_anysee with
rmmod dvb_usb_anysee 

All your dvb devices in /dev/dvb should vanish. Now try loaded the driver again but with the correct options:-
modprobe dvb_usb_anysee adapter_nr=0 delsys=0
modprobe dvb_usb_anysee adapter_nr=1 delsys=0
modprobe dvb_usb_anysee adapter_nr=2 delsys=1

Have a look in dmesg to see if the correct drivers are loaded/ the correct tuner is used. If that works we can just add the commands to rc.local.

Regards
Ian Dobson

---

### Post by jensk on 2010-10-04
Hi Ian.
I have restarted with load of the modules. I entered 
rmmod -f dvb_usb_anysee

lsmod | grep anysee showed that dvb_usb_anysee was not loaded

ls /dev/dvb showed no directories

Then entered
modprobe dvb_usb_anysee adapter_nr=0 delsys=0
modprobe dvb_usb_anysee adapter_nr=1 delsys=0
modprobe dvb_usb_anysee adapter_nr=2 delsys=1

dmesg shows:
```
[71103.863794] dvb-usb: found a 'Anysee DVB USB2.0' in warm state.
[71103.863893] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[71103.864132] DVB: registering new adapter (Anysee DVB USB2.0)
[71103.867172] anysee: firmware version:0.1.2 hardware id:15
[71103.876929] DVB: registering adapter 2 frontend 0 (Philips TDA10023 DVB-C)...
[71103.881662] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/input/input7
[71103.881878] dvb-usb: schedule remote query interval to 200 msecs.
[71103.881889] dvb-usb: Anysee DVB USB2.0 successfully initialized and connected.
[71242.542597] usbcore: deregistering interface driver dvb_usb_anysee
[71242.684769] dvb-usb: Anysee DVB USB2.0 successfully deinitialized and disconnected.
[71242.754884] dvb-usb: Anysee DVB USB2.0 successfully deinitialized and disconnected.
[71242.824900] dvb-usb: Anysee DVB USB2.0 successfully deinitialized and disconnected.
[71271.990746] dvb-usb: found a 'Anysee DVB USB2.0' in warm state.
[71271.991882] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[71271.992123] DVB: registering new adapter (Anysee DVB USB2.0)
[71271.996069] anysee: firmware version:0.1.2 hardware id:15
[71272.012316] DVB: registering adapter 0 frontend 0 (Philips TDA10023 DVB-C)...
[71272.017585] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-1/input/input8
[71272.018032] dvb-usb: schedule remote query interval to 200 msecs.
[71272.018053] dvb-usb: Anysee DVB USB2.0 successfully initialized and connected.
[71272.019967] dvb-usb: found a 'Anysee DVB USB2.0' in warm state.
[71272.021483] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[71272.022138] DVB: registering new adapter (Anysee DVB USB2.0)
[71272.031687] anysee: firmware version:0.1.2 hardware id:15
[71272.043366] DVB: registering adapter 1 frontend 0 (Philips TDA10023 DVB-C)...
[71272.047965] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/input/input9
[71272.048242] dvb-usb: schedule remote query interval to 200 msecs.
[71272.048257] dvb-usb: Anysee DVB USB2.0 successfully initialized and connected.
[71272.050267] dvb-usb: found a 'Anysee DVB USB2.0' in warm state.
[71272.050460] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[71272.051238] DVB: registering new adapter (Anysee DVB USB2.0)
[71272.058327] anysee: firmware version:0.1.2 hardware id:15
[71272.069704] DVB: registering adapter 2 frontend 0 (Philips TDA10023 DVB-C)...
[71272.075360] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/input/input10
[71272.075611] dvb-usb: schedule remote query interval to 200 msecs.
[71272.075626] dvb-usb: Anysee DVB USB2.0 successfully initialized and connected.
[71272.078960] usbcore: registered new interface driver dvb_usb_anysee

```

As you can se all three modules are loaded with the DVB-C configuration even though the delsys=1 was set for the last modprobe line.
 
I guess that there is something wrong on how the module reads the delsys parameter.
Thanks
Jens

---

### Post by ian dobson on 2010-10-04
Hi,

Unless you can type the three modproble commands within 1 second, I imagine that loading the driver once is enough to get all three cards setup at once.

Sorry I've got no further ideas, maybe you can try getting in contact with the author of the driver (crope@iki.fi) Antti Palosaari.

The only other idea would be to hack the driver abit so that there are two versions, the stanadard version and one a hacked version that only supports dvb-t.

Regards
Ian Dobson

---

