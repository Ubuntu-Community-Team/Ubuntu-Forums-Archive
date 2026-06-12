---
title: "Banshee stopped recognising my iPod"
date: 2006-08-01
forum: Multimedia &amp; Video
---

### Post by craig552 on 2006-08-01
I've tried several packages to get music on and off my ipod, and I've settled on Banshee. Which has now stopped recognising my iPod.

It was all working fine until I syncronised my iPod last week. It said **"please wait..."** for hours, then crashed. Now it can't see my iPod at all.

[FONT="Courier New"]$ipod --list[/FONT] 
   shows that it's properly mounted and all that, but banshee just can't see it.

I have no idea what could have caused it to stop working just like that.
Has anyone else had this problem? Or better yet solved it??

Any help would be greatly appreciated
Cheers

---

### Post by Benedolt on 2006-08-05
Having somehat the same problem here...
Banshee says this, when the iPod is plugged in:

```
System.ArgumentOutOfRangeException: Index is less than 0 or more than or equal to the list count.
Parameter name: index
596
in <0x00096> System.Collections.ArrayList:get_Item (Int32 index)
in <0x001a7> IPod.SongDatabase:LoadOnTheGo (Int32 num)
in <0x0001b> IPod.SongDatabase:LoadOnTheGo ()
in <0x000c6> IPod.SongDatabase:Reload (Boolean createFresh)
in <0x00117> IPod.SongDatabase:.ctor (IPod.Device device, Boolean createFresh)
in <0x0004f> IPod.Device:LoadSongDatabase (Boolean createFresh)
in <0x0007d> Banshee.Dap.Ipod.IpodDap:LoadIpod ()
in <0x000e9> Banshee.Dap.Ipod.IpodDap:Initialize (Hal.Device halDevice)
in <0x0004c> Banshee.Dap.DapCore:AddDevice (Hal.Device device, System.Type type)
System.ArgumentOutOfRangeException: Index is less than 0 or more than or equal to the list count.
Parameter name: index
596
in <0x00096> System.Collections.ArrayList:get_Item (Int32 index)
in <0x001a7> IPod.SongDatabase:LoadOnTheGo (Int32 num)
in <0x0001b> IPod.SongDatabase:LoadOnTheGo ()
in <0x000c6> IPod.SongDatabase:Reload (Boolean createFresh)
in <0x00117> IPod.SongDatabase:.ctor (IPod.Device device, Boolean createFresh)
in <0x0004f> IPod.Device:LoadSongDatabase (Boolean createFresh)
in <0x0007d> Banshee.Dap.Ipod.IpodDap:LoadIpod ()
in <0x000e9> Banshee.Dap.Ipod.IpodDap:Initialize (Hal.Device halDevice)
in <0x0004c> Banshee.Dap.DapCore:AddDevice (Hal.Device device, System.Type type)

```

Any idea, anyone? I also hear that a new version of Banshee has been released. It's a bugfix release. When is that going to be in the Ubuntu repositories?
-Benedolt

---

### Post by Benedolt on 2006-08-05
Good news, Craig!
I just found a way how to fix it! (at least it worked for me)
I just installed "gtkpod" (it's in Synaptic, probably universe...) loaded my iTunes db and syncronized it again using gtkpod. Now Banshee works perfectly again.
Good luck
Benedolt

---

### Post by craig552 on 2006-08-11
Excellent, cheers mate!

---

### Post by gamma on 2006-08-15
I'm also having this problem. I've been using gtkpod for syncing at the moment, but I can't get my iPod to be displayed in banshee. I reflashed the firmware with the Apple ipod-updater, but still no dice.. It stopped displaying after banshee locked up in syncing too.. help D:

UPDATE: Banshee apparently doesn't play nice with the latest version of iPod nano firmware (1.2), so downgrading to 1.1.1 makes things work again. The ipod program was telling me it wasn't a valid iPod and to reboot the iPod.

---

