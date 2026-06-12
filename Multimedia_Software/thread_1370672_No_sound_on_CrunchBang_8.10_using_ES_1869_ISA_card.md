---
title: "No sound on CrunchBang 8.10 using ES 1869 ISA card"
date: 2010-01-02
forum: Multimedia Software
---

### Post by FactTech on 2010-01-02
I ran into this issue while setting up a Compaq DeskPro SB PD1000 Series computer, using CrunchBang Lite 8.10 as the OS. After some diagnosis, I'm reasonably certain that the issue is something that would affect all Ubuntu variations, so I marked this thread that way.

The issue is that the sound was not working. Since the sound card on this machine was an old ISA PNP (plug-and-play) card, I assume it was just not detected automatically.

The output of command 'lsmod' showed no sound modules were loaded, so I figured that loading the correct driver would solve the issue. Command 'lspci' didn't show the card (because it's ISA), so I installed the 'pnputils' package ('sudo apt-get install pnputils') and looked at the output of command 'lspnp -v'.

The lspnp output showed a card was present but not active, and identified it as an ESS1869. There's an appropriate ALSA module called 'snd-es18xx', so I loaded that using 'sudo modprobe snd-es18xx' -- since the driver is plug-and-play compatible, no further options should be needed.

The module loaded fine, and 'lspnp -v' now shows the card is active. Also, the output of 'aplay -l' shows a card is seen -- 'ESS AudioDrive ES1869', which appears to be the correct hardware. However, I still get no sound, and trying to launch 'alsamixer' returns an error message about the default device not being present. I'm not sure what to do from here out. Any hints?

---

### Post by FactTech on 2010-01-02
SOLVED

I was close to having solved it already, but a nice person on the Ubuntu IRC channel (DasEi) walked me through some basic troubleshooting and pointed me to a web page that said to check and make sure the active user was a member of group 'sound'.

I checked the contents of /etc/group ('cat /etc/group | more'). There was no group called 'sound', but there was one called 'audio'. Checking my own groups with command 'groups' indicated I wasn't a member.

I added myself to the audio group with command 'sudo adduser <myusername> audio' (anyone following along with the same issue will want to replace '<myusername>' with their own username -- leaving out the <> angle brackets) and logged out and back in to confirm my membership with 'groups'.

I think at this point 'alsamixer' started working as expected, but I can't remember for sure. At any rate, I knew the setup was working, so I added a line with 'snd-es18xx' at the bottom of file /etc/modules ('sudo nano /etc/modules'), rebooted, and now everything works fine.

I'll probably have to add any new users to the 'audio' group manually, but I can live with that.

Thanks to DasEi for the help!

---

