---
title: "Aus eeepc 1001HA netbook RaLink RT3090/Atheros AR8132"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by dave collin on 2010-02-05
Hi, Just purchased above with XP.
Run 9.04 on 2 other laptops no problems.
Installed 9.10 on this net book - no wireless/no wired with Dlink DLS-G604T.
But, at my work plug into wired server, change one firefox setting as advised by my iT guy and wired does work well.
All info attached as as requested.
With wired at home can ping Ubuntu (350 or so m/s) and Google (50m/s).
Have downloaded  "atheros-wired-driver-1005ha-linux"and "AR81Family-linux-v1.0.1.4", but not installed this time yet. (did install 9.10 before and really screwed up changing things, so currently fresh install no changes).
Any help please.
Dave

  	 	 	 	 	 	  1, Asus Eee PC 1001HA
 

 2. dave@dave-laptop:~$ lspci -nn | grep RaLink  
 02:00.0 Network controller [0280]: RaLink RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]  
 dave@dave-laptop:~$ lspci -nn | grep Atheros  
 01:00.0 Ethernet controller [0200]: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter [1969:1062] (rev c0)  
 dave@dave-laptop:~$  
 

 dave@dave-laptop:~$ lsusb  
 Bus 001 Device 005: ID 1307:0163 Transcend Information, Inc. 512MB/1GB Flash Drive  
 Bus 001 Device 002: ID 13d3:5108 IMC Networks  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 004 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 dave@dave-laptop:~$  
 

 3. dave@dave-laptop:~$ ifconfig  
 eth0      Link encap:Ethernet  HWaddr e0:cb:4e:62:86:0d   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:28  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:4 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:4 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)  
 

 dave@dave-laptop:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 dave@dave-laptop:~$  
 

 4. dave@dave-laptop:~$ lsmod  
 Module                  Size  Used by  
 nls_iso8859_1           3740  1  
 nls_cp437               5372  1  
 vfat                   10716  1  
 fat                    51452  1 vfat  
 usb_storage            52544  1  
 usbhid                 38208  0  
 binfmt_misc             8356  1  
 ppdev                   6688  0  
 snd_hda_codec_realtek   203328  1  
 snd_hda_intel          26920  2  
 snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel  
 snd_hwdep               7200  1 snd_hda_codec  
 snd_pcm_oss            37920  0  
 snd_mixer_oss          16028  1 snd_pcm_oss  
 snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss  
 iptable_filter          3100  0  
 joydev                 10272  0  
 ip_tables              11692  1 iptable_filter  
 snd_seq_dummy           2656  0  
 snd_seq_oss            28576  0  
 snd_seq_midi            6432  0  
 snd_rawmidi            22208  1 snd_seq_midi  
 snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi  
 x_tables               16544  1 ip_tables  
 uvcvideo               59080  0  
 snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event  
 psmouse                56180  0  
 snd_timer              22276  2 snd_pcm,snd_seq  
 videodev               36736  1 uvcvideo  
 lp                      8964  0  
 snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq  
 eeepc_laptop           13936  0  
 serio_raw               5280  0  
 v4l1_compat            14496  2 uvcvideo,videodev  
 parport                35340  2 ppdev,lp  
 snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 atl1c                  30880  0  
 soundcore               7264  1 snd  
 snd_page_alloc          9156  2 snd_hda_intel,snd_pcm  
 fbcon                  36640  72  
 tileblit                2460  1 fbcon  
 font                    8124  1 fbcon  
 bitblit                 5372  1 fbcon  
 softcursor              1756  1 bitblit 
 i915                  221064  3  
 drm                   159584  3 i915  
 i2c_algo_bit            5760  1 i915  
 intel_agp              27484  2 i915  
 agpgart                34988  2 drm,intel_agp  
 video                  19380  1 i915  
 output                  2780  1 video  
 dave@dave-laptop:~$  
 

 6. dave@dave-laptop:~$ sudo lshw -C network  
 [sudo] password for dave:  
   *-network UNCLAIMED      
        description: Network controller  
        product: RT3090 Wireless 802.11n 1T/1R PCIe  
        vendor: RaLink  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        version: 00  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress bus_master cap_list  
        configuration: latency=0  
        resources: memory:fbff0000-fbffffff  
   *-network  
        description: Ethernet interface  
        product: Atheros AR8132 / L1c Gigabit Ethernet Adapter  
        vendor: Attansic Technology Corp.  
        physical id: 0  
        bus info: pci@0000:01:00.0  
        logical name: eth0  
        version: c0  
        serial: e0:cb:4e:62:86:0d  
        capacity: 100MB/s  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair  
        resources: irq:28 memory:f7fc0000-f7ffffff ioport:ec00(size=128)  
 dave@dave-laptop:~$  
 

 7.  dave@dave-laptop:~$ iwlist scan  
 lo        Interface doesn't support scanning.  
 

 eth0      Interface doesn't support scanning.  
 

 dave@dave-laptop:~$  
 

 8. dave@dave-laptop:~$ lsb_release -d  
 Description:	Ubuntu 9.10  
 dave@dave-laptop:~$  
 

 9. dave@dave-laptop:~$ uname -mr  
 2.6.31-14-generic i686  
 dave@dave-laptop:~$  
 

 10. dave@dave-laptop:~$ sudo /etc/init.d/networking restart  
  * Reconfiguring network interfaces...                                   [ OK ]  
 dave@dave-laptop:~$

---

### Post by bkratz on 2010-02-06
Have you see this thread?

[http://ubuntuforums.org/showthread.php?t=1345577&highlight=RT3090](http://ubuntuforums.org/showthread.php?t=1345577&highlight=RT3090)

---

### Post by dave collin on 2010-02-06
Thanks, have read that thread. Had rt3090 dkms already downloaded but didn't have dkms package installed. Just found it at Debian, downloaded, installed dkms, installed rt3090, restarted and now Dlink has been found and is listed as a wireless network. Now have all bars - full connection - but times out when searching for google.
Must still have settings wrong somewhere. Did ask for wep password - seemed to work but times out.
Any suggestions?
Dave

---

### Post by bkratz on 2010-02-06
> **dave collin said:**
> Thanks, have read that thread. Had rt3090 dkms already downloaded but didn't have dkms package installed. Just found it at Debian, downloaded, installed dkms, installed rt3090, restarted and now Dlink has been found and is listed as a wireless network. Now have all bars - full connection - but times out when searching for google.
Must still have settings wrong somewhere. Did ask for wep password - seemed to work but times out.
Any suggestions?
Dave

Can you change the router encryption? First make sure everything works without encryption and then try other modes. Mine for instance, will not work with wep, but works fine with WPA2 encryption which is a whole lot better anyway.

---

### Post by chili555 on 2010-02-06
> but times out when searching for google.Please try something for us. Open a Firefox browser and type *about:config* in the address bar. In the filter, type ipv6. You should see network.dns.disableIPv6;false. Highlight it, right-click and select Toggle, so that it reads ***true***. Close Firefox and start it up again. Is the timeout behavior improved?

---

### Post by northd_tech on 2010-02-06
> **dave collin said:**
> 
Installed 9.10 on this net book - no wireless/no wired with Dlink DLS-G604T.
But, at my work plug into wired server, change one firefox setting as advised by my iT guy and wired does work well.
All info attached as as requested.

With wired at home can ping Ubuntu (350 or so m/s) and Google (50m/s).
Have downloaded  "atheros-wired-driver-1005ha-linux"and "AR81Family-linux-v1.0.1.4", but not installed this time yet. (did install 9.10 before and really screwed up changing things, so currently fresh install no changes).

I have been working on a Toshiba Satellite P505D with that same Atheros AR8132 ethernet interface.  I remember it being something of a hassle with the older Ubuntus (no wired or wireless also), but the ethernet just worked "out of the box" when we installed 64-bit (and later 32-bit to try to fix the WiFi) Ubuntu 9.10.  (We still have no Realtek 8192E WiFi though- but I've finally got some hope there).

I don't think that you should need to mess with compiling Atheros driver modules & all that, since you can see/ping the outside world both at home and at work.

It might be something in your router settings at home (but I haven't ever worked with that Dlink DLS-G604T before), since you get different behavior at home than those settings do at your workplace.

---

### Post by northd_tech on 2010-02-06
Reviewing the modules, it looks like you've got this one loaded: 
"atl1c                  30880  0"

I remember having a major hassle about atl**1c** *vs.* atl**1e** (and possibly more) *vs.* some other brand's module that the Atheros was identifying as by default.  Unfortunately, that laptop is someone else's, and he's asleep right now.  I may not have access to that computer for several days to check what is working on his Atheros AR8132 under Ubuntu 9.10.

---

### Post by dave collin on 2010-02-06
See post no. 5.
Hey chili555 - did as you said - all works (so far!!!!) perfectly, thanks heaps. (quick too - no delays when loading or anything)
Little asus is now almost fully functional (although i'm still working on some of the F keys.
Would it be worth putting a summary of this somewhere for other Asus 1001HA users - 'cause it's a real pain trying to sort out from all the posts here and elsewhere - go to Debian,. go to ppa, come back here, ask questions etc etc etc?????
Dave

---

### Post by dave collin on 2010-02-07
Whoops - spoke to soon.
did a restart and it didn't - came up with all sorts of error scripts.
Tried in recovery and same.
Just did fresh install 9.10.
Reinstalled dkms and rt3090 driver and restarting works ok but no internet, when about:config in firefox and toggling ivp6 to true internet works but synaptic, update manage and emails do not work.
Did a restart with toggled true and on restart errors again.
So 'm going to install 9.04 and try again. Stay tuned.

---

### Post by dave collin on 2010-02-07
Ok heres the go.
In 9.04 I installed dkms and rt3090-dkms driver and this time everything works - full signal strength, no time out problems, synaptic, email, system updates all work flawlessly.
Restart is fine. ipv6 in firefox config is shown as false.
Basically a one minute fix (for 9.04).
I don't know what will happen after doing the last 10 months of updates, but will put one more post here and let you know before marking as solved.
Funny, but after reading heaps of reports of 9.10 I guess this is just another case of 9.10 not being quite good enough. I sure hope the next version (LTS) version will be better.
But for now Asus eee 1001HA's need 9.04 not 9.10 for simple people like me who do not want to recompile kernels, etc.
Thanks everyone
Dave

---

### Post by dave collin on 2010-02-07
OK, did all updates, wireless stopped working (wired as well). rt3090 driver still showed as enabled in DRIVERS but wasn't. Left it, reinstalled driver and all working again. Have been using for a few hours now, installed all my normal apps, medibuntu etc, started and restarted many times. Not one problem. So now I will mark as solved! (but 9.04 NOT 9.10) Tanks again all. Dave

---

