---
title: "Why is wireless so difficult in Dapper?"
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by irw on 2006-06-01
I ran Breezy on my laptop with a perfect wireless conection via a Netgear USB WG111v2. Set up with ndiswrapper was straightforward, and easy to sort out even when I was a total newbie with fora help. :) 

On Dapper it does not work. :confused: 

I have spent hours trawling the fora, trying everything that sounded vaguely related, with little or no success.  It worked once for a few minutes, but the next time I rebooted, it was gone. ](*,) 

Looking through the fora, there seem to be a lot of people with problems.  Is there a common issue to these all, - ie one thing that effects a lot of people, or is it just that there are a lot of broken bits in dapper?

My reason for asking is to see if anyone can offer some generic solutions or pointers that could get us going in the right direction rather than all asking the same questions about different hardware / problems.

---

### Post by javaJake on 2006-06-01
First of all, I assume that you are attempting to get ndiswrapper installed. If you are sure this is the way to go (Dapper supports a lot of wireless cards natively now) then I recommend that you check to be sure that ndiswrapper is not conflicting with a driver that already exists. If there is an existing driver, you should blacklist it first.

Unfortunately, I have no clue how to find what driver would belong to your card, or how to blacklist. (Could someone else jump in for me for this part? :p )

---

### Post by irw on 2006-06-01
With a fresh install of dapper, initially there was enough of a connection to tell me updates were available to download.  Seconds later I could not connect anymore despite fiddling with every setting I could find.

I then installed ndiswrapper, and tried both Win98 & XP drivers. There was a 
conflict with the rtl8187 driver which I black listed, based on advice in another thread. I then had a working connection for an hour or two, but on booting the next day there was no connection. I have tried to re-create the steps I took, including uninstalling all I had installed, re-installing parts, re-black listing and removing drivers, etc, all with no success.

I may try another fresh install and see where we go this time ...

---

### Post by kiddyfurby on 2006-06-02
just some stupid guesses that you might want to ignore

"initially there was enough of a connection to tell me updates were available..."
so native driver works (at least for a little while)!!

Are you using NetworkManager?
Did you specify the SSID of access point you 'd like to connect to?

Ubuntu connect to "best-signal" network, so make sure you card does not automatically switch.
It might be that, which make your card stop working

---

### Post by irw on 2006-06-02
I never got to download network manager before it gave up!

I did specify the SSID, and there was only one wireless signal - coming from m router about 12 inches away, so signal strength was not a problem.

---

### Post by Killerah on 2006-06-03
Hi there, first off, I agree with you, for some reason wireless in Dapper seems alot more difficult for me than it was in Breezy. I came across this thread while browsing this section and saw that you have the same wireless card (err... dongle) as I do. I had this working before in Dapper (it took me forever too), but then my hard drive failed and I had to re-install ubuntu. Now I'm stuck in the same situation I was before except that what I had tried doesn't seem to help. How did you find out that the device was conflicting with the rtl8187 driver, and how did you blacklist it? Maybe that will work for me... Anyway, I don't want to hijack this thread, but here's my output from iwconfig.

```
nate@ntop:~$ iwconfig wlan0
wlan0     802.11b/g link..  ESSID:"loudon"
          Mode:Managed  Channel=10  Access Point: 00:0F:66:52:8C:A0
          Bit Rate=11 Mb/s   Sensitivity=4/6
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``` To be a little more specific about my problem, when I try to set up the network, it can see the 3 APs in range, but when I try to connect it just hangs there on the "activating interface wlan0" dialog. The progress bar goes back and forth for a long time and then it finishes and nothing is different. I'm using ndiswrapper and the win2000 drivers (I've tried them all of course).

---

### Post by gbw69 on 2006-06-04
Hi Guys
I've been doing my head in trying to get this usb netgear wifi to work.
After i successfully installed ubuntu from the internet, i was very chuffed with myself, I tryed to install the wifi usb dongle using ndiswrapper.
I managed to install the driver:

root@spankass:~# ndiswrapper -l
Installed ndis drivers:
netwg111        driver present

Should it say something about hardware present?
I thought it might be something to do with using a usb2 device on a usb1 port, but the system see the wg111v2 on the usb port.

root@spankass:~# lsusb
Bus 001 Device 004: ID 0846:6a00 NetGear, Inc.
Bus 001 Device 001: ID 0000:0000

i was also following steps from the wiki on how to install the wg111, without a hitch upto where you run

root@spankass:~# modprobe ndiswrapper
root@spankass:~# tail /var/log/messages
Jun  4 14:36:37 localhost -- MARK --
Jun  4 14:56:37 localhost -- MARK --
Jun  4 15:16:37 localhost -- MARK --
Jun  4 15:36:37 localhost -- MARK --
Jun  4 15:56:37 localhost -- MARK --
Jun  4 16:01:02 localhost kernel: usb 1-2: USB disconnect, address 3
Jun  4 16:01:06 localhost kernel: usb 1-2: new full speed USB device using uhci_hcd and address 4
Jun  4 16:16:43 localhost -- MARK --
Jun  4 16:36:44 localhost -- MARK --
Jun  4 16:56:44 localhost -- MARK --

wiki says i should see a 'wlan0' or something like that, but i don't.
have i overlooked something?

---

### Post by apejcic on 2006-06-04
check if maybe islsm drivers got loaded, because they could be conficting with ndiswrapper
also check "iwconfig" command

---

### Post by gbw69 on 2006-06-04
There seems to be no conflics in device manager.
root@spankass:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

---

### Post by gbw69 on 2006-06-05
Can someone send me a clue, maybe a tutorial or some basic commands that i might not be doing?:-\"

---

### Post by Killerah on 2006-06-05
there are some commands on [here](https://wiki.ubuntu.com/WirelessTroubleshootingGuide?highlight=%28wireless%29) that you might not have tried. 
And what model are you using? You seem to say that you have a wg111v2 but you appear to be using the drivers for the wg111. You might want to grab the disc that came with your wireless dongle and use those instead of whatever you might be using.

Also, I'm still wondering how I would find out if there are any conflicts and how to blacklist them.

---

### Post by gbw69 on 2006-06-05
Thanks for that link, a few steps closer to the truth, i can't follow the steps beyond
lshw
it brings back alot of informationd but nothing along the lines of wlan0 or netgear, it does however give me this:
  *-network:1 DISABLED
       description: controller
       physical id: 2
       logical name: sit0
not sure what to do next. the commands that follow states something about pcmcia but this device is usb
lsusb returns:
spankass@spankass:~$ sudo lsusb
Bus 001 Device 002: ID 0846:6a00 NetGear, Inc.
Bus 001 Device 001: ID 0000:0000

I got the driver of the netgear website, and i followed the steps from the wiki.
Could it be something to do with the version of ubuntu i'm running?

---

### Post by Killerah on 2006-06-05
Are you sure you got the right drivers though, you need the drivers for the wg111v2, not the wg111. That's probably why it doesn't say hardware present. But if you're like me that won't help you out much anyway (though it's better than nothing). There's definitely something different with Dapper from Breezy though, because I had it working flawlessly in Breezy without having to jump through a bunch of hoops to get it to work.

---

### Post by 11hjpphty76lkjj on 2006-06-05
I've had the same experience with Dapper.  Breezy to Upgrade Flight 6 = Wifi Broke (works great in breezy.) Breezy to CD Flight 6 = Wifi Broke. again works great in Breezy...  Going from dapper to breezy means a full re-install, and I'd loose too much data at this point.  I can't remember which wifi card I have but it's a Belkin that works out of the box with Breezy, ie it has the correct chipset to work easily with breezy without using the NDISWrapper.  I've spent a lot of time working with wifi cards and breezy. :) 

Anyway, I'll try the live cd but if it doesn't work out of the box then I wont be going to dapper anytime soon.  Which makes me sad. ](*,)

Dapper should be increasing functionality, honest i would have rather we focused on other problems instead of going to the live cd install thing.  Which is lovely don't get me wrong, but with other more pressing problems to resolve it seems like a waste of time.  There are so many other things i'd rather see.  but anyway that's another topic.

Will wifi work as stable in breezy with the dapper release?

*shakes magic 8 ball*

---

### Post by bsell on 2006-06-05
[QUOTE=gbw69]Thanks for that link, a few steps closer to the truth, i can't follow the steps beyond
lshw
it brings back alot of informationd but nothing along the lines of wlan0 or netgear, it does however give me this:
  *-network:1 DISABLED
       description: controller
       physical id: 2
       logical name: sit0
not sure what to do next. the commands that follow states something about pcmcia but this device is usb
lsusb returns:
spankass@spankass:~$ sudo lsusb
Bus 001 Device 002: ID 0846:6a00 NetGear, Inc.
Bus 001 Device 001: ID 0000:0000

I got the driver of the netgear website, and i followed the steps from the wiki.
Could it be something to do with the version of ubuntu i'm running?[/QUOTE]


Netgear wg111v2 USB is supported in Dapper. I'm using it right now. You don't need ndiswrapper.

---

### Post by irw on 2006-06-05
How did you get it running without ndiswrapper?

I've finally got it working - with ndiswrapper - I'll post the steps I took in a minute

---

### Post by bsell on 2006-06-05
[QUOTE=irw]How did you get it running without ndiswrapper?

I've finally got it working - with ndiswrapper - I'll post the steps I took in a minute[/QUOTE]
 
I configured it with Networking in Administration. It was as easy as setting up ethernet. Just make sure wlan0 is the default gateway and the connection is enabled. NETGEAR should appear in the drop down essid menu in Properties.

This is the first distro I've never had to use ndiswrapper with my USB wireless.

---

### Post by irw on 2006-06-05
I've cracked it!!! =D> 

From a clean Dapper install:

```
sudo gedit /etc/modprobe.d/blacklist 
```

At the end of that file I added:```
blacklist r8187
blacklist islsmusb
blacklist islsm
blacklist islsm_usb
```

I then installed ndiswrapper, and the WinXP driver, followed by
```
sudo ndiswrapper -i /*path-to-driver*/net111v2.inf.inf
sudo depmod -a
sudo modprobe ndiswrapper
```

At this point wireless worked :p 

I rebooted, and it didn't:( 

However, ```
sudo gedit /etc/modules
``` and add ```
ndiswrapper
``` to the end of the file, save reboot ...

and it works!!:grin: =D>

However, out of interest, I may got back to the fresh install and try what you say.

---

### Post by irw on 2006-06-05
Back to my original question,  I wonder whether it is all down to driver conflicts, and blacklisting certain ones is the key.

Is there a list anywhere of the drivers present, the devices they support?

---

### Post by bsell on 2006-06-05
[QUOTE=irw]Back to my original question,  I wonder whether it is all down to driver conflicts, and blacklisting certain ones is the key.

Is there a list anywhere of the drivers present, the devices they support?[/QUOTE]

You can check in Device Manager to see if your devices are supported. 

You can use the Live Dapper CD to verify if your wireless will work (it should).  Configure it in Networking to see if you can get it up and running. If you can't, you might not want to reinstall.

---

### Post by Killerah on 2006-06-05
[QUOTE=irw]I've cracked it!!! =D>...[/QUOTE]
You sir, are my hero! Your method worked flawlessly! And I had given up all hope of it being fixed before I leave tomorrow. One thing would be awesome though, could you tell me how you figured out what to blacklist so that I can fix problems like that in the future?

Thanks
-Nate

---

### Post by tkoster on 2006-06-05
I had the wireless working briefly with bcm43xx driver and at first it died intermitently. But then it wouldn't come back at all so I switched back to the ndiswrapper and it started doing the same thing. 

After hours of experimenting, I found that for some unexplainable reason the "essid" setting was turning off.

sudo iwconfig eth1 essid on 

fixed the problem, at least temporarily. Any ideas as to why this setting would be unstable?

---

### Post by irw on 2006-06-06
my blacklist was based on trawling through the fora; r8187 came up as problems when I looked at the output of dmesg, islsm I saw mentioned a couple of times, so thought I would try it - nothing too scientific!!

---

### Post by gbw69 on 2006-06-13
Aaarg! I'm seriously lost...
After more than two weeks of trying everything i can find my hands on regarding this wireless, i've hit a dead end.
Maybe it something to do with the accesspoint setup, not sure.
I have the ndiswrapper installed and doing its job.
the wlan0 shows in system| admin | network
iwconfig wlan0 shows:

spankass@spankass:~$ sudo iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:2432 B   Fragment thr:2432 B
          Encryption key:off
          Power Management max timeout:0us  mode:All packets received
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

this would be the final step, i hope.
please can someone help me?;)

---

### Post by bsell on 2006-06-13
What wireless card are you using? Have you scanned for available networks?

---

### Post by gbw69 on 2006-06-13
Hi
I'm using a netgear wg111v2 usb dongle

the scan reads:
spankass@spankass:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:13:A3:98:0F:89
                    ESSID:"SpeedStream"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-84 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0

it seems that it does pickup the router.

I cant get the card to associated with the router.

spankass@spankass:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:13:A3:98:0F:89
                    ESSID:"SpeedStream"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-87 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0

spankass@spankass:~$ sudo iwconfig wlan0 essid "SpeedStream" commit
spankass@spankass:~$ sudo iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:2432 B   Fragment thr:2432 B
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

neither does:

spankass@spankass:~$ sudo iwconfig wlan0 AP 00:13:A3:98:0F:89 commit
Password:
spankass@spankass:~$ sudo iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:2432 B   Fragment thr:2432 B
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Any ideas?

---

### Post by bsell on 2006-06-14
Did you try:

System>Administration>Networking

In the dialog box, click on the wireless connection Properties. Next to the Network Name, click on the drop down menu and see if your network is listed.

---

### Post by Sasquatch2000 on 2006-06-14
You guys might want to go here and read (and VOTE!):

[[wireless] Ubuntu 6.06 - Dapper Drake 6.06: "Improved Wireless Support"](http://ubuntuforums.org/showthread.php?t=191557)

---

### Post by gbw69 on 2006-06-14
[QUOTE=bsell]Did you try:

System>Administration>Networking

In the dialog box, click on the wireless connection Properties. Next to the Network Name, click on the drop down menu and see if your network is listed.[/QUOTE]

Yes, its listed.
the trouble shooting guide suggests that i'm not assosiated/connected to a router. not sure what that means. Is it a command that i have to run "sudo iwconfig wlan0 ap "networkname or router name or router mac" , i posted the result of these commands on a previous post.
it would seem that the system doesn't change anything when i run these commands.
does this happen to anybody else?:?: :confused:

---

### Post by 11hjpphty76lkjj on 2006-06-14
I've found that directly configuring the /etc/network/interfaces file was a lot easier than trying to use the gui tools for some reason.

```

# The primary network interface


iface eth1 inet **dhcp**
**wireless-essid XXXXXXXXXXX**
**wireless-key XXXXXXXX**

auto eth1


```

Just change the eth1 to your wifi card, ie run ifconfig and it should be clear.

Change the wireless-essid to your wifi router, change the wireless-key XXXX to your wep key, if needed.

save, exit.

sudo /etc/init.d/network restart

it should connect, claim an IP, and be on the network. 

in a perfect world of course...your mileage may vary, objects in mirror are closer than they appear, etc, etc.

:-({|=

---

### Post by javaJake on 2006-06-14
[QUOTE=kalosaurusrex]I've found that directly configuring the /etc/network/interfaces file was a lot easier than trying to use the gui tools for some reason.[/QUOTE]I have also found this. If only their implementation would be better...

It doesn't even tell you if something went wrong when connecting. It even says that the device is activated! Is there a bug report about this already?

---

### Post by 11hjpphty76lkjj on 2006-06-14
I'm not sure, but someone should submit something.

searching:

[https://launchpad.net/distros/ubuntu/+search?text=wireless](https://launchpad.net/distros/ubuntu/+search?text=wireless)

I found several wifi areas, but I'm not clear as to what area the defect should be submitted.  seems like there needs to be a ubuntu wifi team dedicated to wireless issues and for pushing for a more solid wifi solution...

---

### Post by bsell on 2006-06-14
[QUOTE=gbw69]Yes, its listed.
the trouble shooting guide suggests that i'm not assosiated/connected to a router. not sure what that means. Is it a command that i have to run "sudo iwconfig wlan0 ap "networkname or router name or router mac" , i posted the result of these commands on a previous post.
it would seem that the system doesn't change anything when i run these commands.
does this happen to anybody else?:?: :confused:[/QUOTE]

What happens when you click on your network name to set it as your essid? Does it activate your wireless interface?

---

### Post by gbw69 on 2006-06-15
[QUOTE=bsell]What happens when you click on your network name to set it as your essid? Does it activate your wireless interface?[/QUOTE]

Nothing happened at first, then i tried unplugging it and when plugged it back in my laptop hung solid. On restarting the network module failed and i tried undoing what i did last and unplugging the dongle the network manager says there are no network devices but ifconfig says gives me the lan0 settings correctly but no wlan0 neither does iwconfig.
I'm gona start from the begining to see if it might be the procedure i followed.:sad:

Interesting!
removed the ndiswrapper driver, undid the black list settings and uninstalled network-manager, then it worked with the native driver only for about 10-20 seconds then the system hangs.
gona try the ndiswrapper setup again.

Yup, its not that. I get the same result.
Why would the system hang when i use the native drivers?

---

### Post by gbw69 on 2006-06-15
Anyway its working now with the native drivers.
at least i know how to troubleshoot some things and have a better understanding of how linux works.
Thanks to everone who steered me in the right direction.;)

---

### Post by irw on 2006-06-15
Throughout all of this, I have never got Network-manager to work; wifi-radar works fine for connection to different networks though.

I've just cracked my other problem now as well - I can now also dial-up via my mobile phone to check for emails etc when away from home .. I'm having a successful couple of weeks.  Next step: update my desltop PC to dapper - I rely on that so much, I am more nervous about that step than messing around with the laptop!

---

### Post by matlock on 2006-06-16
[QUOTE=gbw69]Anyway its working now with the native drivers.
at least i know how to troubleshoot some things and have a better understanding of how linux works.
Thanks to everone who steered me in the right direction.;)[/QUOTE]

Could you tell me how you got it working?
iwlist shows me my Network(sometimes) and the hardware is found and everything, but somehow it doesn't work with native drivers. Maybe you have the right solution for my problem.

---

### Post by bsell on 2006-06-17
[QUOTE=matlock]Could you tell me how you got it working?
iwlist shows me my Network(sometimes) and the hardware is found and everything, but somehow it doesn't work with native drivers. Maybe you have the right solution for my problem.[/QUOTE]
 
Try System>Administration>Networking

The thread OP was a discussion on how to get the Netgear wireless USB (WG111v2) working in Dapper, which has native Linux drivers for it. Using ndiswrapper creates a lot of problems when a native driver is also being used.

---

### Post by irw on 2006-06-17
whether or not Dapper has native drivers for this, it didn't work for me without ndiswrapper. 

System>Administration>Networking -> no wireless device listed, so making rather difficult to progress from there.

---

### Post by dimeotane on 2006-06-18
Anyone else find that with a clean install of Dapper that when trying to use ndiswrapper to setup your wifi, you type into the command prompt:

sudo ndiswrapper -i ~/yourdriverpath/drivername.inf 

 (for me it's ~/drivers/bcmwl5.inf)

and ubuntu tells you "command not found"

I remember this working in breeze and hoary

---

### Post by gbw69 on 2006-06-19
[QUOTE=dimeotane]ubuntu tells you "command not found"

I remember this working in breeze and hoary[/QUOTE]

Look for ndiswrapper in your repository, you might just need to be installed.

---

### Post by gbw69 on 2006-06-19
[QUOTE=matlock]Could you tell me how you got it working?
iwlist shows me my Network(sometimes) and the hardware is found and everything, but somehow it doesn't work with native drivers. Maybe you have the right solution for my problem.[/QUOTE]
Basically it just worked! Do you have the same usb dongle as I and did you checkout the wifi troubleshooting quide in the ubuntu wiki?

---

### Post by Nrvnqsr on 2006-06-19
[QUOTE=irw]I've cracked it!!! =D> 

and it works!!:grin: =D>
[/QUOTE]

I would like to say I love you (platonically), my wifi works without me turning the power manually through terminal, though I must figure out how to get gnome network manager to connect.

thanks irw =D>

---

