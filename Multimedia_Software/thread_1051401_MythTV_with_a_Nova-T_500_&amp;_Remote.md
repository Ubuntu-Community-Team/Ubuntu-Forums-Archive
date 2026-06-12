---
title: "MythTV with a Nova-T 500 &amp; Remote"
date: 2009-01-26
forum: Multimedia Software
---

### Post by quagz1 on 2009-01-26
Hello,

This is just a quick note to let everyone know how I got my Nova-T 500 & remote to work properly and (more importantly) reliably, as I was getting I2C read errors in the kernel.

System:
-----------
Ubuntu 8.10, fully updated with Mythbuntu-desktop added.
512mb RAM (soon to be 1G)
200GB Hard Drive (will be upgraded if this system works)
AMD 3800X2
Gigabyte K8NF-9
DVD Drive
PCIe Nvidia 6600GT 128mb DDR2
1x Nova-t 500 w/ Hauppage USB remote (came with it in box)

Steps I took:
---------------
1. Install Ubuntu from regular CD (my download limit is 5GB so I bought a PC magazine which had an ISO) and get *all* the updates, especially kernel updates.

2. Enable Universe and Multiverse and apt-get install mythbuntu-desktop

3. Download proprietary video drivers, sound card drivers and test to make sure everything works as it should.

4. System -> Mythbuntu Control Centre -> Configure as Backend server

5. Re-compile the kernel with the latest V4L (search this on google - you do it using Mercurial) - I included experimental drivers "not compatible with this kernel version"

6. Add your video cards into Mythbuntu through the Backend configuration, ensuring you disable EIT. Follow the mythtv wiki for step by step instructions. [http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI)

7. Add two video sources (one for each card) and select No Grabber

8. Test your tuners to make sure you can watch TV

9. Go into myth control centre and add a remote - My Nova-T 500 came with a USB remote. After looking at the dmesg output it was a Philips remote. I selected Windows Media Centre - New (Philips et al.). Some buttons need tweaking but thats all easy once it actually works.

10. Reboot and test your remote - you might need to configure lirc more to get this to work properly.

11. Check dmesg output to see if you have any USB errors or I2C write errors - if you do then something is not right and you must go back and get the latest software/drivers/kernel and recompile.

12. Add Shepherd (google) which automatically populates your Program Guide.

13. Add other modules/tweak or in my case watch TV.

Notes:
----------------
The Nova-T 500 has great output quality and is pretty good in low sig. strength. All my channels are around 60% because I live with a huge hill between my and the TV transmitter. Make sure you enable the buggy_sfn for the ABC and low_noise_amplifier options in /etc/modprobe.d/options to get better signal strength.

If you are getting I2C read errors and are losing tuners you need to ensure you are using the latest V4L. I had the latest everything (except V4L) and was losing tuners & remote commands after about 5 mins - eventually lost everything USB.

You must disable EIT when adding the cards and also in the video sources - you wont need it because Shepard will do it for you. EIT is also known to cause some issues on the Nova-T 500 cards.

Why must you use V4L and Mercurial?? Lots of changes are made to V4L but they are not added to the standard V4L package upstream, I assume this is due to testing/QA. You have to download the changes and compile the modules yourself.

If you need any help getting your system working I will be happy to give advice - just reply here.

Sorry about the low quality post - I'm at work and in a rush.

Cheers,
:popcorn:
Sean

---

