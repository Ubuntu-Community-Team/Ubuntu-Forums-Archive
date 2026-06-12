---
title: "How to connect local server from Internet"
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by mthalis on 2010-11-09
I have dynamic internet connection. In my network one machine run glassfish server in port 8080 (it IP address 192.168.1.3). If I type [http://192.168.1.3:8080/](http://192.168.1.3:8080/) that load my glassfish server page. What I want is using dynamic IP like  http://<DynamicIP>:8080/ load my glassfish server page. How can I do it ? My router is Dlink GLB-802C > I haven't good knowledge about network.

Thank you.

---

### Post by zarqoon on 2010-11-09
Check the configuration menu of your router. There should be something named virtual server or port forwarding. In that menu you can tell your router to forward a request to a specific port from the internet to an ip/port on your local network.
Just forward 8080 to 192.168.1.3:8080.
One thing though after you do that everybody that knows your ip or just connects randomly will be able to connect to your server. It might be better to use a port that is not that common. Anything between 10000 and 65535 will do. Securing the server itself with a password should also be done if you have not done so already.

---

### Post by mthalis on 2010-11-09
I tried it. But now working, below show images how i did it please correct if I'm wrong.
1st attachment show run locally server
2              show home interface in my router
3              show how i configure it
4              show what happen what but gave error message
5              show IP Filter Configuration


After configure reboot I commit and reboot it

please help me to solve this problem.

---

### Post by zarqoon on 2010-11-09
Check what other names are available in the if name field. Of your nat rule dialog. According to the user manual (Google search "glb802c + manual" if you do not have it) you should set this to your WAN device. eth-0 looks like a lan device to me.

Can you access the server from another computer on your local network? You could try doing that to rule out any configuration problems that would block non localhost access.

Are you connecting to your wan ip from your local network? I am not sure if nat rules work if your source is not actually outside your local network. They might but i never tried doing that.

---

