---
title: "SSH connection problem (Ubuntu12.10)"
date: 2013-04-18
forum: Networking &amp; Wireless
---

### Post by Wolfbator on 2013-04-18
Hi everybody !

First of all, I AM FRENCH, so please, dont take care of my spelling and and my grammary :)

I'm gonna try to explain what's my problem. Im in an internship and my job is to create a local network with 8 computers all with ubuntu 12.10.

The aim is to be able to "parallelise" a R algorithm betwen these 8 machines. That means , my algorithm take a loooooot of time to be done by one computer. And that's why i want to divide the job between my 8 computers. 

I've already succeeded , it works. But one of my mchines is very big (32cores => 8000dollars) and i want her to be the "master". OK I call "master" the machine who got the R program, who creates SSH connection to the 7 others "slaves" machines and allocates job between the 7 slaves. 

When i succeeded with a normal machine as master (a basic 8 cores computer) i could see in every slave (using this command line in thier proper shell :
 ```
 tail -f /var/log/auth.log 
```
every connections that the master did with the slave. 

With my software who launch the R algorithm, it opens one connection SSH with the slave for each core it has. So it opened 8 SSH connections for a 8 cores slave and 32 SSH connections for a 32cores slave. 
And when my algorithm is done, there is a function in my algorithm that stops the "cluster" of 8 machines and send for slaves 8 "disconnect SSH messages" (or 32 "disconnect SSH messages" for the big computer). I don't if it's normal, but it works. 

But when i want to use my big machine as master, the first slave encountered receives only one "open SSH connection message" directly followed by a "disconnect SSH message". That completely blocks my software in the begginning and my algorithm cant be launched.

PLEASE i have bean stuck on this problem for 4 days now...

Thanks for your reading and answers

---

### Post by Wolfbator on 2013-04-18
Up !

---

### Post by QIII on 2013-04-18
Hello!

Please do not bump a thread so quickly.

Remember that this is a world-wide community of volunteers who spend our time here as we have time to spend.  It may be that the person with the best answer lives in Seoul or Kolkata or Buenos Aires or Honolulu.  At any time, users may be sleeping, at work, playing with their children, eating meals, spending time with their spouses, or simply taking a break from the Forum.

Please allow your post to make a 24 hour trip around the world first.  If you get no response, it might be OK to bump it again at 12 hours to see if you catch users in different time zones.

Thanks,

QIII

---

### Post by steeldriver on 2013-04-18
Take your custom software out of the equation first - what happens when you try to initiate a simple ssh connection at the terminal from your big machine ("master") to the first slave? You can use the -vvv switch to get detailed information about the connection / authentication sequence e.g.

```
ssh -vvv user@xxx.xxx.xxx.xxx
```

---

### Post by Wolfbator on 2013-04-18
Ok QIII , sry its my first time in this forum ! :)
Thanks steeldriver , im gonna try it tomorrow morning because I dont have the machines in front of me now. Ill post what I'll obtain ;)

---

### Post by Wolfbator on 2013-04-19
Hello people ! 

When i used the following command line in my Master shell :

```
ssh -vvv user@slave_name 
```

I got the following answer :

```

jm@mega:~$ ssh -vvv jm@mini

OpenSSH_6.0p1 Debian-3ubuntu1, OpenSSL 1.0.1c 10 May 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to mini [192.168.10.6] port 22.
debug1: Connection established.
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/jm/.ssh/id_rsa" as a RSA1 public key
debug1: identity file /home/jm/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/jm/.ssh/id_rsa-cert type -1
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/jm/.ssh/id_dsa" as a RSA1 public key
debug1: identity file /home/jm/.ssh/id_dsa type 2
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: identity file /home/jm/.ssh/id_dsa-cert type -1
debug1: identity file /home/jm/.ssh/id_ecdsa type -1
debug1: identity file /home/jm/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.0p1 Debian-3ubuntu1
debug1: match: OpenSSH_6.0p1 Debian-3ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.0p1 Debian-3ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug3: load_hostkeys: loading entries for host "mini" from file "/home/jm/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/jm/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com,ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
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
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
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
debug1: Server host key: ECDSA 23:e0:1e:cf:ed:d5:47:3e:1f:0c:70:3c:5d:fd:b1:21
debug3: load_hostkeys: loading entries for host "mini" from file "/home/jm/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/jm/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug3: load_hostkeys: loading entries for host "192.168.10.6" from file "/home/jm/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/jm/.ssh/known_hosts:2
debug3: load_hostkeys: loaded 1 keys
debug1: Host 'mini' is known and matches the ECDSA host key.
debug1: Found key in /home/jm/.ssh/known_hosts:1
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
debug2: key: /home/jm/.ssh/id_dsa (0x7f857d6f24f0)
debug2: key: /home/jm/.ssh/id_rsa (0x7f857d6f24b0)
debug2: key: /home/jm/.ssh/id_ecdsa ((nil))
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug3: start over, passed a different list publickey,password,keyboard-interactive
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering DSA public key: /home/jm/.ssh/id_dsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Offering RSA public key: /home/jm/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Server accepts key: pkalg ssh-rsa blen 279
debug2: input_userauth_pk_ok: fp 83:1c:e8:0f:60:16:cf:03:e5:35:a4:aa:d3:46:10:a0
debug3: sign_and_send_pubkey: RSA 83:1c:e8:0f:60:16:cf:03:e5:35:a4:aa:d3:46:10:a0
debug1: Authentication succeeded (publickey).
Authenticated to mini ([192.168.10.6]:22).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: fd 3 setting TCP_NODELAY
debug3: packet_set_tos: set IP_TOS 0x10
debug2: channel 0: request pty-req confirm 1
debug1: Sending environment.
debug3: Ignored env SSH_AGENT_PID
debug3: Ignored env GPG_AGENT_INFO
debug3: Ignored env TERM
debug3: Ignored env SHELL
debug3: Ignored env XDG_SESSION_COOKIE
debug3: Ignored env WINDOWID
debug3: Ignored env GNOME_KEYRING_CONTROL
debug3: Ignored env GTK_MODULES
debug3: Ignored env USER
debug3: Ignored env LS_COLORS
debug3: Ignored env XDG_SESSION_PATH
debug3: Ignored env XDG_SEAT_PATH
debug3: Ignored env SSH_AUTH_SOCK
debug3: Ignored env SESSION_MANAGER
debug3: Ignored env DEFAULTS_PATH
debug3: Ignored env XDG_CONFIG_DIRS
debug3: Ignored env PATH
debug3: Ignored env DESKTOP_SESSION
debug3: Ignored env PWD
debug1: Sending env LANG = fr_FR.UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env MANDATORY_PATH
debug3: Ignored env UBUNTU_MENUPROXY
debug3: Ignored env COMPIZ_CONFIG_PROFILE
debug3: Ignored env GDMSESSION
debug3: Ignored env SHLVL
debug3: Ignored env HOME
debug3: Ignored env GNOME_DESKTOP_SESSION_ID
debug3: Ignored env LOGNAME
debug3: Ignored env COMPIZ_BIN_PATH
debug3: Ignored env XDG_DATA_DIRS
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS
debug3: Ignored env LESSOPEN
debug3: Ignored env XDG_RUNTIME_DIR
debug3: Ignored env DISPLAY
debug3: Ignored env XDG_CURRENT_DESKTOP
debug3: Ignored env LESSCLOSE
debug3: Ignored env COLORTERM
debug3: Ignored env XAUTHORITY
debug3: Ignored env _
debug3: Ignored env OLDPWD
debug2: channel 0: request shell confirm 1
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel_input_status_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 2097152
debug2: channel_input_status_confirm: type 99 id 0
debug2: shell request accepted on channel 0
Welcome to Ubuntu 12.10 (GNU/Linux 3.5.0-26-generic x86_64)


 * Documentation:  https://help.ubuntu.com/


4 packages can be updated.
4 updates are security updates.


Last login: Fri Apr 19 09:39:00 2013 from mega


jm@mini:~$ exit
dÃ©connexion
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: client_input_channel_req: channel 0 rtype eow@openssh.com reply 0
debug2: channel 0: rcvd eow
debug2: channel 0: close_read
debug2: channel 0: input open -> closed
debug2: channel 0: rcvd eof
debug2: channel 0: output open -> drain
debug2: channel 0: obuf empty
debug2: channel 0: close_write
debug2: channel 0: output drain -> closed
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
  #0 client-session (t4 r0 i3/0 o3/0 fd -1/-1 cc -1)


Connection to mini closed.
Transferred: sent 3640, received 2480 bytes, in 51.8 seconds
Bytes per second: sent 70.3, received 47.9
debug1: Exit status 0



```

You can see that I disconnected the master from the slave by myself to see the result.

I hope there is an explanation ! :)

---

### Post by steeldriver on 2013-04-19
OK so there seems to be no problem with the basic SSH connection / authentication - have you checked /var/log/auth.log on the slave machine to see if there are any clues there?

Maybe the problem is related to opening multiple sessions? In some circumstances a host may think that's malicious and block / drop the connection I think

---

### Post by Wolfbator on 2013-04-19
Yeah i've already checked the /var/log/auth.log and it is on this file I could see that my ig 32 cores master machine only send 1 connection and one disconnection 1 sec after... :/
Some people in other form said that the problem could comes from the Iptables file, bad configured... I don't know

---

