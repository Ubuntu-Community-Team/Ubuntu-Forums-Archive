---
title: "Cannot play WMV file in Jaunty"
date: 2009-04-30
forum: Multimedia Software
---

### Post by Eric B on 2009-04-30
Hi. It might just be a missing package issue, but I cannot play WMV. I was ale to do this with a previous release. I tried installing different players, but none of them seem to decode wmv files.

Any suggestions?

---

### Post by CheesyD on 2009-05-03
I have the same problem. The wmv files played without a hitch in Intrepid. Nothing but sound in Jaunty...

---

### Post by Eric B on 2009-05-04
I cant even get sound. the players either close or complain.

---

### Post by CheesyD on 2009-05-04
The wmv's won't play on my Acer laptop that is dual boot with XP and Jaunty (ext3). I also have an old desktop with nothing but Jaunty on it (ext4) and when I tried to play the same wmv file it wouldn't play... said missing plugins. It then found and installed the gstreamer0.10-plugins-ugly. Once that was installed the wmv file played just fine on the desktop, sound and all.

I'm going to go check my laptop and see if it has the same plugins installed. Will report back shortly.

---

### Post by CheesyD on 2009-05-04
Ok, so I checked my Acer laptop and the gstreamer0.10-plugins-ugly were already installed. I had it do a complete uninstall of that, and tried to play the wmv file. I received the message that plugins were missing and it searched and found the gstreamer0.10-plugins-ugly and asked if I wanted to install. I did. Once it was reinstalled I rebooted and then tried the wmv file. Nothing changed. I still have sound but no video.

Weird.

---

### Post by pastalavista on 2009-05-04
Open Synaptic Package Manager, in the search, type 'gstreamer'... then install them all with Windows Media in the description

make sure you have Universe and Multiverse checked in your repositories

---

### Post by CheesyD on 2009-05-04
> **pastalavista said:**
> Open Synaptic Package Manager, in the search, type 'gstreamer'... then install them all with Windows Media in the description

make sure you have Universe and Multiverse checked in your repositories

Tried that... still just sound... no video. 

I even tried a reinstall of Jaunty and switched to ext4 as that is what I have on my desktop and the wmv's play fine on that box. No go...

---

### Post by Another Monkey on 2009-05-15
Do you have Intel graphics?  You might want to read this [http://ubuntuforums.org/showthread.php?t=1134473](http://ubuntuforums.org/showthread.php?t=1134473)

---

### Post by Eric B on 2009-05-15
I don't have the original WMV files that I was trying to view, but I got a new one and that looks like it may have done the trick. Wonder why the new drivers would play everything else.

---

### Post by Eric B on 2009-06-10
That did indeed work, but other things started displaying worse. It wasn't worth it just for wmv video.

---

