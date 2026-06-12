---
title: "Banshee no longer recognizes Android phone."
date: 2011-01-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2011-01-03
Banshee has stopped syncing or recognizing my android phone lately. I have the extensions enabled.

> [Info  11:26:58.388] Running Banshee 1.9.1: [Ubuntu natty (development branch) (linux-gnu, i686) @ 2010-12-27 03:33:16 UTC]
[Info  11:26:59.800] Updating web proxy from GConf
[Info  11:26:59.832] All services are started 1.145181
[Info  11:27:01.013] nereid Client Started
[Warn  11:27:01.285] Caught an exception - System.ArgumentNullException: Argument cannot be null.
Parameter name: s (in `mscorlib')
  at System.Int32.Parse (System.String s) [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.UsbDevice.GetBusNumber (IUsbDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.UsbDevice.get_BusNumber () [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.Device.ResolveUsbPortInfo () [0x00000] in <filename unknown>:0 
  at Banshee.Dap.Mtp.MtpSource.DeviceInitialize (IDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] in <filename unknown>:0 
[Info  11:27:01.403] AppleDeviceSource is ignoring unmounted volume 21 GB Filesystem
[Warn  11:27:01.404] Caught an exception - System.InvalidOperationException: Operation is not valid due to the current state of the object (in `Banshee.Dap.AppleDevice')
  at Banshee.Dap.AppleDevice.AppleDeviceSource.DeviceInitialize (IDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] in <filename unknown>:0 

Thanks.

---

### Post by anders_c_ on 2011-01-03
It finds my android phone just fine, try a livecd and see if it works there.

---

### Post by fluteflute on 2011-01-03
Report a bug :)

---

### Post by gnomeuser on 2011-01-03
[http://www.banshee.fm/file-bugs](http://www.banshee.fm/file-bugs)
[http://live.gnome.org/Banshee/CommonQuestions/Logs](http://live.gnome.org/Banshee/CommonQuestions/Logs)

and we will have a look at it.

---

### Post by donniezazen on 2011-01-04
Thank you all.

There is a similar bug filed in banshee bug tracking system.
[https://bugzilla.gnome.org/show_bug.cgi?id=638397](https://bugzilla.gnome.org/show_bug.cgi?id=638397)

I will just add my information to it.

---

