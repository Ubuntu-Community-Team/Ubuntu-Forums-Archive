---
title: "Automatic logon to internet using scripts"
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by Adrian N. on 2010-09-05
Hello to you all.
I'm working in France right now. And my internet access is through a router on a local network (LAN) of the hotel in which I stay. In order to have internet access I must type in my room number, my name, check the agreement and then click Enter.
The problem is that the router cuts off internet every two hours.
What I need is some script that does the followings:
- detect if there is no more internet connection (the LAN connection stays on)
- if there isn't to run the script that does all those things above.
What I've managed to do is the script that puts room number, name, check the agreement and click Enter using DejaClick, making it a bookmark and then open the firefox and run the script.
The command that I've used in Terminal and which I think I can use in my script was:
**firefox dejaclick:///home/username/.mozilla/firefox/hex2xi8w.default/dejaclick/recordings/wifilogon.xml**
It works well. It's connecting to the net.
What remains is the detection of the cut off of the internet connection.
Tried with Wicd, going to the properties of the wireless connection and then on Script. But here I'm stucked... Don't know what to do anymore.It has the post-disconnection script option, but my LAN connection is not disconnecting, only the Internet access through this LAN is disconnecting.
Can anybody guide me please?
Thanks in advance. 
I'm an Ubunter and I'm happy with it.

---

### Post by BkkBonanza on 2010-09-05
What you want to do is put a sleep loop in your script with a ping or wget to access some site. Test the return result and continue to sleep if ok, and do your connect if not. Then loop again on the whole thing.

You would start the script as a background process using scriptname& so it continues to run.

Also that method for starting the connection is really awkward. You could just look at the form for the login and then put a wget command in the script that does the login POST/GET request.

eg. for GET is easier, 
(this is just an example, the actual values are in the login form on the login page)

wget [http://hotelsite/login-page?room=234&pwd=1234](http://hotelsite/login-page?room=234&pwd=1234)

so an untested example script might be,

```
#!/bin/bash

while true; do

while true; do
wget google.com
if [ $? -ne 0 ]; then
break
fi
sleep 60
done;

wget hhtp://hotel-login-page-url?room=etc

done;


```
That's just off the top of my head, it needs debugging, testing.

It tests for successfully reaching google and if good then sleeps 60 seconds. If failed then it does the GET REQUEST to re-login.
And then returns to the first loop.

If you call the script keep connected and chmod 770 then you run it like this,

If the login form uses POST instead of get then you need to modify the login wget command to use --post-data=... instead of the example. Anyway, that can be tested from the command line to see if it works.
**./hotelconnect&**

And kill it like this,

**pkill hotelconnect**

You can make desktop shortcuts for both cases.

---

