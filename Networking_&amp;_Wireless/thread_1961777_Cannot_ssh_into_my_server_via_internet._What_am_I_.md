---
title: "Cannot ssh into my server via internet. What am I missing?"
date: 2012-04-19
forum: Networking &amp; Wireless
---

### Post by russki_drewski on 2012-04-19
So I've been experimenting with ssh-server on an old computer I've got. Following the [ubuntu ssh configuration wiki]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring"), I can ssh into it just fine via my local wlan, but when I try to use my public ip address I just get a timeout error and it seems that the request is not making it through at all to my server from what I can see in the ssh log file. I have ssh-server configured to work on an arbitrary port and I'm specifying exactly that port when trying to log in.

I'm pretty sure the source of the problem is the port forwarding on my router, but I'm almost certain I've set it up correctly. I've attached some pictures to show what I'm doing to setup the port forwarding. Can someone tell me if there is something fundamental that I am missing?

I realize that trying to ssh into a server via the internet from the same lan can sometimes upset the router, but I've been trying to ssh in via the wireless hotspot on my phone. I can ssh into my university account, but when I try to ssh into my home server it just times out. To find my public ip address I just googled "what's my ip address" and used the address it showed me.

Can anyone point to me where I am mistaken? Is there a problem some where that I'm not getting? Searching google and the forums I have found others with similar problems, but the fixes included something that I have done already. Anyone???

Thanks for the help!

---

### Post by Ms. Daisy on 2012-04-19
I had a very similar problem recently.  see this post in particular

[http://ubuntuforums.org/showpost.php?p=11817884&postcount=3](http://ubuntuforums.org/showpost.php?p=11817884&postcount=3)

for a link to a website that has explicit directions on port forwarding for like every router ever made.

---

### Post by russki_drewski on 2012-04-19
I've been to that post before. I've done everything on it and I still can't ssh into my computer via my public ip.

I guess, I can try again. Just after a while of doing the same thing without results, it seems rather pointless.

Could this be a problem with a firewall? or maybe my isp?

---

### Post by for.i.am.root on 2012-04-19
It's not your ISP and it's not your firewall.

It's your LAN. You need to set up a static address for the computer you want to SSH into. Your router will have that capability.

After you have a static address you need to set up the port forward.

Then try to connect using username@ipaddress : port (silly thing thought I wanted a Smiley :-D)
No spaces in between the host and port, by the way.

Ms. Daisy is 1000% right. Just takes time to figure everything out.

---

### Post by azmyth on 2012-04-19
Did you edit the ssh config file to listen on your port since you changed the default port?

---

### Post by for.i.am.root on 2012-04-20
The one thing I don't like about my tablet is that it is a pain to view images like the screenshots above. Hence why I didn't click on them to view them and why I just spent the last 2 minutes trying to figure out how you determined that he changed the default port.

*doh*

---

### Post by ammofreak on 2012-04-20
Hi ):P: can you ping your router via phone hotspot?

---

### Post by newbie-user on 2012-04-20
I suggest switching back to the default ssh port 22 and trying again. Once you get it working with the default port, then you can change the port to 12345.

---

### Post by Ms. Daisy on 2012-04-20
> **newbie-user said:**
> I suggest switching back to the default ssh port 22 and trying again. Once you get it working with the default port, then you can change the port to 12345.
This isn't a bad idea.

Did you try the debugging line from the wiki ```
ssh -v localhost
``` Do this on the server itself.

---

### Post by russki_drewski on 2012-04-20
@for.i.am.root
I have a static ip setup on my router for my server. It looks at the mac address of my server and assigns it the same local ip address.

@asmyth
I can ping my public ip and it is able to send and receive data apparently.

@Ms. Daisy
On my server I can run 'ssh -v localhost' and it lets me ssh into the host from the host. But what do I do from here? It worked. That's all I know from doing this.

@all
I've reassigned the the ssh port in sshd_config to 22 and set the port forward on my router to port 22. I restarted the ssh server after doing this. I rebooted my router and double checked the port forwarding and static ip address of the server to make sure nothing changed. I checked my public ip to make sure it didn't change after rebooting the router.

After doing the above I can still login on the local network, but trying to log-in via the internet still gives a time out error.

:confused: What's missing?

@edit
Is my router having problems/malfunctioning? I just bought it a couple of months ago and paid extra to get one that's a bit nicer. That's going to be a pain if that's the case.

---

### Post by Ms. Daisy on 2012-04-20
My first thought is to make sure you have configured the port forwarding on the router exactly as shown in that link sejeisensei gave me in the other thread.  I didn't have to configure the beginning and ending port, so I'm not sure what's needed there.
 
Sorry, I'm pretty new to ssh so I can't give you a simple solution, I can just suggest some points to research if no one else gives you solutions. It may help to look at your auth logs on the server to see what's going on when you try to ssh from an external IP.  Set the log level to high if it's not showing much.  If you're not showing anything happening on the server then you know the problem is with the router.  You can also look at the router logs, you can probably set the level of logging- that may indicate where the failure is.

---

### Post by azmyth on 2012-04-20
If you're trying to access your LAN over the WAN while you're on your LAN it will not work. You will have to try a different hotspot.

---

