---
title: "remote desktop/vnc from ubuntu 10.04 into windows vista"
date: 2010-05-12
forum: Networking &amp; Wireless
---

### Post by _BIG_ on 2010-05-12
ive tried searching and reading thru a sea of text on this and have gotten more confused as ive gone on lol.

i have realvnc enterprise server installed on my home desktop with windows vista and can connect to it perfectly using realvnc viewer from other windows systems.

when i try to connect from ubuntu 10.04 using remote desktop viewer with protocol set to VNC and host set a few different things ive tried (example host: 192.168.111.1 or host: 192.168.111.1:5XXX or host: 192.168.111.1::5XXX) i get back a reply of "Authentication method to host 192.168.111.1 is unsupported. (5)"

i have installed these packages in synaptic package manager in attempts to help get this workin from reading other threads:
libgtk-vnc-1.0-0
tsclient
vinagre
vino
xvnc4viewer

i have also downloaded "VNC Enterprise Edition Viewer for Linux (x64)
Stand-alone Viewer
Version 4.5.3"
from [http://www.realvnc.com/download/enterprise/4.5.1''both](http://www.realvnc.com/download/enterprise/4.5.1''both) the executable(which i dont know how to run) and the gzipped file(again dont know what to do with) to try and solve this problem.

ive read many suggestions saying things about ssh but would prefer not to have to go thru that as i am very new to linux and feel i might get even more lost with that.

from what i understand realvnc encrypts everything so security shouldnt be too bad with it i dont think


thanks again

---

### Post by terminator14 on 2010-07-02
I don't know if you're still having problems with this after 2 months but when you download the viewer from realvnc.com, it comes as an executable. To run it, copy it to your desktop (or /usr/bin if you want to run it from terminal) and give yourself execute permissions for that file. To do this, open terminal, cd to the folder it is located in, and run chmod on it. Eg:

```
cd [COLOR="Sienna"]~/Desktop[/COLOR]
sudo chmod a+x [COLOR="Red"]vnc-E4_5_4-x64_linux_viewer[/COLOR]
[COLOR="Red"]./vnc-E4_5_4-x64_linux_viewer[/COLOR]
```

Change [COLOR="Red"]vnc-E4_5_4-x64_linux_viewer[/COLOR] to the filename you downloaded and [COLOR="Sienna"]~/Desktop[/COLOR] to the folder where you placed it. By default it should actually be in ~/Downloads when firefox downloads it.

---

