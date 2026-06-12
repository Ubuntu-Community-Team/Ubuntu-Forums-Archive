---
title: "Banshee not detecting Android phone in natty"
date: 2011-03-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by alexmurray on 2011-03-24
Is anyone else finding that Banshee doesn't detect their phone in natty? It worked fine in maverick and rhythmbox detects it fine in natty but no go for banshee. This is a fresh install too not an upgrade, and my phone is a HTC Desire HD.

---

### Post by Steel-Bunz on 2011-03-24
Same problem here. HTC Inspire. No luck with Banshee Documentation either.

---

### Post by alexmurray on 2011-03-24
Have just filed bug [#741695]("https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/741695") reporting this

---

### Post by jpeddicord on 2011-03-24
I believe hardware support is broken in Banshee at the moment:```
jacob@termina: ~ $ banshee
[Info  09:44:49.584] Running Banshee 1.9.5: [Ubuntu Natty (development branch) (linux-gnu, x86_64) @ 2011-03-11 13:57:57 UTC]
[Warn  09:44:50.733] Hardware manager extension failed to load - System.InvalidOperationException: Type 'Banshee.Hardware.Gio.HardwareManager' not found in add-in 'Banshee.Gio,1.0' (in `Mono.Addins')
  at Mono.Addins.RuntimeAddin.GetType (System.String typeName, Boolean throwIfNotFound) [0x00000] in <filename unknown>:0 
  at Mono.Addins.TypeExtensionNode.get_Type () [0x00000] in <filename unknown>:0 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] in <filename unknown>:0 
  at Mono.Addins.InstanceExtensionNode.CreateInstance (System.Type expectedType) [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.HardwareManager..ctor () [0x00000] in <filename unknown>:0 
[Warn  09:44:50.734] Service `Banshee.Hardware.HardwareManager' not started: No HardwareManager extensions could be loaded. Hardware support will be disabled.
[Warn  09:44:50.734] Caught an exception - System.Exception: No HardwareManager extensions could be loaded. Hardware support will be disabled. (in `Banshee.Services')
  at Banshee.Hardware.HardwareManager..ctor () [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 

```Looks like a fix has been committed, though.

I was rather confused at first; I just bought an HTC Thunderbolt and couldn't figure out why Banshee wouldn't recognize it. :P

---

### Post by bluenova on 2011-03-24
> **jpeddicord said:**
> I believe hardware support is broken in Banshee at the moment:```
jacob@termina: ~ $ banshee
[Info  09:44:49.584] Running Banshee 1.9.5: [Ubuntu Natty (development branch) (linux-gnu, x86_64) @ 2011-03-11 13:57:57 UTC]
[Warn  09:44:50.733] Hardware manager extension failed to load - System.InvalidOperationException: Type 'Banshee.Hardware.Gio.HardwareManager' not found in add-in 'Banshee.Gio,1.0' (in `Mono.Addins')
  at Mono.Addins.RuntimeAddin.GetType (System.String typeName, Boolean throwIfNotFound) [0x00000] in <filename unknown>:0 
  at Mono.Addins.TypeExtensionNode.get_Type () [0x00000] in <filename unknown>:0 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] in <filename unknown>:0 
  at Mono.Addins.InstanceExtensionNode.CreateInstance (System.Type expectedType) [0x00000] in <filename unknown>:0 
  at Banshee.Hardware.HardwareManager..ctor () [0x00000] in <filename unknown>:0 
[Warn  09:44:50.734] Service `Banshee.Hardware.HardwareManager' not started: No HardwareManager extensions could be loaded. Hardware support will be disabled.
[Warn  09:44:50.734] Caught an exception - System.Exception: No HardwareManager extensions could be loaded. Hardware support will be disabled. (in `Banshee.Services')
  at Banshee.Hardware.HardwareManager..ctor () [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 

```Looks like a fix has been committed, though.

I was rather confused at first; I just bought an HTC Thunderbolt and couldn't figure out why Banshee wouldn't recognize it. :P



+1, Subscribed.

---

### Post by donniezazen on 2011-03-24
I had same problem but it was quickly fixed by adding my phones details in media-info-server by developers. I suggest you file a bug in banshee bugzilla. I will post the link of my bug, gnome bugzilla is down right now.

---

### Post by jpeddicord on 2011-03-25
> **soham_1207 said:**
> I had same problem but it was quickly fixed by adding my phones details in media-info-server by developers. I suggest you file a bug in banshee bugzilla. I will post the link of my bug, gnome bugzilla is down right now.

That is the correct place for device information, and it is likely that the Thunderbolt needs to be added to that, but at the moment Banshee isn't loading *any* hardware devices, hence the previously-mentioned bug report.

I actually manually added entries to media-player-info & kludged the .is_audio_device file on the phone to get it to work, but it won't really do a whole lot until the problem is fixed in Banshee. :)

In any case, it's supposedly been fixed upstream, so I think it makes sense to wait and see if it works there first.

---

### Post by CaptainMark on 2011-04-04
+1 Subscribed. HTC Desire, thought it was me going crazy,

---

### Post by jpeddicord on 2011-04-04
> **CaptainMark said:**
> +1 Subscribed. HTC Desire, thought it was me going crazy,

The bug should be fixed. If you're still having issues and you're up-to-date, you may want to consider filing another bug.

---

### Post by bluenova on 2011-04-05
> **jpeddicord said:**
> The bug should be fixed. If you're still having issues and you're up-to-date, you may want to consider filing another bug.

Yes Banshee has come through updates and it's now working for me (HTC Hero - Android 2.3.3)

---

### Post by directhex on 2011-04-05
> **jpeddicord said:**
> The bug should be fixed. If you're still having issues and you're up-to-date, you may want to consider filing another bug.

Amazing how troublesome confusing "y" and "yes" can be

---

