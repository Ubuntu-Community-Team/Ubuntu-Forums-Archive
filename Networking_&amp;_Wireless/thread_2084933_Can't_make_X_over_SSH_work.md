---
title: "Can't make X over SSH work"
date: 2012-11-16
forum: Networking &amp; Wireless
---

### Post by mullba on 2012-11-16
I have a server set up and I would like to be able to log into the server remotely (it's on the same network as my desktop) and run a program with the output displayed on my desktop.  I keep reading it's possible, but every tutorial I find I end up running whatever program on the server (displaying on the server) with no display on the desktop.

I'm absolutely lost and frustrated.

---

### Post by mullba on 2012-11-17
Still working on it...

So far it doesn't matter if I use SSH or PuTTY, the DISPLAY variable on the server never gets set.  Even if I set it manually, it doesn't seem to have any effect.  I've tried setting it to :0.0, the desktop IP, and the server IP, but it doesn't seem to do anything.  Any ideas?

---

### Post by Lars Noodén on 2012-11-17
Are you using the -X option in ssh when connecting to the server?

```

ssh -X mullba@server.example.org

```

Does the machine you are connecting from have a running X server?  It is built into systems like OS X and Linux.  But if you are connecting from a legacy system the X server may be missing and would have to be added manually.  Xming is one option there.

---

### Post by mullba on 2012-11-17
Thanks for the response. 

Tried connecting with both -X and -Y.  Both computers have everything X installed.  My desktop has Ubuntu 10.04 LTS installed and the server is Ubuntu 12.04.  Both have X server, Xauth, etc. installed.  Both have the SSHD_Config forwarding stuff enabled too.

---

### Post by Lars Noodén on 2012-11-17
[sshd_config](http://manpages.ubuntu.com/manpages/precise/en/man5/sshd_config.5.html) should have the following.  

```

X11Forwarding yes
X11DisplayOffset 10

```

The only way I can get an error is if I turn off X11Forwarding.  

Exactly what is the error message that you get when you try to run a graphical program?

---

### Post by mullba on 2012-11-17
> **Lars Noodén said:**
> [sshd_config]("http://manpages.ubuntu.com/manpages/precise/en/man5/sshd_config.5.html") should have the following.  

```

X11Forwarding yes
X11DisplayOffset 10

```The only way I can get an error is if I turn off X11Forwarding.  

Exactly what is the error message that you get when you try to run a graphical program?

I have both of those set on both computers.  The thing is there is no errors, it just displays the program on the server while the desktop waits with a blinking cursor.

-Edit:  It does the blinking cursor thing after I manually set the display variable.  Otherwise I get the "Can't open display" error.

---

### Post by Lars Noodén on 2012-11-17
On the machine that you log into, what is the value of $DISPLAY?

```

echo $DISPLAY

```

---

### Post by mullba on 2012-11-17
> **Lars Noodén said:**
> On the machine that you log into, what is the value of $DISPLAY?

```

echo $DISPLAY

```


Blank

---

### Post by koenn on 2012-11-17
you're starting those programs on the **client**, right ?

---

### Post by mullba on 2012-11-17
> **koenn said:**
> you're starting those programs on the **client**, right ?

Uh...  Probably not?  I do it while logged into the server.  How would I run the program from the server on the client?  

lol...  I'm very new to this stuff.  All I know comes from googled tutorials.

---

### Post by Lars Noodén on 2012-11-17
Well, something is not right.  DISPLAY should not be blank on the remote host if you have connected with -X.  The default with X11 forwarding is localhost:10.0.  What happens when you try setting it manually on the remote host and then try running a graphical program?

```

export DISPLAY=localhost:10.0

```

---

### Post by mullba on 2012-11-17
> **Lars Noodén said:**
> Well, something is not right.  DISPLAY should not be blank on the remote host if you have connected with -X.  The default with X11 forwarding is localhost:10.0.  What happens when you try setting it manually on the remote host and then try running a graphical program?

```

export DISPLAY=localhost:10.0

```

That gives the error "Can't open display: localhost:10.0"

---

### Post by koenn on 2012-11-17
> **mullba said:**
> I do it while logged into the server.  How would I run the program from the server on the client?  

hm, maybe my question wasn't clear :

you do something like this **all** in a terminal **on the desktop pc** :
```

me@desktop:~$  ssh -X me@server
password: 

me@server:~$ firefox

```

right ? 


-----
sorry to butt in, Lars. Just checking the obvious.

---

### Post by mullba on 2012-11-17
> **koenn said:**
> hm, maybe my question wasn't clear :

you do something like this **all** in a terminal **on the desktop pc** :
```

me@desktop:~$  ssh -X me@server
password: 

me@server:~$ firefox

```right ? 


-----
sorry to butt in, Lars. Just checking the obvious.


Yep, exactly what I'm doing.

---

### Post by Lars Noodén on 2012-11-17
> **mullba said:**
> That gives the error "Can't open display: localhost:10.0"

Ok.  That seems to confirm that X is not getting forwarded.  I don't suppose that you have any special firewall changes affecting the interface **lo**, do you?

---

### Post by Lars Noodén on 2012-11-17
I wonder if any clue can be had by running the client in more verbose mode?

```

ssh -X -vv server.example.org

```

---

### Post by Lars Noodén on 2012-11-17
Did you disable IPv6 in any way?   There is one case which sound similar which was caused by turning off IPv6.  The work-around was here:
[http://www.linuxquestions.org/questions/linux-networking-3/x-forwarding-though-ssh-not-working-%24display-not-set-879365/#post4349612](http://www.linuxquestions.org/questions/linux-networking-3/x-forwarding-though-ssh-not-working-%24display-not-set-879365/#post4349612)

---

### Post by mullba on 2012-11-17
I did disable IPv6 on the server.  I tried both solutions from the link above and nothing changed.  

Here's the result of connecting with -vv

> brian@brian-desktop:~$ ssh -X -vv brian@192.168.1.71
OpenSSH_5.3p1 Debian-3ubuntu7, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.71 [192.168.1.71] port 22.
debug1: Connection established.
debug1: identity file /home/brian/.ssh/identity type -1
debug1: identity file /home/brian/.ssh/id_rsa type -1
debug1: identity file /home/brian/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.9p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.9p1 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu7
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
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
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 136/256
debug2: bits set: 516/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '192.168.1.71' is known and matches the RSA host key.
debug1: Found key in /home/brian/.ssh/known_hosts:1
debug2: bits set: 525/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/brian/.ssh/identity ((nil))
debug2: key: /home/brian/.ssh/id_rsa ((nil))
debug2: key: /home/brian/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/brian/.ssh/identity
debug1: Trying private key: /home/brian/.ssh/id_rsa
debug1: Trying private key: /home/brian/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: Next authentication method: password
brian@192.168.1.71's password: 
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Requesting [EMAIL="no-more-sessions@openssh.com"]no-more-sessions@openssh.com[/EMAIL]
debug1: Entering interactive session.
debug2: callback start
debug2: x11_get_proto: /usr/bin/xauth  list :0.0 2>/dev/null
debug1: Requesting X11 forwarding with authentication spoofing.
debug2: channel 0: request x11-req confirm 0
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 1
debug1: Sending environment.
debug1: Sending env LANG = en_US.utf8
debug2: channel 0: request env confirm 0
debug2: channel 0: request shell confirm 1
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel_input_status_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 2097152
debug2: channel_input_status_confirm: type 99 id 0
debug2: shell request accepted on channel 0
Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-25-generic x86_64)


---

### Post by mullba on 2012-11-17
> **Lars Noodén said:**
> Ok.  That seems to confirm that X is not getting forwarded.  I don't suppose that you have any special firewall changes affecting the interface **lo**, do you?

I don't think so.  Both computers are on the same LAN, so I've never touched any firewall stuff.

---

### Post by mullba on 2012-11-17
Got it working.  On the server I ran ```
sysctl -w net.ipv6.conf.all.disable_ipv6=0 
``` to re-enable IPv6, and everything started to work.  Now I just have to hope it doesn't kill the server's network speed (the reason I disabled it in the first place)

---

### Post by holiday on 2012-11-17
On the client:

$ ssh -X user@server

On the server :
 In /etc/ssh/sshd_config

enable X11 forwarding. 

You will need to know the command line to open the application you're interested in.

When ssh opens your remote console:

$ nautilus . &

forexample.

---

### Post by holiday on 2012-11-17
Since you're new, here's a neat trick.

On the client:

$ ssh-keygen

It will give you a series of prompts. Keep pressing enter until it's done.

Then, on the client:

$ ssh-copy-id serverusername@server

You will be prompted to accept the server key, and then to enter the serverusername's password. 

Do so. 

Now you can log in without giving a password. Convenient and the only way to script a session. 

This does not compromise the server. The only way you can login without a password is when you are logged in as your user on the client.

---

