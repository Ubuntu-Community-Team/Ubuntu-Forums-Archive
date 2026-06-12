---
title: "Cannot configure cable internet connection"
date: 2011-11-12
forum: Networking &amp; Wireless
---

### Post by siriusbg on 2011-11-12
Hello! I am normally a Windows user, but learned about the Ubuntu project and got very enthusiastic to try it out! I read some information to realise that it will be a bit hard to get used to it. 
This morning I installed Ubuntu 11.10 using Wubi. The installation was smooth and I experienced no problems at all. 
Of course, the newly installed OS comes with no video drivers and the default refresh rate was killing me (70Hz, I guess). That's why I wanted to establish an internet connection to deal with it. 
The problem is - I didn't know how to do it. The Ubuntu help section gives a pattern to configure a "wired" internet connection. 
The problem is - Ubuntu doesn't let me edit the connection manually. What I mean - I click the network menu, click Edit connections and have an already established Wired Connection 1. It IS installed, though the IP, subnet mask and gateway are not the same I have in Windows, which can't be possible, I think.
Whenever I try to edit it (clicking on the IPv4 tab and selecting Manually instead of Automatic) the Save button goes blank and can't be used. No matter what I insert in IP Adress, Network, Gateway (the three collumns that can be seen under this tab)the Save button is off. I checked and am logged as the "user", not as guest - I have sufficient administrative rights.
Under Windows I also have a Local Area connection button, as well as a specific "Lan Client" program to enter my username and password, obtained from the ISP. As far as I have seen, there is also a .gz file with this software.  
I realise the dumbness of my questions, but I really would like to use ubuntu and setting up the internet connection is vital for me. Thanks!

---

### Post by jonkiribati on 2011-11-12
You've to put a DNS address too so that the save button will be activated ;)

---

### Post by wildmanne39 on 2011-11-12
Hi, welcome to the forum! Usually setting up ethernet connection manually is not needed and will cause problems, it should find your ethernet connection in all most all cases.

Before you changed your settings did you check to see if you could get online?
Thank you

---

### Post by siriusbg on 2011-11-26
Hello! I got the internet connection working ... but just for a while. It disappears after 10 minutes or so when I log in. I have no explanation why it happens, since I was assured by my ISP that there is no malfunction.. Has anyone come across such a situation?

---

### Post by praseodym on 2011-11-26
Hi,

which hardware is in use? Router/Modem or single modem? Please show the terminal (CTRL+ALT+T) outputs of the commands:

```
uname -a
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
```

---

### Post by critin on 2011-11-26
wired connection has never failed on me, it finds and connects automatically.  Do you have the modem on when you boot or turn it on afterwards?  Did you have it on while you installed the OS?  It should be on.  It sounds like you're using dial-up, but you say cable.  Cable and modem is left on or turned on before the computer starts.  It will work unless you've modified settings to not start automatically.

---

### Post by siriusbg on 2011-12-08
I just had to configure another internet connection and it started working! Consider this thread closed! Thanks for the help!

---

