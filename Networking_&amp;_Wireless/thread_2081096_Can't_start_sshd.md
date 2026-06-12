---
title: "Can't start sshd"
date: 2012-11-05
forum: Networking &amp; Wireless
---

### Post by netsense on 2012-11-05
Hi all,

I'm nearing the end of a Mythbuntu 12.04 setup, and one of my remaining issues is that ssh won't start - at boot, or manually thereafter. I've googled it, and the superficial symptoms appear fairly common, but the solutions don't work.

Apart from the obvious "connection refused", symptoms are

[LIST=1]
[*]```
sudo service ssh status
ssh stop/waiting
```
[*]dmesg, syslog & kern.log show variants of
> [18344.110054] init: ssh main process (8193) terminated with status 255 [18344.110154] init: ssh main process ended, respawning [18344.134244] init: ssh main process (8196) terminated with status 255 [18344.134351] init: ssh main process ended, respawning [18344.156683] init: ssh main process (8199) terminated with status 255 [18344.156781] init: ssh main process ended, respawning [18344.178392] init: ssh main process (8202) terminated with status 255 [18344.178486] init: ssh main process ended, respawning [18344.198454] init: ssh main process (8205) terminated with status 255 [18344.198554] init: ssh main process ended, respawning [18344.221485] init: ssh main process (8208) terminated with status 255 [18344.221573] init: ssh main process ended, respawning [18344.243958] init: ssh main process (8211) terminated with status 255 [18344.244126] init: ssh main process ended, respawning [18344.267251] init: ssh main process (8215) terminated with status 255 [18344.267343] init: ssh main process ended, respawning [18344.290456] init: ssh main process (8218) terminated with status 255 [18344.290597] init: ssh main process ended, respawning [18344.316569] init: ssh main process (8221) terminated with status 255 [18344.316690] init: ssh main process ended, respawning [18344.341336] init: ssh main process (8224) terminated with status 255 [18344.341427] init: ssh respawning too fast, stopped
[*]auth.log shows
> Nov  6 13:52:38 HTPC sudo:    edwin : TTY=pts/1 ; PWD=/home/edwin ; USER=root ; COMMAND=/usr/sbin/service ssh start Nov  6 13:52:38 HTPC sudo: pam_unix(sudo:session): session opened for user root by edwin(uid=1000) Nov  6 13:52:38 HTPC sudo: pam_unix(sudo:session): session closed for user root Nov  6 13:53:51 HTPC sudo:    edwin : TTY=pts/1 ; PWD=/home/edwin ; USER=root ; COMMAND=/bin/cat /etc/network/interfaces Nov  6 13:53:51 HTPC sudo: pam_unix(sudo:session): session opened for user root by edwin(uid=1000) Nov  6 13:53:51 HTPC sudo: pam_unix(sudo:session): session closed for user root Nov  6 13:54:58 HTPC sudo:    edwin : TTY=pts/1 ; PWD=/home/edwin ; USER=root ; COMMAND=/bin/ps ax Nov  6 13:54:58 HTPC sudo: pam_unix(sudo:session): session opened for user root by edwin(uid=1000) Nov  6 13:54:58 HTPC sudo: pam_unix(sudo:session): session closed for user root Nov  6 13:56:57 HTPC sudo:    edwin : TTY=pts/1 ; PWD=/home/edwin ; USER=root ; COMMAND=/usr/bin/nano /etc/ssh/sshd_config Nov  6 13:56:57 HTPC sudo: pam_unix(sudo:session): session opened for user root by edwin(uid=1000) Nov  6 14:00:57 HTPC sudo: pam_unix(sudo:session): session closed for user root Nov  6 14:08:25 HTPC sudo:    edwin : TTY=pts/1 ; PWD=/home/edwin ; USER=root ; COMMAND=/usr/sbin/service ssh status Nov  6 14:08:25 HTPC sudo: pam_unix(sudo:session): session opened for user root by edwin(uid=1000) Nov  6 14:08:25 HTPC sudo: pam_unix(sudo:session): session closed for user root Nov  6 14:09:01 HTPC CRON[9237]: pam_unix(cron:session): session opened for user root by (uid=0) Nov  6 14:09:01 HTPC CRON[9237]: pam_unix(cron:session): session closed for user root Nov  6 14:11:49 HTPC login[7520]: pam_unix(login:session): session closed for user edwin
[*]ifconfig shows 
> eth0      Link encap:Ethernet  HWaddr 00:25:22:47:1d:64                                    inet addr:172.31.255.104  Bcast:172.31.255.255  Mask:255.255.255.0               inet6 addr: fe80::225:22ff:fe47:1d64/64 Scope:Link                               UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1                               RX packets:823733 errors:0 dropped:0 overruns:0 frame:0                          TX packets:443120 errors:0 dropped:0 overruns:0 carrier:0                        collisions:0 txqueuelen:1000                                                     RX bytes:1166182373 (1.1 GB)  TX bytes:33179526 (33.1 MB)                        Interrupt:21                                                                                                                                            lo        Link encap:Local Loopback                                                        inet addr:127.0.0.1  Mask:255.0.0.0                                              inet6 addr: ::1/128 Scope:Host                                                   UP LOOPBACK RUNNING  MTU:16436  Metric:1                                         RX packets:41413 errors:0 dropped:0 overruns:0 frame:0                           TX packets:41413 errors:0 dropped:0 overruns:0 carrier:0                         collisions:0 txqueuelen:0                                                        RX bytes:6636451 (6.6 MB)  TX bytes:6636451 (6.6 MB)
[*]ps ax | grep ssh shows                                                   
> 2049 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-s ession /usr/share/mythbuntu/session.sh                                            9954 pts/1    S+     0:00 grep --color=auto ssh
[*]sshd_config, stripped of comments, reads as follows:
 > Port 22
#ListenAddress ::
ListenAddress 172.31.255.0
Protocol 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
UsePrivilegeSeparation yes
SyslogFacility AUTH
LogLevel INFO
PermitRootLogin yes
StrictModes yes
RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile    %h/.ssh/authorized_keys
IgnoreRhosts yes
RhostsRSAAuthentication no
HostbasedAuthentication no
#IgnoreUserKnownHosts yes
PermitEmptyPasswords no
# ChallengeResponseAuthentication yes
PasswordAuthentication yes
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes
#GSSAPIAuthentication no
X11Forwarding yes
PrintMotd yes
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no
#MaxStartups 10:30:60
#Banner /etc/issue.net
AcceptEnv LANG LC_*
Subsystem sftp /usr/lib/openssh/sftp-server
UsePAM yes
IgnoreUserKnownHosts no
GatewayPorts no
AllowTcpForwarding yes
KeepAlive yes
# PasswordAuthentication yes
[/LIST]
Can anyone help -please? :(


THanks.

---

### Post by Lars Noodén on 2012-11-06
What output do you get from trying to start it manually in debug mode?

```

sudo /usr/sbin/sshd -Dd

```

---

