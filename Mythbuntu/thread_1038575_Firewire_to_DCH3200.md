---
title: "Firewire to DCH3200"
date: 2009-01-12
forum: Mythbuntu
---

### Post by oldpgmr on 2009-01-12
My firewire connection was working fine when I had a DCT6200 STB.  Then last week the box died and Comcast replaced it with a DCH3200.  
The fire_tester showed a successful connection using Broadcast and the log does not show any firewire failures.  However, 8.10 refuses to recognize the firewire.  

Is this a configuration issue or should I try to get Comcast to trade for another DCT6200?  

Motherboard: Machspeed P4M800
CPU: Intel Celeron 2.4Ghz 
RAM: 1 gb
Video Card: NVIDIA GeForce 7600GS 256 mb
Sound Card: VIA Chipset
HD: 
Remote: N/A
Tuners: Hauppauge PVR-150, Firewire to DCH3200

---

### Post by crez79 on 2009-01-13
I ran into a similar problem. For me I deleted the firewire tuner and wanted to add it back but it would get recognized. It ended up being I didn't have ownership of raw1394 when running the mythtv setup program. 

try ```
ls -l /dev/raw1394
``` to see who owns it. If it is root take ownership of it with ```
sudo chown mythtv:mythtv raw1394
``` and verify mythtv has ownership and try to setup the tuner again. 

Initially, I used parts of the [Firewire howto]("https://help.ubuntu.com/community/MythTV_Firewire") to get it to work, which required editing of /etc/init.d/mythtv-backend to add the permission steps. The priming steps were already there for me.

Hope this helps.

---

### Post by oldpgmr on 2009-01-17
For all of the flailing around I did yesterday I seem to have gotten the box to recognize the firewire.  This seems to be indicated by the setup displaying the id of the card where before this was blank.  However, whatever I did has disconnected the backend server.  Hopefully this is something simple.

Thanks for the help.

> Starting mythfrontend.real..
2009-01-16 22:20:19.086 New DB connection, total: 2
2009-01-16 22:20:19.100 Connected to database 'mythconverg' at host: localhost
2009-01-16 22:20:19.127 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-16 22:20:19.127 Enabled verbose msgs:  important general
2009-01-16 22:20:20.449 Unable to parse themeinfo.xml for glass-wide
2009-01-16 22:20:20.449 The theme (glass-wide) is missing a themeinfo.xml file
2009-01-16 22:20:21.093 Unable to parse themeinfo.xml for glass-wide
2009-01-16 22:20:21.093 The theme (glass-wide) is missing a themeinfo.xml file
2009-01-16 22:20:22.069 No theme dir: /home/bolingw/.mythtv/themes/Mythbuntu-8.04
2009-01-16 22:20:22.074 Primary screen 0.
2009-01-16 22:20:22.076 Using screen 0, 1024x768 at 0,0
2009-01-16 22:20:22.081 No theme dir: /home/bolingw/.mythtv/themes/Mythbuntu-8.04
2009-01-16 22:20:22.083 Switching to square mode (Mythbuntu-8.04)
2009-01-16 22:20:22.135 Using the Qt painter
[B]mythtv: could not connect to socket
mythtv: No such file or directory
2009-01-16 22:20:22.136 lirc_init failed for mythtv, see preceding messages[/B]
2009-01-16 22:20:22.137 JoystickMenuClient Error: Joystick disabled - Failed to read /home/bolingw/.mythtv/joystickmenurc
2009-01-16 22:20:25.097 Specified base font 'medium' does not exist for font clock
2009-01-16 22:20:25.098 Specified base font 'medium' does not exist for font small
2009-01-16 22:20:25.098 Specified base font 'medium' does not exist for font medium
2009-01-16 22:20:25.099 Specified base font 'medium' does not exist for font large
2009-01-16 22:20:25.103 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-01-16 22:20:25.271 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-16 22:20:25.604 Registering Internal as a media playback plugin.
2009-01-16 22:20:25.927 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-16 22:20:26.495 MythMusic adding CD-Writer: 0,0,0 -- DVD A  DH20A4P  
2009-01-16 22:20:26.665 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
[B]SIP listening on IP Address 192.168.0.162:5060 NAT address 192.168.0.162
SIP: Cannot register; proxy, username or password not set[/B]
2009-01-16 22:20:27.288 No theme dir: /home/bolingw/.mythtv/themes/Mythbuntu-8.04
2009-01-16 22:20:30.583 Connecting to backend server: [B]127.0.0.1:6543 (try 1 of 5)
2009-01-16 22:20:30.584 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-01-16 22:20:34.595 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-16 22:20:34.599 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.[/B]
2009-01-16 22:21:06.149 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-16 22:21:06.150 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-01-16 22:21:07.329 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-16 22:21:07.329 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-01-16 22:21:21.406 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-16 22:21:21.407 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-01-16 22:21:22.599 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-16 22:21:22.599 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.

---

