---
title: "Filemanger Hangs with fstab mount"
date: 2012-05-13
forum: Networking &amp; Wireless
---

### Post by alastairpjb on 2012-05-13
UBUNTU 10.04
 

 _Problem_
  (Filemanger hanging when NAS (network area storage) not turned on)


[U]My Networks
[/U]
1) Wireless BT Internet router,
2) Wireless Personal belkin router (This has Printer and NAS connected)
 3) Laptop Ubuntu 10.04


NB: Router are not connected to each other



The problem is caused when I swap between networks. When I am connected to the belkin router everything is fine. When I switch to the bt router internet works ok, I can open firefox, but whenever I try doing something that opens the file manger i.e access desktop files, folders, open a recently downloaded file; then it freezes up (not the whole computer just anything filemanger related).  When I swap back to the belkin router everything that froze opens very quickly all at once and works fine.

So I have tried swaping file manger to dolpin from nautilus. same problem occurs.(swaped back to nautilus now)

This leads me to think that the way I have mounted my nas (the only non gui(graphic user interface) setup on the computer) is causing the problem?


_*How I mounted the Nas*_
Getting the nas to mount was a total nightmare until I knew how, below are the steps I followed that worked.
 

 -Reinstall network manger (sorted nas automount at boot)
 -Place following code in etc/fstab.
  //192.168.2.69/megadrive /megadrive cifs username=XUSERNAMEX,password=XPASSWORDX,dir_mode=0777,file_mode=0666,nounix 0 0
 

 So the problem summarized;  
 

 my filemanger will only work properly when I am on the belkin wireless network where the nas is connected? If I switch the nas off the file manger hangs in the ways described above even if I am on the belkin network.
 

 I can see two possible solutions to this problem but no idea how to implement them.
 

 
[LIST=1]
[*]Create an unmount button/file
[*]Mount the drive in a different way     so the filemanger does not hang when I am not on my personal network.
[/LIST]
Any help would be greatly appreciated,

Thanx

---

### Post by steeldriver on 2012-05-13
I'm by no means an expert but I think it's generally a Bad Idea (TM) to use fstab for things that might not be there

I'm on 11.10 and that handles all the SAMBA stuff out of the box (I didn't realize that 10.xx does not) - public CIFS shares on my NAS show up automagically in Thunar, and if I want to access my private home share I just do

Go --> Open location --> smb://mynas/username/

and enter my credentials. (There's probably a way to cache those if that bugs you, or you could just make the share public - arguably no worse than exposing the credentials in fstab.)

Alternatively you could probably do what you want via autofs, I have done that for NFS automounting the same NAS (it exports as both CIFS and NFS)

---

