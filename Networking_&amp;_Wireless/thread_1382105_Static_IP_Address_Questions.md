---
title: "Static IP Address Questions"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by Dweomer on 2010-01-15
Hello. First day on Ubuntu, or any OS besides Windows for that matter.

I'm trying to port forward, and for that I need to set up a Static IP address. I looked through the archive, and found[ this thread]("http://ubuntuforums.org/showthread.php?t=537938") in the hopes of doing this myself. Unfortunately, I have to bother you guys with questions anyway.

First off, how do I access/restore the backup (for sudo nano -B /etc/network/interfaces) if I mess up the new file and lose my internet connectivity? Being able to ask the community how to fix my stupid mistakes is a lifeline I definitely don't want to risk cutting. -_-

Second, in Windows I would also have a place to provide my DNS server addresses. Further, I don't know what to put in the 'network' entry. See below for what I have so far. I have a preferred and alternate DNS server address that I can put in, I just need to know where.

Third, is there a way to do this without the terminal in a 'more user friendly' manner?

```

auto lo 
iface lo inet loopback

# <Static IP Address>
auto eth0
iface eth0 inet static
        address 192.168.1.37 
        netmask 255.255.255.0
        network    
        broadcast 192.168.1.255
        gateway 192.168.1.1

```And again, I'm sure you get this question a lot, so sorry for having to ask.

---

### Post by Iowan on 2010-01-15
Network address is probably optional (as is broadcast), but when used, it's generally the same as your IP address but with "0" for last digit (192.168.1.0).

File backup (you may know):```
sudo cp /etc/network/interfaces  /etc/network/interfaces.bak
``` To restore, either delete or rename */etc/network/interfaces*, then copy or move:
```
sudo cp /etc/network/interfaces.bak  /etc/network/interfaces
``` or ```
sudo mv /etc/network/interfaces.bak  /etc/network/interfaces
``` The last version renames only - it doesn't make a second file.

If you have access to DHCP server, it might be easier to configure static lease (based on MAC address) and leave the machine alone. If you opt for this route, you can put your preferred DNS servers on the "prepend" line in */etc/dhcp3/dhclient.conf*.

---

### Post by KarlIvan on 2010-01-15
the default only contains:

auto lo
iface lo inet loopback

so you shouldnt even need to worry about a backup...if your looking to backup your own settings, then yes, doing what Iowan posted is the way to go i suppose.

furthermore, network and broadcast are optional, and whenever i statically set up my ip addressed, i dont need them. i dont imagine you would either

as far as doing it in a more "user-friendly" way, I don't believe it gets more user friendly than that. its fairly easy, just set up your addresses, then restart it:
sudo /etc/init.d/networking restart

---

### Post by lisati on 2010-01-15
My personal preference is to set up static IP addresses within my routers. That way I don't need to mess around with the settings on Ubuntu and/or Windows so much, and it can help avoid IP numbering conflicts if I need to connect my hardware to someone else's network or change the way my own network is hooked up for some reason. The exact method can depend on the router(s) used.

---

### Post by Dweomer on 2010-01-15
Things have not gone well. When attempting to find out if the port forwarding worked, I tried to check it with the actual application (Starcraft, via Wine). I was able to connect to battle.net before with major GUI problems, but the program ran fine. Now suddenly I can't connect, and when I exited, now I can't change files, including etc/network/interfaces.

I have no permissions despite being the only account. In fact I don't have permissions to even try to change permissions. [IMG]http://i45.tinypic.com/adz0ps.png[/IMG]

This seems to just be getting more and more complicated. I'm going to try restarting and see if that does anything. Also, one last thing. I can't get into Winecfg either. Not really a networking thing, but maybe somebody happens to know what's going on. I tried $ /usr/local/bin/winecfg as instructed by the wine hq page, but it said the file or directory was not found.

---

### Post by KarlIvan on 2010-01-15
theres your problem...youre trying to use the gui! lol

dont ever use the gui, use the command shell

and if your account doesnt have permissions, then use the superuser account by typing sudo before any command...i.e.:

```
$makeMeASandwich
Permission Denied

$sudo makeMeASandwich
is turkey ok?
```

---

### Post by Dweomer on 2010-01-15
That allowed me to get into winecfg, to change the setting to allow me to play Starcraft which swallowed the spider to eat the fly. Port forwarding didn't work though. Oh well. Too tired to keep trying to make things work today. Thank you for the help, everyone.

---

### Post by Dweomer on 2010-01-16
[IMG]http://i48.tinypic.com/2lkfjns.png[/IMG]

Good morning... Going to try to do this again. This is what I mean though. It won't let me save this file anymore. Speaking of which, I'm not entirely sure I'm even saving correctly. I chose ctrl + o, but I wasn't at all sure that was correct. The terminal confuses and frightens my savage wondoze brain.

---

### Post by CharlesA on 2010-01-16
Forgot to be at the root of the drive:

It should say **/**etc/networking/interfaces

Other then that, the config looks good.

---

### Post by Dweomer on 2010-01-16
Oh. :redface: 

Thanks.

It's still not working, and I never found out what to do with my DNS server addresses. My router is configured for 192.168.1.37 so other than the DNS server addresses I'm not sure what else would be causing the trouble. So much to learn... I just downloaded VirtualBox, I'm going to take a look at that and see if I can use it as a crutch for my specific starcraft problem.

EDIT: Oh no, VirtualBox requires me to install Windows on it. That's certainly not a practical solution to my problems. I installed Ubuntu because I *didn't* want to pay for Windows, and I'm pretty sure my old Windows disks from bought computers can't be used due to licensing and all that.

---

### Post by CharlesA on 2010-01-16
The router's IP is 192.168.1.1 right?

What's the exact problem you have with starcraft?

Anyway. To add the DNS entries you need to edit the /etc/resov.conf file like so:

```

nameserver 192.168.1.1
nameserver insert.ip.address.here
```

---

### Post by Dweomer on 2010-01-16
> **CharlesA said:**
> The router's IP is 192.168.1.1 right?

What's the exact problem you have with starcraft?

Anyway. To add the DNS entries you need to edit the /etc/resov.conf file like so:

```

nameserver 192.168.1.1
nameserver insert.ip.address.here
```

Well I'm port forwarding in the hopes that I'll be able to host games for Starcraft. Though from Linux through Wine it may not be possible at all. That's why I hoped VirtualBox would work since Starcraft is not a needy program, resource wise.

And yes, the router's IP is 192.168.1.1

---

### Post by CharlesA on 2010-01-16
Oh gotcha. Um, maybe install a copy of XP in VirtualBox and set it as a "bridged" adaptor. You should be able to set a static IP in windows and forward the ports over.

If you do an ifconfig -a does it show the correct static IP?

---

### Post by Dweomer on 2010-01-16
> **CharlesA said:**
> Oh gotcha. Um, maybe install a copy of XP in VirtualBox and set it as a "bridged" adaptor. You should be able to set a static IP in windows and forward the ports over.

If you do an ifconfig -a does it show the correct static IP?

>install a copy of XP in VirtualBox

Can I do that with my old XP disks? I thought they were tied to a single machine.

>Correct Static IP

Hm. No it does not. It's showing 192.168.1.6

---

### Post by CharlesA on 2010-01-16
Has the machine been rebooted since you set the static IP in the interfaces file?

Should be able to install a copy of XP, might have to call them to get it activated though.

---

### Post by Dweomer on 2010-01-16
> **CharlesA said:**
> Has the machine been rebooted since you set the static IP in the interfaces file?

Should be able to install a copy of XP, might have to call them to get it activated though.

Yes, it has been rebooted since saving with the 192.168.1.37 static IP. CTRL + O is save in the terminal text editors, right?

I will try to see if old XP CDs will work in VirtualBox. If I can reuse them and get VirtualBox working, it might be my best bet for a lot of things.

Edit: Should I try ```
sudo /etc/init.d/networking restart
``` And then check the ifconfig again?

---

### Post by CharlesA on 2010-01-16
should be CTRL + X to exit and "Y" to save changes.

You could try running:

```
cat /etc/network/interfaces
```

to see if the changes were saved.

---

### Post by Dweomer on 2010-01-16
It did save.

---

### Post by CharlesA on 2010-01-16
Do you have network manager installed by chance?

---

### Post by Dweomer on 2010-01-16
> **CharlesA said:**
> Do you have network manager installed by chance?

I'm not sure. I didn't install a Network Manager, I just have whatever came with Karmic Koala. However, I did happen to see that I had a /etc/NetworkManager folder when using the GUI.

---

### Post by CharlesA on 2010-01-16
Double click on the icon on the dock and set a static IP from there. See it that gets it working.

---

### Post by Dweomer on 2010-01-16
Took me a long time to find what you meant, but I personalized the panels (which is what I assume you meant by dock) in the process, and got my port forwarding working! Thank you so much to everyone who helped me out. Marked as solved.

---

