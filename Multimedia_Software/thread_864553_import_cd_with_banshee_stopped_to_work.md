---
title: "import cd with banshee stopped to work"
date: 2008-07-19
forum: Multimedia Software
---

### Post by heliopaixao on 2008-07-19
Hi,

I always have used banshee to import songs from audio cd. Now when I try to import a audio cd I got the following error:

Could not import CD
Failed to open file 'media-import-audio-cd': No such file or directory


Banshee continues to play the cds normally.


[forhelio@uecnbk6044 ~]$ banshee-1 
[Info  16:40:19.543] Running Banshee 1.0.0
[Info  16:40:21.466] Querying MusicBrainz for Disc Release (CaG1dXHdVuU7DxynSU45bJA7zMY-)
[Warn  16:40:21.882] Cannot connect to NetworkManager - An available, working network connection will be assumed
[Info  16:40:21.889] All services are started 2.129373s
[Info  16:40:22.743] nereid Client Started

(Nereid:7541): Pango-CRITICAL **: pango_layout_set_text: assertion `length == 0 || text != NULL' failed

** (Nereid:7541): CRITICAL **: br_destroy: assertion `ripper != NULL' failed
[Error 16:40:27.165] Could not import CD - Failed to open file 'media-import-audio-cd': No such file or directory
[Warn  16:40:27.171] Caught an exception - Failed to open file 'media-import-audio-cd': No such file or directory (in `gdk-sharp')
  at Gdk.Pixbuf..ctor (System.String filename) [0x00000] 
  at Banshee.Gui.Widgets.UserJobTile.UpdateIcons () [0x0008d] in /builddir/build/BUILD/banshee-1-1.0.0/src/Core/Banshee.ThickClient/Banshee.Gui.Widgets/UserJobTile.cs:245 
  at Banshee.Gui.Widgets.UserJobTile.UpdateFromJob () [0x00201] in /builddir/build/BUILD/banshee-1-1.0.0/src/Core/Banshee.ThickClient/Banshee.Gui.Widgets/UserJobTile.cs:190 
  at Banshee.Gui.Widgets.UserJobTile..ctor (IUserJob job) [0x0002d] in /builddir/build/BUILD/banshee-1-1.0.0/src/Core/Banshee.ThickClient/Banshee.Gui.Widgets/UserJobTile.cs:65 
  at Banshee.Gui.Widgets.UserJobTileHost.AddJob (IUserJob job) [0x0003c] in /builddir/build/BUILD/banshee-1-1.0.0/src/Core/Banshee.ThickClient/Banshee.Gui.Widgets/UserJobTileHost.cs:78 
  at Banshee.Gui.Widgets.UserJobTileHost+<>c__CompilerGenerated10.<OnJobAdded>c__58 (System.Object +17, System.EventArgs +18) [0x0003e] in /builddir/build/BUILD/banshee-1-1.0.0/src/Core/Banshee.ThickClient/Banshee.Gui.Widgets/UserJobTileHost.cs:96 
  at Banshee.Base.ThreadAssist.ProxyToMain (System.EventHandler handler) [0x00015] in /builddir/build/BUILD/banshee-1-1.0.0/src/Core/Banshee.Services/Banshee.Base/ThreadAssist.cs:58 
  at Banshee.Gui.Widgets.UserJobTileHost.OnJobAdded (System.Object o, Banshee.ServiceStack.UserJobEventArgs args) [0x00016] in /builddir/build/BUILD/banshee-1-1.0.0/src/Core/Banshee.ThickClient/Banshee.Gui.Widgets/UserJobTileHost.cs:87 
  at Banshee.ServiceStack.UserJobManager.OnJobAdded (IUserJob job) [0x0000d] in /builddir/build/BUILD/banshee-1-1.0.0/src/Core/Banshee.Services/Banshee.ServiceStack/UserJobManager.cs:73 
  at Banshee.ServiceStack.UserJobManager.Register (IUserJob job) [0x00032] in /builddir/build/BUILD/banshee-1-1.0.0/src/Core/Banshee.Services/Banshee.ServiceStack/UserJobManager.cs:52 
  at Banshee.ServiceStack.UserJob.Register () [0x0000a] in /builddir/build/BUILD/banshee-1-1.0.0/src/Core/Banshee.Services/Banshee.ServiceStack/UserJob.cs:74 
  at Banshee.AudioCd.AudioCdRipper.Start () [0x0012d] in /builddir/build/BUILD/banshee-1-1.0.0/src/Extensions/Banshee.AudioCd/Banshee.AudioCd/AudioCdRipper.cs:125 
  at Banshee.AudioCd.AudioCdSource.ImportDisc () [0x00025] in /builddir/build/BUILD/banshee-1-1.0.0/src/Extensions/Banshee.AudioCd/Banshee.AudioCd/AudioCdSource.cs:202 







Thanks

---

