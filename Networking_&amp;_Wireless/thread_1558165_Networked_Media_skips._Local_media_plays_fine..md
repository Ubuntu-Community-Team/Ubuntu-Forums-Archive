---
title: "Networked Media skips. Local media plays fine."
date: 2010-08-21
forum: Networking &amp; Wireless
---

### Post by p0p0a on 2010-08-21
Hi, I've been running Ubuntu for years on a Laptop designed for ubuntu. A few days ago, I decided to switch to Lubuntu to save resources. I have a network consisting of the Laptop mentioned and another computer which is still running Ubuntu. The Ubuntu computer has samba shares that I wanted to access to play media from the laptop. I didn't install samba on the laptop but edited fstab with

//server/share /media/samba cifs user=guest,uid=1000,gid=100,noperm 0 0

to add each share I wanted to mount. For some reason, I still have to mount them manually at boot using

mount /media/share

This isn't a big deal, the real problem is that all my media skips on average once per every 2 minutes (especially once near the beginning) if played from the samba shares. If I copy that same media to my local hard drive however, it will play fine.

Just to clarify, I've run Ubuntu for years on this system with no problem. This problem just arose when I installed Lubuntu. Also: My wireless network hasn't changed during this period either, it's been a high quality wireless N network the whole time.

Any help would be appreciated. Thanks.

---

### Post by LightningCrash on 2010-08-21
install ifstat

play some media from the samba share, make sure it's >1min worth
run `ifstat 5 20` in a terminal
paste the results here

get us a copy of your `iwconfig` output as well.... but do it **during** the playback. sometimes wireless speeds negotiate dramatically lower once you saturate the link

on a related note, i had my wireless crap out one time... everything I did was slow, the Internet, copying from the fileserver, VNC, everything! Everyone in the neighborhood was on channel 6 (go figure) and I was on 12, i had never had any problems until then. When it crapped out I noticed it started connecting at 5mbps :P
Turns out one other AP had popped up on 12. I switched to channel 1 and I was back to 54mbps immediately.

---

### Post by p0p0a on 2010-08-21
there are no networks in range of me but I'll try that

---

### Post by p0p0a on 2010-08-21
:~$ ifstat 5 20
       eth0               wlan0                tun0       
 KB/s in  KB/s out   KB/s in  KB/s out   KB/s in  KB/s out
    0.00      0.00    241.19    112.50      0.00      0.00
    0.00      0.00    244.32     98.17      0.00      0.00
    0.00      0.00    262.66    115.67      0.02      0.04
    0.00      0.00    232.33     83.17      0.00      0.00
    0.00      0.00    228.09     94.16      0.00      0.00
    0.00      0.00    254.71    108.08      0.00      0.00
    0.00      0.00    250.84     91.01      0.00      0.00
    0.00      0.00    253.45    106.70      0.00      0.00
    0.00      0.00    253.55    107.52      0.01      0.02
    0.00      0.00    248.33    103.08      0.01      0.01
    0.00      0.00    252.80    106.70      0.00      0.00

:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"******"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: ******   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

tun0      no wireless extensions.

---

### Post by LightningCrash on 2010-08-21
Your wireless connection looks good from what I can tell.

Can you try an SSHFS mount to the other computer instead of Samba?

---

### Post by p0p0a on 2010-08-21
> **LightningCrash said:**
> Your wireless connection looks good from what I can tell.

Can you try an SSHFS mount to the other computer instead of Samba?

How do you do this?

---

### Post by p0p0a on 2010-08-22
> **LightningCrash said:**
> Your wireless connection looks good from what I can tell.

Can you try an SSHFS mount to the other computer instead of Samba?

OK I've had a couple of people ask me to do this. Why do you want me to do this? I don't want to do it unnecessarily because it exposes me to hackers. Also, it worked fine before with SAMBA, why shouldn't it work with SAMBA now?

---

### Post by LightningCrash on 2010-08-22
> **p0p0a said:**
> OK I've had a couple of people ask me to do this. Why do you want me to do this? I don't want to do it unnecessarily because it exposes me to hackers. Also, it worked fine before with SAMBA, why shouldn't it work with SAMBA now?

We're just ruling out the samba mount, that's all.

sshfs is as secure as an ssh connection. that means it's very secure.
I'm assuming you have the same username on the remote computer too, so:

```

mkdir ~/tmp
sshfs remote:/remote/dir ~/tmp

```

it will ask you for your password, which would be the same as when you SSH over.
that's all you have to do to mount with sshfs. 

then you can play something from ~/tmp and see if **it** skips too.

to unmount when you're done:
```

fusermount -u ~/tmp

```

---

### Post by p0p0a on 2010-08-22
I'm sorry I'd rather not install an openssh server on my computer, which is what others have told me I'll need to do to get this to work. Is there any other way to go about this?

> **LightningCrash said:**
> We're just ruling out the samba mount, that's all.

sshfs is as secure as an ssh connection. that means it's very secure.
I'm assuming you have the same username on the remote computer too, so:

```

mkdir ~/tmp
sshfs remote:/remote/dir ~/tmp

```it will ask you for your password, which would be the same as when you SSH over.
that's all you have to do to mount with sshfs. 

then you can play something from ~/tmp and see if **it** skips too.

to unmount when you're done:
```

fusermount -u ~/tmp

```

---

### Post by LightningCrash on 2010-08-22
> **p0p0a said:**
> I'm sorry I'd rather not install an openssh server on my computer, which is what others have told me I'll need to do to get this to work. Is there any other way to go about this?

upnp server (ushare, mediatomb)
nfs server


take your pick

---

