---
title: "VLC Skins"
date: 2007-05-17
forum: Multimedia &amp; Video
---

### Post by Bohlio on 2007-05-17
Can someone give me the code to put into terminal that will extract a folder on my desktop called "vlc-skins.zip" to the skins folder, which is located at "/usr/share/vlc/skins2". Im trying to install skins into the media player but when i drag and drop I get a permissions error. From my basic understanding, the sudo command acts like you are logged in under "root" which is kinda like Admin in windows, and will let me get around the permissions error?
Thanks in advance :)

---

### Post by taurus on 2007-05-17
You can try using 

```
gksudo nautilus
```

---

### Post by Bohlio on 2007-05-17
thank you, that worked perfectly.

Just to check if my understanding is correct...
Nautilus is the file browser
Sudo allows you to run commands under "root"
and the gk is for....?

---

### Post by taurus on 2007-05-17
If you want to run as root from a terminal, you would use sudo.  But if you want to run some GUI app as root, then you need to use gksudo.  Running "sudo nautilus" can cause nightmares for you later.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Bohlio on 2007-05-17
Ahhhh, Thank you for the link Taurus, It was very helpful and informative. The community probably is the best part about Ubuntu :-P

---

