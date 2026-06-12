---
title: "samba4 and openldap domain controller"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by mraouf on 2009-09-30
[COLOR=black][FONT=Verdana]hi,[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I setup ubuntu doamin controller with **samba4 and openldap**. I can add and search my windows users and join them with romaing profile. [COLOR=red](ubuntu 9.04)[/COLOR][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]now I have some problems:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]**1.** I want to setting [COLOR=red]mandatory profile for my users[/COLOR], but when user login to domain controller I get an error as windows can't load roming profile ....[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I think that this refer to share directory permissions. [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]**2.** When I run "**[COLOR=red]getent passwd[/COLOR]**" though all I get are the[/FONT]
[FONT=Verdana]local users.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]how to can I change my share directory?[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]**3.** When I run **"[COLOR=red]chown root.Domain users /sharedir -R[/COLOR]"** , I get an error.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]would you please help me? [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]thanks.[/FONT][/COLOR]

---

### Post by whoop on 2009-11-24
Did you use any tutorial setting this up?

---

