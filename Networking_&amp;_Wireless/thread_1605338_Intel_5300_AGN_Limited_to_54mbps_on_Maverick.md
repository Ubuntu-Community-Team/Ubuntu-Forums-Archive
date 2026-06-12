---
title: "Intel 5300 AGN Limited to 54mbps on Maverick"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by ojconcentrate on 2010-10-25
Hello all,

I've just upgraded to maverick and while the wireless works fine it is always limited to 54mbps (i get this number when i run iwconfig) and the card can't transfer more than 2.5MB/s (which is faily normal for a 54mbps connection). When i had lucid installed, the output of the iwconfig showed the speed of 0mbps but it i knew it was connected at 300mbps (to my netgear DGND3300) because i could transfer on the network at around 7-8MB/s. Has anyone else experienced this?

All the tests were done right next to the router. The wireless is connected at 5ghz so there is no inteference from neighbors or anything like that.


thanks in advance

---

### Post by chili555 on 2010-10-25
Do you have a file called /etc/modprobe.d/intel-5300-iwlagn-[COLOR="Red"]disable11n[/COLOR].conf? You might try renaming it so it doesn't operate on your system and see if it helps:```
sudo mv /etc/modprobe.d/intel-5300-iwlagn-disable11n.conf /etc/modprobe.d/intel-5300-iwlagn-disable11n.conf.bak
sudo rmmod -f iwlagn
sudo modprobe iwlagn
```Please post back and let the searchers know.

---

### Post by ojconcentrate on 2010-10-26
Many thanks. i've edited the file and replaced "options iwlagn 11n_disable=1" with options iwlagn 11n_disable=0 and rebooted.

It seems to connect now at 270mbps (which is what i expected anyway) but now i need to test reliability. I It would seem that a lot of people are saying that it locks up after a while but i need to test it myself.

Many thanks again

---

### Post by chili555 on 2010-10-26
> a lot of people are saying that it locks up after a whileWhich is evidently why it is preferable to disable N. We will be interested in your experience.

---

### Post by joshruehlig on 2010-10-27
Yeah I just set disable to 0 too, been testing the intel 5300 for two days now on ubuntu 10.10.

My card sees alot of wireless networks but it doesn't always seem to connect or will randomly choose to connect or not connect. I do notice it disconnecting sometimes but immediately reconnecting.

I installed this on a asus 1015pem that had a bcm card that i had to enable restricted drivers to get working. That card took 4-5seconds to connect after boot or resume, intel card connects 1second after booting or resume.

---

### Post by C0derBear on 2010-11-02
1 day + overnight on Dell Lattitude D630 (2007 model) with intel 5300 seems to be stable, will try to update in a couple days after I finish configuration. I have converted this machine from Win 7 to 10.10 x64 desktop.

addendum: Wow, really 3 weeks has gone by now? Well, seriously, no problems with the higher data rate. Even with the 'untu using it while virtualbox'd w7 is using it.

---

### Post by chili555 on 2010-11-02
> I have converted this machine from Win 7 to 10.10 x64 desktop.Outstanding! I love getting a new or Ebay-ed laptop and scrubbing other OSes!

---

### Post by cprofitt on 2010-12-26
I am curious why 'N' is disabled on 5300s.  Sucks that I happen to have the one card that appears to be an issue.

---

### Post by chili555 on 2010-12-26
My understanding is that, with some firmware versions, N speeds were flaky or impossible. I assume that, while it was being worked on, N was disabled. If it works fine for you with it reinstated, you're all set.

---

### Post by wolke on 2011-01-10
status check- how are you guys doing with N enabled?

also, is anyone using bleeding edge (or recent, or stable) compat-wireless?

---

### Post by morgwai on 2011-01-30
> **wolke said:**
> status check- how are you guys doing with N enabled?

also, is anyone using bleeding edge (or recent, or stable) compat-wireless?

I enabled N on my thinkpad with Intel Centrino Advanced-N 6200 chip few days ago and so far it works quite ok, but not 100% perfect:

- no lost packets at all, but rtt when pinging my router is a bit high:
100 packets transmitted, 100 received, 0% packet loss, time 99157ms
rtt min/avg/max/mdev = 6.492/7.526/33.323/3.598 ms
when in G mode it's much lower:
100 packets transmitted, 100 received, 0% packet loss, time 99011ms
rtt min/avg/max/mdev = 0.732/0.949/3.655/0.401 ms

- I didn't have occasion to test maximum throughput as this is my only N capable device. When fetching web ui of my router network manager was reporting speed about 144Mbs.

---

### Post by Ingenium on 2011-08-04
About a month ago, I installed the latest compat-wireless package (linux-backports-modules-compat-wireless-2.6.38-2.6.35-30-generic) and commented out the line in intel-5300-iwlagn-disable11n.conf to disable n. It worked perfectly and I got N speeds with no packet loss.

However, I noticed several days ago that I was limited to 54mbit (according to the device listing on my router, according to "iw dev wlan0 link", and based on benchmarks where my speed peaked at 2-2.5MB/sec). I set my router to be N only, but the issue is still there. My other devices connect at N speeds without a problem. "iw list" only shows bitrates up to 54 Mbps, so it seems that speeds above that are somehow disabled.

Was there some recent update that got pushed out that might have caused this? I haven't made any changes to my system, so I don't know what else could have caused it. This is on kernel 2.6.35-28-generic (with linux-backports-modules-compat-wireless-2.6.38-2.6.35-28-generic) and the version that I got yesterday, 2.6.35-30-generic.

---

### Post by chili555 on 2011-08-04
> **Ingenium said:**
> About a month ago, I installed the latest compat-wireless package (linux-backports-modules-compat-wireless-2.6.38-2.6.35-30-generic) and commented out the line in intel-5300-iwlagn-disable11n.conf to disable n. It worked perfectly and I got N speeds with no packet loss.

However, I noticed several days ago that I was limited to 54mbit (according to the device listing on my router, according to "iw dev wlan0 link", and based on benchmarks where my speed peaked at 2-2.5MB/sec). I set my router to be N only, but the issue is still there. My other devices connect at N speeds without a problem. "iw list" only shows bitrates up to 54 Mbps, so it seems that speeds above that are somehow disabled.

Was there some recent update that got pushed out that might have caused this? I haven't made any changes to my system, so I don't know what else could have caused it. This is on kernel 2.6.35-28-generic (with linux-backports-modules-compat-wireless-2.6.38-2.6.35-28-generic) and the version that I got yesterday, 2.6.35-30-generic.Please post:```
modinfo iwlagn | grep lib
```I have a suspicion...

---

### Post by Ingenium on 2011-08-04
> **chili555 said:**
> Please post:```
modinfo iwlagn | grep lib
```I have a suspicion...

```
filename:       /lib/modules/2.6.35-30-generic/updates/compat-wireless-2.6.38/iwlagn.ko
```

---

### Post by chili555 on 2011-08-04
My suspicion was wrong. I have no suggestions.

---

### Post by Ingenium on 2011-08-04
I also noticed the following in modinfo:

```
parm:           swcrypto50:using crypto in software (default 0 [hardware]) (deprecated) (bool)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable50:disable 50XX 11n functionality (deprecated) (int)
parm:           11n_disable:disable 11n functionality (int)
```

So it appears that 11n is enabled, but it's using software crypto instead of hardware crypto for some reason. I've read that you need AES encryption to get 11n speeds, so could that be something to do with it? Since it's not being hardware accelerated, maybe it's dropping to the slower speeds?

---

### Post by chili555 on 2011-08-04
I think one of us is mis-reading the parameter. Doesn't it say crypto is done in *hardware* by default? You could certainly try software:```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn swcrypto=1
sudo ifconfig wlan0 up
```If it helps, we can write one quick conf file to make it persistent.

---

### Post by Ingenium on 2011-08-04
I tried doing this with both swcrypto=1 and swcrypto=0, and that line in modinfo remained the exact same for both and the speed was the same. It looks like it says the default is hardware crypto, but that it's using software crypto ("swcrypto:using crypto in software"). I think something is preventing it from using hardware crypto somehow.

---

### Post by chili555 on 2011-08-04
The modinfo doesn't tell you what it's operating at now; it tells you what parameters are able to be set by us, the humble users. Until a newer driver gets written, those lines never change, except, of course for the location in a newer kernel.> filename:       /lib/modules/[COLOR="Red"]2.6.35-30-generic[/COLOR]/updates/compat-wireless-2.6.38/iwlagn.ko

---

