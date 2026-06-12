---
title: "Bluetooth working sometimes (sometimes not)"
date: 2011-09-03
forum: Networking &amp; Wireless
---

### Post by josvanr on 2011-09-03
hi

11.04 kubuntu, trying to transfer files from my phone to my notebook via bluetooth. Sometimes it works and sometimes it doesn't. Can't really figure out why. I tried playing with all kinds of settings but it doesn't really have a reproducable effect. I will be able to send a file, and when I try to send the next, it won't work anymore. Restarting bluetooth also doesn't help (service bluetooth restart). Any ideas about this?....

josvanr

---

### Post by 2F4U on 2011-09-03
Do you get any error messages in case that the file is not transferred? Maybe a look into the system log reveals an error message?

---

### Post by josvanr on 2011-09-03
I should have checked. There seems to be some error message/warning
I'll look for that one..


jos@samsungsucks:/var/log$ sudo service bluetooth restart
[sudo] password for jos: 
 * Stopping bluetooth                                                                                                                                                                                                    [ OK ] 
 * Starting bluetooth                                                                                                                                                                                                    [ OK ] 
jos@samsungsucks:/var/log$ 
jos@samsungsucks:/var/log$ 
jos@samsungsucks:/var/log$ grep blue * -i|grep 19:52
grep: btmpauth.log:Sep  3 19:52:51 samsungsucks sudo:      jos : TTY=pts/3 ; PWD=/var/log ; USER=root ; COMMAND=/usr/sbin/service bluetooth restart
: Permission denied
grep: btmp.1: Permission denied
syslog:Sep  3 19:52:52 samsungsucks bluetoothd[9597]: Stopping hci0 event socket
syslog:Sep  3 19:52:52 samsungsucks bluetoothd[9597]: Stopping SDP server
syslog:Sep  3 19:52:52 samsungsucks bluetoothd[9597]: Exit
syslog:Sep  3 19:52:53 samsungsucks bluetoothd[11961]: Bluetooth deamon 4.91
syslog:Sep  3 19:52:53 samsungsucks bluetoothd[11963]: Starting SDP server
syslog:Sep  3 19:52:53 samsungsucks bluetoothd[11963]: Listening for HCI events on hci0
syslog:Sep  3 19:52:53 samsungsucks NetworkManager[856]: <warn> bluez error getting default adapter: No such adapter
syslog:Sep  3 19:52:53 samsungsucks bluetoothd[11963]: HCI dev 0 up
syslog:Sep  3 19:52:53 samsungsucks bluetoothd[11963]: input-headset driver probe failed for device D4:88:90:C7:A5:A1
syslog:Sep  3 19:52:53 samsungsucks bluetoothd[11963]: Adapter /org/bluez/11961/hci0 has been enabled

---

