---
title: "Wireless at boot!"
date: 2006-02-19
forum: Networking &amp; Wireless
---

### Post by h0mer on 2006-02-19
hi,

I have a broadcom and successfully installed the ndiswrapper drivers. I can connect to the Internet and my local network just fine.

However, I can't get it to work automatically at boot time. When booting, the startup process will hang at 'Configuring network interfaces', and just stay there  for near a minute (making the boot process unbearably long)... I think it's try to get some signal out the network devices. This is a laptop, so the ethernet jack is usually unplugged, and it doesn't seem to find the wireless card. Then it just gives up and resume the boot process.

Once in gnome, the wireless is not working. But all I have to do is enter the Network Configurator, I see 'Wireless Connection: the wlan0 interface is active',  so I just press 'disable', then again 'enable', and voila! the wireless connects successfully.

Similarly, right after entering gnome I can just go to console and try

```
sudo ifdown wlan0
sudo ifup wlan0
``` 

and wireless starts working. How can I get this to start working automatically? How can I configure it to start working from the boot process as to not take so much time? thanks!

---

### Post by Lambert on 2006-02-19
Open up your interfaces file by doing this from terminal

```
sudo gedit /etc/network/interfaces
``` 
If your cable is unplugged then that might be the extended boot time as it's trying to configure that interface. remove the line *auto eth0* from the file.

To start your wireless during boot there should be a line *auto wlan0* 

if that's already there and removing the auto eth0 doesn't help at all, post your file here.

 XXX out any personal information.

---

### Post by crd on 2006-02-19
Have the exact same problem, except mine is much pickier about getting it to come back up once booted.  Not sure which Broadcom you have, but you might consider switching the driver you are using (Win98 or WinXP) if there are two .inf driver files available. 

I ended up installing the latest "Testing" version of ndiswrapper (v. 1.11 rc1) from source and so far it seems to be working **much **better than 1.10.

Others mentioned using the linuxant drivers, but if I don't have to pay 20 bucks, I'd rather not.  Just an option if you're in need.

Good luck.

crd

---

### Post by jakemikey on 2006-02-19
Wow, I was having this same problem.  Commented out the eth0 stuff in the interfaces file and bootup went much faster.

Here's the wireless-relevant stuff I found in the file:

iface wlan0 inet dhcp
wireless-essid XXXX
wireless-key XXXX

I tried adding the 'auto wlan0' as you suggested, but that in addition with the above stuff disabled wlan0, so I just left the stuff above as is.

Another question though:

When I bring my laptop on campus and boot up, things get squirly because wlan0 can't find the essid mentioned (it's my home network, not the campus one).  It then takes several disconnect-reboot cycles to get wlan0 to use anything else as the network.  Is there a way to have a list of several of the most 'common' networks used, with a last resort option to join any available unsecured network (r none if nothing is available)?  I'm assuming this stuff would be added to this 'interfaces' file for configuration on bootup...

Thanks in advance.

---

### Post by Lambert on 2006-02-19
Using multiple AP, I would suggest a wireless manager such as gtkwifi, network manager. Network manager is in the repos, gtkwifi is a third party project found here in the forums.

If those don't work you create virtual interfaces such as this

iface home inet dhcp
xxx
xxx

iface work inet dhcp
xxx
xxx

Leave any auto stanzas out and then you can run this command to bring up the correct interface.

sudo ifconfig wlan0=home up
or
sudo ifocnfig wlan0=work up

and it will bring up the interface based on the virtual interface settings.

There are also some scripts floating around here in the forums that automates this where it will search for known aps and then connect to it. I can't help there but you can search. I believe it made it to the udsf doc.gwos.org but could be wrong, can't check as server appears down recently.

---

### Post by h0mer on 2006-02-20
ok, so I took a look at my /etc/network/interfaces, and effectively, there was a "auto eth0" that didn't seem right. The full doc is something like this (ommiting comments)":

```

auto lo
iface lo inet loopback

mapping hotplug
	script grep
	map eth0

iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless-essid xxx
wireless-key xxx


auto wlan0

auto eth0

```

I'm not sure about the hotplug part, but I think I pretty much get the rest of it. So I commented out #auto eth0, and rebooted. As expected, it got to "Configuring network devices" and ok'ed in a few seconds instead of the near minute. However, it stuck on the next step -"Waiting for interfaces to come up". After almost a minute, it finally ok'ed. However, once in gnome, the situation was pretty much the same: no networking. If I look into Connection Properties, there are two tabs, General and Support. Under Support, I only see Network Device (not certain about the english locale), no Internet Protocol IPv4. 

So it's back to Configure -> Select Wireless -> Disable -> Enable. Works perfectly, network is on. Now, under the Support tab, above the Network Device info there is the Internet Protocol IPv4 with my IP on it.

I take a new look at /etc/network/interfaces, and, right below my commented #auto eth0, there's a brand new line! another uncommented auto eth0 appeared magically at boot!! 

Any new ideas? I don't think it's a problem with the ndiswrapper or windows driver; once I manually enable networking, it's rock solid. 

As a sidenote, I tried wifi-radar, which succeeds at detecting wifi networks, but when trying to connect to any just hangs at 'connecting' so I have to kill it. I'll give gtkwifi a try, but I'm not sure I want to tackle the 'automatically get on different APs as I'm at different locations' issue, until I can get it to connect automatically to my home network as default.

Thanks for the help!

---

### Post by AndyCooll on 2006-02-20
If you look under System-->Administration-->Networking is your wireless connection listed as being configured? Further, is it also listed as being the default gateway device?

:cool:

---

### Post by h0mer on 2006-02-20
[QUOTE=AndyCooll]If you look under System-->Administration-->Networking is your wireless connection listed as being configured? Further, is it also listed as being the default gateway device?

:cool:[/QUOTE]
yes. precisely, Under System->Admin->Networking, is where i check my wireless connection, and it starts by saying 'Connection is active' (again, not sure about the english locale, my ubuntu is in spanish). But since it doesn't work right after boot, here is where i must press the buttons at the right; first "Disable"(disactivate)" then "Enable(activate)" and the network kicks in. It works whatever says it's the default gateway, which is never quite predictable. Sometimes it's blank, sometimes its eth0... I tried changing it to wlan0, but realized it doesn't make much difference, once I disable->reenable the wireless connection, it works whatever says there, and by just setting this to wlan0 it wont.

Any ideas why "auto eth0" is auto-appending itself to the interfaces file at boot?

---

### Post by mr_ed on 2006-02-20
[QUOTE=h0mer]Any ideas why "auto eth0" is auto-appending itself to the interfaces file at boot?[/QUOTE]

It will append "auto eth0" to that file if you go into System->Administration->Networking, and then click OK.  (You see that "Default gateway device: eth0?  If you were to change that to wlan0, then "auto wlan0" would start auto-appending to that file).

If you don't want that to happen, use Cancel instead of OK.

If you use DHCP only, try NetworkManager (in the Ubuntu repositories, it's network-manager), and just don't use that Network Settings app at all.  When I tried it, it was a little bit unstable for me, but it may work for you.
Once you've installed it, type "nm-applet &" and close the window.  Then when you go to log out, save your settings.  It should come back up next time you log in.

(Hm, I just noticed that there's no option to do that in Dapper.  :()

---

### Post by h0mer on 2006-02-20
> If you use DHCP only, try NetworkManager (in the Ubuntu repositories, it's network-manager), and just don't use that Network Settings app at all.

Ok, I installed it and it detected my wifi network just fine. What about the /etc/network/interfaces file? is it unrelated? what should it (not)say for network-manager to function properly?... and ideally not take a whole minute out of my boot time?

> Then when you go to log out, save your settings. 

What do you mean by this exactly? which settings are you referring to? 

thanks for your help!

---

### Post by atomicmoose on 2006-02-22
What I usually do(I am not sure if this is even good) is hit Ctrl-C if it hangs at the network connections section in the boot process. I have yet to have an ill effect from that.

---

### Post by crd on 2006-02-22
[QUOTE=atomicmoose]What I usually do(I am not sure if this is even good) is hit Ctrl-C if it hangs at the network connections section in the boot process. I have yet to have an ill effect from that.[/QUOTE]

you might try changing your DHCP timeout..  I think that might be where you are hanging on boot.  My default was 60 seconds (entirely too long for most people).  Changing it to 4-8 seconds might help out.

crd

---

### Post by Topper_H on 2006-02-23
Solved this issue by adding ndiswrapper at the end of my /etc/modules

Hope it helps

---

### Post by atomicmoose on 2006-03-15
[QUOTE=crd]you might try changing your DHCP timeout..  I think that might be where you are hanging on boot.  My default was 60 seconds (entirely too long for most people).  Changing it to 4-8 seconds might help out.

crd[/QUOTE]Where can I change this setting at?

---

### Post by ash211 on 2006-05-10
[QUOTE=atomicmoose]Where can I change this setting at?[/QUOTE]

```
sudo gedit /etc/dhcp3/dhclient.conf
```

Remove the # from this line: 
#timeout 60;
and change 60 to whatever you want the timeout to be.

---

### Post by panurge77 on 2006-06-15
I was having the samer problem and the fix was changing the /etc/network/interfaces file putting the key before the essid. My card won't accept the essid without the key set up. So I made this:
```
iface wlan0 inet dhcp
wireless-key open xxx
wireless-essid xxx

```
I used the open option to tell it it's open, I think restricted is the default...

---

### Post by AudioMove on 2006-07-07
i commented out auto eth0 and eth1 but it still hangs and wont load my wireless configuration. Ctrl-C doesnt even work anymore, can some help me get back into my system , thx.

---

### Post by iguanaphobic on 2006-07-10
I have the exact same problem. ACX 111 chipset, Netgear WG311 v2. No network at the default desktop, but if I hit the terminal with:

```
sudo ifdown wlan0
```
followed by
```
sudo ifup wlan0
```

I then have a bulletproof connection.

Strangely, the network applet in the panel tells me that I have no network connection.

All I want to know is how to make it work at boot.

---

### Post by jrogers on 2006-07-12
I have a ThinkPad that auto config's great from the Live cd... but my HD install won't go online.... Any suggestions?
-J

---

### Post by fbonjour on 2006-07-13
Hi,

I may have the same problem, on a Dell wireless card:

0000:02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)

The symptom is similar: when I boot, the network doesn't come up, but as soon as I have a chance, I can login (in text mode), type

/etc/init.d/networking restart

and it works fine (so /etc/networking/interfaces should be OK).

One thing that puzzles me is this: how does the kernel name the interface? In dmesg, I get this:

[17179596.640000] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
[17179596.992000] ndiswrapper: driver bcmwl5 (Broadcom,05/26/2005, 3.120.27.0) loaded
[17179596.992000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[17179596.996000] ndiswrapper: using irq 7
[17179598.324000] wlan0: vendor: ''
[17179598.324000] wlan0: ndiswrapper ethernet device 00:11:f5:16:71:05 using driver bcmwl5, 14E4:4324.5.conf
[17179598.324000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

so it looks like the kernel calls the interface "wlan0". Yet, when I log in, before I even do the /etc/init.d/networking restart, I can see from iwconfig that the wireless device is eth1:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"fbwifi"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:BF:26:03:4C
          Bit Rate:48 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management min timeout:0us  mode:All packets received
          Link Quality:100/100  Signal level:-59 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

(I ran this command just now, online, which is why the card is configured.) Here is my modprobe.d file ndiswrapper:

alias wlan0 eth1
alias eth1  ndiswrapper if_name=eth%d

So, could this be a device naming problem in the kernel?

Any help woul dbe appreciated!

Filipe

---

### Post by game_plan on 2008-04-14
I can't find anywhere in the system that shows any network device coming up.

my /etc/network/interfaces file looks like this:
```

auto lo
iface lo inet loopback

```

Yet Network manager shows the LAN active on boot and I'm able to get the wireless to start by running
```

/wlan0up

```

I've tried adding your suggested code to interfaces but it does nothing. I've had the same issue with 7.10 and now 8.04. PLEASE help.

---

### Post by The Cog on 2008-04-14
I don't know how many people are likeky to see this post - you have tail-ended a 21-month old thread. I suggest you start a new thread of your own.

I would expect to see some stanzas about waln0 in /etc/network/interfaces but I'm not too hot on wireless so I can't be sure of the details. Maybe these two lines would work:
```
auto wlan0
iface wlan0 inet dhcp
```

---

