---
title: "Ubuntu Will NOT Establish DHCP w/ Router from the Command Line; nm-applet works fine"
date: 2010-04-27
forum: Networking &amp; Wireless
---

### Post by GSF1200S on 2010-04-27
Im wondering if im missing something. I have nm-applet installed, and it has no issue connecting to an unencrypted home wireless network (named linksys). On my arch box, I connect in the following manner:
```
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid linksys
sudo dhclient wlan0
```
and I receive a DHCP bind with the router just fine. On Ubuntu, it just repeats "DHCPDISCOVER" over and over again, never giving me a dhcp release. I can Ctrl+C out of dhclient, and immediately get a DHCP bind no issue with nm-applet.

I can ping the router just fine, but it will not give me DHCP from the command line. Is there a lock file or pid I need to kill in order to do this?

I ask because I have another issue where my screen shuts off if I kill GDM (/etc/init.d/gdm stop); Im trying to connect via the command line so I can ssh into my box while the monitor is off and see if I can restart X. Any help would be appreciated...

---

### Post by GSF1200S on 2010-05-05
I installed the latest nvidia from the X ppa and it fixed my framebuffer issue; I can now kill GDM and get to a console. I tried again to connect to the internet via command line but could not establish a dhcp release- I can connect to the router, ping the router and receive a response (by this I mean I can connect to the essid and ping the routers IP as seen by other computers in the house), but when I attempt to run:
```
sudo dhclient wlan0
```
It just hangs on dhcpdiscover being repeated over and over until it terminates. Anyone with an idea?

If you dont have any ideas, but connect to a wireless network (and are on 10.04), can you please try a connection via the command line and let me know if you get a dhcp release? If this affects more than just me, Ill file a bug report..

---

### Post by WalmartSniperLX on 2010-05-05
Actually I noticed I did one extra step before doing "sudo ifconfig wlan0 up
" 

```
sudo wpa_supplicant -Bw -c/etc/wpa_supplicant.conf -iwlan0 
```

Then I do what you have listed. Not sure if that will do anything for you but I get positive output when running ```
 sudo ifconfig wlan0 up
``````

sudo dhclient wlan0
```

---

### Post by GSF1200S on 2010-05-05
> **WalmartSniperLX said:**
> Actually I noticed I did one extra step before doing "sudo ifconfig wlan0 up
" 

```
sudo wpa_supplicant -Bw -c/etc/wpa_supplicant.conf -iwlan0 
```

Then I do what you have listed. Not sure if that will do anything for you but I get positive output when running ```
 sudo ifconfig wlan0 up
``````

sudo dhclient wlan0
```

wpa_supplicant is something you use when you have a WPA encrypted home network. For ease of installing Arch and such, I recently switched my routers WPA encryption off, but Ubuntu will still not connect via command line- Arch connects just fine. Thanks for the suggestion :)

---

### Post by GSF1200S on 2010-05-06
This issue drove me insane, as I must have internet for the command line in that I run X ppa's and bleeding edge video drivers (sometimes even to use the links web browser on command line). I finally traced it down to gnome-network-manager, which Xubuntu uses by default.

It turns out that gnome-network-manager will not allow dhclient or wicd to establish a dhcp address if its installed. The only way to get internet working on boot before GDM loads is to right click on the network manager applet and go to: Edit Connections. In the box that follows, select the wireless tab, select the network you want to make available, and then check the checkbox at the bottom that says "Make Available to All Users." 

However, that only allows nm-applet to connect you to that network at boot (before X loads). As gnome-network-manager doesnt have a cli-interface, you cant connect to the internet if that network is not available (even if other networks are).

What I eventually did was install wicd:
```
sudo apt-get install wicd
```
and also installed the GUI interface, ncurses interface, and the CLI interface:
```
sudo apt-get install wicd-gtk wicd-curses wicd-cli
```

With this setup, you can use Wicd-gtk (which autostarts in your systray just like nm-applet) to connect to the network when X loads. If X doesnt load or you are in the CLI for some reason, you can use:
```
wicd-curses
```
to get a listing of your networks, as well as connect to them (it will prompt you for passwords and everything if necessary).

Hope this helps someone who suffers with the problem as I did :)

---

