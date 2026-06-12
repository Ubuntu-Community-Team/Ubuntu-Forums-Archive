---
title: "Why is browsing so sloooooooow?"
date: 2011-07-01
forum: Networking &amp; Wireless
---

### Post by Chris Richard on 2011-07-01
Thought it might have been FF, because I've had so many problems with it on Windows and OS X on this same computer, but downloaded Google Chrome and it didn't improve.

This is a Mac Pro with blazing  processor and 2 GB memory, triple boot (now) with OS X Snow Leopard, Windows XP and, now Ubuntu. 

Browsing on Ubuntu is DEATHLY slow. So slow I simply cannot use Ubuntu for internet anything at all. On OS X and Windows, no problems with Google Chrome at least, and even though FF can get slow after long periods of continuous use, it's still better than any browser on Ubuntu.

Can anyone tell me what gives?

Is there something I ought to be checking in the system settings? With this computer, on cable, it should be screaming much faster than it is. Just loading Google.com can sometimes take up to a full minute.

Quite often I have to stop loading and reload up to three or four times, and maybe it'll respond somewhat quickly.

No idea what to look for to fix  this, but  man, I've GOT to fix this, otherwise Ubuntu is totally useless to me.

---

### Post by sanderj on 2011-07-01
Open a terminal with CTRL + ATL + T.

Then type "time wget www.google.com" and "time host www.cisco.com". Post the output here. Here's mine:

```

sander@R540:~$ time wget www.google.com
--2011-07-01 09:08:02--  http://www.google.com/
Resolving www.google.com... 74.125.77.147, 74.125.77.99, 74.125.77.104
Connecting to www.google.com|74.125.77.147|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://www.google.nl/ [following]
--2011-07-01 09:08:02--  http://www.google.nl/
Resolving www.google.nl... 74.125.77.147, 74.125.77.99, 74.125.77.104
Reusing existing connection to www.google.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html.3'

    [ <=>                                                                                                                           ] 9,844       --.-K/s   in 0.002s  

2011-07-01 09:08:02 (4.25 MB/s) - `index.html.3' saved [9844]


real	0m0.552s
user	0m0.010s
sys	0m0.000s
sander@R540:~$ 

sander@R540:~$ time host www.cisco.com
www.cisco.com is an alias for www.cisco.com.akadns.net.
www.cisco.com.akadns.net is an alias for geoprod.cisco.com.akadns.net.
geoprod.cisco.com.akadns.net is an alias for www.cisco.com.edgekey.net.
www.cisco.com.edgekey.net is an alias for www.cisco.com.edgekey.net.globalredir.akadns.net.
www.cisco.com.edgekey.net.globalredir.akadns.net is an alias for e144.cd.akamaiedge.net.
e144.cd.akamaiedge.net has address 84.53.164.170

real	0m0.217s
user	0m0.010s
sys	0m0.000s
sander@R540:~$ 



```

---

### Post by lovinglinux on 2011-07-01
Please provide the results of [http://www.speedtest.net/](http://www.speedtest.net/)

Are you using wireless or cable?

Have you tried to disable ipv6? See [http://www.webgapps.org/tutorials/firefox/troubleshooting/connection-issues-and-solutions](http://www.webgapps.org/tutorials/firefox/troubleshooting/connection-issues-and-solutions)

---

### Post by Chris Richard on 2011-07-01
Thank you both for the responses.

@ sanderj:

CTRL + ALT + T doesn't do anything. Is that your custom key command? That's okay though. I set my own up, which is different. Here's the results:

```
chrisrichard@Burlington:~$ time wget www.google.com
--2011-07-01 11:44:55--  http://www.google.com/
Resolving www.google.com... 74.125.115.99, 74.125.115.104, 74.125.115.103, ...
Connecting to www.google.com|74.125.115.99|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html.2'

    [ <=>                                   ] 9,879       --.-K/s   in 0.002s  

2011-07-01 11:44:55 (4.04 MB/s) - `index.html.2' saved [9879]


real	0m0.212s
user	0m0.000s
sys	0m0.004s
chrisrichard@Burlington:~$ time wget www.cisco.com
--2011-07-01 11:45:06--  http://www.cisco.com/
Resolving www.cisco.com... 69.192.16.170
Connecting to www.cisco.com|69.192.16.170|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 21900 (21K) [text/html]
Saving to: `index.html.3'

100%[======================================>] 21,900      --.-K/s   in 0.03s   

2011-07-01 11:45:35 (633 KB/s) - `index.html.3' saved [21900/21900]


real	0m28.795s
user	0m0.004s
sys	0m0.000s
chrisrichard@Burlington:~$ 

```

@ lovinglinux:

As I mentioned in the OP, it's cable. Speedtest.net test failed. "Download test returned an error while trying to read the download file."

Thanks for the tip on disabling ipv6. I do recall reading a lot of folks have a problem with that. It is now disabled, but it didn't make any noticeable difference at all.

@ ALL:

This should be some helpful information:

I do run a combined wireless/ethernet NAT router, however I am certain the neither the network nor the ISP are the problem. I have seven computers on this network. This  one runs OS X, Windows XP and Ubuntu. The others are all running both OS X and Windows XP, one other runs Vista. None of the other operating systems have this problem. They all run multiple browsers as well, and none of the browsers pose this  problem on those OS's. The obvious conclusion is that the only defining difference is the OS, Ubuntu. 

There has got to be either a bad setting in the network settings, or something different about the way browser pages are being processed.

For example, just trying to get back to this thread took nearly ten minutes. I'm only using Google Chrome now, because I've tired of FF memory bloat on all my other systems. Maybe it doesn't have that problem on Linux, but I don't have the time to play with it and find out so Google Chrome it is, for now.

1) Typed the address into the address bar, but forgot to add "www," so waited  30 seconds for Google to load.

2) Clicked the Google link for ubuntuforums.org, and waited 90 seconds. Gave up, quit loading, and clicked the link again. Waited 60 seconds, quit loading and clicked again. Bam! Page loaded almost immediately. 

3) Clicked the link for this forum, waited 2 minutes. Nothing. Clicked again, waited 90 seconds, quit loading again, refreshed the page, clicked again. BAM! Page loaded immediately.

Repeated the same basic scenario until I finally got to this edit page. The total time was around ten to twelve minutes for a task that normally takes less than thirty seconds on this network.

Basically, page load times are inconsistent. Most of the time it will be between 30 seconds to 2 minutes attempting to load. Most of the time, stopping the load and either just clicking the link again, or re-entering in the address bar, or refreshing and trying links again, the pages load quickly, but it could take two to four tries.

To me, it seems to obviously be a software issue. Something under the hood, behind the browsers slowing them down. FF and Google Chrome behave exactly the same.

Just so you know, because I know most of you guys hate it when noobies don't bother to research anything, the only reason I'm in here instead of Googling the problem is simply because I cannot waste as much time  as it takes to Google from Ubuntu right now. I can from the other systems, yes, but I have to keep rebooting into Ubuntu to try various fixes. All that rebooting takes just as much time as waiting for these slow browsers, so it's kind of  a "catch-22" right  now.

Once I can solve this problem I'll be able to research others I encounter (and I'm CERTAIN there  will be others) without pestering the community here so much before doing my own research.

Thanks for your understanding. ;)

And your input, of course! :)

---

### Post by sanderj on 2011-07-01
@Chris:

I asked "time wget www.google.com" and "time host www.cisco.com"

You've done twice a wget. BTW Notice the your seconde wget is extremely.

Anyway: what's the output of 

"time host www.cisco.com"
and
"time host www.surfnet.net"

NB: type this once, and get the output. The second type the result could be different.

---

### Post by Chris Richard on 2011-07-01
One thing did occur to me. It is possible I suppose that Linux may not be playing "nice" with my router, which is a fairly old Belkin 54g. Even just loading the control panel for it can take just as long as loading an Internet page. 

I run a Xampp server on a different computer on my network, and loading THOSE pages takes no time at all, so it's looking like this is a problem with Ubuntu not working well with this router.

Would anyone know if there is any documentation on Ubuntu-router compatibility?

---

### Post by Chris Richard on 2011-07-01
One thing did occur to me. It is possible I suppose that Linux may not be playing "nice" with my router, which is a fairly old Belkin 54g. Even just loading the control panel for it can take just as long as loading an Internet page. 

I run a Xampp server on a different computer on my network, and loading THOSE pages takes no time at all, so it's looking like this is a problem with Ubuntu not working well with this router.

Would anyone know if there is any documentation on Ubuntu-router compatibility?

While I wait, I'm gonna switch to another OS and research this...

---

### Post by Chris Richard on 2011-07-01
It appears the router vs. Ubuntu "liking" it, IS the problem.

I can't even load the control panel through a browser. Performing "time wget" on both the Xampp server and the router returns this result:

```

chrisrichard@Burlington:~$ time wget 192.168.2.4
--2011-07-01 12:36:24--  [http://192.168.2.4/](http://192.168.2.4/)
Connecting to 192.168.2.4:80... connected.
HTTP request sent, awaiting response... 403 FORBIDDEN
2011-07-01 12:36:29 ERROR 403: FORBIDDEN.


real	0m5.113s
user	0m0.000s
sys	0m0.000s
chrisrichard@Burlington:~$ time wget 192.168.2.1
--2011-07-01 12:36:44--  [http://192.168.2.1/](http://192.168.2.1/)
Connecting to 192.168.2.1:80... connected.
HTTP request sent, awaiting response... Read error (Connection timed out) in headers.
Retrying.
```

The 403 is the correct response, and the timing is just about right because of a security software on the server that reroutes pinging and puts a delay on pings to prevent brute force attacks.

After at least ten minutes, the router didn't respond at all.

So at least I seem to be narrowing down the root of the problem. (No pun intended)

---

### Post by sanderj on 2011-07-01
I think it's your DNS / name-resolving. So do the "time host ...", and we'll know.

---

### Post by Chris Richard on 2011-07-01
> **sanderj said:**
> @Chris:

I asked "time wget www.google.com" and "time host www.cisco.com"

You've done twice a wget. BTW Notice the your seconde wget is extremely.

Anyway: what's the output of 

"time host www.cisco.com"
and
"time host www.surfnet.net"

NB: type this once, and get the output. The second type the result could be different.

Oops I cross-posted you and missed this due to the browser being so slow. Yep. I missed that. My eyes aren't as good as they used to be.

```

chrisrichard@Burlington:~$ time host www.cisco.com
www.cisco.com is an alias for www.cisco.com.akadns.net.
www.cisco.com.akadns.net is an alias for geoprod.cisco.com.akadns.net.
geoprod.cisco.com.akadns.net is an alias for www.cisco.com.edgekey.net.
www.cisco.com.edgekey.net is an alias for www.cisco.com.edgekey.net.globalredir.akadns.net.
www.cisco.com.edgekey.net.globalredir.akadns.net is an alias for e144.cd.akamaiedge.net.
e144.cd.akamaiedge.net has address 69.192.16.170

real	0m0.162s
user	0m0.008s
sys	0m0.000s
chrisrichard@Burlington:~$ time host www.surfnet.net
www.surfnet.net has address 174.137.125.45

real	0m0.280s
user	0m0.004s
sys	0m0.000s
chrisrichard@Burlington:~$ 

```

Looks fair there. 

The thing is though, it's all very inconsistent. One minute pages take up to two minutes to load, or not at all, the next, they bang right in there. 

There definitely are some network issues. I just started getting some conflicting IP errors from my other machines, and I'm not sure why yet. I need to take some time and look into that. I do use static IP's to prevent repetitive conflicts with Xampp server (on a different computer) and local access to the pages there, among a few other reasons. Ubuntu is not yet set up as static. 

I need to do some network pinging to find the problem there, but there is also an issue  with the router at this point. Can't access the control panel from anywhere right now, so time to reboot that too. 

Maybe some improvement after that. We'll see.

BTW: I broke down and dusted off an old keyboard to hook up to another box so hopefully I won't miss responses from here on, but I'm used to running Synergy with shared clipboards and that's not working  just yet either so I feel like I'm back at my 1995 job rolling between three different computers on the same network. :P

I can answer now more quickly, but if I have to copy anything to send from the Linux screens, it might take a while.

---

### Post by sanderj on 2011-07-01
An easy network check is to open up a terminal, and then type "mtr 8.8.8.8"

---

### Post by Chris Richard on 2011-07-01
Thanks. That'll come in handy in the future for sure.

It was the IP conflicts. Solved that by setting my 3 machines to static 192.168.2.101 and up, and left the others to fend for themselves down below on DHCP.

You know what makes this really ridiculous? It was our Wii we just hooked into the wireless a couple of days ago that started the conflicts.

Anyway, it's all good now. 

Next to tackle: getting Synergy working on Ubuntu.

Wish me luck!

---

### Post by Chris Richard on 2011-07-03
Well I thought this issue was resolved, but apparently it isn't.

My network IP's have been cleaned up. There are no more conflicts.

I actually changed ALL the machines on this network back to DHCP except the one I use as a Xampp server to avoid having to look up it's IP when accessing from the LAN. That one is set to 192.168.2.104 to ensure none of the DHCP assigned IP's ever conflict with it.

Still it is taking forever to load pages in Ubuntu browsers, and they often fail to load at all, resulting in inability to even find servers. 

I did run mtr 8.8.8.8, and the results were dismal. Packet loss at the router level is around 35%, whereas all other entries below that  are about double that.

Again, NO other OS except Ubuntu on this machine is showing this problem. I do have Ubuntu set up on an iMac through wireless. Ran the same test on it, and it shows practically zero losses.

I don't know what's going on with this set up.

---

### Post by Chris Richard on 2011-07-03
Now I *really* don't know what's going on. This morning I ran the mtr test again on the Mac Pro, (no changes since the last test), and Loss right down the line is all 0%.

Browsers are screaming now.

#-o

I think I'll leave this thread as is for a few days. If there aren't any more problems, I'll mark it resolved...

---

### Post by Chris Richard on 2011-07-03
Still not really "solved." My Traceroute is extremely inconsistent. At times the loss column is either all 0's or maybe one at 1-2 percent. Other times, the router shows up to 30-35 percent and all others below it display twice that in losses.

Something is rotten here.

Anyone got anything to offer for advice on this? I'm baffled. #-o

EDIT: I did make some changes between the last "good" test and this one, however the changes were only to the Windows install, not Ubuntu. I don't know if they could possibly be related (Windows is on an entirely separate disk). This latest "bad" test happened right after updating Windows XP to SP 3. The previous bad tests were also after updating Windows to SP 3 (I've had to reinstall it a few times already due to not being able to boot into Windows after Ubuntu installs (multiple). That problem stopped happening once I got Ubuntu boot files installed correctly.

---

### Post by Chris Richard on 2011-07-04
mtr 8.8.8.8 test today shows (again) no losses. One time it's fine, the next, it's bad.

Note this is the only OS on the entire LAN that displays this behavior. OS X and Windows XP SP3 on the same computer don't have this problem at all.

Does anyone have any idea at all what could cause this kind of inconsistency?

---

### Post by Chris Richard on 2011-07-05
Pretty sure I finally got this problem solved. It never ceases to amaze me how often the obvious escapes me, but I'm pretty sure even the obvious was only part of the problem.

Turns out DHCP client ID in IPv4 settings was set to the router IP, which, of course, is wrong. I can't remember if I just had a brain cramp and set it that way while trying to set static IP's across the LAN (a set up I've since given up since it interferes with proper Syngergy operation on OS X ~ no idea why, I just know it doesn't work). I suspect I did. But even after I corrected that, packet loss was still bad so I tried turning IPv6 back on (DCHP only), and suddenly no packet losses at all after several reboots in and out of each OS.

As inconsistent as the connections have been though, and due to the fact that I am already seeing small packet losses of about 1-2% on one server, I'm a little wary to mark this as solved just yet.

On a side note, while researching this problem I found quite a few posts here and on other forums stating that Wicd network manager solved similar problems for others. I would not recommend Wicd for Mac Pros however, because Mac Pros have TWO Ethernet connections (one in, one out), and Wicd only shows settings for one of them. It does not detect or offer any settings for the second Ethernet connection so it seems to me to be useless for Mac Pros.

---

