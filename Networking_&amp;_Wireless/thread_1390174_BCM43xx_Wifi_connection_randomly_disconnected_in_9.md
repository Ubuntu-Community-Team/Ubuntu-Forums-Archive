---
title: "BCM43xx Wifi connection randomly disconnected in 9.10"
date: 2010-01-25
forum: Networking &amp; Wireless
---

### Post by ePierre on 2010-01-25
Hi,

I have an Asus laptop with a BCM4318 wifi chipset.

result of lspsci command about wifi cards:
```
00:09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

For some reason, I often get disconnected. Once it's disconnected, I cannot connect anymore and I need to reboot my laptop in order to get the connection back!

I didn't have this problem when I was on Ubuntu 8.04.

I checked in /var/log/syslog and I found this when the network is disconnected:

```
Jan 25 23:35:31 trane kernel: [10596.796020] wlan0: no probe response from AP 00:22:cf:08:cf:f6 - disassociating
Jan 25 23:35:31 trane wpa_supplicant[955]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jan 25 23:35:31 trane NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Jan 25 23:35:31 trane NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 25 23:35:32 trane wpa_supplicant[955]: CTRL-EVENT-SCAN-RESULTS
Jan 25 23:35:47 trane wpa_supplicant[955]: last message repeated 2 times
Jan 25 23:35:47 trane NetworkManager: <info>  (wlan0): device state change: 8 -> 3 (reason 11)
Jan 25 23:35:47 trane NetworkManager: <info>  (wlan0): deactivating device (reason: 11).
Jan 25 23:35:47 trane NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 1752
Jan 25 23:35:47 trane NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Jan 25 23:35:47 trane NetworkManager: <info>  Activation (wlan0) starting connection 'Auto <xxxx>'
Jan 25 23:35:47 trane NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jan 25 23:35:47 trane NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 25 23:35:47 trane NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 25 23:35:47 trane NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 25 23:35:47 trane NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 25 23:35:47 trane NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 25 23:35:47 trane NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jan 25 23:35:47 trane NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto <xxxx>' has security, but secrets are required.
Jan 25 23:35:47 trane NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jan 25 23:35:47 trane NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 25 23:35:47 trane NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jan 25 23:35:47 trane avahi-daemon[785]: Withdrawing address record for 192.168.1.103 on wlan0.
Jan 25 23:35:47 trane avahi-daemon[785]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.103.
Jan 25 23:35:47 trane avahi-daemon[785]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jan 25 23:35:48 trane NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 25 23:35:48 trane NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 25 23:35:48 trane NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jan 25 23:35:48 trane NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 25 23:35:48 trane NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 25 23:35:48 trane NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 25 23:35:48 trane NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jan 25 23:35:48 trane NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto <xxxx>' has security, and secrets exist.  No new secrets needed.
Jan 25 23:35:48 trane NetworkManager: <info>  Config: added 'ssid' value '<xxxx>'
Jan 25 23:35:48 trane NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jan 25 23:35:48 trane NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Jan 25 23:35:48 trane NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Jan 25 23:35:48 trane NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan 25 23:35:48 trane NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan 25 23:35:48 trane NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 25 23:35:48 trane NetworkManager: <info>  Config: set interface ap_scan to 1
Jan 25 23:35:50 trane NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 25 23:35:52 trane wpa_supplicant[955]: CTRL-EVENT-SCAN-RESULTS
Jan 25 23:36:48 trane wpa_supplicant[955]: last message repeated 8 times
Jan 25 23:36:48 trane NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Jan 25 23:36:48 trane NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jan 25 23:36:48 trane NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Jan 25 23:36:48 trane NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jan 25 23:37:03 trane NetworkManager: <info>  wlan0: link timed out.
```

I really don't know what's going on... Could you help me to understand where the problem comes from, and maybe to try to solve it?

Thanks in advance!

---

### Post by Canada Lee on 2010-04-22
I am having probs too...the driver must be crashing, or getting HUNG up.

You can hit the light (which is a button) on the front of your laptop to turn the radio off, wait 5 or 10 seconds then turn it back on.

You may have to then select your wireless network connection up on the top bar again, cuz if it tried that by itself earlier, it gives up and wont try again.

I am looking for a real solution as well...

---

### Post by Canada Lee on 2010-04-24
I am running Ubuntu Karmic 9.10 (fresh install) on an Acer Aspire 3000 laptop with a Broadcom BCM4318 Airforce One 54g Rev 02 wireless...

I have wireless connectivity with the B43 driver showing up in the Hardware Drivers application. I have used fwcutter, and can't be certain it completed and downloaded the necessary firmware, as there is a known bug relating to it, where it has a YES / NO question about downloading the firmware, and once selecting YES it exits...without any explanations as to success or failure...search for that fwcutter bug, and you'll know what I mean.

Anyways, what I am experiencing like so many others with broadcom's are experiencing is connectivity with random disconnects. I have been trying to troubleshoot this for months, and I think we need to be digging deeper...not looking on the surface... Here's what I've found out...

Need to have a controlled environment, so...
Laptop is running on AC with battery disconnected to rule out any power saving modes or functions attempting to interfere with operation. Also, screen saver has been deactivated, and in power saving settings it is set while on AC to leave monitor on and never turn it off.

I have a big torrent downloading, and my wifi led light is flashing, and I have System Monitor running to show a graph of SENT & RECEIVED...when I see the LED light stop flashing (sometimes it may be off, or it may be on - but its state will remain constant, as in if its off, it stays off and doesnt fluctuate, if on, it stays on and doesnt fluctuate...and when I say the led may be off and stays in that state, I mean the wifi is on, but the led is blinking on and off to represent data xfer and the light just happened to be in the off state when it got HUNG UP.

When the led light gets stuck in whatever state, I know its about to loose connectivity, so I go to my terminal, and I >> ping -c 1 -I wlan0 [www.google.com]("http://www.google.com/") << and sure enough, the ping fails...so I do a >> sudo ifconfig wlan0 down << and if the led was stuck in the ON state, I will see the led go out, and the network manager starts scanning (it wont connect though till)...I then do a >> sudo ifconfig wlan0 up << and then the led light comes up...and the networking manager is still scanning and connects.

So...you dont have to do a reboot to get back your network connectivity...
So I made a little wireless script to KEEP-ALIVE the connection, and if lost, do the DOWN and UP command...sounds like it'd work you think...but makes me think something else may be causing the wireless to BE IGNORED...

Here's my keep-alive script...
#!/bin/bash
while [ 1 = 1 ]
do
if [[ ! `ping -c 1 -I wlan0 www.google.co.uk` ]]; then
echo "$(date)"
ifconfig wlan0 down
sleep 5s
ifconfig wlan0 up
sleep ${1}s
fi
done

I place it in my /usr/local/bin folder, make it executable...open a term, and run it with
sudo keep-alive 60
the 60 can be whatever you want it to be, it tells it to wait 60 seconds then ping, then wait 60 seconds then ping...it will run till you stop it with a CTRL-C...if a ping fails it will DROP the wlan0 interface, wait 5 seconds and then bring it back UP. It will also echo in the terminal the ping failure and the time and date.

Thing I noticed, the terminal window is open, my keep-alive is running (I even had it echoing the successful pings every 60 secs) and I can see my cursor blinking in the terminal window...but when I notice the wifi led light not blinking, I know it is going to loose connectivity...and the cursor in the terminal has stopped blinking, and the clock on the top panel has stopped updating...everything on the screen is frozen to a snapshot of when the wifi was working...if I hit the mouse touchpad, the cursor in the terminal starts blinking, the clock in the top panel updates, my torrent display updates. Its like the display went to sleep...and me touching the pad woke it...and it wasnt ASLEEP long enough for loss of connectivity, I know this cuz I waited longer before hitting the touchpad, and when that woke it, then I see a bubble saying disconnected from my network...and then the network manager scanning...and it wont connect, then my keep-alive script drops the wlan and brings it up, and then the netman scanning connects...

You have to remember, I have told it not to spin down hard drives, never to turn off or blank the display, nor screensaver.

But I know my keep-alive script was frozen, everything was frozen...no heavy CPU usage, just like asleep. and me touching the pad woke it from that sleep, and it continued where it was before the sleep...

What makes it sleep like that? What components of Ubuntu perform that job? It cant be the wifi driver just stopped communicating to the kernal, cuz me waking it by swiping my finger on the mouse touchpad should not be able to influence a modem communication driver...

On the other hand, a power savings mode, inactivity, screensavers and so on can be influenced by user input to interrupt their behavior.

So even when power savings is off, something is suspending things...and it is not at constant intervals, it is at random intervals. There is no overheating going on here, and the cpu in not throttling. I am using only max of 10% when torrent is dloading. And if there was overheating or throttling, who ever heard of influencing their state by swiping the touchpad!

Anybody know where to look for something that is making the kernal or some other area going to sleep?

---

### Post by Canada Lee on 2010-04-24
Also, I have followed instructions from the following site to set up my firmware, as that site seemed to relate different scenarios for the b43legacy the b43 and the b43xx drivers, while other sites seem to only use the b43 for all scenarios...

[http://wireless.kernel.org/en/users/.../b43#fw-b43-lp]("http://wireless.kernel.org/en/users/Drivers/b43#fw-b43-lp")

I had the same connectivity with random disconnects before using the b43 provided by the Hardware Devices application, and after following that website.

No change in random disconnects...but it never disconnects when I'm at the laptop using it...because my every move keeps the computer in a state of being awake.

Its only once I have left it alone, that it seems to go to sleep and when it does, everything even the screen display, and the wifi led light, just freezes or pauses...and will stay that way...and my keep-alive program wont save it, cuz it has stopped doing pings, cuz its been paused.

I set it to echo the time and date of each successful ping every 60 seconds, and it would, and it would...but then when the wifi led light's state gets stuck, I know the prob is happening again, and sure enough, no more successful pings, no more failed pings being echoe'd to the screen...clock aint updating...touch the pad...everything on the display updates, then a min later a failed ping (3 mins after the last ping shown on screen - a ping should be happening every 60 seconds)...then a bubble for disconnected network...then the netman scanning, then cuz my prog did a DOWN & UP, connection.

But I shouldnt have to be here to wake it from sleep.  There is no setting in the BIOS for this.

Someone must have an idea where to look?!

---

### Post by Canada Lee on 2010-04-25
Well, I found a way to prevent my broadcom from disconnecting at random intervals...

You know when you watch a movie, it prevents the screensaver from starting while your watching the movie...it must be preventing the INACTIVITY timer from tripping...

Thats one way...or another way, less cpu intensive, is to play a MP3 with rhythmbox...set the volume low and have it repeat...

My keep-alive program, thats why I tried echoing successful pings every minute, to show Ubuntu there is a program active, and sending info to the screen...but that didnt stop the INACTIVITY timer I guess...

So now I can file a bug report, but against what PROCESS?  The inactivity timer?

---

### Post by chrisblue on 2010-04-27
Some interesting ideas there Canada Lee. I am having a problem with my wifi dropping and a networkmanager restart doesn't fix it. The only solution so far has been a reboot.

It maybe inactivity that is causing it but in any regard I quite like your workaround with the down and up script. I might try that manually and see how it works.

Cheers

---

### Post by Canada Lee on 2010-04-27
I have experienced random disconnects for 2-3 months...and I have searched for other peoples solutions or fixes, even looked for possibly new drivers / firmware etc...

Found nothing that worked, so I spent a week trying to find out what was going on...

For my problem of random disconnects, it has been solved for about 2 to 3 days straight now.  Not using the keep-alive program, the longest my laptop ran before one of these random disconnects was about 3 hours.  Now I have ZERO random disconnects because I have Rhythmbox playing one MP3 (muted) repeatedly, and that is keeping the Operating System from clicking into INACTIVITY...Even though I still have ALL power savings/screensavers/spin down hard drives/turn monitor off after xx time/etc etc DISABLED...and if that Rhythmbox isn't playing a MP3, then my connection will randomly disconnect.

chrisblue:
One thing I noticed is...you can only SAVE the random disconnect if YOU, or a program like my keep-alive steps in before the WIFI driver is totally disregarded.  What I mean is, I kept my downloads window open, and I opened a TERMINAL window with its background set to transparent, so that the TERMINAL window was in front of the downloads window, but I could still see the progress of the downloads through the terminal window.  And when I noticed my WIFI led light stuck in a state of OFF or ON, I could see through the terminal window that the downloads had stopped...even though Network Manager still looked as though I am connected...

If the wifi light had JUST been paused or suspended (cuz the OS INACTIVITY or something), then swiping my finger on the touchpad would RESUME the wifi and downloads without any interruption.

But if the wifi light had been paused or suspended for a longer period of time, like maybe 4 mins or more, then when I swiped my finger on the touchpad, it did not RESUME...and thats when the >> sudo ifconfig wlan0 down << and then wait 5 seconds then the same command substituting >> down << for >> up << DID WORK.
And because I sat over the laptop trying to monitor its progress, I was able to either save the connection, or initiate a new connection to my net.  With my keep-alive program running, if it was able to save the first occurrence of a failed ping, then it would on every subsequent failed ping.  But I did observe 50% of the time (if not more) that my keep-alive program was also being suspended, and when I noticed this, all I would have to do is swipe on the touchpad, then my prog would fail a ping, then DOWN then UP and it was good.  But I could not be certain if the next occurrence would require my intervention as well.

There were a few times when coming back from work it was again suspended (and my keep-alive too!) and when swiping the touchpad, that woke it up, but the wifi must've been down TOO long...and there must be some processes which ARE NOT suspended that try and talk to the wifi driver, and it doesnt respond.  I suppose if it cannot communicate with the wifi after maybe 10 mins, maybe 20 mins or more, either the wifi driver hangs, or a process that communicates to the wifi driver will hang.  Because my program, nor I was able to restart the network, then I had to shutdown and restart the computer to gain use of my wifi again.

In my situation I discovered my keep-alive program was useless to me, as it was being suspended along with the display, the clock, the wifi, everything...  So what keeps the computer in a state of ALWAYS ACTIVE?  Playing a movie or a MP3 does.

But others might find that keep-alive works for them, or maybe they can use it likewise to diagnose their wifi.

I've got a BCM4318 chipset wifi, and using the B43 version of driver I have, and then again, add the version of firmware I am using, along with whichever key processes in my Ubuntu...this combination = random disconnects due to various processes being suspended by the INACTIVITY monitor.

If you have a different chipset, or different firmware or something, you may not have the same combination.

But it can equally be said that Ubuntu is allergic to any of the B43 drivers, and any B43 driver (if found in the system) will be CLASSIFIED into the power savings catagory along with turning down monitors, spinning down hard drives etc.

Try running Rhythmbox (muted) on repeat to see if it prevents you loosing connection.  I would like to know if THIS solves anyone elses situation.

---

### Post by Canada Lee on 2010-04-27
Thats what I was doing, manually typing in the ping command, and the sudo ifconfig wlan0 down and so on...then whenever I needed to do them again, I used the up arrow on the cursor movement keys to quickly pull the necessary macro from its history.

For me, the down and up only worked if the connection was lost in the last 4 mins or so...if it was any longer than that it prob didnt work because by then the driver was broke.

Try playing a MP3 on repeat and see if your able to retain your connection THAT way!

---

### Post by chrisblue on 2010-04-28
Hey CL, came across this thread trawling through the forums [http://ubuntuforums.org/showthread.php?t=1459564](http://ubuntuforums.org/showthread.php?t=1459564)

seems like it might be a pointer for a proper solution to your issue.

Cheers. Chris

---

### Post by Canada Lee on 2010-04-28
Thanks chrisblue for the thought, but sadly this does not work for either the hardware, or the drivers that provide the features for the hardware.

I was playing with all those sudo iwconfig wlan0 power off (or on, or auto) settings before, and some other options with the iwconfig, but I get the following error with almost all...i cannot set anything...

Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.

But that is a good TIP that I'm sure someone out there will be able to use!

---

### Post by chrisblue on 2010-06-04
Whilst not exactly a fix I did come up with a workaround for my issue.

My wifi connection is only used to get program guide data for my mythbuntu backend. It usually holds 8 days of guide data so if I don't have a wifi connection for a few hours it is not an issue.

What I did was put together a basic script that pings the router and in the event that it doesn't get a response does a networkmanager restart.

Dropped this into the hourly cron jobs and it successfully brings the wifi back up without me even noticing most of the time.

Acknowledged this wouldn't work as well for ppl that are running more wifi time critical apps though.

---

### Post by Canada Lee on 2010-06-09
This is an update about the random disconnects, in case this can benefit anyone else.

I thought it might have been the network manager periodically scanning to see what available wifi is in the area, and it randomly hanging...like when it sends a command to scan for avail wifi, it hangs, or maybe waiting for a response, it waits forever.

But I doubt that is the issue.

So far since I diagnosed my problem and solved it by playing a MP3 forever using rhythmnbox, my prob has stayed in the closet and has never shown its face.  So thats a few months of it being suppressed.

I recently connected to my net using the ethernet cable, and turned off my wifi radio, as well as right clicking on Network Manager and turning off Enable Wireless.

Being as I was using ethernet, and all wireless was off, I thought, HEY I should be able to QUIT rhythmnbox now...I dont need to keep the wifi AWAKE...

Surely enough, minutes later everything was sleeping...the little led light by the ethernet cable was lit solid...and the display was showing a still image of what was displayed last when it WAS awake.  Swiped my finger cross the touchpad...and immediately the display updated...this confirmed my suspicion that it was sleeping...then the ethernet light starts flashing...I watch the display and all the speed counters are dropping to ZERO...then a couple of minutes it starts making connections and the speed counters start increasing...

So, this random disconnects of mine, due to some kind of inactivity timer is not the BROADCOM driver...I thought the broadcom driver might have been written to be power saving or something...But when I right click on Network Manager and click on Connection Information, it shows the ETH0 connector using a different driver, not a broadcom one...

So this prob is either some kinda power savings mode, or inactivity for all communications.  Not just broadcom, not just wifi...  A little more system wide than that.

In my Ubuntu, I have turned off all forms of power savings I can find...spin down drives...turn of monitor...suspend etc etc.

And being a laptop, it may be a part of the BIOS.  I have flashed the BIOS with the latest available from the Acer website.  And going into the BIOS settings, there are no ACPI or power savings settings anywhere.  So they do not allow you to change them.

Playing an MP3 repeatedly keeps the system awake when using the ethernet as well...so I am still forced to play a MP3 to solve my prob whether I use wireless or wired.

Ubuntu may not even have any control over this problem if its embedded inside the BIOS itself.

Hope this helps someone.

---

### Post by ePierre on 2010-06-10
Thanks for your answers and your feedbacks.

This is a very strange issue... and I kinda gave up, installing the latest Ubuntu. It seems to work much better, I didn't experienced a lot of disconnections since I updated.

---

### Post by atulkakrana on 2010-08-07
Command for turning power monitoring off is

sudo iwconfig eth1 power off

your adapter could be different, Use 'ifconfig' to find correct adapter

---

### Post by ePierre on 2010-08-08
Hi atulkakrana,

If I type iwconfig, here is the result I have before trying your command:


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"XXX"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:CF:08:CF:F6   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          **Power Management:off**
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


So apparently the power management is already off.

When I try your command, I have this:


$ sudo iwconfig wlan0 power off
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.


So I don't think it's related to power management.

Thanks anyway!

---

### Post by Ryzzen on 2011-04-27
I've been suffering this exact same problem. You'd think there would be a legitimate fix by now. :-?

Anyway, I came up with a slightly more elegant solution than running Rhythmbox all the time, since it uses more memory and cpu than I'd care to give up on my tiny netbook. Plus, I don't like the tray icon being there all the time.

First I created a one-second silent .ogg file in Audacity. To do so, simply start Audacity, click on Generate > Silence..., enter 000,001 seconds, and export it as an .ogg file. I saved mine as silence.ogg and moved it to /usr/share/sounds/.

**ogg123** is a command-line ogg-player that should come with every system. It uses a very minimal amount of cpu and ram, so it's perfect for running in the background and playing, well, silence. The easiest way I've found to implement this is to create a .desktop file and add it to /etc/xdg/autostart/, like so:

```
[Desktop Entry]
Encoding=UTF-8
Name=Keep Alive
Comment=Prevent wireless from shutting off when inactive
Exec=ogg123 -r -q /usr/share/sounds/silence.ogg
Terminal=false
Type=Application
X-GNOME-Autostart-enabled=true
```

This will run every time you log in, so you shouldn't have to worry about it ever again. Plus, it doesn't interfere with any other music you may want to play.


Hope this helps somebody.

If anyone has a better way of doing this, let me know. :D

---

### Post by maestrobwh1 on 2012-08-19
This is STILL an issue with Ubuntu 12.04. Nothing REALLY works that addresses the actual problem. One suggestion that does help is installing WICD and removing network-manager. I don't think network-manager is the issue but wicd seems to reconnect more reliably, there is box to check under preferences that when enabled, will reconnect with a connection loss.

 I used to use ndiswrapper back in the Dapper 6.06 days.  It never disconnected, and fwcutter worked okay in Lucid, seemed slower but reliable.  The issue is somewhat annoying but it is on an old acer that I don't use frequently.

---

### Post by wildmanne39 on 2012-08-19
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

