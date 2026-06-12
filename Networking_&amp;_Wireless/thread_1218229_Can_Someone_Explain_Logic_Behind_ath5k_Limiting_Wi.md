---
title: "Can Someone Explain Logic Behind ath5k Limiting Wireless Rate?"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by moore.bryan on 2009-07-20
As per the [Linux Wireless]("http://linuxwireless.org/en/users/Drivers/ath5k") page when using the completely FOSS ath5k driver:
> You'll probably see an immediate rate drop to 1M, this is because of how we currently handle rate control. You should be able to keep at least at 11M but for now set this manually:```
iwconfig wlan%d rate 11M
```

Can someone please try to explain to me why in the world someone would want to use this driver if it limits things to 11M, whereas the Madwifi driver (ath_pci) can give you 54M?

I'm just trying to understand the logic here...

---

### Post by JohnnySage50307 on 2009-07-20
My only suposition is in the instance of a high-traffic local network...this way no one user hogs bandwidth.  A brother of a friend of mine did a paper and noticed people begin to claim that the network is breaking if and only if the network they're currently using begins running slower than it has in the past.
 
Again, this is only a suposition.  I'm studying Computer Engineering at Pitt and typically we frown upon such limitations and say build better hardware and code better drivers :-P

---

### Post by Seq on 2009-07-20
> **moore.bryan said:**
> As per the [Linux Wireless]("http://linuxwireless.org/en/users/Drivers/ath5k") page when using the completely FOSS ath5k driver:

Can someone please try to explain to me why in the world someone would want to use this driver if it limits things to 11M, whereas the Madwifi driver (ath_pci) can give you 54M?

I'm just trying to understand the logic here...

Because ath5k is a fully Free driver, and the madwifi devs are focusing on it. There are still some issues, as you've pointed out.

Also, according to iwconfig, I'm at 54 Mb/s. Then again, I'm not that far from the AP.

```
[chris@macbook:~]$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"CIAWesome"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:1E:E5:76:BA:B1   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm  Noise level=-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

virbr0    no wireless extensions.

pan0      no wireless extensions.
```

---

### Post by moore.bryan on 2009-07-20
Interesting thoughts, John. I hadn't considered traffic hogs; however, how does this make sense when, in most situations, you're only talking about a couple of people being on a home lan at any one time?

I agree with the "better drivers" comment. Madwifi works fine at full-speed, so I find it interesting the *next generation* Atheros driver limits things.

I have a few former students currently at Pitt... excellent school.

---

### Post by Seq on 2009-07-20
> **JohnnySage50307 said:**
> My only suposition is in the instance of a high-traffic local network...this way no one user hogs bandwidth.  A brother of a friend of mine did a paper and noticed people begin to claim that the network is breaking if and only if the network they're currently using begins running slower than it has in the past.
 
Again, this is only a suposition.  I'm studying Computer Engineering at Pitt and typically we frown upon such limitations and say build better hardware and code better drivers :-P

I believe it is an interference/noise issue. To counteract noise, the rate drops. The wiki linked to indicates their formula for doing this just drops to 1M all the time and needs to be fixed (Though I don't seem to see that).

---

### Post by moore.bryan on 2009-07-20
> **Seq said:**
> Because ath5k is a fully Free driver, and the madwifi devs are focusing on it. There are still some issues, as you've pointed out.
You've hit on one of my fundamental questions: what does/should the free part have anything *whatsoever* to do with the wireless rate?
> 
Also, according to iwconfig, I'm at 54 Mb/s. Then again, I'm not that far from the AP.
I've tried ath5k up and down sitting right next to the router and I can't get even close to 18M; what's your magic secret?
;-)

---

### Post by Seq on 2009-07-20
> **moore.bryan said:**
> I agree with the "better drivers" comment. Madwifi works fine at full-speed, so I find it interesting the *next generation* Atheros driver limits things.

The ath5k driver is a complete rewrite, so it will not have 1:1 functionality compared with madwifi until such a time that it does ;)

ath5k (and 9k) work without the proprietary Atheros HAL, so it's probably more work for them to support certain features.

---

### Post by Seq on 2009-07-20
> **moore.bryan said:**
> You've hit on one of my fundamental questions: what does/should the free part have anything *whatsoever* to do with the wireless rate?

It's all new code, so of course it has an effect. Different software can give you different results.

Try comparing for example the open radeon driver to the closed fglrx. There is a feature difference between the two on the same hardware.

> **moore.bryan said:**
> I've tried ath5k up and down sitting right next to the router and I can't get even close to 18M; what's your magic secret?
;-)

No idea. Here's the relevant part of my lspci:

```
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
	Subsystem: Apple Computer Inc. Device [106b:0086]
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0400000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k
	Kernel modules: ath5k

```

---

### Post by Seq on 2009-07-20
> **Seq said:**
> No idea.

Wait.. I may have an idea ;)

```
[chris@macbook:~]$ uname -a
Linux macbook **2.6.31-020631rc3-generic** #020631rc3 SMP Tue Jul 14 09:06:10 UTC 2009 x86_64 GNU/Linux
```

The advantage of a Free driver (especially one included in the kernel) is I can use a newer kernel without any issues. If I had an nvidia graphics card, or using a madwifi, I'd have to do some extra work.

---

### Post by moore.bryan on 2009-07-20
Did you self-compile a "latest" kernel? Hmm... *that* may actuall play a role!

EDIT:

Interesting... I installed the latest Ubuntu kernel (2.6.31-020631rc3-generic), enabled ath5k, **and** specified a wireless-rate of 54M in the /etc/network/interfaces file; voila, my iwconfig now tells me I'm connected at 54M and my link quality is *incredibly* improved. Now, if I can only shut-off the irritating wireless LED!

---

### Post by martinbaselier on 2009-07-20
you can write a config file for the kernel module in /etc/modprobe.d/

Create a file there with a sensible name, like ath5k.conf or wifi.conf

For example this is the output of the config for my driver:

```

cat /etc/modprobe.d/ipw2200.conf 
options ipw2200 led=1

```
I wanted to turn the led of my ipw2200 on, because it indicates wetter I have contact or not. The options for your driver will probably be different, but it might work and it will give you an idea what to search for in google.

---

### Post by moore.bryan on 2009-07-20
Thanks for the advise; I'll try it out!

EDIT:
Okay, so adding ```
options ath5k led=0
``` to a file named ath5k.conf in /etc/modprobe.d totally broke my wireless; the ath5k driver didn't even load and my hardware became invisible. Deleting file brought everything back to normal.

---

### Post by martinbaselier on 2009-07-21
Have you tried searching for an option for your driver in google? As I said, the driver probably has different options than mine.

---

### Post by moore.bryan on 2009-07-21
Yeah, although it was just a quick and precursory look... no dice. I'm actually starting to get used to it again, so it might be a moot point. ;-)

---

### Post by lswb on 2009-07-21
You can check the options available for loading modules with the command:

modinfo modulename

Look for lines that begin with "parm" It's often somewhat cryptic so you still may need to google for details. running "modinfo ath5k|grep parm" on my system shows only one load option:

parm:           nohwcrypt:Disable hardware encryption. (int)


On the OP question, I guess it's just a matter of time and work for the developers to get full functioning of the ath5k driver. The signal is encoded differently for the 56M rate than at the 11M rate so it is probably a software problem they just need to work out. In the meantime, in the US it's unlikely you incoming service is faster than a few Mbs anyway, unless you're using FIOS or something similar.

---

### Post by moore.bryan on 2009-07-22
> **lswb said:**
> ```
modinfo modulename
```
Thanks for this little nugget; never heard of this command before. Unfortunately for me, I get only two options:
```
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           all_channels:Expose all channels the device can use. (bool)
```
> On the OP question, I guess it's just a matter of time and work for the developers to get full functioning of the ath5k driver. The signal is encoded differently for the 56M rate than at the 11M rate so it is probably a software problem they just need to work out.
Makes sense, but what I've come to realize is although the webpage reports 11M as the threshold, with the latest kernel, I *can* in fact get 54M. So, overall, the Atheros driver makers are doing a bang-up job!

---

### Post by martinbaselier on 2009-07-22
They might add this feature in the future. The current driver (kernel 2..6.28-13) does not show any parameter. It will probably not be on the top of their priority list though. Thanks for the tip, lswb. I hadn't noticed modinfo showed that. The drivers I used it on, did not have any parameters.

---

