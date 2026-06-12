---
title: "Local network (shared internet access) in Ubuntu for mobile phone Sony Ericsson W890i"
date: 2010-12-31
forum: Networking &amp; Wireless
---

### Post by kotek on 2010-12-31
Hello!

I managed to configure my W890i phone to get access to internet through an ubuntu-based computer. It's very easy to use the phone to give internet access to the computer, but the opposite is quite more tricky. For that I've done the following (I explain the whole process so that it can be useful for anyone wanting to do the same):

----On the phone---

-Set the USB network option to "through computer", so that the phone uses the computer's internet connection and not the opposite.

-Decide and set "Shared Network" parameters: user, pasword and workgroup.

-In "conectivity-> internet connection" set "allow local network" to "yes"



----On Ubuntu 10.04---

-Install samba, samba-client, smbfs, smbclient, firestarter and dhcp3-server

-Configure Samba (System-> Administration-> Shared folders): same workgroup as in the phone, add new user (the phone), passwd this new user. In my case the user was called "w890i" and the password given was the same.

-Once the phone is connected to the computer through USB (then select "phone mode"), a new connection appears in NetworkManager: usb0. The aim is to create a shared network that gives internet access to this device. Edit the IPv4 parameters of this new connection, set them to Manual and give an IP adress (192.168.0.1) and a subnet mask (255.255.255.0); the rest of the fields are left empty. Connect this network.

-Set firestarter to use dhcp3:
sudo ln -sf /etc/init.d/dhcp3-server /etc/init.d/dhcpd

-Launch firestarter and follow the wizard. Set "allow internet shared connection", choose the device for the primary internet access, and then the device for the shared network (usb0). Then change the settings for firestarter: activate DHCP for local network, set IP to the one we gave before (192.168.0.1).

-Open dhcp3-server config file
sudo gedit /etc/default/dhcp3-server
And set INTERFACES="usb0"

-Set the policies of firestarter: in incoming connections, allow connections from the IP adress given to the phone (192.168.0.1). Then add rules for the ports that need to be open for this connection. I opened HTTP, HTTPS, SMB, SMTP, POP3, IMAP, IMAPS, DHCP for all the connections in the local network.

-Apply policies and start the firewall.


------------

After all this, the phone can access the internet through the computer. Two problems appeared:

1. I couldn't get access to https sites, like webmails. The phone gave a "communication error". But then I tried with Opera instead of the browser built in the phone's firmware, and I could finally get to https sites.

2. I couldn't retrieve mail, neither POP nor IMAP nor IMAPS. I thought it was a firmware problem again, and I tried out several mobile phone email clients written in java, but none of them worked.

So this is at the moment the problem. If I connect from the phone to the internet directly through 3G, the email clients work for all my accounts. I don't think it's a firewall problem, because the ports are opened for this connection.

Any ideas about it?
-

---

### Post by PatchesTheCaveman on 2010-12-31
When you're trying to connect to your mail server on your phone, open Firestarter and check the *Active connections* area of the main screen to see if it's making it through to the Ubuntu machine or getting blocked by the phone.

Also, you might want to open the firewall for everything on the local network.  Just add *192.168.0.0/24* to *Allow connections from host* in the Policy tab.

It is not necessary to open the specific ports like you did.  That opens them *inbound* to your computer, as if you were providing an HTTP web server, mail server, etc.

---

### Post by kotek on 2010-12-31
Thanks man!
I think you actually got the clue. Although I gave manually an IP adress to the connection, Firestarter showed me that the actual "origin" when I was trying to connect from the phone was another: 192.168.0.2 instead of 192.168.0.1. So I didn't have a rule allowing this IP adress to connect (but I had access to the internet anyway!). Writing the rule for the whole local network as you suggested solved this problem (eventhough I don't understand why my connection gets that IP adress instead of the one I gave).

So I can't still get my mails through the firmware - It's definitely gets blocked by the phone this way, because firestarter shows no connections from the local network.

BUT I managed somehow to get some mails through SmartMail, and at least the connection appears in Firestarter (192.168.0.2), although it is directed to a strange unknown port (7997)... I downloaded 9 mails, no more, and now it says there's nothing new in my inbox. I think now it's a problem from this software, I'll give a try to another mail client in java to see what happens...

---

### Post by kotek on 2010-12-31
Yes, it definitely works!
Now I just need a good java email client... that's not easy!
I'll mark the post as solved
Thanks again!

---

