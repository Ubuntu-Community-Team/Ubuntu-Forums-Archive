---
title: "HP Pavilion dv2000 &quot;wireless is disabled by hardware switch&quot;"
date: 2011-08-04
forum: Networking &amp; Wireless
---

### Post by pauljj on 2011-08-04
Hi,

I recently installed ubuntu 11.04 but I'm having problems connecting to the internet via wireless. 
I did the "rkill list" which ended up like this:
phy0: wireless Lan
soft blocked: yes
hard blocked: yes
hp wifi: wireless Lan
soft blocked: yes
hard blocked: no
hp-bluetooth: Bluetooth
Soft blocked: yes
Hard blocked: no

EDIT: the switch is turned ON but it's still orange

---

### Post by chili555 on 2011-08-04
Is there any improvement if you do:```
sudo rmmod -f hp-wmi
sudo rfkill unblock all
rfkill list all
```Thanks.

---

### Post by erotavlas on 2012-02-02
> **chili555 said:**
> Is there any improvement if you do:```
sudo rmmod -f hp-wmi
sudo rfkill unblock all
rfkill list all
```Thanks.

Hi,

I have a HP dv2780 and I have the same problem with Ubuntu 11.10. I used your procedure and it worked only one time. Now if I type rfkill list all i get
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

What can I do?

Thank you

---

### Post by bkratz on 2012-02-02
> **erotavlas said:**
> Hi,

I have a HP dv2780 and I have the same problem with Ubuntu 11.10. I used your procedure and it worked only one time. Now if I type rfkill list all i get
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```What can I do?

Thank you


The removal of  hp-wmi would only affect the current operation--rebooting would reload the file the next time so you would have to remove it again.  You need to look up "blacklisting modules" and add it to your "blacklist"  to make it not load during the next reboot cycle.

---

### Post by erotavlas on 2012-02-02
> **bkratz said:**
> The removal of  hp-wmi would only affect the current operation--rebooting would reload the file the next time so you would have to remove it again.  You need to look up "blacklisting modules" and add it to your "blacklist"  to make it not load during the next reboot cycle.

Ok, but now the command sudo rfkill unblock all doesn't work. Why?

---

### Post by bkratz on 2012-02-02
> **erotavlas said:**
> Ok, but now the command sudo rfkill unblock all doesn't work. Why?



So you did add this to the blacklist file and reboot? If so, you may want to post the results of:

```
lsmod
rfkill list all
```

using the code tags <> to make it easier to read.

---

### Post by erotavlas on 2012-02-04
> **bkratz said:**
> So you did add this to the blacklist file and reboot? If so, you may want to post the results of:

```
lsmod
rfkill list all
```using the code tags <> to make it easier to read.

Hi,

this is my output of rfkill list all command
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes

```

then when I execute the commands
sudo rmmod -f hp-wmi
sudo rfkill unblock all
rfkill list all
the output became
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

Thank you

---

### Post by chili555 on 2012-02-04
> Hard blocked: yesThat strongly suggests that the hardware wireless switch on your laptop is set to 'Off.'

---

### Post by erotavlas on 2012-02-04
> **chili555 said:**
> That strongly suggests that the hardware wireless switch on your laptop is set to 'Off.'

Now the switch does not work. If I change the position the light remains orange...It worked only first time...why?

---

### Post by chili555 on 2012-02-04
Forget about the light for now. Please do:```
sudo rmmod -f hp-wmi
sudo rfkill unblock all
rfkill list all
```Is it still hard blocked? Move the switch and check:```
rfkill list all
```Is there any setting in the BIOS related to the wireless switch?

---

### Post by erotavlas on 2012-02-04
> **chili555 said:**
> Forget about the light for now. Please do:```
sudo rmmod -f hp-wmi
sudo rfkill unblock all
rfkill list all
```Is it still hard blocked? Move the switch and check:```
rfkill list all
```Is there any setting in the BIOS related to the wireless switch?

Yes is still hard blocked. There is no BIOS setting for wifi. The strange is that it worked the first time when I saw the post.

---

### Post by bkratz on 2012-02-04
Note to Dr. Chili,

Do you think post 19 of this thread would help? It seems to have done the trick for another user>

[http://ubuntuforums.org/showthread.php?t=1775555&page=2](http://ubuntuforums.org/showthread.php?t=1775555&page=2)

---

### Post by chili555 on 2012-02-04
> **bkratz said:**
> Note to Dr. Chili,

Do you think post 19 of this thread would help? It seems to have done the trick for another user>

[http://ubuntuforums.org/showthread.php?t=1775555&page=2](http://ubuntuforums.org/showthread.php?t=1775555&page=2)> You can add a module parameter for the module hp_wmi:
```
echo "options hp_wmi wireless=1" | sudo tee /etc/modprobe.d/hp_wmi.conf

```
Reboot your system and:
```
sudo rfkill unblock all
```

Here's the problem with that. Please look at:```
$ **modinfo hp-wmi**
filename:       /lib/modules/3.0.0-15-generic/kernel/drivers/platform/x86/hp-wmi.ko
alias:          wmi:5FB7F034-2C63-45e9-BE91-3D44E2C707E4
alias:          wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C
license:        GPL
description:    HP laptop WMI hotkeys driver
author:         Matthew Garrett <mjg59@srcf.ucam.org>
srcversion:     0E6B229578FB67D418B8C90
depends:        wmi,sparse-keymap
vermagic:       3.0.0-15-generic SMP mod_unload modversions 686 
```As you can see, 'wireless=1' is not a loadable parameter. In fact, there are *NO* loadable parameters.

---

### Post by bkratz on 2012-02-04
Always a learning experience, thanks Doc!

---

### Post by chencho on 2012-09-19
I just installed 12.04 and I'm having the same issue. It says that the "wireless is disabled by a hardware switch". I've already done the "sudo rfkill unblock all" command and rebooted without any results.

EDIT: I managed to find a solution, woohoo!

Found it here: [http://askubuntu.com/questions/137437/wireless-network-not-working-on-hp-pavilion-dv2000](http://askubuntu.com/questions/137437/wireless-network-not-working-on-hp-pavilion-dv2000)

**Have you tried uninstall & reinstall from the command line?**

  I realize you said you have already tried uninstalling &  reinstalling, but since the best recommendation I have been able to come  up with was [this answer]("http://askubuntu.com/a/132693/52923") by [Mattlinux1]("http://askubuntu.com/users/54224/mattlinux1") to his own question, I figured it was at least worth suggesting.
  Please have a look at his answer (and question) for the complete  context. What he suggests appears to be just uninstalling and  reinstalling the drivers using the command line in a terminal window.
  The excerpt below was copied from Mattlinux1's answer which I provided a link to above.
  
[LIST]
[*]**Note:**
Before doing an  apt-get install, please use sudo apt-get update to ensure you get the most recent version when you do the install.
[/LIST]
  [INDENT]   I used the commands:
  sudo apt-get remove bcmwl-kernel-source sudo apt-get install bcmwl-kernel-source       *Or use purge instead of remove to wipe it, then re-install.*
      This worked to re-install the wifi drivers now my wifi is working.
 [/INDENT]

I ended up doing those two commands rebooting and found the new "enable wireless" option and clicked on it. Then I chose my wireless network. For a moment there I thought I was going to have to reinstall Windows on this computer. It's just so much faster running Ubuntu.

---

