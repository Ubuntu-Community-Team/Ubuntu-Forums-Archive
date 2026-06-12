---
title: "NFS Not Starting at Boot(?)"
date: 2009-06-27
forum: Networking &amp; Wireless
---

### Post by SeanOB on 2009-06-27
Hi,

It looks like NFS is not starting for me at boot. I'm not sure if it's starting or not -- but I'm guessing that it isn't starting. I might be wrong - since a 'restart' fixes it and it doesn't complain about stopping the nfs kernel on a restart.

When I try to access my nfs shares from a remote machine I get a 'access denied by server while mounting' error.
And I can fix this by simply going to my nfs server and typing:
sudo /etc/init.d/nfs-kernel-server restart

Where I see no issues:
 * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
 * Exporting directories for NFS kernel daemon...                        [ OK ] 
 * Starting NFS kernel daemon                                            [ OK ] 

Once I restart the server everything is groovy - and my clients have access again.
Any ideas of what's going on?

This is with 09.04.

Thanks!

-Sean

---

### Post by jhannah on 2009-06-28
What do you get from '/etc/init.d/nfs-kernel-server status' when you first boot up? Since it reports OK, it sounds like the server is starting on boot. If that isn't the case, you can add it with 'update-rc.d nfs-kernel-server defaults' but it should automatically be added once you install it. You should also check the status of the portmap service with '/etc/init.d/portmap status' and add that too if it is missing.

Provided it is starting on boot, do you see anything in /var/log/messages or /var/log/daemon.log? Try the below commands and see what results you get before restarting the service:

```
grep -Hi nfs /var/log/messages /var/log/daemon.log
```

---

### Post by SeanOB on 2009-06-29
Thanks for the help...

On Boot:
```
> sudo /etc/init.d/nfs-kernel-server status
nfsd running
```

```
> grep -Hi nfs /var/log/messages /var/log/daemon.log
/var/log/messages:Jun 28 20:19:49 foo kernel: [   20.445675] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
/var/log/messages:Jun 28 20:19:54 foo kernel: [   26.659199] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
/var/log/messages:Jun 28 20:19:54 foo kernel: [   26.664320] NFSD: starting 90-second grace period
```

Attempted connection from remote client... FAILED.

Restart:
```
>  sudo /etc/init.d/nfs-kernel-server restart
 * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
 * Exporting directories for NFS kernel daemon...                        [ OK ] 
 * Starting NFS kernel daemon                                            [ OK ] 

```

```
> sudo /etc/init.d/nfs-kernel-server status
nfsd running
```


Attempted connection from remote client - SUCCESS!

Any other logs to look at?

Thanks again for the help!  Remembering to run my 'fixnfs' alias to restart nfs on every reboot is a pain...

-Sean

---

### Post by SeanOB on 2009-07-23
I think that I know what the issue is - but I don't know how to resolve it cleanly.

I believe that its a permissions issue - where I have the resolved network names of the machines in my /etc/exports rather than the ip addresses.

I have something like:
```
/home myhappymachine(rw,sync,no_subtree_check) clientmachine(rw,sync,no_subtree_check)
```

Rather than:
```
/home 192.168.0.10(rw,sync,no_subtree_check) 192.168.0.11(rw,sync,no_subtree_check)
```

My router uses DNSmasq - and everything is resolved through that DNS server.  My theory is that when I boot my server that it doesn't (yet) know the resolved names.  But once booted - restarting the nfs server works because at that point it does know the names.

So 2 possible fixes:
1) just use IP addresses
2) figure out the order that the services start - and put the service that resolves the names before the nfs daemon start

Option 1 looks much easier!

-Sean

---

### Post by darrelsanchez23 on 2009-11-17
[B]is there another way how to start automatically the NFS server??

and is there a way to mount the shared directory from the server automatically at boot up for the client machine??


pls help...tnx[/B]

---

