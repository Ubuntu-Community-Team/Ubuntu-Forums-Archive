---
title: "VLC Media Player - play complete folder &amp; adding to queue"
date: 2019-03-06
forum: Multimedia Software
---

### Post by octoberrust2 on 2019-03-06
There's already a thread by that title*, but it's closed and marked as solved, but IMHO it's just a workaround.
I am not satisfied with having to open a folder an mark all audio files to open them in VLC.

Isn't there a way to right click on just the folder to achieve this?



* [https://ubuntuforums.org/showthread.php?t=2236236](https://ubuntuforums.org/showthread.php?t=2236236)

---

### Post by deadflowr on 2019-03-06
*Thread moved to **Multimedia Software***

---

### Post by Holger_Gehrke on 2019-03-07
Since you've put 'xubuntu' into the heading I assume you're using Thunar as your file manager. In Thunar you can set user defined actions. Simply create a new action with 'vlc %U' as the command and assign it to be available for folders, videos, audio files and images.

Holger

---

### Post by ajgreeny on 2019-03-07
The simplest way is to use the VLC menu **Media  -> Open Directory**.

It will then add all files to a playlist and proceed to play them in order.

---

### Post by octoberrust2 on 2019-03-07
> **Holger_Gehrke said:**
> Since you've put 'xubuntu' into the heading I assume you're using Thunar as your file manager. In Thunar you can set user defined actions. Simply create a new action with 'vlc %U' as the command and assign it to be available for folders, videos, audio files and images.

Holger

Xubuntu/Thunar, exactly! (In Ubuntu this is already implemented.)

I wasn't familiar with Thunar and its "actions", now it works like a charm. Thank you very much indeed!

---

### Post by octoberrust2 on 2019-03-07
> **ajgreeny said:**
> The simplest way is to use the VLC menu **Media  -> Open Directory**.

It will then add all files to a playlist and proceed to play them in order.

To me this would be even more inconvenient than dragging and dropping selected files from Thunar to VLC.
Additionally, by using the VLC menu/"open directory" one cannot pick more than one folder.

Holger's "action" (see above) works perfectly though!

---

### Post by ajgreeny on 2019-03-09
Indeed it does, and I use that method in Xubuntu as well as the VLC -> Open Directory menu item, but use what works best for you.

I did not see that you are using Xubuntu otherwise I might also have thought about using these custom actions, many of which I use for various file actions and also making changes to audio/video files.

Please now mark as SOLVED from the Thread Tools menu up-top if this is solved to your satisfaction. It is a great help to users searching the forum.

---

