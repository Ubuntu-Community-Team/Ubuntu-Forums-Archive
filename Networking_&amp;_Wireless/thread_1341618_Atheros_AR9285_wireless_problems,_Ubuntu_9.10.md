---
title: "Atheros AR9285 wireless problems, Ubuntu 9.10"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by allsaythat on 2009-11-29
Hi all,
I've just put Ubuntu 9.10 on a Compaq Presario CQ61 with a Atheros AR9285 WiFi adapter. At first, connecting to my home (WEP) network, it works fine. However it then seems to have the signal drop off. It re-asks me for my wireless key, and I give it the correct one. After a while, it asks again. Even though the key is correct, I cannot re-connect.
It's a dual-boot machine, and the adapter and network connection work correctly from the same place while running Windows 7.
Any suggestions?

---

### Post by voronin on 2009-12-13
I have this problem too.. on my HP Pavilion dv3-2220er with Atheros AR9285 under Ubuntu 9.10.
Can anybody help?
After some time wireless connection is drops, and only reboot helps to up the wireless.

---

### Post by mdshaver on 2009-12-14
same here on my emachines laptop. mandriva 2010 has no problems with this wireless card but i do have difficulty with my ati graphics driver

---

### Post by mckemie on 2009-12-26
I, too, have an emachines laptop.  I had an earlier version (9.04?) working well.  Did a network upgade and finally got everything working again.  I've made the mistake of doing online updates whenever prompted.  Somewhere along the way, the atheros got broken but I didn't notice until I had to do one of my infrequent reboots.  I installed Mepis 8 which handles the atheros well, but doesn't detect the display.  Now, I'm looking for a way to repair my broken Ubuntu 9.10 atheros which has internet access only as mounted partition under Mepis.

---

### Post by MCorreia on 2010-01-07
I have the same problema, same wireless card...

I have been reading some threads about related issues, specifically the flaky connection Karmic has with wpa/wpa2 and hidden connections...

After reading a bit, it seems that there is something wrong with the Atheros drivers on Karmic's default 2.6.31 kernel. Many people recommended this fix: 

```

sudo apt-get install linux-backports-modules-karmic-generic
sudo apt-get install linux-backports-modules-wireless-karmic-generic

```Installing these packages should bring back backported drivers from the 2.6.32 kernel. 

Most of them also recommended installing WICD, but i skipped that...

This solved my hidden connection problems and boosted up the connectivity a bit - not ideal yet...

My problem is only with WPA connections because WEP works fine. I only tried one of the packages - didn't know about the other - and the connection remained flaky. I have know installed both packages, but can't test it because i can't access/configure my connection to WPA. As soon as i can configure or access a WPA connection i'll try to say something...

In the meanwhile, i would apreciate feedback on if the packages work on AR9285...

---

### Post by allsaythat on 2010-01-20
Thanks, it worked beautifully.
It's probably a good idea not to use wicd, because when I installed it after using this fix it disabled all my wireless until I re-installed the gnome network manager.

---

### Post by srailsback on 2010-01-20
Thanks MCorreia - your solution worked perfectly!

---

### Post by wesd3fer on 2010-01-25
Thank you MCorreia! My network connection is so much better now. I have been getting aggravated with it's speed since I installed Ubuntu on my system a week ago. Those two installs worked beautifully.

-Wesd3fer

---

### Post by bama7474 on 2010-02-05
Hey guys I've been reading alot about the AR9285 fix for weak wireless signals and the backports install got me up from 30% to 75% sitting in the exact same spot after a reboot.  I appriciate everyones post, they definately help noobs like me. Just incase others are experiancing the same problem, this fix work for UNR 9.10 on a Toshiba NB305-N410BL with AR9285 Wireless Network Adapter...Thanks again!!!:popcorn:

---

### Post by tdskate on 2010-02-15
Worked like butter for me as well.

---

### Post by silvari on 2010-02-28
I used MCorreia's backports fix on my Toshiba NB205 running UNR 9.10 (I was experiencing weak-signal problems) and this worked like a charm.

---

### Post by balikka on 2010-03-15
Works!
(AR9285, Sony Vaio Y series)

---

### Post by donmatas on 2010-03-15
> **MCorreia said:**
> I have the same problema, same wireless card...

I have been reading some threads about related issues, specifically the flaky connection Karmic has with wpa/wpa2 and hidden connections...

After reading a bit, it seems that there is something wrong with the Atheros drivers on Karmic's default 2.6.31 kernel. Many people recommended this fix: 

```

sudo apt-get install linux-backports-modules-karmic-generic
sudo apt-get install linux-backports-modules-wireless-karmic-generic

```Installing these packages should bring back backported drivers from the 2.6.32 kernel. 


In the meanwhile, i would apreciate feedback on if the packages work on AR9285...

It work for me with the sambsung n210

thanks!

DM

---

### Post by letank on 2010-03-20
> **donmatas said:**
> It work for me with the sambsung n210

thanks!

DM


Did not work , the sudo apt gave me an error....for the samsung n210, but I am using WUBI with 9.10 and kernel default 2.6.31, the wireless works under windoze 7, arrrrgh.

Michel

Update: I can see the wireless and am connected to , but it is slow. I need to update the libraries, as I installed WUBI for 9.10 a few days ago.

SECOND update: After a second restart, lets knock on wood, it is working.

---

### Post by owf on 2010-03-21
This did work for me, but the last-but-one kernel update broke AR9285 support again (Eeepc 1005PE). To add insult to injury, the last kernel update didn't fix the AR9285, but broke the previously rock-solid RTL8187B support, too :(

I've tried removing and re-installing the above-mentioned modules, but to no avail.

Any ideas anyone?

---

### Post by in-sanity on 2010-04-08
Lovely! It work on my Asus X50-GL as well... This post should be made sticky as I see quite a few people facing this problem.

Thanks.

---

### Post by ninjaaron on 2010-04-15
Worked. I have the same machine as the OP, Compaq Presario CQ61. Thanks.

---

### Post by creatorbri on 2010-04-30
Just about to reboot back into Linux and try this fix, will let you know how it goes. (Posting here now because I want to find this post again quickly via search!)

---

### Post by sudanmas on 2010-06-02
I'm running Karmic Koala 9.10 on a Gateway netbook w/ an Atheros AR9285.  Wireless throughput would drop from 75% down to 51% a few seconds after logging in.

Ran the first of the two commands mentioned on page 1 

**sudo apt-get install linux-backports-modules-karmic-generic**

and I'm now able to get at least 85% signal strength - enough sit on the back deck in the sun with my nettop / lapbook and enjoy the weather.

And I agree that this post should be stickied.  A simple fix to a difficult problem.

Rob

---

### Post by Cavin on 2010-07-13
[This was happening to me]("http://ubuntuforums.org/showthread.php?t=1527994") the AR9285 on my new Dell Mini 10n with Ubuntu Moblin Remix. Installing the first package fixed the issue! :)

---

### Post by deedsofhaphazzard on 2010-09-22
This solution worked perfectly on my HP G62 144DX with the Atheros AR 9285. I now have a significantly stronger WiFi signal and am not experiencing disconnects anymore. Thanks a lot...

---

