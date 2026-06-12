---
title: "How to Access files on Windows Server - VPN"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by the_pod on 2010-03-02
Hi.  I'm stumped. I'm sure there's a simple answer to this but I'm not sure what it is.  

My company runs a Windows server.  I can connect remotely via a very slow desktop emulator program in VirtualBox or I can just VPN and access whatever files I need.  #2 is the preferred option.

So far I have officially setup the VPN and everything.  It logs in. It gives me the little lock symbol above the Network Manger icon.  I'm connected!

But...

How do I actually access the darn files available via the VPN?  We keep most files on a single server for the company.  Internally, it looks something like "//Bob/Folder/".  At the office I have the shortcut set to the "folder" portion of the above since that's where things are located.

I'm not seeing anything related to the VPN in Nautilus, under Network... squat.  I've tried several methods of using the "Places > Connect to Server" function while setting it to "Windows Share" as well.  Honestly, I'm unsure if this is appropriate nor what to put in the fields (Server, Share, Folder, User Name, Domain Name) if this is the right place to be.

Could someone point me in the right direction?  Thanks for any help.

---

### Post by emanresu on 2010-03-09
i'm in the same boat as the_pod. does anyone have an answer to this?

---

### Post by emanresu on 2010-03-11
i think i got half-way there. i messed around with "connect to server" and got this message:

```
Cannot display location "smb//stwfile06.ad.edu/"
**No application is registered as handling this file** 

```


can someone tell me what application to use to address the bold statement?

---

### Post by bcbc on 2010-03-11
Click on "Places", "Connect to Server", For Service type. select 'Windows Share'.
Then enter server name/ip, share name, userid, and domain - add a bookmark to reconnect easily.

For my server I just use it's internal IP 10.1.1.1 (not the VPN IP).

---

### Post by emanresu on 2010-03-12
thanks for your response, bcbc. i had gotten past the server part yesterday.




actually, i'm in. yay, me!

---

