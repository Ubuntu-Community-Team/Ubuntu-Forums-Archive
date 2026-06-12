---
title: "vsftpd not working over the 'net"
date: 2012-03-05
forum: Networking &amp; Wireless
---

### Post by zatho on 2012-03-05
Hello everyone :) to start off with I have done several searches to try to find a solution to this to no avail, so if it has already be answered I beg forgiveness.

I am trying to setup up a file server for my family to share pictures and the kids to back up school work and what not. It seemed pretty easy at first, I got vsftpd installed and set up to work over the LAN with no problems at all. As soon as we tried to used it outside the LAN though, it didn't work. I found [this]("http://www.imovedtolinux.com/2009/07/configure-vsftpd-for-passive.html") page that pointed me to using the following settings:

pasv_enable=YES
pasv_min_port=60000
pasv_max_port=60100
pasv_address=0.0.0.0

Tried that, but still not connecting (also adding these settings makes the server not work over LAN). I figured the 0.0.0.0 might be a dummy address, so I went to whatismyip.com and substituted that IP in for the 0's and still nothing. 

I get the same error message both with and without the above settings:

Connection attempt failed with "ECONNREFUSED - Connection refused by server"

when I have those enabled, I can still connect over lan, but my client (filezilla) returns a can't retrieve directory listing message.

I have a belkin router which uses something they call "virtual servers" instead of port forwarding, but I'm pretty sure its the same thing. I have that set up to forward ports 20, 21, and 60000-60100 to the file server.

I'm almost ready to just give everybody flash drives and be done with it, but I would really to make this work just to keep my ego intact. I would really appreciate some help from anyone willing :D

if you need any further info just let me know.

---

### Post by jonobr on 2012-03-05
Maybe your client doesnt like passive mode?

If it doesnt it will never list or transfer,
It will allow you login in and thats about it.

Set to no and see what happens.

Also try using a tcpdump packet trace.

```

sudo tcpdump -i any port 20
```

This will show you data packets being sent.

If you wanted to only see control stuff  type 

```
sudo tcpdump -i any port 21
```
You should see packets going back and forth 

If you see no packets for 20 its being blocked,
but the way you describe it may be passive mode.

As a final alternative, try using openssh on the server and winscp on your windows box to copy files.
Its also far more secure

---

### Post by zatho on 2012-03-07
I am using Filezilla as my client, and I am 99% sure that it does support passive mode. In any event, I have tried this several times with passive mode enabled and disabled, and none have worked. I will be trying openSSH server tonight when I get home and see if can do what I want. Thanks for the advice, I'll post back with my results.

---

### Post by jonobr on 2012-03-07
No problem,

If your used to filezilla, which it sounds like you are,
then openssh on your server and a [winscp]("http://winscp.net/eng/download.php") client wont be too much different for you.

It gives the windows explorer style interface with drag and drop file setup.

to install openssh just

```
sudo apt-get install openssh
```
One thing that may be a fly in the ointment is some ISP block ssh.

Again, you can test for that using 
```
sudo tcpdump -i any port 22
```
then ssh from outside and if you see packets then its working.

---

