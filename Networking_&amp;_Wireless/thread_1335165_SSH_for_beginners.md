---
title: "SSH for beginners"
date: 2009-11-23
forum: Networking &amp; Wireless
---

### Post by weks87 on 2009-11-23
SSH for beginners, like me.

Alright so I've browsed a lot of previous threads about SSH problems but the solutions seem to vary so I'll post a open question here.

Background:
My friend and I have set up a Ubuntu 9.10 Server on a location that we both have very limited local access to, and we would of course like to manage the server remotely from where we usually are.

Now the server is connected directly to a ADSL modem and gets a dynamic IP from the ISPs DHCP server.

Well, we built a... crude method of getting the IP form the server, where the server just mails us with its ifconfig output. We thought that it was enough that we knew the public IP of the server, but apparently not. Now it worked when we used putty to access the server localy using the public dynamic IP, but when we returned home we couldn't, even though we can ping the IP successfully. Now we didn't do any port forwarding on the modem, so I'm guessing that's the reason it won't work remotely.

But the question is; what else might we need to do the next time we have local access to the server? Do we need to edit any configs in openSSH? The server firewall and so on? I'm also new to port forwarding so any tips on that subject is welcomed as well.

It can sometimes take weeks in between times we have local access to the server and we can't test if it works remotely while we are there so we need to know everything we must/might need to do for the next time we are there.

many thanks in advance,
WEKS

PS.

We have the same problem with FTP, though that is of less importance right now.

---

### Post by yc2 on 2009-11-23
I only used SSH for a while, I am not an expert.

Just a few thoughts.

You have no possibility to assign a dynamic DNS service and address the server with a domain name. (The server runs a script on time schedule and sends information to the DNS if IP has changed.)

I don't think you need to forward ports? You have no router/local network?

Since it is your first bean I wish to welome you to ubuntuforums, even though I also belong to the newbies :)

---

### Post by prshah on 2009-11-23
> **weks87 said:**
> set up a Ubuntu 9.10 Server on a location that we both have very limited local access to

gets a dynamic IP from the ISPs DHCP server.

crude method of getting the IP form the server

Now we didn't do any port forwarding on the modem, so I'm guessing that's the reason it won't work remotely.

But the question is; what else might we need to do the next time we have local access to the server? 

We have the same problem with FTP

Yes, you need to perform port forwarding on the ADSL router. For more detailed steps, please post your ADSL router model/make here, or use that information to find the correct steps from [www.portforward.com](www.portforward.com).

You also need to allow the ports for SSH and FTP (22 and 21 by default) on your server's firewall, if you have activated it. On Ubuntu, the usual firewall settings utility is ufw. You can allow the ports (for example) with the command```
sudo ufw allow 22
sudo ufw allow 21
```

Once you have SSH access, you can change any settings remotely in the future.

One important point: Most routers have SSH and (T)FTP servers built into them; if you are using the default ports for SSH and FTP, aside from forwarding them properly, you also have to disable WAN-side (Internet-side) access to the ROUTER's SSH and FTP services. When you do this however, you can no longer remotely change settings on the modem; you will have to ssh to your server, and from there, ssh (locally) to your router. If the router's settings are shot, you will not be able to reach your server, and hence you will not be able to remotely fix the router. Do I make sense?

If you use non-standard ports, this is not an issue.

Most router's have a built in method to use (for example) a dynamic ip forwarding service such as dyndns.org. Or, ubuntu comes with a client that will work with dyndns.org. Please visit the website and setup a free account; it will be far more elegant than your method.

---

### Post by weks87 on 2009-11-24
EDIT2:

Got it to work, it took some explaining to a person over IM to a non-tech savy person but we got it.

Apparently the default 22 port didn't work, so changing it and using that sudo ufw allow #port_number# was all it took.

---

### Post by yc2 on 2009-11-24
Great! You will not be limited by when you have physical access to the server any more. Just hard work all the time now ;)

---

