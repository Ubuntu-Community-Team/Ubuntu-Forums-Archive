---
title: "Can't access company sharepoint via vpn"
date: 2010-10-05
forum: Networking &amp; Wireless
---

### Post by paulphillips on 2010-10-05
I am attempting to setup my home ubuntu-box (10.04, 64bit) to vpn into work (cisco).

My attempt has been partially successful - connecting successfully to shared drives - but I can't access the internal company sharepoint site (using network-manager-vpnc).  When I enter the URL into firefox, it tries for a few seconds then displays the "connection was reset" error page (see attached). I don't even get the normal pop-up dialog asking for my credentials! The URL is resolvable to an IP, and the server can be pinged successfully.

So, to make sure my home network wasn't to blame, I brought home a work laptop with a windows vpn client. This worked fine.

I then went to work with Ubuntu-NR on a USB stick and booted up into ubuntu to make sure ubuntu wasn't to blame. This worked fine.

So my only conclusion then is that it must be the VPN setup itself. Any clues anyone?  Thanks in advance!

---

### Post by kreggz on 2010-10-06
try entering the fully qualified domain name e.g

[http://sharepoint.microsoft.com](http://sharepoint.microsoft.com)

and if you have any proxies setup in your browser, make sure they are removed.

---

### Post by paulphillips on 2010-10-06
Thanks for the suggestion, but I did try that - no success unfortunately.  No proxies either - direct connection to internet.

---

### Post by kreggz on 2010-10-06
try this from terminal

telnet [website] 80

if it says connection closed, it means the tunnel needs more access.

If it says open, type

GET /

and press enter after the slash. It should output HTML code if it works.

---

### Post by paulphillips on 2010-10-06
> **kreggz said:**
> try this from terminal

telnet [website] 80

if it says connection closed, it means the tunnel needs more access.

If it says open, type

GET /

and press enter after the slash. It should output HTML code if it works.

Ok - tried this and got the following result:

```
telnet <URL> 80
Trying <IP address>...
Connected to <URL>.
Escape character is '^]'.
GET /
...
You do not have permission to view this directory or page using the credentials that you supplied because your Web browser is sending a WWW-Authenticate header field that the Web server is not configured to accept.
<hr>
<p>Please try the following:</p>
<ul>
<li>Contact the Web site administrator if you believe you should be able to view this directory or page.</li>
<li>Click the <a href="javascript:location.reload()">Refresh</a> button to try again with different credentials.</li>
</ul>
<h2>HTTP Error 401.2 - Unauthorized: Access is denied due to server configuration.<br>Internet Information Services (IIS)</h2>
...
Connection closed by foreign host.
```

Now obviously this suggests there's something wrong with authentication, and given that there's no problem authenticating from a live-ubuntu session connected to the office LAN, I'm guessing there's a problem with my routing table?

Any tips for determining what's missing?

---

### Post by kreggz on 2010-10-06
the telnet suggests you can get to the page. Could you try another browser perhaps? e.g Chrome

---

### Post by paulphillips on 2010-10-07
> **kreggz said:**
> the telnet suggests you can get to the page. Could you try another browser perhaps? e.g Chrome

Ok. I installed chromium and it failed too (see below)

```
This webpage is not available.

The webpage at http://projectcentral.community.topcon.com/ might be temporarily down or it may have moved permanently to a new web address.

  More information on this error
Below is the original error message

Error 101 (net::ERR_CONNECTION_RESET): Unknown error.
```

I did note that there was a long delay between hitting enter on "GET /" command inside telnet and the HTTP error being reported on VPN vs. in the office.

---

### Post by kreggz on 2010-10-07
Looks like your being directed through a proxy. Thats all I can tell you for now... :confused:

---

### Post by paulphillips on 2010-10-10
Solved!

I did some digging around the net when I got the same authentication error in the office using cygwin bash shell.  This suggested an intermittent fault rather than a routing table fault. Also remember that had issues mounting windows shares - would sometimes work ok, sometimes not.  

Searching on the net for other similar "intermittent" faults, let me to believe there might be an MTU mismatch.

It seems it was a misconfiguration of the tun0 interface.  MTU was set to 1412 - too high. I changed it to 1300 which apparently is typical for VPNs?

```
sudo ifconfig tun0 mtu 1300
```

Anyway - that did the trick!

Thanks for all your suggestions - they certainly helped!

---

### Post by paulphillips on 2010-10-10
Now I need to figure out how do set this up permanently, and determine if it's a bug or not.

Found this bug link:
[https://bugs.launchpad.net/ubuntu/+source/network-manager-vpnc/+bug/112248](https://bugs.launchpad.net/ubuntu/+source/network-manager-vpnc/+bug/112248)

Appears that there network-manager-vpnc either does or used-to set MTU using hardcoded value.

---

### Post by kreggz on 2010-10-11
Typically a lower MTU size is used for VPN connections. IPSEC adds an overhead which can push the data size over 1500 bytes. Routers don't tend to like this.

---

### Post by paulphillips on 2010-10-17
Found this link - which appears to describe my problem perfectly:

[https://bugzilla.gnome.org/show_bug.cgi?id=603575](https://bugzilla.gnome.org/show_bug.cgi?id=603575)

...although it looks like there's still no progress on deciding a final solution...

From the problem description, there's an environment variable that can be set: "INTERNAL_IP4_MTU". I haven't tested this yet, but if it works, I'll need to figure out a way of setting this automatically at login time or at bootup. Hardcoding to 1300 would appear to be undesirable, but perhaps it will a satisfactory workaround for now.

---

### Post by SeijiSensei on 2010-10-18
OpenVPN supports a link-mtu parameter; see "man openvpn" for details.  You should probably add it to both the server and client configuration files.

---

### Post by paulphillips on 2010-10-18
> **SeijiSensei said:**
> OpenVPN supports a link-mtu parameter; see "man openvpn" for details.  You should probably add it to both the server and client configuration files.

I'm not sure I understand. I thought OpenVPN was a different plugin for network manager? The plugin I'm using is vpnc - which I thought was required for Cisco. Are you saying I can use openvpn instead, or are you saying this "link-mtu" parameter should be available also for vpnc?

---

### Post by SeijiSensei on 2010-10-19
Sorry I thought you were using OpenVPN since that's the most common *nix VPN solution these days.  If you have to use a proprietary Cisco client, you'll need to talk to them or to your company's IP administrator.

If you just need to set an environment variable, you can do it either in /etc/profile if you want it available to all users on the machine, or in /home/user/.profile.  Both these scripts are run automatically at, respectively, startup and login.

---

### Post by paulphillips on 2010-12-11
Solved!!

I added a file called "02-mtu" to /etc/NetworkManager/dispatcher.d to set the mtu after the vpnc link is up.

It's a workaround, but it works nicely.  See attached file (remove .txt extension and make sure you copy it in as root and set chmod a+x

---

