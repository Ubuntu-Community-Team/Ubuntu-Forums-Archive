---
title: "Networking lost on ISP switch"
date: 2006-02-07
forum: Networking &amp; Wireless
---

### Post by m.musashi on 2006-02-07
I have Breezy installed on a Dell Inspiron 600m. My wireless was recognized and I haven't had any problems with Internet either wirelessly or wired. I often have it connected via wire to my Linksys router. I recently switched from cable to DSL and now I no longer have Internet. My IP has obviously changed but connecting through the router should mask that (I think). If not, how do I get Ubuntu to recognize the new IP?

What's weird is it will work over wired at work and wireless at my Univ. It must have something to do with my router or how Ubuntu seems my router but I can't figure it out. In Windows the switch wasn't even an issue.

On a related issue, Ubuntu always hangs on boot when it gets to "configuring network interfaces". Usually I just ctrl-c over it and networking has worked. It's an annoyance though.

Any thoughts?

Here is the output from ifconfig (but I'm currently connected at work and I don't know if that's changes anything)
> 
eth0      Link encap:Ethernet  HWaddr 00:12:3F:FA:01: DB
          inet addr:172.18.20.17  Bcast:172.18.255.255  Mask:255.255.0.0
          inet6 addr: fe80::212:3fff:fefa:1db/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:623 errors:0 dropped:0 overruns:0 frame:0
          TX packets:391 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:125084 (122.1 KiB)  TX bytes:37041 (36.1 KiB)
          Interrupt:11

eth1      Link encap:Ethernet  HWaddr 00:13:CE:3F:E8:8A
          inet6 addr: fe80::213:ceff:fe3f:e88a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:864 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Memory:faffd000-faffdfff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1375 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1375 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:124527 (121.6 KiB)  TX bytes:124527 (121.6 KiB)

Thanks.

---

### Post by bscbrit on 2006-02-07
Well there can be quite a few possibilities here.

When you changed your ISP you probably should also change your DNS settings. I do not think that this is always essential (after all, a DNS server should just work) but it might be advisable.

Do both your new connection and the old use DHCP or were you given a static IP address to use?  Without knowing the details of either it is difficult to say what is not set correctly.  When you have the information relevant to your new connection please post it and the contents of your /etc/network/interfaces file here please.

Do you have NetworkManager installed?  It can sometimes make decisions about your network's configuration which are not what you want.  Unless you absolutely need it, I would remove it.  But it does appear to do the job it is intended to do - it just doesn't always tell you what it is doing!

Can you ping your router?  Is your router giving the appropriate indications to show that it has established a satisfactory DSL connection?  

If your boot sequence stalls when configuring network devices then there is something wrong.  Your ctrl-c might have hidden the real problem in the past, but not anymore it seems.....  Have you used the appropriate trouble-shooting / fault-finding guides in the wiki?  If not, that should be your first step.

[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)
[https://wiki.ubuntu.com/UserDocumentation#head-d38b79db7b0f5a1765d182a02a00ed8f3b0d0289](https://wiki.ubuntu.com/UserDocumentation#head-d38b79db7b0f5a1765d182a02a00ed8f3b0d0289)
[https://wiki.ubuntu.com/UserDocumentation#head-2167d6cc9b218b20c4e1a883d65101c212f19a12](https://wiki.ubuntu.com/UserDocumentation#head-2167d6cc9b218b20c4e1a883d65101c212f19a12)

---

### Post by m.musashi on 2006-02-07
When I switched I just reset my router (which uses DHCP) and from Windows all was well. New also uses DHCP (I think). Actually, going through a router would it matter what my ISP does? The router used DHCP.

I did have nm-applet installed (is that NetworkManager?). It was more trouble than it was worth so I removed it.

Here is the contents of /etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

iface eth1 inet dhcp
wireless-essid tsunami

auto eth1

iface eth0 inet dhcp

auto eth0
```

As for pinging my router I'll have to wait until I'm home to try but I was able to log into the router and check settings so I assume that means I would also be able to ping it and that my connection to the router is fine.

---

### Post by bscbrit on 2006-02-07
Well first of all remove NetworkManager:

sudo apt-get remove network-manager

You have removed the applet but not the program.  

Are you trying to connect now to your wireless or wired network?  And is your router your DHCP server?  - I assume so.  

Once we have decided what we are trying to achieve, we will connect your networks one at a time.  Did you look at the troubleshooting guides that I gave as links?  If so, what did you find?

Is your router giving all the correct indications - if it hasn't connected to your ISP there is not much point in trying to move forward.  Again, I'll assume so because you hint that  'from Windows all was well'.

---

### Post by m.musashi on 2006-02-07
By all measures I shouldn't be having a problem. I am writing this from a Windows box connecting through my router (wired) and connected to the DSL modem. The laptop that is having the problem is a dual boot and also does not have a problem from Windows.

Network-manager is removed. The remove command returned "package network-manager is not installed, so not removed."

I would like to be able to both wired and wirelessly but lets start with wired. The router is my DHCP server.

I went through the troubleshooting guide for wired and all tests were postive (i.e. no problems) except for the pinging an address other than my router. That one returned "ping: sendmsg: Operation not permitted".

Since I'm online via this router and modem via Windows I believe it's safe to say the router and modem are working well. The laptop was also working well. It would connect both wired and wirelessly up to a few days ago when I connected a new ISP. That is also about the same time that I uninstalled Network-Manager. The first time I only removed the nm-applet from the preferences -> sessions -> startup programs tab. That actually didn't work and upon reboot it still started (i.e. the little icon still loaded on the upper panel. I then used synaptic to remove it.

Interestingly, synaptic has been behaving weird. While at work and connected wired with an active internet connction I get an error about the "following problems" and then a list of errors like this...

W: couldn't stat source package list [http://us.archive.ubntu.com](http://us.archive.ubntu.com) breezy-updates/main packages (/var/lib/apt/lists/
us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_packages) - stat (2 no such file or directory)

This repeats several times for what I assume is every package source. Understand, this happens when the computer is connected with a live internet connection.

At home, with the bad connection synaptic acts as if it does load all repositories but a refresh appears to load 5 of 7, hangs and then gives the could not download all repository indexes message followed but the above error. Related?

Like I said, this is odd. The computer is talking to the router, the router is talking to the modem, the modem is talking to the internet but I get no connection. At work I can connect via wire. At school I can connect over the wireless network. At home...nada (even though windows on both my desktop and laptop connect).

Thanks for taking the time to help me through this.

---

### Post by bscbrit on 2006-02-08
If your desktop and laptop are on the same network can you ping each from the other?  Please confirm that you have both computers on the same network - I am getting very confused.  Are they both wired? Which computer was the /etc/network/interfaces file for that you provided below?  Which one are we trying to set up?

The fact that the system works under windows does prove that the hardware is working, but the hardware is reconfigured each time you boot. So the configuration that works under windows is NOT the same as the one that you have under Ubuntu.  What we have to do is correct it.

---

### Post by bscbrit on 2006-02-08
Do you have a firewall fitted?  The problem with the pings can be caused by a firewall, the computer running out of resources or a kernel problem.  Assuming that you are using the standard Ubuntu kernel appropriate to your cpu then we can discount the latter.  My first hunch would be a firewall/iptables blockage.  If it was a resource limitation then you would have problems pinging any address but this seems to be a problem getting the pings through the router.  Do you have some form of filtering in the router?

---

### Post by m.musashi on 2006-02-08
I'm getting confused too. Both the desktop and laptop are connected via ethernet wire to the router. It has 4 wired ports and is also a wireless router. Assuming I did it right, I cannot ping the desktop from the laptop (desktop is in Windows and laptop in Ubuntu). However, I can ping the laptop from the desktop.

Here is the Windows ping results
```
Microsoft Windows [Version 5.2.3790]
(C) Copyright 1985-2003 Microsoft Corp.

C:\Documents and Settings\Jim>ipconfig

Windows IP Configuration


Ethernet adapter Local Area Connection 2:

   Connection-specific DNS Suffix  . : domain.actdsltmp
   IP Address. . . . . . . . . . . . : 192.168.1.100
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.1.1

C:\Documents and Settings\Jim>ping www.google.com

Pinging www.l.google.com [72.14.207.104] with 32 bytes of data:

Reply from 72.14.207.104: bytes=32 time=45ms TTL=241
Reply from 72.14.207.104: bytes=32 time=45ms TTL=241
Reply from 72.14.207.104: bytes=32 time=45ms TTL=241
Reply from 72.14.207.104: bytes=32 time=45ms TTL=241

Ping statistics for 72.14.207.104:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 45ms, Maximum = 45ms, Average = 45ms

C:\Documents and Settings\Jim>ping 192.168.1.102

Pinging 192.168.1.102 with 32 bytes of data:

Reply from 192.168.1.102: bytes=32 time<1ms TTL=64
Reply from 192.168.1.102: bytes=32 time<1ms TTL=64
Reply from 192.168.1.102: bytes=32 time<1ms TTL=64
Reply from 192.168.1.102: bytes=32 time<1ms TTL=64

Ping statistics for 192.168.1.102:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms

C:\Documents and Settings\Jim>
```

The laptop just hangs (no response) when trying to ping.

The /etc/network/interfaces posted above is from the Ubuntu laptop - the one having trouble.

Your question about a firewall got me thinking. Since this is a new modem I thought the problem might be there. I ran the modem configuration (via a browser to the modem IP address). I did this from the Ubuntu laptop. There isn't a firewall option that I could see, but after doing the modem config (I didn't really do anything but save the settings again) my internet connects sort of works. By that I mean that if I open firefox and wait 30 seconds or so it pulls up google. Likewise, if I wait long enough (sometimes as much as a minute or so) I can access other sites like Amazon or Yahoo. I can ping google by name ([www.google.com](www.google.com)) but it's slow. 5 sequences took 30 seconds or so. Pinging google by IP was faster - 8 sequences in about 7 seconds. However, the time reported for each ping was about the same - 99 ms for either name or IP ping but longer delays between with name. I don't know if that's useful or not.

As for router filtering, under the security tab for firewall it says the firewall is enabled and the following options are checked: block anonymous internet requests, filter multicast, and filter IDENT (port 113). Disabling the firewall doesn't speed things up and neither does unchecking the options.

So, in short, it's working but quite slow. Something is still odd. We are making progress, though.

Thanks again for the help.

---

### Post by bscbrit on 2006-02-08
This now sounds like a DNS or IPV6 problem.  What DNS settings have you got on your windows machine?  What is in /etc/resolv.conf on your Ubuntu machine?  As I said in post #2 in this thread, you should have changed your DNS when you changed to your new ISP.  Check that you have done so on the Ubuntu machine.  However, if you ping your windows machine from the laptop using numbers i.e. ping 192.168.1.100, there shouldn't be any delay - because DNS is not required.  Try it please and let me know what happens. (You have already confirmed this by your previous attempts at pinging [www.google.com](www.google.com) by name and by number, but I am just making sure that I am not confusing myself again! :-D )

The following link is about troubleshooting wired networks [;) ] - see near the end for how to disable IPV6 : [http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

---

### Post by bscbrit on 2006-02-08
[http://www.ubuntuforums.org/showthread.php?t=78337&page=2](http://www.ubuntuforums.org/showthread.php?t=78337&page=2)

See this thread,  Option 1 first, and if it doesn't help, we will do Option 3 next. :D

---

### Post by m.musashi on 2006-02-08
Thanks again for the help. It is greatly appreciated. Just make sure you get some sleep. From the timing of your posts I'm not sure where you find time.

I'm at work right now so I'll have to wait until I'm home to try most of your suggestions. However, here is some info.

My /etc/resolv.conf file has just two items:
```
search wsd.k12.co.us
nameserver 172.31.1.26
```
This relates to my network at work which is where the laptop is connected at the moment. Will this change when I connect to a different network?

Since a laptop moves around, do these entries change depending on what network you connect to? I wouldn't want to set this up so that it works at home but nowhere else.

Following your links, one of them talks about setting up DNS servers via system -> administration -> networking. When I click the DNS tab I find the same info as above (172.31.1.26 and wsd.k12.co.us). I assume that from home this would change and need to reflect my ISP.

Last night I was not able to ping the desktop from the Ubuntu laptop but I could ping the laptop from the desktop. In both cases using an IP address.

I will check all this when I get home and see if it changes.

When booting, I am not using the ctrl-c option when setting up networking hangs. It waits about a minute or so before continuing on. I don't know if it is just timing out or if it is actually doing something. This doesn't change from location to location. It's slow at work where everything works fine and slow at home where it doesn't.

Thanks again.

---

### Post by bscbrit on 2006-02-08
One of the functions of NetworkManager is to handle all the connection issues when you move a laptop from location to location.  It does this by taking control of the network configuration and DNS settings.  However, it can also interfere with your desired settings, particularly when you are trying to debug a network connection.  It makes changes without informing you and thus values that you believe to be set are changed.  NetworkManager has a definite place and role, but it does not help troubleshooting, hence we made sure that it was removed.  

It is quite likely that your DNS settings will have to change between your work and your home networks but it isnot  absolutely certain that this will be the case.  You will have to configure these changes manually if they are required - or use something like NetworkManager to do the job for you.  There are ways of semi-automating the manual case using scripts but we will look at those once we have a working network.

Let me know when you have tried the various options to prevent IPV6 from causing the problem.

---

### Post by bscbrit on 2006-02-08
Oh yes, sleep, I must do that sometime......:D

---

### Post by m.musashi on 2006-02-08
I know all about getting stuck on a computer problem and staying up to wee hours working on it. Of course those were windows problems and I didn't have a great support forum. Actually, how do windows users get help?

Anyway, I digress. We have acheived success. It turns out it was a DNS problem. My router did not pick up the new DNS addresses from the new ISP. I ended up calling them for the numbers and changed them manually. I also made some of the changes recommended above so I can't be sure if it was one or all of them but anyway, it is working. Thank you so much for the help. I never would have figured this out. I'm also a bit wiser and that is a good thing too.

Now comes the problem of wireless. I have not had major problems with wireless before but everything seems to have broke when I switched ISP and removed nm-applet. Although my wired conection now seems to be working. I cannot switch to wireless without rebooting. After reboot it does seem to work. This was one reason I had installed network-manager. Without it, I had to go into the networking applet and manually deactivate and reactivate eth1 (wireless) before it would be recognized. That is still a problem except now I have to actually reboot the computer for it to work. I cannot just switch - even manually. If I switch back to eth0 then nothing works. If I then switch back to eth1 it also no longer works and I have to reboot.

Obviously not an ideal situation.

Do I want to reinstall network-manager now that it is sort of working or do I still have problems to work out first? I didn't really like nm. It would always try to connect to my neighbor's router rather than mine (I have a hidden essid). It also often crashed and wouldn't do anything and I was forced to reboot to get a connection. At other times it just wouldn't connect even though everything was set up the same way it had been before.

Also, there is still the problem of the long wait during boot up. When it gets to "setting up networking" it still hangs for a minute or so. I don't think it's doing anything and it slows down the boot process quite a bit.

I guess I still don't have all the kinks worked out.

Thanks again. Your help has been invaluable.

---

### Post by m.musashi on 2006-02-08
D*** I spoke too soon. I leave my computer (off) and come back a couple hours later and it's back to square one. No network.

I had switched to wireless (eth1) to see if it would work. It didn't until I rebooted. Then I tried to switch back to wired (eth0). It didn't work either until I rebooted. When I shut down I was on eth1 with a non-working network (didn't reboot I guess) and the wire was plugged in. When I restarted I was still on eth1 with the wired connection plugged in and nada. I tried putting everything back (eth0 selected and wired) and rebooting. Nada. I don't get it. What is going on.

On the plus side, all the surfing the forums had taught me a lot. I now have a cool new GDM, splash screen, desktop theme and icons. All improvements that will greatly improve my productivity and allow me to make up for the time I've spent making the changes :). And it looks cool too.

---

### Post by m.musashi on 2006-02-09
Okay. I went back through everything. Made the IVP6 changes as per your links. Rebooted. Nada. Made the option 1 changes. Rebooted. Nada. Made the option 3 changes. Rebooted. I am now writing this from my ubuntu laptop. Seems to be working again. I have not tried to switch to wireless as the last time I did everything got fried. Will try when I have the nerve and things seem to be working well.

---

### Post by bscbrit on 2006-02-09
Can you identify what it is that is changing to make you computer unusable?  

When you next have a working system (now, hopefully) make a backup copy of /etc/network/interfaces and /etc/resolv.conf.  If it stops working again check the current versions of these files with your backup files to see what, if anything, is changing in them.  I do not know which program might change the settings, other than NetworkManager, but it might be useful to identify what it causing the problem rather than fix the results of the problem each time.

Try keeping a hand-written log of what you do and see if we can identify a pattern that is linked to your problem.  How old is the computer that is experiencing the problems?  Could it be something trivial (at least trivial in network configuration terms!) like a failing component?

---

### Post by m.musashi on 2006-02-09
I tried to be very methodical but in my zeal I kind of lost it. The first time I got things to work I had set up the correct DNS addresses. However, when I switched to see if wireless was also working things got kind of broke. I started over and went through the various steps outlined in the links you gave. After each step I tested and if I didn't work I went to the next. I did not undo what I did but just added the next possible fix. In the end, it was the option 3 from one of the links that involved commenting out a bunch of lines. After a reboot everthing worked wired. I did not try and switch to wireless.

It's odd that I needed to make all these changes. Prior to the ISP switch everything was working fine. Once I got the correct DNS set up I would have thought that would have fixed it. 

Boot is still hanging at the network config though. I assume that means there are still issues.

The /etc/resolv.conf file has not changed. Even though I'm at work and yesterday the addresses were my work network. When I when home I set up DNS with my home ISP DNS. Now back at work it did not switch back to the work addresses. However, I have a network connection.

/etc/network/interfaces does not seem to be changing but I'll make a copy and compare. The one thing that does change is my wireless essid. It reflects the last wireless network I was on or attempted to use (school, hotspot or home).

Personally, I think the whole networking issue in ubuntu is not yet perfected. Even though I have eth1 (wireless) active and with the correct essid, I cannot click on the network icon on the top panel and then choose eth1. It doesn't show up. I have to click configure and then deactivate and reactivate it before it will show up.

Even though it kind of works, I would like to have a trouble free set up. If you have any more ideas please share them. In any case. Thank you so much for sticking with me through this.

---

### Post by bscbrit on 2006-02-09
You're welcome.

At what point exactly in the boot sequence does the hangup occur?  Are you sure that it is at the network configuration or could it be when ntp runs?  Without a network connection, ntp hangs around quite a while before continuing.

What other networking issues remain that you would like some help with?

---

### Post by m.musashi on 2006-02-09
I'd still like to get wireless working too. It will not switch from wired to wireless. Even after restarting it won't. In fact, everything just broke again. No network wired or wireless. The resolv.conf and /network/interfaces did not change.

Everything worked last night wired. I went to work today and it connected right up. I came back home and it connected. Seemed to be working fine. I tried to switch to eth1 (wireless) but it was not an option. I had to open network manager and deactivate eth1 and then reactive it. After that it was available in "connection Properties" (the icon on the top panel that looks like two TV). I chose it and there was no conncection. I rebooted and there was no connection. I switched back to eth0 and no connection. I rebooted and no connection.

Wireless worked before and I didn't have to use ndswrapper (or something like that). About the hardware, it's a 6 month old Dell Inspiron 600m. It's never had hardware problems.

This is getting frustrating. I'm thinking of just reinstalling from scratch. Who knows if I goofed something up. It still works fine in Windows. Very frustrating when I'm trying to move away from Windows and it's the only thing that works. It even worked when my router had the wrong DNS addresses.

Well, good bye to all my nice new eyecandy.

---

### Post by bscbrit on 2006-02-09
The choice of whether to re-install is yours - I hate to give up on a problem but you will want a working system and a re-install might be the quickest option. :D 

Its too late tonight to get much done but I should be here tomorrow and most of the weekend, if you want to give it a try its OK by me.

---

### Post by m.musashi on 2006-02-10
I hate to give up too. I don't learn anything - except how to install :).

However, it is frustrating. I have it working again (wired). It is slow to respond like before but works. It is not consistent. I'm starting to think it is my router. I pluged straight into the DSL modem, rebooted, and it seemed to be working fine but with a short 5 to 10 seconds before it pulls up a site (a delay I don't have in Windows). I have gone through and totally reset the modem and router. Still acts goofy. I reconnected to the router and at first it didn't work at all. Firefox waited about 2 minutes or so and then said can't find Google. I closed firefox a bit later and opened it and after a few seconds it pulls up google. I also have some the weather applets and they updated. Some quickly, some after a 2 minute or so delay (I clicked update). When connected to the modem directly the weather applets update almost immediately after boot even though firefox has that delay.

There have been no changes to resolv.conf or network/interfaces either by me or "automatically". I don't get it. It's like a car that only makes the weird noise when the mechanic isn't around

With respect to the boot problem, it hangs right after "setting up ALSA card 0". That says OK and then "configuring network interfaces" hangs. I removed the npt option a while back (even when things were working well) becuase even then it wouldn't connect during boot. The hanging has been a problem since I installed.

I just reconnected back to the router and once again things aren't working. Firefox sits there spinning but no response and then the server not found error. Just moments ago I had a more or less normal connection when directly connected to the modem. This certainly sound like a router problem but I understand why. It works fine in windows. Does ubuntu need any special setting for a router? Actually, since it worked before that answer should be no.

Well, I need to sleep now. I'll check back tomorrow. Let me know if all of this troubleshooting leads you in a new dirrection.

Thanks again.

---

### Post by m.musashi on 2006-02-10
Okay, I just tried one more thing on a whim. Using system -> admin -> networking I deactivated both eth0 and eth1 and rebooted. When I logged in my weather applets all updated almost immediately and when I opened Firefox I had a network connection with no real delay. eth0 reactivated itself. I didn't do anything. Although it does say something about auto eth0 and auto eth1 in networking/interfaces. Perhaps that's what it means. I don't know why that should have made things suddenly work but it did. eth1 (wireless) is still deactivated. It did not come up even though my wireless card is active and there is an active wireless network.

I activate eth1 and switch to it. Nothing works. I switch back to eth0 and now it no longer works. I deactive both again and reboot. My weather applet tells me it's 23F and cloudy (actually it's snowing - much not be very accurate) and internet works fine again.

Go figure. I guess if I don't want to use wireless anymore I'm set.

---

### Post by DravenHavok on 2006-02-10
I think I have a similar problem, I just had to reset my router (DSL modem) because I changed the password from my ISP, and the internet connections stopped working. I called tech support and they told me to how to reset the router, but I was only able to do it from my windows computer. I have two computer connected to the router, my linux (through Ethernet), and a windows (through USB). And the windows works now, but my linux doesn't. I figured I had to somehow make the linux recognize new new router. But I do not know how. I don't mean the IP for the router, I tried setting that on the networking properties of eth0. Any idea on how I can make it work? Thanks a lot.

---

### Post by mips on 2006-02-10
Gents,

Something funny here. On the first page of the thread there is the output of linux ifconfig -a   and windows ipconfig for the wired interface. The address ranges do not correspond at all ?

m.musashi,

Could I suggest you post the following info here:
Windows-
ipconfig /all

Linux-
ifconfig -a
route -n
cat /etc/network/interfaces
cat /etc/resolv.conf

Please distinguish between the wired and wireless interfaces.

While you are at it you might as well list your router brand/model, dsl modem brand/model and ISP.

---

### Post by bscbrit on 2006-02-10
mips - I'm glad that you have popped up on this one!  I'll confess to being a bit confused because I cannot spot any rhyme or reason behind the symptoms that are being reported. Even more frustrating (!) is that sometimes it appears to work again and I think we are getting somewhere and then it stops again.

I'm watching this one with great interest.

bscbrit

---

### Post by mips on 2006-02-10
[QUOTE=bscbrit]mips - I'm glad that you have popped up on this one!  I'll confess to being a bit confused because I cannot spot any rhyme or reason behind the symptoms that are being reported. Even more frustrating (!) is that sometimes it appears to work again and I think we are getting somewhere and then it stops again.

I'm watching this one with great interest.

bscbrit[/QUOTE]

No probs, you doing fine so far ;) Lets wait and have a look at the info to be posted.

---

### Post by m.musashi on 2006-02-10
Thanks for taking an interest in my problem. I was afraid that with it acting so weird people would just say I'm crazy. I'm not. I may be a relative newbie but I've been around computers for a good 15 years.

However, I'm still a Linux and networking newbie and that has contributed to some confusion. Sorry.

The ubuntu ifconfig posted in post #1 was generated while connected at work. The IP addresses are relative to my work network and therefore not real helpful as I can now see (I'm learning a lot with this). The windows output results from running ipconfig were from my home desktop and those IP addresses relate to my home network - specifically my router.

192.168.1.100 is the IP address that was assigned to my desktop by the router.

192.168.1.1 is the IP address of the router (i.e. that is the IP address I type to access the router's settings). It is also the default gateway but I don't exactly know what that means.

The ping on 192.168.1.102 was from my desktop to my laptop. That IP address was also assigned by the router. As you can see that worked. What did not work was pinging the windows desktop from the ubuntu laptop.

I will post the requested data in a couple hours when I get home so as to not confuse the issue more.

Here are the hardware specs:

Router - [Linksys WRT54G](http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=c%3DL_Product_C2%26cid%3D1127782957298&pagename=Linksys%2FCommon%2FVisitorWrapper)

DSL Modem - [Actiontec](http://www.actiontec.com/products/broadband/usb_eth_rout_homedslii/index.php)  I'm not 100% sure this is the right one but based on the descripton it sounds like it. Actually, this one can connect two computer but the one I have can only connect one (or the router in my case). I can't seem to find the exact one on their web site.

ISP - [Quest DSL](http://www.qwest.com/residential/productsandservices/internet/index.html)

The modem is set up with DSCP and so is the router. I thought maybe both shouldn't be doing that so I turned of DHCP on the modem and then nothing worked. I was also wondering if PPPoA could be part of this problem. I don't really understand all this much but PPPoA is what my ISP uses. There is no PPPoA option on the router but I can choose between DHCP, PPPoE and some others. I don't know if that's useful but I'm trying to provide as much info as possible.

---

### Post by mips on 2006-02-10
The mentioning of the word Actiontec sent shivers down my spine. Check the bottom of the Actiontec Unit for the Model number.

Going to bed now but will respond in the morning, way to tired, went to bed when the birds woke up this yesterday morning...

Before I go though I have a question.

I assume the  physical setup looks like this:

PC---------\
.................Linksys-------Actiontec-----DSL-2-ISP
PC---------/ ..^
.................. /
................./
Wireless<---


Why does this forum remove the spaces ?! :confused:  Gotto use ... instead of space.

---

### Post by m.musashi on 2006-02-10
[QUOTE=mips]The mentioning of the word Actiontec sent shivers down my spine. Check the bottom of the Actiontec Unit for the Model number.[/QUOTE]

That doesn't sound good :cry: It's model GT701R. I didn't have a choice. It came free with the service. I guess you get what you pay for.

Your graphic is an accurate depiction of my setup.

Here is the output from the tests you requested.

Linux ```
jim@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:12:3F:FA:01:DB
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:755 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1450 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:530555 (518.1 KiB)  TX bytes:128361 (125.3 KiB)
          Interrupt:11

eth1      Link encap:Ethernet  HWaddr 00:13:CE:3F:E8:8A
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:53 errors:0 dropped:42 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0xc000 Memory:faffd000-faffdfff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2292 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:180025 (175.8 KiB)  TX bytes:180025 (175.8 KiB)
```

```
jim@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

```
jim@ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

iface eth1 inet dhcp
wireless-essid sircrapsalot2209



iface eth0 inet dhcp
```

```
jim@ubuntu:~$ cat /etc/resolv.conf
search domain.actdsltmp
nameserver 205.171.3.65
nameserver 205.171.2.65
```

Windows
```
Microsoft Windows [Version 5.2.3790]
(C) Copyright 1985-2003 Microsoft Corp.

C:\Documents and Settings\Jim>ipconfig /all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : number6
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Unknown
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : domain.actdsltmp

Ethernet adapter Local Area Connection 2:

   Connection-specific DNS Suffix  . : domain.actdsltmp
   Description . . . . . . . . . . . : NVIDIA nForce Networking Controller #2
   Physical Address. . . . . . . . . : 00-15-F2-04-0A-96
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   IP Address. . . . . . . . . . . . : 192.168.1.101
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.1.1
   DHCP Server . . . . . . . . . . . : 192.168.1.1
   DNS Servers . . . . . . . . . . . : 205.171.3.65
                                       205.171.2.65
                                       192.168.0.1
   Lease Obtained. . . . . . . . . . : Friday, February 10, 2006 5:16:24 PM
   Lease Expires . . . . . . . . . . : Saturday, February 11, 2006 5:16:24 PM

C:\Documents and Settings\Jim>
```

Nothing is currently connected via wireless but for clarity eth0 on ubuntu laptop is wired, eth1 is wireless. The windows desktop (would be ubuntu too if I could get it to install :)) is only wired.

[QUOTE=mips]Why does this forum remove the spaces ?!  Gotto use ... instead of space.[/quote]
Since you all have been so helpful, perhaps I can answer this (or was it rhetorical?). Spaces are not recognized in html (beyond 1) and that may be the case in VB too. As for preserving spaces, the "code" comand seems to preserve all original formatting.

Seeing how you know a heck of a lot more than me that probably wasn't very helpful. Just trying to give something back if I can. Helpful people like you two are too cool and much appreciated.

---

### Post by bscbrit on 2006-02-11
Good morning - or at least it is here....!:-D 

Firstly, I don't think that your network cards are set to be automatically configured at boot up.  There is no 'auto eth0' or 'auto eth1' in your /etc/network/interfaces file.  That would explain why they have to be manually configured.  Not quite sure how they function when you are at work then.......:-k 

On your home network, what serves the DHCP addresses?  Ah - spotted it, the router is set up according to the windows machine.  What range of addresses is it set to issue?

I'm not sure of the significance of the 'Actiontec' router - it is not one that I am familiar with.  But from the advertising blurb I found this:

> What wireless cards will work in my Actiontec Wireless-Ready DSL Gateway?
The Actiontec Wireless-Ready DSL Gateway will only work with Actiontec 802.11b wireless cards numbers 802CI2 and 802CI3.  I'm surprised that they say it will only work with specific wifi cards but that might just be a marketing ploy.  If it isn't, it suggests that there is something non-standard with the way it works but that is not your immediate problem.

Reading further, I then found this:

> 
What is the valid IP range I can use for my home network?
The valid IP range for the Actiontec Wireless-Ready DSL Gateway is 192.168.0.2 to 192.168.0.254 by default. 

That range of addresses does not tie in with the ones that you printed in your post.  Have you reconfigured your Actiontec and, if so, what to?

I suspect that mips will also spot some things that I have missed. :-D

---

### Post by bscbrit on 2006-02-11
Just doing my homework on ActionTec.  It seems that others on this forum are also experiencing unusual problems - [http://ubuntuforums.org/showthread.php?t=128219](http://ubuntuforums.org/showthread.php?t=128219)
Ah well, lets see if Google has any answers.

---

### Post by mips on 2006-02-11
[QUOTE=m.musashi]
Since you all have been so helpful, perhaps I can answer this (or was it rhetorical?). Spaces are not recognized in html (beyond 1) and that may be the case in VB too. As for preserving spaces, the "code" comand seems to preserve all original formatting.

Seeing how you know a heck of a lot more than me that probably wasn't very helpful. Just trying to give something back if I can. Helpful people like you two are too cool and much appreciated.[/QUOTE]

Thanks, that indeed was very helpfull as I have'nt a clue about html & vb.

How would I use the code command in my posts to preserve spaces ?
Sorry to hijack your thread  :p

---

### Post by mips on 2006-02-11
[QUOTE=bscbrit] That range of addresses does not tie in with the ones that you printed in your post.[/QUOTE] 

Keep in mind that he has a Linksys LAN router behind the Actiontec so the addresses will/have to differ as both devices cant be in the same network. The Linksys 'WAN' port will have a 192.168.0.x address and it assigns addresses via dhcp in the 192.168.1.x range

Busy writing up a little procedure/guide and will post it shortly.

---

### Post by bscbrit on 2006-02-11
Thanks mips - I obviously haven't woken up properly!

---

### Post by m.musashi on 2006-02-11
[QUOTE=mips]Thanks, that indeed was very helpfull as I have'nt a clue about html & vb.

How would I use the code command in my posts to preserve spaces ?
Sorry to hijack your thread  :p[/QUOTE]

Wow:o. I was helpful? Maybe there is hope for me yet. [this](http://www.ubuntuforums.org/misc.php?do=bbcode) page gives some basic info on using various codes in your posts. I'm just learning about them myself. For example, I found out how to use a hyperlink for a url rather than pasting the whole thing.

I'm on my way out the door right now but I'll respond to some of the questions and comments latter today.

Don't worry, it's not a hijack. It's an asside. Besides, it's fun to be helpful rather than just helped.

Thanks.

---

### Post by m.musashi on 2006-02-11
[QUOTE=bscbrit]Good morning - or at least it is here....!:-D 

Firstly, I don't think that your network cards are set to be automatically configured at boot up.  There is no 'auto eth0' or 'auto eth1' in your /etc/network/interfaces file.  That would explain why they have to be manually configured.  Not quite sure how they function when you are at work then.......:-k[/QUOTE]

If you refer back to post #2 you find the following in the /etc/network/interfaces file:

```
iface eth1 inet dhcp
wireless-essid tsunami

auto eth1

iface eth0 inet dhcp

auto eth0
```

So originally they were being automatically configured. I think that must have changed when I deactivated eth0 and eth1 and rebooted. However, it's interesting that with those lines missing (and I didn't even notice it - thanks) it does auto up eth0 anyway and gives me a normal connection. I am wired at boot so maybe that has something to do with it. In fact, the hang on boot seems to be gone now. I don't know way that little change (deactivating eth0 and eth1 and rebooting) would have these effects though.

What is still goofy is if I go into networking and activate eth1, even if that is the only thing I do, then the whole network stops working. Even I go back and deactivate it, it stays not working until I reboot. That seems significant somehow.

Okay, now I'm off.

---

### Post by mips on 2006-02-11
1. Update the firmware on your Actiontec & Linkys to the latests versions. Seeing you got yours from Qwest you might have to ask them for a firmware image for the Actiontec.

2. Actiontec:
Disable the DHCP server.
Ensure the LAN side is fully configured
Address 192.168.0.1
Network 192.168.0.0
Gateway Point it to the WAN/Modem side, probably don't have to.
Broadcast 192.168.0.255
Netmask 255.255.255.0
DNS 205.171.3.65 205.171.2.65

3. Linksys:
Configure the WAN side(actiontec) with full details,
Address 192.168.0.2
Network 192.168.0.0
Gateway 192.168.0.1
Broadcast 192.168.0.255
Netmask 255.255.255.0
DNS 205.171.3.65 205.171.2.65 192.168.0.1

Configure the LAN(home network) side,
Address 192.168.1.1
Netmask 255.255.255.0
Network 192.168.1.0
Broadcast 192.168.1.255
Gateway 192.168.0.2
DNS 205.171.3.65 205.171.2.65 192.168.0.1



Lets try and disable dhcp on your pc for now, we can turn it back on later.
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

auto eth1
iface eth1 inet dhcp
wireless-essid sircrapsalot2209


auto eth0
iface eth0 inet static
	address 192.168.1.102
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255

```



Change your resolv.conf to;
```
search *your qwest.domain.here, I dunno what it is or leave it out for now.*
nameserver 205.171.3.65
nameserver 205.171.2.65
nameserver 192.168.0.1
nameserver 192.168.1.1
```

4. Disable IPv6 as per the link in this thread, edit  /etc/modprobe.d/aliases file

5. Not really applicable but keep in mind [http://www.linuxquestions.org/questions/showthread.php?t=244026](http://www.linuxquestions.org/questions/showthread.php?t=244026)

---

### Post by bscbrit on 2006-02-11
I suspect that, although you are ifdown eth0 and ifup eth1, for example, the rest of the computer is still trying to access the previous interface.  However, I am not sure how you would tell your computer to change from one to the other for accessing the outside world.  The gateway that you have specified is common to both.

I have experimented this afternoon with a similar configuration and I cannot get it to change cleanly from one to the other either, although it does seem to sort itself out after a while.  Is there any particular reason why you would want to switch from a working interface device to another on the same machine?  What will you gain by doing so?  Basically, if your ubuntu desktop and windows machine both work wired, and your laptop (?) works on wifi then why change?  (I am assuming that this is your setup based on the diagram that mips provided and which you said was OK, although you didn't specify which machine in on the end of each link - or if you did I must have missed it again!) Or you have one computer that has both wired and wifi and you just want to be able to switch between the two - hence my question why would you want to?

Anyway, mips has now posted a guide on how to get a working network so give that a try and we will see where we get to.

---

### Post by mips on 2006-02-11
If you are going to switch between working networks then you will have hiccups. There is a utility out there that allows you to switch networks but I cannot remember what it is called. Mostly used with laptops, people switching between different wireless networks or between wired & wireless.

I'm to lazy to search now but it is a very common utility.

---

### Post by m.musashi on 2006-02-11
NetworkManager might be the app you are thinking of. I had it installed but it was more trouble than it was worth.

My laptop is a dual boot with ubuntu and windows. I use it wirelessly most of the time but sometimes when I using my desktop (windows only until I can get ubuntu to play with my mobo) I use both - often when troubl shooting so I can read info on one and work on the other. When I do this I usually plug in but I guess there is no reason too. I guess partly for security reasons but most of the time I'm not doing anything sensitive. The other part is that I only have a wired network at work so I have to switch to eth0 when at work. My school and home have wireless so as I move around I still need to switch back and forth.

I don't mean to beat a dead horse but all of this is not a problem in Windows. I have faith ubuntu will get there but in the meantime a working and not too cumbersome set up would be nice.

Mips, a question or two before I go through and make the suggested changes:

1. You suggest to disable DHCP on the Actiontec modem. I did do this while looking for a solution and when I did the router was not able to see the modem and everything stopped working. When you say "Ensure the LAN side is fully configured" I assume that is supposed to overcome that problem. Is that the case?

2. Are we essentially setting up a non-DHCP or static IP router? On the setup page for the router I have the choice between DHCP, static, PPPoE and a couple others I've never heard of. If we are doing a static set up should I then set this to static?

3. When you mentioned on the linksys to set up the WAN and LAN sides, I don't really see that option - at least not in those terms. I guess that's not really a question. I'm just not sure what to do there.

4. If I set eth0 to static, will that preclude me from connecting at work?

Okay, I guess that was more than two :). I guess I'm hesitant to make those changes when it works wired - suggesting the router and modem are set up correctly - or at least correct enough to work. The problem seems to be when aticivating eth1 (wireless) on the laptop. That's when I lose conectivity and that is starting to sound like an ubuntu problem to me.

Before I try this I'm going to try another experiment. I have a somewhat older laptop that is currently running Suse. I don't really like Suse as much so I'm going to install ubuntu on it. If I end up with the same problems that might indicate that it really is a router/modem problem. If that one works just fine then maybe it's a problem with the setup on my current ubunut laptop.

---

### Post by bscbrit on 2006-02-12
No, you are quite right to expect the computer to do what you want - I just wasn't quite sure of what the desired outcome was intended to accomplish.  I suspect that you _will_ require DHCP at work but I think mips' strategy is to get a working system and then reactivate DHCP later in order to identify precisely what is causing the current problem and, if possible, correct it.  If everything is given static addresses then the problem of the router not being able to see the modem should not occur - or at least, if it does, then we are homing in on part of the problem.

Let us know how your experiment works out.  

NetworkManager is indeed the program that mips was refering to but it will always favour a wireless network over a wired if both are available.  It is not mature software but can work well and there are many who swear by it.  I, on the other hand, ended up swearing at it because it would not accept my wired network but preferred to try to communicate with a neighbour's network which it couldn't do properly because of encryption. YMMV.

---

### Post by m.musashi on 2006-02-12
Okay, here are the results of my experiment. I now have another laptop set up with ubuntu. I set up wireless during the install and I'm writing this from that laptop.  I did not make any changes to the network hardware yet (router or modem) except to update the modem firmware. Note to self - do not update the firmware on the actiontec modem. It took me a couple hours and two useless phonecalls to tech support to get it running again.

So here are the stats:
Ubuntu laptop #1 works with wired network
Ubuntu laptop #2 (ex suse) works with wireless network
If either is switched from eth0 or eth1 to the other then the whole thing breaks and a reboot is all that will get networking up again.

Here is some network details
```
jim@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
jim@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0E:35:B3:37:18
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:feb3:3718/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4626 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3346 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4836263 (4.6 MiB)  TX bytes:427125 (417.1 KiB)
          Interrupt:5 Base address:0x4000 Memory:fcffe000-fcffefff

eth1      Link encap:Ethernet  HWaddr 00:11:43:3C:67:06
          inet6 addr: fe80::211:43ff:fe3c:6706/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10018 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10018 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:766622 (748.6 KiB)  TX bytes:766622 (748.6 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

I assume that sit0 has something to do with IPv6 that we disabled on the other laptop.

So, given all this, do you recommend that I go ahead and make the changes suggested by mips or is this as good as it gets right now and we call it fixed?

I do find it odd that prior to my ISP switch there were no problems going from wireless to wired, etc. I did have NetworkManager installed then, however, so maybe it was making things work that won't now.

In any case, thanks for all the advice and help. It's a bit late and I'm off to bed.

---

### Post by mips on 2006-02-12
Wait, don't make any changes yet.

So this only happens when you switch between wired & wireless ???

When you switch I assume you get allocated and IP address in the same 192.168.1.xxx range ???

---

### Post by mips on 2006-02-12
[QUOTE=bscbrit]I suspect that you _will_ require DHCP at work but I think mips' strategy is to get a working system and then reactivate DHCP later in order to identify precisely what is causing the current problem and, if possible, correct it.[/QUOTE]

Yip, that's the idea. 
Kinda follow the Sherlock Holmes approach, &#8220;Once you eliminate the impossible, whatever remains, no matter how improbable, must be the truth.&#8221; ;)

---

### Post by m.musashi on 2006-02-12
[QUOTE=mips]Wait, don't make any changes yet.

So this only happens when you switch between wired & wireless ???

When you switch I assume you get allocated and IP address in the same 192.168.1.xxx range ???[/QUOTE]

Okay, I'll hold off.

This is getting to be a rather long thread. As such, and because some of the changes suggested were successful in one way or another, the problem now is not exactly as the original.

Originally, I had no connectivity at all. Following the tips and hints given I was able to get a working connection - but it's not entirely flawless.

As the original problem affected both wired and wireless we were focusing only on wired to start with.

What I have now is a working wired connection. Even the hang on boot at "configuring network interfaces" is gone. It does pause for 5-10 seconds on "waiting for network to come up" but there is no real problem.

What is a problem is if I try and switch to wireless. In order for wired to work, eth1 (wireless) has to be deactivated. If I activate it, it first takes about a minute to actually activate, the network settings interface hangs for another minute on close and then nothing works. In fact, I just tried again and now even after activating eth1 it is not an option in the connection properties dialog (i.e. it is not an option to choose from, just eth0 and lo). If I deactive eth0 and leave eth1 active I have nothing but loopback left.

On reboot with eth1 (wireless) activated and eht0 deativated the computer hangs on configuring network again and I have no connectivity. I deativate everthing and reboot. There is no hang. I activate wireless and there is a minute or so wait while it says activating and then another minute or two when I cleck ok to close the dialog box. I still don't have an eth1 to choose from, just loopback.

So I reboot again. This time with eth1 active. Once again, it hangs on boot. There is no connectivity. I deactivate wireless and activate wired and what do you know...connection.

I think the issue has something to do with wireless. I know that's a dicey issue in ubuntu but it has always worked before on this computer. I also have the other ubuntu laptop now and it is connecting via wireless just fine. Although it won't switch to wired.

---

### Post by bscbrit on 2006-02-12
Switching between wired and wireless is always problematic, as was mentioned a few posts back.  That is why NetworkManager (NM) was written; to assist with the process of switching between the two and between wireless networks when on the move.  _But_ it will _always_ use a wireless connection in preference to a wired connection if one is available.  That didn't fit in with my system so I removed it.

To cope with the changes associated with a move from network to network, NM also has to take control of your /etc/resolv.conf and other files to ensure that whatever network is connected can access other machines on the local network and beyond.  _If_ that is what you wish to achieve then you might need to consider re-installing NM now that we have the various network cards working.  There isn't (as far I as can find out - and our efforts here seem to be supporting such findings) an easy way of switching between wired and wireless connections _on the same network_ because why would anyone want to?  I also raised this question some posts back.  

The simple way of doing things (at least I think it is both simple and sensible :D ) is to have a wired network at home but have your mobile computer set up for wireless - but not wired.  It will then be able to move between wireless networks fairly easily but your home network should be relatively trouble free.

You are still experiencing problems with the installation.  Your configuration shouldn't be losing settings when you reboot even if those settings are unworkable.  So I think there is still an issue or two to resolve in this thread if you (and mips!) are content to continue, but you will also need a clear objective in mind so that the thread doesn't sort of meander from one problem to another.  I personally think that each thread should address one specific problem or family of related problems.

Imagine how little I would learn if I still used Windows everyday....  The corollary is, of course, that while I am learning it is at the expense of your network!

Where we go next is most definitely your call.

---

### Post by WildTangent on 2006-02-12
Don't have time to read the whole thread...but did you try configuring your router to use PPPoE to connect to your new ISP?

-Wild

---

### Post by m.musashi on 2006-02-13
I guess it would be best if I could get wireless working at home. I have not been to any other wireless spots since many of the changes were made so that would be a good test to see if it's the computer or the network. However, since the other laptop I just set up works with wireless on my home network, I'm inclined to think it's the computer.

So, for a clear objective, and if everyone is willing to continue to try and sort this out, I'd say focus on the wireless problem. Do you think reinstalling NetworkManager is a possible solution or should we examine the config files and see if there is an identifiable problem?

Thanks again for all the help. I don't mind anyone learning at my expense. In fact, I kind of felt I was learning at your expense. After all, you are spending a fair amount of your time on my problem. If you can gain something from that then all the better.

[QUOTE=WildTangent]Don't have time to read the whole thread...but did you try configuring your router to use PPPoE to connect to your new ISP?[/QUOTE]

That was something I thought about but my ISP doesn't support PPPoE. I never got a clear answer from tech support about it but they just said "we don't support PPPoE'. Sometimes (most of the time?) tech support isn't very useful.

---

### Post by bscbrit on 2006-02-13
Are you now content that your wired network is reliable? Even after reboots?

---

### Post by m.musashi on 2006-02-13
Well, as long as I don't try to activate wireless (which is what I would like to do) then wired is working fine. I had it hooked up at home and then came to work and it worked fine on both networks. So in that sense I am content. However, since it breaks when I activate wireless if we can get wireless working again I'd be happier if it didn't break.

Let me know what sort of info you need to proceed and I'll do my best to provide it.

One thing I haven't tried is undoing the changes we made earlier to see if there is a point where things work better on both wired and wireless. Of course, since those changes seemed to be what resulted in a working network (it was not working at all) that may not be useful.

One thought I had concerned the second laptop I set up. I selected the wireless network during install and it works fine wireless. It won't switch to wired. I'll play around a bit more with it but that was a fresh install and that, to me, suggests that it is at least somewhat ubuntu releated.

---

### Post by mips on 2006-02-14
Please follow the network-manager guide in the link below and use the packages listed on that page and not the ones from the repositories.

[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Multiple_Wireless_Profiles](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Multiple_Wireless_Profiles)

---

### Post by m.musashi on 2006-02-14
Just to clarify, is it the belief that my problems are related to a lack of native support for wireless switching?

The reason I ask is that when I first installed ubuntu these issues did not exist. I later added NM as I read somewhere that it helped switch between wired and wireless. What I discovered is that even with a wired connection it would try and connect wirelessly - usually to my neighbor's router.

It is not installed right now but the problem is that even just activating wireless (via system->admin->networking) it breaks my wired connection and eht1 (wireless) still doesn't show up as a connection choice.

If this is the type of problem that NM will address then I'll give it a shot. If it sounds like there might be more going wrong then I can try to address that too.

As always. Thanks again for the help.

---

### Post by mips on 2006-02-14
Yes, trying to switch between networks without hiccups.

Have you tried disconnecting the wired link by unplugging the cable or disabling the interface. Then enabling the wireless followed by a disconnect and then reconnect the wireless.

Would be interesting to see what happens, at your expense offcourse.

---

### Post by m.musashi on 2006-02-14
Okay, I'll give this a try when I get home.

When switching before, I left the wire plugged in and then activated eht1 and nothing worked. I seem to recall this not being an issue when I first set up ubuntu but I can't remember the order of everything.

As an asside... shouldn't switching be a simple issue? I realize that the new ISP could have caused some hicups but we solved those (I think). The switching seems to be ubuntu related. Even the new laptop I just set up has the same problem. Is updating to dapper a fix here? I understanding they are working to make ubuntu more laptop friendly. Perhaps I should wait for the official release but I "hear" flight 3 is quite stable.

As I mentioned in another post with a similar issue I am not too worried about breaking this system. Actually, it's already sort of broke and if it gets totally fried I can always reinstall.

---

### Post by m.musashi on 2006-02-14
[QUOTE=mips]Have you tried disconnecting the wired link by unplugging the cable or disabling the interface. Then enabling the wireless followed by a disconnect and then reconnect the wireless.[/QUOTE]

Okay, I gave this a shot. Deactivated wired on eth0 and unpluged. Activated wireless on eth1. Switched to eth1. Good signal strength -- no connection. Reboot. Computer hangs on network config. I let it time out and finish booting. Wireless connection is now working.

In short, a reboot is required to switch.

Now switch back to wired. Deactivate eth1. Notice that eth0 is already active after reboot even though it was deactivated before. However, not listed as an option to selected so deactivate and reactivate. Select eth0 -- yeah!!! Working connection.

So, it seems that switching to wireless is the problem. I'm off to install NM and see what happens.

Thanks.

---

### Post by m.musashi on 2006-02-14
Okay, that didn't work.

Network Manager installed via the link provided. Now nothing works. Network Manager will not actually run. When I try the termal just hangs - cursor blinks but nothing happens and I don't return to a prompt.

I also have no wired or wirelss conectivity. I'll try to uninstall and see if I can get back to square one.

EDIT: That was easy. Removed the three packages, deactivated wireless, and I'm back to a working wired connection. I really don't get it.

---

### Post by bscbrit on 2006-02-14
This seems to be a wireless problem, after all.

How is you Access Point set up. Are you using WEP (64/128), WAP ?

---

### Post by m.musashi on 2006-02-15
I agree. However, I'm not sure it's my AP since I can access it and the Internet from the second ubuntu laptop I just set up.

As for the AP, I used to have WAP set up but ubuntu wouldn't work with it so I downgraded to WEP and then took that off too so as to make it as simple as possible. I also used to have a hidden essid but I unhid it so now it's a very simple setup.

EDIT: Okay, I kind of got this working. I went back and looked at my /etc/network/interfaces and resolv.conf and noticed that they were not what they had been. The resolv.conf had only one line saying not to edit as network manager had set it up. I deleted that and added the DNS info from my ISP. I also edited /etc/network/interfaces with auto eth1 and took out auto eth0 on the assumption that I should just get this to work wirelessly and not worry too much about wired. I rebooted and wireless is working fine.

I'm not going to try and switch back to wired. I'm pretty sure it will break again. I think I'm going to limp along until Dapper and then upgrade. Perhaps everything will play more nicely then.

If anyone has more info or suggestions I'm happy to give it a shot. However, I think I have drunk enough from the cup of kindness and I don't want to infringe upon any more of your time. I really appreciate all the help and I've enjoyed working with you two. Thanks.

Well, one last requst...If you have any thoughts on why Network Manager did not work when I installed via the info in the sourceforge link let me know. Thanks again.

---

### Post by bscbrit on 2006-02-15
I wasn't suggesting that the fault lies in your AP, simply that without knowing the settings it is hard to try to identify what faults/problems might stop your network from behaving the way you want it to.

But you seem to have achieved what you wanted - so, good luck, and we will see you around the forums \\:D/

---

### Post by m.musashi on 2006-02-15
[QUOTE=bscbrit]you seem to have achieved what you wanted[/QUOTE]
Well, at least what I can settle for. What I really want is a bit more trouble free set up in ubuntu. I really like this distro and don't mind putting in the effort but I'd really like if certain things "just worked".

If you happen to have any thoughts on network manager please share.

Again, thank you so much for helping me get this to be functional again. I've also learned a lot. I linked someone having a very similar problem to this thread and it seemed to help them too so that is double cool.

Now if I could just get ubuntu to recognize my nvidia chipset....

---

