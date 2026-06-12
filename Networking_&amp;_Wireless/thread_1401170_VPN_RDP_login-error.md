---
title: "VPN RDP login-error"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by venkatad on 2010-02-07
Hi Guys
I have been trying CISCO VPN connecting to my office.
I am able to connect, in my network manager it shows the "plugged-in icon" when i clicked on network manager->VPN->myvpn.
WHEN i go to a terminal and type rdesktop 10.11.12.13(example of My Ip) IT GIVE s me the WIN-login screen of my office computer. 
Here the problem araises:
 In the login name field it by default takes my username of the ubuntu machine from where I am trying to do RDP. if I changes that to my windows office user name(ex jsmith) and put my password, it gives me log in error: The system could not log you on make sure the user name and domain are correct, then type your password again.
Why it is taking my ubuntu username by default?
Even if i change that to my windows domain name why it does NOT let me log in?
How can i configure this?
HOWEVER, I AM able to login to my remote office computer through XP cisco client.
PLEASE HELP ME..
thanks

---

### Post by gombadi on 2010-02-07
> 
WHEN i go to a terminal and type rdesktop 10.11.12.13(example of My Ip) IT GIVE s me the WIN-login screen of my office computer


If you type rdesktop on the command line it will display a help message. From that you will notice -u and -d are used to enter username and domain so you could try -

```

rdesktop -u jsmith -d somedomain 10.11.12.13

```

As for why it is not letting you login - not sure. Check your logs and let us know what you find.

---

### Post by venkatad on 2010-02-07
> **gombadi said:**
> If you type rdesktop on the command line it will display a help message. From that you will notice -u and -d are used to enter username and domain so you could try -

```

rdesktop -u jsmith -d somedomain 10.11.12.13

```As for why it is not letting you login - not sure. Check your logs and let us know what you find.
I dont know, i think its bcos of .conf file in /etc/vpnc

---

