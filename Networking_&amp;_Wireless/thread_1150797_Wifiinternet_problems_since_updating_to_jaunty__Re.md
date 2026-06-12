---
title: "Wifi/internet problems since updating to jaunty?  Read this!"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by AnthraxMouthwash on 2009-05-06
Here's the solution.

It worked fine for me.

1A.  Get a web connection (another machine, another OS, whatever) if no wifi means no web for you (like me).

1B.  Go here -- [http://packages.ubuntu.com/jaunty/all/wicd/download](http://packages.ubuntu.com/jaunty/all/wicd/download)

1C.  Pick a mirror from the page in #2 and download wicd.  Save the DEB somewhere you can get to it from Ubuntu.  If you are on a different machine, put it on a memory stick or something.

1D.  Boot Ubuntu Jaunty.

2.  Open your package manager (ie Synaptic).  Mark network-manager and network-manager-gnome for complete removal.

To do this, click in the big pane on the right and start typing "network".  Once you see the packages network-manager and network-manager-gnome (already installed), right click each and select "mark for complete removal".  Then click apply and let it do its stuff.

3A.  If you did all the steps in #1, get your DEB file of wicd.  Find it and double-click it.  Install it.

3B.  If you have internet working okay in Ubuntu Jaunty, stay in Synaptic and install wicd from there (it's in the universe).

4.  You should now have "Wicd Network Manager" somewhere on your programs menu.  If not, you may have to edit the menu to find it and put it in a submenu that is visible.  (I had to).

5A.  Go into wicd.  Find your wireless network on the list.  It should have a green bar next to it.  The rest is easy.  Click the little down-arrow next to the network name to display more info on the network.  Click advanced settings and enter your encryption info (key etc).  Make sure you have this information.

5B.  If your network says "<hidden>", you will need to know your ESSID.  Click the down-arrow next to the big "Network" button.  Click hidden network.  Enter your ESSID.  Do this AGAIN (for some reason).  If your network still says "<hidden>", don't worry.

6.  Restart Ubuntu.

7A.  Go into wicd again.  If you had to enter your ESSID manually, you might see two networks here: one named with your ESSID, the other "<hidden>".  If you do see TWO WIFI NETWORKS: disconnect from the hidden network (you'll notice it has the same IP as the named one).  Untick the automatically connect tickbox.  Make sure the named network (with your ESSID) has its auto connect box ticked.  Also, check the advanced settings.  They should still have your encryption info.

7B.  If you had two wifi nets and did #7A, restart Ubuntu again.

8.  Open wicd.  You should see one network, named with your ESSID.  It should be connected and working.

There you go.

---

### Post by AnthraxMouthwash on 2009-05-06
May I suggest making this sticky?

I spent ages trying to get internet / wifi working in Jaunty with no avail until I installed wicd.

Lots of people keep posting with simmilar issues, so I posted this as a semi-definitive solution.  Or at least, I had a lot of issues and it solved them all, so...

---

### Post by grappler on 2009-05-08
While I find wicd great and I've been using it for a while, I now need to use vpn connections which, I believe, wicd does not support. I am not sure if it supports multiple connections either. 

It seems that for my 64 bit jaunty install neither knetworkmanager (which when last I looked in jaunty was totally broken - couldn't even enter the parameters of a wireless connection) nor gnome network applet are able to see my wireless device - at least with the latest update over the last couple of days.  The wireless device is certainly there and I've written a shell script to configure each of my most frequent connections using iwconfig, ifconfig, route,  but it is a pain to do this for all of the casual wireless connections I make. 

I thought I would list what I would like from a network manager, since I think it will be similar to many other users.

1. My regular wireless and wired connections should just be found and connected. When I'm at home and open up my laptop it should just see the connection and connect. Similarly for my office. 

2. It should handle vpn accounts with just a one-off configuration. 
I should not need to reconfigure every time I connect.

3. It should enable multiple connections to different wireless/wired networks at the same time. At my office, for instance, my printer is on a wireless network, but my internet connection is wired. 

The gnome-network-manager was doing all of these, but at the moment it just isn't working for me - 64bit jaunty kernel 2.6.28-12-server on a Lenovo Thinkpad T61p with 4965 wireless card. As I've already said, it doesn't seem to know that there is a wireless card in the machine. 

Here's a great site for command line wireless connections:

[http://wirelessdefence.org/Contents/LinuxWirelessCommands.htm](http://wirelessdefence.org/Contents/LinuxWirelessCommands.htm)

---

### Post by papangul on 2009-05-08
I think it would be better if the following instruction is added in your manual(from [http://wicd.sourceforge.net/download.php):](http://wicd.sourceforge.net/download.php):)

Make sure that the only entry in your /etc/network/interfaces file is:
 
auto lo
iface lo inet loopback

---

### Post by Ansible on 2009-05-09
Thumbs up on these directions.  Removed network-manager, installed wicd, now it works.  I had to reboot before my network was detected though, somehow it had gotten scrambled and was only seeing a few of the networks available in my building.  

Something is definitely wrong with the network-manager in 9.04, in 8.10 it was working fine.

---

### Post by banduan on 2009-05-09
I was really hoping this would work, but alas, my Broadcom 4312 still can't detect my wireless network.

btw, I used a wired connection and just used synaptics to download wicd. It automatically removes Gnome network manager.

---

### Post by superprash2003 on 2009-05-09
nice stuff..good job.

---

### Post by iClouseau88 on 2009-05-09
Hi,

I am in big trouble and I need help fast.  Followed your instructions. After downloading wicd deb package and removing network manager, I cannot find wicd anywhere.  Now I have no internet and I cannot do any update or using Synaptic becaause the source cannot be resolved.

Please help me, thanks alot!

---

### Post by iClouseau88 on 2009-05-09
bump!

---

### Post by Ansible on 2009-05-09
> **iClouseau88 said:**
> bump!

You installed the deb?  Did you get an error message?  When I installed it Wicd appeared under the Applications->Internet menu.

---

### Post by iClouseau88 on 2009-05-09
No, I did not get any error message.  When I clicked on the package a menu appears that has an automatic installer (gdebi?) so I hit Enter.  This happens so fast I did not remember the exact names of the menu items.

I urgently need help finding the package because right now I cannot use the Internet from my Ubuntu machine.

---

### Post by iClouseau88 on 2009-05-09
PS: I got error message: "Could not resolve archive.ubuntu.com" when I try Add/Remove to look for wicd.

---

### Post by iClouseau88 on 2009-05-09
bump

---

### Post by iClouseau88 on 2009-05-10
Update:

I am getting somewhere: Downloaded and saved the pkg to USB key then copied it to Home folder in Ubuntu machine.  Installed wicd.  Found it very difficult to set up.  I cannot see a window to enter my passphrase unless I tick on "autoconnect..".  Even when I finally get the screen to show connected (to wired network...IP 192.168.x.y" I still get page load error.  This is way more difficult than it should be.  I may have to consider re-installing network manager and wait for Canonical to fix NM.

So, I am not THERE yet!  Help!

---

### Post by iClouseau88 on 2009-05-10
Finally get the net via wired connection.  Still find wicd very clunky to set up.  May consider returning to NM.

---

### Post by Mastermind1980 on 2009-05-17
Similar problem here: [http://ubuntuforums.org/showthread.php?p=7291722](http://ubuntuforums.org/showthread.php?p=7291722) Please help!

---

### Post by DaleZ on 2009-05-18
I've installed wicd and rebooted twice.
How do I enable encryption? It is wpa2.  I use ndiswrapper to load the driver.
Whenever I click on my network I get the msg "encryption needed".

---

### Post by rbond on 2009-06-28
Posting in case this helps someone. I have been following a few wifi related threads because I had problems with wifi after upgrading to Jaunty.

In the past I had manually setup my wifi WPA settings in the /etc/network/interfaces file. Then I started using the Gnome Network Manager. My manual settings did not cause a problem until I upgraded to Jaunty. Just for the heck of it I removed the manual settings from my file and it fixed the problems that I had. 

I know that for some people this is a kernel issue, but for me it turned out to be a problem with Gnome Network Manager not liking my config settings.

If you are having problems and you had previously manually configured settings, back up your current copy and try to revert to only auto settings such as this....

```
auto lo
iface lo inet loopback


iface eth1 inet dhcp

auto eth1

iface wlan1 inet dhcp

auto wlan1

```Hope this helps someone.

Forgot to note this: For the newbies - the eth1 and wlan1 values may be different on your machine. Use the network interface names for your machine.

---

