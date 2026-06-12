---
title: "Problems after switch from ATI catalyst to radeonhd, upgrading kernel"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by inovermyhead on 2009-11-02
I got no response to this after several days in the Mythbuntu forum so I thought I might try my luck here.  I hate to cross post but I couldn't figure out how to get it moved.

I've been struggling to get satisfactory performance from my Mythbuntu 9,04 system for months now. Among many challenges, I've never managed to get smooth playback on my 780G based board using the integrated ATI HD3200 GPU and an AMD 5050e CPU. I tried a series of Catalyst driver versions all the way up to 9.9 but never quite got there. I've wanted to try the open source drivers again and was waiting for the radeonhd driver to get to the point where it looked like it was worth giving it a go. The radeon driver that I installed initially from the release 9.04 CD was a disaster performance wise which is why I had abandoned it in favor of the Catalyst driver. That and the fact that I'm using HDMI digital audio output, and the radeonhd driver seemed to lag the radeon driver in terms of enhancements and fixes for quite some time. 

Last weekend I noticed the 1.3.0 version of radeonhd released in mid-September appeared to have everything I needed, potentially. I installed it using the instructions I found here:

[http://www.x.org/wiki/radeonhd:INSTALL]("http://www.x.org/wiki/radeonhd:INSTALL")

After reboot, things looked fairly promising to start with, much to my surprise. HDMI digital audio continued to work with no issues just as it had with the Catalyst drivers. ClearQAM SD channels played more smoothly than with the Catalyst drivers, although HD channels were much worse in that they basically played in slow motion and had my CPU maxed out, to the point where it barely responded to my remote. All the same, it was progress of a sort and I resolved to verify that I had correct optimal settings and try some other tweaks. First however, I decided to take a newly posted kernel update shown in update manager with security fixes. This was the 2.6.28-16-generic, and it replaced my 2.6.28-15-generic. 

This is where things slowly began to get ugly. When the box booted to the xfce4 desktop it took a lot longer than usual, and the desktop would flash several times before starting up mythfrontend automatically. Mythtv continued to work normally, but on exiting mythfrontend my desktop had only icons on it, no menu bar across the top of my screen like usual. I rebooted several times with the same result. The only way to get to commands from my desktop was to right-click on the desktop and use the drop down menus from there. I observed that initially while the desktop was starting up and apparently thrashing, flashing the screen, etc, the menu bar across the top would be there initially but after a few flashes would disappear leaving only the icons, then mythfrontend would eventually start automatically as usual. After several hours of googling(on another machine) I finally found a solution to this problem when I found a post somewhere where someone seemed to be experiencing something very similar. The recommendation was to delete the ~/.cache directory. I tried this and rebooted and it did the trick. My menu bar returned, and my startup was now much faster than it had been in a long time. I think this was because this process also cleared out some applications, like update manager and some Terminal windows which used to always start automatically on every boot even though I had tried everything I knew how to in "Session and Startup" to make them go away. It had been stuck that way for a long time, long before I upgraded to radeonhd or the new kernel, and I had given up on it eventually.

Thinking I was now back in business, I went to pull up firefox and realized that my wireless was no longer working. From the first day I installed 9.04 this is one thing that always just worked. A reboot didn't cure it either. No programs requiring network connection, like update manager, were working. The wireless adapter was recognized, and the NetworkManager process was running, but still nothing. So then I decided to start looking at logs. I ran Mythbuntu Log Grabber from the menu, and it showed an empty file. Weird. I then ran it manually from a Terminal window and got an error. I wondered about file and directory permissions but as far as I can tell they look fine. I then ran the Mythbuntu Log Grabber as super-user, and it worked. I didn't learn anything about what's going on from there, or in any of the logs in /var/log/. I did notice however that there were other log files empty and not getting filled. On the other hand most of the log files are are being filled as usual.

By the way, I tried loading the old 2.6.28-15 kernel via Grub, but the results are exactly the same. No network, and odd behavior w/respect to log files. I'm stumped. I've looked and looked and can't find any description of similar problems anywhere. The only things I did were the radeonhd driver update mentioned above, and I followed those instructions exactly, and then upgraded to the new kernel, and then lastly deleted the cache directory. I don't which of those got me into my current pickle. I do know that the network was still working after the radeonhd upgrade since I was able to upgrade the kernel through update manager afterwards. I also don't know at which step the log writing problem kicked in. Any suggestions on how I can troubleshoot either of these issues would be greatly appreciated.

 It appears after further and more cautious reading that perhaps instead of deleting the entire ~/.cache directory I should perhaps only have deleted the ~/.cache/sessions directory and that might have sufficed to cure the desktop problem I had. That may have been what led to my other problems.

---

### Post by inovermyhead on 2009-11-02
Can anyone suggest how I might at least begin troubleshooting this?

---

### Post by inovermyhead on 2009-11-03
I'm guessing it was stupidly wiping out my ~/.cache directory that got me into my current pickle, or more accurately made it worse.  As mentioned above, my problems started with xfce4 acting very strange which is what led me to deleting it, and it did seem to work, or improve things at least wrt xfce4.  On the other hand it may be that my problem with some log files not being written, and my network problems were already occurring even before I deleted ~/.cache but who knows.  I would love to find out what's stored in the various directories there and what I may need to re-initialize to get them back.
 
I did go back and select a couple earlier versions of kernel from the Grub menu, 2.6.28-15 and 2.6.28-13 with exactly the same results, so obviously the kernel itself isn't causing the problem.
 
 
Obviously my problems go beyond just the networking problems but I've decided to try and troubleshoot that first.  I just verified that my wireless adapter, wlan0 is being recognized and also that NetworkManager is starting up.  I also found that nm-applet is running once I added the Notification Area to my desktop.  Once I got that added, I had to manually tell it to connect to my wireless network and it did and shows a good signal.  
 
That's the good news, now for the bad.
1)  If I log out and back in, or reboot, the Notification Area goes away and I have to add it back all over again.
2)  After adding the Notification Area back, the nm-applet is already shown running, but it is not connecting to my wireless network until I once again tell it to do so manually.
3) Although everything indicates that I'm successfully connected to my wireless network and have a good signal, I still can't get to the internet successfully from Firefox or Update Manager, so there's still a piece missing.  Perhaps a DHCP problem?
 
Any thoughts on the next steps I should take in troubleshooting?  I've never had to mess around in this area at all since the wireless networking just worked from day 1 in true plug and play fashion so I never had to even think about it.

---

### Post by inovermyhead on 2009-11-04
Any suggestions on how I can get my Notification Area to stick or where to begin troubleshooting my lack of internet connectivity even though my wlan0 is successfully connecting.

---

### Post by inovermyhead on 2009-11-06
I'm still struggling to get my xfce4 environment, logging, and network connectivity back.  I read a few threads here and elsewhere about restoring the xfce4 environment from a gorked state.  I removed(and saved for what it's worth) my ~/.config/xfce4/panel directory and after reboot this restored my taskbar to an almost ideal state.  I say almost because there are still a number of anomalies(new ones) and I still don't have internet connectivity, or even connectivity to my Wireless AP.  When my desktop comes up I have the taskbar on the bottom of the screen and for 2 or 3 seconds I get a popup notification telling me to click on it to select a wireless network.  If I click on it, nothing happens.  The appearance of the popup though suggests that my panel must have a Notification Area and the nm-applet is running inside it.  However, neither is visible on the taskbar.  If I move my mouse from one end to the other there is no sign of it.  I can't add the Notification Area to the panel because it says it's already running, and I can't remove it and add it back because I can't select it since it isn't visible.  Arrggh!

There are some other oddities as well.  If I use the menus to log out or reboot this works fine and I get the same desktop and taskbar environment.  If however, I try to make any change to the taskbar panel, like change it's location on screen from the properties pulldown menu, the change takes effect, but upon exit from the properties window the taskbar panel goes away completely, as if I'd quit out of it somehow.  If I log out and back in or reboot it comes back as before.

In other strangeness, if I use the pulldown menu to log out or reboot it always works, but if I click the save session box first, the logout or reboot doesn't take effect, i.e. I'm left with my desktop and no logout or reboot occurs.  If I then try to do it again, I get a popup message saying that there was no reply from the session manager.  At that point I can no longer log out or reboot from the window system.  I have to open a terminal window and reboot from the command line.  Following reboot I'm back to where I started again.

Also, it would seem that removing ~/.cache should not yield catastrophic results after all so I'm not sure whether that had anything to do with my predicament.  I'm thinking that I was just unfortunate and ran into an esoteric bug somehow.

Still looking for any suggestions or guidance.

---

### Post by Tony Ricena on 2009-11-06
Thats very odd... I have an ATI Radeon HD 4650 on my PC and everything is working fine even using the Proprietary driver from ATI.  Have you tried doing a complete re-install and using a different filesystem?  I know I had problems at one point and I just reinstalled everything using ext4 Journal and everything worked fine.  Just a suggestion, I know its not the best answer but if you don't have much on the PC that is valuable it might be worth the time.

---

### Post by inovermyhead on 2009-11-06
Thanks.  I'm still hoping not to have to do anything as drastic as reinstalling.  Getting my system to the point I had it before all this weird stuff started happening wasn't exactly a picnic to begin with.  I'm willing to struggle to figure out what's going on for a bit longer, and perhaps even learn something in the process.  If I have to give up I'll probably install 9.10 from the edge.  At that point, if 9.04 was any indication, I'll start troubleshooting a fresh new set of problems ;)

---

### Post by inovermyhead on 2009-11-07
Bumping on the off chance of finding someone who knows the resolution to one or more of my issues, or some suggestions on troubleshooting.

---

