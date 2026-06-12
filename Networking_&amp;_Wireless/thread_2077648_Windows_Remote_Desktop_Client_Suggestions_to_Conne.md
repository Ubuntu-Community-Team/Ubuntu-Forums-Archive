---
title: "Windows Remote Desktop Client Suggestions to Connect to Ubuntu Server"
date: 2012-10-29
forum: Networking &amp; Wireless
---

### Post by akm3 on 2012-10-29
Hi,

Does anybody has specific suggestions for a neat remote desktop solution to connect to an Ubuntu server from a Windows machine (in my case Windows 7 to Ubutnu 12.04 64-bit).

I have tried free VNC clients like tightVNC, as well as NX client. Are there other options to suggest?

I am specifically concerned with graphical remote access. One problem that I have faced is that I can connect remotely, but I do not see the applications open on the remote desktop, instead see an empty desktop (of course processes are running as checked by ps -e), e.g. I have eclipse running but I cannot see my active session, unless that I kill the process and re-open it, which is not very desired. (not sure if this is related or helps, but server has two monitors, extended desktop)

If you have had any other experience remotely and graphically accessing your linux from a windows machine, I appreciate you to share it with me:)

---

### Post by reptilezone2002 on 2012-10-29
> **akm3 said:**
> Hi,

Does anybody has specific suggestions for a neat remote desktop solution to connect to an Ubuntu server from a Windows machine (in my case Windows 7 to Ubutnu 12.04 64-bit).

I have tried free VNC clients like tightVNC, as well as NX client. Are there other options to suggest?

I am specifically concerned with graphical remote access. One problem that I have faced is that I can connect remotely, but I do not see the applications open on the remote desktop, instead see an empty desktop (of course processes are running as checked by ps -e), e.g. I have eclipse running but I cannot see my active session, unless that I kill the process and re-open it, which is not very desired. (not sure if this is related or helps, but server has two monitors, extended desktop)

If you have had any other experience remotely and graphically accessing your linux from a windows machine, I appreciate you to share it with me:)


install x11vnc on ur ubuntu server and connect with a vnc client from windows

---

### Post by akm3 on 2012-10-29
> **reptilezone2002 said:**
> install x11vnc on ur ubuntu server and connect with a vnc client from windows

I have the x11vnc. It looks fine, except that on the client, I can not see applications already open in the server. I see the processes are open, but I cannot see the windows.

Is it related to the VNC client I use in Windows? or the fact that ubuntu server has two monitors, while Windows client has one?

Can remote desktop clients handle this?

Any suggestion for a seamless client on Windwos?

---

### Post by Derek Karpinski on 2012-10-29
[http://www.teamviewer.com/en/index.aspx]("http://www.teamviewer.com/en/index.aspx")

Works great and seems to be the least laggy I've used.

---

### Post by reptilezone2002 on 2012-10-30
> **akm3 said:**
> I have the x11vnc. It looks fine, except that on the client, I can not see applications already open in the server. I see the processes are open, but I cannot see the windows.

Is it related to the VNC client I use in Windows? or the fact that ubuntu server has two monitors, while Windows client has one?

Can remote desktop clients handle this?

Any suggestion for a seamless client on Windwos?

try installing xrdp on linux machine then connecting from windows using remote desktop

---

### Post by reptilezone2002 on 2012-11-04
well in my pc i can see the current session with opened windows & im using x11vnc even in my android phone i can see the windows .. have u tried xrdp & try connecting from a windows remort desktop sharing
note im using ubuntu 12.04 with the gnome-panel ( classic gnome)

---

### Post by steeldriver on 2012-11-04
> **akm3 said:**
> I have the x11vnc. It looks fine, except that on the client, I can not see applications already open in the server. I see the processes are open, but I cannot see the windows.

Is it related to the VNC client I use in Windows? or the fact that ubuntu server has two monitors, while Windows client has one?

I think it's most likely related to lack of VNC support for Compiz - if you switch your session to ubuntu-2d (metacity) or gnome-classic it should work. As far as I can tell the same applies to xrdp - I couldn't get that to work with 3d either.

---

