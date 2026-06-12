---
title: "Trouble connecting"
date: 2010-10-01
forum: Networking &amp; Wireless
---

### Post by IuliusCezar on 2010-10-01
Hello.
I have an issue with Linux. I am a student and I live on  the college campus where we have a PPPoE connection.That is,you are  given a username and password,and the DHCP server assigns your IP and  DNS based on them.
I have had no trouble with the connection on the  campus,I use the "pppoeconf" command to configure my network card and it  works just fine.
However,since I am not very familiar with  networking in linux,I can't seem to get my internet connection to run at  home. I have a DSL modem which ,again,assigns the properties of the  connection through a DHCP server.The problem is it doesn't seem to work.
Now,I've  popped in a live cd and I'm running it off it and the connection works  just fine,that's how I've logged in to the forums.
So,as far as I can  tell,the problem is that linux tries to connect to the faculty network  but since it can't find it,the DSL connection at home doesn't work  either.
I chose the option to start the pppoe connection on boot so maybe that's the problem.

Is there a way to disable that connection and to allow my laptop to receive its parameters from my home connection?

I have tried shutting it down with "poff dsl-provider" but it won't work.

Thing  is,it works fine on Win7,and from the cd,which is how it should  work.Which means that a fresh install allows it to connect properly. (I  read that with a DHCP connection,all you do is plug in your ethernet  cable and it just works).

---

### Post by relay_man on 2010-10-02
Have you tried to configure a second connection using network manager? 
System>preferences>network connections should get you where you need to be to configure another connection that should work at your home. You may have to select/enable it manually (right click on the network icon in the upper panel) after boot, but mine works this way just fine.

---

