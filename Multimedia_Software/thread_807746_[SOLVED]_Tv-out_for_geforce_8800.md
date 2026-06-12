---
title: "[SOLVED] Tv-out for geforce 8800"
date: 2008-05-26
forum: Multimedia Software
---

### Post by king vash on 2008-05-26
So i have a TV (low res) that I would like to use as a second moniter. My computer eVGA geforce 8800 has a tv out so i plugged in a svideo to composite cable and then I googled "tv out geforce 8800" and started modifying my Xorg according to this guide ([https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut))

I stared with Xorg.conf.txt (see the attachment)
and make Xorg.conf.mod.txt, however it didn't work

what should I do? did I make some small mistake? is this not the way to do it on a geforce 8800? is there an easier way?

---

### Post by kpkeerthi on 2008-05-26
Restore your xorg.conf if you have made any changes.
Install nvidia-settings using synaptic.
Connect your TV and run nvidia-settings. Use auto-detect and select your TV as a second monitor.

* Nvidia settings should be available in Applications -> System Tools menu
* To run it from command-line, type the below command.
```
nvidia-settings
```

---

### Post by king vash on 2008-05-26
Thanks so much kpkeerthi for your reply

After Using nvidia-settings everything worked

ps 

I had to use 
```
Sudo nvidia-settings
```

---

