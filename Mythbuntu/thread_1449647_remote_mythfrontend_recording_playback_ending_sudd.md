---
title: "remote mythfrontend recording playback ending suddenly"
date: 2010-04-08
forum: Mythbuntu
---

### Post by Eldis on 2010-04-08
My bedroom mythfrontend has been having this issue for some time now. This problem seems to mainly occur when watching recordings, I can't remember if it has happened when watching other media. On my backend + frontend combo in the other room I have never had this issue (ofc the files are local there so why should it happen).

Yesterday this happened ~10 times in a few hours so it's not rare it's very common and extremely annoying. Any ideas what could be wrong ? This is not a wifi network it's on my home LAN. It also happens when watching live tv but not sure if the error message is the same.

This is on a zotac ion 330 atom mobo with mythbuntu 9.10

```

2010-04-07 22:18:12.375 RingBuf(myth://10.0.0.5:6543/1003_20100407210000.mpg): Waited 2.0 seconds for data to become available... 
2010-04-07 22:18:12.474 NVP(0): Prebuffer wait timed out 10 times. 
2010-04-07 22:18:14.076 NVP(0): Prebuffer wait timed out 20 times. 
2010-04-07 22:18:14.376 RingBuf(myth://10.0.0.5:6543/1003_20100407210000.mpg): Waited 4.0 seconds for data to become available... 
2010-04-07 22:18:15.677 NVP(0): Prebuffer wait timed out 30 times. 
2010-04-07 22:18:17.279 NVP(0): Prebuffer wait timed out 40 times. 
2010-04-07 22:18:18.378 RingBuf(myth://10.0.0.5:6543/1003_20100407210000.mpg): Waited 8.0 seconds for data to become available... 
2010-04-07 22:18:18.880 NVP(0): Prebuffer wait timed out 50 times. 
2010-04-07 22:18:20.481 NVP(0): Prebuffer wait timed out 60 times. 
2010-04-07 22:18:22.082 NVP(0): Prebuffer wait timed out 70 times. 
2010-04-07 22:18:22.730 MythSocket(7f1563069840:52): readStringList: Error, timed out after 7000 ms. 
2010-04-07 22:18:22.940 RemoteFile::Read(): No response from control socket. 
2010-04-07 22:18:22.940 RingBuf(myth://10.0.0.5:6543/1003_20100407210000.mpg) Error: RingBuffer::safe_read(RemoteFile* ...): read failed 
2010-04-07 22:18:22.942 [mp2 @ 0x7f1595a14820]incomplete frame 
2010-04-07 22:18:22.942 AFD Error: Unknown audio decoding error
```

---

### Post by ian dobson on 2010-04-09
Hi,

That looks like a network problem. I have a similar problem with my remote frontend until I replaced all the network wiring/wall plugs for the entire network. It took me most part of a weekend to run about 150meters network cable, replace 4 wall plugs. But now I can run 1Gbit from anywhere to anywhere without any problems.

Try going to the terminal prompt and pinging your backend from the frontend in an endloss loop (ping ip_address -c 1000). If you see any dataloss then check your wiring.

Regards
Ian Dobson

---

### Post by Eldis on 2010-04-09
Thanks for your reply.

My cabling is fairly new and up to snuff for 1G already. I've suspected cabling already but haven't yet made any major changes. I will if I have to but I am trying to avoid it. My router might also be the problem and I'm considering testing a different one to see if changes anything.

I did discover yesterday evening that it might also have to do with my backend running a bit too hot. Very old htpc case filled with too many things and with too little cooling. I've ordered a better case now it will come in a few weeks. Yesterday I tried opening the case and opening the balcony door and that dropped the temperature to arround 45 degrees and the bedroom frontend worked fine all evening. It did stutter once or twice but it didn't once drop to menu as it has been doing every 10 mins in the last few days. The case is now closed again with a few extra fans.

I'll post back later with a few hours worth of ping results. More ideas of causes are welcome and I'll keep testing until I find a cure.

---

### Post by Eldis on 2010-04-09
Well after some testing I learned something I guess:

Here are the results of pinging when the backend server case is open + balcony door open.

```
1000 packets transmitted, 1000 received, 0% packet loss, time 999036ms
rtt min/avg/max/mdev = 0.128/0.253/0.430/0.066 ms
```

Results when backend is running "hot" below ( I repeated the test 6 times with the same results ~ 980-990 received out of 1000 ) I also did it from 2 laptops over wifi resulting in similiar results. So basically I now know it's the router, cabling from router to server or problem with the server either heating, network card or something I can't think of.

```
1000 packets transmitted, 988 received, 1% packet loss, time 999031ms
rtt min/avg/max/mdev = 0.188/0.279/5.391/0.436 ms

1000 packets transmitted, 982 received, 1% packet loss, time 999076ms
rtt min/avg/max/mdev = 0.132/0.257/5.254/0.304 ms
```


I'll do more cold condition testing to see if the 1000 of 1000 packets was a fluke or not.

---

### Post by Eldis on 2010-04-09
After more cold tests it would seem the 1000/1000 was a fluke.

Checking the cable next, pulling one on the floor from the router.

On the other hand while I do have some packet loss it seems to have a much less severe effect on the remote frontend when wathching media. Let's see how it goes with the new cable.

---

### Post by Eldis on 2010-04-09
I repeated the ping test again a few times with a cable directly connected to the router.

I got:


```

test1:
1000 packets transmitted, 1000 received, 0% packet loss, time 998988ms
rtt min/avg/max/mdev = 0.093/0.346/5.449/0.586 ms


test2
1000 packets transmitted, 998 received, 0% packet loss, time 999016ms
rtt min/avg/max/mdev = 0.101/0.326/5.455/0.599 ms



test3
1000 packets transmitted, 1000 received, 0% packet loss, time 999125ms
rtt min/avg/max/mdev = 0.146/0.266/0.604/0.104 ms

test4
1000 packets transmitted, 1000 received, 0% packet loss, time 999000ms
rtt min/avg/max/mdev = 0.092/0.210/0.418/0.056 ms

```

I guess I can conclude that there is something wrong with the cable or the sockets. I've pulled the cable and attached the connections  myself so I the downside is I have myself to blame. :). I'll check the connections first and if that fails I'll pull a new cable...

---

### Post by ian dobson on 2010-04-09
Hi,

So it looks like it's time to pull new cables :)

Maybe first check which pins are connected where, ethernet might work if 2 wires are swapped but it might not be stable.

Regards
Ian Dobson

---

### Post by Eldis on 2010-04-09
It appears the problem was the pins...

```
1000 packets transmitted, 1000 received, 0% packet loss, time 999008ms
rtt min/avg/max/mdev = 0.202/0.285/18.814/0.595 ms


1000 packets transmitted, 1000 received, 0% packet loss, time 998996ms
rtt min/avg/max/mdev = 0.161/0.227/0.414/0.055 ms

1000 packets transmitted, 1000 received, 0% packet loss, time 998996ms
rtt min/avg/max/mdev = 0.106/0.225/0.449/0.063 ms



```

Thanks for the help. It appears to be fixed now. I'll let my comp heat up again and see if I can get some errors going but even if I do I know now that the pins being wrong / too loose was the main reason.

---

### Post by Eldis on 2010-04-12
It's been a few more days now and the problem I was having hasn't reappeared. 

My backend case has been closed and running hot the whole time so that had very little or even nothing to do with it.

---

