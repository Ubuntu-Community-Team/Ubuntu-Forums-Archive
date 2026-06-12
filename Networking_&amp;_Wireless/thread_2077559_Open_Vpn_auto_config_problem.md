---
title: "Open Vpn auto config problem"
date: 2012-10-28
forum: Networking &amp; Wireless
---

### Post by Digitallysick on 2012-10-28
In windows, i download the open vpn client, enter the server/port login and pass, it automatically gets whatever keys needed and thats it. 

In linux, i cant seem to get it to function that way, what am i doing wrong?  I for sure do not want to try to get these keys manually, and shouldnt have to do it that way since in windows and mac it auto gets the keys

How do i do it? 

Thanks

---

### Post by ahallubuntu on 2012-10-28
I'm not sure what you mean that it "automatically gets whatever keys it needs"?  You have to provide the keys/certificates on the client side manually by copying them to the client.  If you simply provided a password to login, what would be the point of having keys in the first place?  Then anyone who could crack your password would be able to connect, defeating the point of the extra security provided by keys/certificates.

It is possible to set up the OpenVPN server not to use keys or certificates at all (just a passcode).  Perhaps that's all you have set up?  In that case, if you have set up your Linux OpenVPN client to use keys the server isn't asking for, of course it will fail.

Perhaps you could describe exactly how your OpenVPN server is now set up?  Post your OpenVPN server configuration file?

---

### Post by Digitallysick on 2012-10-28
Currently in windows, i run the open vpn app, put the ip and port, login and pass and hit connect. It asks me about accepting a key which i do, and its connected

For mac, I use an app viscosity , i originally go to "import settings from server" put in the ip and port, login and pass, import settings and then just connect

In linux, i cant find these options .  I can see that viscosity imported all the keys and etc that were needed 

But i dont have them for linux, i need the open vpn option to import them like i do in windows/mac

I don't know the configuration, i just know that in windows its the app + login/pass/server ip and its all automatic even on first launch or initial setup

---

