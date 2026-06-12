---
title: "HP g60-619ca wireless issue"
date: 2011-03-17
forum: Networking &amp; Wireless
---

### Post by samriggs on 2011-03-17
Hi everyone
My poor wife was doing a scan last night and while she was doing it I pressed the wireless connection button (beside the on/off button) and now it will not turn on the wireless anymore, I tried to enable it but its blued out and will not allow it to be clicked but the network enable is clicked, I tried to press the button again to reconnect the wireless with the button but no go it will not enable it at all.
the wireless card is intergrated 10/100 eternet LAN
Is there anyway that anyone knows to get this thing connecting again?
I feel bad that it was me that click the stupid button but on my laptop it works fine with no issues and always reconnects, it doesnt make sense to me, I tried to find the hardware drivers but all that shows up in 10.10 is additional drivers and nothing shows up in there in my laptop or hers.

any help would be appreciated.

Probably something simple but Im tired of trying to press that stupid button to reconnect it and it wont.

Thanks in advance
Sam

:confused:

---

### Post by samriggs on 2011-03-17
Also I cannot locate the drivers list when I click on additional drivers (since Hardware drivers does not show up at all in the menu and I cannot find it in the menu or add it) maybe its been renamed to additional drivers instead
It shows no drivers at all. 
I thought all I could do was find that driver for the wireless card and enable it. when I do the unblock wifi through the terminal nothing happens when I get the list it still shows its blocked.
hopefully someone can answer this one for me or Im going to have to reinstall it (another solution one person came up with which is one I am trying to avoid).
Who knew pressing the wireless button would disable it this way where it will not be enabled again through that same button.
Weird
Sam

---

### Post by Vi3tHoneyX on 2011-03-17
Make sure the wireless chip is turned back on and then right click on the Network Manager Icon (where you can choose what network to connect to) and see if "Enable Wireless" is able to be checked.

---

### Post by samriggs on 2011-03-17
How can I turn the wireless chip back on?
I tired to press the wireless button but it stays orange, I tired to find the drivers but nothing shows up, I even tried sudo rfkill unblock wifi but it remains blocked.
In the last version the drivers showed up under hardware drivers in 10.10 nothing shows up.
Hopefully you can tell me how to turn the chip back on because I think thats all it needs to enable it again, everything else works.

Thanks again for any help you can provide my wife thanks you also.
Especially if I get this fixed, we used the button before to disconnect wireless and it turned back on no problem, I just did it in the middle of a scan this time and no it will not enable at all.

Sam

---

### Post by samriggs on 2011-03-17
I just seen this in another post

Fixed! The card *was* off and just needed to be turned back on with:
 	Quote:
 	 	 		 			 				modprobe tc1100-wmi
echo "on" > /proc/acpi/wmi/WMID/wlan 			 		 	 	 
You can also turn it off (for plane flights, longer battery life etc) with:
 	Quote:
 	 	 		 			 				echo "off" > /proc/acpi/wmi/WMID/wlan 			 		

This was for a different ubuntu os version and not my card but this might be the solution, where can I find this in my computer to switch this on?

Anyone know?

Thanks in advance
Sam

---

### Post by varunendra on 2011-03-20
If you haven't reinstalled it yet, please post the outputs of:
```
lsmod
```

```
dmesg | grep wlan
```

```
sudo lshw -C network
```

and
```
ifconfig -a
```

Also, see if the wireless interface is "on" in BIOS, and if it works with a live CD.

---

### Post by samriggs on 2011-03-20
I tried most of those  checked out the reports and it kept saying network disabled or wireless disabled rfkill was 2.
if there was some file to turn it on somewhere like the other person did that would be great but I couldn't find the file on my wifes computer.
So I did the nightmare thing, reinstalled windows (YUK) the button turned blue again and bam there was a connection with no problem at all, then I resienstalled ubuntu again without windows again since we got absolutley no use for it. and put back her files, so shes got a clean computer now lol.
Just wish there was a button that would let me turn the switch back on, thats the first time its done that.
Anyhow thanks for trying to help anyhow.
I heard one of the updates did this to some netbooks that had the same issue I did, wondering if that same update did it to me on a notebook?
They fixed it by reverting back to a previous update instead.
well other than that, I love this OS, way better than windows crap virus infected overbloated slow as crap system, and mac.
thanks again
Sam):P

---

