---
title: "Network access to server periodically stalls, diagnosis suggestions?"
date: 2013-02-04
forum: Networking &amp; Wireless
---

### Post by pharcycle on 2013-02-04
Hello all,

I've got a server streaming media to my fronend client in my living room. Every so often when watching on XBMC, the video freezes. Sometimes it resumes after 5 seconds, sometimes longer, other times it causes XBMC to bail out the video after waiting about 30s to 1min and then has to be manually resumed.

I've got the folders on JFS partitions on the server mounted via NFS on my client and I can read, write and execute from them remotely all fine and dandy... usually

I'm using the latest version of Mythbuntu 12.04.1, fully updated on both machines.

I think it a network related problem as during periods of stalling, I can't access the folders (via Thunar) and if I have a VNC window to the server open then that doesn't respond either.

I use wired gigabit ethernet between the machines although the client is behind a netgear gigabit switch.

Its an intermittent issue so having written this post it may not do it again for a week but its been happening a lot recently.

I appreciate that there is probably not enough info to offer any kind of solution but I'm just after some help diagnosing the issue. Are there any recommended monitoring tools I could download and have run constantly for example on the client/server or any logs recommended to check when it happens next?

I could set up the two machines just on their own switch but as I said, its an intermittent issue, so even if it worked for a week like that, I still couldn't be sure if that had fixed it! Not to mention the inconvenience of no internet access on either of them for the duration!

My network tree is as follows:

```

Virgin Media Cable modem (integral 4-port GBit switch)
->HTPC server
->Living room 1 GBit NETGEAR switch
  -> Frontend HTPC
  -> XBOX 360
  -> PS3
  -> Raspberry Pi
->Upstairs 100 MBit NETGEAR switch
  -> Main PC

```

The problem is evident even when the 2x HTPCs are the only devices powered up on the network (except the switches and modem)

I've reinstalled mythbuntu on both the client and server machines and the problem has remained.

Any help greatly appreciated.

Thanks

---

### Post by TheFu on 2013-02-04
I've seen USB storage lock up machines when too many programs made requests around the same time - 20-30 seconds, the entire machine would appear to be locked up.  
This applies to USB2 and USB3 storage.

What to the system logs show? Any warnings or errors?
I figure since you got MythTV working, that you know your way around.  My 3 attempts with Myth have always failed. Humbling.

Also, if you are trying this over wifi, know that wifi is not a good way to stream anything. Too many variable that are outside our control to make it worth the effort.

---

### Post by pharcycle on 2013-02-04
Hi,

thanks for the suggestions.

These are SATA II drives internal to the server and the network is all wired. I too have had too many issues with wifi to bother any more! Streaming live HD content for example can be up to 50Mbit/s so you'd need to be on N wifi at the very least and yes, walls, people moving around, magneto-ignition scooters etc all cause intermittent issues.

RE: mythtv, I kind of cheated and just went with the mythbuntu distro! I could get almost everything working using a standard ubuntu install and putting myth on top of it but could not get my head around the mysql permissions and so forth that it needed.

next time it freezes, I'll have a look at XBMC logs and dmesg. are there any specific logs for networks in /var/logs?

Thanks

---

