---
title: "Last resort on AR5001 chipset."
date: 2011-06-25
forum: Networking &amp; Wireless
---

### Post by Dangertux on 2011-06-25
I know that there are about 500,000 posts on this chipset. I feel as though I've read them all. 

Situation : Wife's laptop has AR5001 Wireless Adapter laptop model is Toshiba Satellite A215 

Problem : Wireless networking randomly loses connectivity and can not regain connectivity, the only apparent solution is a full power down , this is not even certain to work. The card works under Windows, she hates Windows. (I love her for this) I know it's not faulty hardware , because it will work for days on end under Windows without problems.

Things I've tried  : 

madwifi drivers (any and all versions available) : These increase stability of the signal and seem to delay the inevitable however it still happens. When using these drivers the only option is to unload them modprobe -r then reboot then remove them again and re add them. It makes no sense why this works, and if I don't remove them prior to rebooting it will not work. 

ATH5K drivers  : These are pretty much junk, results are unpredictable at best, sometimes it will work perfectly for a few hours, sometimes it will not work at all. Nothing is repeatable, I can't seem to force whatever condition is causing this. rfkill does not show the wifi being blocked (hard or soft), unblocking it anyway does nothing, only way to make this work and it's iffy is to fully power down wait 5-10 minutes turn it back on and it MAY decide to work. 

Firmware update : Updated the Toshiba BIOS to the latest version of the firmware 2.0 no joy here either. Same issue both sets of drivers.

Tried different distros and kernels : I've tried Mint 9,  10 ,11 ; Ubuntu 10.10, 10.04  , 9.10 and 11.04 (which is currently installed) , Fedora and OpenSUSE. All are giving the same problems. I have also tried a slew of different kernels no joy from any of them (I'm not at the computer with the issue now I will post exactly what kernel versions I've used when I have access to the machine).

Another useful bit of information that might help , the hard switch to disable/enable wifi WILL disable it but turning it back on does absolutely nothing. The hotkey does nothing at all. The bios does not have an option to disable or enable  the wireless card. 

I will also post the typical lsmod , lspci , iwconfig all that good stuff when I get back to the computer in question. I'm probably just going to buy a PC card for it and give up on that one, but this is driving me insane and I would really like to see it resolved even if I do replace the hardware.

This is mostly just a last ditch effort that maybe someone may know something I don't or if someone has seen a post that I haven't , I've been searching for about 2 1/2 weeks for a resolution to this issue and have seen numerous bug reports for this chipset. Some people have reported great success with the workarounds I've already tried, but I'm just not lucky like that I suppose lol. 

Thanks in advance for anyone who can help or even tries this one is a mind boggler ;-)

On a side note her computer is the first I installed Natty on and it looks amazing lol.

---

### Post by TBABill on 2011-06-25
I have the same card in one laptop and on my Debian install I simply installed wicd and use it to connect without issue. Network manager was part of my problem. I have seen where users have removed network manager, then reinstalled it and that solved the problem. I have not tried that myself.

---

### Post by josephmills on 2011-06-25
if that wont work you could find a compat wireless file for your kernel and compile it there you go all patched up

---

### Post by Dangertux on 2011-06-25
> **TBABill said:**
> I have the same card in one laptop and on my Debian install I simply installed wicd and use it to connect without issue. Network manager was part of my problem. I have seen where users have removed network manager, then reinstalled it and that solved the problem. I have not tried that myself.

This appears to have solved the issue. Thank you very much for the outside perspective, I was so hung up on the driver issue I didn't think to even troubleshoot nm. 

The final fix that I did for Ubuntu 11.04 is this. In case anyone has this problem in the future. 

I had to use the madwifi drivers for this wicd did not even recognize any networks using the ath5k drivers.

All commands assume root so prepand sudo as necessary or sudo -i before doing this
```
 svn checkout http://madwifi-project.org/svn/madwifi/trunk - madwifi
cd madwifi
make && make install

```
Make sure you have subversion installed. For this to work (apt-get install subversion)
```

rm /etc/modprobe.d/blacklist-ath_pci.conf
echo "ath_pci" >> /etc/modules
echo "ath5k" >> /etc/modprobe.d/blacklist.conf
modprobe -r ath5k
modprobe ath_pci

```

Now to install Wicd 

```

apt-get install wicd

```

Now adding the Wicd network manager to the unity systray. You will need the dconf-tools package
```

apt-get install dconf-tools
dconf-editor

```

Go to desktop , unity , panel
Append 'Wicd' to the systray whitelist entry. 

Reboot or restart x server and enjoy. 

This works on the standard kernel that comes with 11.04 

It also works with the aforementioned wireless compatibility kernels however using the ath5k driver does not work on either at least for me.

---

