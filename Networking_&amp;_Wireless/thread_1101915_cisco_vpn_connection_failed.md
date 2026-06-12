---
title: "cisco vpn connection failed"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by xrayjohn on 2009-03-20
I am in the process of switching to Ubuntu from Vista and the Cisco VPN is one of the few remaining hold-ups. I am using a Dell Inspiron 1521 with AMD Turion 64 bit processor. I dual boot with Intrepid.

I installed the Cisco-compatible VPN client and network management framework within the synaptic package manager. From there I created a new connection, added the appropriate gateway, user, and password info. When I try to connect, i get a bubble with an error message in it that simply states the connection failed.

Sooooo, is this Cisco compatible VPN client not good with my system? Have I missed something? Or do I start hounding the IT guys at work for something on their end... (they will probably not want to support my Linux habit).

Thanks

---

### Post by sp0nge on 2009-03-21
I use cicso VPN almost daily from ubuntu. It certainly should work. You said:

> When I try to connect, i get a bubble with an error message in it that simply states the connection failed.

Does this mean you are using a GUI to connect? If so, open a terminal and try the following:

```
cd /etc/opt/cisco-vpn(this might not be exact)/Profiles
ls
```

There should be a profile for the connection you want. Then we do:

```
sudo /etc/init.d/vpnclient_init start
<password>
vpnclient connect <name of profile here>
```

Now my profiles all end with a file extension(I think) .pcf- sorry, I'm unfortunately on a windows machine so my specifics may be off at the moment. The point is that you need to only enter the profile name- not the file extension. I am a big fan of tab completion, so I type the first few letters, TAB, then delete the last 4 characters.. 

Then you should connect. I hope this helps. I'll check back after I get these new windows put in my house ! :guitar:

---

### Post by xrayjohn on 2009-03-21
It tells me that the profile selected could not be read... I will check with the guys at work and make sure my profile information is correct.

Thanks,

---

### Post by xrayjohn on 2009-03-21
I checked my profile and went through the commands you posted and as far as I can tell from the info in the terminal it worked. However,when I go back to the GUI it says I am not connected. I am very new to Linux... Not really sure what I am doing here.

---

### Post by xrayjohn on 2009-03-21
I have it working fine by command line, but not GUI... Thanks for your help!

---

