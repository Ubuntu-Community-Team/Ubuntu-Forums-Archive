---
title: "Internet drops during 'heavy' usage"
date: 2011-07-03
forum: Networking &amp; Wireless
---

### Post by oliveira_cj on 2011-07-03
Hello all

It seems that I'm not the only one that's had this problem, but I can't seem to find a solution for my situation on the net.  I'm definitely an Ubuntu noob so please take it easy on me!  Hopefully you can help.

I have an Acer Aspire One ZG5 and am running Ubuntu (originally 10.10 but upgraded to 11.04).  Originally I had windows on this laptop, but it was unbearably slow.  I was impressed with ubuntu on a new desktop I had built so I switched the netbook over as well.  Anyway, everything is great except the internet drops during 'heavy' usage.  Basically downloading files, youtube videos, etc.  

It didn't have this problem with windows.  When this happens I have to unplug the router and remember to not use the netbook for these activities (which is a pain).  Honestly, espn has videos pop up on a lot of its pages and that will freeze me out!  Very frustrating!

Thanks for your consideration in this matter.
Chris

---

### Post by SeijiSensei on 2011-07-03
You need to reduce the number of **simultaneous connections** in your torrent client if you're running one.  (Note, this isn't the same as "bandwidth".)  Try setting it to some number like 50 and see if that helps.

---

### Post by oliveira_cj on 2011-07-03
Thanks so much, but I don't believe I'm using a Torrent client on this netbook.  I've used one before on a different computer to download mame roms, but I'm not really trying to download anything like that on this netbook.

Is it possible something like that is working in the background?  I honestly don't know much about torrent except what I've described.

Thanks again for the response.

Chris

---

### Post by SeijiSensei on 2011-07-03
You'd know if you were using one, so that's not the explanation.

---

### Post by oliveira_cj on 2011-07-03
That's what I thought.  Bummer!

Thanks for your suggestion though.

Happy 4th!

---

### Post by oliveira_cj on 2011-07-07
Any other suggestions?  I have a relatively old Belkin router.  Would it matter if I changed the router?

Thanks
Chris

---

### Post by jvgeli on 2011-07-08
same issue here. Running 10.10 on DSL. with regular usage my internet is fine but with heavy usage it will drop and I have to restart to connect again. Some forums mentioned that it could be with the kernel but not sure though. hope we someone could figure this out.

---

### Post by Jake.Debord on 2011-07-08
@Oliv Does both machines cause this? Or just the laptop? If they are both causing this to happen then your router may be nearing the end of the road. Routers, like computers can overheat and crash. 

@JV When you say restart, do you mean reboot your machine or your router?

---

### Post by jvgeli on 2011-07-08
I have to reboot my machine. Recently forced update Maverick to Kernel 2.6.36 from 2.6.35 but haven't tested it fully as I am at work now. I have windows on another partition and the connection there is stable.

---

### Post by psusi on 2011-07-08
Your description is a little unclear.  When you start a big download on the laptop, is it just that download that stalls, or all connections?  Even from the other computer?  If so, then it sounds like the router is bad.  If it is only the big download that stalls, you might have the MTU problem.  Try lowering your MTU and see if it clears up:

```
sudo ifconfig eth0 mtu 1492
```

---

### Post by HipHopBlond on 2011-07-09
I have the same problem, on the same machine, with the same internet connection, with the same software and I found it while I was downlaoding different roms (I'm a GBA fan since I was 13, so I've decided to download some roms :P)

I found out the problem the same way. /Ubuntu 11.04

---

