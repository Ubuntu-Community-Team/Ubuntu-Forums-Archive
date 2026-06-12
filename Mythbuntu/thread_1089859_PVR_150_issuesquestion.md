---
title: "PVR 150 issues/question"
date: 2009-03-07
forum: Mythbuntu
---

### Post by codymyth on 2009-03-07
i am trying to set up my pvr 150 to work with mythtv and using marks guide to set it all up. i can do the first 6 steps but then i step 7 when i try to run 'modprobe lirc_dev debug=1 && modprobe lirc_pvr150 debug=1' i get a fatal error message and it tells me the the operation is not permitted 

Can anybody help me out and tell me what i did wrong or didn't do.

thanks

p.s. here is the website [http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24)

---

### Post by scooter29 on 2009-03-07
:(  Been there done that! LOL.

I had to completely remove lirc to get this to work. Make backups of /etc/lirc/lircd.conf and hardware.conf FIRST! at least hardware.conf for sure!

sudo apt-get --purge remove lirc (from command line)

This will also uninstall mythbuntu Control Centre - mythbuntu-lirc-generator as well! Don't fret as when you're done just reinstall with synaptic package manager.

Then follow Marks directions. 
[http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24)


Don't do his commands together or that have the && sign combining them. break them up. For example your fatal error loaded lirc_dev however squakked about lirc_pvr150. Just do a modprobe lirc_dev debug=1. When finished do a modprobe lirc_pvr150 debug=1.

You will need the firmware saved under /lib/firmware and Mythbuntu's lircd.conf files _DO NOT WORK!!!_ Follow Mark's directions on creating your own, putting the blaster before the remote (in your custom cofig file)  and saving as /etc/lirc/lircd.conf 

Edit your hardware.conf ( /etc/lirc/hardware.conf ) file listing only "lirc_dev lirc_pvr150" in the modules selection of remote and "/etc/lirc/lircd.conf" as your location everything else left blank or "" in both remote and blaster sections. 

Bear with me as I'm not on my machine right now, playing from memory. I googled and found a shell script for my change channel.sh as I had problems with perl. you should be able to irsend from command line, just remember that mythbuntu loads your blaster as /dev/lircd not /dev/lirc0 ( after reboot, or you can just modify Marks command when he loads device, so as to not confuse you with your script ) Also Mythbuntu needs to say irsend -d /dev/lircd to work correctly. 

I should also tell you that I looked at the mythbuntu installation guide under serial ir transmitter, and I had to create a file under /etc/modprobe.d/lirc I believe; reconfigured lirc-serial
 
sudo dpkg-reconfigure setserial

selected manual and added text ( /dev/ttyS0 uart none ) to /var/lib/setserial/autoserial.conf and then saved and copied that file in /etc/serial.conf folder as well.

Then I went to synaptic package manager searched for mythbuntu control centre and selected to reinstall. When it loads it will try and overwrite your lircd.conf file and hardware.conf file just select keep your own. 

Open up Mythbuntu Control Centre and select ir devices, select custom for remote, your config is /etc/lirc/lircd.conf, check to make buttons. _DO NOT SELECT A IR DEVICE._ Reboot, if you hit cntrl,F1 when your splash screen loads it looks like lirc fails, however if your lircd.conf file is set correctly it should work. 

All of this together should get you going. :popcorn:

Stay at it as I fumbled with this for over a month with no help and trial and error. If you follow Marks guide and Mythbuntu setup guide as well as good lircd.conf, hardware.conf, and change_channel.sh scripts you shoud be up and running! Good luck!!

I wish someone had helped me even this much probably would have taken only a couple of hours versus, spotting baldness, Divorce pappers and a huge ulcer LOL.:)

---

### Post by scooter29 on 2009-03-09
Did this help you?

---

