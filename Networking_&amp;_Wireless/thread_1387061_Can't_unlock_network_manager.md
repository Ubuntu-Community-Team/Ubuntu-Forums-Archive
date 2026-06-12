---
title: "Can't unlock network manager"
date: 2010-01-21
forum: Networking &amp; Wireless
---

### Post by AfefTech on 2010-01-21
I am working to connect several Ubuntu computers to a Hughs satelite radio via a Trednet switch.  The ISP requires static IP addresses on our machines.  Obviously, to do that I need to access the Network Manager.
 
When I click on the Unlock button the machines wait for a minute or so and return a "could not authenticate" message.  It never prompts for a password.
 
When I loaded the OS on these computers in the states, there were no issues with the install or updates and configuration.  Now that they have been shipped to Africa there is something which has happened to all the computers and they will not unlock.
 
If i reload the OS they do fine...whats going on?
 
Thanks

---

### Post by iponeverything on 2010-01-21
Try configuring the interfaces via the file: 

```
/etc/network/interfaces
```

---

### Post by iponeverything on 2010-01-22
[replying to pm]

In your file

```
/etc/network/interfaces
```

add something like this were the information is correct for your network configuration:

```

iface eth0 inet static
  address 192.168.1.44
  netmask 255.255.255.0
  gateway 192.168.1.1
# 
auto eth0

```


You can from the prompt do:

```

sudo -i
cd /etc/network
nano interface

```

nano is the editor that you can use to edit the file.

---

### Post by AfefTech on 2010-04-27
That is exactly how I was able to work around that problem...but the problem of working within the GUI remains (the issue of unlocking).  I have done allot of checking on this and it appears to be a very common problem but a good solution has yet to be found.

---

