---
title: "Questions about wireless on HP dv6 Intel Centrino WirelessN 1000"
date: 2011-11-01
forum: Networking &amp; Wireless
---

### Post by Dxh3378 on 2011-11-01
Very inexperienced user here.
I am running Ubuntu 11.10 from fresh install.
HP Pavilion dv6 with an Intel Centrino WirelessN 1000

The issues I am having include:
When I first boot up, I am connect to my home network just fine, but as I surf, the network speeds slow to a crawl.  I have done some research on the forum and if I use the 

sudo rmmod iwlagn
sudo modprobe iwlagn 11n_disable=1 

commands in the terminal, my browsing speeds return to normal.

2.This is all well and good until the computer goes into a suspend.  Once it wakes back up, the network appears to search for a network to connect to endlessly, and will not reconnect until I reboot.
I did some more research and was able to install the 2.6.38 kernel.  When I boot off of the older kernel and enter the previously mentioned commands everything seems to function as it should, that is until, I place a dvd in the dvd drive.  Then the whole system crashes. 
So basically I am looking for some advice on how to get everything working properly while on the current 11.10 kernel.

Thank you in advance to the Forum Super Heroes who take the time to educate the newbs.

P.S. Speak to me as though you are trying to communicate with an infant ;)

---

### Post by wildmanne39 on 2011-11-01
Hi, welcome to the forum! Please try making that command permanent I think that will help.
```
gksu gedit /etc/modprobe.d/options.conf
```
And add the following to it.
```
options iwlagn 11n_disable=1
```
then save and exit.
Thank you

---

### Post by Dxh3378 on 2011-11-02
(gedit:4537): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
hernam@hernam-HP-Pavilion-dv6-Notebook-PC:~$ 




This was the output after fallowing the two steps.

Just to make sure I am doing this correctly, after the first command, [gksu gedit /etc/modprobe.d/options.conf],a window pops up and then I c&p,[gksu gedit /etc/modprobe.d/options.conf], in it, then when I hit save, it asks me to name the file and select a folder.  So I named it wireless workaround and saved it to the modprobe.d file that auto populated in the window below.

Like I said very inexperienced, Please feel free to talk slower and louder lol.
And thanks again for the help!

---

### Post by wildmanne39 on 2011-11-02
Hi, /etc/modprobe.d/options.conf is the name of the file, you do not need to rename it.

---

### Post by Dxh3378 on 2011-11-03
Ok, I navigated to the /etc/modprobe.d/options.conf, and the options.cof file does contain the [options iwlagn 11n_disable=1] code.  

I think I am good to go, because I surfed around for quite some time and did not see any reduction in speed, nor did I re-enter the commands from OP.

I also see the file that I renamed, in the modprobe.d file, it is blank 0kb, I want to get rid of it, but it said I do not have permission, when I tried to move it to the trash.  

So on to issue 2.
While running the 11.10 3 kernel I was still unable to connect to my network after waking back up after a suspend with out a reboot.

I can put it to sleep and wake it back up all day long on the 2.6.38 kernel without any problems.  I don't really want to stay on the old kernel though, cause whenever I put a dvd into the drive, the system will crash.  That is the only major failure I have experienced, but who knows what else may not be jiving.  
Thank you
Dx

---

### Post by wildmanne39 on 2011-11-03
Hi, for the suspend and resume wireless issue please try this:
```
gksu gedit /etc/pm/config.d/config
```
Add this single line:
```
SUSPEND_MODULES="iwlagn"
```
Proofread, save and close gedit.

Please let me know if it does and would you please go to the top of the page and mark this thread solved if it works by clicking on thread tools. Thank you so much.

This should do it.

---

### Post by Dxh3378 on 2011-11-05
No Dice wildmanne.
like with the previous instructions, I can navigate to /etc/pm/config.d/config

and the code is there.  
but still cannot connect after suspend and resume
thank you

---

### Post by wildmanne39 on 2011-11-05
Hi, please post the results of:
```
lspci -nnk | grep -iA2 net
```
Thank you

---

### Post by Dxh3378 on 2011-11-05
hernam@hernam-HP-Pavilion-dv6-Notebook-PC:~$ lspci -nnk | grep -iA2 net
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Hewlett-Packard Company Device [103c:1658]
	Kernel driver in use: r8169
--
0d:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0084]
	Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1315]
	Kernel driver in use: iwlagn
hernam@hernam-HP-Pavilion-dv6-Notebook-PC:~$ 


This is what I came out.
Just realized, I ran the command while on the 2.6.38 kernel.  
If it will make a difference let me know and i'll reboot onto 3 and then re-post.

---

### Post by wildmanne39 on 2011-11-05
Hi, I am going to ask a friend that is our main network expert on the forum to take a look, I have researched this issue and I have not find much on it.
Thank you

---

### Post by chili555 on 2011-11-06
> **wildmanne39 said:**
> Hi, for the suspend and resume wireless issue please try this:
```
gksu gedit /etc/pm/config.d/config
```
Add this single line:
```
SUSPEND_MODULES="iwlagn"
```
Proofread, save and close gedit.

Please let me know if it does and would you please go to the top of the page and mark this thread solved if it works by clicking on thread tools. Thank you so much.

This should do it.Please amend the file here:```
gksu gedit /etc/pm/config.d/config
```Edit the entry you had previously to:```
SUSPEND_MODULES="iwlagn 11n_disable=1"
```Proofread carefully, save and close gedit. Let us hear your report, please.

---

### Post by Dxh3378 on 2011-11-06
@wildmanne39 
Thank you so much for all your help with these issues, sorry we couldn't get you another [SOLVED]

@chili555,
eehhh What's up doc? and welcome aboard!

(gedit:3206): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.DKUK4V': No such file or directory

(gedit:3206): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:3206): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.9L3J4V': No such file or directory

(gedit:3206): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory


this was the output after I pasted the 
[SUSPEND_MODULES="iwlagn 11n_disable=1"]  Code in the config window that pops up after terminal command 
[gksu gedit /etc/pm/config.d/config]
saved and exit.
Still no success reconnecting after suspend and resume on 3kernel.

---

### Post by wildmanne39 on 2011-11-06
Hi Dxh3378, that is alright, we are here to help and also to learn and hopefully I will have more knowledge after we are done with your issue then before we started.
Thank you

---

### Post by chili555 on 2011-11-06
> Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directoryPlease try:```
sudo mkdir -p /root/.local/share
```Now try the commands again and tell us if you get the errors.> Still no success reconnecting after suspend and resume on 3kernel. Did *iwlagn* load as expected after suspend?```
lsmod | grep iwl
```

---

### Post by Dxh3378 on 2011-11-07
hernam@hernam-HP-Pavilion-dv6-Notebook-PC:~$ sudo mkdir -p /root/.local/share
[sudo] password for hernam: 
hernam@hernam-HP-Pavilion-dv6-Notebook-PC:~$ gksu gedit /etc/pm/config.d/config

(gksu:2025): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2025): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2025): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2025): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
hernam@hernam-HP-Pavilion-dv6-Notebook-PC:~$ lsmod | grep iwl
iwlagn                314213  0 
mac80211              310872  1 iwlagn
cfg80211              199587  2 iwlagn,mac80211
hernam@hernam-HP-Pavilion-dv6-Notebook-PC:~$ 



So still a no go 
After running all the commands (while on 3kernel)I went up to the top right and clicked suspend.
When it woke back up, it was still acting like it was searching for the network, then prompts me to enter my network password (which is auto-populated) I click enter and then it continues to cycle through those steps.

I rebooted and selected the 2.6.38kernel and something happened that I had not experienced before.  While booting at the Ubuntu logo with the red dots, a message came up saying "checking for disk drivers" with an ascending percentage.  When it finished, the boot process continued as normal.  Don't know if this means anything, but that was the first time that had happened, and I just want to provide as much detail as I can

---

### Post by chili555 on 2011-11-07
> While booting at the Ubuntu logo with the red dots, a message came up saying "checking for disk drivers" with an ascending percentage. When it finished, the boot process continued as normal. Ubuntu is set up to do an automatic file system check every thirty boots; it's entirely normal. 

Are there any clues as to why the system won't reconnect here?```
sudo cat /var/log/syslog | grep etwork | tail -n20
```If the output is sparse, check in syslog.1

---

### Post by Dxh3378 on 2011-11-08
hernam@hernam-HP-Pavilion-dv6-Notebook-PC:~$ sudo cat /var/log/syslog | grep etwork | tail -n20
[sudo] password for hernam: 
Nov  8 20:39:58 hernam-HP-Pavilion-dv6-Notebook-PC NetworkManager[970]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Nov  8 20:39:58 hernam-HP-Pavilion-dv6-Notebook-PC NetworkManager[970]: <info>   address 192.168.1.103
Nov  8 20:39:58 hernam-HP-Pavilion-dv6-Notebook-PC NetworkManager[970]: <info>   prefix 24 (255.255.255.0)
Nov  8 20:39:58 hernam-HP-Pavilion-dv6-Notebook-PC NetworkManager[970]: <info>   gateway 192.168.1.1
Nov  8 20:39:58 hernam-HP-Pavilion-dv6-Notebook-PC NetworkManager[970]: <info>   nameserver '209.18.47.61'
Nov  8 20:39:58 hernam-HP-Pavilion-dv6-Notebook-PC NetworkManager[970]: <info>   nameserver '209.18.47.62'
Nov  8 20:39:58 hernam-HP-Pavilion-dv6-Notebook-PC NetworkManager[970]: <info>   domain name 'carolina.rr.com'
Nov  8 20:39:58 hernam-HP-Pavilion-dv6-Notebook-PC NetworkManager[970]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Nov  8 20:39:59 hernam-HP-Pavilion-dv6-Notebook-PC NetworkManager[970]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Nov  8 20:39:59 hernam-HP-Pavilion-dv6-Notebook-PC NetworkManager[970]: <info> Policy set 'linksys' (wlan0) as default for IPv4 routing and DNS.
Nov  8 20:39:59 hernam-HP-Pavilion-dv6-Notebook-PC NetworkManager[970]: <info> Activation (wlan0) successful, device activated.
Nov  8 20:39:59 hernam-HP-Pavilion-dv6-Notebook-PC NetworkManager[970]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Nov  8 20:39:59 hernam-HP-Pavilion-dv6-Notebook-PC NetworkManager[970]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Nov  8 20:39:59 hernam-HP-Pavilion-dv6-Notebook-PC NetworkManager[970]: <warn> bluez error getting default adapter: No such adapter
Nov  8 20:40:17 hernam-HP-Pavilion-dv6-Notebook-PC NetworkManager[970]: <info> (wlan0): IP6 addrconf timed out or failed.
Nov  8 20:40:17 hernam-HP-Pavilion-dv6-Notebook-PC NetworkManager[970]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Nov  8 20:40:17 hernam-HP-Pavilion-dv6-Notebook-PC NetworkManager[970]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) started...
Nov  8 20:40:17 hernam-HP-Pavilion-dv6-Notebook-PC NetworkManager[970]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Nov  8 20:40:17 hernam-HP-Pavilion-dv6-Notebook-PC NetworkManager[970]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Nov  8 20:40:17 hernam-HP-Pavilion-dv6-Notebook-PC NetworkManager[970]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) complete.
hernam@hernam-HP-Pavilion-dv6-Notebook-PC:~$ 

Here is the output of [sudo cat /var/log/syslog | grep etwork | tail -n20] command

Just to clarify, in order to do "check in syslog.1" would I just be adding the [.1]to where syslog appears in the command line above?

---

### Post by chili555 on 2011-11-09
> Just to clarify, in order to do "check in syslog.1" would I just be adding the [.1]to where syslog appears in the command line above?Yes, exactly. When the system log (/var/log/syslog) fills up with several hundred lines, it is copied to syslog.1 for archive purposes. Syslog.1 is moved to syslog.2 and compressed with gzip and so forth. If we happen to check syslog a short time after the process took place, there may be no or only a few lines related to our problem. If your command asks for tail -n20 (show me only the last twenty lines) and you get only a few, say five, then you know to check the previous file syslog.1.> Nov 8 20:39:58 hernam-HP-Pavilion-dv6-Notebook-PC NetworkManager[970]: <info> address 192.168.1.103
Nov 8 20:39:58 hernam-HP-Pavilion-dv6-Notebook-PC NetworkManager[970]: <info> prefix 24 (255.255.255.0)
Nov 8 20:39:58 hernam-HP-Pavilion-dv6-Notebook-PC NetworkManager[970]: <info> gateway 192.168.1.1
Nov 8 20:39:58 hernam-HP-Pavilion-dv6-Notebook-PC NetworkManager[970]: <info> nameserver '209.18.47.61'
Nov 8 20:39:58 hernam-HP-Pavilion-dv6-Notebook-PC NetworkManager[970]: <info> nameserver '209.18.47.62'
Nov 8 20:39:58 hernam-HP-Pavilion-dv6-Notebook-PC NetworkManager[970]: <info> domain name 'carolina.rr.coIt looks like it connected perfectly to me! I see no faults that show any indication of why and how it slows down and fails to reconnect after suspend.

There are a variety of parameters available in the driver *iwlagn*:```
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           no_sleep_autoadjust:don't automatically adjust sleep level according to maximum network latency (bool)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)
parm:           ucode_alternative:specify ucode alternative to use from ucode file (int)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           bt_ch_inhibition:Disable BT channel inhibition (default: enable) (bool)
parm:           plcp_check:Check plcp health (default: 1 [enabled]) (bool)
parm:           ack_check:Check ack health (default: 0 [disabled]) (bool)
```The parameter we added above didn't seem to help in any way. Let's try some other likely sounding candidates. Please do:```
sudo rm /etc/modprobe.d/options.conf
sudo gedit /etc/modprobe.d/iwlagn.conf
```A new empty file will open. Add one line:```
options iwlagn no_sleep_autoadjust=true
```Proofread carefully, save and close gedit. Now do:```
sudo gedit /etc/pm/config.d/config
```Change the text within to:```
SUSPEND_MODULES="iwlagn"
```Proofread carefully, save and close gedit.

Reboot and let us have your report.

-------------------

Reference for Chili: [http://www.spinics.net/lists/linux-wireless/msg75566.html](http://www.spinics.net/lists/linux-wireless/msg75566.html)

---

### Post by wildmanne39 on 2011-11-09
Hi Chili555, thank you for your help on this one.

I am watching, I just do not have anything to add.

---

### Post by Dxh3378 on 2011-11-09
Ok so that absolutely did not have the desired effect.
After reboot, there is no initial wireless connection.
From the network icon, all the available networks are gone as well.
If I go to system settings, and then to network, only the wired option is available.


Edit:
I entered the [sudo gedit /etc/modprobe.d/iwlagn.conf] command again, and when the window with [options iwlagn no_sleep_autoadjust=true] comes up, I highlighted and deleted the line, then save and exit... same process for second set of commands.  Rebooted and was able to get wireless to initialize again.

---

### Post by chili555 on 2011-11-10
Let's try another parameter. Amend the file to:```
options iwlagn bt_coex_active=true
```Reboot and try again.

If you have no wireless, please do:```
sudo modprobe iwlagn bt_coex_active=true
```Note and report any errors or warnings.

---

### Post by Dxh3378 on 2011-11-12
Well [options iwlagn bt_coex_active=true] borked out the wireless again.
I did [sudo modprobe iwlagn bt_coex_active=true] and that did't get it back either.
I used the method I used previously to restore wireless.


hernam@hernam-HP-Pavilion-dv6-Notebook-PC:~$ sudo modprobe iwlagn bt_coex_active=true
[sudo] password for hernam: 
WARNING: All config files need .conf: /etc/modprobe.d/Wireless workaround, it will be ignored in a future release.
FATAL: Error inserting iwlagn (/lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko): Invalid argument
hernam@hernam-HP-Pavilion-dv6-Notebook-PC:~$

---

### Post by chili555 on 2011-11-12
> hernam@hernam-HP-Pavilion-dv6-Notebook-PC:~$ sudo modprobe iwlagn bt_coex_active=true
[sudo] password for hernam:
WARNING: All config files need .conf: /etc/modprobe.d/Wireless workaround, it will be ignored in a future release.As Spock says, fascinating. Let's unravel that first. Please show me:```
cat /etc/modprobe.d/Wireless\ workaround
```I can't imagine what it is; we'll probably delete it ar at least change its name. Next, please try:```
sudo modprobe iwlagn bt_coex_active=1
```Note any errors or warnings.

---

### Post by wildmanne39 on 2011-11-12
I am learning from the surgeon.
Thank you

---

### Post by Dxh3378 on 2011-11-13
hernam@hernam-HP-Pavilion-dv6-Notebook-PC:~$ cat /etc/modprobe.d/Wireless\ workaround
hernam@hernam-HP-Pavilion-dv6-Notebook-PC:~$ sudo modprobe iwlagn bt_coex_active=1
[sudo] password for hernam: 
WARNING: All config files need .conf: /etc/modprobe.d/Wireless workaround, it will be ignored in a future release.
hernam@hernam-HP-Pavilion-dv6-Notebook-PC:~$ 


Here is the output from the above commands.
Thanks again for all your help guys.

---

### Post by chili555 on 2011-11-13
> hernam@hernam-HP-Pavilion-dv6-Notebook-PC:~$ cat /etc/modprobe.d/Wireless\ workaroundWhen there was no output, that suggests there is nothing inside the file; let's remove it.```
sudo rm /etc/modprobe.d/Wireless\ workaround
```We added bt_coex_active successfully; does it seem to help your problem?

---

### Post by Dxh3378 on 2011-11-13
hernam@hernam-HP-Pavilion-dv6-Notebook-PC:~$ sudo rm /etc/modprobe.d/Wireless\ workaround
[sudo] password for hernam: 
hernam@hernam-HP-Pavilion-dv6-Notebook-PC:~$ 

Unfortunately [bt_coex_active], did not seem to help, while on 3kernel, network will still not reconnect after resuming from a suspend.
thank you

---

### Post by Dxh3378 on 2011-11-15
OK so obviously I don't know Jack from Jill when it comes to Ubuntu.  I've been thinking about this whole issue and wanted to throw an idea out there. 

So I boot up and log in and auto connect to my wireless network, right.
Then, once a suspend, or close the laptop occurs, upon waking back up and logging back in, I am not able to re-establish a connection.

Here is my thought, (feel free to roll your eyes, and snicker at the newb), after logging back in, the led on the wireless key is blue (connected), if I click on the wireless icon on the top bar, my network name ONLY gives the option to disconnect, (as if I am already connected).  It seems as though all the commands we have been trying are system configuration oriented.  Could the issue possibly be a bug/glitch with the auto authentication/ saved password process, as it then keeps asking for the network password over and over again.

It just seems so weird that the wireless is definitely ON, as some things we have tried have disabled it.  It is like it's saying, "OK, you are connected to your network, I'm just not going to allow you access to it".

Although I have been failing left and right here, I have learned so much more than when I started. Thanks again guys for all your efforts.

---

### Post by northd_tech on 2011-11-16
> **Dxh3378 said:**
> 
So I boot up and log in and auto connect to my wireless network, right.
Then, once a suspend, or close the laptop occurs, upon waking back up and logging back in, I am not able to re-establish a connection.

Have you tried to boot with the "**acpi=off**" option in your GRUB[2] bootloader to see if you experience the same WiFi problem with Power Management disabled?

I believe you can change that somewhat easily by "**gksu**" editing **/etc/default/grub** to read something like this:

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"Or for me, because I HATE that useless splash screen and miss those informative diagnostic messages scrolling by:

> GRUB_CMDLINE_LINUX_DEFAULT="acpi=off"[http://ubuntuforums.org/showpost.php?p=11452892&postcount=39](http://ubuntuforums.org/showpost.php?p=11452892&postcount=39)

Then saving, quitting the editor, issuing a **sudo update-grub** command, rebooting, and testing extensively to see if your suspend problems have gone away.


Alternately, grubconf, Grub Customizer, gnome-system-tools and KGRUBEditor are all reported to be "easy" ways to reconfigure your GRUB bootloader.  (Grub Customizer is for GRUB2).

KGRUBEditor
[http://kde-apps.org/content/show.php?content=75442](http://kde-apps.org/content/show.php?content=75442)

QGRUBEditor
[http://www.ubuntugeek.com/qgrubeditor-a-visual-grub-configuration-editor.html](http://www.ubuntugeek.com/qgrubeditor-a-visual-grub-configuration-editor.html)
[http://qt-apps.org/CONTENT/content-files/60391-QGRUBEditor-2.5.0-src.tar.bz2](http://qt-apps.org/CONTENT/content-files/60391-QGRUBEditor-2.5.0-src.tar.bz2)

GRUBConf
[http://grubconf.sourceforge.net/](http://grubconf.sourceforge.net/)

GNOME-system-tools
[http://projects.gnome.org/gst/#what](http://projects.gnome.org/gst/#what)

GRUB Customizer
[http://ubuntu-tweak.com/source/danielrichter2007-grub-customizer/](http://ubuntu-tweak.com/source/danielrichter2007-grub-customizer/)

---

### Post by psycho_killer on 2011-11-19
Just wanted to add that I've been having this same problem: [http://ubuntuforums.org/showthread.php?t=1840116](http://ubuntuforums.org/showthread.php?t=1840116)

So, Dxh3378, you're not alone...__

---

### Post by Dxh3378 on 2011-11-24
@psycho_killer
Thanks for the moral support, I checked out your link, sucks we cant get this straightened out.  Are you still running 11.10, and if so, have you tried booting from the 2.6.38 kernel?  That works for me, and the only issue I have come across is when I try to play a dvd, the system will crash.  But I don't really use my machine for anything ultra important either, so I'm ok with that work-around.

---

### Post by psycho_killer on 2011-11-27
Dxh3378, any idea where I can find a -lowlatency version of that kernel?  The generic version shows some promise (I can't test it fully yet because I just broke my ancient router trying to update the firmware) but it messes my sound up (whereas the newest generic kernel was working okay in that regard).  I can't seem to find a source for it online...

---

### Post by Dxh3378 on 2012-01-04
Bump
No real urgency here, getting along OK with reboot after a suspend, just wanted to see if anyone had any new ideas or input.
Thanks 
D

---

### Post by wildmanne39 on 2012-01-05
Hi, I am sorry still no new information on your problem.
Thanks

---

