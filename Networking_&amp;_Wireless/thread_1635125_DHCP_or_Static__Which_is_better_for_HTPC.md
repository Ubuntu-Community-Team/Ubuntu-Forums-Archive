---
title: "DHCP or Static?  Which is better for HTPC?"
date: 2010-12-01
forum: Networking &amp; Wireless
---

### Post by fogNL on 2010-12-01
I have a Zotac MAG computer in my living room acting as my HTPC.  It connects to my network via WPA2 Wireless connection.  On my router (dd-wrt), I have statically set DHCP address list so that my HTPC always gets 192.168.1.6.

I've been noticing that often I have failed services on boot up due to the network connection not being completely established at the time when they try to start (such as SabNZBD).  So, I was thinking that maybe setting up the HTPC with a static address may be faster than "negotiating" DHCP with the router.  Would this help my issue?

I was originally thinking that pushing the affected services to towards the end of the bootup process, however, as it stands right now, my system starts, boots into Openbox and launches Boxee which sometimes reports theirs no internet connection yet.  So, it seems it takes my system a long time to get the connection active.

---

### Post by gordintoronto on 2010-12-01
Is it running Ubuntu 10.10?  On my computer, the DHCP connection with 10.10 takes a small fraction of the time it took in previous versions, maybe 1 second instead of 10 seconds. I'm also using wpa security.

---

### Post by fogNL on 2010-12-02
> **gordintoronto said:**
> Is it running Ubuntu 10.10?  On my computer, the DHCP connection with 10.10 takes a small fraction of the time it took in previous versions, maybe 1 second instead of 10 seconds. I'm also using wpa security.

Sorry, probably should have mentioned that.  Its Ubuntu 10.04 32bit as installed by XBMCFreak cd.

---

### Post by AgentZ86 on 2010-12-02
> **cquilliam said:**
> I have a Zotac MAG computer in my living room acting as my HTPC.  It connects to my network via WPA2 Wireless connection.  On my router (dd-wrt), I have statically set DHCP address list so that my HTPC always gets 192.168.1.6.

I've been noticing that often I have failed services on boot up due to the network connection not being completely established at the time when they try to start (such as SabNZBD).  So, I was thinking that maybe setting up the HTPC with a static address may be faster than "negotiating" DHCP with the router.  Would this help my issue?

I was originally thinking that pushing the affected services to towards the end of the bootup process, however, as it stands right now, my system starts, boots into Openbox and launches Boxee which sometimes reports theirs no internet connection yet.  So, it seems it takes my system a long time to get the connection active.

I would think that assignment of a free IP by default of the DHCP to the HTPC would be faster because it will request and IP and recieve with no intermittent cycle.The PC will simply receive and apply.
With reserving the IP within the DHCP range of the router I would think that the router will still send out IP's on the network via DHCP but then has to wait for the computer to receive the acceptable IP which is reserved so I would think it may cycle somewhat until the parameters are met. As oppose to the router just sending out the first available IP within the DHCP IP range, and having the first computer sending the request to accept any old IP address.

I don't really know the ordering process for DHCP with a reserved address vs DHCP default.

But surely turning off the reserved IP in the router to examine the connection results may shed some light on subject a little

Happy hacking

---

### Post by AgentZ86 on 2010-12-02
Oh and one last thing

Typically DHCP is probably better for HTPC and I don't see a need for having a static

However, it depends on your setup and if your using it as a file server or movie server also. In this case you may need to have a static IP for folder sharing etc.

Also if you set your workgroup names all the same then you would also not really need a static because you could share file/folder with the whole network by way of workgroup shares.

Anyhow thats all I know

---

### Post by fogNL on 2010-12-02
> **AgentZ86 said:**
> Oh and one last thing

Typically DHCP is probably better for HTPC and I don't see a need for having a static

However, it depends on your setup and if your using it as a file server or movie server also. In this case you may need to have a static IP for folder sharing etc.

Also if you set your workgroup names all the same then you would also not really need a static because you could share file/folder with the whole network by way of workgroup shares.

Anyhow thats all I know

I'll check out your earlier suggestion on shutting off the static ip address to see if it makes any difference.

However, in the long run, I do really need the static IP due to multiple services running on my HTPC that I access from outside of my local lan, therefore have certain ports forwarded (gui's from my cell phone to control things for example)

---

### Post by AgentZ86 on 2010-12-04
> **cquilliam said:**
> I'll check out your earlier suggestion on shutting off the static ip address to see if it makes any difference.

However, in the long run, I do really need the static IP due to multiple services running on my HTPC that I access from outside of my local lan, therefore have certain ports forwarded (gui's from my cell phone to control things for example)

I see, so static should not really cause a failure though even though it could be speculated to take a few nano seconds longer to sync with the router and internet etc. 

I'm not sure why it would fail, but at least if you try it to allow the dynamic then you can at least note the differences if any and diagnose from further from there.

---

