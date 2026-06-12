---
title: "Tried to fix wireless and broke it, how to reset?"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by carbon512 on 2010-06-05
Very new user here... 4000 miles from Ubuntu guru friend who set me up and was mentoring me.. just spent three hours reading the sticky about ndiswrapper and troubleshooting and doing all steps but I am stuck, tired and frustrated. Here is the problem:

Acer 1410 with Intel Wifi Link 1000 card. Everything worked perfectly for months and was working on everything, except encountered one WPA personal secure network that gave me weird problems (that is for another post. Really weird problems) Problems were only in Ubuntu, not Windows. IT guy said install ndiswrapper.. so, I installed ndisgtk and I think I installed ndiswrapper at that time as well. (?)

Using ndisgtk, at first run, no windows drivers showed. I installed a windows XP driver for my card, from intel site, then system froze on next wakeup and wireless has disappeared (in Ubuntu.) Then I read more and went back and downloaded a different driver (windows 7, which is what came with my machine)

Here are the confusing results of the terminal commands spelled out in that great sticky post:

uname -m
i686

ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netw5s32 : driver installed
    device (8086:0083) present (alternate driver: iwlagn)

lshw -C
network UNCLAIMED
       description: Network controller
       product: WiFi Link 1000 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:92500000-92501fff

so, I ran 
lsmod | grep ndisgot this:
ndiswrapper    184677  0

so I guess it is being loaded? I did
sudo modprobe ndiswrapper and got
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

then I got confused. Last step -- typing 
dmesg | grep -e ndis -e wlan 
gave me I a lot of errors that begin with "**unknown symbol**,"[FONT=monospace]

I have already tried all the windows drivers -- and in fact, the one I installed matched what the info about the driver I found when I booted into Windows and checked it: windows said current driver was 13.0.0.107, using netw5s64.sys... but the [/FONT][FONT=monospace]netw5s64.inf [/FONT][FONT=monospace]driver didnt work either, I assume because it is 64-bit and I need 32 bit?

This is where my newness and ignorance kicks in.

All I know is everything was working except for one stupid problem I could have lived with and now I have broken it all entirely. Using the network connection icon, there is not even an option for wireless anymore... I just want to click my heels and go home to the way it was...

ANy help would be really appreciated. Thanks so much.
[/FONT]

---

