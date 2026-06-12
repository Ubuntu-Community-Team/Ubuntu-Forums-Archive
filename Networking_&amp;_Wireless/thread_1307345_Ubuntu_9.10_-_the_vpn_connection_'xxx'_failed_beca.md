---
title: "Ubuntu 9.10 - the vpn connection 'xxx' failed because there were no valid vpn secrets"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by sweisler on 2009-10-31
How is it that the bug in networkmanager/pptp-plugin that causes this error message - "the vpn connection 'xxxxxx' failed because there were no valid vpn secrets" - is STILL NOT FIXED?  This has been a known issue with gnome since the the Ubuntu 8.10 alpha.  We have now gone 3 full releases where this is broken.

I have tried both x86 and x64 installs of Ubuntu 9.10, with a number of purported "fixes" or workarounds for this issue, with no success.  I use my Ubuntu-installed laptop as my main business work tool.  I HAVE to have PPTP and VPNC connectivity to connect to client sites.  Which is why I'm still stuck on 8.04.

While I know my way around the linux cli, I don't have the inclination to waste time on the cli when there's a GUI interface that should, and used to, do the job. 

Will this critical networking component STILL BE BROKEN when the 10.4 LTS release rolls around?

---

### Post by jithoosin on 2009-11-01
I too had this issue in 9.10 and a restart fixed it.

---

### Post by sweisler on 2009-11-03
I had restarted the pc on all the test setups I had ran with no luck. Your response got me to reset my frustration level and try again.

I went back and tried working the whole process over again.  I have managed to get PPTP, VPNC, and OpenConnect working on x86.  PPTP and VPNC work on x64 as well.  I am still working on OpenConnect connectivity on x64.

The biggest issues were:
1.  The remaining bug between NetworkManager and Gnome Keyring when you attempt to save passwords
2.  translating PPTP settings in Ubuntu 8.04 to 9.10

My apologies to the Gnome and Ubuntu development teams for my rant.  This issue has been a HUGE point of frustration for me with 8.10 and 9.04.

If anyone wants me to post my setup steps or various VPN client configurations, please post your requests and I will do my best to respond.

---

### Post by daffyduc on 2009-11-03
I am trying to get this working as well... please post up the steps of x86 on pptp

Thanks

---

### Post by Marti68 on 2009-11-04
> **sweisler said:**
> I had restarted the pc on all the test setups I had ran with no luck. Your response got me to reset my frustration level and try again.

 If anyone wants me to post my setup steps or various VPN client configurations, please post your requests and I will do my best to respond.

Potentially resetting frustration level here :)

Your notes (VPNC) would be appreciated especially as you have grasped that the fastest way to loose  newbies is streams of CLI.  WE HATE IT.
Yea, I know it's powerful.  So is a an a steam train and they belong to history as well.

Sorry, missed the ranty reset.

---

### Post by sweisler on 2009-11-06
Here's a synopsis of my VPN setups.  I have proven this to work on both x86 and x64 for all 3 VPN types.

Important note/disclaimer: I tested these configurations on VMware Workstation 7 VM's and a Dell Vostro 220.  All installations were fresh installs, not upgrades.  Also, please notice that I detail what type of firewall/VPN I am connecting to for each VPN type.  There are so many variations on these VPN implementations that it is  extremely difficult to generalize a known-good configuration for each.

1. Install various VPN components
[INDENT]a. PPTP[/INDENT]
[INDENT][LIST]
[*]pptp-linux 
[*]network-manager-pptp
[/LIST][/INDENT]
[INDENT]b. VPNC[/INDENT]
[INDENT][LIST]
[*]vpnc
[*]network-manager-vpnc
[/LIST][/INDENT]
[INDENT]c. OpenConnect[/INDENT]
[INDENT][LIST]
[*]openconnect
[*]network-manager-openconnect
[/LIST][/INDENT]

2. Reboot

3. PPTP VPN Configuration - This setup works for connecting to ISA 2004/2006 PPTP VPNs.  It should work for connecting to MS PPTP VPN implementations in general.  I can't speak for other PPTP VPN implementations.
[INDENT]
a.  Create new PPTP connection[/INDENT]
[INDENT][LIST]
[*]VPN Tab Settings
[/LIST][/INDENT]
[INDENT][INDENT][LIST]
[*]Set Connection name
[*]Set Gateway
[*]Set username (for domain-based user accounts, use *domain\username*)
**[*]DO NOT SET PASSWORD**
**[*]DO NOT SET NT DOMAIN**
[/LIST][/INDENT][/INDENT]
[INDENT][INDENT][LIST]
[*]PPTP Advanced Options (Advanced button)
[/LIST][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][LIST]
[*]uncheck all auth methods **EXCEPT MSCHAPv2**
[*]check "Use Point-to-Point encryption (MPPE)"
[INDENT][INDENT][INDENT][INDENT][LIST]
[*]leave Security set at "All Available (Default)"
[*]trying to force encryption level causes this option to become unset
[/LIST][/INDENT][/INDENT][/INDENT][/INDENT]
[*]check "Allow stateful inspection"
[*]uncheck "Allow BSD Data Compression"
[*]uncheck "Allow Deflate Data Compression"
[*]uncheck "Use TCP Header Compression"
[*]uncheck "Send PPP Echo Packets" (although connection works either checked or unchecked)
[/LIST][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][LIST]
[*]save configuration
[/LIST][/INDENT][/INDENT]

[INDENT]b.  Initial Connection attempt[/INDENT]
[INDENT][INDENT][LIST]
[*]enter password in login box
[*]**DO NOT** check either password save box at this time
[*]once connection establishes, verify remote connectivity - ping, rdp, ssh, etc.
[*]disconnect VPN session
[/LIST][/INDENT][/INDENT]

[INDENT]c.  2nd connection attempt[/INDENT]
[INDENT][INDENT][LIST]
[*]enter password in login box
[*]check both password save option boxes
[*]once again verify remote connectivity
[*]disconnect VPN session
[/LIST][/INDENT][/INDENT]

[INDENT]d.  Subsequent connection attempts[/INDENT]
[INDENT][INDENT][LIST]
[*]VPN session should automatically connect using saved auth credentials
[/LIST][/INDENT][/INDENT]
4. VPNC VPN Configuration - This setup works connecting to an ASA5510 - software version 8.2(1).  I didn't have any other Cisco devices to test against.[INDENT]
a.  Create new VPNC connection[/INDENT]
[INDENT][INDENT][LIST]
[*]set connection name
[*]set Gateway
[*]set Group Name
[*]set User Password to "Saved" and enter password
[*]set Group Password to "Saved" and enter password
[*]set username
[*]set domain (if applicable)
[*]leave Encryption Method at "Secure (Default)"
[*]set NAT traversal to "NAT-T"
[*]save configuration
[/LIST][/INDENT][/INDENT]
	
[INDENT]b.  Initial Connection attempt[/INDENT]
[INDENT][INDENT][LIST]
[*]open VPNC connection
[*]if prompted, select "Always Allow" if you want connection to be automatic
[*]verify remote connectivity - ping, rdp, ssh, etc.
[*]disconnect VPN session
[/LIST]
[/INDENT][/INDENT]
[INDENT]c.  Subsequent connection attempts[/INDENT]
[INDENT][INDENT][LIST]
[*]open VPNC connection - session should automatically connect
[/LIST][/INDENT][/INDENT]

5. OpenConnect VPN Configuration - This setup works connecting to an ASA5510 - software version 8.2(1).  I didn't have any other Cisco devices to test against.

[INDENT]a.  Create new OpenConnect connection[/INDENT]
[INDENT][INDENT][LIST]
[*]set connection name
[*]set Gateway
[*]set Authentication type to "Password/SecurID"
[*]no need to set username, OpenConnect won't store it yet
[*]save configuration
[/LIST][/INDENT][/INDENT]
[INDENT]
b.  Initial connection attempt[/INDENT]
[INDENT][INDENT][LIST]
[*]open VPN connection
[*]check "Automatically start connecting next time"
[*]click Close
[*]you will get the "No Valid VPN Secrets" VPN failure message
[/LIST][/INDENT][/INDENT]

[INDENT]c.  2nd connection attempt[/INDENT]
[INDENT][INDENT][LIST]
[*]open VPN connection
[*]accept certificate (if prompted)
[*]change Group (if necessary) 
[*]enter username (may need to be *domain\username*)
[*]enter password
[*]click Login
[*]if VPN connection fails, see note below
[*]verify remote connectivity - ping, rdp, ssh, etc.
[*]disconnect session
[/LIST][/INDENT][/INDENT]

[INDENT]d.  Subsequent connection attempts[/INDENT]
[INDENT][INDENT][LIST]
[*]open VPN connection
[*]enter password
[*]session should connect
[/LIST][/INDENT][/INDENT]

[INDENT]**Note:**  If you get the "Login Failed" message, cancel and wait 15-30 minutes before attempting to connect again.  Also, I ended up having to use the NT style *domain\username* pair for authentication, even though a Cisco AnyConnect client connecting to the same ASA only requires *username*.[/INDENT]

[INDENT]**More Detail:**  OpenConnect has been brutal to get connected.  I got failed attempt after failed attempt.  When I checked the NPS (IAS) log and the Security Event log on the W2K8 domain controller, I could see my user account authenticating properly via RADIUS from the ASA.  Yet the OpenConnect client came back with a "Login Failed" message. I'm not an ASA expert, so I have no idea what to check in the ASA configuration to troubleshoot this problem, other than the basic AAA configuration.  But I believe the problem lies in the ASA configuration because when I get the OpenConnect "Login Failed" message, the AnyConnect client from my Windows laptop fails as well.  I think it may be a ridiculously short timeout or max failure setting.  Whatever the issue is, I have to wait for some length of time (~15-30 minutes) for whatever the problem is to reset.

 However, once I finally get the OpenConnect client to successfully connect, it worked from then on.  (Just don't mess with the connection configuration, or you will get to go thru this whole process again.)[/INDENT]

-----------------------------

P.S.  Please leave me feedback for what worked and didn't work for you.  Also, if you can, please post a short description documenting what firewall/VPN device you were connecting to and any modifications you may have made to the VPN connection configuration.  Maybe we can make this a thread for known-good configurations.

Thanks.

---

### Post by PaBLoX_CL on 2009-11-17
I'm using Xubuntu 9.10 installed yesterday.

I followed your steps (pptp) (except introducing the user and pass which i did it) and it didn't work in the first time. I restarted the network manager with

sudo /etc/init.d/network-manager restart

And it asked me for my pass (weird because is already there), it also asked me if I wanted to save the pass to the keyring, but I denied everything. Finally it worked. Are you still having troubles?

---

### Post by sweisler on 2009-11-18
No issues with VPN connectivity to this point.  Once properly configured, the various VPN types perform as expected. The biggest issues surrounded discovering the correct options for each VPN type and getting the OpenConnect client to successfully connect the first time.

---

### Post by wasutton3 on 2009-11-18
I have followed this guide and i am not able to get it working. i am using a wrt150n with ddwrt-vpn on it. my iphone connects properly (as does my girlfriends mac) I dont have a windows computer to test with at the moment.

---

### Post by sweisler on 2009-11-18
It appears from reading the DD-WRT wiki that *<shudder>* CHAP is the authentication method used by DD-WRT.  You will need to go into the PPTP Advanced Options and select CHAP in the authentication methods list.

---

### Post by wasutton3 on 2009-11-20
I tried that method as well, without any success. :/

---

### Post by tubbyeddie on 2009-11-20
Well I'm able to establish a VPN connection now following the guide above. Thanks! But not all traffic is getting through or I'm not really connected to the local network. When connected to VPN I can see the outside world but not the local machines on the network. Works fine on windows.

---

### Post by tubbyeddie on 2009-11-20
Never mind. It was just not able to resolve names to IP addresses. Adding our dns server to resolve.conf fixed it.

---

### Post by VSKM on 2009-11-22
Note that the method suggested by sweisler does not work if firestarter is running. The best thing is to stop firestarter and then it works. You may even want to uninstall firestarter.

---

### Post by Rendawg on 2009-12-07
Great instructions.  The PPTP configuration worked as oulined.  I have had no luck getting my Cisco VPN connected.  I'm still trying and when I figure it out I will post my findings if they end up being any different then sweisler.  

Thanks for the great effort out here sweisler.

---

### Post by Rendawg on 2009-12-10
Hey Everyone,

As promised I'm back to post an update to my connection issues using VPNC.  

Issue: 
Can't connect to cisco VPN using VPNC no matter what settings I use in the Gui.  I always get a connection failure immediately upon trying to connect.  

Work around solution:
Started VPNC up in the console: sudo vpnc-connect

Then manually inputted all the settings to the host (just follow the requests via the command line) 

VPNC should connect.  Then open up your terminal server client (Applications/Internet/Terminal Server Client) and fill in the necessary info and you should connect.

It's not the cleanest or most convenient but does work for me. 

Hope this helps someone.  

Rene

---

### Post by firozm on 2009-12-18
Dear Sweisler,

Thanks a million for mentioning the steps. I have been struggling to connect to vpn on ubuntu 9.10 for last couple of weeks without any success and your information saved my life.

Really appreciate your help.

---

### Post by fstonedahl on 2009-12-30
I'll second that: Thanks sweisler!  I got my university VPN working just fine on 9.10 with the help of your clear PPTP instructions. :-)

---

### Post by sayantandas on 2010-01-04
Hi all,
Even after following the exact steps described above, I am still not able to connect to PPTP VPN connections. 
Here is the log viewer o/p. I keep getting the same sequence of errors

```
Jan  4 22:53:57  NetworkManager: <info>  VPN plugin failed: 1
Jan  4 22:53:57  NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan  4 22:53:57  pptp[8262]: nm-pptp-service-8256 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Jan  4 22:53:57  pptp[8262]: nm-pptp-service-8256 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Jan  4 22:53:57  pptp[8268]: nm-pptp-service-8256 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Jan  4 22:53:57  pptp[8268]: nm-pptp-service-8256 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Jan  4 22:53:57  pptp[8268]: nm-pptp-service-8256 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Jan  4 22:53:57 NetworkManager: <info>  VPN plugin failed: 1
Jan  4 22:53:57  NetworkManager: <info>  VPN plugin failed: 1
```

---

### Post by ubenturocks on 2010-01-21
I tried this but when I attempt to connect it does not ask for a password. I restarted the OS but it still does not work.

Is there any log file where I can see what goes wrong?
How do I make PPTP VPN work on 9.10?

Lars

---

### Post by J117 on 2010-01-29
> **PaBLoX_CL said:**
> I'm using Xubuntu 9.10 installed yesterday.

I followed your steps (pptp) (except introducing the user and pass which i did it) and it didn't work in the first time. I restarted the network manager with

sudo /etc/init.d/network-manager restart

And it asked me for my pass (weird because is already there), it also asked me if I wanted to save the pass to the keyring, but I denied everything. Finally it worked. Are you still having troubles?

That fixed my issues with the no secrets stuff. :grin:

---

### Post by isaac_liu on 2010-01-31
I am using UBUNTU 9.10 (64 bit) on AMD. I followed all the steps but I got the following messages in the log after I entered my password. I also tried using different options and even command line but this is the best I got. Please help.

Jan 31 14:47:06 Traverse NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Jan 31 14:47:06 Traverse NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 2684
Jan 31 14:47:06 Traverse NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Jan 31 14:47:06 Traverse NetworkManager: <info>  VPN plugin state changed: 1
Jan 31 14:47:13 Traverse NetworkManager: <info>  VPN plugin state changed: 3
Jan 31 14:47:13 Traverse pppd[2687]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Jan 31 14:47:13 Traverse NetworkManager: <info>  VPN connection 'AnsoftVPN' [COLOR=Red](Connect) reply received.[/COLOR]
Jan 31 14:47:13 Traverse pppd[2687]: pppd 2.4.5 started by root, uid 0
Jan 31 14:47:13 Traverse pptp[2689]: nm-pptp-service-2684 log[main:pptp.c:314]: [COLOR=Red]The synchronous pptp option is NOT activated[/COLOR]
Jan 31 14:47:13 Traverse pppd[2687]: Using interface ppp0
Jan 31 14:47:13 Traverse pppd[2687]: Connect: ppp0 <--> /dev/pts/3
Jan 31 14:47:13 Traverse NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan 31 14:47:13 Traverse NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): [COLOR=Red]no ifupdown configuration found.[/COLOR]
Jan 31 14:47:44 Traverse pppd[2687]: LCP: timeout sending Config-Requests
Jan 31 14:47:44 Traverse pppd[2687]: Connection terminated.
Jan 31 14:47:44 Traverse NetworkManager: <info>  VPN plugin failed: 1
Jan 31 14:47:44 Traverse NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan 31 14:47:44 Traverse pppd[2687]: Modem hangup
Jan 31 14:47:44 Traverse NetworkManager: <info>  VPN plugin failed: 1
Jan 31 14:47:49 Traverse pppd[2687]: Exit.
Jan 31 14:47:49 Traverse NetworkManager: <info>  VPN plugin failed: 1
Jan 31 14:47:49 Traverse NetworkManager: <info>  VPN plugin state changed: 6
Jan 31 14:47:49 Traverse NetworkManager: <info>  VPN plugin state change reason: 0
Jan 31 14:47:49 Traverse NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Jan 31 14:47:49 Traverse NetworkManager: <info>  Policy set 'Auto default' (wlan0) as default for routing and DNS.
Jan 31 14:48:02 Traverse NetworkManager: <debug> [1264967282.001826] ensure_killed(): waiting for vpn service pid 2684 to exit
Jan 31 14:48:02 Traverse NetworkManager: <debug> [1264967282.002028] ensure_killed(): vpn service pid 2684 cleaned up

---

### Post by isaac_liu on 2010-01-31
I entered the wrong IP for the VPN host. Now I managed to connect. But the speed is too slow to be of any use. I remember that I have seen posts talking about speed. I will work on it later.

Thanks to everyone who has posted helpful information everywhere!

---

### Post by gladstone1990 on 2010-02-02
Sweisler,

Your instructions on pptp were excellent and worked perfectly.

You've saved me a lot of annoyance walking back and forth to Uni to get data.

Cheers dude.

---

### Post by RayDeCampo on 2010-02-08
I have posted sweisler's excellent synopsis to [https://wiki.ubuntu.com/VPN](https://wiki.ubuntu.com/VPN).  I would encourage anybody who has any additions or edits to update there as well.

---

### Post by emab on 2010-03-20
> **sweisler said:**
> Here's a synopsis of my VPN setups.  I have proven this to work on both x86 and x64 for all 3 VPN types.

Important note/disclaimer: I tested these configurations on VMware Workstation 7 VM's and a Dell Vostro 220.  All installations were fresh installs, not upgrades.  Also, please notice that I detail what type of firewall/VPN I am connecting to for each VPN type.  There are so many variations on these VPN implementations that it is  extremely difficult to generalize a known-good configuration for each.

1. Install various VPN components[INDENT]a. PPTP[/INDENT][INDENT]
[LIST]
[*]pptp-linux
[*]network-manager-pptp
[/LIST]
[/INDENT][INDENT]b. VPNC[/INDENT][INDENT]
[LIST]
[*]vpnc
[*]network-manager-vpnc
[/LIST]
[/INDENT][INDENT]c. OpenConnect[/INDENT][INDENT]
[LIST]
[*]openconnect
[*]network-manager-openconnect
[/LIST]
[/INDENT]2. Reboot

3. PPTP VPN Configuration - This setup works for connecting to ISA 2004/2006 PPTP VPNs.  It should work for connecting to MS PPTP VPN implementations in general.  I can't speak for other PPTP VPN implementations.[INDENT]
a.  Create new PPTP connection[/INDENT][INDENT]
[LIST]
[*]VPN Tab Settings
[/LIST]
[/INDENT][INDENT][INDENT]
[LIST]
[*]Set Connection name
[*]Set Gateway
[*]Set username (for domain-based user accounts, use *domain\username*)
[*]**DO NOT SET PASSWORD**
[*]**DO NOT SET NT DOMAIN**
[/LIST]
[/INDENT][/INDENT][INDENT][INDENT]
[LIST]
[*]PPTP Advanced Options (Advanced button)
[/LIST]
[/INDENT][/INDENT][INDENT][INDENT][INDENT]
[LIST]
[*]uncheck all auth methods **EXCEPT MSCHAPv2**
[*]check "Use Point-to-Point encryption (MPPE)"[INDENT][INDENT][INDENT][INDENT]
[LIST]
[*]leave Security set at "All Available (Default)"
[*]trying to force encryption level causes this option to become unset
[/LIST]
[/INDENT][/INDENT][/INDENT][/INDENT]
[*]check "Allow stateful inspection"
[*]uncheck "Allow BSD Data Compression"
[*]uncheck "Allow Deflate Data Compression"
[*]uncheck "Use TCP Header Compression"
[*]uncheck "Send PPP Echo Packets" (although connection works either checked or unchecked)
[/LIST]
[/INDENT][/INDENT][/INDENT][INDENT][INDENT]
[LIST]
[*]save configuration
[/LIST]
[/INDENT][/INDENT][INDENT]b.  Initial Connection attempt[/INDENT][INDENT][INDENT]
[LIST]
[*]enter password in login box
[*]**DO NOT** check either password save box at this time
[*]once connection establishes, verify remote connectivity - ping, rdp, ssh, etc.
[*]disconnect VPN session
[/LIST]
[/INDENT][/INDENT][INDENT]c.  2nd connection attempt[/INDENT][INDENT][INDENT]
[LIST]
[*]enter password in login box
[*]check both password save option boxes
[*]once again verify remote connectivity
[*]disconnect VPN session
[/LIST]
[/INDENT][/INDENT][INDENT]d.  Subsequent connection attempts[/INDENT][INDENT][INDENT]
[LIST]
[*]VPN session should automatically connect using saved auth credentials
[/LIST]
[/INDENT][/INDENT]4. VPNC VPN Configuration - This setup works connecting to an ASA5510 - software version 8.2(1).  I didn't have any other Cisco devices to test against.[INDENT]
a.  Create new VPNC connection[/INDENT][INDENT][INDENT]
[LIST]
[*]set connection name
[*]set Gateway
[*]set Group Name
[*]set User Password to "Saved" and enter password
[*]set Group Password to "Saved" and enter password
[*]set username
[*]set domain (if applicable)
[*]leave Encryption Method at "Secure (Default)"
[*]set NAT traversal to "NAT-T"
[*]save configuration
[/LIST]
[/INDENT][/INDENT]    [INDENT]b.  Initial Connection attempt[/INDENT][INDENT][INDENT]
[LIST]
[*]open VPNC connection
[*]if prompted, select "Always Allow" if you want connection to be automatic
[*]verify remote connectivity - ping, rdp, ssh, etc.
[*]disconnect VPN session
[/LIST]
[/INDENT][/INDENT][INDENT]c.  Subsequent connection attempts[/INDENT][INDENT][INDENT]
[LIST]
[*]open VPNC connection - session should automatically connect
[/LIST]
[/INDENT][/INDENT]5. OpenConnect VPN Configuration - This setup works connecting to an ASA5510 - software version 8.2(1).  I didn't have any other Cisco devices to test against.
[INDENT]a.  Create new OpenConnect connection[/INDENT][INDENT][INDENT]
[LIST]
[*]set connection name
[*]set Gateway
[*]set Authentication type to "Password/SecurID"
[*]no need to set username, OpenConnect won't store it yet
[*]save configuration
[/LIST]
[/INDENT][/INDENT][INDENT]
b.  Initial connection attempt[/INDENT][INDENT][INDENT]
[LIST]
[*]open VPN connection
[*]check "Automatically start connecting next time"
[*]click Close
[*]you will get the "No Valid VPN Secrets" VPN failure message
[/LIST]
[/INDENT][/INDENT][INDENT]c.  2nd connection attempt[/INDENT][INDENT][INDENT]
[LIST]
[*]open VPN connection
[*]accept certificate (if prompted)
[*]change Group (if necessary)
[*]enter username (may need to be *domain\username*)
[*]enter password
[*]click Login
[*]if VPN connection fails, see note below
[*]verify remote connectivity - ping, rdp, ssh, etc.
[*]disconnect session
[/LIST]
[/INDENT][/INDENT][INDENT]d.  Subsequent connection attempts[/INDENT][INDENT][INDENT]
[LIST]
[*]open VPN connection
[*]enter password
[*]session should connect
[/LIST]
[/INDENT][/INDENT][INDENT]**Note:**  If you get the "Login Failed" message, cancel and wait 15-30 minutes before attempting to connect again.  Also, I ended up having to use the NT style *domain\username* pair for authentication, even though a Cisco AnyConnect client connecting to the same ASA only requires *username*.[/INDENT][INDENT]**More Detail:**  OpenConnect has been brutal to get connected.  I got failed attempt after failed attempt.  When I checked the NPS (IAS) log and the Security Event log on the W2K8 domain controller, I could see my user account authenticating properly via RADIUS from the ASA.  Yet the OpenConnect client came back with a "Login Failed" message. I'm not an ASA expert, so I have no idea what to check in the ASA configuration to troubleshoot this problem, other than the basic AAA configuration.  But I believe the problem lies in the ASA configuration because when I get the OpenConnect "Login Failed" message, the AnyConnect client from my Windows laptop fails as well.  I think it may be a ridiculously short timeout or max failure setting.  Whatever the issue is, I have to wait for some length of time (~15-30 minutes) for whatever the problem is to reset.

 However, once I finally get the OpenConnect client to successfully connect, it worked from then on.  (Just don't mess with the connection configuration, or you will get to go thru this whole process again.)[/INDENT]-----------------------------

P.S.  Please leave me feedback for what worked and didn't work for you.  Also, if you can, please post a short description documenting what firewall/VPN device you were connecting to and any modifications you may have made to the VPN connection configuration.  Maybe we can make this a thread for known-good configurations.

Thanks.


thank you very useful

---

### Post by marge123 on 2010-04-06
Hi, Sweisler :KS--

Reporting here on the happy result of your instructions above.

After installing and verifying the installation of the packages you listed, I set up a PPTP connection as described.  It succeeded on the 2nd attempt with both "password save option boxes" checked.

Thank you so much for this information -- I'd been troubleshooting this for about 6 hours when i made one last attempt using the error message for search criteria.

My connection is to a corporate VPN server on a Microsoft network with Active Directory.  Can't tell you what the version is.  LDAP is v3.

I access the server through a LAN, that is maintained by my son, who runs Debian.  I presume that the firewall is a Debian package.

Again, thanks so much.

Marge123

---

### Post by lajfi on 2010-04-20
> **sweisler said:**
> Here's a synopsis of my VPN setups.  I have proven this to work on both x86 and x64 for all 3 VPN types.

Important note/disclaimer: I tested these configurations on VMware Workstation 7 VM's and a Dell Vostro 220.  All installations were fresh installs, not upgrades.  Also, please notice that I detail what type of firewall/VPN I am connecting to for each VPN type.  There are so many variations on these VPN implementations that it is  extremely difficult to generalize a known-good configuration for each.

1. Install various VPN components
[INDENT]a. PPTP[/INDENT]
[INDENT][LIST]
[*]pptp-linux 
[*]network-manager-pptp
[/LIST][/INDENT]
[INDENT]b. VPNC[/INDENT]
[INDENT][LIST]
[*]vpnc
[*]network-manager-vpnc
[/LIST][/INDENT]
[INDENT]c. OpenConnect[/INDENT]
[INDENT][LIST]
[*]openconnect
[*]network-manager-openconnect
[/LIST][/INDENT]

2. Reboot

3. PPTP VPN Configuration - This setup works for connecting to ISA 2004/2006 PPTP VPNs.  It should work for connecting to MS PPTP VPN implementations in general.  I can't speak for other PPTP VPN implementations.
[INDENT]
a.  Create new PPTP connection[/INDENT]
[INDENT][LIST]
[*]VPN Tab Settings
[/LIST][/INDENT]
[INDENT][INDENT][LIST]
[*]Set Connection name
[*]Set Gateway
[*]Set username (for domain-based user accounts, use *domain\username*)
**[*]DO NOT SET PASSWORD**
**[*]DO NOT SET NT DOMAIN**
[/LIST][/INDENT][/INDENT]
[INDENT][INDENT][LIST]
[*]PPTP Advanced Options (Advanced button)
[/LIST][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][LIST]
[*]uncheck all auth methods **EXCEPT MSCHAPv2**
[*]check "Use Point-to-Point encryption (MPPE)"
[INDENT][INDENT][INDENT][INDENT][LIST]
[*]leave Security set at "All Available (Default)"
[*]trying to force encryption level causes this option to become unset
[/LIST][/INDENT][/INDENT][/INDENT][/INDENT]
[*]check "Allow stateful inspection"
[*]uncheck "Allow BSD Data Compression"
[*]uncheck "Allow Deflate Data Compression"
[*]uncheck "Use TCP Header Compression"
[*]uncheck "Send PPP Echo Packets" (although connection works either checked or unchecked)
[/LIST][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][LIST]
[*]save configuration
[/LIST][/INDENT][/INDENT]

[INDENT]b.  Initial Connection attempt[/INDENT]
[INDENT][INDENT][LIST]
[*]enter password in login box
[*]**DO NOT** check either password save box at this time
[*]once connection establishes, verify remote connectivity - ping, rdp, ssh, etc.
[*]disconnect VPN session
[/LIST][/INDENT][/INDENT]

[INDENT]c.  2nd connection attempt[/INDENT]
[INDENT][INDENT][LIST]
[*]enter password in login box
[*]check both password save option boxes
[*]once again verify remote connectivity
[*]disconnect VPN session
[/LIST][/INDENT][/INDENT]

[INDENT]d.  Subsequent connection attempts[/INDENT]
[INDENT][INDENT][LIST]
[*]VPN session should automatically connect using saved auth credentials
[/LIST][/INDENT][/INDENT]
4. VPNC VPN Configuration - This setup works connecting to an ASA5510 - software version 8.2(1).  I didn't have any other Cisco devices to test against.[INDENT]
a.  Create new VPNC connection[/INDENT]
[INDENT][INDENT][LIST]
[*]set connection name
[*]set Gateway
[*]set Group Name
[*]set User Password to "Saved" and enter password
[*]set Group Password to "Saved" and enter password
[*]set username
[*]set domain (if applicable)
[*]leave Encryption Method at "Secure (Default)"
[*]set NAT traversal to "NAT-T"
[*]save configuration
[/LIST][/INDENT][/INDENT]
	
[INDENT]b.  Initial Connection attempt[/INDENT]
[INDENT][INDENT][LIST]
[*]open VPNC connection
[*]if prompted, select "Always Allow" if you want connection to be automatic
[*]verify remote connectivity - ping, rdp, ssh, etc.
[*]disconnect VPN session
[/LIST]
[/INDENT][/INDENT]
[INDENT]c.  Subsequent connection attempts[/INDENT]
[INDENT][INDENT][LIST]
[*]open VPNC connection - session should automatically connect
[/LIST][/INDENT][/INDENT]

5. OpenConnect VPN Configuration - This setup works connecting to an ASA5510 - software version 8.2(1).  I didn't have any other Cisco devices to test against.

[INDENT]a.  Create new OpenConnect connection[/INDENT]
[INDENT][INDENT][LIST]
[*]set connection name
[*]set Gateway
[*]set Authentication type to "Password/SecurID"
[*]no need to set username, OpenConnect won't store it yet
[*]save configuration
[/LIST][/INDENT][/INDENT]
[INDENT]
b.  Initial connection attempt[/INDENT]
[INDENT][INDENT][LIST]
[*]open VPN connection
[*]check "Automatically start connecting next time"
[*]click Close
[*]you will get the "No Valid VPN Secrets" VPN failure message
[/LIST][/INDENT][/INDENT]

[INDENT]c.  2nd connection attempt[/INDENT]
[INDENT][INDENT][LIST]
[*]open VPN connection
[*]accept certificate (if prompted)
[*]change Group (if necessary) 
[*]enter username (may need to be *domain\username*)
[*]enter password
[*]click Login
[*]if VPN connection fails, see note below
[*]verify remote connectivity - ping, rdp, ssh, etc.
[*]disconnect session
[/LIST][/INDENT][/INDENT]

[INDENT]d.  Subsequent connection attempts[/INDENT]
[INDENT][INDENT][LIST]
[*]open VPN connection
[*]enter password
[*]session should connect
[/LIST][/INDENT][/INDENT]

[INDENT]**Note:**  If you get the "Login Failed" message, cancel and wait 15-30 minutes before attempting to connect again.  Also, I ended up having to use the NT style *domain\username* pair for authentication, even though a Cisco AnyConnect client connecting to the same ASA only requires *username*.[/INDENT]

[INDENT]**More Detail:**  OpenConnect has been brutal to get connected.  I got failed attempt after failed attempt.  When I checked the NPS (IAS) log and the Security Event log on the W2K8 domain controller, I could see my user account authenticating properly via RADIUS from the ASA.  Yet the OpenConnect client came back with a "Login Failed" message. I'm not an ASA expert, so I have no idea what to check in the ASA configuration to troubleshoot this problem, other than the basic AAA configuration.  But I believe the problem lies in the ASA configuration because when I get the OpenConnect "Login Failed" message, the AnyConnect client from my Windows laptop fails as well.  I think it may be a ridiculously short timeout or max failure setting.  Whatever the issue is, I have to wait for some length of time (~15-30 minutes) for whatever the problem is to reset.

 However, once I finally get the OpenConnect client to successfully connect, it worked from then on.  (Just don't mess with the connection configuration, or you will get to go thru this whole process again.)[/INDENT]

-----------------------------

P.S.  Please leave me feedback for what worked and didn't work for you.  Also, if you can, please post a short description documenting what firewall/VPN device you were connecting to and any modifications you may have made to the VPN connection configuration.  Maybe we can make this a thread for known-good configurations.

Thanks.

just letting you know the above works perfectly! thanks a million !

---

### Post by samjam on 2010-05-11
> **PaBLoX_CL said:**
> I'm using Xubuntu 9.10 installed yesterday.

I followed your steps (pptp) (except introducing the user and pass which i did it) and it didn't work in the first time. I restarted the network manager with

sudo /etc/init.d/network-manager restart

And it asked me for my pass (weird because is already there), it also asked me if I wanted to save the pass to the keyring, but I denied everything. Finally it worked. Are you still having troubles?

Fixed it for me too! I wasted half a day until I found your suggestion.

Thanks

Sam

---

### Post by fishtron on 2010-07-21
Thanks a billion. On Lucid, only took two tries to get through to my university's cisco vpn configuration.

Steps: installed everything and created a new configuration, failed to connect the first time ("VPN Service ended unexpectedly"). Certificate prompt did not come up. Second time, certificate popped up, then I entered my credentials, and was able to log in.

\\:D/

---

### Post by T40 on 2010-08-07
Hello to you,

I have done what was advised and I got connected but I can't believe that's the solution !
I'm using VPNC for connecting to my corporate network. We're using RSA SecureID tokens and have unique pins. 

First of all I managed to get myself connected using pure terminal. I invoke a command, it asks me for user name and password and I'm in.

I tried to make it more user friendly and I installed a Cisco plugin for Gnome Network Manager.
I imported PCF file but I could not connect, It was not even asking me for user name and password just giving me an error as in the subject.

Turning point was when I actually put my user name, my PIN and current code from the token and tried to connect.
This time it did connect successfully so it works.

BUT THIS IS NOT ACCEPTABLE SOLUTION. 

Could anyone advise what config/ software combination one uses to connect to VPN ? 
I'm not going to edit VPN profile each time I want to connect, it is just TOO MUCH hassle. 

Ideally I wish to just click on the profile, click connect, put my user name and password and I'm in.

At the moment, I need to edit profile, put my passcode and quickly save and connect before password change on the token. NOT very user friendly. 

Please advise, maybe I should use different network manager ? 


VPNC VPN Configuration - This setup works  connecting to an ASA5510 - software version 8.2(1).  I didn't have any  other Cisco devices to test against.[INDENT]
a.  Create new VPNC connection[/INDENT][INDENT][INDENT]
[LIST]
[*]set connection name
[*]set Gateway
[*]set Group Name
[*]set User Password to "Saved" and enter password   -!?!?!
[*]set Group Password to "Saved" and enter password  - ?!?!?!
[/LIST]
[/INDENT][/INDENT]

---

### Post by zaigham_tt on 2010-09-24
Dear all fellows,

i have installed Linux i.e ubuntu 10.04 on my PC in which i have installed pptp client and able to connect it successfully but problem is that it unable to browse internet. in windows it works fine.
Kindly help me out.
Regard,
Syed Zaigham Ali.

---

