---
title: "vlc stream no audio"
date: 2008-03-08
forum: Multimedia &amp; Video
---

### Post by o55555o on 2008-03-08
Hi all, here is an absolute beginner talking.

I installed ubuntu just now, everything is fine except that, I normally watch TV something called "VLC stream" , a service which my ISP provides for free, you just need to set it up properly on your modem.

Now, I have the VLC plugin for ubuntu Gutsy Gibbon 7.10 installed, (following instructions provided by their website), and video is just as good as under win xp, but no sound. Reboot doesn't help, neither reinstall the plugin.

So I am just wonering if someone here has similar issue, or could anyone help me with this.

thank you all

---

### Post by hyperair on 2008-03-08
Could you post a link to the site you saw these instructions? I can't seem to find them. By the way, installing VLC and its plugin on Ubuntu is as simple as installing the vlc and mozilla-plugin-vlc packages in Synaptic Package Manager, then restarting Firefox.

EDIT: Never mind I found the instructions. Now what we need to see is if you've installed them correctly. 
```
apt-cache policy vlc mozilla-plugin-vlc
```

---

