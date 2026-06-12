---
title: "Networking Ubuntu computers"
date: 2011-09-17
forum: Networking &amp; Wireless
---

### Post by Betanu701 on 2011-09-17
Hello,

I have been searching the forums and all over the internet for quite a while now. I am trying to connect my computers through a network router. Each is online and works. I however cannot see the computers from the other computer. I cannot connect through ffp, ssh, windows serv, or anything else. 

I have installed samba and GADMIN-samba, I have tried to configure it on both computers. 

Both computers are running Ubuntu 11.04 and has all the updates.

I do not know what to do or how I can solve my problem. 

I am able to ping the computers and responds, as well i have done a trace route. the trace route reaches but takes 1.XXX-2.XXX ms to return.

I will provided anything that can help solve my problem.

Thanks in Advance.

Beta

---

### Post by haqking on 2011-09-17
> **Betanu701 said:**
> Hello,

I have been searching the forums and all over the internet for quite a while now. I am trying to connect my computers through a network router. Each is online and works. I however cannot see the computers from the other computer. I cannot connect through ffp, ssh, windows serv, or anything else. 

I have installed samba and GADMIN-samba, I have tried to configure it on both computers. 

Both computers are running Ubuntu 11.04 and has all the updates.

I do not know what to do or how I can solve my problem. 

I am able to ping the computers and responds, as well i have done a trace route. the trace route reaches but takes 1.XXX-2.XXX ms to return.

I will provided anything that can help solve my problem.

Thanks in Advance.

Beta


To ssh then the remote machine needs to be running the sshd or ssh server daemon.

see here for file sharing [https://help.ubuntu.com/10.04/internet/C/networking-shares.html](https://help.ubuntu.com/10.04/internet/C/networking-shares.html)

right click on a folder and choose sharing options, install the service.  On your other machine in natutilus type the IP address of the machine with the share and voila !

---

### Post by Betanu701 on 2011-09-17
Thank you haqking,

I have already read that and tried everything. My problem is, the folders or computer in general does not show up at all on either side.

---

### Post by haqking on 2011-09-17
> **Betanu701 said:**
> Thank you haqking,

I have already read that and tried everything. My problem is, the folders or computer in general does not show up at all on either side.


So the machines are on the same lan and with the same network id in the IP address ?

You right click a folder and choose sharing options, install the service to share and then from other machine when you type in the IP address in the nautilus bar nothing shows up ?

or go to places and choose connect to server and choose windows share, type in IP address of the destination and then click connect and nothing happens ? an error message ?

---

### Post by Betanu701 on 2011-09-17
> **haqking said:**
> So the machines are on the same lan and with the same network id in the IP address ?

You right click a folder and choose sharing options, install the service to share and then from other machine when you type in the IP address in the nautilus bar nothing shows up ?

or go to places and choose connect to server and choose windows share, type in IP address of the destination and then click connect and nothing happens ? an error message ?

I have enabled the sharing options, added sharing folders. installed the servises. then on the other machine if i go to connect to server, and type in the IP of the other machine the timer times out. 

If I go to places (where the windows network is) I do not see the machine and if I click windows network i get a message, "failed to retrieve share list from server"

I do not know if this has something to do with it but when i go to terminal and type "
[B]sudo service smbd start

I get an out put of this 
 926 ?        00:00:00 smbd
 1098 ?        00:00:00 smbd
 2561 ?        00:00:00 nmbd

[/B]

---

### Post by Betanu701 on 2011-09-17
Oh, and the computers are connected to the same router, one is connect directly to the ethernet, the other is wireless. if that makes a difference.

---

### Post by haqking on 2011-09-17
> **Betanu701 said:**
> I have enabled the sharing options, added sharing folders. installed the servises. then on the other machine if i go to connect to server, and type in the IP of the other machine the timer times out. 

If I go to places (where the windows network is) I do not see the machine and if I click windows network i get a message, "failed to retrieve share list from server"

I do not know if this has something to do with it but when i go to terminal and type "
[B]sudo service smbd start

I get an out put of this 
 926 ?        00:00:00 smbd
 1098 ?        00:00:00 smbd
 2561 ?        00:00:00 nmbd

[/B]


mm well samba is primarily for windows shares, short of reinstalling the samba service in this instance ?...do you havw a firewall on that machine ?

also can you ssh to it then ?
```

sudo apt-get install openssh-server openssh-client

```

on the machine that is sharing (the client is not necessarily needed unless it be a client also)

then the client part on the client.

Then places, connect to server, choose ssh, add the IP, port 22, folder you want to connect to on the ssh server and the username.

then it should connect ?

---

### Post by haqking on 2011-09-17
> **Betanu701 said:**
> Oh, and the computers are connected to the same router, one is connect directly to the ethernet, the other is wireless. if that makes a difference.


shouldnt make a difference, but for complete peace of mind you might want to connect the other via ethernet to remove that as a ?...however i doubt that will make a difference.

so you can simply ssh to the box ?

---

### Post by Betanu701 on 2011-09-17
No the ssh does not work. I get an error cannot display connection, no route to host

---

### Post by haqking on 2011-09-17
> **Betanu701 said:**
> No the ssh does not work. I get an error cannot display connection, no route to host


can you show us the ip, subnet mask and gateway addresses from both machines ?

---

### Post by Betanu701 on 2011-09-17
> **haqking said:**
> can you show us the ip, subnet mask and gateway addresses from both machines ?

Yes, but is there an easy way to recall those from terminal or do I have to get it another way?

---

### Post by haqking on 2011-09-17
> **Betanu701 said:**
> Yes, but is there an easy way to recall those from terminal or do I have to get it another way?

I assume they are statics ?:

**ifonfig** on each machine

and **route -n** on each machine

or using GUI network manager on show connection information, right click NM applet and choose show connection information then post the images here for each machine

---

### Post by Betanu701 on 2011-09-17
> **haqking said:**
> I assume they are statics ?:

**ifonfig** on each machine

and **route -n** on each machine

or using GUI network manager on show connection information, right click NM applet and choose show connection information then post the images here for each machine


I have attached the pictures. I tried the ssh again and i get something like, ssh terminated unexpectedly. so i might be making some head way but it is still not working

---

### Post by haqking on 2011-09-17
> **Betanu701 said:**
> I have attached the pictures. I tried the ssh again and i get something like, ssh terminated unexpectedly. so i might be making some head way but it is still not working


mmm well IP configurations looks ok.

So it must be something to do with your services.

So any errors when install the ssh service ? and you have added server to one machine and the client to the other ? Openssh i take it ?

see here to trouble shoot save me typing it all [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#Troubleshooting](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#Troubleshooting)

---

### Post by Betanu701 on 2011-09-17
> **haqking said:**
> mmm well IP configurations looks ok.

So it must be something to do with your services.

So any errors when install the ssh service ? and you have added server to one machine and the client to the other ? Openssh i take it ?

see here to trouble shoot save me typing it all [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#Troubleshooting](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#Troubleshooting)


Thank- you

I got some major improvement. I am able to ssh to one computer. but i am not able to ssh into the other computer from the original one. on the one that fails i get a message ssh unexpectedly terminated. think that would just be something to do with my machine?

---

### Post by haqking on 2011-09-17
> **Betanu701 said:**
> Thank- you

I got some major improvement. I am able to ssh to one computer. but i am not able to ssh into the other computer from the original one. on the one that fails i get a message ssh unexpectedly terminated. think that would just be something to do with my machine?


are they both running the server or just the client on one, the server and client needs to be running on both if you want to do both from both etc ?

---

### Post by Betanu701 on 2011-09-17
> **haqking said:**
> are they both running the server or just the client on one, the server and client needs to be running on both if you want to do both from both etc ?

Both are running the exact same as the other

---

### Post by haqking on 2011-09-17
> **Betanu701 said:**
> Both are running the exact same as the other


mmm well i can only refer you back to the troubleshooting, at least one is working...so if i was you i would remove the ssh on the one not working and reinstall and then troubleshoot from a fresh install, there was obvioulsy something up orginally with the config as you have only just got it working.

---

### Post by Betanu701 on 2011-09-17
> **haqking said:**
> mmm well i can only refer you back to the troubleshooting, at least one is working...so if i was you i would remove the ssh on the one not working and reinstall and then troubleshoot from a fresh install, there was obvioulsy something up orginally with the config as you have only just got it working.


Thank you for all your help!!

I decided to just make the one that i can ssh into the main server which will allow me to transfer back and forth.

Thank you again.

---

### Post by haqking on 2011-09-17
> **Betanu701 said:**
> Thank you for all your help!!

I decided to just make the one that i can ssh into the main server which will allow me to transfer back and forth.

Thank you again.


No problem, you are very welcome.

Peace

---

