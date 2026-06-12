---
title: "samba net usershare: Where are my folders?"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by MartinMAP on 2011-05-08
Hello,

im a totaly noob to Ubuntu, but already love it! Just one thing is driving me crazy the whole day: I want to share my folders between notebook and desctop-PC. 
The desctop is linked to my Netgear-Webrouter by ethernatecable and the notebook by wireless. Everything is working well.

I followed these instructions: [http://wiki.ubuntuusers.de/Heimnetzwerk#Dateien-versenden](http://wiki.ubuntuusers.de/Heimnetzwerk#Dateien-versenden) (german)

i got no errors, everything fine, but where can i find my opend folders in the network?? Where to search for? Where is the "Workgroup"? Over "network" i just can see the windwosnetwork from other PC linked to the same router.

Is there a detailed noob-tutorial how to install a network over router?

Thank you!

PS: Notebook: easypeasy (ubuntu 10.04), Desktop: Ubuntu 11.04

---

### Post by SteveDee on 2011-05-08
If you are running Ubuntu and have the Samba GUI (menu System > Administrator > Samba) you can create shares from this interface.

You should also be able to see the shared folders across the network from Ubuntu (menu Places > Network). This will display "Windows Network" and clicking this should show your network (probably as "Workgroup" if you have not changed the default name).

Within your workgroup you should see your other network computers, and by clicking on them you should see any shared folders.

On Ubuntu the Samba interface is downloaded the first time you try to setup a folder share. Or you can manually install it via Synaptic, search for system-config-samba.

I hope this helps.

---

### Post by MartinMAP on 2011-05-08
Thanks! I Installed "system-config-samba" and created some shared folders. Now I can see the clients in "Network->Workgroup" but i cant connect to them. 

"receiving the memory list from the server has failed" 

BTW: That was a perfekt helping post! ;) Thanks!

Martin

---

### Post by SteveDee on 2011-05-08
OK try this:-
 - Open the Samba interface, double click on one of your shares.
 - Select the "Basic" tab and enable "writeable" and "Visible".
 - Select the "Access" tab, and then select "Allow access to everyone".

If this works, you can reset these settings to limit access if required.

---

### Post by MartinMAP on 2011-05-08
Already did - doesn't work :(

---

### Post by Morbius1 on 2011-05-08
This may not be a share issue but a name resolution problem. The two computers can't convert the host name to an ip address. Try to connect to the other machine by ip address rather than browsing to it:

In a terminal type:
```
nautilus smb://192.168.0.100
```Change 192.168.0.100 to the ip address of the machine you are trying to access.

---

### Post by MartinMAP on 2011-05-09
Bingo! Thats the problem! I connected from desctop to the ip from my notebook: Works!

Thanks!

But is that now the only way to connect?

Martin

---

### Post by Morbius1 on 2011-05-09
This name resolution problem isn't really a samba issue it's a networking issue but you can use samba to help the situation. Here's two things you can look at:

[1] Host name length. 

The Ubuntu installer has a bad habit of creating a hostname based on your login name + the word desktop ( or laptop ). So if my login name is morbius1 and I'm on a desktop the installer makes my host name:
```
morbius1-desktop
```The problem is that's 16 characters long. One character too long for the protocol so that machine becomes unresolvable.

Samba gives you an easy way out of this by allowing you to specify a shorter name in /etc/samba/smb.conf by allowing you to add the following line to the [global] section of smb.conf:
```
netbios name = morbius1-desk
```Just make sure it's less than or equal to 15 characters long.

[2] Name resolve order.

By default the only working mechanism is something called broadcast ( bcast ). But it's listed last in the order so place it first by editing smb.conf again and adding another line to the [global] section:
```
name resolve order = bcast host lmhosts wins
```In either case you need to restart samba after making any changes to smb.conf:
```
sudo service smbd restart
```No guarantee that [1] or [2] will fix you're particular situation but you'd be surprised how many it has fixed in this forum alone.

---

### Post by MartinMAP on 2011-05-09
Doasnt work :( Btw. my computersname are "map-note" and "map-pc". On both I have the same username "map".

Btw.: How can I change my computers name?

Thanks so far!

---

### Post by Morbius1 on 2011-05-09
Well, the remedies for browsing to the share from here get kind of complcated and one boarders on witchcraft as far as I'm concerned :)

A simple one usually offered is to give all your machines static ip addresses ( I recommend doing this via the router using "DHCP Reservation" ) and then populating the "hosts" file: /etc/hosts. For example a hosts file would look like this:
```
127.0.0.1    localhost
127.0.1.1    morbius
192.168.0.101 map-pc
```The logic in this one escapes me since if all your machines have static ip address you no longer need to "browse" to them. You can access them directly and then bookmark them so it shows up under "Places" in Nautilus. Just like a "mapped drive" does in Windows. Anyway, it does work since the "name resolve order" option will choose "hosts" and then look to the hosts file as a lookup table when you browse. All your machine will have to populate their hosts file.

Another way is to set one machine up as a WINS Server which is relatively easy to do on the Server end but it requires three things:
* The WINS server must be running or else none of the other machines can see each other.
* The WINS server must have a static ip address.
* And all the other machines on the network have to be reconfigured to point to the WINS server for name resolution.

You could also see if another router will fix it. All of this LAN side DNS resolution stuff should be happening in the router so changing the router might fix it.

I personally would suggest seeing if your router can assign static ip address. You know the ip address method works.

---

