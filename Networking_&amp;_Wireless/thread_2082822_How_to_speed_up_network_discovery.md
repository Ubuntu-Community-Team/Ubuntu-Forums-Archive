---
title: "How to speed up network discovery"
date: 2012-11-10
forum: Networking &amp; Wireless
---

### Post by Rebelli0us on 2012-11-10
When I need files I send a magic packet to wake up a machine and then I expect to access the files immediately. But on my networks and when I try to fetch files from another machine I get error messages, “failed to mount share”. Then I noticed that if you wait 10-20 minutes the shares eventually become available. Ironically, at the same time my Windows VMs running under the same Linux host have instant access to the same shares.

So it seems that Nautilus does a “lazy” discovery?:popcorn:

Is there a way to speed up access to network shares?

---

### Post by Morbius1 on 2012-11-10
This is pretty normal activity really although 20 minutes is a bit long. I guess it all depends on how many machines are in your network. You can try rearranging the netbios to ip address resolution parameter in smb.conf - in the [global] section:
```
name resolve order = bcast host lmhosts wins
```Then restart samba:
```
sudo service smbd restart
```bcast ( broadcast ) is the only one in the list that works by default and by default it's listed last on all your Linux machines.

[COLOR=Blue]*If you want to try something a little out of box use something Apple invented to discover your Samba hosts:*[/COLOR]

*** Create an avahi service file:***
```
gksu gedit /etc/avahi/services/samba.service
```***Add this content:***
```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
   <name replace-wildcards="yes">%h SMB</name> ## Display Name
   <service>
       <type>_smb._tcp</type>
       <port>445</port>
   </service>
</service-group>
```***Make sure avahi is running:***
```
sudo service avahi-daemon status
```***Start it if not:***
```
sudo service avahi-daemon start
```***Then as a test run the following command to see if you can see the samba shares on that same box:***
```
avahi-browse -at | grep IPv4
```It will be a bit confusing since after the 20 minutes you will see 2 references to the machine in Nautilus: one as HOSTx and another as HOSTx SMB but ...

This should work for all of your Linux machines that have avahi installed and running. Like I said it's a little out of the box but ...

---

### Post by Rebelli0us on 2012-11-10
Thank you.

I recently discovered the smb.conf file 

The line is there but commented out with semicolon:

;   name resolve order = lmhosts host wins bcast

Something keeps commenting out lines and I can't stop it, particularly in my share definitions:

[File System]
	path = /
;	available = yes
;	browseable = yes
	writeable = yes
	valid users = xxx yyy zzz



How come all WIndows VMs fetch the shares immediately without a problem?

---

