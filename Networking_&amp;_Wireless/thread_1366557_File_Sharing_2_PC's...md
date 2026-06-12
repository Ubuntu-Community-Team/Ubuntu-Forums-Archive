---
title: "File Sharing? 2 PC's.."
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by Pissed_off_Linux_n00b on 2009-12-28
hi,

im probably sure you guys see enough about this but i have to computer one running Windows Vista and one running Ubuntu 9.10 on a Netgear WGR614v9 router (both computers are wired to it).
im trying to figure out how to do this file share between the two computers just for music and pictures only how could i do this?

i also have my file share on Windows Vista enabled..

---

### Post by headvampyre@hotmail.co.uk on 2009-12-28
goto applications -> accessories -> terminal and type

sudo apt-get install samba smbclient smbfs

then when its installed close terminal and goto

/etc/samba/smb.conf

erase all the file and replace with this

[global]
    
    workgroup = put the name of your filesharing group here with no spaces
    netbios name = put the name you want your computer to appear as here
    server string = WorkGroup Controller
    local master = yes
    preferred master = yes
    os level = 20
    security = workgroup

[Music]
    
    path = put the path to your music folder here
    comment = Music On %L
    read only = no
    writeable = yes
    browseable = yes

[Photo's]
 
    path = path to your photo folder here
    comment = Photo's on %L
    read only = no
    writeable = yes
    browseable = yes
    printable = yes


that is all you need so save smb.conf

and on vista goto control panel -> system -> computer name -> change -> workgroup then type the name of your workgroup in there click ok the reboot.now when you have rebooted you want to add the drives to my computer so goto my computer -> tools -> map network drive and locate through my network places -> entire network -> workgroup name -> computer name -> folder to access then click ok.you can map as many drives as you want but make sure your connected to router and the computer with the shares is on

---

### Post by Pissed_off_Linux_n00b on 2009-12-28
> **headvampyre@hotmail.co.uk said:**
> goto applications -> accessories -> terminal and type

sudo apt-get install samba smbclient smbfs

then when its installed close terminal and goto

/etc/samba/smb.conf

erase all the file and replace with this

[global]
    
    workgroup = put the name of your filesharing group here with no spaces
    netbios name = put the name you want your computer to appear as here
    server string = WorkGroup Controller
    local master = yes
    preferred master = yes
    os level = 20
    security = workgroup

[Music]
    
    path = put the path to your music folder here
    comment = Music On %L
    read only = no
    writeable = yes
    browseable = yes

[Photo's]
 
    path = path to your photo folder here
    comment = Photo's on %L
    read only = no
    writeable = yes
    browseable = yes
    printable = yes


that is all you need so save smb.conf

and on vista goto control panel -> system -> computer name -> change -> workgroup then type the name of your workgroup in there click ok the reboot.now when you have rebooted you want to add the drives to my computer so goto my computer -> tools -> map network drive and locate through my network places -> entire network -> workgroup name -> computer name -> folder to access then click ok.you can map as many drives as you want but make sure your connected to router and the computer with the shares is on


ok i done everything so far but im stuck on saving the conf file its a read only file..

---

### Post by Pissed_off_Linux_n00b on 2009-12-28
> **Pissed_off_Linux_n00b said:**
> ok i done everything so far but im stuck on saving the conf file its a read only file..

never mind i got it thanks for all your help though much appreciated! :) 
i will respond back later on to let you know how things turn out..

---

### Post by lisati on 2009-12-28
> **Pissed_off_Linux_n00b said:**
> ok i done everything so far but im stuck on saving the conf file its a read only file..

You probably need "root" privileges to edit and save it, e.g. through the sudo command. Good to see that you've figured out saving it. Good luck, and all the best with your adventures!

---

### Post by Pissed_off_Linux_n00b on 2009-12-28
how do i find my music folder address? i thought it was \\J0SH-PC\Music but it "does not exist" on samba server..

---

### Post by dmizer on 2009-12-28
If you want to access files on Vista, please see the 6th link in my sig.

---

