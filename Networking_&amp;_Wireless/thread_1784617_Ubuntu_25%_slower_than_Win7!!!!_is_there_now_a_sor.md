---
title: "Ubuntu 25% slower than Win7!!!! is there now a sorted fix?"
date: 2011-06-17
forum: Networking &amp; Wireless
---

### Post by Ace..... on 2011-06-17
Just installed the latest 11.04 64bit ubuntu, using std cd install alongside windows7, ticking the "add all extras" option, to ensure I got all the latest drivers etc..

The pc is brand new
Acer emachines E644 - AMD 2 Core C-50
3Gb DDR3 mem
500 Gb hard drive

Pre-installed: 64bit Win 7 home premium
I've literally changed nothing in win7 other than using wubi to install ubuntu 1st time around (ubuntu appears as a win program - and was _un-installed_ as such).

**Note**: It is too late to now check, but......... under wubi/win7 I had no sense that the browser firefox was running slow - i didn't do a speedtest.net cos of other priorities (and it seemed fine).

On advice, I started again (new partitions etc).

**The Problem:** Ubuntu is now 25% slower (broadband) than Win7!!!!

Actually, it feels worse than that - more like it was on my previous lap top that had 512Mb ram running xp.
Here are the results after switching os's a couple of times. 

Firefox...................... dn........up...ping
11:04    PM","GMT","4.29","0.78","93","Paris","200"
11:05    PM","GMT","3.61","0.77","71","Paris","200"
11:12    PM","GMT","3.95","0.77","70","Paris","200"
11:23    PM","GMT","4.23","0.77","72","Paris","200"
11:23    PM","GMT","4.07","0.77","71","Paris","200"
11:24    PM","GMT","3.82","0.77","71","Paris","200"
11:27    PM","GMT","3.87","0.77","71","Paris","200"
11:37    PM","GMT","5.89","0.77","72","Paris","200"
11:38    PM","GMT","3.90","0.78","71","Paris","200"
11:39    PM","GMT","3.84","0.77","72","Paris","200"
11:40    PM","GMT","4.47","0.77","71","Paris","200"
11:40    PM","GMT","3.85","0.77","72","Paris","200"

Win7 Explorer.......... dn.......up.....ping
11:08    PM","GMT","5.48","0.78","65","Paris","200"
11:31    PM","GMT","5.48","0.78","55","Paris","200"
11:31    PM","GMT","5.48","0.78","65","Paris","200"
11:32    PM","GMT","5.48","0.78","65","Paris","200"
11:33    PM","GMT","5.48","0.78","65","Paris","200"
11:33    PM","GMT","5.47","0.78","57","Paris","200"
11:48    PM","GMT","5.49","0.78","65","Paris","200"
11:48    PM","GMT","5.49","0.79","65","Paris","200"
11:49    PM","GMT","5.48","0.78","65","Paris","200"

Firefox managed one spurious result of 5.89, but the graph (on the speedtest display) was absolutely all over the shop (like it's overall results).

Compare that to iExplorer - total stability, and in fact, more like 30% faster + a much better ping.

Anyway, I guess you know all this, I've seen that plenty of others have noticed this speed drop in the past, so:

**The Solution:**

Has a solution been found to this problem?
If not.......are any developers working on a fix?

---

### Post by chili555 on 2011-06-17
> The Problem: Ubuntu is now 25% slower (broadband) than Win7!!!!
Perhaps it is, for your ISP, router, wireless card and driver, but, in my limited experience, it is not a universal truth that the developers are fighting to solve and find a sorted fix. What wireless card and driver are you using? Is there a driver conflict? Is there a newer version of the driver available that you haven't discovered and installed?> Firefox...................... dn........up...ping
11:04 PM","GMT","4.29","0.78","93","Paris","200"
11:05 PM","GMT","3.61","0.77","71","Paris","200"
11:12 PM","GMT","3.95","0.77","70","Paris","200"
11:23 PM","GMT","4.23","0.77","72","Paris","200"
11:23 PM","GMT","4.07","0.77","71","Paris","200"I'm really not sure what test this represents, so I am unable to replicate it.

---

### Post by Ace..... on 2011-06-17
sorry... i just finished doing these tests and posting results.
I'm not using wireless, i use ethernet and usb, both output from my broadband box.

hopefully these tests show where the bug is, but I need somebody to confirm or deny this.

******

A bit more info:
I tested the download speed of my broadband box:
6.2 Mb/sec Down
928kb:sec  Up

This at least tells us what is the max that I could achieve.
Whether it is ever possible to achieve this max speed I just don't know, but windows gets reasonably close at 5.5Mb/sec.

I did a search on TCP optimizer for ubuntu, and found that others had gone before me on this - I drew a blank.

But what i did find is that some people think that the mtu setting is too high in ubuntu.

The test I believe is this;
alt+F2, type gnome-terminal
in the terminal window 
after the $ sign paste:

ping -s 1464 -c1 google.com (enter)

where 1464 is the mtu

this is my result

[COLOR=Navy]mark@mark-eME644:~$ ping -s 1464 -c1 google.com
PING google.com (209.85.227.147) 1464(1492) bytes of data.
From 192.168.0.254 icmp_seq=1 Frag needed and DF set (mtu = 1468)

--- google.com ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

mark@mark-eME644:~$ ping -s 1464 -c1 google.com
PING google.com (209.85.147.103) 1464(1492) bytes of data.
From 192.168.0.254 icmp_seq=1 Frag needed and DF set (mtu = 1468)

[/COLOR][COLOR=Black]Note: here it says Frag needed and 100% packet loss (ouch)[/COLOR]


[COLOR=Navy]--- google.com ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

mark@mark-eME644:~$ ping -s 1300 -c1 google.com
PING google.com (209.85.147.104) 1300(1328) bytes of data.
72 bytes from bru01m01-in-f104.1e100.net (209.85.147.104): icmp_req=1 ttl=52 (truncated)

--- google.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 87.525/87.525/87.525/0.000 ms
mark@mark-eME644:~$ ping -s 1350 -c1 google.com
PING google.com (209.85.146.103) 1350(1378) bytes of data.
72 bytes from bru01s01-in-f103.1e100.net (209.85.146.103): icmp_req=1 ttl=54 (truncated)
[/COLOR]
[COLOR=Black]here [/COLOR][COLOR=Black]I re-pasted the code changing the mtu to 1350
result was 0% packet loss and no frag problem[/COLOR]


[COLOR=Navy]--- google.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 89.857/89.857/89.857/0.000 ms
mark@mark-eME644:~$ ping -s 1400 -c1 google.com
PING google.com (209.85.147.106) 1400(1428) bytes of data.
72 bytes from bru01m01-in-f106.1e100.net (209.85.147.106): icmp_req=1 ttl=54 (truncated)[/COLOR]
[COLOR=Black]
[/COLOR][COLOR=Black]here [/COLOR][COLOR=Navy][COLOR=Black]I re-pasted the code changing the mtu to 1400
result was 0% packet loss and no frag problem[/COLOR]

[/COLOR]


[COLOR=Navy]--- google.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 91.142/91.142/91.142/0.000 ms
mark@mark-eME644:~$ ping -s 1464 -c1 google.com
PING google.com (209.85.227.147) 1464(1492) bytes of data.
From 192.168.0.254 icmp_seq=1 Frag needed and DF set (mtu = 1468)
[/COLOR]
[COLOR=Black]so just checked againg with 1464
and once again frag needed and 100% packet loss[/COLOR]

[COLOR=Navy]--- google.com ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

mark@mark-eME644:~$ ping -s 16436 -c1 google.com
PING google.com (209.85.227.103) 16436(16464) bytes of data.

--- google.com ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms[/COLOR]
[COLOR=Black]
[/COLOR][COLOR=Black]I then loaded network tools using the application icon on the launch bar
On the fiirst tab page "Devices" it lists my mtu as 16436

so just checked again with 16436
and once again frag needed and 100% packet loss[/COLOR]

In all my past experience mtu figures have always been 1500 or below.

So.......could this be the bug that is causing the probs?

The big question now, is how to change the mtu??

I tried pasting 2 different commands but neither worked:

gksudo gedit /etc/network/interfaces
sudo ifconfig mtu 1400

as shown here:

[COLOR=Navy]mark@mark-eME644:~$ gksudo gedit /etc/network/interfaces

(gedit:3487): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:3487): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.IVL3WV': No such file or directory

(gedit:3487): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
mark@mark-eME644:~$ sudo ifconfig mtu 1400
SIOCSIFADDR: No such device
mtu: ERROR while getting interface flags: No such device[/COLOR]


Obv........I have no idea what I'm doing.... just trying things that other people have suggested.
The last 2 commands might be out of date by now.... who knows?

But at face value...... it does look as the the mtu is incorrect.

any comment?

---

### Post by chili555 on 2011-06-17
> Obv........I have no idea what I'm doing....Obv...., indeed.

First of all, with Network Manager installed and running, /etc/network/interfaces is ignored, except for loopback. Second of all, ifconfig requires an interface to be declared; your ethernet interface is probably eth0. So:```
sudo ifconfig [COLOR="Red"]eth0[/COLOR] mtu whatever
```Next, Network Tools shows the MTU for the loopback interface as 16436. For ethernet, eth0, it's 1500.

Frankly, for you to perform ill-informed tests and then assert, without documentation, that:> Ubuntu 25% slower than Win7!!!!Is, in my opinion, very misleading. 

If you think MTU is incorrect at 1500, perform some meaningful tests and come back to ask us how to persistently set the more correct number. It's easy.

---

### Post by Ace..... on 2011-06-17
Wow!......what a great response.
A bit of vigor not least (and a gauntlet, slapped in the face, and then contemptuously thrown on the floor).

I don't think anybody could ask for better (and all this is in the honorable tradition of scientific debate).

So thanks [chili555]("http://ubuntuforums.org/member.php?u=35909")

Okay.....lets deal with the primary issue (which is all that I can deal with really) and that is the (disputed) FACT that: Ubuntu is running 25% (+) slower than Win7.

> **chili555 said:**
> 
Frankly, for you to perform ill-informed tests and then assert, without documentation, that:
Ubuntu 25% slower than Win7!!!!                      
Is, in my opinion, very misleading. 

 
In direct response to this, I need to point out that my tests with speedtest.net were as simultaneous as was allowed by the shutdown and reboot time.

I repeatedly tested the connection to Paris (using ubuntu & Firefox) and the results each time confirmed my own user experience (that something was wrong).

Actually I tested, then booted to windows, then rebooted to ubuntu, then back to windos then to ubuntu.
(check the times listed.....you can follow the story)

In fact I did this more times than are listed above, but the tests only confirmed what had already been shown.

While you may assert (surely not?) that I have fabricated these results...... the reality is that I can create a freebie account, and then share these results with you (avoiding copy and paste).

So...... on the primary issue of whether Ubuntu is running 25% slower than windows7........ as far as real world computing and browsing is concerned....... this is a fact (until you can tell me that speedtest.net is a total con - something I can take on board, if you have proof).

 As for your argument on mtu loopback interfaces (etc.)........ I really don't have a clue what you're talking about (hence my declaration to that effect).

What I do know is that I used ubuntu help documents, in order to gain the test instructions.

here is the link..... it's not the original ubuntu link, but I'd read the original earlier and recognised that it was the same document.

[http://swik.net/Ubuntu/Only+Ubuntu/How+to+Optimize+your+Internet+Connection+using+MTU+and+RWIN/cbnda](http://swik.net/Ubuntu/Only+Ubuntu/How+to+Optimize+your+Internet+Connection+using+MTU+and+RWIN/cbnda)

It is this document that outlines how to establish whether your mtu setting is too high.

I simply followed the advice....... and..... the tests (according to the document) produced results in line with what was expected.
ie. if the mtu is set too high, then you will have problems with connection speed.

If these instructions are incorrect...... or..... I did not follow them correctly...... then tell me.... but the tests appeared to produce the desired results ie. mtu too high = problems, mtu lower = no problems.

Obviously, the next step was to determine what my mtu settings were.

I had to go to the network tools application, that is provided for us..... and..... I had to believe what it said.
Why shouldn't I?

It stated that the mtu was 16436.

Well.... if that figure is being mis-reported, then we need to do something about it, cos there is no point in ubuntu help docs quoting one figure, and applications quoting another.
That much is clear.

So where do we stand now?

Certainly Ubuntu IS running 25% slower than Win7 (even though these speedtest.net results are ill informed).

What we don't yet know, is whether the network tools application is mis-reporting the mtu, neither do we know if the tests I did are valid, nor whether the help document is valid, nor whether I carried out the tests correctly.

Therefore, if I was you (in this very friendly debate), I would forget about challenging whether ubuntu is running 25% slower than windows (download speed)..... that's a lost cause.

We know what the box can deliver.
We know what Win7 can deliver (or feed through to the browser)
and similarly, we know what Ubuntu can deliver

The real question is:

**Why is Ubuntu so remarkably slower?**

Is it the mtu setting?
if not.... it must be something else.

But, one thing is for sure......... there is definitely a problem here, that is being experienced by very many people.

---

### Post by chili555 on 2011-06-17
Please see attached. What does the MTU for ethernet show?> I would forget about challenging whether ubuntu is running 25% slower than windows (download speed)..... that's a lost cause.
Perhaps for your ethernet driver, your ethernet card, your router and your ISP, it is. That I will concede. My upload and download times run at and sometimes slightly above the advertised speed from my ISP. I have no desire or budget to purchase Windows 7 to try to disprove you.

---

### Post by wildmanne39 on 2011-06-17
Hi, I have run ubuntu for years and I have windows 7 which I never boot but they run at the same speed, It is just something with your particular set up.

---

### Post by Talon2 on 2011-06-17
[QUOTE=Ace.....;10951926
**Why is Ubuntu so remarkably slower?**

[/QUOTE]

I'm seeing something that is slow but it isn't Ubuntu.

Do you really expect help given your attitude?

Do you work for Microsoft?

---

### Post by Ace..... on 2011-06-18
Sorry, but I just don't get this.
How can I have a bad attitude???? (and work for microsoft?????????)
 
I started this thread, with a clear outline, about the pc and the fact that both os's were new installs.
ie. whatever was wrong, was a result of the install.
 
After noticing a significant drop in internet performance, I tested, quite rigorously the 2 os's and posted the results.
 
I did a search and found others had the same problem....... and found ubuntu documentation....... and tried to find the problem myself (whilst hoping that somebody could point me to a fix).
 
**Is that not the absolute perfect forum attitude???????**
**Is that not how you'd like everybody to behave?????**
 
As for the title...... the first thread I started was **New PC & new to ubuntu - 1. Partition the disk?**
It went well, but became more complex.
[COLOR=darkslateblue]nothingspecial[/COLOR] suggested
> **nothingspecial said:**
> The point is, that your thread looks like a new user looking for advice on how to partition for install.....
....which it is.
Now, this is a huge place. There are users here who may know a great deal about your new issue. But may not bother reading this thread because of the title.
.... but my point is, you've got to tailor your title for the right expertise, if you see what I mean.
I just happened upon your thread, a more specific title is more likely to attract someone who knows how to solve your issue.
 
So I used the best title possible, to attract the people with the expertise to help me (and obviously I could back up the title with test results).
 
So I was expecting expertise, but instead, what I got was some 75 year old Doctor of Science, looking down from his lofty position, telling me that my speedtest.net tests were "ill-informed" (without even attempting to explain why).
 
**Is that not bad attitude?????**
**Would we really want everybody to behave like that?????**
 
So instead of actually getting on with some meaningful work, I'm forced to defend my claim that ubuntu is running slower than win7.
Which note, by the way, chili555 did accept...... and that's cool, and I'm fine with that and him.
 
My portrayal of him as a 75 year old fart is a light hearted jest, in reality pointing out that this "high & mighty attitude should have been ditched decades ago.
 
But anybody who replies to an argument, accepting the stated argument........ to me is a top bloke, the best to have in a forum, so i really have no problems with chili555.
 
I think he was just annoyed cos it looked like I was putting ubuntu down.
 
So can we please stop this discussion about attitudes (it wasn't good while it lasted).
 
What I do need is a solution to the problem.
Other people are interested in installing ubuntu, but they can't go ahead until I've sorted this out.
It's just too important.
 
For myself, I've looked at chili555 images, and have understood them (thanks chili555)
I have now changed the mtu to 1400.
and will now test again, and post the results (if they are any different from before).
 
Note: I was forced to copy this text to text notes, and save it in a Win7 directory, cos firefox would not connect again.
 
My missus had been unable to connect earlier (before changing the mtu).
I rebooted to ubuntu, but still no connection.
 
I was forced to load win7 and post this using iExplorer.
 
bummer.

---

### Post by Ace..... on 2011-06-19
Okay, setting the mtu to 1400, using network tools, actually prevented connection, so I re-set mtu to automatic.

Downloaded google-chrome, and via speedtest.net, witnessed comparable speed results with iExplorer.

So a kind of bodge solution is to simply install google-chrome.

However, that doesn't solve the underlying problem.

The clue may be found in the graph display shown during each test.

Check these out:

**iExplorer** download is totally stable - apparently a consistent stream of fast data (5.48Mb/s) running in Win7.

**Chrome** (in ubuntu) achieves similar quoted speed (5.55Mb/s), but look at the download - simply all over.
Chrome is considered by testers to be the fastest browser, yet here it is just managing to match iExplorers headline figure.

**Firefox** (in ubuntu) achieves a low speed (3.68Mb/s) and it's download graph is all over the shop.

What seems clear is that something is not right for both chrome and firefox.

What I'll do next is download chrome and firefox to windows7 and run these tests again.

---

### Post by bkratz on 2011-06-19
Have you considered upgrading to firefox 4 (I believe 5 is out too)? My browsing seems to be a lot faster (more like Chrome) than version 3.?

[http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)

---

### Post by Ace..... on 2011-06-20
I've just checked the firefox version and it is 4.0.

I am wondering whether firefox simply did a better job of their win7 variant, especially when you see the graphics below.


Ok...... having seen how chrome & Firefox perform in ubuntu, I wanted to see how they performed in Win7, so downloaded both browsers.

**Firefox & Chrome tested in Win7 (speedtest.net)**

What is interesting is that both browsers do perform better - Firefox, substantially so.

What may be worth noting is that the Firefox download graph was _very similar_ (uncannily identical in fact) to the iExplorer graph, as was the download speed.

Ping was down on iE but was an improvement over its ubuntu ping.

Chrome absolutely flew, to an extent that the download speed was more than what my broadband box display indicates.(?????)

My package is up to 8Mb/s but my box is currently connected at 6368 Kb/s.

Does this mean that the speedtest.net tests are unreliable?
I'll talk to them about that.

Anyway, here are the screenshot graphics, the file name indicates the download speed.

The next tests will be pingtest.net.

---

### Post by Ace..... on 2011-06-20
Just to round off the comment of those test results.

In Win7, both iExplorer & Firefox, produced very stable consistent results (ie. i tested a good few times and the results stayed the same).

The same couldn't be said for Chrome - each test produced a different result, though to be fair: always fastest 6+ to 7+ Mb/s


At this point, it seems there are two possibilities:

1. Both Firefox and Chrome have done a better job on their Windows variants.

2. Something/settings in the ubuntu os is preventing them from achieving the speeds that they show in Windows.

---

### Post by collisionystm on 2011-06-20
> **Ace..... said:**
> Just installed the latest 11.04 64bit ubuntu, using std cd install alongside windows7, ticking the "add all extras" option, to ensure I got all the latest drivers etc..

The pc is brand new
Acer emachines E644 - AMD 2 Core C-50
3Gb DDR3 mem
500 Gb hard drive

Pre-installed: 64bit Win 7 home premium
I've literally changed nothing in win7 other than using wubi to install ubuntu 1st time around (ubuntu appears as a win program - and was _un-installed_ as such).

**Note**: It is too late to now check, but......... under wubi/win7 I had no sense that the browser firefox was running slow - i didn't do a speedtest.net cos of other priorities (and it seemed fine).

On advice, I started again (new partitions etc).

**The Problem:** Ubuntu is now 25% slower (broadband) than Win7!!!!

Actually, it feels worse than that - more like it was on my previous lap top that had 512Mb ram running xp.
Here are the results after switching os's a couple of times. 

Firefox...................... dn........up...ping
11:04    PM","GMT","4.29","0.78","93","Paris","200"
11:05    PM","GMT","3.61","0.77","71","Paris","200"
11:12    PM","GMT","3.95","0.77","70","Paris","200"
11:23    PM","GMT","4.23","0.77","72","Paris","200"
11:23    PM","GMT","4.07","0.77","71","Paris","200"
11:24    PM","GMT","3.82","0.77","71","Paris","200"
11:27    PM","GMT","3.87","0.77","71","Paris","200"
11:37    PM","GMT","5.89","0.77","72","Paris","200"
11:38    PM","GMT","3.90","0.78","71","Paris","200"
11:39    PM","GMT","3.84","0.77","72","Paris","200"
11:40    PM","GMT","4.47","0.77","71","Paris","200"
11:40    PM","GMT","3.85","0.77","72","Paris","200"

Win7 Explorer.......... dn.......up.....ping
11:08    PM","GMT","5.48","0.78","65","Paris","200"
11:31    PM","GMT","5.48","0.78","55","Paris","200"
11:31    PM","GMT","5.48","0.78","65","Paris","200"
11:32    PM","GMT","5.48","0.78","65","Paris","200"
11:33    PM","GMT","5.48","0.78","65","Paris","200"
11:33    PM","GMT","5.47","0.78","57","Paris","200"
11:48    PM","GMT","5.49","0.78","65","Paris","200"
11:48    PM","GMT","5.49","0.79","65","Paris","200"
11:49    PM","GMT","5.48","0.78","65","Paris","200"

Firefox managed one spurious result of 5.89, but the graph (on the speedtest display) was absolutely all over the shop (like it's overall results).

Compare that to iExplorer - total stability, and in fact, more like 30% faster + a much better ping.

Anyway, I guess you know all this, I've seen that plenty of others have noticed this speed drop in the past, so:

**The Solution:**

Has a solution been found to this problem?
If not.......are any developers working on a fix?


Try your speedtest with chromium. The browser itself has alot to do with the results.

---

### Post by psusi on 2011-06-20
Did you ever check what ifconfig says your MTU is?

---

### Post by Ace..... on 2011-06-20
RE using chrome - see above - i agree, it is faster.

Re ifconfig

No, but here it is:

[COLOR="Blue"]eth0      Link encap:Ethernet  HWaddr 1c:75:08:f9:18:71  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::1e75:8ff:fef9:1871/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:111755 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86989 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:132149111 (132.1 MB)  TX bytes:9797818 (9.7 MB)
          Interrupt:40 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:50600 (50.6 KB)  TX bytes:50600 (50.6 KB)

wlan0     Link encap:Ethernet  HWaddr ec:55:f9:70:c9:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/COLOR]




this was the test i did:

[COLOR="Navy"]mark@mark-eME644:~$ ping -s 1464 -c1 google.com
PING google.com (209.85.227.147) 1464(1492) bytes of data.
From 192.168.0.254 icmp_seq=1 Frag needed and DF set (mtu = 1468)

--- google.com ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

mark@mark-eME644:~$ ping -s 1464 -c1 google.com
PING google.com (209.85.147.103) 1464(1492) bytes of data.
From 192.168.0.254 icmp_seq=1 Frag needed and DF set (mtu = 1468)[/COLOR]

Note: here it says Frag needed and 100% packet loss (ouch)


[COLOR="navy"]--- google.com ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

mark@mark-eME644:~$ ping -s 1300 -c1 google.com
PING google.com (209.85.147.104) 1300(1328) bytes of data.
72 bytes from bru01m01-in-f104.1e100.net (209.85.147.104): icmp_req=1 ttl=52 (truncated)

--- google.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 87.525/87.525/87.525/0.000 ms
mark@mark-eME644:~$ ping -s 1350 -c1 google.com
PING google.com (209.85.146.103) 1350(1378) bytes of data.
72 bytes from bru01s01-in-f103.1e100.net (209.85.146.103): icmp_req=1 ttl=54 (truncated)[/COLOR]

here I re-pasted the code changing the mtu to 1350
result was 0% packet loss and no frag problem


[COLOR="navy"]--- google.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 89.857/89.857/89.857/0.000 ms
mark@mark-eME644:~$ ping -s 1400 -c1 google.com
PING google.com (209.85.147.106) 1400(1428) bytes of data.
72 bytes from bru01m01-in-f106.1e100.net (209.85.147.106): icmp_req=1 ttl=54 (truncated)[/COLOR]

here I re-pasted the code changing the mtu to 1400
result was 0% packet loss and no frag problem


I tried changing the mtu in network tools from "automatic" to 1400, but the pc stopped connecting, so I returned the settings to automatic.

YET.......the above tests did show that there was packet loss above mtu 1400.

The only problem is that I do not know if these tests are valid.

---

### Post by chili555 on 2011-06-20
> The only problem is that I do not know if these tests are valid.
I don't believe so.> ping [COLOR="Red"]-s[/COLOR] 1464 -c1 google.comIs packet size identical to MTU? Is the result identical in every respect if you do:```
sudo ifconfig eth0 mtu 1464
ping -c1 www.google.com
```This is from *man ping*:>  -s _packetsize_
              Specifies the number of data bytes to be sent.  The default is 56, which translates into 64 ICMP data bytes when combined with the 8 bytes of ICMP header data.

---

### Post by psusi on 2011-06-20
Are you using a router?  It looks like you have a broken router that is feeding you an incorrect MTU and it needs adjusted downward because you have one of those crappy ISPs that use PPPoE, which chews up a few bytes from each frame.

---

### Post by Ace..... on 2011-06-20
@chili555

Thanks for correcting me there chili.
I ran your commands:

[COLOR="Navy"]mark@mark-eME644:~$ sudo ifconfig eth0 mtu 1464
mark@mark-eME644:~$ ping -c1 [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (209.85.147.103) 56(84) bytes of data.
64 bytes from bru01m01-in-f103.1e100.net (209.85.147.103): icmp_req=1 ttl=51 time=72.0 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 72.061/72.061/72.061/0.000 ms[/COLOR]

As you can see: no packet loss.
So..... does this mean that it is not an mtu setting problem ie. is the Network Tools "Automatic" setting likely to be functioning correctly?

One other thing:
Can we eliminate the idea that both Firefox & Chrome have been better tuned to Win7........ or could that be a reality, seeing as Windows dominates the desktop market?

@psusi

The broadband box provides the routing facilities.
An ethernet cable, plus a usb cable.

All tests have been carried out with only the ethernet cable attached, ie. only the test pc using the connection.

I have a fixed IP address.

As for whether it's crappy; well these things are made to price, cos they're given to you on joining.

However.... These tests are directly comparing the performance of firefox & chrome, in Win7....... and Ubuntu.

Both performed better in Win7 by quite a good margin (results above).

All tests used the same broadband box/router, so both os's have the same chances.

**Perhaps we should just get back to basics:**

If we assume that both ubuntu browsers are close enough in similarity to their Win7 variants (to the point where little difference should be seen).

What then, are the variables that exist between the pc ethernet plug, and the browser?


And just to make things simpler...... lets forget chrome.
Just look at firefox.

What could make firefox behave so differently in the 2 os's, based on these download graphs (bearing in mind that these graphs always came out something like this - stable and solid in win7, erratic in Ubuntu).

There has to be a clue in here somewhere no?

(note: re ping: iE is always lower than both chr &  FFox in win7 - something they're doing for their own browser perhaps?)

iE-Win7......................FFox-Win7......................FFox-Ubuntu - (filename lists download speeds)

---

### Post by psusi on 2011-06-20
> **Ace..... said:**
> 
As you can see: no packet loss.
So..... does this mean that it is not an mtu setting problem ie. is the Network Tools "Automatic" setting likely to be functioning correctly?

No, you just did a 64 byte ping.  The question is, did setting the MTU improve your speedtest results?

> **Ace..... said:**
> All tests used the same broadband box/router, so both os's have the same chances.

You ( or the installer ) probably installed their silly software in Windows, which may have fixed the MTU setting in windows.

---

### Post by Ace..... on 2011-06-21
[SIZE=2]@Chili555:[/SIZE]

**[SIZE=4]YES!!![/SIZE]**

See the graphs below - I've shown just 2, but Ffox is now running just as stable/consistent as it was in win7.

More on this below the graphs.

@psusi:

Ah yes, I get it now [COLOR=Navy]$ sudo ifconfig eth0 mtu 1464 [COLOR=Black]set the mtu, and it stayed set, presumably until reboot.[/COLOR]
[COLOR=Black]
Thanks for the timely remark!

Re: the 2nd remark - win7 was pre-installed on the brand new laptop.
Prior to installation of any software, iExplorer exhibited similar performance to what FFox is displaying now.

Therefore, I have to say that this setting was "correct out of the box".

One of the key aspects of these tests, was that I knew, everything was bog standard, and untouched.

Here are the graphs:


[/COLOR][/COLOR]

---

### Post by Ace..... on 2011-06-21
**What a great success **- thanks to everybody who has contributed.

It's not over yet though:

[LIST=1]
[*]I need to set the mtu permanently
[*]We need to determine whether this was a million to one installation glitch, or whether the install app is failing to correctly set the mtu
[/LIST]
**On the latter**: 
This was a major drop in performance........is it the case that everybody (who downloads this version 11.04 64bit) will not have their mtu set correctly?
If so, then the next version surely should have the fix in.

OR if every pc is different, then why not incorporate a "network config" routine.

**Ideas to permanently set the mtu**:

Should I try network tools again?

And what packet exactly have I tested
1464-28 = 1436
1464
1464+28 = 1492

And from this question.......... is the mtu size perfect?
Should I carry out further tests, to find the ideal setting.
ie. we now know the mtu was incorrectly set, but does that mean I've found the right setting 1st time. 

Anyway, here are a couple of mtu setting methods, but both don't seem to work as they stand
This first method seems to be mooted everywhere, but like many before me, all I have in my network interfaces file is:

auto lo
iface lo inet loopback

So perhaps this method is simply out of date.
[INDENT][COLOR=Navy]*********
Step 1 : Go to your Terminal(Applications->Accessories->Terminal) and type sudo gedit /etc/network/interfaces and enter your sudo password
Step 2 : Your text editor should now open with the interfaces file.
Step 3 : Now in the interfaces file you should find a line like this

iface eth0 inet dhcp or iface eth0 inet static

(if in your case eth1 is the interface connected to the internet then look for
[/COLOR][COLOR=Navy]iface eth1 inet dhcp or iface eth1 inet static)

Step 4 : Now under this line , add the following line
mtu 1492

So for example it would look like

iface eth0 inet dhcp
mtu 1492
*********
[/COLOR][/INDENT]This other idea seems to be to issue the "set mtu" command at boot time (yes?)
Problem is, I can't find either of these files. So this method may also be out of date.
[INDENT][COLOR=Navy]*********
in a console/terminal window type in
su - [hit enter]
[enter root password]
ifconfig eth0 mtu 1492
exit

add the ifconfig line to /etc/init.d/boot.local or on some flavors of linux to /etc/rc.local using your favorite text editor.
**********[/COLOR]
[/INDENT]Any other suggestions or modifications to bring these up to date?

:D

---

### Post by chili555 on 2011-06-21
> add the ifconfig line to /etc/init.d/boot.local or on some flavors of linux to /etc/rc.local using your favorite text editor.Please do, in a terminal:```
sudo gedit /etc/rc.local
```Add one line above the last line, exit 0:```
ifconfig eth0 mtu 1492
```Proofread, save and close gedit.

I believe ethernet interfaces come with MTU set to 1500 by default is because the developers have no idea whether you will connect to a cable modem, DSL modem, router, switch, etc. In many cases, any slight mismatch will be negligible and unnoticable to most users. The few that test and care will know or find out how to make this adjustment permenent.

---

### Post by psusi on 2011-06-21
Your router is supposed to specify the correct MTU in the DHCP lease, which is why is said before that the problem is your broken router.  1500 is correct for everyone not using the horrible broken very bad protocol known as PPPoE.

---

### Post by Ace..... on 2011-06-21
Okay, great, however, there has been an OS update today - June 21st 2011 - including lots of stuff for Firefox and everything else by the look of it.
[INDENT][I]I'd rebooted to see if my xp hard drive (from the knackered laptop) would boot from a usb port.
It wouldn't, nor in any of the safe modes - whether this is a bad boot sector or incompatibility with the 64bit architecture, I don't yet know (I can see all the data)
anyway, I got all the updates..
[/I][/INDENT]First thing I did was to check ifconfig..........mtu 1500

I then ran a few speedtest.net.
The results were: totally stable downloads!!!

I changed it to 1492 using
ifconfig eth0 mtu 1492confirmed it had changed...... ran the speedtest.net.......... similar results to mtu 1500

Rebooted....confirmed mtu 1500
ran the speedtest.net...... and the graphic below is the result.

Prior to the update, rebooting the computer made no difference at all (speeds were always down and erratic).

The only thing that has changed is the update.
Can the problem have been fixed in two or three days ie. in response to the stated problem?

Or perhaps more likely, it was earlier understood, and been a planned fix.

I kind of feel like a climber that has just struggled to make it to the peak, only to find somebody already stood there, holding a flag, and grinning.

It's what I wanted....... and the knowledge isn't lost....... I guess it was my baptism of fire.

Thanks again for everybody's help

:)

---

### Post by chili555 on 2011-06-23
Breaking news! Linux is faster than Mac or Windows!!

[http://www.zdnet.com/blog/open-source/the-best-fastest-computers-are-linux-computers/9121](http://www.zdnet.com/blog/open-source/the-best-fastest-computers-are-linux-computers/9121)

Sorry; I couldn't help myself and isn't it a bit early for my second Irish coffee???

---

### Post by psusi on 2011-06-23
> **chili555 said:**
> 
Sorry; I couldn't help myself and isn't it a bit early for my second Irish coffee???

It's 5 o'clock somewhere :)

---

