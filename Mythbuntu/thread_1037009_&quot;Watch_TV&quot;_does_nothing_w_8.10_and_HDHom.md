---
title: "&quot;Watch TV&quot; does nothing w/ 8.10 and HDHomeRun"
date: 2009-01-11
forum: Mythbuntu
---

### Post by gungfujoe on 2009-01-11
I'm pretty new to Linux, and very new to setting up a proper HTPC (I had a Win2K system in the living room that I'd use to feed downloaded videos until recently.  No tuner, no DVR, etc).  I'm trying to set mine up with Mythbuntu 8.10, and decided on SiliconDust's HDHomeRun ATSC tuner.  I went through all of the initial setup, and successfully did a channel scan (which told me that Mythbuntu is communicating with the HDHomeRun successfully).  I haven't yet signed up with the scheduling service, wanting first to get everything working.

After running through the setup, when I hit "Watch TV" from the MythTV frontend, the screen simply refreshes (goes black for a small fraction of a second and then goes back to the menu).  No error message or anything, it just doesn't work.

I've verified that the HDHomeRun is functional and set up correctly by installing the Windows software on another machine on the network.  I can pick any channel, launch it in VLC, and it plays just fine.  So obviously, I've screwed something up in my Mythbuntu setup.  Without any kind of error message, though, I have no idea what.

Any help would be greatly appreciated.

---

### Post by RonPDX on 2009-01-11
Eric, 

I was having the same problems that your were but with a different card. To get mine up and running I setup an account with Schedules Direct (they offer a free trial) then setup my Video Source, after scanning my scanning my channels, I updated my database and I was able to watch TV. 

Mythbuntu has a great install manual that helped me out a lot [http://www.mythbuntu.org/installation_manual](http://www.mythbuntu.org/installation_manual)

---

### Post by gungfujoe on 2009-01-11
Ron,

I'd already gone through the manual, and didn't see anything in there that applied.  SchedulesDirect can be used as a video source, but so can the cable-transmitted data.  So while using SchedulesDirect will certainly be better in the long run, there's no reason I'm aware of that not using it should prevent me from using the "Watch TV" function at all.

And given the number of problems I'm finding with Mythbuntu (no sound, no ability to watch TV, frequent freezing...), I'm reluctant to sign up for a 7-day free triel of Schedules Direct when it's entirely possible that it'll take more than 7 days to get this system up and running to the point where I can actually try it and determine if it's worth paying for (I'm pretty content to use the old VCR method, telling the system to record channel X from time Y to time Z).

---

### Post by cholland on 2009-01-11
I have an HDhomerun with an ATI mombo and found that if you're running of a DHCP router, mythbackend can startup before it has aquired an IP. I just restart the backend after I login /etc/init.d/myth-backend restart .. or soemthing close to that. For the long run I'll probably configure my myth box to have a static ip.

To get audio working over HDMI I had to go get the ALSA patch on these forums that pushed me to version .18a from .17 that is in the ubuntu repository. Now I get audio.

My last problem is that when watching some shows like a true 1080i signal vs a 720p signal the filters required for interlacing screw things up. My TV is a 1080i and if I pick none I can watch my 1080i stuff just fine, but my 720 stuff is all fractured all over. If I use a linear filter then I can watch 720 stuff but not 1080i stuff it gets fractured all over.

Hope this helps some.

Also /var/log/mythtv/mythfrontend.log has all the relevant output for the frontend.

Here is the link to the post with the sound upgrade script.

[http://ubuntuforums.org/showthread.php?t=962695&highlight=alsa+upgrade](http://ubuntuforums.org/showthread.php?t=962695&highlight=alsa+upgrade)

---

### Post by ikke2808 on 2009-01-12
Hi gungfujoe,

I am pretty sure this has to do with right to your Mythtv temp. dir.

Live TV needs a place to right the files to and if you mythtv user is not allowed, it does not start.

Please check your temp dir and set it to wirtable for your Mythtv user.

Cheers.

---

### Post by DrJohn999 on 2009-01-12
Same problem here. I'm configured with the SiliconDust to use EIT (on both  sources). When I boot the system, WatchTV does nothing. If I then go all the way down into MythTV setup and then run mythfilldatabase on exit, then (and only then) does Watch TV work.

IKKE2808 : please inform those of us who don't know, where is the MythTV tmp directory, and what is the default username for the MythTV user? Then I can make some sense of the question of folder permissions. I looked in /tmp and can't find anything suitable.

Thanks,

DrJohn

---

### Post by uncle hammy on 2009-01-13
If you schedule recordings, do they work?  It sounds to me like your backend isn't finding your hdhomerun units on boot up.  Does your backend use a static ip, or dhcp assigned?

It could be that your backend is loading before your backend's network is running.  It would make sense that you can watch tv after you run the back end setup because you are restarting the backend service after you have network availability.

If this is the case, you either set up your backend with a static ip (not a bad idea for a server anyways), or set myth-backend to start as one of the last things during boot... [http://ubuntuforums.orgshowthread.php?t=925242](http://ubuntuforums.orgshowthread.php?t=925242) 

hope this helps

---

### Post by ikke2808 on 2009-01-14
DrJohn,

run mythtv-setup and go to the Storage directories.
check the LiveTV directory.
Then check the rights for this directory. Set it to rw for all.

Normally the user should be mythtv, but that is not really needed.

Cheers.

---

### Post by DrJohn999 on 2009-01-15
So far no success.

ikke2808: the /var/lib/mythtv folder and contents have 775 permission with mythtv as user and group. Changing to 777 has no effect on this problem. Thanks for the suggestion, tho.

uncle hammy: A static IP addr in /etc/network/interfaces or the default netmanager DHCP client setup makes no difference. The server's dhcpd is set to give a predetermined IP per the MAC anyway.

Moving /etc/rc2.d/S20mythtv-backend to S99 makes no difference.

Adding up to a 10-sec sleep in /etc/init.d/mythtv-backend just before it tries to start the backend makes no difference.

Manually stopping and restarting /etc/init.d/mythtv-backend has no effect. The mythtvbackend task is active and running. Curiously, stopping the backend with /etc/init.d/mythtv-backend stop raises an error message:
```

$ sudo /etc/init.d/mythtv-backend stop
 * Stopping MythTV server: mythbackend 
 No /usr/bin/mythbackend found running; none killed.
 [ OK ]

```
even though the task appears to be active. And the active task is not killed. Also, running MythSetup after the above manual starts warns that the backed is still running.

So, I'm at the same impasse. FWIW, the hw is:

Asus M3N78-EM, Phenom 9600, 2 GB, 1 TB SATA, Antec Fusion w/ iMon VFD/IR/knob (of which only the VFD is working thus far), and a 1680 x 1050 LCD for the current debugging work (the onboard HDMI works too). Also, an Adesso wireless kb / touchpad, working fine.

The net topology is 1000/100/10 wired with 8.04 LTS server, which serves dhcp, dns, ntp, etc., Shorewall, and the web. The server, Myth system and the HDHomeRun are plugged into a single 1000 switch. There are 4 other systems plus a print server device on this subnet, and there's a separate wireless subnet on the server. Ssh to the Myth system is functional.

-- DJ

---

### Post by DrJohn999 on 2009-01-15
Oh Yeah, Ron PDX: I forgot to mention that it makes no difference whether I use EIT or SchedulesDirect, other than how long it takes to update the database.

-- DJ

---

### Post by linuxisevolution on 2009-01-15
I have found that xbmc ( [www.xbmc.org](www.xbmc.org) ) is much better than mythtv. Mythtv gave me many problems too...

---

### Post by gungfujoe on 2009-01-15
> **cholland said:**
> I have an HDhomerun with an ATI mombo and found that if you're running of a DHCP router, mythbackend can startup before it has aquired an IP. I just restart the backend after I login /etc/init.d/myth-backend restart .. or soemthing close to that. For the long run I'll probably configure my myth box to have a static ip.
I think this is my problem.  If I run MythTV setup, which closes the backend, do nothing, exit setup, and try "Watch TV", it works.  I did have the "double horizontal image" problem a few minutes ago, but I've seen that discussed here, so I'll look around for troubleshooting before asking for help on that.  I suspect a static IP is the solution here.  I'll look around and see if I can figure out how to do that. :)  (15+ years of DOS and Windows expertise isn't helping me with Linux system administration, and I feel like a complete neophyte again).

> **cholland said:**
> To get audio working over HDMI I had to go get the ALSA patch on these forums that pushed me to version .18a from .17 that is in the ubuntu repository. Now I get audio.
I'm not sure I have time to try this out tonight, but thanks for the link, and I should be able to play with it tomorrow, and hopefully get audio out of either HDMI (preferable) or S/PDIF (take what I can get).

> **cholland said:**
> Also /var/log/mythtv/mythfrontend.log has all the relevant output for the frontend.
This didn't tell me squat when "Watch TV" didn't work.  The last two lines would be about connecting to the backend and using port 40.  No indication that it succeeded or failed.  When it works, I see a lot more in the log, though.  When it works, I also see some ALSA errors.  Audio is being disabled by MythTV because it can't set ALSA parameters.

Thanks again for your help.  I'm slowly getting there, and will hopefully be able to _use_ MythTV over the long weekend.

---

### Post by gungfujoe on 2009-01-15
> **linuxisevolution said:**
> I have found that xbmc ( [www.xbmc.org](www.xbmc.org) ) is much better than mythtv. Mythtv gave me many problems too...
Looking at their website, though, XBMC appears to be a media server only, but not a DVR.  The whole point of scrapping my basic Win2K setup and installing Mythbuntu was to also have a DVR.  To me, simply using Win2K, Explorer windows, MediaPlayer Classic, and a wireless keyboard was sufficient for a basic media server.  It doesn't cut it for DVR functions, though.

---

### Post by DrJohn999 on 2009-01-15
> **DrJohn999 said:**
>  ... Manually stopping and restarting /etc/init.d/mythtv-backend has no effect. The mythtvbackend task is active and running. Curiously, stopping the backend with /etc/init.d/mythtv-backend stop raises an error message:
```

$ sudo /etc/init.d/mythtv-backend stop
 * Stopping MythTV server: mythbackend 
 No /usr/bin/mythbackend found running; none killed.
 [ OK ]

```
...


HIGHLY RECOMMEND UPDATING TO LATEST WEEKLY MYTHTV BUILD

I've had a little success tonight. In a default fresh install the "Updates Available" icon appears, but the update itself fails (not able to connect to the server). I changed the update server from "Main Server" (the default) to "United States" and thence uploaded and installed 140 or so new files. This itself had no effect on the problem at hand.

I then followed instructions [here ]("http://www.mythbuntu.org/auto-builds")to add the Mythbuntu Automatic Weekly Build repository to my installation and then updated / upgraded using apt-get.

Now, after booting the system, if I run
```
~$ sudo /etc/init.d/mythtv-backend restart
```
I am subsequently able to "WatchTV". Nor do I see the previous error message on restart.

Still need to do the restart, however, so the possible issue of the timing between the backend and the network startup remains.

**Static IP:**
I had configured /etc/networks/interfaces with a static IP, but had not disabled Network Manager. However, it may not be necessary to disable NM, but rather set the static in it instead,[see towards the end of this thread]("http://ubuntuforums.org/showthread.php?t=969873&highlight=static+IP&page=2") (and thanks uncle hammy for starting that thread!). I'll play with the static IP idea and post my result.

-- DJ

---

### Post by DrJohn999 on 2009-01-15
No luck with the Static IP. I was able to get to a static address with NetManager per the thread above. Just fill in all the fields the first time (name="default", MAC address, "system" checked, IPV4 address, mask, gateway, DNS, search) and it works fine for IP connection, but no luck with getting "WatchTV" to go without first restarting the back end.

-- DJ

---

### Post by _jdj_ on 2009-01-16
I had the same problem.  Network manager was bringing up the network after logging on. Way after the backend started.  Apparently  /etc/network/if-up.d/mythtv-~if-ip.d was not doing what it was supposed to do - restarting the backend.  I disabled the network manager by adding:

auto eth0
iface eth0 inet dhcp

to /etc/network.interfaces
Now the network comes up early and I don't have to restart the backend.  BTW I also assign a static ip via dhcp - mac based.

Joel

---

### Post by DrJohn999 on 2009-01-17
Got it all to work by: 1) updating all packages, 2) static IP (via net manager), and 3) moving /etc/rc2.d/S20mythtv-backend to /etc/rc2.d/S40mythtv-backend for the slightly later startup.

Now to get the sound, VFD, IR, and knob to work... But that's another day, more threads.

-- DJ

---

### Post by linuxisevolution on 2009-01-17
> **gungfujoe said:**
> Looking at their website, though, XBMC appears to be a media server only, but not a DVR.  The whole point of scrapping my basic Win2K setup and installing Mythbuntu was to also have a DVR.  To me, simply using Win2K, Explorer windows, MediaPlayer Classic, and a wireless keyboard was sufficient for a basic media server.  It doesn't cut it for DVR functions, though.

Oh, I understand. With MythTV, do you need to have a second computer running the backend too? Or can you just have one do both without a server?

---

### Post by Damanther on 2009-01-17
Assuming the hardware on the single computer is robust enough, It is OK, and even desirable to run the backend and frontend on a single PC in my experience.

Damanther

---

### Post by gungfujoe on 2009-01-17
> **cholland said:**
> To get audio working over HDMI I had to go get the ALSA patch on these forums that pushed me to version .18a from .17 that is in the ubuntu repository. Now I get audio.
This worked... sortof.  I get audio with the system now (at least via S/PDIF, I haven't tried re-enabling HDMI), but I still don't get any audio when playing TV.  I can play Apple trailers via MythTV with audio, though, so it's working within MythTV.

Right now, my biggest issue is random freezing, though.  Without resolving that, nothing else matters. :(

---

### Post by Shadowfire on 2009-07-29
See the following link:  (I think this will solve your issue if you haven't seen this already) 

[http://ubuntuforums.org/showthread.php?t=1018339](http://ubuntuforums.org/showthread.php?t=1018339)

---

