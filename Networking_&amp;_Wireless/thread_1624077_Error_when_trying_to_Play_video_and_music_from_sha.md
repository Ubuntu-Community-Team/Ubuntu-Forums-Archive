---
title: "Error when trying to Play video and music from shared Windows folder (through samba)"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by edistaeonas on 2010-11-17
Hello,
I would like to **read multi-media files** with my (K)Ubuntu computer, files that are stored in a shared folder, on another computer in my **network**, running **Windows** 7. But when I try to open a video or a music file, I get an **error**.

Local media files on my Linux machine play well with VLC.
I can access the Windows shared folder in my Linux laptop, and I can open small files, like text files or photos. The problem is when I try to play an avi or mp3 file; VLC shows the error message!

I used Kubuntu 10.10
Dolphin file manager, then "Network" places, then Samba Shares, Workgroup, MyPCName, then I log in with user & password of my Windows PC, and I see the remote shared folder. I try to open a video with VLC Media Player, and it says

* "You're input can't be opened : VLC is unable to open the MRL. 'smb://john@windowspc/video/test.avi'.  Check the log for details".*

I guess it's because it cannot read directly files on the remote location and wants to copy it in a temporary folder locally, but I don't know enough to work around this issue...
The system log doesn't say anything about the error.. (unless I opened the wrong log)...

Has any one managed to play directly in Linux, video & music files stored on Windows, within the home network?

Thank you very much.

---

