---
title: "Flaky internet fixed on Wireless Atheros"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by metasparks on 2009-05-24
I have an atheros based D-link card. It is the model dwa-556. 

I installed Ubuntu Jaunty 9.04 and so happened to have my wired connection going. All was perfect. Than, I disabled my wired connection and connected via my wireless card and all hell broke loose. It would connect, but the first thing I noticed was that my signal level was way off normal (usually sits at 100% strength, was around 70%). Than, as I started surfing, the websites would all of the sudden stop responding. My DNS service appeared to be failing constantly. Any file being downloaded larger than 1MB would stall out. The only thing I could do was disable networking and re-enable it, resetting my connection to my router.

I hunted down the solution, one possible one being madwifi, the other, IPv6. I went for the IPv6 fix. I was told how to disable it here: [http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html)

After following the directions, all is well in my universe. No more flakiness, lag spikes. Even my signal strength jumped back up to 100%. Man, the first day using Linux and its already making me jump hurdles. WTF.

Good luck. Hope this post helps other noobs like me.

---

### Post by dbuell on 2009-05-25
Awesome! Thank you very much! This seems to have worked perfectly except that my wireless adapter(DWA-556) still has an ipv6 address. I don't mind really, it was just not the expected result. Are you sure it's not just a fix in the kernel?

I looked all over for a solution and all I found was the mad-wifi fix. I was hoping for another solution and never used mad-wifi.

Previously a ping would have a delay of 250-1500ms and after pinging us.archive.ubuntu.com for 15 minutes I would hover around a 40% packet loss. After updating the kernel I had 0% lost packets and a delay of 180ms.

Thanks again and have a wonderful day!

One more thing. After updating the kernel I had to remake and reinstall my soundblaster XFi drivers. Is this normal?

---

### Post by dbuell on 2009-09-11
In case anybody finds this on google. 

Unfortunately in my noobness I may have missed a simpler solution.

Although it was an interesting exercise to compile a customer kernel I wouldn't recommend it because you miss out on updated kernels from canonical (unless you recompile again).

After several installations on computers with the DWA-556 card I found the easiest solution to this was installing the linux-backports-modules-jaunty package.

Use 

sudo apt-get install linux-backports-modules-jaunty

Signal strength is up and packet loss is non-existant

---

### Post by deviantdan on 2009-09-11
I've had the same issues.... I have a DWA-547 and (after I got it working) it only gets 43% signal strength and my audio/video streaming (from Freenas, firefly) is really glitchy etc etc...

that first fix looks way to complex for me (n00b) and I tried installing the backports, but it hasn't made any difference.

not sure what to do, definitely a linux issue as it works fine under windows (dual boot)...

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"La Trobe Slutzorz"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:1C:F0:FD:9C:AC   
          Bit Rate=0 kb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=46/100  Signal level:-64 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

---

### Post by deviantdan on 2009-09-12
Ok, so after restart I am getting 82%.... YAY... still not super fast (like it should be), only getting 1.2MB/sec from my freeNAS server.

hmmm, we can do better than this I think

---

