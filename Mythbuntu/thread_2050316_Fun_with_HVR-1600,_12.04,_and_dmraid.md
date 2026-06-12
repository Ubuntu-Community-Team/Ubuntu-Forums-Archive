---
title: "Fun with HVR-1600, 12.04, and dmraid"
date: 2012-08-30
forum: Mythbuntu
---

### Post by eriktheblu on 2012-08-30
This is my second MythTV box and I'm reusing the Hauppauge WinTV HVR-1600. My goal is to record analog cable, and use as file server. 

My cable provider encrypts digital, so I was looking for analog signals. The analog side has some known issues with MythTV .24 and .25. The workaround seems to be upgrading from a prior version, which do not seem to be available in Precise. 

Easy enough I thought, I'll just use Lucid (still run it on my desktop) since it worked just fine for my last box. Go to install Lucid, and the HDDs are not recognized. Keep in mind I already have Precise installed on one of these HDDs.

More research shows me a bug involving dmraid from around 9.10 to 11.04 or so. I attempted to get around this with setting the boot option nodmraid. No change.
I tried dmraid -r -E /dev/sda Which returned something along the lines of the disk not existing. No change in installer.
Also removed dmraid and the dependent library in synaptic and with apt-get, disk still didn't show.
Also note that the disks are not available in Gparted, and do not appear in /dev.
I'm thinking that dmraid is not my bug.

Just for grins, I changed the BIOS behavior for HDDs from the default IDE to AHCI. The only result is that it then failed to boot from USB (tested on 10.04, 10.10, and 11.04)

I've tried 32 and 64 bit installs with the same result.

Copying files from my old machine is not an option as I no longer have a working MOBO that supports PATA.

My next move is to attempt to install Hardy, then dist-upgrade to Lucid. Failing that, an alternate distro (I am reluctant to learn a new distro)

If you made it this far, thanks for the consideration. If you have any ideas I am quite open.

---

### Post by klc5555 on 2012-08-30
That's quite a corner you seem to be painted into. What are you trying to end up with --a 10.04 installation or a 12.04 installation?

You tried an installation of 12.04 to confirm that your hardware is subject to the "HVR 1600 no /dev/videoX in mythtv-setup" bug? 

I don't think 8.04 yet included a working cx18 driver for the 1600. Or the conexant firmware either --I'm not certain. If you were to run 8.04 for the sake of configuring the Hauppauge 1600 prior to upgrading, you'd need at least to compile the cx18 driver from source from about July 2010 or newer to get it working well or at all (the cx18 in 10.04 also wasn't quite prime-time, but the analog part of it was sort of OK).

Now of course your new MOBO supports PATA --it just doesn't have a controller for it. To this end, for the sake of getting the mythconverg backup and whatever other files off the old drive you may want, it might be worth shelling out $10 for a used junk PCI IDE controller card or even $15 for a USB external IDE hard disk enclosure to access the data on the old drive. You could get your old 10.04 mythconverg backup off the drive, restore it to a brand-new 12.04 installation, and your 1600 analog would be usable once the old mythconverg was schema-upgraded.

---

### Post by eriktheblu on 2012-08-31
As will often happen with my gremlins, as soon as I bring them to someone else's attention it resolves itself.

Solution: needed to change signal type from bcast to cable in the general backend settings (or at least that's the only change I think I made). I had it to cable on the card settings, just not on general.

I now have playback on analog channels, and still configuring everything.

I'm actually quite indifferent to which version I use. So long as it records and replays, I would have been happy.

My plan with 8.04 was to work around the HDD not being recognized, and immediately dist-upgrade to 10.04. This plan of course failed, as 8.04 found it inconceivable that I would install from anything other than a CD-ROM, and refused to proceed when failed to detect the optical drive.

Even with a PATA controller, I would have had great difficulty locating the proper drive, then figure out which file(s) to copy. I was holding out for something easier.

I am still baffled by the installer(s) behavior with the HDDs. Same thing even happened with Mythdora.

Thanks for the interest.

---

