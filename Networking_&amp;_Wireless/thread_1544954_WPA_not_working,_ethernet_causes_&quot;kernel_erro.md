---
title: "WPA not working, ethernet causes &quot;kernel error&quot;, really need some sort of advice"
date: 2010-08-03
forum: Networking &amp; Wireless
---

### Post by dissembly on 2010-08-03
Hey all,

My wireless doesn't work, and the ethernet crashes whenever i plug the cable in. My machine (a 10" laptop) doesn't have a CD drive, so i am unable to upgrade to the 10.04 kernel and see if the problems (below) go away.

I got the machine with Ubuntu 9.10 Karmic Koala pre-installed on Friday - this is my first experience with Ubuntu, so my knowledge level is very low, and I have some trouble following some of the threads i've turned up that deal with this.

This lack-of-knowledge has lead me to try three fixes without really knowing if they were relevant to my problem (i don't know what my problem is, but details below). So i don't know if i've sabotaged myself by doing these three things, and i can't follow a lot of what was posted in the threads that led me to do them. I also don't know enough to know if i'm worrying about nothing.

I started up this thread -> [http://ubuntuforums.org/showthread.php?t=1543506](http://ubuntuforums.org/showthread.php?t=1543506) - because i beleived that i might have downloaded the wrong driver. However i no longer believe that.

I have downloaded, and, as far as i can tell, installed the Realtek 8192SE driver for use with a Realtek 8172 wireless card. I think this has worked, because NetworkManager now has "Wireless Networks" listed in it's menu - although it is perpetually grayed-out. This is after successfully completeing this tutorial on installing the driver: [http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10](http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10)

I don't think there is a problem there anymore.

My wireless network is a WPA one, i assume "personal" (i don't know how to tell for sure, but the other options have more fields - i only ever need the network name and a password).

This is the output from **iwconfig** and **iwlist wlan0 scanning**, as i have some impression that they are relevant tests:

> david@david-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.452 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          Retry: on   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

david@david-laptop:~$ iwlist wlan0 scanning
wlan0     Scan completed :

david@david-laptop:~$ I have tried using NetworkManager to make it search for a "Hidden" wireless network, with no success.



This is the ethernet problem i have:

After plugging in the ethernet cable, a scary looking red exclamation mark appears next to the icon for the NetworkManager Applet, and when I double-click on it, I get a message that says: > 
                                                 Your system encountered a serious kernel problem.

Your system might become unstable now and might need to be restarted.

You can help the developers to fix the problem by reporting it.

(report problem) (close) So the internet is completely inaccesible on that laptop. (I am restricted to copying things onto a flash drive and moving them across that way.) I also have no CD drive on the Ubuntu machine, or i would have upgraded to 10.04 to see if the problems went away.

I am worried that i am sabotaging the process of figuring out the problem, and making things more complicated, by partially trying fixes that i stumble across in other threads (without really knowing enough to know if those fixes are applicable... i don't even know what the problem is yet). Either way, none of the actions below have made any change to the failure to detect my WPA network.

Although, i suppose i should mention, that after trying to second of these steps, my NetworkManager icon switched position on the panel on my desktop, and is now on the other side of my battery life icon. I'm not sure if that means anything, i thought it was odd though.

Can anyone help me by telling me whether or not i have done the wrong things here:

First i did this:> From: [http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)
1) Open a terminal window and type:
      Code:
     wpa_passphrase your_ssid your_psk 
Note: your_ssid is the name of your wireless network (a.k.a. SSID) and your_psk is the password you want to use to protect your network. (Look below for an example).
 
 2) Now copy the psk string you got as output.
 
 3) Type:
      Code:
     sudo gedit /etc/wpa_supplicant.conf 
Then paste this as follow:
      Code:
     ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={

       ssid="your_ssid"
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=your_psk
} 
Note: your_psk is the psk string you got from step 1.Then this:> From: [http://ubuntuforums.org/showthread.php?t=1329254&page=2](http://ubuntuforums.org/showthread.php?t=1329254&page=2)
Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file
 sudo touch /etc/default/wpasupplicantThen, just a few minutes ago, this:> From: [http://www.ubuntugeek.com/enable-wpa-wireless-access-point-in-ubuntu.html](http://www.ubuntugeek.com/enable-wpa-wireless-access-point-in-ubuntu.html)
Please open a terminal and do:

sudo gedit /etc/modules
Add a single line:r8192se_pci 
Currently i have about eight threads open and am browsing through them, but my experience with each is roughly the same - i don't generally understand what problems the other people in the threads were having, and so can't assess whether the solutions posted are appropriate for me, and i've already made three changes to my system (above) that i don't understand. At this stage i thought, anything else i do based on these threads is only going to make this problem bigger, if it really *is* a problem. All i'll be doing is digging my hole deeper. 

So i panicked, and decided to post again in the forums to ask for WPA-specific help.

Can anyone help me in:
1) Troubleshooting why the wireless card does not detect my WPA network, or helping me find out what the problem is with either the wireless or the ethernet (the ethernet is something i would normally never use, but at least if i can get that working, then i might have some method of upgrading the kernel or adding programs to my computer)?
2) Telling me whether or not i should try to undo the three changes i made while searching for a solution (above)?
3) Helping me upgrade to 10.04 (with no wireless, ethernet or CD drive) to see if the problem dissappears?

---

### Post by khelben1979 on 2010-08-03
> **dissembly said:**
> I have downloaded, and, as far as i can tell, installed the Realtek 8192SE driver for use with a Realtek 8172 wireless card. I think this has worked, because NetworkManager now has "Wireless Networks" listed in it's menu - although it is perpetually grayed-out. This is after successfully completeing this tutorial on installing the driver: [http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10](http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10)

I don't think there is a problem there anymore.

Hmm.. I think you should install [Wicd]("http://en.wikipedia.org/wiki/Wicd") and post in this thread about what happens with that.

You write that you have a Realtek 8172 wireless card. I think that you need a proper driver to be able to use that. The Linux operating system do have a so called kernel modules. These kernel modules might contain a driver for your wireless networking card and hopefully Wicd can detect that and activate this module by itself.

If the kernel module for your wireless is not shipped with your Ubuntu kernel, then the solution might be just as you have written down before, that when you upgrade to Ubuntu Lucid, you get a newer Linux kernel which supports that network device.

Did you know that it's possible to boot with an usb stick? If you succeed in doing that, you can have an installation of Ubuntu Lucid on that usb stick. A full reinstallation would be to recommend if your current system is not working good with your computer hardware. It's easier. Also, make sure you do backups first if you need to.

---

### Post by dissembly on 2010-08-04
Thank-you very much for the reply! 

Attempting to upgrade to 10.04 seems like maybe the first thing i should try, but i have two questions:

*The how-to guide for installing from a flash drive as if it was a CD: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) - it only talks about installing Ubuntu new onto a Windows machine. But in this case i would be doing an upgrade, and doing it onto an Ubuntu machine, not a Windows machine. Do you know of any instructions for getting Ubuntu (Karmic Koala) to treat a USB drive like a CD (as i imagine the process would be different than the process for Windows)?

*I have seen suggestions that upgrades can go badly (or just not work) when there is no internet access, as the upgrader tries to grab some files from online - could this be a problem?

About wicd: I'm concerned that attempting to install wicd will only raise a new batch of problems; i've seen people say that wicd installs often just end up being tricky, without resolving whatever the underlying problem is.

I'm not sure about the 8172 card and the 8192SE driver, but i suspect that the driver is working, as it does show up on the list of modules, and installing it did give me the "Wireless" option in NetworkManager (albeit greyed out). But then i am not familiar with what it should look like if a driver doesn't work - i have been assuming that it just acts as if there is no card, but i take it that this is a bad assumption?

---

### Post by khelben1979 on 2010-08-04
> **dissembly said:**
> I'm not sure about the 8172 card and the 8192SE driver, but i suspect that the driver is working, as it does show up on the list of modules, and installing it did give me the "Wireless" option in NetworkManager (albeit greyed out). But then i am not familiar with what it should look like if a driver doesn't work - i have been assuming that it just acts as if there is no card, but i take it that this is a bad assumption?

Since it's greyed out, I don't think it's working even though you see it in the list.

About booting from USB: this is what I would do:

**1.** Grab an Ubuntu CD/DVD ISO image.
**2.** Open it up and copy over all files on the USB stick.
**3.** Edit your BIOS settings so that your BIOS will choose your USB stick as boot up device.
**4.** Make sure the USB stick is inserted and let the pc reboot with it, that should start the installation process of Ubuntu.

---

### Post by dissembly on 2010-08-07
Hi, sorry for the late reply to the thread; have been busy with work and school.

I have done steps 1 and 2 that you suggested - i have a usb drive with all the data from the CD image on it, but i do not know how to get the system to boot from that usb.

The USB Startup Disk Creator doesn't work (i click "Format", and nothing happens), so i tried it just by copying the data onto the usb. But now i don't know how to get the system to treat the USB as if it was the CD.

When i start up the laptop, there is a brief screen that says "Press F2 for system utilities"; i press F2, but nothing happens.

Is there any way to go about getting it to treat the USB as if it was a CD?

---

### Post by dissembly on 2010-08-09
My WPA problem is solved! 

I would be interested if anyone has anything to add about the ethernet error, or about anything else that was raised, but i thought i should post that the WPA is no longer a problem, and I think i will be fine from here on.

The solution is slightly embarrasing.

A key on my laptop, the F12 key, had another function. Apparently it switches the wireless card on and off. *facepalm*

I pressed it, and my WPA issues dissappeared...

I'm going to go and die of embarassment now.

---

