---
title: "EDGE USB Modem configuration"
date: 2006-01-09
forum: Networking &amp; Wireless
---

### Post by michal.svk on 2006-01-09
Hi all, 

here a quick help, how to connect to the internet using an EDGE USB Modem. This works fine in Slovakia, Czech republic and Austria, but should work well in other countries with other local providers too.

1. To find out, to which port is the USB modem connected

Open the Device Manager, check the USB hubs and look for “8-bit FIFO”- device.  
On the “Advanced”-tab, check the key linux.device_file, the value of this key shows the location of the USB modem (like /dev/ttyUSB0, /dev/ttyUSB1 etc.). This value is needed for the configuration script, step 2.

2. The file „EDGE“ – path: /etc/ppp/peers/

/etc/ppp/peers/edge

/dev/usb/ttyUSB0 230400
crtscts
user ""
debug
noauth
connect '/usr/sbin/chat -v -f /etc/chatscripts/edge'
nodetach
noipx
usepeerdns
ipcp-accept-local
local
novj
novjccomp
nobsdcomp
disconnect '/usr/sbin/chat -v -f /etc/chatscripts/edge-hang'
defaultroute
usepeerdns

In the first line, there is the location of the modem (see step 1), here /dev/usb/ttyUSB0 and then the speed (here 230400 bps, but You will get this setting from Your provider).

The line „connect '/usr/sbin/chat -v -f /etc/chatscripts/edge'“ shows the location of the dialing script, which is used to establish the connection.

The line “disconnect '/usr/sbin/chat -v -f /etc/chatscripts/edge-hang'” shows the location of the script, that is used to terminate the connection.

3. The file „EDGE“ – path: /etc/chatscripts/

/etc/chatscripts/edge

TIMEOUT 20
ABORT BUSY
ABORT "NO CARRIER"
ABORT VOICE
ABORT "NO DIALTONE"
""
ATZ OK
at+cgdcont=1,"IP","internet" OK
"ATD*99#" CONNECT

The phone number comes in the last line, here *99#. You will get it from Your provider.

4. The file „EDGE-HANG“ – path: /etc/chatscripts/

/etc/chatscripts/edge-hang

"" "+++ath"

5. The files „CHAP-SECRETS“ and “PAP-SECRETS” – path for both: /etc/ppp/

/etc/ppp/chap-secrets
/etc/ppp/pap-secrets

*[Tab]*[Tab]""

There is no username or password, the modem uses the SIM-card data for authentication.

6. The connection

In terminal, type 
pppd call edge

---

