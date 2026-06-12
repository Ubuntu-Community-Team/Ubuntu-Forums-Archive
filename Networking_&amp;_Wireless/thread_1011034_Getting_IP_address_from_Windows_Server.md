---
title: "Getting IP address from Windows Server"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by RRCampbell12 on 2008-12-14
I'm a professional software developer, but I'm new to Linux.  I set up an Ubuntu 8.10 machine for my kids to let them access the Internet and for me to learn about Linux.  But I need some parental controls, so I'm using OpenDNS.  This works fine on another computer they use (WinXP) and it seemed like it would be easy in Ubuntu, but it's not.

What I want to accomplish is ...

1) Get the Ubuntu machine to secure its IP address from my Windows 2003 Small Business Server, which is the DHCP server for my network.

2) Use the OpenDNS servers for the DNS servers on the Ubuntu machine.

The problem right now seems to be that although I can go into Network Configuration and make what seem to be the necessary changes, the data is not saved.  I tried to access a normally restricted site and I get to it fine.  So I thought maybe a reboot was in order.  I did that, but when I go back to Network Configuration, my changes are gone.  I went through the manual instructions on the OpenDNS site and they didn't do the job either.  Any help would be appreciated.

---

### Post by jonobr on 2008-12-19
Im not familiar with using opendns, I know what it is but I have no need to use it mysefl but could you supply a bit more information.


Im guessing that your restricting access using opendns or something?
Are you configuring the actual sites to prevent access to?
If so you can remedy that by adding an entry for that site or address in your hosts file and map it to your localhost address, so when they try and go there they are prevented due to local mapping.

Im thinking if openDNS does the legwork, or identifying your prevented websites, then its failing for you, but again, Im not sure about opendns or hows its configured.

ME adding this post will surely bump it, and hopefully someone has a better idea

---

### Post by cb951303 on 2008-12-19
> **RRCampbell12 said:**
> 
The problem right now seems to be that although I can go into Network Configuration and make what seem to be the necessary changes, the data is not saved.  I tried to access a normally restricted site and I get to it fine.  So I thought maybe a reboot was in order.  I did that, but when I go back to Network Configuration, my changes are gone.  I went through the manual instructions on the OpenDNS site and they didn't do the job either.  Any help would be appreciated.

It's a known bug for 8.10, try searching. there already lots of threads and posted workarounds for this

---

### Post by MeURi on 2008-12-19
I have a similar problem too. With NetworkManager, I created my custom configuration called "Home", and I switch manually to it after every logon (once a day :-)). Maybe there's a way to make this automatic.

Or, you can change to Wicd, wchich is an alternative to NetworkManager and works, keeping you settings after a reboot. I went back to NetworkManger because... err... I can't remember :-P

Give Wicd a try ;-)

---

### Post by Insane_Homer on 2008-12-19
Instead of setting the DNS manually. Why not use the DHCP server to specify the DNS settings for the machines within the scope and assign them with the DHCP lease?

or Use the Windows 2003 Small Business Server as your DNS server and setup Open DNS as you DNS Forwarders.

Then you can lock down the network manager for the kids and they won't be able to change the DNS settings manually to bypass your controls.

---

### Post by doas777 on 2008-12-19
I had trouble getting network manager to save static settings for a while. the answer was to delete the "auth eth0" profile for your nic, and create a new one, for eth0. 

hope that helps,
franklin

---

### Post by RRCampbell12 on 2008-12-19
> **jonobr said:**
> Im not familiar with using opendns, I know what it is but I have no need to use it mysefl but could you supply a bit more information.


Yes, OpenDNS.com does the legwork.  There are simply too many sites to just add them to the hosts file.  OpenDNS works very well on the XP machine the kids use.  I'm sure it will work equally as well on the Ubuntu machine once I get around the bug that's causing the changes to not save.

---

### Post by RRCampbell12 on 2008-12-19
> **Insane_Homer said:**
> Instead of setting the DNS manually. Why not use the DHCP server to specify the DNS settings for the machines within the scope and assign them with the DHCP lease?

or Use the Windows 2003 Small Business Server as your DNS server and setup Open DNS as you DNS Forwarders.

Then you can lock down the network manager for the kids and they won't be able to change the DNS settings manually to bypass your controls.

Ah, yes, I could do all that, except that I'm just not familiar with SBS to that level of detail.  Back in the day, my company did networking and software development.  Now it's just software development because it's too hard to do both well.  I get my former business partner - now solely a networking guy - to help me out with stuff like this, but I hate to lean on him too much.  He does have paying clients after all.  Also, I'm not always aware of all the features and the things that can be done.  As for the kids changing it, they are not yet old enough or savy enough to do that, so I'm safe for now with this technique.  Thanks for the suggestion though.  I might get my friend to help me out with that.

---

### Post by RRCampbell12 on 2008-12-19
> **doas777 said:**
> I had trouble getting network manager to save static settings for a while. the answer was to delete the "auth eth0" profile for your nic, and create a new one, for eth0. 

hope that helps,
franklin

Me, too!  Thanks for the reply.  I had not yet looked at the workarounds/fixes, so I hope it's that easy.

---

### Post by Iowan on 2008-12-20
[workaround]("http://ubuntuforums.org/showthread.php?t=974382").

---

