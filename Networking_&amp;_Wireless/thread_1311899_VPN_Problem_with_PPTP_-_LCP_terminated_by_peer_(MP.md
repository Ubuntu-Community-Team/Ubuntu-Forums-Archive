---
title: "VPN Problem with PPTP - LCP terminated by peer (MPPE required)"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by diskace on 2009-11-02
I have tried to have my VPN connection up and i am unable to make it work after several tricks. The VPN session work fine from my Windows machine.

- refuse eap under .gconf/system/networking/connections/1/vpn#

here is the syslog:

Nov  2 19:10:09 fixit-desktop pppd[3331]: Using interface ppp0
Nov  2 19:10:09 fixit-desktop pppd[3331]: Connect: ppp0 <--> /dev/pts/4
Nov  2 19:10:09 fixit-desktop pptp[3339]: nm-pptp-service-3318 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Nov  2 19:10:09 fixit-desktop pptp[3339]: nm-pptp-service-3318 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Nov  2 19:10:09 fixit-desktop pptp[3339]: nm-pptp-service-3318 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Nov  2 19:10:10 fixit-desktop pptp[3339]: nm-pptp-service-3318 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Nov  2 19:10:10 fixit-desktop pptp[3339]: nm-pptp-service-3318 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Nov  2 19:10:10 fixit-desktop pptp[3339]: nm-pptp-service-3318 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 7936).
Nov  2 19:10:10 fixit-desktop pppd[3331]: CHAP authentication succeeded
Nov  2 19:10:10 fixit-desktop pppd[3331]: LCP terminated by peer (MPPE required but peer negotiation failed)
Nov  2 19:10:10 fixit-desktop pptp[3339]: nm-pptp-service-3318 log[pptp_read_some:pptp_ctrl.c:544]: read returned zero, peer has closed
Nov  2 19:10:10 fixit-desktop pptp[3339]: nm-pptp-service-3318 log[callmgr_main:pptp_callmgr.c:258]: Closing connection (shutdown)
Nov  2 19:10:10 fixit-desktop pptp[3339]: nm-pptp-service-3318 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Nov  2 19:10:10 fixit-desktop pptp[3339]: nm-pptp-service-3318 log[pptp_read_some:pptp_ctrl.c:544]: read returned zero, peer has closed
Nov  2 19:10:10 fixit-desktop pptp[3339]: nm-pptp-service-3318 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Nov  2 19:10:10 fixit-desktop pppd[3331]: Modem hangup
Nov  2 19:10:10 fixit-desktop pppd[3331]: Connection terminated.
Nov  2 19:10:10 fixit-desktop NetworkManager: <info>  VPN plugin failed: 1
Nov  2 19:10:10 fixit-desktop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Nov  2 19:10:10 fixit-desktop pppd[3331]: Exit.
Nov  2 19:10:10 fixit-desktop NetworkManager: <info>  VPN plugin failed: 1
Nov  2 19:10:10 fixit-desktop NetworkManager: <info>  VPN plugin state changed: 6
Nov  2 19:10:10 fixit-desktop NetworkManager: <info>  VPN plugin state change reason: 0
Nov  2 19:10:10 fixit-desktop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Nov  2 19:10:10 fixit-desktop NetworkManager: <info>  Policy set 'Ethernet' (eth0) as default for routing and DNS.

MPPE option is on.

---

### Post by diskace on 2009-11-03
Anyone ?

I managed to get the vpn up by disabling the nm-client control and connecting from the shell with 'pon' but i would prefer to have that automated.

---

### Post by jonobr on 2009-11-03
Have you seen this resource?.[PPTP troubles]("http://pptpclient.sourceforge.net/howto-diagnosis.phtml#mppe_rbpnf")

Its pretty good, and has a reference to what your error message, but Im not sure if it relates


> MPPE required but peer negotiation failed
Symptom: require-mppe-128 option is set, and debug logs contain this sequence:

sent [CCP ConfReq id=0x1 <mppe +H -M +S +L -D -C>]
rcvd [CCP ConfReq id=0x4 <mppe +H -M -S -L -D +C>]
MPPE required but peer negotiation failed
sent [LCP TermReq id=0x4 "MPPE required but peer negotiation failed"]  

with the essential component being the immediate termination by the local host on receipt of a CCP ConfReq that has the encryption bits turned off (-M -S -L).

Diagnosis: this is a defect of pppd on your system. It is terminating the connection on the basis that the peer started to suggest no encryption. Your pppd is not first negotiating to achieve encryption. The version of pppd you are using takes the require-mppe-128 option pedantically; refusing to connect if the peer is configured to allow no encryption, even if the peer may allow encryption after negotiation.


2005-01-19  

Solution: you may fix this by (either); 

using a later version of pppd that is not so pedantic, and will negotiate further to achieve encryption (a fix was made in revision 1.49 of file pppd/ccp.c in PPP CVS as the solution to closed Debian bug 294232 but is not yet released by the PPP project ... so you can upgrade to PPP CVS or apply the patch in the bug report), or

2006-03-09  

removing the require-mppe-128 option from the file /etc/ppp/options.pptp and any other options given to pppd, if you are content with not using encryption (which can be risky),

configuring the peer to require encryption. 
If the peer is a server is on the public internet, you may wish to warn the administrator that it is not set to require encryption, and so tunnels may be established in the clear, which is an information security risk. If they change the configuration to require encryption, this seems to fix this problem, because the initial negotiation attempt includes MPPE.


2005-01-19  


(If the peer is Microsoft Windows 2000 acting as a server, check that the No Encryption option in Remote Access Policies is disabled. Rob Gamble provided us with instructions to fix this.) 



---

