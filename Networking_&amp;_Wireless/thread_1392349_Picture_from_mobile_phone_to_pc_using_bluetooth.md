---
title: "Picture from mobile phone to pc using bluetooth"
date: 2010-01-28
forum: Networking &amp; Wireless
---

### Post by hoboy on 2010-01-28
I want to send picture from my mobile to my pc, for that purpose I want to use bluetooth, I am using ubuntu 9.10.
I went to Synaptic bluetooth is installed; I have also run this sudo apt-get install blueman.
when I go to system/preferences/bluetooth manager I get the following error.
connection to BlueZ faile:
Bluez daemon is not runing

---

### Post by pdc on 2010-01-28
this post

[http://www.iamatechie.com/set-up-bluetooth-in-ubuntu/](http://www.iamatechie.com/set-up-bluetooth-in-ubuntu/)

talks of the command 

> sudo /etc/init.d/bluez-utils restart

or 

> sudo /etc/init.d/bluetooth restart

similarly 

[http://www.thinkwiki.org/wiki/How_to_setup_Bluetooth](http://www.thinkwiki.org/wiki/How_to_setup_Bluetooth)

talks of connecting phones and suggests the command

su or sudo > /etc/init.d/bluetooth restart

---

### Post by hoboy on 2010-01-28
Thanks PDC.
Now new problem when I go to system/preferences/bluetooth manager.
I get :
No bluetooth Adapters present.
Your computer does not have any bluetooth adapters plugged in.

---

### Post by pdc on 2010-01-28
> Your computer does not have any bluetooth adapters plugged in

could there be any truth in this allegation?

..................

> well, google, dear friend

happy hunting

---

