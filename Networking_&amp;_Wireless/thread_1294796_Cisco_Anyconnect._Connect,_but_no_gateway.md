---
title: "Cisco Anyconnect. Connect, but no gateway?"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by briwood on 2009-10-18
Thanks in advance for any suggestions.

After a few months of flawless operation, I can no longer use the campus VPN.  This seems to be a problem with my particular laptop configuration.  (AnyConnect works from Windows.)

I'm using:

Ubuntu 8.04 on AMD64
Any Connect 2.3.2016 
(problem was also occuring with 2.3.0254)

Here are my symptoms:

I authenticate successfully to the vpn using any of the full or split tunnel options.

I receive an IP assignment. The client status shows "Connection State: Reconnecting"

At this point I cannot connect to any destination that requires the tunnel. i.e. if I've connected to split tunnel I cannot connect to [www.berkeley.edu--if](www.berkeley.edu--if) I'm using full tunnel I can't connect anywhere.

After about 2 min the client status shows "Connection State: Reconnecting" and it never reconnects.

The problem seems to be I don't have a gateway after connecting to the vpn:

If NOT connected to the vpn /sbin/route give me:
```

bwood@voutcity:~/install$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 wlan0
link-local      *               255.255.0.0     U     0      0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
default         *               0.0.0.0         U     1000   0        0 eth0
```

When connected to the vpn

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 wlan0
136.152.208.0   *               255.255.254.0   U     0      0        0 cscotun0
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0

```
I don't think that the problem is my local wireless network.  I'm having this problem when trying to use the vpn from 2 different wireless networks both of which I've used successfully in the past.

In syslog I see some interesting lines:

```

Oct 18 12:30:31 voutcity vpndownloader: [p:30262  pp:30261]: ../../../Api/ProfileMgr.cpp:356 (0) getProfileNameFromHost No profile available for host ucbvpn-1-external.Berkeley.EDU.

 Oct 18 12:30:31 voutcity vpnagentd: A complete VPN connection has been established.
 Oct 18 12:30:31 voutcity vpnagentd: Establishing the Primary DTLS connection
 Oct 18 12:30:31 voutcity vpnagentd: [p:4325  pp:1]: error - IPC/SocketTransport_unix.cpp:1568 (1) send
 Oct 18 12:30:31 voutcity vpnagentd: [p:4325  pp:1]: error - IPC/SocketTransport_unix.cpp:888 (fe1f000b) internalWriteSocket
 Oct 18 12:30:31 voutcity vpnagentd: [p:4325  pp:1]: error - TlsProtocol.cpp:980 (fe1f000b) CSocketTransport::writeSocket
 Oct 18 12:30:31 voutcity vpnagentd: [p:4325  pp:1]: error - TlsProtocol.cpp:885 (fe1f000b) CTlsProtocol::flushNetworkBio
 Oct 18 12:30:31 voutcity vpnagentd: [p:4325  pp:1]: error - TlsProtocol.cpp:502 (fe1f000b) CTlsProtocol::initialHandshake
 Oct 18 12:30:31 voutcity vpnagentd: [p:4325  pp:1]: error - CdtpProtocol.cpp:507 (fe1f000b) initiateTunnel
 Oct 18 12:30:31 voutcity vpnagentd: [p:4325  pp:1]: error - TunnelStateMgr.cpp:1040 (fe1f000b) ITunnelProtocol::initiateTunnel callback
 Oct 18 12:30:31 voutcity vpnagentd: [p:4325  pp:1]: error - TunnelMgr.cpp:600 (fe1f000b) CTunnelStateMgr::initiateTunnel callback
 Oct 18 12:30:31 voutcity vpnagentd: The Primary DTLS connection is down
 Oct 18 12:30:31 voutcity vpndownloader: [p:30261  pp:30260]: ../../../Downloader/DownloaderDlg_unix.cpp:90 (0) downloader_GetOverallSuccess
 Oct 18 12:30:31 voutcity vpnui: [p:30239  pp:1]: ProfileMgr.cpp:356 (0) getProfileNameFromHost No profile available for host ucbvpn-1-external.Berkeley.EDU.

```

FWIW here's full syslog output during a VPN connection attempt:

```

Oct 18 12:30:09 voutcity vpnui: [p:30239  pp:1]: i18n/MsgCatalog.cpp:390 (fe000009) MsgCatalog::setCatalog Message translation catalog <AnyConnect> not in use.
Oct 18 12:30:09 voutcity vpnui: [p:30239  pp:1]: ClientIfcBase.cpp:80 (0) vpnapi vpnapi version 2.3.0254 () Initializing.
Oct 18 12:30:09 voutcity vpnui: [p:30239  pp:1]: PreferenceMgr.cpp:783 (0) loadPreferences Loading default preferences
Oct 18 12:30:09 voutcity vpnui: [p:30239  pp:1]: warning - CvcGtkNotifyBalloon.cpp:87 (0) dlopen libnotify.so.1: cannot open shared object file: No such file or directory
Oct 18 12:30:09 voutcity vpnui: [p:30239  pp:1]: ClientIfcBase.cpp:254 (0) ClientIfcBase :: attach Client successfully attached.
Oct 18 12:30:09 voutcity vpnui: [p:30239  pp:1]: ClientIfcBase.cpp:269 (0) ClientIfcBase :: attach Event detection implemented in client program.
Oct 18 12:30:17 voutcity vpnui: [p:30239  pp:1]: ProfileMgr.cpp:356 (0) getProfileNameFromHost No profile available for host ucbvpn-1-external.Berkeley.EDU.
Oct 18 12:30:17 voutcity vpnui: [p:30239  pp:1]: ProfileMgr.cpp:428 (0) ProfileMgr :: getHostInitSettings Profile "" not found. Using default settings
Oct 18 12:30:17 voutcity vpnui: [p:30239  pp:1]: ProfileMgr.cpp:356 (0) getProfileNameFromHost No profile available for host ucbvpn-1-external.Berkeley.EDU.
Oct 18 12:30:17 voutcity vpnui: [p:30239  pp:1]: ProfileMgr.cpp:428 (0) ProfileMgr :: getHostInitSettings Profile "" not found. Using default settings
Oct 18 12:30:17 voutcity vpnui: [p:30239  pp:1]: ProfileMgr.cpp:356 (0) getProfileNameFromHost No profile available for host ucbvpn-1-external.Berkeley.EDU.
Oct 18 12:30:17 voutcity vpnui: [p:30239  pp:1]: ProfileMgr.cpp:428 (0) ProfileMgr :: getHostInitSettings Profile "" not found. Using default settings
Oct 18 12:30:17 voutcity vpnui: [p:30239  pp:1]: ProfileMgr.cpp:356 (0) getProfileNameFromHost No profile available for host ucbvpn-1-external.Berkeley.EDU.
Oct 18 12:30:17 voutcity vpnui: [p:30239  pp:1]: ConnectMgr.cpp:682 (0) ConnectMgr :: connect Initiating connection to: https://ucbvpn-1-external.Berkeley.EDU/
Oct 18 12:30:17 voutcity vpnui: [p:30239  pp:1]: ConnectMgr.cpp:2046 (0) ConnectMgr :: setPromptAttributes CA is disabled
Oct 18 12:30:30 voutcity vpnui: [p:30239  pp:1]: ConnectIfc.cpp:930 (0) ConnectIfc::connect Auth Cookie acquired
Oct 18 12:30:30 voutcity vpnui: [p:30239  pp:1]: ConnectIfc.cpp:939 (0) ConnectIfc::connect Config Cookie acquired
Oct 18 12:30:30 voutcity vpnui: [p:30239  pp:1]: ConnectMgr.cpp:1128 (0) processIfcData Authentication succeeded
Oct 18 12:30:31 voutcity vpnui: [p:30239  pp:1]: ConnectIfc.cpp:1187 (0) ConnectIfc::getUpdateFileContent Update file located
Oct 18 12:30:31 voutcity vpnui: [p:30239  pp:1]: ConnectMgr.cpp:4280 (0) ConnectMgr :: launchCachedDownloader Successfully launched the cached downloader
Oct 18 12:30:31 voutcity vpndownloader: [p:30262  pp:30261]: ../../../Api/PreferenceMgr.cpp:783 (0) loadPreferences Loading default preferences
Oct 18 12:30:31 voutcity vpndownloader: [p:30262  pp:30261]: ../../../Api/ProfileMgr.cpp:356 (0) getProfileNameFromHost No profile available for host ucbvpn-1-external.Berkeley.EDU.
Oct 18 12:30:31 voutcity vpnagentd: [p:4325  pp:1]: MainThread.cpp:771 (0) (version 2.3.0254 )
Oct 18 12:30:31 voutcity kernel: cscotun0: Disabled Privacy Extensions
Oct 18 12:30:31 voutcity vpnagentd: [p:4325  pp:1]: RouteMgr.cpp:1401 (0) logInterfaces IP Address Interface List: 192.168.0.130
Oct 18 12:30:31 voutcity vpnagentd: [p:4325  pp:1]: VpnMgr.cpp:1689 (fe0b000c) CPublicProxies::setupProxyInfo
Oct 18 12:30:31 voutcity vpnagentd: [p:4325  pp:1]: warning - Utility/Win/HModuleMgr.cpp:133 (0) dlopen libz.so: cannot open shared object file: No such file or directory
Oct 18 12:30:31 voutcity vpnagentd: [p:4325  pp:1]: warning - CZLib.cpp:243 (fe000007) CHModuleMgr::STLoadLibrary
Oct 18 12:30:31 voutcity vpnagentd: [p:4325  pp:1]: error - CstpProtocol.cpp:345 (fe19000b) CZLib::CZLib
Oct 18 12:30:31 voutcity vpnagentd: Establishing the Primary SSL connection
Oct 18 12:30:31 voutcity vpnagentd: The Primary SSL connection has been established
Oct 18 12:30:31 voutcity vpnagentd: route cmd success: route add 169.229.205.229 255.255.255.255 0.0.0.0
Oct 18 12:30:31 voutcity vpnagentd: setting default gateway to 136.152.208.82
Oct 18 12:30:31 voutcity vpnagentd: route cmd success: route delete 0.0.0.0 0.0.0.0 0.0.0.0
Oct 18 12:30:31 voutcity vpnagentd: route cmd success: route add 0.0.0.0 0.0.0.0 136.152.208.82
Oct 18 12:30:31 voutcity vpnagentd: route cmd success: route delete 0.0.0.0 0.0.0.0 0.0.0.0
Oct 18 12:30:31 voutcity vpnagentd: route cmd success: route delete 0.0.0.0 0.0.0.0 192.168.0.1
Oct 18 12:30:31 voutcity vpnagentd: route cmd success: route delete 192.168.0.0 255.255.255.0 0.0.0.0
Oct 18 12:30:31 voutcity vpnagentd: route cmd success: route delete 169.254.0.0 255.255.0.0 0.0.0.0
Oct 18 12:30:31 voutcity vpnagentd: route cmd success: route add :: :: 0 9
Oct 18 12:30:31 voutcity vpnagentd: route cmd success: route delete fe00:: :: 7 4
Oct 18 12:30:31 voutcity vpnagentd: route cmd success: route delete ff00:: :: 8 4
Oct 18 12:30:31 voutcity vpnagentd: route cmd success: route delete ff00:: :: 8 4
Oct 18 12:30:31 voutcity vpnagentd: route cmd success: route delete fe80:: :: 7 4
Oct 18 12:30:31 voutcity vpnagentd: A complete VPN connection has been established.
Oct 18 12:30:31 voutcity vpnagentd: Establishing the Primary DTLS connection
Oct 18 12:30:31 voutcity vpnagentd: [p:4325  pp:1]: error - IPC/SocketTransport_unix.cpp:1568 (1) send
Oct 18 12:30:31 voutcity vpnagentd: [p:4325  pp:1]: error - IPC/SocketTransport_unix.cpp:888 (fe1f000b) internalWriteSocket
Oct 18 12:30:31 voutcity vpnagentd: [p:4325  pp:1]: error - TlsProtocol.cpp:980 (fe1f000b) CSocketTransport::writeSocket
Oct 18 12:30:31 voutcity vpnagentd: [p:4325  pp:1]: error - TlsProtocol.cpp:885 (fe1f000b) CTlsProtocol::flushNetworkBio
Oct 18 12:30:31 voutcity vpnagentd: [p:4325  pp:1]: error - TlsProtocol.cpp:502 (fe1f000b) CTlsProtocol::initialHandshake
Oct 18 12:30:31 voutcity vpnagentd: [p:4325  pp:1]: error - CdtpProtocol.cpp:507 (fe1f000b) initiateTunnel
Oct 18 12:30:31 voutcity vpnagentd: [p:4325  pp:1]: error - TunnelStateMgr.cpp:1040 (fe1f000b) ITunnelProtocol::initiateTunnel callback
Oct 18 12:30:31 voutcity vpnagentd: [p:4325  pp:1]: error - TunnelMgr.cpp:600 (fe1f000b) CTunnelStateMgr::initiateTunnel callback
Oct 18 12:30:31 voutcity vpnagentd: The Primary DTLS connection is down
Oct 18 12:30:31 voutcity vpndownloader: [p:30261  pp:30260]: ../../../Downloader/DownloaderDlg_unix.cpp:90 (0) downloader_GetOverallSuccess
Oct 18 12:30:31 voutcity vpnui: [p:30239  pp:1]: ProfileMgr.cpp:356 (0) getProfileNameFromHost No profile available for host ucbvpn-1-external.Berkeley.EDU.
Oct 18 12:30:31 voutcity vpnui: [p:30239  pp:1]: ConnectMgr.cpp:4309 (0) ConnectMgr :: launchCachedDownloader Cached Downloader terminated normally
Oct 18 12:30:31 voutcity vpnui: [p:30239  pp:1]: warning - ConnectMgr.cpp:1227 (0) processIfcData No profile configured on the secure gateway.
Oct 18 12:30:31 voutcity vpnui: [p:30239  pp:1]: ProfileMgr.cpp:356 (0) getProfileNameFromHost No profile available for host ucbvpn-1-external.Berkeley.EDU.
Oct 18 12:30:31 voutcity vpnui: [p:30239  pp:1]: ProfileMgr.cpp:428 (0) ProfileMgr :: getHostInitSettings Profile "" not found. Using default settings
Oct 18 12:30:31 voutcity vpnui: [p:30239  pp:1]: warning - PreferenceInfoBase.cpp:494 (0) addNewPreference Trying to create an existing preference.
Oct 18 12:31:11 voutcity vpnagentd: [p:4325  pp:1]: error - CstpProtocol.cpp:1507 (fe1e000b) CCstpProtocol::handleExpiredDPD
Oct 18 12:31:11 voutcity vpnagentd: [p:4325  pp:1]: error - TunnelStateMgr.cpp:1175 (fe1e000b) ITunnelProtocol::OnTunnelStatusChange callback
Oct 18 12:31:11 voutcity vpnagentd: The Primary SSL connection is being re-established
Oct 18 12:31:11 voutcity vpnagentd: The VPN client has sent a close message to the gateway: "Reconnecting to recover from error.", Severity 3, Type 17
Oct 18 12:31:11 voutcity vpnagentd: Low level reconnect reason code 6: "Reconnecting due to the disruption of the VPN connection to the secure gateway."
Oct 18 12:31:12 voutcity vpnagentd: [p:4325  pp:1]: warning - Utility/Win/HModuleMgr.cpp:133 (0) dlopen libz.so: cannot open shared object file: No such file or directory
Oct 18 12:31:12 voutcity vpnagentd: [p:4325  pp:1]: warning - CZLib.cpp:243 (fe000007) CHModuleMgr::STLoadLibrary
Oct 18 12:31:12 voutcity vpnagentd: [p:4325  pp:1]: error - CstpProtocol.cpp:345 (fe19000b) CZLib::CZLib

```

---

### Post by briwood on 2009-10-19
I am not totally sure what step I took fixed this:

Per Ryan Lovett (thanks Ryan!) I tried installing OpenConnect (instructions: [http://blog.bitengine.ca/?p=12](http://blog.bitengine.ca/?p=12)).  This required installing libxml2 (sudo apt-get install libxml2-dev) which was not on my system.  I aborted trying to use Open Connect because it requires 3 patches to my version of OpenSSL (ref: [http://www.infradead.org/openconnect.html](http://www.infradead.org/openconnect.html) (bottom of pg))

Uninstalled OpenConnect.  (I had used checkinstall to build from sources, so uninstalling was a breeze ([https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)))

Reinstalled the latest AnyConnect and was about to muck with route command when I realized that it was, well, working! Maybe installing libxml2 fixed it (I'm too scared to uninstall that right now to test).

The routes were at least part of the problem  here 's what my routes looked like when it was NOT working, but connected to the full tunnel:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 wlan0
136.152.208.0   *               255.255.254.0   U     0      0        0 cscotun0
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0
```

Here are my healthy routes now that it's working

```
bwood@voutcity:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
ucbvpn-1-extern 192.168.0.1     255.255.255.255 UGH   0      0        0 wlan0
192.168.0.0     *               255.255.255.0   U     0      0        0 wlan0
136.152.208.0   *               255.255.254.0   U     0      0        0 cscotun0
link-local      *               255.255.0.0     U     0      0        0 eth0
default         ucbvpn-208-119. 0.0.0.0         UG    0      0        0 cscotun0

```

It makes sense that 192.168.0.1 needs to be in there.  That's my wireless router. Without that, there is no talking to the internet.

Brian

---

### Post by briwood on 2009-10-19
Editing title to solved.

---

### Post by briwood on 2009-10-20
Found a workaround.  Plug an ethernet cable into my wireless router and bypass wireless altogether.

Looking at the healthy vs unhealthy logs here's the problem:

Healthy:

```
    Oct 19 12:23:13 voutcity vpnagentd: route cmd success: route add 169.229.205.229
         255.255.255.255 192.168.0.1

```
Unhealthy:

  ```
  Oct 20 11:34:22 voutcity vpnagentd: route cmd success: route add 169.229.205.229
         255.255.255.255 0.0.0.0
```

Note the 0.0.0.0.  So it occured to me that vpnagentd is often unable to find my wireless router.  Not surprising as wireless networking is unfortunately still a rocky area in linux.

I think wireless could be made to work if I write a shell script that takes in the vpn ip that I'm assigned as an argument and manually sets the routes.  I'll try that when I have time.

Brian
   

Brian Wood wrote:
> Hi Derek,
>
> Really appreciate your help.  It worked yesterday.  I used the full tunnel for 5 hours.  Then I rebooted.  Today the old problem is back.  The first thing I did was to uninstall/reinstall anyconnect via the shell scripts in the tarball from software.berkeley.edu.  That does not fix it.
>
> I will try manually issuing route commands, but I'm not entirely sure that's the problem.  Here are two syslog excerpts showing the difference between a healthy and unhealthy connection.  I find nothing googling "vpnagentd "IPC/SocketTransport" -voutcity" (The "-voutcity" excludes my own post on ubuntuforums yesterday.)
>
>
>     Healthy connection yesterday syslog:
>    
>         Oct 19 12:23:13 voutcity vpnagentd: Establishing the Primary SSL connection
>         Oct 19 12:23:13 voutcity vpnagentd: The Primary SSL connection has been establis
>         hed
>         Oct 19 12:23:13 voutcity vpnagentd: route cmd success: route add 169.229.205.229
>          255.255.255.255 192.168.0.1
>         Oct 19 12:23:13 voutcity vpnagentd: setting default gateway to 136.152.208.119
>         Oct 19 12:23:13 voutcity vpnagentd: route cmd success: route delete 0.0.0.0 0.0.
>         0.0 192.168.0.1
>         Oct 19 12:23:13 voutcity vpnagentd: route cmd success: route add 0.0.0.0 0.0.0.0
>          136.152.208.119
>         Oct 19 12:23:13 voutcity vpnagentd: route cmd success: route delete 0.0.0.0 0.0.
>         0.0 192.168.0.1
>         Oct 19 12:23:13 voutcity vpnagentd: route cmd success: route delete 192.168.0.0
>         255.255.255.0 0.0.0.0
>         Oct 19 12:23:13 voutcity vpnagentd: route cmd success: route delete 169.254.0.0
>         255.255.0.0 0.0.0.0
>         Oct 19 12:23:13 voutcity vpnagentd: A complete VPN connection has been establish
>         ed.
>         Oct 19 12:23:13 voutcity vpnagentd: Establishing the Primary DTLS connection
>         Oct 19 12:23:13 voutcity vpndownloader: [p:4755  pp:4754]: ../../../Downloader/DownloaderDlg_unix.cpp:90 (0) downloader_GetOverallSuccess
>         Oct 19 12:23:13 voutcity vpnui: [p:32474  pp:1]: ConnectMgr.cpp:4407 (0) ConnectMgr :: launchCachedDownloader Cached Downloader terminated normally
>         Oct 19 12:23:13 voutcity vpnui: [p:32474  pp:1]: warning - ConnectMgr.cpp:1282 (0) processIfcData No profile configured on the secure gateway.
>         Oct 19 12:23:13 voutcity vpnui: [p:32474  pp:1]: ProfileMgr.cpp:357 (0) getProfileNameFromHost No profile available for host ucbvpn-1-external.Berkeley.EDU.
>         Oct 19 12:23:13 voutcity vpnui: [p:32474  pp:1]: ProfileMgr.cpp:429 (0) ProfileMgr :: getHostInitSettings Profile "" not found. Using default settings
>         Oct 19 12:23:13 voutcity vpnui: [p:32474  pp:1]: ApiCert.cpp:143 (0) ApiCert :: getCertList Number of certificates found: 0
>         Oct 19 12:23:13 voutcity vpnui: [p:32474  pp:1]: warning - PreferenceInfoBase.cpp:494 (0) addNewPreference Trying to create an existing preference.
>         Oct 19 12:23:13 voutcity vpnagentd: The Primary DTLS connection has been established
>        
>
>
>
>     Unhealthy connection today syslog:
>    
>         Oct 20 11:34:22 voutcity vpnagentd: Establishing the Primary SSL connection
>         Oct 20 11:34:22 voutcity vpnagentd: The Primary SSL connection has been establis
>         hed
>         Oct 20 11:34:22 voutcity vpnagentd: route cmd success: route add 169.229.205.229
>          255.255.255.255 0.0.0.0
>         Oct 20 11:34:22 voutcity vpnagentd: setting default gateway to 136.152.208.103
>         Oct 20 11:34:22 voutcity vpnagentd: route cmd success: route delete 0.0.0.0 0.0.0.0 0.0.0.0
>         Oct 20 11:34:22 voutcity vpnagentd: route cmd success: route add 0.0.0.0 0.0.0.0 136.152.208.103
>         Oct 20 11:34:22 voutcity vpnagentd: route cmd success: route delete 0.0.0.0 0.0.0.0 0.0.0.0
>         Oct 20 11:34:22 voutcity vpnagentd: route cmd success: route delete 0.0.0.0 0.0.0.0 192.168.0.1
>         Oct 20 11:34:22 voutcity vpnagentd: route cmd success: route delete 192.168.0.0 255.255.255.0 0.0.0.0
>         Oct 20 11:34:22 voutcity vpnagentd: route cmd success: route delete 169.254.0.0 255.255.0.0 0.0.0.0
>         Oct 20 11:34:22 voutcity vpnagentd: A complete VPN connection has been established.
>         Oct 20 11:34:22 voutcity vpnagentd: Establishing the Primary DTLS connection
>         Oct 20 11:34:22 voutcity vpnagentd: [p:25821  pp:1]: error - IPC/SocketTransport_unix.cpp:1568 (1) send
>         Oct 20 11:34:22 voutcity vpnagentd: [p:25821  pp:1]: error - IPC/SocketTransport_unix.cpp:888 (fe1f000b) internalWriteSocket
>         Oct 20 11:34:22 voutcity vpnagentd: [p:25821  pp:1]: error - TlsProtocol.cpp:980 (fe1f000b) CSocketTransport::writeSocket
>         Oct 20 11:34:22 voutcity vpnagentd: [p:25821  pp:1]: error - TlsProtocol.cpp:885 (fe1f000b) CTlsProtocol::flushNetworkBio
>         Oct 20 11:34:22 voutcity vpnagentd: [p:25821  pp:1]: error - TlsProtocol.cpp:502 (fe1f000b) CTlsProtocol::initialHandshake
>         Oct 20 11:34:22 voutcity vpnagentd: [p:25821  pp:1]: error - CdtpProtocol.cpp:507 (fe1f000b) initiateTunnel
>         Oct 20 11:34:22 voutcity vpnagentd: [p:25821  pp:1]: error - TunnelStateMgr.cpp:1040 (fe1f000b) ITunnelProtocol::initiateTunnel callback
>         Oct 20 11:34:22 voutcity vpnagentd: [p:25821  pp:1]: error - TunnelMgr.cpp:600 (fe1f000b) CTunnelStateMgr::initiateTunnel callback
>         Oct 20 11:34:22 voutcity vpnagentd: The Primary DTLS connection is down
>        
>        
>
>
> Derek Chan wrote:
>> Yes, you are correct.
>>
>> I started a reply, wondered about which tunnel config you were using (the
>> routes would be different) and missed one.
>>
>> On Mon, Oct 19, 2009 at 12:25:57PM -0700, Brian Wood wrote:
>>   
>>> Here are my healthy routes now that it's working
>>>
>>> bwood@voutcity:~$ route
>>> Kernel IP routing table
>>> Destination     Gateway         Genmask         Flags Metric Ref    Use 
>>> Iface
>>> ucbvpn-1-extern 192.168.0.1     255.255.255.255 UGH   0      0        0 
>>> wlan0
>>> 192.168.0.0     *               255.255.255.0   U     0      0        0 
>>> wlan0
>>> 136.152.208.0   *               255.255.254.0   U     0      0        0 
>>> cscotun0
>>> link-local      *               255.255.0.0     U     0      0        0 eth0
>>> default         ucbvpn-208-119. 0.0.0.0         UG    0      0        0 
>>> cscotun0
>>>     
>>
>> Yes, this looks right.
>>
>> Traffic to the VPN gateway goes out through your router.
>> Traffic to the local network and to the VPN subnets would not require a
>> gateway, and
>> Everything else (full tunnel) would go through the vpn gateway.
>>
>>   
>>> If I'm right about that, after connecting I think I should issue these 2 
>>> commands.
>>>     
>>
>> route del default
>> route add <vpn ip> gw 192.168.0.1
>> route add default gw 136.152.208.82
>>
>> Or maybe, as your above suggests, maybe 136.152.208.119.  I'm not sure exactly
>> what the VPN infrastructure looks like.  Might depend on the gateway you
>> connect to, or it might not matter at all.
>>
>>   
>

---

### Post by briwood on 2009-10-22
Not solved.  The wired connection work around works in general, but means you always have to be tethered.  It looks like this is the fix on Windows: [http://ubuntuforums.org/showthread.php?p=8146547](http://ubuntuforums.org/showthread.php?p=8146547)

---

### Post by dwmw3 on 2009-11-02
> **briwood said:**
>   I aborted trying to use Open Connect because it requires 3 patches to my version of OpenSSL (ref: [http://www.infradead.org/openconnect.html](http://www.infradead.org/openconnect.html) (bottom of pg))


You don't need the OpenSSL patches to get connectivity; you only need them if you want to use DTLS (UDP). It would be _nice_ if ubuntu were to ship a current version of OpenSSL, but you don't actually need it. OpenConnect ought to work fine anyway.

---

