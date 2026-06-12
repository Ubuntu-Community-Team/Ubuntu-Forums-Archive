---
title: "Network Settings Don't Take Effect Until Restart?"
date: 2011-08-15
forum: Networking &amp; Wireless
---

### Post by Wardrop on 2011-08-15
Can someone explain to me what I have to do to make network settings take effect? If I go into Network Settings on Ubuntu Desktop 11.04 and make changes to eth0, the changes I make don't take effect until I restart the computer. The kind of changes I'm changing are the IP address, default gateway and DNS servers.

Is this restarting your computer for network settings to take effect a normal and accepted behaviour of Ubuntu or what?

PS: I just ruined my installation by running the following command: sudo apt-get remove krb5-config krb5-user krb5-doc libldap-2.4-2. Somehow that uninstalled almost every app on my Ubuntu installation. My patience is wearing thin...

---

### Post by requeth on 2011-08-15
to restart eth0 network settings there's a few options. Ubuntu likes to break all of them:
1. 
You have to have a cable plugged in for this one.
sudo ifdown eth0
sudo ifup eth0

2. 

service networking restart (this one doesn't work for most people out of the box)

3. /etc/init.d/networking restart (this one restarts all but my wireless for some reason)

I once deleted x by trying to remove some programs I didn't need (mail, messenger, etc). I learned to really watch  what each app says it's going to install along with what you ask it to remove.

---

