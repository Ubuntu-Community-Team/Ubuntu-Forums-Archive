---
title: "How to netboot Grub2 from PXE server on uEFI system"
date: 2012-02-16
forum: Networking &amp; Wireless
---

### Post by Luos on 2012-02-16
Hello,
I am setting up a PXE server for uEFI x64 clients to do netboot with Ubuntu.
Since pxelinux.0 does not work on uEFI, I decide to use Grub2 to replace it. The bzr trunk of Grub2 supports UEFI and tftp.

I used below command to make grub.efi and adding efinet and tftp modules
```
grub-mkimage -O x86_64-efi -d . -o grub.efi -p "/boot/grub" efinet tftp
```
and this error show on my client
> error: timeout: could not resolve hardware address

I tracked Wireshark on server and can see client keep asking for ARP.
My Server does report its MAC address but client just keep on asking.....

Now I am totally stuck:confused:


Thank you

---

