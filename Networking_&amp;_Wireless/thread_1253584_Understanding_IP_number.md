---
title: "Understanding IP number"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by Benzaa on 2009-08-30
Hi,

I was wondering if you could help me to understand something related to networking. I am new to this field, but I am very interested on learning more.

I just configured my computers to be connected using ssh inside a LAN. To connect to the computer, I got the IP number using ifconfig. This gave me a number such as 192.168.1.104. Searching for tutorials on the net, I found that this number (or similar) is common. So, inside a LAN this number can be repeated in several reds.

Now, I want to find a way to access my computer from the outside. I found the IP for the computer using a website. Let say the result is 123.456.789.123. Now, I notice that the same number is shared by all the computers inside the LAN. 

So, my question is, if I want to access my computer using ssh, is this command right?

ssh USERNAME@123.456.789.123

and if so, how does the router knows that I want to access the computer with IP 192.168.1.104 and not 192.168.1.105??

Any help will be appreciated.

---

### Post by Vaphell on 2009-08-30
your computers have private class addresses - 192.168.x.x
your router gets public class IP - 123.234.123.234 and acts as a middleman
all your computers are represented by it. It's like a building - whan you are on the street all you see is address but you have no idea how many apartments (computers) are inside.

If you want to log to one of the PCs from the outside you have to configure router to forward incoming ssh connection to a selected PC (something like telling the doorman to send all packages to flat nr 34)
There should be some forwarding configuration and you tell the router that from now on IP 192.168.1.105 gets all packets incoming from the outside at port 22.

---

### Post by Benzaa on 2009-08-30
Thanks Vaphell, that was very useful and clear. 

Now, how can I tell ssh that I want to route all incoming messages to a particular computer.

One thing that I forgot to mention is that I dont own the red. I am sharing the LAN with 4 more people. I am the only one using linux and the router is out of my reach (it has a password and I have no idea what it is)

With all of this considerations, is it still possible to access my computer from the outside??

---

### Post by DFlame on 2009-08-30
The above is pretty much the gist of it. You can use Portforward to find full instructions for setting this up [here](http://www.portforward.com/english/applications/port_forwarding/SSH/SSHindex.htm). Just select the model of your router and it'll tell you how to do it.

I must warn you however that forwarding port 22 is a potentially dangerous action if you do not properly secure your SSH server. Look [here](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring) for some tips on setting up good security. As an example, I use public/private key authentication instead of passwords, denyhosts to block unauthorised access attempts, a non-standard port (i.e. not port 22) and have disabled password logins altogether.

---

### Post by DFlame on 2009-08-30
If you can't access the router, you can't forward any port at all - 22 or otherwise. You will have to seek permission from the owner of the router before proceeding further.

---

### Post by Benzaa on 2009-08-30
> **DFlame said:**
> The above is pretty much the gist of it. You can use Portforward to find full instructions for setting this up [here](http://www.portforward.com/english/applications/port_forwarding/SSH/SSHindex.htm). Just select the model of your router and it'll tell you how to do it.

I must warn you however that forwarding port 22 is a potentially dangerous action if you do not properly secure your SSH server. Look [here](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring) for some tips on setting up good security. As an example, I use public/private key authentication instead of passwords, denyhosts to block unauthorised access attempts, a non-standard port (i.e. not port 22) and have disabled password logins altogether.

Thanks for the suggestion, I already followed all the suggestions for a secure ssh connection. I have my keys and I forbid all passwords connections. 

The only thing I couldnt do was to cancel root log in. When I type "PermitRootLogin no" in my /etc/ssh/ssh_config it tells me that the option is not valid.

I will try to get permission from the owner to get the password of the router and see if I can get it done. By the way, is it possible to use other port?? and if yes, how do you open it?

---

### Post by bukwirm on 2009-08-30
Yes, you can use a different port - just change the "Port 22" line /etc/ssh/sshd_config to "Port XXXX" (where XXXX is whatever port you want, 2222 is a good alternative SSH port), then forward that port from the router.

EDIT: Make sure you don't have a firewall on your computer blocking port XXXX, as well.

---

