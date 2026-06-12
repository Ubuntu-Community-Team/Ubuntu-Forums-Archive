---
title: "nm-applet doesn't start on ubuntu startup"
date: 2010-05-23
forum: Networking &amp; Wireless
---

### Post by srikesh on 2010-05-23
Hello,

I am not sure why, but my wireless networking icon on the top right of the panel doesn't show up any more during startup.  Previously during startup, the applet would show up and then after a while connected to my wireless network seamlessly.

The only thing I did before and after it stopped working was to enable auto login.  I cannot disable auto-login through the GUI and according to postinings in the forums no one knows how to do it through the command line interface.

In the 'Startup Applications' menu it is checked for startup with the command line saying "nm-applet --sm-disable".  What can I do to have the network manager icon automatically startup when I turn on Ubuntu? Right now I get it to work by typing "sudo nm-applet" in the terminal window and then pasting my wireless encryption key.

Thanks in advance for your help.

OS: Ubuntu 10.04
Kernel: 2.6.32-22-386
GUI: Gnome

---

### Post by Iowan on 2010-05-23
You might try adding a "Notification Area" to the top panel - some threads have fixed their Network Manager applet problems this way. 
(Your mileage may vary ;) )

---

### Post by srikesh on 2010-05-24
> **Iowan said:**
> You might try adding a "Notification Area" to the top panel - some threads have fixed their Network Manager applet problems this way. 
(Your mileage may vary ;) )

Thanks Iowan,

I tried that.  The newly added notification area has no icons at all.  Adding "Notification Area" doesn't solve my problem.

---

### Post by decoherence on 2010-05-24
In my case it appears to have started, it just doesn't show up. If i try to run nm-applet from the command line i'm told it is already running, also

** (nm-applet:3166): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

Notification area is showing and completely empty.

---

### Post by gsimpson on 2010-05-27
After installing Skype (from Ubuntu software center)The wireless applet disappeared (may have been coincidence as I had played with autohide). I got it to display by selecting "show hide buttons" (right click on top panel and select properties). The applet reappeared and stays there when "show hide buttons" is deselected.

---

### Post by mmepis on 2010-05-28
I had the same problem start yesterday. I noticed the sound wasn't working so after running an update I attempted to restart or shut down but the system would only log off. After a hard power off and restart the nm-applet wont autostart even though it's still checked in the Startup Applications. I've had to manually start the nm-applet to get online.

---

### Post by The_Eddster on 2010-06-27
I've had the same problem but it only started a few days ago, about the same time the suspend mode stopped working.

Sometimes the nm-applet starts on boot, but starts disabled by default. Other times the icon doesn't appear and instead I get a white square in the indicator tray. The only way I can fix it temporarily is to manually shutdown and restart the nm-applet from the terminal:

kill-all nm-applet
nm-applet

---

### Post by kwestrom on 2010-07-09
The nm-applet is not starting up anymore upon system boot. The network manager just suddenly stopped working(=became disabled) and then disappeared in trying a reboot to see if the nm-applet would enable afterwards.  
When 'apt-get check' or 'apt-get autoremove' is run it shows: 
'The following packages have unmet dependencies:  kdelibs5: 
Depends: libqt4-qt3support (>=4:4.6.2) but it is not installed; Recommends: kdebase-runtime (>=4:4.2.2) but it is not installed.' 

The system is an Acer Aspire One running 10.04 UNR/UNE, and there is no capability to reenable the nm-applet in the title bar without a big fix underneath. Please help, thanks.

---

### Post by Inder on 2011-06-04
Similar problem here. nm icon doesn't show and right clicking the top bar doesn't do anything (so no preferences option...). Also, killall nm-applet doesn't kill nm-applet, I can still see it in the system monitor and trying to relaunch it outputs > An instance of nm-applet is already running.
I also tried click "end process" from the system monitor. Nothing happens. It's like an invincible process!

I can use wired AND wireless internet, but the wireless sometimes fails.. It fails less often than before upgrading from 10.04 to 11.04 though.

---

### Post by rajendran.bits on 2011-08-02
I am also facing the same problem. The nm-applet is not at all auto starting.. I have tried in google for many days and didn't find any solution... If any of you find any solution please let me know.. that would help me in big way.. 

Thanks,
Rajendra

---

### Post by dineshs on 2011-08-03
Go to system-preferences-startup applications and ensure that network manager is ticked.What do you get for ```
cat /etc/network/interfaces
```

---

### Post by Inder on 2011-08-03
I get this

$cat etc/network/interfaces
> auto lo
iface lo inet loopback

edit: And I can't find system-preferences-startup...

---

### Post by nm_geo on 2011-08-04
Please Note Natty 11.04 information.

There is some good info on the link below.  I believe you will  get your nm-applet back if you make the whitelist 'all' or if you add wicd it can then be in the upper panel.

[Install Dconf Editor]("apt:dconf-tools")
 Now hit the ALT+F2 key combination and type *[COLOR=#008080]dconf-editor[/COLOR]*. Click the Dconf-editor icon. When the "Configuration Editor" window appears go to "[COLOR=#808080]*desktop -> unity -> panel*[/COLOR]", click the value line on the systray-whitelist option and replace everything on that line with [COLOR=#008080]*'all'*[/COLOR]. Log out and log back in. See the below screenshot, we now have Pidgin on system tray, yes!

[http://news.softpedia.com/news/Ubuntu-11-04-Unity-Tips-and-Tricks-]("http://news.softpedia.com/news/Ubuntu-11-04-Unity-Tips-and-Tricks-204538.shtml")
[204538.shtml]("http://news.softpedia.com/news/Ubuntu-11-04-Unity-Tips-and-Tricks-204538.shtml")

another way in terminal run this.

```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```

---

### Post by ispecialboy on 2012-07-25
try command: sudo service network-manager restart.
After that, if the applet turns up again, it means the network manager itself is good. All we need to do is to change the boot sequence of DBUS & NM.
if your DEAMONS in rc.conf reads as below,
DAEMONS=(hwclock syslog-ng netfs networkmanager @crond dbus @cpufreq)
change to 
DAEMONS=(hwclock syslog-ng netfs @crond dbus networkmanager @cpufreq)
or maybe (sorry that I haven't had a chance to test yet. But I sure I got the applet icon
back in the notification area after restart the NM service).
DAEMONS=(hwclock syslog-ng netfs dbus networkmanager @crond @cpufreq)
 
This solution comes from [https://bbs.archlinux.org/viewtopic.php?pid=1036598](https://bbs.archlinux.org/viewtopic.php?pid=1036598).
 
Hope it works for you as well.

---

### Post by wildmanne39 on 2012-07-25
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

