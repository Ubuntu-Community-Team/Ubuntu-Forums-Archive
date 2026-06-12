---
title: "Unable to communicate anymore"
date: 2010-07-14
forum: Networking &amp; Wireless
---

### Post by jbra5516 on 2010-07-14
One problem has led to another.. I had notebook version 9.10 and it worked OK. I Downloaded 10.04 onto USB and all seemed fine. After upgrade - disaster. I have as Asus Eee PC901.

1. I am in Italy and bought a TIM USB mobile broadband modem - Ubuntu can see the device but nothing happens except a bizzare message with no information at all 'Unable to Open Archive'. I have no idea what that meant nor what I should do to resolve whatever it is, so I went back to my older USB modem which worked under 9.10 - Now even that device does nothing.

2. as a result, Ubuntu software centre does not work, Synaptic Package manager is the same; also update manager.
3. Limited communications are available via the university wireless network. That network requires me to work through their own proxy;port address (with username and password)  which I have set up using proxy manager including the username and password. This allows me to carry out web surfing and point to point downloads.

4. Firefox works fine, and it obeys the requirements for registering with the proxy. Thunderbird, evolution, Synaptic, Update manager, Software centre etc all fail because they failed to authenticate with the proxy. They all have been set up to use system proxy. (Also tried direct proxy address;port in each package but no go)

5. The ultimate frustration has come from the direct download of Skype (.deb). Double click and it starts to install then crashes because of numerous dependencies (things like libqtgui4).

I know that I am a complete beginner but I am totally stumped as to how I can get back on to mobile broadband - which, hopefully will sort the other problems out.. Can anyone help me?

---

### Post by echeadle on 2010-07-20
My problem was I set the proxy using the gnome app system->Preferences->Network Proxy when my machine was connected to a network behind a proxy.  When i connected to a network that did not have the proxy, I used the app to create another location. That did not work so I cleared the values. Again failure. I also changed the variable http_proxy with no success. Noticing apt-get was getting the same result and the fact that on the Internet a post stated that the gnome panel was a front-end to apt-get. I looked around the /etc directory because it is where most of the config files are stored.  I saw that apt had a directory so I searched the files and found a proxy setting in the apt.conf file.

So to get update-manager to work in 10.4 I deleted the proxy line in the file /etc/apt/apt.conf.   After that it worked. As for the other apps you mentioned in your post, there is probably an similar setting in each of their config files.

---

