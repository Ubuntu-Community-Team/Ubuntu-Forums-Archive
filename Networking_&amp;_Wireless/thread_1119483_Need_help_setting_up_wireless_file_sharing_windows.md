---
title: "Need help setting up wireless file sharing windows-&gt;linux"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by Kronie on 2009-04-08
I bought Dell Mini 9, and since it only has 8 gigs of storage i would like to use my main computer to store my files. Main comp is running windows 7 build 7000
Dell Mini 9 is running ubuntu
i have a wireless router NetGear WNR834Bv2
i put sharing on the hard drive on my windows machine, and it shows up in the network settings
[IMG]http://img21.imageshack.us/img21/9599/capturevsg.png[/IMG]
but my ubuntu machine can't see those shares
[IMG]http://img219.imageshack.us/img219/5643/sharesubuntu.png[/IMG]
what do i need to do so that my dell mini would be able to access my windows shares wirelessly?

---

### Post by superprash2003 on 2009-04-08
try this. find out the ip address of  kronie-pc by going to the command prompt of windows and typing **ipconfig**.. and try accessing by typing smb://x.x.x.x where x.x.x.x is the ip address ..incase it doesnt work.. try refreshing the page .. or opening it 2 or 3 times.

---

### Post by Kronie on 2009-04-08
nope, still blank :(
just tried connecting computers through ethernet(straight connection. no router) still nothing..

---

### Post by Kronie on 2009-04-09
*Bump*
Anyone?


the thing is, windows can see and create\change files on ubuntu shares, but not the other way around.. which is kinda weird.

---

### Post by superprash2003 on 2009-04-09
is the ubuntu machine able to ping the windows machine via ip ?

---

### Post by Kronie on 2009-04-09
ubuntu has failed me yet again :(
no matter how hard i try to make a switch(even partitial), something will allways stop me..
installed windows 7 7077 on dell mini, networking works like a charm out of the box. 
and yes i could ping windows machine from ubuntu.

---

### Post by inobe on 2009-04-09
kronie i had no problem setting up samba on my network and many others.

[https://help.ubuntu.com/8.10/internet/C/networking-shares.html](https://help.ubuntu.com/8.10/internet/C/networking-shares.html)

that is the proper method, ubuntu documentation is really useful !

---

### Post by Kronie on 2009-04-26
> **inobe said:**
> kronie i had no problem setting up samba on my network and many others.

[https://help.ubuntu.com/8.10/internet/C/networking-shares.html](https://help.ubuntu.com/8.10/internet/C/networking-shares.html)

that is the proper method, ubuntu documentation is really useful !

yeah, it explains how to share files from ubuntu to windows.. i need it to be the other way around (linux netbook has only 8 gig SSD, so there isn't much to share)


edit:
i dont know if it didnt work before because i was on dell-customized (8.04) ubuntu, or because i did something wrong, but i decided to check out new version of ubuntu(and possibly give it another go) and so i installed it, installed smbfs(and made account for it), and ubuntu now sees windows shares :) 
the only problem is, whenever i mount a share it leaves a shortcut on a desktop, and it's a bit annoying.. is there any way to make ubuntu leave those shortcuts in some other place, or possibly have it NOT make those shortcuts at all?

---

