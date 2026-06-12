---
title: "Cant manage to connect to Uni campus net"
date: 2011-02-21
forum: Networking &amp; Wireless
---

### Post by xic816 on 2011-02-21
Lately I have been trying to get my laptop up and running online on uni campusnet but the problem starts with the network programs beeing not compatible with linux. 

I sendt an mail to IT support at uni and he told me to just create VPN connection with given gateway and add username and pw after request but I dont seem to work.

An VPN connection has been made and tried out but it just sais failed to connect, 
can anyone help?

R

MSS

---

### Post by xic816 on 2011-02-23
Additional info:

Here are the manual for apple users

-Connect your laptop to the University network via the Ethernet port on your computer. Begin by
choosing System Preferences… from the menu, or by clicking on the System
Preferences icon in the Dock, which is also located at: /Applications/SystemPreferences.

The best option is to create a new network location for your CampusNet connection. Do so by choosing New Location… from the Location pop-up menu. You may need to click on the lock icon at the bottom of the window in order to make changes. This requires you to have an administrator password for your computer. Now you will need to disable your modem connection by choosing Network Port Configurations from the Show pop-up menu.Make sure you disable the Internal Modem port configuration by un-checking the box next to it. Press the Apply Now button to save your changes and quit System Preferences.

Now you need to open the Internet Connect application located at:/Applications/Internet Connect.
The application will ask if you wish to use a VPN or add a port configuration. Press the Use VPN button.
You will receive a notice that you need to set up for VPN connections. Press the Continue button.

Now you will need to enter the server address for the Stirling VPN/CampusNet, along with a user name and password. The server address is: 192.168.12.254 and your user name and password are the same as you would use to log-on to the university lab computers. Ticking the Add to Keychain box will save your password so that you won't have to re-type it each time you connect.

Go back to System Preferences, click the Network icon and choose Network Port Configurations from the Show pop-up menu. Check that you can now set PPTP to “On”. If this does not show, quit System Preferences and re-launch it. Built-in Ethernet should also be on.

Choose PPTP from the Show pop-up menu. Now you need to set the TCP/IP settings for your
connection. In the DNS Servers field enter 139.153.100.7 and 139.153.13.200 as shown below.
The other values should configure themselves automatically.

Next, press the Proxies tab. Tick the Web Proxy (HTTP) box and enter the value
wwwcache.stir.ac.uk and the number 8080 in the Port field as shown below. Press the Apply
Now button to activate your configuration. This configuration can now be chosen via the
Apple menu under Location.

Then tick the box next to ‘Secure Web Proxy’ and enter wwwcache.stir.ac.uk and port 8080
The configuration is now complete, the only step left is to open Internet Connect again and press the Connect button.

Whenever you wish to connect to the VPN, make sure the Location is set to “Uni VPN” (or
whatever you chose as a name) from the menu, open Internet Connect and press the
Connect button. Remember to press Disconnect when you are done.

---

### Post by Kirboosy on 2011-02-23
Are  you trying to connect with OpenVPN?

---

### Post by xic816 on 2011-02-23
> **Caboose885 said:**
> Are  you trying to connect with OpenVPN?

No just the integrated VPN addon on Network manager

---

### Post by xic816 on 2011-02-23
> **xic816 said:**
> No just the integrated VPN addon on Network manager

Just tried to download OpenVPN from 
[http://openvpn.net/index.php/access-server/download-openvpn-as-sw.html](http://openvpn.net/index.php/access-server/download-openvpn-as-sw.html)

I only found versions for ubuntu 8 and 9, anywayz I tried ubuntu 9 32bit edition but dont seem to install.. -_-

---

### Post by Kirboosy on 2011-02-23
You actually might not need OpenVPN. I forgot that new Ubuntu has VPN built in. Previously you had to install packages. (FYI when looking for new programs I would always check Synaptic first. System-->Admin-->Synaptic) You could try it with OpenVPN though.

---

### Post by xic816 on 2011-02-23
> **Caboose885 said:**
> You actually might not need OpenVPN. I forgot that new Ubuntu has VPN built in. Previously you had to install packages. (FYI when looking for new programs I would always check Synaptic first. System-->Admin-->Synaptic) You could try it with OpenVPN though.

Mhm, so how to setup VPN?

---

### Post by Kirboosy on 2011-02-23
Looking  through those instructions it would seem that you could just follow those. Its really hard for me to troubleshoot since I can't access your VPN and every VPN is different.

---

### Post by xic816 on 2011-02-23
> **Caboose885 said:**
> Looking  through those instructions it would seem that you could just follow those. Its really hard for me to troubleshoot since I can't access your VPN and every VPN is different.

Yeah I understand. I tried to follow it but my VPN seems limited so I'm having problems applying different elements (which I cant find), it looks like this; /see pictures

---

### Post by xic816 on 2011-02-23
> **xic816 said:**
> Yeah I understand. I tried to follow it but my VPN seems limited so I'm having problems applying different elements (which I cant find), it looks like this; /see pictures

Okey just managed to get connected by following this manual;

                                  **Re: VPN Ubuntu 10.10 to MS VPN**             
                                                                I followed the below taken from here and it worked for me to connect from Ubuntu 10.10 to my SBS 2008 server

[http://ubuntuforums.org/showthread.php?t=1307345&page=3](http://ubuntuforums.org/showthread.php?t=1307345&page=3)

3. PPTP VPN Configuration - This setup works for connecting to ISA  2004/2006 PPTP VPNs. It should work for connecting to MS PPTP VPN  implementations in general. I can't speak for other PPTP VPN  implementations.

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

Got a questionn, what does he mean by "DO NOT check either password save box at this time once connection establishes, verify remote connectivity - ping, rdp, ssh, etc."?

Thanks for reply!

---

### Post by Kirboosy on 2011-02-23
I'm guessing the reason why he said that is to verify that you are connecting to the right server first and that everything works fine. 

I'm not entirely sure on that. Maybe he is just a security nut and doesn't like saved passwords. ;)

---

