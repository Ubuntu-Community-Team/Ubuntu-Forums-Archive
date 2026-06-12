---
title: "FTP Server Issues on Oneiric Ocelot"
date: 2012-04-23
forum: Networking &amp; Wireless
---

### Post by Tsulagi on 2012-04-23
[COLOR=black][FONT=Verdana]Good Morning All,[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]    I am fairly new to Ubuntu/Linux though I am well versed in a few other OS's. Yesterday I decided to pull out an old desktop I haven’t used in quite a while and install Oneiric Ocelot on it. The setup went off without a hitch and I started playing around with the system, tweaking where I could and just learning in general.  Now, my wife owns a small business that is just getting off the ground and she talked to me about making an FTP server so that her and her business partner could share files back and forth. I, being a complete noob on Ubuntu, decided that using Ubuntu for this purpose would be a good learning experience. I installed Gadmin-Proftpd and got it setup, I setup the user accounts both in proftpd and in Ubuntu, went into my router and setup the port forwarding, the whole nine on that. It was actually a fairly simple process. Then the moment of truth came. I typed in the FTP server address from an external computer; got the pop up window for Log On (I celebrated a little) I input the username and password and then NOTHING. I thought that was strange, so I went back to the 11.10 machine and checked the logs for the server, it said that an attempt was made and was successful for log on. I went back to the external computer and tried again, only I couldn’t do anything, my net was completely down. So I reset my modem and router connection.... tried again, got the log on screen, entered user and pass and clicked enter... and the same reaction. I had to reset the router and modem again. I took this course of action about 8 times before I gave up, each time I checked the logs and verified that the server was seeing it as a successful connection yet my net was dropping off upon connection. What am I doing wrong? Could it be that the connection is actually being terminated by my ISP?[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Side note: The external machine I was using is a Windows 7 machine, I tried doing it through Firefox, Explorer(gag) and then through Filezilla, all three gave me the same issue. But in Filezilla I get a connection time out message just after it tells me I am connected. Please keep in mind that I am just learning and if you throw a lot of script at me I may start twitching involuntarily, lol[/FONT][/COLOR]

---

### Post by jonobr on 2012-04-23
Hi There


Not sure if you knew this, apologies if you do!

FTP uses two ports,
FTP control works on port 21, if forwarded correctly this will allow login listing and so on.

FTP data occurs on port 20. Can you check thats forwarded also?

Lastly I would recommend a secure protocol like scp (secure copy)
With FTP its easy enough to crack passwords etc.

On the server side

```
sudo apt-get install openssh
```

on the win7 side use something like [winscp]("http://winscp.net/eng/index.php") to copy back and forth,
it uses an explorer type interface so its pretty easy to use.

---

