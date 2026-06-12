---
title: "Install realvnc instead of tightvnc, 11.10 desktop"
date: 2011-10-25
forum: Networking &amp; Wireless
---

### Post by lparsons42 on 2011-10-25
I have found that on my Kubuntu desktop workstations, when I run ```
sudo apt-get install vncviewer
``` I end up with tightvnc installed.  However on a Ubuntu 10.10 server install, the same command results in realvnc instead.  

In using both, I find that realvnc has a distinct advantage, in that scrolling actually works.  If I am connecting to a dual-display system running vnc server and I scroll in tightvnc, I cannot scroll back.  However realvnc allows me to do that.  

Hence I would like to uninstall tightvnc on my workstations and install realvnc instead.  Is there a way to do this with apt-get?  I can't find specific entries for realvnc, though I might not be looking in the right place.

---

### Post by lparsons42 on 2011-10-25
I found it.  [http://www.plugintolinux.ca/smf/index.php?topic=815.0]("http://www.plugintolinux.ca/smf/index.php?topic=815.0")

Apparently RealVNC is hiding out as the package 'xvnc4viewer' - at least in desktop installations of ubuntu.  Why it comes up by default in ubuntu server I have no idea.  Personally, I see no advantage to tightvnc in ubuntu (though I may be missing something), and highly value the fact that RealVNC allows me to scroll in **both** directions.

---

