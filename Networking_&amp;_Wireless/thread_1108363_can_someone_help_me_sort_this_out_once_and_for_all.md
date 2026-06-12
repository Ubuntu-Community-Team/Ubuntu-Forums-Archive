---
title: "can someone help me sort this out once and for all???"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by scrypt on 2009-03-27
Can somebody Help me sort this issue out.
I have been plugging away at it for days with no joy.

I want to patch my intel pro/wireless 3945abg wireless card's driver to this driver:

type wget [http://dl.aircrack-ng.org/drivers/ipwraw-ng-2.3.4-04022008.tar.bz2](http://dl.aircrack-ng.org/drivers/ipwraw-ng-2.3.4-04022008.tar.bz2)

I have extracted and installed it, but i cannot seem to blaclist the original default driver correctly.

my ubuntu seems to reset itself back to the original driver and setup.

Can somebody please give me a hand?

Im still relatively new to ubuntu so lease be gentle??


thnak's

---

### Post by chili555 on 2009-03-27
Open a terminal and do:```
cat /etc/modprobe.d/blacklist
```Please post the result here.

---

### Post by scrypt on 2009-03-27
Chili thanks for replying i will try the command

---

### Post by scrypt on 2009-03-27
Chili I got this output:


mark@ubuntu:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp
mark@ubuntu:~$

---

### Post by scrypt on 2009-03-27
These are the commands i have been given originally but im not sue if they are a;; correct:

Can you see where im going wrong:

sudo apt-get install build-essential (get core files)

sudo apt-get install libssl-dev (get supporting library)

wget [http://dl.aircrack-ng.org/drivers/ip...022008.tar.bz2](http://dl.aircrack-ng.org/drivers/ip...022008.tar.bz2) (downloads driver)

tar -xjf ipwraw-ng* (extract the archive file)

cd ipwraw-ng (go to the extracted folder)

make (compile the source files into a binary)

sudo make install (install the driver)

sudo make install_ucode

echo "blacklist ipwraw" | sudo tee /etc/modprobe.d/ipwraw (blacklist the default ipwraw)

sudo depmod -ae (create a dependency file for the modules)

sudo modprobe -r iwl3945 (unload driver that you do not need)

sudo modprobe ipwraw (load the driver that you installed)

sudo ifconfig wlan0 up (enable the network adapter)

When you're done, open a terminal and type lsmod, you should see the ipwraw driver loaded.

---

### Post by chili555 on 2009-03-27
> echo "blacklist ipwraw" | sudo tee /etc/modprobe.d/ipwrawPlease also let me see:```
cat /etc/modprobe.d/ipwraw
```Also, do:```
sudo gedit /etc/modprobe.d/blacklist
```Add a new line:```
blacklist iwl3945
```Check your work, save and close gedit. Reboot. Does your system work correctly now?

---

### Post by scrypt on 2009-03-27
Thanks chili555

sr to ask but where should i add the line


blacklist iwl3945

---

### Post by scrypt on 2009-03-27
Do those list of commands look okay to you?

I want to allow packet injection for my Intel pro/wirless3945abg??

---

### Post by scrypt on 2009-03-27
I mean where should i add the line the text editor that opened,

Is there anywhere specific??

---

### Post by scrypt on 2009-03-27
This is the driver I want to remove using this command:  sudo modprobe -r iwl3945

and this is the New driver driver i want to load: sudo modprobe ipwraw

I am not entirely familiar with editing uesing a text editor.

---

### Post by chili555 on 2009-03-27
> **scrypt said:**
> I mean where should i add the line the text editor that opened,

Is there anywhere specific??Here is the last little bit of your file:> # most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcspJust add the new line so it looks like this:> # most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

#chili says add it here:
blacklist iwl3945
The wording behind # are comments that are ignored by the system, but just remind us why the entry is here.

---

### Post by chili555 on 2009-03-27
> **scrypt said:**
> Do those list of commands look okay to you?

I want to allow packet injection for my Intel pro/wirless3945abg??The one I quoted in post #6 above looks wacky to me. That's why I asked to see the file.

---

### Post by scrypt on 2009-03-27
I added #blacklist iwl3945

To the first line

saved and rebooted

---

### Post by chili555 on 2009-03-27
> **scrypt said:**
> I added #blacklist iwl3945

To the first line

saved and rebootedAnd when you do:```
lsmod | grep iwl
```is *iwl3945* there or no? And when you do:```
lsmod | grep ipwraw
```Is it loaded?

What does:```
cat /etc/modprobe.d/ipwraw
```Say to us?

---

### Post by scrypt on 2009-03-27
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

#blacklist iwl3945

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

---

### Post by scrypt on 2009-03-27
mark@ubuntu:~$ lsmod | grep iwl
iwl3945                99316  0 
rfkill                 17048  2 iwl3945
mac80211              216820  1 iwl3945
led_class              12164  1 iwl3945
cfg80211               32392  2 iwl3945,mac80211

---

### Post by scrypt on 2009-03-27
mark@ubuntu:~$ lsmod | grep iwl
iwl3945                99316  0 
rfkill                 17048  2 iwl3945
mac80211              216820  1 iwl3945
led_class              12164  1 iwl3945
cfg80211               32392  2 iwl3945,mac80211
mark@ubuntu:~$ sudo cat /etc/modprobe.d/ipwraw
blacklist ipwraw

---

### Post by scrypt on 2009-03-27
Here is what it looks like since i added:

#blacklist iwl3945

Right at the bottom (Without the (Chili said add it here) Ha
# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

#blacklist iwl3945

---

### Post by scrypt on 2009-03-27
Oh and i removed it from the top aswell where i added it incorrectly...

---

### Post by scrypt on 2009-03-27
Here is the lsmod | grep iwl output since i added :


#blacklist iwl3945

mark@ubuntu:~$ lsmod | grep iwl
iwl3945                99316  0 
rfkill                 17048  2 iwl3945
mac80211              216820  1 iwl3945
led_class              12164  1 iwl3945
cfg80211               32392  2 iwl3945,mac80211

What do you say??

---

### Post by scrypt on 2009-03-27
Yes it loaded, cool

But aren't the old drivere still loading or am i mistaken??

mark@ubuntu:~$ lsmod | grep iwl
iwl3945                99316  0 
rfkill                 17048  2 iwl3945
mac80211              216820  1 iwl3945
led_class              12164  1 iwl3945
cfg80211               32392  2 iwl3945,mac80211
mark@ubuntu:~$ sudo cat /etc/modprobe.d/ipwraw
[sudo] password for mark: 
blacklist ipwraw

---

### Post by scrypt on 2009-03-27
Thank chili

How can i make sure i connect to my LAN ethernet cable, so that I can kep my Wireless card for packet injection?

Do you know??

---

### Post by scrypt on 2009-03-27
No worries about the last post i just changed what connects automatically in the Network Tools... :)

---

### Post by scrypt on 2009-03-27
sorry I just removed the # from the edit then resved it...

---

### Post by scrypt on 2009-03-27
why is this driver blacklisted. ths is the driver i need to be using isnt it??

mark@ubuntu:~$ cat /etc/modprobe.d/ipwraw
blacklist ipwraw

---

### Post by chili555 on 2009-03-27
> **scrypt said:**
> why is this driver blacklisted. ths is the driver i need to be using isnt it??

mark@ubuntu:~$ cat /etc/modprobe.d/ipwraw
blacklist ipwrawYes, it is! I have no idea why the instructions would ask you to build a nice shiny new module, *ipwraw* and then do something that appears to blacklist it. I suggest commenting it out temporarily so that your */etc/modprobe.d/ipwraw* file looks like this:```
#blacklist ipwraw
```Also, please edit your */etc/modules* file to add a new line at the bottom, unless it's already there:```
ipwraw
```Proofread, save and close. Now, after a reboot, do:```
lsmod | grep iwl
```I hope you do ***not*** see *iwl3945.* Then do:```
lsmod | grep ipw
```I hope you ***do*** see ipwraw.

---

### Post by scrypt on 2009-03-28
Hi ya Chili.

I completely understand if you need a good break after trying to help me out last night, Ha ah..

I managed to put it in Monitor Mode.

Here is my iwconfid output Now:

mark@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     unassociated  ESSID:off/any  
          Mode:Monitor  
          
rtap0     no wireless extensions.

pan0      no wireless extensions.

BUT It should look this: (From iwconfig command):

lo no wireless extensions.

eth0 no wireless extensions.

wmaster0 no wireless extensions.

wlan0 IEEE 802.11abg ESSID:"ROUTER"
Mode:Managed Frequency:2.437 GHz Access Point: 00:1E:74:6C:22:96
Bit Rate=54 Mb/s Tx-Power=15 dBm
Retry min limit:7 RTS thrff Fragment thr=2352 B
Encryption key:2387-BFEE-4C96-8850-5522-9F08-8314-43B8-3BD9-D7A9-1E56-0F13-0ACF-1D8B-4869-2D6C [2] Security modepen
Power Managementff
Link Quality=98/100 Signal level:-26 dBm Noise level=-62 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0


rtap0     no wireless extensions.

pan0      no wireless extensions.

I also cannot put my wireless card back into Managed Mode to span0 no wireless extensions.

BUT I am getting this output:

mark@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     unassociated  ESSID:off/any  
          Mode:Monitor  
          
urf the net?

Can you suggest what I can do to fix this please?

Thank-you in advance

---

### Post by scrypt on 2009-03-28
Im not sure, but i think it is becuse I cannot enable my wireless card?

Is this correct?

How do i enable it?

---

