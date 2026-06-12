---
title: "Network printer woes"
date: 2012-08-06
forum: Networking &amp; Wireless
---

### Post by paul1945 on 2012-08-06
I am fairly new to Ubuntu and have been trying to automate printing to my network printer, but am not sure where to start.
The program I am using is an old business program that is written in xBase; it produces raw print files of various names with a .prn suffix, as output.
The program locks up in DosEmu and has other problems there, but works fine under DosBox.
So far I have written a small file xbaseprn.sh that gets the data to the printer fine and that contains the following lines:

#!/bin/bash
lp -d HP-LaserJet-m2727-MFP -l -r -o raw /home/paul/dosdrive/*.PRN

But this file has to be executed manually.
What I want to know is whether there is a way to get the Ubuntu printing system (Cups or whatever) to check regularly whether a .prn file exists and then print this automatically.
And if so, how to accomplish this.
One would expect that this is possible, as according to the doc this is precisely how the Ubuntu printing system works anyway; maybe I only have to send the files to a particular directory to accomplish this, or maybe it just requires editing some config file.
Any help would be greatly appreciated.

---

