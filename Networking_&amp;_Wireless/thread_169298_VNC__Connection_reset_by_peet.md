---
title: "VNC : Connection reset by peet"
date: 2006-05-02
forum: Networking &amp; Wireless
---

### Post by lilian on 2006-05-02
Hi,

I have ubuntu breezy installed on an AMD64. When I was on hoary, before the upgrade, I have succeeded configuring the remote desktop and I was able to access my opened session from another computer with
"vncviewer pclilian".

After that, I installed vncserver to remotely open a new session instead of taking control of the opened one. For this, I followed this : [http://ubuntuforums.org/printthread.php?t=42941](http://ubuntuforums.org/printthread.php?t=42941)

It was ok, the vncviewer command take me to the gdm login.

Since the upgrade to breezy, it does not work anymore.

Now, I am trying to make the remote desktop working again. I have uninstalled vncserver. When I try to connect to my ubuntu box, I always get "connection reset by peer (104)".

In the login screen configuration, I have the following checked under the Security tab (translated from french :S) :
-Activate XDMCP
-Display menu with pictures
-Display actions menu
-Allow XDMCP execution selector from the login screen
-Always prohibit TCP connections to X server (disable all remote connections but does not affect XDMCP)

Under the XDMCP tab :
-Honor indirect requests.
-And the default values.

In the remote desktop preferences configuration :
-Allow other users to see your desktop
-Allow other users to control your desktop

I have also tried with firestarted disabled.

What's wrong ?

Thank you for your help.
Lilian

---

### Post by lilian on 2006-05-03
An idee ?

---

### Post by lilian on 2006-05-03
It's OK, it saw in the firestarter events tab that it blocked requests to port 5901 from the client. I adjusted the policy and now its OK.

But I need to user "vncviewer pclilian:5901" because the problem is always the same with "vncviewer pclilian" (no events in firestarted, 5900 is open).

---

