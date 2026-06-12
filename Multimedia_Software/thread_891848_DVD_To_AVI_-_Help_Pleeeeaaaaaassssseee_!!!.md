---
title: "DVD To AVI - Help Pleeeeaaaaaassssseee !!!"
date: 2008-08-16
forum: Multimedia Software
---

### Post by bipolaric on 2008-08-16
hi people, I want to back-up my DVD collection to my Hard Drive (avi format), but I don't know what program to use, or how to do it.  I am a linux virgin, so any help would be greatly appreciated.  I would also like to note that some of my DVD's have "forced subtitles" in them, is there anything I can do to have them included in the film once ripped.

Many Thanks - Mark

---

### Post by freddyg on 2008-08-16
Hey bipolaric, 
i use acidrip as an interface for mencoder, it seems the easiest to use and setup to me. others will have other suggestions, and all are valid. make sure your restricted repositories are enabled and installing acidrip should get you most of the way there as far as installing. Using acidrip is kind of an art from a configuration standpoint. play with it and ask questions, you'll be up in no time.

---

### Post by strick242 on 2008-08-16
I'll second acidrip!  I tried to use others, but have poor results.  To get it use Synaptic Package Manager or type this in terminal:
sudo apt-get install acidrip

---

### Post by hvthao on 2008-08-17
dvdrip and ogmrip also work great! Especially, ogmrip can make the h264 format.

---

### Post by araz_233 on 2008-08-28
I've got a kinda strange problem with Acidrip when trying to rip DVDs which have been copied to hard disk. Giving files path and trying to load them I get this message:
AcidRip message - Reading DVD / file(s)... please wait
AcidRip message - No valid files found.

though I think lsdvd works just fine. Here is the output:
[I]
Couldn't read enough bytes for title.
Disc Title: unknown
Title: 01, Length: 00:00:16.280 Chapters: 02, Cells: 02, Audio streams: 08, Subpictures: 32

Title: 02, Length: 01:45:55.080 Chapters: 17, Cells: 17, Audio streams: 03, Subpictures: 00

Title: 03, Length: 00:26:54.360 Chapters: 04, Cells: 04, Audio streams: 01, Subpictures: 00

Title: 04, Length: 00:00:08.000 Chapters: 01, Cells: 01, Audio streams: 01, Subpictures: 00

Title: 05, Length: 00:00:46.240 Chapters: 02, Cells: 02, Audio streams: 01, Subpictures: 00

Title: 06, Length: 00:00:45.240 Chapters: 02, Cells: 02, Audio streams: 01, Subpictures: 00

Longest track: 02
[/I]

Do you think not being able to read disk title would be the cause?

I've tried dvd::rip before that. Though it loads DVD contents and rips vob files, transcode failed each time with some reason and hung up in the middle of the process and I couldn't find out what was the problem.

---

### Post by djRobbieF on 2008-08-29
The best solution for ripping DVD on Ubuntu is handbrake

I've done tutorials on using it, if you want help.

---

### Post by thebigfatgeek on 2008-08-31
Hello Mark

I have created a DVD::RIP PXE server that will create a cluster from a bunch of machines to do what you are intending to do quickly and easily. I have written a HOWTO if people are interested in it, which should take less than an hour to configure the first time around, and less than 5 minutes after that.

My cluster consists currently of 7 machines, one master (AMD 64 Dual Core, 512mb ram, 2 x Gb Ethernet cards, HDD and DVD-RW) and 6 nodes (AMD 64 Dual Core, 1280Mb Ram, No HDD, no DVD, PXE Ethernet card) and I am able to rip at 70fps per machine, all on a Belkin gigabit switch. A 2h30min DVD transcode in 55 minutes, and a 90min movie in 26 minutes.

The system can probably go quicker if my network could be improved, as that is my major bottleneck at present.

The beauty of the systems is that can PXE boot any machine (even windows machines etc, with existing operating systems) and they will mount an NFS drive on the main RIP server and act as a node without any impact on their operating systems. Any server administrators with nothing to do on nightshift with a couple hundred CPU's and a nice network can now rip dvd's at the speed of light!!

You can of course just transcode on the main machine if you do not yet have any spare machines, and just add them later. Let me know if there are any interest

---

