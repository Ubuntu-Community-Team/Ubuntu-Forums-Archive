---
title: "netgear wg311"
date: 2006-06-20
forum: Networking &amp; Wireless
---

### Post by guine on 2006-06-20
I just got a netgear wg311 and Im not able to get any sort of connection with it.  The card shows up in someplaces(a wireless card is listed when I do lspci in the terminal) but isnt seen most of the time(no wireless cards are listed when I try ifconfig and nothing shows up under network settings).  /etc/network/interfaces shows both an eth0 and eth1 in it

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth0

# The primary network interface
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

I believe that eth0 is my regular ethernet card which works fine.  I know i ended up with a different version of the card than ubuntu lists in the hardware compatibility guide because they dont include the version number on the box.  Any clues on how to fix this or would I be better off returning the card and trying something else?  Thanks.

---

### Post by stupidkid on 2006-06-20
Try Atheros chipset cards. They work really well. The madwifi drivers are great.

---

### Post by noname101 on 2006-06-20
You could try following [this]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo") how to. Asuming your card doesn't have a version number. If its version two then you'll need to use ndiswrapper. Also your card is Atheros chipset according to [this]("http://linux-wless.passys.nl/query_part.php?brandname=Netgear").

---

### Post by guine on 2006-06-20
I saw some directions for using ndiswrapper on the wg311 version 3 that said to copy WG311v3.INF and WG311v3XP.sys from the cd that came with the card into the same folder and then do this:
ndiswrapper -i WG311v3.INF

ndiswrapper -l

This then gave me a return message of

wg311v3 driver present, hardware present 

which was supposed to happen but it didnt leave much in the way of directions for after that except that I need to then use use iwconfig and the other wireless tools.  Does anyone know what I should do from here with the ndiswrapper method or would I be better off trying to use madwifi.  Thanks.

---

### Post by noname101 on 2006-06-20
Since you have version 3 madwifi won't work. But to get ndiswrapper to work do this:
```
sudo ndiswrapper -m
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

```
then edit /etc/modules and add at the bottom ndiswrapper
```
sudo gedit /etc/modules
```
Now go to System | Administration | Networking to set up your card. It should be wlan0 or eth1 or something but not eth0.

---

### Post by guine on 2006-06-21
After doing the sudo modprobe ndiswrapper my computer crashed.  Both times I tried it a new prompt came up in the terminal right before the crash so Im not sure if the sudo modprobe ndiswrapper worked.
Also, is system settings - network settings the kde equivalent of System | Administration | Networking?  Thanks
PS.  do most of you use gnome for this and would I be better off if I downloaded gnome for setting up the wireless card?

---

### Post by noname101 on 2006-06-21
[http://linuxcompatible.org/Netgear_WG311v3_WLAN_PCI_Card_with_Debian_Linux_Testing_t33271.html](http://linuxcompatible.org/Netgear_WG311v3_WLAN_PCI_Card_with_Debian_Linux_Testing_t33271.html)
Uninstall the driver you already installed with sudo ndiswrapper -e driver.
You can get the driver name by doing ndiswrapper -l.
Then just put the WG311v3.INF and WG311v3XP.sys in the same folder and then run 
ndiswrapper -i WG311v3.INF. Then do 
```
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```
The kde network settings might work. I can't remember not using kde anymore. But you can just edit /etc/network/interfaces too.
You would put something like this in it at the bottom:
iface wlan0 inet dhcp
wireless-essid xxxxxxxxxxx
wireless-key xxxxxxxxxxxxx
auto wlan0

---

### Post by guine on 2006-06-21
Sorry about more stupid and/or strange issues, but modprobe disappeared as a command that I can use(command not found).  The only things that Ive done to my computer since I was able to use modprobe before is purge firefox and then reinstall it(this is another issue but i dont want to worry about this for now) and install ubuntu-desktop(and everything that synaptic wanted with it) so that I could try to get my wireless card activated through gnome. This made me uninstall libesd0 and libgksu1.2-0.  I decided to try to reinstall those packages to see if that would let me use modprode again but libesd0 won't install with ubuntu-desktop and synaptic said that there is no available version of libgksu1.2-0 even though it shows up in a search.  Any clues on this one?](*,)

---

### Post by guine on 2006-06-22
Never mind about the modprobe command not found thing, that seems to have decided to work since I turned my computer on this morning.
When i tried installing using sudo ndiswrapper -i wg311v3.inf
i got this:
Installing wg311v3
couldn't copy wg311v3.inf at /usr/sbin/ndiswrapper line 135.

Then I was able to run sudo modprobe -r ndiswrapper fine.
On sudo modprobe ndiswrapper I got this message:
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-25-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

and the card isnt showing up under System | Administration | Networking for me to try to activate.
Heres the area around /usr/sbin/ndiswrapper line 135 in case thats part of the problem(I marked line 135 in italics):
sub isInstalled {
    my $installed;
    my $name = shift;
    my $mode = (stat("$confdir"))[2];
    if (!S_ISDIR($mode)) {
***	return 0;***
    }
    open(LS, "ls -1 $confdir|");
    while(my $f = <LS>) {
	chomp($f);
	$mode = (stat("$confdir/$f"))[2];
	if (S_ISDIR($mode) and $name eq $f) {
	    $installed = 1;
	}
    }
    close(LS);	
    return $installed;
}

Any ideas on whats going wrong?  Thanks.

---

### Post by noname101 on 2006-06-22
You need to put the path to wg311v3.inf
path/to/wg311v3.inf
Also linux is case sensitive.
So it might be WG311V3.INF.

---

### Post by deadlycow21 on 2006-06-26
[QUOTE=noname101]You need to put the path to wg311v3.inf
path/to/wg311v3.inf
Also linux is case sensitive.
So it might be WG311V3.INF.[/QUOTE]

actually it would be WG311v3.inf not WG311V3.INF :-D 

Thanks for the help on this, i need to get this to work aswell, and i think that the suggestions earlier may help :-k

oh, and, do you know where i might find the .deb for this, i cannot get internet upstairs because we are moving in two days. :) if someone could attach this, it would be greatly appreciated.

Cheers, (I'm not british, but "cheers" just sounds cool)
-jacob (deadlycow21)

---

### Post by Perrorist on 2006-09-03
I have a WG311 V3 wireless card and understand the procedure for installing it with 6.06 (i.e using ndiswrapper to encapsulate the WIN drivers). However, whenever I type:

~$: **sudo ndiswrapper [whatever]**

I get 'command not found'. Modinfo can find ndiswrapper, so it's not missing.

Also, iwconfig can't find wlan0.

I'm using a wired connection (eth0) as a fallback but I need to be wireless.

Any suggestions on what might be needed to get this to work?

---

