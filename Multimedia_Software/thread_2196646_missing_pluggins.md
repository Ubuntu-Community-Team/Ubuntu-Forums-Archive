---
title: "missing pluggins"
date: 2013-12-30
forum: Multimedia Software
---

### Post by hero2011 on 2013-12-30
I have just installed my new ubuntu in a mini laptop.but the problem is that i can not play any music and video using the rhythmbox player or even video player.it tells me i need MPEG 4 AAC decoder plugin.how can get them since am trying to dowload but in vain.please assist me.

---

### Post by dsc1596 on 2013-12-30
You are probably trying play restricted formats, which isn't a bad thing, it's just that the plugins you need are proprietary. Try [this link]("https://help.ubuntu.com/community/RestrictedFormats"). It walks the reader through installing ubuntu-restricted-extras and also shows how to enable encrypted DVD playback.

---

### Post by Dreamer Fithp Apprentice on 2013-12-30
> **hero2011 said:**
> I have just installed my new ubuntu in a mini laptop.but the problem is that i can not play any music and video using the rhythmbox player or even video player.it tells me i need MPEG 4 AAC decoder plugin.how can get them since am trying to dowload but in vain.please assist me.Most video players should tell you EXACTLY what codec you are missing and usually offer to install it for you. If your's doesn't, I suggest you install synaptic if it didn't come on your system (type "sudo apt-get install synaptic" without the "s in a terminal and press the [enter] key, etc.). Then open synaptic and search whatever it said you needed and install it. If that doesn't do it you might try searching "gstreamer" and installing all you find. If that still doesn't do it try searching other words that might be associated like "codec". Or, easier, just install vlc (sudo apt-get install vlc) and use it. Vlc will play almost anything right out of the box. You may occasionally still have to look for a codec or plugin, especially with formats like flv, but plain vlc will play any common formats.

BTW, if synaptic hangs on you and won't respond, you get out of it by pressing cntrl-alt-F1 (all three keys at the same time and logging in on the resulting black and white text interface, called a tty, by entering your username, pressing enter, entering your password, and pressing enter again. After you log in succesfully, type "sudo pkill synnaptic" and press enter. Then type "exit" and press enter. Then cntrl-alt-F7 to get back to your desktop. Hopefully you won't have to do that but synaptic has been buggy for me lately. If you go the vlc route you won't need to mess with synaptic anyway, just install it in a terminal.

---

### Post by Yellow Pasque on 2013-12-31
```
sudo apt-get install gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly
```

---

### Post by Bucky Ball on 2013-12-31
Also, you could install:

ubuntu-restricted-extras

Not sure if you have VLC installed but that drags in a lot of what you are probably missing.

---

