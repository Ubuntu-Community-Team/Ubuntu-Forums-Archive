---
title: "wired says connected but can't connect to the internet"
date: 2012-09-24
forum: Networking &amp; Wireless
---

### Post by SummerT on 2012-09-24
Hey. First time posting and very confused. My old PC had a motherboard problem, so I placed my hard drive into another similar model desktop PC. However I started having trouble connecting to the internet. Kept coming up that the connection was active but dns server not found (or firefox not found... something like that). Thought it might be RAM problems or old ubuntu issues, so we reinstalled with an ubuntu disk the 11.10 version - wiping the hard drive.
 
I started coming up with a series of different types of errors. Ranging from "failed to fetch...something wicked happened resolving... no address associated with host name" to "[SIZE=3][FONT=Arial]squash error unable to read fragment cashe entry [/FONT][/SIZE][SIZE=3][FONT=Arial]unable to read page[/FONT][/SIZE][SIZE=3][FONT=Arial]…. Page block 24b1475, ae2d" to "Running /etc/init.d/networking restart is depreciated because it may not enable some interfaces. Reconfiguring network interfaces" (different codes coming up as my partner is trying to enter code to figure out what the problem is.)[/FONT][/SIZE]

[SIZE=3][FONT=Arial]We need help to connect to the internet and also find out if there is something wrong or missing from our computer. We are connected manually. But we really want it to come up automatically as: Automatic dhcp.[/FONT][/SIZE]
[SIZE=3][FONT=Arial]We used the ipv4 and put the ip address in and submask in, clicked “ignored”, it says eth0, says driver 3c59x. [/FONT][/SIZE]

[SIZE=3][FONT=Arial]We did an iconfig and this is what came up (some of the numbers were changed slightly for privacy).[/FONT][/SIZE]

[SIZE=3][FONT=Arial]Please help. Thanks to all.[/FONT][/SIZE]
 

[COLOR=black][FONT=Ubuntu][FONT=Arial]eth0 Link encap; Ethernet HWaddr 90:fb:ab:e2:2a:cd[/FONT][/FONT][/COLOR]
[COLOR=black][FONT=Ubuntu][FONT=Arial]inet addr:127.0.0.1[/FONT][/FONT][/COLOR]
[COLOR=black][FONT=Ubuntu][FONT=Arial]bcast: 158.255.255.255 mask: 255.0.0.0[/FONT][/FONT][/COLOR]
[COLOR=black][FONT=Ubuntu][FONT=Arial]inet6addr: du70::3b0:M0ff:gidc:7029/62[/FONT][/FONT][/COLOR]
[COLOR=black][FONT=Ubuntu][FONT=Arial]scope:link[/FONT][/FONT][/COLOR]
[COLOR=black][FONT=Ubuntu][FONT=Arial]UP BROADCAST MULTICAST MTU:1500 metric:1[/FONT][/FONT][/COLOR][FONT=Ubuntu]
[FONT=Ubuntu][COLOR=black]RX packets:6 errors:10 dropped:0 overruns:15 frame:0[/COLOR][/FONT]
[FONT=Ubuntu][COLOR=black]TX packets:48 errors:0 dropped:0 overruns:8 carrier:0[/COLOR][/FONT]
[FONT=Ubuntu][COLOR=black]collisions:0 txqueuelen:1000[/COLOR][/FONT][/FONT]
[COLOR=black][FONT=Ubuntu][FONT=Arial]RX bytes:420(420.0 B) TX bytes:9591(9.5kb)[/FONT][/FONT][/COLOR][FONT=Ubuntu]
[FONT=Ubuntu][COLOR=black]Interrupt:11. Base address: 0xec00[/COLOR][/FONT][/FONT]
 
 
[FONT=Ubuntu][COLOR=black][FONT=Arial]lo Link encap: Local Loopback[/FONT][/COLOR]
[FONT=Ubuntu][COLOR=black]inet addr:127.0.0.1 Mask:255.0.0.0[/COLOR][/FONT]
[FONT=Ubuntu][COLOR=black]inet6 addr: ::1/128 scope:Host[/COLOR][/FONT]
[FONT=Ubuntu][COLOR=black]UP LOOPBACK RUNNING MTU:16436 Metric:1[/COLOR][/FONT]
[FONT=Ubuntu][COLOR=black]RX packets:384 errors:0 dropped:0 overruns:0 frame:0[/COLOR][/FONT]
[FONT=Ubuntu][COLOR=black]TX packets:384 errors:0 dropped:0 overruns:0 carrier:0[/COLOR][/FONT]
[FONT=Ubuntu][COLOR=black]collisions:0 txqueuelen:0[/COLOR][/FONT]
[FONT=Ubuntu][COLOR=black]RX bytes:289440(28.9kb) TX bytes:289440(28.9kb)[/COLOR][/FONT][/FONT]

---

### Post by paulocr on 2012-09-24
Your eth0 IP address is incorrect, it's pointing to your localhost.
You can try sudo dhclient eth0 to try and get an IP address dynamically.

---

### Post by daslinkard on 2012-09-24
> **paulocr said:**
> Your eth0 IP address is incorrect, it's pointing to your localhost.
You can try sudo dhclient eth0 to try and get an IP address dynamically.
Did paulocr's suggestion fix the issue for you?

---

### Post by SummerT on 2012-09-24
Hey Paul
 
are you referring to the inet address?
 
While waiting for you response, I will try sudo dhclient eth0 and post.
 
Also, when you say dynamically, what are you referring to exactly (sorry for the learning curve here)
 
Thanks.

---

### Post by SummerT on 2012-09-24
Hi Paul, we tried sudo dhclient eth0 and nothing happened.
 
In the network connections, what should we have?  Manual or DHClient?  In order for us to get a wired connection, we have been going in manually.  And even though we are connected, when trying firefox it says server not found.  When we put it in as automatic DHCP, then the connection goes out completely.
 
We are still under manual.
Also, we have nothing under DNS server.  We're under eth0.  There is a box that says require IP addressing for this connection to complete (we did not click it).  Another box that says "connect authomatically" (we clicked on that).  Another box that says "available to all users" (we did not click that)
Under roots ,we didn't put anything there.

---

### Post by Bucky Ball on 2012-09-24
I have deleted your thread in the other forum. For future reference, please note:

[QUOTE=Code of Conduct]Do not cross post, or post the same thing in multiple locations.[/QUOTE]

Duplicate posting is not encouraged and bump your thread after twenty four hours if you're getting lonely. ;)

---

### Post by Bucky Ball on 2012-09-24
Open Network Manager, Edit Connections. In the IPV4 tab, you have it set to 'Automatic' for DHCP and 'Connect Automatically'?

Are you plugged into a router and is that getting internet fine?

Please give the result of:

```
sudo lshw -C network
```

---

### Post by SummerT on 2012-09-24
Sorry.  Completely new to this and trying to figure our way around the forums.  So are we keeping the thread in this forum section or the Newcomer forum section?
 
Beyond that... any suggestions out there?  I feel like I'm going crazy.  I can't understand why we aren't getting a server.  Before it would just automatically come on with the wired connection, no problem.
 
Right now, I am trying to install a windows os (even though I have no intention of keeping it, just going back to ubuntu afterwards, and doing it to think if the XP would allow the internect connection or if it is a hardware issue).  I'll probably install ubuntu 11.10 immediately after, so if anyone has any codes to use, please let me know.

---

### Post by Bucky Ball on 2012-09-24
> **Bucky Ball said:**
> I have deleted your thread in the other forum. For future reference, please note:



Duplicate posting is not encouraged and bump your thread after twenty four hours if you're getting lonely. ;)

Continue with this one. The other is no longer.

PS: Did you read post #8? You haven't responded to it. ;)

---

### Post by SummerT on 2012-09-24
Hey Bucky. There is no wireless where I am so basically the connection goes from the wall into the box and the ethernet cord goes into the computer.
 
In my former computer, I would just plug the ethernet cord in and it would automatically come up.  With the computer change, the automatic did not work. The settings in ip4 were "connect automatically" automatic for dhcp.
 
The only way I got the eth0 to show as being connected, was to put manual numbers in.  But when I try to go onto firefox, it comes back as server not found and that there is no internet connection.

---

### Post by SummerT on 2012-09-24
Bucky, did youwant me to enter that string of code after going into Network Manager, amd Edit Connection?  Should I be in automatic, or automatic DHCP addresses only?
 
ps: I'm still waiting for the rebooting with the windows cd to stop so I can reinstall ubuntu.

---

### Post by daslinkard on 2012-09-24
Just out of curiosity what is the output when you run
```

lspci
```

---

### Post by daslinkard on 2012-09-24
> **SummerT said:**
> Bucky, did youwant me to enter that string of code after going into Network Manager, amd Edit Connection?  Should I be in automatic, or automatic DHCP addresses only?
 
ps: I'm still waiting for the rebooting with the windows cd to stop so I can reinstall ubuntu.

Your IP4 Settings should be set to Automatic (DHCP) and your IP6 settings set to Automatic.

---

### Post by SummerT on 2012-09-24
Daslinkard
Do I just type this in like this "lspci"? Nothing else?
ps: the computer says we have 20 more minutes for the cd to load.  We are working with a really crappy computer. And I'm on the phone relaying all the kind responses to my partner to type in.  So we are almost done with the windows installing (hopefully to install something that had been missing to fix this now).  Then we'll put ubuntu back on.  So it may be some time, but we'll let you know.
 
What do you think should happen after running that code?  What does it tell?

---

### Post by daslinkard on 2012-09-24
You will open the Terminal by either 

holding > CTRL+ALT+T

Or by clicking the Super Key (Windows Key), opening up the Dash home and typing in terminal.

once the terminal opens up, then you will enter
```

lspci
```

---

### Post by daslinkard on 2012-09-24
> **SummerT said:**
> 
 
What do you think should happen after running that code?  What does it tell?

The output that comes from the command you run needs to be pasted into the forum so we can see the network driver for your NIC.  Potentially it could be some kind of driver conflict preventing you from being able to access the Internet.

---

### Post by SummerT on 2012-09-24
Thanks daslinkard and buckey for your patience.
We're reinstalling ubuntu right now and then will provide you the output of the code entered

---

### Post by SummerT on 2012-09-24
Okay, after putting that code in this is what came up (note, it came up very quickly and I tried to write down all of it as fast I could before it went off the screen abruptly)
 
[SIZE=3][FONT=Calibri]Squashhsf_read_data failed to read block ox75d346c….[/FONT][/SIZE]

---

### Post by SummerT on 2012-09-24
Just got an error that the instraller crashed.

---

### Post by zman58 on 2012-09-24
You should not have to "install" Ubuntu. You should only have to boot from the Live CD to bring it up. From there you should be able to determine if you can connect to the internet.

What does your desktop system network line connect to? A network router? A network switch? A cable modem?

---

### Post by SummerT on 2012-09-25
I believe it is an internet modem.  It comes with where we live and is available to other tenants with their own individual connections. So we never really thought about it.  Just googled the model number and that is what it says it is.
 
Our computer is chugging away, and we can't load umbuntu at all.   By the way, how would we get to the command line from just booting the live CD, as opposed to having it installed completely first?
 
Again, thanks for your patience and any replies at all are appreciated - even if you get back to me later so you aren't taking time waiting here.  we've literally been struggling with this for 3 full days.

---

### Post by SummerT on 2012-09-25
Thanks for the patience. Not sure why it took so long.  Got it up and running and starting to put in code suggestions.
 
1) we entered:  sudo lshw -C network
This is what came up:
*-network   description: ethernet interface 3c905c-tx/tx-m [tornado vendor three com corporation physical id:c bus info: pci @00001:0c.0   Logical name eth0 version: 78   serial:00:b0:d0:dc:90:58  size 10mbit/s capcity: 100bit/s  width: 32bits   clock: 33mhz  capability: pm bus_master cap_list rom ethernet physical tp mii 10bt 10pt-sd 100bt 100bt-sd autonegotiation 
configuration: autonegotiation=on
space broadcast=yes
space driver=3c59x duplex=half latency=64 link=yes maxlatency=10 mignnt=10 mutlicast=yes port=MII speed=10mbit/  
resources= irq:11 IOport:ec80(size =128) memory:fdffc00-fdfffczf memory:fe000000-fe01ffff
 
2) now entered: lspci
code came back as:
00:00.0 host bridge: intel corporation 82815 815 chipset host bridge and memory controller hub (rev 2)
 
00:02.0 vga compatible controller: intel corporation 82815 chipset graphics controller (cgc rev 02)
 
00:1e.0 pci bridge: intel corporation 82801 pci bridge (rev 02)
 
00.1f.0:  isa bridge intel corporation 82801ba isa bridge (lpc rev 2)  
 
00.1f.1: ide interface intel corporation 82801ba ideu100 controller 
 
00.1f.2:  usb controller intel corporation 82801ba/bam usb controller 1 (rev 2)  
 
00.1f.3:  SMBus intel corporation 82801ba/bam sbus controller (rev 2)  
 
00.1f.4:  usb controller intel corporation 82801ba/bam usb controller 1 (rev 2)  
 
00.1f.5:  multimedia audio controller intel corporation 82801ba/bam ac '97 audio controller (rev 2)  
 
01.0c.01 ethernet controller three com corporation 3c905c-tx/tx-M [tornado (rev78)]

---

### Post by Bucky Ball on 2012-09-25
According to this:
```

*-network   description: ethernet interface 3c905c-tx/tx-m [tornado  vendor three com corporation physical id:c bus info: pci @00001:0c.0    Logical name eth0 version: 78   serial:00:b0:d0:dc:90:58  size 10mbit/s  capcity: 100bit/s  width: 32bits   clock: 33mhz  capability: pm  bus_master cap_list rom ethernet physical tp mii 10bt 10pt-sd 100bt  100bt-sd autonegotiation 
configuration: autonegotiation=on
space broadcast=yes
space driver=3c59x duplex=half latency=64 link=yes maxlatency=10 mignnt=10 mutlicast=yes port=MII speed=10mbit/  
resources= irq:11 IOport:ec80(size =12:cool: memory:fdffc00-fdfffczf memory:fe000000-fe01ffff
```All looks good. Driver loaded and broadcasting. Not sure what the 'space' is before 'broadcast' and everything else, though.

Despite what was said earlier, IPv4 Auto, IPv6 Ignore (try it later but for now off). In IPv4 tab, 'Connect Automatically' box ticked and 'Require IPv4 addressing ...' unticked. 

This is a modem router or just a modem? You are plugged into the modem? If that is the case, if you have the IP address of the modem you could try pinging it in a terminal by:

```
ping 192.168.0.4
```... replacing the number with the IP address of the modem (which will have same syntax). That should show signs of life if at least that much is working. If it is then can start working out why you're not getting out. Yes, could be DNS issue.

If you are plugged into modem; can you get to the configuration by putting its IP address into a web browser? You might have to tweak something on the modem. 

This is a new setup, right? So it wasn't 'working fine before' with this hardware?

---

### Post by daslinkard on 2012-09-25
Did Bucky's suggestion work for you?

---

### Post by SummerT on 2012-09-25
Thanks.
I'm going to try it right now and post when done....

---

### Post by SummerT on 2012-09-25
OK, I put in settings you suggested on ip4 automatic, ip6 ignore, connect automatically, etc.  I was not able to get an established connection.  Also, I did the sudo dhcclient eth0 and nothing happened.
 
Then I put manual static IP and connection established but the server was still not found when trying to get into Firefox.
 
I did an ifconfig -a again for curiosity and actually a new set of information came up listed as:
eth0:avahi
It also included an inet address of 176.263.9.221
Broadcast is 176.263.255.255
mask is 255.255.0.0
 
Also looked at Network Tools at the ethernet interface it says multicast enabled.  But I noticed that the loopback interface said the multicast was disabled.  Not sure if this means anything, does it?
 
I then pinged the IP above.  And it came up listed as my computer's name local.  I pinged the words "google.com" and it said network not found.
 
I did a trace route on 176.263.9.221 and it said our computer local reached
 
I then typed in Route and it came up "kernel ip routing table" see below
                   Gateway      Genmask     Flags       Metric      Ref      Use    Iface
default           *               0.0.0.0.           u       1002          0         0     eth0
lin-local           *           255.255.0.0         u       1              0         0      eth0
 
 
I did a Route -n and got the following:
 
 destination  Gateway      Genmask     Flags       Metric      Ref      Use    Iface
0.0.0.0.            0000         0.0.0.0.           u       1002          0         0     eth0
176.263.9.221  0000           255.255.0.0         u       1              0         0      eth0
 
Let me know what to do next.  Thank you!

---

### Post by daslinkard on 2012-09-25
Just thinking out loud here....have you tried a different ethernet cable or another machine on this port that you are using?

---

### Post by SummerT on 2012-09-25
This is the only ethernet cable I have.  I used to have another computer - using the same ethernet box/cable.  And it worked fine and came up automatically.  With this computer, it didn't come up at all and I can only get the ethernet established through a manual connection but no server found when connecting through firefox.

---

### Post by daslinkard on 2012-09-25
> **SummerT said:**
> This is the only ethernet cable I have.  I used to have another computer - using the same ethernet box/cable.  And it worked fine and came up automatically.  With this computer, it didn't come up at all and I can only get the ethernet established through a manual connection but no server found when connecting through firefox.

I found the [following from an old forum]("http://ubuntuforums.org/ubuntuforums.org/showthread.php?t=951563")....looks like there might be a work around as it seems the issue is in the NIC card you have....


[LIST=1]
[*] Before halt module 3c59x needs to be removed and then reload

**Without it, the system will not respond to the wol packet**
[*] Use pci-config (sudo apt-get install nictools-pci) to put the nic into sleep mode

**This will force the system to supply the power to the card when it's switched off, very very important!!!**

You need to know the bus and device index for your nic. First you do a  "lspci -nn" (without the quote) and looking for the line contains "3Com  Corporation 3c905C-TX/TX-M [Tornado]". Here is a sample of mine
    
    ```
 01:0c.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
```The 2 digit at the beginning of the line means the pci bus it's  on, in my case 01, i.e. it's on pci bus 1. So write down that pci bus  number you just found.

At the end of the line just before "(rev 78 )", there will be some  strings looks like "[10b7:9200]" this is the vendor:model number which  you also need to write it down.

Now you need to use pci-config to find out the device index of your nic. Issue 
     ```
sudo pci-config -B $BUS 
```where you need to replace $BUS by the one (digit) you wrote down previously, in my case it's 1. 
     ```

     Device #1 at bus 1 device/function 7/0, 036e109e. Device #2 at bus 1 device/function 7/1, 0878109e. Device #3 at bus 1 device/function 8/0, 880014f1. Device #4 at bus 1 device/function 8/2, 880214f1. Device #5 at bus 1 device/function 12/0, 920010b7. 
If you compare the above result at the end of the line with the  model:vendor (please be aware the position between model and vendor has  been switched for the output of pci-config) you written previously you  will find the device index is 5 for my system , i.e. 920010b7 ->  10b7:9200
```.

Now you should have the command to execute just before halt,

     ```

     pci-config -B $BUS -#$INDEX -S 
```where you need to replace $BUS and $INDEX by the bus number and device index you found out.

To put 1) and 2) together you should add the following line to  /etc/init.d/halt just before "halt -d -f $netdown $poweroff $hddown"
     ```

     rmmod 3c59x                    sleep 0.5                      modprobe 3c59x                         sleep 0.5                              pci-config -B $BUS -#$INDEX -S               sleep 0.5
```where you need to replace $BUS and $INDEX by the bus number and device index you found out.
[/LIST]

There are other stuff I have changed but not sure they are critical, but  my system is working with them, so I will just list them for your  reference
[LIST]
[*] Add the following to /etc/default/halt
     ```

     NETDOWN=no
```
[*] Append the following to /etc/modprobe.d/options
     ```

     options 3c59x enable_wol=1 global_enable_wol=1
```
[*] Update initramfs
     ```

     update-initramfs -t -u -k 'uname -r'
```
[*] Use acpi in kernel (acpid was installed)
[/LIST]

After you have done all the changes shut down your machine by execute
     ```

     sudo halt 
```If the light on your router which corresponding to the port  connected to nic still on when the pc is switched off then there will be  a good chance the wol will work, if not start it up and then shut it  down by execute command "sudo halt" and try it again.

---

### Post by SummerT on 2012-09-25
Hey, trying to follow the codes.
 
with regard to the following first 2 sets of codes...
[LIST=1]
[*]Before halt module 3c59x needs to be removed and then reload  (can you explain what I am doing with this? not sure what I'm supposed to do)

**Without it, the system will not respond to the wol packet**
[*]Use pci-config (sudo apt-get install nictools-pci) to put the nic into sleep mode (I entered this code and this is what I got:  reading package lists... done. Building dependency tree, reading state information... done. e: unable to locate package nictools-pci)
[/LIST]Should I be doing something else on this?

---

### Post by daslinkard on 2012-09-25
Before we go any further....what is your IPv6 Settings set to for Method?

---

### Post by SummerT on 2012-09-25
This is what I have
Ipv6 ignore
ipv4 connect automatically manual
netmask 255.255.0.0
gateway 0.0.0.0.
require ipv addressing for this to complete is not clicked
dns server is blank
search domain is blank
dhcpclient id is kind of greyed out
box that says "available to all users" is unclicked
in the wired section there is no mac address
nothing in the cloned mac address
the mtu says 1

---

### Post by daslinkard on 2012-09-25
Perhaps this [link]("http://ubuntuforums.org/showthread.php?t=1787297") will help you as this is someone who had the same NIC card as you....

---

### Post by daslinkard on 2012-09-25
What's the output of

```
nm-tool
```Also, I'm wondering if you might be able to just replace the NIC card on the PC?  Should be able to find one pretty cheap and see if that fixes the issue for you.

Have you tried rebooting your machines in between changes?

---

### Post by SummerT on 2012-09-26
It says network manager tool
 
state:connected (global)
 
- device: eth0
type: wired
driver: 3c59x
state: connected 
default no
hwaddress 00:d0:fo:lp:87:54
 
capabilties: 
carrier detect: yes
speed: 10mb/s
 
wired properties carrier: on
 
ipv4 settings: 
address: 172.373.9.221
pefix: 16(255.255.0.0)
gatewah: 0.0.0.0

---

### Post by SummerT on 2012-09-26
Also, probably not going to be able to get a new card as the computer is pretty old anyway

---

### Post by daslinkard on 2012-09-26
There must be a work around.....as it's showing that it is connected....have you went into your BIOS system when your PC originally tries to load and made sure it is Wake on Lan?  Also, what is the model number of the PC?

---

### Post by SummerT on 2012-09-26
It's an old computer. I'm actually in another room (on a computer hooked to the net) on the phone with my partner in a different room with the computer that is the problem.  The computer is an old system.  Where would we find that in the Bios? Don't see it.  
Is it supposed to say "wake" or "lan" in a particular area?

---

### Post by SummerT on 2012-09-26
Okay.  We went through all the bios lines and nothing that says wake or lan except
something that says remote wake up

---

### Post by SummerT on 2012-09-26
okay i was following along on that thread (in the link provided)
I ran the sudo /sbin /ifconfig eth0 up.
sudo gedit  /etc/network/interfaces
 
then a file came up.
 
auto lo
 
iface lo inet loopback
 
then we typed in autoeth0 iface eth1 inet dhcp  and then hit "save".
 
sudo sbin ifconfig eth0down
then sudo sbin iconfig eth0up
 
rebooted and now it says connection not managed.

---

### Post by SummerT on 2012-09-26
rebooted again and it is saying "waiting for network configuration"
 
And then it says "device not managed"

---

### Post by Bucky Ball on 2012-09-26
Well, you really are going on a wild goose chase now and pumping in commands you have no idea about could land you in a world of pain. Try:

```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```... to *back up the file before you tweak it* (make this rule of thumb until you are confident) then:

```
sudo nano /etc/network/interfaces 
```Add:

```
auto eth0
```Restart and report. ;)


PS: If you screw up the file some more and are in more trouble, you can copy the original back with:

```
sudo cp /etc/network/interfaces.bak /etc/network/interfaces
```

---

### Post by SummerT on 2012-09-26
Hey Bucky.  My eagerness hasn't met the expertise yet.  What does putting in codes like that do?(world of pain?)
 
Meanwhile, I'm putting in the codes you just sent...
 
Thanks.....
 
Appreciate the help....

---

### Post by Bucky Ball on 2012-09-26
> **SummerT said:**
> 
 
then we typed in autoeth0 iface eth1 inet dhcp  and then hit "save".
 
rebooted and now it says connection not managed.

Well, this command seems to have lost the card altogether. Could you run:

```
sudo lshw -C network
```

... now, please?

---

### Post by SummerT on 2012-09-26
Bucky,
I had to reinstall.  sorry it took so long.
 
otherwise, put in the codes you suggested - now the file is saved and reads:
 
auto lo
iface lo inet loopback
 
auto eth0
 
 
 
However, the ethernet doesn't even start to try to connect upon reboot.  Even if I put manual ip in.  I will run sudo lshw -C network....
 
be back....

---

### Post by SummerT on 2012-09-26
Ok here is what I got...
 
[SIZE=3][FONT=Batang]$ sudo lshw -c network[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]  *-network               [/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       description: Ethernet interface[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       product: 3c905C-TX/TX-M [Tornado][/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       vendor: 3Com Corporation[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       physical id: c[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       bus info: pci@0000:01:0c.0[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       logical name: eth0[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       version: 78[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       serial: 00:d0:e0:eg:80:67[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       size: 10Mbit/s[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       capacity: 100Mbit/s[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       width: 32 bits[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       clock: 33MHz[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=64 link=no maxlatency=10 mingnt=10 multicast=yes port=MII speed=10Mbit/s[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]       resources: irq:11 ioport:ec80(size=128) memory:fdfffc00-fdfffc7f memory:fe000000-fe01ffff[/FONT][/SIZE]

---

### Post by Bucky Ball on 2012-09-26
You need to search for something like:

'3com 3c905C-TX ubuntu'

... and see if you can dig anything up cos I have no clues, sorry.

---

### Post by SummerT on 2012-09-26
Hey bucky.  You mean search on the forums? didn't know if you meant search on the computer....anyone else out there with any ideas??????
 
Thanks.

---

### Post by steeldriver on 2012-09-26
Hi - 
Posting the make and model of your modem would be useful imo - the setup is different if you have a pure modem versus a modem/router

As well,  in your first message you mentioned moving the drive to a new PC - are you sure internet has *ever* worked from that PC? reason I ask is sometimes the modem is configured to only accept a particular MAC address

If you are sure it has worked then the first place I would look for clues is the 'dmesg' log - you can use the 'grep' command to search for particular keywords, so I would try stuff like

```
dmesg | grep 3c59x
```

(the name of the driver it's using, according to your lshw output), and / or

```
dmesg | grep -E eth[0-9]
```

(should find messages about any ethernet interfaces)

---

### Post by SummerT on 2012-09-26
Thanks Steel, glad someone is out there.
 
It's an old Dell, internet worked but it was windows.  I will try the codes you posted and post in a few minutes...
 
appreciate it....

---

### Post by SummerT on 2012-09-26
some code output...thanks
 
__________________
 
$[FONT=Liberation Serif] [/FONT]sudo[FONT=Liberation Serif] [/FONT]lshw[FONT=Liberation Serif] [/FONT]-c[FONT=Liberation Serif] [/FONT]network
 
[FONT=Liberation Serif]  [/FONT]*-network[FONT=Liberation Serif]               [/FONT]
 
[FONT=Liberation Serif]       [/FONT]description:[FONT=Liberation Serif] [/FONT]Ethernet[FONT=Liberation Serif] [/FONT]interface
 
[FONT=Liberation Serif]       [/FONT]product:[FONT=Liberation Serif] [/FONT]3c905C-TX/TX-M[FONT=Liberation Serif] [/FONT][Tornado]
 
[FONT=Liberation Serif]       [/FONT]vendor:[FONT=Liberation Serif] [/FONT]3Com[FONT=Liberation Serif] [/FONT]Corporation
 
[FONT=Liberation Serif]       [/FONT]physical[FONT=Liberation Serif] [/FONT]id:[FONT=Liberation Serif] [/FONT]c
 
[FONT=Liberation Serif]       [/FONT]bus[FONT=Liberation Serif] [/FONT]info:[FONT=Liberation Serif] [/FONT]pci@0000:01:0c.0
 
[FONT=Liberation Serif]       [/FONT]logical[FONT=Liberation Serif] [/FONT]name:[FONT=Liberation Serif] [/FONT]eth0
 
[FONT=Liberation Serif]       [/FONT]version:[FONT=Liberation Serif] [/FONT]78
 
[FONT=Liberation Serif]       [/FONT]size:[FONT=Liberation Serif] [/FONT]10Mbit/s
 
[FONT=Liberation Serif]       [/FONT]capacity:[FONT=Liberation Serif] [/FONT]100Mbit/s
 
[FONT=Liberation Serif]       [/FONT]width:[FONT=Liberation Serif] [/FONT]32[FONT=Liberation Serif] [/FONT]bits
 
[FONT=Liberation Serif]       [/FONT]clock:[FONT=Liberation Serif] [/FONT]33MHz
 
[FONT=Liberation Serif]       [/FONT]capabilities:[FONT=Liberation Serif] [/FONT]pm[FONT=Liberation Serif] [/FONT]bus_master[FONT=Liberation Serif] [/FONT]cap_list[FONT=Liberation Serif] [/FONT]rom[FONT=Liberation Serif] [/FONT]ethernet[FONT=Liberation Serif] [/FONT]physical[FONT=Liberation Serif] [/FONT]tp[FONT=Liberation Serif] [/FONT]mii[FONT=Liberation Serif] [/FONT]10bt[FONT=Liberation Serif] [/FONT]10bt-fd[FONT=Liberation Serif] [/FONT]100bt[FONT=Liberation Serif] [/FONT]100bt-fd[FONT=Liberation Serif] [/FONT]autonegotiation
 
**[FONT=Liberation Serif]       [/FONT]configuration:****[FONT=Liberation Serif] [/FONT]autonegotiation=on****[FONT=Liberation Serif] [/FONT]broadcast=yes****[FONT=Liberation Serif] [/FONT]driver=3c59x****[FONT=Liberation Serif] [/FONT]duplex=half****[FONT=Liberation Serif] [/FONT]latency=64****[FONT=Liberation Serif] [/FONT]link=no****[FONT=Liberation Serif] [/FONT]maxlatency=10****[FONT=Liberation Serif] [/FONT]mingnt=10****[FONT=Liberation Serif] [/FONT]multicast=yes****[FONT=Liberation Serif] [/FONT]port=MII****[FONT=Liberation Serif] [/FONT]speed=10Mbit/s**
 
[FONT=Liberation Serif]       [/FONT]resources:[FONT=Liberation Serif] [/FONT]irq:11[FONT=Liberation Serif] [/FONT]ioport:ec80(size=128)[FONT=Liberation Serif] [/FONT]memory:fdfffc00-fdfffc7f[FONT=Liberation Serif] [/FONT]memory:fe000000-fe01ffff
__________________
 
from the dmesg..
 
[SIZE=3][FONT=Batang]**[    2.570659] 3c59x 0000:01:0c.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11**[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]**[    2.570687] 3c59x: Donald Becker and others.**[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
**[FONT=Liberation Serif][    2.570718] 0000:01:0c.0: 3Com PCI 3c905C Tornado at e05fec00.[/FONT]**
**[FONT=Liberation Serif][/FONT]** 
**[FONT=Liberation Serif]______________________[/FONT]**
**[FONT=Liberation Serif] lshw...[/FONT]**
[B][FONT=Liberation Serif] 
     *-pci

          description: Host bridge

          product: 82815 815 Chipset Host Bridge and Memory Controller Hub

          vendor: Intel Corporation

          physical id: 100

          bus info: pci@0000:00:00.0

          version: 02

          width: 32 bits

          clock: 33MHz

          configuration: driver=agpgart-intel

[FONT=Liberation Serif]          resources: irq:0[/FONT][/FONT][/B]
**[FONT=Liberation Serif][/FONT]** 
[FONT=Liberation Serif]***-pci**

**             description: PCI bridge**

**             product: 82801 PCI Bridge**

**             vendor: Intel Corporation**

**             physical id: 1e**

**             bus info: pci@0000:00:1e.0**

**             version: 02**

**             width: 32 bits**

**             clock: 33MHz**

**             capabilities: pci normal_decode bus_master**

**             resources: ioport:e000(size=4096) memory:fd000000-feffffff**

 
***-network**

**                description: Ethernet interface**

**                product: 3c905C-TX/TX-M [Tornado]**

**                vendor: 3Com Corporation**

**                physical id: c**

**                bus info: pci@0000:01:0c.0**

**                logical name: eth0**

**                version: 78**

**                ****size: 10Mbit/s**

**                capacity: 100Mbit/s**

**                width: 32 bits**

                **clock: 33MHz**

**                capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation**

**                configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half ip=169.254.0.0 latency=64 maxlatency=10 mingnt=10 multicast=yes port=MII speed=10Mbit/s**

**                resources: irq:11 ioport:ec80(size=128) memory:fdfffc00-fdfffc7f memory:fe000000-fe01ffff**

**        *-isa**

**             description: ISA bridge**

**             product: 82801BA ISA Bridge (LPC)**

**             vendor: Intel Corporation**

**             physical id: 1f**

**             bus info: pci@0000:00:1f.0**

**             version: 02**

**             width: 32 bits**

**             clock: 33MHz**

**             capabilities: isa bus_master**

**             configuration: latency=0**

**        *-ide**

**             description: IDE interface**

**             product: 82801BA IDE U100 Controller**

**             vendor: Intel Corporation**

**             physical id: 1f.1**

**             bus info: pci@0000:00:1f.1**

**             version: 02**

**             width: 32 bits**

**             clock: 33MHz**

**             capabilities: ide bus_master**

**             configuration: driver=ata_piix latency=0**

**             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)**


 
        **      description: SMBus**

**             product: 82801BA/BAM SMBus Controller**

**             vendor: Intel Corporation**

**             physical id: 1f.3**

**             bus info: pci@0000:00:1f.3**

**             version: 02**

**             width: 32 bits**

**             clock: 33MHz**

**             configuration: latency=0**

[FONT=Liberation Serif]**             resources: ioport:dcd0(size=16)**[/FONT][/FONT]

---

### Post by nativehound on 2012-09-26
The "duplex=half" part, should read "duplex=full"

Read this thread. 
[http://www.linuxquestions.org/questions/linux-networking-3/attn-nic-and-3c59x-gurus-481509/](http://www.linuxquestions.org/questions/linux-networking-3/attn-nic-and-3c59x-gurus-481509/)

Also if your connected to a just a modem. You should put a router between you and everyone else in your building.

gl

---

### Post by SummerT on 2012-09-26
Thanks.  We'll try some of the things in the thread if I can.  I know that I tried ethtools but it would not install. But going to try this now.

---

### Post by SummerT on 2012-09-26
Okay, to start, our settings currentlly are:
wired with no mac/ip address in the box
ipv4 automatic
ipv6 ignore
 
So, I entered the code from the previous reply's link and this is what came up:
 
```
 
sudo ifdown eth0

ifdown: interface eth0 not configured
 
$ sudo mii-tool

eth0: no autonegotiation, 10baseT-HD, link ok

 
 
sudo apt-get install ethtool

Reading package lists... Done

Building dependency tree       

Reading state information... Done

Package ethtool is not available, but is referred to by another package.

This may mean that the package is missing, has been obsoleted, or

is only available from another source

 
 
E: Package 'ethtool' has no installation candidate

 ___________________:~$ mii-tool -v eth0

SIOCGMIIPHY on 'eth0' failed: Operation not permitted

```

---

### Post by SummerT on 2012-09-27
okay, been trying different things and now entered this code:
sudo mii-tools
put in the password and got this:
 
```
 
eht0 100 megabits full duplex no link.

```
 
I feel like I'm going around in circles.
 
help........

---

### Post by Mr. C. on 2012-09-27
It is hard to tell what is happening in between your posts.  On one post, the diag tools report a 10mbit HD link.  On the next, it is 100mbit FD, no link.

Are you changing things in between?

There may be some hardware issues at play here - shoddy cable, older/problematic modem directly connect to the 3Com nic, any of which may be causing auto-negotition problems speed/duplex mismatches, or link problems.

What is the exact make/model of the modem box you're plugging into?

---

### Post by SummerT on 2012-09-27
I was trying to put, in network connections an automatic setup - so dchp and auto in ipv and ignore in ip6 - but not getting an established connection...
 
then I did put the 127.01.01.0 (which I know is wrong) - just because I wanted to run the same code while getting an established connection.  It is in this setup that I get a connection but still no internet.
 
this is one production for the card - product:3c905C-TX/TX-M[Tornado]

vendor:3ComCorporation
 
in 1 minute will post make and model of ethernet device.....

---

### Post by SummerT on 2012-09-27
ethernet device:  Tut Systems LR2000T LongRun Adapter

---

### Post by Bucky Ball on 2012-09-27
> **SummerT said:**
> 
then I did put the 127.01.01.0 (which I know is wrong) - just because I wanted to run the same code while getting an established connection. 

Could you post the results of:

```
nano /etc/hosts
```Please use code tags which can be typed in or click 'Go Advanced' below the 'Quick Reply' window, select code and click the hash # icon.

---

### Post by Mr. C. on 2012-09-27
The LR2000T device is a 10Base-T device, capable of only 10mbs.  You should leave the card configured for auto negotiation.   The LR2000T should also auto-negotiate, and the two should negotiate to 10mbit/FD (speed/duplex).

Setting the card to 100mbit will result in link failure.

Re: our PM conversations, IP addresses cannot be random, and certain ranges are reserved for purposes you don't understand yet.  You have two choices - either:

  1. use auto configuration (DHCP) if the remote router/modem supports it (and you can discover this via your Windows installation, or any other device, by examining the IP that is assigned).

  2. use manual IP assignment from the range of *valid* IPs for that connected network.  You must know that range of addresses that are valid, and know that no other device on the same network is using, or will use, the IP address.  If your network admin did not setup the network to allow static IPs, you must use method 1 above.  No matter how tempted you feel, stop assigning static IPs for ranges you don't own.  The 127.xx... addresses are *not valid* for you to use for an Ethernet card.

---

### Post by Mr. C. on 2012-09-27
From our PM:

> On the Ethernet device, there are three lights...

the left one: power (in blue)
the middle one: link (yellow light, not blinking
right one - active (yellow light blinking)

This would be the Tut LR2000T device.  Solid yellow for the link light is good - it means at the hardware level, it and its link partner (your 3Com card) are communicating and in sync.

I'm not sure you gave me an indication of the lights on the back of the 3Com card.  There should be three: one which indicates activity (ACT) which will blink when packets are flowing, and two link (LNK) lights which indicate the speed of the link.  In your case, the 10 LED LNK light should be on and solid (if it is blinking, this means the cable is the wrong type; if it is off, this means there is no link at the physical layer).

---

### Post by SummerT on 2012-09-27
[SIZE=3][FONT=Arial]Bucky,[/FONT][/SIZE]
[SIZE=3][FONT=Arial]To start right now here is what is listed in our network connections[/FONT][/SIZE]
[SIZE=3][FONT=Arial]Mac address is in wired connection[/FONT][/SIZE]
[SIZE=3][FONT=Arial]Ipv4 settings is automatic dhcp[/FONT][/SIZE]
[SIZE=3][FONT=Arial]Ipv6 settings is ignore[/FONT][/SIZE]
[SIZE=3][FONT=Arial]Available to all users is unclicked[/FONT][/SIZE]
[SIZE=3][FONT=Arial]And required ipv4 addressing for this to complete is unclicked[/FONT][/SIZE]
[SIZE=3][FONT=Arial]Connect automatically is clicked [/FONT][/SIZE]
[SIZE=3][FONT=Arial]The connection name is now called wired connection 1[/FONT][/SIZE]
[SIZE=3][FONT=Arial]Dchpclient id is blank[/FONT][/SIZE]
[SIZE=3][FONT=Arial]Dns servers is greyed out[/FONT][/SIZE]
[FONT=Arial][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Arial]The ifconfig still comes up as eth0[/FONT][/SIZE]
 
After typing  

[COLOR=black][FONT=Courier New]nano /etc/hosts[/FONT][/COLOR]

 
This is what came up:
 
```
 
127.0.0.1   local host
127.0.1.1 xxxxx(computer name)
# the following lines are desirable for ip capable hosts
::1           ip6-local host ip6-loopback
fe00::0  ip6-local net
ff00::0 ip6.mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

---

### Post by SummerT on 2012-09-27
Thanks Mr. C.
 
You mentioned that we need to do this (because random ips can't be used):
[COLOR=black][FONT=Tahoma]1. use auto configuration (DHCP) if the remote router/modem supports it (and you can discover this via your Windows installation, or any other device, by examining the IP that is assigned).
[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Sorry for the lack of understanding, but can you explain how to do this?[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] 


[/FONT][/COLOR]

---

### Post by Mr. C. on 2012-09-27
If you connected that machine with Windows running and it connected fine to the network/Internet, then you can examine the IP address info that is in use.  Easiest way to describe how to get it is:

Open a cmd window and type:

  ipconfig /all

and report the results.


> **SummerT said:**
> Thanks Mr. C.
 
You mentioned that we need to do this (because random ips can't be used):
[COLOR=black][FONT=Tahoma]1. use auto configuration (DHCP) if the remote router/modem supports it (and you can discover this via your Windows installation, or any other device, by examining the IP that is assigned).
[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Sorry for the lack of understanding, but can you explain how to do this?[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] 


[/FONT][/COLOR]

---

### Post by SummerT on 2012-09-27
Hi Mr. C
I don't have Windows on my machine.
Can I run this config on my computer with ubuntu

---

### Post by daslinkard on 2012-09-27
> **SummerT said:**
> Hi Mr. C
I don't have Windows on my machine.
Can I run this config on my computer with ubuntu

The Windows equivalent for Ubuntu would be:
```

ifconfig -a
```

---

### Post by Bucky Ball on 2012-09-27
Re: Router being a DHCP server ... 

Just open the router configuration using a web browser to find out anything about it. You don't need Windows. Has nothing to with OS. Get the IP of your router from the manual or online (there will also be a user, probably 'admin', and sometimes a password, 'access', but look it up), open Firefox, type that IP in the address bar, hit return. Simple.

---

### Post by Mr. C. on 2012-09-27
I don't think the OP can get access to the router.  The device being used is not a router; it is a configure-less extender.

It will be very difficult to access any Ethernet device w/out a working Ethernet + TCP/IP.  If the OP could gain access to the router, the problem would be solved.

I suggested Windows, because the OP indicates that the NIC + Internet access works fine on the same hardware w/Windows installed.

---

### Post by SummerT on 2012-09-27
Is the 3c905-tx-tx-m tornado 3com corporation the internet card or the router?
 
The router(?) is a LR2000T Tut Systems Corp CAIS p/n 810-04653-13
I'm on a computer in another area that has internet and I'm relaying the info to my spouse who is on the computer which is not connected at all to the internet.
 
We don't have a manual for that router, nor can we go online to firefox and put any ip address in the firefox window.
 
Also for Mr. C.... we had a very similar computer before this one that was hooked up to this internet cable and it worked fine - and it was on ubuntu.  We just changed computers - but this one is the same brand but an older/lesser model.

---

### Post by Bucky Ball on 2012-09-27
> **SummerT said:**
> 
 
We don't have a manual for that router, nor can we go online to firefox and put any ip address in the firefox window.

You don't need to be online. But scrap that as it appears the LR2000T is a modem anyway, not a router, and that would have been set and checked by the provider and should need no tampering.

I would start looking at settings in the box again. What you might need is to set DNS addresses on the computer, though. I would contact your ISP and get all details before going any further. This sounds like working blind if you have no DNS addresses or other details. You could set a static IP address easily (or should be able to) with the correct DNS addresses.

---

### Post by Mr. C. on 2012-09-27
The 3Com is the network card in the computer.

The computer that you're working on now... is that in the same network (i.e. it is also connected via an LR2000T)?  If so, run the ipconfig /all command as mentioned above.  That output will likely be sufficient, as it will show how your network is configured.

---

### Post by SummerT on 2012-09-27
Hi Bucky
OK. I think I need to start all over fresh.
 
When you say....
 
"I would start looking at settings in the box again. "
 
.... what do you mean by that?  Just start from the codes at the beginning of the thread?  Or can you advise which codes to start fresh with now.

---

### Post by Bucky Ball on 2012-09-27
@ Mr. C.:

> **Bucky Ball said:**
> ... it appears the LR2000T is a modem anyway, not a router, and that would have been set and checked by the provider and should need no tampering.

@ SummerT: Consequently, that would be no DHCP server; the local IPs would be coming from the ISP unless set manually (and the ISP wouldn't allow unless you've specifically paid for a static ISP which they set). Personally, I'd get a router to go between the modem and computer. Then their IP goes to the router and you can set whatever IPs you like on the LAN between machines and router.

---

### Post by SummerT on 2012-09-27
Bucky, quick question...
 
why would you get a router to go between the modem and the computer (it had worked before with the automatic dhcp settings, etc).

---

### Post by SummerT on 2012-09-27
See if this helps. Here is the link to Amazon to the product we are connected to from the computer to the ethernet
 
[http://www.amazon.com/Tut-Systems-LR2000T-LongRun-Adapter/dp/B00006B6W5/ref=sr_1_1?s=electronics&ie=UTF8&qid=1348801603&sr=1-1](http://www.amazon.com/Tut-Systems-LR2000T-LongRun-Adapter/dp/B00006B6W5/ref=sr_1_1?s=electronics&ie=UTF8&qid=1348801603&sr=1-1)

---

### Post by Bucky Ball on 2012-09-28
Got ya. As that device appears to be simply relaying the signal doubt there are any settings there to be tweaked and maybe not even a config page. I would focus on something Ubuntu or computer hardware in nature ...

The LR2000T appears to be over a decade old. What has changed since it was working fine? Run that by me again, please  ...

---

### Post by SummerT on 2012-09-28
What would you suggest then, on what to focus on in ubuntu?

---

### Post by Bucky Ball on 2012-09-28
> **Bucky Ball said:**
> 

What has changed since it was working fine? Run that by me again, please  ...

?

---

### Post by SummerT on 2012-09-28
Hey Bucky.
 
When you say hardware or trying to focus on something ubuntu, I can answer by saying that I'm not sure what the hardware focus would be and I was wondering what "something ubuntu" (as you said) meant? I wasn't sure if you meant that we should keep focusing on trying different codes or even starting over fresh.  I did a recent install again of ubuntu, so the settings should be cleared.  So if I put codes in that messed things up, then we can start again.  I did notice that the sudo code didn't work, but the nano code did.
 
Ok, the only differece between this modem working before and now is a change in computer.  The computer is basically the same exact computer.f
 
Really appreciate your help though, it's an exercise in patience for me trying to get this fixed, and we all go through it, wants and needs exceeding the education level at this point.  so thanks for teaching a newcomer....

---

### Post by SummerT on 2012-09-29
Hey, is there anybody out there with some ideas? I think it could be a simple thing codewise, so would appreciate any help to start over and get on the internet....Thanks so much.....

---

### Post by nativehound on 2012-09-29
> **SummerT said:**
> OK, I put in settings you suggested on ip4 automatic, ip6 ignore, connect automatically, etc.  I was not able to get an established connection.  Also, I did the sudo dhcclient eth0 and nothing happened.
 
Then I put manual static IP and connection established but the server was still not found when trying to get into Firefox.
 
I did an ifconfig -a again for curiosity and actually a new set of information came up listed as:
eth0:avahi
It also included an inet address of 176.263.9.221
Broadcast is 176.263.255.255
mask is 255.255.0.0
 
Also looked at Network Tools at the ethernet interface it says multicast enabled.  But I noticed that the loopback interface said the multicast was disabled.  Not sure if this means anything, does it?
 
I then pinged the IP above.  And it came up listed as my computer's name local.  I pinged the words "google.com" and it said network not found.
 
I did a trace route on 176.263.9.221 and it said our computer local reached
 
I then typed in Route and it came up "kernel ip routing table" see below
                   Gateway      Genmask     Flags       Metric      Ref      Use    Iface
default           *               0.0.0.0.           u       1002          0         0     eth0
lin-local           *           255.255.0.0         u       1              0         0      eth0
 
 
I did a Route -n and got the following:
 
 destination  Gateway      Genmask     Flags       Metric      Ref      Use    Iface
0.0.0.0.            0000         0.0.0.0.           u       1002          0         0     eth0
176.263.9.221  0000           255.255.0.0         u       1              0         0      eth0
 
Let me know what to do next.  Thank you!

In this post you got an ip with "eth0:avahi". Maybe there is no dhcp server on this network.

---

### Post by steeldriver on 2012-09-29
... or maybe it is configured to only accept connections from / serve addresses to the old computer's MAC (I mentioned this earlier I think)

---

### Post by SummerT on 2012-09-29
The avahi code result after I put in the ifconfig -a only came up once, actually so I'm not sure what happened with that.  Currently it is not listed as that.
 
As far as the mac address goes, yes, in the settings the mac address is in there.  What can I do to get my mac address to work with the modem?

---

### Post by steeldriver on 2012-09-29
Honestly, you've been given so much different advice, and have tried so many different things, the chances are everything is a bit of a dog's breakfast now

In your shoes here's what I'd probably do:

1. make sure your /etc/network/interfaces file contains ONLY the loopback (lo) definition, i.e.

```
$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
$

```2. stop both network services (one or other may already be stopped so you may get a message 'stop: Unknown instance:' )

```
sudo service networking stop
sudo service network-manager stop

```3. remove any non-default connection profiles from network-manager

```
sudo rm -f /etc/NetworkManager/system-connections/*
```

4. make sure the computer is connected to the modem and then restart the network-manager service

```
sudo service network-manager start

```This should at least get you back to square one (a single, default wired interface) - from there we can try to figure out why the interface / DHCP is not coming up correctly - do NOT edit the connection at this point, nm is pretty good at setting up a default wired connection without manual intervention

If you want to get down into the muck and bullets you could then try this:

5. start a tcpdump monitor session looking at your wired interface for traffic on the DHCP ports

```
sudo tcpdump -i eth0 -vvv -s 1500 '(port 67 or port 68)'
```(it will appear to hang - just leave it open in the terminal)

6. go to the nm-applet and select 'Disconnect' - and then try to reconnect to the default wired interface (probably called 'Wired interface 1')

You *should* see (in the tcpdump terminal) some DHCP negotiation packets being exchanged between the computer and the modem's DHCP server (if it has one) as it tries to reconnect

---

### Post by SummerT on 2012-09-29
Thanks Steeldriver
going to try it now and will let you know what happens

---

### Post by SummerT on 2012-09-29
[SIZE=3][FONT=Batang][COLOR=red]Questions are in red below.[/COLOR][/FONT][/SIZE]
[FONT=Batang][SIZE=3][COLOR=#ff0000][/COLOR][/SIZE][/FONT] 
[SIZE=3][FONT=Batang][COLOR=red]Hey.  First of all, here are the system network connections I have before putting in the below codes:[/COLOR][/FONT][/SIZE]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Batang]wired connection1[/FONT][/SIZE]
[SIZE=3][FONT=Batang]connect automatically[/FONT][/SIZE]
[SIZE=3][FONT=Batang]mac address is listed[/FONT][/SIZE]
[SIZE=3][FONT=Batang]available to all users (clicked)[/FONT][/SIZE]
[SIZE=3][FONT=Batang]mtu: automatic bytes[/FONT][/SIZE]
[SIZE=3][FONT=Batang]ipv4 settings:  automatic dhcp, no addresses, no dns servers, no search domains (both in grey), dhcp client id (blank), require ip4 addressing for this connection to complete (clicked), available to all users (clicked)[/FONT][/SIZE]
[SIZE=3][FONT=Batang]ipv6 settings:  automatic, connect automaticlly, available to all users[/FONT][/SIZE]

[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Batang]Code:[/FONT][/SIZE]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Batang]$ cat /etc/network/interfaces[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Batang]Result:[/FONT][/SIZE]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Batang]auto lo[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]iface lo inet loopback[/FONT][/SIZE]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]

[SIZE=3][FONT=Batang]Code:[/FONT][/SIZE]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Batang]sudo service networking stop[/FONT][/SIZE]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Batang]Result:[/FONT][/SIZE]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Batang]stop: Unknown instance:[/FONT][/SIZE]

[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Batang]Code:[/FONT][/SIZE]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Batang]sudo rm -f/etc/NetworkManager/system-connections[/FONT][/SIZE]

[SIZE=3][FONT=Batang]Code:[/FONT][/SIZE]
[SIZE=3][FONT=Batang]$ sudo rm -f /etc/NetworkManager/system-connections/[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Batang]Result:[/FONT][/SIZE]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Batang]rm: cannot remove `/etc/NetworkManager/system-connections/': Is a directory[/FONT][/SIZE]

[SIZE=3][FONT=Batang]Code:[/FONT][/SIZE]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]$ sudo tcpdump -i eth0 -vvv -s 1500  [/SIZE][/FONT]
[SIZE=3][FONT=Batang][COLOR=red]**(note: I did not include the info with the parentheses '(port 67 or port 68)' in my code. Do I need to do this?  It looked like it wasn't part of the instruction, but something to look for.  If I need to re-enter the code with the info inside the parentheses, please let me know how exactly to write this.**[/COLOR][/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Batang]Result: (posting what is coming up so far....but it is still running for a while...and hasn't stopped...) - **[COLOR=red]DO I  TRY TO RECONNECT ON WIRED CONNECTION 1 WHILE THIS IS STILL RUNNING? WHEN I GO INTO THE UPPER RIGHT HAND CORNER AND HIT THE NM APPLET, IT IS LISTED AS DISCONNECTED, SO I HADN'T HIT THE WIRED CONNECTION 1 BUTTON AS OF YET...PLEASE ADVISE)[/COLOR]**[/FONT][/SIZE]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Batang]tcpdump: WARNING: eth0: no IPv4 address assigned[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 1500 bytes[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]22:47:18.970540 00:02:6f:87:c6:05 (oui Unknown) 802.1B I > Broadcast Null Unnumbered, test, Flags [Command], length 46[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]22:47:25.627687 00:02:6f:87:c3:f7 (oui Unknown) 802.1B I > Broadcast Null Unnumbered, test, Flags [Command], length 46[/FONT][/SIZE]
[SIZE=3][FONT=Batang]22:47:25.627687 00:02:6f:87:c3:f7 (oui Unknown) 802.1B I > Broadcast Null Unnumbered, test, Flags [Command], length 46[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]22:47:26.916055 ARP, Ethernet (len 6), IPv4 (len 4), Request who-has 169.254.255.255 tell 10.71.0.116, length 46[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]22:47:27.018420 IP6 (hlim 255, next-header UDP (17) payload length: 54) fe80::2b0:d0ff:fedc:9058.mdns > ff02::fb.mdns: [udp sum ok] 0 PTR (QM)? 255.255.254.169.in-addr.arpa. (46)[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]22:47:28.020215 IP6 (hlim 255, next-header UDP (17) payload length: 54) fe80::2b0:d0ff:fedc:9058.mdns > ff02::fb.mdns: [udp sum ok] 0 PTR (QM)? 255.255.254.169.in-addr.arpa. (46)[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]22:47:29.132249 ARP, Ethernet (len 6), IPv4 (len 4), Request who-has 10.71.0.116 tell 10.71.0.116, length 46[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]22:47:30.023032 IP6 (hlim 255, next-header UDP (17) payload length: 54) fe80::2b0:d0ff:fedc:9058.mdns > ff02::fb.mdns: [udp sum ok] 0 PTR (QM)? 255.255.254.169.in-addr.arpa. (46)[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]22:47:30.738837 00:02:6f:89:3a:09 (oui Unknown) 802.1B I > Broadcast Null Unnumbered, test, Flags [Command], length 46[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]22:47:32.026163 IP6 (hlim 255, next-header UDP (17) payload length: 50) fe80::2b0:d0ff:fedc:9058.mdns > ff02::fb.mdns: [udp sum ok] 0 PTR (QM)? 116.0.71.10.in-addr.arpa. (42)[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]22:47:33.025348 IP6 (hlim 255, next-header UDP (17) payload length: 50) fe80::2b0:d0ff:fedc:9058.mdns > ff02::fb.mdns: [udp sum ok] 0 PTR (QM)? 116.0.71.10.in-addr.arpa. (42)[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]22:47:35.026480 IP6 (hlim 255, next-header UDP (17) payload length: 50) fe80::2b0:d0ff:fedc:9058.mdns > ff02::fb.mdns: [udp sum ok] 0 PTR (QM)? 116.0.71.10.in-addr.arpa. (42)[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]22:47:37.630406 IP6 (hlim 255, next-header ICMPv6 (58) payload length: 16) fe80::7e11:beff:fe80:81f1 > ip6-allrouters: [icmp6 sum ok] ICMP6, router solicitation, length 16[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]            source link-address option (1), length 8 (1): 7c:11:be:80:81:f1[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]              0x0000:  7c11 be80 81f1[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]22:47:40.747753 00:02:6f:89:3a:09 (oui Unknown) 802.1B I > Broadcast Null Unnumbered, test, Flags [Command], length 46[/FONT][/SIZE]
[FONT=Batang][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Batang]22:48:06.337909 IP (tos 0x0, ttl 1, id 16990, offset 0, flags [none], proto UDP (17), length 54)**.....[COLOR=red]CODE CONTINUES TO RUN.....[/COLOR]**[/FONT][/SIZE]
[SIZE=3][FONT=Batang]**[COLOR=red][/COLOR]**[/FONT][/SIZE] 
[SIZE=3][FONT=Batang][COLOR=red]**Please advise what to do next. Thanks**[/COLOR][/FONT][/SIZE]

---

### Post by SummerT on 2012-09-30
I tried to  click wired connection 1 a few times while the code keeps rolling.  It tries to connect, but then after a while, says "connection offlline".  Every once in while, I will keep trying it and the same thing comes up.
 
will the code keep running all night? will it stop if it finds a dchp connection that works? 
 
Please advise.  Thanks.

---

### Post by steeldriver on 2012-09-30
Hi

You can hit Ctrl-C in the terminal window to kill the tcpdump process

Yes you should have included the part in parentheses - that's what tells tcpdump to look specifically for DHCP traffic, there's no harm done by leaving it out but it makes it harder to read the output because the terminal will fill up with stuff you don't care about

Also the command to delete any non-default connections didn't work because you left off the *

```
sudo rm -f /etc/NetworkManager/system-connections/**[COLOR=Red]*[/COLOR]**
```

---

### Post by SummerT on 2012-09-30
I'll post the code result putting in the *.   Thanks.
 
 I will put in the parentheses in the code as well.  So it's exactly like this?:
 
sudo tcpdump -i eth0 -vvv -s 1500 ('port 67 or port 68)'
 
I'll try with the new code wording...thanks, we'll keep trying..... 
 
___________________________________________
 
Also, I copied some result with the words magic cookie and was curious what this was
 
Here it is:
 
**[FONT=Batang][SIZE=3] [/SIZE][/FONT]**
**[SIZE=3][FONT=Batang]          Vendor-rfc1048 Extensions[/FONT][/SIZE]**
**[FONT=Batang][SIZE=3][/SIZE][/FONT]**
**[SIZE=3][FONT=Batang]            Magic Cookie 0x63825363[/FONT][/SIZE]**
**[FONT=Batang][SIZE=3][/SIZE][/FONT]**
**[SIZE=3][FONT=Batang]            DHCP-Message Option 53, length 1: Discover[/FONT][/SIZE]**
**[FONT=Batang][SIZE=3][/SIZE][/FONT]**
**[SIZE=3][FONT=Batang]            Hostname Option 12, length 8: "Computer"[/FONT][/SIZE]**
**[FONT=Batang][SIZE=3][/SIZE][/FONT]**
**[SIZE=3][FONT=Batang]            Parameter-Request Option 55, length 17: [/FONT][/SIZE]**
**[FONT=Batang][SIZE=3][/SIZE][/FONT]**
**[SIZE=3][FONT=Batang]              Subnet-Mask, BR, Time-Zone, Default-Gateway[/FONT][/SIZE]**
**[FONT=Batang][SIZE=3][/SIZE][/FONT]**
**[SIZE=3][FONT=Batang]              Domain-Name, Domain-Name-Server, Option 119, Hostname[/FONT][/SIZE]**
**[FONT=Batang][SIZE=3][/SIZE][/FONT]**
**[SIZE=3][FONT=Batang]              Netbios-Name-Server, Netbios-Scope, MTU, Classless-Static-Route[/FONT][/SIZE]**
**[FONT=Batang][SIZE=3][/SIZE][/FONT]**
**[SIZE=3][FONT=Batang]              NTP, Classless-Static-Route, Classless-Static-Route-Microsoft, Option 252[/FONT][/SIZE]**
**[FONT=Batang][SIZE=3][/SIZE][/FONT]**
**[SIZE=3][FONT=Batang]              NTP[/FONT][/SIZE]**
**[FONT=Batang][SIZE=3][/SIZE][/FONT]**
**[SIZE=3][FONT=Batang]            END Option 255, length 0[/FONT][/SIZE]**
**[FONT=Batang][SIZE=3][/SIZE][/FONT]**
**[SIZE=3][FONT=Batang]            PAD Option 0, length 0, occurs 27[/FONT][/SIZE]**

---

### Post by SummerT on 2012-09-30
okay I tied in the code with the * and the thing I noticed is instead of "wired connection" it started reading as "auto ethernet connection"
 
Then I put the port 67 and port 68 line in and it came up as "warning IPV4 address not assigned" and hung there in the window
 
I hit the autoethernet connection to try and connect and basically got the code I posted previously (the one with the magic cookie stuff in it)
 
I left it and we'll see what happens after that
 
Question:  Do I keep hitting the auto ethernet button trying to connect? Or do I allow the code to keep running in the terminal? I'm not sure what is supposed to happen next
 
Please advise
Thanks

---

### Post by steeldriver on 2012-09-30
^^^ that's exactly the kind of thing we're looking for - it's a DHCP discover packet - a broadcast message from your computer asking if there's a DHCP server that is willing to talk to it

I think what should happen next is the server should respond with an offer packet - if you don't see any responding DHCP traffic then that's a pretty sure sign that there is no DHCP service running - if that is the case then you will need a static IP, but you can't just guess it, you will have to get it from the old computer's configuration OR contact your building management (or ISP) - whoever provides / manages your internet service

[http://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol#Technical_details](http://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol#Technical_details)

---

### Post by SummerT on 2012-10-01
Hey.  code still running. once in a while I click to try to connect on autoet0, but it flashes for a few seconds, then says "not connected" and the like.  
 
What should I try next? I don't think I'll be able to get the ip address from the isp based on my home situation.
 
So any suggestions would be great (perhaps I can get the ip somewhere else?).  
 
Still trying, will keep going.....

---

### Post by Bucky Ball on 2012-10-01
If you are straight into the modem, the modem isn't running a DHCP server to offer you an IP, then unless you've set a static IP on your machine (not a good idea as it will block any offers) you must be getting the IP from the ISP server.

Maybe ring them and see if the modem is configurable (has a DHCP server) or whether they are sending you one. Maybe if you get facts about how things are set up at their end it could give some fresh clues ...

---

### Post by SummerT on 2012-10-02
Hey Bucky
Because of my living situation I can't really call and get an ip address.  The former computer worked fine with this modem - and the computer was pretty much the same model, just a slightly older version I think.  So basically I'm trying to either reset the modem or ask everyone how I might find a static ip to use.
 
There is no reset button (or pinhole) on the modem.
 
I stopped the TCP dump as I kept getting the same codes. i.e. "magic cookie"???
 
So I don't know if it has to do with the duplex or if anyone knows how to reset the modem box without using a hole/button on the box.  So any codes for me to continue to try would still be appreciated.  Getting tired and frustrated but thankful for all of your great people on the ubuntu forums and hopefully we will all figure this out before I reach 1000 beans.
 
Let's keep trying.  Thanks!!!

---

### Post by nativehound on 2012-10-02
Try adding a static ip in 192.168.0.X range.
Edit wired connection1:
ipv4 Settings tab:
```
click  manual
click Add
Address
192.168.0.2 (or higher like 192.168.0.11)
Netmask
255.255.255.0
Gateway
192.168.0.1
For DNS
8.8.8.8, 8.8.4.4
```
Do a full restart and see what happens.
also try goggles Ip
```
firefox 74.125.224.72
``` 

gl

---

### Post by Bucky Ball on 2012-10-02
> **nativehound said:**
> Try adding a static ip in 192.168.0.X range.


I'm presuming (and have posted) that as this is a relay device/modem it has no DHCP server, therefore the ISP will be serving an IP directly to the OP through that device. Static IPs are usually extra charge (at least in Australia) and are set by the ISP. You would need a router to do as you suggest successfully in this case, as then the ISP is serving the router an IP from the WAN side and you are settings your static IPs on the LAN side. No conflict. From the outside world it seems like there is one machine. But here there is no router, only a *direct connection through the modem to the ISP*. 

While your suggestion will remove any and all chance of a successful connection if the ISP is attempting to serve an IP at the same time, it may be worth a try on the grounds my presumption might be wrong and nothing else has worked. OP can't ring ISP (try an email?) to confirm the setup so all blind alleys, really. ;)

(* Other thing: If static IP has not been arranged with the ISP you won't be able to connect directly to, or through, their server anyhow. That would mean anyone could. They need to recognise the IP, static or not. I'm wondering if internet is getting to the modem device in the first place. In post 91 it appears a local discover  packet is being sent but there is no offer from any remote server. )

---

### Post by SummerT on 2012-10-02
Hey.  Will try nativehound's suggestion and then post.  Wondering if using any ip in that range is what I'm supposed to try...
 
bucky, what you say makes sense, but (since I'm relatively a beginner) the only difference between the last piece of similar hardware and this hardware is that the old hardware connected via dhcp immediately without a problem.  So with the same modem, this piece does not.  that's why I didn't know if we kept focusing on the ip was the way to go (as the hw address of course changed).  
 
How can I tell if there is traffic going through the modem without connecting to the internet?
 
I won't be able to call the isp and get the info unfortunately, so need some sort of workaround.  I'll try whatever you guys suggest at this point....
 
thanks everyone for your patience.  This could be the longest connection in history...

---

### Post by SummerT on 2012-10-02
ok, maybe you guys can fine tune this.  As far as the modem being connected...
 
I did try nativehound's suggestion to manually add a 192.168.0.2 (or higher like 192.168.0.11), then the netmast and gateway and 8.8.8.8. dns.  I did n't try every combination, but something did interesting happen:
 
number one, it came up as an established connection
 
number two - when I tried to open firefox, it did not IMMEDIATELY go to "server not found."
 
I tried a few websites and it said "connecting" and spun but then eventually came up with "server not found"
 
I tried the 74.125.224.72 and it did what the other urls did.  What is goggles ip anyway, curious?
 
So there was a difference in that it did try to connect and took a while vs. immediately going to server not found.  mystery continues.
 
Let me know too if I should try specific combinations in the 192 range (and what does that range represent anyway?), as well as netmast, gateway and dns (for example, I did not try 8.8.4.4...)
 
Any thoughts appreciated as we try to figure this out...

---

### Post by Bucky Ball on 2012-10-02
There is no way of knowing what DNS you should be using. That is provided by the ISP.

This expands and slightly changes my theory. If setting a static IP is getting some results, perhaps your modem/relay is attached to a router somewhere in the building. Who knows ...

---

### Post by SummerT on 2012-10-03
We live in kind of like an Inn with several apartments attached.  The landlord is virtually not existent and hard to reach, even though the net is coming through him somehow. That's why there is no way I can call anyone and have to try on my own. I can't even email this person.  It sounds strange, but  I think we're getting into non computer work here.
 
So basically all I know that this exact modem worked with the previous computer.  And with the last thing I did, I definitely think that the static ip is closer to getting it connected (even though it was auto dhcp before).  So if anyone out there gives me anything else to try (including dns and ips) it would greatly help.  Something has to work somewhere sometime.

---

### Post by nativehound on 2012-10-03
Do you guys think this could be a netbios/zeroconfig issue. Since it connected earlier on the other laptop via dchp. 
Do you still have access to the old computer to grab the mac addy off it and then spoof it on the new computer? I think this device is trying to connect via netbios and/or mac addresses only. Your in real a pickle.

gl

---

### Post by nativehound on 2012-10-03
Read this thread. 

[http://ubuntuforums.org/showthread.php?t=88206]("http://ubuntuforums.org/showthread.php?t=88206")

gl

---

### Post by nativehound on 2012-10-03
> **SummerT said:**
> This is what I have
Ipv6 ignore
ipv4 connect automatically manual
netmask 255.255.0.0
gateway 0.0.0.0.
require ipv addressing for this to complete is not clicked
dns server is blank
search domain is blank
dhcpclient id is kind of greyed out
box that says "available to all users" is unclicked
**in the wired section there is no mac address**
nothing in the cloned mac address
the mtu says 1

Add your mac address to the the empty field.
it's the first line:  Link encap:Ethernet  HWaddr "mac address"

```
ifconfig -a
```check if your in the avahi group as well.

 ```
groups YourUserNameHere
```if none of the above gets you nowhere, I'm stumped. 

gl

---

### Post by SummerT on 2012-10-03
I'll try the above and post...thanks
 
oh, and the old hardware's board got fried, so no go on that...

---

### Post by SummerT on 2012-10-04
Hey, I quickly looked at the thread you linked to, but haven't delved into it yet.  The one thing I thought first is that I try to install packages but since I can't access the internet, the packages don't get to me, I've gotten messages to that effect.
 
with the ranges of ips to try as you suggested last time....what are differenct combinations would you suggest? If you can give me some examples of what might work, let me know.  For example, should I try 192.168.0.2 (or higher like 192.168.0.11), using the 8.8.8.8 or 8.8.4.4? Or any other 192 ips addresses...
 
And since the connection spins a bit, I feel at least there is more of a connection (yes, a non expert way of saying that), whereas before the message for "server not found" would come up immediately.  I know we are close to this here because at least I connect right away, just not to firefox...and the internet....

---

### Post by nativehound on 2012-10-04
The 192.168.0.x is the default ip range for most home networks.
Without knowing the correct ip range it's a never ending guessing game.
Seeing that this is a in house HPNA setup connecting to a MDU?/switch?/hub?/router?/windows box? only the system admin has the answer. 

If you still can't get online you could try the Link-local only in NM ipv4 settings tab.That's for ad-hoc and point-to-point connections without a dhcp server. That should give you an ip in the 169.254.0./16 range.
But seeing how this a high turnover access point in a Inn, there has to be a dhcp server.

gl

---

### Post by SummerT on 2012-10-04
Hi nativehound
Changed the link local.  
I rebooted then clicked connection info and got the 169 ip number.
ipv6 ignored
It said what the driver is.
And then what do I do now?

---

### Post by nativehound on 2012-10-04
Thats a go time to try something else. Have you tried from the live cd? the older 10.04 live cd would be the choice. They changed a lot of stuff since. If you can get online with the live cd then we knows it something with your currant install. I think it has something to do with avahi/Netbios the Tut could be using unicast dns too.


You can download winbind here:
[http://www.ubuntuupdates.org/package/nathan-renniewaldock_ppa/precise/main/base/winbind](http://www.ubuntuupdates.org/package/nathan-renniewaldock_ppa/precise/main/base/winbind)

Load it on a usb/phone or burn it to a disc.

---

### Post by SummerT on 2012-10-05
firstly, I think I still have 10.10 on a disc.  Should I try that? So now 11.10 is loaded on...so just reinstall completely with10.10? Let me know what I would do it from the live cd...I've never done that before - either with 10.10 or 11.10...so instructions would be helpful (yes, please write it down for me!)...
 
 
secondly, also, can you explain a little bit about what winbind is exactly in laymans terms?
 
So please explain what I would do after I burn it to a disc or usb....the instructions afterwards...
 
Thanks for keeping the help going....must...connect...to ....internet.....
Thanks.

---

### Post by Bucky Ball on 2012-10-05
I would try 10.10 by booting to a desktop from the USB/disk and see if it gets you online. If so, install.

---

### Post by SummerT on 2012-10-06
so I put the 10.10 install disk in....I go through the beginning parts of the 10.10 install? then see if there is a connection? Or do I go through a further part of the install?
 
I've never done this before, so if you can detail exactly what I need to do, let me know...
 
I have 11.10 on right now....
 
Thanks

---

### Post by SummerT on 2012-10-06
i just didn't know if i put the disc in and see if i can get on the internet...or
 
reinstall 10.10......

---

### Post by SummerT on 2012-10-08
you guys still out there?????

---

### Post by Bucky Ball on 2012-10-08
Boot from the disk.

---

### Post by edybear on 2012-10-08
Hi, first move check you connectivity from your PC to your(server/router) and make sure your IP Address is the same with the range of your network address from your (server/router). And in applying IP Address, the best way to check your connectivity is to apply it by manually. 

If you have already IP Address check your connectivity by using "ping"....
and try to ping your server/router from your PC.

And, if you ping have reply it means your network connectivity now is okay...

In browsing, try to check if you have using proxy settings

Hope I give you little shine......

---

### Post by Bucky Ball on 2012-10-08
> **edybear said:**
> Hi, first move check you connectivity from your PC to your(server/router) and make sure your IP Address is the same with the range of your network address from your (server/router). And in applying IP Address, the best way to check your connectivity is to apply it by manually. 

If you have already IP Address check your connectivity by using "ping"....
and try to ping your server/router from your PC.

And, if you ping have reply it means your network connectivity now is okay...

In browsing, try to check if you have using proxy settings

Hope I give you little shine......

Welcome.

Please read thread before posting. Most of this has been covered. ;)

---

### Post by SummerT on 2012-10-08
bucky, I assume you were talking about the previous person trying to help me...
 
if not for anyone else, I put a random ip address in the 168 range and it establishes a connection but doesn't get to the internet...so for those who are not reading, I can't find the network address of the modem (because of my apartment house/inn arrangement).  I made sure that firefox advanced tab for connecting is set to "no proxy"
 
bucky, also as you know I am a newcomer to networking...so please detail me how to "boot from disk"....(even if it seems like talking to a kid, which is fine)...
 
Thanks everyone...still going....

---

### Post by Bucky Ball on 2012-10-08
You need to get to the BIOS (the key to do this varies but could be F2 or 'Delete' key) by hitting the appropriate key at boot and change the boot order to boot from the optical drive (or USB). 

Put the disk (or USB) in and hit F10 to save changes and exit. That should boot from the disk. Let it go until you get to a desktop.

---

### Post by SummerT on 2012-10-08
Thanks Bucky.
I've done this several times before, but it just reinstalls the ubuntu os. Is that what you mean for me to be doing?  If so, unfortunately it doesn't help either.  I've reinstalled so many times, even using different versions just in case there might be something wrong with the install disk.

Now the disk that is in the cdrom - this is the install disk, right?  Or is there some other ubuntu disk you may be referring to other than the installation disk?

---

### Post by Bucky Ball on 2012-10-08
No that's it. You should be 'Try Ubuntu' when you get to that screen. Not install. You just want to run Ubuntu from the CD.

---

### Post by SummerT on 2012-10-09
Okay. Thanks. We didn't try that yet, so we'll try now.

---

### Post by SummerT on 2012-10-10
Didn't work booting from the CD
Need some more codage ideas

---

### Post by SummerT on 2012-10-10
Ok, I loaded windows xp on my machine and got a hold of someone on the network to try to fix the problem.  They said that an ip in the 169.254.xxx.xxx range was forced on my machine and they are trying to figure out why.  The gateway still reads as 255.255.0.0.  No dns information.  So if anyone can give me some clue as to why I was forced that ip address (which cannot connect to the internet) and what that means and what I could do, please let me know.
 
I have not reloaded ubuntu 11.10 again, but wanted to give you guys that bit of information first to see if it would help.
 
Supposedly they are trying to find out why I was given that ip address that couldn't connect, but we'll see.  Any ideas to try would be greatly appreciated.
 
Let me know...Thanks.

---

### Post by steeldriver on 2012-10-11
nevermind

---

### Post by SummerT on 2012-10-11
right now I have windows loaded, so if you can post the commands for windows that would be great...
 
otherwise, I tried ipconfig /release
 
and then ipconfig /renew
 
but it won't let me renew
 
I did the link local when ubuntu was installed but it didn't work.
 
any ideas on how to get a new ip?

---

### Post by SummerT on 2012-10-11
also, in the wndows arrangement, i uninstalled the network card and rebooted, it reinstalled it but then I still could not release then renew an ip.

---

### Post by Bucky Ball on 2012-10-11
***If you are now looking for Windows support with this, please post a thread on a Windows forum. This is a Ubuntu support site.***

---

### Post by SummerT on 2012-10-12
ok, in ubuntu...
please tell me how to clear the 169 ip address.
I've tried a gazillion different codes.  the network is "forcing" the 169 ip.

---

### Post by SummerT on 2012-10-12
...and I just loaded windows so I could get the ip address they were giving me in my apartment situation.  I'm sure everyone can see that I want to use ubuntu as that is what my thread has been about all this time....  I'm trying everything I can (including starting with windows).  You guys asked me to get the ip, so I got that 169.xxx ip and was giving it to you guys because I'm sure that that ip comes up with ubuntu as well.  So I can't relase and renew the ip right now, so if anyone has any ideas that would be appreciated.  The not giving up part you can view as a good thing (especially since my knowledge is not up to par with my willing to keep trying).  I apologize as well as I do not know the etiquette of the forums nor the proper terminology of many things.  I do know that there are people out there who want to keep helping, so I will keep trying to reach out to you people out there who are reading this and want to help out someone who is not an expert....Thank you.

---

### Post by steeldriver on 2012-10-12
It's hard to help you since you can't give us any information about how the network is set up

I think we've fairly conclusively established that there is no DHCP server (or at least not one that is responding to your network card) and you don't recall having been given a static IP to use

AFAIK the remaining option is APIPA, which I don't really know anything about, but is a 'link-local' addressing scheme which (as I understand it) provides a way for peers to negotiate non-conflicting IP addresses in the absence of a DHCP server - basically each host guesses an IP in the 169.254.xxx.xxx reserved address range and then tests whether another local device is already using it, if yes it guesses again, if not then it keeps the address. **Personally I have only ever seen devices obtaining 169.254.xxx.xxx addresses when they are configured for DHCP but don't get a DHCP offer (which appears to be exactly the case here).** In that sense nothing is "forcing" that IP except for the absence of any other options.

---

### Post by SummerT on 2012-10-13
been trying to talk to the isp people to no avail.  I have some information about the system, but you guys would have to ask so I could get you that information.  They supposedly changed the ip to a 10.71.xx.xx.xx address, but that did not work.  When I released the ip it went to zeros, but then tried to renew and it didn't let me renew it.
 
Am thinking it might be a duplex issue - like the old 3com modem runs on full duplex and the system is at half duplex? let me know what you think and how to change it to full duplex.  Do you think that's the problem?
 
Otherwise, let me know of any thing to look up about the system and I'll report back.  the isp has not been helpful.  I did switch modems and that appears to be fine (same type though..the tuts modem).  As I said, I'm in a place with a lot of residences and did take the computer in another apartment to try it and the same thing happened, so it's something in the system I think that may need to be changed.
 
Let me know your thoughts and anything for me to try and to report.  Thanks again...

---

### Post by SummerT on 2012-10-13
changed the speeds and tried different ones..10, 100, full, half.  still nothing.
 
so any ideas...thanks....

---

### Post by SummerT on 2012-10-13
update:  I tried to connect the comp to the main residence computer and it worked, but this particular box (not mine) is tp-link (a six port fast ethernet switch).  it looks different than the modem in my apartment (the 3com tut systems one).  Do I need to buy some sort of other modem? which would you suggest? and do you think it's a modem issue or code/hardware issue?  is it just that I can't connect to this box with my computer? strange in that my old hardware worked fine with the tuts box....thoughts?....

---

### Post by SummerT on 2012-10-13
So the exact "box" we hooked into...
 
So we went to where the main public computer is and the ethernet port from the wall went into this box:  TP-Link fast ethernet switch, model TL-SF1005D. 
 
This is the link to amazon for this product.
[http://www.amazon.com/TP-Link-TL-SF1005D-5-Port-Unmanaged-Desktop/dp/B0019WDZUU/ref=sr_1_1?ie=UTF8&qid=1350116185&sr=8-1&keywords=tl-sf1005d](http://www.amazon.com/TP-Link-TL-SF1005D-5-Port-Unmanaged-Desktop/dp/B0019WDZUU/ref=sr_1_1?ie=UTF8&qid=1350116185&sr=8-1&keywords=tl-sf1005d)
 
With regard to this switch, do you think that our computer just needs a higher performance modem, or this type of switch?  Or is this thing just a hub to allow multiple units connect to the ethernet port and we just happen to be able to connect through here?  We want to know if we should buy this thing or if it will be a waste of money if it is not necessary (the old computer worked with the current Tuts modem, so my question is since this computer is similar but a slightly older model, is this why there could be connection problems?)
 
Also, we checked the IP address when we were able to connect to the net through this switch and it was the 10.71.xxxxx that I mentioned before- which I believe they connected with our hardware address, so if you know how to clear the hardware address I'd like to be able to do this as well.

---

### Post by SummerT on 2012-10-14
Update:
So, finally an IT tech was able to see that the network seems to be dropping packets between the main computer bank and the line into my apartment.  They suggested swapping out the line card in the d-slam.  But it might not be for a few days before they can do that.
 
Does that sound like a common thing that happens and the solution?  Just wanted to ask because I went through a number of technicians and a number of them I ended up making suggestions for them to check out because they didn't sound like they knew fully of what was going on or wanted to check into it.
 
So basically, I am connected to the network, I now have a valid IP address.  I ruled out some issues and know that the modem is not the problem, the wire is not the problem, the computer is not the problem (since it worked in the main center through a direct ethernet line).  So let me know if you have any coding ideas that would resolve any issues with the network "dropping packets".  (ps: I did try changing the different duplex speeds and it only works when either on auto select or 100/full).
 
thank you again for all your help. I know we are close...

---

### Post by SummerT on 2012-10-16
bump

---

### Post by nativehound on 2012-10-17
Adding a "router" would give you a dhcp server to connect to but the router may not connect to the upstream hardware beyond the Tut. 

When you hooked up to the switch and got a10.71.xxxxx ip did you write down all the info.
Such as the gateway and dns ips too?

Do you now have a 10.71.xxxxx with the Tut box?
If you do try google's ip addy

```
*74.125.224.72*
```or if not, have you tried a static ip in the 10.71.xxxxx range?

---

### Post by SummerT on 2012-10-17
yeah, I wrote down the 10.71xxx number they gave me plus the gateway dns that they suggested....it still isn't dhcp though.  It was what I was given as a static ip to enter...
 
 
the it people said that they could see my connection and that it was trying to connect to the internet sites, but that it was still dropping packets.  Basically, that's how they left it and they can't figure it out, even at their "level two"....
 
so I have to figure out what to do on this end with the forums' help....wondering if since this is such an older computer (with little ram..483ram) and an old pci card whether I should try to change the ram and the card...let me know if you think that is why it's dropping packets...
 
I got a usb wireless adaptor which I can't get to work well either...I probably should post for that....
 
let me know any ideas...would rather do wired anyway....

---

