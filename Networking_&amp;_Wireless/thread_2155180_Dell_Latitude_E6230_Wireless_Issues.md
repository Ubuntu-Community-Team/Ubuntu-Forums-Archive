---
title: "Dell Latitude E6230 Wireless Issues"
date: 2013-06-17
forum: Networking &amp; Wireless
---

### Post by rondamato on 2013-06-17
Let me tell you what's happening--perhaps you can tell me if what I THINK is happening is indeed happening. This is a Dell Latitude E6230 laptop running 12.04LTS...and yes, a lot of this post is copypasta'ed from last week--same issue!

When I restart the computer the same thing that I posted about last week again happens--no wireless. We have a "Guest" network that requires no security--this is what I am trying to connect to.
 
When I start I am told that there are &#8220;wireless networks available.&#8221; When I try to connect the wireless icon at the top of the screen just &#8220;scans&#8221; until the machine errors out with &#8220;Wireless Network&#8212;Disconnected.&#8221;

The only way that I can connect is, when the machine is logged into and a term window is opened, I issue these commands:

```

sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma

```
...and the wireless icon changes from a "scanning" icon to a solid "outline" of the icon.

To connect to the network though I must enter:

```

sudo modprobe wl

```


After this the icon turns solid and the computer informs me that I am connected to "guest." But ONLY after I type this line.

When I look in the /etc/modules file the only modules that are shown are lp, rtc, and wl.

So...I have no trouble getting this to work as long as I issue the above commands--what I'm not understanding is WHY these commands are not persistent...ie, why do I HAVE to run them each and every time the computer is booted and what can I do to prevent this?

I appreciate all of your help and I'm sorry that I'm not "getting" this--trust me, it's frustrating especially since my deadline for this machine's completion is in about two hours!

Thanks again,

Ron


PS--Thought it might help to know that I cannot enter ONE of those lines and get it to work. Thought just the "modprobe wl" would suffice but it does not--I must enter

```

sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma

```

first and then

```

sudo modprobe wl

```


After this the computer automatically connects to the "Guest" account in about 8-10 seconds.

I have tried blacklisting b43, ssb, bcma, and brcmsmac in /etc/modprobe.d/blacklist.conf and it&#8217;s still the same story&#8230;I thought that I had this fixed but upon reboot it just cycles until the wifi eventually gives out. If I enter the above modprobe lines it all works though.

I have tried to run a

```

sudo apt-get update && apt-get upgrade

```


Also&#8230;to no effect. This is infuriating as it worked last week and I shut the computer down for the weekend&#8230;now it no longer works&#8212;which just doesn&#8217;t make sense.
Anybody have any ideas?

As always thank you--the Ubuntu community is THE BEST--in fact the community is WHY I run this OS (besides for it kicking serious ass). So thanks!

---

### Post by Hadaka on 2013-06-17
Hi, give this a try...
```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```

---

### Post by rondamato on 2013-06-17
Hello,

Nope, same story.

The wireless networks show up in the drop-down, but selecting one just shows the icon scanning...scanning...until finally it says "Network Disconnected--You are now offline"--and then the scanning again.

If I try to select "Guest" I get "Wireless Network--you are now disconnected" and the scanning...scanning...until the icon goes to an outline and I get "Wireless Network--You are now offline."

Keep in mind that a

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma[/FONT][/COLOR]
```

followed by a

```
sudo modprobe wl
```

allows it to connect to "Guest" WITHOUT ME DOING ANYTHING. No selecting, no nothing--it just works. Arrrgh!!

Thanks Hadaka and everyone else--this is driving me batty. If any of you need specific output just let me know.

Ron

---

### Post by Hadaka on 2013-06-17
ok,lets look at some stuff..
please post the output of..
```
lsmod
cat /etc/modules
cat /etc/network/interfaces
cat /etc/modprobe.d/blacklist.conf | grep blacklist 
```
thanks.

---

### Post by rondamato on 2013-06-18
Hello friends!

OK, sorry for the delay. I will send that output now. Keep in mind that I am ON the machine in question right now--connected through wireless on the "guest" account using the procedure that I described a few messages ago.

```
lsmod
```

Module                  Size  Used by
wl                   3074942  0 
cfg80211              208382  1 wl
snd_hda_codec_hdmi     32476  1 
snd_hda_codec_idt      70774  1 
rfcomm                 47562  0 
bnep                   18240  2 
bluetooth             211812  10 rfcomm,bnep
nls_iso8859_1          12714  1 
coretemp               13642  0 
kvm_intel             137888  0 
kvm                   422160  1 kvm_intel
ghash_clmulni_intel    13221  0 
aesni_intel            51134  0 
cryptd                 20531  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
dell_wmi               12682  0 
sparse_keymap          13891  1 dell_wmi
ppdev                  17114  0 
dell_laptop            17426  0 
dcdbas                 14491  1 dell_laptop
snd_hda_intel          34117  3 
snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
microcode              23030  0 
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
psmouse               102075  0 
serio_raw              13216  0 
lpc_ich                17145  0 
mei                    41410  0 
i915                  530857  3 
drm_kms_helper         49259  1 i915
drm                   290344  4 i915,drm_kms_helper
i2c_algo_bit           13565  1 i915
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    83674  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15092  1 snd
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
lib80211_crypt_tkip    17391  0 
parport_pc             32867  0 
wmi                    19257  1 dell_wmi
video                  19598  1 i915
lib80211               14382  2 wl,lib80211_crypt_tkip
mac_hid                13254  0 
lp                     17800  0 
parport                46563  3 ppdev,parport_pc,lp
sdhci_pci              18749  0 
sdhci                  33145  1 sdhci_pci
e1000e                198734  0 

```
cat /etc/modules
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
wl

```
cat /etc/network/interfaces
```
auto lo
iface lo inet loopback

```
cat /etc/modprobe.d/blacklist.conf | grep blacklist
```
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist b43
blacklist ssb
blacklist bcma
blacklist brcmsmac



Sorry that all took so long but I went home for the evening and didn't have the machine handy!

Many thanks folks,

Ron

---

### Post by Hadaka on 2013-06-18
Hi, your last printout shows a working connection (Guest?)
Just so I'm not confused..when you say..GUEST...is it actually guest?
as in  does your Desktop log on area look like this..

Rondamado
[password area]
Guest

if thats what you are calling guest...its not...thats normal.
so set me straight on this and we shall go forward..
thanks.

---

### Post by rondamato on 2013-06-18
Hello,

No, there is one user in this machine (besides for the root account)--his name is Raju. So at the login screen I click "Raju" and enter password.

"GUEST" is just the name of our company-wide "guest" wifi network. When I run those modprobes the machine connects to it via wifi first because it has no security.

The other company-wide wifi networks also show up in the drop-down list but these are all WPA2 and require typing in company username/pw creds to login. Right now I am using the example of "guest" because it is easiest and will probably be the WAP that Raju uses when he gets his new Ubuntu machine.

Hope I cleared that up for you good sir!

Ron

---

### Post by Hadaka on 2013-06-18
Hi, Im only slightly confused now..thanks..
Is this GUEST network on a separate router...or a router that can have 2 connections?

either way... you should have a separate ap connection defined for it. see attached.
[ATTACH=CONFIG]243941[/ATTACH]

---

### Post by rondamato on 2013-06-18
Hello again,

Yes, it is set up like that. If I go into Edit Connections>Wireless (forgive me, not in front of it right at this minute) the GUEST connection exists and security is set to NONE...just like in your screenshot. It also shows how many minutes since last connected, etc.

So yeah, you are NOT confused, you are 100% correct.

As I said, the networks DO show up in the dropdown, and YES, they all originate from the same WAP (or rather hundreds of WAPs). So I can SEE their names in the dropdown, I can select them, but when I do the icon just "scans" until it finally gives up.

If I issue the modprobe commands the machine will, within 5 seconds, "lock onto" GUEST and the "scanning" is replaced by a solid wireless icon that shows signal strength, as it should be. BUT, unless I issue the modprobe commands, the machine will not "lock onto" ANY of the WAPs' networks no matter which one I select. It will just "scan" and eventually throw up a message that says "Wireless Networking--You are Disconnected" or something of the sort.

Hope this helps the confusion but it seems like you DO understand perfectly after re-reading your post. You ARE on track so no worries there!

Thanks much!

Ron

---

### Post by Hadaka on 2013-06-18
Hi, I'm here for about an hour then will back late
this afternoon. Try this, (I want to narrow this down)
try to connect to your "Guest" access point.
when it fails, do this..
```
sudo modprobe -rf wl
sudo modprobe wl
```
does it connect?
*If yes, then try to connect to "Guest" again..
this time, no commands, uncheck "ENABLE WIRELESS"
and then recheck it.....does it connect now?
thanks.

---

### Post by rondamato on 2013-06-20
OK, here's what happened (and I'm sorry for taking so long to answer--was off yesterday):

Booted machine--did not connect--wifi icon just kept "scanning."

Entered first command--box comes up saying that wireless is disconnected.

Entered second command--machine connected to "Guest" nearly immediately.

Unchecked "enable wireless"--icon immediately turned to an "outline" of the wifi icon and machine was disconnected.

Re-checked "enable wireless" and the machine did NOT connect--icon just keeps "scanning." Although I can see "Guest" in the last of available APs, when I click it a box pops up that says "Guest--You are now disconnected" and the scanning continues.

Tried a reboot--same story. Icon just keeps "scanning." Just so it's clear--when I reboot if I simply enter:

```
sudo modprobe wl
```

The icon keeps scanning--no connection. I MUST enter the 

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma[/FONT][/COLOR]
```

FIRST and then enter the 

```
sudo modprobe wl
```

command for it to connect to the "Guest" AP. If I only enter one line or another--or enter them out of order--the machine will NOT connect to "Guest." BOTH lines must be entered...and in the same order.

If at any time I uncheck "Enable Wireless" the machine disconnects from the AP and will NOT connect again unless I re-open a term and re-enter the two modprobe commands.

Thanks for all your help friends!

Ron

---

### Post by Hadaka on 2013-06-20
Hi, this line you enter..

[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma

is an indication that one or more of those drivers is
being loaded. Yet they are blacklisted. boot the machine
and try to connect,but...leave "WL" OUT of the list. I would like
to determine if other drivers are being loaded or if there is a problem
with whith the wl driver.
so on reboot do..
[/FONT][/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono][COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -r b43 ssb brcmfmac brcmsmac bcma
[/FONT][/COLOR][/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
then.
```
sudo modprobe wl
```
thanks.
[/FONT][/COLOR]

---

### Post by rondamato on 2013-06-20
Hello there,

OK, I see where you're going with this! I had never had to mess with these drivers so much in the past!

OK, just rebooted, right now the screen shows the wifi icon (in the upper right) "scanning" and not connecting. It finally timed out and now there is just an outline of the wifi icon with the inside blank.

Going to a term, I am typing:

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -r b43 ssb brcmfmac brcmsmac bcma[/FONT][/COLOR]
```

leaving the "wl" out of the command...and nothing happened of course, and the wifi icon is still an outline.

Now I am issuing the 

```
sudo modprobe wl
```

command.

Absolutely nothing happened, the wifi icon is still "outlined" and there were no pop-up boxes telling me anything. That kinda surprised me.

I went back and issued the 

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma[/FONT][/COLOR]
```

and then the

```
sudo modprobe wl
```

commands, which will usually start up the connection. After a brief minute of "scanning" the machine displayed the "disconnected" box, now it is just "scanning" and will not connect to anything.

Went ahead and rebooted the machine; the wifi icon is "scanning" as usual--no connection. I then went into a term and issued my original two commands, the

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma[/FONT][/COLOR]
```

followed by the

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe wl[/FONT][/COLOR]
```

command as usual--and of course the machine nearly instantly connected to "Guest."

I'm not sure what this means but the weirdness is starting to get to me!!

Thanks,

Ron

PS--Just to make sure I'm understanding this--it's the "wl" driver that's making the wifi chipset "work"--correct? By entering the first command I surmise that I am removing those modules (drivers) from memory--then by issuing the second command (the modprobe wl one) I am loading ONLY the "wl" driver, correct? Now I'm guessing that the "blacklist" should prevent the loading of drivers...so, of the package, the "wl" driver should be the only one loading. Am I correct in this description? I care far more about understanding what commands I am issuing than getting the thing to work of course! Thanks.

---

### Post by Hadaka on 2013-06-20
Hi, yes..thats correct the wl driver is what your card
uses. so lets try the same thing but with just the wl
and leave the rest out.
boot..let it fail
then do..
```
sudo modprobe -r wl
sudo modprobe wl
```
does it connect?

also "So at the login screen I click "Raju" and enter password."
do you have a "list" of possible users..or just Raju...and why would you
have to choose his name?..if he is the only user besides root..his name
should be above the password field.
im trying to get a crystal clear picture of exactly whats going on.
thanks.

---

### Post by rondamato on 2013-06-20
OK, trying now.

Issued the ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -r wl[/FONT][/COLOR]
``` command and received the pop-up stating "Disconnected--You are now offline."

I then entered the ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe wl[/FONT][/COLOR]
``` command. I got the pop-up "Network Disconnected--You are now offline" followed by the "scanning" icon. The wifi never reconnected. The list of APs is still there, but choosing one just results in the icon "scanning" for awhile, then a message pops up saying "Wireless Network--Disconnected. You are now offline" followed by more scanning. Again, the list of APs is still there, but choosing one will not do anything--it will just continue "scanning."

I then tried issuing the same two commands that I have been issuing, namely the ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma[/FONT][/COLOR]
``` followed by the ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe wl[/FONT][/COLOR]
``` command, and the machine, again, nearly instantly connects to the "guest" network.

If all of this is driving you as crazy as it is me please don't let it!! If we cannot knock this one I'd understand and very much appreciate your help...amazing! Thank you.

Ron

PS--BTW, it will not let me change it in the CP for these forums for some reason but in case you haven't caught on (/s) I am NOT running Gutsy...I am running 12.04LTS!

---

### Post by Hadaka on 2013-06-20
ok.fun !
let's try this..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
then post this..
```
dmsg | tail -n 20
```
thanks.

---

### Post by rondamato on 2013-06-20
OK, I purged bcmwl-kernel-source and then reinstalled it. At no time did I lose the wifi connection. It is still sitting up there^ with 4 "bars" of signal strength.

I then issued the ```
dmsg|grep wl
``` command. It appears as though dmsg is not installed, which is weird. It's telling me that it's in "util-linux" yet when I try to install "util-linux" it tells me that I already have the newest version.

I then noticed...command was missing an 'e'. Continuing.

Here are the results:

[ 2977.497305] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 2995.859959] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[ 2995.859971] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[ 2995.859975] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[ 2995.859979] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[ 2995.859982] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[ 2995.859985] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[ 2995.859989] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[ 2995.859993] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[ 2995.859996] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[ 2995.860000] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[ 2995.860003] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[ 2995.860006] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[ 2995.860009] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[ 2995.860013] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[ 2995.860017] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[ 2995.860020] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[ 2995.860023] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[ 2995.860026] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[ 2995.860030] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0

Remember that I have not yet rebooted, and the wifi is connected. At no point did I lose the connection.

R

---

### Post by rondamato on 2013-06-20
OK...just tried rebooting the machine. Here are the results:

I entered the password to get into the machine and guess what?? OMFG, the icon is there! It's solid! The machine is returning pings!

Now for the tricky part. I actually shut the machine down, using ```
sudo shutdown now
```then attempted a cold reboot. Once I logged in the wifi icon was there, but only the "outline." What's very curious is that now, in the list of APs, the "Guest" AP is gone. I tried to connect to a hidden network, and the "Guest" AP was in the dropdown box already. I chose it and the wifi icon started scanning never to connect. I tried connecting to one of the "secure" APs--it asked me for my username and pw as it's supposed to, but never connected. Just keeps "scanning."

Just for kicks I tried the same two modprobe commands that get me onto "Guest" when I issue them...and the machine connected almost immediately.

Oh so close and yet so far...

Ron

---

### Post by Hadaka on 2013-06-20
ok, sorry about the "e"
the machine needs to not be connected to the wifi
just boot up..let it not connect..or time out
then do.
the same set of commands as before.
remove then install the driver
thanks.
```
dmesg | tail -n 20
```
with the "e" :D

---

### Post by rondamato on 2013-06-20
Hello again,

I disconnected (disabled) wireless networking and tried again. Remember that I had to plug in a piece of hot RJ to be able to dl the driver (as the output from dmesg will show you).

I removed the drivers (actually purged them) and reinstalled them. I then tried to turn wireless networking back on. Did not get anything besides the "scanning" as usual. Plugged the RJ back in to send this message.

Here is the result of the dmesg command:


 [   19.242503] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[   19.242504] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[   19.242505] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[   19.242507] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[   19.242508] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[   19.242509] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[   19.242511] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[   19.242512] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[   19.242513] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[   19.242515] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[  127.830446] e1000e: eth0 NIC Link is Up 100 Mbps Half Duplex, Flow Control: Rx/Tx
[  127.830457] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  127.834234] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  250.439675] e1000e: eth0 NIC Link is Down
[  255.066730] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  321.753416] audit_printk_skb: 36 callbacks suppressed
[  321.753421] type=1400 audit(1371751642.947:24): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=893 comm="cupsd" pid=893 comm="cupsd" capability=36  capname="block_suspend"
[  337.866929] e1000e: eth0 NIC Link is Up 100 Mbps Half Duplex, Flow Control: Rx/Tx
[  337.866940] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  337.871248] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

I'm going to try and reboot but I doubt it will help...

Right now, the only change is that those two modprobe commands that used to make the wifi work no longer work. Bummer!

Thanks...I know this has gotten out of hand!

Ron

PS--Indeed, rebooting did not help. Wireless still "scanning" and APs are still showing up--just won't let me connect. Running those two modprobe commands will no longer connect me to "guest." I have been doing this a long time and have never ran into such an issue that was SO easy to solve on the surface, yet SO difficult to actually get working when it comes down to it. Hey, at least I'm learning, for what its worth! With these problems you don't really "learn" it until something like this happens...story of my life.

---

### Post by rondamato on 2013-06-21
Hey Hadaka...

Just though you should know this:

I booted the machine up and ran a ```
dmesg|grep wl
```. The results were interesting:

[11.740771] wl: module license mixed/proprietary taints kernel.
[11.781207] wl 0000:02:00.0: enabling device (0000 -> 0002)
[11.811902] INFO @wl_cfg80211_attach : Registered CFG80211 phy

Of course, it will still not connect to wireless (I have an "outline") although the APs DO show up and wireless is enabled.

Thought that bit about "taints kernel" might interest you.

Thanks for ALL of your help!!!

Ron

---

### Post by chili555 on 2013-06-21
Hadaka has left the building....but only temporarily. He has asked the doctor for a fee-splitting consultation. > Thought that bit about "taints kernel" might interest you.It doesn't affect us at all! Parts of the Broadcom STA driver are proprietary and parts are free and open source. The proprietary parts make the kernel no longer 100% completely pure as the driven snow free and open source; just 99.99%. It's a trivial disclaimer that has no effect on your ability to connect.

Please reboot so we have a clean slate with no connection at all. Before you do anything, do:```
dmesg > rond.txt
lsmod >> rond.txt
lspci -nn -d 14e4: >> rond.txt
iwconfig >> rond.txt
cat /etc/rc.local >> rond.txt
```Find the text file rond.txt in your user directory. Connect by whatever means and attach it to your reply using the paperclip tool at the top of the reply box.

Thanks.

---

### Post by rondamato on 2013-06-21
Hey Doc!

Good to see you.

Before I send this let me make the disclaimer that I DID reboot and run those commands first thing. However--before I rebooted (a few hours ago) I also disabled wireless to get rid of the boxes popping up telling me about the impossibility of a connection. So if you need me to either enable it before creating/appending that textfile or enable and connect using the modprobe commands before creating I can do either of those. Right now I am connected with a piece of RJ...and by the way, sorry for taking so long to reply! I'm out of here in an hour so if we don't get this solved today I'll be back in on Monday at 5:30am CST.

Without further adieu, here is the Very Long Textfile (attached--I think. This upload manager kind of sucks).

Thanks!!

Ron

PS--The upload manager will NOT let me upload the file...it's telling me the maximum filesize is 19.5k and this file is 145k...what to do? I can PM you the file...
PSS--No, actually I cannot PM it...or send it to you in any other way, it seems. I uploaded it to GDrive. It is at <https://docs.google.com/file/d/0B15bGf2Ud1KbeEZwbTBrNnE1SlU/edit?usp=sharing> and named "ubuntu textfile."

---

### Post by chili555 on 2013-06-21
> Before I send this let me make the disclaimer that I DID reboot and run those commands first thing. However--before I rebooted (a few hours ago) I also disabled wireless to get rid of the boxes popping up telling me about the impossibility of a connection. So if you need me to either enable it before creating/appending that textfile or enable and connect using the modprobe commands before creating I can do either of those.I thought my meaning was quite clear:> Please reboot so we have a clean slate with no connection at all. Before you do anything, do:I didn't mean by that, 'reboot a few hours ago, make a bunch of changes, hope it's OK and run the commands.' Your dmesg file has an ending timestamp of 11521.653087 implying that the machine was booted about 3 1/2 hours before the diagnostics were taken; not what I'd hoped for.

Before you go back and do the process as I requested, I see the following:> [11511.869446] ACPI: EC: input buffer is not empty, aborting transaction
[11511.869457] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20120320/evregion-501)
[11511.869475] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.ECDV.ECR1] (Node ffff880212892c58), AE_TIME (20120320/psparse-536)
[11511.869496] ACPI Error: Method parse/execution failed [\ECBT] (Node ffff880212892d70), AE_TIME (20120320/psparse-536)
[11511.869511] ACPI Error: Method parse/execution failed [\ECG2] (Node ffff880212892e88), AE_TIME (20120320/psparse-536)
[11511.869523] ACPI Error: Method parse/execution failed [\ECG6] (Node ffff880212892fa0), AE_TIME (20120320/psparse-536)
[11511.869537] ACPI Error: Method parse/execution failed [\_SB_.BAT0._BST] (Node ffff880212893780), AE_TIME (20120320/psparse-536)
[11511.869557] ACPI Exception: AE_TIME, Evaluating _BST (20120320/battery-455)There are many, perhaps dozens, of repeats of this error. I suggest you try to find out more about this and try to fix it. I'm not an expert in ACPI, so I have no ideas.> lib80211_crypt: registered algorithm 'TKIP'Is your router set to TKIP encryption? Many, perhaps most wireless drivers will refuse to connect at N speeds with TKIP. The preferred encryption method is AES.> cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule: [COLOR="#FF0000"]blank[/COLOR]In this context, a blank means default, one size may or may not fit all. I suggest we set the country code explicitly:```
sud iw reg set US
```Does this help you connect? If so, we'll amend one file and make it persistent.

Please run:```
nm-tool
```Does it report that your wireless access point uses WPA and WPA2 in mixed mode? WPA2 only is preferred. Is this a change you could try?

---

### Post by rondamato on 2013-06-22
Hello,

First of all, sorry about that! I rebooted and walked away I thought. I don't remember running any commands. I told you this quite clearly so very very sorry for any misunderstandings. YOU were clear also and I should have listened instead of rebooting and walking away.

But, just to make it all right, I rebooted fresh, connected to my home network using the modprobe commands, and made another "rond.txt" file.

This is in Google Drive as "Ubuntu Textfile #2" Link here: <https://docs.google.com/document/d/1kufBsH6G8mZZLP7vzkqtiFVki2UfcKP3QzikRDE1_7o/edit?usp=sharing>

I tried running the ```
sudo iw reg set US
``` and that went through with no errors.

Then for the nm-tool. Here is the output (long):

NetworkManager Tool

State: connected (global)

- Device: eth2  [linksys] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        1C:3E:84:C4:D8:D1

  Capabilities:
    Speed:           24 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    2WIRE461:        Infra, B0:E7:54:CA:9A:E1, Freq 2447 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    wml:             Infra, 5C:D9:98:68:B6:36, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    ATT8224:         Infra, 4C:60:DE:BA:5A:F0, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA2
    donteventry:     Infra, 20:10:7A:C3:4C:BE, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA2
    2WIRE357:        Infra, B0:E7:54:2B:A3:01, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    HOME-9FE8:       Infra, B8:9B:C9:69:9F:E8, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    linksys:         Infra, 00:0F:66:A9:B3:ED, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WEP
    *linksys:        Infra, 00:23:69:2A:ED:C7, Freq 2462 MHz, Rate 54 Mb/s, Strength 63 WEP

  IPv4 Settings:
    Address:         192.168.1.106
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             75.75.75.75
    DNS:             75.75.76.76


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        B8:CA:3A:CF:D0:78

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



As I said, I am connected at home right now by firing off the two modprobe commands. I can then pick my home AP (WEP), enter the key, and it connects. I will reboot, then edit this post to tell you if it successfully connects without the modprobes.

Thanks!!!

Ron


PS--I shut the machine down and rebooted...and it connected! No modprobes, no nothing. It just worked. Not sure how or why...but it worked! Thank you.

I will not know for SURE if this works with our un-protected "guest" network at Headquarters until I get back to work so I'm going to hold off on marking this solved until Monday morning (if you think I should)--but is it correct to assume that, if it connects upon reboot here and NOT at work that the issue is with the AP? I mean, other machines connect to it with no issue including my two desktop Ubuntu machines (10.04 and 12.04)--which are both Dell 5430s. But for now, Doctor, I think this problem is knocked. I don't know HOW exactly (and I'd really like to know if you do) but it is.

Hadaka, thank YOU also for all your hard work and advice. You taught me a LOT of good stuff and that's very important to me. Thank you again so very much.

---

### Post by chili555 on 2013-06-22
> I will not know for SURE if this works with our un-protected "guest" network at Headquarters until I get back to work so I'm going to hold off on marking this solved until Monday morningWe look forward to your report. My belief is that it's not solved until you are happy, so we'll read your report on Monday.

---

### Post by rondamato on 2013-06-24
Hello friends,

Well, I'm back at work...and the news is not good.

At home, I run a cheap Linksys router with WEP enabled. The computer found the WAP, allowed me to enter the key, and let me reboot-restart it many times...all the while it connected (automatically, I may add) right to the AP. No issues.

Back at work today...the machine cannot connect to the unprotected "guest" AP. It just keeps "scanning." It cannot connect to either of the other two WPA-2 protected APs either. It will ask me for creds but then just scans...and eventually times out.

This is really confounding me. EVERY computer on my desk is connected to the Guest AP--many computers here at the headquarters use it. As I typed this I just connected to it first-time (as in...I never connected to it before with this device) with my ASUS Transformer II. It connected instantly.

Well...at least we know that this thing effortlessly connects to the protected network in my home...and will NOT connect to the unprotected network here unless the modprobe commands that I've mentioned a few dozen times before are entered into a terminal.

I've been hacking on Ubuntu for about 5-6 years and Windows for FAR longer and have NEVER seen anything like this. To be honest--I am fresh out of ideas here. Even the computer that I am typing this on is connected to "Guest" (a Dell Lat E5430) but it's running Windows. More telling, my Ubuntu 12.04 desktop running Xubuntu can connect to it as well without issues...it's also a Dell, just not the same model as the "problem" machine.

I'm ready to just let this one go as it seems completely non-sensible as to why these VERY strange symptoms would occur. I am now THOROUGHLY confused with this.

To summarize:

1) Machine will NOT connect to unprotected "Guest" AP unless I use the "modprobe" commands.
2) Machine will not connect to any other AP in this building protected or not. Even if I turn on ICS on a Mac or something it won't connect to THAT either (without the modprobe commands).
3) Machine connects to WEP-protected network at home with no issues whatsoever. No modprobe commands need be used. It worked EXACTLY the way it should from the get-go.

That's all I have. Again, I thank the Community LOADS for helping me to troubleshoot and solve this incident!

Ron

---

### Post by chili555 on 2013-06-24
The modprobe -r b43 ssb etal shouldn't have any real effect because those modules are blacklisted and not loaded on boot; unless, of course, your ethernet device is also a Broadcom, some of which use b44 *and* ssb. When you cold boot and then check the loaded modules, are those loaded?```
lsmod | grep -e b43 -e ssb -e brcmsmac -e wl
```I suspect only wl is loaded, the driver created by bcmwl-kernel-source. Therefor, I'd assume the modprobe commands could simply be:```
sudo modprobe -r wl
sudo modprobe wl
```Does that work?

Perhaps there is a later version of bcmwl-kernel-source that would work better. Which version do you have?```
dpkg -s bcmwl-kernel-source | grep Version
uname -r
```

---

### Post by rondamato on 2013-06-24
Hey Chili,

OK, now doing exactly what you told me. I am on the affected laptop using eth0 for the network connection, but wireless IS enabled...just not working.

OK--tried the first command and got:

wl                   3074942  0 
cfg80211              208382  1 wl
lib80211               14382  2 lib80211_crypt_tkip,wl


I pulled the RJ temporarily and yes, simply entering:

```
sudo modprobe -r wl
```
```
sudo modprobe wl
```

does indeed bring up the wifi, and allow the machine to connect to "guest" almost instantaneously. Of course, when I reboot I lose connectivity and must enter these commands again.

Version shows up as being "6.20.155.1+bdcom-0ubuntu0.0.1." Kernel version is 3.5.0-23-generic.

Now that we know that those commands will get the wireless running is there any way to make them persistent? Any way, that is, other than putting the commands into the Linux version of "autoexec.bat" (which I'm guessing is init.d here in Ubuntu)? 

I'm nearly 100% sure that I understand what you are doing here...does the 
```
sudo modprobe -r wl
```
remove the wl driver from resident memory (or something like that) and the

```
sudo modprobe wl
```
put it back in?

Thanks again for all your help. Not only are we solving the issue--I am learning a LOT which, to me, is FAR more important than getting this machine's wireless to actually "work" correctly.

What steps can I take from here to make those commands persistent and allow the wireless to work each and every time the machine is cold-booted?

Thanks again friend!

Ron

---

### Post by chili555 on 2013-06-24
> Version shows up as being "6.20.155.1+bdcom-0ubuntu0.0.1." Kernel version is 3.5.0-23-generic.Ohhh? Here it says the version for your kernel is altogether different: [http://packages.ubuntu.com/quantal/bcmwl-kernel-source](http://packages.ubuntu.com/quantal/bcmwl-kernel-source)> bcmwl-kernel-source (5.100.82.112+bdcom-0ubuntu3)Where or how did you get 6.20.155? 

I'd prefer to get the correct version running correctly, if we can, rather than any other trickery.> I'm nearly 100% sure that I understand what you are doing here...does the
Code:

sudo modprobe -r wl

remove the wl driver from resident memory (or something like that) and the

Code:

sudo modprobe wl

put it back in?It removes it from loaded modules and reloads it.

---

### Post by rondamato on 2013-06-24
Hmm, very interesting!

I didn't do anything "special" to get that version...just got it through apt-get as I was told by Dell to do. They say that driver is the correct one for this computer. I'm not sure of how to "downgrade" drivers exactly--especially since this was not a specially downloaded driver--I got it straight from the Ubuntu repositories.

Just to ask:

[COLOR=#000000]*I did NOT make it persistent and here's why: I note that I can only run the command as sudo. If I put "sudo [anything]" in rc.local how does the machine operate on that? I mean, doesn't a password have to be entered once the machine hits the "sudo" command in rc.local?*[/COLOR]

[COLOR=#000000]*Also, it says in the file that the rc.local is disabled and to "change the execution bits" to enable it. I assume that this means to set user, group and world to "execute" using chmod? Right now I did an "ls -la" on the file and it appears to be set already to 755. So, although there is nothing in the file, it is ALREADY executing, correct?*[/COLOR]

[COLOR=#000000][I]This is actually a question that I've had all along--if I have a "sudo" in a script and a user with less-than-admin privs goes to run it how does Linux handle that? Does it prompt for a PW? Does it depend on how the said file is chmod'ed?

Thanks!

Ron[/I][/COLOR]

---

### Post by chili555 on 2013-06-24
> This is actually a question that I've had all along--if I have a "sudo" in a script and a user with less-than-admin privs goes to run it how does Linux handle that? Does it prompt for a PW? Does it depend on how the said file is chmod'ed?I'm not an expert on scripts, but I doubt it is advisable to include sudo in them. I believe the idea is to require sudo to run the entire script instead of its component parts. ```
sudo some_script
```> I did NOT make it persistent and here's why: I note that I can only run the command as sudo. If I put "sudo [anything]" in rc.local how does the machine operate on that? I mean, doesn't a password have to be entered once the machine hits the "sudo" command in rc.local?/etc/rc.local is run in its entirety by the system with full (~sudo) priveleges. Therefor, you can put the commands in without sudo; for example:```
<snip>
# By default this script does nothing.

modprobe -r wl
sleep 3
modprobe wl
iw reg set US

exit 0
```> it appears to be set already to 755. So, although there is nothing in the file, it is ALREADY executing, correct?Correct, although until you add something it is only executing 'exit 0'. I suppose one could, for reasons unknown to me, disable rc.local by chmodding to 600 so it was readable and writable by root only but not executable.

Just for the fun of it, let's try rc.local and let me know the result. Off to lunch.

---

### Post by rondamato on 2013-06-24
Thank you for such a detailed and great post! I learned a lot of things that I had always wondered about. So basically everything in /etc/rc.local is run with root privileges, correct? So all I need to do is basically apply a chmod 755 to the file and it will run, as root, and run the commands as "sudo" automatically. So, basically, this file IS exactly what I was referring to--the Linux equivalent to an "autoexec.bat" file, right? Any commands/calls that I have in this file will run at startup. That is, if I am right about that.

Another question: do you think that I should simply do pretty much exactly what you just did there and add nearly the same snip of code to my rc.local? By the looks of it that will basically run the commands that I've been running "by hand" to get the wifi to work.

It may not be the "right" way to do it, precisely, but the cool thing is that it looks to me like that would work. What's your opinion on this? A better question would be: are there any disadvantages to doing things like this that way? I mean, I can't think of any off the top of my head. The only thing that I wonder is when, exactly, is the rc.local run? Will the correct system resources already be up and loaded? What I'm getting at: if I put the *modprobe* commands in the rc.local will the hardware be ready to accept them? Is there a "rule" on this? Is the rc.local run near last when the system is starting up? I ask because, since its a file, it won't show up in a *ps*.  If/when it runs it should show up in boot.log or some other log, correct?

It really, at this point, doesn't matter to me how or why this isn't working. What we DO know is that those *modprobe* commands get it to fire up. And the person that is to be using this machine will never, ever open a terminal I'm guessing.

Thanks for the help on this one Chilii! If you give the green light I will just go ahead and get these commands into the rc.local...and be done with this issue.

Ron

---

### Post by rondamato on 2013-06-24
Just to let you know, I added this to the rc.local (before the *exit 0*)

```
sudo modprobe -r wl
sleep 3
sudo modproe wl
iw reg set US
```

It did not work. Rather, the locale setting worked, the network settings did not.

I surmise the reason is this: when I cold-boot the computer, it takes about 30 sec to 1 minute for "Guest" to show up in the list of available wireless networks. For some reason the first two (the protected ones) show up nearly instantly, but "Guest" takes longer.

If I wait about 45 seconds to be safe and run:

```
sudo modprobe -r wl
sudo modprobe wl
```

it works; the machine connects to "Guest" right away.

So it was a good idea...but it didn't do the trick. Hey, at least I am now SURE of how the rc.local file works, and I have you to thank for that!

---

### Post by Hadaka on 2013-06-24
Hi, change the rc file to..
```
sleep 60
```
this will give it a full minute to execute
the reloading of the wl driver...so by that
time...your guest wap will be available.
then do..
```
sudo gedit /etc/modules
```
remove wl
save and close gedit.
this will prevent /etc/modules and rc.local from
fighting over who gets to load the wl dirver.

---

### Post by rondamato on 2013-06-24
Hello!

OK, went into */etc/modules *and commented out the "wl" line.

I then replaced the ```
sleep 3
``` line with ```
sleep 60
```. I even tried a short *sleep* before all of the *modprobes*.

For some reason, it still will not work. When I type the password and the desktop comes up, the wifi icon is "outlined" and the pop-up says "Disconnected-You are now offline."

In the meantime (before the 60 seconds is up) I looked in the drop-down for the wireless icon. There are no APs listed there. The APs do not show up until the *sleep* is commenced...and by that time it's too late. It runs the *modprobes* but, since "Guest" just popped into the list, it does not connect to it.

After 60 seconds the icon starts "scanning" and the list of APs populates...however, the machine does not connect to "Guest"--even if I pick it from the drop-down.

Since this did not work I went and un-commented the "wl" line from */etc/modules *and then re-commented every line in */etc/rc.local *except for the ```
[COLOR=#000000][FONT=Ubuntu Mono]iw reg set US[/FONT][/COLOR]
``` line.

Rebooted and am back to where I was. I, of course, can still simply wait until the drop-down populates and then issue the *modprobe* commands to get the wifi connected.

It seems that, if there were a way to run those lines AFTER the desktop were loaded we'd be good.

Anyhow, thank you again!

R

---

### Post by chili555 on 2013-06-24
> ```
sudo modprobe -r wl
sleep 3
sudo modproe wl
iw reg set US
```

It did not work. Rather, the locale setting worked, the network settings did not.Doctor! After all we discussed!!

Please try, instead:```
modprobe -r wl
sleep 3
modpro[COLOR="#FF0000"]b[/COLOR]e wl
iw reg set US
```I still want to address the version you have; in particular:> just got it through apt-get as I was told by Dell to do.How or where did *Dell* tell you to do this? 

I wonder if this is perhaps actually a Network Manager issue. Obviously, when you unload wl, NM can't connect and then can't start trying again until it's reloaded.> So all I need to do is basically apply a chmod 755 to the file and it will run, as root, and run the commands as "sudo" automatically.I think it is such already. You needn't chmod at all; you simply need to add some things to run to get it to work.> It may not be the "right" way to do it, precisely, but the cool thing is that it looks to me like that would workPerhaps it would work; however, there seems to be another underlying problem. In most cases wl connects like a champ with no human intervention. We need to correct that deficiency.

When you right-click the NM icon and select 'Edit Connections' is it set to automatically connect to anything? To Guest? To something else?? Please see attached.

---

### Post by rondamato on 2013-06-24
Hello,

I am not at work now but let me clarify some things:
  
First of all, the sleep was set to THIRTY, not three. Also I DID type "modprobe." My trusty IBM Model M keyboard has been skipping certain letters and spaces...think that I may be overloading the buffer...but that's another matter. ALSO...when I added those lines I did not prefix the modprobe commands with "sudo"--that was just me blasting out a post without thinking of what I was writing. I am aware that sudo is not needed in the *rc.local* file. Well, at least NOW I am aware of that! ; ')

My company is HUGE and has all of its computers supplied by Dell. We have MANY "support specialists" dedicated solely to us. One of these specialists (who's title says that she is an 'Ubuntu Support Specialist') told me to use ONLY the Ubuntu Software Center or the apt-get utility (of course I went with apt-get since I HATE guis) to install the "bcmwl-kernel-source" package because they would "automatically blacklist the right drivers" (which, btw, she was wrong about--I blacklisted them myself). I simply ran ```
sudo apt-get bcmwl-kernel-source
``` and the machine installed the driver from the Ubuntu repos. I did NOT at any time install any other drivers. I guess that this is the very first laptop that Dell has actually certified for Ubuntu--and will allow you to order with 12.04LTS pre-installed, although this machine had Win7 installed on it. I simply re-partitioned the drive and put Ubuntu on it from a bootable USB stick.

Sorry about that--I will be more dilligent about proofreading my posts in the future!

Anyhow, I put it back to the way that it was; I fired up vim and commented out the lines that I added in the */etc/rc.local* file and also uncommented the "*wl"* driver in */etc/modules*...so I am back to where I started. The ```
modprobe -r wl
``` followed by the ```
modprobe wl
``` gets the wireless up and running with absolutely no issues.

I even tried to create a very simple shell-script called "wifi" which could be run from the user's homedir...but that didn't work. I got an error telling me, in essence, that the script could not unload (-r) the wl driver. I suppose that this was due to a permissions violation. I have not done any shellscripting in many years and could not remember if I could put *sudo*s in there.

Anyhow, glad to clarify all of that. When I am back at work tomorrow morning with the computer in question I will try what you told me to try and see where we are left, OK?

Thank you guys very much, as usual!

Ron

---

### Post by chili555 on 2013-06-25
> My company is HUGE and has all of its computers supplied by Dell. We have MANY "support specialists" dedicated solely to us. Very interesting. I had not been aware of such a thing previously. I certainly thought a hardware vendor would station support specialists at a major customer, but since Ubuntu is such a niche, I am enlightened to find that a Dell *Ubuntu* specialist would be provided! Are there many Ubuntu computers there?> One of these specialists (who's title says that she is an 'Ubuntu Support Specialist') told me to use ONLY the Ubuntu Software Center or the apt-get utility Very good advice. As an experiment, I will load up a live CD and install linux-image-3.5.0-23-generic and bcmwl-kernel-source and see what I get. I'm not saying it's incorrect; I'm saying it's puzzling.

Going back to the thought that i may actually be a Network Manager issue, instead of unloading and reloading wl, please reboot and then try:```
sudo service network-manager stop
sudo service network-manager start
```Does it connect? If this lappy is staying at work, you may consider removing NM altogether and coding the connection details into /etc/network/interfaces.

Are there any clues as to what's wrong here, run immediately after boot?```
cat /var/log/syslog | grep -e wl -e etwork -e eth1 | tail -n25
```After you do connect, let's see:```
nm-tool
```

---

