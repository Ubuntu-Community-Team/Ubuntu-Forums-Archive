---
title: "I need a straight forward remote connection method."
date: 2011-09-15
forum: Networking &amp; Wireless
---

### Post by masterkale on 2011-09-15
Ok my sister recently moved away and has a laptop running ubuntu 8.10. Now she is having issues installing a printer driver. I need the simplest way I can get remote access (command line is fine) to her machine. She is only able to do minimal setup on her end because of her lack of linux knowledge. I am running mac os but have access to windows too.

Does anyone have a direction I should be looking in or maybe a tutorial? I don't know whether to go with ssh, vnc or something entirely different. I appreciate the advice, thank you.

---

### Post by dansang on 2011-09-15
Team Viewer is a good easy to setup graphical way! ssh is good if you can get it working on both your sisters machine server and yours the client. Although i am having problems with ssh myself at the moment and as i've never done ssh before am struggling.

Perhaps your sister may have more knowledge then me!

Sorry i can't help further.

---

### Post by agillator on 2011-09-16
I know nothing abut a Mac, but if you can use ssh on it, that is probably the way to go. Getting you sister to install the ssh server should be easy. Have her open a terminal (applications | accessories | terminal). In there type sudo apt-get install openssh-client openssh-server. It should tell her that the client is already the newest and then install the server. If she doesn't have the client or it isn't the newest, that will be taken care of. No configuration should be necessary, but if there is [https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html) is a good reference. The final thing to check is the firewall she is running, if she is. You need to open port 22 if it is not already open. Then you sign in as her: ssh her-username@her-ip. Note you will probably have to use her ip, not a domain name. She gets that in the terminal with the command ifconfig. Read the output and look for inet addr. Do not get the one from the lo section (127.0.0.1). Her machine should ask for her password. Give it and you will get a welcome message and then a prompt. You are now working on her machine as her. Note: sounds more complicated than it is.

---

### Post by SeijiSensei on 2011-09-16
If, as one would hope, your sister is behind a firewall of some kind, you won't be able to see her computer over the Internet with SSH unless she can forward a port from the router back to port 22 on her machine.  If she doesn't have control over her firewall, I think this is going to be difficult to accomplish.

GoToMyPC.com is a clever solution to this problem, but it only works with Windows PCs and Macs.

I communicate with remote machines behind firewalls using [OpenVPN]("http://openvpn.net/").  I make the remote machine a client that connects with my Linux firewall when it boots up.  That's a good longer-term solution, but not something you can cobble together long-distance.

---

### Post by haqking on 2011-09-16
> **agillator said:**
> I know nothing abut a Mac, but if you can use ssh on it, that is probably the way to go. Getting you sister to install the ssh server should be easy. Have her open a terminal (applications | accessories | terminal). In there type sudo apt-get install openssh-client openssh-server. It should tell her that the client is already the newest and then install the server. If she doesn't have the client or it isn't the newest, that will be taken care of. No configuration should be necessary, but if there is [https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html) is a good reference. The final thing to check is the firewall she is running, if she is. **You need to open port 22 if it is not already open. Then you sign in as her: ssh her-username@her-ip. Note you will probably have to use her ip, not a domain name. She gets that in the terminal with the command ifconfig. Read the output and look for inet addr. Do not get the one from the lo section (127.0.0.1)**. Her machine should ask for her password. Give it and you will get a welcome message and then a prompt. You are now working on her machine as her. Note: sounds more complicated than it is.


using ifoncfig will give you her LAN IP (probably a private class C address in the format 192.168.x.x

You cant SSH to that remotely as your system would do a *boolean* AND operation and end up looking for a destination on the local LAN.

You will need to SSH to the WAN IP and have it forwarded to the local LAN IP

---

