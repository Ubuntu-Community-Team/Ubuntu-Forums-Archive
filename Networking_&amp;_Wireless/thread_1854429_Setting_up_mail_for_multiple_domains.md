---
title: "Setting up mail for multiple domains"
date: 2011-10-04
forum: Networking &amp; Wireless
---

### Post by computerfox on 2011-10-04
Hello everyone,

As the name of the thread states, I am in need of help to setup mail on my server for multiple domains.

My administrative software:

Ubuntu Server 11 (YAY!)
Webmin
DNS with zonomi
Also setup DNS Zones in Webmin

I set up virtual servers using Webmin

What I did so far:

Made sure postfix is running
Added all the domains I want to accept email for in my destinations
Added MX to both DNS locations (check previously stated)

Included is a copy of my Postfix settings
Also, I am running Courier service to allow users setup outlook

Any suggestions?

PS-The most important thing is that I need it to be setup with multiple domains.

---

### Post by collisionystm on 2011-10-04
Is this a new server you just built? If so, save yourself alot of headache and  just install zental. [www.zentyal.com](www.zentyal.com)

---

### Post by computerfox on 2011-10-04
Technically, yes, I did just rebuild it, but I have about 6 GB of files.  Also, would I be able to use Webmin with it?  I would kind of rather prevent having to reinstall the whole thing if I could.

---

### Post by collisionystm on 2011-10-04
> **computerfox said:**
> Technically, yes, I did just rebuild it, but I have about 6 GB of files.  Also, would I be able to use Webmin with it?  I would kind of rather prevent having to reinstall the whole thing if I could.

It already has a built in Web Interface. Blows away anything you have ever used before. It is worth using.

---

### Post by computerfox on 2011-10-04
Really 0-o?

I also see that it runs on top of Ubuntu.  Is it safe to assume that I can simply install it on top of my Ubuntu Server?

---

### Post by collisionystm on 2011-10-04
Is it 10.04? Then yes, yes you can.

---

### Post by collisionystm on 2011-10-04
[http://doc.zentyal.org/en/installation.html#id6](http://doc.zentyal.org/en/installation.html#id6)

[http://trac.zentyal.org/wiki/Documentation/Community/Installation/InstallationGuide?redirectedfrom=Document%2FDocumentation%2FInstallationGuide](http://trac.zentyal.org/wiki/Documentation/Community/Installation/InstallationGuide?redirectedfrom=Document%2FDocumentation%2FInstallationGuide)

---

### Post by computerfox on 2011-10-04
No, it's 11 :-(

---

### Post by collisionystm on 2011-10-04
Darn. You may want to think about rolling back to 10.04 anyways. It is supported until 2015. 11 Is only 2012 or 2013 I think?

This is why I like running things virtual now lol. Instead of dedicating an entire box to an installation, you just build a good frame and run your machines on that.

---

### Post by computerfox on 2011-10-04
That's actually what I'm doing, or trying to do.  I have one physical server and I'm running a lot of virtual servers.

---

### Post by collisionystm on 2011-10-04
Gotcha. What are you using for your Virtual host?

---

### Post by computerfox on 2011-10-04
Grrr... now I'm really mad because I was advised to go to 11

---

### Post by computerfox on 2011-10-04
> **collisionystm said:**
> Gotcha. What are you using for your Virtual host?

Webmin ;-)  That's why it's important I am still able to use it.  Not a fan of the interface, but it allows me to quickly configure my virtual servers.

---

### Post by collisionystm on 2011-10-04
Well you could always try it anyways. If the machine is virtualized, make a snapshot and install. If it fails, go back to your snapshot before it happened.

---

### Post by collisionystm on 2011-10-04
And technically it should not break anything. It is going to use apache, mysql and load its own modules. You should be ok to try it out.

---

### Post by computerfox on 2011-10-04
I actually am interested in it, but I also don't want to have to install this, just to find out that I have to reinstall US (v10, this time).

---

### Post by computerfox on 2011-10-04
Does anyone have any more suggestions?

---

### Post by computerfox on 2011-10-04
How would you setup new users for each specific domain using the instructions from [here](http://rimuhosting.com/support/settingupemail.jsp?mta=sendmail)

---

### Post by computerfox on 2011-10-04
Okay, so I installed Citadel, so now I have webmail. I tested it in two ways, internal (sending mail to my linux user) and external (sending to gmail).  It did not work for the external method.  Also, is there a way that I can distinguish which users belong to which domain?

---

### Post by collisionystm on 2011-10-04
Are these valid domains that you are paying for?

---

### Post by computerfox on 2011-10-04
of course.... \\:D/

---

### Post by computerfox on 2011-10-04
Okay, so I uninstalled Citadel and now I'm trying to setup through Postfix again.  

My biggest issue I'm having right now is that it won't send or the message doesn't reach the email account outside of the server.  Any ideas or suggestions to set it up?

---

### Post by computerfox on 2011-10-04
hello everyone, can someone please tell me or give me the simplest method of setting up a mail server for multiple domains?  i'm already on my second time having to reinstall my server, so i would appreciate it if (i feel that ) we could just stop guessing around and try to figure this out.  forgive me for my choice of words, but so far two people tried to help me and i got nowhere other than having to rebuild my server.  so i'm a little irritated at this point.  if you truly know how to set up a mail server for multiple domains where i can send mail outside of the server and set it up with programs such as outlook, thunderbird, and mac mail, you would have my deepest appreciation.  all i'm asking  for is a straight answer to my problem and not guesses.  

what do i need to have a working mail server for multiple domains?
how would i configure it?
how exactly would i set up the mx and dns?

i can set up everything else for a server, just not this mail thing, so can someone please aid in my learning.

---

### Post by computerfox on 2011-10-05
just as an update i had to rebuild my server so i tried out that zentyal server and it caused more issues than fixed.  i have now went back to my older ubuntu server and i'm still searching for ways to setup a mail server.

as an added note, i have to let something off of my chest, not to be rude, but i feel that if someone doesn't know how to do something, they shouldn't try and help someone else who is having issues (blind leading the blind).  i don't mean to offend anyone and forgive me if i have.  it's not that i don't appreciate it, but so far, with this issue at least, i'm going two steps back instead of 1 step forward.  i hope you can understand my frustration.

for those who have set up working mail servers for multiple domains, i hope you can still help me with this.  is there any easy way to set up a mail server for multiple domains?

keep in mind, i am on ubuntu server 6, using webmin for administration, and it's important that i can send and receive mail for multiple domains using outside email programs such as apple mail, windows live, outlook, and outlook express.  you help is always appreciated, i would just like some help without having to rebuild my system multiple times.

-fox

---

### Post by deltacomp on 2011-11-13
Hello, I have used and setup Citadel in the past and have little problems with it, until I installed a PHP forum system which requires me to reconfigure the ports. 
 
Ayway, I suggest going back to Citadel and configuring the system that way. You can add several domains to the system by going to administration, domain name configuration and adding the domains you want. Make sure the domain name server you are using has the xmail.yourdomain.com is setup. 
 
In order to send and recieve emails through citadel, ensure that all your ports are properly configured to go to the ip of your virtual servers. That is pretty important. 
 
Also if you want to send email to external users such as gmail, you need to ensure that the external port 25 is open, not the one on your router...What I mean is that the ISP (ATT or Verizon or COX) typically will block port 25 (in an effort to block spammers I think), so you will need to call them and have them open port 25 on their end. 
 
Once that is done, you should be able to send and recieve emails via webcit (the web interface). Also adding users is as simple as going to administration and adding them. 
 
:D

---

