---
title: "Cannot use large playlists in any audio players"
date: 2010-12-20
forum: Multimedia Software
---

### Post by dunk on 2010-12-20
Hi All.

I'm having a really frustrating problem with regard to playing my MP3s.

I have tried these Applications:

Banshee
Rhythmbox
Exaile

What I like to do, and have been able to for years using Windows is to set my entire collection (13500) in a playlist and just leave it on random. I have been able to do this for years using Winamp or WinMP or pretty much any Win MM Application.

Anyone shed any light on the issue? It's driving me mental!!

Cheers

Dunk

---

### Post by dunk on 2010-12-20
No one??? :(

---

### Post by cchhrriiss121212 on 2010-12-20
> Anyone shed any light on the issue?
What is the issue? Are you getting an error message, crashes or what?

---

### Post by dunk on 2010-12-20
That's a good point, sorry lol!

They all just lock up, go grey and you have to force quit them. I've tried leaving them for half hour or so to see if it's gonna take a while to catch up with itself.

Banshee was able to import all my tunes to its library, but when I went to play my entire collection in a playlist, just locked up again.

Cheers

Dunk

---

### Post by cchhrriiss121212 on 2010-12-20
Try opening them from a terminal and see what output you get. You could also try out some other players:
Deadbeef
Quod Libet
Guayadeque
Audacious 

Also, is there any reason you are using a playlist if it contains all of your files? You could just set up a directory to watch and then use random.

---

### Post by dunk on 2010-12-20
I'm actually using DeadBeef now, which seems to work, although it doesn't really have a nice media library as such. 

When I load Banshee from Terminal I get this. It only craps out when I actually click on the Play Queue with all my tracks in it (without anything playing)
```

dunk@Server:~$ banshee-1
[Info  21:51:32.230] Running Banshee 1.8.0: [Ubuntu 10.10 (linux-gnu, i686) @ 2010-11-26 13:53:04 UTC]
[Info  21:51:41.830] Updating web proxy from GConf
[Info  21:51:42.242] All services are started 8.582044
[Info  21:51:49.917] nereid Client Started
[Warn  21:51:50.817] Caught an exception - System.ArgumentNullException: Argument cannot be null.
Parameter name: s (in `mscorlib')
  at System.Int32.Parse (System.String s) [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.UsbDevice.GetBusNumber (IUsbDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.UsbDevice.get_BusNumber () [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.Device.ResolveUsbPortInfo () [0x00000] in <filename unknown>:0 
  at Banshee.Dap.Mtp.MtpSource.DeviceInitialize (IDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] in <filename unknown>:0 
[Warn  21:51:51.793] Caught an exception - System.ArgumentNullException: Argument cannot be null.
Parameter name: s (in `mscorlib')
  at System.Int32.Parse (System.String s) [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.UsbDevice.GetBusNumber (IUsbDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.UsbDevice.get_BusNumber () [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.Gio.Device.ResolveUsbPortInfo () [0x00000] in <filename unknown>:0 
  at Banshee.Dap.Mtp.MtpSource.DeviceInitialize (IDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] in <filename unknown>:0 
[Info  21:51:51.871] AppleDeviceSource is ignoring unmounted volume Movies
[Warn  21:51:51.872] Caught an exception - System.InvalidOperationException: Operation is not valid due to the current state of the object (in `Banshee.Dap.AppleDevice')
  at Banshee.Dap.AppleDevice.AppleDeviceSource.DeviceInitialize (IDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] in <filename unknown>:0 

```

---

