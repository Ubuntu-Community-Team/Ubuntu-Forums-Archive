---
title: "Slow SSH authentication times"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by manolo123 on 2010-10-25
Hi guys,

I know that this problem has already been discussed a few times in the past, but none of the solutions work for me. I a have a 8-core Xeon server, running Ubuntu Server 10.04 LTS. It is also the host of 5 Ubuntu Server virtual machines (8.04 and 10.04).

The problem is, when I ssh into the main server itself, the authentication takes around 5 to 10 seconds, but in case of logging into VMs it all works fine.

Here is the log from executing the command "time ssh -vvv xxx@localhost true". I marked the place where the biggest hang occurs, it is after the password is provided:


```
OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to localhost [::1] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/identity type -1
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu4
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug3: Wrote 792 bytes for a total of 831
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: 

diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-gro

up1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: 

aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-

cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: 

aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-

cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: 

hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: 

hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: 

diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-gro

up1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: 

aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-

cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: 

aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-

cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: 

hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: 

hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
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
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug3: Wrote 24 bytes for a total of 855
debug2: dh_gen_key: priv key bits set: 134/256
debug2: bits set: 525/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: Wrote 144 bytes for a total of 999
debug3: check_host_in_hostfile: filename /root/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 18
debug1: Host 'localhost' is known and matches the RSA host key.
debug1: Found key in /root/.ssh/known_hosts:18
debug2: bits set: 507/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug3: Wrote 16 bytes for a total of 1015
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug3: Wrote 48 bytes for a total of 1063
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /root/.ssh/identity ((nil))
debug2: key: /root/.ssh/id_rsa ((nil))
debug2: key: /root/.ssh/id_dsa ((nil))
debug3: Wrote 64 bytes for a total of 1127
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /root/.ssh/identity
debug3: no such identity: /root/.ssh/identity
debug1: Trying private key: /root/.ssh/id_rsa
debug3: no such identity: /root/.ssh/id_rsa
debug1: Trying private key: /root/.ssh/id_dsa
debug3: no such identity: /root/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
debug3: packet_send2: adding 64 (len 57 padlen 7 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug3: Wrote 144 bytes for a total of 1271
debug1: Authentication succeeded (password).
debug2: fd 6 setting O_NONBLOCK
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug3: Wrote 128 bytes for a total of 1399
debug2: callback start
debug2: client_session2_setup: id 0
debug1: Sending command: true
debug2: channel 0: request exec confirm 1
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug3: Wrote 48 bytes for a total of 1447

-------------------- Big hang ---------------------------------

debug2: channel 0: rcvd adjust 2097152
debug2: channel_input_status_confirm: type 99 id 0
debug2: exec request accepted on channel 0
debug2: channel 0: rcvd eof
debug2: channel 0: output open -> drain
debug2: channel 0: obuf empty
debug2: channel 0: close_write
debug2: channel 0: output drain -> closed
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: client_input_channel_req: channel 0 rtype eow@openssh.com reply 0
debug2: channel 0: rcvd eow
debug2: channel 0: close_read
debug2: channel 0: input open -> closed
debug2: channel 0: rcvd close
debug3: channel 0: will not send data after close
debug2: channel 0: almost dead
debug2: channel 0: gc: notify user
debug2: channel 0: gc: user detached
debug2: channel 0: send close
debug2: channel 0: is dead
debug2: channel 0: garbage collecting
debug1: channel 0: free: client-session, nchannels 1
debug3: channel 0: status: The following connections are open:
  #0 client-session (t4 r0 i3/0 o3/0 fd -1/-1 cfd -1)

debug3: channel 0: close_fds r -1 w -1 e 6 c -1
debug3: Wrote 32 bytes for a total of 1479
debug3: Wrote 64 bytes for a total of 1543
debug1: fd 2 clearing O_NONBLOCK
Transferred: sent 1376, received 1960 bytes, in 0.5 seconds
Bytes per second: sent 2715.9, received 3868.5
debug1: Exit status 0


```Also, smaller hangs occur after other "Wrote XX bytes" statements. As I said, logging into VMs is OK, which is quite strange for me. Do you guys have any ideas?

Regards,
Manolo

---

### Post by yesrno on 2010-10-25
Hmm well I once had this kind of problem and the cause was DNS. So you could try adding the ip and hostname of the server in /etc/hosts and try again.

---

### Post by manolo123 on 2010-10-25
As I said, I tried everything I could find about his issue, including DNS, MOTD and disabling some authentication methods, with no effect. I think this might be some kind of IO problem, but I am not sure how to proceed wit it.

---

### Post by SeijiSensei on 2010-10-25
The number one reason for slow SSH logins is problems with DNS resolution on either end.  Make sure that *forward and reverse resolution* are established for both server and client, or use compatible entries for both machines in their /etc/hosts.  

You can disable DNS checking in /etc/ssh/sshd_config and /etc/ssh/ssh_config.

---

### Post by socci79 on 2010-11-17
Hi,
i have had the same problem.
Please have a look if avahi-daemon is running and try to stop it if you dont need it.

Regards,
Volker

---

