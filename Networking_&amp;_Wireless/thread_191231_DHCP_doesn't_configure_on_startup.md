---
title: "DHCP doesn't configure on startup"
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by Cellular on 2006-06-07
Hi!

In the face of all the big network problems people are having with Dapper, this sounds a bit trivial, but i can't figure it out on my own.

Dapper doesn't seem to do a DHCP request on startup, so when i start the computer, i don't have an ethernet connection. If i run
"sudo dhclient eth0"
, everything works fine. If i start the computer not long after the last time it was on, it sometimes has working internet, if it's been a little while longer, i have to re-run dhclient.

On Breezy, during startup i used to see a message about DHCP, but there's nothing about that when starting Dapper.

I'm sure it's a simple problem, but i've been searching the forums and can't find a solution on my own. I'm thankful for any help.

---

### Post by lkagan on 2006-06-07
Go to System->Administration->Networking
When the dialog box comes up, highlight the correct Ethernet connection and click on the properties button.  Ensure the checkbox is checked for 'Enable this connection'.  And ensure that the 'Configuration' selection is on DHCP.  I used to know how to do this in Redhat from the command line but I don't know where the configuration scripts are for networking so if anyone knows please reply.

Larry

---

### Post by Cellular on 2006-06-07
Thanks for the tip, but my settings are already like you advised. I tried changing them and changing back, to see if that changes it.

---

### Post by DougC on 2006-06-07
I've got exactly the same problem. Sometimes it start OK, but usually I have to do a /etc/init.d/networking restart then everythings ok. It's a bit anoying to say the least.

Doug

---

### Post by lkagan on 2006-06-07
Your /etc/network/interfaces file should look like this.
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
I found the config file for networking, yours should look similar to this with the exception that the word 'static' below would probably 
# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

More info on this file can be found [here]("http://help.ubuntu.com/ubuntu/serverguide/C/network-configuration.html").

Larry

---

### Post by tom56 on 2006-06-07
DHCP seems to be broken in some cases...

->[http://www.ubuntuforums.org/showthread.php?p=1091343](http://www.ubuntuforums.org/showthread.php?p=1091343)
->[http://www.ubuntuforums.org/showthread.php?p=1096987](http://www.ubuntuforums.org/showthread.php?p=1096987)
->[https://launchpad.net/distros/ubuntu/+bug/42608](https://launchpad.net/distros/ubuntu/+bug/42608)

---

### Post by DougC on 2006-06-08
Well guess I can wait for the bug fix.

There were a cuople of things to look at in those posts though so heres hoping.

or I could just go for the static IP address, but I'd rather it just worked.

Many thanks,
Doug.

---

### Post by Cellular on 2006-06-08
Ikagan, my file looks exactly like yours.

Guess we'll have to wait for a bugfix then... 

Thanks everyone for the pointers!

---

