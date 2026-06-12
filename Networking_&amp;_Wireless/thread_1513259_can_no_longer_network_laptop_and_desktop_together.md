---
title: "can no longer network laptop and desktop together"
date: 2010-06-19
forum: Networking &amp; Wireless
---

### Post by larryfroot on 2010-06-19
Hallo. I have just changed providers and they have left me with an ambit cable modem model number E08C013.00 and a Netgear WRN2000 v2.

I connected the cables (wired connections on my lappy and desktop) and although I can still access the net with both machines, they are no longer connecting together, which is pretty major for me as the usb of the laptop is screwed and the CD burner on it is tempramental to say the least. I was using my lucid desktop to access my karmic laptop and do a major backup of the files on it. Now I can't even see it in Networks (Nautilus) anymore.

If anyone can tell me how to proceed I would be Very Grateful Indeed.Thanks, LF

---

### Post by irv on 2010-06-19
The first step is to find out what the ip address is of each machine, and then try to ping them from one another. This will tell you if you are seeing them. If you can then it is a rights or security issue.

---

### Post by larryfroot on 2010-06-19
Thanks mate! I did the ping thing and I have 100% OK happy pings at either end. I suppose the next question is, where do I figure out if its a rights or permissions thing, and how do I change it if it is.

Networking...its my achilles heel...so thank you so much for your help.

---

### Post by larryfroot on 2010-06-19
I have just added user priviliges connect to wireless and ethernet networks to my personal user account on my desktop - it was already set to that on my laptop. No joy. Rebooted, still no joy.

---

### Post by irv on 2010-06-19
I have a server, desktop, and laptop that I can access from one another. I use VNC to remote into my server from my laptop to do updates etc. Here is a screen shot of my setup. I have noting set on my laptop but set the remote desktop on the server side. go to System > Preferences > Remote Desktop and set it to access rights.
Of course you need to install xvnc4viewer and server to do this.
Take a look at my screen shot. I use Alt/F2 and run the xvnc4viewer + ip address to remote into the server. Works great.
[ATTACH]160909[/ATTACH]

---

### Post by larryfroot on 2010-06-19
What an excellent way to get a message across - most intelligent of you, sir. I will try that! Thank you for your continuing interest in my learning curve, appreciated.

---

### Post by larryfroot on 2010-06-19
I am happy to report that the vnc is working perfectly - but I cannot move files across from one machine to the other, sorry to keep coming back at you like a persistent zombie, but is there anyway the clipboard can be shared in xvnc? Thanks again : )

---

### Post by irv on 2010-06-19
This is one of the best forums on the Internet for learning all the in and out of Ubuntu. I have been into computing for over thirty year, and bar none I have learn more out here then any other place. There is always someone who has an answer to your question, but sometimes you have to wait until someone finds you thread. At this very moment there are over 10 thousand active users on line all over the world so the chances of getting help is very good.

---

### Post by larryfroot on 2010-06-19
Today I have learnt about vcn, and now I am learning about ssh. Its all good stuff, and I am amazed by so many people contributing time and effort to achieve so much. If it wasn't for adobe I would happily cast microsoft into a dark hole. In fact, if adobe were ever to port, or wine had a 100 percent result with a recent CS suite, then I am sure that would be a huge nail in microsofts coffin. 

Anyways, I digress. As I am about to ask a ssh question of the community, perhaps you can answer it first! It is simple but it is so annoying. I have generated keys, made a passphrase, stored it...and still the ssh connection tells me I am entering the wrong password for my laptop. 

If any light can be shed on this, then I will continue to be grateful and somewhat overwhelmed by the kindness of others.

---

### Post by irv on 2010-06-19
Take a look at this link, it might help:
[http://www.techotopia.com/index.php/Configuring_Ubuntu_Linux_Remote_Access_using_SSH]("http://www.techotopia.com/index.php/Configuring_Ubuntu_Linux_Remote_Access_using_SSH")

---

### Post by larryfroot on 2010-06-19
oooh irv, I have just taken a peek and I think it might just help. Will let you know how I got on, just to help satisfy that all-so-human curiosity that all geeks are born with!

---

### Post by irv on 2010-06-19
Ok, if you haven't got it going yet, Here is a quick howto.
On the machine you want to ssh onto install openssh-server. The command is 
[PHP]sudo apt-get install openssh-server[/PHP]
On your laptop goto Place > Connect to Server.Then select ssh and type in the server name or IP and login Name.
[ATTACH]160929[/ATTACH]
After typing in password of the box you are trying to ssh into you will get this:
[ATTACH]160931[/ATTACH]

---

### Post by larryfroot on 2010-06-19
That's exactly what I have done Irv. The password for my laptop when I try to access it via ssh from my desktop is rejected, time and time again.I have added its ip as an allow rule in ufw, and also opened up port 22 while I'm at it as that is the port I have been specifying in the connect to server dialogue box. I have created a passphrase for my ssh key and stored it in the default location. I'm beginning to think I need to get back to my laptop to configure ufw from that end as well.

---

### Post by irv on 2010-06-19
> **larryfroot said:**
> That's exactly what I have done Irv. The password for my laptop when I try to access it via ssh from my desktop is rejected, time and time again.I have added its ip as an allow rule in ufw, and also opened up port 22 while I'm at it as that is the port I have been specifying in the connect to server dialogue box. I have created a passphrase for my ssh key and stored it in the default location. I'm beginning to think I need to get back to my laptop to configure ufw from that end as well.

Maybe it is something so simple but we both are missing it. It works on my setup but I have the same password on both machines, but that shouldn't make a difference. I think I need to rest my brain for a minute and maybe it will come to me. I hope someone is reading this and can add some input.

---

### Post by larryfroot on 2010-06-19
Thank you so much for your time. I too will put it to one side for a while. If it gets no-where I shall bump it...take care and thanks again LF

---

