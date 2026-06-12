---
title: "help installing wicd"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by l3ecl on 2011-05-08
I removed network manager on my laptop via sudo apt-get remove --purge network manager network-manager-gnome but now I can't install wicd because I don't have internet. 

Help

---

### Post by 73ckn797 on 2011-05-08
You will need to make a wired connection or reinstall Ubuntu. The wired connection is easiest. If you ever plan on doing this again then you need to select wicd first to install and also select network manager to uninstall. You really did not need to uninstall network manager. You can go to System/Preferences/Startup Applications and just turn network manager off. It will always be there if you ever have a wicd problem.

You can also look here in your system files: ```
/var/cache/apt/archives
``` and look to see if the network-manager.deb (I believe that is the name) file is stored. You could right click on it and install with "Gdebi Packager Installer". You may be able to retrieve the file from the LiveCD though that may require a little more effort.

---

### Post by l3ecl on 2011-05-08
Yeah I noticed what I did was stupid.

I've attached an ethernet connection to my laptop but there's still no Internet connection.

---

### Post by 73ckn797 on 2011-05-08
> **l3ecl said:**
> Yeah I noticed what I did was stupid.

I've attached an ethernet connection to my laptop but there's still no Internet connection.
Guess that I should have thought about that obvious issue.

---

### Post by 73ckn797 on 2011-05-08
If you have another computer that is connected, try this link. I think you can download the package, transfer it to a USB flash and copy to your laptop. Then install as I suggested before with Gdebi Package Installer.

```
http://packages.ubuntu.com/natty/network-manager
```

---

### Post by l3ecl on 2011-05-08
oh wow that's really awesome. I didin't know that about that. I got my ethernet working and I can continue from there. Thanks!

---

### Post by 73ckn797 on 2011-05-08
> **l3ecl said:**
> oh wow that's really awesome. I didin't know that about that. I got my ethernet working and I can continue from there. Thanks!
It looks like you are using Lucid? Just replace Natty with Lucid in the link or go to ```
http://packages.ubuntu.com
``` and select the release you are using.

---

### Post by l3ecl on 2011-05-08
I installed network-manager from the archives and got my ethernet working, then went on to install wicd but it got stuck to "Obtaining an Ip Address" so back to network-manager for me.

I got everything back to square one anyhow and marking this thread solved. Thanks 73ckn!

---

### Post by 73ckn797 on 2011-05-08
> **l3ecl said:**
> I installed network-manager from the archives and got my ethernet working, then went on to install wicd but it got stuck to "Obtaining an Ip Address" so back to network-manager for me.

I got everything back to square one anyhow and marking this thread solved. Thanks 73ckn!

Did you use Startup Manager to disable NM and enable WICD? There could be a conflict. 

You are welcome.

---

