---
title: "wireshark can't save captures"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by gregnorc on 2010-02-08
I've run into a sort of catch 22.

I installed wireshark via apt-get on my Eee 1008HA, but when it is launched, it does not allow any capture interfaces. I think this is because the shortcut created in my applications paneldoes not start it as root.

So I went into terminal, typed in "sudo wireshark" and it popped up, as root. I was then able to capture on my wireless interface. However, if I try and specify my home folder as the location for the capture to be saved, I get an error that permission was denied, which seems odd since the process is running as root and should be able to do pretty much whatever it wants.

How can I get wireshark set up so I can both capture _and_ save the .pcap files I generate?

I'm running karmic koala, the full output of uname -a is: Linux ruckus-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux.

---

### Post by suseendran.rengabashyam on 2010-02-10
Hi,

Enter the following commands in the terminal:

```
sudo apt-get install libcap2-bin

sudo setcap cap_net_raw=+ep /usr/bin/dumpcap
```

Now access Wireshark from Applications->Internet, see whether you can capture on an interface and save the .pcap files in your home folder.

Let me know if this helps.

---

