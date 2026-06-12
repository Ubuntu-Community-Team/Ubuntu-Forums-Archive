---
title: "MythMote and server address settings"
date: 2013-03-13
forum: Mythbuntu
---

### Post by iboothy on 2013-03-13
Posting this in a new thread as my last went slightly off topic.
I can't seem to connect MythMote to MythTV 0.25.
I haven't changed any IP addresses in the server settings, but they are currently default as localhost.
Can someone explain to a layman how I go about changing this to listen to MythMote?

---

### Post by PhilWig on 2013-03-14
Myth can be very confusing, and not just at first.  I've not used Mythmote, but if I were trying to get it working I'd try these steps:

Google "mythmote"  ->
[https://play.google.com/store/apps/details?id=tkj.android.homecontrol.mythmote&hl=en](https://play.google.com/store/apps/details?id=tkj.android.homecontrol.mythmote&hl=en)
Note the text:  "you must have mythfrontend network remote control enabled."

Google "mythfrontend network remote control enabled"  ->
[http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Frontend](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Frontend)
See 3.1.9
This tells us that the handset communicates with the frontend via port 6546 but needs enabling in frontend.  It's in  setup> general > page 7.

You'll almost certainly need a fixed IP address for your backend which it uses every time it starts.   
If it 'asks the router' each time (dynamic allocation) via a protocol called DHCP then it could get a different address each time so any IP address configured in mythmote will be invalidated.
To fix this, either configure Ubuntu with a 'static' address OR login to your router and configure it to give same address every time.  I found the latter much easier.

Terminal session command ifconfig will give you information on the address - look for 'inet addr:' under (probably) eth0.
It will also list 'lo' with address 127.0.0.1 which is a loopback (ie call one-self) and which is exploited by an 'out of the box' combined frontend/backend mythtv setup.  Also if you ping 127.0.0.1 it will tell you whether your network interface software is working.  

So, since Mythmote communicates with frontend and contrary to my comments elsewhere, it doesn't look as if backend setup should need any changes.
  
Regards
Phil

---

### Post by iboothy on 2013-03-15
Thanks Phil,
I will get on to this over the weekend and let you know how I get on.

---

### Post by iboothy on 2013-03-15
Phil,
There doesn't appear to be anything on your 2nd link.  Is it correct?

---

### Post by Akriss on 2013-03-15
looks like the forum scripts manhandled the link.?

```
http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Frontend
```

copy/pasted that in your url bar and your good to go. =)


Hope it helps

Kris

---

### Post by iboothy on 2013-03-18
Thanks Kris,
Didn't get round to looking at it at the weekend so it's a job for this week.

---

