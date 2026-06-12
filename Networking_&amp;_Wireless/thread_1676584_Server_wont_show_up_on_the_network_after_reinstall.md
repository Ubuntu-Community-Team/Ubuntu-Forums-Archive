---
title: "Server wont show up on the network after reinstalling hard drive...help"
date: 2011-01-27
forum: Networking &amp; Wireless
---

### Post by ludlow on 2011-01-27
Removed hard drive from our office server to check model number (windows pc). reinstalled same hardrive and now i can't connect to server from the network (MAC). it gives me error code -43.

---

### Post by grahammechanical on 2011-01-27
A silly question. Did you shutdown the server before removing its hard drive? Have you re-booted the network computers since replacing the hard drive?

Regards.

---

### Post by ludlow on 2011-01-27
of course! to both of your questions. still nothing. id be happy just to be able to access the files from the actual server to transfer to an external harddrive. but it seems like there should be a simple fix or redirect to getting the server to show up again. I plugged the machine into a different ethernet port thinking maybe the cable was bad. the server showed up and allowed me to connect but i couldnt access/copy/edit any of the files. (We usually work off the server as well as back up)

---

### Post by ludlow on 2011-01-27
and it appears to be "pinging" successfully...

---

### Post by cgb on 2011-01-27
Are you able to access the shares from the server itself by entering the command below, with your specific information replacing the servername and sharename fields, into windows explorer?  Is this server the DNS server or is their another DNS server?  Possible DNS is not updating and you obtained a new IP address after the reboot cycle.   

```
\\servername\sharename
```

---

### Post by ludlow on 2011-01-27
heres the problem im a mac user-no experience with code/server any of that-i just know theres a missing connection somewhere on the server since thats the only thing i touched. when i go to network configurations on the server there is a static IP address thats the same as it was before. im just wondering if theres steps i can take or code i can enter in terminal to have the server "connecting" again. i reboot from the same port pretty frequently (power issues) and have never had this issue its almost like taking the hardrive out and then reinserting it disconnected a setting or something. im still connected to the same port as before...

---

### Post by cgb on 2011-01-27
Just removing and reinstalling a hard drive should not have caused the issue.  It's possible other issues came into play when the server was rebooted though.  Such as, was their a new virus software or even software update installed prior to the reboot?  If so when the machine was rebooted it could have changed firewall settings and thus preventing access to the machine.  If possible it would be best to test the connection from the server itself to see if the shares are still even accessible locally.  We need to somehow narrow down the issue.  If you can get onto the machine and know the IP address try going into the start menu and then selecting run.  From here enter the command below, replacing "ip Address" with the server's ip address.  Let us know if you can now see the shares and access the files.  

```
\\"ip Address"
```

---

### Post by ludlow on 2011-01-28
thats what i was thinking too but i cant figure out what else it could have been. i can access the server from the server no issues there (just not the files). can i enter the command below into terminal? i dont see a "start/run" option on the actual machine...heres what i see

at the top of the desktop-Applications-Places-System 

so i went to System-Admin-Network Tools-Devices

i see the IP address -Protocol IPv4 under interface info it says link speed not avail
status-inactive

and when i type the IP address in the terminal after admin@fileserver:~$//actual ipaddress here

it tells me no such file or directory

---

### Post by cgb on 2011-01-28
> Removed hard drive from our office server to check model number (windows pc)

Okay I'm confused.  Is the server a Windows PC or a Linux server?  From the above quote I assumed the server was actually a windows PC but maybe their was a missunderstanding.

---

### Post by ludlow on 2011-01-31
linux server-sorry

---

### Post by cgb on 2011-01-31
Then you should be able to do a similar test from within the linux server.  Open Nautilus (Places/Computer) and press Ctrl+L to ensure the Location box is shown.  In the location box enter the code below with your appropriate information..  By entering this can you see the shares and also browse into them and view the files?  

```
smb://ip_address_ofServer
```

---

