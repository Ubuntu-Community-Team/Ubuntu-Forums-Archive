---
title: "Newbie needs help with accessing internet"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by Zarakava on 2008-12-06
Ok, so while I'm not new to computers, I just started with linux. I know nothing, but I really want to learn. However, if I could get my wireless internet working with Ubuntu that would help a ton. I currently have Vista and Ubuntu dual booted. I have been trying to find the Network manager, but to no avail. 

I have a belkin wireless receiver. Please help someone in need.

Zarakava

---

### Post by lovelyvik293 on 2008-12-06
First of all welcome to ubuntu.
):P whenever you are asking any question at this forum specify your ubuntu distribution.
In this condition please specify the full name and the type(usb or pci) of wireless adaptor.

And to check the network manager and the connections use the ifconfig and iwconfig(wireless) in terminal.

---

### Post by frankleeee on 2008-12-06
The network manager is the two small screens in the top panel in Ubuntu, left click if your running wireless and it will drop down available wireless links look for yours. If you need to put a password and name in it is on the same drop down if you need to edit it right click then hit edit connections, this is assuming your using 
intrepid. Hardy and earlier distros' are even easier. If your screens are not in the panel NM is in system-preferences and is called network configuration.

---

### Post by Zarakava on 2008-12-06
ok. I am using the ubuntu-8.10-desktop-amd64.iso

my router (not attatched to this computer)

my receiver is a USB Belkin Wireless G Network Adapter model F5D7050

also, i know my SSID is linksys, but when i plug it in to the double screens in the corner, nothing happens. I know there is no encryption on my wireless.

and i have no clue what ifconfig and iwconfig(wireless) are. As I said, I just installed Ubuntu, and want to get internet up so I can read tutorials without having to switch back over to Vista.

---

### Post by m_duck on 2008-12-06
If you left click the network manager icon in the top right, does it give you a list of available wireless networks? If so you should just be able to click your network and it will connect automatically. If none are displayed, open a terminal (Applications -> Accessories -> Terminal) and post the output of ```
ifconfig
iwconfig
sudo lshw -C network
```(run each of the above separately and press enter after typing each one in)

From a quick google it seems like you may have to use ndiswrapper which is a utility for using the Windows driver for your wireless card in Linux. However, if you just post the above, we shall see where to go from there.

EDIT: also, could you post what version your wireless adapter is? It is probably written on the card itself.

---

### Post by Zarakava on 2008-12-06
Ok, so I think ive figured out part of the issue. I think it must be the drivers because i don't get the green light on my Usb stick for it being active. Now, when I tried to follow the steps for Ndiswrapper,

1

Install ndisgtk (System &#8594; Administration &#8594; Synaptic Package Manager).
2

Open ndisgtk (System &#8594; Administration &#8594; Windows Wireless Drivers).

I was able to get to the package manager, but when i did a search for ndisgtk, it wasnt there...

also, all my usb says is what i posted above, Made In China, a mac address, and 802.11g - 54 Mbps.

Sorry for being so unexperienced here, But i want to get this working well.

Zarakava

---

### Post by m_duck on 2008-12-06
If you put the CD you used to install Ubuntu in the drive, then go back into synaptic, then click Settings -> Repositories and then at the bottom of the Ubuntu Software tab and make sure the tick box next to the cdrom is checked. Close that dialogue, then click Reload in synaptic. This should index the packages that are available on the CD. Next, click the Search button and search for "ndiswrapper". You should get three results, one being "ndisgtk". Click to install ndisgtk (it will automatically select the other two for installation. Once that is installed, Windows Wireless Drivers should be available in System -> Administration.

Next step is finding the .inf file for your wireless adapter. If you put the CD in that came with your wireless card, can you find a .inf file in there? A .sys file is also needed. They are probably in a folder called WinXP2K. If you do not have the CD, the Belkin site has info on how to find the version number to enable us to get the correct drivers [here]("http://www.belkin.com/uk/support/article/?lid=enu&pid=F5D7050uk&aid=6122&scid=0").

Once you have located the .sys and .inf files, goto System -> Administration -> Windows Wireless Drivers, and follow the on screen instructions. If it all loads properly, left clicking on network manager in the top right should find your wireless and allow you to connect.

[Ubuntu documentation regarding ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Zarakava on 2008-12-06
ok, I have the windows driver installed. It's still not picking up my network, but I'm just about to try turning roaming on.

ok, the driver seems to be working, because it recognizes my USB. However
System | Administration | Networking

I don't have this. The only "N" under admin is Network Tools, and that has nothing about roaming in it

---

### Post by Zarakava on 2008-12-06
anyone know how to get this working?

---

### Post by Zarakava on 2008-12-06
Final thing I can add. I see the administrative program "Network" under add applications. However, I cannot add it because I can't connect to the internet. Can I get it by downloading somewhere on my vista side?

---

### Post by m_duck on 2008-12-06
Can you type```
iwconfig
```in terminal (Applications -> Accessories -> Terminal) and post the output here?

---

### Post by Zarakava on 2008-12-06
```
zarakava@zarakava-desktop:~$iwconfig

lo        no wireless extensions.


eth0      no wireless extensions.


pan0      no wireless extensions.


```

---

### Post by Zarakava on 2008-12-06
basically, I think I need the Network application.

---

### Post by m_duck on 2008-12-06
From that output it looks like the driver didn't load properly. If you type ```
ndiswrapper -l
```in terminal, it should say whether the driver is installed properly and if it recognises the hardware. I would have expected to see an entry such as wlan0, wifi0 or eth1 for example from the iwconfig command with something other than "no wireless extensions."

I am not sure what you mean be the network application? In the Administration menu on my computer here, the only network entry I have is "Network Tools".

---

### Post by Zarakava on 2008-12-06
reply

```
zarakava@zarakava-desktop:~$ ndiswrapper -l
blkwgu : driver installed
	device (050D:705E) present (alternate driver: rtl8187)
zarakava@zarakava-desktop:~$ 



```

---

### Post by m_duck on 2008-12-06
Hmm, that seems strange. I've only had limited contact with ndiswrapper so I may be missing something. I'll have a look around and see what I can find that might be of use. Did you find what version it was in the end? After googling the driver and the card it seems like its probably a version 5000, but just checking.

EDIT: possibly a silly question but have you restarted since installing the driver? It's surprising how many problems I've had that have been solved with a restart.

---

### Post by Zarakava on 2008-12-06
yeah it was. Sorry I forgot to put that. From the site you gave me, it ended with -F

---

### Post by m_duck on 2008-12-06
After a reboot, try typing in terminal```
sudo depmod -a
sudo modprobe ndiswrapper
```That is what is needed to load the driver into memory (from community docs link I posted before). After that, run ```
iwconfig
```again, and with a bit of luck, hopefully there will be a "wlan0" entry.

---

### Post by Zarakava on 2008-12-06
Nothing different. here's a new idea though.

Under windows drivers, when I click network configuration (or something to that effect)

it says no network tools detected.

---

### Post by m_duck on 2008-12-07
Hmm, thats odd. As far as the error, there, looking at another thread, if you install the package gnome-network-admin that should fix it. As you have no internet connection, you will need to download the .deb file from somewhere then copy it over and install it. By the way are you using 32 bit or 64 bit Ubuntu?

Someone in [this thread]("http://ubuntuforums.org/showpost.php?p=4295631&postcount=29") seems to have got the same wireless adapter that you have online.

Also, are you using Ubuntu 8.10 (intrepid) or an older version?

If using Intrepid, the .deb files I mentioned earlier are (just click one of the mirrors closest to you to begin the download):
      [32-bit]("http://packages.ubuntu.com/intrepid/i386/gnome-network-admin/download")
      [64-bit]("http://packages.ubuntu.com/intrepid/amd64/gnome-network-admin/download")

---

### Post by Zarakava on 2008-12-07
ok. One last question. How do I install that .deb. I know where to find it from ubuntu, cuz its under my windows downloads folder.

Thanks

---

### Post by m_duck on 2008-12-07
If you double click it, it will prompt you for your password and then bring up a window with "install" as an option. Click that, and it should just install it so when you click configure in the windows wireless drivers thing it will bring up the proper window instead of the error. .deb files are similar to something like a setup.exe in windows, but they don't ask so many questions (if any).

---

### Post by Zarakava on 2008-12-07
ok. We're getting somewhere. I realized that I needed to install my 64 bit Belkin driver. Now the light appears on the device. However, as soon as I do this, it essentially breaks Ubuntu.

I can't really open or run anything, and terminal won't respond to any commands. I don't think it's that package I installed, but I don't have the time to reinstall ubuntu again. (I had just tried that)

If it can help, whenever I tell ubuntu to reset, it pops out of my desktop into a black screen where it says

```
Can't open /dev/isdninfo or /dev/isdn/isdninfo. No such device or address.
```

---

### Post by Zarakava on 2008-12-07
Bump

---

### Post by m_duck on 2008-12-07
Sorry, I should have asked which version you were using at the beginning #-o

If you unplug your wireless adaptor, do you still have the problem when you can't run programs/type into the terminal/reboot?

If not, can you unload the wireless driver in the Windows Wireless Drivers section, then try and load the driver again but from the command line? Hopefully, if something is going wrong, the terminal will output something useful.

You can use the following command to do this:```
sudo ndiswrapper -i /path/to/driver.inf
```If it gives a nice output such as, "Driver installed, hardware present" or suchlike, run:```
sudo depmod -a
sudo modprobe ndiswrapper
```Hopefully, if you then run```
iwconfig
```in terminal, it should have an entry for wlan0. If that is the case you **should** be able to use network manager to connect to your wireless network. If a less nice output is given to any of the above, post it here and we'll see what can be done...

Apologies for not being able to help more with this! Hopefully someone who **knows** how to fix the problem will be able to help soon too!

---

### Post by utnubuuser on 2008-12-07
I think the network configuration tool your lookin for are under System>>Preferences, not System>>Adminisration

---

### Post by Zarakava on 2008-12-08
None of that worked, but it's only when the reciever is plugged in.

---

### Post by Zarakava on 2008-12-09
Bump

---

### Post by Zarakava on 2008-12-09
Hey, I've got a question. Should i try downgrading to an earlier ubuntu or different linux?

---

### Post by m_duck on 2008-12-09
You could try it. I think it will be the same story on other distro's too. From [here]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#USB") it shows that your adapter will work in Ubuntu. It does seem odd that there seems to be so much of a problem getting it to work though. I've not used ndiswrapper for a while but do not remember having much trouble with it. It's probably just a step missed somewhere. It may be worth reinstalling Ubuntu and following the [Ubuntu ndiswrapper guide]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") to the letter.

Just to clarify in my head more than anything else, are the following the details that we need:

**OS:** Ubuntu Intrepid 8.10 (64-bit)
**WiFi:** Belkin F5D 7050 USB Dongle (version 5000) (050D:705E)
   - Realtek RTL8187B chipset (rtl8187 driver)
   - Needs ndiswrapper

Is that all correct? Let me know if your reinstalling, or want to keep fiddling with this install or are installing a different OS. It **WILL** work in the end!

---

### Post by Zarakava on 2008-12-11
thats all correct except chipset, I'm not sure what that is. Also, May it be an issue with my ISP, Comcast?

---

### Post by Zarakava on 2008-12-11
BUMP... please help

---

