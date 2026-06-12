---
title: "Vino Random Port?"
date: 2010-03-28
forum: Networking &amp; Wireless
---

### Post by iamgeniusrnti on 2010-03-28
I have Ubuntu Ultimate on an Acer One.  I am using the built in remote desktop and the SSH server.  I connect thru my Droid via SSH into my box and use port forwarding on the Droid.  Once the connection is established, I can use AndroidVNC to remote control the desktop.

Here's the problem, sometimes when I reboot teh box, the Vino will change ports.  So far it's only used ports 5900 and 5901.  So my SSH is set up to forward both ports.  Any reason why it's switching ports and are there any other ports I should be prepared for?

---

### Post by suseendran.rengabashyam on 2010-03-29
Hi,

Try the following steps in your Ubuntu Machine

1) Go to Application->Accessories->Terminal

2) Enter the following command to install 'gconf-editor'

```
sudo apt-get install gconf-editor
```

after installing, enter

```
gconf-editor
```

3) Go to desktop->gnome->remote_access

4) Check the option 'use_alternative_port'

5) Click on 'alternative_port' and change its value to suit your needs eg: 5903

Close the 'gconf-editor' and make necessary changes to your Droid so that you can VNC to your Ubuntu machine.

Hope this helps.

---

