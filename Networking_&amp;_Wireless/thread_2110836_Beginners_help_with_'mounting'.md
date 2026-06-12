---
title: "Beginners help with 'mounting'"
date: 2013-01-31
forum: Networking &amp; Wireless
---

### Post by New Boy on 2013-01-31
After many years absence from Linux I have just recently loaded 12.10 using VirtualBox on Windows7

For the last day I have been searching for a 'How to:' to explain how one mounts drives on a NAS and also drives on other computers.

The Synology Diskstation says that the mounting information is ":/volumn1/Linux" .  But I can't find out how to 'mount'.

You may need further info in order help me - please ask.  My PC is hardwired to a BTHub3 and there is a wireless Laptop and a Synology Diskstation attached to the router.  All the attachments have fixed IP addresses in the range 192.168.1.1xx

Thanks for any help

---

### Post by howefield on 2013-01-31
Have you tried opening Nautilus (File Manager) and taking the Browse Network link to get to your NAS ?

Other drives should show up in here as well, left clicking on them should mount them, if you want them mounted automatically, you would need to add to your fstab.

---

### Post by New Boy on 2013-01-31
Thanks for your reply.  Yes I have and here is the error I get:

[ATTACH]230865[/ATTACH]

David

---

### Post by howefield on 2013-01-31
If this is a Virtualbox VM, do you have Network set to Bridged Adapter in the VM settings ?

---

### Post by steeldriver on 2013-01-31
if you open a terminal, can you ping the diskstation by its IP address?

do you generally have network connectivity from the virtual machine? (can browse web etc?)

FWIW I can mount my netgear NAS via nfs OR browse to it via nautilus / samba within a Mint13 VM on VirtualBox 4.2.4 under Win7 - my VM networking is the standard NAT mode

---

### Post by furything on 2013-01-31
I have seen a number of vm issues in the last few days - not being able to mount usb drives to browsing the network.

I have just done a 12.10 install on windows 7 64 bit and both network browsing and usb devices just work.

Have you ensured Additional options have been fully successfully installed?

How are you telling the vm to connect to ethernet?

Mine is setup to bridge to the physical lan port so it actually gets an ip address from the dchp server (I note you are using static but should not make a difference)

Are you using the NAT option or bridged adapter?
(I note as posting somone else asking same questions)

From your second reply I guess you can see the NAS box but if behind the NAT ethernet option could this be causing the problem?

In one solution to gain access to the usb it was suggested to map a shared folder from the Devices menu. It looks like you can do the same with network shares. Would this be a feasible for you?

Now I see the image I note you cannot see the network. try the ping first and check the adapter settings the default is NAT

---

### Post by New Boy on 2013-01-31
No I didn't have  Network set to Bridged Adapter - have now done so and on clicking Diskstation I get the error:

[ATTACH]230867[/ATTACH]  

I can't find any instructions anywhere as to how you do a mount.  Can you point me in the right direction please.

Many thanks
Dvid

---

### Post by furything on 2013-01-31
Now you have set to bridged adapter and can see NAS can you please check confirm following? 

The static ip of VM is in your 192.168.1.x your network mask (which is very important) should be 255.255.255.0 I expect and your default gateway is 192.168.1.1. make sure the NAS box is on the same subnet mask.

Disable the network from top panel of ubuntu menu bar and re-enable just to make sure connection does not hold problem with the NAT.

See if this works if not we will go through mounting a share through vm devices.

---

### Post by New Boy on 2013-01-31
> **furything said:**
> Now you have set to bridged adapter and can see NAS can you please check confirm following? 

The static ip of VM is in your 192.168.1.x your network mask (which is very important) should be 255.255.255.0 I expect and your default gateway is 192.168.1.1. make sure the NAS box is on the same subnet mask.

Disable the network from top panel of ubuntu menu bar and re-enable just to make sure connection does not hold problem with the NAT.

See if this works if not we will go through mounting a share through vm devices.

The IP address of the VM is 192.168.1.70
The static IP address of the Synology Diskstation is 192.168.1.108
According to the BT Hub the Subnet Mask is 255.255.255.0
According to the BT Hub the DHCP Network Range is 192.168.1.64 - 192.168.1.253 (Default)

I have disconnected and re-connected and clicking the Diskstation a window appears asking me for the Diskstation password etc which I complete and click OK 

But then I get the same error as follows:
[ATTACH]230871[/ATTACH]

David

---

### Post by furything on 2013-01-31
Ok you normally have to provide username password and domain (which can be workgroup) but this is how you share the folder to the VM

Probably best to shut down vm as I believe you need to reboot.

So in VMBox mngr select the shutdown ubuntu machine and ensure viewing details - select shares (you may need to scroll down depending on screen etc).

Click shared folders. In the new window click the +/folder icon (see attached).
Use folder path to select a shared local machine folder or across the network to a shared folder.

Give the share a sensible name if yo don't like the recommended one.

Then select auto mount and press OK (again see attached).

The new share should exist as a machine folder. Transient folder live with the session when added and die on reboot.

I found that guest additions would not install for me so follow this
[https://forums.virtualbox.org/viewtopic.php?t=15679](https://forums.virtualbox.org/viewtopic.php?t=15679)

You also need to mount the folder - follow
[https://forums.virtualbox.org/viewtopic.php?t=15868](https://forums.virtualbox.org/viewtopic.php?t=15868)

---

