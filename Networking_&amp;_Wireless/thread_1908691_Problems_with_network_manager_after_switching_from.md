---
title: "Problems with network manager after switching from WiCD (no wireless or tray icon)"
date: 2012-01-13
forum: Networking &amp; Wireless
---

### Post by laurac1022 on 2012-01-13
Hi, I am pretty new to ubuntu and seem to have gotten myself into a bind.

I downloaded wicd to see if it would fix the issue I was having with the wireless connection being dropped when resuming from suspend...it did not.  Now I am trying to switch back to network manager and after installing it there is no tray icon and the wireless doesn't work.

Using ubuntu 11.04.  I am not familiar with linux so any help would be greatly appreciated.

---

### Post by 2F4U on 2012-01-14
Did you completely remove WICD? It most likely causes problems if you have both enabled.

---

### Post by varunendra on 2012-01-14
Hi,

First off, here's the link to your previous thread where you originally asked the question providing necessary details: [http://ubuntuforums.org/showthread.php?t=1906643](http://ubuntuforums.org/showthread.php?t=1906643)

Now, just to make sure wicd gets removed properly, and (hopefully) NM comes back to normal, please issue these commands one-by-one:
```
sudo apt-get purge wicd
sudo apt-get install --reinstall network-manager
sudo /etc/init.d/networking restart
```Once it gets back to normal, we can try resolving further issues you were having.

---

### Post by laurac1022 on 2012-01-14
hi,

thank you both for replying.  I am pretty sure I uninstalled wicd when I tried to reinstall network manager.

Output of the commands suggested:

```
laura@Satellite:~$ sudo apt-get purge wicd
[sudo] password for laura: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wicd is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

``````
laura@Satellite:~$ sudo apt-get install --reinstall network-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 4 not upgraded.
Need to get 498 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ natty/main network-manager amd64 0.8.4~git.20110319t175609.d14809b-0ubuntu3 [498 kB]
Fetched 498 kB in 2s (237 kB/s)           
(Reading database ... 168489 files and directories currently installed.)
Preparing to replace network-manager 0.8.4~git.20110319t175609.d14809b-0ubuntu3 (using .../network-manager_0.8.4~git.20110319t175609.d14809b-0ubuntu3_amd64.deb) ...
Unpacking replacement network-manager ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Setting up network-manager (0.8.4~git.20110319t175609.d14809b-0ubuntu3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

``````
laura@Satellite:~$ sudo /ect/init.d/networking restart
sudo: /ect/init.d/networking: command not found

```

---

### Post by varunendra on 2012-01-14
> **laurac1022 said:**
> [/CODE]```
laura@Satellite:~$ sudo /[COLOR=Red]**ect**[/COLOR]/init.d/networking restart
sudo: /ect/init.d/networking: command not found

```
Hi,
Sorry, it was a typo on my part. It should have been** /etc... **I have corrected that in my original post.

Anyway, a restart would also do what 'restart networking' can do. So do you have NM back now?

---

### Post by laurac1022 on 2012-01-14
there is still no tray icon....once again thank you
```
laura@Satellite:~$ sudo /etc/init.d/networking restart
[sudo] password for laura: 
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          ssh stop/waiting
ssh start/running, process 2340
ssh stop/waiting
ssh start/running, process 2444
                                                                         [ OK ]

```

---

### Post by varunendra on 2012-01-14
> **laurac1022 said:**
> there is still no tray icon
Please try this: press Alt+F2 > type nm-applet > press 'Enter'
Does this bring up the applet (tray icon)?

Also, please go to **/etc/xdg/autostart **directory and see if **nm-applet.desktop** file is there.

---

### Post by laurac1022 on 2012-01-14
that brought up the icon, however when you click on it, in the drop down menu is says 'device not managed' under wired network and wireless network.

nm-applet is in the autostart directory

thank you

---

### Post by varunendra on 2012-01-14
> **laurac1022 said:**
> that brought up the icon, however when you click on it, in the drop down menu is says 'device not managed' under wired network and wireless network.

nm-applet is in the autostart directory

thank you
You're welcome. However, I don't think I deserve so many 'thank-you's yet.. :D

Please open the file on gedit (you can do so by either drag and drop or by - **Alt+F2** > type **gedit /etc/xdg/autostart/nm-applet.desktop**) > scroll to the bottom and make sure the following line is set to 'true':
> X-GNOME-Autostart-enabled=true
If it is not, you can change it to true by opening it with 'gksu' (**Alt+F2** > **gksu gedit /etc/xdg/autostart/nm-applet.desktop**)

As for the 'Not managed problem', I'll need to do some digging since many things seem to have changed in 11.10. But right now I have to leave for dinner. Will be back, hopefully, in about half an hour or so with something that makes sense. Meanwhile, try 'Edit connections' and see if "Connect Automatically" is checked for the wifi.

---

### Post by varunendra on 2012-01-14
Ok, got it!

It was nothing new and I was just lost (probably I was too hungry to think straight ! :))

Please open your /etc/network/interfaces file (**Alt+F2** > **gksu gedit /etc/network/interfaces**) and make sure it contains only these two lines:
> auto lo
iface lo inet loopbackDelete all other lines (I'm sure there would be many, including your wifi interface name)

close the file, then open a terminal and run the following command:
```
sudo /etc/init.d/networking restart
```Post back how it goes.

---

### Post by laurac1022 on 2012-01-14
ok I opened the autostart file and the line you specified did read 'true' so I left the file alone.

I also edited /etc/network/interfaces so it only contains the loopback interface.

```
laura@Satellite:~$ sudo /etc/init.d/networking restart
[sudo] password for laura: 
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          
Ignoring unknown interface eth0=eth0.
Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]

```

---

### Post by varunendra on 2012-01-14
And..?

Is the NM applet there? Does it show wireless networks now? Any other significant details you think worth mentioning?

---

### Post by laurac1022 on 2012-01-14
sorry....initially nothing changed.  the applet was still showing from when I manually started it and the menu still read the same 'device not managed'. So I decided to see what would happen with a restart.  It shutdown fine then  when restarting the system froze at the post/bios screen.  Did a hard kill and then it booted up fine.  The applet did not start automatically but after I manually started it (<Alt+F2 >  nm-applet) it showed both networks...connected to both wired and wireless!!! 

I haven't unplugged to see if wireless works yet.  I wanted to make sure I could post my progress first.

I will post back with wireless status.

---

### Post by laurac1022 on 2012-01-14
Posting via wireless connection now!  

I think a thank you is deserved for that. :D

Any idea why the applet needs to be manually started?

---

### Post by varunendra on 2012-01-14
> **laurac1022 said:**
> Posting via wireless connection now!  

I think a thank you is deserved for that. :D
I think it is still too early for that (not that I want to scare you.. ;))

> **laurac1022 said:**
> Any idea why the applet needs to be manually started?Maybe a look at the contents of your /etc/xdg/autostart/nm-applet.desktop file can help answering that. Please post its contents.

In the meanwhile, you can try manually adding nm-applet to Startup Applications. To do so:
goto Dash > type Startup Applications > open it > click "Add" > browse to /usr/bin/nm-applet > click "Open" > give a relevant name and description (optional) > click "Add" > close and restart system to see if it takes effect.

---

### Post by laurac1022 on 2012-01-14
```
[Desktop Entry]
Name=Network Manager
Comment=Control your network connections
Icon=nm-device-wireless
Exec=nm-applet --sm-disable
Terminal=false
Type=Application
OnlyShowIn=GNOME;XFCE;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=general
X-GNOME-Autostart-enabled=true
X-Ubuntu-Gettext-Domain=nm-applet
```

---

### Post by varunendra on 2012-01-14
> **laurac1022 said:**
> ```

Exec=nm-applet [COLOR=Red]**--sm-disable**[/COLOR]
Terminal=false
Type=Application
OnlyShowIn=GNOME;XFCE;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=general
X-GNOME-Autostart-enabled=true
X-Ubuntu-Gettext-Domain=nm-applet
```
I suspect the part highlighted in bold red is the reason why it isn't executing nm-applet command.

Just delete it so it looks like:
> Exec=nm-applet
Terminal=false
Type=Application
OnlyShowIn=GNOME;XFCE;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=general
X-GNOME-Autostart-enabled=true
X-Ubuntu-Gettext-Domain=nm-applet
(You will have to open it with gksu to be able to edit it)

And.... I think that's enough from me for today (am feeling too sleepy to keep up!! :(). See you tomorrow!

---

### Post by laurac1022 on 2012-01-14
When I opened up startup applications there was still an entry for 'WiCD network manager' so I removed it and added entry for the path you specified.  When I restarted it brought up the applet and connected automatically.  

Also right before it shuts down it flashes a screen with script all over it.  It disappears before I can read anything.  not sure what thats about

---

### Post by laurac1022 on 2012-01-14
ok tomorrow then...thanks for your help.

---

### Post by varunendra on 2012-01-15
Okay, I'm back (and you're gone ;)).. So when you come back, I'd like to know if my last suggestion made any difference.

> **laurac1022 said:**
> ..Also right before it shuts down it flashes a screen with script all over it.  It disappears before I can read anything.  not sure what thats about
I've no idea about that either. But I believe it can't be anything related with our attempt to manually add nm-applet to autostart. Besides, you shouldn't need that manual entry after making the change in nm-applet.desktop file as suggested in post #17.

After it gets completely sorted, I think you should start a new thread for your ath5k driver problem (if it's still bothering you) which caused all this mess. Then post its link here so I can follow (I don't remember having sorted out any athxk problem ever, but I like to follow such threads in hope of learning something new..).

---

### Post by laurac1022 on 2012-01-15
Well good news is network manager starts automatically and the wireless was working flawlessly.....until woke it from suspend after having left it for awhile.  So I am now having to use the wired connection again.  Even restarting does not get the wireless to recognize network.

Thank you so much for your help.  I will start a new thread for this wireless issue and post link here.

---

### Post by varunendra on 2012-01-15
You're welcome!

Please share with us whether the changes in nm-applet.desktop file did any good or is it still the manual entry which runs nm-applet.

With that I think you should mark this thread as [Solved] now. I'll surely wait for the link to your new thread with the wifi problem (although may not reply there to see if an expert picks it up).

---

### Post by laurac1022 on 2012-01-15
Link to new thread:
[http://ubuntuforums.org/showthread.php?t=1909361](http://ubuntuforums.org/showthread.php?t=1909361)

How will I know which one is starting the applet?  As I both edited the file and manually added startup entry...not sure how to tell.

---

### Post by varunendra on 2012-01-15
> **laurac1022 said:**
> How will I know which one is starting the applet?  As I both edited the file and manually added startup entry...not sure how to tell.
Simply remove the manual entry from startup apps. If nm-applet fails to auto-load next time, we'll know the file edit didn't work (although I'm quite hopeful it should).

---

### Post by laurac1022 on 2012-01-15
Ok it was definitely the startup entry that is starting app.  I disabled it and restarted and no applet.  

current contents of /etc/xdg/autostart/nm-applet.desktop for reference:
```
[Desktop Entry]
Name=Network Manager
Comment=Control your network connections
Icon=nm-device-wireless
Exec=nm-applet
Terminal=false
Type=Application
OnlyShowIn=GNOME;XFCE;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=general
X-GNOME-Autostart-enabled=true
X-Ubuntu-Gettext-Domain=nm-applet
```

---

### Post by varunendra on 2012-01-15
And what if you further edit it so that it looks like:
> [Desktop Entry]
Name=Network Manager
Comment=Control your network connections
Icon=nm-device-wireless
Exec=nm-applet
Terminal=false
Type=Application
**[COLOR=Red]# [/COLOR]OnlyShowIn=GNOME;XFCE;**
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=general
X-GNOME-Autostart-enabled=true
**[COLOR=Red] # [/COLOR]X-Ubuntu-Gettext-Domain=nm-applet**
That is, add a # before the lines in bold (or better, create a backup of the file and completely remove those two lines)
Actually, in my file the first line in bold says: "NotShowIn=KDE", while the second line does not exist at all. So this suggestion is partially based on comparison and partially on some logic (you are using Unity, neither XFCE nor GNOME).

Let's check it.

---

### Post by laurac1022 on 2012-01-15
still didn't get it working.  I made a copy and deleted the two lines and it seemed to make no difference.  After it failed to autostart I tried to manually start it and it worked fine.  That is so weird...I wonder what is preventing it from starting on its own?

currently file looks like:
```
[Desktop Entry]
Name=Network Manager
Comment=Control your network connections
Icon=nm-device-wireless
Exec=nm-applet
Terminal=false
Type=Application
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=general
X-GNOME-Autostart-enabled=true

```

---

### Post by varunendra on 2012-01-16
Ok, I just figured out something I didn't think of earlier:

**[Reason (can be safely skipped)]**
As soon as we 'manually' add any application to startup, an 'autostart' directory immediately gets created (if doesn't already exist) in .config directory in our home (that is - /home/*<user>*/.config/), and a file with startup details pertaining to that app gets created in it.

In our case, this is nm-applet.desktop file (no, it's not a copy of the one in /etc/xdg/autostart, just the name is same but the code it contains is slightly different). Now what I was expecting was- such files should be automatically deleted with the removal of their pertinent application's entry from 'Startup Apps'. But for some reason (that I can only guess, but can't say for sure), this nm-applet.desktop file doesn't get deleted. Instead, only the value of a line in it - "Hidden=false" gets changed to "Hidden=true".
[B][/End of Reason]
[/B]
Now (with quite a shaken confidence this time ;)) I think all you need to do is to delete this file manually. To do so, open your **home **directory and make hidden directories visible from either view menu in nautilus or by pressing Ctrl+H keys. (All files/directories whose names start with a 'dot'(.) are hidden by default in Linux). Go into **.config/autostart** directory and delete **nm-applet.desktop** file from there (please don't tell me this file or the autostart directory itself doesn't exist at all! I would fall off my chair this time..).

Restart, and you should see nm-applet come up by itself, without its manual entry in 'Startup Apps' (Amen!).

---

