---
title: "can't ssh into server unless a user is logged in"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by jourosis on 2010-03-04
So I've managed to set up my desktop to be used as ssh server when needed. I can ssh into it from my laptop both in and out of the network, but only when I have physically logged into the desktop. Authentication is setup for only RSA public/private key. I've uncommented the line in sshd_config that points towards the 'authorized_keys' file in ~/.ssh/  Not sure what I should do, didn't have this problem in 8.10. Only arose when I did a clean install to 9.10. Let me know if I should attach my sshd_config, known_hosts, authorized_keys, etc.

---

### Post by Iowan on 2010-03-04
Network Manager only activates the network on login, and apparently doesn't play nice with */etc/network/interfaces* like it used to... To activate the network on power-up - you may need to disable Network Manager (I hate to recommend removing it entirely - but that might be the next step).

---

### Post by jourosis on 2010-03-04
Thanks for the response Iowan, but was it directed towards my post or was it a mis-post? I'm not sure I follow what Network Manager has to do with it (nor have I ever actively worked with it). Happen to have any instructions or links to disable it?

---

### Post by Iowan on 2010-03-04
It was intentional - desktops from Hardy onward normally use Network Manager by default (servers without desktop still use */etc/network/interfaces*). As the versions progress, NM seems to become more aggressive - I had my Jaunty laptop configured via "interfaces" without removing NM, but Karmic doesn't seem to work the same way.
System>Preferences>Startup Applications might let you disable NM. you can then try setting up your interface via */etc/network/interfaces* - even to get DHCP address. - If it doesn't work, you can un-do things - until you un-install something...

---

### Post by jourosis on 2010-03-04
So I disabled (or at least unchecked) Network manager from System>Pref>Startup App. 
My interfaces looks like:
```

auto lo
iface lo inet loopback
 auto eth0
iface eth0 inet static
	address 192.168.1.143
	network 129.168.1.0
	netmask 255.255.255.0
	broadcast 192.168.1.255
	gateway 192.168.1.1

```

For what it's worth, if I try to SSH into the desktop during Post/Grub etc, it comes back:
ssh: connect to host jourosis.ipstuff.com port 1199: No route to host

During Ubuntu startup, but before the login screen:
ssh: connect to host jourosis.ipstuff.com port 1199: Connection refused

At the login screen:
Permission denied (publickey).

Any further ideas? Is a full uninstall of Network Manager necessary?

---

### Post by jourosis on 2010-03-04
Hmm....as an interesting fact: I can ssh in at the login screen if I use  'root' instead of my username. Same RSA key works fine...so now I'm intrigued.

---

### Post by jobix on 2010-03-04
Try using the "-v" option and see what it tells you. Use it in both cases - where it works and where it doesn't.

> ssh -v your_machine


---

### Post by jourosis on 2010-03-04
ssh into desktop while logged on it already

```
mitchell@eeepc:~$ ssh -v mitchell@192.168.1.143
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /home/mitchell/.ssh/config
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.1.143 [192.168.1.143] port 1199.
debug1: Connection established.
debug1: identity file /home/mitchell/.ssh/identity type -1
debug1: identity file /home/mitchell/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/mitchell/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-6ubuntu2
debug1: match: OpenSSH_5.1p1 Debian-6ubuntu2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '[192.168.1.143]:1199' is known and matches the RSA host key.
debug1: Found key in /home/mitchell/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/mitchell/.ssh/id_rsa
debug1: Server accepts key: pkalg ssh-rsa blen 277
debug1: Authentication succeeded (publickey).
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: Requesting X11 forwarding with authentication spoofing.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
Linux mit-desk 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

Last login: Thu Mar  4 15:24:09 2010

```

ssh into desktop at login screen:
```

mitchell@eeepc:~$ ssh -v 192.168.1.143
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /home/mitchell/.ssh/config
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.1.143 [192.168.1.143] port 1199.
debug1: Connection established.
debug1: identity file /home/mitchell/.ssh/identity type -1
debug1: identity file /home/mitchell/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/mitchell/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-6ubuntu2
debug1: match: OpenSSH_5.1p1 Debian-6ubuntu2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '[192.168.1.143]:1199' is known and matches the RSA host key.
debug1: Found key in /home/mitchell/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/mitchell/.ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/mitchell/.ssh/identity
debug1: Trying private key: /home/mitchell/.ssh/id_dsa
debug1: No more authentication methods to try.
Permission denied (publickey).

```

Now of note: I found I can ssh into as root at the login screen only because: 
I copied my ~/.ssh/authorized_keys into /etc/ssh/ and also changed the sshd_config to point to /etc/ssh/authorized_keys. Changing either the sshd_config or the auth_keys file makes trying to ssh in as root have the same result. 

Also, my laptop user name is also 'mitchell' so the tags might be slightly confusing.

---

### Post by Gh0st83 on 2010-05-01
Is the OP still having this issue? I just came across this same issue yesterday.

Hadn't noticed it until now.  I was on my couch and my box was in Windows 7 (dual boot) and wanted to put it in Ubuntu, so remoted in and restarted it from Win7.  It boots by default into Ubuntu so I didn't have to get off my couch.  :P

But I noticed that I couldn't ssh in.. 

So I had to get off the couch.  :cry:


Like the first responder suggested, I added my eth0 iface settings into interfaces file.  No route.. no networking at start up until Gnome-Network-Manager starts.  Easy peasy.

Then I started getting access denied messages that it's rejecting my key even though it hasn't changed. But lo and behold it will log in fine when my local user is logged in.

I haven't tried root yet but that's where I was headed (at work now so I have my local user logged in and can't test).  It looks like a simple permissions issue (I checked, 700 on the key file), but if root is "logged in" to start (the default user that has to start all the services etc.), shouldn't it be able to read the authorized_keys file?

Or is it because the path specified in my sshd_config has the  current user's home variable and is directing to root's authorized_keys file?  Then it might be as simple as duplicating my keys file to root's .ssh directory...

Something to mull over while I pass the time at work.  :)

---

### Post by Gh0st83 on 2010-05-01
Back home.. and I have a small update.

I cp'ed my auth keys over to /root/.ssh but still can't ssh in while it's on the login screen.

I can however like the OP log in as root.  After in as root, I can su to my local user and THEN ssh in from a different console.  So at least there's a work around.. but I'd still like to be able to ssh straight in as my username.

I did notice that on the -v option for the non-logged in user there's a line that reads something to the effect of "new_key_added: 0" where as the attribute is a "1" when my user is already logged in and will let me log in.

I'll have to look more online and see if anything stands out.

---

### Post by sstiger on 2010-06-11
FWIW, I just found this thread on a search and wanted to say I'm having the same issue.

Attempting to log in to my Ubuntu 9.04 Server box from a 9.10 Desktop installation. I can't log in unless I've actually logged in on the server first. If it's on the login screen, I get the Permission denied (publickey).

---

### Post by Johan! on 2010-06-11
Is your home directory encrypted?
If it is, ~/.ssh/authorized_keys is not available until you log in on the server.

---

### Post by Johan! on 2010-06-11
.

---

### Post by sstiger on 2010-06-11
Holy cow. (headslap)
That must be it! I've been pulling my hair out with file permissions and it's gotta be the encrypted home directory!

---

### Post by Johan! on 2010-06-11
In that case, this is a possible solution:
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Troubleshooting](https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Troubleshooting)

---

### Post by sstiger on 2010-06-11
Sheer genius. Thank you so much!

---

### Post by verymagicalguy on 2010-06-25
So what's the verdict? Has anyone successfully gotten this to work? I'd like to have access without ssh keys.

---

### Post by msrk on 2012-01-25
I believe the following simple solution works.


Open the 'System Setting' dialog which can be found in the same drop down menu that has 'Log Out...' in it.

Then choose the 'Network' settings and then 'Wired' and then hit the 'Configure' button.  Make sure the 'Avaialable to all users' check box is checked and save it.  That works for me.

Good luck.

---

### Post by sahilsuneja on 2012-10-21
Thanks msrk 
That does indeed work!

---

### Post by wildmanne39 on 2012-10-21
Old thread closed.

---

