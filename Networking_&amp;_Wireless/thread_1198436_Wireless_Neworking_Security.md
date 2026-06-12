---
title: "Wireless Neworking Security"
date: 2009-06-27
forum: Networking &amp; Wireless
---

### Post by Roblegge on 2009-06-27
Everynow and then I try out a Linux distro to see if it's worth using, and every time I do I vape it laughing. This time it's Ubuntu 9.04 and the reason I'm going to vape it, unless someone can come up with a solution is simple. It's wireless networking. Now the card is there (it's an HP laptop about 18 months old). But, not suprisingly it doesn't connect through the router. After all that's password protected, so into Network connections we go, edit the connection, enter the SSID, Leave the IPv4 settings alone and go into the security tab. Select WPA/WPA2 from the dropdown, enter the password for the router - that's the same one used by this desktop, my server, my mobile phone, laptop, 2 netbooks and my Media centre. Click apply. Restart the machine. No network connection. Back into security I find out why. Click show password. No, that's not the one I entered. Re-enter MY password. Click apply. Check again. Ubuntu has set it back to ITS password. I don't want to use that - I want to use MY password because I use it on all my other machines. Check again. Nope. It's been reset again.
 
Now unless someone can tell me how to get Ubuntu to keep the password I enter and use that to connect then I'm afraid it's back to the land of vapour ware until Ubuntu can come up with a system that work. You just don't get this sort of problem with Windows 7 - not even the beta version.

---

### Post by DGortze380 on 2009-06-27
> **Roblegge said:**
> Everynow and then I try out a Linux distro to see if it's worth using, and every time I do I vape it laughing. This time it's Ubuntu 9.04 and the reason I'm going to vape it, unless someone can come up with a solution is simple. It's wireless networking. Now the card is there (it's an HP laptop about 18 months old). But, not suprisingly it doesn't connect through the router. After all that's password protected, so into Network connections we go, edit the connection, enter the SSID, Leave the IPv4 settings alone and go into the security tab. Select WPA/WPA2 from the dropdown, enter the password for the router - that's the same one used by this desktop, my server, my mobile phone, laptop, 2 netbooks and my Media centre. Click apply. Restart the machine. No network connection. Back into security I find out why. Click show password. No, that's not the one I entered. Re-enter MY password. Click apply. Check again. Ubuntu has set it back to ITS password. I don't want to use that - I want to use MY password because I use it on all my other machines. Check again. Nope. It's been reset again.
 
Now unless someone can tell me how to get Ubuntu to keep the password I enter and use that to connect then I'm afraid it's back to the land of vapour ware until Ubuntu can come up with a system that work. You just don't get this sort of problem with Windows 7 - not even the beta version.

If you're that happy with Windows, go use Windows.

WPA support is dependent on the driver for your wireless card. Post the output please:

```

lspci

```

---

### Post by linuxmagick on 2009-06-27
I haven't tried to use wireless with the default network manager.  I'm not a big fan of it (just my opinion), and immediately installed wicd (sudo apt-get install wicd) for managing my connections.  No issues with my wireless card and security settings.  Just a thought.

---

