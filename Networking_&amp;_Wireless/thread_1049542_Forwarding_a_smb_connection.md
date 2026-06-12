---
title: "Forwarding a smb connection"
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by short4lif2 on 2009-01-24
I am currently running a desktop and a laptop on kubuntu intrepid.  I am having some trouble setting up a fairly complicated idea I've had. My room-mate is using a wireless network on which he is sharing a folder, from a windows pc.  My desktop, however, which is connected to my own, wired router has no access to this shared folder, as we are on a different data connection.  
Here is how I figured I could solve the problem.  I want to use either ssh or smb to connect my laptop and my desktop on the wired network, since my laptop has wired and wireless access, and then tunnel through the laptop which inevitably accesses the remote folder with smb.  My original idea for doing this was to use smbmount to mount the network resource to a local folder on the laptop, and then accessing that folder on my desktop via ssh.  This solution got stopped at the mounting because that just, well, didn't work at all.  My other idea was to use forwarding in ssh, but I know nothing about this, and it seemed more complicated than a problem like this necessitated.  Does anyone know of a simple way solve this?

---

### Post by nixscripter on 2009-01-25
I can tell you about forwarding ssh. You could use this technique to forward the data from his computer over the encrypted connection.

If the laptop can access it directly, and the desktop would need to be forwarded, then run this command on the laptop:

```
ssh -L 445:friendip:445 youruser@desktop
```

Here's how it would work:

1. Command is run, and a connection is established between the laptop and the desktop machine.

2. Later, desktop connects to laptop as if it were an SMB server (on port 445 with whatever SMB client you use).

2. Laptop recieves that connection, and connects to the room-mate's computer on 445 (his SMB).

3. Laptop then fowards all data to desktop over the secure connection, and sends all data recieved to the room-mate's computer.

In other words, the laptop in the middle is transacting the data back and forth, and neither computer knows the difference.

Also, refer to the [SSH man pages]("http://www.openbsd.org/cgi-bin/man.cgi?query=ssh&sektion=1") for helpful flags to run the command in the background, and optionally, not to ask for a password.

Hope this helps.

---

### Post by short4lif2 on 2009-01-28
Thanks for the prompt response, nixscripter.  Unfortunately, this seems to have thrown some error.  Here is the full output of that command

> me@laptop:~$ sudo ssh -L 445:192.168.1.147:445 me@192.168.0.2
me@192.168.0.2's password: 
bind: Address already in use
channel_setup_fwd_listener: cannot listen to port: 445
Could not request local forwarding.
Linux box 2.6.27-11-generic #1 SMP Thu Jan 22 17:22:40 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
Last login: Wed Jan 28 11:32:25 2009 from laptop.local
me@desktop:~$ exit
logout
Connection to 192.168.0.2 closed.
me@laptop:~$ 


where 192.168.0.2 is desktop and 192.168.0.3 is laptop

Any ideas?  perhaps i have to close smbd in order for the port to open?  what else could be using it?

---

### Post by nixscripter on 2009-01-28
Yes, you will have to close smbd for this to work. Please do that and try again.

Also note that you will have to keep that connection open for as long as you want the forwarding to work. The -N and -f flags (see the man pages) can make it less annoying.

---

### Post by short4lif2 on 2009-01-28
Hm, it seems we;re getting somewhere, I ran the same command with the -N flag and got no output after the password prompt, but all that happened is that laptop dissappeared from desktop's view.  The MSHOME workgroup shows up under smb:/// (which is the laptop's workgroup) but it's empty.  perhaps I am doing this wrong?

---

### Post by nixscripter on 2009-01-28
No output after the password prompt is normal. It should have just sort of "hung there" with the connection open. And you left it open when you tried to connect to the laptop, right?

I don't know enough about SMB to debug that, unfortunately.

---

