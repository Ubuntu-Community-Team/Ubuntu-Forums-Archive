---
title: "Network folder mounting in Nautilus"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by mhdbnoimi on 2010-01-16
I'm using samba so all shared paths begin with smb:// which is not accepted in many applications so I want to know how I can mount network folder in Nautilus or any GUI tool?

I don't want to use terminal it needs a mile of strange commands, I tried to mount network folder by terminal but I failed so I read [https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently) but it increased my hate to terminal.

---

### Post by CompyTheInsane on 2010-01-17
> **mhdbnoimi said:**
> 
I'm using samba so all shared paths begin with smb:// which is not accepted in many applications.

Here's one way for you to be able to access files from your network folders on such applications without having to resort to the command line:
You can use your GVFS mount point to access files on your network folders from applications that don't accept smb:// paths.
For example, to browse mounted network folders in those programs, enter /home/<username>/.gvfs/
Be sure your network folders are mounted first.

> **mhdbnoimi said:**
> 
so I want to know how I can mount network folder in Nautilus or any GUI tool?

Just click on Network, then click on Windows Network, select the computer containing the network folder(s) that you are trying to access, then double click on the share(s) that you're trying to access. Entering the smb:// locations into Nautilus work as well.

---

### Post by mhdbnoimi on 2010-01-17
> **compugeek32 said:**
> Here's one way for you to be able to access files from your network folders on such applications without having to resort to the command line:
You can use your GVFS mount point to access files on your network folders from applications that don't accept smb:// paths.
For example, to browse mounted network folders in those programs, enter /home/<username>/.gvfs/

In nautilus I've mounted the shared folder then browsed this path: 
```
smb://192.168.0.1/bashir%20backup/Backup/Academic/342441735
```

but when I inputed the following path as you said:
```
/home/bashir/.gvfs/bashir%20backup/Backup/Academic/342441735
```
it didn't work!!! Could you tell me whats wrong, is the above path is wrong?

---

### Post by mhdbnoimi on 2010-01-17
I forgot to tell you that when I tried to input the following path in nautilus:
```
/home/bashir/.gvfs/bashir%20backup/Backup/Academic/342441735
```

it gave me the following error:
> **Could not find "/home/bashir/.gvfs/bashir%20backup/Backup/Academic/342441735".**
Please check the spelling and try again.


---

### Post by CompyTheInsane on 2010-01-17
Have you already tried browsing your mounted network folders just by typing /home/bashir/.gvfs/?

I'll see if I can try to clarify the first reply further when I get back.

---

### Post by mhdbnoimi on 2010-01-17
> Have you already tried browsing your mounted network folders just by typing /home/bashir/.gvfs/?
Yes, it works all mounted folders (bashir backup on 192.168.0.1) but when I click on one of them I got smb:// path not /home/bashir/.gvfs/ path.

---

### Post by gradinaruvasile on 2010-01-17
Open it in a terminal:
first go to the .gvfs folder:

cd ~/.gvfs

Then see whats in it:

ls -al

Then enter the smb directory:

cd bashir (and here press tab, it will be autofilled)

Now you are in the gvfs mounted samba folder. You have the full path after the $ sign. Copy-paste that path in any app. 
But there is a catch: If the path contains spaces you either escape them or place the full path between "".

---

### Post by mhdbnoimi on 2010-01-17
I successfully did this procedure in terminal but when I past the path in the applications they didn't accept it for example:

when I tried to add the path 
```
/home/bashir/.gvfs/"bashir backup on 192.168.0.1"/Backup/test
```
in areca backup system I got the following error message:
```
10-01-17 18:42 - ERROR - An error occured while writing the target's history
com.myJava.util.xml.AdapterException: java.io.FileNotFoundException: /home/bashir/.gvfs/"bashir backup on 192.168.0.1"/Backup/test/367639434/history (No such file or directory)
	at com.myJava.util.history.XMLHistoryAdapter.write(XMLHistoryAdapter.java:131)
	at com.myJava.util.history.HistoryHandler.writeHistory(HistoryHandler.java:92)
	at com.myJava.util.history.HistoryHandler.addEntryAndFlush(HistoryHandler.java:100)
	at com.application.areca.AbstractTarget.processBackup(AbstractTarget.java:330)
	at com.application.areca.ActionProxy.processBackupOnTarget(ActionProxy.java:52)
	at com.application.areca.launcher.gui.Application$15.runCommand(Application.java:1168)
	at com.application.areca.launcher.gui.Application$ProcessRunner.run(Application.java:1645)
	at java.lang.Thread.run(Thread.java:636)
Caused by: java.io.FileNotFoundException: /home/bashir/.gvfs/"bashir backup on 192.168.0.1"/Backup/test/367639434/history (No such file or directory)
	at java.io.FileOutputStream.open(Native Method)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:209)
	at com.myJava.file.driver.DefaultFileSystemDriver.getFileOutputStream(DefaultFileSystemDriver.java:351)
	at com.myJava.file.driver.DefaultFileSystemDriver.getFileOutputStream(DefaultFileSystemDriver.java:343)
	at com.myJava.file.driver.CompressedFileSystemDriver.getOutputStream(CompressedFileSystemDriver.java:325)
	at com.myJava.file.driver.CompressedFileSystemDriver.getFileOutputStream(CompressedFileSystemDriver.java:306)
	at com.myJava.file.driver.event.EventFileSystemDriver.getFileOutputStream(EventFileSystemDriver.java:306)
	at com.myJava.file.FileSystemManager.getFileOutputStream(FileSystemManager.java:397)
	at com.myJava.util.history.XMLHistoryAdapter.write(XMLHistoryAdapter.java:113)
	... 7 more

10-01-17 18:42 - DETAIL - Processing /home/bashir/aTunes/Uninstaller
10-01-17 18:42 - ERROR
java.io.FileNotFoundException: /home/bashir/.gvfs/"bashir backup on 192.168.0.1"/Backup/test/367639434/100117/.installationinformation (No such file or directory)
	at java.io.FileOutputStream.open(Native Method)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:209)
	at com.myJava.file.driver.DefaultFileSystemDriver.getFileOutputStream(DefaultFileSystemDriver.java:351)
	at com.myJava.file.driver.DefaultFileSystemDriver.getFileOutputStream(DefaultFileSystemDriver.java:343)
	at com.myJava.file.driver.CompressedFileSystemDriver.getOutputStream(CompressedFileSystemDriver.java:325)
	at com.myJava.file.driver.CompressedFileSystemDriver.getFileOutputStream(CompressedFileSystemDriver.java:356)
	at com.myJava.file.driver.event.EventFileSystemDriver.getFileOutputStream(EventFileSystemDriver.java:290)
	at com.myJava.file.FileSystemManager.getFileOutputStream(FileSystemManager.java:401)
	at com.application.areca.impl.IncrementalDirectoryMedium.storeFileInArchive(IncrementalDirectoryMedium.java:114)
	at com.application.areca.impl.AbstractIncrementalFileSystemMedium$1.run(AbstractIncrementalFileSystemMedium.java:1183)
	at com.application.areca.impl.AbstractIncrementalFileSystemMedium.doAndRetry(AbstractIncrementalFileSystemMedium.java:1220)
	at com.application.areca.impl.AbstractIncrementalFileSystemMedium.store(AbstractIncrementalFileSystemMedium.java:1174)
	at com.application.areca.AbstractTarget.processBackup(AbstractTarget.java:340)
	at com.application.areca.ActionProxy.processBackupOnTarget(ActionProxy.java:52)
	at com.application.areca.launcher.gui.Application$15.runCommand(Application.java:1168)
	at com.application.areca.launcher.gui.Application$ProcessRunner.run(Application.java:1645)
	at java.lang.Thread.run(Thread.java:636)

10-01-17 18:42 - ERROR
java.io.FileNotFoundException: /home/bashir/.gvfs/"bashir backup on 192.168.0.1"/Backup/test/367639434/100117/.installationinformation (No such file or directory)
	at java.io.FileOutputStream.open(Native Method)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:209)
	at com.myJava.file.driver.DefaultFileSystemDriver.getFileOutputStream(DefaultFileSystemDriver.java:351)
	at com.myJava.file.driver.DefaultFileSystemDriver.getFileOutputStream(DefaultFileSystemDriver.java:343)
	at com.myJava.file.driver.CompressedFileSystemDriver.getOutputStream(CompressedFileSystemDriver.java:325)
	at com.myJava.file.driver.CompressedFileSystemDriver.getFileOutputStream(CompressedFileSystemDriver.java:356)
	at com.myJava.file.driver.event.EventFileSystemDriver.getFileOutputStream(EventFileSystemDriver.java:290)
	at com.myJava.file.FileSystemManager.getFileOutputStream(FileSystemManager.java:401)
	at com.application.areca.impl.IncrementalDirectoryMedium.storeFileInArchive(IncrementalDirectoryMedium.java:114)
	at com.application.areca.impl.AbstractIncrementalFileSystemMedium$1.run(AbstractIncrementalFileSystemMedium.java:1183)
	at com.application.areca.impl.AbstractIncrementalFileSystemMedium.doAndRetry(AbstractIncrementalFileSystemMedium.java:1220)
	at com.application.areca.impl.AbstractIncrementalFileSystemMedium.store(AbstractIncrementalFileSystemMedium.java:1174)
	at com.application.areca.AbstractTarget.processBackup(AbstractTarget.java:340)
	at com.application.areca.ActionProxy.processBackupOnTarget(ActionProxy.java:52)
	at com.application.areca.launcher.gui.Application$15.runCommand(Application.java:1168)
	at com.application.areca.launcher.gui.Application$ProcessRunner.run(Application.java:1645)
	at java.lang.Thread.run(Thread.java:636)

10-01-17 18:42 - ERROR
com.application.areca.ApplicationException: com.application.areca.StoreException: Error during storage of .installationinformation : /home/bashir/.gvfs/"bashir backup on 192.168.0.1"/Backup/test/367639434/100117/.installationinformation (No such file or directory)
	at com.application.areca.AbstractTarget.processBackup(AbstractTarget.java:342)
	at com.application.areca.ActionProxy.processBackupOnTarget(ActionProxy.java:52)
	at com.application.areca.launcher.gui.Application$15.runCommand(Application.java:1168)
	at com.application.areca.launcher.gui.Application$ProcessRunner.run(Application.java:1645)
	at java.lang.Thread.run(Thread.java:636)
Caused by: com.application.areca.StoreException: Error during storage of .installationinformation : /home/bashir/.gvfs/"bashir backup on 192.168.0.1"/Backup/test/367639434/100117/.installationinformation (No such file or directory)
	at com.application.areca.impl.AbstractIncrementalFileSystemMedium.store(AbstractIncrementalFileSystemMedium.java:1206)
	at com.application.areca.AbstractTarget.processBackup(AbstractTarget.java:340)
	... 4 more
Caused by: java.io.FileNotFoundException: /home/bashir/.gvfs/"bashir backup on 192.168.0.1"/Backup/test/367639434/100117/.installationinformation (No such file or directory)
	at java.io.FileOutputStream.open(Native Method)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:209)
	at com.myJava.file.driver.DefaultFileSystemDriver.getFileOutputStream(DefaultFileSystemDriver.java:351)
	at com.myJava.file.driver.DefaultFileSystemDriver.getFileOutputStream(DefaultFileSystemDriver.java:343)
	at com.myJava.file.driver.CompressedFileSystemDriver.getOutputStream(CompressedFileSystemDriver.java:325)
	at com.myJava.file.driver.CompressedFileSystemDriver.getFileOutputStream(CompressedFileSystemDriver.java:356)
	at com.myJava.file.driver.event.EventFileSystemDriver.getFileOutputStream(EventFileSystemDriver.java:290)
	at com.myJava.file.FileSystemManager.getFileOutputStream(FileSystemManager.java:401)
	at com.application.areca.impl.IncrementalDirectoryMedium.storeFileInArchive(IncrementalDirectoryMedium.java:114)
	at com.application.areca.impl.AbstractIncrementalFileSystemMedium$1.run(AbstractIncrementalFileSystemMedium.java:1183)
	at com.application.areca.impl.AbstractIncrementalFileSystemMedium.doAndRetry(AbstractIncrementalFileSystemMedium.java:1220)
	at com.application.areca.impl.AbstractIncrementalFileSystemMedium.store(AbstractIncrementalFileSystemMedium.java:1174)
	... 5 more

10-01-17 18:42 - ERROR - An error occured while writing the target's history
com.myJava.util.xml.AdapterException: java.io.FileNotFoundException: /home/bashir/.gvfs/"bashir backup on 192.168.0.1"/Backup/test/367639434/history (No such file or directory)
	at com.myJava.util.history.XMLHistoryAdapter.write(XMLHistoryAdapter.java:131)
	at com.myJava.util.history.HistoryHandler.writeHistory(HistoryHandler.java:92)
	at com.myJava.util.history.HistoryHandler.addEntryAndFlush(HistoryHandler.java:100)
	at com.application.areca.AbstractTarget.rollbackBackup(AbstractTarget.java:531)
	at com.application.areca.AbstractTarget.processBackup(AbstractTarget.java:359)
	at com.application.areca.ActionProxy.processBackupOnTarget(ActionProxy.java:52)
	at com.application.areca.launcher.gui.Application$15.runCommand(Application.java:1168)
	at com.application.areca.launcher.gui.Application$ProcessRunner.run(Application.java:1645)
	at java.lang.Thread.run(Thread.java:636)
Caused by: java.io.FileNotFoundException: /home/bashir/.gvfs/"bashir backup on 192.168.0.1"/Backup/test/367639434/history (No such file or directory)
	at java.io.FileOutputStream.open(Native Method)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:209)
	at com.myJava.file.driver.DefaultFileSystemDriver.getFileOutputStream(DefaultFileSystemDriver.java:351)
	at com.myJava.file.driver.DefaultFileSystemDriver.getFileOutputStream(DefaultFileSystemDriver.java:343)
	at com.myJava.file.driver.CompressedFileSystemDriver.getOutputStream(CompressedFileSystemDriver.java:325)
	at com.myJava.file.driver.CompressedFileSystemDriver.getFileOutputStream(CompressedFileSystemDriver.java:306)
	at com.myJava.file.driver.event.EventFileSystemDriver.getFileOutputStream(EventFileSystemDriver.java:306)
	at com.myJava.file.FileSystemManager.getFileOutputStream(FileSystemManager.java:397)
	at com.myJava.util.history.XMLHistoryAdapter.write(XMLHistoryAdapter.java:113)
	... 8 more

10-01-17 18:42 - INFO - Rollbacking backup ...
10-01-17 18:42 - INFO - Rollback completed.
10-01-17 18:42 - ERROR
java.io.IOException: No such file or directory
	at java.io.UnixFileSystem.createFileExclusively(Native Method)
	at java.io.File.createNewFile(File.java:900)
	at com.myJava.file.driver.DefaultFileSystemDriver.createNewFile(DefaultFileSystemDriver.java:68)
	at com.myJava.file.driver.CompressedFileSystemDriver.createNewFile(CompressedFileSystemDriver.java:83)
	at com.myJava.file.driver.event.EventFileSystemDriver.createNewFile(EventFileSystemDriver.java:156)
	at com.myJava.file.FileSystemManager.createNewFile(FileSystemManager.java:285)
	at com.application.areca.metadata.AbstractMetadataAdapter.close(AbstractMetadataAdapter.java:130)
	at com.application.areca.impl.AbstractIncrementalFileSystemMedium.rollbackBackup(AbstractIncrementalFileSystemMedium.java:961)
	at com.application.areca.AbstractTarget.rollbackBackup(AbstractTarget.java:534)
	at com.application.areca.AbstractTarget.processBackup(AbstractTarget.java:359)
	at com.application.areca.ActionProxy.processBackupOnTarget(ActionProxy.java:52)
	at com.application.areca.launcher.gui.Application$15.runCommand(Application.java:1168)
	at com.application.areca.launcher.gui.Application$ProcessRunner.run(Application.java:1645)
	at java.lang.Thread.run(Thread.java:636)
```

---

### Post by gradinaruvasile on 2010-01-17
The whole path must be between "".

---

### Post by mhdbnoimi on 2010-01-17
> **gradinaruvasile said:**
> The whole path must be between "".

I tried but it didn't work!
any way I tried to use a mounted folder without space, it gave me same errors

---

### Post by gradinaruvasile on 2010-01-17
Ok, try this:
Create a link for that folder:

ln -s "/home/bashir/.gvfs/bashir backup on 192.168.0.1/Backup/test" ~/Desktop/bashir

This will create a link to that folder: /home/bashir/Desktop/bashir - give this path to the program see if it works.

---

### Post by mhdbnoimi on 2010-01-17
> Create a link for that folder:
It fixed the issue, Thanks  gradinaruvasile.

---

### Post by xlevus on 2010-01-23
I've been using the .gvfs folder in scripts and such for a while now, but I've noticed that gvfs doesn't always create it, and it's **really** irritating.

e.g. 
```
xin@x:~$ ls -a .gvfs/
.  ..
xin@x:~$ gvfs-mount smb://xin@bebop/media
Error mounting location: Location is already mounted
```

Is there any way to force its creation?

---

