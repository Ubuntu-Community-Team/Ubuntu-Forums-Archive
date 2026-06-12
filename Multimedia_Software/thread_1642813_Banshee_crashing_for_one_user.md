---
title: "Banshee crashing for one user"
date: 2010-12-10
forum: Multimedia Software
---

### Post by Rifester on 2010-12-10
I have always used and enjoyed Banshee.   I recently did a fresh install of Maverick Meerkat.   Banshee runs fine under my user account but crashes instantly under my wife's.   I am pulling my hair out trying to figure out how to fix this. Any ideas would be great.   I have tried deleting all config files and re-installing.  Here is the terminal output when starting the program:  

 banshee-1
[Info  21:36:54.134] Running Banshee 1.8.0: [Ubuntu 10.10 (linux-gnu, i686) @ 2010-11-26 13:53:04 UTC]
[Info  21:36:58.351] Updating web proxy from GConf
[Info  21:36:58.458] All services are started 3.594578
[Info  21:37:00.919] nereid Client Started

Unhandled Exception: System.ArgumentException: UNC paths should be of the form \\server\share.
  at System.IO.Path.InsecureGetFullPath (System.String path) [0x00000] in <filename unknown>:0 
  at System.IO.Path.GetFullPath (System.String path) [0x00000] in <filename unknown>:0 
  at System.IO.FileSystemWatcher.get_FullPath () [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.IO.FileSystemWatcher:get_FullPath ()
  at System.IO.InotifyWatcher.StartDispatching (System.IO.FileSystemWatcher fsw) [0x00000] in <filename unknown>:0 
  at System.IO.FileSystemWatcher.Start () [0x00000] in <filename unknown>:0 
  at System.IO.FileSystemWatcher.set_EnableRaisingEvents (Boolean value) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.IO.FileSystemWatcher:set_EnableRaisingEvents (bool)
  at Banshee.LibraryWatcher.SourceWatcher.Watch () [0x00000] in <filename unknown>:0 

Thanks!

---

### Post by Rifester on 2010-12-12
(Bump)

Does anybody have any ideas?

---

