---
title: "Tethering 8100 ATT LCP errors"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by idlehands on 2009-08-05
I have Ubuntu 8.10, a blackberry pearl 81xx, and a tethering plan. Through some guides posted here and elsewhere I was able to cobble together a link, as evidenced by me posting now, through the bluetooth tether connection. 

However I'm getting a couple errors

```
ug  5 10:19:47 johannt61p kernel: [ 2467.000035] FIREWALL: IN=ppp0 OUT= MAC= SRC=75.119.207.211 DST=10.112.225.226 LEN=40 TOS=0x00 PREC=0x00 TTL=252 ID=17698 PROTO=TCP SPT=80 DPT=47591 WINDOW=0 RES=0x00 RST URGP=0 
Aug  5 10:19:48 johannt61p pppd[7659]: LCP: Rcvd Code-Reject for code 9, id 77

```

id started at 0; they just keep popping up. My config info:
/etc/ppp/pap-secrets
```

#	*	password

"WAP@CINGULARGPRS.COM" BluetoothDialup "CINGULAR1"

```

#/etc/bluetooth/rfconf
```
rfcomm0 {
        bind yes;
        device your-phone-mac-address;
        channel your-phone-rfcomm-channel;
        comment "Bluetooth PPP Connection";
}

```

/etc/ppp/peers/bluetoothdialup

```
connect "/usr/sbin/chat -v -f /etc/chatscripts/AttGPRS"
usepeerdns
/dev/rfcomm0 115200
defaultroute
crtscts
lcp-echo-failure 0
user ""
password ""


``` 
# /etc/chatscripts/AttGPRS 
```
TIMEOUT 35
ECHO ON
ABORT '\nBUSY\r'
ABORT '\nERROR\r'
ABORT '\nNO ANSWER\r'
ABORT '\nNO CARRIER\r'
ABORT '\nNO DIALTONE\r'
ABORT '\nRINGING\r\n\r\nRINGING\r'
'' \rAT
#OK 'AT+CGDCONT=1,"IP","isp.cingular"'
OK 'AT+CGDCONT=1,"IP","wap.cingular"'
OK ATD*99***1#
CONNECT ""


```


I tried nothing in pap-secrets and isp.cingular as the most recent guide mentioned, and that did not work for me. when i swapped to pap-secrets and wap.cingular that got me this far. 

I'm hoping someone can explain the issues with LCP /Firewall errors, and if i should worry about changing them, or deal with the errors. Also why the difference between isp/wap cingular?

Thanks

---

