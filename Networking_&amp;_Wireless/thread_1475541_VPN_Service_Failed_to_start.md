---
title: "VPN Service Failed to start"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by driebel on 2010-05-07
Just completed the upgrade to 10.04 from 8.04, and ironing out the wrinkles.  Since the upgrade, I'm not able to establish a VPN connection to my institute (a problem since outgoing mail REQUIRES a VPN connection)  The pull down menu shows the connection as an option, but clicking on it brings up a separate window that simply says "The VPN connection CfA failed because the VPN Service failed to start."  Never had this issue under Hardy, so not sure what's going on.  Under "Configure VPN" the settings look the same as they always did.

Help?

Dave

---

### Post by megandy on 2010-05-09
Same here using a Thinkpad T60.

---

### Post by sledwich on 2010-05-10
Same here on 64bit desktop. I can see in the logs there is a message like:

nm_vpn_connection_connect_cb(): VPN connection 'MY-VPN' failed to connect: 'No VPN secrets!'.

I think its something to do with the passwords

---

### Post by Crio on 2010-05-10
> **sledwich said:**
> Same here on 64bit desktop. I can see in the logs there is a message like:

nm_vpn_connection_connect_cb(): VPN connection 'MY-VPN' failed to connect: 'No VPN secrets!'.

I think its something to do with the passwords
I seem to remember that you should NOT have "Available to all users" checked for VPN connection to have passwords being saved and retreived correctly.

---

### Post by knobcottage on 2010-05-12
Me too.  Clean install of 10.04 and it (vpn) worked out of the box.  Then updated and it broke.  I found this and it fixed it for me.  Perhaps it will help you too.
[http://linux.dipin.info/2010/02/howto-vpn-connection-setup-on-ubuntu.html](http://linux.dipin.info/2010/02/howto-vpn-connection-setup-on-ubuntu.html)

---

### Post by driebel on 2010-05-20
In exact contrast to crio's statement above ;) I just fixed this issue by making sure "Available to all users" IS checked under VPN configuration.  That's all I changed, VPN works perfectly.

---

### Post by Lamellama on 2010-12-05
> I seem to remember that you should NOT have "Available to all users" checked for VPN connection to have passwords being saved and retreived correctly.

On 10.10, I had this problem and Crio's comment did the trick, thanks.

---

### Post by Csirkefogo on 2011-06-01
> **Lamellama said:**
> On 10.10, I had this problem and Crio's comment did the trick, thanks.

Same here! Even now in 2011 problem exists on 10.10 and this "trick" solves it!

Thanks:popcorn:

---

### Post by efalzon on 2011-09-25
> **Crio said:**
> I seem to remember that you should NOT have "Available to all users" checked for VPN connection to have passwords being saved and retreived correctly.

Yep, Lucid 10.04 and just turning off "[] Available to all users" removed my "VPN service failed to start" error. Connected like a charm. Thanks, Crio!

Quick note: I'm using the openVPN service. Don't know if this problem is limited to a specific kind of VPN connection.

---

### Post by carxfrog on 2011-10-05
Noticed that you are using openVPN.  I have also been using that product - but in the Windows 7 environment.  Would like to move to Ubuntu 11.04.  My question concerns where do I put the associated configuration and key files within Ubuntu?  I went looking for openVPN - and it is installed, however when I execute it - from Terminal - I receive a wonderfully detailed configuration options.  I was hoping I could put my openVPN config files from Windows someplace within Ubuntu file structure and everything would work seamlessly.  Can you assist?  Thanks.

---

### Post by pavan4748 on 2012-06-20
Available to all users trick dint work. Added the same VPN connection again. Worked like a flash.

---

