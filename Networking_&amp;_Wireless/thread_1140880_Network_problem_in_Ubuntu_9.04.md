---
title: "Network problem in Ubuntu 9.04"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by rogsmn on 2009-04-28
Hello Everybody, a few days back i installed Ubuntu 9.04 on my system and since then i am facing some weird network problems. First i have configured my eth0 interface using pppoeconf command. After that when ever i  connect to the internet using pon, well it gets connected but suddenly after some time i stop receiving the data and after some time the data resumes transmission. Also the speed is very slow. I am using HUAWEI MT880 modem. I know that i can add a dsl connect through NETWORK MANAGER but it does'nt show up when i left click the icon on the panel. i am sending u the output of PLOG that i have captured i hope after seeing that u can get some idea of what is going on. Any help will be appretiated.

roger@astron-desk:~$ sudo pppoeconf
Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
roger@astron-desk:~$ plog
Apr 28 10:07:49 astron-desk pppd[4142]: CHAP authentication succeeded
Apr 28 10:07:49 astron-desk pppd[4142]: peer from calling number 00:E0:FC:45:2E:7F authorized
Apr 28 10:07:49 astron-desk pppd[4142]: Cannot determine ethernet address for proxy ARP
Apr 28 10:07:49 astron-desk pppd[4142]: local  IP address 59.95.78.106
Apr 28 10:07:49 astron-desk pppd[4142]: remote IP address 59.95.64.1
Apr 28 10:07:49 astron-desk pppd[4142]: primary   DNS address 218.248.255.177
Apr 28 10:07:49 astron-desk pppd[4142]: secondary DNS address 218.248.255.193
Apr 28 10:08:05 astron-desk pppd[4683]: Plugin rp-pppoe.so loaded.
Apr 28 10:08:05 astron-desk pppd[4683]: RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
Apr 28 10:08:05 astron-desk pppd[4685]: pppd 2.4.5 started by root, uid 0
roger@astron-desk:~$ plog
Apr 28 10:11:00 astron-desk pppd[4142]: Using interface ppp1
Apr 28 10:11:00 astron-desk pppd[4142]: Connect: ppp1 <--> eth0
Apr 28 10:11:03 astron-desk pppd[4142]: CHAP authentication succeeded: Authentication success,Welcome!
Apr 28 10:11:03 astron-desk pppd[4142]: CHAP authentication succeeded
Apr 28 10:11:03 astron-desk pppd[4142]: peer from calling number 00:E0:FC:45:2E:7F authorized
Apr 28 10:11:03 astron-desk pppd[4142]: Cannot determine ethernet address for proxy ARP
Apr 28 10:11:03 astron-desk pppd[4142]: local  IP address 59.95.71.108
Apr 28 10:11:03 astron-desk pppd[4142]: remote IP address 59.95.64.1
Apr 28 10:11:03 astron-desk pppd[4142]: primary   DNS address 218.248.255.177
Apr 28 10:11:03 astron-desk pppd[4142]: secondary DNS address 218.248.255.193
roger@astron-desk:~$ plog
Apr 28 10:15:28 astron-desk pppd[4685]: Connect time 4.0 minutes.
Apr 28 10:15:28 astron-desk pppd[4685]: Sent 63140 bytes, received 1353025 bytes.
Apr 28 10:15:34 astron-desk pppd[4685]: Connection terminated.
Apr 28 10:15:34 astron-desk pppd[4685]: Modem hangup
Apr 28 10:15:38 astron-desk pppd[4393]: No response to 4 echo-requests
Apr 28 10:15:38 astron-desk pppd[4393]: Serial link appears to be disconnected.
Apr 28 10:15:38 astron-desk pppd[4393]: Connect time 2.5 minutes.
Apr 28 10:15:38 astron-desk pppd[4393]: Sent 400 bytes, received 104 bytes.
Apr 28 10:15:44 astron-desk pppd[4393]: Connection terminated.
Apr 28 10:15:44 astron-desk pppd[4393]: Modem hangup
roger@astron-desk:~$ plog
Apr 28 10:15:28 astron-desk pppd[4685]: Connect time 4.0 minutes.
Apr 28 10:15:28 astron-desk pppd[4685]: Sent 63140 bytes, received 1353025 bytes.
Apr 28 10:15:34 astron-desk pppd[4685]: Connection terminated.
Apr 28 10:15:34 astron-desk pppd[4685]: Modem hangup
Apr 28 10:15:38 astron-desk pppd[4393]: No response to 4 echo-requests
Apr 28 10:15:38 astron-desk pppd[4393]: Serial link appears to be disconnected.
Apr 28 10:15:38 astron-desk pppd[4393]: Connect time 2.5 minutes.
Apr 28 10:15:38 astron-desk pppd[4393]: Sent 400 bytes, received 104 bytes.
Apr 28 10:15:44 astron-desk pppd[4393]: Connection terminated.
Apr 28 10:15:44 astron-desk pppd[4393]: Modem hangup
roger@astron-desk:~$ plog
Apr 28 10:15:28 astron-desk pppd[4685]: Connect time 4.0 minutes.
Apr 28 10:15:28 astron-desk pppd[4685]: Sent 63140 bytes, received 1353025 bytes.
Apr 28 10:15:34 astron-desk pppd[4685]: Connection terminated.
Apr 28 10:15:34 astron-desk pppd[4685]: Modem hangup
Apr 28 10:15:38 astron-desk pppd[4393]: No response to 4 echo-requests
Apr 28 10:15:38 astron-desk pppd[4393]: Serial link appears to be disconnected.
Apr 28 10:15:38 astron-desk pppd[4393]: Connect time 2.5 minutes.
Apr 28 10:15:38 astron-desk pppd[4393]: Sent 400 bytes, received 104 bytes.
Apr 28 10:15:44 astron-desk pppd[4393]: Connection terminated.
Apr 28 10:15:44 astron-desk pppd[4393]: Modem hangup
roger@astron-desk:~$ plog
Apr 28 10:16:58 astron-desk pppd[4476]: CHAP authentication succeeded: Authentication success,Welcome!
Apr 28 10:16:58 astron-desk pppd[4476]: CHAP authentication succeeded
Apr 28 10:16:58 astron-desk pppd[4476]: peer from calling number 00:E0:FC:45:2E:7F authorized
Apr 28 10:16:58 astron-desk pppd[4476]: not replacing existing default route through ppp1
Apr 28 10:16:58 astron-desk pppd[4476]: Cannot determine ethernet address for proxy ARP
Apr 28 10:16:58 astron-desk pppd[4476]: local  IP address 59.95.75.180
Apr 28 10:16:58 astron-desk pppd[4476]: remote IP address 59.95.64.1
Apr 28 10:16:58 astron-desk pppd[4476]: primary   DNS address 218.248.255.177
Apr 28 10:16:58 astron-desk pppd[4476]: secondary DNS address 218.248.255.193
roger@astron-desk:~$

---

### Post by ayonkhan on 2009-05-01
Same problem here. :(

---

### Post by SACHINVD on 2009-05-01
Same Problem here

---

### Post by ehsun7b on 2009-05-01
I receive this: RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5

After sudo pon dsl-provider too

---

### Post by darkhole on 2009-05-03
Same problem here:
[http://ubuntuforums.org/showthread.php?t=1144666](http://ubuntuforums.org/showthread.php?t=1144666)

Seems like a Network Manager Bug:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/355826](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/355826)

---

### Post by SACHINVD on 2009-05-03
Problem solved

I just set up dsl connection by clicking icon(Network connection) at right side of menu bar and net starts working.

---

### Post by ayonkhan on 2009-05-03
> **SACHINVD said:**
> Problem solved

I just set up dsl connection by clicking icon(Network connection) at right side of menu bar and net starts working.
But it also stopped working with me. :(

---

### Post by SACHINVD on 2009-05-23
> **ayonkhan said:**
> But it also stopped working with me. :(

@ayonkhan :: Same trick not working for u 

What problem u r getting ?

---

### Post by contadinoste on 2009-09-04
Apr 28 10:15:38 astron-desk pppd[4393]: No response to 4 echo-requests 

if you get this try to put the value 
10 instead of 4 in /etc/ppp/options at the line "echo request failure" o similar

---

### Post by perlsite on 2009-12-12
I'm not sure whether this is the same bug or some weird coincidence:
I have Internet problems since... some of latest apt updates, let's say since one or two weeks: my Internet become sooo slow. My connection drops time to time (rarely) and when I do "sudo /etc/init.d/networking restart" I receive the following messages:
* Reconfiguring network interfaces...                                                                                                                                           SIOCDELRT: No such process
Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5

which I remember, I have never experienced before. After small network research I found that I have 30-50% packets loss. I found this thread and then noticed that my network manager has selected "Enable wireless" on the menu, but I have explicitly disabled through (hardware) key on my notebook, so maybe there is some conflict. Then I removed the "Enable wireless" check and then immediately my internet start to fly again and now no packets loss.
I hope this is not a temporary solution/effect.. try and report..

---

