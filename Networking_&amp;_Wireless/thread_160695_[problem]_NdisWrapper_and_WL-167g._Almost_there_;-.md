---
title: "[problem] NdisWrapper and WL-167g. Almost there ;-P"
date: 2006-04-15
forum: Networking &amp; Wireless
---

### Post by mechx on 2006-04-15
Now, I know this problem was posted like zillion of times here, but never found any working solution. I hope you'll be so kind to help me and other lost souls using USB WiFi adapters by finding a way to solve this once and for all:

I use an Asus WL-167g adapter going with RT2500 chipset and would like to run it with Breezy 5.10. Of course the driver's sourcefiles posted by the manufacter are worth a squat, so the NdisWrapper seems to be the way.

First got it to my comp.:
```

mechx# apt-get install ndiswrapper-source
mechx# apt-get install ndiswrapper-utils

```

As I'm a Ubuntu newbie, it proved useful to download the Gnome app. to manage the NdisWrapper installations:
```

mechx# apt-get install ndisgtk

```

Then, after unzipping the Win drivers for this particular card, I've made it installed by ndiswrapper:
```

mechx# ndiswrapper -i /<driver's directory>/rt2500usb.inf

```
and since ndisgtk showed the Hardware to be not present, I had to show it's usb id:
```

mechx# ndiswrapper -d 0b05:1706 rt2500usb

```

Everything worked fine until the time came to insert the module:
```

mechx# modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

```

Does anybody know what does this message mean and how to fix it?

iwconfig shows:
```

lo        no wireless extensions.

sit0      no wireless extensions.

```

What did I do wrong? Is there ANY way to run this adapter?

---

### Post by Subetealabici on 2006-04-15
[Hi I also new in this, maybe you need to get log in as a super user, also i have the same problem traing to put the wirelees network here](*,) [http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

---

### Post by mechx on 2006-04-17
> maybe you need to get log in as a super user
As you can see, there is a '#' in my prompt, so I already do the above as a superuser. I'm not really convinced about the 'sudo' syntaxes and think about disabling them.

As for the topic. I've read somwhere that ndiswrapper available in the form of ubuntu packages is not fully functional and may cause abovementioned errors. I think I will download the sources from the official site and try to compile them as soon as they'll fix the power supply in my ubuntu laptop :)

---

### Post by Mr_Welfare on 2006-04-17
Once again, you are not the only one with this problem. I am trying to get my D-Link DWL-G122 working as well. Anyways...
 
Mechx,
 
I've seen that problem before listed in a howto guid somehwere on this site.. I think that you are getting this error because ndiswrapper in conflicting with your card's native linux driver (which is already built in to Breezy. Not sure how to access it though). I'm still pretty new to this but if you check out this migh solve your problem.
 
[See section three: Troubleshooting]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?highlight=%28Wifi%29%7C%28Troubleshooting%29")
 
Hope this helps.
 
Mr_Welfare

---

### Post by mechx on 2006-04-24
Now guys! That is some progress:

I've uninstalled the ubuntu's bundled ndiswrapper (apt-get remove ndiswrapper), downloaded the new one from the NdisWrapper site (ndiswrapper.sourceforge.com) and compiled it by entering the directory and issuing 'make install'.

After that a usual procedure:
```

root@pumba# ndiswrapper -i /<driver directory>/rt2500usb.inf
Installing rt2500usb
root@pumba# ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
root@pumba# ndiswrapper -d 0b05:1706 rt2500usb
Driver 'rt2500usb' is used for '0B05:1706'
root@pumba# ndiswrapper -l
Installed drivers:
rt2500usb               driver installed, hardware present

```

So far so good I've got the driver installed and hardware detected, but it doesn't work:
```

root@pumba# ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39345 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39345 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2931313 (2.7 MiB)  TX bytes:2931313 (2.7 MiB)

root@pumba# iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

```

It's only about putting up the interface? What do I do now?

---

