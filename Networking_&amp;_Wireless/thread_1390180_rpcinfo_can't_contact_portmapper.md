---
title: "rpcinfo can't contact portmapper"
date: 2010-01-25
forum: Networking &amp; Wireless
---

### Post by tholy on 2010-01-25
I've reported this as a bug (#507546), but it occurs to me that maybe others aren't having the same problems, so maybe it's an issue with the configuration of my machine.

I upgraded to Kubuntu 9.10 (Karmic) from Jaunty. Ever since the upgrade, I'm getting a number of weird networking problems (though basic webbrowsing & email work fine):
1. I can't mount an NFS partition, one that has worked on this laptop with every previous version of Kubuntu, and one that still works on other computers. If I do
$ sudo mount /usr/lab
I get
mount.nfs: rpc.statd is not running but is required for remote locking.
mount.nfs: Either use '-o nolock' to keep locks local, or start statd.

So then I do this:
$ sudo start statd
and get this:
statd start/running, process 18709

Then this happens again:
$ sudo mount /usr/lab
mount.nfs: rpc.statd is not running but is required for remote locking.
mount.nfs: Either use '-o nolock' to keep locks local, or start statd.:

but
$ sudo start statd
start: Job is already running: statd

so then I do this:
$ rpcinfo -p
and it hangs for something pretty close to 3 minutes and then says this:
rpcinfo: can't contact portmapper: RPC: Remote system error - Connection timed out

See also this:
$ ps ax | grep port
18017 ?        Ss     0:00 portmap
18878 pts/27   R+     0:00 grep port

Note that the 3-minute hang with rpcinfo -p also happens if I do not attempt to manually start statd first.


2. Whenever I try to print something from okular, the window freezes for about 3 minutes and then the print dialog comes up. The printers I want (network printers) are not shown in the list.

3. My department uses Retrospect (commercial closed-source software, sorry) for backups, and I haven't been backed up since I upgraded. The problem, again, is that when I try to start the backup client it hangs for about 3 minutes but then fails to come up.

4. And some new information not in my bug report: I've noticed that certain (but not all) OOo Impress presentations cause Impress to freeze for about, you guessed it, 3 minutes before the window opens. I just copied one of the troublesome presentations over to another Kubuntu Karmic machine, and it opens fine there. I believe that machine can also mount NFS partitions without trouble.

So it smells like some pervasive networking/communications problem specific to the configuration of my own laptop. But, I don't really know where to start. This has never been a problem before, and I don't think my networking setup is extensively tweaked. I'd be happy to provide more information, if I knew what to provide.

Thanks very much in advance for your help!

---

### Post by tholy on 2010-01-26
I had switched to managing my network with wicd, because I was using a hidden SSID. It turns out wicd was not configuring the loopback interface ("lo" was absent from the list when I typed "ifconfig" from the command line). I switch back to network manager, and the weird problems seem to have vanished.

---

