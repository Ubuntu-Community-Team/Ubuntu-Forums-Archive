---
title: "Mythbuntu 11.04 Snapstream Firefly not working"
date: 2011-05-22
forum: Mythbuntu
---

### Post by daninca on 2011-05-22
I just upgrades to 11.04 (x86_64) and I can't get my Snapstream Firefly remote to work.  I've tried both the user space atilibusb setup (which is what MythControlCenter sets up) and the old lirc_atiusb driver (which is what worked in 10.10).  irw shows nothing in either case.

If it helps, this is what I did to get it working under 10.10:
[http://ubuntuforums.org/showpost.php?p=10631140&postcount=16](http://ubuntuforums.org/showpost.php?p=10631140&postcount=16)

Anybody else have this working under 11.04 (64 bit)?

-Dan

---

### Post by lightning9 on 2011-05-23
Bummer! I started working on the same problem yesterday and was hoping someone had figured it out.

Using lirc_atiusb and configuring the kernel module for debug, I got it to the point where I can see buttons being pressed in /var/log/syslog, but I can't get irw or irrecord to display anything. 

:confused:

---

### Post by mbrinson on 2011-06-06
Lightning9 - I found your great walk-through for how you got snapstream remote working with MythBuntu 8.04.

I just wiped out my MythDora setup because I was having issues (about a year.. have just been dealing with them.. frequent reboots and general slowness) and did a fresh MythBuntu Install.  I was excited to find your walkthrough and then disappointed to discover that things have (of course) been changed with the latest MythBuntu and now the solution no longer works.

Of course I realize it is not MythBuntu itself, but all of the different components that go into it.  It's really amazing to me that any of it works at all.  It's such an awesome project.

Anyway, here's hoping you or someone else are able to discover the solution.  Unfortunately I am not enough of a linux ninja yet to be a real player.  I'm steadily working on it, but definitely not there yet.  For now I just rely on all of you smart people to help me along.  ;)

Okay, here's my little contribution.  There are a couple of other threads I've found with some contributions from the great and famous Jarrod Wilson - seriously I'm a big fan.
So maybe if I link to those then the ideas will come together and the great minds will be able to find the solution.

[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/787742](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/787742)
 [https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/787735](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/787735)

---

### Post by lightning9 on 2011-06-06
As you pointed out, the issue isn't with myth, it is with lirc. I even tried compiling and running the latest lirc source to no avail. 

From looking at all the Snapstream bug reports and how long they have existed without resolution, it appears not many developers care about the remote. Guess there aren't enough of us Firefly'ers out here?

Actually, due to the low level of support, high maintenance and numerous other issues with myth, I ditched it and switched to xbmc quite a while ago. 

And because of this lirc issue, I have also reverted to Ubuntu 10.04 LTS so I could be "guaranteed" to have lirc and other OS support for nearly a couple more years. In fact, I am running 10.04 Server as the base so, in theory, it should be supported for almost four more years! (We'll see.) But, hopefully, something better and more stable will come out long before then.

---

### Post by mbrinson on 2011-06-07
Thanks for your reply Lightning9.  So now you have me curious.  I spent some time checking out xbmc and it looks like in order to view liveTV, pause, schedule recordings, etc. then I actually would need to use xbmc in connection with mythTV as the backend, right?
Is this how you have it set up?
Thanks for any input you can give me.  :)

---

### Post by lightning9 on 2011-06-07
Sorry, can't help you there.

I tried using the PVR part of myth with an HDHomeRun but didn't get enough (or the right) channels to make it worth while. Also, that's where a lot of the high maintenance was. Instead, I mainly used it as a media player frontend for pre-existing audio, video and photo content.

xbmc is now supposed to have PVR support, but again, I don't use it. I returned the capture box many, many moons ago.

---

### Post by mbrinson on 2011-06-07
Okay, sorry to keep pestering you.. I'll make this my last question.

So what is your current setup?  Do you just use a proprietary solution (whatever is provided by your service provider) and then just use XBMC for viewing media?

I'm just curious to know what your setup is for your home entertainment solution.

Thanks!

---

### Post by lightning9 on 2011-06-08
No worries. 

Yes, I use the Time Warner DVR for what little TV I watch (NHL and cycling is about it). Both of those sports are usually shown on VS which I can't get without a decoder. I  didn't want to get into all the IR Blaster stuff and have even more maintenance, so back went the HDHomeRun. And as soon as the Stanley Cup is over, I will probably cancel my cable TV service. Can't see spending nearly $100/month for two sports.

For my digital media, I have an atom based file server running Ubuntu 10.04 Server (sans GUI) and a couple atom/ION HTPCs running 10.04 Server with a minimal gnome installation (gnome-core, et al) and xbmc nightly builds.

As everbody lately, been trying to be a little greener. The server runs 24/7, serves up a 4TB stripe, has a separate drive for the rootfs, is powered by a solid state dc power supply and weighs in at a whopping 35W. The HTPCs are only on when needed. They are capable of decoding 1080i (p, too?) in HW using the NVidia vdpau drivers, are also powered by dc power supplies and have a footprint of about 30W each.

Er...and then there's the not-so-green...Gb LAN (partially green), a 61" DLP TV and 600W receiver. (Oh well, better to be part green than not at all, eh?)

So how did I end up with a Snapstream Firefly? That all started about 5 years ago when I had a "powerhouse" machine with an SD capture card running BeyondTV and burning 300+W around the clock! That all has obviously changed, but I still haven't found an MCE remote laid out as well as the Snapstream. 

Long live the Firefly!

---

### Post by williammanda on 2011-06-11
I have snapstream working with 11.04 using the ATI/NVidia/X10 RF Remote driver.

---

### Post by lightning9 on 2011-06-12
Cool! Would you mind sharing the details? Thanks.

---

### Post by teejster on 2011-09-23
This is a bit late, but here's how I got it working.  I am testing a switch to Mythbuntu from Mythdora, as it sounds like the project is wrapping up.

These instructions are a mashup of the fedora & ubuntu instructions found here:
[http://www.mythtv.org/wiki/Snapstream_Firefly](http://www.mythtv.org/wiki/Snapstream_Firefly)

1. Install the lirc package (using Synaptic, Aptitude, or just "sudo  apt-get install lirc").  When the configuration screen comes up, select  "ATI/NVidia/X10 I & II RF Remote" as the receiver driver and none as  the transmitter driver.
2. Edit /etc/lirc/lircd.conf to remove the auto-configured "include"  line and add the contents of the lircd.conf file for lirc_atiusb driver.
3. Further edit /etc/lirc/lircd.conf by pasting the contents of the code listing marked 
**lircd.conf (atilibusb driver(current standard in Fedora) **

4. (optional) you can test to see that your machine is reading the input from the remote now.  
4a. sudo service lirc restart
4b. irw
4c. Press some buttons on the remote.  You should see output in your terminal window.
5. Make your /home/username/.mythtv/lircrc file (listed below) - the code listing is called
**lircrc for the Firefly **
5a. Follow the advice to change repeat = 3 to repeat = 5.  There are lots to change (74 IIRC), so use a text editor with find & replace functionality.  
6.  I restarted lircd again just in case (sudo service lirc restart)
7.  Launch MythTV frontend and try navigating around.  

I hope this helps!
-T. J.

---

### Post by hoolahoous on 2011-10-11
can you please post your hardware.conf also from the /etc/lirc folder too?
for me irw is not showing any key presses at all..

---

### Post by teejster on 2011-10-11
I'm afraid I don't have a hardware.conf file.  I wound up installing Fedora 15 x64.

The contents of my lirc directory are

[FONT=Courier New][tj@mythserv lirc]$ ll
total 12
-rw-r--r--  1 root root 4827 Sep 29 23:11 lircd.conf
-rw-r--r--. 1 root root  115 Jun 21 13:04 lircmd.conf
[/FONT]

---

### Post by williammanda on 2011-10-13
To get the snapstream firefly working use this link:

[http://ubuntuforums.org/showthread.php?t=1598700&highlight=snapstream](http://ubuntuforums.org/showthread.php?t=1598700&highlight=snapstream)

---

### Post by hoolahoous on 2011-10-13
thanks to everyone. I uninstalled lirc and reistalled. then i copied the config files and it worked !

---

