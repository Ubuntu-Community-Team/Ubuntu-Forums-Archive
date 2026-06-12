---
title: "getting wireless on my desktop"
date: 2010-01-27
forum: Networking &amp; Wireless
---

### Post by rockclimber112358 on 2010-01-27
Hello everyone!  I'm a new linux-user, I just installed it yesterday.

I'm having some trouble figuring out how to set-up my wireless connection (on my desktop computer).  I bought a wireless receiver that worked great when I was running Windows, but I can't figure out how to get it to work on the Ubuntu side.  It's a DWA-131 Wireless N Nano USB Adapter, if that's important :)

I have an installation cd, but I can't figure out how to get the install to run.  I also have access to internet via my wife's laptop (which is how I'm typing this right now), so I could download drivers, etc.  The problem is, I don't really know what I'm doing, which drivers to download, and how to run a driver on Ubuntu.  Any help would be greatly appreciated!

I'm also pretty new at this, so please try to post at a fairly basic level :)  Thanks so much!

---

### Post by chili555 on 2010-01-27
There are a few things we can try. This is apparently the pretty new Realtek 8192su chipset, and a module already in the kernel might work. Please insert the device and open a terminal (Applications -> Accessories -> Terminal) and do:```
sudo modprobe r8192s_usb
iwconfig
```Do you now have a wireless interface? Can you click Network Manager and connect?

If not, please post:```
lsusb
```We will all learn together.

---

### Post by rockclimber112358 on 2010-01-27
Hey, thanks for the quick response, and for helping me out with this.  Ok, so the first thing we tried didn't work.  Here's the output when I entered lsusb:

Bus 001 Device 007: ID 07d1:3303 D-Link System 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 413c:3200 Dell Computer Corp. Mouse
Bus 003 Device 004: ID 413c:2010 Dell Computer Corp. 
Bus 003 Device 003: ID 413c:1003 Dell Computer Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by chili555 on 2010-01-27
OK, here comes Plan B! We are going to try to get this card going using a scheme called ndiswrapper, which uses the Windows, usually XP, driver. First, open up your Home Folder (Places -> Home Folder) and create a folder (File -> Create folder) and let's call it Dlink. Next, open the driver CD and drag the contents to the Dlink folder. Open it and tell us what's in it. We are looking for a Drivers folder, within which is a WinXP folder, then an x86 folder, within which are rtl8192su.sys and net8192su.inf. Those are the files we need for ndiswrapper. Do you have them?

---

### Post by chili555 on 2010-01-27
We will follow the procedure here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

We will start at section 3.4.2.

---

### Post by rockclimber112358 on 2010-01-27
Hmm...  Okay, so I have the files you mentioned.  I created a drivers directory in /home, and I tried running:  sudo ndiswrapper -i ~/drivers/net8192su.inf

But, I got an error saying "sudo: ndiswrapper: command not found"

Thanks again for your help!

---

### Post by chili555 on 2010-01-27
If you have internet connectivity, you can do:```
sudo apt-get install ndisgtk
```Everything you need will be pulled in for you. Then run the commands again.

---

### Post by rockclimber112358 on 2010-01-27
Is there anyway I can do it without internet connectivity?  I only have wireless, and I'm using a laptop with windows to post.  So, I don't have a way of running that code...

---

### Post by chili555 on 2010-01-27
I think ndiswrapper is on your install CD. Please drop the CD in the tray and try:```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```It's late, see you in the morning.

---

### Post by rockclimber112358 on 2010-01-27
It works!  Hooray!  Thanks so much for you help, I couldn't have done it without you.

---

### Post by chili555 on 2010-01-28
Great! This is a relatively new chipset, so I'm sure the searchers will see this. Glad it's working for you!

---

### Post by rockclimber112358 on 2010-01-29
Hey man, I don't know if you're still reading this thread, but I have some more problems with this.  The wireless worked great yesterday after I followed everything you recommended.  Then, it asked me if I wanted to install updates, so I said yes (I'm not sure what exactly they were, but I think it was something like system updates).  I installed them, and it took a long time, so I let it run overnight.  When I got back on this morning, the updates were finished, but my internet connection was gone.  I don't know what could have happened, but I'm guessing the updates did something?  Any ideas would be greatly appreciated.  Thanks for putting up with my questions :)

---

### Post by chili555 on 2010-01-29
First, let's see if the ndiswrapper module is still loaded:```
lsmod | grep ndis
```If no result is shown, let's reload it:```
sudo modprobe ndiswrapper
```If the module is still loaded, let's check its status:```
ndiswrapper -l
```Check to see if you have a wireless interface now:```
iwconfig
```

---

### Post by rockclimber112358 on 2010-01-29
I believe the module is still loaded, after running the first command I get:

ndiswrapper           193436  0

I tried reloading it anyways, just in case.  Also, I think the driver is installed and working, here's the output from the third command:

net8192su : driver installed
    device (07D1:3303) present

Then, when I run iwconfig, I get the following output:

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I know there's no issue with my wireless signal, since I'm using a laptop to connect to the internet wirelessly on the same connection... I'm really puzzled :)

---

### Post by rockclimber112358 on 2010-01-29
Ok, so pasting the output was a bad idea.  This should be better...  Here's the output from iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by chili555 on 2010-01-29
> wlan0 IEEE 802.11g ESSIDff/any
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Bit Rate:1 Mb/s Tx-Power:20 dBm Sensitivity=0/3 
--- snip ---You have a working wireless interface waiting for the command to connect! What happens, or doesn't, when you click the Network Manager icon and try to connect?

Incidentally, you might right-click the icon, select Edit Connections, select the Wireless tab, highlight your home network, select Edit and check  Connect Automatically.

---

### Post by rockclimber112358 on 2010-01-29
Ok, so I click the network manager icon (the icon next to the volume control, right?), and then select the network I want to connect to.  It brings up a "Unlock Keyring" screen, so I type in my admin password and that screen goes away.  Then I see two green bubbles with a blue haze circling them where my connection manager icon is.  Then, it says "linksys connected" and... everything worked... Hmm...

Ok, so I feel really stupid, but I could have sworn I tried that before and it didn't work.  Also, the connection is extermely slow, especially compared to my laptop which also has wireless.  Could that just be that my wireless receiver on my desktop doesn't work as well as the wireless card in the laptop?  Although, when I was running Windows XP on my desktop, it seemed to be working fine using the same wireless receiver...

Anyways, thanks for all the help, and sorry for asking dumb questions sometimes :)

I'm really excited to start learning linux, and your help has really encouraged me to do this.

---

### Post by chili555 on 2010-01-29
> Bit Rate:1 Mb/s> Also, the connection is extermely slowSeriously slow, actually! Please do:```
sudo iwconfig wlan0 rate auto
iwconfig wlan0
```Does that fix it? If so, please do:```
sudo gedit /etc/rc.local
```Add a new line above 'exit 0.'```
iwconfig wlan0 rate auto
```Sudo is not needed in *rc.local*. You may also have better luck with *sudo iwconfig wlan0 rate 54M*. Use whichever gives the best, most stable, fastest, most righteous, delicious result.

---

### Post by rockclimber112358 on 2010-01-29
Ok, cool.  I logged in this morning, and the rate was up to 7Mb/s.  I ran both of those commands you recommended, followed by iwconfig each time, and the rate stayed at 7Mb/s.  It's alot faster than it was yesterday (as it should be, being at 7 instead of 1).  Could the problem just be that my internet is slow?  If there's another way to test if it can go faster, I'd love to hear it though!

Thanks, you've been awesome.

---

### Post by Oz3507 on 2010-01-30
Hi, I hope you don't mind me joining this thread, I am trying to do exactly the same thing i.e. getting DWA-131 to work with Ubuntu (having also just installed - 9.04 - Jaunty). Any help would be much appreciated.
 
I seem to have managed to complete most of the steps and iwconfig seems to show that Ubuntu has now recognised the USB adaptor.
 
[FONT=Courier New]wlan0 IEEE 802.11g ESSID:off/any [/FONT]
[FONT=Courier New]Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated [/FONT]
[FONT=Courier New]Bit Rate:65 Mb/s Tx-Power:20 dBm Sensitivity=0/3 [/FONT]
[FONT=Courier New]RTS thr:off Fragment thr:off[/FONT]
[FONT=Courier New]Power Management:off[/FONT]
[FONT=Courier New]Link Quality:0 Signal level:0 Noise level:0[/FONT]
[FONT=Courier New]Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0[/FONT]
[FONT=Courier New]Tx excessive retries:0 Invalid misc:0 Missed beacon:0[/FONT]
 
I was then expecting to be able see wLan0 in the same way as eth0 in Network connections so that I can enter the SSID etc, but I can't... Thanks in advance

---

### Post by chili555 on 2010-01-30
You want to click the Network Manager icon and see if you see your network. Please see attached. The icon is at the upper right, and will look like two monitors.

Click on your network, and if you have encryption, WEP, WPA or the like, you will be asked for the key or password and you will connect. Sometimes, it takes a few moments, so be patient.

---

### Post by Oz3507 on 2010-01-31
Thanks - that worked, the only remaining thing was to set the DNS details in /etc/resolv.conf as described 4.5.
 
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#dns](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#dns)
 
And I have internet, thanks again!! Hopefully the result will be as good when the router and adaptor are more than 3 feet apart...

---

### Post by rockclimber112358 on 2010-02-01
Alright, I'm back again with more problems...

So, my wireless works sometimes, but it doesn't seem very consistent.  I've right-clicked on the Network Manager icon and gone to "Edit Connections", and then looked at the settings for my wireless network.  It seems to always erase my password.  I've tried creating new connections, as well as editing the current ones, and I have several wireless networks shown that (I think) are all the same one with different settings.  I can occassionally connect, but I seem to sometimes be able to connect with one setting, and sometimes with another.  But, then there are times when I can't connect at all.  Any ideas?  Are there any specific settings I should have?

When I run iwconfig, I'm still showing that I'm connected, at a rate of 7Mb/s:
```

josh@josh-desktop:/etc/init.d$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:6B:83:C1:D6   
          Bit Rate=7 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:39/100  Signal level:-71 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```Is there any other wireless networking device?  Network Manager just seems like it's not working well at all for me...

Well, thanks again for your help!

---

### Post by chili555 on 2010-02-01
> Link Quality:39/100How do you feel about this? Are you quite a distance from the router, or do you feel like this is an erroneous figure?

You may be able to connect automatically by right-clicking the Network Manager icon, Edit Connections, select Wireless, highlight your network and select Edit. Check Connect Automatically. See attached.> I have several wireless networks shown that (I think) are all the same one with different settingsCan you connect to any and all of them? Do any have better signal strength?

---

### Post by rockclimber112358 on 2010-02-01
Hmm...

Yeah, I edited Network Manager, and the connection that I've had the best luck with is set to connect automatically.  I had tried probably 10 times to connect to that network (and others) last night, and nothing worked.  I logged in this morning, and it worked on the first try.  It just seems very unstable.

I am a pretty good ways from the router, so 37/100 or 39/100 seem like reasonable numbers.

Do you think it could possibly be that the wireless receiver I have doesn't work well with Linux?  I googled "D-Link DWA-131 Linux" and it seems like some other people have had my same problem.  Maybe I just need to go out and buy a new receiver?

Thanks again!

---

### Post by lygmoo on 2011-03-01
*[SIZE="3"]**Chili555, could you please help me too?**[/SIZE]*

As you may guess, I'm also a linux newbie and have problems with making D-link DWA-131 work.

I've followed a lot of steps, described above.

Here's my lsusb results:

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04d9:1203 Holtek Semiconductor, Inc. Keyboard
Bus 002 Device 002: ID 09da:000e A4 Tech Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 13fe:1d00 Kingston Technology Company Inc. DataTraveler 2.0 1GB/4GB Flash Drive / Patriot Xporter 4GB Flash Drive
Bus 001 Device 004: ID 07d1:3303 D-Link System 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

ndiswrapper -l

```
net8192su : driver installed
	device (07D1:3303) present (alternate driver: r8192s_usb)
```

iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Access Point: Not-Associated   Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Actually, network manager (or how do you call this icon in the top of the screen) doesn't show me any available wireless networks, just no networks. In the same time I'm typing this message using my home wi-fi through a netbook with WinXP.

The strange point is that ESSID. My wi-fi is called "BotFam", computer can't find it. BUT it is "connected" to this strange network (while no networks to connect to are available in network manager).:confused:

Hope on your help. Thank you in advance.

---

### Post by chili555 on 2011-03-02
> net8192su : driver installed
	device (07D1:3303) present ([COLOR="Red"]alternate driver: r8192s_usb[/COLOR])It looks like the native Linux driver is loading, too and conflicting with ndiswrapper. Let's fix it:```
sudo su
echo "blacklist r8192s_usb" >> /etc/modprobe.d/blacklist.conf
rmmod r8192s_usb
rmmod -f ndiswrapper
modprobe ndiswrapper
exit
iwconfig
```Any improvement?

---

### Post by lygmoo on 2011-03-02
Yahoo!)
Yes, it works!
Thank you very much, Chili.:)
You are really inspiring genius of ubuntu!:)

---

### Post by jaguare22 on 2011-03-27
Hi, I followed the thread to get DWA-131 working but at the end I had this (built in card is off):

computer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

computer:~$ ndiswrapper -l
net8192su : driver installed                                                   
        device (07D1:3303) present (alternate driver: 8712u)

Kubuntu 10.04, KDE 4 - Thanks....

---

