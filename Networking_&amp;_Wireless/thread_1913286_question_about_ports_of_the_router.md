---
title: "question about ports of the router"
date: 2012-01-22
forum: Networking &amp; Wireless
---

### Post by esbrinartot on 2012-01-22
I typed sudo nmap 192.168.1.0/24. So I can see all the ports are opened in my computer and my router.

Router ip 192.168.1.1: (I guess it's the router) 
PORT   STATE SERVICE
22/tcp open  ssh
53/tcp open  domain
80/tcp open  http

Computer 1 ip 192.168.1.10:
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
5800/tcp open  vnc-http
5900/tcp open  vnc

Computer 2 ip 192.168.1.12:
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
5800/tcp open  vnc-http
5900/tcp open  vnc

I know for sure I can establish connections ssh and ftp inside my local network. But can I do it from outside? Can I establish a connection in Case I'm working in my office?? I understand I can't because the only ports opened in the router are:
22/tcp open  ssh
53/tcp open  domain
80/tcp open  http

Can you confirm with this configuration I just can establish connections shh??

Is it possible to open the ports without knowing the user and password of the router? The user and the password are not standard and the internet company doesn't want to provide me neither the user nor the password. Any solution?

---

### Post by haqking on 2012-01-22
> **esbrinartot said:**
> I typed sudo nmap 192.168.1.0/24. So I can see all the ports are opened in my computer and my router.

Router ip 192.168.1.1: (I guess it's the router) 
PORT   STATE SERVICE
22/tcp open  ssh
53/tcp open  domain
80/tcp open  http

Computer 1 ip 192.168.1.10:
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
5800/tcp open  vnc-http
5900/tcp open  vnc

Computer 2 ip 192.168.1.12:
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
5800/tcp open  vnc-http
5900/tcp open  vnc

I know for sure I can establish connections ssh and ftp inside my local network. But can I do it from outside? Can I establish a connection in Case I'm working in my office?? I understand I can't because the only ports opened in the router are:
22/tcp open  ssh
53/tcp open  domain
80/tcp open  http

Can you confirm with this configuration I just can establish connections shh??

Is it possible to open the ports without knowing the user and password of the router? The user and the password are not standard and the internet company doesn't want to provide me neither the user nor the password. Any solution?

If ssh is running on the machine you want to ssh to and as long as you know the authentication information or have the key and the router your connect to from outside is set to forward yoru ssh request to the machine then in theory yes you can connect.

Above does not display any port forwarding information.

Your router needs to forward port 22 requests to the machine you wish to ssh to.

From outside you ssh to your external IP which may change so good idea to use dynamic DNS

your ISP wont provide you with username and password of your router ? unlikely, and besides you can reset it and configure it yourself if it is yours.

---

### Post by esbrinartot on 2012-01-22
> **haqking said:**
> If ssh is running on the machine you want to ssh to and as long as you know the authentication information or have the key and the router your connect to from outside is set to forward yoru ssh request to the machine then in theory yes you can connect.

Above does not display any port forwarding information.

Your router needs to forward port 22 requests to the machine you wish to ssh to.

From outside you ssh to your external IP which may change so good idea to use dynamic DNS

your ISP wont provide you with username and password of your router ? unlikely, and besides you can reset it and configure it yourself if it is yours.

So please confirm I understood what you said. I'm newy

1- I must setup the router and indicate the port 22 is for the computer I have at home with IP for example 192.168.1.6

then from my office I could type:

ssh user@public_ip    "and that's all"

Can you confirm it?

In case I have two machines asigned to the port 22:
192.168.1.6 and 192.168.1.4

What I should do from my office to chose which want I want to connect:

ssh user@public_ip:local_ip_of the computer of my network??

thks in advance

---

### Post by haqking on 2012-01-22
> **esbrinartot said:**
> So please confirm I understood what you said. I'm newy

1- I must setup the router and indicate the port 22 is for the computer I have at home with IP for example 192.168.1.6

then from my office I could type:

ssh user@public_ip    "and that's all"

Can you confirm it?

In case I have two machines asigned to the port 22:
192.168.1.6 and 192.168.1.4

What I should do from my office to chose which want I want to connect:

ssh user@public_ip:local_ip_of the computer of my network??

thks in advance

only you can confirm it will work.

However yes thats all as long as port forwarding is working correctly it should then ask you to authenticate and thats it.

As for more than one machine with SSH running, on a home network i would change the port on one of the machines to run something other than 22 which is a good security measure anyways then forwards that to the correct IP

Cheers

---

### Post by esbrinartot on 2012-01-22
> **haqking said:**
> only you can confirm it will work.

However yes thats all as long as port forwarding is working correctly it should then ask you to authenticate and thats it.

As for more than one machine with SSH running, on a home network i would change the port on one of the machines to run something other than 22 which is a good security measure anyways then forwards that to the correct IP

Cheers

To close to post:

1- I can't setup the router. I don't have the password and is not an standard one. A couple of months ago the internet provider rejected to give me to password. I will insist again this afternoon

2- Change the port 22 to another one... yes it's a little bit more secure but I think they just have to scan the ports to see the new one.

3- is it correct this syntax??
ssh username@public_ip:Local_ip

(after : shoudl I write the port instead the local IP) I don't know the correct command I have to type. If you know it help me please. So the doubt is how to chose the computer you want to connect if you are outside your local network. Maybe I wrote well by change by I don't know it.

4- You talked about a dynamic DNS. I think I have an static public IP. I switch off and switch on the router and the IP is the the same. I will observe a for a time whether it changes or not.

thks for all your help

---

### Post by haqking on 2012-01-22
> **esbrinartot said:**
> To close to post:

1- I can't setup the router. I don't have the password and is not an standard one. A couple of months ago the internet provider rejected to give me to password. I will insist again this afternoon

2- Change the port 22 to another one... yes it's a little bit more secure but I think they just have to scan the ports to see the new one.

3- is it correct this syntax??
ssh username@public_ip:Local_ip

(after : shoudl I write the port instead the local IP) I don't know the correct command I have to type. If you know it help me please. So the doubt is how to chose the computer you want to connect if you are outside your local network. Maybe I wrote well by change by I don't know it.

4- You talked about a dynamic DNS. I think I have an static public IP. I switch off and switch on the router and the IP is the the same. I will observe a for a time whether it changes or not.

thks for all your help

1. reset the router and you can configure it how you like or buy your own one to use.

2. everyone knows that port 22 is ssh, if you change it it may appear on a port scan but people wont know it is ssh thats the point and is best practice, you change it in /etc/ssh/sshd_config and edit the port line to suit, dont use a well known or reserved port obviously or one used by another service that you use, you then need to specify that port in your syntax such as 

ssh -p 54327 user@sshserver where 54327 is the port you chose or similar

3. the syntax is ssh user@ip and you can always ssh from one box to the other

4. if IP is static then no worries though you usually need to pay for that, some ISP give you it, even if it is dynamic it may often stay the same for a while due to lease time etc, if not then use dynamic DNS or similar service

If you want multiple machines running ssh, then configure whatever ports you liike on the router to forward to your internal machines such as on router

port 22345 forwarded to port 22 on machine 1
port 22346 forwarded to port 22 on machine 2

and then adjust ssh connect syntax to suit the port which correlates to the forwarding to the correct internal machine

Cheers

---

### Post by esbrinartot on 2012-01-22
> **haqking said:**
> 1. reset the router and you can configure it how you like or buy your own one to use.

2. everyone knows that port 22 is ssh, if you change it it may appear on a port scan but people wont know it is ssh thats the point and is best practice, you change it in /etc/ssh/sshd_config and edit the port line to suit, dont use a well known or reserved port obviously or one used by another service that you use, you then need to specify that port in your syntax such as 

ssh -p 54327 user@sshserver where 54327 is the port you chose or similar

3. the syntax is ssh user@ip and you can always ssh from one box to the other

4. if IP is static then no worries though you usually need to pay for that, some ISP give you it, even if it is dynamic it may often stay the same for a while due to lease time etc, if not then use dynamic DNS or similar service

If you want multiple machines running ssh, then configure whatever ports you liike on the router to forward to your internal machines such as on router

port 22345 forwarded to port 22 on machine 1
port 22346 forwarded to port 22 on machine 2

and then adjust ssh connect syntax to suit the port which correlates to the forwarding to the correct internal machine

Cheers

thks now the theory is well understood. Now I just have to apply it. But first step will be to solve the router issue.

I'm afraid to reset the router. I will explain the reason. It's because this worked with "telefónica" then I changed the internet provider and I used the old router. At the beginning the old router didn't work so I gave it to the new company to configure it. After the configuration worked.

If I reset the router I'm so afraid I will recover the original information and I won't have internet.

So the best solution I think is insist again with the internet provider.

---

### Post by jimwill on 2012-01-22
One thing I do to avoid having to wait to get to another location, is to use one of the free proxy servers. I use [www.hidemyass.com](www.hidemyass.com) to check outside connectivity to my other machine. But there are many others available, just do a search for them.
This way, whenever you make a change, you can check it out almost immediately!
Altho, thinking about it, they may not work with ssh. Just have to try and see.

---

