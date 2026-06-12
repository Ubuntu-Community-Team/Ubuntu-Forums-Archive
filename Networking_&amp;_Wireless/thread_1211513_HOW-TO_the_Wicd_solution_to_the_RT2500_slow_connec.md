---
title: "HOW-TO: the Wicd solution to the RT2500 slow connection problem"
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by RavanH on 2009-07-12
Hi all, 

Let me start with a short description of the extremely slow speed and timeouts **problem** I was facing with my Ralink RT2500 based (integrated laptop) wireless card. After that, I will describe my **solution** step by step. And although all went smooth for me, I will follow with a short list of possible **issues** you might encounter and finish with how to **revert** to your old setup. 

[COLOR="DarkRed"]NOTE: This is a hands-on, DIY solution that I have tested only for a short period (impatiently wanting to share it ;) ) so please let me know if I can expect to run into any problems. And if there is another/better way, which I have not found, to solve the issue.
This method has been tested on Ubuntu 9.04, Xubuntu 9.04 and [Ubuntulite]("http://u-lite.org/") 0.8 (thanks to [hellion0]("http://ubuntuforums.org/member.php?u=383591")).

REQUEST: I am a (X)Ubuntu user but I hope this works for Kubuntu too. If you find there should be some changes to make it work on these or other distros, please let me know and I will incorporate them.
Thanks![/COLOR]


[INDENT][FONT="Century Gothic"][SIZE="5"][COLOR="DimGray"]**Problem**[/COLOR][/SIZE][/FONT][/INDENT]

I have a laptop with integrated Ralink wireless card using --like many others-- the RT2500 chipset. Since my upgrade to Jaunty, I found that my connection speed was always extremely slow. Webpages would trickle load for several minutes if not just time out, and any streaming media impossible to listen/watch because after each two seconds the stream would stall and hang for *more* than a few seconds. Even the admin page of my router would be subject to this tiresome slowness. Another oddity was the fact that signal strenght was always shown at much lower level than should be.

All this would no longer be the case as soon as I reconnected to my trusty old LAN cable again. (Sadly, since lightning struck our telephone wire, my LAN card is toasted. Now I really HAD to find a solution!)

I had originally installed Wicd because I like it much and it saved me from problems with the same RT2500 card a long time ago (under Feisty, I think) but I decided to try Network Manager again. Sadly, the problem persisted. However I learned from the connection information that Network Manager gave me that the connection speed (rate) was fixed at 1Mb instead of anything nearer the max 54Mb if my WLAN router.

Searching these forums I notice I am not the only one with this problem. A quick fix was presented in one thread in the form of entering the following in a terminal window, where the 11M stands for a connection speed (rate) of 11Mb/s:
```
sudo iwconfig wlan0 rate 11M
```

I tried this and immediately my reported connection speed jumped up to 11Mb, signal strenght was reported at a more convincing level and more importantly: actual surfing and streaming was back at comfortable speed ! Hurray :)

But then I realized that I would have to do this after each boot/login. Not very convenient, so I searched further and found another thread where the fix was combined with hard coding it into another, unrelated (anacron) boot script so that this would be automatically done during each boot-up. An excellent solution but not very elegant, I thought, considering it could be overwritten during an upgrade or what not.

Then it hit me: Trusty old Wicd! Did I not notice an option to set up scripts to run on pre-, post- and disconnection? *Oooh, my preciousssssss... come back to me!* ;)


[INDENT][FONT="Century Gothic"][SIZE="5"][COLOR="DimGray"]**Solution**[/COLOR][/SIZE][/FONT][/INDENT]

This step-by-step should be fairly simple, but if anything is unclear, please ask and I will edit if necessary. 

**Prerequisites**
- You should be logged in as user that is in the sudoers list, meaning you have administrative rights (but are not root) so you can install packages.
- If you already have Wicd on your system you can skip to Part II of the process.


[INDENT]**Part I: "Get Wicd with it!"**[/INDENT]

**1. Add the Wicd repository to your sources list.**

NOTE: This is  OPTIONAL but ADVISED for pre-Karmic users. If you feel more comfortable with sticking to official Ubuntu packages, you *can* skip this step *but* there is a somewhat outdated version of Wicd in the official Ubuntu repositories. At the time of writing this how-to (Juli 15, 2009) this is version 1.5.9 and although, it works just fine it will only allow you set up a connection specific speed-up script but no global pre-connection speed-up script. The latter is useful for those that use their wireless for roaming (see part II). Karmic repos carry version 1.6.1, which is better, but to get the latest stable version with more options (and improved performance if you select **ioctl backend** under Preferences > Advanced Settings -- I highly recommend it :) ) continue with this step. At the time of writing the latest stable version is up to 1.6.2.

Open Synaptic Package Manager and go to Settings > Repositories > Third Party Software > Add..., and enter the following line:
```
deb http://apt.wicd.net jaunty extras
```

Open a terminal window and enter the following line:
```
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
```

Close the Package Sources dialog window and hit 'Refresh' in Synaptic Package Manager or do in terminal:
```
sudo apt-get update
```

ALTERNATIVE: Download the deb package of the latest stable version from [http://downloads.wicd.net/pkgs/stable/](http://downloads.wicd.net/pkgs/stable/) (browse through to the latest version, choose ***xUbuntu*** folder - small x meaning any Ubuntu derivative not just Xubuntu!) and install it by double clicking the downloaded file.

**2. Get the default Network Manager packages stored locally.** 

NOTE: This is OPTIONAL but [COLOR="DarkRed"]ADVISED if you are solely dependent on wireless for your Internet connection! You are also advised to note down the instructions on **Reverting to Network Manager** at the bottom...[/COLOR] Without it, you will not have deb packages of Network Manager to fall back on, in case Wicd does not play for you. If you can easily connect via your LAN (an Ethernet card and that gray cable, remember? ;) ) you *can* skip this step.

[INDENT]For Ubuntu/Xubuntu users, Network Manager + the Gnome Front-end:
```
sudo apt-get install -d --reinstall network-manager gnome-network-manager
```

For Kubuntu users, Network Manager + the KDE Front-end:
```
sudo apt-get install -d --reinstall network-manager network-manager-kde
```[/INDENT] 

**3. Install Wicd** (Wireless Internet Connection Daemon, read more on [http://wicd.net/]("http://wicd.net/")) the easy "Ubuntu way". You can find it in Synaptic or just do in terminal: 
```
sudo apt-get install wicd
```

This will force Network Manager to be ***removed*** from you system. 

NOTE: After Network Manager being removed, you will get an error message from the running NM Front-end about missing resources and it will close. Just move to the next step and all will be fine again.

**4. Reboot your system and use Wicd to connect to your wifi signal.**

Open the Wicd Manager by double cliking the system tray icon. If you have no Wicd systray applet/icon, open the Wicd Network Manager from the your Application Menu or give the command wicd-client (use the -n switch if you are running a desktop without notification area) in terminal. Set your WPA or other encryption options under 'Advanced Settings' (1.5.9) or 'Properties' (1.6.x), right below the signal entry (in version 1.5.9 you need to unfold the entry pane by clicking the connection title). You can check 'Automatically connect to this network' if you like too.


Now that you have Wicd up and running and your connection is active -- although still painfully slow -- we can move to the actual fix...


[INDENT]**Part II: "Speed it up!"**[/INDENT]

**5. Add the speed-up script** 

The actual script we will be using below is ```
sh -c "/sbin/iwconfig wlan0 rate 11M"
```

[COLOR="DarkRed"]NOTE 1: The last part of the speed-up script '11M' will force the connection speed to jump to 11Mb/s which is is just fine for me since it gives me a very stable connection (as opposed to the full 54MB which is also possible with my Wifi router) and my provider limits my bandwidth to 2Mb anyway. But if you absolutely need more speed, just experiment and pump it up to e.g. 36MB or 54MB if you like.

NOTE 2: If your wireless card is not set up to be available on *wlan0* but for example on *eth1*, *wmaster0* (thanks [acutshall1]("http://ubuntuforums.org/member.php?u=890558")) or *ra0*  (thanks [hellion0]("http://ubuntuforums.org/member.php?u=383591")), adapt the script accordingly.[/COLOR]

Now you have two options here. If you use your wireless to connect to the same few wifi signals (or just one home signal) all the time, you can follow only the easy part **5. Home/Office** but if you use your wireless for a large part for roaming (connecting to new signals often) you might want to (also) follow part **5. Roaming**.

[INDENT]**5. Home/Office**. 

I. Open Wicd Network Manager by clicking on the tray icon or via your Network menu. Then click **Scripts** (1.5.9, unfold the entry pane by clicking the connection title) or **Properties > Scripts** (1.6.x) right below your active connection and enter your user password. The Configure Scripts dialog comes up. 

II. Now enter in the script (above) in the Pre-connection Script field. 

III. Hit OK to save.

Do this again for any secondary signal you normally connect to like your Office or the public wifi at you regular lunch place :) Depending on signal strength and connection stability, you can experiment with higher speeds for each signal.

NOTE: You might run into a little bug in Wicd after entering your password. If so, you will get a system warning about Wicd Manager not responding anymore. Ignore it and just hit Cancel to continue. The Scripts dialog window might be hidden behind the Wicd Manager window!

**5. Roaming**. 

If you use your laptop for roaming and connect to new signals on a regular basis, you might want to make the speed-up script available for each new connection. After that, you can still use the Home/Office method if you want to tweak your regular wifi signals. 

I. Create a new file by opening a terminal window and entering the command
```
sudo gedit /etc/wicd/scripts/preconnect/rt2500fix
```
NOTE: Adapt this to use **kate** for Kubuntu/KDE or **mousepad** for Xubuntu/XFCE instead of gedit.
This will bring up the text editor with a blank file. 

II. Now enter the script (above) as the only (!) content. 

III. Hit 'Save' and close the editor.

IV. Finally in terminal enter ```
sudo chmod a+x /etc/wicd/scripts/preconnect/rt2500fix
```[/INDENT]

**6.** Disconnect and reconnect to make the script run and go and visit your favorite download or streaming website! :)

You should immediately notice you are back to browsing at normal speed... If not, read on.


[INDENT][FONT="Century Gothic"][SIZE="5"][COLOR="DimGray"]**Possible issues & Tips**[/COLOR][/SIZE][/FONT][/INDENT]

**TIP: faster connection time**
For better performance in establishing a connection, get the latest stable version (read step 1.a) and select **ioctl backend** under Preferences > Advanced Settings.

**I am unable to connect**
If you cannot get Wicd to connect to any wifi signal, you might want to:
**1.** Check the content of /etc/network/interfaces. It should be nearly empty, only containing: 
[INDENT]auto lo
iface lo inet loopback[/INDENT]
If it doesn't, edit the file (and make a backup copy) with ```
gksudo gedit /etc/network/interfaces
``` (for Gnome, so adapt this command for your distro specifics: use *mousepad* in xubuntu, *kate* on Kubuntu instead of *gedit*)
**2.** Make sure Wicd is set up to manage the correct wireless interface. Open the Wicd Manager and hit 'Preferences'. Check if the field 'Wireless Interface:' shows the correct interface. Normally this would be **wlan0** but on your system it might be set up differently like **eth1**, **wmaster0** (thanks [acutshall1]("http://ubuntuforums.org/member.php?u=890558")) or **ra0**(thanks [hellion0]("http://ubuntuforums.org/member.php?u=383591")) for example .

**There is no Wicd tray icon after login**
Open Startup Applications (under System > Preferences menu, in Gnome at least) and see if there is an entry for Wicd. If so, make sure there is a check mark beside it or if the content is correct. If not, add a new entry with Name: **Wicd** and Command: **wicd-client**, then save and logout and back in again. If that does not do the trick, head over to the [Wicd forum]("http://wicd.sourceforge.net/punbb/") to get expert help on manually getting the systray applet up and running.
 
**I can connect but still at turtle slow speed** :( 
First reboot the system and reconfirm. Then you might want to check if the script should be altered in any way to fit your system. Open the Wicd Manager and hit 'Preferences'. The field 'Wireless Interface:' shows your current (and apparently working) interface. Normally this would be **wlan0** but if it is anything else like **eth1** or **ra0** (thanks [hellion0]("http://ubuntuforums.org/member.php?u=383591")) for example, please copy the content of the field and use that to replace the wlan0 part of the script.
If that still does not work, use the original code **sudo iwconfig wlan0 rate 11M** (or adapted code to fit your system) in a terminal screen to find any errors. Report them in this forum thread...

**All works well but signal *strength* is still not shown correctly**
Place a check mark at the option 'Use dBm for displaying signal strength' under 'Preferences' (1.5.9) or 'Preferences Advanced Settings' (1.6.x) in the Wicd Manager.

**I can connect to any open signal and speed fix works but cannot connect to encrypted signal**
I found the only setting for WPA Supplicant-driver under Preferences in the Wicd Manager that works on my system is **wext** but you might try other options (like the ralink legacy driver) to see if that fixes the issue. Please head over to the Wicd forum on [http://wicd.sourceforge.net/punbb/]("http://wicd.sourceforge.net/punbb/") for expert help.

**I get a system message: The window "Wicd Manager" does not respond**
You might run into a little bug in Wicd, where after clicking the Scripts button, you get a warning like "The window Wicd Manager is unresponsive" with the options Cancel and Force close. Just choose Cancel to continue and ignore this warning. 
[COLOR="DarkRed"]NOTE: The Scripts dialog window might be hidden behind the Wicd Manager window![/COLOR]


[INDENT][FONT="Century Gothic"][SIZE="5"][COLOR="DimGray"]**Reverting to Network Manager**[/COLOR][/SIZE][/FONT][/INDENT]

Wicd did not play for you? No problem. Just reinstall the Network Manager packages and your system is back to where you were before and search on for your slow connection problem.

[INDENT]For Ubuntu/Xubuntu users, Network Manager + the Gnome Front-end:
```
sudo apt-get install network-manager gnome-network-manager
```

For Kubuntu users, Network Manager + the KDE Front-end:
```
sudo apt-get install network-manager network-manager-kde
```[/INDENT]

There is a good [alternative method suggested by olejon involving ndiswrapper]("http://ubuntuforums.org/showthread.php?t=1211513&page=2#11") in this thread. Other ways to get around the slow connection issue can be found on these forums. Try [http://ubuntuforums.org/showthread.php?t=1148109](http://ubuntuforums.org/showthread.php?t=1148109) or [http://ubuntuforums.org/showthread.php?t=1251983](http://ubuntuforums.org/showthread.php?t=1251983) for instance.

---

### Post by hellion0 on 2009-07-13
Thanks for that! Suddenly my Thinkpad is usable again thanks to this fix. You can add U-Lite to the systems it's known to work on.

Quick note: On my system (installed as Feisty and upgraded since all the way to Jaunty), the interface is ra0 instead of wlan0. This may be common for more upgraded systems, so there's one to look for if you're not sure.

I've also posted a link to this How-To on my blog.

---

### Post by RavanH on 2009-07-14
> **hellion0 said:**
> Thanks for that! Suddenly my Thinkpad is usable again thanks to this fix. You can add U-Lite to the systems it's known to work on.

Quick note: On my system (installed as Feisty and upgraded since all the way to Jaunty), the interface is ra0 instead of wlan0. This may be common for more upgraded systems, so there's one to look for if you're not sure.

I've also posted a link to this How-To on my blog.

Glad it worked out :) Thanks for the tip on ra0, i'll edit it in...

---

### Post by scxtt on 2009-07-15
worked great for me too, thank you so much! :)

---

### Post by demonon on 2009-07-15
Thanks, I needed this solution because I did not like to play around with the other boot up script.
This solution is just fine to me.

---

### Post by hhh on 2009-07-26
Ravan, found your thread via...
[http://ubuntuforums.org/showthread.php?t=1148109](http://ubuntuforums.org/showthread.php?t=1148109)

Thanks for the wicd solution. Moment of panic when it spit out an error message about missing something after install, but everything was working after the reboot (running Ubuntu Jaunty). An elegant solution, I even like the tray icon, cheers.

---

### Post by RavanH on 2009-07-26
> **hhh said:**
> Ravan, found your thread via...
[http://ubuntuforums.org/showthread.php?t=1148109](http://ubuntuforums.org/showthread.php?t=1148109)

Thanks for the wicd solution. Moment of panic when it spit out an error message about missing something after install, but everything was working after the reboot (running Ubuntu Jaunty). An elegant solution, I even like the tray icon, cheers.

Glad it worked out for you too. 

Do you remember what that message was? When did it happen: you started Wicd after install and got the error but after reboot, that error no longer happened?  I will try and reproduce this with a fresh install of Jaunty if I have the time.

Just a TIP: read about the latest version on [http://wicd.net/punbb/viewtopic.php?id=595](http://wicd.net/punbb/viewtopic.php?id=595) (why it is not in the Ubuntu repo's yet and more importantly where to get it ;) )

The current version in the Ubuntu repo is 1.5.9 but a greatly improved version 1.6.2 is out since the beginning of July. It responds much faster than older versions when you select the IOCTL backend under Prefs > Advanced Settings.

---

### Post by hhh on 2009-07-26
> **RavanH said:**
> Glad it worked out for you too. 

Do you remember what that message was? When did it happen: you started Wicd after install and got the error but after reboot, that error no longer happened?
I was running Network Manager as I installed Wicd, so the message I'm sure was just Wicd protesting that it wasn't ready to make a connection yet (immediately after install, before the first reboot - Wicd started automatically after install if I'm remembering right). Crap, I can't remember what it was missing exactly, something it needed to establish a connection, not a dependency, a missing service? Module? A reboot is necessary anyway after install and that sorted it, so I wouldn't worry about it.

When you say the new version responds quicker, do you mean you get a faster connection speed or that the connection gets established quicker? Also, I installed via your second method, apt-get. What's the best way to upgrade?

I'm busy now but I'll post my driver info to the workaround sticky and quote your solution from earlier in that thread.

---

### Post by RavanH on 2009-07-27
> **hhh said:**
> I was running Network Manager as I installed Wicd, so the message I'm sure was just Wicd protesting that it wasn't ready to make a connection yet (immediately after install, before the first reboot - Wicd started automatically after install if I'm remembering right). Crap, I can't remember what it was missing exactly, something it needed to establish a connection, not a dependency, a missing service? Module? A reboot is necessary anyway after install and that sorted it, so I wouldn't worry about it.

When you say the new version responds quicker, do you mean you get a faster connection speed or that the connection gets established quicker? Also, I installed via your second method, apt-get. What's the best way to upgrade?

I'm busy now but I'll post my driver info to the workaround sticky and quote your solution from earlier in that thread.

Right, that reboot is defenately needed to get rid of the last residues of NM and for Wicd to come up. I will put some more emphasis on it in the how-to.

When I say that latest version is faster (at least in my experience) I mean it establishes a wifi connection much faster, just after login or if a connection is dropped. Before I would sometimes get a response from my IM client that autostarts on login that there'd be no network available (IMpatient little client ;) ) but now Wicd has got the connection up even before any tray icon has loaded so I-M happy now...

---

### Post by RavanH on 2009-07-27
> **hhh said:**
> ...Also, I installed via your second method, apt-get. What's the best way to upgrade?...

Just follow the link in the other installation method, browse through to the latest version and choose your Linux variant (xUbuntu in your case, where small x stands for any flavour of Ubuntu), download and open the deb package ( double-click it from your desktop for example) and that version will be installed over the older one. You can still always revert or remove it via apt-get or the Synaptic packages manager. If a newer version becomes available in the official repo's, it will upgrade automatically together with other packages through the Update Manager.

---

### Post by olejon on 2009-08-01
I bought a CNet Wireless-G CWP-854 PCI-card some years ago, and it has a RT2500 chip. It worked fine then (with the then called rt2500 kernel module), but now with Kubuntu 9.04 and the default rt2500pci kernel module, it sucks. It goes to 1 Mb/s on auto (I get like 8 Kb/s), and I solved that by adding this to /etc/rc.local before "exit 0" (no need for Wicd for this):

```
iwconfig wlan0 rate 54M
```

Every rate above 1 Mb/s (like 2 Mb/s) seems to give maximum speed for me, around 2 Mb/S. 54 Mb/s also gives around 2 Mb/s. I am a bit far from the access point.

But still it was VERY unstable, and disconnected all the time, and as mentioned, I got only 2 Mb/s.

I solved ALL my problems by using ndiswrapper:

1. I installed "ndisgtk"
2. I downloaded this file and installed the .exe in Windows: [http://www.cnet.com.tw/driver/cwp854degcwm854degcwc854degh.zip](http://www.cnet.com.tw/driver/cwp854degcwm854degcwc854degh.zip)
3. I removed the rt2500pci module before the next step using "sudo rmmod rt2500pci"
4. I opened "ndisgtk" and chose "Install new driver" and then I browsed to my Windows partition to find the Rt2500.INF file, in "C:/Windows/Program Files/RALINK/RT6x Wireless LAN Card/Installer/WINXP" and installed it
5. Blacklisted the module "rt2500pci" by putting "blacklist rt2500pci" in /etc/modprobe.d/blacklist.conf
6. Restarted

No I have better signal strenght, it does not disconnect at all, and goes to 54 Mb/s on auto, even though I am far from the AP, and I get full speed (same as other machines in the room). I am happy.

---

### Post by ugm6hr on 2009-08-02
Have just tried Wicd 1.6.2 + your script with 36M speed on an Edimax EW-7318USg (RT2501 USB chipset) with Jaunty default rt73usb / rt2500usb driver combination using static IP.

Still a little unstable, in that it appears to disconnect and reconnect at will.  Nevertheless, it gives torrent download rates of up to 250kB/s according to Transmission.  Pinging from another network attached computer appears to get a ping back in 40-60ms even when it is in the process of disconnecting (compared to 4-6ms at other times).

Glad for the help...

EDIT: I think I have a hardware problem :(

---

### Post by SammyBoy247 on 2009-08-02
[SIZE="7"]Thank-you[/SIZE]

---

### Post by acutshall1 on 2009-08-12
ubuntu wmp54g.....sorry for being such a newbie but which one of these do I download

---

### Post by TheNosh on 2009-08-12
i've been using wicd for a couple of months and i love it, i'll have to try that script of yours though, thanks.

---

### Post by acutshall1 on 2009-08-12
I downloaded the 1.6.2 all.deb and installed, received and error about conflicts with NM. I went to synaptics and installed the included version of wicd and then installed the 1.62. that seemed to work .

The issue I have is now I do not get a wireless signal at all. there is no wireless tab in the wicd

this is what i have
network               
       description: Ethernet interface
       product: 82547EI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 00
       serial: 00:11:d8:8e:db:cf
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI duplex=full firmware=N/A ip=192.168.1.9 latency=0 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: a
       bus info: pci@0000:03:0a.0
       logical name: wmaster0
       version: 01
       serial: 00:23:69:d8:d0:cc
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 5e:33:ef:bb:73:0f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes




this is what I had when it was working



*-network               
       description: Ethernet interface
       product: 82547EI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 00
       serial: 00:11:d8:8e:db:cf
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI duplex=full firmware=N/A latency=0 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: a
       bus info: pci@0000:03:0a.0
       logical name: wmaster0
       version: 01
       serial: 00:23:69:d8:d0:cc
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=rt2500pci ip=192.168.1.9 latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2e:1e:e9:4f:2e:b9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


 i have tried the legacy RAlink and wext. my network uses wep 40 bit, broadcast ssid. I am not seeing any networks at all.

any suggestions?

---

### Post by RavanH on 2009-08-13
> **acutshall1 said:**
> I downloaded the 1.6.2 all.deb and installed, received and error about conflicts with NM. I went to synaptics and installed the included version of wicd and then installed the 1.62. that seemed to work .
Thanks for pointing this out. Indeed installing the version from the officail repo first is the best way to go about it...

> **acutshall1 said:**
> ... The issue I have is now I do not get a wireless signal at all. there is no wireless tab in the wicd

...
any suggestions?

My first thoughts are: 
- Check if Wicd is trying to connect with your wifi card on **wmaster0** (not eth1 or wlan0 or anything else) by opening the Wicd Manager > Preferences > tab General Settings, the value at "Wireless interface" should be wmaster0. 
- Else: do you have this issue with the version (1.5.9) from the Ubuntu repo as well or only with the new version 1.6 ? Are your networks 'hidden' or are they open? 
- And what if you do in terminal: "sudo ifconfig wmaster0 up"?

To truely help you out with this technical issue is over my head, sorry. But I am very sure you can get help from the main devs over at the Wicd forum on [http://wicd.net/punbb/index.php](http://wicd.net/punbb/index.php) (they will be interested in why it did not work out of the box for you!)

---

### Post by RavanH on 2009-08-13
> **acutshall1 said:**
> ubuntu wmp54g.....sorry for being such a newbie but which one of these do I download

Do not be sorry, newbies are very welcome :) (besides, i am NO expert myself ;) )

About your question: I do not understand what you mean, can you explain to me what download you are talking about? 

If you are tryin to download the latest version of Wicd, please install the one included in the oficial Ubuntu repo **first** by opening a Terminal window (find it in your Applications > Accessories menu) and entering the command
```
sudo apt-get install wicd
```

---

### Post by RavanH on 2009-08-13
> **olejon said:**
> I bought a CNet Wireless-G CWP-854 PCI-card some years ago, and it has a RT2500 chip. It worked fine then (with the then called rt2500 kernel module), but now with Kubuntu 9.04 and the default rt2500pci kernel module, it sucks. It goes to 1 Mb/s on auto (I get like 8 Kb/s), and I solved that by adding this to /etc/rc.local before "exit 0" (no need for Wicd for this):

```
iwconfig wlan0 rate 54M
```

Every rate above 1 Mb/s (like 2 Mb/s) seems to give maximum speed for me, around 2 Mb/S. 54 Mb/s also gives around 2 Mb/s. I am a bit far from the access point.

But still it was VERY unstable, and disconnected all the time, and as mentioned, I got only 2 Mb/s.

I solved ALL my problems by using ndiswrapper:

1. I installed "ndisgtk"
2. I downloaded this file and installed the .exe in Windows: [http://www.cnet.com.tw/driver/cwp854degcwm854degcwc854degh.zip](http://www.cnet.com.tw/driver/cwp854degcwm854degcwc854degh.zip)
3. I removed the rt2500pci module before the next step using "sudo rmmod rt2500pci"
4. I opened "ndisgtk" and chose "Install new driver" and then I browsed to my Windows partition to find the Rt2500.INF file, in "C:/Windows/Program Files/RALINK/RT6x Wireless LAN Card/Installer/WINXP" and installed it
5. Blacklisted the module "rt2500pci" by putting "blacklist rt2500pci" in /etc/modprobe.d/blacklist.conf
6. Restarted

No I have better signal strenght, it does not disconnect at all, and goes to 54 Mb/s on auto, even though I am far from the AP, and I get full speed (same as other machines in the room). I am happy.

Thanks for sharing :)

---

### Post by acutshall1 on 2009-08-13
> **RavanH said:**
> Thanks for pointing this out. Indeed installing the version from the officail repo first is the best way to go about it...



My first thoughts are: 
- Check if Wicd is trying to connect with your wifi card on **wmaster0** (not eth1 or wlan0 or anything else) by opening the Wicd Manager > Preferences > tab General Settings, the value at "Wireless interface" should be wmaster0. 
- Else: do you have this issue with the version (1.5.9) from the Ubuntu repo as well or only with the new version 1.6 ? Are your networks 'hidden' or are they open? 
- And what if you do in terminal: "sudo ifconfig wmaster0 up"?

To truely help you out with this technical issue is over my head, sorry. But I am very sure you can get help from the main devs over at the Wicd forum on [http://wicd.net/punbb/index.php](http://wicd.net/punbb/index.php) (they will be interested in why it did not work out of the box for you!)


I noticed that the logical name had changed and I believe it is listed as WLAN0 in WICD properties so I will check that out first.
Network is broadcasting SSID and using wep,40 bit; I did not see anywhere in WICD to enter these
When you do an install of 1.6 over exsiting WICD does it over write 1.5.9, if so how do I get it back? How do I unistall1.6?
 Thanks if all else fails I will  contact the WICD forum; I will also post the results of my endeavor here for others.

thx!

---

### Post by RavanH on 2009-08-13
> **acutshall1 said:**
> I noticed that the logical name had changed and I believe it is listed as WLAN0 in WICD properties so I will check that out first.
Network is broadcasting SSID and using wep,40 bit; I did not see anywhere in WICD to enter these
When you do an install of 1.6 over exsiting WICD does it over write 1.5.9, if so how do I get it back? How do I unistall1.6?
 Thanks if all else fails I will  contact the WICD forum; I will also post the results of my endeavor here for others.

thx!

I never done it before but in Synaptic there is an option to 'force' a version. Open Synaptic Package Management and find wicd. Highlight wicd and click the menu Package > Force version... You can now select the older 1.5.9 version.

I am not sure what happens if Canonical decides to put a newer version up in the official repo. Your Upgrade Manager might stick with this older version whatever happens...?

---

### Post by acutshall1 on 2009-08-14
> **RavanH said:**
> I never done it before but in Synaptic there is an option to 'force' a version. Open Synaptic Package Management and find wicd. Highlight wicd and click the menu Package > Force version... You can now select the older 1.5.9 version.

I am not sure what happens if Canonical decides to put a newer version up in the official repo. Your Upgrade Manager might stick with this older version whatever happens...?


although I rebooted several times after installing wicd my wireless connection was never found...however I go to work for 8hours,  come home and it is working. Kinda like my mac.... if i try to boot it up after 8 hours it never launches the OS however if I reboot immediately after it has been running it works fine; go figure!

Something else mysterious.. if I enter the logical name of my network**(wmaster0)**
***-network DISABLED**
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: d
       bus info: pci@0000:03:0d.0
       logical name: wmaster0
       version: 01
       serial: 00:23:69:d8:d0:cc
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci latency=64 module=rt2500pci


 in the wicd\preference\wireless interface it doesnot work howevr if I put **wlan0** it does.

***-network**
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: d
       bus info: pci@0000:03:0d.0
       logical name: wmaster0
       version: 01
       serial: 00:23:69:d8:d0:cc
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci ip=192.168.1.9 latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11bg



Although using wicd has solved the issue of disconnecting I am still at a speed of 1.5 mbps even though I entered script in wicd. My signal strength is 59dbm/using wep


Any suggestions?

---

### Post by RavanH on 2009-08-14
@acutshall1

Why wlan0 works and wmaster0 does not, i have no clue... Very strange. 

Do you use wlan0 or wmaster0 in the pre-connection script?

What is the output of iwconfig in terminal window?

---

### Post by acutshall1 on 2009-08-14
tried both; I also tried this

The script I picked was /etc/init.d/anacron, which I kludged as follows:
[quote]

     (start of  anacron script)
	|
	|
	|
# Short-Description: Handle anac(h)ronistic cron
### END INIT INFO
# /etc/init.d/anacron: start anacron
#

PATH=/bin:/usr/bin:/sbin:/usr/sbin

# kludge to speed up wlan0
iwconfig wlan0 rate 36M
# end kludge

test -x /usr/sbin/anacron || exit 0

. /lib/lsb/init-functions

case "$1" in
  start)
	|
	|
      (etc)
[unquote]



does not make a difference, when I use speedcheck.net my speed is 1.5 download and 3.5 up.

Here is my Twindow

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"6TJQE"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:24:D2:68:4D:7E   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=70/100  Signal level:-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

 **sudo lshw -C network**





*-network
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: d
       bus info: pci@0000:03:0d.0
       logical name: wmaster0
       version: 01
       serial: 00:23:69:d8:d0:cc
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci ip=192.168.1.9 latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11bg

Thanks

---

### Post by RavanH on 2009-08-15
@acutshall1,

you should definately be using wlan0 not wmaster0 (even though that is reported by lshw) so if you do in terminal ```
sudo iwconfig wlan0 rate 54M
``` then wait 20 or 30 seconds and try ```
iwconfig
``` again, you should be seeing that the line > ...
Bit Rate=11 Mb/s   Tx-Power=20 dBm
...
changed to 
> ...
Bit Rate=54 Mb/s   Tx-Power=20 dBm
...

If it does, at least the script is working and something else is causing slow data throughput. If not, somehow your Wireless card is limited to 11Mb/s which it should not be since it reports being a "wireless=IEEE 802.11bg" card.

In any case, you download speed is much lower than it should be even with a 11M rate. Do you know if there are other access points in your neighborhood that are using the same channel (2.462 GHz = channel 11 if I am not mistaken) or channels close to yours (using channels 8 to 10 or 12+, if allowed) with any significant signal strength? Can you change your router to use a channel that is at least three channels away from any other channel used by a strong wifi signal in your neighborhood?

If you live in an apartment building and there are many wifi signals around using a wide spectrum or channels, choose a channel that overlaps with the weakest signal that you can find but has NO (or minimal) strong signals that are 2 or (better) 3 levels up and down from the chosen channel. 

Hope i explained that clearly :)

---

### Post by yo shu la on 2009-10-12
Thank you RavenH. 
I Am using Linux Mint "Gloria" and a real nOOb at all this. I found your guide a real gem and was pleased with myself for managing to follow it without making a real mess of things.
I presume you need to run the "Speed it up" script for each wireless network you connect too? If so is there a way around this.
Thank you again.
Yo Shu La!

---

### Post by RavanH on 2009-10-13
> **yo shu la said:**
> ...
I presume you need to run the "Speed it up" script for each wireless network you connect too? If so is there a way around this.
Thank you again.
Yo Shu La!
Hi Yo Shu La, welcome to the Linux user community and thanks for your kind words!  :)

Yes, you are right. The script will only be triggered when reconnecting to the network you have set the script up for. If you are roaming and constantly using new networks, it might be inconvenient for you to keep adding the same script to the new network, then disconnecting and reconnecting again to make it work... 

An alternative would be to hit Alt+F2 (after each new connection where speed is again slow) and enter ```
gksudo iwconfig wlan0 rate 54M
``` (adapt to your wireless and preferred speed) and after a few seconds, the speed should go up. The command window will remember this command for the next time. Just do Alt+F2 again and hit the arrow down (either on your keyboard or by clicking the arrow next to the command field) and that same command can be used over and over again!

All the way at the end of the how-to, I gave some links to other threads with alternative methods. Most may seem a little more daunting for any newby but you might try.  

I'll propose some global pre-connection script feature to the developers of Wicd. It would indeed be a nice improvement for RT2500 users that want full speed roaming! :)

EDIT: OK, the Wicd devs informed me that this is already possible with version 1.6+ and told me how on [http://wicd.net/punbb/viewtopic.php?pid=2912](http://wicd.net/punbb/viewtopic.php?pid=2912) . I'll add the method to the How-to.

---

### Post by Stefoufou on 2009-10-23
Does this workaround work un Karmic ?

---

### Post by RavanH on 2009-10-23
> **Stefoufou said:**
> Does this workaround work un Karmic ?

Have not tested that yet but asked elsewhere on another thread. I'd be interested to learn this too... Anyone gone there before?

---

### Post by bruno321 on 2009-11-01
Worked perfectly in Kubuntu 9.10, thank you! The only difference is that the package network-manager-kde has changed to "plasma-manager" or something like that.

---

### Post by petsoukos on 2010-07-18
I've tried this solution but it will not work on my comp :(

It connects faster with the access point but the same slow download speed... 60-70 kb/s

Any ideas ?

---

### Post by Handssolow on 2010-10-10
I found this thread as broadband speeds were becoming no better than dial-up. A web based broadband speed test confirmed the slow speed. For what it's worth I also noticed the occasional spike of faster data transfer. I'm using a Belkin pci wifi card.

Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

Bought this as a Linux friendly wifi card but the  RT2500 chipset hasn't proved to be that great. On my own PC a while back, I switched over to using a wired link to my wifi router. I'm now using it again in a new PC that's closer to the router.

Installing Wicd using Synaptic didn't remove Network Manager as I'd expected but it did cured the slow connection speeds. I'm leaving things as they are. It looks like Network Manager is working but not configured properly, time will tell if I'll have to revisit this problem and remove Network Manager. Or I might buy a replacement pci wifi card. For the moment though the Belkin is working well enough.

---

### Post by SeijiSensei on 2010-10-10
The stock kernel drivers for this chipset have undergone some regressions in more recent kernel releases.  However the current Maverick kernel, 2.6.35-22-generic, has eliminated them all for me.  I'm using a Linksys WUSB54 v.4 USB adapter.  My connection now stays up for days at a time at 54 Mbit.

---

### Post by maniqui on 2011-01-05
Hi RavanH, thanks for the tutorial.

Sadly, it seems that the fix doesn't work properly on my Ubuntu 10.10 installation. I mean, the tutorial worked fine, the instructions were very clear and I got success installing Wicd, setting the connection and the pre-connection script. But the connection quality is still bad: very slow, low quality signal and so, unstable (it disconnects very often). 

This is an internal MSI PCI wireless card with RaLink RT2500, which worked pretty well on Windows, with my current router (DLink 600 with DD-WRT firmware).
I'll do some more testing, and if I can't get a reliable connection, I'll probably upgrade to a newer card.

---

### Post by RavanH on 2011-01-05
> **maniqui said:**
> Hi RavanH, thanks for the tutorial.

Sadly, it seems that the fix doesn't work properly on my Ubuntu 10.10 installation. I mean, the tutorial worked fine, the instructions were very clear and I got success installing Wicd, setting the connection and the pre-connection script. But the connection quality is still bad: very slow, low quality signal and so, unstable (it disconnects very often). 

This is an internal MSI PCI wireless card with RaLink RT2500, which worked pretty well on Windows, with my current router (DLink 600 with DD-WRT firmware).
I'll do some more testing, and if I can't get a reliable connection, I'll probably upgrade to a newer card.

Hi maniqui, it' s been a VERY long time since I wrote this tut. After using Wicd for years, I found after some upgrade of Ubuntu that my RT2500 was working fine again under Network Manager... Until the card died... (Killed? I saw nothing but maybe it was 'The Manager' ;) )

Recently I have ordered a replacement card but I do not know it if will have the same chipset. If so, I'll do some testing with Wicd and see what happens :)

---

### Post by Handssolow on 2011-01-05
I came to the conclusion that my Belkin RT2500 based card had an intermittent fault, though so far it's not gone out in the trash bin. I had to buy two wifi cards before I got one which worked properly with Ubuntu.

The next was a Micronet with RTL8185 chipset but Ubuntu's current driver is more for RTL8180 so the signal strength and quality was poor. 

Finally got an Edimax EW-7128G pci wifi card from Amazon which worked out of the box. Has RT61 chipset if I remember correct.

---

### Post by HappyTimeHarry on 2011-05-28
I would like to reiterate that the ndiswrapper solution on page 2 worked for me with my wusb54g wireless lan card on linux mint 9 (Ubuntu 10.04) (although I didn't read that solution until after i had already tried basically the same thing on my own).  

  As it turns out I had the original windows drivers on cd, (rt2500.inf) so no windows install was necessary and also I just blacklisted the rt2500usb kernel module and restarted (as step 2) as described on page 2, (blacklist rt2500usb) I didn't use "sudo rmmod rt2500pci". I don't know if that makes any difference but it hasn't caused me any problems. 

Hopefully someone who doesn't catch the link to the second solution on the first page (like me) will read and try this before resorting to using newer kernels as I've seen suggested elsewhere, or even worse resorting to a different distro altogether. 

To re-reiterate 
1. Get rt2500usb.inf somehow. (for wusb54g version 4 in my case, you may have to do some hunting for your specific version)
2. in /etc/modprobe.d/blacklist.conf blacklist rt2500usb or rt2500pci if that's what you have.
3. restart
4. Use ndiswrapper to install rt2500usb.inf
5. Configure connection according to your router settings
6. Enjoy (hopefully) 

Sorry if this doesn't fully apply to ubuntu, but my guess is that it does seeing as how I did almost the exact same thing in ubuntu 8.04 to get the wireless working.

---

