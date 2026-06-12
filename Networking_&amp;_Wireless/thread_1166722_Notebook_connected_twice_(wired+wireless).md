---
title: "Notebook connected twice (wired+wireless)"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by dclement on 2009-05-22
Hello,

I have just noticed that when my laptop was docked under Jaunty, it appears connected twice to my LAN. First, wired (which is normal), and second, also wireless. (And indeed it is listed twice in the router.)

I'm sure that in Hardy, the wired connection took precedence and disabled the wireless one when docked.

I just wondered if that was harmless and, if not, what should be done about that.

TIA - regards, Daniel

---

### Post by superprash2003 on 2009-05-22
as long as your internet is fine and you are able to access your network , i'd say leave it as it is..

---

### Post by dclement on 2009-05-23
Thanks for replying. I'd gladly second this sensible point of view but I was just worried about this:

- At times, I'd prefer to be connected only wired for security reasons, e.g. when purchasing on the Internet or connecting to my bank account (You may think that disabling the wireless connection would suffice then, but unfortunately it re-enables itself in seconds!),

- After all, it should work in Jaunty as well as it did in Hardy...

Regards, Daniel

---

### Post by superprash2003 on 2009-05-24
how do you disable?? do you use the ifdown command?

---

### Post by dclement on 2009-05-24
No, I just (left-) click the network manager icon and uncheck the line which corresponds to my wireless network. (I'm not sure but, isn't that a GUI-way of doing the same?) This line is checked by default in Jaunty, while it was unchecked in Hardy. This is the problem.

Then, I get a message popup telling me that my wifi network is disconnected, I can see the turning animation of the network icon and 2 or 3 seconds later, another popup saying that the wifi network is connected again...

After reading you I read man ifdown and I tried (after checking that the wifi card was eth1):
```
sudo ifdown eth1
```Strangely I got:
```
Ignoring unknown interface eth1=eth1.
```
... while the syntax I used was the same as one of the examples in the help!

---

### Post by Iowan on 2009-05-24
You might try:
Right-click NM applet, then Edit connections.
Un-check the "Connect automatically" box on Wireless connection then see if problem remains - might need to restart NM to make changes take effect.
At least, if you disable wireless, it *should* stay disabled - and not reconnect.

---

### Post by Brandon Williams on 2009-05-24
To disable wireless, simply right click the network manager icon in the status bar and uncheck the box next to 'Enable Wireless'.

If you tend to have the ethernet cable plugged in when you log in, then you could enable or disable the wireless automatically when you log in using a script like this:
```
#!/bin/sh
if ip link list eth0 | grep -q 'state UP'
then
    dbus-send --system --type=method_call --dest=org.freedesktop.NetworkManager \
        /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Set     \
        string:org.freedesktop.NetworkManager string:WirelessEnabled            \
        variant:boolean:false
else
    dbus-send --system --type=method_call --dest=org.freedesktop.NetworkManager \
        /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Set     \
        string:org.freedesktop.NetworkManager string:WirelessEnabled            \
        variant:boolean:true
fi
```
If you create this script and define it as a startup application for your window manager, it will use dbus at startup to automatically disable or enable your wireless in NetworkManager based on whether or not your ethernet link is UP.

I _think_ this will work regardless of whether or not the ethernet interface has aquired an address yet.

This is definitely only a work-around, as you cannot rely on the dbus interface into network-manager remaining the same from release to release. For example, these dbus-send calls work in Jaunty, but not in previous releases.

---

### Post by dclement on 2009-05-25
Thanks to both for your replies.

@Iowan: indeed I can disable the wifi when the box is unchecked. Alas, it does not re-enable itself automatically when my laptop is undocked. I think I remember that the box was checked under Hardy.

@Brandon Willams: what an elaborate syntax... I'd be well incapable of devising such a script myself! While I tried to understand it a little, I ran into the following problem:

(1st, I assumed "eth0 -> eth2" because, to make things even simpler, eth0 is the wired interface builtin to the notebook. The one that is used is eth2, in the docking station...)

if I run (manually)
```
ip link list eth2
```
I get:```

3: eth2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 00:08:74:46:8c:47 brd ff:ff:ff:ff:ff:ff
```
thus "UNKNOWN" state!?

Maybe _this_ is the problem? If the system, for whatever reason, doesn't "know" that eth2 is UP, it activates the wifi interface?

BTW, wifi is eth1 and answers state UP!

---

### Post by Brandon Williams on 2009-05-27
It took a _lot_ of trial and error for me to figure out the dbus-send call syntax for this ... but that's another story :-)

I get 'state UNKNOWN' from my eth0 when it hasn't been plugged in at all. I get 'state DOWN' if when it has been plugged in and then I disconnected it. And I get 'state UP' when it is plugged in. I see that LOWER_UP is only present for me when my interface is plugged in ... maybe you could use that instead. Try replacing "grep -q 'state UP'" with "grep -q LOWER_UP" and see if that is a reliably way to tell the difference between when your eth2 is plugged in and when it isn't.

I don't think that this has anything to do with the UNKNOWN state, since I get the same behavior with the builtin interface on my laptop. NetworkManager no longer seems to care that my ethernet cable is plugged in. It used to disable my wifi if the ethernet was active. I haven't filed (or looked for) a bug report, because I almost never use the ethernet jack.

---

### Post by Iowan on 2009-05-27
Seems like I saw a bug mentioned (within the last 24 hours) about reconnecting... but don't remember where I saw it.  I'll post back if I find it!

---

### Post by HumidBean on 2009-05-27
> **superprash2003 said:**
> as long as your internet is fine and you are able to access your network , i'd say leave it as it is..

Wifi uses spectrum in the 2.4GHz range, which just about every other wireless device uses (keyboards, mice, bluetooth headsets, phones).  In my case, having wifi on when I don't need it on means interfering with my bluetooth headset.  The current option is to either turn off wireless and not get the auto-switching that 8.04 (and possibly 8.10) had between ethernet and wifi, or to leave it on all the time and accept that other wireless devices may fail even when the laptop is on ethernet.

---

### Post by dclement on 2009-05-28
Thank you for your input.

@Iowan: absolutely right! I confirm that if I unplug, then replug my wired eth2, it reports state UP.

Also, I was able to check that, under Hardy, there was no "state XYZ" item in the results of ip link list.

@Brandon Williams: I realized that I can't test under the form: 
```
if ip link list eth2 | grep -q 'state UP'
```
(or maybe LOWER_UP instead), because when I am undocked there is simply no eth2 and ip link list reports
```
Device "eth2" does not exist.
```
So, I'd be fine if I could test the *presence* of device "eth2". But I don't know how to test if a *device* exists...

---

### Post by Brandon Williams on 2009-05-28
To test whether the interface is present, simply use 'if ip link list eth2 2>/dev/null'. I would recommend that you do both, so that you only disable wireless if you are docked and plugged in, something like this:
```
if ip link list eth2 2>/dev/null && ip link list eth2 | grep -q LOWER_UP
then
    # dbus command to disable wireless
else
    # dbus command to enable wireless
fi
```

---

### Post by dclement on 2009-05-28
> **Brandon Williams said:**
>  [...] simply use 'if ip link list eth2 2>/dev/null'. [...] 

This is well done! I know this 2>/dev/null command, but I always forget to use it. This is the test I needed, for sure.

>  [...] I would recommend that you do both, so that you only disable wireless if you are docked and plugged in, [...] 

Actually I don't think it's critical in my case, since my docking station is *always* connected to the router (even when the laptop is undocked).

I confirmed that the test worked by creating a dummy script that just answered "present" or "absent".

Then I tried to run the dbus part at startup, but it appears not to disable my wifi when it should.

First of all I just wanted to check if I set it up properly: I put a toggle_wifi.sh script in my home directory, allowed it to run as a program, then I created an entry in the startup programs with ```
sh '/home/daniel/toggle_wifi.sh'
``` as the command line.

Is that the proper way?

---

### Post by Brandon Williams on 2009-05-28
If the first line of the script is '#!/bin/sh' and you have marked the script executable, then you shouldn't need to explicitly run it with sh. "/home/daniel/toggle_wifi.sh" should work on it's own, instead of "sh '/home/daniel/toggle_wifi.sh'".

It should work as a startup application, provided that it works from the command line. When you execute the command from the command line, does it disable your wireless if your laptop is docked? For me, if I have my ethernet cable plugged in and the script I originally suggested, it disables my wireless in Jaunty. And if I run the script with the cable disconnected, it enables the wireless in Jaunty.

If it works from the command line but not as a startup app, then there might be something about your command line environment that's different than the environment that the startup apps are run in. Try adding these two lines immediately after the '#!' line ... make them lines 2 and 3:
```
exec 2>>/tmp/toggle_wifi.log
set -x
```
Now log out and log back in. Then look at the file /tmp/toggle_wifi.log. Are there any error messages in the log? Run it again from the command line and compare the log contents from when it was run during login and when you ran it from the command line to see if there are any important differences.

---

### Post by dclement on 2009-05-29
It's working perfectly now, many thanks for your patience!

I could check first from the command line, and it was apparently the "sh" in the startup application command that was in excess.

It does precisely what one can do by hand by left-clicking the network icon and disabling / enabling wireless.

It is a pretty fine workaround for sure, but do you think the thread should be tagged as "solved"? After all, we still can't see in Jaunty what was automatic in Hardy, that is: wireless enabled but disconnected in the presence of a wired connection.

Still hoping for a Jaunty update (not very numerous these days, BTW).

Regards, Daniel

---

### Post by Brandon Williams on 2009-05-29
Great! I'm glad it's working for you.

As a forum thread, it's probably solved if it's working for you. Still, it required a lot of effort to do something that was the standard behavior, so it's probably worth a bug report if one doesn't already exist.

---

### Post by dclement on 2009-05-30
OK, I mark it solved (at least I try).

To summarize, here is the version of the script that works for me:
```
#!/bin/sh
if ip link list eth2 2>/dev/null
# eth2 is the docking station ethernet port
then
    dbus-send --system --type=method_call --dest=org.freedesktop.NetworkManager \
        /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Set     \
        string:org.freedesktop.NetworkManager string:WirelessEnabled            \
        variant:boolean:false
else
    dbus-send --system --type=method_call --dest=org.freedesktop.NetworkManager \
        /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Set     \
        string:org.freedesktop.NetworkManager string:WirelessEnabled            \
        variant:boolean:true
fi
```The script runs from the command line as well as a startup app.

Regards, Daniel

---

### Post by SgtPepperKSU on 2009-06-18
Was a bug filed for this?  It really should be automatic (not needing to manually running a script when you plug in or out the ethernet cable).

In my case, having both wired and wireless connections at the same time (even for a short time) messes up my Static DHCP allotment (configured to give the same IP to both MAC addresses since it is the same machine).

This would have worked fine under previous versions of Ubuntu.

---

### Post by dclement on 2009-06-19
In my case, I was almost forced to give different IP to the wired-connected and wireless-connected (same) notebook. I did this through IP reservation in the router.

I'm OK to file a bug since I initiated the thread. Not done yet because...

Just to be sure not to make any mistake: 
- can you confirm it still worked as expected under Intrepid? (I skipped this version.)
- do you agree that this bug should be filed for Network Manager? (the Intrepid and Jaunty versions look pretty much the same...)

---

### Post by dclement on 2009-06-26
Update: I came across [_this bug report_]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/328665").

Not quite the same, but... Given this, do you think another report should be filed?

---

### Post by Iowan on 2009-06-26
> **dclement said:**
> OK, I mark it solved (at least I try).
Another recommendation  for marking a thread "solved" was to add the "solved" tag.

---

### Post by dclement on 2009-06-27
Well, some seem to think is is not solved. 

Brandon Williams has provided a valuable workaround, but one can't deny Jaunty does worse than Hardy on this matter. In Hardy, there was nothing special to do.

(I can't tell for Intrepid as I skipped this version.)

---

### Post by rjcardoso on 2010-12-02
hi there!

I'm new to ubuntu (1 month) and i have the same problem, "how to auto-disable wireless when ethernet cable plugged in"?. It's awkward to turn off wireless card manually each time i start ubuntu.

I've read several articles until this one.

Right now, i'm running Wicd instead of Network Manager. Is it suitable to run the script used for "dclement" user?

Is there a way to do it only with only within Wicd?

Thanks!

Rjcardoso

---

### Post by dclement on 2010-12-04
Hi,

I initiated this thread a while ago, so I fell I have to answer. I can only say that Lucid (which I am using at present) behaves the same way as Jaunty.

That is, I am still to use the script that Brandon Williams kindly provided (fortunately, it still works under Lucid).

As you guessed, this script is pretty much tailored for Network Manager. I'd bet it can be "translated" for Wicd, but I have no experience to help there.

I don't know whether Maverick shows any improvement about this precise problem. Is it the distro you are using?

---

### Post by EricDHH on 2010-12-04
My 10.10 does the same, so i disabled auto for my wifi conncetion in the network manager. Sometimes the laptop sit on his dockingstation where it get lan, sometimes i use it somewhere in the roof. Then i have to click once on my ssid in the list.
Bug or feature? It can be disabled, so i think thats okay for me.

---

### Post by rjcardoso on 2010-12-05
Thanks for the replies!

I will then wait for future ubuntu updates, fingers crossed in order to have an upgrade regarding this issue.

I don't like to see me as a paranoid :p but even if disable auto connect to wireless network, my laptop will still waste some energy right? i was trying to avoid that as well...

Regards,

Ricardo Cardoso

---

