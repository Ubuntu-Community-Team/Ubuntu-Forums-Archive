---
title: "ssh not working"
date: 2011-09-29
forum: Networking &amp; Wireless
---

### Post by cheatos on 2011-09-29
Hi,

I hope this is the right forum for this, but I try connecting my iPhone and my computer using ssh.
I already have figured out logging in to my computer from my iPhone but what I was more interested in is connecting to my iPhone from my computer.

When I try to build up a connection through terminal using

ssh root@(IP adress of my iPhone)

I always receive the error message

ssh: connect to host (IP adress of my iPhone) port 22: connection refused

How can I change the connection port?
Or is it because my computer is logged in over a LAN and my iPhone over WLAN?
But I think then I would also not have been able to control my computer from my iPHone, right?

And another question, is it only possible to log into a system as admin?
Because I have two users on my computer michael (which is my admin/sudo-user) and user (which I usually use) and when I tried connecting as user it also didn't work but with the sudo-user it worked without any problems.

Thanks guys

---

### Post by scorp123 on 2011-09-29
> **cheatos said:**
>  what I was more interested in is connecting to my iPhone from my computer.

When I try to build up a connection through terminal using

ssh root@(IP adress of my iPhone)

I always receive the error message

ssh: connect to host (IP adress of my iPhone) port 22: connection refused

Are you sure you have the SSH service running on your iPhone and that it is turned on??

Screenshot from my iPhone 3GS with SSH turned off:

[IMG]http://dl.dropbox.com/u/1614648/tmp/29.09.11%20photo%20411.png[/IMG]


And with SSH turned on:

[IMG]http://dl.dropbox.com/u/1614648/tmp/29.09.11%20photo%20410.png[/IMG]

To remote control your phone you need something like **Veency** (also shown in the screenshots above), not SSH. SSH will give you access to the shell and the Unix OS underneath the iPhone's IOS but unless you know what you're doing you won't find that interesting at all I think.

---

### Post by scorp123 on 2011-09-29
And here what SSH onto an iPhone looks like ... On the iPhone there are only two users that can be used with SSH: **"root"** and **"mobile"** (and *DO NOT* mess with these accounts unless you know what you are doing!!). Other accounts such as "nobody" don't have a shell (similar to the situation on a Linux system).

So I am using "root" here:

[IMG]http://dl.dropbox.com/u/1614648/tmp/ssh-to-iPhone.jpg[/IMG]

---

### Post by cheatos on 2011-09-29
okay, thanks for your advice, I'm pretty sure I have ssh running.
Is the program you've mentioned for the iPhone or my computer?

And what I thought about was transferring files between my computer and the iPhone without having to connect it. Wouldn't that be possible?

edit: As i see now, veeny is on the iPhone, thank you

---

### Post by scorp123 on 2011-09-29
> **cheatos said:**
>  And what I thought about was transferring files between my computer and the iPhone without having to connect it. Wouldn't that be possible? 
Only works for photos! Those are located in:
**/var/mobile/Media/DCIM/100APPLE**

Uploading MP3's still requires iTunes because transferring the MP3 files alone isn't enough ... you still need iTunes to handle the database (yes, how sick is that?? There is a friggin' database in an obscure binary format right there ...) and update it for you or else the iPod application won't "see" the MP3's you uploaded.

Only way around that is to install alternative MP3 players from the **Cydia** store, e.g. **pwnplayer** ... but that program isn't free anymore and I don't trust PayPal anymore (... long, long story ...) so I personally never bothered to get it.

---

### Post by cheatos on 2011-09-30
okay, thanks, thats really odd, that you can't just put mp3s on the device...

I'll mark this thread as solved.

---

### Post by scorp123 on 2011-09-30
> **cheatos said:**
> okay, thanks, thats really odd, that you can't just put mp3s on the device...  You can do that with Android devices, yes. There it's just a matter of drag & drop.

Apple? Nope. They insist you use iTunes. As I said: there's a database on every Apple device too. Placing the files onto the device alone won't do it. You also have to update the database on the device, and unless someone reverse-engineers the thing this means only iTunes can do it.

---

