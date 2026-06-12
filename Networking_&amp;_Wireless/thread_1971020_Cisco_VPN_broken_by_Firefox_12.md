---
title: "Cisco VPN broken by Firefox 12"
date: 2012-05-02
forum: Networking &amp; Wireless
---

### Post by RudyG on 2012-05-02
Hi.

I have a strange problem. After upgrading my Firefox from 11 to 12, my Cisco VPN stopped working. :( I get a message "warning: the following certificate received from the server could not be verified:" and an option of Accept or Disconnect. If I hit Accept it just pops up the message again indefinitely. Removing Firefox solves the problem. This happened in 11.10 and 12.04. My system is 32bit Pentium 4.
The Cisco VPN client I'm using in the one that I installed with a script that I downloaded from Cisco. I can't seem to get the KVPNC and the base networking VPN client to work.

Does anyone have any ideas?
TIA
Rudy

---

### Post by geno83 on 2012-05-08
I have the same problem with Firefox 12. Removing Firefox solves my problem. Any other solutions?

---

### Post by RudyG on 2012-05-08
Sadly, I haven't found a solution yet. :( KVPNC doesn't work as it requires a group password which I don't have and using the vpnc protocol from the Network Management panel gives me an error. :(
However, as a temp workaround I downloaded a Firefox and unzipped it into a single subdirectory, and I run it from there.

I'll try posting this on the Kubuntu forum, maybe there someone has run across a solution for this. If I find it I'll post it here.

Rudy

---

### Post by Sergius14 on 2012-05-08
You should have that group password.

Ask to the Firewall admin which it is or configure one.

KVPNC fully works...

Even the VPNC Network Applet (native gnome networking integration) works.

---

### Post by RudyG on 2012-05-08
> **Sergius14 said:**
> You should have that group password.

Ask to the Firewall admin which it is or configure one.

KVPNC fully works...

Even the VPNC Network Applet (native gnome networking integration) works.
Hi Sergius.

Thank you very much for the reply. I would of course prefer to use the VPNC that is already in the system rather than have all the KVPNC stuff added to my system but at the end of the day whatever works is what I'll go with. :)
Here's the message I get when I try to use the VPNC Network Applet:
No agents were available for this request.
It's a dialog box that pops up.

I will try to contact the Networking team for the Group Password. However, when I use the Cisco VPN client I don't need that Group Password, so I can't understand why KVPNC requires it then.:confused:

Thanks again.
Rudy

---

### Post by Sergius14 on 2012-05-09
About the "No agents were available for this request", need futher research why is not working. Maybe is missing something or somethings is uncompatible.

Just to remember: The applet also needs vpnc

About the Group Password: Inside the .PCF file, there is a hash with the Enc Password.

Open it with a text editor and you will see.

Fortunatelly for you, Enc password is 100% vulnerable and reversible:

[http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode]("http://www.unix-ag.uni-kl.de/%7Emassar/bin/cisco-decode")

Put there you Encrypted (Group) Password to decode it and have the answer in a typable way.

---

### Post by RudyG on 2012-05-09
Thank you Sergius I really appreciate your time.
> **Sergius14 said:**
> About the "No agents were available for this request", need futher research why is not working. Maybe is missing something or somethings is uncompatible.

Just to remember: The applet also needs vpnc Here's a list of packages that I have installed trying to get this working:
1. VPNC
2. network-manager-vpnc
3. network-manager-vpnc-gnome
4. kvpnc

> **Sergius14 said:**
> About the Group Password: Inside the .PCF file, there is a hash with the Enc Password.

Open it with a text editor and you will see.

Fortunatelly for you, Enc password is 100% vulnerable and reversible:

[http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode]("http://www.unix-ag.uni-kl.de/%7Emassar/bin/cisco-decode")

Put there you Encrypted (Group) Password to decode it and have the answer in a typable way.Searching my hard drive did not yield any .pcf files. :( Do you by chance know the directory it should be in?

Thanks.
Rudy

---

### Post by Sergius14 on 2012-05-10
Should be at:

x86: C:\Program Files\Cisco Systems\VPN Client\Profiles

x64: C:\Program Files (x86)\Cisco Systems\VPN Client\Profiles

---

### Post by RudyG on 2012-05-10
> **Sergius14 said:**
> Should be at:

x86: C:\Program Files\Cisco Systems\VPN Client\Profiles

x64: C:\Program Files (x86)\Cisco Systems\VPN Client\Profiles:shock: I had no idea you meant a Windows Machine. :) LOL. My Windows version is XP. and it too does not have any *.PCF files on it. Just went through the entire drive.
The directory structure on XP is
C:\Program Files\Cisco\Cisco AnyConnect VPN Client\res

I even searched through the registry to see if the group password might be there. :D But so far nothing.

Thanks you again.
Rudy

---

### Post by Sergius14 on 2012-05-10
The VPN Client should creates a PCF file for every conection you create or import....

Can you connect with the Windows PC?

---

### Post by RudyG on 2012-05-10
> **Sergius14 said:**
> The VPN Client should creates a PCF file for every conection you create or import....

Can you connect with the Windows PC?Yes absolutely. The windows machine is my laptop and it is running Windows XP as I mentioned. I'm afraid to upgrade the Firefox on it to 12. And it has the Cisco VPN client installed on it from Cisco.

Kubuntu is my Desktop. It too has the Cisco VPN client installed on it from Cisco. Both clients on both machines work just fine, until Firefox 12 enters the picture.

Thank you Sergius.
Rudy

---

### Post by DesertDude on 2012-05-22
I ran into the same problem (running Kubuntu 11.10 as a 32 bit VM) -- the update to Firefox 12 stopped a working AnyConnect VPN connection for me.  After installing the latest Cisco AnyConnect version (2.5.3055) which didn't fix the issue, I found an article at [http://askubuntu.com/questions/129477/server-certificate-problem-with-cisco-anyconnect-vpn-client](http://askubuntu.com/questions/129477/server-certificate-problem-with-cisco-anyconnect-vpn-client) that indicated that Cisco looks at a different location for its certs -- it suggested copying the certs from /etc/ssl/certs/ to /opt/.cisco/certificates/ca.  I did this and my VPN connection started working again.

---

### Post by RudyG on 2012-05-23
Thanks DesertDude great post and a great link. I would be a whole lot happier to see the issue resolved though. But as another workaround this is quite excellent. I imagine the files need not be copied, as they can be also be symbolically linked.
It just seems weird to me as to what Firefox did to introduce this problem into people's systems.:confused:

Rudy

---

