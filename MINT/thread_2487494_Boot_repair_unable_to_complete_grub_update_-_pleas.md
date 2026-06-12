---
title: "Boot repair unable to complete grub update - please help"
date: 2023-06-06
forum: MINT
---

### Post by ineuw on 2023-06-06
Using the USB Live installation key, I tried to rebuild the boot grub of a dual boot Linux Mint Cinnamon 21.1, overwritten by a Windows 11 installation. During boot repair, the process found some bad packages on Linux Mint which aborted the repair. I couldn't repair it even with Timeshift restores. This is the link to the boot report [URL=http://*******.us/Zil8zl[/URL]  I don't even know what site this report should be posted to.

---

### Post by oldfred on 2023-06-06
You did not post to a standard pastebin site. Boot-Repair normally uses pastebin.
Not sure what site it is, but forum changed to *** so not usable.

---

### Post by MAFoElffen on 2023-06-07
As oldfred and I were involved with testing this for Yan, and I was a contributor to... I am familiar with the code. I just search through all the scripts involved, and there are only three pasebins that are used:
[http://paste.debian.net](http://paste.debian.net)
[http://paste.ubuntu.com](http://paste.ubuntu.com)
[COLOR=#ff0000]http://*******.us[/COLOR] ### <--- This is where that link leads me to his 'boot-info' report.

Snipped from gui-actions.sh in function pastebinactions():
```


[/cif [[ "$UPLOAD" ]] && [[ "$repup" = yes ]];then
    [[ ! "$(type -p $FILETOTEST)" ]] && installpackagelist
    [[ "$GUI" ]] && echo "SET@_label0.set_text('''$LAB (net-check). $This_may_require_several_minutes''')"
    check_internet_connection
    ask_internet_connection
    [[ "$GUI" ]] && echo "SET@_label0.set_text('''$LAB (url). $This_may_require_several_minutes''')"
    if [[ "$(type -p pastebinit)" ]];then #[[ "$INTERNET" = connected ]] && 
        if [[ "$(lsb_release -is)" = Debian ]] && [[ ! "$(lsb_release -ds)" =~ Boot-Repair-Disk ]];then
            PASTEB="[COLOR=#ff0000]paste.debian.net[/COLOR]"
        elif [[ "$(lsb_release -is)" = Ubuntu ]];then
            PASTEB="[COLOR=#ff0000]paste.ubuntu.com[/COLOR]"
        else
            PASTEB="[COLOR=#ff0000]*******.us[/COLOR]"
        fi
        PASTEBIN_URL=$(cat "${TMP_LOG}b" | pastebinit -a $APPNAME -f bash -b $PASTEB)
        pastebin_retry
        pastebin_retry
    fi
fi

```

To get past the Forum filters: " s p r u n g e . u s "

---

### Post by MAFoElffen on 2023-06-07
What was done:
```

Default settings: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi of
sda2,
using the following options:  sda1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the Linux Mint 21.1 Vera (21.1) entry (sda1/efi/****/grub****.efi (**** will be updated in the final message) file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\****\grub****.efi (**** will be updated in the final message)

User settings: _________________________________________________________________

The settings chosen by the user will purge and reinstall the grub-efi of
sda2,
using the following options:  sda1/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups


/boot/efi added in sda2/fstab
rm /mnt/boot-sav/sdc1/efi/Boot/bootx64.efi
mv /mnt/boot-sav/sdc1/efi/Boot/bkpbootx64.efi /mnt/boot-sav/sdc1/efi/Boot/bootx64.efi
Mount sda1 on /mnt/boot-sav/sda2/boot/efi
chroot /mnt/boot-sav/sda2 apt-get -y update
Running in chroot, ignoring command 'start'
Purge the GRUB of sda2
grub-efi available

The following additional packages will be installed:
grub-efi-amd64
The following packages will be REMOVED:
grub-gfxpayload-lists grub-pc
The following NEW packages will be installed:
grub-efi grub-efi-amd64
0 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
3 not fully installed or removed.
DEBCHECK debOK, grub-efi
DEBCHECK debOK
Please type: sudo chroot "/mnt/boot-sav/sda2" dpkg --configure -ansudo chroot "/mnt/boot-sav/sda2" apt-get install -fynsudo chroot "/mnt/boot-sav/sda2" apt-get purge --allow-remove-essential -y grub-com*nsudo chroot "/mnt/boot-sav/sda2" apt-get purge --allow-remove-essential -y grub2-com*nsudo chroot "/mnt/boot-sav/sda2" apt-get purge --allow-remove-essential -y shim-signednsudo chroot "/mnt/boot-sav/sda2" apt-get purge --allow-remove-essential -y grub-common:*nsudo chroot "/mnt/boot-sav/sda2" apt-get purge --allow-remove-essential -y grub2-common:*n
Then type: sudo chroot "/mnt/boot-sav/sda2" apt-get install -y grub-efi

Unhide GRUB boot menu in sda2/etc/default/grub

======================== Reinstall the grub-efi of sda2 ========================

chroot /mnt/boot-sav/sda2 grub-install --version
grub-install (GRUB) 2.06-2ubuntu7.2
chroot /mnt/boot-sav/sda2 modprobe efivars

chroot /mnt/boot-sav/sda2 efibootmgr -v before grub install
BootCurrent: 0006
Timeout: 1 seconds
BootOrder: 0000,0005,0002,0006
Boot0000* Windows Boot Manager    HD(1,GPT,1f7d92fb-41b8-499e-92c7-16871c608251,0x800,0x32000)/File(EFIMICROSOFTBOOTBOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0002* ubuntu    HD(1,GPT,f68a7bfb-7d84-4ca1-947a-e8b1d4eabc0a,0x800,0x33000)/File(EFIUBUNTUSHIMX64.EFI)
Boot0005* ubuntu    HD(1,GPT,1f7d92fb-41b8-499e-92c7-16871c608251,0x800,0x32000)/File(EFIUBUNTUSHIMX64.EFI)..BO
Boot0006* UEFI:  USB, Partition 2    PciRoot(0x0)/Pci(0x14,0x0)/USB(24,0)/USB(0,0)/HD(2,GPT,07896644-3e61-4841-b418-ca3f44823cce,0x4fc954,0x2130)..BO

chroot /mnt/boot-sav/sda2 uname -r
5.15.0-56-generic

chroot /mnt/boot-sav/sda2 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
[COLOR=#ff0000]grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.[/COLOR]
Installation finished. No error reported.
df /dev/sda1
mv /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bootx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/sda2/boot/efi/efi/ubuntu/grubx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bootx64.efi
df /dev/sdc1
mv /mnt/boot-sav/sdc1/EFI/Boot/bootx64.efi /mnt/boot-sav/sdc1/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/sda2/boot/efi/efi/ubuntu/grubx64.efi /mnt/boot-sav/sdc1/EFI/Boot/bootx64.efi

chroot /mnt/boot-sav/sda2 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
[COLOR=#ff0000]grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
[/COLOR]Installation finished. No error reported.

chroot /mnt/boot-sav/sda2 efibootmgr -v after grub install
BootCurrent: 0006
Timeout: 1 seconds
BootOrder: 0000,0005,0002,0006
Boot0000* Windows Boot Manager    HD(1,GPT,1f7d92fb-41b8-499e-92c7-16871c608251,0x800,0x32000)/File(EFIMICROSOFTBOOTBOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0002* ubuntu    HD(1,GPT,f68a7bfb-7d84-4ca1-947a-e8b1d4eabc0a,0x800,0x33000)/File(EFIUBUNTUSHIMX64.EFI)
Boot0005* ubuntu    HD(1,GPT,1f7d92fb-41b8-499e-92c7-16871c608251,0x800,0x32000)/File(EFIUBUNTUSHIMX64.EFI)..BO
Boot0006* UEFI:  USB, Partition 2    PciRoot(0x0)/Pci(0x14,0x0)/USB(24,0)/USB(0,0)/HD(2,GPT,07896644-3e61-4841-b418-ca3f44823cce,0x4fc954,0x2130)..BO
Warning: NVram was not modified.

chroot /mnt/boot-sav/sda2 update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/50_linuxmint.cfg'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Script `/boot/grub/grub.cfg.new' contains no commands and will do nothing
[COLOR=#ff0000]Syntax errors are detected in generated GRUB config file.[/COLOR]
[COLOR=#ff0000][B]Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.[/B][/COLOR]

Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your UEFI firmware boot on the Linux Mint 21.1 Vera (21.1) entry (sda1/efi/ubuntu/grubx64.efi file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi


============================ Boot Info After Repair ============================


```

---

### Post by s9032g@comcast.net on 2023-06-07
Why aren't you asking at the Mint Forum site?

---

### Post by oldfred on 2023-06-07
Moved to Mint sub-forum.

You now have two Ubuntu entries, one valid & one invalid as it uses a GUID/partUUID that does not exist.
UEFI system check fstab mount of ESP, UEFI entry & files in ESP. 
cat /etc/fstab should have UUID of ESP.
 sudo efibootmgr -v should have GUID/partUUID of ESP. 
To see UUID/partUUID. 
lsblk -o +PARTUUID /dev/sda & 

For entry  with invalid GUID/partUUID.
sudo efibootmgr -v
Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B

---

### Post by ineuw on 2023-06-09
> **oldfred said:**
> Moved to Mint sub-forum.

Many thanks and will note the location of future issues related to grub.

Why here? I post very rarely, and didn't know where.

---

### Post by ineuw on 2023-06-09
Replying with a question???? :P

---

