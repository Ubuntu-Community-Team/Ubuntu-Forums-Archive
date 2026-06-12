---
title: "Dell Latitude E6230 Wireless Issues..."
date: 2013-06-07
forum: Networking &amp; Wireless
---

### Post by rondamato on 2013-06-07
Hello friends,

I just had to perform a "pilot" install of 12.04.2 LTS on one of our company's new Dell E6230 sub-notebooks. Now remember, these are the ones that you can get Ubuntu pre-installed on also! I suppose that saving a few dollars came into play there because it came with Win7. Remember also that this thing has the funky new UEFI BS going on--so it was a bitch to get it to boot after installing Ubuntu from a USB stick--kept getting "Invalid Partition Error" at boot until I played around for a bit with the UEFI settings. I DID manage to get it to boot.

My problem is getting the WiFi to work consistently. An "lspci" shows this thing to have a Broadcom BCM 43228 (14e4:4359).

I followed this really good guide over at <[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Switching_between_drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Switching_between_drivers)> and actually got the WiFi to connect to the guest network--but as these instructions are for 11.10 I don't think they cover me.

Anyhow, it was connected so I installed some updates and then rebooted. After the reboot it would no longer connect--which the directions I referenced SAID it "wouldn't" do unless I typed some commands. Guess what? Of course, it STILL lost connection at reboot.

If I issue the command "sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma" and follow that with "sudo modprobe wl" it connects again...but I have to wait. If I reboot and try to issue the first modprobe command right away I get an error...don't have it handy but it was like "FATAL: Error removing wl" then listed something in the /lib directory.

After I typed this for about 10 minutes I tried both modprobe commands again and there were NO errors--in fact it's sitting right next to me connected to our guest network!!

Anybody have any idea what's going on here??

I wouldn't mind entering both modprobe commands every time I logged in to bring up the wifi but the executive this laptop is going to just ain't gonna go for it! ; ') I know that I can probably put them in a script and then put a sleep in the script to run them after X minutes but that's just SO inelegant...there has to be a way to do this.

Can anybody help me or tell me what I'm doing wrong here? It sure would be appreciated! Had all week to build this thing but HAD to wait to the deadline due to an enterprise-wide Ubuntu VDI issue (which, of course, Ubuntu is not at fault in).

Thanks so much and Happy Friday everyone!

Ron

---

### Post by Hadaka on 2013-06-07
Hi, this will insert the wl module on boot for you.
open a terminal ctrl/alt/t and then copy and paste in these commands
```
sudo su 
echo 'wl' >> /etc/modules
exit

```
thanks.

---

### Post by rondamato on 2013-06-07
Hello!

Oh so VERY close!!

I now get the "outline" of the wireless signal indicator up on the right and my wifi led is on, but no connection. 

I tried "connecting to hidden network" and "Guest" was right there, however it just cycles and does not connect.

After it sat trying to connect for a while (like 3 minutes) I saw all of the rest of the wifi networks slowly add themselves to the list--including "Guest" which was previously hidden.

I tried to select Guest and it just kept cycling, followed by a black box saying "Wireless Network--You are now offline!" (or something like that). I then tried the WPA WAP (entered my user id and password) and it cycled more and more...then the box asking for my username and pw for the "protected" WAP popped up again--with my username and PW fields already filled out.

You are right about this...it seems to "like" the wl driver. When I run those two commands all is peachy.

Hey, thanks for trying! If there is any further info or screenshots that would help let me know, OK?

Thanks!!

Ron

---

### Post by Hadaka on 2013-06-07
Hi, lets take a look at what you may have done
trying to get this to work.
please post the output of..
```
lsmod
rfkill list
lspci -nnk | grep -iA3 net
```
thanks

---

### Post by rondamato on 2013-06-07
Thank you!! OK, I just got a long enough piece of RJ to reach from my switch...here goes:

raju@raju-Latitude-E6230:~$ lsmod
Module                  Size  Used by
rfcomm                 47562  0 
bnep                   18240  2 
bluetooth             211812  10 rfcomm,bnep
nls_iso8859_1          12714  1 
snd_hda_codec_hdmi     32476  1 
snd_hda_codec_idt      70774  1 
joydev                 17694  0 
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
snd_hda_intel          34063  3 
snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
parport_pc             32867  0 
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
wmi                    19257  1 dell_wmi
lib80211_crypt_tkip    17391  0 
mac_hid                13254  0 
microcode              23030  0 
i915                  535128  3 
drm_kms_helper         49259  1 i915
drm                   290344  4 i915,drm_kms_helper
snd_timer              29990  2 snd_pcm,snd_seq
i2c_algo_bit           13565  1 i915
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
video                  19653  1 i915
snd                    83674  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wl                   3074942  0 
psmouse               102506  0 
serio_raw              13216  0 
lpc_ich                17145  0 
cfg80211              208382  1 wl
soundcore              15092  1 snd
lib80211               14382  2 lib80211_crypt_tkip,wl
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
mei                    41410  0 
lp                     17800  0 
parport                46563  3 ppdev,parport_pc,lp
ahci                   25869  3 
libahci                27338  1 ahci
sdhci_pci              18749  0 
sdhci                  33145  1 sdhci_pci
e1000e                198734  0 


raju@raju-Latitude-E6230:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


raju@raju-Latitude-E6230:~$ lspci -nnk | grep -iA3 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Dell Device [1028:0532]
    Kernel driver in use: e1000e
    Kernel modules: e1000e
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
    Subsystem: Dell Device [1028:0014]
    Kernel driver in use: wl
    Kernel modules: wl


BTW, as I was posting this thread the "box" saying "Wireless Network--Disconnected" kept popping up in the right corner; figure about every minute or so.

Also, since I am a TOTAL n00b posting to the forums, how do you format text to show up as "code" (as you did in your message to me)?

Thanks for all of the help friend--MUCH appreciated. I also appreciate learning the "lsmod" command--never knew that one! I am pretty new to Ubuntu (four years) so I learn new stuff every day which I LOVE!

Ron


PS--Also, ONLY IF you have time, can you tell me what it is you are looking for with these commands' outputs? I'm MUCH more interested in figuring out the "whys" of this problem than getting the wifi to work, you know?  ; ')  I understand that the text (dell_wmi) is the module name but what do the numbers denote--both the long and short ones? Thanks so much again!!

---

### Post by Hadaka on 2013-06-07
Hi, I didnt see any thing weird..which is good.
so Let's cover a few things you asked about..
but first...this.. removes as in -r all those modules...6 of them
including the one you want..so you do Not need to run that again...ever
```
sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma
```
This you found on your own..notice there are 2 sets of numbres for your card
43228 and 14e4:4359. The BCM43228 is nothing more than the number for the card
it has NOTHING to do with the required driver...this number 14e4:4359  called a PCI ID
IS the number to look up for the correct driver...it is ALWAYS that way with broadcom drivers.
```
Broadcom BCM 43228 (14e4:4359)
```
This module..dell_wmi, is a Windows Manager Interface..a.k.a WMI....Its use is for keyboard
functions like..Prnt Scrn,keyboard volume control,FN function key combinations and other normally
used keyboard functions when running windows...and of course you want those same functions in
Ubuntu.
```
wmi 19257 1 dell_wmi
```
Now on to the more current issue...all looks well..Im guessing you need to set your WIFI connections
correctly. soo..click the icon..next to the envelope..upper right corner..then click Edit Connections...then
click Wireless...then click YOUR ssid and then click Edit.  below set your IPv4 and Ipv6 exactly like you see
below..including the dns..8.8.8.8,8.8.4.4 then set your security for YOUR connection...choose WPA2 only not mixed
*If that is infact what you use..other wise..set it to what your system router requires...be sure to also make sure
that *CONNECT AUTOMATICALLY is checked...afer you do this...click save..  see attached examples..
[ATTACH=CONFIG]243612[/ATTACH][ATTACH=CONFIG]243613[/ATTACH]
and lastly..to use "code tags" click the "#" on the reply page..its in the center row on the top with the
rest of the icons..looks like this.. # <> jhdj. Click the # then copy and paste between the code tags. They look
like this [.CODE] *paste here* [./CODE]

---

### Post by rondamato on 2013-06-10
Hello again!

Thank you very much for your help!

I tried what you told me to do but am still having no luck.

Let me tell you what's happening--perhaps you can tell me if ehat I THINK is happening is indeed happening.

When I restart the computer the same thing happens--no wireless. We have a "Guest" network that requires no security--this is what I am trying to connect to.

The only way that I can connect is, when the machine is logged into, I issue these commands:

```
sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma
```

...and the wireless icon changes from a "scanning" icon to a solid "outline" of the icon.

To connect to the network though I must enter ```
sudo modprobe wl
```

After this the icon turns solid and the computer informs me that I am connected to "guest."

If I understand what you're saying the "modprobe -r" command removes all modules listed after it...and the "modprobe wl" reloads and then starts the ONLY the wl module.

When I look in the /etc/modules file the only modules that are shown are lp, rtc, and wl.

So...I have no trouble getting this to work as long as I issue the above commands--what I'm not understanding is WHY these commands are not persistent...ie, why do I HAVE to run them each and every time the computer is booted and what can I do to prevent this?

I followed your instructions (which taught me a lot BTW) but they didn't solve my problem--I guess what I need to know is why this module needs to be loaded by hand every time the computer is booted?

I appreciate all of your help and I'm sorry that I'm not "getting" this--trust me, it's frustrating especially since my deadline for this machine's completion is in about two hours!

Thanks again,

Ron

PS--Thanks for the help with the code tags--they work very well! ; ')

PSS--Thought it might help to know that I cannot enter ONE of those lines and get it to work. Thought just the "modprobe wl" would suffice but it does not--I must enter
```
sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma
```
first and then
```
sudo modprobe wl
```

After this the computer automatically connects to the "Guest" account in about 8-10 seconds.

---

### Post by Hadaka on 2013-06-10
Does the admin network log in ok?
please do..
```
sudo apt-get update
sudo apt-get upgrade
```
thanks.

---

### Post by chili555 on 2013-06-10
The doctor has been called in on a consultation. > -I must enter
Code:

sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma

That implies that those modules were loaded on boot. A proper installation of the STA driver wl should blacklist or prevent that. However, sometimes things don't go as perfectly as we wish. Let's fix it:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Add these lines at the end:```
blacklist b43
blacklist ssb
blacklist bcma
blacklist brcmsmac
```Proofread carefully, save and close gedit. Reboot and let us hear your report.

---

### Post by rondamato on 2013-06-10
Hello there!

Well, this issue is solved!

Dig this:

First,  I figured out that I had messed up the kernel. Not really knowing how  to fix it, I simply re-installed from USB. I had nothing to lose anyhow.

Then, I went to a terminal and ran this command:

```
sudo apt-get update && sudo apt-get upgrade
```

Waited a looong while for all of the updates to come down, then rebooted. When the machine went back to the BIOS screen I unplugged the network cable.

When it came back up, I logged in and it had already connected to my guest network! I tried the WPA2 network--also worked.

Sooo...I think this problem is solved.

Most importantly, thanks to all of you I learned how kernel modules work, how and when to blacklist, and a lot of other stuff. So thanks!!

For now, I am up and running. Thank you all! :KS

R

---

### Post by chili555 on 2013-06-10
Awesome! Glad it's working.

---

### Post by rondamato on 2013-06-11
Well, I THOUGHT I had this solved by doing an update/upgrade...but it turns out that I also had to add the mentioned modules to the blacklist.conf.

These were:

```

blacklist b43
blacklist ssb 
blacklist bcma 
blacklist brcmsmac

```

I am now up and running after several reboots. Thank you everyone!!

---

