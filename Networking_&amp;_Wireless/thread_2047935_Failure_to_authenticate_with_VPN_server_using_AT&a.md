---
title: "Failure to authenticate with VPN server using AT&amp;T Global Network client"
date: 2012-08-25
forum: Networking &amp; Wireless
---

### Post by susja on 2012-08-25
Hello,
I'm using AT&T Global Network client in order to connect to my [[COLOR=blue][COLOR=blue !important][FONT=inherit !important][COLOR=blue ! important][FONT=inherit ! important]corporate [/FONT][/COLOR][COLOR=blue ! important][FONT=inherit ! important]network[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.computing.net/answers/networking/failure-to-authenticate-with-vpn-server-using-at-t-client/50112.html#").  I am connecting over existing internet connection. After I profided all  credentials I've got message 'Authentication suceeded' . Next message:  'Connecting to [[COLOR=blue][COLOR=blue !important][FONT=inherit !important][COLOR=blue !important][FONT=inherit !important]VPN [/FONT][/COLOR][COLOR=blue !important][FONT=inherit !important]server[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.computing.net/answers/networking/failure-to-authenticate-with-vpn-server-using-at-t-client/50112.html#") ...' and here it hangs.
For  some reason it failed to connect to VPN. I was using AT&T client on  Ubuntu 12.04. Then I installed AT&T client on Windows XP but I've  got exact same issue and timed-out while trying to connect to [[COLOR=blue][COLOR=blue !important][FONT=inherit !important][COLOR=blue !important][FONT=inherit !important]VPN[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.computing.net/answers/networking/failure-to-authenticate-with-vpn-server-using-at-t-client/50112.html#"). 
My ISP is FiOS Verizon and I'm connected wired to router.
Here are the detailed message while it tries to connect:
08/25 18:33:19.293 [0441] CSC Adapter 'eth0' has fam=10 addr=0.0.0.0.
08/25 18:33:19.294 [0441] CSC starting auth command: /opt/agns/bin/smx_auth 204.146.172.230   
08/25 18:33:19.298 [0441] CSC authProcessingThread() started.
08/25 18:33:19.306 [1451] GUI AGNC ACTIONREQUESTED: '100'
08/25 18:33:19.306 [1451] GUI in action_requested_callback, parameter = 100
08/25 18:33:19.362 [0441] CSC FSM: [[COLOR=blue][COLOR=blue !important][FONT=inherit !important][COLOR=blue !important][FONT=inherit !important]VPN [/FONT][/COLOR][COLOR=blue !important][FONT=inherit !important]connection[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.computing.net/answers/networking/failure-to-authenticate-with-vpn-server-using-at-t-client/50112.html#") requested.
08/25 18:33:19.363 [0441] CSC FSM: agnclientd version is 2.0.1.3003.
08/25 18:33:19.364 [0441] CSC SLR1000 - SLRStartNewVPNConnection() was called.
08/25 18:33:19.364 [1451] GUI agnState changed from 10 to 100.
08/25 18:33:19.365 [0441] CSC STATE received.
08/25 18:33:19.368 [1451] GUI agnState changed from 100 to 200.
08/25 18:33:19.392 [0441] CSC STATE received.
08/25 18:33:29.003 [0441] CSC [[COLOR=blue][COLOR=blue !important][FONT=inherit !important][COLOR=blue !important][FONT=inherit !important]authentication[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.computing.net/answers/networking/failure-to-authenticate-with-vpn-server-using-at-t-client/50112.html#") completed, auth_rc = 0
08/25 18:33:29.004 [0441] CSC authProcessingThread() ended.
08/25 18:33:29.004 [0441] CSC FSM: Authentication response received (SMX 0x00 - 00000000).
08/25 18:33:29.004 [0441] CSC FSM: Authentication succeeded. (first VPN server 204.146.24.55)
08/25 18:33:29.005 [1451] GUI agnState changed from 200 to 300.
08/25 18:33:29.006 [0441] CSC STATE received.
08/25 18:33:29.031 [1451] GUI Connecting status 'Authentication succeeded.'
08/25 18:33:29.031 [1451] GUI Connecting status 'Connecting to VPN server...'

---

### Post by beboylips on 2012-08-26
Is it possible to use alternative VPN clients to connect to your corporate network? If yes, you should try those.

---

