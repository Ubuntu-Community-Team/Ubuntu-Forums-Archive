---
title: "Trouble getting Cisco VPn to start"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by hd79 on 2008-12-14
I updated from ubuntu 7.10 to 8.04. I reinstalled the cisco vpn client software, and I found some instructions on the web for installing a patch file, and I got a message that a couple of files were changed or modified, after running the patch. I think it installed successfully, as I got the message at teh end about possibly needing to modify some permissions, and the warning about needing to run the /etc/init.d/vpnclient_init start command.

The problem I am having now happens when I try to start the client. I type 
sudo /etc/init.d/vpnclient_init start, and I get this message:

Starting /opt/cisco-vpnclient/bin/vpnclient: insmod: error inserting '/lib/modules/2.6.22-16-generic/CiscoVPN/cisco_ipsec.ko': -1 Invalid module format
Failed (insmod)

anyone have a clue as to what is going on here, or what I need to do to fix this?

Thanks

---

### Post by Waderider on 2008-12-16
Hello hd79, don't know if this helps, I think the patch has been unsuccessful.

I've just successfully installed cisco vpn on this computer, but initially when trying to build the vpn module was getting the message in terminal "Failed to make module "cisco_ipsec.ko".

I followed the advice on [this]("http://thoughtworker.in/2008/11/19/ubuntu-cisco-vpn-client-installation-on-intrepid/") web page and it worked for me. Don't know if this is the patch you've already tried.

---

