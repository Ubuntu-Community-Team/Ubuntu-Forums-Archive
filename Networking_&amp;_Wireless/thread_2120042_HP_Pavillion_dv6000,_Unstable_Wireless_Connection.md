---
title: "HP Pavillion dv6000, Unstable Wireless Connection"
date: 2013-02-25
forum: Networking &amp; Wireless
---

### Post by Myst1234 on 2013-02-25
Hello all,

I have an HP Pavillion dv6000 running a b43 driver. I have had some seriously unstable wireless connections recently.

I had to do a fresh install of 11.10 and then upgrade to 12.04 on this laptop. I have done the following to try and settle the wireless connection -

IPV6 Ignored
Purged bcmwl-kernel-source
Installed b43-firmware
Used NameBench to get a better primary, secondary and ternary DNS

After all that I still see it go from 54MB/s down to 11Mb/s or even disconnect momentarily at times. 

I tried running this command

sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1

And it seemed to do a little bit better, only dropping to 36Mb/s but it still seems unstable dropping and rising constantly.

What can I do?

Thanks

---

### Post by chili555 on 2013-02-25
Please try instead:```
sudo modprobe -r b43
sudo modprobe  b43 btcoex=0
```Also, please run and post:```
dmesg | grep -e b43 -e ssb
```

---

### Post by Myst1234 on 2013-02-25
dmesg | grep -e b43 -e ssb Read Out -
```
[    1.303722] b43-pci-bridge 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, high) -> IRQ 19
[    1.303734] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[    1.320153] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[    1.320164] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[    1.320172] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[    1.320179] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[    1.384191] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[   18.344351] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   18.531043] Registered led device: b43-phy0::tx
[   18.531113] Registered led device: b43-phy0::rx
[   18.531183] Registered led device: b43-phy0::radio
[   19.816075] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  144.852121] b43-phy0: Radio hardware status changed to DISABLED
[  149.844114] b43-phy0: Radio hardware status changed to ENABLED
[  150.008096] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
```

I ran ```
sudo modprobe -r b43
sudo modprobe  b43 btcoex=0
```

It first disconnected me, then reconnected me, and now it says there are restricted drivers available. Should I mess with any of that?

---

### Post by chili555 on 2013-02-25
> It first disconnected me, then reconnected me, and now it says there are restricted drivers available. Should I mess with any of that?No, just tell us if it's more or less stable.

---

### Post by Myst1234 on 2013-02-25
It dropped from 54Mb/s to 48Mb/s and for the most part it seems to be staying at 48Mb/s. Though it does jump back up to 54 every so often.

Are the new restricted drivers that popped up of any concern? Would they possibly put me back up to 54Mb/s?

**EDIT**

It is a proprietary driver, Broadcom STA wireless driver

currently not activated

---

### Post by Myst1234 on 2013-02-25
Installed the driver it kept prompting me too and it failed to install. Shut down the wireless, did a reboot and now back to beginning.

```
sudo modprobe -r b43
sudo modprobe  b43 btcoex=0
```

Seemed to do ok. Should I make it permanent? If yes, how?

Also, why did the driver fail to install? Is this a problem?

And finally how can I get and keep my 54Mb/s connection?

---

### Post by Hodevah on 2013-02-25
I had a similar problem a while back. The way that it was solved was 

```
 sudo gedit /etc/rc.local
```Here you can edit the *rc.local* file to have the speed you want. 
Mine was edited the following way

```
#!/bin/sh -e
iwconfig wlan0 **rate 5.5M**
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
```The **emboldened **part is what you can change. 

And yes, it is fine to install restricted drivers. I assume that inside Software Sources>Ubuntu Software>Restriced Drivers, select that option. Then go to Additional Drivers TAB and select the driver you want.

The reason why you are getting temperamental speeds is because the driver has unstable speeds balanced with it. You need to manually adjust that speed. If you dont, you will keep getting drop outs and variations in speed. If you have it too high, your going to get drop outs. Hence the manual adjustment.

---

### Post by Myst1234 on 2013-02-25
When I tried installing the driver that prompted, I got a failure and a message to check var/log/jockey something. Not sure what that means so I simply rebooted. That undid the changes.

```
sudo modprobe -r b43
sudo modprobe  b43 btcoex=0
```

Seemed to help a bit, but that is also what made the driver prompt, which led to overall wireless failure.

I will try the local file edit and report back.

---

### Post by Myst1234 on 2013-02-25
This is what sudo gedit /etc/rc.local brought up

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
```

The section you mentioned to change did not appear when above command was entered.

---

### Post by Hodevah on 2013-02-25
```
sudo iwconfig wlan0 rate 5.5M
```change the '5.5M' to what you feel you like.


For example, 10M, 25M

What do you get?

What happens if you insert the rate you want into the *rc.local *now? 
Dont forget. Remove the '#' when inserting the rate.

**EDIT:** Since editing that file are you connectable after a reboot?

---

### Post by Myst1234 on 2013-02-25
There is no line to edit the rate in my local file. Should I write it in?

---

### Post by Hodevah on 2013-02-25
Yes. You must use the command I gave you in post #7 to do so. You must be sudo.
And dont forget, edit out the '#' while inserting your desired rate. Reboot.
If you set the rate too high, remember you can get drop outs. A low rate will not harm your connection.

---

### Post by Myst1234 on 2013-02-25
What is a decent rate?

Ideally I'd like to get and keep my 54Mb/s connection.

---

### Post by Myst1234 on 2013-02-25
I edited the local file, and no matter what number I put in, after reboot my connection information said I was running at 5 Mb/s. MUCH lower than I have ever seen it. 

Don't think that is the solution for me.

---

### Post by ahallubuntu on 2013-02-25
~

---

### Post by Myst1234 on 2013-02-25
Yea figured that out through this thread. 

I'm asking for a solution

---

### Post by chili555 on 2013-02-25
> **Myst1234 said:**
> When I tried installing the driver that prompted, I got a failure and a message to check var/log/jockey something. Not sure what that means so I simply rebooted. That undid the changes.

```
sudo modprobe -r b43
sudo modprobe  b43 btcoex=0
```

Seemed to help a bit, but that is also what made the driver prompt, which led to overall wireless failure.

I will try the local file edit and report back.Was I not clear in post #4? You asked if you should mess with restricted drivers and I said, I thought clearly, NO. But now you say:> When I tried installing the driver that prompted, I got a failure Why? If you are going to ask for guidance, I'd suggest you follow it and not blindly make up your own solutions.

---

### Post by Hodevah on 2013-02-25
In that case, I've got to apologize to Myst1234. As I didn't know that iwlwifi is for an Intel wireless card and not for a Broadcom wireless card. 
Tried to provide some aid. Terribly sorry.

---

### Post by Myst1234 on 2013-02-25
You were clear, however I could not get the prompt to go away so I tried something. Obviously it was the wrong thing. I'm sorry but there's no need to snap at me just because I don't know the right answer.

Just because I listed things I tried does not mean I know much about Linux and such. Everything I did and learned I got from this forum.

So back to the issue,

I did the 
sudo modprobe -r b43
sudo modprobe  b43 btcoex=0

And it seemed more stable, but my connection was lower than normal and still slightly unstable.

Is there anything I can do about this? And if this is the best I can do, how do I make it permanent?

**EDIT:**
Also how do I make the driver prompt go away if I won't be needing it?

---

### Post by Myst1234 on 2013-02-26
Anyone? At least how can I make the modprobe command permanent? Everytime I boot it's back to very unstable

---

### Post by Myst1234 on 2013-03-01
```
sudo modprobe -r b43
sudo modprobe  b43 btcoex=0
```

Has still been unstable and its "full" strength seems to be 36Mb/s instead of 54. I've lost strength and it is still unstable.

Please help this is making it extremely difficult to get my work done.

---

### Post by bellaseem on 2013-03-01
Well, 1st off, you messed up your chances of getting advice from the admin(chili) who's like a god at these things as far as I know... so maybe you should to get him to answer you.

2nd, try this in a terminal window: ```
 sudo iwconfig wlan0 rate 54M 
``` (you might have to change wlan0 to whatever your card's name is [it's usually wlan0 or wlan1]) then type iwconfig and see what rate it gives (you might have to wait a few seconds for the rate to change). If the rate changed, then great!

Then you can make it permanent by adding " iwconfig wlan0 rate 54M " to rc.local (without a # before it!, that comments it out [in other words, everything written after a # is discarded by the computer])

Also you can make any terminal command run at startup (permanent) by editing the rc.local file, so basically you do this:
```
 sudo gedit /etc/rc.local 
```
and add in whatever commands you want to run at startup (like modeprobe or whatever you were asking about) without the # before it as I mentioned...
Also, don't forget to make rc.local executable, if it isn't already:
```
 sudo chmod +x /etc/rc.local 
```
If it doesn't, then I don't really know... (beg chili to help you lol)... plus 5Mb/s isn't so bad... It might also be because you need an excellent signal to maintain a 54Mb/s rate... or the hardware doesn't play nice with each other... Well I'm not sure about all the info here, I'm not an expert but from things I read from good sources online.

---

### Post by Myst1234 on 2013-03-01
This seems to have helped. Thank you!

On a side note I didn't mean to **** anyone off. My connection was killing my productivity and my work was suffering. So I panicked. Not the best thing to do I know, but as I said I panicked.

---

### Post by bellaseem on 2013-03-01
I'm not sure if you'll get full bandwidth with this though... Also 54Mb/s = 6.75 Mbytes per second max (and you probably won't ever get that high)... I edited the older post too to add some things btw...

PS: mark as [SOLVED] pls and thanks :).

---

### Post by Myst1234 on 2013-03-01
Oh so this is just a mask? Will it actually keep a 54 rate and a stronger connection like I've seen it do? Or will this just make it report that it is running at 54?

I obviously don't know much about this stuff. I have 2 laptops that within the past 6 months I've changed to Linux Ubuntu. My smaller one (an asus eee pc) hasn't had any wireless issues since the original switch. However my larger laptop (HP Pavillion dv6000) hasn't cooperated. I recently had to do a fresh install and have been trying to hammer out this wireless issue ever since.

---

### Post by bellaseem on 2013-03-01
Well, for me it sets the rate to what it says, so I'm guessing it does  work and isn't just a mask, but anyhow you should try to see if your  connection reaches its maximum potential. What speed plan do you have  from your ISP? Try testing at testmy.net , do a manual test with a large  file size, what speed do you get? Also remember not to have any downloads/torrents/anything that uses internet running while running the test...

---

### Post by Myst1234 on 2013-03-01
Download - 6.7 Upload - 1.5-----is this good for a wireless connection?

Not totally sure what I'm supposed to be getting from my ISP. How do I find out?

---

### Post by bellaseem on 2013-03-01
Yup that's excellent! 6.75 is actually the max but it's impossible to get the exact maximum rate, anything better than 6.5 is very good (btw the rate 54M means 54 mega _bits _which when you divide by 8 , you get 6.75 mega _bytes_ and that's the maximum, so your rate is superb.)

---

### Post by Myst1234 on 2013-03-01
Thanks a ton!

---

