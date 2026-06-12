---
title: "Wireless USB suspend/resume problem RTL8192SU adapter"
date: 2011-04-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by walt.smith1960 on 2011-04-22
I'm having a minor problem with Natty and one USB WiFi adapter. The problem child is a TreneNet 649UB (RTL8192SU) adapter. It works fine when cold booted or just plugged into a USB port. When the machine is suspended then resumed, I see one or two flashes of the device LED then nothing.  Network Manager shows wireless networks grayed out/disconnected.  If I click on "connect to hidden wireless network" in Network Manager, the little icon shows 1 green dot but no lights on the adapter and no indication of the adapter being active.


iwconfig when the adapter is working:

wlan3     IEEE 802.11bgn  ESSID:"xxxxxxx"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:26:62:7C:B1:5B   
          Bit Rate:150 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=98/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwconfig when the adapter is not working:

wlan3     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsusb shows the same whether the adapter is active or not. 

lsmod when the adapter is either active or inactive shows this:  
r8712u                281937  0 

This problem is present on two machines. One is a desktop with Gigabyte AMD running Natty and the other is a ThinkPad R61i running xubuntu 11.04. Both are 32 bit and fully updated. There is one difference is on the xubuntu machine. After resuming from suspend if I click on "connect to wireless network", I'm asked for an administrative password because it wants to make a change that requires authorization. I don't see any indication what change it wants to make. I have two other wireless adapters, an ath9k based device and an older RTL8187B. Both of these suspend and resume as expected.  

I'd like to file a bug report but I'm not sure how to do it without apport.  What logs to attach, where on launchpad to send it etc. I'd appreciate any input or suggestions. Thanks.

---

### Post by walt.smith1960 on 2011-04-26
I was premature in marking this solved.  It worked a couple times now it's back to requiring the unplug/replug routine. Crap!

---

