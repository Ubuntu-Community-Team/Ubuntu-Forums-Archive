---
title: "Wireless Problems"
date: 2013-04-26
forum: Networking &amp; Wireless
---

### Post by LinuxPhenox on 2013-04-26
I just installed Ubuntu Server 12.04 LTS on my computer hoping to turn it into a home server. I have just found out that it doesn't want to accept my network adapter (Belkin Model:F7D1101 v1) wireless adapter but it doesn't want to use it. So i tried to use an ethernet cable and it won't accept that either. I don't have a disk for the usb adapter and i don't know if i need an adapter for an ethernet port that is built into my motherboard. But if anyone has any ideas on what to do i would greatly appreciate it. I am on the shell so if anyone knows how to get a gui on it without network access that would help me too since i don't know that much about the command line. I literlly know only enough to install something from a repository, and get the IP address.

---

### Post by Compynerd255 on 2013-04-26
OK, so I'd like to clarify: what exactly do you mean by "won't accept"? Do you mean that you don't get Internet no matter which of these devices you use? How do you know that you don't have Internet?

I'm a little new to Linux as well, but I have picked up some tips about working with the command line and troubleshooting with it. I myself don't know how to get a gui on Ubuntu Server, but you would tend to operate that system from the command line. Here's some hints I can give:
- The man pages are your friends. Use "man x" where "x" is some command you want to look up to view some information about what it is and how to use it.
- Additionally, most programs accept "--help" as an argument to get help on command line usage
- "help" gives some commands relating to the shell itself, which you can use to navigate and modify files
- "lspci" and "lsusb" list pci and usb devices, respectively.

---

### Post by LinuxPhenox on 2013-04-26
> **Compynerd255 said:**
> OK, so I'd like to clarify: what exactly do you mean by "won't accept"? Do you mean that you don't get Internet no matter which of these devices you use? How do you know that you don't have Internet?

Yes, and i know this because i tried to install a GUI from an external repository and it couldn't find the file, or repo, i was talking about. and when i did the command ifconfig to find my ip address it gave me a redirect address as my ip. i asked my dad and he said that that ment i didn't have an internet connection. the ip it gave me was 127.0.0.1.

---

### Post by Compynerd255 on 2013-05-02
And you did "ifconfig" with all configurations, including Ethernet? And you should note that there are several networking interfaces, not just one. If *any one* of them displays an "inet addr" as something other than 127.0.0.1 (localhost), you have Internet. And if you don't have Ethernet support, that's a serious problem.

---

