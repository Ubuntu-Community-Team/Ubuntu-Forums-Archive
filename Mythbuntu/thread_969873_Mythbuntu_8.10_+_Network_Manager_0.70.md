---
title: "Mythbuntu 8.10 + Network Manager 0.70"
date: 2008-11-03
forum: Mythbuntu
---

### Post by uncle hammy on 2008-11-03
I can't seem to figure out the new Network Manager 0.7 in Mythbuntu 8.10.  I just did a fresh install on one of my frontends, and it went reasonably well.  However, the new network manager doesn't seem to retain settings.  

First, I opened up my connections, selected "eth0", went to IPv4, changed it from DHCP to "manual" and entered all the relevant information.  After clicking OK on the edit screen and CLOSE on the network manager, I restarted and all my changes were gone and the connection was back to DHCP.

Next, I added a new connection, set it up as manual, and restarted.  This new connection did stick around, however I now had 2 connections, it defaulted to connecting to the DHCP.  I was able to switch between the two with no trouble.  I tried deleting the DHCP connection, however after reboot, it was back.

Finally, I tried unchecking "Connect Automatically" in the DHCP connection and checking it in my new manual connection, however after reboot, everything was back again.

So, it seems I am unable to make any changes to the installation created DHCP connection that will persist.  This isn't a huge deal for this frontend, however I would like to resolve the problem before moving on to upgrading my backend.

Any suggestions?

---

### Post by uncle hammy on 2008-11-03
I take that back, I have found a significant issue with not being able to set my frontend up a static ip.  If the machine hasn't managed to obtain it's IP address before mythfrontend launches, then I have to go through the setup process.  This has actually happened 3 times now tonight alone.

---

### Post by uncle hammy on 2008-11-05
Nobody has any thoughts on how to get a static IP set with the new network manager?

---

### Post by Monsieur Gonzalez on 2008-11-05
Well, I guess you can always do it the old way...

Edit your /etc/network/interfaces (I use nano, so I'd do sudo nano /etc/network/interfaces). 
My file looks like this: 

auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.196
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0


Obviously, you should customize it to fit your network setup.

---

### Post by uncle hammy on 2008-11-05
I tried that, and when I rebooted, I had no connectivity at all.  

I have managed to find a few posts and bugs with NM 0.70, and it's looking more and more like I am not alone, and perhaps NM 0.70 isn't really ready for release (I would love to be corrected on that observation).

From what I have found so far, it appears the only real "solution" is to remove NM, and go old school with /etc/network/interfaces and /etc/resolv.conf.

---

### Post by mjezell on 2008-11-05
Had a similar problem with a clean 8.10 alternate amd64 install where i could not get connectivity to the internet but was fine for my local network. To get the static IP to work properly I had to remove the network-manager and network-manager-grnome packages and edit the /etc/resolv.conf file to include the nameservers i use. After that everything is working fine. Hope this helps.

---

### Post by lmclaren on 2008-11-06
I second mjezell's suggestion, I had the same problem and the fix was to remove the network manager and go manual. I found a few mentions on the net regarding the network manager and slow to bring up the network.

regards

Lee McLaren

---

### Post by fatmonk on 2008-11-06
A bit of lateral thiunking for the static IP...

I've set up the router than runs the DHCP on my network to always allocate the same IP address to my MythBox.

The effect is that I have a static IP that I can connect to from remote frontends and for MythWeb.

Obviously this would depend on where your dynamic IP address is being allocated from and whether it has the option of fixing a devices IP, but it's an alternative way of achieving approximately the same thing.

-FM

---

### Post by gemini91 on 2008-11-06
I got this working, at least through 3 boots. I put the info into
/etc/network/interfaces and then the required info into
/etc/resolv.conf.

Re-booted and the info in resolv.conf was gone. Replaced it and
re-booted again and that time it stayed in, and the machine connected
with the static address that I wanted.

So far I have re-booted three times and it continues to work.

---

### Post by uncle hammy on 2008-11-06
Yep, that's the route I ended up going.  Removed Network Manager, manually edited /etc/network/interfaces and /etc/resolv.conf.  Had to redo resolv.conf after the first reboot, and now I'm good to go.  Shame Network Manager isn't working the new version seems like it has potential, though I notice there was no where to add hosts.

My router doesn't have the option of doing DHCP reservations, though I may look at setting up my Myth backend as a DHCP server at some point.  It's on all the time anyways.

---

### Post by maks_zbogar on 2008-11-17
I have Ubuntu 64bit on a 6 computer lan and I too need static IP. Is this realy the only way? I cant believe something so important as network manager, doesn't work in Ubuntu. :(

---

### Post by uncle hammy on 2008-11-17
The only way I was able to get a truly static IP was to uninstall the network manager, and then manually edit hosts and resolv.conf

I actually ended up installing DHCP on my backend (which has since been moved to an Endian firewall box), and set up reserved IPs for my frontends in the DHCP configuration.

---

### Post by xeddog on 2008-11-23
I have used the Netowrk Manager to assign a static ip address to my machine.  Here is what works for me:

Right click on the icon in the upper panel and select "Edit Connections"

Click "+ADD" to create a new connection.  In the IPv4 settings, select "manual" the Method and enter all of the information that you need to for ip address, netmask, gw, dsn servers, etc.  
 
The one thing that MUST be specified is the name of the connection MUST be "default".  No other name has worked for me including "Default", so make sure the name is all lower case "default". 

I have not filled in the mac address field, but I only have one ethernet interface.  You may need the mac address info if you have more than one ethernet interface.

Once you have all of the settings entered, click OK to save them.  That should bring you back to the point where you have the connections listed.  Delete every other profile.  This would include the one that (on my machine) says auto eth0.  That should leave you with only the "default" that you just created.
That should do it.  It has worked for me several times now so hopefully it will work for you too.

xeddog

---

### Post by xeddog on 2008-11-23
A couple of things have come to mind since I posted my solution.  One, when editing "default", make certain that the "Connect Automatically" and "System setting" boxes are checked.  Two, at some point you should get a root password prompt.  I don't remember if it is when saving "default", deleting "Auto Eth0" or both, but I seem to remember it was when saving default.  If you do not get a root password prompt, Auto Eth0 will just keep coming back and I don't know how to stop that one.  

And a note.  I posted my method when I had just started a Mythbuntu 8.10 install.  It installs the Xfce desktop and when I tried this procedure after the install finished, it never prompted me for root password and so does not work.  That was the first time the process failed for me after installing Ubuntu 8.10 (both some betas and LTS), a couple of Xubuntu 8.10 betas, and a couple of Kubuntu 8.10 betas.  Wouldn't you know it.  CRAP!!

xeddog

---

### Post by xeddog on 2008-11-24
An update.  I finally got the static ip address on my mythbuntu Intrepid system.  I had to edit connections, delete auto eth0 again, make sure that "Connect Automatically" and "System setting" were checked.  Then I did two things and I don't know which, if not both, did the trick, I closed the edit connections panel.  Re-opened it and edited default again.  I then added the MAC address (copy and pasted from a "sudo ifconfig -a" command), and changed the name to "default " (with a trailing space).  I assume the key thing is to copy the mac address into the "default" connection.

Hope this helps

xeddog

---

### Post by Milan Knizek on 2008-11-25
I have read in bugs.launchpad that the trick to force NM to retain the settings as "system default" is some funny repeating of the same steps (like entering some information and possibly deleting it if it is actually not needed, activating/deactivating/reactivating the "system default" tick, etc.) until NM behaves correctly.

It seems NM is not properly tested yet, but once it works, it simply works (in my case I use WPA2 WLAN connection with fixed IP address).

---

### Post by freddyg on 2009-01-14
hey guys, thanks for pointing me in the right direction, just to save anyone else a step, the proper format for /etc/resolv.conf is a 1 or 2 liner with:
nameserver xxx.xxx.xxx.xxx

where xxx.xxx.xxx.xxx is the ip address of your name server, enter a nameserver line for each name server you have.

---

### Post by neutron68 on 2009-03-01
> **mjezell said:**
> Had a similar problem with a clean 8.10 alternate amd64 install where i could not get connectivity to the internet but was fine for my local network. To get the static IP to work properly I had to remove the network-manager and network-manager-grnome packages and edit the /etc/resolv.conf file to include the nameservers i use. After that everything is working fine. Hope this helps.
I had to do the same exact thing because I could not get the Network Manager to work, either.  In my case, the Network Manager icon turned into a red triangle icon just after I edited the /etc/network/interfaces file.  I have just left the Network Manager in this disabled mode.

Eric

---

### Post by Red Bow Tie on 2009-05-08
I have the same problem. The frontend starts prior to the backend receiving an ip address. The result is the frontend cannot connect to the backend on startup. Once the backend gets its address then by pressing enter twice to get out of the error, the frontend is then able to connect to the backend.

I have setup up my router with a static ip address assigned to the machine.

I deleted network manager.

I have tried the suggestions about manually editing the /etc/network/interface file and have put the following in it. I kept the information about the loopback address. i.e. 127.0.0.1

iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0
gateway 192.168.0.1

auto eth0

then I entered /etc/resolve.conf

and entered

nameserver xxx.xxx.xxx.xxx
namserver  xxx.xxx.xxx.xxx
 
The reason resolve.conf loses the nameserver entry is because of the top commented line. This states that the entries were put there by network manager. If you delete network manager you remove the entries. So I manually put them back in.

All to no avail. I have no connection whatsoever if I do this.

There must be some way to delay the frontend until the backend gets an address.

I have tried manipulating the rc2.d to rc5.d files and put the backend at s99 so it is behind network manager.Still no good. Again the frontend starts too soon and can't connect to the backend at startup.

Can anybody help? How I can automatically login in Mythbuntu and not receive an error message from the frontend starting before the backend gets it's ip address?:(

---

