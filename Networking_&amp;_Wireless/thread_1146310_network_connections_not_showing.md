---
title: "network connections not showing"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by sdahlin on 2009-05-02
Just installed 9.04 and I was experimenting with tweaking network setup using the files itself.  However, I restored the files back to their original state.  I have a wired connection working but the icon in the menubar does not show any connections and it does not recognize the available wireless connection.  How can I restore the connections manager to its original state?

Thanks,
Steve

---

### Post by stretch427 on 2009-05-02
Do you need restricted drivers?  I know for my own gear it wouldn't show my WIFI until I had installed the restricted drivers. 

System->Administrator->Hardware Drivers

And try and get those updates. I am assuming you have Internet just not the icons? Or they aren't showing your available connection. 

At any rate check to see if you need them. I know mine wouldn't work until I had them installed.

---

### Post by RedSingularity on 2009-05-02
You can reinstall the network manager if all else fails.

---

### Post by stretch427 on 2009-05-02
maybe check out this link

[http://ubuntuforums.org/archive/index.php/t-52916.html](http://ubuntuforums.org/archive/index.php/t-52916.html)

Hopefully it helps

---

### Post by sdahlin on 2009-05-02
So how to I reinstall the network manager?

Thanks,
Steve

---

### Post by stretch427 on 2009-05-02
To reinstall the network Manager with GNOME

```
sudo aptitude reinstall network-manager
```

Full details here at the bottom I didn't want to type it all out

[http://ubuntuforums.org/showthread.php?t=246643](http://ubuntuforums.org/showthread.php?t=246643)

---

