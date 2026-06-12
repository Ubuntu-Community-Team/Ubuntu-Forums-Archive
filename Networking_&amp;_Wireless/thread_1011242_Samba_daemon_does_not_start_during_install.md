---
title: "Samba daemon does not start during install"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by pwrstick on 2008-12-14
I've been having problems with Samba after upgrading Ubuntu (cli, no gui) from 6.x to 8.10.  Everything else works great except for Samba (networking is fine - I can ssh into the box to troubleshoot Samba).

Being a Windows dude I eventually uninstalled/reinstalled the package, and when it gets to "* Starting Samba daemons" it just hangs there.

I did a testparm on my config and it checks out.

Any ideas why its hanging?

```
philip@files:/etc/samba$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  samba-doc openbsd-inetd
Use 'apt-get autoremove' to remove them.
Suggested packages:
  smbldap-tools
The following NEW packages will be installed:
  samba
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4369kB of archives.
After this operation, 12.2MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 28770 files and directories currently installed.)
Unpacking samba (from .../samba_2%3a3.2.3-1ubuntu3.3_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ufw ...
Setting up samba (2:3.2.3-1ubuntu3.3) ...
Generating /etc/default/samba...
 * Starting Samba daemons

```

---

### Post by pwrstick on 2008-12-14
Interesting - the daemon eventually loaded!  I just left it there, and now if I restart samba it loads very quickly.

However, I am having problems now getting to the shares I have in smb.conf.  I'm accessing them via a Windows box, and it just times out.

On the Ubuntu box I did the following:
```
sudo smbclient -L 127.0.0.1
timeout connecting to 127.0.0.1:445
timeout connecting to 127.0.0.1:139
Connection to localhost failed (Error NT_STATUS_ACCESS_DENIED)
```
Those must be samba ports?  I wonder if the smbd daemon is loading correctly.  It *is *showing up from a "sudo ps -A | grep smbd" command (twice).

The log.smbd mentions something about not being able to start the CUPS server, but I don't even have cups setup in my smb.conf.

Very confused.

---

### Post by Tilex on 2008-12-14
I've got exactly the same problem.

And when I try to restart Samba, it says it "can't kill the process", as if the Samba daemon wasn't loaded.

> 
alex@itx-technologies:~$ sudo /etc/init.d/samba restart
 * Stopping Samba daemonsstart-stop-daemon: warning: failed to kill 9639: No such process
                                                                                                                                                 [ OK ]
 * Starting Samba daemons                                                                                                                        [ OK ]


---

### Post by pwrstick on 2008-12-14
> **Tilex said:**
> I've got exactly the same problem.

And when I try to restart Samba, it says it "can't kill the process", as if the Samba daemon wasn't loaded.

Interesting - I had restarted it before successfully, but I just did so again (after waiting 20 minutes or so) and got the same error you got: No such process.

It must not be loading correctly...

---

### Post by pwrstick on 2008-12-14
Here's an old thread where they had this problem.  Didn't help me, but maybe helps you?
[http://ubuntuforums.org/archive/index.php/t-465081.html]("http://ubuntuforums.org/archive/index.php/t-465081.html")

---

### Post by pwrstick on 2008-12-15
Bumpification.  Hoping to get some more coverage on this - the solution eludes me!

---

### Post by pwrstick on 2008-12-15
OK... weird, I guess this is a more general networking question?  I didn't even think to get this basic because, well, because I'm ssh'ing into the troubled box, so I figured networking is running just fine.

However, while ssh'd into the machine (named files), all of these fail:

ping files (resolves to 127.0.1.1)
ping 127.0.0.1
ping 10.10.10.10 (the ip address of the NIC, eth2)

How is *that* possible?! Lol! :p

---

### Post by pwrstick on 2008-12-15
I discovered that my loopback interface was not starting correctly at boot, and while that is a separate issue I am now going to work on, I at least know that there is nothing wrong with Samba.

So, if your Samba daemon is stalling at load (you don't get an [OK] at boot or at "sudo /etc/init.d/samba restart"), be sure to ping 127.0.0.1 or localhost and see if you get a result.  If not, perhaps a ```
sudo ifconfig lo up
``` is in order to bring up your lo.

May also want to check out "[Troubleshooting: The Samba Checklist]("http://us6.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html")"

Now I just have to figure out why lo is down at boot... but SAMBA WORKS! Transferring files files off my NAS at over 100MB/s!  :guitar:

---

### Post by myoldhouse on 2009-01-16
Another thing that can prevent smbd (the smb daemon) from starting is if the file /var/lib/samba/secrets.tdb is bad or corrupt. The solution is to delete the secrets.tdb file and restart samba with:

sudo /etc/init.d/samba restart

then do a:

sudo /etc/init.d/samba status

and you should get:

* nmbd is running.
* smbd is running.

Fixed my issues with not being able to share folders via Nautilus. Samba recreates the secrets.tdb file when it restarts so there is no harm in trying this if other trouble shooting techniques don't work. I got this tip from the Launchpad bug # 302605

---

