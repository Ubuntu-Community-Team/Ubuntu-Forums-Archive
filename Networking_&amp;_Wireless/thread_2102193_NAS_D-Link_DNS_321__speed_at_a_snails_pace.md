---
title: "NAS D-Link DNS 321  speed at a snails pace"
date: 2013-01-06
forum: Networking &amp; Wireless
---

### Post by jpaulb on 2013-01-06
I have a D-Link DNS 321 mounted using the following in fstab

192.168.0.14:/Volume_1        /mnt          cifs  guest,_netdev,noperm  0  0 
192.168.0.14:/Volume_2        /mnt/Backup     cifs  guest,_netdev,noperm  0  0

The NAS settings are
LAN SETTINGS :  Speed 100 Mbps
JUMBO FRAME SETTINGS : enabled
MTU 9000

The fastest file transfer speed it has achieve is about 2 MB/sec upload and 6MB/sec download. Is this the limit for this box or is there a way to get little more speed out of it?

---

### Post by jpaulb on 2013-02-22
Hallo any one out there??
Am I the only one with a D-Link DNS 321?

---

### Post by varunendra on 2013-02-23
> **jpaulb said:**
> Am I the only one with a D-Link DNS 321?
Apparently not. Just search the forums with keyword "DNS-321" or variations of it). However, I couldn't find any promising one about speed issues, so guess I'll try my wits here.
(but first you should try searching the forums as I suggested above)

At the first glance, that looks a bit suspicious to me -
> **jpaulb said:**
> MTU 9000
What OS the NAS runs upon? Can you run shell commands on it? ifconfig?

If yes, I'd like to see outputs of ifconfig on both NAS and the client PC.

If not, try setting it to 1500 on NAS, and default on the client PC. You may also try 1492 on the NAS, and turning Jumbo Frames off. Although higher MTU and Jumbo Frames are supposed to enhance speeds, but may also adversly affect it if any of the devices on the network doesn't support them or have bottolnecks.

---

### Post by jpaulb on 2013-02-24
Thanks

I set lan speed to auto, choices 10, 100 or auto. Set Jumbo frames to disabled there was a slight increase in speed from 7MB/s  to about 10 MB/s

---

### Post by varunendra on 2013-02-24
> **jpaulb said:**
> there was a slight increase in speed from 7M**[COLOR="Red"]B[/COLOR]**/s  to about 10 M**[COLOR="Red"]B[/COLOR]**/s
Are you sure it is MB/s not Mb/s ? Because LAN card speeds are given in Mb/s.

b = bit
B = Byte = 8 bits

If the current speed is in MB/s, then consider it the max you can get on that interface.

---

### Post by jpaulb on 2013-02-24
Thanks
Down loading a 1.9GB file from the DNS-321 to the main Hdd required 225 seconds about 8.4MB/sec uploading the same file required 685 seconds about 2.7MB/s. Quite a difference in read and write 

I  got one thing straight the switch and router is rated in Mb/s and the files MB/s

Any suggestion on how to speed up the write process.

---

### Post by varunendra on 2013-02-24
> Any suggestion on how to speed up the write process.
Not much except a few wild shots.

First one is to try a test partition with ext3/4 or a better, natively supported filesystem.

From what I know (and am open to new revelations), cifs is for ntfs filesystem which is not very well supported by Linux. The commonly used ntfs-3g driver is known for its poor write performance, and I guess the same or a similar driver is being used by the NAS OS/firmware as well.

---

