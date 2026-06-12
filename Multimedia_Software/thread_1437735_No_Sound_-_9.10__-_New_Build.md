---
title: "No Sound - 9.10  - New Build"
date: 2010-03-24
forum: Multimedia Software
---

### Post by SolitaryMan1941 on 2010-03-24
Hello, I am a brand newbie looking for some *basic* assistance. I have recently completed my first self build. I cannot get any sound. I have a Gigabyte MA785GM-US2H motherboard and intend to run sound through the on-board sound card Realtek ALC889A. Here is what I have done so far:

1. I have installed the codec provided by the Realtek website

[http://www.realtek.com.tw/downloads/...&GetDown=false]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false")


From the terminal:

cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC889A

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
j@j:~$ alsamixer



2. I have made sure nothing is muted (via the alsamixer).

3. I have made sure the on-board audio in enabled in BIOS

4. I have installed g streamer plug-ins

5. I have restarted the computer just to make sure everything installed correctly.


I am at a loss...any and all help is much appreciated.

---

### Post by RedSingularity on 2010-03-24
Post the output of 

lspci -v

---

### Post by SolitaryMan1941 on 2010-03-25
Here is the output with codec:

htpc@htpc:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC889A

htpc@htpc:~$ lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
    Subsystem: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
    Flags: bus master, 66MHz, medium devsel, latency 32
    Memory at <ignored> (64-bit, non-prefetchable)
    Capabilities: <access denied>

00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
    Flags: bus master, 66MHz, medium devsel, latency 99
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fde00000-fdffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fdd00000-fddfffff
    Prefetchable memory behind bridge: 00000000fda00000-00000000fdafffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (prog-if 01)
    Subsystem: Giga-byte Technology Device b002
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 22
    I/O ports at ff00 [size=8]
    I/O ports at fe00 [size=4]
    I/O ports at fd00 [size=8]
    I/O ports at fc00 [size=4]
    I/O ports at fb00 [size=16]
    Memory at fe02f000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
    Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
    Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at fe02c000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
    Memory at fe029000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
    Subsystem: Giga-byte Technology Device 4385
    Flags: 66MHz, medium devsel
    Capabilities: <access denied>
    Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
    Subsystem: Giga-byte Technology Device 5002
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at fa00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: Giga-byte Technology Device a002
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at fe024000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
    Subsystem: ATI Technologies Inc SB700/SB800 LPC host controller
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fdc00000-fdcfffff
    Prefetchable memory behind bridge: fdb00000-fdbfffff

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at fe028000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
    Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc Device 9710
    Subsystem: Giga-byte Technology Device d000
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at ee00 [size=256]
    Memory at fdfe0000 (32-bit, non-prefetchable) [size=64K]
    Memory at fde00000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

01:05.1 Audio device: ATI Technologies Inc Device 970f
    Subsystem: Giga-byte Technology Device 960f
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at fdffc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
    Subsystem: Giga-byte Technology Device e000
    Flags: bus master, fast devsel, latency 0, IRQ 26
    I/O ports at de00 [size=256]
    Memory at fdaff000 (64-bit, prefetchable) [size=4K]
    Memory at fdae0000 (64-bit, prefetchable) [size=64K]
    [virtual] Expansion ROM at fda00000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
    Subsystem: Giga-byte Technology Device 1000
    Flags: bus master, medium devsel, latency 32, IRQ 22
    Memory at fdcff000 (32-bit, non-prefetchable) [size=2K]
    Memory at fdcf8000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

---

### Post by RedSingularity on 2010-03-25
In a terminal type,

alsamixer

and make sure all the levels are up.  (Especially the master)

---

### Post by lidex on 2010-03-25
> **SolitaryMan1941 said:**
> Hello, I am a brand newbie looking for some *basic* assistance. I have recently completed my first self build. I cannot get any sound. I have a Gigabyte MA785GM-US2H motherboard and intend to run sound through the on-board sound card Realtek ALC889A. Here is what I have done so far:

1. I have installed the codec provided by the Realtek website



Not sure how that would help since I believe that's a windows driver (could find no documentation of linux support). Anyway, ubuntu uses alsa as the audio foundation and alsa uses it's own drivers, in your case snd-hda-intel. But before getting dirty with that make sure pulseaudio is properly configured (courtesy psyke83): [http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by lidex on 2010-03-25
Once that's done go here:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

Please remember to post text blocks using the code tags: the "#" in the toolbar.  Thankyou.

---

### Post by SolitaryMan1941 on 2010-03-25
Update:

1. I made sure all of the levels were maxed out and not muted in the alsamixer via:
```

alsamixer

```2. I also stored the settings via:
```

sudo alsactl store

```2. The codec provided on the Realtek website is Linux driver (2.6) Version 5.14rc5

3. I completed all of the tests from [https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats) and all diagnosis were good to go.

4. I made sure all of the pulseaudio software was up to date via the ubuntu software center.

5. I restarted the computer just in case.

Unfortunately, I still don't have any sound. Does that mean it's time to get down and dirty?

---

### Post by lidex on 2010-03-25
Cincinnati, eh? You're in my neighborhood.
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by SolitaryMan1941 on 2010-03-25
Yeah, Cincinnati. Not my hometown but it has some nice features that keep me around.

Here is the link

```

http://www.alsa-project.org/db/?f=a4ebbfb965a885f829737dee11891d8975d49483

```Thank you for the help btw.

---

### Post by lidex on 2010-03-25
> **SolitaryMan1941 said:**
> Yeah, Cincinnati. Not my hometown but it has some nice features that keep me around.

Here is the link

```

http://www.alsa-project.org/db/?f=a4ebbfb965a885f829737dee11891d8975d49483

```Thank you for the help btw.
Not a problem. An aside here: for urls use the icon with the globe and chain link. When you click it paste the link into the box that pops up.

OK. Click the alsa-upgrade link in my sig and follow the instructions there to update alsa to the latest version.

---

### Post by SolitaryMan1941 on 2010-03-25
I know this must sound ridiculous but I cannot figure out the second step of:

Short Alsa-Upgrade script install instructions:

1. download the script and save it somewhere
2. cd <your-download-dir>
3. tar xvf AlsaUpgrade-1.0.22.1-2.tar
4. sudo ./AlsaUpgrade-1.0.22.1-2.sh -d
5. sudo ./AlsaUpgrade-1.0.22.1-2.sh -c
6. sudo ./AlsaUpgrade-1.0.22.1-2.sh -i
7. sudo shutdown -r 0

Like I said I'm a brand newbie. This is my second computer and my first build. I assume this is something that needs to be entered into a terminal...

---

### Post by Yellow Pasque on 2010-03-25
If you're using Firefox, click on Tools -> Downloads. Then right click on the AlsaUpgrade file and select 'Open Containing Folder' from the menu. This will show you what directory downloaded files go to.

---

### Post by SolitaryMan1941 on 2010-03-25
Sorry, I wasn't clear. I know what directory the file is in. I don't know what it should look like when I enter it into the terminal. The directory name is "htpc".

---

### Post by Yellow Pasque on 2010-03-25
What directory is htpc in? That's why I wanted you to open it in a file browser where you could click 'up' button and see the PATH to the file.

---

### Post by SolitaryMan1941 on 2010-03-25
Figured out step two. Working on step three...

---

### Post by SolitaryMan1941 on 2010-03-25
'htpc' is my home directory. I typed in 

```

cd alsa-drive-1.22.1.0

```I think this gave me access to the correct folder.
Now I'm getting:

```

htpc@htpc:~$ cd alsa-driver-1.0.22
htpc@htpc:~/alsa-driver-1.0.22$ tar xvf AlsaUpgrade-1.0.22.1-2.tar
tar: AlsaUpgrade-1.0.22.1-2.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
htpc@htpc:~/alsa-driver-1.0.22$ 

```Baby steps...

---

### Post by Yellow Pasque on 2010-03-25
Your home directory is /home/htpc, so..
```
cd /home/htpc
```
Your home directory also has a shortcut to make life easier:
```
cd ~/
```

---

### Post by lidex on 2010-03-25
cd is the command to change your working directory and is used just once. Once you are in that directory, run the commands exactly as given on the script page. The terminal defaults to your user directory "/home/htpc" so if the file was downloaded there you don't have to "cd". To check if the file is actually there type in ```
ls
``` to list the directory contents.

BTW: I think home can be a little confusing as the actual home directory is "/home" and contains the user directories - in your case "/home/htpc". Mostly when someone refers to "your home directory" they mean the latter, which can be referenced as "~/ " as Temüjin points out.

---

### Post by SolitaryMan1941 on 2010-03-25
I think I understand the cd folder series process now.

The script (both zipped and extracted) is in home/htpc/installers.

Here is what I have so far...

```

htpc@htpc:~$ cd ~/installers
htpc@htpc:~/installers$ tar xvf AlsaUpgrade-1.0.22.1-2.tar
tar: AlsaUpgrade-1.0.22.1-2.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
htpc@htpc:~/installers$ 

```This makes me a bit confused because 'alsa-driver.1.0.22.tar.bz2' and 'alsa-driver-1.0.22' are in the directory 'installers'. There is nothing mentioned in the trouble shooting about this type of error. I have downloaded the script twice just to make sure there wasn't any error. Any suggestions? I am willing to move the script to another file just for install if it will make life easier.

---

### Post by lidex on 2010-03-26
snip

Check that directory in nautilus - that file must be some where else. try ~/Downloads

---

### Post by SolitaryMan1941 on 2010-03-26
I made a little progress...

Short Alsa-Upgrade script install instructions:

1. download the script and save it somewhere
2. cd <your-download-dir>
3. tar xvf AlsaUpgrade-1.0.22.1-2.tar
4. sudo ./AlsaUpgrade-1.0.22.1-2.sh -d
5. sudo ./AlsaUpgrade-1.0.22.1-2.sh -c
6. sudo ./AlsaUpgrade-1.0.22.1-2.sh -i
7. sudo shutdown -r 0

For step three I entered the tar file name incorrectly - I copy/pasted from the directions but the file names were different.

Bad```

tar xvf AlsaUpgrade-1.0.22.1-2.tar
```Good (for me)
```
tar xvf alsa-driver-1.0.22.tar.bz2
```Now I'm working on writing up step four
```
sudo ./AlsaUpgrade-1.0.22.1-2.sh -d
``` Any tips on this are appreciated.

My folders exist as such:

~/alsa-driver-1.0.22 (extracted)
~/alsa-driver-1.0.22.tar.bz2 (zipped)

---

### Post by lidex on 2010-03-26
Wow. Do me a favor. ;) Click on this link:
[http://ubuntuforums.org/attachment.php?attachmentid=142650&d=1262758447]("http://ubuntuforums.org/attachment.php?attachmentid=142650&d=1262758447")
Download to your home directory. Open a terminal. Copy and paste these commands - one line at a time - press enter and allow to complete before entering the next one. Watch the terminal output, it will tell you when the current process is finished.
```
tar xvf AlsaUpgrade-1.0.22.1-2.tar
```
```
sudo ./AlsaUpgrade-1.0.22.1-2.sh -d
```
```
sudo ./AlsaUpgrade-1.0.22.1-2.sh -c
```
```
sudo ./AlsaUpgrade-1.0.22.1-2.sh -i
```
```
sudo shutdown -r 0
```

---

### Post by SolitaryMan1941 on 2010-03-26
Good news, lidex your last post worked like a charm. :)
"Wow. Do me a favor. ;)"
Bad news, still no sound. ](*,)
Additional info: the tech support at Realtek have confirmed the driver is installed correctly, though my friends on this forum already knew that. Once again I am at a loss.

---

### Post by lidex on 2010-03-27
Make sure to open alsamixer and recheck levels.

How many audio jacks (analog)? Is there a digital (spdif) out?
How many audio channels?

---

### Post by SolitaryMan1941 on 2010-03-27
> **lidex said:**
> Make sure to open alsamixer and recheck levels.

How many audio jacks (analog)? Is there a digital (spdif) out?
How many audio channels?

alsamixer levels are maxed out and not muted
There is a spdif out
There are six analog jacks (I am currently using the green one)
There is a headphone jack & mic jack on the front panel
The Realtek ALC889A is a 7.1+2 channel sound card

---

### Post by lidex on 2010-03-27
OK.
Run this command:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

Add this line to the bottom of that file:
```
options snd-hda-intel model=6stack-dig 
```

Save. Close. Reboot.

---

### Post by SolitaryMan1941 on 2010-03-27
No problems with:
> **lidex said:**
> OK.
Run this command:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```Add this line to the bottom of that file:
```
options snd-hda-intel model=6stack-dig 
```Save. Close. Reboot.
Still no sound. I am going to buy a spdif cable. try it and update forum.

---

### Post by SolitaryMan1941 on 2010-03-27
The spdif cable was a futile attempt. My TV doesn't have a digital in port and I don't own a receiver. It looks like I'm analog or bust.

---

### Post by SolitaryMan1941 on 2010-03-27
So... in typical newbie fashion I overlooked something basic and obvious. Instead of running the output from the computer into the input of the TV, I plugged speakers directly into the audio jack and *viola*, sound. Now this doesn't quite solve my problem because I now need to unplug the speakers each time I switch from TV to HTPC but it does mean that the HTPC is working. I'd just like to thank everyone who has put in on this issue of mine.

---

