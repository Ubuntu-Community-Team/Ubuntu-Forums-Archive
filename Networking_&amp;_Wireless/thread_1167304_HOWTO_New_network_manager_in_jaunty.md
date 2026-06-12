---
title: "HOWTO: New network manager in jaunty"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by expelledboy on 2009-05-22
I have had a problem with jaunty's net-manager from the get go. I started up from a fresh install and it didn't automatically connect to my DHCP server and get its ip and other info. I then tried to add a static connection via the applet with no luck.. Finally I manually edited /etc/network/interfaces and got my connection up and running. The only problem I could see was that the applet could not be used at all to configure the network. No biggy..

It came to pass one day that I had nothing to do and the applet was teasing me.. with its unused wireless meter (even though I only use wired..) poking at my firm statement that jaunty has to be so far the best OS ever.. I got down, used my windows admin skills inherited from my father combined with my linux guru magic, and fixed the bug in my otherwise perfect install.

Before we start let us put on some protection and backup all that we are about to edit.:cool:
```
mkdir ~/condom; sudo cp /etc/network/interfaces ~/condom/
```


Firstly edit your interfaces file..
```
sudo vim /etc/network/interfaces
```
..or if you dont know how to use vim use your favourite editor, or if you dont know how call up a editor from the terminal at all..
```
gksudo gedit /etc/network/interfaces
```
[LIST]
[*]remove all interfaces except loopback or comment them out
[/LIST]

So your interfaces file should look something like this..
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
```

[LIST]
[*]remove all connections made in your network-manager app
[/LIST]

(here is where my windows experience really kicks in..)

[LIST]
[*]restart :P
[/LIST]

That should be it. If you have DHCP it will automatically connect. If you want you can change it, to a static address, you can.. via the applet! Heh, technology these days advancing so fast for a old timer like me.. born in the days when Metallica release the most successful album ever called "Metallica" and Freddie Mercury one day after announcing he had AIDS died of AIDS.. :D

---

### Post by Iowan on 2009-05-22
My Jaunty install worked on both wired and wireless for a couple of days, then - after a wifi session at a local restaurant - refused to connect via DHCP.  I successfully added a manual IP address via */etc/network/interfaces*, then, duplicated the success by commenting out configuration in */etc/network/interfaces* and setting up a similar address via NM applet.  Finally, took advice and commented out "rfc3442" (details [here]("http://ubuntuforums.org/showthread.php?t=1156441")). Now, I have DHCP configuration that defaults to static address if DHCP fails.  So far I'm liking Jaunty.

---

### Post by expelledboy on 2009-05-23
I think the old style network manager was better.. Maybe when the bugs are worked in this one out it will grow on me?

Two things that really ticks me off with this one is when the 'apply' button greys out. I found the problem was the MAC address field had not been filled in, so I found it via *ifconfig*. The other fix it is do what I did above. It seems to work everytime. 
The other thing is when you finally do click the apply button in *IPv4 Settings* the gateway field changes to *0.0.0.0*. The solution was simple. Remove the entire entry in the addresses widget and start over.

It is unfortunate the NM does this. I install and maintain quite afew ubuntu computers and I hate it when someone comes back and wants to go back to windows because the applet does not do what its supposed to, or a service like dictd with gnome-dictionary doesn't work. :(

---

### Post by expelledboy on 2009-05-25
> **Iowan said:**
> My Jaunty install worked on both wired and wireless for a couple of days, then - after a wifi session at a local restaurant - refused to connect via DHCP.  I successfully added a manual IP address via */etc/network/interfaces*, then, duplicated the success by commenting out configuration in */etc/network/interfaces* and setting up a similar address via NM applet.  Finally, took advice and commented out "rfc3442" (details [here]("http://ubuntuforums.org/showthread.php?t=1156441")). Now, I have DHCP configuration that defaults to static address if DHCP fails.  So far I'm liking Jaunty.

I think you had dhcp problems, not NM-applet issues? I have to say I have never had your problem but thanks for linking.. I am sure I will run into your problem sooner or later. :)

---

