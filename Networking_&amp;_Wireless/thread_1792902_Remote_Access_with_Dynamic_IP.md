---
title: "Remote Access with Dynamic IP"
date: 2011-06-28
forum: Networking &amp; Wireless
---

### Post by emdiesse on 2011-06-28
Hi,

I am looking for a way to be able to access my PC from a remote place. The problem is that I have a dynamic IP. I have registered at dyndns and have found settings in the router to 'Activate Dynamic DNS' and then you supply your dyndns address, password and tell it to update the WAN ip address automatically. This works, however only internally and only to the router as opposed to my PC

The router is a ZyXEL P-660R-D1 if that helps at all.

I am not interestes in accessing the router to configure that remotely, only accessing my own PC.

Is this something I can accomplish with:
A ZyXEL P-660R-D1 router
A dynamic WAN IP address
A PC connected to the router
A static IP address for my PC

How can I go about configuring this. 
Thanks.

---

### Post by Zymonick on 2011-06-28
I am not entirely sure, if I understand the nature of your problem. 

My guess would be that you need to implement port forwards on your router towards the computer. There should be some settings on your router. So for example for SSH, simply tell your router to forward everything that arrives on port 22 to the static IP of your PC.

---

### Post by jcr1138 on 2011-06-28
My router allows me to set dynamic dns, but I prefer to update it my self with ipcheck. I just opened the ssh and web ports on the router.

ipcheck -l -i eth0 -r checkip.dyndns.org <my_dyndns_username> <dyndns_password> mymachine.dyndns.org

I also opened ssh and web ports with iptables in ubuntu. That's the way I can log in from another machine.

---

### Post by emdiesse on 2011-06-29
> **jcr1138 said:**
> My router allows me to set dynamic dns, but I prefer to update it my self with ipcheck. I just opened the ssh and web ports on the router.

ipcheck -l -i eth0 -r checkip.dyndns.org <my_dyndns_username> <dyndns_password> mymachine.dyndns.org

I also opened ssh and web ports with iptables in ubuntu. That's the way I can log in from another machine.

Would it be possible for me to run something from my pc behind the router that will allow me to visit mymachine.dyndns.org and access my machine completely bypassing the need to put dyndns on the router? Then running ipcheck routinely to keep dyndns up-to-date with my pc's ip?

---

### Post by SoFl W on 2011-06-29
I created scripts, to let me know of a computer's current IP address but they all require a server with a static IP as a central contact point.  I then look at the static server for the addresses of the other computers I want to contact.

I did come up with an idea yesterday, but have not worked on it and wont be able to.  Creating a private twitter account, and having the target computer send a tweet listing its current IP address.  "Computer1 123.45.123.56"   If you want to contact that computer remotely, you look at the tweets from the private account.  

Just throwing out ideas....
I don't know if something like GoogleDocs allows you to automate  uploading of files or not.  Are you familiar with any scripting  language?  You could grab the computers IP address and send a text  message to your phone every hour.

---

### Post by jcr1138 on 2011-06-29
I wrote a script with the ipcheck command like posted yesterday. Then I run that script in the crontab with this line:

```
# Update my dyndns hostname with dynamic ip address
*/30 9-23 * * * /root/dyndns/dyndnsupdate
```

That's the way I can log in with ssh from another pc, laptop over the world. If the router gets another ip address, the script will update the ip/hostname every 30 minutes between 9am and 11pm. You even set that cron as close as 10 minutes.

As I said yestarday, I didn't set anything about dynamic dns in the router.

---

