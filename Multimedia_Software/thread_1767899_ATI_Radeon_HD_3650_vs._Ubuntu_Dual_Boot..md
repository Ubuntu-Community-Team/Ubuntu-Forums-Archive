---
title: "ATI Radeon HD 3650 vs. Ubuntu Dual Boot."
date: 2011-05-26
forum: Multimedia Software
---

### Post by DeamonZA on 2011-05-26
I have recently installed Ubuntu 11.04 as a dual boot on a Lenovo T500 already running Windows XP Pro SP3.
The install went fine and Ubuntu seems to run the graphics without a hitch, the problem comes when I shut Ubuntu down to run XP, the ATI graphic drivers have all been removed and I have to re-install the ATI graphics card using the self-installer package (.EXE) and then restart the laptop to get the graphics running.
 
I have checked this on another computer (same model) and the same problem comes up.
 
I have given Ubuntu full HD access to all document and folders on the entire Hardisk so is there an issue where Ubuntu is changing the driver or program files during it's start-up and shut-down sequences ? If so, is there a fix ???

---

### Post by Joe of loath on 2011-05-26
Ubuntu shouldn't be affecting drivers installed in Windows. Are you sure it's not a Windows driver bug?

---

### Post by samysamy on 2011-06-28
Hello I have related issues. My graphics driver is not installed properly in Ubuntu, so every time there is an error. I have to log into windows, reboot, and enter normally to Ubuntu. I am using Lenovo T500 (ATI HD3650) windows XP and Ubuntu 11.04. It is 64 bits version. Basically, I want to install correctly the driver... any suggestion? I have tried many options the update manager, but it is the same. Using the utility to install the driver is failing when it tries to install.
Thank you!

---

### Post by dave2001 on 2013-02-23
My guess is that your problems are caused by your lappy having TWO video cards. Your laptop offers support to the OS for switching video card "on the fly".. ATI card for heavy graphics, intel onboard for battery life. Unfortunately ubuntu doesn't do well with this. 

Going into the bios and picking only one card to activate, rather than leaving it on some kind of "auto choose" behavior, may help your problems.

---

