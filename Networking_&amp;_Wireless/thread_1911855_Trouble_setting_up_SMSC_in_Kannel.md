---
title: "Trouble setting up SMSC in Kannel"
date: 2012-01-19
forum: Networking &amp; Wireless
---

### Post by newmobdev on 2012-01-19
Hello,

I'm having trouble setting up a SMSC. I'm trying to use the Huawei K3770 USB Modem as a SMSC to send an sms to a mobile device. I'm running Kannel 1.4.3 in Ubuntu 11.10, all in a VirtualBox. When I run the bearerbox, Kannel doesn't connect to the device (the status page always says "connecting"). The following is a section of the bearerbox log file. I'm not sure why the device is always opening then closing:

2012-01-19 15:09:53 [4726] [6] DEBUG: AT2[huawei_k3770_00]: device opened. Telnet mode = 0
2012-01-19 15:09:54 [4726] [6] DEBUG: AT2[huawei_k3770_00]: device opened
2012-01-19 15:09:54 [4726] [6] INFO: AT2[huawei_k3770_00]: speed set to 9600
2012-01-19 15:09:54 [4726] [6] DEBUG: AT2[huawei_k3770_00]: --> ^M
2012-01-19 15:09:56 [4726] [6] DEBUG: AT2[huawei_k3770_00]: --> AT^M
2012-01-19 15:10:00 [4726] [6] DEBUG: AT2[huawei_k3770_00]: --> AT^M
2012-01-19 15:10:01 [4726] [6] DEBUG: AT2[huawei_k3770_00]: <-- ^DSFLOWRPT:00001C86,00000000,00000000,000000000000E566,0000000000028248,00010000,00010000
2012-01-19 15:10:04 [4726] [6] DEBUG: AT2[huawei_k3770_00]: --> AT^M
2012-01-19 15:10:08 [4726] [6] INFO: AT2[huawei_k3770_00]: Closing device
2012-01-19 15:10:08 [4726] [6] INFO: AT2[huawei_k3770_00]: cannot detect speed
2012-01-19 15:10:08 [4726] [6] ERROR: AT2[huawei_k3770_00]: Couldn't connect (retrying in 10 seconds).
2012-01-19 15:10:18 [4726] [6] DEBUG: AT2[huawei_k3770_00]: detecting modem speed. 
2012-01-19 15:10:18 [4726] [6] INFO: AT2[huawei_k3770_00]: opening device
2012-01-19 15:10:18 [4726] [6] DEBUG: AT2[huawei_k3770_00]: device opened. Telnet mode = 0
2012-01-19 15:10:19 [4726] [6] DEBUG: AT2[huawei_k3770_00]: device opened
2012-01-19 15:10:19 [4726] [6] INFO: AT2[huawei_k3770_00]: speed set to 115200
2012-01-19 15:10:19 [4726] [6] DEBUG: AT2[huawei_k3770_00]: --> ^M
2012-01-19 15:10:21 [4726] [6] DEBUG: AT2[huawei_k3770_00]: --> AT^M
2012-01-19 15:10:25 [4726] [6] DEBUG: AT2[huawei_k3770_00]: --> AT^M
2012-01-19 15:10:29 [4726] [6] DEBUG: AT2[huawei_k3770_00]: --> AT^M
2012-01-19 15:10:33 [4726] [6] INFO: AT2[huawei_k3770_00]: Closing device
2012-01-19 15:10:33 [4726] [6] INFO: AT2[huawei_k3770_00]: opening device
2012-01-19 15:10:33 [4726] [6] DEBUG: AT2[huawei_k3770_00]: device opened. Telnet mode = 0


etc... I also get "trying to open device with not closed device". Here is my configuration file contents:


#
# Configuration file for Kannel Bearerbox and Smsbox
#
group = core
admin-port = 13000
admin-password = bar
admin-deny-ip = "*.*.*.*
admin-allow-ip = "127.0.0.1"
log-file = "/tmp/kannel.log"
log-level = 0
smsbox-port = 13001
box-deny-ip = "*.*.*.*"
box-allow-ip = "127.0.0.1"
dlr-storage = mysql

# SMSC CONNECTIONS
# SMSC GSM - Huawei K3770
group = smsc
smsc = at
smsc-id = huawei_k3770_00
port = 13012
modemtype = auto
device = /dev/ttyUSB1
sms-center = +2772xxxxxxx #SIM Number
my-number = +2772xxxxxxx #SIM Number
connect-allow-ip = "127.0.0.1"
pin = xxxx #SIM PIN

# MODEMS!
group = modems
id = huawei_k3770_00
name = "Huawei K3770"
speed = 7200000
detect-string = "Huawei"
detect-string2 = "K3770"

# SMSBOX SETUP
group = smsbox
smsbox-id = mysmsbox
bearerbox-host = "127.0.0.1"
sendsms-port = 13013
sendsms-chars = "0123456789 +-"
# global-sender = 13013

# SEND-SMS USERS
group = sendsms-user
username = tester
password = foobar

# SMS SERVICES
group = sms-service
keyword = nop
text = "You asked nothing and I did it!"

# SMS SERVICE Default
# there should be default always
group = sms-service
keyword = default
text = "No service specified"

# MYSQL CONNECTION
group = mysql-connection
id = mydlr
host = "127.0.0.1"
username = xxxx
password = xxxx
database = dlr
max-connections = 1

# DLR TABLE STRUCTURE
group = dlr-db
id = mydlr
table = dlr
field-smsc = smsc
field-timestamp = ts
field-destination = destination
field-source = source
field-service = service
field-url = url
field-mask = mask
field-status = status
field-boxc-id = boxc


I am very new to Kannel (and Ubuntu) so any assistance would be greatly appreciated!!

---

