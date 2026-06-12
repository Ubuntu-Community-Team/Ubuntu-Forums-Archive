---
title: "Anyone else lose networking?"
date: 2010-06-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2010-06-05
I'd installed a few updates today and had kept using Maverick, then took care of some chores, and when I came back I decided to install Debian Squeeze in another partition just so I can watch what's going on there.

After installing Squeeze I tried all of my other installations (Lucid, Karmic, Mint 9, and of course Maverick) only Maverick now lacks an internet connection :(

It's hardly a big deal but just wondered if anyone else had experienced this :)

My DSL has always just worked "out-of-the-box" with "Auto eth0".

---

### Post by ronacc on 2010-06-05
I Updated a couple of hoursago and noticed that a new kernel came down , I didnt reboot before I shut that box down for the night . Try booting the previous kernel .

---

### Post by ranch hand on 2010-06-05
After reading your post I logged into my backup main which was just updated.  I am on DSL and it came right up.

I was just checking the posts before switching to 9.04 for the night and checked on  my way out so I didn't linger.

I will have to tomorrow because it did give me a bunch of could not write broken pipe messages before booting.  Probably better look into that before I update my main Mangy Moose.

---

### Post by kansasnoob on 2010-06-06
Well, it's back this AM through no effort on my part, so maybe something just didn't "load" properly on boot :confused:

---

### Post by ronacc on 2010-06-06
on an earlier install of mangy I was having a similar problem ,some times would not connect on bootup, wired or wireless and could not be made to connect without a reboot , it was random and didn't seem to make any difference whether it was a "cold" boot or a reboot . I haven't had it happen since I reinstalled (about a week ago ).

---

### Post by ronacc on 2010-06-06
update : I was writing the above on my stable box while my test box was booting , I connected wireless but the network Icon was gone from the pannel and there is a strange new icon for the notification area ??? .This is the first boot after the udate I mentioned in last nights post .

---

### Post by youoh on 2010-06-07
same here.

eth1 will not connect. eth0 working without a problem.

eth0 is connected to my dsl-modem

eth1 is connected to my internal LAN und ip4 setting are the connection sharing thing.
don't know the english translation for it.

---

### Post by wilee-nilee on 2010-06-07
I just did a distro-upgrade from the terminal as the kernel update was being held back. I also added the xorg crack ppa just to make things really fun rebooted looks good, but the wireless didn't work until I put the wpa password in again, in the edit of NM. Wired etho worked fine.

I have the VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
So I was curious how this was going to integrate.

---

### Post by cariboo on 2010-06-07
I couldn't load the Broadcom wl restricted driver after updating Maverick UNE to the latest kernel (2.6.35-1) this morning. I re-installed  Lucid, as Unity and appmenu don't work in Maverick, yet. Hopefully this coming Thursday they'll be uploaded to the Maverick repositories.

---

### Post by koso on 2010-06-08
I am not able to connect to wireless network. It seems there is a problem with IP address retrieving using dhclient. And it is related to new kernel, old one works.

---

### Post by wilee-nilee on 2010-06-08
> **koso said:**
> I am not able to connect to wireless network. It seems there is a problem with IP address retrieving using dhclient. And it is related to new kernel, old one works.

Mine took about 3 minutes to connect I plugged in the etho wired and re-entered the password in NM edit. Not sure if this helps.

---

### Post by bennachie on 2010-06-08
I had the same wireless problem as koso. Reverting to the earlier kernel fixed it. I returned to the new kernel, connected to the Internet through my 3G dongle (which didn't seem to be affected) and the next round of updates fixed the problem. Typical alpha behaviour, I suppose.

---

### Post by kansasnoob on 2010-06-08
I did have a recurrence this AM but recycling the DSL modem brought it back.

I sometimes wonder about my SpeedStream modem but trying to deal with AT&T if you buy a third party modem is just totally insane :mad:

I see they have cable here up to either 6 or 10 mbs now so it might be worth a switch :confused:

---

### Post by ronacc on 2010-06-08
if the cable company is or has anything to do with comcast , don't even think about it , they are much worse than AT&T .

---

