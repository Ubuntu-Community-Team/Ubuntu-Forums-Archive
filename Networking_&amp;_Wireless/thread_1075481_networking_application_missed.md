---
title: "networking application missed"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by Dalal on 2009-02-20
hi everybody.

I wanted to know how to  connect to internet
 so i went to help ...
it said that i must go to 

System -> Administration -> Network 

and do some work 
but ;) i did not find the "network entry" in  the administration menu at all .
so what is the reason ...why it is not found 
and can I activate it 
or it is just an extra package and I must install it  

thanks for help ...

REGARDS.

---

### Post by superprash2003 on 2009-02-20
system->preferences->networking

---

### Post by Dalal on 2009-02-21
ok ..ok :D but u do not think that this  error is my problem  , Do u?
 it is  not found 

there are these entries:

>  network tools 
>  proxy configuration(as i remember because i am working with xp now ;) )
 any way  there is no "network" or "networking"  entry nor in preferences neither in administration 
so what is it ?

thanks for replying .

REGARDS.

---

### Post by hobo on 2009-02-21
What version of Ubuntu are you using? Do you have an application called WiCd
installed?

---

### Post by Dalal on 2009-02-23
hi
i have Ubuntu 8.10  intrepid ibex
kernel version if wanted is : 2.6.27-11-generic

and i think this application is not installed by default but i am not sure with  my system .
how to be sure about that and why u are asking about this application ,please explain to me .

REGARDS .

---

### Post by hobo on 2009-02-24
The ability to edit your Network Connections should be within a small icon on your top most panel. It looks like 2 displays with a red X in your case. If it is there, just right Click it and select ->Edit Connections

btw...Please go to the terminal and type "lspci" and paste the output to this thread

WiCd is another network manager that when installed deletes the default MN in Ubuntu. I have found Wicd to work much better for me.

---

### Post by ndoftaworld on 2009-02-25
I *somehow* removed the panel in Intreprid (Kubuntu) and now, I can add the panels' for FF, Terminal, etc. BUT can't find how to get Network Manager back...

So, can't connect to wifi :(

Any suggestions?

Thx 

Nd

---

### Post by hobo on 2009-02-25
So in Kubuntu you don't have a lower panel (Task Manager)? It can be hidden. ctrl-s will bring up the settings screen for TM. Also is there a small "icon" at the top right of your screen? If so right click and select "add widgets", then page down to "Task Manager" then select add. Also my NM shows up in what is called the **System Tray**, it is a added wiget also on The TM panel.

---

### Post by ndoftaworld on 2009-02-25
Thank for the reply. I donno how, but opened another panel on top of the bottom one :(

Closed that and all widgets are restored, even Network manager :)

Thx again!


Nd

---

### Post by Dalal on 2009-02-25
hi 
thnx for replying 
infact I have this icon at right up corner  but I only  can connect to the lan (i have  auto ethe connection )and i connect to internet  via lan 
but what if i want to connect with another  created connection(dialup modem as example ) ...how to do that if i do not have the apility to get to connection creation .
I am sorry if my words seem ;) but ....this is the situation

i am not sure if my modem is defined ...could this be the reason of  "network" entry  disappearing?




 BY THE WAY I NO MORE want  MODEM CONNECTION  SO NO PROBLEM TO ME IF NOT DEFINED ....:lolflag:

REGARDS .

---

