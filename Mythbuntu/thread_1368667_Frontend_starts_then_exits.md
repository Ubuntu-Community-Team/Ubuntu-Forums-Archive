---
title: "Frontend starts then exits"
date: 2009-12-30
forum: Mythbuntu
---

### Post by mediaslayer on 2009-12-30
I built a backend that appears to be working fine, so I decided to try a frontend using the live Mythbuntu disc and running the frontend from the disc.
 
Everything booted fine and it appeared to connect to my backend database.  When first started it asked me to select a server (I have two unrelated backends, one of them is not used), the screen went blank and then brought me back to Xfce.  Tried again with the same results.  I don't know what else I should try.
 
At one point it did ask for me to set the Security Pin on the backend, which I did and set it to 0000. 
 
I'm not a Ubuntu (or Linux) expert, but I do know how to get around (and still learning!). so please consider this in your reply.
 
Thanks to anyone that can help.

---

### Post by SiHa on 2009-12-31
In your backend setup, you need the physical IP of the machine entered in the 'general' page. IIRC there are two spaces, one for the IP of that machine, and one for the IP of the master backend server, both should normally be the same. The default for these is 'localhost' - 127.0.0.1, which is fine if you have BE and FE on the same box.

You will also have to change this in the FE that exists on the BE machine.

To get the IP address of the BE machine, in a terminal window,  type ```
ifconfig
```
```
mythbox@mythbox-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:52:d0:dd  
          inet addr:**[COLOR="Red"]192.255.100.100[/COLOR]**  Bcast:192.255.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe52:d0f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:117991464 errors:0 dropped:0 overruns:0 frame:0
          TX packets:199103032 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2654882092 (2.6 GB)  TX bytes:457268123 (457.2 MB)
          Interrupt:23 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:143905 errors:0 dropped:0 overruns:0 frame:0
          TX packets:143905 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:52080473 (52.0 MB)  TX bytes:52080473 (52.0 MB)
```

 You want the one in the first section, eth0.

'0000' for the PIN is correct as far as I remember, it means that there is no PIN, so don't enter one in the frontend.

Another thing to note is that if you are connecting via a router that uses DHCP, the IP address is likely to change ocasionally. You would be advised to set a static IP for the backend. I'm not a networking expert, but there's quite a bit about it on these forums (fora?).

HTH,

Simon

---

### Post by mediaslayer on 2009-12-31
> **SiHa said:**
> In your backend setup, you need the physical IP of the machine entered in the 'general' page.
I did put my static IP in these fields on the backend.  I forgot to mention that in the original post

> **SiHa said:**
> Another thing to note is that if you are connecting via a router that uses DHCP, the IP address is likely to change occasionally. You would be advised to set a static IP for the backend.

My IP address is assigned by the DHCP server, but I have a static mapping so it always gets the same IP.

Is there a log on the frontend somewhere that might help troubleshoot the problem?

Thanks.

---

### Post by azmyth on 2009-12-31
I suspect the remote computer doesn't have permission to access the db. On the remote FE, stop the FE open up a terminal and start it manually to see what the log says.

$mythfrontend
or
$mythfrontend.real

---

### Post by larsolav on 2009-12-31
Are the frontend and the backend machines set up to the same location? When I first installed my new FE/BE machine I selected Chicago as the location as the location map didn't have a dot for Houston (or any other Texas city as I can remember). When I set up a new FE machine I set it to another central time zone city (not Chicago) and the FE machine would exit FE like in your case. But once I got both machines set to Chicago the problem went away. Hope this is what is causing your problem as well as it is an easy fix. Otherwise, I have no clue!

---

### Post by mediaslayer on 2009-12-31
> **larsolav said:**
> Are the frontend and the backend machines set up to the same location? When I first installed my new FE/BE machine I selected Chicago as the location as the location map didn't have a dot for Houston (or any other Texas city as I can remember). When I set up a new FE machine I set it to another central time zone city (not Chicago) and the FE machine would exit FE like in your case. But once I got both machines set to Chicago the problem went away. Hope this is what is causing your problem as well as it is an easy fix. Otherwise, I have no clue!

Since I'm using the Live disk, I never select a Timezone.  I do know my backend is in the my timezone (EST).  Where would I change the timezone on the Live disk?

---

### Post by larsolav on 2009-12-31
Hmmmm. Is there a clock on the upper right corner of the desktop? I think if you right click it you can set the time zone / location. Also, maybe there is a settings menu or something like that on the upper bar? Not only does the time zone need to be the same on the FE and BE, but also the actual selected city for some reason.

---

