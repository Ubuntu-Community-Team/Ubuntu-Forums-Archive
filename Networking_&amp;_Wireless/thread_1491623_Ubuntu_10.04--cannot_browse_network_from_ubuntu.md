---
title: "Ubuntu 10.04--cannot browse network from ubuntu"
date: 2010-05-23
forum: Networking &amp; Wireless
---

### Post by dnpate on 2010-05-23
I cannot browse the network from Ubuntu, but I can see the ubuntu machines from the windows including file and printing.  
Nautilus gives the following error:
      Could not display "network:///".
      Nautilus cannot handle "network" locations.

Workgroup names all set the same
Sharing allowed on all machines

I have read all of the postings on this I think and have not been able to implement a solution.
TX for help

---

### Post by klein de usa on 2010-05-23
hi 
i have some what the same problem i have 5 ubuntu 8.04 computers that have shearing working. when i add in the 10.04 machine and go to places> network> it only gives me an icon for windows network if i click on that it gives me an icon for workgroup and if i click on that it tells me it failed to retrieve share list from server BUT if i go to any of my 8.04 computers i can browse and open the shared file on the 10.04 computer copy and past thing in and out of it. win7 can see the 10.04 computer too and connect to it the same as the 8.04's do i guess the 10.04 has a problem with the computer that is acting as the server for samba

---

### Post by klein de usa on 2010-05-23
i may have fixed my problem, the computer that was acting as the samba server i rebooted and that made samba use another computer,  now it is working with the exception of the original samba computer samba was using i might have to reinstall net working.

---

### Post by klein de usa on 2010-05-24
dnpate

i struggled with this very same thing a while back until i got a new router and my new router also does lan dns, or it acts as an dns server you could say, an dns server puts the ip of each computer on your lan together with each computers name. so when you go to places > network each computer should show up by it's name in there. 

this is my prompt in my terminal xxxxx@amd64x2:~$ so amd64x2 is my computer name and my router links that name with my ip address weather it is static or dhcp assigned, 
i beleive you can also add right under your workgroup = workgroup name in smb.conf    netbios=amd64x2 then install winbinds but i could never get that to work 


in ubuntu 10.04 i changed my smb.conf file too, there was one line different between 10.04 and 8.04 smb.conf. i uncommented > socket options = TCP_NODELAY <      

if i'm wrong please correct me

---

### Post by beumont2 on 2010-05-24
I have the same problem. I used before linux mint 8 and than moved to win7 for a while everything was working on my network.

I have a server setup with fedora and a password protected samba share.
I cannot access it from my ubuntu system 10.04. I going on to network and then he asks about the password which I am normaly typing in win7 and it doesnt work. Can anybody help me? 

If I am trying to mount the share from the cli with mount -t cifs it works but only as root. This is uselles for me, I will access these shares as normal user.

---

### Post by gpalarea on 2010-06-01
I have been having issues with mounting windows shares since 9.04 (and now in 10.04 also), and every time it has been solved by adding the following lines to /etc/samba/smb.conf, after the line "server string = %h server (Samba, Ubuntu)":

   client lanman auth=yes
   client ntlmv2 auth=no

It has worked for me. It is not my solution, I found it in some forum quite a while ago, I don't remember where...

Good luck!

---

### Post by mag9lubuskie on 2011-03-10
It didnt worked for me. Instead of it I swiched off WINS support and changed naming service order to as figured below


```
wins support = no
name resolve order = wins bcast lmhosts host 

```

and THAT WORKS FOR ME!

---

