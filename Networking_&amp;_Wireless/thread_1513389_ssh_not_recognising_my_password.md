---
title: "ssh not recognising my password"
date: 2010-06-19
forum: Networking &amp; Wireless
---

### Post by larryfroot on 2010-06-19
Hi people. Have a load of stuff that I must get off my laptop. Laptop's usb is shafted, and the burner is really flaky. I was using a common or garden network connection that magically appeared for me whenever I needed it on my desktop machine. But I have just changed providers, and the connection is no longer there. I then installed ssh server etc, installed it on both machines but when I use it, the password is refused. Turned down. Rejected.

I have pinged from and at to each machine - 100 per cent fine. There is only two machines on this local network, I have turned caps lock off and my passwords are a mixture of numbers and letters.

Any help? Please? Thank you big time.

---

### Post by prshah on 2010-06-19
> **larryfroot said:**
> I then installed ssh server etc, installed it on both machines but when I use it,

You don't need ssh server on both machines; put it on any ONE. I suggest your desktop.

Change configuration parameters (especially PORT) in /etc/ssh/sshd_config (on the server machine).

Then, restart the server ```
sudo service ssh restart
```

Now, from your client machine, attempt to log into the server```
ssh -P 2121 user@server
``` where:
2121 is to be replaced by your custom port number as entered in the /etc/ssh/sshd_config file;
user is your user id on the **server**
server is your ssh server; you can put in your server's ip address here

Once you are able to log in, you can use scp to transfer your files between client and server.

For example, to xfer your home directory from client to server, use```
scp -rP 2121 /home/client user@server:/home/user/
```

If you run into problems, please post back with details.

---

### Post by larryfroot on 2010-06-20
Firstly, thank you very much for the interest you have shown in my problem. I am afraid that I don't understand networking very well, so please be patient with me as I try and do everything correctly.

I removed the ssh server from my laptop.

I then noted that I had to change configuration parameters in sshd_config. I know to change the port, but what are the other parameters I must change?

I googled to find out how to find an unused port in ubuntu that I could assign to ssh, but for the life of me, I couldn't find any simple, step by step instructions on how to do that! sshd_config is set to port 22 by default, so I left it at that.

Finally, the command;

ssh -P 2121 user@server

I can understand -P 2121 but user@server...

would that be myusername@myipaddress?

Sorry to be dense, but this is a real learning curve for me, and I really am grateful for your help. Thanks

---

### Post by pdtpatrick on 2010-06-20
Yup that's what that means. so enter yourusername@ipaddressofserver

---

### Post by larryfroot on 2010-06-20
Hallo, and thank you

the error I get back (I also changed the port from 22 to 80 in sshd_config) 
is

ssh: connect to host 80 port 22: Invalid argument

I am using my username and the ipaddress of my desktop, as that is where the server is now that I have removed it from the laptop.

---

### Post by larryfroot on 2010-06-20
is the ip address of my desktop the same as the ip address of the ssh server?

---

### Post by larryfroot on 2010-06-20
I have 'declared' a service in the router (as ssh wasn't an option in the dropdown menu) on offer of SSH and set the port to 22. (I also reset the port in sshd_config back to 22) I have set port 22 as allowing incoming and outgoing in uwf. 

Still no joy : (

---

### Post by prshah on 2010-06-20
> **prshah said:**
> ;
user is your user id on the **server**
server is your ssh server; you can put in your server's ip address here[/code]

> **larryfroot said:**
> 
I removed the ssh server from my laptop.
but what are the other parameters I must change?

I can understand -P 2121 but user@server...


Don't change any other parameters. If you don't know what port to use, use 2121; or as long as you don't plan to expose your ssh server (desktop) to the Internet, you can also stick to 22 (not recommended). Don't use port 80; that is reserved for HTTP. You can use any random number above 1024.

> **larryfroot said:**
> 
ssh: connect to host 80 port 22: Invalid argument

You have mistyped something. What is your exact command?

> **larryfroot said:**
> is the ip address of my desktop the same as the ip address of the ssh server?

Yes.

> **larryfroot said:**
> I have 'declared' a service in the router

Gone too far. You don't need to do this unless you want to access your ssh server (desktop) across the Internet. Please undo this.

---

### Post by larryfroot on 2010-06-21
Thank you so much for hanging on in there with me.

OK, the password no longer seems to be an issue...I have deleted the ssh thingy in the router, have changed the port number in sshd_config to 1027.

Where 'my_username' appears in the following it is the user name on my laptop (which is different from the username on my desktop).

Where 'my_ipaddress' is used, I have put down the ip address of my laptop - I am trying to access it via my desktop, btw.

The command I am using is ssh -P 1027 my_username@my_ipaddress

The output I now get is:

connect to host 1027 port 22: invalid argument

Thanks again, I really appreciate it as I am not trying to get those files from my laptop just for fun.

I also reinstalled ssh server and client...could this be anything to do with the keys? I assumed that the old files containing keys would be wiped and new keys required. but I haven't been prompted for any.

---

### Post by wojox on 2010-06-21
Reade this page [forgot root password or reset root password ]("http://www.debianadmin.com/forgot-root-password-or-reset-root-password-in-debian.html")

---

### Post by prshah on 2010-06-21
> **larryfroot said:**
> 
The command I am using is ssh -P 1027 my_username@my_ipaddress

OK My mistake; the "-P" is supposed to be "-p" (lower case). "-P" is to be used with scp only.

---

### Post by larryfroot on 2010-06-21
Hi!

We seem to be narrowing it down a bit...latest error message after using lower case p is:

Permission denied, please try again.

I have added myself to ssh group on both machines. I have also granted permissions to use ethernet networks on both machines. 

Thanks so much for your help...

---

