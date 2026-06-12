---
title: "openvpn through networkmanager does not connect on lucid"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by Hoaxe on 2010-07-27
I have been trying to figure this out for a while now but can't seem to find the solution. here is the situation

i have added a vpn connection on my Lucid desktop machine, but every time i try and connect, it fails. I also have the same, _identical vpn connection on my karmic_ install on my laptop. _everything works perfectly on Karmic, but Lucid is having problems_. I have followed identical steps for creating the vpn connection on both machines:

vpn connections can be made in 2 ways, the first is through the network manager, but trying to connect through the nm-applet returns an error about vpn failing to connect and "no valid vpn secrets".

the second way to connect is through the terminal, running this command: 

```
$ openvpn --config ~/.openvpn/client.ovpn
```

this give me the following errors: 
```
Note: Cannot ioctl TUNSETIFF tun: Operation not permitted (errno=1)
Note: Attempting fallback to kernel 2.2 TUN/TAP interface
Cannot allocate TUN/TAP dev dynamically
Exiting 
```

by searching around i found out that in kernel that came with Lucid, the tun module was built into the kernel, hence, running 
```
lsmod | grep tun
``` 
will _return nothing in Lucid_ but will return the following with karmic:
```
tun                    13788  0 
```

I suspect this is at the root of the problem. The only way for my Lucid machine to successfully connect through the command line is if I run the openvpn command under sudo. This bypasses the permission problems but does not solve the problem with the network manager.

if anyone has any insight I would greatly appreciate.

I found some bug reports related to what i am talking about, but nothing seems to be specifically this problem.

---

### Post by Hoaxe on 2010-07-27
I found this conversation on the ubuntu-bugs mailing list. 

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2290652.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2290652.html)

it turns out i needed to make a /lib/modules/modprobe.conf file and put the statement

```
install tun /bin/true
```

i made my modprobe.conf file inside /lib/modules and now openVPN with lucid works through the network manager. no more tun module errors or permission errors.

---

### Post by aim on 2010-08-09
actually all you need is to add yourself to the group 'netdev' and unchek 'available to all users' in vpn settings window in networkmanager

---

