---
title: "Import export archive recordings problem in 8.04"
date: 2008-04-25
forum: Mythbuntu
---

### Post by GordonEndersby on 2008-04-25
Hi, I have just installed the release candidate of 8.04.
Before I installed 8.04 rc I archived a few recordings to an external drive from mythbuntu 7.10
But now I am unable to import the video files.
Also Im unable to export a recording I have just made from live TV.

The log screen shows no activity and goes straight to exit.
I have errors in mythfrontend.log:

ExportNativeWizard::createConfigFile: Failed to open file for writing - /usr/share/mythtv/mytharchive/.tmp/config/mydata.xml
sh: cannot create /usr/share/mythtv/mytharchive/.tmp/logs/progress.log: Directory nonexistent
chmod: cannot access `/usr/share/mythtv/mytharchive/.tmp/': No such file or directory
chmod: cannot access `/usr/share/mythtv/mytharchive/.tmp/work': No such file or directory
chmod: cannot access `/usr/share/mythtv/mytharchive/.tmp/logs': No such file or directory
chmod: cannot access `/usr/share/mythtv/mytharchive/.tmp/config': No such file or directory
2008-04-25 17:23:27.155 XMLParse::LoadTheme using /usr/share/mythtv/themes/default-wide/mythnative-ui.xml
sh: cannot create /usr/share/mythtv/mytharchive/.tmp/logs/progress.log: Directory nonexistent


/usr/share/mythtv/mytharchive/.tmp
This is the working directory I created through the setup gui.
The directory did not appear in the directory tree.
I tried creating this manually as sudo but import still doesnt work.
I should imagine this is something to do with permissions but it has the same permissions as the other files within /usr/share/mythtv of  drwxr-xr-x

Can anyone give me a pointer?

Im also unable to watch or import a DVD. Is this related as well?
If not Ill create another post on that subject.

Thanks

Gordon

---

### Post by GordonEndersby on 2008-04-28
OK, no answers so I had bit more of a play.

I ran update against the weekly fixes.
Still no good.

I manualy created the directories:
/usr/share/mythtv/tmp
/usr/share/mythtv/tmp/work
/usr/share/mythtv/tmp/logs
/usr/share/mythtv/tmp/config

The owner is root and I set read write permissions for everybody.
Should the owner be mythtv and what should the permissions be?

progess.log now shows a new error:
2008-04-28 13:14:09.122 Archive DB version: 1160, Local DB version: 1214
2008-04-28 13:14:09.134 Import recording using chanID: 1001
2008-04-28 13:14:09.134 Archived recording xml file: /media/disk/Doctor Who/1001_20080419181800.nuv.xml
QSqlQuery::value: not positioned on a valid record
2008-04-28 13:14:09.136 Copying video file.
2008-04-28 13:14:09.136 copying from /media/disk/Doctor Who/1001_20080419181800.nuv
2008-04-28 13:14:09.136 to /1001_20080419181800.nuv
2008-04-28 13:14:09.136 ERROR: Unable to open destination file
2008-04-28 13:14:09.136 Do you have write access to the directory?

This looks like its trying to write to the root of the filesystem.
Where should it be writing to and how do I change it?

Thanks

Gordon

---

### Post by GordonEndersby on 2008-04-29
Ive now tried re-installing with full release rather than the release candidate and Ive still got the same problem.
So restored the previous version as documented above.

Can anyone help me?

Thanks

Gordon

---

### Post by superm1 on 2008-04-29
This sounds like you might be working from a remote frontend.  If so, there is an open bug out there that mytharchive only works on the machine with the recordings, or if you set the recordingprefix:

[https://bugs.edge.launchpad.net/ubuntu/+source/mythplugins/+bug/118700](https://bugs.edge.launchpad.net/ubuntu/+source/mythplugins/+bug/118700)

---

### Post by GordonEndersby on 2008-04-29
Ill have a look at that.
Mines a combine frontend/backend on same machine.
It might give me some pointers on where the directories are configured.

Gordon

---

### Post by GordonEndersby on 2008-04-30
Getting a bit further.

I turned on logging for mysql and watched the queries being run for the archiving and found this:
SELECT dirname FROM storagegroup WHERE groupname = 'Default' AND hostname = 'mythtv'

There was no value set.
So I set the dirname value for default in the storage groups settings in the backend setup.

Now I can import the archived program.

But in the archive log Im now getting the error:
ICE default IO error handler doing an exit(), pid = 7064, errno = 32
It hasnt stopped the import of the file but Id better find out what it means and try and fix it.

Unless anyone knows what this is and can give me a few pointers?
Its taken me a week to get this far.

Gordon

---

### Post by GordonEndersby on 2008-04-30
OK, found a post refering to the error message.
Fix was to delete .ICEauthority in the users home directory.
It solved that error.

The only thing broken now is the cancel and update buttons.
I think Ill live with that for a while.

A I realy the only user of Mythbuntu with this problem?

Gordon

---

