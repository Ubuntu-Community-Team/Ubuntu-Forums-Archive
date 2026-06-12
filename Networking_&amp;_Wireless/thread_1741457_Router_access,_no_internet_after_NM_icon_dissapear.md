---
title: "Router access, no internet after NM icon dissapeared"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by jaguare22 on 2011-04-28
Today I set my HPG50 with Ubuntu 10.10.  I used network install disk, then tasksel to add Ubuntu Desktop.  Everything was fine, I set up my samba shares and a few other things.  I had the NM icon on the panel but did have to configure.  I was on wired connection and I could surf no problem.  When I went to set up the wireless, I noticed the icon was gone.  I know it was there after the install.  At some point the network manager icon disappeared, not sure when because I could still access the router and internet.  I spent a few hours surfing google and the forums trying to find an answer.  Then, after running update and upgrade I lost internet.  Even though I could see the router, I connected straight to the modem, still no internet access.   I unplugged the cable from that machine and plugged it into my other system and I could surf just fine.  

It was clear that nm-applet was running from running nm-applet at the terminal -

nm-applet - "An instance of nm-applet is already running - Warn Couldn't initialize the D-Bus manager.

nm-tool - State - connected, Driver r8169, State Unmanaged, Default no.  NetworkManager.State - All three entries are set to "true".
 
It seems clear that some other app is managing my connection as I can access the router and am currently serving video to my apple tv from this system.  How do I find which app is managing my connection?

Thanks, I'll see if I can ssh from here so I can cut and paste more info...

---

### Post by uncaspi on 2011-04-28
See man netstat

---

### Post by jaguare22 on 2011-04-28
Thanks, the -i options tells me there are no packets being dropped, that helps.  Still reviewing man page.

dmesg last few lines -

r8169 0000:01:00.0: eth0: link down
r8169 0000:01:00.0: eth0: link up

These two lines repeat about 10 more times.

Also, further up is - eth0: no IPv6 routers present

Not sure if those lines help to diagnose....

---

### Post by jaguare22 on 2011-04-28
More info....

Couple things to note, router access controls are not blocking systems IP.  Also, I am surfing from a different system on the same router right now.  I can VNC to the problem system from this system.

Wireless is down too.  Button is blue but pressing or pressing and holding has no effect.  rfkill list all lists no soft or hard blocks.  

lshw -C network -
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=             latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:42 ioport:3000(size=256) memory:90410000-90410fff memory:90400000-9040ffff memory:90420000-9043ffff
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-28-generic firmware=N/A ip=          latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:92600000-9260ffff

---

### Post by uncaspi on 2011-04-28
Could be that there is a bad wired connector since repeting of the UP/DOWN lines 10 times.Do you have another cable you could try?

---

### Post by jaguare22 on 2011-04-28
Tried another cable to be sure, though I had already used the same cable on another system successfully.  No change.  I have router access but no internet.

Tried installing WICD by downloading to other system and transfering over LAN.  WICD config asked for intltool, ran that no errors.  Then WICD asked for gettext, ran that no errors.  But when I ran WICD config again it still said can't find GNU Gettext. ????

Any other ideas?  Thanks.

---

### Post by uncaspi on 2011-04-28
Do you have nm icon now? What about your wireless? What do you get from sudo iwlist scan

---

### Post by jaguare22 on 2011-04-28
Thanks again for the help.  Still no icon.  Wireless button is blue (goes red during reboots) but pressing or pressing and holding for 10, 20 even 30 seconds has no effect.

iwlist scan -

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

---

### Post by uncaspi on 2011-04-28
Plug in your cable and do sudo dhclient eth0
See if you got an ipaddress sudo ifconfig eth0

---

### Post by jaguare22 on 2011-04-28
Well dhclient reported the IP I expected all appeared to be in order from that command but it also killed the connection to the router.  Tried ifconfig, ifconfig down and ifconfig up all reported "no device found". Had to reboot.  

I should mention I have the NIC configured with static IP and the router leasing that IP to that system.  

Either way, after reboot I still have same scenario.  

While I prefer to find solutions rather that band-aids or backtracking, I am seriously considering re-installing the system.  I decided to use the mini.iso cd and tasksel believing it would give me a liter install, it did under 4 GB.  Was this the wrong approach?

Thanks....

---

### Post by uncaspi on 2011-04-28
reinstall is a solution since it seems to be something more than only NM.

---

### Post by jaguare22 on 2011-04-28
Looked at ifconfig again decided to start eliminating variables.  Commented wireless interface out of interfaces config. When I restarted the network I had no connection at all.  After I rebooted though I have internet access again, wired of course.  Seems safe to say that the wireless was interfering some how?  Still have no nm icon though and still don't know how/what is managing the network.  At least now I can access the repositories.  

Not sure where to go from here.  Would like to have wireless option but wireless still unresponsive to button press. Going through System, Admin, Network I can bring up config screen, there are no entries wired or wireless.

How can I find out what is managing the connection?

---

### Post by uncaspi on 2011-04-28
You could skip NM and try wicd. sudo apt-get remove network-manager
sudo apt-get install wicd

---

### Post by jaguare22 on 2011-04-28
Shoot, wish I'd seen that before I rebooted again....back to same issue.  Based on info from another post I changed "managed=false" to managed=true in nm-system-settings.conf and rebooted.  No icon, no internet, just lan.  Changed it back and rebooted but it didn't help.

---

### Post by jaguare22 on 2011-04-28
Just wanted to say how much I appreciate all of the people who try to help others in the forum.  I have found most of my help just searching and can't say enough about how great it is to have this resource....



dmesg - 

m="apparmor_parser"
[   19.577518] type=1400 audit(1304025996.360:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=799 comm="apparmor_parser"
[   19.608557] r8169 0000:01:00.0: eth0: link up
[   19.608564] r8169 0000:01:00.0: eth0: link up
[   19.828994] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1a0b1, caps: 0xd04711/0xa00000/0x20000
[   19.892353] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input10
[   20.325304] type=1400 audit(1304025997.108:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1095 comm="apparmor_parser"
[   20.347813] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.828684] Skipping EDID probe due to cached edid
[   21.196101] Skipping EDID probe due to cached edid
[   21.319970] ppdev: user-space parallel port driver
[   21.572485] padlock: VIA PadLock not detected.
[   21.597632] padlock: VIA PadLock Hash Engine not detected.
[   22.175021] Adding 6143996k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:6143996k 
[   22.472553] Skipping EDID probe due to cached edid
[   22.611814] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro,commit=0
[   22.840041] Skipping EDID probe due to cached edid
[   23.216028] Skipping EDID probe due to cached edid
[   23.576541] Skipping EDID probe due to cached edid
[   25.280012] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro,commit=0
[   30.296025] eth0: no IPv6 routers present
[   39.292069] Skipping EDID probe due to cached edid
[   39.656034] Skipping EDID probe due to cached edid
[   40.016048] Skipping EDID probe due to cached edid
[   40.392046] Skipping EDID probe due to cached edid
[   43.748040] Skipping EDID probe due to cached edid
[   47.624531] Skipping EDID probe due to cached edid
[   67.389224] lo: Disabled Privacy Extensions

---

### Post by uncaspi on 2011-04-28
After you executed the dhclient eth0 command you have to add a route to the router to access internet.sudo route add default gw x.x.x.x eth0
where x.x.x.x is your router. View with sudo route -n

---

### Post by paul_will on 2011-04-28
I have an issue with a dual boot and rebooting - I have to actually power off and drain the system for 10 seconds or so because the network card (onboard) remembers its config and does not seem to get reinitialised with a soft reboot. I wonder if the LAN may be using the mac address which doesn't change (normally) but the system may be confused not knowing its IP which the internet must use? Anyway try a full power down - off at the mains.

---

### Post by jaguare22 on 2011-04-28
Here are the results with IP's in x's...

sudo route add default gw x.x.x.x eth0
SIOCADDRT: File exists
G50:~$ sudo route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
x.x.x.x                 0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0               x.x.x.x            0.0.0.0              UG    0      0        0 eth0

Paul_Will, 

Tried your suggestion as well and internet was restored.  Not sure if it was because of that or the commands issued above.  Wireless button still unresponsive and no nm-applet icon.  

Should I try installing WICD?

---

### Post by uncaspi on 2011-04-28
x.x.x.x = ipaddress gateway to your router i.e 192.168.0.1

---

### Post by jaguare22 on 2011-04-28
Sorry for not being clear.  I used the correct IP's for the command but changed input/output IP's to x's for the post.  I had read it is best to exclude IP's and MAC's in posts.

---

### Post by uncaspi on 2011-04-28
ok. To access internet now through your eth0 card you must put the nameservers into /etc/resolv.conf

can you now ping google.com

---

### Post by jaguare22 on 2011-04-28
uncaspi,

The name server IP was already there but I had also installed WICD.  WICD is working with some effort required after booting.  

- After reboot, hard or soft, I have to open WICD (it's in start up and connects automatically) and disconnect then reconnect the wired connection.  If I don't do that the system can still access the router but not the internet.  Once that is done the wired connection works fine.  I have not yet tested wireless.

I will continue to work on getting to the bottom of the problem and would welcome additional help in that regard.  

For now should I remove network manager from the start up apps list?  Should I remove it from the system entirely?    

Thanks, J

---

### Post by uncaspi on 2011-04-28
You should remove it.

---

### Post by paul_will on 2011-04-28
Think I have the same network driver as you so I'd hold out for the powerdown! Just looked up to my panel to see my nm-applet had vanished too. Logged in as another user and found it OK. Returned and still gone so..:
```

paul@Blackbox:~$ nm-applet
An instance of nm-applet is already running.
paul@Blackbox:~$ ps -ef|grep nm-app
alex      2697  2622  0 Apr28 ?        00:00:01 nm-applet --sm-disable
paul      4126  4101  0 00:21 pts/0    00:00:00 grep --color=auto nm-app
paul@Blackbox:~$ sudo kill -9 2697
[sudo] password for paul: 
paul@Blackbox:~$ nm-applet
** Message: applet now removed from the notification area
** Message: applet now embedded in the notification area
```
and lo and behold its back on my panel - and my driver is the r8169. GOK why another user should have privately claimed the applet. Following code above I'm the only one with it now.

'Fraid I'm not using wireless so can't help on that one.

---

### Post by paul_will on 2011-04-28
OMG just about to shutdown for bed when I noticed this  on my terminal added to the code in my last post:
```
** (nm-applet:4131): DEBUG: going for offline with icon: notification-network-ethernet-disconnected
** (nm-applet:4131): DEBUG: foo_client_state_changed_cb

(nm-connection-editor:4237): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

** (nm-connection-editor:4237): WARNING **: dispose: CEPolkitButton object 0x9b0d80 disposed twice

(nm-connection-editor:4237): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

** (nm-connection-editor:4237): WARNING **: dispose: CEPolkitButton object 0x9b0c60 disposed twice
```

but the icon is still in place and working!  Goodnight!

---

### Post by jaguare22 on 2011-04-28
Thanks Paul_Will, very interesting.  Here is mine, though it has some extra stuff - Warning about D-Bus manager, it's essentially the same only my icon did not reappear.


user1@G50:~$ nm-applet
An instance of nm-applet is already running.

** (nm-applet:3057): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

user1@G50:~$ ps -ef|grep nm-app
user1    1841  1743  0 16:03 ?        00:00:00 nm-applet --sm-disable
user1    3065  3038  0 16:58 pts/1    00:00:00 grep --color=auto nm-app
user1@G50:~$ sudo kill -9 1841
[sudo] password for bigcat: 
user1@G50:~$ nm-applet
** Message: applet now removed from the notification area
** (nm-applet:3081): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:3081): DEBUG: old state indicates that this was not a disconnect 0

Guess I will just uninstall as uncaspi suggests and continue with WICD.  At least I can get to the gui, disconnect/reconnect and have it working.  With nm I could get to the gui through the menus but there were no connections there and when I added one it never got used/connected.  Well it has been educational as usual.  Still wins over doze every time.

J

---

### Post by jaguare22 on 2011-04-28
Update - Installing WICD gave me a workaround for network functionality.  Then I started looking into why the icon for Wally (desktop background program) wasn't there either I found Indicator Applet developers page and in questions this command and statement 

- gconftool --recursive-unset /apps/panel && killall gnome-panel
Will set the panels to defaults and you can build from there - 

Doing this brought back my Wally icon and brought up a WICD icon which had not been there following the install of WICD.

Now running nm-applet at the prompt brings - 

@G50:~$ nm-applet
** Message: applet now removed from the notification area
** Message: applet now embedded in the notification area
** (nm-applet:4481): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:4481): DEBUG: old state indicates that this was not a disconnect 0

But still no icon.  For anyone who has lost nm-applet icon, I would have tried this first....

---

### Post by paul_will on 2011-04-29
In case anyone else should want to kill and rerun nm-applet, I (we?) made the mistake of running it in foreground. If you close the terminal the applet dies with it. So suggest running it in background:  nm-applet&    or more silently 
```
nm-applet >dev/null 2>&1 &
```But this still won't give it to other users. Maybe someone can tell us how gdm runs it for everyone? It looks to me like the first login takes ownership or the process. I have plenty more questions about gdm with more than one user so I'm off to start a new thread: Logout hangs the console.

---

