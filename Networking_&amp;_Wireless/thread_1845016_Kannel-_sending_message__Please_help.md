---
title: "Kannel- sending message  Please help"
date: 2011-09-16
forum: Networking &amp; Wireless
---

### Post by lukengup_forum on 2011-09-16
This is my kannel configuration
group = core
admin-port = 13000
admin-password = "moses"
status-password = "moses"
smsbox-port = 13001
wapbox-port = 13002
log-file = "/var/log/kannel/bearerbox.log"
log-level = 1
#wdp-interface-name = "*"
box-deny-ip = "*.*.*.*"
box-allow-ip = "127.0.0.1"
#store-type=mysql
dlr-storage = mysql
smsbox-max-pending=100


group = smsc
smsc = smpp
smsc-id =1911
system-type =VMA
service-type=SMS
host =hostname
smsc-username=username
smsc-password=password
port = 2775
transceiver-mode = 1
interface-version=34
bind-addr-ton = 1
bind-addr-npi = 1
connect-allow-ip = "127.0.0.1;192.168.*.*"
send-url = "http://localhost:13013/cgi-bin/sendsms"

this is the php script to send SMS

<?php
error_reporting(E_ALL);
ini_set('display_errors','On');
define('CONFIG_KANNEL_USER_NAME', 'kanneluser');
define('CONFIG_KANNEL_PASSWORD', 'moses');
define('CONFIG_KANNEL_HOST', 'localhost');
define('CONFIG_KANNEL_PORT', '13013');

sendSmsMessage('0710862896','test');


function sendSmsMessage($in_phoneNumber, $in_msg)
 {
   $url = '/cgi-bin/sendsms?username=' . CONFIG_KANNEL_USER_NAME
          . '&password=' . CONFIG_KANNEL_PASSWORD
          . '&charset=UCS-2&coding=2'
          . "&to={$in_phoneNumber}"
        . '&text=' . urlencode(iconv('utf-8', 'ucs-2', $in_msg));
          

   $results = file('http://'
                   . CONFIG_KANNEL_HOST . ':'
                   . CONFIG_KANNEL_PORT . $url);
   print_r($results);
 }

?>

This is the message I get from the browser:
Array (     [0] => 0: Accepted for delivery ) 

this is the status message from kannel admin
**C2TSMPP**    SMPP:higate2.integrat.co.za:2775/2775:C2TestSMPP:VMA (online 1002s, rcvd 0, sent 0, failed 1, queued 0 msgs)

this is the kannel log

2011-09-16 10:46:45 [8208] [6] WARNING: SMPP: PDU NULL terminated string (message_id) has no NULL.
2011-09-16 10:46:45 [8208] [6] ERROR: SMPP[1911]: SMSC returned error code 0x00000194 (Unknown/Reserved) in response to submit_sm.

Can anyone knows why  the message is failling. I have tried my service provider support. they are also clueless.

---

