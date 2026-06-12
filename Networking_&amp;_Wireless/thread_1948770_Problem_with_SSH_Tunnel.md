---
title: "Problem with SSH Tunnel"
date: 2012-03-28
forum: Networking &amp; Wireless
---

### Post by targilnar on 2012-03-28
I am running Ubuntu Server 11.10. Any help would be appreciated.

I am able to connect via SSH and can administer the computer via command line without any problems. The problem comes when I try to use an SSH tunnel (in my case for VNC or Webmin access).

From /var/log/auth.log
Mar 28 20:46:49 SHODAN sshd[1889]: error: connect_to 127.0.0.1 port 1000: failed.


Using CYGWIN is appears that the TCP connection is being refused on the remote machine
ssh -vvv -p 22 -L 1001:127.0.0.1:1000 XXXX@SHODAN

OpenSSH_5.8p1, OpenSSL 0.9.8r 8 Feb 2011
debug2: ssh_connect: needpriv 0
debug1: Connecting to SHODAN [192.168.1.66] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /home/XXXXX/.ssh/id_rsa type -1
debug1: identity file /home/XXXXX/.ssh/id_rsa-cert type -1
debug1: identity file /home/XXXXX/.ssh/id_dsa type -1
debug1: identity file /home/XXXXX/.ssh/id_dsa-cert type -1
debug1: identity file /home/XXXXX/.ssh/id_ecdsa type -1
debug1: identity file /home/XXXXX/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.8p1 Debian-7ubuntu1
debug1: match: OpenSSH_5.8p1 Debian-7ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.8
debug2: fd 3 setting O_NONBLOCK
debug3: put_host_port: [shodan]:22
debug3: load_hostkeys: loading entries for host "[shodan]:22" from file "/home/XXXXX/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/XXXXX/.ssh/known_hosts:5
debug3: load_hostkeys: loaded 1 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: [email]ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com[/email],ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: [email]ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com[/email],ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss,ecdsa-sha2-nistp256
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-ctr hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA 9b:2b:15:d0:02:8a:37:09:ad:89:aa:78:6b:a2:cd:32
debug3: put_host_port: [192.168.1.66]:22
debug3: put_host_port: [shodan]:22
debug3: load_hostkeys: loading entries for host "[shodan]:22" from file "/home/XXXXX/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/XXXXX/.ssh/known_hosts:5
debug3: load_hostkeys: loaded 1 keys
debug3: load_hostkeys: loading entries for host "[192.168.1.66]:22" from file "/home/XXXXX/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/XXXXX/.ssh/known_hosts:5
debug3: load_hostkeys: loaded 1 keys
debug1: Host '[shodan]:22' is known and matches the ECDSA host key.
debug1: Found key in /home/XXXXX/.ssh/known_hosts:5
debug1: ssh_ecdsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/XXXXX/.ssh/id_rsa (0x0)
debug2: key: /home/XXXXX/.ssh/id_dsa (0x0)
debug2: key: /home/XXXXX/.ssh/id_ecdsa (0x0)
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/XXXXX/.ssh/id_rsa
debug3: no such identity: /home/XXXXX/.ssh/id_rsa
debug1: Trying private key: /home/XXXXX/.ssh/id_dsa
debug3: no such identity: /home/XXXXX/.ssh/id_dsa
debug1: Trying private key: /home/XXXXX/.ssh/id_ecdsa
debug3: no such identity: /home/XXXXX/.ssh/id_ecdsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
XXXXX@shodan's password:
debug3: packet_send2: adding 48 (len 64 padlen 16 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
Authenticated to SHODAN ([192.168.1.66]:22).
debug1: Local connections to LOCALHOST:1001 forwarded to remote address 127.0.0.1:1000
debug3: channel_setup_fwd_listener: type 2 wildcard 0 addr NULL
debug3: sock_set_v6only: set socket 4 IPV6_V6ONLY
debug1: Local forwarding listening on ::1 port 1001.
debug2: fd 4 setting O_NONBLOCK
debug3: fd 4 is O_NONBLOCK
debug1: channel 0: new [port listener]
debug1: Local forwarding listening on 127.0.0.1 port 1001.
debug2: fd 5 setting O_NONBLOCK
debug3: fd 5 is O_NONBLOCK
debug1: channel 1: new [port listener]
debug1: channel 2: new [client-session]
debug3: ssh_session2_open: channel_new: 2
debug2: channel 2: send open
debug1: Requesting [EMAIL="no-more-sessions@openssh.com"]no-more-sessions@openssh.com[/EMAIL]
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 2
debug2: fd 3 setting TCP_NODELAY
debug3: packet_set_tos: set IP_TOS 0x10
debug2: channel 2: request pty-req confirm 1
debug2: channel 2: request shell confirm 1
debug2: callback done
debug2: channel 2: open confirm rwindow 0 rmax 32768
debug2: channel_input_status_confirm: type 99 id 2
debug2: PTY allocation request accepted on channel 2
debug2: channel 2: rcvd adjust 2097152
debug2: channel_input_status_confirm: type 99 id 2
debug2: shell request accepted on channel 2
Welcome to Ubuntu 11.10 (GNU/Linux 3.0.0-17-server x86_64)

 * Documentation:  [https://help.ubuntu.com/11.10/serverguide/C](https://help.ubuntu.com/11.10/serverguide/C)

  System information as of Wed Mar 28 20:29:17 EDT 2012

  System load:  0.08              Processes:            110
  Usage of /:   5.8% of 43.87GB   Users logged in:      1
  Memory usage: 37%               IP address for wlan0: 192.168.1.66
  Swap usage:   0%

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

0 packages can be updated.
0 updates are security updates.

Last login: Wed Mar 28 20:28:31 2012 from 192.168.1.42
XXXXX@SHODAN:~$ debug1: Connection to port 1001 forwarding to 127.0.0.1 port 1000 requested.
debug2: fd 9 setting TCP_NODELAY
debug3: fd 9 is O_NONBLOCK
debug3: fd 9 is O_NONBLOCK
debug1: channel 3: new [direct-tcpip]
channel 3: open failed: connect failed: Connection refused
debug2: channel 3: zombie
debug2: channel 3: garbage collecting
debug1: channel 3: free: direct-tcpip: listening port 1001 for 127.0.0.1 port 1000, connect from 127.0.0.1 port 55539, nchannels 4
debug3: channel 3: status: The following connections are open:
  #2 client-session (t4 r0 i0/0 o0/0 fd 6/7 cc -1)

---

### Post by targilnar on 2012-03-28
Solved. Missing a digit on the port. Should have been 10000 instead of 1000

---

