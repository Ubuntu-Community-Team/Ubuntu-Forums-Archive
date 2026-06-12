---
title: "VLC not defult player nor can it play at all when using samba"
date: 2008-02-13
forum: Multimedia &amp; Video
---

### Post by jijin on 2008-02-13
Hello,

I seem to have a problem with VLC. It absolutely refuses to play a mp3 from a local network on a windows machine via samba.

VLC will play through ntfs-3g just fine and it is setup as the default player in both the mp3 properties as well as the system>pref>preferred apps

It works perfectly other then anytime I access media via samba.

Movie player keeps coming up and after I installed the codecs it worked great.

Any ideas?

Thanks in advance.

EDIT: I also wanted to add dragging it into VLC does not work either. I do get a plus sign but nothing else.

---

### Post by tact on 2008-02-13
I think I struck this some time ago with vlc.  If i am not mistaken I believe I got around it by actually mounting the remote folder across samba, maybe using CIFS I am not sure...  then when vlc can see the file as if its on the local machine (eg. /media/remote_folder/something.mp3) then it would play.

Must you use vlc to play mp3 audio files?  rythymbox supports DAAP for playing/sharing music across network.

---

