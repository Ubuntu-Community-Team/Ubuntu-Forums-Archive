---
title: "Cannot play MP3 files with Amarok via SMB"
date: 2007-11-11
forum: Multimedia &amp; Video
---

### Post by snakyjake on 2007-11-11
**_Situation:_**

I'm trying to play mp3 music files from a network folder hosted via Windows network file sharing using SMB.

I would like to use Amarok to open mp3 files via SMB without needing to mount the share.  Is this possible?  What else can I try to make this work correctly and as intuitively expected?

**_Repro Steps:_**

I browse to the mp3 file via Konqueror, and I open the mp3 file I wish to listen with Amarok.

Amarok reports an error when trying to open the mp3 file via SMB.


**_Error Message from Amarok:_**

Error Loading Media
No suitable input plugin.  This often means that the url's protocl is not supported.  Network failures are possible causes.
smb//192.168.0.200/music/filename.mp3


**_Troubleshooting:_**

1.  I can play the mp3 files if I copy the files locally. 
2.  I can play the mp3 files over the network if I mount the SMB network location.


Thank you.

---

### Post by Witchlight on 2007-11-14
Ya Im having issues playing music via my smb share as well..

I can play tunes fine locally but my music is on setup on a file server.
I have mounted the music share in the fstab like I always have before but when I try to play i get maybe 2sec of the start then it no sound.

fstab 
//192.168.1.110/tunes        /media/black/tunes        smbfs    auto,username=****,passwd=****,uid=1000,umask=000,user 0 0


Worked fine in FF but not GG.

---

### Post by tech9 on 2007-11-14
try vlc...
sudo apt-get install vlc

---

### Post by Witchlight on 2007-11-14
Rythmbox gives the same results so its not an amarok specific issue.

---

### Post by Rolie on 2007-12-05
I just solved this error for me with Mandriva 2008.0, and I did this by installing xine-smb. For me that is done with
```
# urpmi xine-smb
```
but with the Debian package management utility I think it would be something like
```
# apt-get install xine-smb
```

---

### Post by AxMstrLP on 2008-06-02
I'm running kubuntu 8.04.  Adept shows amarok-xine 1.4.9.1 installed.  I can't find a package called xine-smb.  Is it supposed to be integrated now?

I'm getting the same "don't know how to handle smb url"... :(

---

