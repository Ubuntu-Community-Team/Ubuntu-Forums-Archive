---
title: "I need help with WUSB600N!"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by scarob995 on 2009-03-30
I need help with getting a WUSB600N wireless device to work with Ubuntu. ty :) :wink:

---

### Post by z.s.tar.gz on 2009-04-20
Do this to make it work:

> **mizunoX said:**
> I've noticed a few posts from people frustrated with the WUSB600N and the lack of support for it in Ubuntu/Linux so I thought I'd set the record straight for those searching the forums for answers.

The Linksys WUSB600N doesn't work in Ubuntu out of the box (current as of the release of Ibex)
Also it does not play nice with ndiswrapper (frequent disconnects, no 5Ghz support, no WPA2 support)

I was able to get it working with 5ghz and WPA2 by following steps that I found here:
[https://answers.launchpad.net/ubuntu/+question/45440]("Posting on external website")
Credit goes to the original author.

I've downloaded and modified the driver source for your convenience.  

Step 1 - Download the modified driver source here: [http://rapidshare.com/files/160951015/WUSB600N.tar]("http://rapidshare.com/files/160951015/WUSB600N.tar")
Step 2 - Extract WUSB600N.tar to a folder
Step 3 - Open a terminal and navigate to the newly created WUSB600N folder
Step 4 - type "sudo make" without quotes
Step 5 - Copy the file:
[LIST]
[*]sudo mkdir /etc/Wireless
[*]sudo mkdir /etc/Wireless/RT2870STA
[*]sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat
[/LIST]
Step 6 - open the WUSB600N/os/linux folder and type "sudo insmod rt2870sta.ko" again without quotes.

The wireless card should now be working.

Then do this to make it perminent:

> **mizunoX said:**
> Okay here's what I've found (and anyone with more linux knowledge is free to correct me if there's a better way).

Copy the .ko file to the kernel modules folder:
```
sudo mkdir /lib/modules/<kernel version>/wireless
sudo cp rt2870sta.ko /lib/modules/<kernel version>/wireless
```

Edit the modules list
```
sudo gedit /etc/modules
```

Add the following to the bottom:
```
rt2870sta
```

Edit the startup script:
```
sudo gedit /etc/rc.local
```

Add this near the end but before "exit 0"
```
sudo insmod /lib/modules/<kernel version>/wireless/rt2870sta.ko
```


I'm at work so I'm going to have to try this later when I get home.

I didn't make this, but I know it works.

---

### Post by RegPerrin on 2010-01-07
All I get when I try to 'make' is the following error:
Desktop/WUSB600N/os/linux/../../os/linux/rt_profile.c:1594: error: ‘struct task_struct’ has no member named ‘fsgid’

Can anyone help?
I am using Ubuntu 9.1 64-bit

---

### Post by Claymore2106 on 2010-02-08
Yea, I'm having the same problem as RegPerrin. This is my first time using any Linux based OS, so I'm completely lost as to what I'm supposed to do in this situation.

---

### Post by brendshav on 2010-02-10
Bumping for same problem.  I just switched to Ubuntu; I used Fedora a couple years ago. This is awfully frustrating.  I've done almost everything a forum post told me to do for 2 days.

---

### Post by brendshav on 2010-02-10
Well, solved that problem.  Used my netbook as a wireless bridge and just used the ndisgtk frontend and for some reason that worked.  Now my problem is that it is only connecting at G and it should be connecting at N.  Really slowing down my speeds and I'd like to stream my Highdef again. Any ideas on that?

---

