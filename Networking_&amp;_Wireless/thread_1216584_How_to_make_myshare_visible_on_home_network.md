---
title: "How to make /myshare visible on home network?"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by raymondvillain on 2009-07-18
Running Jaunty 64 bit on a laptop.

Samba is installed.  From Places>Network I can see all the machines in my workgroup, and their files.

When I installed Samba, I created a directory, /myshare, and gave it 0777 permissions:

sudo mkdir /myshare
sudo chmod 0777 /myshare

I also installed winbind and altered /etc/init.d/nsswitch.conf accordingly (inserted wins in front of dns).

Then reboot.  Things work OK, but when I view the laptop from the other computers on the net, I do not see the /myshare directory on the laptop.

The only thing I see is a directory called print$.

Is there a way to have /myshare (or its contents) show up when viewed from the other computers on the network?

If I do:

gksudo nautilus

and select /myshare>properties>share and try to share it, I get error messages in the terminal window that launched nautilus, something like "cannot share everyone...2 items left in hash table...etc."

What is to be done?

---

### Post by swerdna on 2009-07-18
You are getting errors when you attempt to use the Nautilus share tool. These are called "usershares". So check your usershare setup (which is in the [global] stanza of the Samba config file). In fact it wouldn't hurt to step by step check the four or five important aspects of a Samba setup, particularly the "name resolve order" parameter. They can be found here for example:
[Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home & Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")

---

