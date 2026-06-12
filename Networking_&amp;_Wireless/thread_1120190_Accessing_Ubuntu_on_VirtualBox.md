---
title: "Accessing Ubuntu on VirtualBox"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by caperaven on 2009-04-08
I have a windows machine running virutalbox.
On virtualbox I have a ubuntu install with a working appache server.

I want to access the appache server from my windows box.

I noticed that I can ping the windows machine from the ubuntu virtual box, but I can not ping the ubuntu from windows.

I disabled the firewall to no avail.

Can you please advise on how I can do this.

---

### Post by Jose Catre-Vandis on 2009-04-08
How did you set up the network on the guest? Did you use a bridged (host) interface? Is the guest on the same subnet as the host? Can you http:// to the guest as you have apache running?

---

### Post by BkkBonanza on 2009-04-08
If you setup the guest with default (NAT) network mode then you cannot get to the ports on the guest except by adding NAT rules to allow the access. See virtualbox manual for that. Also the NAT blocks any ping (ICMP) traffic and I don't think there's a way to bypass that.

If you setup with "Host mode", then the guest will appear like another machine on your network with it's own ip assigned by your router. This is probably the preferred way for running a server. You can change the mode by using the settings button in the VirtualBox control panel tool.

---

### Post by caperaven on 2009-04-09
Ja I left it on default (nat), will change it to host and see what happens, thanks a lot.

---

### Post by Spider7 on 2009-04-09
> **caperaven said:**
> Ja I left it on default (nat), will change it to host and see what happens, thanks a lot.

I use vmware and NAT, and everything works just fine. basically, vmware sets up a interface on the windows host that's in the same subnet as the guest os. NAT is done when the packet is routed in the windows box. 

if you do ipconfig on your windows host cmd window, is there an interface that's in the same subnet as the guest ip?

---

### Post by GoodPanos on 2009-05-05
What if you want to browse from the host using the name of the guest?  Right now I can only browse sites I have created on the Ubuntu guest via the IP address only.  Is there a way to do via the host name of the guest machine?

---

### Post by Spider7 on 2009-05-05
> **GoodPanos said:**
> What if you want to browse from the host using the name of the guest?  Right now I can only browse sites I have created on the Ubuntu guest via the IP address only.  Is there a way to do via the host name of the guest machine?

You should be able to add an entry to hosts file on your host machine. For my case, the following entry was added to the file - c:\windows\system32\drivers\etc\hosts

192.168.1.10  ubuntu8

---

### Post by GoodPanos on 2009-05-06
I want to put this as a new post but lets see if we can dissect part of my issue(s) here.

I would make an entry into my hosts file if my guest had a static IP address.  What if I don't have a static IP address?

I have the guest running on a laptop in VB bridged mode, so depending on what network I connect to, the IP address and schema changes.

---

### Post by BkkBonanza on 2009-05-06
I believe you can add a hostname value into the interfaces config file so that when dhcp gives you or your guest an address it will also update it's dns records with the name so that the name will be resolved correctly. I don't have this setup myself but I think it works something along that lines.

---

### Post by GoodPanos on 2009-05-06
So, how do you...> add a hostname value into the interfaces config file?

---

### Post by BkkBonanza on 2009-05-07
According to **man interfaces** you can add a line like below to /etc/network/interfaces when configured using dhcp method (follows iface line):

hostname my_host_name

---

### Post by Spider7 on 2009-05-07
Check this discussion on setting hostname for dhcp

[http://ubuntuforums.org/showthread.php?t=1439](http://ubuntuforums.org/showthread.php?t=1439)

---

### Post by GoodPanos on 2009-05-10
Thank you all for the responses but none of the recommended solutions worked.  I still can't ping the hostname.

I also realized that I have to get this working because with WorPress you have to specify the address of the site.  So if the IP address changes, I have to also change the address in WP in order to see it on the host machine.

In seantellis post he set up a domain name.  Do I have to use a domain name or just a hostname is fine?  I did it both ways, anyways to no avail.

---

### Post by conceptrat on 2009-06-24
> **caperaven said:**
> I have a windows machine running virutalbox.
On virtualbox I have a ubuntu install with a working appache server.

I want to access the appache server from my windows box.

I noticed that I can ping the windows machine from the ubuntu virtual box, but I can not ping the ubuntu from windows.

I disabled the firewall to no avail.

Can you please advise on how I can do this.

Okay I've just done this again, this time with VirtualBox on MacOSX host.  There's more than one way to do this but I've chosen this particular route before and it works fine for me.  I'll talk about that at the end but for now lets just get stuck into it :)

Okay so VirtualBox, by default, sets up a network interface for the VM using NAT which allows for packets to be routed out of the guest interface to the active network on the host but not the other way around unless they were initiated from the VM.  So we need an interface and route for the packets coming from the host to the VM and returning.  Stop the VM, if it's running, and then in the "Details" tab in the VirtualBox interface, click on "Network".  This takes you to the setting for the network adapters.  You should see the default network adapter "Adapter 1" as "Attached to: NAT".  Now click on "Adapter 2" and tick "Enable Network Adapter" then change the "Attached to:" to "Host-only Adapter".  The "Name:" field should be filled in with a default.  Just click "OK".

So now power on the VM and in your host OS, in your case Windows, check for this new network adapter and bring up the details for it via the "Networking" control panel.  Look for the IP address and Network it's connected to and make a note of these.

Now login into the VM and then verify that the second network interface has been detected by dropping into a shell and use "ip addr".  You should see "eth1" show up for you if your running an Ubuntu VM and you haven't done anything else.  It will most likely not be currently "UP" and not allocated an IP address because it hasn't been setup yet.  That's what we're going to do :)

Okay so now you need to setup this interface.  Lets do it from the shell initially to test things out and make sure that it works.  First we add an IP address to the interface and we need to choose one in the same range that the host has allocated for the second network interface we retrieved the details for above.  So say for example the details above came out with an IP address of "192.168.56.1" and netmask of "255.255.255.0" then we'd choose, for simplicity's sake, an IP of "192.168.56.2" and the same netmask (we want to be in the same subnet).

Now we can use the "ip" command again but this time you'll need to use "sudo" to run it with "superuser" privileges.  So type:

```
sudo ip addr add 192.168.56.2/255.255.255.0 dev eth1
```

If you haven't already used sudo, in the last 5 minutes, the you'll need to enter in your login password.

If you don't get any errors then next we bring up the interface with:

```
sudo ip link set eth1 up
```

Now if you type:

```
ip addr
```

You should see the new IP address allocated to "eth1" and it should also be "UP".  Try pinging it now.  If you're not running a firewall on the host then you should also be able to ping the host's secondary interface, using the IP address that we noted down from the host.

Okay now you should also be able to ping this new IP address from the host and hopefully also be able to point your browser at this IP address and get the "It works!" default or maybe something else if you've already installed something under Apache's root dir.

So if it's all going now then the last step is to add this IP address setup to the network interface configuration file so that it will get setup automatically for us next time we start up the VM.  Almost there now :)

So we need to edit "/etc/network/interfaces" so type:

```
sudo vim /etc/network/interfaces
```

Feel free to use another editor.  And add the following to the end of the file:

```
auto eth1
iface eth1 inet static
  address 192.168.56.2
  netmask 255.255.255.0
```

Now save that and reboot the VM.  When the VM comes back up, if you have the Apache server starting up at boot, then you should, again, be able to browse to it via that IP from the host :)  The "auto eth1" in "/etc/network/interfaces" is the bit that make the network interface come up at boot time without it you have to start it manually using "sudo ipup eth1" via the shell.

I hope I haven't forgetten anything?

And now to the reason I did it this way...

I figured it was slightly more secure for me as I don't wish my VM to get an IP allocated from the DHCP on my network or if I'm connected via an open wireless hotspot, then from an external router with a visible external IP.  And I don't need any other machines on my network to access this VM.  Hope that makes sense :)

Cheers
Julz

---

