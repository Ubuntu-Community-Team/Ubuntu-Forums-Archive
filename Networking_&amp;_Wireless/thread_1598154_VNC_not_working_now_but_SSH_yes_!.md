---
title: "VNC not working now but SSH yes !"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by pimpys on 2010-10-16
Hi again,

This is now strange, I did a reboot and now SSH is working but no VNC

[[IMG]http://i26.servimg.com/u/f26/10/06/94/88/putty10.jpg[/IMG]]("http://www.servimg.com/image_preview.php?i=219&u=10069488")

[[IMG]http://i26.servimg.com/u/f26/10/06/94/88/can_t_10.jpg[/IMG]]("http://www.servimg.com/image_preview.php?i=218&u=10069488")

See previous post [http://ubuntuforums.org/showthread.php?t=1597764](http://ubuntuforums.org/showthread.php?t=1597764)

Thanks once more,

---

### Post by pimpys on 2010-10-21
Do you have any idea why this is not working now ?
Thanks,

---

### Post by CharlesA on 2010-10-21
Are you trying to tunnel VNC over SSH, or just connect directly to the vnc server?

Which VNC server are you using?

---

### Post by ThatBum on 2010-10-21
If you are using SSH as a tunnel, do you have port forwarding set up right?

I see you are using PuTTY to SSH. You should go to Tunnels under SSH directory thing in the left part of PuTTY's configuration, and set a port forward there.

Source port=5900
Destination=localhost:5900

Then you have to tell the VNC viewer to connect to localhost::5900.

This is assuming that your VNC server is running on the default port, and is listening to loopback requests. Also assuming that you are not running a VNC server on the machine you are VNC'ing *from.* Then you have to set a different source port so it won't conflict.

If you're just trying to do plain un-tunneled VNC (unwise outside your LAN), make sure that the VNC server is *not* only listening to loopback. Also make sure something stupid isn't happening, like iptables rejecting the connection or possibly a firewall in Windows blocking the outgoing connection (had that happen to me more than once, lawl).

EDITz0rz: I just looked at the other post. I've seen you're wrestled with iptables before getting SSH working. If you're wondering, ufw is a frontend for iptables. ufw being an acronym for Uncomplicated FireWall. Fun. You have to add rules to allow both 22 and 5900, of iptables will reject them.

If you haven't already:

sudo ufw allow 5900
sudo ufw allow 22

Then make sure they work by

sudo ufw status

BTW, I would change your SSH port to something other than 22 to reduce the hacking risk somewhat. Security through obscurity, and all that. Just choose something unused over 1023, because that's how high most port scanners/scripts go.

---

