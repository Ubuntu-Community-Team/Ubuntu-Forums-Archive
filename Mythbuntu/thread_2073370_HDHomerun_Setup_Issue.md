---
title: "HDHomerun Setup Issue"
date: 2012-10-19
forum: Mythbuntu
---

### Post by JWB47 on 2012-10-19
I just received a HDHomerun tuner (model HDHR3-US) that I cannot get to be recognized.

The message I get when I run hdhomerun_config is "no devices found". Nothing shows up when I use the gui even after repeated rescans.

The HDHR is on my network, it does get a valid IP address, I can ping it, see it with nmap and point my browser to it and get the webpage. The HDHR is at firmware 20120405 which I believe is current.

Both the HDHR and my mythbackend server are plugged into 2 of the 4 ports on my router, an ASUS RT-N66U.

I just did an upgrade on the server to bring it to an up to date status. I am running 12.04.1 LTS with the Kernel 3.2.0-32 x86-64. MythTV is also current at 0.25.2+fixes.20121004. The backend is operational and fully functional with an HVR-2250 dual tuner installed.

The backend has ufw enabled with anyone on 192.168.1.0 having access to any port. I get the same "no devices found" message whether it is enabled or not.

I also noticed in dmesg that dvbhdhomerun_utils terminated with a status of 127.

Anyone have an idea as to how to get this HDHR recognized?

Thanks

John

---

### Post by nickrout on 2012-10-19
why are you running dvbhdhomerun? it is unnecessary with mythtv and may be confusing things.

what is the output of ```
hdhomerun_config discover
```

---

### Post by JWB47 on 2012-10-19
> **nickrout said:**
> why are you running dvbhdhomerun? it is unnecessary with mythtv and may be confusing things.

what is the output of ```
hdhomerun_config discover
```
As a part of my trying to get it working last night and address the "no devices found" message fom "hdhomerun_config discover", I found instructions (not for MythTV) that implied dvbhdhomerun needed installing from a PPA (ref [http://sourceforge.net/apps/trac/dvbhdhomerun/wiki/UbuntuPackages](http://sourceforge.net/apps/trac/dvbhdhomerun/wiki/UbuntuPackages)). 

I have now removed it, the associated utils and rebooted the backend.

Rerunning the command as you requested, I get the same result.

 ```
jwb@mmbe:~$ hdhomerun_config discover
no devices found

```Running nmap, you can see that the HDHR is present.

```
Starting Nmap 5.21 ( http://nmap.org ) at 2012-10-19 16:25 EDT
Nmap scan report for HDHR-10371EB2 (192.168.1.117)
Host is up (0.0049s latency).
Not shown: 999 closed ports
PORT   STATE SERVICE
80/tcp open  http

```

John

---

### Post by nickrout on 2012-10-20
I suspect firewall issues.

---

### Post by JWB47 on 2012-10-20
> **nickrout said:**
> I suspect firewall issues.

I have been thinking that was the case, but now to find out where the trouble is.

To test things out as it did not seem to matter on the backend whether ufw was enabled or not, I tried to discover the HDHR on some of my other systems. Counting my laptop and the backend, I tried to discover the HDHR on 5 separate computers ALL running Ubuntu 12.04.1 LTS.


[LIST]
[*]laptop -- no devices found
[*]backend -- no devices found
[*]mythfrontend #1 -- discover successful
[*]mythfrontend #2 -- discover successful
[*]music/photo server -- discover successful
[/LIST]

They were all tested with ufw disabled and ufw enabled with the rule "allow from 192.168.1.117" included. 192.168.1.117 is the IP address of the HDHR3. I got the same result regardless the ufw setting.

The only operating system difference between these machines is the backend and music/photo server are running a 64 bit version of 12.04.1. All the others are 32bit versions.

I will try to figure out what the difference is between these machines to cause the issue. Alternatively, I guess I could make the music/photo server a slave backend for the HDHR.

Any other suggestions would be appreciated.

Thanks for your help.

John

---

### Post by nickrout on 2012-10-20
Very odd. Just as faras firewalling is concerned I am pretty sure hdhr uses udp so make  sure that is allowed. Silicon Dust have good forums. Try there perhaps.

---

### Post by JWB47 on 2012-10-23
I have found the problem. It wasn't directly firewall related, but was the fact the backend has 2 LAN ports. Apparently this is a known routing related issue.

hdhomerun_config requires the IP address to access the HDHR as it won't automatically discover it because of the multiple LAN ports.

Knowing this and going into mythtv-setup to configure the capture card, the option "Manually Set IP Address" for the HDHomerun makes sense. Entering the IP address, manually entering the tuner # and performing a scan for each tuner and all is well.

Thanks for the help.

John

---

### Post by u2nTu on 2012-12-18
@JWB47, thanks for this thread, where those like us who don't like following [COLOR=DarkRed]**[the guide]("https://help.ubuntu.com/community/HDHomeRun/MythTV")**[/COLOR] will seek an answer. O:)

But even with a fresh install, I had an additional problem that the firewall (ufw, 'Uncomplicated Firewall') was blocking LAN traffic (as nickrout mentioned).```
userME@MYhome-1234:~$ hdhomerun_config discover
no devices found
```To fix, I removed all blocking on my local subnet (which is OK as  it's quite secure)```
 userME@MYhome-1234:~$ sudo ufw allow from 192.168.1.0/24
```Problem solved:```
userME@MYhome-1234:~$ hdhomerun_config discover
hdhomerun device 1088D77C found at 192.168.1.103
```

---

### Post by torbenbn on 2013-04-16
I just had another variant of this issue.  I had screwed up my netmask on the Ubuntu box that runs the tvheadend server; here it was 255.0.0.0, but on my router's DHCP settings that are handed out to the HDHOMERUN box it was 255.255.255.0. 

Going by tcpdump output, I guess what happened was that the [FONT=courier new]hdhomerun_config discover[/FONT] command sent out a UDP broadcast on 10.255.255.255 which didn't match the 10.0.0.255 address the HDHOMERUN box would have been listening on. I could see the request going out, but no reply coming back.

Once I changed the netmask to be the same, I could see the tuner.  

/Torben

---

