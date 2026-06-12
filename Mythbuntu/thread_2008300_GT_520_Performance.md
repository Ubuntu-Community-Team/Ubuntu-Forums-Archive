---
title: "GT 520 Performance"
date: 2012-06-22
forum: Mythbuntu
---

### Post by jlp_engineer on 2012-06-22
As luck would have it, I happened upon some old Lenovo Core 2 Duo low profile systems, that seemed like they would make decent MythTV frontends.  They are off-lease computers from a local college, I think, but for $55 per system, with 2.00 GHz C2D, 1 GB memory, 80 GB HDD, DVD/CDRW, Gigabit Ethernet, and a really quiet fan, they seemed like a good deal.  They were only lacking in one area, that I could tell, and that was graphics.  So I purchased a Zotac GT 520 card to put in it, and I hope I have not made a mistake.  

I saw a bunch of GT 430 solutions, but the TDP (Thermal Design Point) made me a little nervous that the PSU in the computer would not be able to power it.  The computer has a 280 watt PSU, but the 12V lines seem more than adequate for the power requirements of at least some of the current PCIe graphics cards.  So I went with the GT 520 which had a much lower TDP.  I was also restricted by the size of the card - had to be low profile of course, but also had to be only one slot wide.  That eliminated a lot of cards, just from physical size.  

The last element of this, is that Newegg.com was selling them for 50 bucks, with a 25 dollar rebate.  That seemed almost too good to be true, but I guess I will find out when I mail in the rebate form.  In any case, my question is, did I make a mistake?  Would there be a better card for the same amount of money, or a little more, that would meet all the requirements (size, height, power)?

Thoughts?  Opinions?

---

### Post by Grenage on 2012-06-22
280 (if it's delivering that) is tight, but to be honest I'd just try it.  You've already bought it, after all.

---

### Post by jlp_engineer on 2012-06-24
Well...it works!  I had my doubts, as the outside of the package had a minimum of 18 amps on the 12 volt line, and the max on the power supply is 17 amps. Evidently there was some margin designed into the specs on the side of the package. I wish there was an easy way to measure the actual current, but I will bet that it isn't anywhere close to 18 amps, since the power supply was only slightly warm after running for close to 12 hours playing LiveTV.

Does anyone know if there is a way to stress test the video card so it will pull the maximum power in the system? That way I know it will be OK...

---

### Post by sikk on 2012-06-24
Never done it myself, but have a play with Furmark and Wine.

[http://www.ozone3d.net/benchmarks/fur/](http://www.ozone3d.net/benchmarks/fur/)

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=21574&iTestingId=57563](http://appdb.winehq.org/objectManager.php?sClass=version&iId=21574&iTestingId=57563)

---

### Post by nickrout on 2012-06-24
> **jlp_engineer said:**
> Well...it works!  I had my doubts, as the outside of the package had a minimum of 18 amps on the 12 volt line, and the max on the power supply is 17 amps. Evidently there was some margin designed into the specs on the side of the package. I wish there was an easy way to measure the actual current, but I will bet that it isn't anywhere close to 18 amps, since the power supply was only slightly warm after running for close to 12 hours playing LiveTV.

Does anyone know if there is a way to stress test the video card so it will pull the maximum power in the system? That way I know it will be OK...

Find the hardest to decose h264 video file you can find and play it continuously using vdpau - try 

```
while true; do mythavtest hardfile.mkv; done
```

Try this file as being a good one to try:

[http://www.auby.no/files/video_tests/h264_1080p_hp_4.1_40mbps_birds.mkv](http://www.auby.no/files/video_tests/h264_1080p_hp_4.1_40mbps_birds.mkv)

ctrl-c to get out of the loop.



nvidia-settings will give you temperature readings too.

---

### Post by Grenage on 2012-06-25
> **jlp_engineer said:**
> if there is a way to stress test the video card so it will pull the maximum power in the system? That way I know it will be OK...

Graphical benchmarks for gaming systems (such as the futuremark stuff) will do the job, but I'd be surprised if your system didn't bottom out while running them; you'll be pulling far more juice.

---

