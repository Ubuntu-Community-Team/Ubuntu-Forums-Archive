---
title: "Network/Internet connection slow as of a few days ago...?"
date: 2020-08-04
forum: MINT
---

### Post by RallyDarkstrike on 2020-08-04
Hi all,

Mint 20 has been good to me so far....until a day or two ago.

All has been well but within the last 3 or so days I had restarted my machine and noticed that my WiFi speeds were somewhat sporadic, though mostly OK...and (the main thing) my network speeds when accessing or copying files to other machines on my network has completely gone into the crapper. I had installed updates quite awhile back....(late-July?) but had been lazy and hadn't restarted my laptop since then, only putting it into Suspend as I was working on a large project and didn't want to have to organize everything again after a restart. As I installed the updates awhile back and then didn't actually restart my machine until yesterday, I don't recall now what updates were installed...

I see a lot of other posts about WiFi and network transfer issues lately on the forums here, any idea what might be the matter or how to solve it I tried to copy 78Mb of photos to one of the other machines on my network earlier and it took almost 10 minutes!!! That would've been done in a matter of seconds before...

Mint and network transfers were working fine before that though...? Any ideas what could be up?

I do have Samba set to use SMB2 and my actual internet connection speed seems the same as before on WiFi as loading websites and such is mostly fine and my speeds are still around 15-20mbps Down and 2-5mbps Up...which is about normal for my laptop as my bedroom is on the exact opposite end of the house the router is on. It only seems to be network connections that seem slower....and sporadically my actual internet connection.

**EDIT - Adding details...connection used to be 15-20mbps Down on this laptop, now it's only 4mbps.....my phone in the same room is still 20mbps, so something is definitely up here. I tried going back to a previous kernel and that has made no difference...**

```
System:  Kernel: 5.4.0-42-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 
  Desktop: MATE 1.24.0 Distro: Linux Mint 20 Ulyana base: Ubuntu 20.04 focal 
Machine:
  Type: Laptop System: Hewlett-Packard 
  product: HP Pavilion TS 14 Notebook PC v: 0881100000305E00000620100 
  serial: <filter> 
  Mobo: Hewlett-Packard model: 216D v: 31.0F serial: <filter> UEFI: Insyde 
  v: F.02 date: 08/06/2013 
Battery:
  ID-1: BAT0 charge: 59.7 Wh condition: 59.7/59.7 Wh (100%) 
  model: Hewlett-Packard Primary status: Full 
CPU:
  Topology: Quad Core model: AMD A6-5200 APU with Radeon HD Graphics 
  bits: 64 type: MCP arch: Jaguar rev: 1 L2 cache: 2048 KiB 
  flags: avx lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm 
  bogomips: 15970 
  Speed: 1529 MHz min/max: 800/2000 MHz Core speeds (MHz): 1: 799 2: 799 
  3: 798 4: 798 
Graphics:
  Device-1: AMD Kabini [Radeon HD 8400 / R3 Series] vendor: Hewlett-Packard 
  driver: radeon v: kernel bus ID: 00:01.0 
  Display: x11 server: X.Org 1.20.8 driver: ati,radeon 
  unloaded: fbdev,modesetting,vesa resolution: 1366x768~60Hz 
  OpenGL: renderer: AMD KABINI (DRM 2.50.0 5.4.0-42-generic LLVM 10.0.0) 
  v: 4.5 Mesa 20.0.8 direct render: Yes 
Audio:
  Device-1: AMD Kabini HDMI/DP Audio vendor: Hewlett-Packard 
  driver: snd_hda_intel v: kernel bus ID: 00:01.1 
  Device-2: AMD FCH Azalia vendor: Hewlett-Packard driver: snd_hda_intel 
  v: kernel bus ID: 00:14.2 
  Sound Server: ALSA v: k5.4.0-42-generic 
Network:
  Device-1: Intel Centrino Wireless-N 130 driver: iwlwifi v: kernel 
  port: 4100 bus ID: 01:00.0 
  IF: wlp1s0 state: up mac: <filter> 
  Device-2: Realtek RTL810xE PCI Express Fast Ethernet 
  vendor: Hewlett-Packard driver: r8169 v: kernel port: 2000 bus ID: 05:00.0 
  IF: eno1 state: down mac: <filter> 
Drives:
  Local Storage: total: 465.76 GiB used: 228.41 GiB (49.0%) 
  ID-1: /dev/sda vendor: Western Digital model: WD5000LPCX-22VHAT1 
  size: 465.76 GiB 
Partition:
  ID-1: / size: 443.18 GiB used: 228.40 GiB (51.5%) fs: ext4 dev: /dev/sda6 
  ID-2: swap-1 size: 14.00 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda5 
Sensors:
  System Temperatures: cpu: 58.2 C mobo: N/A gpu: radeon temp: 58 C 
  Fan Speeds (RPM): N/A 
Repos:
  No active apt repos in: /etc/apt/sources.list 
  Active apt repos in: /etc/apt/sources.list.d/google-chrome.list 
  1: deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
  Active apt repos in: /etc/apt/sources.list.d/google-earth-pro.list 
  1: deb [arch=amd64] http://dl.google.com/linux/earth/deb/ stable main
  Active apt repos in: /etc/apt/sources.list.d/kritalime-ppa-focal.list 
  1: deb http://ppa.launchpad.net/kritalime/ppa/ubuntu focal main
  Active apt repos in: /etc/apt/sources.list.d/official-package-repositories.list 
  1: deb http://mirrors.evowise.com/linuxmint/packages ulyana main upstream import backport
  2: deb http://mirror.its.dal.ca/ubuntu focal main restricted universe multiverse
  3: deb http://mirror.its.dal.ca/ubuntu focal-updates main restricted universe multiverse
  4: deb http://mirror.its.dal.ca/ubuntu focal-backports main restricted universe multiverse
  5: deb http://security.ubuntu.com/ubuntu/ focal-security main restricted universe multiverse
  6: deb http://archive.canonical.com/ubuntu/ focal partner
  Active apt repos in: /etc/apt/sources.list.d/remmina-ppa-team-remmina-next-focal.list 
  1: deb http://ppa.launchpad.net/remmina-ppa-team/remmina-next/ubuntu focal main
  Active apt repos in: /etc/apt/sources.list.d/skype-stable.list 
  1: deb [arch=amd64] https://repo.skype.com/deb stable main
  Active apt repos in: /etc/apt/sources.list.d/slack.list 
  1: deb https://packagecloud.io/slacktechnologies/slack/debian/ jessie main
  Active apt repos in: /etc/apt/sources.list.d/teamviewer.list 
  1: deb http://linux.teamviewer.com/deb stable main
  Active apt repos in: /etc/apt/sources.list.d/teejee2008-ppa-focal.list 
  1: deb http://ppa.launchpad.net/teejee2008/ppa/ubuntu focal main
Info:
  Processes: 274 Uptime: 12m Memory: 7.25 GiB used: 2.32 GiB (32.0%) 
  Init: systemd runlevel: 5 Compilers: gcc: 9.3.0 Shell: bash v: 5.0.17 
  inxi: 3.0.38 
```

Thanks for any help! I work remotely and this is really killing me!!!

---

### Post by TheFu on 2020-08-04
Does wired network work slow now too?  Need to determine where the network issue actually is. I've had my ISP connection get really slow after some chipmunks were eating the cable - it was fine until rain to in.  When the soil dried, it was fast again.

Wifi is almost impossible to figure out without having a few local LAN-only systems to test between. There is just so much interference which can get in the way. The only way around that is to find different channels that don't have the interference from neighbors.  Neighbors can change their settings. That can mess with your performance.

More devices connect will slow down the whole wifi network too for older protocols. Turn off all other wifi devices and test.

Some locations are just in a bad spot. Try moving closer and farther away, while still line of sight.

Gather some actual facts using reproducible tools like iperf3 and speedtest-cli.

If you haven't cleaned out the dust from inside the laptop, do that too. The CPU seems a little hot.

There is a wifi data gathering script in a sticky thread at the top of the Networking and Wireless sub-forum. Get that, run it, and post the results or URL that it makes.

---

