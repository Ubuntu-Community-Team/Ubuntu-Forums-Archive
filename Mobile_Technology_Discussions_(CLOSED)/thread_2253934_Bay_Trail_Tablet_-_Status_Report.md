---
title: "Bay Trail Tablet - Status Report"
date: 2014-11-23
forum: Mobile Technology Discussions (CLOSED)
---

### Post by ronniepinsky on 2014-11-23
Wireless: Works ok with this kernel module and an edited device ID: [https://github.com/hadess/rtl8723as](https://github.com/hadess/rtl8723as) .  Find your device ID/address inside a special folder (usually mmc1:0001:1) in /sys/bus/class/devices.  Your device ID/address can be found by looking at the contents of the special file inside called "device".  Replace the second address with your address (0x0523 for this device) below the heading "CONFIG_RTL8723B" in ** [yoursource/os_dep]("https://github.com/hadess/rtl8723as/tree/3dd8594d850502fb76d0170209ef24d93e372753/os_dep")/[linux]("https://github.com/hadess/rtl8723as/tree/3dd8594d850502fb76d0170209ef24d93e372753/os_dep/linux")/[B]sdio_intf.c** [/B]and recompile the kernel module.  I used kernel 3.16.2 from the Ubuntu mainline kernel ppa and the second commit from the repository referenced.

Graphics: Works ok by default.
1.  Console error : "mismatch in adjusted mode" - fixed with nomodeset boot parameter in /etc/default/grub but seems harmless.
2.  Grub screen corruption with "?", question marks - fixed with uncommenting "GRUB_TERMINAL=console" in /etc/default/grub .

Input:  Touchscreen works ok with this kernel module : [https://github.com/hadess/gt9xx/tree/master](https://github.com/hadess/gt9xx/tree/master) and as a tip - holding the down button while booting will bring up a useful EFI menu.

Storage:  Works ok by default - can dual boot with Windows in EFI mode.
1.  Errors from unsupported security partitions on EMMC that cause slowdown but currently can be ignored.  EMMC main "disk" can be backed up by dd without problem.
2.  Grub needs "configfile (hd0,gpt5)/boot/grub/grub.cfg" to load the menu properly because of Ubuntu bugs.  Instead, you can manually create /boot/grub/ in the EFI partition and copy the stub grub.cfg from /EFI/ubuntu/ into it to boot without being dumped to the grub shell.
3. bootia32.efi must be added alongside ubuntu's EFI files because the EFI bootloader is 32-bit on this device.
4.  bootia32.efi can be chosen manually in EFI boot menu or you can do this "sudo efibootmgr -c -w -l \\EFI\\ubuntu\\bootia32.efi -p 1 -d /dev/mmcblk0"

 ACPI: Not interested in getting this working - can use Windows for this.
1.  No battery life reporting.
2. USB must be connected at boot to work - USB charge or USB OTG - and can be disconnected and reconnected and still work.
3. Shutdown and reboot work well.  The tablet will charge while off and while in the BIOS if you prefer to not have Windows at all.
4. Brightness may be manipulated with "xrandr --output DSI1 --brightness x" whereas x is anything from about .3 to 1.
5. Lack of screen power saving can be worked around with setting brightness to .2 or so.

Sound: 
Challenge 1: Getting a device to show up at all.
This requires the correct Intel Bay Trail firmware here: [https://chromium.googlesource.com/chromiumos/third_party/linux-firmware/+/refs/heads/stabilize-5339.B/intel/](https://chromium.googlesource.com/chromiumos/third_party/linux-firmware/+/refs/heads/stabilize-5339.B/intel/)
To be sure you are using the correct firmware, uninstall linux-firmware, and be sure there is nothing remaining in /lib/firmware/intel.  Finally copy the contents of that repo (click tgz to download) to /lib/firmware/intel.  You should see an audio device on next boot.
Challenge 2:  Actually getting sound to play.
1. 3.18.0 rc2 with irqpoll option
2. 5339 chromium intel firmware
3. symlink master name to updated 48khz naming
4. t100 state file loaded with "alsactl -f /pathtostatefile restore" : [https://github.com/AdamWill/baytrail-m/blob/master/alsa/t100_B.state](https://github.com/AdamWill/baytrail-m/blob/master/alsa/t100_B.state)
5. unmute dac mixl stereo adc                        
6. everything before it unmuted
7. everything before it maxed
Kernel audio results:
3.18 rc2 standard - strange results when accessing audio device
3.16.2 standard - strange results when accessing audio device
3.18 rc2 with irqpoll - working
3.16.2 with irqpoll - lockup

Bluetooth:  Not interested in getting this working - can use Windows for this.

Micro SD reader: Not interested in getting this working - can use Windows for this.

Front and rear camera: Not interested in getting this working - can use Windows for this.

Other Considerations:
Onboard is a nice looking on screen keyboard that works well.
You can disable the guest user and add a normal guest user with no password to make good use of the touch features and have a totally keyboard-less install.

Other Concerns:
Freezes after a while on 3.16.2 with wireless connected
Scrolling in Firefox is not smooth

---

### Post by hoshi182 on 2014-12-11
I have an Z3740D bay trail tablet and have quite the same thought about it. Will post details but work from asus t100 on ubuntu and fedlet help to access more and more parts of this device, but definitively doesn't boot/install or even run on livecd easily because of kernel emmc problems, and wifi/bluetooth not fonctionning out of the box

---

