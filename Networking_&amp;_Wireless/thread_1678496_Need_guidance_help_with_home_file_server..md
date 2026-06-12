---
title: "Need guidance help with home file server."
date: 2011-01-30
forum: Networking &amp; Wireless
---

### Post by TheBigDogTCS on 2011-01-30
Hello all and thank you in advance.

I've been a Xubuntu/Ubuntu/Lubuntu hobby user for about 18 months now. I started using Linux as a way to revive older computers provide a backup and expand my knowledge of computing. The command line was something new to me but as long as I can find detailed directions on how to do what I want I can usually manage. I set up a Samba server for my home shared network and now I'd like to make the shared drives of that server accessible from outside my network. Via ssh or ftp or some program of the like.  I'd like to have it user name and password protected. Configurable user rights would be nice. (read/write/delete/ect) As well as novice user friendly.  My end goal is a server with read/write capability that I will be able to access from work or a friends house or anywhere with an Internet connection and my laptop. I understand about port forwarding and have done so with my home network behind an AT&T U-verse router/modem. I've researched openssh and some ftp setups but they seem like they can be difficult.

Now for the questions. Is this task something that can be accomplished without a degree in computer networking? Is there a program(s) that would make this a simpler task? Is this more complex than its worth? EDIT: How would I go about setting up such a thing?

---

### Post by SaintDanBert on 2011-01-30
**Short answer:**  Yes, you can accomplish these requirements.

**Caveats:** The devil lies in at least two sets of details. (1) Networking and _security_, and (2) file sharing and _security_.

Inside your home, it is straight forward to have file space and other resources on a server box available to workstations that are wire or wireless connected with that server. Linux can share with Linux in several ways with little or no troubles. SAMBA implies Windows(tm) networking that can present some interesting challenges.

When you want to access all of this sharing from anywhere out on the public internet, there are some networking details to resolve. Foremost is the issue of how will you find your resources? Services like DynDNS might be useful. YOU will behave when connecting with your network. Can we say the same thing about others who might connect? 

With that in mind, I would encourage deployment of a second server.  You connect with that server from the public internet and that server connects with your home network file server. This second server is sometimes known as a demilitarized zone or DMZ. If this server gets slimed, only the DMZ gets dirty.

Bonne chance,
~~~ 0;-Dan

---

### Post by TheBigDogTCS on 2011-01-30
Saint, I see your point about the DMZ and security. And you are correct there are Windows boxes on my network. Whats more important that I failed to ask the first time was how would I go about accomplishing my goal? And couldn't the security issues be resolved by requiring a login to establish a connection? Thanks.

---

### Post by drdos2006 on 2011-01-30
Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by SaintDanBert on 2011-01-30
> **TheBigDogTCS said:**
> 
...
And couldn't the security issues be resolved by requiring a login to establish a connection? Thanks.

The other posting of a Linux Server HOWTO seems valuable for that piece of your project. In my mind a "server" is some computer and software available by data communications that takes requests, does work, and returns results. I have never installed a "server edition" of linux. Instead, I simply added the various services I wanted to a "desktop edition". If needed, I removed "desktop parts" (like games) to simplify and lighten the resource drain on which box I was using. I used a VPN so that I could accomplish "server" admin without the need for a display and keyboard on the chosen box. (Those boxes usually got keys and displays anyway.)

Inside your home LAN, you can be more trusting of individual workstations and their respective users.

I'd use some sort of virtual private network (VPN) between off-world workstations and your DMZ server. Your requirements will dictate whether you want or need a public web server or similar mundane accesss from off-world.

Your DMZ server would then make at least two determinations.
1.  What is a VPN connected session permitted to accomplish on the DMZ server itself?
2.  What can a DMZ server session access throughout the home LAN?

> **TheBigDogTCS said:**
> 
...
Whats more important that I failed to ask the first time was how would I go about accomplishing my goal?
...


Gather some parts and "frankenstein" the box you want to use for the internal server.  [BTW -- this is formally known as an "intra-net"]

Load your favorite distro and make it talk with the public internet.

Add and remove packages so that your "server" has the software parts
to accomplish its desired mission. [highlight]Important:[/highlight] Do these a very few at the time so that it is easy to discover the source of troubles when they happen.

All of the above can happen with everything wire connected to an ethernet switch that gets hung from your cable modem or similar.
If your wireless access point has wire ports too, that does the trick.

I would choose a separate IP-address family [subnet] for your in-house LAN and a different subnet for the DMZ. Hang a second wireless access point (with wire ports) configured with this off-world subnet. 

Frankenstein a second "server" box.  It can be very much smaller because it will store very little. (Could even be an olde laptop...)
Connect it to the DMZ access point. Loading your chosen VPN will be high on the list of DMZ packages.

Now you have a way to work with connections from inside and outside without leaving your comfy chair.

As you add packages, configure so that your in-house workstations can access and use the various services you deploy.  Then change to use the DMZ connections and configure so that you can access what you wish and cannot access what you want locked up.

In the "cute trick" department, if you set your intra-net server to use VPN for remote administration, one can VPN from off-world into the DMZ server and then VPN again from the DMZ server to the intra-net server. Viola!  off-world access to the in-house server. Remember to get the security done well enough or you have a trap door to serious trouble.
Some slime merchant will find your connections if you don't use good locks.

More later if needed,
~~~ 0;-Dan

---

### Post by TheBigDogTCS on 2011-02-02
After careful consideration and a great deal of research I have decided that having my own web accessable file server is not worth the security risk or hassle. Thank you for your help.

---

### Post by SaintDanBert on 2011-02-03
I reached the same conclusion ...
I did implement an in-home intra-net server.
I use Dropbox to put files out where I can reach them from anywhere
using a browser or Dropbox client.

(grinning wickedly) I have some ideas left over from a past life for dealing with files I want but which are not available thru Dropbox ... yet. (Bwa-ha-ha).

Cheers,
~~~ 0;-Dan

---

### Post by dmizer on 2011-02-04
If you ever decide to try this again, I suggest that you look into OpenVPN as a possible secure way of remotely accessing LAN resources that would otherwise be insecure if left in the DMZ.

There are a number of router distributions that are purpose built for handling WAN queries and are fairly easy to configure if you know a little bit about networking. Here are a few that may interest you:

ClearOS -> [http://www.clearfoundation.com/Software/overview.html](http://www.clearfoundation.com/Software/overview.html)
Zentyal (runs on Ubuntu) -> [http://www.zentyal.org/](http://www.zentyal.org/)
Untangle -> [http://www.untangle.com/Lite-Package](http://www.untangle.com/Lite-Package)

There are more, but I have used all of the above systems to great success. I currently host my own email, VPN, DNS, DHCP, and file server on ClearOS.

---

