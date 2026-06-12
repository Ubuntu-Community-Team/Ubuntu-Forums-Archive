---
title: "Configuring Two NIC Cards"
date: 2012-10-11
forum: Networking &amp; Wireless
---

### Post by m4nd4r on 2012-10-11
[FONT=Impact]Hello..!


I need to configure 2 NIC cards on single Ubuntu machine.. I will have  to connect them to two different switches (in the same LAN) so as to  compare and analyze the traffics over each of them.. 

**What should I do in order to configure 2 NIC cards such that both of them should work at a time..?**[/FONT]  [FONT=Impact] 

I have tried it by editing- [/FONT] [FONT=Impact]***sudo vim /etc/network/interfaces***

and then- [/FONT] [FONT=Impact][B][I]sudo /etc/init.d/networking stop
          sudo /etc/init.d/networking start[/I][/B]

It then says- [/FONT] [FONT=Impact][I][B]networking stop/waiting
[/B][/I]But Internet connectivity was still retained with the earlier IP address..  New settings were not being used even after restarting the service..
On the very next system reboot, Internet connectivity was found to be lost..Need help in this concern.. :(:(:(:(:confused::confused::confused:[/FONT]

---

