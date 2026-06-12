---
title: "NetExtender wont stay logged in"
date: 2009-07-24
forum: Networking &amp; Wireless
---

### Post by modsbyus on 2009-07-24
When I try to log in with net extender I get this

Connecting to SSL-VPN Server "204.94.66.6:443". . .
Connected.
Logging in...
Login successful.
Using SSL Encryption Cipher 'DHE-RSA-AES256-SHA'
[COLOR="Red"][B]Using new PPP frame encoding mechanism
&#65533;&#65533;8j&#65533;&#65533;&#65533;&#65533;	H&#65533;&#65533;SSL-VPN logging out...
SSL-VPN connection is terminated.[/B][/COLOR]
Exiting NetExtender client
JNI: LaunchNX: Exiting LaunchNX, returning (0)
Loading saved profiles...
Loaded profile: 204.94.66.6
Done.
2009-07-24 14:28:33 EDT INFO com.sonicwall.gui.NetExtenderRootPanel NetExtender disconnected
JNI: LaunchNX: mypid = 19386
JNI: LaunchNX: Launching NetExtender2
JNI: LaunchNX: Using destination IP 204.94.66.6
JNI: LaunchNX: launching NX

Connecting to SSL-VPN Server "204.94.66.6:443". . .
Connected.
Logging in...
Authentication failure: Login failed - Incorrect username/password
SSL-VPN logging out...
SSL-VPN connection is terminated.
Exiting NetExtender client
JNI: LaunchNX: Exiting LaunchNX, returning (1)
Loading saved profiles...
Loaded profile: 204.94.66.6
Done.
2009-07-24 14:28:38 EDT INFO com.sonicwall.gui.NetExtenderRootPanel Login failed - Incorrect username/password

Please pay speacial attention to the bold red text, as I believe that that is where my problem lies.
I have called SonicWALL and they did their best to troubleshoot this issue and have determined that it does work (with my username and password) in Redhat, Windows, and OSX. I also had no problems logging in and using netextender in windows.
Any help on this will be great. I have been working on this for 2 days and need this to work for my job.

---

