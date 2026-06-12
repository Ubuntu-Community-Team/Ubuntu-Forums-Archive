---
title: "Wireshark problem"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by Just64 on 2009-05-09
Wireshark cant detect my interface, why is this? I have a MSI PR200. Could be that my interface is hiden?

---

### Post by recrispi on 2009-06-04
Hello

I have the same problem. I'm using a Dell Inspiron 6400 and Ubuntu 8.04.
Just64 which is your Ubuntu version?
Thanks for any help.

Update:
This question was answered in the following threads:
[http://ubuntuforums.org/showthread.php?t=1108311&highlight=wireshark](http://ubuntuforums.org/showthread.php?t=1108311&highlight=wireshark)
[http://ubuntuforums.org/showthread.php?t=1086288&highlight=wireshark](http://ubuntuforums.org/showthread.php?t=1086288&highlight=wireshark)
[http://ubuntuforums.org/showthread.php?t=870206&highlight=wireshark](http://ubuntuforums.org/showthread.php?t=870206&highlight=wireshark)
Running Wireshark as normal user shows no interfaces. It needs the propper permissions, as running it as root (warning, insecure) or with the tweak found here:
[http://wiki.wireshark.org/Security#head-ac69042aeeb98cdaed2ec2ff1bd2c983fa03cffd](http://wiki.wireshark.org/Security#head-ac69042aeeb98cdaed2ec2ff1bd2c983fa03cffd)

I'll try it at home tonight.

---

### Post by jonobr on 2009-06-04
if you start wireshark using sudo, do you see it then?

```
sudo wireshark
```

are your doing wireless and not seeing the output?

---

### Post by recrispi on 2009-06-04
Hello!

I've just tryed it.
Yes, running wireshark as root allows me to see all interfaces, but it also is risky.
Following the instructions given in one the links above works fine. The recommendation was to run command:
sudo dumpcap -w ./dumpfile
and later open the file dumpfile with wireshark as normal user so you can filter it as you wish.
I was just trying to run wireshark on my wired ethernet card. Anyway, I think it has solved my problem.
And now to study my network activities :-)

---

### Post by jonobr on 2009-06-05
Hello


You could also capture the output to a file and then open as non root in wireshark for inspection

Heres how you could do it

```
tcpdump -w mytrace.pcap -s 1550 -i any port 80
```

Where -w defines the output file (in this case mytrace.pcap)
-s is the the packet size to capture.
-i is the interface to use, in this case, any, or you could have eth0 etc
port = limits the capture to a certain port in this case 80.

You will have a file created when you stop the capture,
You can then open this with wireshark

---

