---
title: "Dapper Drake and Prism GT/Prism Duette"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by Kathrin.Hoevelmanns on 2010-10-26
Greetings,

I installed Xubuntu 6 to my Fujitsu Lifebook (E Series) yesterday and wired LAN is doing fine. Unfortunately I'm completely clueless, but want to get wireless to work nonetheless*.*
I want to use a PCMCIA wireless card that's labeled "Toshiba projector", furthermore I find on it the specification IEEE 802.11g/b. Network-admin finds radio contact called eth1 and LAN that are around (even mine in particular), but only WEP is supported and my LAN is secured by WPA2. Hence I suppose I have to install a new driver for my card. (Am I right so far?)

Using lspci, I get the result 'Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)'.

iwconfig returns
eth1   IEEE 802.11b/g  Mode:Managed  Frequency:2.442 GHz
          Access Point: Not-Associated   Bit Rate:0 kb/s   Tx-Power=31 dBm
          Sensitivity=20/200
          Retry min limit:8   RTS thr:2347 B   Fragment thr:2346 B
          Link Quality:159  Signal level:0  Noise level:94
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I already installed ndiswrapper and ndisgtk, I also downloaded some random wlan drivers (net5211, netcw10, prisma00 and prismnic), but ndisgtk tells me that no associated Hardware is present.
And that's all I figured out by now. What should I do next? Any help is appreciated.
Thanks in advance, 

Kathrin

---

### Post by desnaike on 2010-10-26
Question why use xubuntu 6 it's 4 years old a version such as xubuntu 9.10 or 10.04 might see your wireless card without trouble.

---

### Post by Kathrin.Hoevelmanns on 2010-10-26
Because this Lifebook' processor is a Pentium II and has only 933mhz. I was afraid I would bring it to its knees by installing anything higher.

---

### Post by desnaike on 2010-10-26
Then I would recommend puppy linux [http://distrowatch.com/table.php?distribution=puppy](http://distrowatch.com/table.php?distribution=puppy)

they also have an ubuntu flavored distro. [http://puppylinux.org/main/Download%20Latest%20Release.htm](http://puppylinux.org/main/Download%20Latest%20Release.htm)

---

### Post by Kathrin.Hoevelmanns on 2010-10-28
Thanks for your advice! I like the idea of Puppy, so I tried Nearly Office Pup. I felt quite satisfied using the live CD, but after I installed it to a USB flash card I found out my notebook is not able to boot from USB and I got totally lost on trying to get GRUB to boot from there. (As mentioned before: I am quite clueless...) I'd like to keep Dapper installed just in case, so I suppose I have to edit Dapper's GRUB? If so: where do I find the concerned files and what should I do to them?

---

