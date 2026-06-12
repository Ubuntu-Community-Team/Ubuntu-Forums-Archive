---
title: "Setup, Config, Troubleshoot MythTV"
date: 2013-07-06
forum: Multimedia Software
---

### Post by Mark_in_Hollywood on 2013-07-06
On install of: MythTV, HDHR Config Gui, and SiliconDust HDHR Dual tuner, I keep going around in circles. 

Currently the Tuner is connected to an ethernet switch. Please bear with me here: as the switch seems to have no input or output ports, but has, previously to this week, worked by at least showing channels found  in the hdhr_gui.

I have uninstalled and re-installed mythtv. Twice so far.

I have these components or devices: a computer with an ethernet port, a monitor for the computer. A SiliconDust HD Home run tuner (dual), and a separate TV with an ethernet port.

What I am trying to do is setup Myth so I can watch TV from either (or both) the computer's monitor or the TV (after this, I'll call it the 50" to try to prevent confusion as to what signal is where). And this watching is to be from a signal sent by the silicondust ethernet port to the computer and/or the 50".

After a week or so of trying to figure out how to edit my network settings, I am here, asking for help.

The business about the Apache2 server is more than confusing to me. Try as I can, the help isn't on the interet. At least as far as my skills for searching for help are concerned.

The terminal opens with a series of screens about whether the apache2 will be running on more than "one machine". Does this mean that the 50" is a machine? That seems to indicate a second computer could be involved (and I don't have one).

Then I cannot seem to understand where all the IP addresses are to go. I know I need more than one and that the eth0 Method: Link-local only is for users who do not have more than one monitor/TV. So, I cannot use 127.0.0.1.

And what I have found in my readings, is that my firewall is blocking some? of (all of?) the eth0 IP address and not connecting. But I have no knowledge of setting up, installing, configuring or using a firewall on this computer, which had a fresh install of 12.04 in mid-June, last.

I know I have two network conections, one is the WiFi. Another is (or will be) the ethernet. And as a reminder, the silicondust tuner's output is an ethernet cable. It goes into my (5 port) switch. Also plugged into this switch are an ethernet cable plugged into the computer and another ethernet cable ready to plug into the TV. Although I bought a switch and ethernet cables, I have no idea of what I'm doing.

If there were a "How To" or Tutorial that were NOT out of date, that would be a help, if you can point me to one that deals with making IP and opening a firewall.

mark@Lexington:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 40:61:86:06:56:14  
          inet6 addr: fe80::4261:86ff:fe06:5614/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2477 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:55746 (55.7 KB)  TX bytes:586578 (586.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:14156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1892304 (1.8 MB)  TX bytes:1892304 (1.8 MB)

wlan0     Link encap:Ethernet  HWaddr 90:f6:52:0c:2d:a4  
          inet addr:192.168.1.73  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2602:306:bdbf:4420:92f6:52ff:fe0c:2da4/64 Scope:Global
          inet6 addr: 2602:306:bdbf:4420:c09d:c73e:9fcb:e137/64 Scope:Global
          inet6 addr: fe80::92f6:52ff:fe0c:2da4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:144398 errors:0 dropped:0 overruns:0 frame:0
          TX packets:93781 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:115413068 (115.4 MB)  TX bytes:18310968 (18.3 MB)

My reading about this makes me believe I need to not use the Link-local. I must use some other Method. Some posts talk about DHCP and others talk about Static IP. Either way I'm completely lost. It cannot be both or all Methods. Is one better than another? Where is the information on IP addresses for this computer that are available? Do they have to be related, e.g., 192.168.1.0 then 192.168.1.1 and 1.2 and so on?

Please pardon these noobie questions. After a week of trying to fix all this, I'm at a complete standstill.

---

### Post by Bucky Ball on 2013-07-06
I have edited the title of your post. A heads up, from the ***Code of Conduct***, regarding why:

> Profanity: We have users of all age groups and of all tolerance levels where profanity is concerned. A language filter is in place to catch most major forms of profanity that may accidentally be used. _Do not attempt to circumvent the language filter by using variations or slight misspellings of profanities._

Thanks. ;)

---

### Post by Bucky Ball on 2013-07-11
Just wondering how you are getting on with all this? Have you made any progress on it?

---

### Post by steeldriver on 2013-07-11
A few comments


[LIST=1]
[*]based on your computer's wlan0 192.168.1.x IP address you are on a LAN with a regular home router; if so, then you almost certainly don't want to be trying to use link-local addressing anywhere, your HDHomeRun box should be able to get its IP via DHCP even through the switch - ideally that should be an IP that's reserved at the router based on the device's MAC (I have exactly this configuration at home)
[*]I suggest disabling any firewall on the computer at least until you get the basic connectivity figured out - arguably a firewall on the computer doesn't even buy you anything if you are already behind a NAT router, however it will be fairly straightforward to configure it *after* you get things up and running (either allowing everything from the HDHOMERUN's reserved IP in ufw, or based on the MAC in iptables)
[*]AFAIK the LAN IP that the apache2 server listens on only matters if you want to use the *mythweb interface* from other computers - similarly you need to set a non-loopback IP for the SQL server (via the mythtv backend setup) ONLY if you want to run *mythtv* frontends on other devices - your 50" TV is almost certainly not a 'machine' or 'frontend' in either of these senses, I don't know anything about IPTV but presumably it will be running some kind of proprietary streaming client (if anything - just because a device has an ethernet port doesn't necessarily mean that it will be able to display streamed media)
[*][somewhat related to 3] the easiest way to view OTA TV on both the 50" TV and your computers is to split the RF signal upstream of the HDHR and use the TV's own ATSC tuner if it has one - leaving both HDHR tuners for viewing / recording via ethernet on the computer(s).
[/LIST]

Step 1 would be : disable any firewall on the computer; connect everything to your LAN (with the switch wherever you need it); then fire up the HDHomeRun Config GUI and/or the router's 'attached devices' page and see if everything can be 'seen' and what IPs get assigned to what

---

### Post by Mark_in_Hollywood on 2013-07-14
Ahhh.... boy I'm feeling pretty dumb, now. Per your advice: [COLOR="#FF0000"]Step 1 would be : disable any firewall on the computer; connect everything to your LAN (with the switch wherever you need it); then fire up the HDHomeRun Config GUI and/or the router's 'attached devices' page and see if everything can be 'seen' and what IPs get assigned to what[/COLOR]

1 - I did not know my router had an "attached devices" page. And, AFAIK, there is no firewall at all. I never installed one and this computer had a clean install of Xubuntu about 50 days ago. I have not knowingly installed a firewall. 

2 - How do I know if I have a server working or otherwise? I have no knowingly installed a server and (I repeat myself), ... clean ... 50 days ago. I have installed both the MythTV back and front ends. 

3 - I'm working on finding my Network Attached Devices "page".

---

### Post by Bucky Ball on 2013-07-15
Have you got static IPs set for all devices? This will make things easier to track. If not, whenever you reboot a device it will have a different IP served from the router's DHCP server. This can make things impossible to get working. (Know it could be a dumb question but just checking as this could be a major stumbling block to setting this up.)

Is MythTV not a media server? If so, the server stuff would have been installed with the backend. I think you are going to need a media server somewhere along the way if you are intending feeding media to serveral devices. Never used it so could be confusing with Mythbuntu, which I'm pretty sure is the idea. (Only thing like it I've used is Xbmc on the Raspberry Pi and still battling with that. ;))

---

### Post by dannyboy79 on 2013-07-15
what guide are you using to setup MythTV? Am I to understand you're running Xubuntu and then you installed mythtv? It may be easiest to actually install mythbuntu-control-center. That's what I did with my Xubuntu 12.04 setup. Since you only have 1 computer, you'll need that to be your mythtv-backend AND mythtv-frontend since you want to watch tv on the computer.

You say your tv has an ethernet port, i am betting that's because it's a smart tv and has netflix and other smart tv functions BUT does NOT have any way to "access" your mythtv backend or your hd-homerun. Unless you connect your computer to the 50" TV or use some other thin client to act as a mythtv frontend.

---

### Post by Mark_in_Hollywood on 2013-07-15
As there are 2 responses, I'm quoting the (short) posts and responding to both here.

Bucky Ball

Is MythTV not a media server? It may be, but that is the first time I seen it described as such. Usually my netsearching leads to: Apache2, LAMP, and some other the name of which escapes me as I type this response.

Following a number of Tutorials, How To's and such, I'm of the understanding that if there is to be more than one device that MythTV drives (sends a tv signal to), then the backend IP address CANNOT be: 127.0.0.1 - towards that end, I tried to find an appropriate IP address and set a static address. I saw some posts (askubuntu.com) about removing certain files to prevent the OS from re-assigning IP address and re-boot and decided against doing that until I was more certain of what I'm doing.

If so, the server stuff would have been installed with the backend. I have the following installed via Ub. Soft Ctr.: MythTv's backend and frontend. And as I have a silicondust tuner, I have the HD_homerun_config_gui. Currently, the devices are physically connected as follows:

between the computer and the tuner there are ethernet cables. Both of those cables run into an ethernet switch. One more cable leave the switch and goes to a TV.

I tried a number of "Methods" of connecting the eht0 to the computer/tv. I tried: DHCP, DHCP (Automatic), I tried Link-Local (only), I tried Manual. I did not try Disabled.

 I think you are going to need a media server somewhere along the way if you are intending feeding media to serveral devices. Never used it so could be confusing with Mythbuntu, which I'm pretty sure is the idea. (Only thing like it I've used is Xbmc on the Raspberry Pi and still battling with that.


dannyboy79 

what guide are you using to setup MythTV?

[https://docs.google.com/document/d/19knOlqz8cV5_8VQ1tCvEd8tjEk6U50KsSOJCROR60o4/edit](https://docs.google.com/document/d/19knOlqz8cV5_8VQ1tCvEd8tjEk6U50KsSOJCROR60o4/edit)
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php) 
[http://www.mythtv.org/wiki/Silicondust_HDHomeRun](http://www.mythtv.org/wiki/Silicondust_HDHomeRun)
[http://www.garron.me/en/linux/add-secondary-ip-linux.html](http://www.garron.me/en/linux/add-secondary-ip-linux.html)

The two below, because I thought I need a "server".

[https://www.digitalocean.com/community/articles/how-to-set-up-apache-virtual-hosts-on-ubuntu-12-04-lts](https://www.digitalocean.com/community/articles/how-to-set-up-apache-virtual-hosts-on-ubuntu-12-04-lts)
[http://linuxpoison.blogspot.com/2012/01/how-to-install-configure-postgresql.html](http://linuxpoison.blogspot.com/2012/01/how-to-install-configure-postgresql.html)

So, yes, there is both an Apache2 and a funky Postgresql on this 'puter.


Am I to understand you're running Xubuntu and then you installed mythtv? Yes. Clean install of Xubuntu about 50 days ago. MythTv work started about 40 days ago.

 It may be easiest to actually install mythbuntu-control-center. 

Sir: Surely you jest?

mark@Lexington:~$ sudo aptitude install mythbuntu-control-center
[sudo] password for mark: 
Couldn't find any package whose name or description matched "mythbuntu-control-center"


That's what I did with my Xubuntu 12.04 setup. Since you only have 1 computer, you'll need that to be your mythtv-backend AND mythtv-frontend since you want to watch tv on the computer. -- Not exactly, I want to watch TV on both my computer monitor and on a "Smart?" TV - well it has an ethernet port.

You say your tv has an ethernet port, i am betting that's because it's a smart tv and has netflix and other smart tv functions BUT does NOT have any way to "access" your mythtv backend or your hd-homerun. Unless you connect your computer to the 50" TV or use some other thin client to act as a mythtv frontend. 

I will do the above paragraph, as soon as I can understand what configuring the backend needs to make two devices on the "network?" - This is the whole of my confusion: does MythTV act as a "server" in the sense it outputs the tv programming to the computer monitor and the TV set? Or do I need MythTV to send it's signal to the (for example) Apache2 server then the Apache2 will send the signal to the computer's monitor and/or the TV set?

---

### Post by steeldriver on 2013-07-15
Mark here are some terminal commands you can run to see exactly what services are running on your mythtv box:

```
service --status-all 2>&1 | grep \+
```

```
sudo netstat -nlptu4
```

You can also open a browser on the mythtv machine and just type 'localhost' in the URL address bar - see if mythweb pops up.

---

### Post by Mark_in_Hollywood on 2013-07-16
Thanks for that info. The terminal output is at [pastebin]("http://pastebin.com/dE4EJ5Pj").

My problem at the moment is that there is no wired connection. The devices are:

computer with ethernet port
ethernet switch 5 port 
silicondust tv tuner with ethernet port 
TV (so-called Smart) with ethernet port

No eth0 shows in "Active Network Connections" of Connection Information of the panel's Network Manager applet.

If I plug the tuner into the computer, there is an eth0 connection with an IP address. But this isn't the configuration I'm looking for. 

At the moment, the computer's networking "sub-system" does not see the above mentioned devices. I'm guessing that I need a network and I'm guessing that all networks have or use a "server", but again, I'm guessing.

Being honest with all responding here: I am not well enough informed to even understand how to ask rudimentary questions.

mark@Lexington:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 40:61:86:06:56:14  
          inet6 addr: fe80::4261:86ff:fe06:5614/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:98 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1015 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33516 (33.5 KB)  TX bytes:522600 (522.6 KB)

---

