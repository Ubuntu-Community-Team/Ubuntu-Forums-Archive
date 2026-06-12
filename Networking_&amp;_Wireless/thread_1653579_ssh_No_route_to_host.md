---
title: "ssh: No route to host"
date: 2010-12-27
forum: Networking &amp; Wireless
---

### Post by Sugi on 2010-12-27
Hello everyone, I am having issues connect to my ssh server now.

It was working on my local network as it was connecting to the same router, but now that it's outside of my router connecting to another router, it will not work.

I have applied these changes which was working on my router.
 - Private/Public Key & Remote has private key
 - server has public key, named as authorized_keys_rem
 - PasswordAuthentication no
 - Change the port from the default
 - PermitRootLogin no
 - gconftool-2 --set /desktop/gnome/remote_access/local_only --type bool true

When I try to connect to the ssh server, it keeps reporting the follow:
ssh -f -p 1234 USER@111.222.0.331 -L 5900:localhost:5900 -N
OpenSSH_5.5p1 Debian-4ubuntu4, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 111.222.0.331 [111.222.0.331] port 1234.
debug1: connect to address 111.222.0.331 port 1234: No route to host
ssh: connect to host 111.222.0.331 port 1234: No route to host

Tried copying a file over to the server:
scp -P 1234 text USER@111.222.0.331:test
ssh: Could not resolve hostname 111.222.0.331: Name or service not known
lost connection



I am guessing this happening, because it can't find the ssh server.  I know this is the right IP of the ssh server, as I am using ifconfig.  I doubt this would even do anything, but I open the port on both routers, the local's and the ssh server's router.  

Please, can someone explain to me what is going wrong with this?

Local: Ubuntu 10.10 x64
ssh: Ubuntu 9.04 x86

Thanks for reading,
Sugi

[http://nixcraft.com/linux-hardware/6366-no-route-host.html](http://nixcraft.com/linux-hardware/6366-no-route-host.html)
[http://www.google.com/#sclient=psy&hl=en&safe=off&site=&source=hp&q=static+%2Fetc%2Fnetwork%2Finterfaces&aq=f&aqi=&aql=&oq=&gs_rfai=&pbx=1&fp=83f87efc6f926f13](http://www.google.com/#sclient=psy&hl=en&safe=off&site=&source=hp&q=static+%2Fetc%2Fnetwork%2Finterfaces&aq=f&aqi=&aql=&oq=&gs_rfai=&pbx=1&fp=83f87efc6f926f13)
[http://principialabs.com/beginning-ssh-on-ubuntu/](http://principialabs.com/beginning-ssh-on-ubuntu/)
[http://portforward.com/english/routers/port_forwarding/Tenda/W302R/BitComet.htm](http://portforward.com/english/routers/port_forwarding/Tenda/W302R/BitComet.htm)

---

### Post by Sugi on 2010-12-31
How can I get this working again?  When I was on the same network with the server, I probably had access no matter what, right?  What can I do to get back to that point having the server on another network?  What allowed it to work on my network?

Sugi

---

### Post by PatchesTheCaveman on 2010-12-31
Make sure you have the port forwarded through the router on the target machine's side.  (I believe you said you did that.)

Also make sure there isn't a firewall preventing the connection.  Many firewalls are configured to allow all traffic from the local network, but block traffic from foreign networks.

To temporarily disable the firewall for testing, run this command on the target server:
```
sudo ufw disable
```

---

### Post by Sugi on 2010-12-31
I won't be able to do the following command until I get the location of the laptop.  Is there anything I can do from my local computer?

---

### Post by PatchesTheCaveman on 2010-12-31
Not really.  Without SSH working you have absolutely no way of controlling the other computer.

---

### Post by Sugi on 2011-01-01
Sorry for the confusion, I might is there any changes or anything I can do on my local computer side that may help me with reaching my server.

Sugi

---

### Post by PatchesTheCaveman on 2011-01-01
It's highly unlikely the problem is on your local computer.

As long as you can access the Internet normally, the problem is likely in the remote host's configuration.

If you want, you can make sure ssh is working properly by connecting to a working server on the internet.  For example, you could try:
```
ssh nobody@github.com
```

Obviously you won't be able to login unless you have an account with GitHub but as long as you get a password prompt you can be sure everything's fine with your local computer.

---

### Post by Sugi on 2011-01-01
I forgot to post the output when trying to connect to the server.  Btw, I know the server is getting an IP, because it's working with firefox and ifconfig.

OpenSSH_5.5p1 Debian-4ubuntu4, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 111.222.0.331 [111.222.0.331] port 1234.
debug1: connect to address 111.222.0.331 port 1234: No route to host
ssh: connect to host 111.222.0.331 port 1234: No route to host

I renamed the key on the server as this authorized_keys_rem.  Is this the problem?  I am doubtful, but maybe it's bad practice?


Sugi

---

### Post by PatchesTheCaveman on 2011-01-01
The authorized_keys file stores public keys that you can use instead of password-based login.  However that file doesn't seem to be necessary, as my SSH server works fine without it.

If you renamed any of these files, you might have a problem:
```
moduli      sshd_config       ssh_host_dsa_key.pub  ssh_host_rsa_key.pub
ssh_config  ssh_host_dsa_key  ssh_host_rsa_key
```

Tou have a web server running on the server you can access?  That would eliminate a lot of possibilites, although the router configuration could still be incorrect for the port SSH is running on.  

Have you tried connecting to SSH on its default port (22)?  Maybe your changes to ssh_config didn't take effect (for instance if you didn't restart the SSH daemon or reboot after making changes).

---

### Post by Sugi on 2011-01-01
I am going to get the server back soon.  I was under time crunch to get it installed, setup and configured thus I did it sloppy, but it's only for me so I didn't screw anyone else over.  When I get it back, I am going to convert back to step 1 with minimal security and test out each setting to see the results.  Though when I test it out on my network, it's working fine, but when it's on an outside network it doesn't work at all.  Is there a way to test inhouse network for an outside network setting?

Btw, the authorized_keys was created on my local computer and the public key was sent to my server.  Then it was renamed on server computer to authorized_keys_rem.  That's what I meant from the earlier post.

Sugi

---

### Post by Sugi on 2011-01-03
Ok, I got the computer back and it's running without changes on the same network.  Even though, these exact same settings wouldn't work on separate networks.  Is there a way to test the settings for an outside of network environment?

Sugi

---

