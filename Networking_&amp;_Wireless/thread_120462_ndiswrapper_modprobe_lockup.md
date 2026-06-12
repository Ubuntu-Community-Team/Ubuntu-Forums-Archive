---
title: "ndiswrapper modprobe lockup"
date: 2006-01-21
forum: Networking &amp; Wireless
---

### Post by kars175 on 2006-01-21
Hi,

I am trying to set up my Intel 2200BG wireless through ndiswrapper. At the state when I do modprobe ndiswrapper the system just locks up and I am forced to restart. I am not sure why this is happening. I have ndiswrapper version 1.8 The linux kernel installed2.6.12-10-686

Can anyone help me out here.

Thanks
karthik

---

### Post by Lambert on 2006-01-25
Before doing modprobe, check to see if ipw2200 is loaded. If so remove it.

sudo modprobe -r ipw2200

to prevent it loading at boot add it to black list at /etc/hotplug/blacklist (I believe that's correct)

And have you tried/considered using the native ipw2200 driver instead of ndiswrapper?

---

### Post by trubblemaker on 2006-01-25
I"m with Lambert, I had the native driver and ndiswrapper going at the same time and I got locked up lots.
maybe try the ndiswrapper -r [driver] and see if you still have wireless, 
```
iwconfig
```

---

### Post by kars175 on 2006-01-28
Unfortunately this did not work either. The system still hangs up. I see a lot of documentation on the native ipw2200 but that does not seem to work either. The drivers on the webpage seem to be out of date with whats on the documentation and if I try it with the latest drivers I still see messages. 

I am sorry for this late reply since I was out of town and did not have access to my laptop. I will be more prompt in my responses.

Thanks for your replies but still hoping to get this wireless issue fixed. Would the next release of Ubuntu take care of this in particular (the 2200BG configuration) since I see so many emails of despair but the solution does not work for everyone.

Thanks
Karthik

---

### Post by hajk on 2006-01-28
You probably compiled the ndiswrapper source with the wrong version of GCC -- this MUST be gcc-3.4, since the Breezy kernel is also compiled that way. If you used gcc-4.0 the computer will surely freeze solid when inserting the module in the kernel.

Make sure that /usr/bin/gcc is a symlink to /usr/bin/gcc-3.4 (and NOT to /usr/bin/gcc-4.0). If necessary, do

sudo rm /usr/bin/gcc
sudo ln -s /usr/bin/gcc-3.4 /usr/bin/gcc

(Of course, the gcc-3.4 package should be installed as well.)

---

### Post by ajaustin on 2006-01-31
First, thanks to Lambert for the blacklist suggestion on another thread.  I tried it and got a kernel panic when trying to boot to gave up on that.

Where I am now is that I have both ndiswrapper and ipw2200 loaded and wireless networking is working - so far.  I have had ipw2200 working for several weeks with little trouble and then suddenly it became so unreliable as to be unusable; failing to load on boot and then just going dead unpredictably forcing another boot.

In order to get ndiswrapper to load at boot time I am using a file /etc/modprob.d/ndiswrapper:-
```

alias eth0 ndiswrapper
options ndiswrapper if_name-eth0
```

I don't know if this is correct but it does load ndiswrapper on boot.

I am using eth0 rather than wlan0 because I had no success with wlan0 and just got kernel SIGIO errors when I tried to use ifup; also wlan0 never showed up in the Networking GUI which I took to be a bad sign.

So here is the question:-

Am I using ipw2200 or am I using ndiswrapper?

I can unload ndiswrapper module and the wireless carries on working, but I think that aliasing eth0 to ndiswrapper may mean that ndiswrapper is being used if it is loaded.

How can I tell?

Tony

---

