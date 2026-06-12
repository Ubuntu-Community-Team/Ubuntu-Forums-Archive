---
title: "Mounting remote directory remotely"
date: 2010-07-15
forum: Networking &amp; Wireless
---

### Post by silentrebel on 2010-07-15
I might be asking a little much with this question, but here it goes anyway...

I have a computer (C1) to which I can connect through the Internet (ssh, for instance) (it has a static ip and though it is sitting behind a router, the appropriate ports are all forwarded).

I have another computer (C2) that doesn't have a fixed ip address and sits behind a router that I cannot fiddle with (so no port forwarding here).

I would like to know if there is any way to connect from C2 to C1 such that a directory on C2 would be mounted on C1.  

Even the most far-fetched of propositions are welcome... I don't mind getting my hands dirty either, if necessary.

Thanks,
Silentrebel

---

### Post by thelosmos on 2010-07-15
Your best bet would be to use something like M$ Terminal Services to remote to c1. In the terminal services client properties you should be able to enable mounting of your local disks on c2 to c1. This should give you access to moving files back and forth.

Although, with RDPv5 encryption has been added I wouldn't suggest having terminal services open from the internet. You might want to setup a vpn tunnel at home and use terminal services once the connection is established.

---

### Post by silentrebel on 2010-07-16
Thank you thelosmos for your suggestion.  However I was hoping for a more Ubuntu-based solution...  Both computers run Ubuntu so it would probably be easier to use some sort of native solution, if possible.

I suppose it's worth a try if we cannot come up with such a solution though...

Anything else?

---

### Post by Endwin on 2010-07-16
I think you can do it with a combination of a reverse SSH tunnel, and sshfs. 

I would have C2 setup a reverse SSH tunnel to C1, and then have C1 use that tunnel to sshfs mount a directory of your choice. 


> ssh -R 2222:localhost:22 USER@C1


That makes the port 2222 on C1 point to port 22 (default ssh) on C2.

Then you do a modified sshs mount.

> sshfs USER_ON_C2@localhost:/DIRECTORY/ON/C2 /C1/mount/point -p 2222

You tell it to mount a directory through the reverse ssh tunnel defined by port 2222 and viola access.

---

### Post by silentrebel on 2010-07-16
> **Endwin said:**
> I think you can do it with a combination of a reverse SSH tunnel, and sshfs. 

That's what I gathered from my research, but I couldn't get it to work...

I'm not excactly sure where you are executing all these commands (on which machine).  Here is what I tried (interpreting your post, as I saw fit) and the results.  (You should know that the port for ssh on C1 is 3621; ssh-server is configured with port 22 on C2).

I ran this on C2.  The terminal seems to login in and give me a prompt on C2 as it normally would.
```
ssh -R 2222:localhost:3621 C1-user@C1 -p 3621
```

Then I ran this in another terminal, still on C2:
```
sshfs user-c2@localhost:/directory/on/c2 c1/mount/point -p 2222
```

I got this message as a result:
> write: Broken pipe




Then, I tried this, still on C2:
```
sshfs /directory/on/c2 user-C1@C1:/mount/point -p 2222
```

When I run this command, I get this message:
> read: Connection reset by peer

What's going on?

---

### Post by silentrebel on 2010-07-16
Okay...  I figured it out. 
Let's get a few things straight first.

The ssh port on c1 will hereafter be referred to as sshc1p.
The ssh port on c2 will hereafter be referred to as sshc2p.
The port through which the reverse tunnel will be set up will hereafter be referred to as sshrp.

So, to get this to work, login to C2 and type in this command:
```

ssh -R sshrp:localhost:sshc2p c1-user@c1 -p sshc1p

```

Then on C2, type in this command:
```

sshfs c2-user@localhost:/directory/on/c2/to/be/mounted /c1/moint/point -p sshrp

```

You should now find that the selected directory on C2 is mounted in the chosen location on C1.
Thank for your help, Endwin!
Enjoy,
Silentrebel

---

### Post by linux7802 on 2011-10-25
you can also refer to the following url to mount the remote mount on your server.

[http://www.theperfectarts.com/2011/10/three-steps-to-mount-remote-directory-on-linux-server/](http://www.theperfectarts.com/2011/10/three-steps-to-mount-remote-directory-on-linux-server/)

---

