---
title: "print on remote Ubuntu machine from an Ubuntu machine"
date: 2006-07-03
forum: Networking &amp; Wireless
---

### Post by william_nbg on 2006-07-03
I've recently upgraded both office computer from Breezy to Dapper. In Breezy after following the 'how to' in the wiki we were able to print from Ubuntu client to Ubuntu server - no problem.

After Upgrading to Dapper though I haven't been able to figure it out.

I tried following this 'how to' for Dapper:

[http://easylinux.info/wiki/Ubuntu_dapper#How_to_print_on_remote_Ubuntu_machine_from_another_Ubuntu_machine]("http://http://easylinux.info/wiki/Ubuntu_dapper#How_to_print_on_remote_Ubuntu_machine_from_another_Ubuntu_machine")

But my cups won't run after adding ip to client.conf file

Anybody have any other idea?

---

### Post by william_nbg on 2006-07-03
Been playing around a bit more with the problem:

The nfs network between the two machines works fine.

The machine with printer, prints fine.

As soon as I tried to add "ServerName 192.168.0.23" to the 'client.conf' and restart cups (which shows no errors) but running lpq I get 'unable to connect'

If I take out the "ServerName" line from this file it seems to work fine, even 'lpq' looks as it should, though when I print, nothing happens - it doesn't send to server machine.

I think it may be a bug in cups??

---

### Post by william_nbg on 2006-07-03
Anyone here have an idea how to best configure the cups "ports.conf" in Dapper??

Just doing a little trouble shoting here.

---

### Post by Camino on 2006-07-04
you can try this one here:

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

works fine for me here...tutorial is for breezy but works also in dapper

Regards

---

### Post by william_nbg on 2006-07-04
[QUOTE=Camino]you can try this one here:

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

works fine for me here...tutorial is for breezy but works also in dapper

Regards[/QUOTE]

Thanks for your reply!

I found that yesterday, but isn't it written for 5.10 only, we're using 6.06. In Dapper there is a newer version of cups and I don't know if it's set up the same way as the old version???

Oh! you've answered that already - I'll give it a try.

---

### Post by william_nbg on 2006-07-12
Just in case anyone else has the same problem!

I found the solution, (at least it works for myself)

server pc (one with the printer plugged in)

I added to the 'port.conf' the ip address of the server pc

added 'Allow clientip' to location section in cupsd.conf

client pc (one without printer)

added 'ServerName serverip' to 'client.conf

Now it's all working as should and we're happy campers once again!:p

---

### Post by _logic on 2006-07-17
[FONT="Arial"][/FONT]did'nt worked here. it worked perfectly since hoary, breezy and dapper. problem rose only after CUPS was upgraded. Following your suggestion, lpstat -p had this error: lpstat: Unable to connect to server

so instead, i tried installing the server using the CLI command: lpadmin -p printer -E -v ipp://server/printers/printer

but returned

printer printer_name is idle.  enabled since Tuesday, 18 July, 2006 10:29:32 AM Network host 'server_ip' is busy; will retry in 30 seconds... 

any suggestions?

---

### Post by william_nbg on 2006-07-18
> **_logic said:**
> [FONT="Arial"][/FONT]did'nt worked here. it worked perfectly since hoary, breezy and dapper. problem rose only after CUPS was upgraded. Following your suggestion, lpstat -p had this error: lpstat: Unable to connect to server

so instead, i tried installing the server using the CLI command: lpadmin -p printer -E -v ipp://server/printers/printer

but returned

printer printer_name is idle.  enabled since Tuesday, 18 July, 2006 10:29:32 AM Network host 'server_ip' is busy; will retry in 30 seconds... 

any suggestions?

The config files for the new version of cups is split up a bit more than the last version.

On server pc (pc with printer), there is a file called port.conf: did you include the server pc ip address in it. This is what solved my problem.

Including the instructions at:

[http://easylinux.info/wiki/Ubuntu_dapper](http://easylinux.info/wiki/Ubuntu_dapper)

---

### Post by _logic on 2006-07-18
yup ive done that, in fact i did that when i moved from breezy to dapper and it worked perfectly, until the last CUPS upgrade.:-k 

all is working fine now. i replaced my server's cupsd.conf with the one in

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

and tweaking it to suit my setup. i know this is for breezy's but until i can find out where in the default cupsd.conf made my server nuts, i think im happy with this :cool:

---

### Post by william_nbg on 2006-07-19
Working is working.

The cups patches didn't seem to affect our system.

Our is also working well, though, on the new cups I have a little conflict with a remote printer and the cups-pdf printer??

---

### Post by _logic on 2006-07-19
printers here are all dot matrix. ill yet have to try printing pdf's on them

---

### Post by engineering.concepts on 2006-07-20
> **Camino said:**
> you can try this one here:

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

works fine for me here...tutorial is for breezy but works also in dapper

Regards

I have been getting fustrated and trying for over a week to network printers on 2 Ubuntu systems, after a simple copy and paste from the link above - everything works perfectly!!!:D 

THANKS!!!

---

### Post by dragon1964m on 2006-07-20
I wish I could get it to work. I cut and paste the instruction and I get :command not found. 
I just want to print from my docked laptop to my desktop. 3 days and no luck. Not with Samba, nor CUPS, nor http:/localhost:631. I'm using 6.06. Why is it so easy in Windows and such a MAJOR NIGHTMARE in Linux!!! ](*,)
Dell Inspiron 8100 using Ubuntu 6.06 > HP m7480n using Ubuntu 6.06 > HP Deskjet-940C.

---

### Post by william_nbg on 2006-07-20
> **dragon1964m said:**
> I wish I could get it to work. I cut and paste the instruction and I get :command not found. 
I just want to print from my docked laptop to my desktop. 3 days and no luck. Not with Samba, nor CUPS, nor http:/localhost:631. I'm using 6.06. Why is it so easy in Windows and such a MAJOR NIGHTMARE in Linux!!! ](*,)
Dell Inspiron 8100 using Ubuntu 6.06 > HP m7480n using Ubuntu 6.06 > HP Deskjet-940C.


Really, I always had trouble to get it to work in Windows.

Which ip/ip's are in the port.conf file of the server pc (pc with printer)?

---

### Post by solusrex on 2006-07-24
IGNORE!!!! FOUND IT!!!!!

> **william_nbg said:**
> Just in case anyone else has the same problem!

I found the solution, (at least it works for myself)

server pc (one with the printer plugged in)

I added to the 'port.conf' the ip address of the server pc

added 'Allow clientip' to location section in cupsd.conf

client pc (one without printer)

added 'ServerName serverip' to 'client.conf

Now it's all working as should and we're happy campers once again!:p

You lucky man. I cannot seem to find a port.conf file anywhere on my system. Any ideas?

---

### Post by solusrex on 2006-07-24
> **solusrex said:**
> IGNORE!!!! FOUND IT!!!!!



You lucky man. I cannot seem to find a port.conf file anywhere on my system. Any ideas?

I LOVE YOU ALL! I CAN PRINT FREELY NOW THANKS TO YOU FRICKIN' GENII!

---

### Post by william_nbg on 2006-07-24
> **solusrex said:**
> I LOVE YOU ALL! I CAN PRINT FREELY NOW THANKS TO YOU FRICKIN' GENII!

Glad I could help. Payback for all the help I've gotten on this here forum.

---

### Post by Shay Stephens on 2006-07-24
I have a USB printer connected to one dapper computer and I print to it with my dapper computer without problem.  The only thing I did was to follow this:
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

Even though it doesn't specifically mention dapper, the instructions still work.

---

### Post by simber on 2006-07-24
excuse me people for my ignorance :

many of you say that following this thread :

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

you have your printers working into a LAN

My question is that i´m not really sure which lines from the example cupsd.conf file do I have to edit. 

Specifically to this 3 lines that appear like 3 or 4 times

BrowseAddress 10.0.0.0/8   ---> I do not know if I have to change it.
BrowseAddress 172.16.0.0/12 ---->  I do not know if I have to change it.
BrowseAddress 192.168.0.0/16   --->  I know I have to change this according to my LAN



If somebody could be more specific I would really appreciate it.

Thanks in advance for your help

---

### Post by Shay Stephens on 2006-07-25
> **simber said:**
> excuse me people for my ignorance :

many of you say that following this thread :

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

you have your printers working into a LAN

My question is that i´m not really sure which lines from the example cupsd.conf file do I have to edit. 

Specifically to this 3 lines that appear like 3 or 4 times

BrowseAddress 10.0.0.0/8   ---> I do not know if I have to change it.
BrowseAddress 172.16.0.0/12 ---->  I do not know if I have to change it.
BrowseAddress 192.168.0.0/16   --->  I know I have to change this according to my LAN



If somebody could be more specific I would really appreciate it.

Thanks in advance for your help


My network is on the 192.168.x.x address space, so I deleted/commented out the other address space lines.  The printer is plugged into the other computer via USB and that computer is setup as the "print server" using the print server instructions.  My computer is setup as the "client machine" using the client machine instructions of that page you linked to.

---

### Post by william_nbg on 2006-07-25
> **simber said:**
> excuse me people for my ignorance :

many of you say that following this thread :

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

you have your printers working into a LAN

My question is that i´m not really sure which lines from the example cupsd.conf file do I have to edit. 

Specifically to this 3 lines that appear like 3 or 4 times

BrowseAddress 10.0.0.0/8   ---> I do not know if I have to change it.
BrowseAddress 172.16.0.0/12 ---->  I do not know if I have to change it.
BrowseAddress 192.168.0.0/16   --->  I know I have to change this according to my LAN



If somebody could be more specific I would really appreciate it.

Thanks in advance for your help


If your using Dapper, I would follow these instructions:

[http://easylinux.info/wiki/Ubuntu_dapper#How_to_print_on_remote_Ubuntu_machine_from_another_Ubuntu_machine](http://easylinux.info/wiki/Ubuntu_dapper#How_to_print_on_remote_Ubuntu_machine_from_another_Ubuntu_machine)

and ad the server ip address to the server port.conf file

---

