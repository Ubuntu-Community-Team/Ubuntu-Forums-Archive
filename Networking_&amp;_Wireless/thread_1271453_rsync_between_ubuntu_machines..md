---
title: "rsync between ubuntu machines."
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-09-20
Just curious - how do you do this?

I rsync all the time, but I rsync on the local machine from 1 drive to another for data redundancy.

What if I wanted to rsync to a new backup server, yet my desktop is Ubuntu and the backup server is Ubuntu. What would I do?

---

### Post by badger_fruit on 2009-09-21
> **Roasted said:**
> Just curious - how do you do this?

I rsync all the time, but I rsync on the local machine from 1 drive to another for data redundancy.

What if I wanted to rsync to a new backup server, yet my desktop is Ubuntu and the backup server is Ubuntu. What would I do?


[http://www.lmgtfy.com/?q=man+rsync](http://www.lmgtfy.com/?q=man+rsync)


Rsync is a generic application and the man pages will give you the information you want.

---

### Post by stumbleUpon on 2009-09-21
```

rsync yourOptions folderInPresentMachine/ destinationMachineIP:destinationFolder/

```

---

### Post by ownaginatious on 2009-09-21
I would suggest maybe mounting the drive you want to sync to automatically to the computer where rsync is running.

I'm kind of new to this, so I'm not sure if this will work, but maybe you can create a script that first mounts the drive of the server, syncs to it, and then unmounts it.

By mounting it to your computer where rsync is running, it should work just as you've been using it already.

---

### Post by badger_fruit on 2009-09-21
> **ownaginatious said:**
> I would suggest maybe mounting the drive you want to sync to automatically to the computer where rsync is running ..../snip

**No no no no no no!**

**With rsync you do not need to do this**!

If the mount fails for whatever reason, your rsync will work but, as the folder will be a local folder, the next time the share is mounted, the contents will be replaced with the mounted share.

To do an un-mounted rsync from Machine A to Machine B you need to create a shared SSH key otherwise, every time you try it will prompt for the password (no good for cron or scripting).

This website here ([http://hocuspokus.net/2008/01/ssh-shared-key-setup-ssh-logins-without-passwords](http://hocuspokus.net/2008/01/ssh-shared-key-setup-ssh-logins-without-passwords)) tells you how this is done and the Man pages (man rsync or use the URL --> [http://www.manpagez.com/man/1/rsync/](http://www.manpagez.com/man/1/rsync/)) will detail how to perform the sync.

---

### Post by Roasted on 2009-09-21
> **stumbleUpon said:**
> ```

rsync yourOptions folderInPresentMachine/ destinationMachineIP:destinationFolder/

```

So an example command would be:

rsync -r --delete /home/jason/ /192.168.1.101/media/storage/

???

Could I use the computer name instead of IP?

---

### Post by badger_fruit on 2009-09-21
> **Roasted said:**
> Could I use the computer name instead of IP?

Yes, although you'd have to ensure a correct DNS entry first
(check in **/etc/hosts**)

---

### Post by stumbleUpon on 2009-09-22
> **Roasted said:**
> So an example command would be:

rsync -r --delete /home/jason/ /192.168.1.101/media/storage/

???

Could I use the computer name instead of IP?

Make sure to have a colon between the IP number and the destination folder

```

rsync -r --delete /home/jason/  [COLOR="Red"]192.168.1.101:/media/storage/[/COLOR]

```

---

### Post by Roasted on 2009-09-22
Good deal guys. Thanks for the help!

---

### Post by Roasted on 2009-11-01
I'm confused over what I might be doing wrong here. Both machines have Samba installed and both machines are in the workgroup "workgroup". 

I even mounted the share on my skynet box to Area51, thinking maybe it was an authentication issue.

But I get:

jason@Area51:~$ rsync -r /home/jason/test/ 192.168.1.108:/home/jason/
ssh: connect to host 192.168.1.108 port 22: Connection refused
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(600) [sender=3.0.5]
jason@Area51:~$ 

192.168.1.108 is the IP of the "skynet" box. I tried to use it with skynet and also the IP. Both don't work.

---

### Post by ownaginatious on 2009-11-01
> **Roasted said:**
> I'm confused over what I might be doing wrong here. Both machines have Samba installed and both machines are in the workgroup "workgroup". 

I even mounted the share on my skynet box to Area51, thinking maybe it was an authentication issue.

But I get:

jason@Area51:~$ rsync -r /home/jason/test/ 192.168.1.108:/home/jason/
ssh: connect to host 192.168.1.108 port 22: Connection refused
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(600) [sender=3.0.5]
jason@Area51:~$ 

192.168.1.108 is the IP of the "skynet" box. I tried to use it with skynet and also the IP. Both don't work.

This works over SSH, not Samba. Make sure you have SSH installed on the target machine.

---

### Post by Roasted on 2009-11-01
> **ownaginatious said:**
> This works over SSH, not Samba. Make sure you have SSH installed on the target machine.

Bingo! Thank you.

How can I incorporate the ssh credentials into a script so I can just launch the script and it auto-run without having to log in?

---

### Post by ownaginatious on 2009-11-01
Just follow the beginning of [this]("http://pkeck.myweb.uga.edu/ssh/") tutorial; it's relatively straight forward. Good luck!

---

### Post by Roasted on 2009-11-01
Thanks. I'll check it out.

One last question:

> **badger_fruit said:**
> Yes, although you'd have to ensure a correct DNS entry first
(check in **/etc/hosts**)

Kind of a dumb question but I just have to ask - this machine should really be a static IP, right? Just with putting in host name + IP to /etc/hosts, if the IP changes, then the DNS wouldn't flow right (I assume). Is my train of thought right? Static?

---

### Post by ownaginatious on 2009-11-01
> **Roasted said:**
> Kind of a dumb question but I just have to ask - this machine should really be a static IP, right? Just with putting in host name + IP to /etc/hosts, if the IP changes, then the DNS wouldn't flow right (I assume). Is my train of thought right? Static?

Ya, the IP always has to be the same to work with the domain name. I have an IP that frequently changes, so I got a free dynamic DNS from no-ip.org. There is software that will automatically update it from your server at a regular interval (available in the Ubuntu repository as far as I remember). It's pretty cool :p.

---

### Post by Lars Noodén on 2009-11-02
> **ownaginatious said:**
> Just follow the beginning of [this]("http://pkeck.myweb.uga.edu/ssh/") tutorial; it's relatively straight forward. Good luck!

That looks useful.  One fine point to add regarding single-purpose keys is that if the connection is automated, it is a good idea on the remote host to have the authorized_keys file, .ssh directory, and home directory unwriteable by the remote user. 



```

# assuming that the account is 'budroe'
# the owner can be root or some other user 
# as long as it is not the automated account
# that has to be able to read, but not write

chown nobody:budroe /home/budroe
chmod 050 /home/budroe

chown nobody:budroe /home/budroe/.ssh/
chmod 050 /home/budroe/.ssh/

chown nobody:budroe /home/budroe/.ssh/authorized_keys
chmod 040 /home/budroe/.ssh/authorized_keys

```

You can see how rsync is run on the remote machine and which parameters are passed, but making the ssh connection manually while running the client in the debug mode using the -v, -vv, or  -vvv to set debug level 1, 2 or 3:

[INDENT][FONT="Courier New"]rsync -e "ssh -t -v" --rsync-path='sudo rsync' \
-av [email]bkupacct@www.example.org[/email]:/var/www/ /tmp/
[/FONT][/INDENT]

One of the lines produced during the connection will start with 'Sending command' e.g.
[INDENT][FONT="Courier New"]debug1: Sending command: sudo rsync --server --sender -e.iLs . /var/www
[/FONT][/INDENT]

Then you can restrict the user to a specific command by prepending [FONT="Courier New"]command="rsync...."[/FONT] to the key.  See [sshd](http://manpages.ubuntu.com/manpages/karmic/en/man8/sshd.8.html) for more details about modifying the key.  

Same for making a custom line in /etc/sudoers.

---

