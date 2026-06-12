---
title: "Setting Up Wireshark Capture"
date: 2011-10-24
forum: Networking &amp; Wireless
---

### Post by just_ken_here on 2011-10-24
I have some question regarding wireshark.
I saw this on their support page :
> 
On Linux, you need to have "packet socket" support enabled in your  kernel; see the "Packet socket" item in the Linux "Configure.help" file.   Your distribution might enable this by default in the kernel.

Can anyone tell me where in Ubuntu is the Configure.help mentioned.

That's all for now.
thanks.

---

### Post by lisati on 2011-10-24
Wireshark is available in the repos. If you install it from synaptic or software centre, you shouldn't need to worry about where the config. files are.

---

### Post by just_ken_here on 2011-10-24
Yeah.. But it says I could not capture anything : "You didn't specify an interface on which to capture packets."

And when I clicked on interface list.. It doesnt show anything.

I ran Ubuntu 10.10.
Is there any other package/dependecies to set up ?

Thank u.

---

### Post by Dangertux on 2011-10-25
try running it with

```

gksudo wireshark

```

Hope that helps.

---

### Post by jonobr on 2011-10-25
If your still having trouble,
you could also capture on command line and view in wireshark.

eg

```
sudo tcpdump -w trace.pcap -s 1600 -i eth0 
```

This will run tcpdump where
-w specifies a file to dump to, (in this case trace.pcap) which wireshark can open,
-s changes the capture size from default 64 bytes to 1600. If you don't change this all packets will appear truncated.
-i specifies an interface , in this case, eth0.

You can get crafty with your capture command line by specifying port numbers, protocol types, host names or IP addresses etc.

When the trace has been ran, control c to stop and open using wireshark.
Wireshark is good however, for watching packets in realtime,
You can do that with tcpdump also using the -v (verbose) option, however, thats not as good as wireshark

---

### Post by psrdotcom on 2011-10-25
After installing the wireshark, select the interface to capture the network. Then click on start capture .. to capture the packets ..

---

### Post by pyro.xyz on 2012-08-27
Hey, I want the same thing, to be able to find the configure.help file, again for wireshark, but it would be nice to know about it for future reference.

---

### Post by linuxexplore on 2012-11-29
You can also see the small tutorials on tcpdump and wireshark:

[Use tcpdump to capture in a pcap file (wireshark dump)]("http://linuxexplore.com/2012/06/07/use-tcpdump-to-capture-in-a-pcap-file-wireshark-dump/")

[Remote packet capture using WireShark & tcpdump]("http://linuxexplore.com/2010/05/30/remote-packet-capture-using-wireshark-tcpdump/")

Cheers,
Linux Explore | Exploring Linux

---

