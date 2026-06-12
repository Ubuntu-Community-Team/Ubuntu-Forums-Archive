---
title: "Windows vs. Ubuntu @Transferring Files"
date: 2012-07-12
forum: Networking &amp; Wireless
---

### Post by uRock on 2012-07-12
Is there a conf file I need to mess with on my Ubuntu machines to make them transfer at the same speed as Windows? I have never been able to get Ubuntu to transfer at more than 3MB/s while transferring files between two Ubuntu machines, yet I started a transfer using Windows to Ubuntu machines and it maxed out at 100Mb/s. As you can see in the screenshot, I had a file transfer going between the two ubuntu machines, then through in the transfer from the Windows machine.

I know hardware isn't the issue here, so I am wondering what must be changed to keep up with the non-ubuntu machine.

---

### Post by OM55 on 2012-07-13
How are you setting the shared folder? Is it with Samba on the Ubuntu machine or a Windows share on the Windows machine? (which is the host machine).
Also, is the partition you are transferring the files to, formated NTFS?

To explain:
Sabma server can be fine tuned to achieve much better speeds than the default settings.
The configuration file is smb.conf and there is a lot of online info and manuals with specific directions on that. I can provide some links if you need and if that is the case.

More important - When Ubuntu is transferring files to an NTFS drive, it uses a special ntfs process that serves ALL ntfs requests and as a result is quite slow. Typical transfer between two Ubuntu machines (formatted Ext4 for example is 30% or more faster than Windows on a single large file).

But you are describing a speed difference in a factor of 30! which is way too much. So I would suggest also to look at the network driver Ubuntu uses. could be that tye default setting is hurting the transfer speed.

---

### Post by uRock on 2012-07-13
The host machine is ubuntu with a shared NTFS drive. The transfers I was doing last night were uploading files from other machines on the network. The Windows 7 machine topped out at 100 Mb/s and the ubuntu upload was around 15Mb/s(less than 2MB/s) for the ubuntu to ubuntu upload.

When I was running the ubutu to ubuntu upload last night I was using a wireless connection. By trying to uplooad with a wired connection with the same uploading host, the speed increased to 5MB/s (45Mb/s). While that is much faster, it still isn't comparable to the upload from the Windows machine.

The links you mentioned sound great and I would like to check them out.


Thanks!

---

### Post by OM55 on 2012-07-13
As I mentioned, using Ubuntu with NTFS formatted drive will be noticeably slower than with EXT4 formatted drive due to the single ntfs process that will run (you can check the process list during the copy and you will see it and how much it takes of the CPU time).

Having TWO Ubuntu machine do that at the same time - doubles the delay, and that would be one reason for the slow transfer speed you experience.
Until you switch the drives on both machines to EXT4 you wont be able to do much about that problem.

As for Samba, here are some links discussing parameters you can tweak to improve the transfer speed:
[http://oreilly.com/openbook/samba/book/appb_02.html](http://oreilly.com/openbook/samba/book/appb_02.html)

Some examples:
[http://www.randombugs.com/linux/speed-up-samba-under-linux.html](http://www.randombugs.com/linux/speed-up-samba-under-linux.html)

Mounting options:
[http://ubuntuforums.org/showthread.php?t=1213688](http://ubuntuforums.org/showthread.php?t=1213688)

There are many other links on the web about speeding up and fine tuning Samba.

Hope that helps.

---

### Post by OM55 on 2012-07-13
Here another link the summarizes some of the Samba options to tweak. Also, very important - the logging level (see at the bottom). If you reduce it to a minimum you will save a lot of time on the transfer!

[https://calomel.org/samba_optimize.html](https://calomel.org/samba_optimize.html)

---

### Post by uRock on 2012-07-13
Thanks for the links. I will make up a diagram, which may be more helpful in the explanation of my setup, the next time I get a chance to fire up PacketTracer.

---

### Post by maestrobwh1 on 2012-07-13
Make sure, if the partition is in fstab, that you do not have "sync" in the options field.  That REALLY bogs down vfat and ntfs transfers.

my options for my ntfs partition are as follows:

defaults,recover,compreession,noatime,shortname=winnt,windows_names,uid=1000,gid=1000 0   0

---

### Post by papibe on 2012-07-13
Hi uRock.

I can easily get 9GB/s on a 100Mb/s network, connecting a 10.04 server with a 10.04 desktop.

By any chance the Ubuntu's have different versions, or maybe different samba versions?

Regards.

---

### Post by uRock on 2012-07-13
> **papibe said:**
> Hi uRock.

I can easily get 9GB/s on a 100Mb/s network, connecting a 10.04 server with a 10.04 desktop.

By any chance the Ubuntu's have different versions, or maybe different samba versions?

Regards.

I have been having this problem with multiple machines with ubuntu over the past few years. I haven't got into checking things out yet. Still winding down from a long day at work.

---

### Post by papibe on 2012-07-13
I see.

Have you test the raw network transfer rate? (using [iperf]("http://askubuntu.com/questions/7976/how-do-you-test-the-network-speed-betwen-two-boxes") for instance).

After checking the graph, it looks like the the copy can't hold fast ethernet speeds and is defaulting to 10Mb/s.

Just a thought.
Regards.

---

### Post by uRock on 2012-07-13
> **papibe said:**
> I see.

Have you test the raw network transfer rate? (using [iperf]("http://askubuntu.com/questions/7976/how-do-you-test-the-network-speed-betwen-two-boxes") for instance).

After checking the graph, it looks like the the copy can't hold fast ethernet speeds and is defaulting to 10Mb/s.

Just a thought.
Regards.

iperf was a great idea for finding the capabilities. ```
[  3] local 192.168.254.252 port 37280 connected with 192.168.254.253 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec   114 MBytes  95.1 Mbits/sec

```

---

### Post by uRock on 2012-07-15
I have added the following to the smb.conf file and it is still moving at 2MB/s. I only have this problem when it is ubuntu TXing/uploading/sending to another host. When Windows is serving it does so at max hardware speed.```
read size = 65536
read prediction = true
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
write raw = yes
read raw = no
max xmit = 65535
```

---

### Post by papibe on 2012-07-15
Your raw transfer rate seems to be OK, but I always test using a bigger bytes amount just to make the transfer run for a longer period of time. For instance:
```
iperf **-n 1g** -c server
```

> **uRock said:**
> I have added the following to the smb.conf file and it is still moving at 2MB/s.
That's is interesting since you effectively reduce your speed to half from your wired example on post #3.

May be playing with other socket values and options could be helpful. Have you try matching your 'read size' with tcp buffer size?.  Here is another [values and options]("http://ubuntuforums.org/showpost.php?p=9949119&postcount=2") you may use.

Another source of slowness (long shot but...) could be an incorrect [MTU]("http://ubuntuforums.org/showthread.php?t=872346") value. 

Sorry if it not much of a help, but may be some of these ideas may hint you in the right direction.
Regards.

---

### Post by uRock on 2012-07-15
> **papibe said:**
> Your raw transfer rate seems to be OK, but I always test using a bigger bytes amount just to make the transfer run for a longer period of time. For instance:
```
iperf **-n 1g** -c server
```


That's is interesting since you effectively reduce your speed to half from your wired example on post #3.

May be playing with other socket values and options could be helpful. Have you try matching your 'read size' with tcp buffer size?.  Here is another [values and options]("http://ubuntuforums.org/showpost.php?p=9949119&postcount=2") you may use.

Another source of slowness (long shot but...) could be an incorrect [MTU]("http://ubuntuforums.org/showthread.php?t=872346") value. 

Sorry if it not much of a help, but may be some of these ideas may hint you in the right direction.
Regards.
The current transfer is going from Ubuntu to Windows. Not sure how to run iperf on Windows. I am working on another install with ubuntu business, which will need the same 12GB transfer. I'll mess with the smb.conf some more before starting that one.

Thanks for helping.:D

---

### Post by uRock on 2012-08-05
I have found that it is my router setting these speeds. I can't wait to get my CCNA home lab equipment, so that I can have full control of how much bandwidth my LAN can use.

---

