---
title: "Ubuntu 10.04 wireless randomly disconnecting"
date: 2010-06-04
forum: Networking &amp; Wireless
---

### Post by oneadvent on 2010-06-04
My wireless card starts off fine, and works good when it is, but at random intervals it disconnects me from my wireless and asks for my wireless key again. If I put the key in it spins around and then asks again, but if I right click on the wireless icon in the corner and turn off networking, and then turn it back on it connects fine.

It doesn't seem to matter if I am doing anything online or not, as when I wake up in the morning it is usually disconnected too. 

The intervals are random, sometimes its 30 minutes, but sometimes its days.

Any help would be appreciated, below is what I could figure out how to do from the "HOWTO POST WIRELESS QUESTIONS" guide.

```
lspci:
05:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
        Subsystem: Intel Corporation Device 1301
        Flags: bus master, fast devsel, latency 0, IRQ 31
        Memory at d1900000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn

lsb_release -d:
Description:	Ubuntu 10.04 LTS

uname -mr:
2.6.32-22-generic i686
```

---

### Post by oneadvent on 2010-06-05
Bump!

---

### Post by llawwehttam on 2010-06-05
Click on the wireless link in my sig.

For each package you may have to replace karmic with Lucid.

---

### Post by oneadvent on 2010-06-05
I will definitely try that when I get home, Stay tuned for news...over the next few days that is...maybe just subscribe.

LOL

---

### Post by adamsiddhi on 2010-06-12
Why is this funny? 
Did you get it to work?

---

### Post by oneadvent on 2010-06-12
not funny, but SLOW, 
I am not convinced, but it hasn't happened but once.

Give me longer to decide please, its SO intermittent.

---

### Post by adamsiddhi on 2010-06-12
By the way, what is the wireless key? 
And how does one get one? 
IS it the password that you assign during installation? 

Thanks,
:adam

---

### Post by oneadvent on 2010-06-12
it would be somethng that you have setup with your router. If you dont know what it is you'll have to either put your gateway into a browser and sign in or call your router manufacturer.

It is not the password you used during setup.

---

### Post by adamsiddhi on 2010-06-12
hmm. what do you mean by 'gateway'?

you said i might have to call my router manufacturer. how would they know the key? by serial number?

---

### Post by oneadvent on 2010-06-15
Okay to your wireless question about gateways you should probably open a new thread. 

To the gentleman that was helping me earlier, I tried to do what you sig said but none would install, kept saying they couldn't be found...

Josh

---

