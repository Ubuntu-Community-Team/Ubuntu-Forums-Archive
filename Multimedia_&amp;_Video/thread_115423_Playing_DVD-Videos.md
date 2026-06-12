---
title: "Playing DVD-Videos"
date: 2006-01-10
forum: Multimedia &amp; Video
---

### Post by John Dooley on 2006-01-10
I wanted to play a DVD-Video (The kind you buy from Best Buy) and had all kinds of trouble. After a day of struggle and confusion I found the simple answer. Along the way I saw some forum entries that suggested that other might be having the same problem. 

When trying to play my DVD I got messages :
  "... no decoders found to handle the stream.."
  "... install the corresponding plugins..."
  
Some times I would see totem quit or my system lock up as I tried all the combinations of stuff suggested in this forum.

I saw reference to totem-xine, but there was no evidence of it in synaptic.

The solution was calling up Help on my system and the navigating to Ubuntu 5.10 Starter Guide|Applications|Music+Movies and following the instructions.
I also learned here to use synaptic to list the multiverse and universe package.

My DVD-Video s run great now.

While I was struggling with the problem I wondered if the were any utliites that would dump the .ifo/.bup and give some information about the .vob files. I could hex dump the .ifo and .bup files but don't know the format. The .vob are too big to dump but a utility to dump a summary (after decrypting) might be useful.

Is there a way to have totem list its plugs (like firefox plugins:)?
Can anyone point to documents, utilites, or any other useful information?

---

### Post by oldlag on 2006-01-10
John, I tried following the Help instructions and they worked for the DVD stuff except for "regionset" which the error message said it couldn't find. Similarly it couldn't find the gstreamer0.8-mad or gstreamer0.8-plugins packages. Any ideas?
Thanks Dave

---

### Post by John Dooley on 2006-01-10
Dave,

When I read the instructions, there was a link to expanding Synaptic repositories to include the MultiVerse and Universe. After following these instructions the synaptic sidebar conating sections should contain new sections. For example, instead of having just a Libraries section you would also see Libraries(multiverse) and Libraries(universe). It sounds that you need to get to this step first - see the (multiverse) and (universe) section entries in the synaptic display. You can then do a search for regionset, gstreamer0.8-map, etc and find them. 

The gstreamer0.8-mapd and gstreamer0.8-plugins packages you mentioned are in Libraries(universe). When I hit apply in synaptic about 53 packages were installed (and one was removed- maybe regionset?). 

BTW I used regionset to change my region code from 0 to 1. However,afterwards I noticed that my DVD jacket said that they were for world code (0). I am not sure what effect changing the region code had. Since it works I don't want to mess with it since the DVD firmware can lock ou out after 4 changes(if I understand what I read correctly).

John

---

### Post by oldlag on 2006-01-10
Hi John, thanks for the reply. I had figured out that I missed following a few steps in the instructions. When I went back I found out what you describe and re-did everything and all worked. Didn't need to use the regionset, it played Region 1 straight away. The only problem that I had was with DMA on the DVD drive which was not set ON at start up. I followed the instructions to change it and the jerky video went away. I have edited the conf file so that dma is ON at start up. However, when I type in:
sudo hdparm /dev/hdc
at the end of what comes back it says:
HDIO_GETGEO failed: Invalid argument

Any idea what that's all about?

Thanks, Dave

---

### Post by StefanoCole on 2006-01-11
oldlag, HDIO_GETGEO returns the media (in this case the disc) geometry. Since no disc was inserted it returned HDIO_GETGEO failed: Invalid argument.
If you hard disc is /dev/hda you can type "sudo hdparm /dev/hda" and see the hard disc geometry.

Stefano

---

### Post by oldlag on 2006-01-11
Stefano, many thanks for the explanation.
Dave

---

### Post by John Dooley on 2006-01-11
My DVD-Video is jerky too. After looking around the forum, the most often suggested remedy is to turn on DMA. After doing some further research, there may be more too it than that. I don't have any definitive answers yet but I have collected a little bit of information. It will be the weekend before I can do the deeper digging.

  o The distrtutions typically set  things up conservatively, so that things won't blow up on event the weirdest configurations.

  o The Linux Trubleshhooting Bible by Christopher Negus and Thomas Weeks has ten pages dedicated to tweaking disk performance. I visited book store and looked thru all the books and this was the most complete. I do not own the book and was not able to take notes. I plan to look on the web for compareable information, or if that a falis, take notes at B&N, or, at last resort buy it.

  o the HDIO_GETGEO - gets the geometry, probably from /proc/ide/ide0/hda/geometry for the hard disk. On my system there is no /proc/ide/ide1/hdc/geometry even when the DVD is in place. The geometry concept concerns heads and platters and may be non-standardized or irrelevant to a DVD. On the other hand, DVDs can be 1 or two sided so may be its a bug.

 o sudo hdparm -tT /dev/cdrom0 can be used to determine the performance. This is useful to see the results of any tweaks, like turning on DMA or changing the io_support mode.

 o sudo hdparm -i /dev/cdrom0 and sudo -I /dev/cdrom0 displays lots of information about the DVD and I am still trying to grok all it is trying to tell.

 o io_support. This is set to zero on my system. I think it means that the IO width is 16 bits. Setting it to 3 (I read somewhere, whats 1 and 2?) increases the transfer width to 32 bits. This should increase perfomance even without DMA being turned on(and maybe safer on some systems- i see many complaints about DMA online). If the device driver writter reasoned that 32-bits transfer would be turned on before DMA, then turning on DMA without maximum io_support might select a weak path in the driver. This is pure speculation, but it is possibilties like this that suggest taking a systematic approach.

Hopefully, by Saturday morning someone has figured it all out so I can spend my weekend programming Python. Otherwise,...

---

### Post by John Dooley on 2006-01-11
Looks like I can spend Saurday with Python.

I searched for disk performance on google.com/linux and the first thing that came up told all I needed to get my DVD-Video non-jerky. The author calls himself Piter Punk.

io_support means: 0 - 16-bit, 1 - 32 bit, 3- 32 bit sync. There is also a 32-bit async and maybe thats 2 - but I don't know.

sudo hdparm -tT /dev/hdc gave me : cached read =1105 MBS and bufered read = 2.47 MBS

sudo hdparm -c3 /dev/hdc puts the system in io_support mode 3 until reboot.

With this set I ran sudo hdparm -tT /dev/hdc and got: cached = 1110 MBS and buffered = 3.41 MBS. This was a lot smoother.

I also set ultra DMA 2 on (see Piter Punk, above) with sudo hdparm -X 66 /dev/hdc and got no real difference with hdparm -tT but decided to leave it on, anyway.

I used hdparm -i /dev/hdc to find out the driver DMA mode (its the one with the * according to Piter Punk).

When running the tests the DVD should be in the drive but not mounted. If if is playing the buffered read goes down to a very low number. This method of using hdparm to set parameters and see how the numbers change worked well.

I think that I can make the above changes permanent by using the hdparm -k parameter which probably just updates /etc/hdparm.conf.This is probably safer than editing the file with an editor. I will probably run this way for a few days to see if anything hangs. If I forget, the jerkiness will come back and that will remind me.

 I have a NEC DVD - 8500A on my Dell Precision 340 (1.7GHZ). I bought this as a refurbisehd system back in 2002 (old technology). I will probably need to upgrade the DVD to get better performance. However, perhaps someone will find another trick?

---

### Post by oldlag on 2006-01-11
Turning on DMA appears to have cured my jerky problem without any other ill effects. Regarding IO_support, mine is set to 1 which it says is 32-bit.

---

### Post by John Dooley on 2006-01-11
I am not sure what the difference between 1 and 3 are except for the names: 32 bit vs 32-bit sync. 1 is 32 bit and 3 is 32 bit sync. I am guessing the highest number is most desirable, but that has little rational basis.

When I ran my test with sudo hdparm -X 66 /dev/cdrom0 that was not a replacement for doing a sudo hdparm -d 1 /dev/hdc. That is why I saw no impovement - both DMA enabled and the type of DMA (-X 66) had to be set at the same time. I corrected this error and reran and saw a great improvement.

With my ultra DMA mode really enabled I my buffered reads shot up from 3.4 to 6.8 MBS as measured by hdparm -tT. Now the movement is extermely smooth with a real DVD-Video.

Here is a recap:

sudo hdparm -c3 /dev/hdc
sudo hdparm -d1 /dev/hdc
sudo hdparm -X66 /dev/hdc

sudo hdparm -tT /dev/hdc gives buffered reads of 6.28 MBS up from 2.47 MBS without the changes. I think this must be near the capacity for my old hardware.

sudo hdparm -i /dev/hdc told me that udma2 was available (*) and the DTR (data transfer rate?) is between 10 MBS and 10MBS, I think. The notation is a bit funny.

sudo cat /proc/ide/ide1/hdc/settings told me that io_32bit was available with a range of 0 thru 3. I assume this is the same as io_support in hdparm /dev/hdc.

With these commands and the Piter Punk's disk performance document found on [www.google.com/linux](www.google.com/linux), hdparm settings can be checked per hardware configuration.

Of course, the above settings only lasts to the next reboot which is good if there are any problems down the line. If the system hangs up, the orgional, conservative settings will be restored on reboot. 

In a week or so I will try making the settings with hdparm's -k parm to see if that really updates /etc/hdparm.conf like I suspect. 

I would really like to know if the DTR in the hdparm -i is really data transfer rate and under waht circumstances it reaches the max?

---

### Post by John Dooley on 2006-01-14
This[link]("http://www.linuxdevcenter.com/pub/a/linux/excerpt/pchacks_50_67/") is an exerpt from a book called PC Hacks by Jim Aspinwall that shows how to set the io_support, DMA, etc. to increase hard disk performance. It is similar to what was written above but its it may be comforting to see it from another source.

Remember that this stuff will also speed up your harddrive as well as eliminate the jitters from your DVD playback. My laptop runs at 700MHZ and was slow starting ubuntu help and office and since setting io_status and the DMA settings things are faster and much more bearable. My 1.7GHZ is positively snappy after the change.

If you search on google.com/linux for hdparm flickenger, this brings up another good explaination with some of the reason why distributions are made with slow hdaparm settings. This artical is called "Speeding up Linux Using hdparm" and was written in 2000.

---

