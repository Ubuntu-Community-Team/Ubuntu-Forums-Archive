---
title: "Help Accessing Home Computer From Work via SSH"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by jlacroix on 2009-05-27
Hello everyone, I went ahead and set up DynDNS for my router so now I can access my home router from anywhere off site. I even set up port forwarding to forward requests to my home computer. Now, I need to know how to open up that port on my Kubuntu box so I can access it from off site.

Any help is appreciated, does anyone know how I can open a particular port for incoming SSH requests on my Linux box?

---

### Post by stefangr1 on 2009-05-27
You don't have to open a port in your Ubuntu machine.

The steps below should do it:
(1) install openssh-server on the server
(2) fix the ip-address of your server inside the local network (preferably in your router)
(3) forward port 22 in your router to the fixed address of the server

---

### Post by Iowan on 2009-05-27
For what it's worth... I'd pick a non-standard port on the router to use for SSH - might cut down on the script-kiddies.

---

### Post by jlacroix on 2009-05-27
> **stefangr1 said:**
> You don't have to open a port in your Ubuntu machine.

The steps below should do it:
(1) install openssh-server on the server
(2) fix the ip-address of your server inside the local network (preferably in your router)
(3) forward port 22 in your router to the fixed address of the server

> **Iowan said:**
> For what it's worth... I'd pick a non-standard port on the router to use for SSH - might cut down on the script-kiddies.

I believe I would need to open a port in order to access individual computers, I have three that I need to access this way. I am thinking that opening a port would allow me to access individual machines anyway, this is the first time I have ever tried doing this. Is there any other way to differentiate one machine from another when I am trying to access them from outside the house? I am new to remote access so I would appreciate any help you guys can give. Thank you!

---

### Post by Iowan on 2009-05-27
There are usually several ways to accomplish the same result.  Forwarding different non-standard ports to different machines would be one option.  SSH-ing into your computer, then SSH-ing to another machine might be another.  

To SSH into that machine means SSH-server must be installed on it. Have you seen [this]("https://help.ubuntu.com/community/SSH?action=show&redirect=SSHHowto") help page?

---

### Post by jlacroix on 2009-05-27
> **Iowan said:**
> There are usually several ways to accomplish the same result.  Forwarding different non-standard ports to different machines would be one option.  SSH-ing into your computer, then SSH-ing to another machine might be another.  

To SSH into that machine means SSH-server must be installed on it. Have you seen [this]("https://help.ubuntu.com/community/SSH?action=show&redirect=SSHHowto") help page?

I can already SSH into any machine in my local network and that all works fine. I just can't do that when I am trying to get in from outside the network. I am not concerned about security so much, because the computer I am connecting to via SSH is always off. If I need access, I will just call my wife and have her turn it on for a few minutes until I got what I need.

---

### Post by pricetech on 2009-05-27
I had problems with non standard ports on Jaunty.  Port 22 was the only one that would work.  My "old" box with Hardy worked just fine with a non standard port as long as I stuck to the same port all the way to the machine.

fail2ban will help with the script kiddies.

---

### Post by dmizer on 2009-05-27
You will need to configure port forwarding in your router: [http://portforward.com/](http://portforward.com/)

---

### Post by jlacroix on 2009-05-27
I already set up port forwarding in my router. I am pretty sure I need to open up something on the Ubuntu side because it just times out whenever I try to connect.

---

### Post by dmizer on 2009-05-27
> **jlacroix said:**
> I already set up port forwarding in my router. I am pretty sure I need to open up something on the Ubuntu side because it just times out whenever I try to connect.

Is your router configured for DHCP? Is the port forwarded to your ssh server's correct IP address? Is the ssh port open on your office network?

---

### Post by lensman3 on 2009-05-27
Does the Linux box that your are forwarding to have a "firewall" turned on?

Kill all of iptables until you have established the connection.

---

### Post by dmizer on 2009-05-27
> **lensman3 said:**
> Does the Linux box that your are forwarding to have a "firewall" turned on?

I don't think this is a problem due to this comment:
> **jlacroix said:**
> I can already SSH into any machine in my local network and that all works fine.

---

### Post by jlacroix on 2009-05-28
> **dmizer said:**
> Is your router configured for DHCP? Is the port forwarded to your ssh server's correct IP address? Is the ssh port open on your office network?

Yes, I am using DHCP. I have the port forwarded to the machine's IP address that I am trying to connect to. As far as the port being open, I doubt it, I don't know how to open ports other than in the router. Perhaps I have to open it in Linux as well?

> **lensman3 said:**
> Does the Linux box that your are forwarding to have a "firewall" turned on?

Kill all of iptables until you have established the connection.

How do I do that?

Thank you guys for being so patient. I will reply to any responses tomorrow evening. :)

Good night!

---

### Post by dmizer on 2009-05-28
Well, if your computer is booting with DHCP, it may not be getting the same IP address as the one you're trying to forward to.

As far as ports being open, I'm talking about the office (your work) side of things, not your home. Sometimes company admins block popular ports for ssh and ftp for example. You'll have to talk to your IT department to determine if this is the case.

---

### Post by jlacroix on 2009-05-28
> **dmizer said:**
> Well, if your computer is booting with DHCP, it may not be getting the same IP address as the one you're trying to forward to.

As far as ports being open, I'm talking about the office (your work) side of things, not your home. Sometimes company admins block popular ports for ssh and ftp for example. You'll have to talk to your IT department to determine if this is the case.

No, my work isn't blocking the port I'm trying to use. The Network Administrator was actually the guy helping me on this and got me this far in the process.

I can say that when I connect to my network locally when at my house it works fine. If I use my outside IP address while at home I get "connection refused". Something inside my network is blocking SSH from the port I am trying to use.

The IP address isn't different, I set up the lease time to be VERY long (1 week) and I checked it just now and its the same.

---

### Post by dmizer on 2009-05-28
> **jlacroix said:**
> If I use my outside IP address while at home I get "connection refused". Something inside my network is blocking SSH from the port I am trying to use.

No, this is a common misconception. Your router simply cannot handle loop back. That is, it gets confused when the originating IP and the terminating IP are both in the same network. The request looks like a boomerang to the router and it can't handle it.

When you are inside your LAN, use your LAN IP. When you are outside your own LAN, then you can use your external IP. Have you tried it from outside your LAN yet?

---

### Post by jlacroix on 2009-05-28
> **dmizer said:**
> No, this is a common misconception. Your router simply cannot handle loop back. That is, it gets confused when the originating IP and the terminating IP are both in the same network. The request looks like a boomerang to the router and it can't handle it.

When you are inside your LAN, use your LAN IP. When you are outside your own LAN, then you can use your external IP. Have you tried it from outside your LAN yet?

Yes, I have been trying it from outside, as I've stated I've been trying it at work.

I'm 90% positive that Ubuntu is refusing my connection. If I remember correctly, non standard ports are not open by default.

---

### Post by dmizer on 2009-05-28
Okay, then please post your /etc/ssh/sshd_config contents.

If you can connect from inside your LAN, you should be able to connect from outside as long as port forwarding is set up correctly, non-standard port or otherwise.

---

### Post by jlacroix on 2009-05-29
> **dmizer said:**
> Okay, then please post your /etc/ssh/sshd_config contents.

If you can connect from inside your LAN, you should be able to connect from outside as long as port forwarding is set up correctly, non-standard port or otherwise.

I played with it some more, and if I set the port forwarding to port 22, I can connect and launch XWindows apps with Xming without any issues. If I set the port forwarding to the port I prefer, I get connection refused in Putty.

Here is the contents of that file. I tried entering the port number that I use in the line after "Port 22" but that didn't work:
```
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

```

---

### Post by dmizer on 2009-05-29
Well as far as I know, you can't have ssh listening on two ports. You'll have to use either port 22 or your preferred port, but not both.

What you can do, is configure your router to forward your preferred external port to port 22 locally.

---

### Post by jlacroix on 2009-05-29
> **dmizer said:**
> Well as far as I know, you can't have ssh listening on two ports. You'll have to use either port 22 or your preferred port, but not both.

What you can do, is configure your router to forward your preferred external port to port 22 locally.

I changed it from port 22 to the port I wanted and that worked! Thank you!!!

Now what I am going to do is disable port forwarding on my router. Whenever I want to connect to my computer, I will log on to my router remotely and turn on the port forwarding just long enough for me to use it. Is that an adequate security policy for me to use?

---

### Post by dmizer on 2009-05-29
> **jlacroix said:**
> Now what I am going to do is disable port forwarding on my router. Whenever I want to connect to my computer, I will log on to my router remotely and turn on the port forwarding just long enough for me to use it. Is that an adequate security policy for me to use?

If it's security you're worried about, I highly suggest getting configured for rsa keypairs and disabling password login. More information here: [https://wiki.ubuntu.com/AdvancedOpenSSH](https://wiki.ubuntu.com/AdvancedOpenSSH) that way, you can just leave the forwarding on and not worry about it.

As for enabling and disabling port forwarding, that may require a router reboot, so that could cause difficulty. Not sure though.

---

### Post by jlacroix on 2009-05-29
> **dmizer said:**
> If it's security you're worried about, I highly suggest getting configured for rsa keypairs and disabling password login. More information here: [https://wiki.ubuntu.com/AdvancedOpenSSH](https://wiki.ubuntu.com/AdvancedOpenSSH) that way, you can just leave the forwarding on and not worry about it.

As for enabling and disabling port forwarding, that may require a router reboot, so that could cause difficulty. Not sure though.

I don't think my router requires a reboot for port forwarding. Whenever I change the ports, it doesn't require me to. Thank you for everything you've done. :)

---

