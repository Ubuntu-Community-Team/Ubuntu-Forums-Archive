---
title: "VNC viewer that will sen Ctrl-Arrow to my local OS?"
date: 2012-07-30
forum: Networking &amp; Wireless
---

### Post by carwe on 2012-07-30
Hi,

I'm running Ubuntu 12.10 and often run VNC to a host at my job. I keep the VNC viewer maximized in one of my workspaces, but I'd like to be able to switch from it by Ctrl-Arrow, as usual. It doesn't work since the VNC viewer will send these keys to the remote host. I don't want that, I want that to switch the local workspace, so I'd like those keys to get interpreted by my local OS.

I'm using Vinagre 3.4.2, "Remote Desktop Viewer", for the moment.

Is there any other viewer that will let me control which keys are sent to the remote host and which are interpreted by my local OS?

Or is there any other way to solve this?

Thanks,
Carl

---

### Post by OM55 on 2012-07-30
Hello Carl,

You probably can achieve what you want to do with Remmina (it is in the Software Center). Remmina is (in my opinion) one of the best VNC and RDP clients out there, and it allows very easily to decide whether the CTRL keys are sent to the host or to the local computer. You can do that with a host key, or by clicking on the keyboard icon (when you are connected to the host).

You can also pre-define a few keys for specific tasks. Keep in mind that you will have hard time to define a combination (like ALT-TAB or similar) because those are already used within the local or remote OS.

Hope that helps.

---

### Post by carwe on 2012-07-31
> **OM55 said:**
> Hello Carl,

You probably can achieve what you want to do with Remmina (it is in the Software Center). Remmina is (in my opinion) one of the best VNC and RDP clients out there, and it allows very easily to decide whether the CTRL keys are sent to the host or to the local computer. You can do that with a host key, or by clicking on the keyboard icon (when you are connected to the host).

You can also pre-define a few keys for specific tasks. Keep in mind that you will have hard time to define a combination (like ALT-TAB or similar) because those are already used within the local or remote OS.

Hope that helps.

Just tried it, seems to work as I want! Thanks!

---

### Post by OM55 on 2012-07-31
You are very welcome.

(No you can mark this thread as 'Solved').

---

### Post by carwe on 2012-08-01
Unfortunately Remnia showed up to be rather buggy (reported by many I have seen). Also it doesn't send the AltGr key which is neccessary for me. A number of characters aren't copied correctly when doing copy/paste.

Is there any other, more general, way to control which keys are catched by an application (the VNC viewer in this case and) which are left to the OS? In that case I could choose VNC viewer independently on such things (instead make sure to find a viewer that isn't buggy, that can send AltGr and works well sith copy/paste)?

---

