---
title: "Home networking question"
date: 2009-07-24
forum: Networking &amp; Wireless
---

### Post by thunderdan on 2009-07-24
I haven't found the answer in any of the posts I've read, but I'm sure it's quite simple.

I have two computers, both running Jaunty, and both connected to a router. What I would like to do is to create a folder on one of the computers in which I can place files and folders to which the second computer has access to. I also want to be able to place files and folders into this folder from the second computer as well.

I'm sure there is a simple way to do this, but I just don't know how. Can anyone point me in the right direction please?

Thank you :)

---

### Post by ibutho on 2009-07-24
One option would be to use NFS. There is some information about it [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo").

---

### Post by thunderdan on 2009-07-24
At the bottom of the page you referred me to, I saw this link:

[http://ubuntuforums.org/showthread.php?t=249889]("http://ubuntuforums.org/showthread.php?t=249889")

I got to the second step:
> Editing /etc/exports
the /etc/exports file is used for creating a share on the NFS server

invoke your favorite text editor or
sudo vi /etc/exports

Here are some quick examples of what you could add to your /etc/exports

For Full Read Write Permissions allowing any computer from 192.168.1.1 through 192.168.1.255

    * /files 192.168.1.0/24(rw,no_root_squash,async)


So, do I need to figure out what the IP address of my second computer is?

---

### Post by ibutho on 2009-07-24
Yes. You maybe better off using static IP addresses because it makes things a bit easier.

---

### Post by thunderdan on 2009-07-24
> **ibutho said:**
> Yes. You maybe better off using static IP addresses because it makes things a bit easier.

Sweet. How do I do that?

---

### Post by superprash2003 on 2009-07-24
here's a tutorial [http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html](http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html)

---

### Post by thunderdan on 2009-07-24
> **superprash2003 said:**
> here's a tutorial [http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html](http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html)

Cool, cool. Thank you. I got to step 8:

> Step 8 : Now under address Enter the static ip address you wish to use , in my case it is 192.168.1.10 .In Netmask set it to 255.255.255.0 ( its suitable in most cases).Under gateway enter your gateway ip which is mostly your modem/router ip address(192.168.1.1 or 192.168.0.1 mostly) , in my case it is 192.168.1.1

So how do I figure out what my gateway ip address is? And in step 9,

> Step 9 : Then Enter the DNS server ips manually, here you can enter your ISP's DNS servers if you wish, if not just enter 208.67.222.222 which is opendns server ips (Recommended)

Do I really want to enter 208.67.222.222?

Thanks,
Daniel

---

### Post by Maheriano on 2009-07-24
This is way too complicated. Forget that stuff and just right click the folder and hit SHARE. When you go to NETWORK on any other computer on that network, it'll show up as a shared folder you can copy files in/out of.

---

### Post by Iowan on 2009-07-24
> **thunderdan said:**
> So how do I figure out what my gateway ip address is?  What IP address do they get via DHCP? As mentioned - the gateway is *probably* your router/modem, and it *probably* has the address 192.168.X.1.

Another option is to set up a static lease in your DHCP server (the router?) to issue the same lease based on MAC address.  DNS information would be passed on by DHCP server.  Some DHCP servers (routers) are not capable of issuing fixed IP addresses, but most are.

---

### Post by thunderdan on 2009-07-24
> **Maheriano said:**
> This is way too complicated. Forget that stuff and just right click the folder and hit SHARE. When you go to NETWORK on any other computer on that network, it'll show up as a shared folder you can copy files in/out of.

I right-clicked on the folder and clicked on "Sharing options." Then I ticked the box "Share this folder." A message popped up saying I needed to install some stuff first, and provided a button to do so. I did that, and then I was required to restart my session. I did that, and right-clicked on the folder and clicked on "Sharing options" again. I ticked the box "Share this folder" and "Allow other people to write in this folder." Then the icon of the folder changed to have a little hand underneath it. So how do I connect to this folder from my other computer now?

---

### Post by thunderdan on 2009-07-24
> **Iowan said:**
> What IP address do they get via DHCP? As mentioned - the gateway is *probably* your router/modem, and it *probably* has the address 192.168.X.1.

Another option is to set up a static lease in your DHCP server (the router?) to issue the same lease based on MAC address.  DNS information would be passed on by DHCP server.  Some DHCP servers (routers) are not capable of issuing fixed IP addresses, but most are.

I don't know what DHCP is.

---

### Post by thunderdan on 2009-07-24
> **thunderdan said:**
> I right-clicked on the folder and clicked on "Sharing options." Then I ticked the box "Share this folder." A message popped up saying I needed to install some stuff first, and provided a button to do so. I did that, and then I was required to restart my session. I did that, and right-clicked on the folder and clicked on "Sharing options" again. I ticked the box "Share this folder" and "Allow other people to write in this folder." Then the icon of the folder changed to have a little hand underneath it. So how do I connect to this folder from my other computer now?

I got it! I clicked on Places > Network and saw my other computer on there. I double clicked on it and saw the sharing folder. I double clicked on that and it asked me for a password. I put in my login password and presto! There's a folder on my desktop now with a little pipeline icon underneath it! Thank you! :)

---

### Post by Maheriano on 2009-07-24
> **thunderdan said:**
> I got it! I clicked on Places > Network and saw my other computer on there. I double clicked on it and saw the sharing folder. I double clicked on that and it asked me for a password. I put in my login password and presto! There's a folder on my desktop now with a little pipeline icon underneath it! Thank you! :)
No problem, you don't need to get into this DHCP and other complicated stuff, this is how I share files on my network. I also share all my media all the time in case any of my roommates wants a song/movie that I have. And just this week I had to download a neighbour's 40 gig hard drive to my machine because his laptop died and I didn't want to burn all his files so I put it in a shared folder, set him up with a user account on my wireless and told him to download it whenever he gets a chance.

Glad you got it sorted out!

---

