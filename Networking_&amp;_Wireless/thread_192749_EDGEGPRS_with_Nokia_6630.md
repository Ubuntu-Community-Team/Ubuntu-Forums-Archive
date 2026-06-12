---
title: "EDGE/GPRS with Nokia 6630"
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by Ali Karam on 2006-06-09
Hi,

I'm having trouble connecting to the net using my Nokia 6630 mobile phone
this is what I have in /etc/ppp/peers/provider :
```
# Serial device to which the GPRS phone is connected
/dev/bus/usb/003/002

# Comment this off, if you don't need more info
debug

# scripts to initialize the 3G / EDGE / GPRS modem
connect /etc/ppp/peers/connect-chat

# AT commands used to 'hangup' the connection
disconnect /etc/ppp/peers/disconnect-chat

# Serial port line speed
460800


# hardware flow control for cable
crtscts

# Ignore carrier detect signal from the modem:
local

# IP addresses
lcp-echo-failure 0
lcp-echo-interval 0

# - accept peers idea of our local address and set address peer as 10.6.6.6
# (any address would do, since IPCP gives 0.0.0.0 to it)
# - if you use the 10. network at home or something and pppd rejects it,
# change the address to something else
:10.6.6.6

# pppd must not propose any IP address to the peer!
noipdefault

# Accept peers idea of our local address
ipcp-accept-local

# Add the ppp interface as default route to the IP routing table
defaultroute

# New route should be our default route to Internet
replacedefaultroute

# User DNS returned by server
usepeerdns

# The phone is not required to authenticate
noauth

# Most phone do not support compression, so turn it off.
novj
nobsdcomp
novjccomp
nopcomp
noaccomp

# Username and password:
# If username and password are required by the APN, put here the username
# and put the username-password combination to the secrets file:
# /etc/ppp/pap-secrets for PAP and /etc/ppp/chap-secrets for CHAP
# authentication. See pppd man pages for details.
# Change this if you are not using Celcom 3G!
# user "celcom3g"

# Persistent connection
persist

# Retry and retry and retry if failed...
maxfail 99999
```

I tried
```
pppd call provider
```
and no output

I checked my logs and found this
```
Jun  9 11:16:13 localhost kernel: [4315301.671000] usb 3-2: generic converter now attached to ttyUSB0
Jun  9 11:16:13 localhost kernel: [4315301.673000] usbserial_generic 3-2:1.10: generic converter detected
Jun  9 11:16:13 localhost kernel: [4315301.673000] usbserial_generic: probe of 3-2:1.10 failed with error -5
Jun  9 11:26:15 localhost pppd[18239]: pppd 2.4.4b1 started by ali, uid 1000
Jun  9 11:26:15 localhost pppd[18239]: Exit.
```

although I can see my Nokia connected when I plug it to the USB using lsusb
```
Bus 003 Device 002: ID 0421:0410 Nokia Mobile Phones 6630 Imaging Smartphone
```

Any idea on how to fix this ?

---

### Post by Ali Karam on 2006-06-09
By the way,

This is my /etc/ppp/peers/connect-chat
```
#!/bin/sh
exec chat                                               \
        TIMEOUT         5                               \
        ECHO            ON                              \
        ABORT           '\nBUSY\r'                      \

        ABORT           '\nERROR\r'                     \
        ABORT           '\nNO ANSWER\r'                 \
        ABORT           '\nNO CARRIER\r'                \
        ABORT           '\nNO DIALTONE\r'               \
        ABORT           '\nRINGING\r\n\r\nRINGING\r'    \
        ''              \rAT                            \
        TIMEOUT         12                              \
        SAY             "Press CTRL-C to close the connection at any stage!"    \

        SAY             "\ndefining PDP context...\n"   \
        OK              ATH                             \
        OK              ATE1                            \
        OK              ATD*99#                         \
        TIMEOUT         22                              \
        SAY             "\nwaiting for connect...\n"    \
        CONNECT         ""                              \
        SAY             "\nConnected." \
        SAY             "\nIf the following ppp negotiations fail,\n"   \

         SAY             "try restarting the phone.\n"
```

and this is my /etc/ppp/peers/disconnect-chat

```
#!/bin/sh
# send break exec /usr/sbin/chat -V -s -S    \
ABORT           "BUSY"          \
ABORT           "ERROR"         \
ABORT           "NO DIALTONE"   \
SAY             "\nSending break to the modem\n"        \
""              "\K"            \
""              "\K"            \

""              "\K"            \
""              "\d\d+++\d\dATH"        \
SAY             "\nPDP context detached\n"
```

---

### Post by mukherjee.siddhartha on 2006-09-27
[http://www.ubuntuforums.org/showthread.php?t=257091&highlight=GPRS+Nokia+6630](http://www.ubuntuforums.org/showthread.php?t=257091&highlight=GPRS+Nokia+6630)

This works for me perfect.

---

