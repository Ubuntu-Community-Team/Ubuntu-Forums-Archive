---
title: "Executing zenity remotely from Ubuntu on Windows"
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by xanaftp on 2010-12-04
Hello... here's my situation:

We have three computers on our network, a desktop, and two laptops. The desktop and one of the laptops contain Ubuntu, whilst the other laptop contains Windows 7.

My goal is to get, through SSH, all of the computers to be able to display message boxes remotely... aka:

If I am on the desktop Ubuntu, and I want to display a message box on the Ubuntu laptop, I'll connect via. SSH using a client on the desktop, and a server on the laptop, then enter "export DISPLAY=:0.0", then enter my zenity command. Bingo! The message box shows up on the laptop.

The same thing was tested vice-versa... a client on the laptop and a server on the desktop. BAM! Works!

I have also tested it using a client on the Windows laptop and a server on either the other laptop or the desktop. BAM! Works!

HOWEVER...

Here's the problem: I have mobaSSH AND zenity windows edition installed on the Windows computer. When I connect to it from the Ubuntu Desktop computer I get a linux-like terminal. I type "cmd.exe" to access the windows terminal. Now, when I type in zenity commands, it says it is not recognized, when both the Ubuntu Desktop computer AND the windows computer BOTH have zenity installed! I have also tried navigating the windows terminal to the zenity.exe executable but it gives me a gtk error.

Other things I've tried: winSSHd on the Windows computer, but when I use the zenity command, nothing happens. No output on the terminal, and no message on the Windows laptop.

So simply put: I'm trying to get a message box to pop up on the Windows computer using zenity from any of the two Ubuntu computers via. SSH.

Help would greatly be appreciated.
Thanks!

---

