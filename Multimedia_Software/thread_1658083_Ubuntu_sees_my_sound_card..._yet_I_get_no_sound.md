---
title: "Ubuntu sees my sound card... yet I get no sound?"
date: 2011-01-02
forum: Multimedia Software
---

### Post by spliffeh on 2011-01-02
Is anyone a wiz with fixing sound issues? Ubuntu sees my onboard sound card but I still get no sound. I've been going nuts for a few days trying to fix it.

**Note this pastebin containing a ton of info I captured: [http://pastebin.com/CnvAfTDU](http://pastebin.com/CnvAfTDU) ... any help would be appreciated... what steps should I take next to troubleshoot?  **

(PS the motherboard is fairly new, it's an [Asus M4A87TD EVO]("http://ca.asus.com/product.aspx?P_ID=YATvwCy0OZLGNWwp"))

---

### Post by spliffeh on 2011-01-02
I've solved this. To document what I've learned and save someone else a few headaches: 

If you install Ubuntu 10.04 (also I tried Fedora 14) on an **Asus M4A87TD EVO** motherboard the sound will come out of a different jack  then it does in Windows. Also the sound will come out at one tenth the volume that you normally get in Windows. These two factors combined makes it very easy to think you're not getting any sound at all - I didn't figure it out for a few days.

So... currently on an Asus M4A87TD EVO you can get 2 channel sound that is very weak... that will suffice for me as Win7 is my main o/s on this machine, but a warning to others thinking of buying this m/b for linux primarily: you will be crippled for any kind of serious htpc / media player / gaming type of usage. Not recommended.

---

### Post by BicyclerBoy on 2011-01-02
Your *buntu is a bit old now unless you have installed backports for kernel/alsa modules.
Remember that 10.04 kernel & alsa modules are >2 years old..

The audio volume is possibly a mixer control preset or a default hardware preset.
Did you run the mixer GUI & check all outputs for mute & levels ?

Some audio outputs can be line out or headphone out levels.

---

### Post by lidex on 2011-01-02
Well, alsa is using the generic parser for your codec chip. Your best bet is to update to the 
latest version to get proper recognition. Probably the easiest approach is updating your alsa-modules.

Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by zeb00 on 2011-02-01
thanks lindex
fixed no  audio issue on a GA-D525TUD.
i had to reboot after installing before mixer would load as i was getting an invalid argument error

---

