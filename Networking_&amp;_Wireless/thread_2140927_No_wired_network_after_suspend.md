---
title: "No wired network after suspend"
date: 2013-05-01
forum: Networking &amp; Wireless
---

### Post by LaptopU on 2013-05-01
Hello, I have found lots of similar posts on wifi but nothing for wired ethernet connection.

If my system suspends, when I resume I have no wired network connection.  In nm-applet I can see everything as it should be before I suspended the system apart from there is no connection to choose.  If I edit connections the connection is there but doesn't appear in the applet drop-down.  Disabling networking and restarting from the drop down doesn't fix it.

I have two NIC's on my motherboard, Marvell and NVidia.  It's the same problem whichever port is connected.  The really strange thing is I also have a wifi dongle and this works fine after a suspend, and this is what seems to make my problem different from others as their problems appear to be the other way around and it's wifi that is the problem.

This started for me back in 12.10 at some point in the last two months.  I didn't notice before as I was using wifi for a point when I ran out of local ethernet ports on my network but when I went back to ethernet two weeks ago that is when I noticed the problem.  I thought perhaps using the wifi dongle had changed the settings in network manager that caused the problem, so yesterday I did a clean install of 13.04 thinking this would fix it.  It hasn't, and the wifi dongle hasn't been near this install.  Essentially this is a totally clean installation.  The only thing that is common with this installation compared with my last install is Wireshark, is it possible Wireshark tweaks network settings to cause this?

Thanks for your help.

---

### Post by LaptopU on 2013-05-01
Some other things I have noticed tonight:

the activity light is still showing on the NIC even when powered down, so the network port is not going to sleep and that's how it was when it worked

I have edited acpi-support to ensure eth0 was not being suspended, that made no difference

Network manager can be stopped and restarted and it makes no difference

out of curiosity I tried uninstalling Wireshark and that made no difference (didn't think it would but I'm clutching at straws really)

Has anyone got an idea what is going wrong?  Here is a pastebin of my system log [http://pastebin.com/uismFRSr](http://pastebin.com/uismFRSr)

---

### Post by matt_symes on 2013-05-01
Hi

Try unloading and then reloading the eth0 driver after resume. 

If it then works you can write a script to unload/reload the kernel driver in /etc/pm/sleep.d.

To find the name of the network card driver...

```
lspci -k
```

Post that back here if you need help.

Kind regards

---

### Post by LaptopU on 2013-05-02
Thanks, I have found if I run sudo rmmod sky2 then sudo modprobe sky2 the network comes back up.

I have tried putting this in a script:

```

#!/bin/sh

case "$1" in
  suspend|hibernate)
    /sbin/rmmod sky2
    ;;
  resume|thaw)
    /sbin/rmmod sky2
    /sbin/modprobe sky2
    ;;
esac
exit 0
```

Saved that in /etc/pm/sleep.d as 00_ethernet_sleep and gave it 755 to make executable - this doesn't work.  Have you any clues where I'm going wrong please?

---

### Post by matt_symes on 2013-05-02
Hi

I believe rmmod is now depricated. Use *modprobe -r* instead. You do not need the second rmmod as well as you unloaded the kernel module during suspend.

Also get into the habit of terminating each line with a semi-colon.

For debug purposes you can also redirect any output into a file. If it throws any error you'll see them.

```

#!/bin/sh  

echo "running sky sleep script with $1" >> /ethernet_debug;

case "$1" in   
    suspend|hibernate) 
        /sbin/modprobe -r sky2 >> /ethernet_debug 2>&1; 
        ;; 
     resume|thaw)     
        /sbin/modprobe sky2 >> /ethernet_debug 2>&1;     
        ;; 
    esac 
exit 0;
```

Also *00_<filename>* will execute it very early. Try changing it to a higher value (say 99_....).

When it works, remember to remove the debug output.

Can you also post the output of

```
ls -l /etc/pm/sleep.d/
```

Kind regards

---

### Post by LaptopU on 2013-05-02
Thanks again for your help.

I'm having no luck with the script, I have pasted your script over my script and renamed it from 00 to 99.  The debug output is:

running sky sleep script with suspend
running sky sleep script with resume

Here is the output of ls -l for the folder:

```

-rwxr-xr-x 1 root root  210 Apr  9 10:29 10_grub-common
-rwxr-xr-x 1 root root  581 Oct  5  2012 10_unattended-upgrades-hibernate
-rwxr-xr-x 1 root root  282 May  2 14:46 99_ethernet_sleep
-rwxr-xr-x 1 root root 1260 May 23  2012 novatel_3g_suspend
```

Yet in a terminal when I type sudo modprobe -r sky2 then sudo modprobe sky2 it works fine, puzzling me :)

---

### Post by chili555 on 2013-05-02
Please try this. 
```
gksudo gedit /etc/pm/config.d/config
```

It will probably be a new file. Add a single line:

```
SUSPEND_MODULES="sky2"
```

Proofread carefully, save and close gedit. Let us hear your report, please.

---

### Post by matt_symes on 2013-05-02
Hi

I'm surprised it's not working as i have used something similar before. 

Give chili555's method a try.

Kind regards

---

### Post by LaptopU on 2013-05-02
This is a bit concerning as Chili's method hasn't worked either.  It was a new file, I selected on screen and copy-pasted to the file so there aren't any errors.  Do I have to chmod or chown at all, or reboot?  Could this be a specific issue to Ringtail?

---

### Post by chili555 on 2013-05-02
> **LaptopU said:**
> This is a bit concerning as Chili's method hasn't worked either.  It was a new file, I selected on screen and copy-pasted to the file so there aren't any errors.  Do I have to chmod or chown at all, or reboot?  Could this be a specific issue to Ringtail?I suggest a reboot, just in case.

I have only used this technique in wireless where it works perfectly in maybe 90% of cases. I have never tried it with ethernet so, I must admit, you are a test mule!

---

### Post by matt_symes on 2013-05-02
Hi

One thing to check is that it's actually loaded the module after resuming from suspend.

Suspend and resume the PC. Don' manually modprobe anything. From the terminal...

```
lsmod | grep sky
```

Kind regards

---

### Post by LaptopU on 2013-05-02
This is the output:

sky2                   57977  0 

It's exactly the same both before and after suspend.

---

### Post by matt_symes on 2013-05-02
Hi 

Is the interface up after the suspend/resume cycle and before manually modprobing ?

What's the output from

```
ifconfig
```

Kind regards

---

### Post by LaptopU on 2013-05-02
You'll be just as confused as me on this one, without any of the mods you guys have suggested I went into suspend, resumed and the network came back on.  I tried this again to make sure it wasn't a fluke and it came back on.  Reboot - nothing happened that time, I suspended several times and the network didn't come back up.  This is a clean Ringtail installation and I don't understand why it can be doing this.

Here's ifconfig:

```

system@system-MS-7100:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:09:d0:88:85  
          inet addr:192.168.0.28  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:fed0:8885/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:69692 (69.6 KB)  TX bytes:24756 (24.7 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:11:09:d0:7f:e3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27480 (27.4 KB)  TX bytes:27480 (27.4 KB)

```

after suspend, still with no network:

```

system@system-MS-7100:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:09:d0:88:85  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:69992 (69.9 KB)  TX bytes:24756 (24.7 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:11:09:d0:7f:e3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27480 (27.4 KB)  TX bytes:27480 (27.4 KB)

```

I'm becoming convinced now this is an Ubuntu bug.

---

### Post by matt_symes on 2013-05-02
Hi

Do the suspend/resume cycle with no mods. When the network is not working, open a terminal and type

```
sudo dhclient eth0
```

Does that get you an IP address ?

If it does, can you ping Googles servers ?

```
ping -c 3 8.8.8.8
```

EDIT: 

You also have 2 interfaces (2 network cards ?). Which one is your main one ? eth0 ?

Kind regards

---

### Post by LaptopU on 2013-05-02
eth0 is my main network port (I have two built onto my motherboard).  I hit suspend, resumed it to test what you've asked and the network came back up again.  Did this twice, network came back again.  Rebooted, no network after first suspend.  Ran dhclient and it hung for over a full minute before I gave up and ctrl-c out of it.  Not able to ping anything either.  When network is on dhclient returns RTNETLINK answers: File exists.

---

### Post by matt_symes on 2013-05-02
Hi

I would start looking in the log files as this is an intermittent problem. You may be able to see a difference between when it works and when it does not.

Check the file

```
/var/log/syslog
```

Kind regards

---

### Post by LaptopU on 2013-05-02
I have seen a line marked

```
<info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
```

The link doesn't necessarily seem like it applies to me though?

I've put this in pastebin here: [http://pastebin.com/7eZNkFfz](http://pastebin.com/7eZNkFfz) - I can see ifconfig problems in there but not sure if they are relevant.

It's giving me a headache though now :(

---

### Post by matt_symes on 2013-05-02
Hi

> May  2 17:19:15 system-MS-7100 kernel: [  206.864057] sky2 0000:02:00.0:  No interrupt generated using MSI, switching to INTx mode.

For a quick test while i continue to look through the logs, boot from grub using this kernel command line option.

```
pci=nomsi
```

Edit the line by selecting 'e' when on the correct kernel line, to boot using grub, and add after it *quiet splash*. F10 or Ctrl + x to continue booting.

Check it worked by typing

```
cat /proc/cmdline
```

and look for the text added above and then test the suspend/resume cycle.

Kind regards

---

### Post by LaptopU on 2013-05-03
Done that, seems to be working so far, here's my system log pastebin:

[http://pastebin.com/Kirvysm8](http://pastebin.com/Kirvysm8)

Going to have another reboot to check this isn't a one-off, will post back in a moment.

Edit, yes it does still work - I went back without that option and still had the problem, put back pci=nomsi (checked /proc/cmdline to see it was definitely in there which it was), network came back on with that option.

Is it sensible/wise/problematic to permanently include that flag on boot then if that solves my problem?

---

### Post by matt_symes on 2013-05-03
Hi

> Going to have another reboot to check this isn't a one-off, will post back in a moment.

I suspect you know this but you will have to add the *pci=nomsi* option after each reboot at the moment as it's not persistent between boots.

To make it persistent you will need to edit 

```
/etc/default/grub
```

Look for the line that contains ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` and add the option after splash.

Then type 

```
sudo update-grub
```

That'll make it persistent across reboots.

> Is it sensible/wise/problematic to permanently include that flag on boot then if that solves my problem?

It should be all right but give your system a good test.

Kind regards

---

### Post by LaptopU on 2013-05-03
Thanks I have made the change persistent - I was aware I had to edit the grub config file to make persistent but wasn't sure how to do it so I was going to google that - you've saved me a job ;)

I really appreciate your help too.

---

### Post by matt_symes on 2013-05-03
Hi

No problem :D

If you could mark this thread as solved it will help others looking for a solution to the same problem.

**EDIT:**

I'll do it for you.

Kind regards

---

