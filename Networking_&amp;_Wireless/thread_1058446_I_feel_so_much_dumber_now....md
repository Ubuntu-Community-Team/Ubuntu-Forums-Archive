---
title: "I feel so much dumber now..."
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by moveright on 2009-02-02
I just decided to switch to linux today.  I did MUCH research and came to the conclusion that Ubuntu was the way to go.  allow me to preface this by saying that I consider myself extremely savvy and there are very few problems in windows I have ever failed to diagnose and fix.

Enter Linux...

wow.  ok, rather than go off on a rant and get myself all upset by explaining everything that is irritating me, let me first say what impresses me.  I have a compaq presario v6719nr and when I chose the live cd method so I could sort of play before I commit, as it booted into the OS, my sound worked.  wow.  that's something that takes a while with windows to make operable after a format.  also, the wired network worked immediately as well.

nice looking OS but I've got an issue.  wifi does not work and when I got to the madwifi website and read the instructions it is like a new language to me.  holy smokes, why can't I just choose to update the wifi driver and point it at the file? (the flaming may now begin)

so I have an Atheros 5006x integrated wireless device and I have found specific info regarding this but I just can't make sense of it.  compile a driver?  and what is all this #apt- blah blah . /$$  stuff???  I have become such a noob.

Is Linux over my head?  Should I just turn around and run now?  Is it just Ubuntu and another distro may be more forgiving to such an unsuspecting trespasser?  Or is a mountain being made of a mole hill and this is really not that complicated?

thanks :)

---

### Post by Twitch6000 on 2009-02-02
Well first what version of ubuntu do you have?

I know ubuntu 8.10 likes my atheros card 5009.

All I had to do is just say enable and click the network.

However if you want a distro with madwifi, which will yes give you better help with atheros cards I would say use mandriva 2009.

---

### Post by moveright on 2009-02-02
I am using 8.10.

wow that was a fast response.

---

### Post by Twitch6000 on 2009-02-02
Humm then it should detect your card..


Go into terminal and type this - 

lspci

And after wards type -

iwconfig wlan0

and copy and paste the outcomes of both.

After we get the info, I bet we can solve the problem :D.

---

### Post by moveright on 2009-02-02
btw Mandriva looks extremely nice, I just finally chose ubuntu because it seemed like that was what everyone was using, hence the most support available.

---

### Post by Twitch6000 on 2009-02-02
> **moveright said:**
> btw Mandriva looks extremely nice, I just finally chose ubuntu because it seemed like that was what everyone was using, hence the most support available.

Well to be honest and this is coming from a distro hopper/multi os user, in my opinion Mandriva 2009 is better then Ubuntu.

However since you are using Ubuntu lets stick with Ubuntu help lol...

---

### Post by moveright on 2009-02-02
ok, gonna have to boot again into it as I did before.  oh also, it DID detect something because when I went to I think system>admin>hardware drivers it had listed the 177 for my nvidia which needed to be downloaded and also it said something about atheros for 802.11g devices and that it was activated.  not sure if that means anything.

well, I will have to boot into the live CD again.  back in a bit.  I may not do it tonight, I haven't decided yet.  being defeated by a computer is a terrible feeling.

---

### Post by Twitch6000 on 2009-02-02
> **moveright said:**
> ok, gonna have to boot again into it as I did before.  oh also, it DID detect something because when I went to I think system>admin>hardware drivers it had listed the 177 for my nvidia which needed to be downloaded and also it said something about atheros for 802.11g devices and that it was activated.  not sure if that means anything.

well, I will have to boot into the live CD again.  back in a bit.  I may not do it tonight, I haven't decided yet.  being defeated by a computer is a terrible feeling.

Humm it seems that it has detected your nvidia card and atheros wireless card aswell.

---

### Post by moveright on 2009-02-03
ok, I did lots of thinking last evening and I came up with the fact that I may not be comparing apples to apples.  I have to load the wireless driver on XP as well the difference is that I HAVE the driver and I also know how to load it.  I believe my frustration comes from the fact that I am not accounting for a learning curve.

nonetheless, I'm at work now, never got a chance to load ubuntu back up, will do later.

I don't understand how this stuff works though, say I get the wifi working, what about my network HP laserjet?  how about my Brother USB local printer I use to scan?  am I going to have hell with these too?

for curiosity, I downloaded Mandriva 2009 One and burned the ISO.  I could not even get it to boot all the way, it hung up on some "audit" text, then I hit the power button ony my laptop and it continued, but then froze about 90% through the next progress bar.

I'm stumped.  Maybe linux hates me.

I'll be back with that wifi info you asked for.

---

### Post by wstout on 2009-02-03
Moveright, if your card is listed in the Hardware Drivers section it will work when you install Ubuntu, or atleast this has been my experience. You will have to actually go there and it will direct you how to download and install the driver after you install Ubuntu to your hard drive, but probably won't work on the live cd since you have to actually install something. If it works the why I think it should you will actually find this is much easier than having to track down a driver in Windows.

---

### Post by timcredible on 2009-02-03
the hp printer is probably already working - hp drivers are included on the cd you installed, try printing something, it should work.  however, you may want to go to system->administration->printing and change the printer options and tell it that you have a black ink cartridge because the hp drivers tend to default to thinking you have no black ink cartridge.  doing this is very similar to working with a printer in windows.

you don't need to compile anything for your wifi.  you probably just have to click 'enable' on the screen that shows the atheros card.  if that doesn't work, install ndiswrapper (ndisgtk in synaptic), and then system->administration->windows wireless drivers and point to the same driver you used for windows.

---

### Post by moveright on 2009-02-03
that makes a lot of sense. yeah, because I was able to download the video driver but then it wanted to restart and I knew if it did, it would not save the video driver so I said to heck with it.

next question since you all are being so nice,  Is Kubuntu basically the exact same thing with the exception of it's desktop appearance?  It seems more graphically advanced but maybe that's just an illusion.

oh and one last thing for now, I have read but do not understand, if I install ubuntu next to windows, if I decide that I can't get used to it or something, can I upgrade easily to kubuntu?

*edit* - didn't see the last post about the printer

---

### Post by moveright on 2009-02-03
> **timcredible said:**
> the hp printer is probably already working - hp drivers are included on the cd you installed, try printing something, it should work.  however, you may want to go to system->administration->printing and change the printer options and tell it that you have a black ink cartridge because the hp drivers tend to default to thinking you have no black ink cartridge.  doing this is very similar to working with a printer in windows.

you don't need to compile anything for your wifi.  you probably just have to click 'enable' on the screen that shows the atheros card.  if that doesn't work, install ndiswrapper (ndisgtk in synaptic), and then system->administration->windows wireless drivers and point to the same driver you used for windows.

well, the screen where I saw the driver was the same screen that had (2) different nvida drivers one was version 177 it said recommended next to it, so I highlighted that and clicked activate and it wanted to download a driver which is good I guess.  but the only other thing in that box was for the wireless and it already had a green light in the circle, so it was "activated" I suppose.  weird.  because then I went into (bad memory sorry) I believe system>networks?  but for wireless tab there was nothing there. I guess I was looking for it to have my wifi device listed, then I could just choose an SSID or whatever.  maybe I am over simplifying it.

---

### Post by wstout on 2009-02-03
> **moveright said:**
> 
oh and one last thing for now, I have read but do not understand, if I install ubuntu next to windows, if I decide that I can't get used to it or something, can I upgrade easily to kubuntu?

You can very simply add the Kubuntu desktop to your Ubuntu install. Simply open a terminal (Applications > Accessories > Terminal) then type ```
 sudo apt-get install kubuntu-desktop 
``` 

You well then be able to chose KDE from the Sessions on your login screen.

---

### Post by moveright on 2009-02-03
ok, regardless of my frustration level, I have now installed kubuntu AND ubuntu on my hdd so I'm sorta in it for good now.  one of these HAS to work.

I will be posting the information requested momentarily.

---

### Post by moveright on 2009-02-03
ok, lspci and the other one wsconfig wlan0 I think.  here is what it spit out...

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

moveright@moveright-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
moveright@moveright-laptop:~$ iwconfig wlan0
wlan0     No such device

moveright@moveright-laptop:~$

---

### Post by Twitch6000 on 2009-02-03
Okay it seems it detects your wireless card,but just doesn't want to connect.(or something like that..)

I am assuming you have installed ubuntu onto your computer?

If so then my only guess for a wifi fix would be download the linux driver from the site itself.

---

### Post by moveright on 2009-02-03
yes ubuntu is installed.  download the driver from what site?

---

### Post by moveright on 2009-02-03
ok, I finally downloaded from the sourceforge site, it's madwifi!  but I don't have to compile it.  so what the heck do I do with this .tar.gz stuff?  and what about my video driver?  omg, sorry, I must seriously be killing you at this point.

---

### Post by maspin on 2009-02-03
I recently came to Ubuntu as well.. About a month ago.
I wouldn't go back to Windows if I had the choice.. Sure, things are complicated, and a bit confusing.. But I am getting the hang of it now (slowly!).

There is so much you can do with Ubuntu that isn't possible in Windows!

Keep it up!

P.S. I had a similar wireless issue.. Can't remember how I solved it. I just read some forums, after a day of utter confusion, I followed some steps people suggested, and somehow got it working! These forums are a lifeline now!!

---

### Post by yther on 2009-02-03
moveright, you did mention a learning curve, and you were right.  After someone has spent many years becoming a power user or expert in one system, it's quite a blow to suddenly become a total beginner again, isn't it?  :o

Regarding Kubuntu, yes, it's the exact same underlying system (kernel, packages, etc.) but defaults to the KDE interface instead of GNOME.  As someone else mentioned, it's quite possible and fairly easy to install the default Kubuntu desktop on top of Ubuntu; then you will be given the choice of which one to start when you log in.  Also, KDE programs can run on a GNOME desktop; it's just a question of making sure the libraries they depend on are installed, and generally the package manager takes care of that.

You might look at Envy for your video driver, since (from your lspci output) it seems you have a GeForce card.  The main interface of Envy is Qt (think KDE) but there is a text interface if you don't care to load all the Qt stuff just for that.  You can install Envy through Adept or Synaptic, or in a terminal type "aptitude search envy" to see which ones are available, then "sudo aptitude install whichever".  Envy will take care of loading the driver for you, and it provides a one-step reversion if things don't work out.  (Just read the Envy help for that tool.)

I can't help with the wireless stuff.  The first time I tried Ubuntu (8.04), my wireless card wasn't fully supported and just plain wouldn't work no matter what I did.  Now, it is recognized without any problems in 8.10 so I didn't have to mess with it.  However, generally if you have a software package in a .tar.gz file (and it's not source that you have to compile), you unpack it like this:

```
cd /some/temporary/place
tar -xvzf /wherever/you/put/the_file.tar.gz .
```

Normally that results in a folder called "the_file" in the current directory (note the final "." there).  Then you'd cd into that folder and run some installer script to put the software where it belongs.  (You might also have some graphical archive manager available that can extract it, but use of those varies, while tar should work the same anywhere.)

---

### Post by moveright on 2009-02-03
IT WORKS IT WORKS!!!!!

I found this:

Here are the steps:

1- Disable the "Support for Atheros 802.11 wireless LAN cards" on Hardware Drivers, and reboot your box.
2- Once it is back on, open a Terminal, and type:
Code:

sudo aptitude install linux-backports-modules-intrepid-generic

It will ask your password, this is what it prints on screen, that is, what it will do:
Code:

esteban@tango:~/Desktop$ sudo aptitude install linux-backports-modules-intrepid-generic
[sudo] password for esteban: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  linux-backports-modules-2.6.27-7-generic{a} 
  linux-backports-modules-intrepid-generic 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1173kB of archives. After unpacking 3772kB will be used.
Do you want to continue? [Y/n/?]

When that is over (you'll get your prompt back), reboot, and enjoy the WiFi connection.
Personally, I can't still believe it, I have spent hours on Hardy with this... The WiFi card used to work, I was able to set an IP address to ip, etc, but it was impossible to connect to any type of network.

But that was Hardy, on Intrepid, after the backports installation, I had no problem connecting to my WPA2 DLink AP (after autenticating me of course).
Good luck, I hope this is useful.

now that my wifi works, I was able to d/l the video driver and everything is AWESOME.

can someone please explain to me what that command did to fix my wifi?  I HAVE to understand things for some reason.

---

