---
title: "VNC Port Number"
date: 2011-08-30
forum: Networking &amp; Wireless
---

### Post by tokyo-joe on 2011-08-30
For some reasons, I would like to control my Ubuntu machine with VNC "NOT" via default port 5900.

How can I configure VNC to change the connection port?

---

### Post by Wayne_V on 2011-08-30
with x11vnc you can use -autoport <base port#>

with Xvnc you can use -rfbport <port>

....

---

### Post by georgemc on 2011-08-30
With the "Configuration-editor" you can change the port.

Applications > System Tools > Configuration-editor >  desktop  >  gnome  >  remote_access

I'm not sure if the "Configuration-editor" is installed by default or not.  If not look for it in the Software Center or in synaptics.

Edit: This is from the 10.04.3 LTS perspective.  Should apply to other versions.

George

---

