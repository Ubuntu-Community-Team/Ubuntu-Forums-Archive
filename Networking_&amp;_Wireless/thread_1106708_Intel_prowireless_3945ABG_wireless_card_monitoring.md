---
title: "Intel pro/wireless 3945ABG wireless card monitoring problem??"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by scrypt on 2009-03-26
I managed to get my intel pro/wireless card running in monitor mode without a hitch earlier on.

But as soon as i rebooted Ubuntu.
I have had trouble configuring it to correctly establish monitoring mode so that I can inject packets from it.

Here is the output from the iwconfig command:

I cannot seem to rectify it. and further more when i try to sort it out a new  mon0 mon1 mon1 tab appears

can anyone help me sort this mess out??


 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  Mode:Monitor  Frequency:2.412 GHz  Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

mon0      IEEE 802.11abg  Mode:Monitor  Frequency:2.412 GHz  Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mon1      IEEE 802.11abg  Mode:Monitor  Frequency:2.412 GHz  Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mon2      IEEE 802.11abg  Mode:Monitor  Frequency:2.412 GHz  Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by scrypt on 2009-03-26
I want to correctly patch my intel pro/wireless 3945abg with this driver:

        wget [http://dl.aircrack-ng.org/drivers/ip...022008.tar.bz2](http://dl.aircrack-ng.org/drivers/ip...022008.tar.bz2)            (downloads driver)

 What are the correct commands to apply the above driver? 

 and also what is the correct command to Blacklist the original default Wireless card driver??
Because this is where I think my problem lies, That it is not coorectly blacklistung and removing the original default driver?

   I have tried this this bellow command I was given to blacklist it, but it still reloads when I re-boot Ubuntu 8.10:

   sudo modprobe -r iwl3945          (unload driver that you do not need).

I then use this command to load the new Driver:

                sudo modprobe ipwraw                 (load the driver that you installed)

 Then I use this command to restart my wireless card along with actually turning on the power suppt too it:

               sudo ifconfig wlan0 up (enable the network adapter): This command never workd though, I get this output form the iwconfig command:

I can put my card into monitor mode using this command:   
                                                                                                   sudo iwconfig wlan0 mode monitor


This seems to work and does put my card into monitor mode. BUT does not change it fully because it should change from wlan0 to wifi0, which it doea not!

Can anyone see where i am going wrong?

also can anybody advise me how to rwctify this??

---

