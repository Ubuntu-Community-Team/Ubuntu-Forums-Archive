---
title: "Newbie Networking With Windows"
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by Nemisis_Ace on 2009-01-24
I have recently tried out ubuntu on my laptop 
and started using this for my main source of torrenting
however i would like to be able to access the torrented files via the network on my windows pc

I have turned on sharing for the specified folder and the only display im getting from windows networks is unkown device in network area

any suggestions would be a great help as i've probably not touched the obviouse ones.

---

### Post by AliTabuger7 on 2009-01-24
Firewall? If i remember my ports right, you need a couple somewhere around 450 and a couple somwhere near 7000 for SAMBA to work right.

Is it possible you are on a different "workgroup" (ex: MSHOME)?

What can you see from the ubuntu laptop and what can be seen from the windows computers?

What did you use to set up the sharing? The nautilus plugin or the system/administration tool?

---

### Post by Nemisis_Ace on 2009-01-25
windows firewall is turned off.
i believe they are on the same workgroup as windows machine can be seen from ubuntu machine and files can be read,its only at the windows end that cannot recognise the ubuntu machine .


i just used system admin to setup the network but will search for this nautilus program you spoke of.

---

### Post by AliTabuger7 on 2009-01-27
You say that your windows firewall is off, but Ubuntu may have a firewall. I don't believe that one is enabled by default though.

one thing to try might be typing the address of the ubuntu computer into your Windows File Explorer 

ex: 
\\192.168.1.100\
or
\\ubuntu-desktop\

it is possible that it is not visible, but is accessible.

---

