---
title: "wireless disabled by hardware switch"
date: 2012-05-10
forum: Networking &amp; Wireless
---

### Post by thegringo44 on 2012-05-10
Hello, I'm currently running ubuntu 12.04 with Intel Corporation Centrino Advanced-N 6230 as my network controller. I cannot connect to wifi because it says "wireless disabled by hardware switch". 

rfkill list
[HTML]0: dell-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: dell-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: yes
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
[/HTML]

I've attempted sudo rmmod dell-laptop then running rfkill unblock all, as well as many variants of that with no success.

The radio button for dell xps 15z is fn+F2, however this doesn't do anything, nor does any other button combination.

---

### Post by chili555 on 2012-05-10
Is it dell-laptop or dell-wmi that's loaded? Find out with:```
lsmod | grep dell
```Remove whichever is loaded: for example:```
sudo rmmod -f dell-laptop
sudo rfkill unblock all
rfkill list all
```Please post the result.

---

### Post by thegringo44 on 2012-05-10
Laptop

[HTML]dell_laptop            18119  0 
dcdbas                 14490  1 dell_laptop
[/HTML]

[HTML]2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
[/HTML]

Still giving the wireless is disabled message.

---

### Post by chili555 on 2012-05-10
And is the Fn+F2 combination still unresponsive?

---

### Post by thegringo44 on 2012-05-10
Still unresponsive. Aside from the Fn+F2 combination there is a button on the side that I didn't notice until today that I assume is for wireless as well. It lights up after I touch it, but doesn't solve the wifi problem. I'm not entirely sure it's for wireless though, because when I was running windows the Fn+F2 is the only combination I ever used.


Edit: Just googled a dell manual, it's a battery indicator, not wireless. lol

---

### Post by chili555 on 2012-05-10
I just saw this: [http://askubuntu.com/questions/69234/centrino-advanced-n-6230-and-bluetooth-wireless-problems-with-dell-xps-15z](http://askubuntu.com/questions/69234/centrino-advanced-n-6230-and-bluetooth-wireless-problems-with-dell-xps-15z)

Is bluetooth enabled or disabled in the panel? How about in the BIOS? Does this help?```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi bt_coex_active=N
sudo rfkill unblock all
rfkill list all
```

---

### Post by thegringo44 on 2012-05-10
Bluetooth is disabled. In fact, I think what started this whole thing was accidentally pressing the bluetooth button at the top. The bluetooth iconDisappears (as I would expect) when the dell laptop is removed.

The BIOS doesn't have an explicit option for wireless/bluetooth, but it's set to the default configurations, so I don't think that's the issue.
[HTML]13: dell-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
14: dell-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: yes
16: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
[/HTML]

I also ran what you just posted by removing the dell-laptop first, which gives:
[HTML]19: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
[/HTML]


I have a bad feeling that fixing this is going to involve installing windows.

---

### Post by chili555 on 2012-05-10
There are three other things you might try. I worked on a case a few months ago where the key combination was mis-mapped in *dell-laptop*. The poster got it to respond with Alt+F2. You might experiment with other combinations including Alt+F3, F4, etc. Then try Ctrl+F2, F3, etc.

Next, try holding down Fn+F2 as you boot. Does the light come on or even flicker? Try the same with the bluetooth button. 

I will keep Googling and suggest you do also.

---

### Post by thegringo44 on 2012-05-10
> **chili555 said:**
> There are three other things you might try. I worked on a case a few months ago where the key combination was mis-mapped in *dell-laptop*. The poster got it to respond with Alt+F2. You might experiment with other combinations including Alt+F3, F4, etc. Then try Ctrl+F2, F3, etc.

Next, try holding down Fn+F2 as you boot. Does the light come on or even flicker? Try the same with the bluetooth button. 

I will keep Googling and suggest you do also.

I've tried every key combination I can think while playing with  rfkill and dell-laptop, and tried to boot it using various key combinations. I even attempted the key combinations using an on screen keyboard on the off chance the keys themselves were messed up lol, but none of it seems to do anything

Edit: It's also slightly frustrating that as far as I know there isn't even a light for wireless connection on this dell model

P.S. - Thank you for the help so far!

---

### Post by chili555 on 2012-05-10
I'm sorry; I'm out of ideas/mojo/talent. I wish I could be more help. You might look for and add to a bug about dell-laptop, or start one. [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

---

### Post by thegringo44 on 2012-05-24
After I made this thread I spent about a week or so googling this problem and came up with nothing. I finally bit the bullet and made a windows partition. As expected, the hardware switch/wireless/bluetooth worked in windows. However, after turning it on in windows and switching back to Ubuntu, it DID NOT turn the wireless switch on or even make the fn+f2 combination responsive in Ubuntu. I can't describe how disappointing this was. Although this allowed me to at least connect to wireless via my windows partition, that still sucked.


A couple of minutes ago I was using Ubuntu on a wired connection when the laptop battery ran out. I plugged it back in and booted into Ubuntu and THE WIRELESS WAS ON! This is probably the highlight of my day.

I have no idea if installing windows had anything to do with this or why letting the battery die even worked, but if anybody is suffering from an issue similar to mine try letting your battery die.

---

### Post by mringer on 2012-05-30
post 4 in this thread may be helpful:

[http://ubuntuforums.org/showthread.php?t=1946474](http://ubuntuforums.org/showthread.php?t=1946474)

I suggest that you backup your files first.

---

### Post by rthorpe on 2012-07-29
I recently had the same problem on my Dell Inspiron 1545 notebook running XUbuntu 12.04.

I booted into the BIOS setup. In the "Wireless" menu there is a menu that controls which wireless cards the hardware switch controls. There are two checkboxes, one for Bluetooth and another for Wireless LAN. I unchecked the Wireless LAN checkbox. After doing that wireless LAN works fine. Since I don't really use the switch that's a good enough fix for me.

---

### Post by ughknight on 2013-04-25
I see that this has been marked solved, but so far I haven't been able to fix this. I believe I've tried everything in this thread (and some stuff not in this thread), both the modprobe rfkill stuff and letting the battery wind down. I even opened it up and unplugged the battery to discharge all the power. Like the above poster, I do have a Windows (7) installation as well, where I am easily able to turn on the wireless with Fn+F2 -- but the change doesn't "stick" on reboot. 

More related information:

1) ACPI.  This laptop has known acpi issues that are detailed elsewhere, that is, the screen doesn't turn on if ACPI is normally enabled. The common fix that is given is to include "acpi=noirq" as a kernel parameter at boot (for my kernel). This *also* does not work for me, I have to include "acpi=off" instead. 

2) This darn problem seems to affect USB wireless cards as well. I picked up a cheap "Tenda" wireless adapter (it's tiny, but it works on other computers fine) and figured I'd give that a go. The Tenda shows up and even claims to be "unblocked" when you run an "rfkill" list -- and can even scan for networks -- but still doesn't seem to be able to connect. Nm-applet reports that it's also hardware blocked, and manually running dhclient hangs. 

Any help, anyone? Thanks so much in advance.

---

### Post by ughknight on 2013-04-25
It fixed itself. This is the strangest problem I have ever seen.  Someone somewhere else reported that it fixed itself after simply plugging in an Ethernet cable.  Mine fixed itself, not after plugging in any cable (it didn't work at home)  -- but once I connected via the same cable at the same location at work where I lost the signal, it fixed itself. That is literally the only thing different, everything else I tried before. What. The. Heck.

---

### Post by MrKappa on 2013-09-10
Same problem here with Toshiba r840 with the same adapter. 
It's a disappointing reason that previously, around 1-2 years ago, this laptop was working fine as far I remember, looks like that support has been removed from the kernel? I don't understand because apparently Intel provide the drivers on their web site.

---

### Post by chili555 on 2013-09-10
> **MrKappa said:**
> Same problem here with Toshiba r840 with the same adapter. 
It's a disappointing reason that previously, around 1-2 years ago, this laptop was working fine as far I remember, looks like that support has been removed from the kernel? I don't understand because apparently Intel provide the drivers on their web site.And you believe it's the Intel wireless driver and not the toshiba_acpi module because...what?

Please post:```
lsmod | grep -e iwl -e tosh
rfkill list all
lsb_release -d
```What model Toshiba is it, exactly?

---

### Post by MrKappa on 2013-09-13
> **chili555 said:**
> And you believe it's the Intel wireless driver and not the toshiba_acpi module because...what?

Please post:```
lsmod | grep -e iwl -e tosh
rfkill list all
lsb_release -d
```What model Toshiba is it, exactly?

Hello' Chili, thanks for the help!

My laptop is Toshiba Tecra R840-11E

iwldvm                220185  0 
mac80211              526519  1 iwldvm
toshiba_acpi           18270  0 
toshiba_bluetooth      12748  0 
iwlwifi               155077  1 iwldvm
sparse_keymap          13658  1 toshiba_acpi
wmi                    18590  1 toshiba_acpi
cfg80211              436177  3 iwlwifi,mac80211,iwldvm


0: Toshiba Bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

Now I'm with LinuxMint because I was testing some distros just to check for changes but no difference. 

I tried with 
" rfkill unblock 1" but it stay hard blocked :(

---

### Post by chili555 on 2013-09-13
> Now I'm with LinuxMint because I was testing some distros just to check for changes but no difference.Please ask here: [http://forums.linuxmint.com/viewforum.php?f=53](http://forums.linuxmint.com/viewforum.php?f=53)

I can assure you that the Intel driver works well and the hardware block is your entire issue.

---

### Post by MrKappa on 2013-09-14
As also reported in this discussion and others for similar issues of "hardware block" I found also that the "crazy" solution is working:

[http://ubuntuforums.org/showthread.php?t=1946474&p=11974636#post11974636](http://ubuntuforums.org/showthread.php?t=1946474&p=11974636#post11974636)

Some users randomly found wi-fi working again after they found the battery completely drained. It explain also why I remember that in previous tests wi-fi was working in the past and I could not understand this problem. I hope can help others.

---

### Post by Torquepsyche on 2014-01-15
Wow, this solution worked for me too. Interestingly, when i connected to my college wifi environment the wireless got disabled which was working fine alright.


root@Basant-Netbook:/home/torquepsyche# rfkill list all
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: sony-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
3: sony-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
root@Basant-Netbook:/home/torquepsyche# rfkill unblock all
root@Basant-Netbook:/home/torquepsyche# rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: sony-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

Thanks all for this information.

---

### Post by andre29 on 2014-09-27
Had the same problem with my Compaq nx7300. Just went the BIOS and restored its configuration to default. Worked for me. Now my > rfkill list shows my wireless LAN soft and hard blocked to NO.

---

