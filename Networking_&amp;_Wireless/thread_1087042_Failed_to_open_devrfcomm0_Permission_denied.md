---
title: "Failed to open /dev/rfcomm0: Permission denied"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by ms3811 on 2009-03-04
Issue: When trying to connect to the Internet using my BlackBerry Pearl 8130 via Bluetooth using the command "pppd call verizon" I get the error message "pppd: In file /etc/ppp/peers/verizon: unrecognized option '/dev/rfcomm0'".

Background: After numerous attempts to get this working, I finally managed to do so by doing the following:

1. fresh install of Ubuntu 8.10
2. created the following files:

/etc/ppp/peers/verizon
debug debug debug
nodetach
rfcomm0
921600
debug
noauth
defaultroute
replacedefaultroute
usepeerdns
connect-delay 10000
user [email]3105551212@vzw3g.com[/email] #replace with my actual phone number
show-password
crtscts
passive
lock

persist        # Redial if connection lost
holdoff 2      # Reconnect after 5s on connection loss

lcp-echo-failure 32
lcp-echo-interval 65535

connect "/usr/sbin/chat -v -f /etc/chatscripts/verizon-connect"
disconnect "/usr/sbin/chat -v -f /etc/chatscripts/verizon-disconnect"

/etc/chatscripts/verizon-connect
TIMEOUT 10
ABORT 'BUSY'
ABORT 'NO ANSWER'
ABORT 'ERROR'
SAY 'Starting WWAN...\n'

""      'ATZ'

OK    'AT'
OK    'AT&F&D2&C1E0V1S0=0'
OK    'AT+IFC=2,2'
OK    'ATS0=0'

# List signal quality
#'OK' 'AT+CSQ'

'OK' 'ATDT#777'
CONNECT

/etc/chatscripts/verizon-disconnect
"" "\K"
"" "+++ATH0"
SAY "Disconnected."

3. edited /etc/ppp/chap-secrets to read as follows:
"3105551212@vzw3g.com" * "vzw" #replace with my actual phone number

4. connected the 8130 to my laptop using bluetooth, entered pins, etc. got connected.

5. ran "pppd call verizon"

6. and bingo, I got connected. 

One time. And then, it stopped working. The next time I ran "pppd call verizon", I got the error message in Issue at the beginning of this post. Since then I have googled this to death. Amongst the various things I tried, I edited /etc/bluetooth/rfcomm.conf to read as follows:
rfcomm0 {
device AA:BB:CC:00:11:22; #replace my actual device id
channel 1;
}

Then I execute "rfcomm bind rfcomm0". Now when I run "pppd call verizon" I get the following:

Starting WWAN...
Connect script failed
Starting WWAN...
Connect script failed

This is a new laptop (Dell Mini9 N series). 

Any help would be really appreciated. Thank you.

---

