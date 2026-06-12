---
title: "Must Disable, then Enable Networking for Wireless..."
date: 2011-01-29
forum: Networking &amp; Wireless
---

### Post by theirishfrog.sh on 2011-01-29
Hello, everyone. I'm having some problems, not with my network card, but with the network manager.

My wireless can connect to my router without a problem, but in order to do so (after boot) I must first disable networking in the Notification Area and then re-enable it.

I don't mind it too much, but when other people use my computer, it's made painfully obvious to me, that this was never an issue with Windows 7 (as much as I despise MS).

Any help? Thanks.

---

### Post by grahammechanical on 2011-01-29
When you boot up do get a message that says Wireless networks available? (I am assuming that you are using 10.10). When you left click the icon do you see a list of available wireless networks? Is your network on the list? If you select it, does network manager then connect?

This could be a simple matter of a failure to set your connection to Connect Automatically. Right click, Edit Connections>Wireless tab>select your connection and tick the Connect Automatically box. Also tick the box Available to Other Users, if the system is set up to allow others to use the computer.

Regards.

---

### Post by theirishfrog.sh on 2011-01-29
**@grahammechanical** - I've double-checked all of my settings. I'm sure it has nothing to do with the "Connect Automatically" or "Available to Other Users" functions, as I already have both of them enabled. Also, I made sure that it is the only network in my list to connect to.

Thanks for the quick reply, but I'm still at a loss for solutions. :-(

 - **TheIrishFrog.sh**

**P.S.**  Also, I'm using Ubuntu 11.04 (64bit) that I updated from 10.10. But I know it doesn't have to do with the fact that I'm using an alpha-release, because this started when I first installed 10.10... Here's a list of my relevant specs:

[I]**Brand:** Toshiba
**Model:** Satellite L505D-LS5002
**OS:** Ubuntu 11.04 - Natty Narwhal (64bit)[/I]

---

### Post by theirishfrog.sh on 2011-02-02
**bump** Anyone? ^_^

---

### Post by irv on 2011-02-02
Right click on the network icon and select Edit Connections.  In the Network Connections dialog box select the Wireless tab, click on the your network connection and click on the edit button. Make sure there is a check mark in the connect automatically check box. That's it. It should connect automatically every time you start up your computer.
[ATTACH]182546[/ATTACH]

---

### Post by irv on 2011-02-02
By the way, when I boot up my laptop, the network is the last thing to connect. It take almost about a full minute before it even tries to connect. Are you giving it enough time to react and try to connect?

---

### Post by theirishfrog.sh on 2011-02-03
I tried waiting for over 5 minutes and nothing happened. Also, I double-checked and my "Connect Automatically" setting is enabled. So I'm still at a loss. :-(

Thanks for the help though... Anyone else?

---

### Post by irv on 2011-02-03
> **theirishfrog.sh said:**
> I tried waiting for over 5 minutes and nothing happened. Also, I double-checked and my "Connect Automatically" setting is enabled. So I'm still at a loss. :-(

Thanks for the help though... Anyone else?

I'm just curious, if this is a laptop do you have a switch to turn the wireless on and off? If so what happens if you turn it off and then back on again? I just wonder if it would enable the wireless connection?
Just curious!

---

### Post by theirishfrog.sh on 2011-02-04
No... Sadly there's no wireless switch.

---

### Post by irv on 2011-02-04
OK, did you have to install a driver for your wireless card when you install the OS? If so was there more then one driver available? I know when I installed my driver, I had two to choose from.

---

### Post by theirishfrog.sh on 2011-02-04
No, the network driver pretty much took care of itself upon OS installation. I haven't messed with it since either. At least we're starting to get past most of the stuff I've already checked though. lolz

Keep it coming guys... We'll fix this yet! ^_^

---

### Post by nm_geo on 2011-02-04
> **theirishfrog.sh said:**
> No, the network driver pretty much took care of itself upon OS installation. I haven't messed with it since either. At least we're starting to get past most of the stuff I've already checked though. lolz

Keep it coming guys... We'll fix this yet! ^_^

Try this code in the terminal before you click the network manager

```
sudo lshw -C network
```Then repeat after you get the wireless established.

Oh by the way also do a 
```
uname -a
or even better try
cat /etc/lsb-release

```

---

### Post by TBABill on 2011-02-04
May also need to look at what drivers are loading BEFORE and AFTER you enable it in the network manager to see if it's just a missing module on startup and you enabling it may do the same as the modprobe command. Just a thought but I may be way off.

Restart the computer and when it's fully booted, go into a terminal and type in ```
lsmod
``` and THEN enable the wireless like you did before and again go into a terminal and ```
lsmod
``` again. Paste both outputs here and we'll find the missing driver if that's the issue. If it is, then it's just a gedit of /etc/modules and adding it to the end of the list. And hopefully it's not somehow blacklisted, but that's another thing for later if this doesn't work.

---

### Post by theirishfrog.sh on 2011-02-05
The only difference that I noticed was that after the network was enabled, the configuration lists my local IP address. Does that help at all?

```

david@david-Satellite-L505D:~$ sudo lshw -C network
[sudo] password for david: 
  *-network               
       description: Wireless interface
       product: RTL8187SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 22
       serial: 70:f1:a1:2c:d7:38
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=r8180 latency=0 multicast=yes wireless=802.11b/g
       resources: irq:16 ioport:7000(size=256) memory:92100000-92103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:26:6c:4d:c1:36
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:43 ioport:6000(size=256) memory:90010000-90010fff memory:90000000-9000ffff memory:90020000-9003ffff

```

```

david@david-Satellite-L505D:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: RTL8187SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 22
       serial: 70:f1:a1:2c:d7:38
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=r8180 ip=192.168.2.2 latency=0 multicast=yes wireless=802.11b/g  link
       resources: irq:16 ioport:7000(size=256) memory:92100000-92103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:26:6c:4d:c1:36
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:43 ioport:6000(size=256) memory:90010000-90010fff memory:90000000-9000ffff memory:90020000-9003ffff

```

```

david@david-Satellite-L505D:~$ uname -a
Linux david-Satellite-L505D 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux

```

```

david@david-Satellite-L505D:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

```

---

### Post by theirishfrog.sh on 2011-02-05
Is this any help at all?

```

david@david-Satellite-L505D:~$ lsmod
Module                  Size  Used by
cryptd                  8140  0 
aes_x86_64              7936  495 
aes_generic            27631  1 aes_x86_64
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
dm_crypt               13381  0 
snd_hda_codec_realtek   300173  1 
snd_hda_intel          26115  2 
snd_hda_codec         100919  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
joydev                 11395  0 
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    64181  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               1240  1 snd
fglrx                2523725  31 
r8187se               167912  0 
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
edac_core              46822  0 
i2c_piix4              10047  0 
edac_mce_amd            9387  0 
k10temp                 3535  0 
shpchp                 34910  0 
eeprom_93cx6            1789  1 r8187se
lp                     10201  0 
psmouse                62080  0 
serio_raw               4910  0 
parport                37032  3 parport_pc,ppdev,lp
usbhid                 42030  0 
hid                    84710  1 usbhid
ahci                   22210  2 
video                  22176  0 
output                  2527  1 video
r8169                  42254  0 
libahci                26148  1 ahci
mii                     5261  1 r8169

```

```

david@david-Satellite-L505D:~$ lsmod
Module                  Size  Used by
cryptd                  8140  0 
aes_x86_64              7936  871 
aes_generic            27631  1 aes_x86_64
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
dm_crypt               13381  0 
snd_hda_codec_realtek   300173  1 
snd_hda_intel          26115  2 
snd_hda_codec         100919  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
joydev                 11395  0 
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    64181  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               1240  1 snd
fglrx                2523725  32 
r8187se               167912  0 
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
edac_core              46822  0 
i2c_piix4              10047  0 
edac_mce_amd            9387  0 
k10temp                 3535  0 
shpchp                 34910  0 
eeprom_93cx6            1789  1 r8187se
lp                     10201  0 
psmouse                62080  0 
serio_raw               4910  0 
parport                37032  3 parport_pc,ppdev,lp
usbhid                 42030  0 
hid                    84710  1 usbhid
ahci                   22210  2 
video                  22176  0 
output                  2527  1 video
r8169                  42254  0 
libahci                26148  1 ahci
mii                     5261  1 r8169

```

---

### Post by nm_geo on 2011-02-05
David your OS/flavor is still Maverick 10.10

david@david-Satellite-L505D:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
But that is a good thing for now.  I know you checked it in the System > About Ubuntu and read you have Natty but that is a bug.. I forget the launchpad number, but it does not matter.  Believe me if you had Natty you would have more problems right now.

Synaptic upgrade to ubuntu-docs - 10.10.4ubuntu0.1 will fix the incorrect text about Natty

So basically you can use your wireless but you must enable it manually each time your boot up? Correct?

 And yes your IP showing up after the manual enable of wireless is important.

---

### Post by nm_geo on 2011-02-05
I have been trying to reproduce your manual connect problem here and I think the answer is in the network-manager settings.  I know you were asked earlier if you are sure the automatically connect radio button was clhecked on Right?  Let's look at another part go to >System > Preferences>  Network Connections>  wireless tab  >  pick your connection and edit

Better yet let's just create a new connection: hit Add

connection name your SSID (david or whatever) 
Make sure the Connect Automatically box is checked 
Put in your SSID 
Mode infrastructure (normally)
MTU should be automatic too

at the bottom check Available to all users

Wireless security tab
Security (whatever your wireless uses) mine is WPA & WPA2 Personal be sure your matches your wireless.
Password _________   whatever is set up in your wireless 
show password if you like and you are the only users typically

Be sure the Available to all users is checked at the bottom.

After you reboot the new one should have Auto in front of the connection name (this may not appear but it should connect automatically)

---

### Post by theirishfrog.sh on 2011-02-05
Well, I tried recreating the network information as a new connection, but it didn't change the fact that I had to manually enable it, after reboot.

Also, how do I do the Synaptic update to ubuntu-docs - 10.10.4ubuntu0.1?

---

### Post by nm_geo on 2011-02-05
> **theirishfrog.sh said:**
> Well, I tried recreating the network information as a new connection, but it didn't change the fact that I had to manually enable it, after reboot.

Also, how do I do the Synaptic update to ubuntu-docs - 10.10.4ubuntu0.1?

Go to Synaptic in the quick search type ubuntu-docs check installed and latest versions.   Yours should be an older version install the newer it fixes the bug that states you are running Natty 11.04.

If you followed the instruction above and shut down all the way before booting, I am about out of ideas. 

Try this 
```
cat /etc/network/interfaces
```

---

### Post by irv on 2011-02-05
Mine must of gotten fixed on the last update.
[ATTACH]182802[/ATTACH]

---

### Post by nm_geo on 2011-02-05
> **irv said:**
> Mine must of gotten fixed on the last update.
[ATTACH]182802[/ATTACH]


It probably did yes.

If David has done his updates he might get that part fixed too, without updating the ubuntu-doc alone. 

The bug has caused many users to think they were upgraded to Natty who really weren't.  It has cause a little confusion, but if you are testing Natty you will know it for sure.. ;)

It breaks about every third day during the Alpha 1 updates and Alpha 2 started out broken.

---

### Post by nm_geo on 2011-02-05
David here is what I just tried, you might not feel like it is weird but if you do it right all will be well.  I picked my wireless connection and deleted it.  Then I looked in the network-manager list and since my wireless router is broadcasting I reconnected. After putting my wireless password back in  the Auto amended to the named connection. See the top I did not add that Auto to the gfk..  gfk is my SSID.

---

### Post by theirishfrog.sh on 2011-02-06
Okay. So I got it to connect automatically on start-up without manually enabling the network connection, by turning on the enabling SSID Broadcast on my router. I guess this will have to suffice, for now. But the overall problem is still there....

How can I get my computer to automatically connect to a hidden wireless network on start-up, without manually enabling the network connection tab? :-(

Also, the upgrade worked... My computer now says it is running Ubuntu 10.10 ^_^

---

### Post by nm_geo on 2011-02-06
> **theirishfrog.sh said:**
> Okay. So I got it to connect automatically on start-up without manually enabling the network connection, by turning on the enabling SSID Broadcast on my router. I guess this will have to suffice, for now. But the overall problem is still there....

How can I get my computer to automatically connect to a hidden wireless network on start-up, without manually enabling the network connection tab? :-(

Also, the upgrade worked... My computer now says it is running Ubuntu 10.10 ^_^

I would turn the wireless broadcast off and see what happens.  

Reasoning you have already made  a connection to the wireless access point and it should persist.  Just try it what can it hurt..

---

