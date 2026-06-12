---
title: "automatically reconnecting &amp; starting up vpn on disconnect"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by KhaaL on 2009-07-08
Hi

I wonder if there is an option to reconnect the vpn connection once it has been disconnected somewhere in ubuntu? right now, once you're disconnected from vpn you have to reconnect to it manually.

Another thing that bothers me is that I have to connect to it manually on every boot via networkmanager, cant this be automated aswell?

---

### Post by mc_scRAT on 2009-07-10
got same interest. googled but found nothing appropriate. it's so terrible, when vpn disconnects twice a minute =(
[http://ubuntuforums.org/showthread.php?t=733948&highlight=vpn+reconnect](http://ubuntuforums.org/showthread.php?t=733948&highlight=vpn+reconnect) - something interesting
[http://ubuntuforums.org/showthread.php?t=568648&highlight=pptp+reconnect](http://ubuntuforums.org/showthread.php?t=568648&highlight=pptp+reconnect) - reconnect scrip, bun no NM actually. but an idea!
bump! really noone to speak 'bout??

---

### Post by vanBuuren on 2009-10-09
I took me some time to solve this problem, but I finally got it with some help from a script a found on the [internet]("http://markmail.org/message/nmpy4ixmasw6v3ue").

This guy Tambet Ingo wrote a dispatcher script in python, which is actually very easy to implement. You can download the script via the link mentioned above. Before you can install the script you'll have edit it first a little bit before you move it to the correct dir. 

Tambet wrote > This functionality is very often requested and a dispatcher script to do that is quite hard to implement. I wrote a script to do that, see the attachment. It needs some configuration first: The UUID of the VPN connection you'd like to get automatically activated, the UUID of the connection with which you want your VPN automatically activated, and the UID of the user who has the VPN connection defined. For the first two, just run the script without any arguments and it'll print out all known connections and their UUIDS. Find your UID with `id -u`. After changing these variables in the beginning of the script with your data, copy it to /etc/NetworkManager/dispatcher.d/ and make sure it's executable.

I looked up the UUID of my internet and vpn connection with gconf-editor. In gconf-editor you'll find the corresponding ids under system->network->connections. Finding your UID is already explained by Tambet. After this was done I changed the script to an executable with
```
sudo chmod +x vpn.py
```
Now you can then test the entered uuids by executing the script. Finally I copied the file like Tambet wrote. 

I must say, for me it works like a charm! VPN now automatically connects when I log in and reconnects after my WLAN-connection briefly is interrupted.

Hope this helps!

---

### Post by vanBuuren on 2011-01-29
I recently found [this small program]("http://sourceforge.net/projects/vpnautoconnect/") doing exactly this.

---

