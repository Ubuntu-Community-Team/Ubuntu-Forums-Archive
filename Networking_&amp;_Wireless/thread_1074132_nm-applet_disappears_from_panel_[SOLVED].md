---
title: "nm-applet disappears from panel [SOLVED]"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by Flymo on 2009-02-18
This is just a heads-up, in case it happens to you....
Whilst fiddling about, I removed the wrong darn thing from my panel.  :oops:

...and the nm-applet was gone.  Nothing said 'nm-applet' in the 'Add to Panel' dialogue.  Networking icon was not the right thing....

So having tried the obvious, and rebooting, and fiddling with the _>System >Preferences >Sessions_ menu, and rebooting again, and finding nothing directly relevant here, I tried various things, like```
sudo nm-applet --sm-disable
```

...which did nothing that I could see, putting it in the background with '&' does the same...

[URL="http://www.linuxquestions.org/questions/linux-newbie-8/no-more-wireless-connection-in-mn-applet-ubuntu-7.10-598769/"]
Found this at Linux-questions which helped me.[/URL]

The relevant part there was :-
```
Check to see if nm-applet is a running (or sleeping) process. If so try this:
In the panel (toolbar) right click
- add to panel
- Notification area icon (scroll down under utilities)

```
...then added the Notification Area to the panel - Success!

Found that I had indeed started three instances of nm-applet, confirmed by ```
ps -ef | grep nm-applet
``` in the terminal.

All the while that my nm-applet display was missing, the WiFi was working fine.:biggrin:

Oh yes, and the other big clue?  The Power Manager icon was also missing from the panel. ** D'oh!**
Of course it too returned in the missing Notification Area.

Hope that something here was useful.

All the best, Ben

Problem was in Ubuntu 804 on Acer 4315, Celeron 540, intel 810 graphics
and Atheros WiFi using NDISwrapper, no problems with it until I did the deed. More[ here.]("http://www.hbclinux.net.nz/acer4315.html")

---

### Post by soni1770 on 2009-11-06
cheers ben, i did just the same, 
but no it's fixed!:popcorn:

---

### Post by MEmO33 on 2009-12-27
I'm absolute beginner. I reinstall the network manager and found that nm-applet didn't show up in the notification area.

So, this is what I did and it worked for me.

1. Go to **_/usr/share/app-install/desktop_** and find** Network Manager**
2. Right click.. Properties.. copy the command line
3. Go to **_System.. Preferences.. Startup Applications_** and look for ****[B] Network Manager
[/B]4. Click Edit and paste the command then save
5. Log out, log in

Command should be something like this
```
nm-applet --sm-disable
```


Hope it works for you.

---

### Post by OCromwell on 2009-12-28
that code was already there in old Network Manager command line.
But I cut & pasted it in anyway.
Saved, logged out & logged back in, no change, NM is still not showing.
Also tried de-installing NM & reinstalling it w. synaptic. that didn't help either.
Anyone got any other suggestions?

---

### Post by MEmO33 on 2009-12-29
> **OCromwell said:**
> that code was already there in old Network Manager command line.
** But I cut & pasted it in anyway.**
Saved, logged out & logged back in, no change, NM is still not showing.
Also tried de-installing NM & reinstalling it w. synaptic. that didn't help either.
Anyone got any other suggestions?

Try to go back to nm in the startup applications to see if nm command is still there because you may cut it!

I'm sorry thats all what i know.

---

### Post by ascending_8 on 2010-01-07
Yes this one helped me too.

I had removed my notification area :|

---

### Post by Bagleemo on 2010-01-13
Brilliant! Thanks very much for sharing this information. Solved my problem, seemingly caused by enabling auto-hide with the panel on Karmic.

---

### Post by iarmolatii on 2010-05-03
Nothing helped me ... no Network Manager in the tray ... however Network Manager is in StartUp Programs ... any ideas?

---

### Post by SabreWolfy on 2010-06-01
Lucid. NM works fine, but fails to autoconnect eth0 when PC powers back automatically after a power failure.

I removed the commented "iface eth0 inet dhcp" line from /etc/network/interfaces and rebooted. Eth0 connected (although it always does; my problem is that it does not connect when the PC powers up from a power failure). However, now NM applet was not showing in the panel, even though it is running). Commenting the line out and restarting returned the applet to the panel.

---

### Post by aspectratio on 2010-06-02
I have this problem in Lucid too. I've found a fairly reliable workaround.

- First make sure you have a notification area applet running in the panel. nm-applet uses this to display itself.
- Open a terminal window and restart network manager

**sudo restart network-manager**

The nm-applet icon should now appear in the notification area.

---

### Post by robfantini on 2010-06-18
Hello, I ran into the same problem using Debian Squeeze.  I got clues to the solution for my setup from this thread.  This is the script I now use. Probably it is overkill but it works for me.

```

cat nm-applet-start

killall  -s 9 nm-applet
/etc/init.d/network-manager stop
/etc/init.d/networking stop
/etc/init.d/networking start
/etc/init.d/network-manager start
/usr/bin/nm-applet --sm-disable


```

use sudo to run the script

---

### Post by mgois on 2010-07-05
I had a similar issue in my system and it turns out that the problem was that no network interface was being managed by the *network-manager*. More precisely, a few days ago I had been messing with **/etc/network/interfaces** and configured the **eth0** interface there. Apparently, *network-manager* ignores the interfaces already configured in this way (which makes sense. if someone configured the interface in this "classic" way, it probably doesn't want it overriden by *network-manager*), and since that's my only network interface, there were none left for it to manage. Solution: remove all mention to **eth0** from the **/etc/network/interfaces** file (since I wanted to benefit from *network-manager*), restart it ```
sudo service network-manager restart
``` and voilá, *nm-applet* is back.
Now, there is a related problem. *nm-applet* was indeed running and on the notification area. It just didn't show an icon (!!), but with some luck, clicking on the area sometimes showed it's menu! This behaviour is undesired since an icon should always be presented even when there are no managed interfaces. I'll file it as a bug. Hope it helps.

---

### Post by jobsworth on 2010-07-12
> **Flymo said:**
> This is just a heads-up, in case it happens to you....
Whilst fiddling about, I removed the wrong darn thing from my panel.  :oops:

...and the nm-applet was gone.  Nothing said 'nm-applet' in the 'Add to Panel' dialogue.  Networking icon was not the right thing....

So having tried the obvious, and rebooting, and fiddling with the _>System >Preferences >Sessions_ menu, and rebooting again, and finding nothing directly relevant here, I tried various things, like```
sudo nm-applet --sm-disable
```

...which did nothing that I could see, putting it in the background with '&' does the same...

[URL="http://www.linuxquestions.org/questions/linux-newbie-8/no-more-wireless-connection-in-mn-applet-ubuntu-7.10-598769/"]
Found this at Linux-questions which helped me.[/URL]

The relevant part there was :-
```
Check to see if nm-applet is a running (or sleeping) process. If so try this:
In the panel (toolbar) right click
- add to panel
- Notification area icon (scroll down under utilities)

```
...then added the Notification Area to the panel - Success!

Found that I had indeed started three instances of nm-applet, confirmed by ```
ps -ef | grep nm-applet
``` in the terminal.

All the while that my nm-applet display was missing, the WiFi was working fine.:biggrin:

Oh yes, and the other big clue?  The Power Manager icon was also missing from the panel. ** D'oh!**
Of course it too returned in the missing Notification Area.

Hope that something here was useful.

All the best, Ben

Problem was in Ubuntu 804 on Acer 4315, Celeron 540, intel 810 graphics
and Atheros WiFi using NDISwrapper, no problems with it until I did the deed. More[ here.]("http://www.hbclinux.net.nz/acer4315.html")

Thank you for your excellent post.
That worked for me to.
I was messing with remote desktop, I think, when the accident happened.
The only difference was that the shutdown icon did not reappear.
Instead there is a Shut down entry in the System Menu,
which happens sometimes. I don't know why.

---

### Post by sightsoundsoul on 2010-07-18
Thank you, everyone. The "sudo restart network-manager" brought the applet back for me in Ubuntu Studio 10.04. Now I just need to figure out how to use it to connect.

---

### Post by walt.smith1960 on 2010-07-18
There's another cause of network manager not appearing.  I don't make a Wireless connection available to all users on a machine.  Instead, I create a connection for each user.  If more than one user is logged on, network manager seems to only appear for one user.  When the first logged-on user logs off, network manager will then appear to the second user.  Noob problem?  Probably, but this might help other noobs.

---

### Post by dpilgrim on 2010-09-10
> **jobsworth said:**
> Thank you for your excellent post.
That worked for me to.
I was messing with remote desktop, I think, when the accident happened.
The only difference was that the shutdown icon did not reappear.
Instead there is a Shut down entry in the System Menu,
which happens sometimes. I don't know why.

Wow, this was a life-saver for me too. Here was my comedy of errors:
* I accidentally removed the notification area (was trying to remove what looked like a duplicate Opera icon on the panel)
* My wireless mistakenly connected to my neighbor's access point across the street (this happens periodically)
* All my attempts to point my wireless to the correct AP were foiled because -- you guessed it -- nm-applet was still running, just not displayed.

By the way, can I just say how much I hate the notification area? Where the heck do I go to configure this thing? Because I still have an Opera icon in it that I do not want, and my battery indicator is gone and I don't know how to get it back, and the whole notification area is not movable on the panel like any normal icon would be. These are the sloppy little bits that drive me crazy about Ubuntu.

---

### Post by cvalentine02 on 2011-04-30
I had random disconnects & disappearances of the nm-applet. Changing manage=true didn't work. Running scripts to restart services as sudo was only temporary. I finally followed the advice here to fix my issue:
[https://bbs.archlinux.org/viewtopic.php?id=63576](https://bbs.archlinux.org/viewtopic.php?id=63576)

I changed the group listed to "admin" which my user is a part of, instead of "network" as described in the thread. I'm confident the issue is directly related to LDAP group permissions, which I use for authentication.

You can verify this is the same issue by attempting to run nm-applet as non-sudo user & you will receive the error:
```
[user@ubuntubox ~]$ nm-applet
** (nm-applet:2622): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service.
   Message: 'Connection ":1.24" is not allowed to own the service "org.freedesktop.NetworkManagerUserSettings" due to security policies in the 
configuration file'
```

---

### Post by isosi on 2011-11-07
I have the same problem with 11.04 Ubuntu Studio. 
nm-applet was not showing up inside Indicator applet and random one applet load error in panel just after login.
The fix was to change a session from Ubuntu safe mode to Ubuntu Classic in user login screen.

---

