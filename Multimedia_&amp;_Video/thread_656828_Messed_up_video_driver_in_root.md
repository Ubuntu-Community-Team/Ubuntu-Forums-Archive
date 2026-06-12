---
title: "Messed up video driver in root"
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by malibusurfer2 on 2008-01-03
Help! How can I change root video driver back to default motherboard video (Intel 945 i810)? I got it back to normal in my user account, but when I log into root, I get a blank white screen, although it seems Ubuntu Gutsy is running as the mouse pointer changes, and I can blindly click and it seems stuff opens - I just can't see anything.

ECS Intel 945 Motherboard
2 GB RAM
Running Ubuntu Gusty and VirtualBox with XP for a few Windows only programs.

 Linux rules!

---

### Post by Yellow Pasque on 2008-01-03
Let me guess.. you were trying to install Compiz?

Regardless, press Ctrl+Alt+F1 to get back to the terminal. Now you can
```
sudo nano /etc/X11/xorg.conf
```
and change the driver line in the Device section to i810. Save. Reboot.

---

### Post by malibusurfer2 on 2008-01-06
No. I built a new computer and added a PCIe video card, had trouble with the card and am using the motherboard video. Got it to work again under my normal user setup, but when I boot into root, all I get is a blank white screen.

Thanks for the assistance. I will give it a hardy linux try.

---

### Post by xeth_delta on 2008-01-06
> **malibusurfer2 said:**
> No. I built a new computer and added a PCIe video card, had trouble with the card and am using the motherboard video. Got it to work again under my normal user setup, but when I boot into root, all I get is a blank white screen.

Thanks for the assistance. I will give it a hardy linux try.

Just out of curiousity, why are you trying to log-in as root? You can run programs/commands with temporary root privileges using:
```
sudo your_command
```

Xeth

---

### Post by Yellow Pasque on 2008-01-06
The driver isn't going to change according to which user you are. I'm sorry; I misunderstood your question. What do you mean by "booting into root". The GNOME login manager shouldn't let you login as root.

Please elaborate.

---

### Post by xeth_delta on 2008-01-06
> **Temüjin said:**
> The driver isn't going to change according to which user you are. I'm sorry; I misunderstood your question. What do you mean by "booting into root". The GNOME login manager shouldn't let you login as root.

Please elaborate.

Temüjin is right, I think that's the reason why you are sent back to the log-in screen. For security reasons the root accout is disabled by default in Ubuntu. To run commands with temporary administrative purposes, you can run the commands as stated in my previous post.

---

