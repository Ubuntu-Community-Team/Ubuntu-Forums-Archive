---
title: "Hipo crashes with Ipod plugged"
date: 2010-02-19
forum: Multimedia Software
---

### Post by flucoe on 2010-02-19
Hi. I'm using Ubuntu 9.04 and Hipo version 0.6.1. Whenever I open the program and the Ipod is plugged, I receive the following message "Detected unsupported database version 42" Details: at IPod.DatabaseRecord.Read (IPod.DatabaseRecord db, System.IO.BinaryReader reader) [0x00000] 
  at IPod.TrackDatabase.Reload (Boolean createFresh) [0x00000] 
  at IPod.TrackDatabase..ctor (IPod.Device device, Boolean createFresh) [0x00000] 
  at IPod.Device.LoadTrackDatabase (Boolean createFresh) [0x00000] 
  at IPod.Device.LoadTrackDatabase () [0x00000] 
  at IPod.Device.get_TrackDatabase () [0x00000] 
  at IPod.Device.get_Name () [0x00000] 
  at IPod.DeviceCombo.AddDevice (IPod.Device device) [0x00000] 
  at IPod.DeviceCombo..ctor () [0x00000] 
  at Hipo.HipoMainWindow.CreateWindow (System.String[] args) [0x00000] 
  at Hipo.HipoMain.Run (System.String[] args) [0x00000] 
  at Hipo.HipoMain.Main (System.String[] args) [0x00000] 

Now, when the Ipod is unplugged, I can open the program without any problems... and the Ipod works perfectly... so, no idea what is going on. I can't do anything. Thanks,

---

### Post by Deiyn on 2010-07-11
Bump, Im having the exactly same problem. Though, this is happening on both Hipo AND gtkpod. This happened after I erased my photos from my GEN1 Ipod nano and saved changes on a new batch.

---

