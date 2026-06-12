---
title: "A little confused with samba network behavior."
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by lannatwin on 2009-05-09
I'm a bit of a noob, so please be gentle.

I'm networking two machines running 8.10 with samba.  Netgear wireless router.

Machine 1 is on a wired connection.  Machine 2 is wireless.

On machine 1 I can go to places/network and I see machine 2.

On machine 2 to see machine 1 I must go to places/network/windows network/workgroup/

Is this normal behaviour? In the past, I thought I could just go to places/network to see either machine.

I haven't made any modifications on either machine- other than setting up a share on the public folders.

Thank you for any assistance / explanation.

---

### Post by lannatwin on 2009-05-11
What, nobody has any thoughts on this?  I thought surely there would be some networking wizards out there that could tell me if something is amiss here.:confused:

---

### Post by klein de usa on 2009-05-13
hi
im no networking wizard, but i believe the easiest way is to set up static ip's on both computers. ubuntu 8.10 has a problem with static ip addressing you can google out ubuntu 8.10 static ip and you should be able to find a good guide. 


creating a share in nautilus works well for me 
did you set a samba password ?

open up network places and in the adress bar at the top put smb://static ip addres/folder you shared 
 
when it asks for a password put your user password in

---

### Post by theozzlives on 2009-05-13
edit your smb.conf as root and make sure the workgroup=WORKGROUP line is the same on both computers

---

### Post by klein de usa on 2009-05-13
hi
this is the guide i used to change ubuntu 8.10 to a static ip [http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html]("http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html")

---

### Post by lannatwin on 2009-05-14
Thanks everybody.  I'll gave that a try.

---

