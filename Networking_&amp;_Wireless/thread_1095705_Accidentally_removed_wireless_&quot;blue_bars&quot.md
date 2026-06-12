---
title: "Accidentally removed wireless &quot;blue bars&quot; icon in Gnome.  Hardy"
date: 2009-03-14
forum: Networking &amp; Wireless
---

### Post by BBBThunda on 2009-03-14
I've been scouring forum postings for a week or two now and I've just about given up.  

A while back I messed up my Gnome desktop, including moving the top panel to the right side of the screen, removing a  bunch of icons such as the battery status icon and the wireless icon that looks like 4 blue bars of varying heights.

Now I can't choose which wireless network I'm connected to.

I've tried the following already:

killall nm-applet
nm-applet --sm-disable

upon running nm-applet, the terminal window hangs indefinietly until I press CTRL+C.

Originally, after installing drivers, etc. I got this working by running "iwconfig" and "iwlist scan", but now when I run iwconfig I get the following output:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated 

Can someone PLEASE help me understand why I'm getting these messages and what I can do to fix them?

Thanks in advance for your help!

---

### Post by BBBThunda on 2009-03-14
**UPDATE:**

This morning I added the Notification Area to the top panel and now I again have the battery meter and update icons, etc. But the wireless icon is still missing.  

In addition, I forgot to mention before, but the network manager icon is there (looks like 2 little monitors), but in no way does this help me control wireless.  I found a screenshot which shows both this NM icon and my missing wireless icon:

[IMG]http://www.debianadmin.com/images/wpa/2.png[/IMG]

I'm connected to the internet through wireless right now, but I'm willing to bet I'm connected to my neighbor's unsecured router, rather than mine.

Any help would be much appreciated!

---

### Post by BBBThunda on 2009-03-14
**ONE MORE UPDATE:**

I just tried prepending the "wlist scan" command with "sudo" and now I'm getting this:

$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:90:4C:7E:00:6E
                    ESSID:"Celtics"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:4/5  Signal level:-63 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s



So I guess eth1 is my wireless adapter?  It continues to list all of the other networks in range, one of which is my network that I want to connect to.  (for now I will figure out how to connect to it through the terminal if that's possible)

But I still do not have the wireless "blue bars" icon in my panel.

---

### Post by |{urse on 2009-03-14
open a terminal and type

nm-applet

does that resolve it?

if so, 

Add nm-applet to Startup Programs.  You can find this in:
Panel Menu > System > Preferences > Sessions

Find the entry for Network Manager.  If it is missing, add one.  The entries are:

Name: Network Manager
Command: nm-applet --sm-disable
Comment: Network Manager applet

---

### Post by ugm6hr on 2009-03-14
> **BBBThunda said:**
> In addition, I forgot to mention before, but the network manager icon is there (looks like 2 little monitors), but in no way does this help me control wireless.  I found a screenshot which shows both this NM icon and my missing wireless icon:

The 2 little monitors are probably NM.

The fact that they don't help connect to wifi does not necessarily mean it is not running.

Post a screenshot of what it looks like when you left-click it.

---

### Post by mattsmatrix on 2009-03-15
All you have to do to add your wireless "blue bars" icon is :

Right click on the panel
Then left click "Add to Panel"
Scroll down to "Notification Area"
Then left click "Notification Area"
After that then left click "Add"
It should bring back your wireless "blue bars" icon. It worked for me and I'm new to Ubuntu. If it doesn't instantly bring it up try restarting your computer. Good Luck and please share your experiences with our new friends and family using Ubuntu Linux!

---

### Post by BBBThunda on 2009-03-22
**UPDATE:**

Ok, after the last post I made I gave up and switched back to Windows for a few days (mainly to test some web design stuff in explorer), and when I finally made it back to Ubuntu, I noticed the icon is back!  And the icon is indeed part of the Notification Area, although I had already added that before my last post (see above).

The NM icon (with the 2 monitors) is also still there and is NOT part of the Notification Area.

Despite restarting a number of times while working on this last week, it still wasn't resolving the issue.  But of course I don't know exactly what I did, so I don't have a specific solution for this issue.

I doubt running nm-applet by itself solved the problem, since that kept hanging, and I know I did not manually add anything to my startup scripts.

If anyone is interested in pursuing root cause further, let me know and I will be happy to provide more info.  But from my end this is resolved.

---

### Post by John Jason Jordan on 2009-04-25
> **mattsmatrix said:**
> All you have to do to add your wireless "blue bars" icon is :

Right click on the panel
Then left click "Add to Panel"
Scroll down to "Notification Area"
Then left click "Notification Area"
After that then left click "Add"
It should bring back your wireless "blue bars" icon. It worked for me and I'm new to Ubuntu. If it doesn't instantly bring it up try restarting your computer. Good Luck and please share your experiences with our new friends and family using Ubuntu Linux!

This installs the notification area which, on my Jaunty computer shows a Bluetooth icon and a Tracker icon as well. I want just the network icon. I can quit the other two, but the next time I log in they are back. 

Is there a way to remove unwanted parts of the notification area permanently? Or is there a different icon that will display available networks as a drop-down list?

---

### Post by jsimonelis on 2010-05-12
Darn. I am having this problem. I'm sad to see it isn't resolved.

---

### Post by hafiz123 on 2010-06-26
i am hafiz from pakistan and i have read all of your posts and i like all of it.thanks for sharing such type data.now i am here unintentionally.but next time i will be here for preparation and submit something different for all of you people kindly wait for me.i ,ll miss you all of you people.

---

### Post by Mahrous on 2010-10-27
i had this problem with Opensuse ...any way the solution is really simple i am not sure if it's the same with ubuntu though , 
open network settings 
in network setup method choose "user controlled with NetworkManager"
 that's it ..the wireless icon appeared in notification area

---

### Post by d5e5 on 2010-11-29
> **mattsmatrix said:**
> All you have to do to add your wireless "blue bars" icon is :

Right click on the panel
Then left click "Add to Panel"
Scroll down to "Notification Area"
Then left click "Notification Area"
After that then left click "Add"
It should bring back your wireless "blue bars" icon. It worked for me and I'm new to Ubuntu. If it doesn't instantly bring it up try restarting your computer. Good Luck and please share your experiences with our new friends and family using Ubuntu Linux!
I made the same mistake and had to live without blue bars for a few days until I read the above solution. I use Ubuntu Karmic Koala and the above steps restored the blue bars right away. Thanks.

---

