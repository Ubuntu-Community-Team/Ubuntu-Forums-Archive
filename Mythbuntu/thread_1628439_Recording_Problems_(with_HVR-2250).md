---
title: "Recording Problems (with HVR-2250?)"
date: 2010-11-22
forum: Mythbuntu
---

### Post by vanbob on 2010-11-22
This is my first Mythbuntu build, but I've been using Ubuntu for 5 years.  I'm having problems with recording programs:

1.  When a program is recording, if I try to watch a different channel on the other tuner (HVR-2250), all I can get is another broadcast on the same channel.  For example, if I'm recording on 2-1 and I try to switch to any other channel, the only one I can get is 2-2.  If I'm recording on 6-1 where there is no additional broadcast (like 6-2), then I can only watch 6-1.  If I stop the recording, I can switch and view any other channel normally.

2.  If I record a program (with and without watching anything), it seems to record okay; however, I usually get two entries on the Watch list where one works fine and the other doesn't.  I can't delete either through the frontend.  From reading similar posts, I've checked ownerships and permissions and I should be okay.

3.  In my frontend Recording list, I get a list of any program that I may have watched.  In fact, even if I am not watching but the backend was running, the program will show up one my Recordings list and I can watch it later.  They are not in the recordings directory, but is in the livetv directory.  I can't delete these through the frontend either.

4.  I haven't been able to record two programs at once, but I think that may be related to #1 above.

Another problem I've seen was excessive frame buffer errors.  I think I might have resolved this by upping the DVB tuning delay as suggested in another thread in this forum.

I've been a huge fan of this Ubuntu Forum since it almost every problem I've seen was posted with a solution -- almost without fail.  And I've tried solutions for similar problems I listed above but found nothing that works (including adjusting the signal and tuning timeouts).  I suspect this is probably caused by my doing something stupid, but I'm at a loss.

Here's my configuration that I've been trying to build:
MSI H57M-ED65 LGA 1156 Intel H57 HDMI Micro ATX
Intel Core i3-560 Clarkdale 3.33GHz 4 x 256KB L2 Cache 4MB L3 Cache LGA 1156 73W Dual-Core
G.SKILL Ripjaws Series 4GB (2 x 2GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800) Desktop Memory
Western Digital Caviar Green WD10EADS 1TB 32MB Cache SATA 3.0Gb/s 3.5" Internal Hard Drive
Rosewill RNX-N2X IEEE 802.11b/g/n USB2.0 Wireless-N 2.0 Dongle (runs great using the blacklist recommendations on the forum)
Hauppauge WinTV-HVR-2250

In a Thermaltake case and powersupply -- nothing fancy.

I'm using Ubuntu 10.10 (64 bit) as my base and loaded Mythbuntu through synaptic.  I'm hooked up to a Samsung TV via HDMI and have gotten the sound to work using 10.10's normal adjustments.

I suspect the problem is related to the HVR-2250.  I used LowSky's tutorial for the 2250 in this forum to load the firmware, but did not recompile since 10.10 recognizes the card once the firmware is installed.  My second thought is maybe I should try the 32bit version on Mythbuntu, but have no good reason for this other than a gut feeling.  Another possibility is Intel's graphics driver for the i3, but this seems like a rather large leap since watching and playback seem to be fine.

---

### Post by LowSky on 2010-11-22
1. When you added the tuner to the backend you need to add it twice. If you have done so and are watching live TV to use the other tuner press M and switch to the other tuner form the menu.

2.If you have two entries it means you are useing two different scheduling list and its getting confused. You should only have one schedule list tied to both tuners.

3. Recordings will should only show if you recorded them, or set Mythtv to record. Again check your settings

4. More than likely you only have one tuner correctly setup and somehow used the same tuner twice when creating input connections.

Frame buffer issues can be from any number of things. we will need to see your mythfrontend logs. It can also be caused by your choice in video playback option.

see my tutorial on getting the hvr-2250 up and running.
[http://ubuntuforums.org/showpost.php?p=9219191&postcount=212](http://ubuntuforums.org/showpost.php?p=9219191&postcount=212)

Many people including myself make errors because of incorrectly reading instructions. Take your time and hopefully things will work out. The tutorial was written for 10.04 but work just fine with 10.10.

---

### Post by vanbob on 2010-11-22
Thanks for the quick response.  I tried "M" to switch tuners and both were listed.  I then went into the backend and deleted all capture cards and carefully re-initialised them.  Restarted the system and tried the frontend again.  This time "M" worked fine -- only the other tuner was listed -- and I could switch easily.  Foolishly, I started recording two programs, got out and went back into the frontend.  For kicks, I tried to watch live TV and a dialog box opened telling me both tuners were busy recording, but I could watch one of the records.  Why not?  I tried one of them and there I was watching the recording -- only I couldn't get out.  I tried everything -- no key seemed to have any effect.  Eventually, I powered the system down, restarted, stopped the recordings, and things seemed to work fine.

It looks like I'm halfway there.  I still have the problem with not being able to delete recordings and there's this messy thing that I just mentioned.  Also, only one of the two recordings I mentioned above showed up on the list of recordings I could watch, but both were in the "recordings" directory.  I'll try a couple things, but I'm afraid I might have to rebuild everything again.

---

### Post by LowSky on 2010-11-22
did you change the paths to were recordings are to be kept, if you did you might not have the correct permissions for that location. They need ot be added to the mythtv group.

---

### Post by vanbob on 2010-11-22
I didn't change any of the paths.  I made that mistake a few days ago and ended up rebuilding the system before posting this.

I've checked to see if I had appropriate permission by deleting some recordings and that worked fine even though the Frontend still shows the deleted recordings in the list of available to watch.  Is there an easy way to reset the list of recordings?  I suspect I did something wrong screwing things up when I created the previous problem.

By the way, if I reinstall everything, should I:
1.  Use 32bit instead of 64?
2.  Recompile the HVR-2250 drivers and install them?  I've always found that the fewer changes from the 'normal' release the better.
3.  Install Mythbuntu directly and not load after Ubuntu?  (I'm starting to get used to Mythbunty interface).

These are probably pretty stupid questions, but I really don't know the answers.

Again, thanks for your quick response.

Cheers,

Bob

---

### Post by LowSky on 2010-11-22
you cant delete recordings from the hard drive directly. it screws up the database. if you end up doing that you need to remove them from the frontend as well.

there is no difference with the 32 and 64 bit verison other than the processing.
you already have the tuners working, that isn't the problem
im using Ubuntu with mythtv, it works fine. I'm guessing you somehow might have messed up your database. without seeing your setup I cant confirm that

---

### Post by vanbob on 2010-11-23
Okay, I rebuilt the system from scratch again taking special care when adding capture device and assigning input.  This was interesting.  I loaded the firmware for the HVR-2250 prior to configuring mythbackend (very first time).  It added me to the mythtv group and I restarted the system as requested.  Now, when I really got into the mythbackend, I found couldn't assign input to the second capture device.  It would only let me assign to the first device.  If I selected the second device, it would always just show the first device (which may have happened before, but I didn't notice).  I went out and tried again and found this time I could assign input to the second device!  Instead I deleted both devices, recreated them, and assigned them to the correct input as I did previously in this thread.

I have no idea why this happened, but remembering my previous setups, I got out of configuring the backend and reentered before completing the assignment of inputs.  Again, I may be doing something stupid; however, there really isn't much time from reinstalling the system and configuring the capture cards for me to really mess things up.

On to watching TV.  It seems to work fine.  I started a recording and found I couldn't watch live TV on the tuner that was used to record.  Fine.  I stopped the recording things seem to work fine.  I'll try two recordings at once again this evening to see if the same problem mentioned about occurs again.  Otherwise, this is livable.

Finally, I tried to watch the recording I just made.  The list showed only the one recording and I was able to watch it.  However, I wasn't able to delete the recording.  When I get some more time, I'll go revisit some threads in this forum that seemed to have encountered a similar problem.

I'm make another post after I finish my homework...

---

### Post by vanbob on 2010-11-24
I tried two recordings last night and the system performed as one would expect.

As for not being able to delete recordings, well, let's just say that this was a user error.  It works fine.

This leaves something happened when I first added the capture device and tried to assign input.  The workaround is simply to carefully inspect the results of these steps prior to proceeding to using the front end.  If necessary, delete all the capture devices and recreate them.

Thanks to LowSky for helping me. :D

---

