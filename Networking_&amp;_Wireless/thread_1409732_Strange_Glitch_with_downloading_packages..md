---
title: "Strange Glitch with downloading packages."
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by Dex1nonly on 2010-02-17
Ok, so I try to install GLX-Dock, however I get the following.

> Failed to download package files.
Check your internet connection.

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cairo-dock/cairo-dock-data_2.0.9-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cairo-dock/cairo-dock-data_2.0.9-0ubuntu1_all.deb) Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111: Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gtkglext/libgtkglext1_1.2.0-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gtkglext/libgtkglext1_1.2.0-1ubuntu1_i386.deb) Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111: Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cairo-dock/cairo-dock-core_2.0.9-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cairo-dock/cairo-dock-core_2.0.9-0ubuntu1_i386.deb) Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111: Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cairo-dock-plug-ins/cairo-dock-plug-ins-data_2.0.9-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cairo-dock-plug-ins/cairo-dock-plug-ins-data_2.0.9-0ubuntu1_all.deb) Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111: Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cairo-dock-plug-ins/cairo-dock-plug-ins-integration_2.0.9-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cairo-dock-plug-ins/cairo-dock-plug-ins-integration_2.0.9-0ubuntu1_i386.deb) Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111: Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cairo-dock-plug-ins/cairo-dock-plug-ins_2.0.9-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cairo-dock-plug-ins/cairo-dock-plug-ins_2.0.9-0ubuntu1_i386.deb) Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111: Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xdotool/xdotool_20090330-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xdotool/xdotool_20090330-1_i386.deb) Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111: Connection refused)


I've Googled and Googled but nothing I've tried worked. sudo-apt get update gets similar errors. It was working fine a few days ago. I can still browse and download via my browser just fine. I can even install packages if I download them through my browser.

I read that it's trying to go through a proxy server or something, but I don't recall installing anything like that.

---

### Post by lidex on 2010-02-18
Are you using the Google Chrome browser? Seems there is an option setting for proxy in it that can cause that.

---

### Post by Dex1nonly on 2010-02-18
> **lidex said:**
> Are you using the Google Chrome browser? Seems there is an option setting for proxy in it that can cause that.

Yes I am. When I go into Options and click on Proxy Settings it brings up the Network Proxy Preferences. Direct Internet Connection is selected.

Also, I'm on a wireless network if that matters.

---

### Post by lidex on 2010-02-18
In those chrome options, click the reset button and then click "Apply System-Wide", making sure the direct connection setting remains selected.

---

### Post by jittuji on 2010-02-23
I too faced a similar issue and was looking up to Ubuntu Forums for a    solution. 
I did not use Google Chrome; tried checking my proxy settings on the    browsers 
(MineField & Opera); 'dpkg' dint help either. I forgot if ever i    installed a proxy. 
It din't lead me anywhere out of the issue until i found the below    thread to fix it.

You may try the same thing as follows. It works well now. :)
 
 $ unset http_proxy ..................... ** It will clear the proxy
  $ unset ftp_proxy ....................... ** It will clear the proxy
  $ sudo apt-get <abc> ................ ** It will work again

Reference Thread:
**[http://ubuntuforums.org/showthread.php?t=1177161](http://ubuntuforums.org/showthread.php?t=1177161)**

---

