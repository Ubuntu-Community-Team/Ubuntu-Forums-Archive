---
title: "HOWTO Connect to Nortel Contivity switch using vpnc"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by finite9 on 2009-08-27
### See this thread first ###

[http://ubuntuforums.org/showthread.php?t=1202896&highlight=nortel+vpn](http://ubuntuforums.org/showthread.php?t=1202896&highlight=nortel+vpn)

### as it uses a later release of vpnc that requires no manual patching and has more info regarding the config file ###

I have been trying to fix this for years, and the resources on the Internet are very hard to find to get this working, but as it happens, one of my colleagues at work had figured this out.  I do not know if he did it himself or got the info from somewhere else, but I want to share it with you all...

I had previously seen this guide:

[http://ubuntuforums.org/showpost.php?p=4431644&postcount=55](http://ubuntuforums.org/showpost.php?p=4431644&postcount=55)

but I had not been able to get it working using those instructions and was getting the same error as everyone else on the thread.  This build that I refer to seems to work correctly in my case though.

My employer uses a Nortel Contivity concentrator for VPN access.  We use Group IDs and Group passwords, so this guide might not be relevant or may need modifying for those who do not use a Group ID.  We use DH-8 and I think the official client for Windows we use is 6.x.  I connect to the VPN using a one time password with a SafeWord keypad.  It generates a 6 digit alphanumeric key that I enter as the only password (apart from the group password)

So, onto the guide:

Download a modified version of vpnc from the Subversion repository.  Note that if you search this forum in the wireless and network category for "nortel contivity" then there is a thread there that is very similar to my guide, and they downloaded the latest version from svn, but I do not know exactly which version they use...probably the one at the time the thread was created.

```
svn co -r 359 [http://svn.unix-ag.uni-kl.de/vpnc/branches/vpnc-nortel/](http://svn.unix-ag.uni-kl.de/vpnc/branches/vpnc-nortel/)
cd vpnc-nortel
```

Apply the patch attached to this post.  Download it and store it in the vpnc-nortel folder created when you downloaded vpnc from svn.

```
patch -p0 < patch.txt
```

make the package and install it:

```
make
sudo make install
```

Create the config file:

```
sudo nano /etc/vpnc/default.conf
```

```
IPSec gateway <DNS name or IP address to VPN switch>
IPSec ID <groupID>
IPSec secret <groupPass>
Xauth username <username>
Vendor nortel
IKE Authmode psk
Nortel Auth Mode gpassword
DPD idle timeout (our side) 0
```

The you can connect to the VPN using

```
sudo vpnc
```

It will prompt you for the password from the SafeWord pad.  Enter the password and hit enter.

That's it!  It uses the default conf file and the vpnc script that exist under /etc/vpnc so you dont need to specify them on the command line.  If you have strict firewall rules you may need to add the "--local-port 0" switch.

To disconnect:

```
sudo vpnc-disconnect
```

[B]Notes
-----[/B]

I could not get this to work whilst connected internally to the company network, but from home it worked OK.  I was however using Ubuntu 8.04 at work and Ubuntu 9.04 at home.

This guide works on amd64 architecture.

For me, DNS worked ok on the company network without any other modifications.

This guide for vpnc creates a tunnel device and lets you have split networking, where you can access the VPN whilst still being connected to your home network.  The official client does not allow this!

Hope this is useful for all the people like me who scoured the net trying to get this working.

---

### Post by strahgn on 2009-11-01
I tried this howto and I still get the same old tired message below...
vpnc: response was invalid [1]:  (ISAKMP_N_INVALID_EXCHANGE_TYPE)(7)

Has anyone figured out what this message actually means and come up with any solutions?

Version check shown below...
vpnc version 0.5.2-359M
Copyright (C) 2002-2006 Geoffrey Keating, Maurice Massar, others
vpnc comes with NO WARRANTY, to the extent permitted by law.
You may redistribute copies of vpnc under the terms of the GNU General
Public License.  For more information about these matters, see the files
named COPYING.
Built without openssl (certificate) support.

Supported DH-Groups: nopfs dh1 dh2 dh5
Supported Hash-Methods: md5 sha1
Supported Encryptions: null des 3des aes128 aes192 aes256
Supported Auth-Methods: psk psk+xauth

---

### Post by benhill70 on 2011-07-23
With the help of this thread plus this one:
[http://ubuntuforums.org/showthread.php?t=1202896&highlight=nortel+vpn&page=2](http://ubuntuforums.org/showthread.php?t=1202896&highlight=nortel+vpn&page=2)

Vpnc nortel works great on 64bit Ubuntu 11.4.

---

