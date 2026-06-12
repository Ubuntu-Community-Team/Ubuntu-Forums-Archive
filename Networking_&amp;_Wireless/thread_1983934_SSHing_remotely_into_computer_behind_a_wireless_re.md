---
title: "SSHing remotely into computer behind a wireless repeater"
date: 2012-05-21
forum: Networking &amp; Wireless
---

### Post by fizikz on 2012-05-21
I would like to ssh remotely into a computer that is setup as follows:

internet -> router -> wireless repeater -> computer

I have set up a static IP on the computer and I have set up port forwarding on the router but I don't think the router 'sees' my computer directly. What do I need to do to make this work?

---

### Post by Chrus on 2012-05-21
Just to be clear, you're trying to SSH to a computer on your network from the outside world?

If thats the case, and your forward is set up correctly, you should be able to get in by SSHing to your external IP address. Do you have a static IP on your internet connection? or are you looking up your dynamic address each time you want to connect?

What router are you using? And how did you set up your port forward? What port(s) did you forward?

---

### Post by Chrus on 2012-05-21
I should probably also ask the obvious... You do have OpenSSH installed on your computer, right? Im assuming its an Ubuntu PC because your asking on an ubuntu forum.

Can you SSH to it from within your network?

---

### Post by fizikz on 2012-05-21
Yes, I'm trying to SSH into a computer on my home network from the outside world when I am away. The port forwarding has been set up on the main router, forwarding the port that I use on this computer for SSH. I have set it so that the computer always gets a static IP on the network. The outside IP is dynamic so I use DynDNS.org. SSH has worked previously on this computer when it was on a different network. The part that is different here is the wireless repeater to which the computer is connected in this network.  

The router is a Siemens Speedstream 6520, and the repeater is an Engenius ESR 9850 in repeater mode.

Yes, OpenSSH is installed on the computer, and I am running Ubuntu 12.04 on it. I can SSH the localhost, but going through the internet times out without a response.

---

### Post by Chrus on 2012-05-21
The fact that you can SSH to your computer from within your network is a good sign. That means theres nothing wrong with your computer, the problem lies on the network setup.

I must say, I did cringe when I read "Siemens Speedstream 6520". Those things arent exactly top quality.

As long as your computer and router are both on the same subnet, there would be no reason the router cant 'see' the computer. Meaning a port forward should work. 

Do you have a port forward set up for port 22 on both TCP and UDP?

---

### Post by fizikz on 2012-05-21
Yes, I can SSH into the computer from within the network, but from outside the network, it isn't working. I have setup SSH with a different port number (which I specify with the ssh -p flag) and I have forwarded the port, both TCP and UDP, on the router. I agree, the Siemens 6520 is not my favorite piece of hardware, but since it is also the internet modem (modem/router), I have to live with it for now. 

How can I verify that the computer and router are on the same subnet? What situation would allow SSH to work within the network, but not from outside it?

---

