---
title: "Jaunty Install Flawed - Reinstalled Intrepid"
date: 2009-05-11
forum: Mythbuntu
---

### Post by Chuckels550 on 2009-05-11
I have given up on Mythbuntu 9.04 AMD64 and gone back to Mythbuntu 8.10 AMD64.  How easy the install and configuration went for the re-install of Mythbuntu 8.10 has made me realize that something is seriously flawed in the Mythbuntu 9.04 AMD64upgrade and install.  

Duo Core 6300 CPU 
2GB PC6400 RAM
MSI Intel P45 NEO3-F(MS-7514) Mainboard
Seasonic S12 Energy Plus (80 Plus) 550 W PSU
Hard drives
- ATA 133 Maxtor 250 GB 16 MB Buffer
- ATA 133 Western Digital 320GB 16MB Buffer
- SATA II Western Digital 750 GB 16 MB Buffer
- SATA II Samsung Spinpoint 1TB 32 MB Buffer
Creative Labs Soundblaster Audigy X-Gamer Soundcard
Asus Nvidia EN9600GT Silent Graphics card
Dlink DWL-G520 Wireless NIC (Atheros)
Hauppauge WinTV PVR 350 and 150 TV Tuners

I started by trying to use the upgrade function in the Mythbuntu 8.10 Upgrade Manager.  The modprobe function was broken so I couldn't fix the initial configuration of my wireless NIC.  A bogus modprobe.conf file in the /etc directory stopped modprobe command from working.  So I gave up on the upgrade.

I used a Mythbuntu 9.04 AMD64 install CD and tried to run the install.  The install failed so often that the install took 12 hours to complete.  The bogus modprobe.conf file was still there, but I didn't need to invoke modprobe.  I was able to install wicd and configure the wireless NIC and take down the temporary wired connection.  I set up the restricted nvidia graphics driver to run the system at 1080i.  I was able to use the Update Manager.  All went well until I rebooted.  From that point on the system would seize up after running three or four minutes so that I could only use a hard reset.  I looked in the syslog files, but couldn't see a problem.  I went into recovery mode and used the autofix graphics option - nothing worked.

I reinstalled Mythbuntu 8.10 and completed the install as well as the configuration in two or three hours.

---

