---
title: "which flash player do I need for ubuntu 9.04?"
date: 2009-10-31
forum: Multimedia Software
---

### Post by Gatorade on 2009-10-31
I'm trying to watch some youtube vids and its telling me to download the lastest flash player.

I see 3 different options for linux, YUM , .tar.gz , and rpm 

which one should I select?

---

### Post by ScottLij on 2009-10-31
You should get the version from the Ubuntu repositories.  Open a terminal and type

```
sudo apt-get install flashplugin-nonfree
```

to install Adobe Flash Player.

---

### Post by Gatorade on 2009-10-31
hi, 

I just tried that and its still telling me I need to install adobe flash player when I go on youtube.

---

### Post by ScottLij on 2009-10-31
> **Gatorade said:**
> hi, 

I just tried that and its still telling me I need to install adobe flash player when I go on youtube.

I think you might have to restart firefox after installing flash.  It should appear under Tools -> Add-ons -> Plugins as 'Shockwave Flash'.

---

### Post by oboedad55 on 2009-10-31
The file in Synaptic is called "adobe-flashplugin". That will give you version 10 and your videos will work.

---

### Post by Gatorade on 2009-10-31
> **ScottLij said:**
> I think you might have to restart firefox after installing flash.  It should appear under Tools -> Add-ons -> Plugins as 'Shockwave Flash'.

hey, thanks.

restarted and its working now.

---

### Post by lsutiger on 2009-10-31
I just upgraded to the latest version of Adobe flash, and OMG! I HOVE NO FLCIKERING!! Awesome! 

It's finally fixed!

---

