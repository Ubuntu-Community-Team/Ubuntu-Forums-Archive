---
title: "Looong wait when booting without internet connection"
date: 2005-03-11
forum: Networking &amp; Wireless
---

### Post by stoffe on 2005-03-11
Just wondering why it has to wait so very long when booting, if there is no internet available. It's not an issue specific to Ubuntu, I know, but is there anything to be done about it? Normally, it isn't a problem, but now that I run Ubuntu on my laptop, I boot without internet access maybe half the time, and it gets really annoying - at the same time as I do want internet access when it is available. When it is, everything works perfectly.

I suppose it's a huge difference in how and why it's done, but this is one of the areas that Windows does better, by not waiting around for the results but rather taking care of it in the background. Not hitting the internet any faster, of course, but leeting you get on with business when you aren't heading that way anyways. Not that I'm switching back over that...  :razz:

So, can this be fixed somehow? Without having something else break that is, of course, like setting a real low timeout and having networking fail instead. ;) Or is it inherent to how the whole bootup procedure is working? Sane timeout could work well enough, probably though. A followup question could be what the default should be on an installation, especially for laptops. :)

---

### Post by alastair on 2005-03-11
It's probably either :

1) NTP server access attempted (e.g. /etc/init.d/ntpdate), or

2) DHCP addressing (not from the "internet" though, I hope)

I'd check for 1). Is NTP active (network time protocol)?

find /etc/rc* -name '*ntp*'

---

### Post by stoffe on 2005-03-11
[QUOTE=alastair]It's probably either :

1) NTP server access attempted (e.g. /etc/init.d/ntpdate), or

2) DHCP addressing (not from the "internet" though, I hope)

I'd check for 1). Is NTP active (network time protocol)?

find /etc/rc* -name '*ntp*'[/QUOTE]
 Yes. I know. It is usually DHCP taking forever to time out, this is the case on most or all Linux distros btw. NTP does the check separately on Ubuntu and fails much quicker (and always fails because at the point it checks internet is not yet activated and logged in - while it is mentioned, could that be moved to much later in the boot process?)

Is there any reason it has to be that way, and can it be changed was the question. Though I might add that it could be nice to see what it is doing, so users who don't know about it understood what it was freezing up on. :)

---

### Post by alastair on 2005-03-11
You can rearrange ntpdate run if you want - look at the file and perhaps use :

update-rc.d

You should try and find out /what/ takes the time on boot - you need to see the boot messages as they boot. Is the "quiet" option enabled on the kernel in GRUB? Take it off.

---

### Post by ozorba on 2005-03-15
This problem exists because linux is waiting for the network command (ifup) to time out.

There is a simple solution for this:

Go to /etc/rcS.d directory and rename S40networking to for example NOT_S40networking.

This will not run network connection and it will be fast during bootup.

However you will need to start the network connection manually from System -> Administration -> Networking. 

Happy fast bootups. :-)

OZ

---

### Post by stoffe on 2005-03-15
[QUOTE=ozorba]This problem exists because linux is waiting for the network command (ifup) to time out.

There is a simple solution for this:

Go to /etc/rcS.d directory and rename S40networking to for example NOT_S40networking.

This will not run network connection and it will be fast during bootup.

However you will need to start the network connection manually from System -> Administration -> Networking. 

Happy fast bootups. :-)

OZ[/QUOTE]

Yeah, doing manual ifup's is probably the way to go, good suggestion. Not all that neat, but saves a lot of waiting. Especially since the three common cases i have is wireless in one location, cable in another, and usually nothing in the rest... :)

---

