---
title: "fwcutter is not working for me"
date: 2011-04-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ClientAlive on 2011-04-17
I had used fwcutter on this machine before when I first installed Ubuntu 11.04 and everything worked flawlessly. Within minutes I was up and running without having to be plugged in through the Ethernet cable. Yesterday/ last night I got myself into a situation that I could only solve by re-installing Ubuntu (11.04 beta 1).

My chipset:

05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


What I did:

Installed b43-fwcutter through the Software Center and then went into Additional Drivers to look for the driver to enable. It was not/ is not listed. I then made sure to update my system by running

```
 sudo apt-get update 
```

Then . . .

```
 sudo apt-get upgrade 
```

After that I uninstalled fwcutter through the Software Center and reinstalled through the command line . . .

```
 sudo apt-get install b43-fwcutter 
```

. . . and, again, went into Additional Drivers. Again/ still, nothing available to "Activate."

Am I missing something here? I followed the instructions given on this:  [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access)  Ubuntu help document.

Any help would really be appreciated.

Thanks
Jake
:)

---

### Post by josephmills on 2011-04-17
please post ```
lspci -vnn | grep 14e4 
```

---

### Post by ClientAlive on 2011-04-17
> **josephmills said:**
> please post ```
lspci -vnn | grep 14e4 
```


~$ lspci -vnn | grep 14e4
05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

Edit: Information not revealed about 14e4 in post

In the above paste there is something that was not carried over.  In terminal the "14e4" part of " . . . [14e4: 4318] . . . "  is actually red in color. It was red in the terminal.


Update:

I while I was away I found "firmware-b43-installer" in a search through Software Center; and: installed it, ran an update on my system, restarted, launched Additional Drivers. No change.

Edit: additional info

The code I was asked to run for that information ```
 lspci -vnn | grep 14e4 
``` was run after installing firmware-b43-installer" and everything I described in that paragraph (the paragraph just above).

The attachment shows what is installed on this machine with regard to b43.

Thanks
Jake

---

### Post by josephmills on 2011-04-17
go back to you package manager and in the search bar type in b43 then take a screen shot please thanks
**EDIT:**
to get to the package mnager go to System-->admin-->synaptic package manager 
then in the search bar type in b43 and then take screenshot thanks

---

### Post by ClientAlive on 2011-04-17
One moment please . . .

--------------------------------------

Attachment shows result of what you requested.

Thanks
Jake

---

### Post by josephmills on 2011-04-17
sorry about the delay could you go to Synaptic package manager then go to Settings-->Repositories (see pic) then take a pic of the "ubuntu software" Tab and the "Other Software" Tab

---

### Post by ClientAlive on 2011-04-17
Sorry now for my delay. I was keeping myself busy with a little Internet radio.

Here we are then.

Thanks

---

### Post by josephmills on 2011-04-17
**EDIT:**Could you upgrade again ```
sudo apt-get upgrade
```thanks after that could I see a ```
rfkill
``` thanks
and a ```
lsmod
```

---

### Post by ClientAlive on 2011-04-17
~$ man rfkill
~$ rfkill
Usage:    rfkill [options] command
Options:
    --version    show version (0.4-1 (Ubuntu))
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm


AND


~$ lsmod
Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  220 
aes_generic            38023  1 aes_i586
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  0 
snd_atiixp             19400  3 
snd_atiixp_modem       18624  5 
snd_ac97_codec        105614  2 snd_atiixp,snd_atiixp_modem
ac97_bus               12642  1 snd_ac97_codec
arc4                   12473  2 
joydev                 17322  0 
snd_seq_midi           13132  0 
snd_pcm                80244  6 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
b43                   296610  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73312  0 
mac80211              257001  1 b43
snd                    55295  21 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  3 snd_atiixp,snd_atiixp_modem,snd_pcm
k8temp                 12872  0 
pcmcia                 39671  0 
shpchp                 32345  0 
cfg80211              156212  2 b43,mac80211
i2c_piix4              13095  0 
serio_raw              12990  0 
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
radeon                896443  4 
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
drm                   180083  6 radeon,ttm,drm_kms_helper
8139too                23208  0 
ssb                    45942  1 b43
8139cp                 22497  0 
pata_atiixp            12968  3 
video                  18951  0 
i2c_algo_bit           13184  1 radeon
ati_agp                13202  0

---

### Post by josephmills on 2011-04-17
sorry about that could I see a ```
rfkill list
``` thanks

---

### Post by ClientAlive on 2011-04-17
Joseph:

Thank you for your help. I don't quite understand where this is going. I just upgraded like 2 hrs ago.

I'll giver er' another go and get that info here, ok? Just a minute.

Thaks
Jake

---

### Post by ClientAlive on 2011-04-17
~$ sudo apt-get upgrade
[sudo] password for jake: 
Sorry, try again.
[sudo] password for jake: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  banshee banshee-extension-soundmenu banshee-extension-ubuntuonemusicstore
  empathy empathy-common evolution-indicator gir1.2-unity-3.0 grub-common
  grub-pc libnm-glib2 libtotem-plparser17 lintian linux-generic
  linux-headers-generic linux-image-generic nautilus-sendto-empathy
  unity-place-applications unity-place-files xserver-xorg-video-all
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.



AND:


~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


AND:


~$ lsmod
Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  238 
aes_generic            38023  1 aes_i586
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  0 
snd_atiixp             19400  3 
snd_atiixp_modem       18624  5 
snd_ac97_codec        105614  2 snd_atiixp,snd_atiixp_modem
ac97_bus               12642  1 snd_ac97_codec
arc4                   12473  2 
joydev                 17322  0 
snd_seq_midi           13132  0 
snd_pcm                80244  6 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
b43                   296610  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73312  0 
mac80211              257001  1 b43
snd                    55295  21 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  3 snd_atiixp,snd_atiixp_modem,snd_pcm
k8temp                 12872  0 
pcmcia                 39671  0 
shpchp                 32345  0 
cfg80211              156212  2 b43,mac80211
i2c_piix4              13095  0 
serio_raw              12990  0 
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
radeon                896443  4 
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
drm                   180083  6 radeon,ttm,drm_kms_helper
8139too                23208  0 
ssb                    45942  1 b43
8139cp                 22497  0 
pata_atiixp            12968  3 
video                  18951  0 
i2c_algo_bit           13184  1 radeon
ati_agp                13202  0

---

### Post by josephmills on 2011-04-17
is bcmwl-modaliases installed under synaptic package manager?

---

### Post by ClientAlive on 2011-04-17
~$ sudo apt-get install bcmwl-modaliases
[sudo] password for jake: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package bcmwl-modaliases is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  bcmwl-kernel-source

E: Package 'bcmwl-modaliases' has no installation candidate



Should I look for "bcmwl-kernel-source"/

---

### Post by josephmills on 2011-04-17
> **ClientAlive said:**
> ~$ sudo apt-get install bcmwl-modaliases
[sudo] password for jake: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package bcmwl-modaliases is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  bcmwl-kernel-source

E: Package 'bcmwl-modaliases' has no installation candidate



Should I look for "bcmwl-kernel-source"/
not yet try and install through the Synaptic package manager (system-->admin-->synaptic package manager)
type in broadcom in the search bar then left click on the box for bcmwl-modaliases and mark for installation (see pic) After you marked for install left click on apply (see pic)

---

### Post by ClientAlive on 2011-04-17
Here's what I have available through synaptic.

Edit: bcmwl-mdaliases is not in the list.

---

### Post by josephmills on 2011-04-17
> **ClientAlive said:**
> Here's what I have available through synaptic.

Edit: bcmwl-mdaliases is not in the list.

install the bcmwl-kernel-source

---

### Post by ClientAlive on 2011-04-17
Installed "   bcmwl-kernel-source" from the terminal. My wireless network showed up in the list through the icon (at the top bar on my desktop. Clicked it, entered pass code. Seems to be working. I'm writing this to you with the Ethernet cable unplugged right now and connected through wireless.

I'd say - problem solved. I'm going to restart though and be sure everything goes well upon reboot.

Thanks.

I'll come back after restart for one more post and let you know if everything is still squared away - as I'm sure it will be.

Please check on my last post please - just in case.

Thanks
Jake

---

### Post by ClientAlive on 2011-04-17
After reboot I no longer have that wireless connection. I took a few pics that, hopefully, show where I am at and what's going on.

Picture_01:

That's what shows in the drop down list from the icon on my desktop. As you can see the option to enable wireless is no longer in the list. (It was there and was checked/ selected when I began this process.

---------------------------------------

Picture_02:

The Firefox test

Picture_03:

Back to the Ethernet cable

Picture_04:

The list after 'plugging in'

---------------------------------------

When I had the wireless connection (before reboot) I got a list of all the wireless networks around me - as it should be. There were about half a dozen of them including mine. After clicking my network and entering the pass code I had it until I rebooted. Even had it with the Ethernet cable removed.

Thanks

---

### Post by josephmills on 2011-04-17
check your package manager what is installed for broadcom. What is in system--admin--> Additional Drivers  is the card there ? did you update && upgrade after wireless was up?

---

### Post by ClientAlive on 2011-04-17
Picture shows what is in Additional Drivers. This is now as it has been all along. Just the one for the software modem.

Ran update through terminal - results are as follows (nothing new in the neighborhood):


~$ sudo apt-get upgrade
[sudo] password for jake: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  banshee banshee-extension-soundmenu banshee-extension-ubuntuonemusicstore
  empathy empathy-common evolution-indicator gir1.2-unity-3.0 grub-common
  grub-pc libnm-glib2 libtotem-plparser17 lintian linux-generic
  linux-headers-generic linux-image-generic nautilus-sendto-empathy
  unity-place-applications unity-place-files xserver-xorg-video-all
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.


This update was not run when I had the wireless connection before reboot. It was run just now, after having to plug back into Ethernet. I just didn't think of it at the time the wireless connection was active.

What seems odd to me is that there is not an item in my drop down list Wireless Enabled (may not be an exact quote of that item, but close). That item has always been there that I can recall and is always checked by default - even when wireless is not set up - it is always there and checked.

Jake

Edit: Sorry, I've attached another picture that shows what is installed. Looks like just fwcutter and the    bcmwl-kernel-source.

---

### Post by josephmills on 2011-04-17
what about the synaptic package manager with "broadcom" in the search what do you see?

---

### Post by josephmills on 2011-04-17
```
rfkill list 
```

---

### Post by ClientAlive on 2011-04-17
"Broadcom" was the search term. I went ahead and did it again just now to be sure. Same list. Notice that it says "Braodcom" in that field in the picture.

Thanks

---

### Post by ClientAlive on 2011-04-17
I almost don''t want to post this because I'm not ready to give up on this and I' hope you aren't either. You are the only person communicating with me in this thread.

Check this out. I don't know what it really means and I don't know that it even applies, but I though I would look around on the internet - google search term:  ubuntu 11.04 bug enable wireless

[http://ubuntuforums.org/showthread.php?p=10626052](http://ubuntuforums.org/showthread.php?p=10626052)

AND:

[http://ubuntuforums.org/showthread.php?t=1713800&page=3](http://ubuntuforums.org/showthread.php?t=1713800&page=3)

Here the result of rfkill list looks different to me somehow. I can't quite place it. Maybe just less information listed.

~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no


Thanks

------------------------------

Edit:

It is different - as compared to what is in post #12 of this thread.

---

### Post by ClientAlive on 2011-04-17
Joseph:

I don't think that fwcutter ever did do anything from the beginning (this time I mean). As I remember it the first time around (before this recent re-install) all I did was install b43-fwcutter, nothing else. Then I went into Additional Drivers, the driver showed up there, I enabled it and everything worked fine. Now one difference between then and now is this. Then (when I first installed Natty) it was the Alpha 3. Now (with this fresh install) it is Beta 1 and then updates/ upgrades up to just a little while ago when we last did it.

Jake

---

### Post by ClientAlive on 2011-04-19
Helleluja!! Problem solved! Thanks you so much josephmills. You really stuck this thing out with me. I'm very new to Linux (roughly a month now) so some of what we did was a little over my head, but we did finally get it working.

I wish I could post more of the details on how this was solved but I really just followed the instructions I was given as we worked though it. Those details are coming though and will be posted here soon.

Thanks so much guys. Lotsa' love in the Linux community. Lotsa' love in my heart tonight.

Sincerely,
Jake
):P

---

### Post by josephmills on 2011-04-19
we would get it working then it would stop on reboot when he ran a ```
dmesg | grep b43
```He would Get ```
<jake_> [    2.095461] b43-pci-bridge 0000:05:02.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
<jake_> [   22.147986] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
<jake_> [   22.342796] Registered led device: b43-phy0::radio
<jake_> [   22.933633] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
<jake_> [   22.933640] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
<jake_> [   22.933644] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
<jake_> [  788.268402] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
<jake_> [  788.268413] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
<jake_> [  788.268422] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
<jake_> [ 1016.706752] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
<jake_> [ 1016.706764] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
<jake_> [ 1016.706772] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
<jake_> [ 1251.368059] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
```  and here lies the trouble we needed to get the b43fwcutter package from a different source so he download a different source. [http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)
then made a folder and called it wireless then put the downloaded package in the new folder (wireless) then opened the terminal and typed ```
sudo cp -r ~/wireless/* /lib/firmware/
``` then ```
cd /lib/firmware/
``` then ```
sudo -s 
``` then ```
tar -xzf b43-all-fw.tar_.gz
``` then ```
exit
```then ```
sudo reboot
```Hope that this helps someone else

---

### Post by ClientAlive on 2011-04-19
That's the Linux Community?
THATS THE LINUX COMMUNITY BABY!!!
Frickin' teamwork dudes!
 wow!!

You rock joshephmills!

---

### Post by xasha on 2011-04-26
Just wanted to say that the solution worked for me too. Thanks to JosephMills for taking the time to help everyone who has this problem too! :grin:

---

