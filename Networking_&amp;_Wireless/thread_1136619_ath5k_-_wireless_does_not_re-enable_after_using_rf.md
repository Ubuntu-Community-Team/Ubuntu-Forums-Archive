---
title: "ath5k - wireless does not re-enable after using rfkill"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by dionblundell on 2009-04-25
I have an Asus EeePC running Ubuntu 9.04
The wireless works okay.
When I go
```
echo 0 | sudo tee /sys/class/rfkill/rfkill0/state
```the wireless, and LED turn off ok
however when I go
```
echo 1 | sudo tee /sys/class/rfkill/rfkill0/state
```the wireless does not re-enable
I have tried:
```
sudo rmmod ath5k
sudo modprobe ath5k
```and reloading these modules does nothing
I have tried
```
sudo /etc/init.d/networking restart
sudo /etc/init.d/NetworkManager restart
```still no luck
here is the output of:
```
cat /var/log/messages | grep ath5k
```gives this:
```
Apr 25 19:09:24 little kernel: [    9.599808] ath5k_pci 0000:01:00.0: enabling device (0000 -> 0002)
Apr 25 19:09:24 little kernel: [    9.599831] ath5k_pci 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr 25 19:09:24 little kernel: [    9.599963] ath5k_pci 0000:01:00.0: registered as 'phy0'
Apr 25 19:09:24 little kernel: [    9.752631] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
Apr 25 20:14:04 little kernel: [ 3896.705831] ath5k_pci 0000:01:00.0: PCI INT A disabled
Apr 25 20:14:30 little kernel: [ 3922.688314] ath5k_pci 0000:01:00.0: enabling device (0000 -> 0002)
Apr 25 20:14:30 little kernel: [ 3922.688341] ath5k_pci 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr 25 20:14:30 little kernel: [ 3922.688745] ath5k_pci 0000:01:00.0: registered as 'phy1'
Apr 25 20:14:30 little kernel: [ 3922.698915] ath5k_pci 0000:01:00.0: PCI INT A disabled
Apr 25 20:14:30 little kernel: [ 3922.702001] ath5k_pci: probe of 0000:01:00.0 failed with error -5

```I notice here one main difference, nothing is happening on the ath5k phy0 line after the inital boot.

Can someone enlighten me as to what I need to do to get my wireless going again after disabling it?
FYI - it works okay after a reboot

---

### Post by dionblundell on 2009-05-14
So the _issue is_ to do with a module called **pciehp** which (is not loaded and) allows **ath5k** to be started/stopped.
You need to forcefully load the module pciehp (*which is now built into the kernel*) with some options on the kernel boot line in:
```
sudo nano /boot/grub/menu.lst
```add the following to the line:
**#defoptions **
_pciehp.pciehp_force=1 pciehp.pciehp_poll_mode=1_
this will likely mean you line would look like:
```
# defoptions=quiet splash pciehp.pciehp_force=1 pciehp.pciehp_poll_mode=1
```I also have other options on mine like:
[I]elevator=noop (speeds up SSD access)
hpet-force (to specify the clock source)[/I][/code]but none of this is necessary _to make ath5k load/unload_ **on the fly**, all you need is **pciehp** to be forcefully **loaded** *with* **poll_mode** _on_.

---

