---
title: "VPN Ubuntu 10.10 to MS VPN"
date: 2010-11-22
forum: Networking &amp; Wireless
---

### Post by f0rcegr0wn on 2010-11-22
Hi all,

first post so I will try to make it brief.

Trying to connect via VPN from Ubuntu 10.10 to Microsoft Servers at company and I keep getting ```
LCP: Timeout sending config-requests.
```I looked around and tried everything but still no go. Oddly running MS Windows in Virtual Box connects fine.

Any ideas?

---

### Post by f0rcegr0wn on 2010-11-26
Anybody ...? Please.

---

### Post by format c: on 2010-12-07
I followed the below taken from here and it worked for me to connect from Ubuntu 10.10 to my SBS 2008 server

[http://ubuntuforums.org/showthread.php?t=1307345&page=3](http://ubuntuforums.org/showthread.php?t=1307345&page=3)

3. PPTP VPN Configuration - This setup works for connecting to ISA 2004/2006 PPTP VPNs. It should work for connecting to MS PPTP VPN implementations in general. I can't speak for other PPTP VPN implementations.

a. Create new PPTP connection
VPN Tab Settings
Set Connection name
Set Gateway
Set username (for domain-based user accounts, use domain\username)
DO NOT SET PASSWORD
DO NOT SET NT DOMAIN
PPTP Advanced Options (Advanced button)
uncheck all auth methods EXCEPT MSCHAPv2
check "Use Point-to-Point encryption (MPPE)"
leave Security set at "All Available (Default)"
trying to force encryption level causes this option to become unset
check "Allow stateful inspection"
uncheck "Allow BSD Data Compression"
uncheck "Allow Deflate Data Compression"
uncheck "Use TCP Header Compression"
uncheck "Send PPP Echo Packets" (although connection works either checked or unchecked)
save configuration
b. Initial Connection attempt
enter password in login box
DO NOT check either password save box at this time
once connection establishes, verify remote connectivity - ping, rdp, ssh, etc.
disconnect VPN session
c. 2nd connection attempt
enter password in login box
check both password save option boxes
once again verify remote connectivity
disconnect VPN session
d. Subsequent connection attempts
VPN session should automatically connect using saved auth credentials

---

### Post by reasonableman on 2010-12-24
I am having the same problem connecting to my universities VPN from 10.10. The suggested solution didn't work and I've tried everything I can think of. I've noticed a message: 'The synchronous pptp option is NOT activated'

Is that likely to be a problem.

---

### Post by kedmond on 2011-01-02
This worked for me!  Thank you so much.

> **format c: said:**
> I followed the below taken from here and it worked for me to connect from Ubuntu 10.10 to my SBS 2008 server

[http://ubuntuforums.org/showthread.php?t=1307345&page=3](http://ubuntuforums.org/showthread.php?t=1307345&page=3)

3. PPTP VPN Configuration - This setup works for connecting to ISA 2004/2006 PPTP VPNs. It should work for connecting to MS PPTP VPN implementations in general. I can't speak for other PPTP VPN implementations.

a. Create new PPTP connection
VPN Tab Settings
Set Connection name
Set Gateway
Set username (for domain-based user accounts, use domain\username)
DO NOT SET PASSWORD
DO NOT SET NT DOMAIN
PPTP Advanced Options (Advanced button)
uncheck all auth methods EXCEPT MSCHAPv2
check "Use Point-to-Point encryption (MPPE)"
leave Security set at "All Available (Default)"
trying to force encryption level causes this option to become unset
check "Allow stateful inspection"
uncheck "Allow BSD Data Compression"
uncheck "Allow Deflate Data Compression"
uncheck "Use TCP Header Compression"
uncheck "Send PPP Echo Packets" (although connection works either checked or unchecked)
save configuration
b. Initial Connection attempt
enter password in login box
DO NOT check either password save box at this time
once connection establishes, verify remote connectivity - ping, rdp, ssh, etc.
disconnect VPN session
c. 2nd connection attempt
enter password in login box
check both password save option boxes
once again verify remote connectivity
disconnect VPN session
d. Subsequent connection attempts
VPN session should automatically connect using saved auth credentials

---

### Post by jbeast on 2011-01-12
Thanks Format C: ! Worked for me too :D

---

### Post by cokvance on 2011-01-22
Thanks! This worked like a charm, really appreciate the post.

---

### Post by jcmtnez on 2011-01-27
This worked for me and I was able to connect to my office network, however it made all my Internet traffic very slow.

If you follow the instructions above, your computer will route all internet traffic through the VPN tunnel that is established between your computer and the network that you are trying to connect to (your office, your school, etc). This is why the PPTP VPN connection makes your Internet traffic slow on Ubuntu. 

This is acceptable if you are connecting to the VPN server through a hostile network and you want all your traffic to be safe and routed by the VPN server.

The solution (if you trust your internet provider):

You need to tell your computer to use the VPN connection only for accessing resources behind the VPN server while the rest of your internet traffic should be routed trough your default gateway.

The following instructions are for Genome. I'm assuming that you configured your VPN connection following the steps from the previous posts:

[LIST=1]
[*]Click System -> Preferences -> Network Connections

[*]Select the VPN tab

[*]Select the VPN connection that you created according the previous posts

[*]Click Edit

[*]Select IPv4 Settings tab

[*]Click Routes

[*]Check the box "Use this connection only for resources on this network"

[*]Click OK, Apply, Close.
[/LIST]

After that you can connect to your PPTP VPN network and your internet traffic will be as fast as it was before because it will not use the VPN connection to access the sites you visit.

Hope it helps!

---

### Post by gauchoproluanco on 2011-02-02
Hi everybody, 

Thanks for the post, it is a really useful information!!!

I have followed the steps of **format c** (thanks!) but for me it's not working... When I try to connect the system sends me a message telling me that the **VPN service could not start up**

Any ideas, 

Thanks in advance, 

Luis

---

### Post by exevil on 2012-10-19
> **format c: said:**
> I followed the below taken from here and it worked for me to connect from Ubuntu 10.10 to my SBS 2008 server

[http://ubuntuforums.org/showthread.php?t=1307345&page=3](http://ubuntuforums.org/showthread.php?t=1307345&page=3)

3. PPTP VPN Configuration - This setup works for connecting to ISA 2004/2006 PPTP VPNs. It should work for connecting to MS PPTP VPN implementations in general. I can't speak for other PPTP VPN implementations.

a. Create new PPTP connection
VPN Tab Settings
Set Connection name
Set Gateway
Set username (for domain-based user accounts, use domain\username)
DO NOT SET PASSWORD
DO NOT SET NT DOMAIN
PPTP Advanced Options (Advanced button)
uncheck all auth methods EXCEPT MSCHAPv2
check "Use Point-to-Point encryption (MPPE)"
leave Security set at "All Available (Default)"
trying to force encryption level causes this option to become unset
check "Allow stateful inspection"
uncheck "Allow BSD Data Compression"
uncheck "Allow Deflate Data Compression"
uncheck "Use TCP Header Compression"
uncheck "Send PPP Echo Packets" (although connection works either checked or unchecked)
save configuration
b. Initial Connection attempt
enter password in login box
DO NOT check either password save box at this time
once connection establishes, verify remote connectivity - ping, rdp, ssh, etc.
disconnect VPN session
c. 2nd connection attempt
enter password in login box
check both password save option boxes
once again verify remote connectivity
disconnect VPN session
d. Subsequent connection attempts
VPN session should automatically connect using saved auth credentials

worked, thnx

---

### Post by exevil on 2012-10-19
> **gauchoproluanco said:**
> Hi everybody, 

Thanks for the post, it is a really useful information!!!

I have followed the steps of **format c** (thanks!) but for me it's not working... When I try to connect the system sends me a message telling me that the **VPN service could not start up**

Any ideas, 

Thanks in advance, 

Luis

Maybe "sudo apt-get install pptp-linux"

---

