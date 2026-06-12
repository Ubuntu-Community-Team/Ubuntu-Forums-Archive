---
title: "DBus.Error.NoReply connecting to SSH server"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by mistafeesh on 2011-01-12
Hi, I've got a file and web server which I've been setting up at the same time as a laptop, both running Ubuntu 10.10 Desktop...

It's worked before, but now when I use the 'connect to server' dialogue and select SSH, enter the IP and username, before I get to enter my password I get an error:
> DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

I can connect from another computer running the liveCD, so maybe the error is on the client rather than the server, but I'm not sure... 

Yesterday I was adding something to the startup items on the server and I removed an UbuntuOne item as I don't use that service... I'm wondering if that's caused the problem as when I googled for that error most of the results were related to UbuntuOne... Doesn't seem to make sense but I don't know for sure.

I've reinstalled ntfs and ssh on the server and ssh on the client, with no change...

---

### Post by PatchesTheCaveman on 2011-01-12
Can you SSH into the server via the command-line?  Go to Applications > Accessories > Terminal and run:
```
ssh *username*@*server*
```

Even if that doesn't work it should give you a more useful error.

---

### Post by mistafeesh on 2011-01-12
Hmmm. I get > ssh: connect to host 192.168.0.2 port 22: No route to host

PS just checked and I CAN connect to the samba server on that machine

---

### Post by PatchesTheCaveman on 2011-01-12
Do you have a firewall on the server machine?  Is port 22 open on it?

Also, verify that the ssh server is running:
```
sudo service ssh start
```

---

### Post by mistafeesh on 2011-01-12
I get 'Job is already running: ssh'
I'm fairly sure it must be a client problem as I can connect from another computer running the liveCD

---

### Post by PatchesTheCaveman on 2011-01-12
Try disabling the firewall on the client machine:
```
sudo ufw disable
```

---

### Post by mistafeesh on 2011-01-14
Thanks. 'Firewall stopped  and disabled on system startup' which is fine with me.
Annoyingly I get the same error though when I try to connect...

Also, it connected fine yesterday for a few hours until I turned everything off for the night... I've also noticed a that the same computer is sporadically unable to find other stuff on the local network such as my web server through the browser and another samba server (running on a mac) even though it's been able to connect to the internet and all other computers on the network can access everything else...

I'm wondering if it could be an error in my network connection set up. I just looked on the network tools thing in 'admin' and it lists my wireless interface as an ethernet interface, but on my previous wubi 10.04 installation on this computer I think it was listed as a wifi interface. Clutching at straws here!

---

### Post by mistafeesh on 2011-01-14
Thanks. 'Firewall stopped  and disabled on system startup' which is fine with me.
Annoyingly I get the same error though when I try to connect...

Also, it connected fine yesterday for a few hours until I turned everything off for the night... I've also noticed a that the same computer is sporadically unable to find other stuff on the local network such as my web server through the browser and another samba server (running on a mac) even though it's been able to connect to the internet and all other computers on the network can access everything else...

I'm wondering if it could be an error in my network connection set up. I just looked on the network tools thing in 'admin' and it lists my wireless interface as an ethernet interface, but on my previous wubi 10.04 installation on this computer I think it was listed as a wifi interface. 

Clutching at straws here, but I thought it'd be best to offer any information that might be relevant!

---

### Post by mistafeesh on 2011-01-19
any ideas anyone? I'm still stuck with this one!

---

### Post by mistafeesh on 2011-01-19
any ideas anyone? I'm still stuck with this one!

---

### Post by mistafeesh on 2011-01-19
any ideas anyone? I'm still stuck with this one....

---

### Post by Darth_tater on 2011-01-20
I also have this issue. Looking for a fix, but so far there is none.

10.10 64 bit.

---

### Post by lillem4n on 2011-02-09
I also got the same problem. However it is only with one specific host and I can SSH to it from the terminal without any problem.

Ubuntu 10.10 64 bit fully patched.

---

### Post by Darth_tater on 2011-02-09
Yep.  Im in the EXACT SAME situation.

i have deployed 10.10 to *other* boxes and dont have this problem.  Only on this computer.

I was running 10.04.1 LTS and then a dist-upgraded to 10.10

I have googeled ALL OVER the internet for a solution, and there seems to be others with this problem, but they solved it by upgrading their openSSH server OR adding directives in the sshd config file to force it to issue keepalive packets.


Neither of theses solutions have worked for me.

I set the debugging in sshd to as verbose as possible, but was not able to see the problem.

I will try again in the future.

---

### Post by registered2-5-2011 on 2011-02-09
I have had this same issue before on a 8.04 server and the "sudo ufw disable" had fixed it. At the time I had firestarter installed and I guess they were conflicting. I am playing with that box more to see if I can reproduce the error.

---

### Post by Darth_tater on 2011-02-09
I do not have fire starter installed and uwf and iptables are disabled.

---

### Post by registered2-5-2011 on 2011-02-09
[LIST=1]
[*]Have you seen anything in /var/log/messages on either machine?
[/LIST]

---

### Post by lillem4n on 2011-02-10
ok... oddest thing. If I use the IP instead of the DNS name, it works.

---

### Post by Darth_tater on 2011-02-10
Sadly, this is not the case for me!

---

### Post by Darth_tater on 2011-02-12
Here's the details,  i set sshd_conf 's logging to DEBUG3 (the most verbose)


UFW is DISABLED!

its along, but here is what gets logged.

Note the time.

```


Feb 11 21:17:22 HOSTNAME sshd[22425]: Connection from IPADDRESS port 57920
Feb 11 21:17:22 HOSTNAME sshd[22425]: debug1: Client protocol version 2.0; client software version OpenSSH_5.5p1 Debian-4ubuntu5
Feb 11 21:17:22 HOSTNAME sshd[22425]: debug1: match: OpenSSH_5.5p1 Debian-4ubuntu5 pat OpenSSH*
Feb 11 21:17:22 HOSTNAME sshd[22425]: debug1: Enabling compatibility mode for protocol 2.0
Feb 11 21:17:22 HOSTNAME sshd[22425]: debug1: Local version string SSH-2.0-OpenSSH_5.5p1 Debian-4ubuntu5
Feb 11 21:17:22 HOSTNAME sshd[22425]: debug2: fd 3 setting O_NONBLOCK
Feb 11 21:17:22 HOSTNAME sshd[22425]: debug2: Network child is on pid 22426
Feb 11 21:17:22 HOSTNAME sshd[22425]: debug3: preauth child monitor started
Feb 11 21:17:22 HOSTNAME sshd[22425]: debug3: mm_request_receive entering
Feb 11 21:17:22 HOSTNAME sshd[22425]: debug3: monitor_read: checking request 0
Feb 11 21:17:22 HOSTNAME sshd[22425]: debug3: mm_answer_moduli: got parameters: 1024 1024 8192
Feb 11 21:17:22 HOSTNAME sshd[22425]: WARNING: /etc/ssh/moduli does not exist, using fixed modulus
Feb 11 21:17:22 HOSTNAME sshd[22425]: debug3: mm_request_send entering: type 1
Feb 11 21:17:22 HOSTNAME sshd[22425]: debug2: monitor_read: 0 used once, disabling now
Feb 11 21:17:22 HOSTNAME sshd[22425]: debug3: mm_request_receive entering
Feb 11 21:17:22 HOSTNAME sshd[22425]: debug3: monitor_read: checking request 5
Feb 11 21:17:22 HOSTNAME sshd[22425]: debug3: mm_answer_sign
Feb 11 21:17:22 HOSTNAME sshd[22425]: debug3: mm_answer_sign: signature 0x7f18b9505cf0(271)
Feb 11 21:17:22 HOSTNAME sshd[22425]: debug3: mm_request_send entering: type 6
Feb 11 21:17:22 HOSTNAME sshd[22425]: debug2: monitor_read: 5 used once, disabling now
Feb 11 21:17:22 HOSTNAME sshd[22425]: debug3: mm_request_receive entering
Feb 11 21:17:25 HOSTNAME sshd[22425]: debug3: monitor_read: checking request 7
Feb 11 21:17:25 HOSTNAME sshd[22425]: debug3: mm_answer_pwnamallow
Feb 11 21:17:25 HOSTNAME sshd[22425]: debug3: Trying to reverse map address IPADDRESS.
Feb 11 21:17:25 HOSTNAME sshd[22425]: debug2: parse_server_config: config reprocess config len 649
Feb 11 21:17:25 HOSTNAME sshd[22425]: debug3: mm_answer_pwnamallow: sending MONITOR_ANS_PWNAM: 1
Feb 11 21:17:25 HOSTNAME sshd[22425]: debug3: mm_request_send entering: type 8
Feb 11 21:17:25 HOSTNAME sshd[22425]: debug2: monitor_read: 7 used once, disabling now
Feb 11 21:17:25 HOSTNAME sshd[22425]: debug3: mm_request_receive entering
Feb 11 21:17:25 HOSTNAME sshd[22425]: debug3: monitor_read: checking request 50
Feb 11 21:17:25 HOSTNAME sshd[22425]: debug1: PAM: initializing for "USERNAME"
Feb 11 21:17:25 HOSTNAME sshd[22425]: debug1: PAM: setting PAM_RHOST to "HOSTNAME"
Feb 11 21:17:25 HOSTNAME sshd[22425]: debug1: PAM: setting PAM_TTY to "ssh"
Feb 11 21:17:25 HOSTNAME sshd[22425]: debug2: monitor_read: 50 used once, disabling now
Feb 11 21:17:25 HOSTNAME sshd[22425]: debug3: mm_request_receive entering
Feb 11 21:17:25 HOSTNAME sshd[22425]: debug3: monitor_read: checking request 3
Feb 11 21:17:25 HOSTNAME sshd[22425]: debug3: mm_answer_authserv: service=ssh-connection, style=, role=
Feb 11 21:17:25 HOSTNAME sshd[22425]: debug2: monitor_read: 3 used once, disabling now
Feb 11 21:17:25 HOSTNAME sshd[22425]: debug3: mm_request_receive entering
Feb 11 21:17:25 HOSTNAME sshd[22425]: debug3: monitor_read: checking request 11
Feb 11 21:17:25 HOSTNAME sshd[22425]: debug3: mm_answer_authpassword: sending result 0
Feb 11 21:17:25 HOSTNAME sshd[22425]: debug3: mm_request_send entering: type 12
Feb 11 21:17:25 HOSTNAME sshd[22425]: Failed none for USERNAME from IPADDRESS port 57920 ssh2
Feb 11 21:17:25 HOSTNAME sshd[22425]: debug3: mm_request_receive entering
Feb 11 21:17:32 HOSTNAME sshd[22170]: debug3: fd 5 is not O_NONBLOCK
Feb 11 21:17:32 HOSTNAME sshd[22170]: debug1: Forked child 22431.
Feb 11 21:17:32 HOSTNAME sshd[22170]: debug3: send_rexec_state: entering fd = 9 config len 649
Feb 11 21:17:32 HOSTNAME sshd[22170]: debug3: ssh_msg_send: type 0
Feb 11 21:17:32 HOSTNAME sshd[22170]: debug3: send_rexec_state: done
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: oom_adjust_restore
Feb 11 21:17:32 HOSTNAME sshd[22431]: Set /proc/self/oom_adj to 0
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug1: rexec start in 5 out 5 newsock 5 pipe 8 sock 9
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug1: inetd sockets after dupping: 3, 3
Feb 11 21:17:32 HOSTNAME sshd[22431]: Connection from IPADDRESS port 57922
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug1: Client protocol version 2.0; client software version OpenSSH_5.5p1 Debian-4ubuntu5
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug1: match: OpenSSH_5.5p1 Debian-4ubuntu5 pat OpenSSH*
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug1: Enabling compatibility mode for protocol 2.0
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug1: Local version string SSH-2.0-OpenSSH_5.5p1 Debian-4ubuntu5
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug2: fd 3 setting O_NONBLOCK
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug2: Network child is on pid 22432
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: preauth child monitor started
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_request_receive entering
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: monitor_read: checking request 0
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_answer_moduli: got parameters: 1024 1024 8192
Feb 11 21:17:32 HOSTNAME sshd[22431]: WARNING: /etc/ssh/moduli does not exist, using fixed modulus
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_request_send entering: type 1
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug2: monitor_read: 0 used once, disabling now
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_request_receive entering
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: monitor_read: checking request 5
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_answer_sign
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_answer_sign: signature 0x7f5f1bab3cf0(271)
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_request_send entering: type 6
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug2: monitor_read: 5 used once, disabling now
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_request_receive entering
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: monitor_read: checking request 7
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_answer_pwnamallow
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: Trying to reverse map address IPADDRESS.
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug2: parse_server_config: config reprocess config len 649
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_answer_pwnamallow: sending MONITOR_ANS_PWNAM: 1
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_request_send entering: type 8
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug2: monitor_read: 7 used once, disabling now
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_request_receive entering
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: monitor_read: checking request 50
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug1: PAM: initializing for "USERNAME"
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug1: PAM: setting PAM_RHOST to "HOSTNAME"
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug1: PAM: setting PAM_TTY to "ssh"
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug2: monitor_read: 50 used once, disabling now
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_request_receive entering
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: monitor_read: checking request 3
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_answer_authserv: service=ssh-connection, style=, role=
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug2: monitor_read: 3 used once, disabling now
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_request_receive entering
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: monitor_read: checking request 11
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_answer_authpassword: sending result 0
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_request_send entering: type 12
Feb 11 21:17:32 HOSTNAME sshd[22431]: Failed none for USERNAME from IPADDRESS port 57922 ssh2
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_request_receive entering
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: monitor_read: checking request 11
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: PAM: sshpam_passwd_conv called with 1 messages
Feb 11 21:17:32 HOSTNAME sshd[22431]: pam_sm_authenticate: Called
Feb 11 21:17:32 HOSTNAME sshd[22431]: pam_sm_authenticate: username = [USERNAME]
Feb 11 21:17:32 HOSTNAME sshd[22431]: pam_sm_authenticate: /home/USERNAME is already mounted
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug1: PAM: password authentication accepted for USERNAME
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_answer_authpassword: sending result 1
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_request_send entering: type 12
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_request_receive_expect entering: type 51
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_request_receive entering
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug1: do_pam_account: called
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: PAM: do_pam_account pam_acct_mgmt = 0 (Success)
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_request_send entering: type 52
Feb 11 21:17:32 HOSTNAME sshd[22431]: Accepted password for USERNAME from IPADDRESS port 57922 ssh2
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug1: monitor_child_preauth: USERNAME has been authenticated by privileged process
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_get_keystate: Waiting for new keys
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_request_receive_expect entering: type 25
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_request_receive entering
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_newkeys_from_blob: 0x7f5f1bace430(122)
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug2: mac_setup: found hmac-md5
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_get_keystate: Waiting for second key
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_newkeys_from_blob: 0x7f5f1bb78730(122)
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug2: mac_setup: found hmac-md5
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_get_keystate: Getting compression state
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_get_keystate: Getting Network I/O buffers
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_share_sync: Share sync
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: mm_share_sync: Share sync end
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug1: PAM: establishing credentials
Feb 11 21:17:32 HOSTNAME sshd[22431]: debug3: PAM: opening session
Feb 11 21:17:32 HOSTNAME sshd[22431]: pam_unix(sshd:session): session opened for user USERNAME by (uid=0)
Feb 11 21:17:33 HOSTNAME sshd[22431]: debug3: PAM: sshpam_store_conv called with 1 messages
Feb 11 21:17:33 HOSTNAME sshd[22431]: User child is on pid 22536
Feb 11 21:17:33 HOSTNAME sshd[22431]: debug3: mm_request_receive entering
Feb 11 21:17:33 HOSTNAME sshd[22536]: debug1: SELinux support disabled
Feb 11 21:17:33 HOSTNAME sshd[22536]: debug1: PAM: establishing credentials
Feb 11 21:17:33 HOSTNAME sshd[22536]: debug1: permanently_set_uid: 1000/1000
Feb 11 21:17:33 HOSTNAME sshd[22536]: debug2: set_newkeys: mode 0
Feb 11 21:17:33 HOSTNAME sshd[22536]: debug2: set_newkeys: mode 1
Feb 11 21:17:33 HOSTNAME sshd[22536]: debug1: Entering interactive session for SSH2.
Feb 11 21:17:33 HOSTNAME sshd[22536]: debug2: fd 13 setting O_NONBLOCK
Feb 11 21:17:33 HOSTNAME sshd[22536]: debug2: fd 14 setting O_NONBLOCK
Feb 11 21:17:33 HOSTNAME sshd[22536]: debug1: server_init_dispatch_20
Feb 11 21:17:33 HOSTNAME sshd[22536]: debug1: server_input_channel_open: ctype session rchan 0 win 2097152 max 32768
Feb 11 21:17:33 HOSTNAME sshd[22536]: debug1: input_session_request
Feb 11 21:17:33 HOSTNAME sshd[22536]: debug1: channel 0: new [server-session]
Feb 11 21:17:33 HOSTNAME sshd[22536]: debug2: session_new: allocate (allocated 0 max 10)
Feb 11 21:17:33 HOSTNAME sshd[22536]: debug3: session_unused: session id 0 unused
Feb 11 21:17:33 HOSTNAME sshd[22536]: debug1: session_new: session 0
Feb 11 21:17:33 HOSTNAME sshd[22536]: debug1: session_open: channel 0
Feb 11 21:17:33 HOSTNAME sshd[22536]: debug1: session_open: session 0: link with channel 0
Feb 11 21:17:33 HOSTNAME sshd[22536]: debug1: server_input_channel_open: confirm session
Feb 11 21:17:33 HOSTNAME sshd[22536]: debug1: server_input_global_request: rtype no-more-sessions@openssh.com want_reply 0
Feb 11 21:17:33 HOSTNAME sshd[22536]: debug1: server_input_channel_req: channel 0 request subsystem reply 1
Feb 11 21:17:33 HOSTNAME sshd[22536]: debug1: session_by_channel: session 0 channel 0
Feb 11 21:17:33 HOSTNAME sshd[22536]: debug1: session_input_channel_req: session 0 req subsystem
Feb 11 21:17:33 HOSTNAME sshd[22536]: subsystem request for sftp
Feb 11 21:17:33 HOSTNAME sshd[22536]: debug1: subsystem: exec() /usr/lib/openssh/sftp-server
Feb 11 21:17:33 HOSTNAME sshd[22536]: debug2: fd 3 setting TCP_NODELAY
Feb 11 21:17:33 HOSTNAME sshd[22536]: debug2: fd 17 setting O_NONBLOCK
Feb 11 21:17:33 HOSTNAME sshd[22536]: debug2: fd 16 setting O_NONBLOCK
Feb 11 21:17:33 HOSTNAME sshd[22537]: debug3: Copy environment: PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
Feb 11 21:17:33 HOSTNAME sshd[22537]: debug3: Copy environment: LANG=en_US.UTF-8
Feb 11 21:17:33 HOSTNAME sshd[22537]: debug3: Copy environment: XDG_SESSION_COOKIE=5065b9877fc57e0bac53767200000011-1297487852.810518-1566051967
Feb 11 21:17:33 HOSTNAME sshd[22537]: debug3: channel 0: close_fds r -1 w -1 e -1



```


and it will just hang at this point for about 10-15 min until gnome comes back saying that it could not connect (dbus error)

---

### Post by Darth_tater on 2011-02-12
Also, it seems that i can not kill ssh server.

```

                                                              [ OK ] 
root@HOSTNAME:/var/log# /etc/init.d/ssh stop
 * Stopping OpenBSD Secure Shell server sshd                                                                                                                                                                                            [ OK ] 
root@HOSTNAME:/var/log# /etc/init.d/ssh status
 * sshd is running




```

---

