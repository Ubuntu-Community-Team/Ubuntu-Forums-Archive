---
title: "Can't find samba-shares"
date: 2013-04-13
forum: Networking &amp; Wireless
---

### Post by Azyx on 2013-04-13
Have a home-server there I have shared some folders and disks on 12.04LTS. If I run testparm on the server it says ok (exempt long name, but It's should only be a problem with old windows-system, and it have worked fine before

```
Azyx@Blackus:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Downloads-guest]"
Processing section "[Downloads]"
Processing section "[500GB-guest]"
Processing section "[500GB]"
Processing section "[Media-guest]"
Processing section "[Media]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions
```


I can connect from Ubuntu 10.04 and 12.04 with VNC, so there are network connection. I have also tried to browse network with a 12.04LTS client, with no results.

---

### Post by prodigy_ on 2013-04-13
Open terminal on the client and try the following command: ```
smbclient //Blackus/Downloads
``` If your samba configuration is OK, you'll be prompted for password and then you'll see **smb: \>** prompt.

---

### Post by Azyx on 2013-04-13
> **prodigy_ said:**
> Open terminal on the client and try the following command: ```
smbclient //Blackus/Downloads
``` If your samba configuration is OK, you'll be prompted for password and then you'll see **smb: \>** prompt.

get this with: smbclient //Blackus/Downloads

```
Connection to Blackus failed (Error NT_STATUS_HOST_UNREACHABLE)
```

But with : smbclient //192.168.0.4/Downloads

```
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.3]
smb: \> 
```

It worked

So It seems to be a problem with the local DNS or something? Yes, my local ip-number have change. I think...

Thanks  				 					[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar518500_2.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=518500") 				 				 					 						 	[**[COLOR=#000000]prodigy_[/COLOR]**]("http://ubuntuforums.org/member.php?u=518500") for putting my in right directions. It's my f*cking broadband 'router' that forget the assanged IP for the computers mac-adress (I cleaned up in the 'router' and restarted and get the assanged IP-number). But it is sad that Ubuntus Network-browser not are able to find samba-servers after ip-number have changed. Is there another browser that really read the local network?

---

### Post by prodigy_ on 2013-04-13
If you use DHCP to assign IP addresses, there are many possible solutions. Some examples:
- [add WINS service to your samba server](http://oreilly.com/openbook/samba/book/ch07_03.html);
- configure your DHCP server to always assign a specific IP to the samba server (by its network card MAC address);
- re-configure the samba server to have a static IP and then add a record to /etc/hosts on the client (or to your local DNS server).

---

### Post by Morbius1 on 2013-04-13
All of your machines are running Ubuntu so as long as you haven't disabled avahi or blocking it with your firewall you should be able to connect to it with an mDNS qualified host name:

```
nautilus smb://blackus.local/downloads
```
*[COLOR=#0000cd]**BTW**[/COLOR], There is a way to force it to show up under "Network" in both Linux and OSX clients by creating an avahi-samba service file if you are interested.*

---

### Post by Azyx on 2013-04-14
> **Morbius1 said:**
> All of your machines are running Ubuntu so as long as you haven't disabled avahi or blocking it with your firewall you should be able to connect to it with an mDNS qualified host name:

```
nautilus smb://blackus.local/downloads
```
*[COLOR=#0000cd]**BTW**[/COLOR], There is a way to force it to show up under "Network" in both Linux and OSX clients by creating an avahi-samba service file if you are interested.*

The problems appears when the server Blackus get another ip-adress. I have avahi activated. In remote desktop I'm able to search the network and new ip.appears, but not in nautilus.

---

### Post by Morbius1 on 2013-04-14
By using **blackus.local** it no longer matters if the ip address changes on every boot. Avahi takes care of that for you by using mDNS. 

Can you or can you not access the server using:
```
nautilus smb://blackus.local/downloads
```
[COLOR=#0000cd] *Make sure port 5353/udp is open*[/COLOR]

[COLOR=#0000cd] *And make sure avahi is running on both systems:*[/COLOR]
```
sudo service avahi-daemon status
```

If you can then the client can just bookmark that location. But you can ( with the addition of one file ) also force the host to show up in Network if you need to browse to that location.

---

### Post by Azyx on 2013-09-26
Thanx! :)

---

