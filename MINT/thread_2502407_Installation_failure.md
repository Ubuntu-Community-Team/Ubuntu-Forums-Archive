---
title: "Installation failure"
date: 2024-11-13
forum: MINT
---

### Post by amscad12 on 2024-11-13
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294512&stc=1[/IMG]I have tried installing 2 versions of linux mint  on my laptop, it is a hp g6 250 notebook....
Both times i get the same fatal error n now this time the old windows 10 system no longer works, error message is unable to install garb in /dev/sda, same both times...
Last linux was downloaded hour and half ago, made usb boot disk as did with first attempt
i have no idea what to do here

---

### Post by howefield on 2024-11-13
Thread moved to the "*MINT*" forum.

---

### Post by yancek on 2024-11-13
Did you verify the download was not corrupted in the process of getting from the Mint server to your computer.  It's explained on their site.  Did you write the iso of Mint to a usb to install?  What software did you use if this is what you did?  Do you know if the drive you are installing to is a gpt drive (you can boot the Mint usb and run the command:  sudo parted -l to list that information.  If it is, there should be an EFI partition on the drive.  Are you installing Mint to the same physical harddrive as windows?  Did you boot and install Mint in UEFI mode?  The parted command will show an EFI partition if there is one.

---

