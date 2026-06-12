---
title: "New build advice"
date: 2012-03-05
forum: Mythbuntu
---

### Post by Chris Musampa on 2012-03-05
Hi all,
Time to replace the old box in the corner, it's about 10 years old, Athlon XP2400, 1GB RAM, a couple of old IDE drives and some old pre-pre-pre-vdpau Nvidia card.  TV card is a Nova TD-500 PCI card (which I want to transfer to the new box).  It runs Mythbuntu 9.10 as a BE+FE and also feeds my laptop FE.  It's also used as a NFS fileserver and torrent downloader (using RTorrent under Screen).  I occasionally use it to watch sopcast streams.

I want a quiet (doesn't have to be silent) mid range replacement  to take over the above tasks as well as the odd bit of VirtualBox use.   I'll hopefully not have to worry about replacing for another 10 years! :D

I've spent a good while googling for possible issues and arrived at the following choices:

Gigabyte GA-Z68XP-UD3 Intel Z68 (REV B3) Socket 1155 DDR3 PCI-Express Motherboard
£107.04
As far as I can tell I'll just need to replace the default network driver, seems fairly straightforward.


Intel Core i5-2300 2.80GHz (Sandybridge) Socket LGA1155 Processor - Retail
£137.80
Should be pretty relaxed with these tasks I think.


8GB GEIL EVO TWO (2x4GB) DDR3 2133MHz 10-11-11-30 Dual Channel kit - GET38GB2133C10ADC
£66.65


Asus Nvidia GeForce GT 430 Graphics Card (1GB DDR3, HDMI, DirectX 11, Nvidia PhysX Technology)
£44.38
OK for VDPAU, sound+video through HDMI connection to LG TV?


1TB Seagate Barracuda 3.5" SATA III Internal Hard Drive [ST31000524AS]
£82.50
Will probably add a smaller drive for OS.


Case???
Not too fussy about the case, box lives in a corner behind the TV,will have a look while in the shop.  

PSU??
Was going to ask about suitable PSU also while in the shop.


I could probably save a few quid buying on line but I'm a bit old fashioned and prefer to be able to rant at someone face to face in the event of a problem :D


I'd like this build to work with Mythbuntu without having to jump through too many hoops and I welcome any advice.

Thanks

---

### Post by Chris Musampa on 2012-03-07
Nobody any experience of this motherboard or chipset?

---

### Post by nickrout on 2012-03-07
i know nothing about that board and motherboards go in and out of production too regularly to keep up. Make sure it has enough slots for your planned tuners.

Your processor and graphics card look fine.

---

### Post by LowSky on 2012-03-08
looks like a sound system. If you want to save some cash get an i3 and use only 4Gb of RAM, if the PC is just going to be for recording TV and spend the saved cash on a larger hard drive. My experience is that I eat up space recording High definition video.

---

### Post by Chris Musampa on 2012-03-08
Thanks for your input.

No immediate plans for more tuners than the TD500 though the board has spare slots available.

I was torn between I3 and I5 but, as I say, I hope this box should last for a few years so I thought it better to have what (currently) seems plenty of power in reserve.

Storagewise, I think I'll probably buy a smaller drive to put the OS on (partitioned to allow for 2 or 3 installs).  I don't currently have HD recording ability, nor do I tend to store tons of media (maybe music, but not TV / video as I tend to watch and delete) so should be OK for a while.

I intend to buy the parts tomorrow so assuming everything works the next question is about the database: Ideally I'd like the new system to know my recording schedules and recording history, is that possible going from such an old version of myth?

---

### Post by nickrout on 2012-03-08
> **Chris Musampa said:**
> Thanks for your input.

No immediate plans for more tuners than the TD500 though the board has spare slots available.

I was torn between I3 and I5 but, as I say, I hope this box should last for a few years so I thought it better to have what (currently) seems plenty of power in reserve.

Storagewise, I think I'll probably buy a smaller drive to put the OS on (partitioned to allow for 2 or 3 installs).  I don't currently have HD recording ability, nor do I tend to store tons of media (maybe music, but not TV / video as I tend to watch and delete) so should be OK for a while.

I intend to buy the parts tomorrow so assuming everything works the next question is about the database: Ideally I'd like the new system to know my recording schedules and recording history, is that possible going from such an old version of myth?

Back up your database using the backup/restore tool and restore it to the new system.

[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

---

### Post by Chris Musampa on 2012-03-08
> **nickrout said:**
> Back up your database using the backup/restore tool and restore it to the new system.

[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

I'd assumed my ancient myth version (have never used anything other than the default 9.10 repos) would be a problem, having read that page sounds like it should be fine, here's hoping.

Cheers.

---

### Post by nickrout on 2012-03-08
> **Chris Musampa said:**
> I'd assumed my ancient myth version (have never used anything other than the default 9.10 repos) would be a problem, having read that page sounds like it should be fine, here's hoping.

Cheers.

You have never said which version of myth you are running, but it should be fine.

---

### Post by crbnrod on 2012-03-08
I have the GT430 video card & have been very pleased with it. It allegedly will give you sound over HDMI but I'm running an old version of myth/ubuntu that I don't think handles that kinda stuff (probably upgrading to the new LTS in a few mos).
If you're doing HD and don't religiously keep up w/your shows, 1 TB might start to get a little cramped. Depends on your habits.

---

### Post by Basher101 on 2012-03-08
you asked about the chipset, well i use this Z68 motherboard for 4 months now and it works like a charm. I only had some minor issues with the graphics card which resolved after some driver updates. i5 CPUs are great^^

regards

edit: the only thing that does not work currently is Lucid Virtu as it is only supported in windows (using both GPUs of your i5 and the discrete graphics card). I usually just stick with the onboard GPU of the i5 when using ubuntu to save power as demanding games do not run (like skyrim..)

---

### Post by Chris Musampa on 2012-03-09
@Nickrout, not sure which version of myth I have but its whatever version Karmic has.




> **Basher101 said:**
> you asked about the chipset, well i use this Z68 motherboard for 4 months now and it works like a charm. I only had some minor issues with the graphics card which resolved after some driver updates. i5 CPUs are great^^

regards

edit: the only thing that does not work currently is Lucid Virtu as it is only supported in windows (using both GPUs of your i5 and the discrete graphics card). I usually just stick with the onboard GPU of the i5 when using ubuntu to save power as demanding games do not run (like skyrim..)

Thanks Basher.

Can't see the lucid thing being a problem as I understand it as I don't intend using the integrated graphics at all.  Good to hear positive experience with Z68.

---

### Post by newlinux on 2012-03-09
I've had a z68 motherboard for a few months now and it has been rock solid with my core i7 processor (see my sig for my hardware). IF you are going to do virtualization you might want to consider still getting 8GB of RAM. It really depends on how much virtualization you are going to want to do, and how you want your VMs configured...

---

### Post by Chris Musampa on 2012-03-10
> **newlinux said:**
> I've had a z68 motherboard for a few months now and it has been rock solid with my core i7 processor (see my sig for my hardware). IF you are going to do virtualization you might want to consider still getting 8GB of RAM. It really depends on how much virtualization you are going to want to do, and how you want your VMs configured...

It's not something I do much of but of but I went for 8G anyway.

Got the box built yesterday.  Failed to get Mythbuntu live cds (tried 11:10 and 10:04, both gave errors during live boot even though I'd checked MD5SUMs) to install but managed to install Ubuntu 10:04 and ran updates.  From there I installed MCC and set the machine as primary BE + FE (though no tuner installed yet).  Got some error about the wrong database schema, seems a bit strange since it is the database it created (no attempt at importing yet), maybe I should've installed and run MCC before updating Ubuntu?.

Had to leave it there and probably won't get back on to it until tomorrow, no doubt I'll be back with more questions.

---

