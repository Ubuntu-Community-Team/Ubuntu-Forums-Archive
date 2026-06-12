---
title: "Ubuntu 10.04 interferes on windows' wifi?"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by yuukosakura on 2010-08-10
Hello to everybody,

I don't know if I'm in the correct place, but this is the place that I think best fits my doubt.

Until yesterday everything was ok on my 2 OS (win vista and ubuntu 10.04). Today I plugged a cable to activate wireless in ubuntu, and really activated. However, when I went work on win vista, the wifi in vista was not detecting anything. To check if my wireless board was working properly, I returned to ubuntu, and the connection was ok! I installed a wifi manager in win, and the program said it was disabled. I already checked all the buttons and everything is enabled. Someone could tell me if ubuntu 10.04 is affecting/disabling wireless on windows?

Sorry if I'm being repetitive, but most of the topics I've seen around here and (almost all) google were from people asking for help for bad-wifi in linux, and my case is the opposite. I know that here is a community of Ubuntu, but many people have dual boot, and I have hope that someone may have had the same problem (solved) to help me.

thanx for the patience, and sorry my bad english. ;)

[]'s

---

### Post by bergfly on 2010-08-10
The first place to look would be in BIOS. When your machine starts to boot, you need to press either DEL or F2 (or other option depending on the machine). This will take you into BIOS and allow you to check on the status of the Wifi card. There is normally an option in there you can change to tell the machine what to do with wifi at boot. Make sure it says enabled at boot in BIOS and then try in windows.

---

### Post by yuukosakura on 2010-08-11
> **bergfly said:**
> The first place to look would be in BIOS. When your machine starts to boot, you need to press either DEL or F2 (or other option depending on the machine). This will take you into BIOS and allow you to check on the status of the Wifi card. There is normally an option in there you can change to tell the machine what to do with wifi at boot. Make sure it says enabled at boot in BIOS and then try in windows.

Hi bergfly,

Thank you for your help!
The wifi status is "enable" in BIOS! Even though, the wifi didn't work on win!

But, I believe that I could solve the problem. I simply turned off the pc and when I turned on again, everything worked fine! I know... shame on me! sorry! :oops:

Apparently happened the following: I installed the wifi on ubuntu and restarted the pc, it didn't work on Win! Even turning off the wifi button and disabling the wifi (by strength), in a Dell's specific program, and turnin on (again), nothing happened (on win). But in linux everything was fine! But, at first, to "fix" it need to turning on and off the pc when you want to switch OS. Well, it works for me! :KS

Again, thank you very much for your help and patience. I really appreciate! ;)

[]'s

---

