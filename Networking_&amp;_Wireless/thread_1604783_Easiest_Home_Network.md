---
title: "Easiest Home Network"
date: 2010-10-24
forum: Networking &amp; Wireless
---

### Post by jereece on 2010-10-24
I now have 3 desktop computers hard wired into my wireless router and another desktop plus 2 laptops connecting wireless.  All are running Ubuntu 10.4 or 10.10.  I have not had the chance to get them all upgraded yet.  What is the easiest way to get these computers connected so that they can share files?  Do I have to set up a server or is there a simpler way? I just want to be able to copy a file from one computer to another.

Thanks,
Jim

---

### Post by perspectoff on 2010-10-24
They should all be visible in your File Manager (Nautilus or Dolphin).

However, I often find it easiest to make a link in Nautilus or Dolphin to the LAN IP address of the computers to with which I share files most frequently.

So, for example if my main desktop is shown by

 ifconfig

to be located at LAN IP address 192.168.0.44, then on another computer I add the network location [http://192.168.0.44](http://192.168.0.44) to Nautilus or Dolphin.

The avoids the time needed for a network search (by Nautilus or Dolphin) for all computers on the LAN.

(Of course, this will only work when the computer always has the same static LAN IP address.)

Otherwise, I have to allow the network to be searched.

Over the years, I have been happier having an independent large (500 Gb or 1 Tb) Network Attached Server (NAS) on the network as a central repository for files. They are inexpensive (around $100) these days, and with many computers on the network it allows me to avoid having to hunt around on multiple computers for the file I need (if the files are all clustered in this one central location in the first place).

Further, then the NAS can have a static LAN IP address and every computer can have a Nautilus (or Dolphin) link on it that points to the NAS.

This becomes especially useful when I centrally store videos or audio files that I may want to stream to any computer on the LAN -- I always know where the files are and streaming is facilitated to any of the computers with a minimum of effort.

---

### Post by jereece on 2010-10-24
I would prefer the other computers to be visible in Nautilus but they are not visible.  Do I have to do something for Nautilus to search for other computers?

---

### Post by Eredeath on 2010-11-20
> **jereece said:**
> I would prefer the other computers to be visible in Nautilus but they are not visible.  Do I have to do something for Nautilus to search for other computers?
I want to give this question a bump because I have the exact same one. Did you ever figure anything out jereece?

---

### Post by spiky001 on 2010-11-20
I use ssh I can then acsess them from nautilus

---

### Post by Eredeath on 2010-11-20
What do you mean by that? I can ssh to my computer via the console but how do i get it to show it's public folders in Nautilus?

---

### Post by spiky001 on 2010-11-20
You would need to set it up 1st then you can use nautilus

---

### Post by Eredeath on 2010-11-20
can u elaborate? What do i need to do to set it up?

---

### Post by spiky001 on 2010-11-20
follow this post [http://ubuntuforums.org/showthread.php?t=1626674](http://ubuntuforums.org/showthread.php?t=1626674)

---

### Post by jereece on 2010-11-27
> **spiky001 said:**
> follow this post [http://ubuntuforums.org/showthread.php?t=1626674](http://ubuntuforums.org/showthread.php?t=1626674)

I read through that post and it just ended in total frustration and no results. It appears that networking computers in Ubuntu 10.4 and after is extremely difficult. I tried everything myself and am now giving up.  I feel like I did way back when Windows for Work Groups first came out.  It just don't work.

---

### Post by Morbius1 on 2010-11-27
Have you tried approaching this as though you were on a WinXP machine?

Open Nautilus ( your Home folder )
Right click on a folder you own, like say ... Documents
Select "Sharing Options"
[COLOR=Blue]*You may be asked if you want to download something - you do.*[/COLOR]
Select "Share this folder", "Allow others to create and delete..", "Guest Access".
Select "Create Share"
It will ask you if you want it to modify permissions - you do.
Done

Go to one of your other machine and see if it can see documents share

[COLOR=Blue]**EDIT:**[/COLOR] I've got to shut down for the day so if you find it doesn't work then from your current machine run the following command to see if it can find it's own shares:
```
smbtree
```Based on my experiences when a problem does occur with this method a high percentage of them are caused by: 

- Firewalls
- Machine names longer than 15 characters long
- Linux file permissions
- Services running out of the correct order
- And in the case of wireless not having "bcast" first in the smb.conf file

All of which are easily fixed.

---

### Post by jereece on 2010-11-27
This is progress but not success.  I can see the other computer under Places / Network but when I click on it I get the error "Unable to Mount Location.  Failed to receive share list from server."  When I try smbtree, I get the following

> 	\\JIM-MEDIAPC    		jim-MediaPC server (Samba, Ubuntu)
cli_start_connection: failed to connect to JIM-MEDIAPC<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL


I rebooted hoping that would help, now I can't see the other computer at all.  However entering "smbtree" I still get the above error.

Any other suggestions?

Jim

---

### Post by Morbius1 on 2010-11-28
Make the following change to smb.conf on both the machine with the folder you are trying to share and the machine that's trying to connect to it:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the global section of smb.conf:
```
name resolve order = bcast host lmhosts wins
```Save the file and restart samba:
```
sudo service smbd restart
``````
sudo service nmbd restart
```If that doesn't do it then post the output of the following commands on the server to see if something is misconfigured with samba itself:
```
net usershare info --long
``````
testparm -s
```An don't forget to disable any firewalls you have enabled. If you didn't touch any firewalls then you should be fine.

---

