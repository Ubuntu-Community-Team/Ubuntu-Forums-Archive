---
title: "Unable to mount location - Failed to retrieve share list from server"
date: 2011-08-14
forum: Networking &amp; Wireless
---

### Post by Eleos on 2011-08-14
It seems this is a common problem.  I used Samba to configure and connect the computer running Ubuntu 11.04 with my Windows Visa workgroup.  This is a wired, not wireless, connection.

In Ubuntu, under Network, I can see the name of the other computer (NOVA_MORAI), but when I click, I get the error:

Unable to mount location - Failed to retrieve share list from server

I tried the nmblookup command, here is the output:

eleos@Planet-Morai:~$ nmblookup NOVA_MORAI
querying NOVA_MORAI on 192.168.1.255
192.168.1.2 NOVA_MORAI<00>

And:

eleos@Planet-Morai:~$ nmblookup -A 192.168.1.2
Looking up status of 192.168.1.2
	NOVA_MORAI      <00> -         B <ACTIVE> 
	PLANET OF FATE  <00> - <GROUP> B <ACTIVE> 
	NOVA_MORAI      <20> -         B <ACTIVE> 
	PLANET OF FATE  <1e> - <GROUP> B <ACTIVE> 

	MAC Address = 00-1B-B9-83-AC-67

There it it.  But when I try the findsmb command, it does not show up.

Does anyone have any ideas?  The error message seems common, but I have been trying solutions all day, and I am still not getting a connection.

Any assistance would be greatly appreciated.  Thank you in advance.

-Eleos

---

### Post by Morbius1 on 2011-08-14
And I betcha if you ran the following command you do not get the error:
```
nautilus smb://NOVA_MORAI
```You may have to play with the capitalization on that. If it doesn't work try:
```
nautilus smb://nova_morai
```Worst case access it by ip address:
```
nautilus smb://192.168.1.255
```
Or whatever the ip address is.

---

### Post by NomadicExistance on 2011-08-16
I'm seeing something similar... Got Natty, and a Buffalo Link Station Live on my home network... 

Within the GUI... Nautilus (I'm more familiar with explorer.. :)), under Network, I can see all of the shared folders on the NAS. However, if I try to access one of these shared folders by simply double clicking on the icon, i get the error "Unable to mount location - Failed to retrieve share list from server". 

Till yesterday, I could access these shares through Nautilus just fine. Not sure what changed. 

If I run *nautilus smb://<nas_name>*, it opens up just fine.. 

Any ideas?

---

### Post by Morbius1 on 2011-08-16
As for the cause, that's part of an ongoing discussion. As for "any ideas", yes I have one: Don't browse to the nas.

Once you do a "*nautilus smb://<nas_name>" *bookmark it: Bookmark > Add Bookmark. 

It will show up as "Windows shares on nas_name" ( which you can rename if you like ) on the left panel of Nautilus. Not unlike a "mapped drive" in explorer on Windows.

---

### Post by NomadicExistance on 2011-08-16
I can live with that.. :) 

For what I can see, this seems to be something within Nautilus. From within Amorak, I don't see any issues. It's picking up my music files just fine. 

Thanks Morbius.

---

### Post by ElderSyrinx on 2012-02-13
I am getting this same error message.  I am attempting to connect to a windows 7 workgroup with a password.  In my files under "network" I have a folder called "Windows Network" which is where I'm receiving this error.  This is confusing on several accounts, first this is a named workgroup and the name doesn't show and second I can not find anywhere to enter in the workgroup password.  I have been trying to connect with Gadmin-Samba where I have entered in under "Workgroup or domain name:" the proper workgroup name but again I see no place for a password.

---

### Post by rodheal on 2012-02-21
Hi I'm using Ubuntu 11.10 32bit on a Samsung NP-Q210 laptop and had the  same problem. Being new to Ubuntu I thought I'd try installing "Samba"  from the Ubuntu software centre, when I looked there was also  "Smb4k"  so I installed that as well. Then when I tried to connect to a windows  network through the "browse network" tab in my "Home Folder" my NAS box had appeared.

I didn't get a chance to try and of the tips but installing those two programs did the trick.

---

### Post by ianchai on 2012-02-22
I found a solution that works for me -- it's a bug in the /etc/samba/smb.conf file in Ubuntu 11.10

Need to add "name resolve order = bcast host" to that file and restart Samba.

I found the solution at [http://askubuntu.com/questions/74789/failed-to-retrieve-share-list-from-server-error-when-browsing-a-share-with-nau](http://askubuntu.com/questions/74789/failed-to-retrieve-share-list-from-server-error-when-browsing-a-share-with-nau)

---

### Post by capscrew on 2012-02-22
> **ianchai said:**
> I found a solution that works for me -- it's a bug in the /etc/samba/smb.conf file in Ubuntu 11.10

Need to add "name resolve order = bcast host" to that file and restart Samba.

I found the solution at [http://askubuntu.com/questions/74789/failed-to-retrieve-share-list-from-server-error-when-browsing-a-share-with-nau](http://askubuntu.com/questions/74789/failed-to-retrieve-share-list-from-server-error-when-browsing-a-share-with-nau)

It's NOT a "bug".  You can configure the method the Samba "node" responds on the network.  Using bcast first makes this a B-node (it broadcasts its IP address and netbios name).

---

